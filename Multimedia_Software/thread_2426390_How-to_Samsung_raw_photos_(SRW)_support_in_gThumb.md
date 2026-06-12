---
title: "How-to: Samsung raw photos (SRW) support in gThumb"
date: 2019-09-08
forum: Multimedia Software
---

### Post by 0x656b694d on 2019-09-08
Hello,

I was looking for an alternative to Shotwell workflow to import photos from an SD card and found that gThumb doesn't support the Samsung raw photos SRW files.

So I created a mime type package file (/usr/share/mime/packages/samsung-raw.xml):
[HTML]
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="image/x-samsung-srw">
    <comment>Samsung raw image</comment>
    <comment xml:lang="bg">&#1048;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1077; &#8212; Samsung SRW</comment>
    <comment xml:lang="ca">imatge «SRW» de Samsung</comment>
    <comment xml:lang="cs">surový obrázek Samsung SRW</comment>
    <comment xml:lang="da">Samsung-srw-billede (raw)</comment>
    <comment xml:lang="de">Samsung SRW-Bild</comment>
    <comment xml:lang="el">&#913;&#957;&#949;&#960;&#949;&#958;&#941;&#961;&#947;&#945;&#963;&#964;&#951; &#949;&#953;&#954;&#972;&#957;&#945; Samsung (SRW)</comment>
    <comment xml:lang="en_GB">Samsung SRW image</comment>
    <comment xml:lang="es">imagen en bruto SRW de Samsung</comment>
    <comment xml:lang="eu">Samsung SRW irudia</comment>
    <comment xml:lang="fi">Samsung SRW -kuva</comment>
    <comment xml:lang="fr">image SRW Samsung</comment>
    <comment xml:lang="ga">íomhá SRW Samsung</comment>
    <comment xml:lang="gl">imaxe en bruto SRW de Samsung</comment>
    <comment xml:lang="he">&#1514;&#1502;&#1493;&#1504;&#1514; SRW &#1513;&#1500; Samsung</comment>
    <comment xml:lang="hr">Samsung SRW image</comment>
    <comment xml:lang="hu">Samsung SRW kép</comment>
    <comment xml:lang="ia">Imagine SRW Samsung</comment>
    <comment xml:lang="id">Image Samsung SRW</comment>
    <comment xml:lang="it">Immagine SRW Samsung</comment>
    <comment xml:lang="ja">Samsung SRW &#30011;&#20687;</comment>
    <comment xml:lang="kk">Samsung SRW &#1089;&#1091;&#1088;&#1077;&#1090;&#1110;</comment>
    <comment xml:lang="ko">&#54028;&#45208;&#49548;&#45769; RAW2 &#49324;&#51652;</comment>
    <comment xml:lang="lv">Samsung SRW j&#275;latt&#275;ls</comment>
    <comment xml:lang="nl">Samsung SRW image</comment>
    <comment xml:lang="oc">imatge SRW Samsung</comment>
    <comment xml:lang="pl">Obraz SRW Samsung</comment>
    <comment xml:lang="pt">imagem em bruto Samsung</comment>
    <comment xml:lang="pt_BR">Imagem SRW da Samsung</comment>
    <comment xml:lang="ru">&#1053;&#1077;&#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1085;&#1085;&#1086;&#1077; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1077; Samsung SRW</comment>
    <comment xml:lang="sk">Surový obrázok Samsung SRW</comment>
    <comment xml:lang="sl">Slikovna datoteka Samsung SRW</comment>
    <comment xml:lang="sr">&#1055;&#1072;&#1085;&#1072;&#1089;&#1086;&#1085;&#1080;&#1082; &#1089;&#1080;&#1088;&#1086;&#1074;&#1072;2 &#1089;&#1083;&#1080;&#1082;&#1072;</comment>
    <comment xml:lang="sv">Samsung SRW-bild</comment>
    <comment xml:lang="tr">Samsung SRW görüntüsü</comment>
    <comment xml:lang="uk">&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1085;&#1103; &#1092;&#1086;&#1088;&#1084;&#1072;&#1090;&#1091; SRW Samsung</comment>
    <comment xml:lang="zh_CN">&#26494;&#19979; SRW &#22270;&#20687;</comment>
    <comment xml:lang="zh_TW">Samsung SRW &#24433;&#20687;</comment>
    <sub-class-of type="image/x-dcraw"/>
    <magic priority="50">
      <match value="MM\x00\x2A\x00\x00" type="string" offset="0"/>
    </magic>
    <glob pattern="*.SRW"/>
    <glob pattern="*.srw"/>
    <alias type="image/x-samsung-srw"/>
  </mime-type>
</mime-info>[/HTML]

... and updated the mime database with [FONT=Courier New]sudo update-mime-database /usr/share/mime[/FONT]

Now Nautilus can distinguish the SRW files from tiff and so I could assign Geeqie as the viewer application for SRW, and gThumb understands it as a raw image format and is even able to display it.

---

### Post by Autodave on 2019-09-08
You know, I have absolutely no idea what you are talking about, but I am sure that there are people out there that will love seeing this someday!  Thanks for sharing!

---

