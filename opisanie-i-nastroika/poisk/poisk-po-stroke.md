---
description: Релиз 2.4.8.0
---

# Поиск по строке

При работе с поиском по строке используется контрол [Поиск. Условия поиска](../../tekhnicheskaya-dokumentaciya/opisanie-kontrolov/1.-poisk-katalog-tovary/poisk.-usloviya-poiska.md).

![&#x41A;&#x43E;&#x43D;&#x442;&#x440;&#x43E;&#x43B; &#x41F;&#x43E;&#x438;&#x441;&#x43A;. &#x423;&#x441;&#x43B;&#x43E;&#x432;&#x438;&#x44F; &#x43F;&#x43E;&#x438;&#x441;&#x43A;&#x430; &#x43F;&#x440;&#x438; &#x434;&#x43E;&#x431;&#x430;&#x432;&#x43B;&#x435;&#x43D;&#x438;&#x438; &#x43D;&#x430; &#x441;&#x442;&#x440;&#x430;&#x43D;&#x438;&#x446;&#x443;](../../.gitbook/assets/image%20%2810%29.png)

Поиск может работать как по выбранному варианту \(артикул, начало артикула, наименование, VIN-номер\), так и в режиме автоопределения нужного варианта поиска.

### Автоопределение

Автоопределение варианта поиска будет срабатывать во всех случаях, когда тип поиска \(search\_searchtype\) не задан.

{% hint style="info" %}
Если тип поиска не задан, то контрол пытается определить наиболее подходящий тип поиска на основании RegExp выражений. Возможны ошибки в определении типа поиска.

Например, если очищенный артикул будет состоять из 17 символов, включающих цифры и буквы латинского алфавита, то автоопределение сработает для поиска по VIN-номеру.
{% endhint %}

### По артикулу

Тип поиска \(search\_searchtype\) = 1.

Происходит поиск по очищенному от лишних символов поисковому запросу \(точное совпадение с очищенным артикулом\). В случае, если по очищенному артикулу больше 1 предложения по брендам, будет переход на страницу "Уточнения артикула и бренда". Если только 1 бренд, то будет переход на страницу "Цены и наличие".

### По началу артикула

Тип поиска \(search\_searchtype\) = 2.

Работает аналогично поиску по артикулу с тем лишь отличием, что идет поиск не по точному совпадению, а по вхождению поискового запроса в начало артикула.

### По наименованию

Тип поиска \(search\_searchtype\) = 3.

Полнотекстовый поиск средствами MS SQL с использованием морфологического поиска Full-Text Search.

Флаг "Отключить режим отображения уточнений при поиске по тексту" позволяет переходить или к уточнениям \(значение флага "Нет"\), или сразу к предложениям \(значение флага "Да"\).

### По VIN для Laximo

Тип поиска \(search\_searchtype\) = 4.

При вводе VIN-номера будет переход на заданную страницу "Поиск по VIN / Frame".
