# Angularjs-demo

### angular有哪些特性：       
* MVC模式       
* 模块系统       
* 指令系统       
* 依赖注入       
* 双向数据绑定       


* 依赖注入的形参是不能变的：
* $scope  是一个作用域
* $rootScope  是一个全局作用域

### angular的指令系统：
* ng-app   
    * 初始化的指令，必须要写
    * 可以局部写，值针对局部
    * 可以在根部HTML上写，针对全局

* ng-controller  
    * 连接视图与控制器的桥梁

### angular的双向数据绑定：
    MVVM
    M数据
    V视图
    V视图
    M数据
    也就是视图影响数据和数据影响视图的改变就是双向数据绑定

* $timeout
    * 定时服务，注入到函数中形参的形式
    * 改变数据相当于setTimeout，但是setTimeout不具备改变数据时候刷新
```javascript
$timeout(function(){
      //do something
},1000)
$timeout.cancel(timer);清除定时器
```

* $interval 
    * 定时炸弹相当于setInterval，但是setInterval不具备改变数据的时候刷新
```javascript
$interval(function(){
//do  something
},1000)
$interval.cancel(timer);清除定时器
```



* ng-click
    * 点击指令相当于click

* ng-model

* currency
    * 过滤器
    * 默认开头前面为美元符号  
    * 修改美元符号为人民币   currency:'RMB'
    * 可以将数字之间划逗号 比如：1000,100

* $watch('iphone.money',function(){})
    * 一共有三个参数，前两个参数必须写，
    * 参数一:监听谁
    * 参数二:监听的这个参数发生变化时的处理函数
    * function(newVal,oldVal){}
    * 接收2个参数：新的数据值，老的数据值
    * 参数三:深度监听    true/false    监听多值/监听单值
    * 监听数据变化，做出相应的处理
    * 如果只写前面2个参数那么只能监听单值的数据的变化
    * 如果要监听多值的监听的话填写第三个参数为true
    * 可以监听数值，也可以监听函数


### angular的模块化：
* angular.module
    * 是一个方法：angular.module('myApp',[])
    * 一共有三个参数：
    * 参数一：创建模块名称
    * 参数二：数组(依赖模块)  没有就是空数组


### angular的工具方法：
* angular.bind
    * 改变this指向

* angular.copy
    * 拷贝对象

* angular.extend
    * 对象继承

* angular.isArray
    * 判断是不是数组

* angular.isDate
    * 判断是不是时间对象

* angular.isDefined
    * 判断一个元素是不是存在的

* angular.isUndefined
    * 判断一个元素是不是undefined

* angular.isFunction
    * 判断是不是函数

* angular.isNumber
    * 判断是不是数字

* angular.isObject
    * 判断是不是对象

* angular.isString
    * 判断是不是字符串

* angular.isElement
    * 判断是不是元素

* angular.version
    * 判断angular当前版本

* angular.equals(a,b)
    * 判断两个元素是否相等

* angular.forEeach(arr,function(  arr,i  ){  },result);
    * 进行遍历操作

* angular.fromJson  /  toJson()
    * 对JSON进行解析  进行转换
    * 相当于原生 JSON.parse() /  JSON.stringify()

* angular.identity  /  noop
    * 参数传递的是什么，那么最终结果是什么
    * noop()返回空函数
    * 来进行一些默认操作的，防止程序出问题

* angular.lowercase  /  uppercase
    * 大转小写 /  小转大写     

* angular.element
    * 来获取元素，对元素进行后续的操作

* angular.bootstrap(document,[])
    * 动态进行初始化 也就是ng-app
    * 一个页面进行多次初始化应用的时候，可以调用这个方法
    * angular.bootstrap(aDiv[0],['myApp1']);
    * angular.bootstrap(aDiv[1],['myApp2']);

* angular.injector
    * angular内部使用的，很少外部来用，注册器


* $scope:
    * $scope.$watch
    * 监听数据改变

* $scope.$apply
    * 针对数据变化，监听数据变化，一旦有变化就会影响视图
```javascript
setTimeout(function(){
$scope.$apply(function(){
$scope.name =  'hi'
})
},2000)
```
正常情况下setTimeout是不会发生视图变化的

