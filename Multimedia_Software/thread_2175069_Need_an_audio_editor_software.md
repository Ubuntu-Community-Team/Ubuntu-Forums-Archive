---
title: "Need an audio editor software"
date: 2013-09-17
forum: Multimedia Software
---

### Post by lovevn on 2013-09-17
Hi everyone.
I have some mp3 files very short, only about 4-7 seconds for one. So now I want to join all them into a bigger file. But, the most important thing I need is it can [COLOR=#333333][FONT=Verdana]allow me to insert silence between the audio MP3 tracks to be merged[/FONT][/COLOR]. For example, after no1 file finishes, no2 file doesn't immediately play, I need 2-3 seconds pause between them.
Do you know some audio software can do it? please tell me. Thanks! :confused:

---

### Post by slickymaster on 2013-09-17
What about [Audacity]("http://audacity.sourceforge.net/")?

---

### Post by tgalati4 on 2013-09-17
Sox is the Swiss Army Knife of audio tools.

Open a terminal:  

```
sudo apt-get install sox
man sox
```

Audacity is good for doing it manually.  But if you have a lot of files to do, then you will want to write a batch file (a script) to do it automatically using sox.

---

### Post by Yellow Pasque on 2013-09-17
Take a look at mp3wrap program.
You could also approach it differently: [http://stackoverflow.com/a/1479701](http://stackoverflow.com/a/1479701)

---

### Post by shantiq on 2013-09-18
now you do not say how many you have but say it it only 10 or 20   THIS IS EASY [even if not used to command line]



1.    create a three-second silent file

```
[COLOR=#000000]*sudo apt-get install sox libsox-fmt-all*[/COLOR]

```to install sox if not installed

then run

```
*sox -n -r 44100 -c 2 -C 320 silence.mp3 trim 0.0 3.0*
```    and it will be found in your home folder


[B]finally to splice

[/B]rename your files and put silence.mp3 in same folder   and run


```
sox  -C 320  1.mp3 *silence.mp3 * 2.mp3 *silence.mp3 *3.mp3 *silence.mp3 *4.mp3 *silence.mp3 *5.mp3   \
*silence.mp3 *6.mp3 *silence.mp3 *7.mp3 *silence.mp3 *8.mp3 *silence.mp3 *9.mp3 *silence.mp3 *10.mp3 FINAL.mp3
```


use  * -C 320  to change your bitrate    128   256    whatever you want *

---

### Post by lovevn on 2013-09-18
> **slickymaster said:**
> What about [Audacity]("http://audacity.sourceforge.net/")?

> **tgalati4 said:**
> Sox is the Swiss Army Knife of audio tools.

Open a terminal:  

```
sudo apt-get install sox
man sox
```

Audacity is good for doing it manually.  But if you have a lot of files to do, then you will want to write a batch file (a script) to do it automatically using sox.

> **Temüjin said:**
> Take a look at mp3wrap program.
You could also approach it differently: [http://stackoverflow.com/a/1479701](http://stackoverflow.com/a/1479701)
Thank you very much! :p I done it.
> **shantiq said:**
> now you do not say how many you have but say it it only 10 or 20   THIS IS EASY [even if not used to command line]



1.    create a three-second silent file

```
[COLOR=#000000]*sudo apt-get install sox libsox-fmt-all*[/COLOR]

```to install sox if not installed

then run

```
*sox -n -r 44100 -c 2 -C 320 silence.mp3 trim 0.0 3.0*
```    and it will be found in your home folder


[B]finally to splice

[/B]rename your files and put silence.mp3 in same folder   and run


```
sox  -C 320  1.mp3 *silence.mp3 * 2.mp3 *silence.mp3 *3.mp3 *silence.mp3 *4.mp3 *silence.mp3 *5.mp3   \
*silence.mp3 *6.mp3 *silence.mp3 *7.mp3 *silence.mp3 *8.mp3 *silence.mp3 *9.mp3 *silence.mp3 *10.mp3 FINAL.mp3
```


use  * -C 320  to change your bitrate    128   256    whatever you want *

Although your solution is a bit complex, but it is quite interesting :D I tried it. Thank you!

---

### Post by tgalati4 on 2013-09-18
You guys are taking all the fun out of doing the real work.

---

