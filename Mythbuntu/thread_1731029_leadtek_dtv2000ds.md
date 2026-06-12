---
title: "leadtek dtv2000ds"
date: 2011-04-16
forum: Mythbuntu
---

### Post by phillipcc on 2011-04-16
hi forum i am running mythbuntu 10.10 i believe it is and i am unable to get the leadtek dtv2000ds identified in mythtv-setup if anyone can help me get it going it would be very much appreciated thanks i have very few linux skills so i can only try my best
thanks in advance for any help
phillip

---

### Post by goffa on 2011-04-21
Hi phillip

you will find information the links below to get this card working

[http://forums.whirlpool.net.au/archive/1476346#r27691011](http://forums.whirlpool.net.au/archive/1476346#r27691011)

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

[http://www.pcmediacenter.com.au/forum/topic/40407-leadtek-dtv2000ds/page__st__90](http://www.pcmediacenter.com.au/forum/topic/40407-leadtek-dtv2000ds/page__st__90)

from the linuxtv wiki
In order to be able to build the V4L-DVB kernel driver modules, you will need:

    * kernel-source or kernel-headers
    * (OpenSuSE and fedora only) kernel-devel
    * make
    * gcc
    * git
    * patch 

If these packages are not currently installed on your system, you should do so now. 

git clone git://linuxtv.org/media_build.git
cd media_build 
./build.sh
sudo make install

install the firmware
wget [http://palosaari.fi/linux/v4l-dvb/firmware/af9015/4.95.0.0/dvb-usb-af9015.fw](http://palosaari.fi/linux/v4l-dvb/firmware/af9015/4.95.0.0/dvb-usb-af9015.fw)
sudo cp dvb-usb-af9015.fw /lib/firmware


the other option is to follow the guide here [http://forums.whirlpool.net.au/archive/1476346#r28528934](http://forums.whirlpool.net.au/archive/1476346#r28528934)

---

### Post by phillipcc on 2011-05-05
hi as i am a begginer i am stumped on how to install the firmware required for this card if their is anyone who can give me step by step instructions i would appreciate it thanks i am an absolute begginer very few ubuntu skills so anything anyone can help me with i would apppreciate
thanks phill

---

### Post by declanmullen on 2011-05-05
I recently setup a Mythbuntu 10.10 with a dtv2000ds. It was relativly simple to get it to work:

[LIST]
[*]Used Update Manager (see System menu) to ensure the system was up to update.
[*]Used the "Additional Drivers" proprietary software install tool (see Sytem menu) to install the DVB firmware.
[*]Did a complete shutdown, turn off and restart.
[*]Registered the dtv2000ds in Mythtv backend as a DVB capture card. Mythtv automatically detected the details (eg giving it a Frontend ID of Afatech AF9013 DVB-T).
[/LIST]

To find the firmware version number, you can search /var/log/syslog for af9013 and you should find somthing like this:
```
May  5 21:47:51 pvr kernel: [   20.331528] af9013: firmware version:4.95.0
```

---

### Post by phillipcc on 2011-05-08
hi all fixed now thanks for that sorry  not to have replied sooner but have been away for a bit ok so thanks for that little bit of information i also worked out why i could not watch or record tv at all it does help to check how much disc space you have left lol id run out and didnt even notice have increased it by a whole 2 terabytes hope i dont run out now chat soon and thanks again
phill



[
QUOTE=declanmullen;10775634]I recently setup a Mythbuntu 10.10 with a dtv2000ds. It was relativly simple to get it to work:

[LIST]
[*]Used Update Manager (see System menu) to ensure the system was up to update.
[*]Used the "Additional Drivers" proprietary software install tool (see Sytem menu) to install the DVB firmware.
[*]Did a complete shutdown, turn off and restart.
[*]Registered the dtv2000ds in Mythtv backend as a DVB capture card. Mythtv automatically detected the details (eg giving it a Frontend ID of Afatech AF9013 DVB-T).
[/LIST]

To find the firmware version number, you can search /var/log/syslog for af9013 and you should find somthing like this:
```
May  5 21:47:51 pvr kernel: [   20.331528] af9013: firmware version:4.95.0
```[/QUOTE]

---

