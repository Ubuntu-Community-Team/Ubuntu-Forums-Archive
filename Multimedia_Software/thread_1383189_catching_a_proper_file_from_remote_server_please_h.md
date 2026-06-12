---
title: "catching a proper file from remote server please help.."
date: 2010-01-16
forum: Multimedia Software
---

### Post by abhicool1 on 2010-01-16
I am having a problem to read file from remote url.
at this stage I have successfully grabbed a video from YouTube and link which is generated is.
$link =
```
[COLOR=#000000][COLOR=#0000bb]http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#ff8000]//v14.lscache2.c.youtube.com/videoplayback?ip=0.0.0.0&sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Calgorithm%2Cburst%2Cfactor&fexp=901421%2C900033%2C903105&algorithm=throttle-factor&itag=5&ipbits=0&burst=40&sver=3&expire=1263679200&key=yt1&signature=76BE713D53D80C026AB6BDB2B83C82FF545B56B8.8626535B14E415A063E18531C0DEFFE78D4E2678&factor=1.25&id=30b46ae0eadc46df[/COLOR][/COLOR]
```now my problem is i want to save this file to localhost. 
I have tried using 
$file1 = file("$link?$QUERY_STRING");
$file1 = @implode("", $file1);
// echo "$file1";
 echo "$file1";  gives raw data of file

```
[COLOR=#000000][COLOR=#0000bb]FLV  [/COLOR][COLOR=#007700]&[/COLOR][COLOR=#ff8000]#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533; &#65533; 8&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533; onMetaData &#65533;&#65533;&#65533; 
[/COLOR][COLOR=#007700]&[/COLOR][COLOR=#ff8000]#65533; duration&#65533;@Aó33333&#65533; starttime&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; totalduration&#65533;@Aó33333&#65533; width&#65533;@y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; height&#65533;@l@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; videodatarate&#65533;@r ¬ë ®Ó&#65533; audiodatarate&#65533;@M”}¹óÓ–&#65533; totaldatarate&#65533;@vB˜'’.Ž&#65533; framerate&#65533;@>&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; bytelength&#65533;A8h®&#65533;&#65533;&#65533;&#65533;&#65533; canseekontime  &#65533; sourcedata &#65533; B4A7D0108HH&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;.......... [/COLOR][/COLOR]
```Now, I want to save it on my local drive so that i can convert it by using FFMPEG

Please help me.

I tried.. 
```
[COLOR=#000000][COLOR=#0000bb]$fh [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]fopen[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"testvideo.flv"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"w"[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000bb]fwrite[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$fh[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]$file1[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000bb]fclose[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$fh[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
```but unable to write data into file. File remains blank after execuation of code.

Please help me. :(

---