* angular.module
    * controller
    * 控制器：调用控制器把数据与视图连接到一起

* run
    * 初始化全局的数据,
```javascript
m1.run(['$rootScope',function($rootScope){
$rootScope.name  =  'hello';
}])
```
注意：只能全局作用域下才能使用


### angular的过滤器
* currency
    * 钱的那个逗号 可以修改单位
    * {{  name |  currency  :  ' ￥ '  }}

* number
    * {{ name | number  :  0  }}
    * 保留小时，可以选择保留多少个小数，最少保留0条小数

* lowercase /  uppercase
    * {{ name |lowercase }}  //转小写
    * {{ name  |uppercase  }}  //转大写

* json
    * 将json格式的字符串显示更友好
    * <pre>{{ name |  json  }}</pre>  //注意：必须在<pre>标签，因为能够识别
    * 转换为：
         ```javascript
            {
            "name"  :  "hello",
            "age"  :  "20"
            }
        ```

* limitTo
    * 截取的操作，数组、字符串
    * {{ name  |  limitTo :  2 }}      //截取2位

* date
    * {{ name  |  date }}   //转换为日期  默认 Feb  13,1970
    * {{ name | data  :  '  yyyy-MM-dd hh:mm:ss '  }}     //结果：2011-05-03 06:39:08 

       
* orderBy
    * 排序 针对数组 数组格式必须：
```javascript
$scope.name =  [
{  name :  'red'  ,  age  :  '20'  },
{  name :  'yellow'  ,  age  :  '15'  },
{  name :  'blue'  ,  age  :  '40'  },
{  name :  'green'  ,  age  :  '10'  },
]
{{  name | orderBy  :    'color'  ： true  }}    //默认从小到大排序  第三个参数可以逆排序
```

* filter
    * 过滤器的方法
         * {{ name  |  filter  :  'red'  :  true }}  
    * 过滤掉当前写的这个  其他全部保留
    * 参数三是true  是匹配整体

#### 过滤器的扩展：
* 一个表达式中使用多个过滤器组合使用
    * {{ name  | limitTo:2 |  uppercase }}

* $filter   和上面的filter是一样的  
* 一个是下表达式中做   {{ name  |  filter  :  'red'  :  true }}  
* 一个是在函数中做   $scope.name =  $filter('  date  ')('  254815  ','  hh ')

#### 自定义过滤器：
* 必须在模块下面进行实现的
```javascript
m1.filter(' firstUpper ',function(){      //自定义过滤器  firstUpper自定义过滤器的名字
return function( str ){
return str.charAt(0).toUpperCase()  +  str.sustring(1);
}
})
```


### 指令：
ng-app       
ng-controller  调用控制器把数据与视图连接到一起       
ng-click       
ng-model       
* ng-repeat       
    * 遍历集合：
    * 通过in的方式遍历每一项
    * ng-repeat="data in dataList"

* ng-repeat指令：
    * 扩展部分：
    * $index
    * 得到遍历的索引
    * <li  ng-repeat="  data in datalist  ">{{ $index }}</li>

* $first
    * 只要是集合的第一项就会返回真 true   否则是false
    * <li  ng-repeat="  data in datalist  ">{{ $first }}</li>

* $middle
    * 中间项都会返回真 true，否则就是假 false   除了首项和尾项  其他都是中间项
    * <li  ng-repeat="  data in datalist  ">{{ $middle }}</li>

* $last
    * 只要是集合的最后一项就会返回真 true 否则是false 
    * <li  ng-repeat="  data in datalist  ">{{ $last }}</li>

* $even
    * 代表奇数，返回true，否则false
    * <li  ng-repeat="  data in datalist  ">{{ $even }}</li>

* $odd
    * 代表偶数，返回true，否则false
    * <li  ng-repeat="  data in datalist  ">{{ $odd }}</li>

ng-repeat-start
ng-repeat-end
```javascript
<div  ng-repeat-start=" data in datalist ">{{ data }}</div>
<p>{{ data }}</p>
<div  ng-repeat-end>{{ data }}</div>
```


### 事件指令：
和传统的事件区别：可以直接写表达式，可以直接操作数据变量，进行动态的操作
ng-click /  dbclick
ng-mousedown /  up
ng-mouseenter /  leave
ng-mousemove /  over /  out
ng-keydown /  up /  press
ng-focus /  blur
ng-submit

