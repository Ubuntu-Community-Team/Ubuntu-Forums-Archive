---
title: "translate srt subtitle fairly easily with Gtranslate and ubuntu"
date: 2023-11-14
forum: Multimedia Software
---

### Post by shantiq on 2023-11-14
&#10122;   change file extension srt to txt file
&#10123;   run >> ```
libreoffice --convert-to "pdf" SRT.txt
```     in Terminal (very quick)
&#10124;   run through GoogleTranslate   >> pick document etc
&#10125;   copy paste into text editor save as ENG.srt ;  make sure numbers at start of lines are separate from times;   often the first few lines are not ... the rest are


ex:


1 
00:00:19,000 --> 00:00:21,680
THE LITTLE BOOK OF JAM
2 
00:00:21,760 --> 00:00:25,080
RAMEN
JAPANESE NOODLE SOUP FOR EVERY DAY


and NOT 


1 00:00:19,000 --> 00:00:21,680
THE LITTLE BOOK OF JAM
2 00:00:21,760 --> 00:00:25,080
RAMEN
JAPANESE NOODLE SOUP FOR EVERY DAY

---

### Post by TheFu on 2023-11-15
Or use **apertium**. No need for selling yourself and data to google or wasting time with PDF.

# To convert from Spanish to English ... 
```
$ apertium es-en "$1" > "$1.en.srt"
```

This is a literal translation, not an expert translation where the meaning is provided. I prefer literal translation when I'm learning a language.
Of course, you can have both and add multiple caption files to the same MKV container, if you'd like both. Then pick which one you'd like displayed for playback.

---

### Post by shantiq on 2023-11-15
good tip   will check

EDIT
OK no idea how to use this the man and the --help do not

Say i have a document called 4.srt and want that to go from ENG to SPA what is the syntax?


OK loox like it is good [from here]("https://www.apertium.org/index.eng.html#docTranslation?dir=eng-spa") but only goes to SPA and other Iberian languages from ENG; does so effectively but not so useful to me as SPA I can follow :KS  but would be cool if ALL languages were there ....    maybe I have not got the info right

---

### Post by TheFu on 2023-11-15
Sorry, I pulled the line from a script that gets passed in a filename, so $1 is the filename passed in.

```
$ apertium en-es "4.en.srt" > "4.es.srt"
```

Manpage:
```
SYNOPSIS
     apertium [-au] [-d datadir] [-f format] language-pair [infile [outfile]]
```

So, I'm using the style of 
```
$ apertium language-pair [infile]
```
The output is sent to stdout, which I redirect.  Looks like I could use 
```
$ apertium en-es "4.en.srt"  "4.es.srt"
```
too. I just prefer the flexibility of shell pipelining input/output. So much more flexible.

apertium has lots of language packs, but since I only need en-spa or spa-en, I haven't looked at any others.  I don't think Japanese, Korean or Mandarin are supported.  Perhaps just the languages based on Latin1 characters?  IDK.

```
$ apertium -l
  eng-spa
  spa-eng
  spa-eng_US

``` shows the packs I have loaded.  Because I run the translations on a few different computers, they are likely to have different versions of apertium. At some point en --> eng or the other way. I don't recall. Same for es <--> spa. I don't know when, but the error happened and was trivial to fix.

Available language pairs: [https://svn.code.sf.net/p/apertium/svn/builds/language-pairs](https://svn.code.sf.net/p/apertium/svn/builds/language-pairs)  Looks like over 25 pairs, but many are for regional languages that I've never heard about. I'm fairly ignorant on SE European languages.  I thought Tatar was a spice, not a language.

---

### Post by shantiq on 2023-11-15
thank you so much for explanations Fu very grateful


[Languages Packs ]("https://wiki.apertium.org/wiki/Install_language_data_using_packaging")    then 

run ```
sudo apt install apertium
```   then ```
apt-cache search apertium
```   then you see all the language pairs

for example then ```
sudo apt-get install apertium-por-cat apertium-eng-cat apertium-en-es apertium-pt-gl
```

ao now i have those pairs

```
shan@shan-Aspire-XC-780:~/Desktop/trial$ apertium -l  cat-eng
  cat-eng_US
  cat-por_BR
  cat-por
  cat-por_PTpre1990
  en-es
  eng-cat_iec2017
  eng-cat
  eng-cat_valencia_iec2017
  eng-cat_valencia
  eng-cat_valencia_uni_iec2017
  eng-cat_valencia_uni
  es-en
  es-en_US
  gl-pt
  por-cat
  pt-gl



```

then time to play will report later EDIT tested and really fast

was trying to turn a GER sub to a Thai movie into a language i read better than GER like SPA or PT but this does not do that but it does many other useful translations; definitely cooler than using GooTranslate and I suppose more pairs will appear with time and folks adding EXCELLENT tool :)

---

### Post by TheFu on 2023-11-16
There seems to be a German<-->English translation [https://github.com/apertium/apertium-eng-deu](https://github.com/apertium/apertium-eng-deu)
Thai will be difficult.  Commercial translation will likely be needed. Google **is** commercial, make no mistake.

---

### Post by shantiq on 2023-11-18
thanx Fu will add GER   i did not need Thai;    the sub i found was in GER and i wanted to make it SPA or POR so to find it easier;   I find using subs a great way to passively learn more language   really cool tool and yes Goo   is commercial AND surveillance data gatherer so you got me out of the hands of Babylon here :) and grateful Muy Agradecido as they say in Bognor Regis ...


EDIT   hmmmm   not sure it is ready this [GER]("https://wiki.apertium.org/wiki/Apertium-eng-deu")   it says nursery and I have failed to install it thus far mired in [compiling]("https://wiki.apertium.org/wiki/Installation_troubleshooting") and it is absent [here too]("https://www.apertium.org/index.eng.html#?dir=por-spa&q=")  probably ineptitude in installing on my side but certainly not plain sailing ...

---

### Post by TheFu on 2023-11-18
I happen to have studied German for 3 yrs, so today I can ask for a bier and toilet, but not much else.  OTOH, I can read German subtitles and get about 40%-80% based on context. Of course, I miss all the jokes.

I did 3 weeks of intensive Spanish training a few years ago. It has been much more helpful, since lots of the construction workers where I live are from Central America and haven't learned much English. We used google translate on our phones to communicate as they worked on fixing some water damage over many, many, months.  Far too many. 

Später.

---

