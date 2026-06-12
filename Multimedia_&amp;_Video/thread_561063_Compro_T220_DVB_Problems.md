---
title: "Compro T220 DVB Problems"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by HighSide on 2007-09-27
Hi 

I have installed Feisty (64bit) and all is good so far, untill I tried to install a DVB-T card,  a Compro _T220_ and have been unable to get it to work.

I initially tried to install the _T200_ driver as this has the same chipset. 

I then tried to install the drivers following the guide - [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)
But still no joy.

I think I have a fundemental problem as there is no /dev/dvb folder.
(Do I just need to create this folder?)

I have also seen on other threads that the firmware may need updating, but this again is not specific to my card. 

Thanks

---

### Post by HighSide on 2007-09-27
I have been searching this forum and have googled the problem ans have done the following:

I followed the instructions in this thread [http://ubuntuforums.org/archive/index.php/t-337960.html](http://ubuntuforums.org/archive/index.php/t-337960.html)
however when i get to  sudo modprobe cx88-dvb  I get the following error

 FATAL: Error inserting cx88_dvb (/lib/modules/2.6.20-16-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

using lspci -v my device is reported as:

05:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: Compro Technology, Inc. Videomate DVB-T200
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at fbfffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>


I have also read that i do not need to worry about the drivers as they are already installed.

Whats going on??

---

### Post by HighSide on 2007-10-02
Still having problems....

I am able to create the folder /dev/dvb/adapter0, 
using sudo chmod 755 MAKEDEV-DVB.sh  
and  ./MAKEDEV-DVB.sh, 

however when i reboot the folder is missing.
I have tried sudo and gksudo but the folders are not there after rebooting.


also before i reboot and the files are lost,
using-  dmesg | grep dvb

I get ... 
[   31.563272] saa7130[0]/dvb: frontend initialization failed

has anyone got any suggestions

Thanks
Stu

---

### Post by steefjeqv on 2007-10-02
Hi,

Type this in terminal :

modprobe saa7134

or

modprobe saa7134-dvb

Greetings,
Steven

---

### Post by HighSide on 2007-10-02
Hi Steven

thanks for the quick reply

I have tried that and have copied both lines into /etc/modules

the script I have been trying is as follows...

!/bin/sh
# Create device nodes for the Linux DVB API with DVB_API_VERSION 2.
# The devices created are suitable for most current PC DVB cards,
# i.e. cards having one frontend, one demux and optionally one
# MPEG decoder.
# The script creates devices for four cards by default.

if [ -e /dev/.devfsd ]; then
        echo "It seems you are using devfs. Good!"
        exit 0
fi

# get rid of old DVB API devices; do it twice for good measure...
rm -rf /dev/ost
rm -rf /dev/ost
rm -rf /dev/dvb
rm -rf /dev/dvb

sudo mkdir /dev/dvb
sudo chmod 755 /dev/dvb

for i in `seq 0 3`; do
        echo "Creating DVB devices in /dev/dvb/adapter$i"
        mkdir /dev/dvb/adapter$i
        chmod 755 /dev/dvb/adapter$i
        mknod -m 0660 /dev/dvb/adapter$i/video0    c 212   `expr 64 \* $i + 0`
        mknod -m 0660 /dev/dvb/adapter$i/audio0    c 212   `expr 64 \* $i + 1`
        mknod -m 0660 /dev/dvb/adapter$i/frontend0 c 212   `expr 64 \* $i + 3`
        mknod -m 0660 /dev/dvb/adapter$i/demux0    c 212   `expr 64 \* $i + 4`
        mknod -m 0660 /dev/dvb/adapter$i/dvr0      c 212   `expr 64 \* $i + 5`
        mknod -m 0660 /dev/dvb/adapter$i/ca0       c 212   `expr 64 \* $i + 6`
        mknod -m 0660 /dev/dvb/adapter$i/net0      c 212   `expr 64 \* $i + 7`
        mknod -m 0660 /dev/dvb/adapter$i/osd0      c 212   `expr 64 \* $i + 8`
        chown root.video /dev/dvb/adapter$i/*
done
===============================================================================

   % chmod 755 MAKEDEV-DVB.sh
   % ./MAKEDEV-DVB.sh  


Any ideas??

Cheers
Stu

---

### Post by steefjeqv on 2007-10-02
Hi again,

I'm afraid I'm not an expert in scripting (or how to use it). 

Do you get any errors when modprobing these drivers ?

Try this in terminal :

sudo modprobe -rV saa7134-dvb

It should give you a text line like "module-init-tools version xxx".

If this works you should be okay to test your DVB card.
I always use a mediaplayer called Kaffeine to test. It recognizes DVB cards quite easily.
It's available through Synaptic or you can type the following in terminal :

sudo apt-get install kaffeine

Greetings,
Steven

---

### Post by HighSide on 2007-10-02
Hi Steven

here is the response

stuart@stuart-desktop:~$ sudo modprobe -rV saa7134-dvb
Password:
module-init-tools version 3.3-pre2

I also opened Kaffine and it says -
cannot find (file:///dev/dvb/adapter0/dvr0)

i then ran the script again, to create the folders and files

kaffine now gives the error:

Resource can not be opened (file:///dev/dvb/adapter0/dvr0)
22:16:20: xine: found input plugin : file input plugin
22:16:14: xine: found input plugin : file input plugin
22:16:07: xine: found input plugin : file input plugin
22:15:46: xine: found demuxer plugin: AVI/RIFF demux plugin
22:15:46: xine: found input plugin : file input plugin

Thanks for the help
Stu

---

### Post by steefjeqv on 2007-10-02
Hi,

Well, the driver is installed but you may have to change the rights of the resource file.

In terminal :

sudo chmod 775 /dev/dvb/adapter0/dvr0

Hopefully Kaffeine is willing to recognize your card now.

Greetings,
Steven

---

### Post by HighSide on 2007-10-02
Hi

This time i get; 

Resource can not be opened (file:///dev/dvb/adapter0/dvr0)
22:41:58: xine: found input plugin : file input plugin

The permissions for the /dev/ folder are still preventing me from making permanent changes. 

Stu

---

### Post by steefjeqv on 2007-10-02
Hi,
 

Did you check if /dev/dvb/adapter0 really exist in your filesystem ?

In terminal :

cd /dev/dvb

Then type : ls

adapter0 should then be listed.

You can also use your file manager to check this.

Greetings,
Steven

---

### Post by steefjeqv on 2007-10-02
Hi,

I think I've made a mistake in my earlier post on changing the permissions :

Try this in terminal :

sudo chmod 775  /dev/dvb/adapter0 

and then :

sudo chmod 775 /dev/video0

Sorry for that one.

Hopefully this will do the trick.

Greetings,
Steven

---

### Post by HighSide on 2007-10-03
It only exists after I run the script.

I have since found that the /dev folder is stored in RAM and therefore is not be saved on reboot. I have found the following ;

[I]come in to shell ...

open folder
/mnt
and mkdir dvb

after it write this command
mount /dev/dvb mnt/dvb

after it open
/etc/fstab
and fill the last row with your new device if you want to do it read only so write "owner" in the right place[/I]

I will give this a try later.

---

### Post by steefjeqv on 2007-10-03
Hi,

I've done a bit of research on the internet and it seems that udev doesn't recognize your card as DVB.

Therefore the needed /dev/dvb/adapter0 isn't created.

The method you suggested in your previous post may give a solution.

There may be another way creating the node /dev/dvb/adapter0 by using something called MAKEDEV. I'm going to look into that this evening (if I don't have to work late:()

I'm off to work now.

Keep me posted.

Greetings,
Steven

---

### Post by steefjeqv on 2007-10-03
Hello again,

You should be able to create the /dev/dvb/adapter0 by using MAKEDEV.

First check if your driver is active, in terminal :

sudo dmesg | grep saa7134

Type in terminal :

sudo MAKEDEV dvb

Check if /dev/dvb/adapter0 exists.

Give kaffeine a try.

If kaffeine isn't able to access your DVB card, try to chmod the two directories mentioned in my previous post. 

Hope this helps.

Greetings,
Steven

---

### Post by HighSide on 2007-10-03
Steven 

Would you post the contents of your udev.conf file please.
Mine appears to be empty.

Apparently Udev  creates the folders for the devices on boot.
It looks in the .conf file for the location of the rules. I guess mine cant find any rules

[I]# udev.conf

# The initial syslog(3) priority: "err", "info", "debug" or its
# numerical equivalent. For runtime debugging, the daemons internal
# state can be changed with: "udevcontrol log_priority=<value>".
udev_log="err"[/I]

I tried my previous post and was unable to mount a /dev node!!

---

### Post by steefjeqv on 2007-10-03
Hello Stu,

I'm using two dvb-cards (one saa7164 and one cx2388) on a Debian based system and my udev.conf is nearly identical to yours.

I've also added the udev.rules file which mentions dvb devices.

I think my previous post may have crossed yours. 
Did you already try the MAKEDEV method ?

Greetings,
Steven

---

### Post by HighSide on 2007-10-03
Thanks for the files.

I tried MAKEDEV dvb, here is what I got;

stuart@stuart-desktop:/dev$ sudo MAKEDEV dvb
udev active, devices will be created in /dev/.static/dev/

I can see the adapters if I navigate to the /dev/.static/dev/dvb folder,
but i cannot see them in the file browser. is the .static folder hidden?

Also, 
stuart@stuart-desktop:/dev$ sudo dmesg | grep saa7134
[   31.751916] input: saa7134 IR (Compro Videomate DV as /class/input/input4
[   32.485616] saa7134 ALSA driver for DMA sound loaded

but then i noticed the chip set is now listed as saa7130

stuart@stuart-desktop:/dev$ sudo dmesg | grep saa7130
[   31.751730] saa7130/34: v4l2 driver version 0.2.14 loaded
[   31.751823] saa7130[0]: found at 0000:05:06.0, rev: 1, irq: 16, latency: 64, mmio: 0xfbfffc00
[   31.751830] saa7130[0]: subsystem: 185b:c901, board: Compro Videomate DVB-T200 [card=71,insmod option]
[   31.751840] saa7130[0]: board init: gpio is 843f00
[   31.896129] saa7130[0]: i2c eeprom 00: 5b 18 01 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   31.896138] saa7130[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   31.896145] saa7130[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 88 ff ff ff ff
[   31.896152] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.896158] saa7130[0]: i2c eeprom 40: ff d5 00 c4 86 1e ff ff ff ff ff ff ff ff ff ff
[   31.896164] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   31.896171] saa7130[0]: i2c eeprom 60: 30 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   31.896177] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.109086] tuner 1-0062: chip found @ 0xc4 (saa7130[0])
[   32.471396] tuner 1-0068: chip found @ 0xd0 (saa7130[0])
[   32.472625] saa7130[0]: registered device video0 [v4l2]
[   32.472655] saa7130[0]: registered device vbi0
[   32.485652] saa7130[0]/alsa: saa7130[0] at 0xfbfffc00 irq 16 registered as card -2
[   32.536383] saa7130[0]/dvb: frontend initialization failed

Is this nothing to worry about?

---

### Post by steefjeqv on 2007-10-03
Hello Stu,

I've just checked and .static is a hidden file.
You can make your file manager show these files. 
In your file manager menu click on the "image" tab (3d tab from the left),  then select "show hidden files".

The driver should be ok. These 2 chipsets are very similar.
Notice the first line in dmesg where it says saa7130/34. This indicates the driver is used for both chipsets.
Your dmesg looks good, except for the last line "frontend initialization failed". 
It also lists your card as a T200 in stead off T220.

I've had this problem " frontend initialization" myself using a Terratec Cinergy 1200 DVB-T.
The solution for that particular card was to add a firmware file which was needed for the tuner. It was recognized  and I could even scan for channels but there was no channel lock.
After adding the firmware, the channels did lock.

Some questions :

After MAKEDEV, do you get a directory in /dev/dvb/adapter0 ?

I suppose the dmesg has been done after you gave the MAKEDEV command ?

Did you try Kaffeine ?

I'm going to sleep in a few minutes, but keep me posted.


Greetings,
Steven

---

### Post by steefjeqv on 2007-10-03
Just one more thing, 

If you restarted the computer, first do the MAKEDEV command, then untar the attached file in your /lib/firmware directory. 

It contains firmware, some of which may be needed for your card to function.

I think you're getting close to a functioning DVB card.

Greetings + good night,
Steven

---

### Post by HighSide on 2007-10-04
Hi Steven

Yea, I think its getting close!

I followed you instructions and tried kaffine  but had the same errors
but I then tried gxine and gave me a different error saying the was no channels.conf was found.

I also get the same saa7130[0]/dvb: frontend initialization failed error, with the firmware files in /lib/
firmware

*After MAKEDEV, do you get a directory in /dev/dvb/adapter0 ?*
No but I get /dev/.static/dev/dvb/adapter0

*I suppose the dmesg has been done after you gave the MAKEDEV command ?*
Yes it was

Any ideas? Do i need to do anything else to the firmware files? ie install?

---

### Post by steefjeqv on 2007-10-04
Hello Stu,

Concerning the firmware :
Do you have the cd-rom which contains the (windows) drivers.
There should be a file on it called xxxxxx.bin (for example tda10064.bin).
This is the firmware which you may need to put in /lib/firmware.
If you're using this card on a Microsoft system you may find the xxxxx.bin file in the Programs folder.

Concerning the channels.conf :
You can create one using dvb-utils.

In terminal :
sudo apt-get install dvb-utils

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Hannington > channels.conf

I suppose you'll have to replace "uk-Hannington" with your region.
Just navigate to the dvb-t folder and choose the one you need.
Then copy the channels.conf to /home/Stuart/.xine.

I'm going to have an "early" night now (got a bit of a cold).

Keep me posted.

Greetings,
Steven

---

### Post by HighSide on 2007-10-14
Hi Steven,

Sorry for the delay, I was away last week.

I did some more research last week and I think I am out for luck on this one. I believe that my card is not supported yet, although it is similar to the T200, it has a slightly different chipset. 

I now have to look for another card, I am not sure which to buy (try!).  I was struggling to find one that would fit in my low-profile case. I would also prefer not to use a USB version, if possible. Any ideas?

Thanks for all the help.

---

### Post by steefjeqv on 2007-10-14
Hi Stu,

It's a pity that this card won't work with Ubuntu (for the moment).
Maybe the next version of the LinuxTV driver will add support for it.

These ones should work with a recent kernel (and they're low profile) :

[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_777_%28A16AR%29]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_777_%28A16AR%29")

[http://www.linuxtv.org/wiki/index.php/TwinhanDTV_Mini_Ter]("http://www.linuxtv.org/wiki/index.php/TwinhanDTV_Mini_Ter")

As you've noticed, the links are from the linuxtv Wiki.
There maybe other low profile cards mentioned here.

I'd go for the Avermedia DVB-T 777.
It's a recent design so it should give good quality TV, and it works with Feisty.

Greetings,
Steven

---

### Post by HighSide on 2007-10-22
Hi Steven,

I bought a new card and have started a new thread as this one doesnt work out the box either!!! But it does work apparently.
[http://ubuntuforums.org/showthread.php?t=587056&highlight=dvb](http://ubuntuforums.org/showthread.php?t=587056&highlight=dvb)

Its an AVerMedia AVerTV Super 007, the only low profile card I could find here in the UK.

I think I have learned my lesson though. 'To seriously check my hardware before I buy!'

Thanks again,
Stu

---

