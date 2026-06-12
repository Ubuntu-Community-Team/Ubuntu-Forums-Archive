---
title: "ALC888 Sound doesn't work through SPDIF"
date: 2009-02-07
forum: Multimedia Software
---

### Post by rowman on 2009-02-07
Hi,

I've just installed Ubuntu 8.10 and it seems my sound-drivers do not work. My mainboard is called Gigabyte GA-EP43-DS3 and I connected my PC through SPDIF with my AVR. Does anybody know what to do? 

Roman

---

### Post by markbuntu on 2009-02-07
There is most likely a switch in your sound mixer to turn that on.

---

### Post by rowman on 2009-02-08
This is my "Audio"-Settings-Window:

[IMG]http://i39.tinypic.com/sqmlur.png[/IMG]

"Automatisch erkennen" is german and can be translated with "Automatic detection"

What device should I choose from the droplist?

EDIT: Got it to work with ALSA Sound Mixer. Just had to activate "IEC958". Haven't heard it before... whatever :)

---

### Post by umicko on 2009-02-08
Not sure what your sound card is but....this worked for me.

from a terminal run

alsamixer

you can mute and unmute channels, you probably find the iec98 is mute which is your spdif, i think its space bar to unmute it, youll notice it when it happens.
From the gnome sound window choose alsa as your sound card and run a test.

Another test which is quite useful is from a terminal
speaker-test
you should hear static noise from your left then right, center etc speakers

otherwise...

Download and compile
alsa drivers
alsa lib
alsa utils

and run the first steps again after the successful install.

This worked for my Asus P5Q pro, might not work for you though....just my thoughts.

---

### Post by operat0r on 2010-05-23
Not sure if this helps anybody but I have mythtv and I could  only 
 SPDIF ( only 5.1 or only DTS ) or ONLY stero I could not do  both ... one or more of these things fixed it ... 

MythTV mplayer  script for videos you have issues with :
Utilities / Setup >  Setup > Media Settings > Video Settings > file types :

#!/bin/bash

IFS=\n'

foobarpath2=`echo  $1| sed -e 's/^myth.*6543/\/var\/lib\/mythtv\/videos/g' -e 's/\[/\\[/g'  -e 's/\]/\\]/g' -e 's/'\''/\\'\''/g' -e 's/(/\\(/g' -e 's/)/\\)/g' -e  's/\&/\\&/g' -e 's/;/\\;/g'`

echo playing $1 >>  /var/log/mythtv/mythfrontend.log
echo playing $foobarpath >>  /var/log/mythtv/mythfrontend.log
echo ls $foobarpath >>  /var/log/mythtv/mythfrontend.log
ls "$foobarpath" -lah >>  /var/log/mythtv/mythfrontend.log

#mplayer -fs "$foobarpath"  >> /var/log/mythtv/mythfrontend.log
# no working spdif mplayer  -fs "$foobarpath2" >> /var/log/mythtv/mythfrontend.log
mplayer  -fs mplayer -ao alsa:device=spdif -ac hwac3 "$foobarpath2" >>  /var/log/mythtv/mythfrontend.log


in mythtv frontned goto :
Utilities  / Setup > Setup > General 
Audo output device ALSA:Default 
Pass-though  device Default 
max audio channgles 5.1
Upmix : Passive
Checked  both SPDIF and uncheck aggressive sound buffering



# add  to : /etc/modprobe.d/alsa-base.conf
options snd-hda-intel  model=6stack-dig
options snd-hda-intel bdl_pos_adj=16
options  snd-hda-intel position_fix=1
options snd-hda-intel power_save=0


#  fix for flash I think in firefox or other apps etc .. maybe not needed  who knows it works no
echo export EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1  > ~/.profile

# /etc/modprobe.conf 
options snd-hda-intel  model=6stack-dig


REFERENCE / OTHER NOTES :
[http://www.mythtv.org/wiki/Configuring_Digital_Sound_with_AC3_and_SPDIF](http://www.mythtv.org/wiki/Configuring_Digital_Sound_with_AC3_and_SPDIF)
my  mobo GA-EP43-UD3L
 :  [http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ProductID=2995](http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ProductID=2995)
Realtek  ALC888 codec 
[http://docs.google.com/Doc?docid=0Aef2nrbnySfjZGhodmQ4OXBfMTdjMnhmaG5kYg](http://docs.google.com/Doc?docid=0Aef2nrbnySfjZGhodmQ4OXBfMTdjMnhmaG5kYg)

---