### 事件指令：
* ng-selected
    * 下拉菜单选中触发
```javascript
<input  type="checkbox"  ng-model= "  aaa ">
<select>
<option>1111</option>
<option  ng-select=" aaa ">2222</option>
</select>
```
当我选中checkbox 下拉框也跟着选中我绑定的aaa

* ng-change
    * 当输入框中的数据发生改变的时候触发
    * <input   type="text"  ng-change=" bbb='hello' "  ng-model=" bbb " />{{ bbb }}
    * 使用ng-change一定要配合ng-model不然没效
    * 只要改变input框的值的时候bbb的值就为hello
    * 也可以写函数形式触发

* ng-copy
    * 在input框进行复制的时候就会触发ng-copy指令
    * <input   type="text"   value="sfsgfdgd"  ng-copy="ccc=true"/>{{ ccc }}
    * 只要进行了复制那么{{ ccc }}的值就会变为true

* ng-cut
    * 在input框进行剪切的时候就会触发ng-cut指令
    * 以上同理

* ng-paste
    * 在input框进行粘贴的时候就会触发ng-paste指令
    * 以上同理


### input 相关指令：
和传统的input事件区别：可以直接写表达式，可以直接操作数据变量，进行动态的操作
* ng-disabled
  	* 按钮禁止使用属性
    * <input type="button" value="{{text}}" ng-disabled="isDisabled"/>
    * 在模块函数中使用 $scope.isDisabled = true;

* ng-readonly
    * input输入框禁止使用属性 显示上面不是禁止的  有光标出现  但是不能输入任何东西

* ng-checked
    * 单选框和复选框的选中状态的操作

* ng-value
    * 和value的区别是：
    * 变量一个要写花括号一个不用谢花括号，建议使用ng-value 因为优化时间上对比ng-value的速度要快，用户体验要好
    * <input type="button" value="{{text}}" />
    * <input type="button" ng-value="text" />

### 其他指令：
* ng-bind
    * <div  ng-bind="text"></div>

* ng-cloak
    * 标签隐藏 相当于style="display:none"

* ng-bind-template   
    * 支持多个指令，支持多个表达式
    * <div  ng-bind-template="  {{text}}  ,  {{text}} "></div>

* bg-bind-html
    * 把HTML标签结构的代码用字符串格式显示在页面当中
    * $scope.text =  '<h1>hello<h1>'
    * <div  ng-bind-html="text"></div>

* ng-non- bindable
    * 不被解析也就是花括号里的写的什么就是什么{{ text }}

### 样式相关的指令：
* ng-class
    * <div  ng-class=" { red:true } "></div>

* ng-style
    * <div  ng-style=" { color  :  '  red  '  ,  background  :  '  yeollw ' } "></div>

* ng-href
    * <div  ng-href="{{url}} "></div>

* ng-src
    * <div  ng-src="{{url}}"></div>

* ng-attr-(suffix)
    * ng-attr-任何属性名称
    * <div  ng-href="{{url}}   ng-attr-title="{{text}}"></div>

### DOM相关指令：
* ng-show
    * <div  ng-show=" true "></div>    显示
    * <div  ng-show=" false "></div>    隐藏
    * 应用：勾选复选框字体显示隐藏
    * $scope.Btn  =  true
    * <input   type="checkbox"   ng-model="  Btn  " />
    * <div  ng-show="  Btn  "></div>

* ng-hide 
    * <div  ng-hide=" true "></div>  隐藏
    * <div  ng-hide=" false "></div> 显示

* ng-if
    * 对DOM节点添加和删除的操作
    * <div  ng-if=" true "></div>   添加
    * <div  ng-if=" false "></div>   删除

ng-swtich
on
default
* when
    * 应用：一开始显示默认效果 当点击复选框的时候显示切换效果  ng-swtich   on=" Btn " 配合使用
    * $scope.Btn  =  true
```javascript
<input   type="checkbox"   ng-model="  Btn  " />
<div  ng-swtich   on=" Btn ">
<p  ng-swtich-default>默认效果</p>
<p  ng-swtich-when="false">切换的效果</p>
</div>
```

