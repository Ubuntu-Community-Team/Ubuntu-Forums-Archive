---
title: "Tips to install XMMS on Lucid"
date: 2010-07-06
forum: Multimedia Software
---

### Post by shantiq on 2010-07-06
**ok** so now we have "non-library" players like Audacious,  QMMP and Deadbeef so XMMS is old hat
but it still has a lot going for it

[IMG]http://img838.imageshack.us/img838/5745/smilie33.png[/IMG]Great clear sound for starters [IMG]http://img838.imageshack.us/img838/5745/smilie33.png[/IMG]


[B]

here i offer you a few routes to install XMMS  some will work for you better than others due to your version of Ubuntu or even similar  distros  (MInt etc...)




                                                                                                                                                                                                            On Pangolin

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216762&d=1335605295[/IMG]

[/B]

[CENTER][FONT=Comic Sans MS]On Oneiric
[/FONT]
[IMG]https://upload.wikimedia.org/wikipedia/en/1/1c/Xmms_coverviewer.png[/IMG]

[/CENTER]



[LEFT][[IMG]http://img839.imageshack.us/img839/4026/screenshot1ya.th.png[/IMG]]("http://img839.imageshack.us/img839/4026/screenshot1ya.png")   [[IMG]http://img149.imageshack.us/img149/7532/selection007.th.png[/IMG]]("http://img149.imageshack.us/img149/7532/selection007.png")[[IMG]http://img7.imageshack.us/img7/2126/d76q.th.png[/IMG]]("http://img7.imageshack.us/img7/2126/d76q.png")[/LEFT]





 







**[SIZE=3]1[/SIZE]**     [  this is the route i took [SIZE=3][B]for Pangolin]
[/B][/SIZE]

**[SIZE=3]Ibidem [PPA    --]("https://launchpad.net/%7Eibid-ag/+ppa-packages")[/SIZE]**     you will probably need the dependencies contained in first 9 boxes of **2. Long route** below if your version is newer than Lucid   SO do those nine boxes first then go to [**here**]("https://launchpad.net/%7Eibid-ag/+archive/oldgtk1/+index?batch=75&memo=75&start=75") and use PPA as you would for Lucid   [change version to Lucid in software sources]


**[SIZE=3]1 B.[/SIZE]**the easy way (requires python-software-properties, usually present)
Code:
```
sudo add-apt-repository ppa:adamkoczur/gtk1.2
sudo add-apt-repository ppa:ibid-ag/oldgtk1
sudo apt-get update
```Then install xmms and any extras you want:  (First set Ibidem software sources to Lucid )






Code:
```
sudo apt-get install xmms 



```for example...


```
sudo apt-get install xmms-skins xmms-xf86audio xmms-wavpack xmms-coverviewer xmms-midi

```






[U][B][SIZE=3]2.[/SIZE] Long route

It takes about an hour to fully install but is worth the effort



[/B][/U]So here a few tips       


 I was asked for x-dev at some point so i have zipped and added it to the next post

first the best guide to install the basics is here
originally posted by [ihitf13anddied]("http://ubuntuforums.org/showthread.php?t=1312757&page=2")

and goes like this


[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]1. Add the necessary repositories to software sources      system/admin/software sources


[/FONT][/FONT][/COLOR]```
[COLOR=#000000] deb [http://www.pvv.ntnu.no/~knuta/xmms/karmic]("http://www.pvv.ntnu.no/%7Eknuta/xmms/karmic") ./[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]



[/FONT][/FONT][/COLOR]```
[COLOR=#000000] deb-src [http://www.pvv.ntnu.no/~knuta/xmms/karmic]("http://www.pvv.ntnu.no/%7Eknuta/xmms/karmic") ./[/COLOR]
```[COLOR=#000000]

then to the terminal 


[/COLOR]```
[COLOR=#000000] sudo apt-get update[/COLOR]
```[COLOR=#000000]   to make sure those new sources we have just added are seen[/COLOR][COLOR=#000000]


[/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Verdana] 2. GTK1.2 is broken in Karmic, we must fix that:


[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo apt-get build-dep libglib1.2-dev[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]


 I was asked for x-dev at this point so i have zipped and added it to the next post



[/FONT][/FONT][/COLOR]```
[COLOR=#000000] apt-get -b source libglib1.2-dev[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]

[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo dpkg -i libglib1.2-dev_1.2.10-19build1_*.deb libglib1.2ldbl_1.2.10-19build1_*.deb[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]

[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo apt-get build-dep libgtk1.2[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]

[/FONT][/FONT][/COLOR]```
[COLOR=#000000] apt-get -b source libgtk1.2[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]

[/FONT][/FONT][/COLOR]```
sudo dpkg -i libgtk1.2_1.2.10-18.1build2_*.deb libgtk1.2-common_1.2.10-18.1build2_all.deb libgtk1.2-dev_1.2.10-18.1build2_*.deb
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana] 3. Next we rebuild XMMS


[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo apt-get install fakeroot[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]

[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo apt-get build-dep xmms[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]

[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo apt-get -b source xmms[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]


4. Now that we have the support, we can install XMMS:


[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo dpkg -i xmms_1.2.11-1_amd64.deb[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]   for 64-bit


or    

[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo dpkg -i xmms_1.2.11-1_i386.deb[/COLOR]
```[COLOR=#000000]   for 32-bit[/COLOR]

THIS IS THE BASIC setup

```
xmms
``` in your terminal will now open the program on your desktop

Then and to my mind the good stuff is adding all the lossless plugins so here goes

I have placed a lot of them in a zip attached below


[CENTER][IMG]http://img227.imageshack.us/img227/791/screenshot1ov.png[/IMG]
[/CENTER]
 
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana][COLOR=Black]you need to place these into /home/yourname/.xmms/Plugins


or /and   to  ```
sudo cp * /usr/lib/xmms/Input
```to find the folder do crtl/H as it is a hidden folder (if it is not there yet create it name it .xmms then name another inside of it "Plugins" and place them there)


ALSO YOU WILL for some of them NEED EXTRA PACKAGES (some of the .so files work by simply being placed in the .xmms/Plugins folders)  Extra packages also attached
[/COLOR][/FONT][/FONT][/COLOR]




_FLAC_ find it in the attached Plugins collection attached below   for 64-bit use [**this one**]("http://ubuntuforums.org/attachment.php?attachmentid=187355&d=1301308023")


_SHORTEN_

[COLOR=Black][COLOR=#000000][FONT=Times New Roman][FONT=Verdana]for shorten you need     [/FONT][/FONT][/COLOR][/COLOR]xmms-shn-2.4.0  (attached)

to make sure shorten is on your system you will need shorten-3.6.1 (attached)


if you want SHORTEN for 64-bit click [here]("http://ubuntuforums.org/attachment.php?attachmentid=193741&d=1306859558")    also on page further down as attachment

_WAVPACK_

[COLOR=Black][COLOR=#000000][FONT=Times New Roman][FONT=Verdana]ok wavpack is fine too you need   xmms-wavpack-1.0.2  (attached) 

and to install it you need to first install libwavpack-dev from the synaptic

For xmms-wavpack for 64-bit see ibidem's instructions [here]("http://ubuntuforums.org/showpost.php?p=10773596&postcount=37")

[U]APE

[/U]you need[/FONT][/FONT][/COLOR][/COLOR] libmacinput.so in zipped attachment

[SIZE=2]you may also need to down[/SIZE][COLOR=#000000][FONT=Times New Roman][FONT=Verdana][SIZE=2]load the i386 libstdc++ package 

[/SIZE][http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)[/FONT][/FONT][/COLOR]

that it says jaunty is not a problem works in Lucid fine

_TTA_  true audio

to install true audio you need ttaenc-3.4.1-src (attached)

then you need to place libxmms-tta.so (attached) in [COLOR=#000000][FONT=Times New Roman][FONT=Verdana][COLOR=Black]/home/yourname/.xmms/plugins



_MP4-AAC_  aac/m4a/mp4  (but sadly not alac)

you need xmms-mp4 (attached in next post)  OR xmms-faad2( do not install both as they may clash)  (attached in next post)  both contain libmp4.so

on my system xmms-faad2 went in straight        xmms-mp4 requires [/COLOR][/FONT][/FONT][/COLOR] libfaad0  (attached further on down this page)    your choice...
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana][COLOR=Black] 

[U]CUEFILE


[/U]if you like to use cuefiles there is a cunning add-on which reads them (attached)

once installed go options/preferences/general plugins/enable

IT WORKS PERFECTLY WITH WAVE FILES AND WITH APE  i have had no success with flac so if you want to see your track data decompress to wav.






Finally    many good skins here on  [/COLOR][/FONT][/FONT][/COLOR][http://www.1001skins.com/](http://www.1001skins.com/) also o the winamp site; only use the .wsz type



as regard the equalizer go into [COLOR=#000000][FONT=Times New Roman][FONT=Verdana][COLOR=Black]/home/yourname/.xmms/  find[/COLOR][/FONT][/FONT][/COLOR] eq.preset and replace with /or create it i use mousepad to do that

```


[Presets]
Preset0=(WinAmp) Classical
Preset1=(WinAmp) Club
Preset2=(WinAmp) Dance
Preset3=(WinAmp) Full Bass
Preset4=(WinAmp) Full Bass & Treble
Preset5=(WinAmp) Full Treble
Preset6=(WinAmp) Laptop Speakers / Headphones
Preset7=(WinAmp) Large Hall
Preset8=(WinAmp) Live
Preset9=(WinAmp) Party
Preset10=(WinAmp) Pop
Preset11=(WinAmp) Reggae
Preset12=(WinAmp) Rock
Preset13=(WinAmp) Ska
Preset14=(WinAmp) Soft
Preset15=(WinAmp) Soft rock
Preset16=(WinAmp) Techno
Preset17=Default

[(WinAmp) Classical]
Preamp=-1
Band0=-1
Band1=-1
Band2=-1
Band3=-1
Band4=-1
Band5=-1
Band6=-7
Band7=-7
Band8=-7
Band9=-9

[(WinAmp) Club]
Preamp=-1
Band0=-1
Band1=-1
Band2=8
Band3=5
Band4=5
Band5=5
Band6=3
Band7=-1
Band8=-1
Band9=-1

[(WinAmp) Dance]
Preamp=-1
Band0=9
Band1=7
Band2=2
Band3=-1
Band4=-1
Band5=-5
Band6=-7
Band7=-7
Band8=-1
Band9=-1

[(WinAmp) Full Bass]
Preamp=-1
Band0=-8
Band1=9
Band2=9
Band3=5
Band4=1
Band5=-4
Band6=-8
Band7=-10
Band8=-11
Band9=-11

[(WinAmp) Full Bass & Treble]
Preamp=-1
Band0=7
Band1=5
Band2=-1
Band3=-7
Band4=-4
Band5=1
Band6=8
Band7=11
Band8=12
Band9=12

[(WinAmp) Full Treble]
Preamp=-1
Band0=-9
Band1=-9
Band2=-9
Band3=-4
Band4=2
Band5=11
Band6=16
Band7=16
Band8=16
Band9=16

[(WinAmp) Laptop Speakers / Headphones]
Preamp=-1
Band0=4
Band1=11
Band2=5
Band3=-3
Band4=-2
Band5=1
Band6=4
Band7=9
Band8=12
Band9=14

[(WinAmp) Large Hall]
Preamp=-1
Band0=10
Band1=10
Band2=5
Band3=5
Band4=-1
Band5=-4
Band6=-4
Band7=-4
Band8=-1
Band9=-1

[(WinAmp) Live]
Preamp=-1
Band0=-4
Band1=-1
Band2=4
Band3=5
Band4=5
Band5=5
Band6=4
Band7=2
Band8=2
Band9=2

[(WinAmp) Party]
Preamp=-1
Band0=7
Band1=7
Band2=-1
Band3=-1
Band4=-1
Band5=-1
Band6=-1
Band7=-1
Band8=7
Band9=7

[(WinAmp) Pop]
Preamp=-1
Band0=-1
Band1=4
Band2=7
Band3=8
Band4=5
Band5=-1
Band6=-2
Band7=-2
Band8=-1
Band9=-1

[(WinAmp) Reggae]
Preamp=-1
Band0=-1
Band1=-1
Band2=-1
Band3=-5
Band4=-1
Band5=6
Band6=6
Band7=-1
Band8=-1
Band9=-1

[(WinAmp) Rock]
Preamp=-1
Band0=8
Band1=4
Band2=-5
Band3=-8
Band4=-3
Band5=4
Band6=8
Band7=11
Band8=11
Band9=11

[(WinAmp) Ska]
Preamp=-1
Band0=-2
Band1=-4
Band2=-4
Band3=-1
Band4=4
Band5=5
Band6=8
Band7=9
Band8=11
Band9=9

[(WinAmp) Soft]
Preamp=-1
Band0=4
Band1=1
Band2=-1
Band3=-2
Band4=-1
Band5=4
Band6=8
Band7=9
Band8=11
Band9=12

[(WinAmp) Soft rock]
Preamp=-1
Band0=4
Band1=4
Band2=2
Band3=-1
Band4=-4
Band5=-5
Band6=-3
Band7=-1
Band8=2
Band9=8

[(WinAmp) Techno]
Preamp=-1
Band0=8
Band1=5
Band2=-1
Band3=-5
Band4=-4
Band5=-1
Band6=8
Band7=9
Band8=9
Band9=8

[Default]
Preamp=-1.11022e-15
Band0=-1.11022e-15
Band1=4
Band2=6.4
Band3=8
Band4=4.8
Band5=-1.11022e-15
Band6=-1.6
Band7=-1.6
Band8=-1.11022e-15
Band9=-1.11022e-15
```on the player on the equalizer click on on


there you are if i think of any more info i will add/ please add any other tips you see i have missed 


1. tip number one   if sound not coming out check you output plugin (options/preferences/output plugin)

on Lucid Esound is the best one for my system for some unknown reason with alsa tracks refuse to move to the next  one at the end of play but fine on Esound
[CENTER]

[CENTER][[SIZE=3]**&#9658;&#9658;&#9658;&#9658;&#9658;&#9658;&#9658;&#9658;  To play cds in xmms **[/SIZE] ]("http://ubuntuforums.org/showpost.php?p=11498710&postcount=73")[/CENTER]



                                                  [SIZE=3]**&#9658;**[/SIZE][SIZE=3]**&#9658;**[/SIZE][SIZE=3]**&#9658;&#9658;&#9658;&#9658;&#9658;&#9658;&#9658;**[/SIZE][**[SIZE=3]Hotkeys for xmms[/SIZE]**]("http://ubuntuforums.org/showpost.php?p=11529389&postcount=78")    and [here with Compiz]("http://ubuntuforums.org/showpost.php?p=11529457&postcount=79")



[B]summarized
[/B]

==============

if you simply want to start XMMS with one hotkey **and** and you have compiz

open CCSM/commands enter

> xmms --t



then click on Key bindings and pick a hotkey say F6

[B]This is the fastest most efficient way to open the program and pause and play
[/B]

[COLOR=#000000][FONT=Times New Roman][FONT=Verdana] 



==================================================================
================================================================[/FONT][/FONT][/COLOR][/CENTER]
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]

There is also a different route [suggested]("http://ubuntuforums.org/showthread.php?t=1511979") [ here]("http://www.shicho.net/lamp/?p=88") not used it myself but i am told it is good too.

[/FONT][/FONT][/COLOR]

---

### Post by shantiq on 2010-07-06
also

[COLOR="Sienna"]To create a launcher
[/COLOR]
right-click on desktop then create launcher xmms command xmms

and then if you want an interesting icon pick one of the official ones or alternative ones I and others have designed


attached below


once you have the one you want you can change its size with right-clickon the icon and stretch icon


**Beyond** 11.04 you will probably need to do[** this**]("http://ubuntuforums.org/showpost.php?p=11420857&postcount=2") first

---

### Post by shantiq on 2010-07-23
> MP4-AAC aac/m4a/mp4 ([COLOR="Red"]but sadly not alac[/COLOR])

you need xmms-mp4 


anyone could think of a way to add alac functionality to xmms? :KS

---

### Post by shantiq on 2010-07-23
[B][SIZE=2]64-bit[/SIZE]
             ======
[/B]

You can install with attached debs here

xmms-flac
xmms-shn
xmms-cueinfo




xmms-mac   attached here       


requires

```
sudo add-apt-repository ppa:ibid-ag/oldgtk1
``````
sudo apt-get update
```then

```
sudo apt-get install monkeys-audio
```**NB: If you have this version     mac_3.99-u4-b5-s6~lffl~lucid~ppa4_amd64.deb of[ mac]("http://ubuntuforums.org/attachment.php?attachmentid=192966&d=1306154095") installed remove it first as it will clash with the new one from Ibidem's PPA**



also in the same way with the ibidem ppa  [This way works for 32-bit and 64 alike]   **again thank you so much ibidem for all the work on these**


you can install coverviewer [for album art] and xmms-wma    also xmms-crossfader and xmms-cueinfo  **and** xmms-mp4plugin for aac and mp4    xmms-mac for ape files and xmms-wavpack   **all in one go**


```
sudo apt-get install xmms-crossfader xmms-wma xmms-cueinfo xmms-mp4plugin xmms-coverviewer xmms-mac xmms-wavpack
```


**easier?**


I have also placed all  lossless plugins in a zip &#9658;&#9658;&#9658; [ATTACH]245937[/ATTACH][ flac wavpack shorten]  ape [mac]  is linked below

For 64-bit  unpack and move to       /usr/lib/xmms/Input

---

### Post by HattieH on 2010-07-26
Hi Shantiq,

Thank you for providing these instructions.

I have tried going through them twice, and this does not work for me.  I am running a new Ubuntu Lucid install, on a single core AMD Athlon 64 bit 3500 and 2 GB RAM.

I do not have any folder labelled ".XMMS", so I cannot put the plugins you provided in the Plugins folder.

Help, please :)

Thank you.

---

### Post by shantiq on 2010-07-27
no problem Hattieh

one has to create it    is the answer    go into your home folder

do control(ctrl) H   and then you see all the other folders with .

for example .icons and .local


So simply right click on the folder page and create a folder called 
.xmms and inside of it one called Plugins

And now place your plugins in there   .xmms/Plugins

Best of luck

---

### Post by aldostrokes on 2010-07-28
HI, I have problems installing the "xmms-mp4_2.6-1.i386.deb" this is the error: "the dependence can't satisfy: libfaad0 (>=2.6)" but also i have already installed the other package .deb that you post the "xmms-fadd2_2.0-1.i386.deb" and i had not problem installing that. I just have problems with the mp4, i hope you can help me, thanks for the other packages. cheers

---

### Post by shantiq on 2010-07-29
ok aldostrokes so install libfaad0 (attached) first then xmms-mp4 again from the deb and it should fly

Had the same situation exactly as the faad we have in the synaptic is 2.7-4 a later version :KS




also if anyone wants to use the musepack .mpc format plugin is attached here

install with make and sudo make install

---

### Post by aldostrokes on 2010-07-30
Shantiq;

Thank you very much for the help, I installed the new "libfaad0_2.6.1-3.1_i386.deb.zip" and there is no problem, and also when I open the ".deb" package "xmms-mp4_2.6-1_i386.deb.zip" at the beggining theres is not problem neither, it says "the units are satisfy" but when it is almost installed there mark and error, this one "(Reading database ... (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database .. . 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (based Reading Data ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ...
119 845 files and directories currently installed.)
Unpacking xmms-mp4 (from .../xmms-mp4_2.6-1_i386.deb) ...
dpkg: error processing / home/aldo/Descargas/xmms-mp4_2.6-1_i386.deb (- install):
 trying to overwrite `/ usr/lib/xmms/Input/libmp4.so" which is also in package xmms-faad2 0:2.0-1
Errors were encountered while processing:
 / Home/aldo/Descargas/xmms-mp4_2.6-1_i386.deb"

so I hope you can help, I can play mi mp4 files yet, I hope I will soon haha. anyway thank you very much. 

cheers.

---

### Post by shantiq on 2010-07-30
ok nearly there

uninstall xmms-faad2 first 

do   ```
sudo dpkg -r xmms-faad2
```


and reinstall  libfaad0_2.6.1-3.1_i386.deb
and xmms-mp4 again 

and this time it will work 


this is the line which tells you where the problem is


```
trying to overwrite `/ usr/lib/xmms/Input/libmp4.so" which is also in package xmms-faad2 0:2.0-1
```


you cannot run xmms-faad2 and xmms-mp4 at the same time


they clash


this time you get there :)))))


and you will see [IMG]http://img230.imageshack.us/img230/1394/preferences008.png[/IMG]    this


Suerte con todo Aldo

---

### Post by aldostrokes on 2010-07-30
Shantiq;

Thank you very much I'm so glad, that works, I could finally play my mp4 files, thanks for all. 

xmms 4 ever haha 

cheers.

---

### Post by shantiq on 2010-08-04
ok well i was playing around on the net and bumped into a nice embellishment for xmms i knew not existed

album cover display

tried it from a few places and no dice then found an .rpm i could switch to .deb with alien which works in Lucid first time



so here goes xmms-coverviewer_0.1.10-2_i386.deb (attached)

NB   may require libgdk-pixbuf2_0.22.0-14_i386.deb first     (attached)

[CENTER][IMG]http://img691.imageshack.us/img691/1768/workspace1010.png[/IMG][/CENTER]



you can also right-click on cover-viewer and hide the player leaving only this

[CENTER][IMG]http://img839.imageshack.us/img839/6726/neuunknown1972001.png[/IMG][/CENTER]

---

### Post by shantiq on 2010-08-14
[IMG]http://img835.imageshack.us/img835/5721/15124568.png[/IMG]



a [really nice skin]("http://www.1001skins.com/search.html?page=2&where=skins&query=futur") for the old player?

---

### Post by shantiq on 2010-08-23
and if you ever wanted to play bonk files here is the way to do it

---

### Post by shantiq on 2010-08-30
AND the good news is works fine on maverick too
use all the tips the way you would for lucid


only coverviewer seems not to work so far do not know why but will look
it crashes the program when trying to enable it   clever suggestions/explanations wanted
:KS

---

### Post by Ibidem on 2011-03-27
I did something similar, and then added it to a PPA.
First, I used the version of gtk1.2 here ([https://launchpad.net/~adamkoczur/+archive/gtk1.2]("https://launchpad.net/%7Eadamkoczur/+archive/gtk1.2")):
#**ppa:adamkoczur/gtk1.2**
deb [http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu) lucid main 

Then my ppa is here ([https://launchpad.net/~ibid-ag/+archive/oldgtk1]("https://launchpad.net/%7Eibid-ag/+archive/oldgtk1")):

#ppa:ibid-ag/oldgtk1
deb [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) lucid main

If you add these to /etc/apt/sources.list manually, you'll probably want
 to run  the following commands for gpg to authenticate the downloads:
#Adam Koczur's key
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys []("http://keyserver.ubuntu.com:11371/pks/lookup?search=0xDE57BAE3982823C15EE2FA01B22F4A3219E58C11&op=index")19E58C11
#Ibidem's key
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 37A9951D


Of course, that's for IF you trust the keys and keyholders.

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra) also has xmms and several updates,
 and the PPA owner is more active than I am.

Feel free to PM me if you'd like a plugin rebuilt for this version.

---

### Post by shantiq on 2011-03-28
thank you ibidem   tried to use your ppa but could not understand the order; could not understand which ones to go for

any chance you could organize the instructions step 1,2 so on for the not-so-bright like myself please...


======================

So in the meantime i went back to the [**instructions on page 1**]("http://ubuntuforums.org/showpost.php?p=9553823&postcount=1") and installed it on Natty 64-bit takes 40 minutes but works still the best sound around no contest:KS:KS



======================

problem on 64-bit though is that my plugins give me this

```
Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
/home/shantiq/.xmms/Plugins/libaac.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libwavpack.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libxmms-tta.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libvorbis.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libshn.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libwma.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libffmpeg.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libmpc.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libmacinput.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libxmms-flac.so: [COLOR="Red"]**wrong ELF class: ELFCLASS32**[/COLOR]
/usr/lib/xmms/Input/libaac.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libwavpack.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libxmms-tta.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libvorbis.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libwma.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libffmpeg.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libmpc.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libmacinput.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libxmms-flac.so: wrong ELF class: ELFCLASS32
Message: device: default

```


Are there any ways around this problem?


================================

ok flac sorted if you need flac for 64-bit attached

---

### Post by Ibidem on 2011-03-28
"Wrong ELF class: ELFCLASS32" probably means the program can only use 64-bit plugins, but you have 32-bit plugins.

**Installing, the hard way (Method A):**
1. Add these lines to /etc/apt/sources.list:
```

#ppa:adamkoczur/gtk1.2
deb [http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu) lucid main
#deb-src [http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu) lucid main
#ppa:ibid-ag/oldgtk1
deb [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) lucid main
#deb-src [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) lucid main
```2. Then run these commands:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 19E58C11
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 37A9951D
sudo apt-get update
```**Method B / the easy way **(requires python-software-properties, usually present)
```
sudo add-apt-repository ppa:adamkoczur/gtk1.2
sudo add-apt-repository ppa:ibid-ag/oldgtk1
sudo apt-get update

```Then install xmms and any extras you want:
```
sudo apt-get install xmms 
#sudo apt-get install xmms-skins xmms-xf86audio xmms-alarms xmms-musepack
```


EDIT:
Here's a good place to go hunting:[URL="http://archive.debian.org/debian/pool/main/x/"]
http://archive.debian.org/debian/pool/main/x/[/URL]
It has all the Debian xmms-* packages (WITH SOURCES), including some very old ones.  About 35 all told.
xmms (>=1.2.11) replaces xmms-dev, but you'll need libgtk1.2-dev as well to compile plugins.

---

### Post by shantiq on 2011-03-28
thank you very much for clarifications ibidem:KS


```
sudo add-apt-repository ppa:adamkoczur/gtk1.2
sudo add-apt-repository ppa:ibid-ag/oldgtk1  [COLOR="Red"]here i had to go to software sources
 and edit natty down to lucid[/COLOR]
sudo apt-get update
```

---

### Post by rifter on 2011-03-28
I am trying to do something similar, but the problem I have is not being able to get libglib1.2-dev since it has been out of the repos since Karmic.  What repository are you using to get that part?

EDIT: Never mind, I see now that the repos you mentioned have glib in them and not just xmms stuff.

---

### Post by pianoporsche on 2011-04-02
[edit] So I got XMMS to install, and I put the two SHN-related plugins in the appropriate folder, but XMMS won't play the files. Same with FLAC files. Nothing happens when I try to get the program to open them. Anybody know why this could be happening?

---

### Post by shantiq on 2011-04-03
pianoporsche    great name!!!!!!!!!!!!!


ok really easy

```
sudo apt-get install aptitude
```


if you do not want to install aptitude simply replace

```
sudo aptitude install fakeroot

```


with

```
sudo apt-get install fakeroot

```




works the same aptitude is just another program not installed by default       your choice:KS

---

### Post by shantiq on 2011-04-10
desktop/right click xmms icon/properties/doubleclick existing image/replace with new bevelled icons to see if you like it/ keep or discard...

---

### Post by shantiq on 2011-04-10
> **pianoporsche said:**
> [edit] So I got XMMS to install, and I put the two SHN-related plugins in the appropriate folder, but XMMS won't play the files. Same with FLAC files. Nothing happens when I try to get the program to open them. Anybody know why this could be happening?


PIANOPORSCHE sometimes put them into

 /home/yourname/.xmms/Plugins   is not enough   you may need to 

also go to your folder where libxmms-flac.so and libshn.so (attached) are and copy them to the following folder this way



```
sudo cp *.so /usr/lib/xmms/Input

```


then reload XMMS and see


i take it you have installed your shorten codec just in case i reattach it [here]("http://ubuntuforums.org/attachment.php?attachmentid=162586&d=1278411609") and also the xmms shorten [plugin]("http://ubuntuforums.org/attachment.php?attachmentid=162589&d=1278411609") which may need to be installed


Sometimes just putting then in Plugins folder is enough other times you have to do all this


tell us how you get on

---

### Post by shantiq on 2011-04-11
> **Ibidem said:**
> "Wrong ELF class: ELFCLASS32" probably means the program can only use 64-bit plugins, but you have 32-bit plugins.


[/CODE]Then install xmms and any extras you want:
```
sudo apt-get install xmms 
#sudo apt-get install xmms-skins xmms-xf86audio xmms-alarms xmms-musepack
```






hi there ibidem trying to [add xmms-wavpack for 64-bit]("http://ubuntuforums.org/showpost.php?p=10663808&postcount=1")   any ideas?

---

### Post by pianoporsche on 2011-04-29
Sorry it took me a while to get to this. I put those two files in the Input folder and made sure the two shn-related folders were in the Plugins folder. However, still nothing. For what it's worth I noticed that when I tweak with the volume setting on the program, the terminal gives me countless displays of this.

```
** WARNING **: oss_set_volume(): Failed to open mixer device (/dev/mixer): No such file or directory

```

Could that be related to the problem?

---

### Post by shantiq on 2011-04-30
well piano it could well be

right click on the player go options/preferences/output plugin

and choose Esound output plugin    or Alsa instead of OSS   personally i use Esound as Alsa has issues with going to the next track on my XMMS setup 



see how that works:KS

---

### Post by pianoporsche on 2011-04-30
So I tried that, and nothing changed, but I just noticed something that's probably hampering things. Right after launching xmms from the terminal, it shows

```
Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
```

That's probably the issue here. Sorry I didn't see that sooner.

---

### Post by shantiq on 2011-05-01
no Piano that really does not matter. It is always there

see my current terminal startup on 64-bit

```
xmms

[COLOR="Red"]Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory[/COLOR]
/home/shantiq/.xmms/Plugins/libaac.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libwavpack.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libxmms-tta.so: wrong ELF class: ELFCLASS32
libfaad.so.0: cannot open shared object file: No such file or directory
/home/shantiq/.xmms/Plugins/libwma.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libffmpeg.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libmpc.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libmacinput.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libaac.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libwavpack.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libxmms-tta.so: wrong ELF class: ELFCLASS32
libfaad.so.0: cannot open shared object file: No such file or directory
/usr/lib/xmms/Input/libwma.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libffmpeg.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libmpc.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libmacinput.so: wrong ELF class: ELFCLASS32
Message: device: default

```



but let me make sure of one thing you have no sound on all formats or simply some?

if it is all of them i would suggest remove all xmms and start the long install from page 1 again keeping an eye on the terminal.  That is my only suggestion really. Best of luck.



or remove all and use ibidem's easy install from previous page


Method B / the easy way (requires python-software-properties, usually present)
Code:
```
sudo add-apt-repository ppa:adamkoczur/gtk1.2

``````
sudo add-apt-repository ppa:ibid-ag/oldgtk1
```
```
sudo apt-get update

```Then install xmms and any extras you want:
Code:
```
sudo apt-get install xmms 

```#```
sudo apt-get install xmms-skins xmms-xf86audio xmms-alarms xmms-musepack
```

---

### Post by pianoporsche on 2011-05-01
All right, so I wasn't able to get xmms to open anything, so I figure I'll try starting from scratch again. I tried that other method, but when I try to install xmms, I get

```
E: Package 'xmms' has no installation candidate
```

I'll just give the other method another go. Thanks for being so patient with me.

---

### Post by Ibidem on 2011-05-04
Shantiq:
The quick, dirty way is just install ia32libs (IIRC) and install a 32-bit XMMS. 
I'd try installing libwavpack-dev and see how far that goes in building, though.

Pianoporsche:
I currently haven't built it for 10.10+; I plan to run Lucid for a few years.

```
cd /etc/apt
grep -r oldgtk1 sources.list*
```The output will look something like this:
```
sources.list:deb [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) lucid main
sources.list:deb-src [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) lucid main
sources.list.d/ibid-ag-oldgtk1-lucid.list.save:deb [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/) lucid main
sources.list.d/ibid-ag-oldgtk1-lucid.list:#deb [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/) lucid main
```As long as it says "lucid" instead of "maverick", "natty", or "oneiric", it's available;
you can edit the relevant line.
If you want to build a deb for your release:
1. Make sure that the "deb-src deb-src [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) lucid main" line is present.
2. ```
apt-get update
apt-get build-dep xmms
apt-get source --compile xmms
```And a few minutes later there should be a new xmms deb.

---

### Post by Ibidem on 2011-05-05
If you want to fix the libcanberra garbage-
sudo gedit /etc/X11/Xsession.d/.52* 
and comment it out
(or delete the file)

---

### Post by shantiq on 2011-05-05
ok ibidem this sounds worth the trip

> The quick, dirty way is just install ia32libs (IIRC) and install a 32-bit XMMS. 
I'd try installing libwavpack-dev and see how far that goes in building, though.


i have ia32-libs installed

now i take it i have to remove all my current 64-bit install to do that   and since this is a bit beyond my competence level i need further advice if you do not mind


if you look to my page 1 guide [**there**]("http://ubuntuforums.org/showpost.php?p=9553823&postcount=1")

when you get to

```
 sudo apt-get -b source xmms
```


it builds me a 64-bit package    how do I make it build me a xmms_1.2.11-1_i386.deb instead


thanx   shan

---

### Post by shantiq on 2011-05-05
> **pianoporsche said:**
> Sorry it took me a while to get to this. I put those two files in the Input folder and made sure the two shn-related folders were in the Plugins folder. However, still nothing. For what it's worth I noticed that when I tweak with the volume setting on the program, the terminal gives me countless displays of this.

```
** WARNING **: oss_set_volume(): Failed to open mixer device (/dev/mixer): No such file or directory

```

Could that be related to the problem?


piano there is a [deb here]("http://www.box.net/shared/c1bg60gv7x") which might sort you out if you are still having no joy with the other routes
i have used it before and it is straighforward you might want to have a look

---

### Post by Ibidem on 2011-05-05
Just install xmms-wavpack from my PPA-I packaged 1.0.3 last night.

---

### Post by shantiq on 2011-05-05
sorry ibidem but confused now; my install is through the first page thing so i do not think i can add your xmms-wavpack to that?

found your[ page]("https://launchpad.net/~ibid-ag/+archive/oldgtk1")

could you be a little specific if you do not mind. I do not have your knowledge of these things 

is there no way you simply can load xmms-wavpack for 64-bit here the way i have done on the first page zip it then load here if that is doable


if not no worries   thanx for help

---

### Post by Ibidem on 2011-05-05
If you download the deb from there, you can extract it.  I'd say to just run 
```
wget https://launchpad.net/~ibid-ag/+archive/oldgtk1/+buildjob/2527778/+files/xmms-wavpack_1.0.3-1_amd64.deb
dpkg-deb -X xmms-wavpack*deb|grep "libwavpack.so"
```and copy the libwavpack.so over to the /usr/lib/xmms/Input folder.
By the way, that version of xmms-wavpack builds cleanly, FWIW.
EDIT:
Alright, here.

---

### Post by shantiq on 2011-05-05
=thanx man 
really grateful   had just got there before you posted this knocking mine out and using [your PPA ]("http://ubuntuforums.org/showpost.php?p=10770716&postcount=31") but good to have it here for some other time   thanx for all your time and KNOWLEDGE :KS:KS   ps linked your info on page 1 of  thread



[CENTER][[IMG]http://img683.imageshack.us/img683/4012/workspace1005p.th.png[/IMG]](http://img683.imageshack.us/img683/4012/workspace1005p.png)[/CENTER]



========================================================================================




**xmms** still has the clearest sound of all music players i have heard  Lie back and NJOI  [CENTER][[IMG]http://img64.imageshack.us/img64/6878/clarissau.th.png[/IMG]](http://img64.imageshack.us/img64/6878/clarissau.png)[/CENTER]

---

### Post by Ibidem on 2011-05-06
Which xmms mp4/aac plugin is preferable? I'd prefer not to try building both.

PS-XMMS is building for natty, right now.  No plugins available yet, though.

---

### Post by shantiq on 2011-05-06
i seem to remember this one [xmms-faad2]("http://ubuntuforums.org/attachment.php?attachmentid=164322&d=1279877749")was better than xmms-mp4   but that was a year ago


on my system xmms-faad2 went in straight xmms-mp4 requires libfaad0 


one that would be cool too would be alac   do not think it has ever been put together; do not know if you know how to do that one or anyone for that matter here are [bits of the codec]("http://ubuntuforums.org/showpost.php?p=9626085&postcount=4")

really cool you making those

---

### Post by pianoporsche on 2011-05-06
So I've got xmms installed with the file support I want and everything, but I'm trying to figure out how to gapless playback for flac and shn files. I found a plugin called "xmms-crossfade," but I can't figure out how to get it to work. [http://www.eisenlohr.org/xmms-crossfade/index.html](http://www.eisenlohr.org/xmms-crossfade/index.html) I've got the files and everything, but I'm not quite sure what to do with them. The installation page doesn't really make sense. Does anybody have experience with this plugin, or another way to get gapless playback on xmms? Thanks!

---

### Post by shantiq on 2011-05-06
look piano there is a quicker route than a plugin here


options/preferences/options   and set Pause between songs to 0 second    **that easy**:KS  but i guess that is not really crossfade...

---

### Post by Ibidem on 2011-05-06
First: I'm packaging some things, but NOT writing new plugins--that's a little beyond my reach.
Second, where does the xmms-faad2 deb come from? I want to build it, but it isn't from faad2--that's xmms-mp4.
By the way, faad2 still includes the xmms plugin stuff--I just built it (not packaged!).

EDIT:
xmms-crossfade is building now ([https://launchpad.net/~ibid-ag/+archive/oldgtk1/+files/xmms-crossfade_0.3.10-1.1_i386.deb](https://launchpad.net/~ibid-ag/+archive/oldgtk1/+files/xmms-crossfade_0.3.10-1.1_i386.deb) & amd64 in progress).

---

### Post by pianoporsche on 2011-05-06
@Shantiq: Sadly, I gave that a go before hunting for plugins. Didn't change anything for me. 

@Ibidem: Gonna give that deb a try. Thanks for putting those together. [EDIT] So the installation went fine, and I selected the crossfade plugin under preferences, but when I change to that plugin and try to play a file, it gives me an error message saying it can't open the audio: "please check that: your soundcard is configured properly, you have the correct output plugin selected, no other program is blocking the soundcard." I'm guessing the fact that I switched out of the eSound output plugin is why it's not playing, but I'm not sure how to have both going at the same time (if that's what I need to do...)

---

### Post by Ibidem on 2011-05-07
Go to Preferences, select Crossfade, **and then click configure**.  Under the output tab, it asks what output method to use--select "output plugin" and then "alsa" or "esound".

---

### Post by shantiq on 2011-05-07
> **Ibidem said:**
> First: I'm packaging some things, [COLOR="DarkRed"]but NOT writing new plugins--that's a little beyond my reach.[/COLOR]


No worries man. I have been looking for someone who can knock up an alac plugin but i do realize it must be quite a task; alac is not even open-source


> Second, where does the xmms-faad2 deb come from? I want to build it, but it isn't from faad2--that's xmms-mp4.
By the way, faad2 still includes the xmms plugin stuff--I just built it (not packaged!).

Short answer is i haven't got a clue found it over a year ago and have lost all coordinates since   sorry

---

### Post by pianoporsche on 2011-05-07
Sweet! So I got the playback to happen, and it's delectibly gapless. However, when I seek in a song or pause it, there is about a 5-second delay before it goes to where I told it to seek to or pauses. However, there isn't this delay for when I hit the play button. Also, about four seconds before the end of the first song, the player shows that it is now playing the next song, even though it's still finishing the prior one.

I tried poking around the "configure" menu of the crossfade plugin, but I couldn't figure out how to get rid of the delay. [EDIT] I figured out a work-around. Under the Advanced panel under "configure" for the crossfade plugin, there's an option that lets you "limit OP buffer usage." If I go below 250 ms, the playback starts getting stuttery, but that was able to cut down most of the delay in response. [/EDIT]

Once again, thank you so much for being so patient with me. I really do appreciate it. I finally have a media player that can do what I want it to. The help I've received from this community has reassured that going with Ubuntu was a good call.

You all are awesome. Thanks a bunch.

---

### Post by shantiq on 2011-05-07
thanx guys would never have thought of using crossfade nice addition to the panoply


also a few "nice" skins attached     place in /home/yourname/.xmms/Skins

---

### Post by Ibidem on 2011-05-08
I found another plugin--xmms-mp4Plugin ([http://fondriest.frederic.free.fr/fichiers/](http://fondriest.frederic.free.fr/fichiers/)), got the source, applied the patch, built it (seems to use faad2 again), and found that it works with m4a.  xmms-mp4 recognizes m4a, but appears not to play it...so, now to package this!
EDIT--Source directory after compiling attached as a tarball...you can find the plugin at 
src/.libs/libmp4.so

REEDIT: packaged as xmms-mp4 in my PPA. Needs libfaad

---

### Post by shantiq on 2011-05-09
thanks ibidem works a charm used it from your attached one 

There is one other plugin i would really like to get going and so far no good on 64-bit although it had always worked perfect on 32


That is xmms-cueinfo.   I use a lot of single file albums with cue and it gives you an extra window with all the data printed


> xmms-cueinfo is a plugin for XMMS that adds support for reading cue files. 
Cue files describe what tracks a single audio file contains, including 
performer and title information. This makes it possible to rip a full CD 
into a single audio file. (The reason people do this is because of the 
audible gaps that occur when the software switches between two files. 
However, these gaps are generally shorter in unix-based operating systems 
than in Windows due to the simpler file I/O subsystem. There are also 
no-gap plugins for many players now, so there aren't really any good 
reasons for ripping CDs like this nowadays.) xmms-cueinfo also makes it 
easy to seek to each track mentioned in the cue file.



Do not want to abuse your goodwill; you have already done so many , but if you have the time and the inclination   ( not sure if you use cuefiles )


Anyway i attach a copy of [**xmms-cueinfo**]("http://ubuntuforums.org/attachment.php?attachmentid=162588&d=1278411609"):KS

---

### Post by Ibidem on 2011-05-09
Myself, I have no amd64 installs.  One of my computers could run amd64, but it has only 1 GB ram, so...  
I'd like to do it, but I'm busy this week with school; it takes about 1-2 hours when the plugin builds cleanly, since I have to check if it builds, package it, check the packaging (includes building a binary and a source package, in two runs), upload to my PPA, check whether it got accepted, and wait for amd64 to build.  I wouldn't be able to check it either, since I have no CD drives right now.
Have you not tried rebuilding it?
It's really pretty simple:
1.a. Have build-essential, libglib1.2-dev, & libgtk1.2-dev installed.
These were needed to install xmms in the first place.
b.  You'll also need xmms-dev (< 1.2.11) or xmms (>= 1.2.11) installed.  
The unofficial 1.2.11 repository includes xmms headers in the xmms package, while "official" Debian/Ubuntu versions (1.2.10 or older) use a separate xmms-dev package. 
xmms 1.2.11 doesn't depend on all the packages needed to build, though (see 1a for those).

2.  Just go about compiling it like you'd compile anything else (untar, ./configure, make, sudo make install/sudo checkinstall make install)

Hope this is helpful.


EDIT: One thing-
If you build xmms-plugin debs, you will need to edit debian/rules in the Debianized xmms source (if you used the apt-get source -b xmms method) and uncomment dh_makeshlibs (which I did in xmms 1.2.11-1ubuntu1+ppa4), then rebuild xmms and install the resulting debs.  
This slows building, but allows dpkg-buildpackage to automatically detect dependencies on xmms--needed when debian/control includes a Depends: ${shlibs}

---

### Post by shantiq on 2011-05-10
thank you man

---

### Post by Ibidem on 2011-05-24
Now it's built in my PPA, along with the XMMS Slideshow plugin (lets you view pictures in XMMS; adding a directory of pictures will start a slideshow).
I've managed to get xmms-record semi-working with quite a fight (bad symlinks break ./configure, obsolete non-ANSI GNU-isms in the code, AND fix the Makefile after that...)--it still only supports OSS & esd, since configure thinks ALSA is broken.  This is an input plugin that uses a mic/line in as a source, to add visualisations or record audio.  With xmms-ladspa it might be relevant.
I suspect that my mhwaveedit-light (GTK1, ALSA/OSS, no JACK) package would be more interesting, though; I haven't uploaded it *yet*.
Also, I built xmms-weasel, but it doesn't work quite right (only hides the player, not the playlist editor or equalizer).

---

### Post by shantiq on 2011-05-24
well ibidem great work; keep at it; the more the merrier
all the plugins we can get ameliorate the marvel that is xmms
if it can walk the dog; clean the dishes, blow one, take one to Vegas and win the jackpot; and finally obtain world peace then we shall rest ::)))   until then the best music player this side of saturn keeps getting better:KS

---

### Post by shantiq on 2011-05-31
well if any of you are seeking xmms-shn for 64-bit look no further
found a plugin in the rpm extension and have now made it into a deb through the agency of alien (the program) not the people




[**here**]("http://ubuntuforums.org/attachment.php?attachmentid=193741&d=1306859558")


also thanks to ibidem for designing a [new xmms-cueinfo]("https://launchpad.net/~ibid-ag/+archive/oldgtk1/+build/2522356/+files/xmms-cueinfo_0.2.0-1ppa1_amd64.deb") which works also on 64-bit see image

cueinfo has only ever worked for me on ape and shorten files and never on flac or wavpack   very strange

still missing a mac/ape plugin for 64-bit
not one anywhere i can see... but hey not the most common of formats anyway; would be nice to have it though

---

### Post by Ibidem on 2011-06-02
I added the library needed to my PPA, but haven't built xmms-mac ([http://morgoth.free.fr/ubuntu/pool/main/x/xmms-mac/](http://morgoth.free.fr/ubuntu/pool/main/x/xmms-mac/)) yet--I forget whether I tried.
That server has the sources, and old i386 binaries. Download just the orig.tar.gz if you don't want a deb, or also the .dsc and diff.gz for building debs.

---

### Post by shantiq on 2011-06-04
bit of variety to decorate desktop
right-click on existing icon/property/double-click on icon then find new icon on computer
all four versions attached

[IMG]http://img4.imageshack.us/img4/111/screenshotww.png[/IMG]

---

### Post by Ibidem on 2011-06-07
Did the xmms-mac plugin build?

I've built a few other plugins since:
sox-input (based on a VERY old sox, so it doesn't support that many formats)
a plugin that uses libsndfile (not all the formats are necessarily working; mostly supports oddball WAV variants)
smpeg-xmms, for MPEG/DivX;) video

And I found (at xmms.org.ua) a bunch of skins and plugins, including two supporting AVI video.
The first one (xmms-avi) has a reputation as being broken; the second, avi4xmms, requires some work:
> 
Requirements:

- XMMS linked with aviplay
  See the INSTALL file for more info on that. (Alternatively you can also
  link all the avifile plugins with "-laviplay -lstdc++" but this is much 
  more complicated than just linking XMMS.)So I may try adding a special version of XMMS, and avi4xmms as well.
Then come several effects plugins, oddcast (an icecast output plugin), a "QuickTime for Linux"-based plugin, and similar things

---

### Post by shantiq on 2011-06-12
```
Did the xmms-mac plugin build?

```   :KS:KS:KS:KS

you mean from [this]("http://ubuntuforums.org/showpost.php?p=10892110&postcount=56")   it did not for me


i do not as yet know how to turn it into a deb ibidem; so no it did not build:KS    if you have the time either to explain howto blow by blow since i have never done that before   or knock it up   would be cool



**PS**    what does sox-input do  ?    do you mean specifically for xmms ?

i use sox all the time to manipulate audio but what is sox-input in relation to xmms ?


another question is : is your xmms-mp4 still in your PPA coz it gives me not found when i try and get it on natty 64-bit 

thanx

---

### Post by Ibidem on 2011-07-15
Sorry for taking so long to answer.  I've been off in Debian land for a couple weeks, and playing with the [OpenCDE]("http://devio.us/%7Ekpedersen/") project for around a month or more, so I've been doing more with Motif than GTK1.
1. ```
dpkg-source -x *.dsc #automatically extracts the tarball & applies the patch (*.diff.gz)
cd xmms-mac*/ #You need to be in the source directory
#the debian/ folder contains all the files that control package building
#debian/control has dependencies/build-depends, and other package info
#while debian/rules is a makefile that actually runs the build process
gedit debian/control 
#change xmms-dev to xmms, and change the maintainer if you want
#Also add "libmac-dev" to the build-depends
fakeroot debian/rules binary #the quick-and-dirty-way to build a deb
# The right way is dpkg-buildpackage  (faster if you use -b to build only a binary package)
#it errors out on line 46 of src/mac.cpp, I think, about a const * char to * char conversion
#So now...fix it.  I used gvim */mac.cpp and removed the "const" on that line
#I know it's NOT the right way, but it builds
gedit */mac.cpp #change line 46, save, exit
make #see whether it compiles alright; it does, so continue
fakeroot debian/rules binary #succeeded this time
```If you have a ppa, heres an example:
```
dch -n
#<edit the changelog>
dpkg-buildpackage -b #to check how it works...
dpkg-buildpackage -S -sa 
#this builds the "source package" (*.orig.tar.gz, *.diff.gz, *.dsc, *.source.changes)
#ONLY USE -sa IF NO COPY OF THIS SOURCE TARBALL HAS BEEN UPLOADED
cd ..
#You need a GPG key and PPA here...
dput ppa:ibid-ag/oldgtk1 xmms-mac*source.changes
```
And yes, I just ran all of that--so it has now been uploaded to my ppa.

2.  xmms-mp4plugin is the package name.

3.  sox-input is an xmms input plugin (based on an older sox version) which lets xmms load all the audio formats that the base sox version supported.  
There's also a sox-effects plugin to go with it (letting you do the manipulations by way of sox); I haven't packaged the latter.

---

### Post by shantiq on 2011-07-16
thank you ibidem


```
sudo apt-get install xmms-mp4plugin
``` totally works and finally i can play all my aac and mp4 files thank you

i am still confused as regards xmms-mac.  On natty 64-bit it gives me 

```
E: Unable to locate package xmms-mac

```


but maybe i misunderstood your explanations
(i can see it is listed on your [[FONT="Comic Sans MS"]**page**[/FONT]]("https://launchpad.net/~ibid-ag/+archive/oldgtk1?field.series_filter="))

but it does not come to my system yet

Is there something i have missed?

Thanx again for all those plugins they really enhance this amazing program

---

### Post by Ibidem on 2011-07-19
Maybe ```
sudo apt-get update
```? (you have to tell the package manager to update the package list after it's been uploaded).

---

### Post by shantiq on 2011-07-20
ok ibidem i should have thought of that  :):)

and it works nicely (altho at times it terminates the program; no clear pattern there)


When installing ```
sudo apt-get install xmms-mac
``` it clashed with my install of mac which was already present so i had to remove it and install your version 
```
sudo apt-get install monkeys-audio
```

overall a great adjunct    thank you


====================================================================

Now have all main lossless  flac wavpack ape   and also shorten      also aac/mp4   ogg   mp3 and even midi    so a very happy bunny

\\:D/\\:D/

---

### Post by meanmrmustard on 2011-08-03
Just wanted to add my thanks for your install instructions - I'm still not over having xmms removed from the repos. Great plugins too.
:guitar:

---

### Post by pianoporsche on 2011-09-29
Hey all. Having problems getting xmms-crossfade to work. Running 64-bit Natty. Ibidem suggested I post what shows up when I run xmms from a terminal, so here goes:

```
Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
/home/pianoporsche/.xmms/Plugins/libxmms-tta.so: wrong ELF class: ELFCLASS32
/home/pianoporsche/.xmms/Plugins/libffmpeg.so: wrong ELF class: ELFCLASS32
/home/pianoporsche/.xmms/Plugins/libshn.so: wrong ELF class: ELFCLASS32
/home/pianoporsche/.xmms/Plugins/libvorbis.so: wrong ELF class: ELFCLASS32
/home/pianoporsche/.xmms/Plugins/libmpc.so: wrong ELF class: ELFCLASS32
/home/pianoporsche/.xmms/Plugins/libmacinput.so: wrong ELF class: ELFCLASS32
/home/pianoporsche/.xmms/Plugins/libwavpack.so: wrong ELF class: ELFCLASS32
/home/pianoporsche/.xmms/Plugins/libwma.so: wrong ELF class: ELFCLASS32
/home/pianoporsche/.xmms/Plugins/libaac.so: wrong ELF class: ELFCLASS32
/home/pianoporsche/.xmms/Plugins/libxmms-flac.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libxmms-tta.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libffmpeg.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libmpc.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libmacinput.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libwavpack.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libwma.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libaac.so: wrong ELF class: ELFCLASS32
Message: device: default

** WARNING **: Failed to open font: "-adobe-helvetica-bold-r-*-*-10-*".
```I made sure to install with the packages on Ibidem's PPA, but I'm still out of luck. I'm sure I've made a rookie mistake, so apologies if the solution is staring me in the face.

---

### Post by shantiq on 2011-09-29
cannot see xmms-crossfade there so maybe not yet installed?


so i guess using ibidem's crossfade PPA thing



```
sudo add-apt-repository ppa:adamkoczur/gtk1.2
sudo add-apt-repository ppa:ibid-ag/oldgtk1
sudo apt-get update
```


then

```
sudo apt-get install xmms-crossfade
```

Apologies if you have already done this:KS

---

### Post by pianoporsche on 2011-09-29
Yup, I've already done that. I tried it again just to make sure and had a message telling me

```
xmms-crossfade is already the newest version.
```

Which makes me wonder why it wasn't showing up in that list of outputs I posted above...

---

### Post by shantiq on 2011-09-29
and you have done the settings   [ thus]("http://ubuntuforums.org/showpost.php?p=10781081&postcount=45")   ?


all those ELFCLASS32 are showing because they are wrong not the 64 you need for your setup 

 xmms-crossfade does not show in that list as you have the right version i guess

---

### Post by Ibidem on 2011-09-29
Make sure all the xmms* packages are 64-bit

---

### Post by pianoporsche on 2011-10-03
Huh. So I completely uninstalled xmms and all the plugins and started over (making sure not to accidentally install both 32- and 64-bit plugins), and that somehow righted things. Thanks for the help!

---

### Post by shantiq on 2011-10-23
Looking ok on Oneiric too


I have put together a bit more [**info**]("http://ubuntuforums.org/showpost.php?p=9626085&postcount=4") about available 64-bit lossless plugins ( Thanx to ibidem)

---

### Post by andrew.46 on 2011-11-22
Hey shantiq!!!

I am a little stuck getting xmms to play audio cds, the only plugin I have is CD Audio Player 1.2.11 (libcdaudio.so). Is there a better cd plugin available? Or perhaps I am just too obtuse to get this one to work.....

---

### Post by shantiq on 2011-11-29
sorry Andrew just saw this    truth is i have never played a cd through xmms   let me see




ok   try this   

works for me amazing **how little strain** is put on the cd drive xmms best here too maybe

apparently reading around one should pick **digital audio extraction** and not analog

then click on + at bottom of playlist which opens Load files box then pick tracks you want to add


[CENTER]
[[IMG]http://img64.imageshack.us/img64/7003/desktop002.th.png[/IMG]](http://img64.imageshack.us/img64/7003/desktop002.png)[/CENTER]



ok as regards the plugin had a look around   found something called [xmms-cdread ]("http://pkgs.org/download/xmms-cdread")  as an alternative to CD Audio Player 1.2.11    for 64 and made a 64 deb [there ]("http://pkgs.org/download/xmms-cdread")is 32 there too if you need

i added it to my setup so i do not know if it works because of this :KS or if 
CD Audio Player 1.2.11 was enough but i have enabled both

[B]
ok
[/B] checking again looks like cdread works for me as it has a    add CD to playlist button under Options which CD Audio Player 1.2.11 has not    

[CENTER][IMG]http://img269.imageshack.us/img269/5515/cdreaderconfiguration00.png[/IMG] [/CENTER]


i attach the deb here [created with alien]   it shows up in options/preferences/  Audio IO plugins   then enable



Hope it all goes tickaboo for you i think just setting it to digital audio extraction and adding from + sign should do it i hope

---

### Post by andrew.46 on 2011-11-30
Thanks shantiq, once I looked a bit more closely at the steps that you explained it is all now working :). I attach a screenshot showing xmms playing a cd (Solaris) with my new best friend fluxbox. I love the way xmms just looks so right with a minimalist setup like fluxbox and I intend to examine all of your xmms posts a little more closely so I can get the most out of this great media player!!

---

### Post by shantiq on 2011-11-30
Brilliant Andrew love your setup   it is slackware is it not?

After the to-my-mind fiasco of the latest distro and the whole direction clearly taken i am looking at possible dual-boot on my set up   keep ubuntu current and start to investigate something new on the side something more pared down


is slackware really hard?


that fluxbox looks amazing again is it hard to use? can it be used on Oneiric?


XMMS blends in perfectly with a zen-ified desktop.  I would just suggest maybe a better skin :KS

many good skins here on [http://www.1001skins.com/]("http://www.1001skins.com/") also on the winamp site; only use the .wsz type

If you use single file lossless with cue the cuefile thing used on XMMS is the best also you can add coverviewer


[CENTER][[IMG]http://img339.imageshack.us/img339/5811/screenshotat20111130094.th.png[/IMG]](http://img339.imageshack.us/img339/5811/screenshotat20111130094.png)[/CENTER]

---

### Post by andrew.46 on 2011-11-30
It is slackware -current which is the development version of Slackware, the stable release at the moment is 13.37. I don't believe it is an especially hard distro but the approach is certainly different to Ubuntu, well worth having at least a look at.

Fluxbux is also pretty straightforward as it really only involves editing a handful of configuration files to make things work well. Big conceptual change from kde, gnome and xfce though and I suspect this is the main challenge.

I tried Fluxbox on Oneiric and did not like it. Better with Slackware where Fluxbox is totally bare and unmodified and you get to shape things as you see fit.

I shall have a look at some skins although I am pretty happy with the basic view. BTW Slackware is one of the few distros that packages the original xmms as part of the distro :).

---

### Post by shantiq on 2011-11-30
>  BTW Slackware is one of the few distros that packages the original xmms as part of the distro .


Gosh did not know anyone still had it as standard:KS
Will definitely take a look

---

### Post by shantiq on 2011-12-11
**[[SIZE=3][FONT=Courier New]from [/FONT][/SIZE]]("http://jimbojw.com/wiki/index.php?title=XMMS%2C_Gnome_and_global_hotkeys_-_setting_up_keybindings")**





[SIZE=2]now xmms does not have a hotkey setup already installed and the plugin i have tried [/SIZE]XF86Audio Keys Control [SIZE=2]gave me no joy [i could not get it to work[/SIZE]]


[SIZE=2]but fear not here is a perfect howto for metacity[/SIZE]
[SIZE=2]now personally i have compiz on my setup so i shall keep on lookin  [**ok found it**]("http://ubuntuforums.org/showpost.php?p=11529457&postcount=79")[/SIZE]


[SIZE=2]i have set this way on mine as these are the only hotkeys i use regularly[/SIZE]


 [COLOR=Black]**[SIZE=2] Even works when minimized[/SIZE]**[/COLOR]

[SIZE=2]**xmms --t **    and this will work for pause and play and also start the program so really that is the one ::]]][/SIZE]
[SIZE=2]xmms --fwd                F10    to go to next track[/SIZE]
[SIZE=2]xmms --rew                Insert[/SIZE]    [SIZE=2]to go to previous track 
[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]but of course each to his own
[/SIZE]

---

### Post by shantiq on 2011-12-11
ok so if you have compiz


you need to do a couple of simple thngs to extend these functions to your desktop


install  CCSM   which you probably have already

```
sudo apt-get install ccsm
```

Then tick in commands on main page of ccsm   see image attached
Click on commands and see your bindings from the gconf-editor set in previous post

That is it :KS:KS   if you do not want to set it all for metacity as well you can can just set it here in ccsm
First  xmms commands in commands then key bindings...



============

If anyone knows how to do this for Unity please add here.  Thanx

---

### Post by shantiq on 2011-12-21
FURTHER refinement
==============

if you simply want to start XMMS with one hotkey [or any program in the same way]

open CCSM/commands  enter   ```
xmms --t
``` then click on Key bindings and pick a hotkey  say F6

This is the fastest most efficient way to open the program:KS **and** pause and play

---

### Post by shantiq on 2012-02-20
if you wish to add option of xmms-pulse on your 64-bit system here is a deb to do that   [worked with alien from rpm]

---

### Post by shantiq on 2012-04-16
I had been trying to enable different European languages on Xmms and had so far been unable to but by sheer luck found a way  .... may be of use to some of you

Here English Turkish Cyrillic and Portuguese all display perfectly [French and German Greek fine too ]


Options/Preferences
Click in use fontsets
and use X fonts ; click on browse in both cases and pick fixed (misc)  in the fonts on the left

I found bold 13 to give a good clear print but the other are cool too
[CENTER]

[[IMG]http://img651.imageshack.us/img651/7481/screenshotat20120416181.th.png[/IMG]](http://img651.imageshack.us/img651/7481/screenshotat20120416181.png)
[/CENTER]

---

### Post by shantiq on 2012-04-28
now running on Pangolin


had to use **1 ** from **[page one]("http://ubuntuforums.org/showthread.php?t=1525072")**   all first nine boxes from **[SIZE=3]2.[/SIZE] Long route** [to make sure all dependencies were there]  then installed Ibidem PPA    and the old beast is good on the latest version of Ubuntu

[CENTER][ATTACH]216762[/ATTACH]
[/CENTER]

---

### Post by shantiq on 2013-03-11
quick note to say to other fans of the old Russian app  just installed on 13.04 [64-bit] and fine too   using info from first post   and Ibidem's PPA   as explained in detail [there]("http://ubuntuforums.org/showthread.php?t=1525072")
xmms moves to the next level

 aac m4a wavpack flac mp3 ape shn ogg wav etc all good!

once you have all dependencies install xmms and plugins in one

 ```
sudo apt-get install xmms xmms-flac xmms-shn xmms-mp4plugin xmms-coverviewer xmms-cueinfo xmms-crossfade xmms-wavpack xmms-midi xmms-musepack xmms-mac
```


[ATTACH=CONFIG]240049[/ATTACH]


 Would still love it if someone knowledgeable knocked up an alac plugin too:KS

---

### Post by shantiq on 2013-10-19
```
sudo add-apt-repository ppa:ibid-ag/oldgtk1 
sudo apt-get update



```run   ```
 software-properties-gtk

```



then


change both ibid lines to lucid




and also while there add:


```
deb http://www.pvv.ntnu.no/~knuta/xmms/karmic ./

```

```
deb-src http://www.pvv.ntnu.no/~knuta/xmms/karmic ./

```

to software sources

=====




add[ x-dev ]("http://ubuntuforums.org/attachment.php?attachmentid=177589&d=1291626076")package


then


```
sudo apt-get build-dep libglib1.2-dev



```happy with enough dependencies by then it seems ....


and then for xmms and plugins from ibidem




```
sudo apt-get install xmms   xmms-cueinfo xmms-mp4plugin xmms-coverviewer  xmms-wavpack

```

if you want to play flac   


install flac


then      install[ deb]("http://ubuntuforums.org/attachment.php?attachmentid=205283&d=1319398314")


if you want to play [shorten]("http://http://ubuntuforums.org/attachment.php?attachmentid=162586&d=1278411609") files also download 


and install   ./configure make sudo make install




then [get ]("http://http://ubuntuforums.org/attachment.php?attachmentid=205281&d=1319398134")   and install 


for some reason libshn went to the wrong place and was not seen


i had to manually move it to /usr/lib/xmms/Input/    where libwavpack is  [which is the correct place]




/usr/lib/xmms/Input/libwavpack.so
/usr/lib64/xmms/Input/libshn.so




you can add ape with xmms-mac from ibidem [personally i do not use it as it clashes with flacon; if you do not use flacon go right ahead]




then you have was flac ape wavpack shorten m4a aac mp3 ogg  all good on xmms on Saucy








set sound to alsa on Saucy  ....    yea   still kickin' the ole russian beast ...

---

### Post by edwardmartinsjr on 2013-12-12
Other GUI client for XMMS2 is the Promoe. Promoe is a client for the XMMS2 music daemon. Promoe’s interface is modeled after XMMS/WinAMP classic and supports Winamp 2 skins. It's written in C++ anduses the Qt4 toolkit.
[http://packages.ubuntu.com/lucid/promoe](http://packages.ubuntu.com/lucid/promoe)
[IMG]http://taufanlubis.files.wordpress.com/2007/12/xmms2.png[/IMG]

---

### Post by shantiq on 2013-12-12
thanx for the info Edward on xmms2 but this thread here is really about xmms not xmms2 ; a different kettle of fish;   personally i use xmms2 also sometimes and favour esperanza as a gui    Promoe is a perfect copy of default xmms skin  ;   maybe [try xmms ]("http://ubuntuforums.org/showthread.php?t=1525072&p=12821399#post12821399")too [if you have not]you will be amazed by sound quality

---

