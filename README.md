laravel-admin select-tree
======

[select-tree](https://github.com/zhpefe/select-tree) 是针对laravel-admin 数据模型树 的 select 联动选择插件, 可集成至表单中，或用于筛选。

### 安装

`composer require zhpefe/select-tree`

### 使用

```
$filter->select_tree(column, {label})->ajax(URL)->topId(1);

$form->select_tree(column, {label})->ajax(URL)->topId(1);
```

* 需要用ajax方法指定AJAX的地址，select的change触发后会GET此地址，并把当前选项的值通过参数q传递，
返回的数据结构为：

```$xslt
{
    "own": {
        "id": 2,
        "parent_id": 1,
        "title": "xxx"        
    },
    "siblings": [
        {
            "id": 2,
            "parent_id": 1,
            "title": "xxx"
        },
        ...
    ],
    "children": [
        {
            "id": 8,
            "parent_id": 2,
            "title": "xxx",
        },
        ...
    ]
}
```
其中 own 代表自身， siblings表示同级， children 为子类。

* topId() 方法为指定顶级ID，默认为0；

