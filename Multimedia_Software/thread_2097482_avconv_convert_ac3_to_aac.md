---
title: "avconv convert ac3 to aac"
date: 2012-12-23
forum: Multimedia Software
---

### Post by asgard2 on 2012-12-23
Hi,  I want to convert an ac3 (5.1) file to aac.  currently I use: 

```
avconv -i file.mp2 -acodec aac -ac 2 -ab 64k -ar 48000 -strict experimental file.aac  
```

How does it work with an ac3 file, should I only change ac to 6 channels? 

Regards, asgard

---

### Post by shantiq on 2012-12-23
wow did not know that aac could handle 6 channels but it does


do you not have ffmpeg on your computer?
i ask this as avconv did not accept 6 channels here
but ffmpeg installed [**this way**]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide") [and maybe any way]accepts 6 channels from ac3 to aac [using libaac][libfdk_aac also happy but not libaacplus]


> ffmpeg -i file.ac3 -ab 448k file.aac

no need to say anything about channels it takes 6 to 6 [5.1]   but stipulate audio bitrate -ab mine was 448 so i ask for that to be kept











maybe your version of ffmpeg can do this too;   or maybe someone knows how to rig up avconv so it does

---

### Post by asgard2 on 2012-12-23
Are you shure that aac can not handle this?

I used these config in StaxRip before, and it works:
[[IMG]http://www0.xup.in/exec/ximg.php?fid=16379188[/IMG]]("http://www.xup.in/dl,16379188/Bildschirmfoto_-_23.12.2012_-_20:31:30.png/")

I search for something equal, in Ubuntu/Linux.

---

### Post by shantiq on 2012-12-23
sorry asgard revised my post:KS [see above]

---

### Post by asgard2 on 2012-12-23
Bei der ffmpeg installation gibt es unerfüllte Abhängigkeiten. (Ubuntu Version 12.04)
```
sudo apt-get -y install autoconf build-essential checkinstall git libass-dev libfaac-dev \   libgpac-dev libjack-jackd2-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev \   librtmp-dev libsdl1.2-dev libtheora-dev libtool libva-dev libvdpau-dev libvorbis-dev \   libx11-dev libxext-dev libxfixes-dev pkg-config texi2html yasm zlib1g-dev
```

```
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 libass-dev : Hängt ab von: libfontconfig1-dev soll aber nicht installiert werden
 libjack-jackd2-dev : Hängt ab von: libdbus-1-dev soll aber nicht installiert werden
 librtmp-dev : Hängt ab von: libgnutls-dev soll aber nicht installiert werden
 libsdl1.2-dev : Hängt ab von: libglu1-mesa-dev soll aber nicht installiert werden
                 Hängt ab von: libpulse-dev soll aber nicht installiert werden
 libx11-dev : Hängt ab von: libxcb1-dev soll aber nicht installiert werden
E: Probleme können nicht korrigiert werden, Sie haben zurückgehaltene defekte Pakete.

```

---

### Post by shantiq on 2012-12-24
> Die folgenden Pakete haben unerfüllte Abhängigkeiten:
E: Probleme können nicht korrigiert werden, Sie haben zurückgehaltene defekte Pakete.


ok some dependencies not there 



**to fix that**

> sudo apt-get -f install



if all this go well start installing ffmpeg again  Viel Glück!



**ps**   if you use this ffmpeg version you will be able to do this

> ffmpeg -i file.ac3 -acodec libfdk_aac  -ab 64k file.aac   using libfdk_aac which is better quality than default libaac

---

### Post by asgard2 on 2012-12-24
-f install doesn't fix the dependency problem, it does nothing, something else goes wrong. 

On another maschine it is working fine with this compilation guide and ```
ffmpeg -i file.ac3 -acodec libfdk_aac  -ab 64k file.aac                      
``` 

Thanks :D

Merry Christmas!

---

### Post by shantiq on 2012-12-24
and Fröhliche Weihnachten to you too:KS

---

### Post by shantiq on 2012-12-24
**PS**   if you want to do many files  [BULK conversion]


> for f in *.ac3; do ffmpeg -i "$f" -c:a  libfdk_aac  -b:a 64k "${f%.*ac3}.aac"; done

---

