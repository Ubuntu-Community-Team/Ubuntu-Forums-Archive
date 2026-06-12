---
title: "Video Conversion Help Needed"
date: 2010-11-01
forum: Multimedia Software
---

### Post by maximus_vk on 2010-11-01
Hi all,

First of all i have a sony dvd-home theatre system with 5.1 channel audio and usb support and i want to play my movies in it. The problem now is that i cant create a proper video file which the DVD-player is capable of playing.
The screen-shot below tells the supported formats. 

[IMG]http://img230.imageshack.us/img230/8983/sonyjo.png[/IMG]


i already have many mp4,mkv format videos with 5.1 channel audio in it, but all of them are encoded in h.264 format (which the DVD player DOES NOT support) .


Could anybody be kind enough to tell me the script/code or tool to be used wherein i can retain the 5.1 channel audio(in either mp3 or aac) but video to be playable in Divx or MPEG4 ?

Please let the conversion be a fast one and quality & resolution be retained very much like the original.

My laptop configuration is Intel Core2Duo 2.0 GHz, 3GB ram, 250GB Hard Disk, 256MB Nvidia GeForce 9200M GS, Ubuntu 10.10 installed.

---

### Post by Jahid65 on 2010-11-01
Have you tried winff? It's in the software center. you may need extra presets. yuo can find [http://winff.org/html_new/downloads.html](http://winff.org/html_new/downloads.html) bottom of the page. you might have to install codecs to use theme properly. 

Or you can use command-line tool ffmpeg.

first go to the folders which contains the source file through terminal. Suppose the file is in Desktop. you run these commands one after one in terminal.
```
cd ~Desktop
```
this will bring you to your desktop folder. then run this.
```
ffmeg -i input.mp4 -f dvd -vcodec mpeg2video -r 29.97 -s 352x480 -aspect 4:3 -b 4000kb -mbd rd -trellis -mv0 -cmp 2 -subcmp 2 -acodec libmp3lame -ab 192kb -ar 48000 -ac 2 output.mpg 
``` 
source file: input.mp4
generated file: output.mpg

this type of code you can find in winff. in edit-> presets

---

### Post by maximus_vk on 2010-11-01
> **Jahid65 said:**
> Have you tried winff? It's in the software center. you may need extra presets. yuo can find [http://winff.org/html_new/downloads.html](http://winff.org/html_new/downloads.html) bottom of the page. you might have to install codecs to use theme properly. 

Or you can use command-line tool ffmpeg.

first go to the folders which contains the source file through terminal. Suppose the file is in Desktop. you run these commands one after one in terminal.
```
cd ~Desktop
```this will bring you to your desktop folder. then run this.
```
ffmeg -i input.mp4 -f dvd -vcodec mpeg2video -r 29.97 -s 352x480 -aspect 4:3 -b 4000kb -mbd rd -trellis -mv0 -cmp 2 -subcmp 2 -acodec libmp3lame -ab 192kb -ar 48000 -ac 2 output.mpg 
```source file: input.mp4
generated file: output.mpg

this type of code you can find in winff. in edit-> presets

Ok .. will try it now and reply about it in some time ..

---

### Post by gordintoronto on 2010-11-01
Use Winff, aka "Video Converter", and specify "XViD fullscreen" as the device preset.

---

### Post by maximus_vk on 2010-11-02
i tried it but conversion not  happening :(

---

### Post by Jahid65 on 2010-11-02
> **maximus_vk said:**
> i tried it but conversion not  happening :(

What type of errors? Have you tried Winff?

---

### Post by maximus_vk on 2010-11-02
[FONT=Book Antiqua]I am sorry to sound like an absolute newb, but i still could not do any conversion.:cry:

Please tell me in a step-by-step manner as to what packages i need to install first , then what steps i need to take after i install them, then command line conversion (preferably from any-file to mp4[not-h.264] or avi)(i wish that the 5.1 channel audio is left intact), even hardsub the subtitles if i have to do it for avi.

Please help me.[/FONT][-o<

---

### Post by Jahid65 on 2010-11-03
Have you install restricted extras? if not install it from software center. You may need medibuntu repo. Open Terminal and type
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Then you have to install libdvdcss2, type in terminal or use USC
```
sudo apt-get install libdvdcss2
```Then
**For 32-bit **
```
sudo apt-get install w32codecs
```**For 64-bit**
```
sudo apt-get install w64codecs
```You can use USC to install this packages.

Then use winff with downloaded presets from their site. 
Is avi with divx format compatible for your dvd?

[IMG]http://img89.imageshack.us/img89/1010/screenshotredobackupavi.png[/IMG]

---

### Post by maximus_vk on 2010-11-05
@Jahid65

I did everything exactly as you have said here. Updated everything and it updated. Yes, DivX and XviD both formats are supported by my dvd player.

Also installed WinFF which i uninstalled earlier. Now i will try to convert some videos. I will post the progress.

Thanks for trying to help me out.

---

### Post by maximus_vk on 2010-11-06
i tried winff, worked well with just the video part. Now there is some problem with audio.

 It says '-ac' in the command line not recognized. I think its audio channel. I had mentioned 6 but it did not work. Next time i left the audio channel option as it is and after video conversion, it said cannot resample 6 channels to 2 channels !!!!

What am i supposed to do ?

---

### Post by ron999 on 2010-11-07
..

---

### Post by Jahid65 on 2010-11-10
> **maximus_vk said:**
> i tried winff, worked well with just the video part. Now there is some problem with audio.

 It says '-ac' in the command line not recognized. I think its audio channel. I had mentioned 6 but it did not work. Next time i left the audio channel option as it is and after video conversion, it said cannot resample 6 channels to 2 channels !!!!

What am i supposed to do ?

Is ac3 format supported? if yes then you try this for your audio option
```
ffmpeg -i input.mp3 -f ac3 -acodec ac3 -ab 192kb -ar 48000 -ac 6 output.ac3
```[[IMG]http://img9.imageshack.us/img9/1833/screenshotje.png[/IMG]]("http://img9.imageshack.us/my.php?image=screenshotje.png")

[http://img9.imageshack.us/img9/1833/screenshotje.png](http://img9.imageshack.us/img9/1833/screenshotje.png)

---

### Post by maximus_vk on 2010-11-12
okay .. will try now..

---