* ng-open
    * 初始控制打开效果
```javascript
<details  ng-open=" true ">     
<summary>Copyright  2011.</summary>
<p>All  pages and graphics on this web site are the property of W3Shool</p>
</details>
```

### 扩展指令：
* ng-init
    * 初始化设置  text变量为hello
    * <div  ng-controller="Aaa"  ng-init=" text='  hello ' ">{{ text }}</div>

* ng-include
    * 通过模板的方式引入文件
    * <div  ng-controller="Aaa"  ng-include="' temp.html '"></div>  引入temp.html文件里的东西

* ng-model  双向数据绑定
* ng-model-options  控制双向数据绑定的具体过程
    * <input type="text"  ng-model="text"  ng-model-options=" { updataOn :  ' blur ' } " />
    * 当光标移出的时候显示数据变化

* updataOn 
    * 控制光标效果


* ng-controller
    * as  支持面向对象构造函数的调用方式
    * FnAaa  as a1    构造函数 as 一个对象的形式可以找到相关的属性和方法
```javascript
var m1=angular.module('  myApp  ',[]);
m1.controller('  Aaa  ',['  $scope  ',  FnAaa]);
function  FnAaa(  $scope  ){
}
FnAaa.prototype.num =  '  123  ';
FnAaa.prototype.text =  '  hello  ';
FnAaa.prototype.show =  function(){
return '  angular.js '
} 
```

```html
<div  ng-controller="FnAaa  as a1">
<div>{{  a1.text  }}</div>
</div>
```



### 标签指令：
* <a>
    * 在angular中<a>标签会阻止默认行为

* <select>
    * ng-options
    * >>  for in
        * 用在表单验证当中
        * 用法：
```javascript
$scope.colors =  [
{  name :  ' red '},
{  name :  ' green '},
{  name :  ' yellow '},
]
```
```html
<div  ng-app="myApp"  ng-controller="Aaa">
<a href="  ">{{ myColor.name }}</a>
<select  ng-options=" color.name for in colors "  ng-model=" myColor ">

</select>
</div>
```
注意： 使用ng-options 必须用 ng-model 不然不显示


<textarea>
<input>
<form>
novalidate 阻止表单默认的行为
```javascript
<form  novalidate>
<input  type="email"/>
</form>
```

### 表单验证：
* $valid
    * 表单验证通过这个值就是真true，验证不通过就是false

* $invalid
    * 表单验证失败就会返回真true，验证成功了就会返回false

* $pristine
    * 验证值，也就是初始值没有进行修改过那么返回值就是true，修改过值那么就是false

* $dirty
    * 验证值，如果是修改过的那么就是true，如果没有被修改过那么就是false

* $error
    * 当验证失败或者验证成功，有验证信息 做后续的验证开发

* 注意点：
    * 通过name的方式进行查找
    * 表单验证一定要写ng-model

用法：
```html
<form  novalidate  name=" myForm "> 
<input   type="email"   name= "  myText  "  ng-model=" text "/>
<div>{{ myForm.myText.$valid }}</div>
<div>{{ myForm.myText.$invalid }}</div>
<div>{{ myForm.myText.$pristine }}</div>
<div>{{ myForm.myText.$dirty }}</div>
<div>{{ myForm.myText.$error }}</div>   
</form>
```

### 表单的验证：
type
email   验证邮箱
number  验证数字
url	验证url
text   文本
password  密码
 
* required
    * 判断表单是否为空
    * 为空就是true,否则就是false

* ng-minlength
    * 判断字符的长度，最小长度

* ng-maxlenght
    * 判断字符的长度，最大长度

* ng-pattern
    * 通过正则的方式来通过验证
```html
<input   type=" text "  name=" myText "  ng-model=" text "   required  ng-minlength=" 5 "  ng-pattern=" /^[a-zA-Z]+$/ ">
```

* 表单验证样式颜色：
    * input.ng-valid{  }    表单验证通过样式
    * input.ng-invalid{  }   表单验证失败样式
    * input.ng-pristine{  }  验证值，初始值没有进行修改过
    * input.ng-dirty{  }  验证值，如果是修改过


### 自定义指令：
 * angular.module
    * 》controller
    * 》 run
    * 》 filter
    * 》 directive   自定义指令的核心
