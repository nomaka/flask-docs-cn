.. _advanced_foreword:

给有经验程序员的前言
====================================

.. _thread-locals-in-flask:

Flask 中的线程局部变量
-----------------------

Flask 的设计决策之一就是让简单归简单，既不需要大量代码实现，也不会限制你的自由。为此，
我们选择了一些可能让人觉得惊讶，甚至是异端的设计。例如，Flask 内部使用线程局部的对象，
这样无须以在处理请求的函数间传递对象的方式来证线程安全。这个方式很实用，只是在依赖注
入或是重用与请求绑定的代码时，需要一个有效的 :term:`请求上下文<Request Context>` 。

.. _web-development-is-dangerous:

Web 开发危机四伏
----------------------------

快乐码 Web，安全记心间。

当你构建一个 Web 应用，你很可能会让用户在服务器上注册账号，并留存他们的数据。用户把数
据托付给了你。即便你是唯一可能在应用中产生数据的用户，你也依然会希望数据被妥善安全地
保存。

不幸的是，攻陷 Web 应用的手段五花八门。Flask 仅可保护你免受在现代 Web 应用中最常见的
一种安全问题的困扰：跨站脚本攻击（XSS）。除非你蓄意把不安全的 HTML 标记为安全，Flask
和底层的 Jinja2 模板引擎已在这个问题上做得足够好。但其他安全问题依然存在。


本文档会在 Web 开发的安全风险点上做出警示。某些安全问题的复杂程度远超出一般人的想象，
并且我们多会低估漏洞被利用的可能——直到一个精明的攻击者利用了我们的应用的漏洞。并且，
不要侥幸认为你的应用微不足道，没有攻击者问津。取决于攻击的形式，有时候会是自动化的僵尸
机器来检测如何在你的数据库中填充垃圾内容、恶意程序的链接或是类似的东西。


开发者在编写满足需求的代码时也要也要留心安全隐患。在这一点上，Flask 与其他框架并无
两样。
