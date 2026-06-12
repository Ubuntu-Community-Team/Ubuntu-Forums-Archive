---
title: "I need .amr format in sound recorder"
date: 2012-07-20
forum: Multimedia Software
---

### Post by i8bugs on 2012-07-20
G'Day- I need to be able to record voice notes in .amr format inside Ubuntu on voice recorder (or any other app that will support it). I have the .amr libraries installed for playback but I don't have the expertise to figure out how to get sound recorder to bring it up as a selection in the format drop down list. Anyone that can assist I would be grateful.
I am running 12.04

---

### Post by ron999 on 2012-07-20
> **i8bugs said:**
> ... I need to be able to record voice notes in .amr format inside Ubuntu on voice recorder...
...to figure out how to get sound recorder to bring it up as a selection in the format drop down list.
Hi
I don't think it's possible to record in amr format using **gnome-sound-recorder**. :(

But if you make the recordings in a different format (such as flac), they can be converted to amr using **FFmpeg**. :P

Install FFmpeg and extra codecs:-
```
sudo apt-get update && sudo apt-get -y install ffmpeg libavcodec-extra-53
```


Then convert the files with commands like these:-
```
ffmpeg -i [COLOR="Red"]filename[/COLOR] -acodec libvo_amrwbenc -ab 12.65k -ar 16k -ac 1 test1.amr
```
```
ffmpeg -i [COLOR="Red"]filename[/COLOR] -acodec libvo_amrwbenc -ab 23.85k -ar 16k -ac 1 test2.amr
```

(Use your own [COLOR="Red"]filename[/COLOR]!)

And if these are successful it will be OK to install **WinFF** gui and easy enough to make the pre-sets.
Tutorial here ---> [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")
:cool:

---

### Post by i8bugs on 2012-07-20
Thanks for the guide...I'll give that a try. I can dual boot in Win7 if that's easier for this task.

---

### Post by shantiq on 2012-07-21
see [**here**]("http://ubuntuforums.org/showpost.php?p=12129362&postcount=10")

---

### Post by i8bugs on 2012-07-21
Thanks Shantiq, I'm good a copy/ paste in terminal, but left to my own devices I don't understand coding.  Any way to make this process a gui, like in WinFF?

---

### Post by shantiq on 2012-07-21
:KS   oh   really here it is simple

if you copy those lines in the boxes in your terminal you can test it easy
no need to understand fully


my only concern is if 8 kHz is enough for you ?   you might want the 16 kHz but i see no way to install it


anyway just try see :KS

---

### Post by i8bugs on 2012-07-21
OK I did the record...how do you stop it? Tried Enter and Esc and neither worked. Sorry can't figure that one.

---

### Post by shantiq on 2012-07-22
ctrl + c     or control +z

---

### Post by shantiq on 2012-07-22
ctrl + c     or control +z  


and to play back  simply



```
play  myvoice.amr-nb
```   or 
```
play  myvoice.amr
```   if you have renamed it to that

---

### Post by shantiq on 2012-07-25
ok  i8bugs cracked it ! with help from the sox forum




now this may look a tad daunting but if u follow step by step here you will record a perfect 16000Hz wideband amr file


**1.**   first remove the sox we already have as we need to compile it from source

**simply enter in terminal **


```
sudo apt-get remove sox libsox-fmt-all
```   


**2.**   download sox from source [**==>here**]("http://sourceforge.net/projects/sox/files/latest/download?source=directory")/once downloaded double-click and save to your home folder    you will now have sox-14.4.0   in your home folder


**3.**   back to terminal   and again  **simply enter in terminal **


```
cd sox-14.4.0
```   then
```
./configure   --enable-dl-amrwb
```   and wait takes 3 to 4 minutes

then  ```
make
```    **and wait 3 to 4 mn**


then ```
sudo make install
```     ** or**     > sudo checkinstall




**now to use   !!**

```
rec -C 7  myvoice.amr-wb
```    -C 7   for highest compression [smallest file]   -C 1 for lowest   your choice 




**ctrl+c    to stop recording**


then rename to amr 


```
mv  myvoice.amr-wb myvoice.amr
```
PLAY


```
play myvoice.amr
```

---

### Post by andrew.46 on 2012-07-25
Perhaps use checkinstall in the final step to integrate the final sox package into the Ubuntu package management system?

---

### Post by shantiq on 2012-07-26
Hi Andrew


to replace sudo make install  ?

can you explain a bit more please?  I have seen this before but do not quite understand how it differs



ha   ok    [**i kind of **]("https://help.ubuntu.com/community/CheckInstall")understand   but still why is it better?


for this reason?


> Usage

Instead of 
sudo make install

 you will use
sudo checkinstall

When called with no arguments, checkinstall will call "make install". If you need other arguments, they can be supplied: 
sudo checkinstall make install_package

[COLOR="DarkRed"]The installed package can then also easily be removed via Synaptic or via the terminal: 

sudo dpkg -r packagename[/COLOR]

---

### Post by andrew.46 on 2012-07-26
Checkinstall is the 'budget' way of creating a debian package, it is a little limited but perfect for packages for use on your own machine. It allows for clean removal as well as automatic updating from the Ubuntu Repositories. When you investigate the options it becomes a very, very useful tool when compiling.

---

### Post by shantiq on 2012-07-26
thank you:KS

---

