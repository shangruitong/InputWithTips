var InputWithTips = (function() {
  /**
   * new InputWithTips
   * */ 
  // 构造类
  function InputWithTips(opts) {
    this.ele = opts.ele;
    this.tips = opts.tips;
    this.input = null;
    this.inputTipsContainer = null;

    this.init();

    // this.updateSuitableTips(this.tips);
  }

  InputWithTips.prototype.init = function() {
    var self = this;
    self.initDOM();
    self.bindEvents();
  };

  InputWithTips.prototype.initDOM = function() {
    var self = this;
    console.log(self.ele);
    // 文本框
    var input = self.input = document.createElement('input');
    input.type = 'text';
    input.className = 'inputwithtips-input';
    self.ele.appendChild(input);

    // Input-tips-container
    var inputTipsContainer = self.inputTipsContainer = document.createElement('div');
    inputTipsContainer.className = 'inputwithtips-tips-container';
    self.ele.appendChild(inputTipsContainer);

  };

  InputWithTips.prototype.bindEvents = function() {
    var self = this;
    var tips = self.tips;

    // 监听input变化，给出相应的提示
    self.input.addEventListener('input', function() {
      console.log(this);
      var value = this.value;
      var suitableTips = [];
      console.log(value);
      for (var i = 0; i < tips.length; i++) {
        console.log(tips[i].indexOf(value) >= 0);
        if (tips[i].indexOf(value) >= 0) {
          suitableTips.push(tips[i]);
        }
      }
      console.log(suitableTips);
      self.updateSuitableTips(suitableTips)
    }, false);

    // 事件代理
    self.inputTipsContainer.addEventListener('click',function(e){
      var classList = e.target.className.split(' ');
      if(e.target && hasClass(e.target, 'inputwithtips-tip')){/*判断目标事件是否为li*/
        console.log('clicked');
      }

      function hasClass(ele,className){
        var classList = ele.classList || ele.className;
        for(var i = 0; i < classList.length; i++){
          if(className === classList[i]){
            return true;
          }
        }
        return false;
      }
    },false);
  };

  // 更新满足条件的列表dom
  InputWithTips.prototype.updateSuitableTips = function(suitableTips) {
    var self = this;

    var length = suitableTips.length;
    var tip;
    var children = self.inputTipsContainer.childNodes;
    for (var i = children.length -1; i >= 0; i--){
      self.inputTipsContainer.removeChild(children[i]);
    }
    
    // 像inputTipsContainer中更新tips
    for (var i = 0; i < length; i++) {
      var tip = document.createElement('div');
      tip.className = 'input-tip';
      tip.setAttribute('data-value',suitableTips[i]);
      tip.innerText = suitableTips[i];
      self.inputTipsContainer.appendChild(tip);
    }
  };
  
  return InputWithTips;
})();
