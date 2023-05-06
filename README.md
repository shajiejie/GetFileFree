# GetFileFree

此代码用于获取一些不可复制网站文本的获取，脚本可以将获得的内容写入指定文件中（word），目前可以设置字体以及大小，如有特殊要求，可按简介更改

## Preliminary

Python 3.8 + pip 

## Step

第一步：搭建python3+pip环境，可使用anaconda、pycharm等集成环境，或纯python环境 （Windows下的环境搭建流程可参考 [Windows搭建python3开发环境&卸载](https://www.jianshu.com/p/2f1acc6ff2c6))

第二步：依赖安装，`pip install lxml `

​                                `pip install BeautifulSoup4`

​                                用法`from bs4 import BeautifulSoup`

|    **解析器**    | **用法**                                                     | **优点**                                                  | **缺点**                                         |
| :--------------: | ------------------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------ |
|   python标准库   | BeautifulSoup(markup,‘html.parser’)                          | python标准库，执行速度适中                                | (在python2.7.3或3.2.2之前的版本中)文档容错能力差 |
| lxml的HTML解析器 | BeautifulSoup(markup,‘lxml’)                                 | 速度快，文档容错能力强                                    | 需要安装c语言库                                  |
| lxml的XML解析器  | BeautifulSoup(markup,‘lxml-xml’)或者BeautifulSoup(markup,‘xml’) | 速度快，唯一支持XML的解析器                               | 需要安装c语言库                                  |
|     html5lib     | BeautifulSoup(markup,‘html5lib’)                             | 最好的容错性，以浏览器的方式解析文档，生成HTML5格式的文档 | 速度慢，不依赖外部扩展                           |

### 分析介绍

`con = requests.get(url)`:向url发送一个GET请求，并将响应存储在con变量中。

`con.encoding = 'utf-8`' :设置响应的字符编码为utf-8。

`text = con.text`:获取响应的文本内容。

`result = BeautifulSoup(texts， 'lxml')`:使用lxml解析器解析文本内容并创建一个BeautifulSoup对象。

`div1 = result.find('div', attrs={'class': 'con_article con_main'})`:查找class属性等于'con_article con_main'的div元素，并将其存储在div1变量中。

`div_zj_list = div1.find_all('p')`:查找div1元素下的所有p元素并将它们存储在div_zj_list变量中。

`doc = docx. document()`:使用docx模块的document()函数创建一个新的Word文档对象。

`font = doc.styles['Normal'].font`:获取文档Normal样式的字体对象。

`font.name = '中文字体'`:设置字体名称为中文字体。

`for div_zj in div_zj_list:`:循环遍历div_zj_list变量。

`para.style.font.size = docx.shared.Pt(10)`:设置段落样式的字体大小为10点。

`heading.style.font.size = docx.shared.Pt(16)`:设置标题样式的字体大小为16点。

`file_path = '/Users/example/Desktop/ .docx`':将Word文档的文件路径分配给file_path变量。

