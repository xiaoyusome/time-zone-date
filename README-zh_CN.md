# 世界各时区工具库
# World time zone tool library


[![NPM version](https://img.shields.io/npm/v/@time-zone/date.svg?style=flat-square)](https://www.npmjs.com/package/@time-zone/date)
[![](https://img.shields.io/badge/github-time--zone--date-%238B36DA?style=flat-square&logo=github)](https://github.com/Oumae-Kumiko/time-zone-date)
[![](https://img.shields.io/badge/github-issues-%2365A30D?style=flat-square&logo=github)](https://github.com/Oumae-Kumiko/time-zone-date/issues)
[![NPM version](https://img.shields.io/npm/dw/@time-zone/date.svg?style=flat-square)](https://www.npmjs.com/package/@time-zone/date)


[English](https://github.com/Oumae-Kumiko/time-zone-date/blob/main/README.md) | 简体中文

<br>

## 前言
* 让代码运行在不同国家环境下，都能准确获得指定国家的时间！  
<br>

## 安装
```bash
npm i @time-zone/date --save
```
<br>

## 用法
* 所有 API 引入方式都一样
```js
import {isUS_Dst,isUS_Wt} from '@time-zone/date'
isUS_Wt()
```
<br>

# 功能介绍
* 判断美国现在是否冬令时
* 判断美国现在是否夏令时

* 获取指定时区的时间  
   1. 完整时间
   2. 完整时间格式调整
   3. 年月日　|　日月年　|　月日年
   4. 年月日格式自定义：顺序、分隔符
   5. 时分秒
   6. 年
   7. 月
   8. 日
   9. 小时（24小时制）
   10. 分
   11. 秒
   12. 星期　　

<br>

> 额外提供，用上面的方法可以替代下面所有内容
* 获取EST时区时间  
   1. 完整时间
   2. 月日年
   3. 时分秒
   4. 年
   5. 月
   6. 日
   7. 小时（24小时制，可设置0为新一天起点或24为新一天起点）
   8. 分
   9. 秒
   10. 星期  
<br>

* 获取UTC时区时间：时差±0  
   1. 完整时间
   2. 年
   2. 月
   2. 日
   2. 时
   2. 分
   2. 秒

<br>  

# API

## getWorldTimeZone()  
> 如介绍的开头内容，这是主要 API ，`locales` 和 `options` 参数参考见文档末尾
- 获取指定时区的时间，第一个参数为返回的语言类型，第二个参数为目标时区
* 参数
* `locales`
  * 用途：`返回对应的语言类型`
  * 类型：`string`
  * 值：　`language[-scripts][-region]`
* `options`
  * 用途：`调整返回的时间格式内容，指定返回时区的时间`
  * 类型：`object`
  * 值：　`详情参数查看下方 options 内容`
```javascript
import { getWorldTimeZone } from '@time-zone/date'
// 获取目标时区完整时间
let date = getWorldTimeZone('zh-Hans',{timeZone:'Asia/Shanghai'})

// 不传则默认代码运行环境时的当前时区
// getWorldTimeZone()
```
<br>


## custom_yyyymmdd_sort()
获取指定时区的年月日，并且可自定义年月日的顺序（月日为个位数的情况下补充0）
* 参数3个
   * `timeZone`：类型 `string`
   * 年月日顺序：类型 `string` 
      * 1、必须为小写。2、字母为`y`、`m`、`d`。3、不传默认yyyymmdd
      * 3个字母的顺序决定返回的顺序
   * 分隔符，不传默认为`/`
```javascript
import { custom_yyyymmdd_sort } from '@time-zone/date'
let ymd = custom_yyyymmdd_sort('Asia/Shanghai','ymd','-')
let dmy = custom_yyyymmdd_sort('Asia/Shanghai','dmy','/')
let ydm = custom_yyyymmdd_sort('Asia/Shanghai','ydm','*-@#$$%^^*&(*&)(_+`~')
let mdy = custom_yyyymmdd_sort('Asia/Shanghai','mdy')

// 年月日可任意组合，并且如果出现重复的，返回结果也会重复出现
let ymdy = custom_yyyymmdd_sort('Asia/Shanghai','ymdy')
```
<br>


## get_mmddyyyy() 　 get_ddmmyyyy() 　 get_yyyymmdd（）
获取指定时区的月日年（月日为个位数的情况下补充0）
* 参数2个
   * `timeZone`：类型 `string`
   * 分隔符，不传默认为`/`
```javascript
import { get_mmddyyyy,get_ddmmyyyy,get_yyyymmdd } from '@time-zone/date'
let mdy = get_mmddyyyy('Asia/Shanghai')
// get_ddmmyyyy 和 get_yyyymmdd 不解释了，看名字就知道顺序了。

```
<br>


## custom_ymd_sort()
- 月日为个位数的情况下不会补充0
- 其他内容跟 `custom_yyyymmdd_sort()` 一致，不再解释
```javascript
import { custom_ymd_sort } from '@time-zone/date'
let ymd = custom_ymd_sort('Asia/Shanghai','ymd','-')
```
<br>


## get_hms()
- 获取目标时区的时分秒
* 参数
   * `timeZone`：类型 `string`
```javascript
import { get_hms } from '@time-zone/date'
let hms = get_hms('Asia/Shanghai')  // 格式：08:00:00
```
<br>

## getYear()
- 获取目标时区的年
* 参数
   * `timeZone`：类型 `string`
```javascript
import { getYear } from '@time-zone/date'
let year = getYear('Asia/Shanghai')  // 返回值 number 类型
```
<br>

## getMonth()
- 获取目标时区的月（0-11）
* 参数
   * `timeZone`：类型 `string`
```javascript
import { getMonth } from '@time-zone/date'
let month = getMonth('Asia/Shanghai')  // 返回值 number 类型
```
<br>

## getDate()
- 获取目标时区的日
* 参数
   * `timeZone`：类型 `string`
```javascript
import { getDate } from '@time-zone/date'
let date = getDate('Asia/Shanghai')  // 返回值 number 类型
```
<br>

## getHours()
- 获取目标时区的小时
- 单独获取目标时区的小时，统一返回值为：`0-23`，避免因美国1-24的问题造成混乱。
* 参数
   * `timeZone`：类型 `string`
```javascript
import { getHours } from '@time-zone/date'
let hours = getHours('Asia/Shanghai')  // 返回值 number 类型
```
<br>

## getMinutes()
- 获取目标时区的分钟
* 参数
   * `timeZone`：类型 `string`
```javascript
import { getMinutes } from '@time-zone/date'
let minutes = getMinutes('Asia/Shanghai')  // 返回值 number 类型
```
<br>

## getSeconds()
- 获取目标时区的秒
* 参数
   * `timeZone`：类型 `string`
```javascript
import { getSeconds } from '@time-zone/date'
let sec = getSeconds('Asia/Shanghai')  // 返回值 number 类型
```
<br>

## getDay()
- 获取目标时区的星期
- 返回值为 `0-6` ，0为星期天，1为星期一，后面依次排序
* 参数
   * `timeZone`：类型 `string`
```javascript
import { getDay } from '@time-zone/date'
let day = getDay('Asia/Shanghai')  // 返回值 number 类型
```
<br>


## getESTDate()  
获取EST时区的时间，返回的语言类型en-US
* 无参数
```javascript
import { getESTDate } from '@time-zone/date'
let date = getESTDate()
```
<br>


## getUTCDate()  
获取UTC时区时间
* 无参数
```javascript
import { getUTCDate } from '@time-zone/date'
let date = getUTCDate()
```
<br>


## isUS_Dst()  
判断美国现在是否夏令时
* 无参数，返回 `true` 表示美国当前是夏令时
* 返回值 `true` | `false`
```javascript
import { isUS_Dst } from '@time-zone/date'
let booleanDate = isUS_Dst()
```
<br>


## isUS_Wt()  
判断美国现在是否冬令时
* 无参数，返回 `true` 表示美国当前是冬令时
* 返回值 `true` | `false`
```javascript
import { isUS_Wt } from '@time-zone/date'
let booleanDate = isUS_Wt()
```
<br>


# `locales` 参数  
* 类型：`string`
* language[-scripts][-region]  
- 特殊编码可传入对应的编码类型替换，具体参考MDN网站
   * language[-scripts][-region]-u-nu-*  
   * language[-scripts][-region]-u-ca-*  

<br>

- 参考值
- 其他值请参考：http://www.lingoes.cn/zh/translator/langcode.htm
```javascript
"zh-Hans" //简体中文
"zh-TW" //繁体中文
"ru-RU" //俄语
"en-GB" //英国
"it-IT" //意大利
"fr-FR" //法语
"pt-PT" //葡萄牙
"de-DE" //德语
"en-US" //美国
"en-AU" //澳大利亚
"en-CA" //加拿大
"ko-KR" //韩国
"ar-EG" //阿拉伯
"ja-JP" //日本
"nl-NL" //荷兰
"es-ES" //西班牙
"hi-IN" //印地语
"eo" //世界语  
```

<br>

# `options` 参数  
* 类型：`object`

* 内置默认参数为
```javascript
const DEFAULT_OPTIONS = {
  year: "numeric",
  month: "numeric",
  day: "numeric",
  hour: "numeric",
  minute: "numeric",
  second: "numeric",
  weekday: "short",
  hour12:false, 
  timeZoneName :"short",
}
```

### 可配置参数，如跟默认参数有相同的属性，则会以传入的参数为主
```javascript
let options = {
  era: "long",  //是否展示公元："narrow", "short", "long"  依次为极短、短、长(完整)
  year: "numeric",  //"numeric"  正常数值表示， "2-digit"  显示两位数
  month: "numeric", //"numeric", "2-digit", "narrow", "short", "long"   
  day: "numeric",   //"numeric", "2-digit"
  hour: "numeric",  //"numeric", "2-digit"
  minute: "numeric",//"numeric", "2-digit"
  second: "numeric",//"numeric", "2-digit"
  weekday: "long",  //"narrow", "short", "long"
  hour12:false,     // true | false
  timeZoneName :"short",  //"short", "long"
  timeZone:"", // 指定城市的时区
}
```

## `options.timeZone` 的参考值：
```javascript
timeZone:'UTC' // UTC 时间
timeZone:'Europe/Berlin' // GMT+1 德国时区
timeZone:'Australia/Sydney' // GMT+11 澳大利亚时区
timeZone:'Europe/Moscow' // GMT+3 俄罗斯时区
timeZone:'Europe/Paris' // GMT+1 法国时区
timeZone:'Europe/London' // GMT 英国时区
timeZone:'Asia/Tokyo' // JST 东京时区
timeZone:'Asia/Shanghai' // GMT+8 北京时区
timeZone:'America/Denver' // MST 美国山地时区
timeZone:'America/Los_Angeles' // PTZ 太平洋时区
timeZone:'America/New_York' // EST 美国东部时区
timeZone:'America/Chicago' // CST 美国中部时区
```

<br>

# 其他 
## EST时间的对应值
* 都不需要传参数
```javascript
import { getESTmmddyyyy, ...... } from '@time-zone/date'
getESTmmddyyyy()  // 月日年
getESThms()  // 时分秒
EST_getYear()  // 年
EST_getMonth()  // 月
EST_getDate()  // 日
EST_getHours(0)  // 美国小时，如果传0表示新的一天起点为0，否则为24
EST_getMinutes()  // 分
EST_getSeconds()  // 秒
EST_getDay()  // 星期
```