* restrict    自定义指令的类型
    * 指令类型有4种：
        * E：element A：attribute M：comment C: class
        * 标签指令 restrict  :  " E ";    // <hello></hello>
        * 属性指令 restrict  :  " A ";    // <div hello></div>
        * class指令 restrict  :  " C";    // <div  class=" hello "></div>
        * 注释指令：restrict  :  " M";  // <!---  两边一定要留空格，不然什么都不会发生 --->没有发生任何变化  *  不会被解析   如果要能够解析出来就要写 replace ：true  原因是让模板替换注释
        * 注意：区分大小写，指令类型是可以组合使用的 比如：'AE'

replace  替换模本        

* template   模板方式           
    * template ：'<div>hello angular</div>'          

templateUrl    引用外部文件作为模板          
templateUrl :  'temp.html'          

* scope          
    * 独立作用域 true
    * 隔离作用域 {}
    * @   指定谁就是谁  当相同的id时候可以使用 只能绑定字符串
    * =    解析的是数据 是变量名  需要实现双向数据绑定的时候使用
    * &   绑定父级函数传递方式
    * 上面3个东西叫做绑定策略

controller   //数据共享  共有的方法   在其他指令可以被找到          
用法：         
```javascript 
var m1 = angular.module('myApp',[]);
m1.directive('myTab',function(){
	return {
		restrict : 'E',   
		replace : true,
		scope : {   //隔离作用域
			myId : '@',
			myName : '=',
			myFn : '&'
		},
		controller : ['$scope',function($scope){
			$scope.name = 'miaov';
		}],  //自定义指令共享的数据
		templateUrl : 'temp2.html'    //引用外部文件作为模板
	};
});
```

* 》link      //link函数主要用于操作当前dom元素,给dom元素绑定事件和监听
    * scope       //指令所在的作用域
    * element   //父级div元素
    * attr             //指令元素的属性的集合  
    * reController
    * 上面四个是link的四个参数：
写法：
```javascript
link : function( scope，element，attr，reController ){
element.datagate(' input ',' click ',function(){
$(this).attr(' class ',' active ').sibling(' input ').attr(' class ','');
})
}
```

angular.equals();       //判断2个对象是否全等   返回布尔值

### 指令的特点：
是能够复用

### 自定义指令高级：                                                                                                
* directive
    * 》 transclude
* ng-transclude   //把内部的东西扔到h1当中
    * 》 require
    * ^   父级去找指令
    * ?   找自身的指令

### angular的服务：
$scope           
$watch          
$apply          
$rootScope          
$timeout          
$interval          
$filter          
$http   相当于ajax          
method    请求方式GET、POST、JSONP          
url          
success          
error          
用法：          
```javascript
var  m1=angular.module(' myApp ',[]);
m1.controller(' Aaa ',[' $scope ',' $http ',function(){
```

```javascript
$http({
method:  ' GET ',
url:  ' data.php '
}).success(function( data,start,headers,config ){
console.log( data );
}).error(function(  data ){
    
});
}]);
```
            
$location          地址服务                      
absUrl()      //得到网址信息的绝对地址                      
path()	     //路径                                
replace()   //替换之前的路径，后退不会存在                      
hash()      //设置或者获取hash值  # + '任意字符'                      
search()  //设置或者获取？号后面的字段信息            
url()   //得到网址信息                                
host()   //主机名                      
port()   //端口号                      
protocol()  //协议                      

* $anchorScroll                      
    * 锚点跳转  跳转到指定的位置                        

$cacheFactory    //缓存服务                             
info()    //缓存的相关信息                             
put()    //缓存设置                             
get()   //获取缓存信息                             
remove()   //删除缓存信息                             

用法：            
var  cache =  $cacheFactory(' myCache ',{ capacity :  2 });  //参数2个，一个是缓存名字，一个是缓存的条数限制       


$log   打印                                         
Log()   打印                        
Info()   详细                        
warn()  警告                        
Error()  错误                        

$interpolate  差值服务                        

$q   就是promise的实现                        
defer()                               
resolve()                        
reject()                        
notify()                        
then()                        


找各种插件的网址：http://www.bootcdn.cn/angular.js/                        
