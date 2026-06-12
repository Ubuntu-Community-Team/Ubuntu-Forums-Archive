---
title: "How to convert mp3 files to aac?"
date: 2011-06-04
forum: Multimedia Software
---

### Post by xxcrestfallenangelxx on 2011-06-04
My sister has a Nintendo DSi that can only play music files if converted to aac format. I could do it on my desktop that runs Windows XP, but unfortunately my tower doesn't have an SD slot to do so. The laptop I'm using does have a slot and is running Ubuntu. The thing is, is there any way I can convert mp3 files to aac so they can play on my sister's DSi?

Replies would be great! 

Thank you.

xxx

---

### Post by 3xp10r3r|X13 on 2011-06-04
ffmpeg is a great tool to convert lots of stuff, although it runs in the terminal and therefore is a bit difficult to handle.

you can get it by either searching through the software center, or you just type:

sudo apt-get install ffmpeg

--> it is really awesome; you can even record your desktop with it - it offers an alternative to gtk-recordmydesktop as well

---

### Post by ken_do_san on 2011-06-04
Try Winff (no it's not a windows app), its in the repositories and it has a GUI (it uses ffmpeg) and is very to use.

---

### Post by shantiq on 2011-06-04
> **xxcrestfallenangelxx said:**
> My sister has a Nintendo DSi that can only play music files if converted to aac format. I could do it on my desktop that runs Windows XP, but unfortunately my tower doesn't have an SD slot to do so. The laptop I'm using does have a slot and is running Ubuntu. The thing is, is there any way I can convert mp3 files to aac so they can play on my sister's DSi?

Replies would be great! 

Thank you.

xxx


**one easy route; once a bit harder; and one really good but a bit more involved**


ok you can use  **sound[COLOR="Red"]k[/COLOR]onverte**r  in synaptic


or install this way    ```
sudo apt-get install soundkonverter
```


then go applications/sound and video/soundKonverter   and set to aac       THAT ROUTE IS really easy  :KS

[CENTER]
[IMG]http://img89.imageshack.us/img89/732/soundkonverter003.png[/IMG][/CENTER]


**this is from the current version on natty which is   Version 1.0.0 rc2  **

========================================
or use command line with ffmpeg

```
sudo apt-get install ffmpeg lame

```


then run  to convert a whole batch

```
for f in *.mp3; do ffmpeg -i "$f" -acodec aac -strict experimental -ab 128k "${f%.mp3}.aac"; done

```

change 128k for 192k or 256k or 320k to suit your needs



=================================================
**or if you want a really high quality convert with tags kept**

This may look difficult but if you follow steps really easy



1.   install neroAacEnc   (attached)

place these 3 codecs in your home folder; then


2.  ```
sudo mv neroAacEnc neroAacDec neroAacTag /usr/bin
```


```
cd /usr/bin
```

```
sudo chmod +x neroAacEnc neroAacDec neroAacTag   
```



3. cd (change directory) to where your files are

4.   enter all of this text in one go in your terminal


```
#!/bin/bash
for f in *.mp3
do
OUTF=`echo "$f" | sed s/\.mp3$/.aac/g`

ARTIST=`ID3  "$f"   --show-tag=GENRE| sed s/.*=//g`
TITLE=`ID3 "$f"   --show-tag=GENRE| sed s/.*=//g`


ALBUM=`ID3 "$f" --show-tag=GENRE| sed s/.*=//g`
GENRE=`ID3 "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKTOTAL=`ID3 "$f" --show-tag=TRACKTOTAL | sed s/.*=//g`
DATE=`ID3 "$f" --show-tag=DATE | sed s/.*=//g`
TRACKNUMBER=`ID3 "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`





lame --decode     "$f" - | neroAacEnc -if -  -cbr 320000 -of  "$OUTF"
neroAacTag "$OUTF"  -meta:artist="$ARTIST" -meta:title="$TITLE" 
done
mkdir "$ALBUM" && mv *.aac "$ALBUM"
```

---

### Post by gordintoronto on 2011-06-04
You can use Synaptic to install Sound Converter.

---

### Post by kiraku on 2013-04-24
> **shantiq said:**
> 
========================================
or use command line with ffmpeg

```
sudo apt-get install ffmpeg lame

```


then run  to convert a whole batch

```
for f in *.mp3; do ffmpeg -i "$f" -acodec aac -strict experimental -ab 128k "${f%.mp3}.aac"; done

```

change 128k for 192k or 256k or 320k to suit your needs



=================================================
[/CODE]

Hi,


i was using menc 0.2.2 in windows, looking for how to do it in linux brought me here...
My question is, is the -ab option the bitrate? i use to use 48 kbps in menc...
if no, how to set it up?

---

### Post by evilsoup on 2013-04-24
Old thread is old but: yes, in shantiq's post '-ab' means 'audio bit rate'; to get 48 kbps you'd use '-ab 48k'. However, in more recent versions of ffmpeg '-ab' is in the process of being replaced with '-b:a' as part of a general syntax clean-up, so you should use '-b:a 48k' instead.

---

### Post by kiraku on 2013-04-24
got it, thankz a lot.

---

### Post by wildmanne39 on 2013-04-24
Thread closed. Please do not post in old threads.

---

