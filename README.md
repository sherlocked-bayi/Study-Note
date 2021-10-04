# C++ Study-Note

## 变量
- 全局变量时初始化为0，局部变量时初始化为随机值
- 全局变量和静态局部变量的存储空间在程序结束时释放，
   局部变量A(A *pa=new A()) 是通过 new 从系统的堆空间中分配的，程序运行结束之后，系统是不会自动回收分配给它的空间的，需要程序员手动调用 delete 来释放。
   局部变量 B(B b) 对象的空间来自于系统的栈空间，在该方法执行结束就会由系统自动通过调用析构方法将其空间释放
- sizeof是操作符，在编译阶段就获得结果，strlen是函数调用，在运行阶段才获得值。在编译时sizeof(float)就是个常量4,所以是一个整形表达式
- 在C++语言中, %运算符要求运算数必须是整型
- C语言规定用户表示只能由字母，数字，下划线组成，且只能由字母或下划线开头，不能是关键字

## 进制常识：
- C语言、C++、Shell、Python、Java语言及其他相近的语言使用字首“0x”，例如“0x5A3”。开头的“0”令解析器更易辨认数，而“x”则代表十六进制（就如“O”代表八进制）。在“0x”中的“x”可以大写或小写。对于字符量C语言中则以x+两位十六进制数的方式表示，如xFF。
- 字节长度：
  char每次移动1个字节；short移动2个字节 ；int , long ,float移动4个字节 ；double移动8个字节

- 单精度浮点数的有效位数是7位。
  双精度浮点数的有效位数是16位。

- 不管32位还是64位机子，int都是4字节，指针在32位是4字节 64位是8字节，32位下操作系统可以使用的最大内存空间是2^32，64位下可以使用的最大内存空间是2^64

- 类空间大小是成员中内存最大值的最小整数倍，虚函数会占用内存空间，32位系统中占用4位，64位系统中占用8位。并且子类占用的空间大小应该加上父类占用的空间大小。空类的内存大小是１个字节

- 结构变量所占的内存空间至少是所有成员变量所占空间之和。系统为结构变量的各个成员依照成员定义的顺序在内存中依次分配空间。联合变量所占的内存大小等于其中最大的一个成员的空间大小

## 虚函数：
- 虚函数必须是成员函数

- 虚函数和函数重载都实现了C++的多态性，但表现形式不一样，函数重载调用根据参数个数、参数类型等进行区分，而虚函数则是根据动态联编来确定调用什么

- 设置虚基类的目的是消除二义性

- 抽象类不可以实例化出对象，但可以有抽象类的指针和引用

- 如果不使用多态机制(虚函数)，那么通过基类的指针虽然可以指向派生类对象，但是只能访问从基类继承的成员
- 构造函数和析构函数：
  构造函数和析构函数的调用顺序刚好相反
- 对齐原则：
   对齐原则：每一成员需对齐为后一成员类型的倍数
   补齐原则：最终大小补齐为成员类型最大值的倍数
- 函数重载：
  1.必须是同一个类
  2.方法名（也可以叫函数）一样
  3.参数类型不一样或参数数量不一样
  4.赋值操作符重载仅发生在对象已经执行过构造函数，即已经创建的情况下
- 函数重写(两同两小一大)：
  1.方法名相同，参数类型相同
  2.子类返回类型小于等于父类方法返回类型
  3.子类抛出异常小于等于父类方法抛出异常
  4.子类访问权限大于等于父类方法访问权限

## 类相关：
- 父类指针指向子类实例对象，调用普通重写方法时，会调用父类中的方法。而调用被子类重写虚函数时，会调用子类中的方法。

- 类空间大小是成员中内存最大值的最小整数倍，虚函数会占用内存空间，32位系统中占用4位，64位系统中占用8位。并且子类占用的空间大小应该加上父类占用的空间大小。空类的内存大小是１个字节

