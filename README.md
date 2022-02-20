## 正方教务系统选课接口分析

本文档主要针对方**正方教务系统**  进行的 关于**选课**的接口分析，仅供开发交流参考，勿用于个人盈利

🎈文档持续完善中，有错误的地方欢迎指正！

### 接口列表

- [**查询已选课程**](#yxkc)
- [**搜索课程**](#sskc)
- **显示课程具体信息**
- **选课**
- **退课**
----------------------------------------------------------------------------------------------------------
### <span id="yxkc">查询已选课程接口</span>

**请求方式**：`POST`

**请求接口**：

```
https://jwgl.XXXX.edu.cn/xsxk/zzxkyzb_cxZzxkYzbChoosedDisplay.html?gnmkdm=N253512&su=学号
```

**请求头**:

`Cookie:JSESSIONID=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`

**请求参数**：

| 变量名    | 值                               | 注释                           | 是否必须 |
| --------- | -------------------------------- | ------------------------------ | -------- |
| `xkxnm`   | 2021                             | 当前学期年份如2021-2022 即2021 | ✓        |
| `xkxqm`   | 12                               | 定值(可能)                     | ✓        |
| `jg_id`   | 14                               | 学院代号                       |          |
| `zyh_id`  | 1401                             | 专业代号                       |          |
| `njdm_id` | 2019                             | 年级代码                       |          |
| `zyfx_id` | wfx                              |                                |          |
| `bh_id`   | XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 个人编号(每个人唯一)           |          |
| `xz`      | 4                                | 学制                           |          |
| `ccdm`    | 3                                |                                |          |
| `xkly`    | 1                                |                                |          |

**返回数据** 

接口返回已选的全部课程的具体信息数据

数据示例如下(参数太多了，就不做注释了，自行领悟)
```json
[{
    "bdzcbj": "2",
    "cxbj": "0",
    "date": "二○二二年二月十九日",
    "dateDigit": "2022年2月19日",
    "dateDigitSeparator": "2022-2-19",
    "day": "19",
    "do_jxb_id": "7b28379a47c35351189829b63e24a0c85ca144aee830e2071385dfdf682b60ea1364f18eb4fe03f3f8f3831c1b7813e22b36d985d6553eb03c9187bab46a808cfeedaaf5d9384a726267a39ddcd382504d63df2fdac1414e6b8e8801a2f39db65986c67224e838a1131c6d0f0157cc834d0bd1c58b9379cd2742c64ff7b86ca4",
    "isInxksj": "1",
    "jgpxzd": "1",
    "jsxx": "0333/XXX/教授",
    "jxb_id": "CEB1CEB1CEB1CEB1CEB1CEB1CEB1CEB1",
    "jxbmc": "高等数学A-2-0008",
    "jxbrs": "122",
    "jxbzls": "1",
    "jxdd": "仁智楼600(多)<br/>仁智楼600(多)<br/>仁智楼600(多)",
    "kch": "MTH110024",
    "kch_id": "180C180C180C180C180C180C180C180C",
    "kcmc": "高等数学A-2",
    "kklxdm": "01",
    "kklxmc": "主修课程",
    "kklxpx": "5",
    "krrl": "15",
    "listnav": "false",
    "localeKey": "zh_CN",
    "month": "2",
    "pageable": true,
    "queryModel": {
      "currentPage": 1,
      "currentResult": 0,
      "entityOrField": false,
      "limit": 15,
      "offset": 0,
      "pageNo": 0,
      "pageSize": 15,
      "showCount": 10,
      "sorts": [],
      "totalCount": 0,
      "totalPage": 0,
      "totalResult": 0
    },
    "qz": "0",
    "rangeable": true,
    "rlkz": "0",
    "rlzlkz": "1",
    "rwlx": "1",
    "sfktk": "1",
    "sfxkbj": "1",
    "sksj": "星期一第3-4节{1-18周}<br/>星期三第3-4节{1-18周}<br/>星期五第3-4节{11-18周}",
    "sxbj": "1",
    "t_kch_id": "180C180C180C180C180C180C180C180C",
    "tktjrs": "0",
    "totalResult": "0",
    "userModel": {
      "monitor": false,
      "roleCount": 0,
      "roleKeys": "",
      "roleValues": "",
      "status": 0,
      "usable": false
    },
    "xf": "4.0",
    "xkgz": "1~0~0~1~D7C9FFFC526E5E7BE0530264A8C0523A~1~0",
    "xkkz_id": "D7C9FFFC526E5E7BE0530264A8C0523A",
    "xxkbj": "0",
    "year": "2022",
    "yxzrs": "122",
    "zckz": "1",
    "zixf": "0",
    "zntgpk": "0",
    "zy": "1"
  },......]
```
----------------------------------------------------------------------------------------------------------
### <span id="sskc">搜索课程接口</span>

**请求方式**：`POST`

**请求接口**：

```
https://jwgl.XXXX.edu.cn/xsxk/zzxkyzb_cxZzxkYzbPartDisplay.html?gnmkdm=N253512&su=学号
```

**请求头**:

`Cookie:JSESSIONID=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`

**请求参数**

| 变量名         | 值                               | 注释                           | 是否必须            |
| -------------- | -------------------------------- | ------------------------------ | ------------------- |
| `rwlx`         | 1                                | 未知                           | 主修课：✓ 选修课：✗ |
| `xkly`         | 1                                | 未知                           | 主修课：✓ 选修课：✗ |
| `zyh_id`       | 1401                             | 专业代号                       | 主修课：✓ 选修课：✗ |
| `njdm_id`      | 2021                             | 年级代码                       | 主修课：✓ 选修课：✗ |
| `bh_id`        | XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 个人编号(每个人唯一)           | 主修课：✓ 选修课：✗ |
| `xkxnm`        | 2021                             | 当前学期年份如2021-2022 即2021 | ✓                   |
| `xkxqm`        | 12                               | 定值                           | ✓                   |
| `kklxdm`       | 01                               | `01`为主修课 `10`为选修课      | ✓                   |
| `kspage`       | 1                                | 页号                           | ✓                   |
| `jspage`       | 10                               | 一页显示的数量                 | ✓                   |
| `bklx_id`      | 0                                |                                |                     |
| `sfkkjyxdxnxq` | 0                                |                                |                     |
| `xqh_id`       | 1                                |                                |                     |
| `jg_id`        | 14                               | 学院代号                       |                     |
| `njdm_id_1`    | 2019                             |                                |                     |
| `zyh_id_1`     | 1401                             |                                |                     |
| `zyfx_id`      | wfx                              |                                |                     |
| `xbm`          | 1                                |                                |                     |
| `xslbdm`       | 421                              |                                |                     |
| `ccdm`         | 3                                |                                |                     |
| `xsbj`         | 4294967296                       |                                |                     |
| `sfkknj`       | 0                                |                                |                     |
| `sfkkzy`       | 0                                |                                |                     |
| `kzybkxy`      | 0                                |                                |                     |
| `sfznkx`       | 0                                |                                |                     |
| `zdkxms`       | 0                                |                                |                     |
| `sfkxq`        | 0                                |                                |                     |
| `sfkcfx`       | 0                                |                                |                     |
| `kkbk`         | 0                                |                                |                     |
| `kkbkdj`       | 0                                |                                |                     |
| `sfkgbcx`      | 0                                |                                |                     |
| `sfrxtgkcxd`   | 0                                |                                |                     |
| `tykczgxdcs`   | 0                                |                                |                     |
| `rlkz`         | 0                                |                                |                     |
| `xkzgbj`       | 0                                |                                |                     |
| `jxbzb`        |                                  |                                |                     |

下列参数为与搜索筛选相关的参数，单独列出
| 变量名            | 值   | 注释         | 是否必须 |
| ----------------- | ---- | ------------ | -------- |
| `filter_list[0]`  | XXX  | 搜索内容     |          |
| `njdm_id_list[0]` | 2022 | 筛选年级     |          |
| `jg_id_list[0]`   | 45   | 筛选学院     |          |
| `zyh_id_list[0]`  | 1906 | 筛选专业     |          |
| `kkbm_id_list[0]` | 115  | 筛选开课学院 |          |
| `kclb_id_list[0]` | 5    | 筛选课程类别 |          |
| `kcxzdm_list[0]`  | 2    | 筛选课程性质 |          |
| `kcgs_list[0]`    | 12   | 筛选课程归属 |          |
| `jxms_list[0]`    | 2    | 筛选教学模式 |          |
| `sksj_list[0]`    | 3    | 筛选上课星期 |          |
| `skjc_list[0]`    | 6    | 筛选上课节次 |          |
| `jxbmc_list[0]`   |      | 教学班名称   |          |
| `cxbj_list[0]`    | 0    | 是否重修     |          |
| `yl_list[0]`      | 1    | 有无余量     |          |

**返回数据** 

接口返回搜索课程的基本信息数据

数据示例如下(参数太多了，就不做注释了，自行领悟)

```
{
  "tmpList": [
    {
      "blyxrs": "0",
      "blzyl": "0",
      "cxbj": "0",
      "date": "二○二二年二月十九日",
      "dateDigit": "2022年2月19日",
      "dateDigitSeparator": "2022-2-19",
      "day": "19",
      "fxbj": "0",
      "jgpxzd": "1",
      "jxb_id": "CEB1CEB1CEB1CEB1CEB1CEB1CEB1CEB1",
      "jxbmc": "高等数学A-2-0008",
      "jxbzls": "1",
      "kch": "MTH110024",
      "kch_id": "180C180C180C180C180C180C180C180C",
      "kcmc": "高等数学A-2",
      "kcrow": "1",
      "kklxdm": "01",
      "kzmc": "自然类,重修课",
      "listnav": "false",
      "localeKey": "zh_CN",
      "month": "2",
      "pageable": true,
      "queryModel": {
        "currentPage": 1,
        "currentResult": 0,
        "entityOrField": false,
        "limit": 15,
        "offset": 0,
        "pageNo": 0,
        "pageSize": 15,
        "showCount": 10,
        "sorts": [],
        "totalCount": 0,
        "totalPage": 0,
        "totalResult": 0
      },
      "rangeable": true,
      "totalResult": "0",
      "userModel": {
        "monitor": false,
        "roleCount": 0,
        "roleKeys": "",
        "roleValues": "",
        "status": 0,
        "usable": false
      },
      "xf": "4.0",
      "xxkbj": "0",
      "year": "2022",
      "yxzrs": "122"
    },
  ],......
  "sfxsjc": "0"
}
```