- C++类可以使用Objective-C对象的指针作为数据成员，Objective-C类也可以有C++对象指针做实例变量

- 抽象类是指具有纯虚函数的类

-
- Objective-C声明一个类所要用到的编译指令是@interface　Someclass

## 指针相关：
- 计算优先级



- 数组指针和指针数组
   数组指针：定义 int (*p)[n]; 本质上是指针，p是一个指针，指向一个整型的一维数组，这个一维数组的长度是n，也可以说是p的步长。
   指针数组：定义 int *p[n]; 本质上是数组，有n个指针类型的数组元素。

## 头文件：
- ifndef/define/endif 的含义:如果未定义 / 那么定义 / 完成假设，一般是用来防止头文件被重复包含，提高编译效率的。

- 用户调用标准库函数，必须利用#include来对其进行声明。

- 标准库函数可以被重载而不能重新定义，重载后函数具有不同的形参，但是原有的定义并不失效。

- 当用户调用标准库函数前，必须使用#include预编译命令将函数所在文件包括到用户源当中。

## 指针和引用：
- 指针传递参数本质上是值传递的方式，它所传递的是一个地址值。值传递过程中，被调函数的形式参数作为被调函数的局部变量处理，即在栈中开辟了内存空间以存放由主调函数放进来的实参的值，从而成 为了实参的一个副本。值传递的特点是被调函数对形式参数的任何操作都是作为局部变量进行，不会影响主调函数的实参变量的值。
- 引用传递过程中，被调函数的形式参数也作为局部变量在栈中开辟了内存空间，但是这时存放的是由主调函数放进来的实参变量的地址。被调函数对形参的任何操作都被处理成间接寻址，即通过栈中存放的地址访问主调函数中的实参变量。正因为如此，被调函数对形参做的任何操作都影响了主调函数中的实参变量。

- 从概念上讲。指针从本质上讲就是存放变量地址的一个变量，在逻辑上是独立的，它可以被改变，包括其所指向的地址的改变和其指向的地址中所存放的数据的改变。
  而引用是一个别名，它在逻辑上不是独立的，它的存在具有依附性，所以引用必须在一开始就被初始化，而且其引用的对象在其整个生命周期中是不能被改变的（自始至终只能依附于同一个变量）。

★相同点：
 都是地址的概念；
 指针指向一块内存，它的内容是所指内存的地址；而引用则是某块内存的别名。
★不同点：
 指针是一个实体，而引用仅是个别名；
 引用只能在定义时被初始化一次，之后不可变；指针可变；引用“从一而终”，指针可以“见异思迁”；
 引用没有const，指针有const，const的指针不可变；
 具体指没有int& const a这种形式，而const int& a是有的，前者指引用本身即别名不可以改变，这是当然的，所以不需要这种形式，后者指引用所指的值不可以改变）
 引用不能为空，指针可以为空；
 “sizeof 引用”得到的是所指向的变量(对象)的大小，而“sizeof 指针”得到的是指针本身的大小；
 指针和引用的自增(++)运算意义不一样；
 引用是类型安全的，而指针不是 (引用比指针多了类型检查）

- 指针指向一块内存，它的内容是所指内存的地址；而引用则是某块内存的别名，引用不改变指向。

## 常见函数作用：
- 字符串比较函数strcmp（参数1，参数2），比较两个参数的ASC||码，若参数1>参数2，则返回正数，若小于则返回负数，相等则返回0

- if语句里可以是任意表达式

- strcpy函数的作用是把含有“'\0'”结束符的字符串复制到另一个地址空间。strcpy是一种C语言的标准库函数，返回值的类型为“char*”；strcpy是“string copy”（字符串复制）的缩写。

- 内联函数在编译时是将该函数的目标代码插入每个调用该函数的地方，类内定义的函数都是内联函数，在类外定义内联函数时需要使用inline修饰符
  内联函数具有一般函数的特性，它与一般函数所不同之处只在于 函数调用 的处理。一般函数进行调用时，要将程序执行权转到 被调用函数 中，然后再返回到调用它的函数中；而内联函数在调用时，是将调用 表达式 用内联函数体来替换。
-- 在内联函数内不允许用 循环语句 和开关语句。　如果内联函数有这些语句，则编译将该函数视同普通函数那样产生函数调用代码,递归函数(自己调用自己的函数)是不能被用来做内联函数的。内联函数只适合于只有1～5行的小函数。对一个含有许多语句的大函数，函数调用和返回的开销相对来说微不足道，所以也没有必要用内联函数实现。
-- 内联函数的定义必须出现在内联函数第一次被调用之前。


- abs 函数是存在于多种编程语言中的一种用于求数据绝对值的函数

- 友元函数是一种在类外定义，在类内特殊声明(加关键字friend)，并且可以在类外访问类的所有成员的非成员函数。友元函数相对于普通函数，增加了访问类成员的权利。友元函数可以像普通函数一样直接调用，不需要通过对象或指针；友元函数不是成员函数，所以不能被继承，也同样没有this指针；由于友元函数和普通函数的区别仅仅是具有访问类成员的权利，和继承性机制没有关系；友元函数破坏了类的封装性

- for 语句使用最为灵活，它完全可以取代 while 语句

## 调用拷贝构造函数的3种情况：
- 用一个对象去初始化同一个类的另一个新对象时
- 函数的形参对象，调用函数进行形参和实参结合时 
- 函数的返回值是类的对象，函数执行返回调用时
  将一个对象赋值给另一个对象，两个对象都存在，调用的是赋值构造函数，不涉及内存的分配，当被赋值的对象不存在调用的是拷贝构造函数。

## 通配符：
-通配符是一种特殊语句，主要有星号(*)和问号(?)，用来模糊搜索文件。
 【 * 可以代表任何文字】
 【 ? 仅代表单个字】

## 数组：
- 一维数组：
  作为实参：一维数组的定义不需要定义长度，系统有时候可以自己判断长度，比如：int a[] = {1,2};
  作为形参：在函数的形参定义时，有没有长度无所谓，参数传递是以指针形式实现的；比如void fun(int a[]){}

- 二维数组则不同：
  作为实参：二维数组定义的时候，一定要给定第二维（列）的长度！
  作为形参：假如定义了int a[2][3]，这里的a不是二级指针int **p，而是表示数组指针，也就是说a是指向大小为3的一维数组的指针，(a+1)则是下一个大小为3的一维数组的指针

## vector：
- vector和built-in数组类似，它拥有一段连续的内存空间，并且起始地址不变，因此它能非常好的支持随即存取，即[]操作符，但由于它的内存空间是连续的，所以在中间进行插入和删除会造成内存块的拷贝，另外，当该数组后的内存空间不够时，需要重新申请一块足够大的内存并进行内存的拷贝。这些都大大影响了vector的效率。

- vector<int>::iterator支持“+”、“+=”、“<”，“[ ]”等操作符

## list：
-list就是数据结构 中的双向链表(根据sgi stl源代码)，因此它的内存空间可以是不连续的，通过指针来进行数据的访问，这个特点使得它的随即存取变的非常没有效率，因此它没有提供[]操作符的重载。但由于链表的特点，它可以以很好的效率支持任意地方的删除和插入。

-list<int>::iterator则不支持“+”、“+=”、“<”、“[ ]”等操作符运算

## 模板：
-  (1)可用来创建动态增长和减小的数据结构 
  （2）它是类型无关的，因此具有很高的可复用性。 
  （3）它在编译时而不是运行时检查数据类型，保证了类型安全 
  （4）它是平台无关的，可移植性 
  （5）可用于基本数据类型

## 运算符
-三目运算符从右到左运算

-只能使用成员函数重载的运算符有：=、()、[]、->、new、delete
