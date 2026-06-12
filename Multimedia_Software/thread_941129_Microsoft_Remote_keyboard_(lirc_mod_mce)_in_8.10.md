---
title: "Microsoft Remote keyboard (lirc_mod_mce) in 8.10"
date: 2008-10-07
forum: Multimedia Software
---

### Post by browneej on 2008-10-07
I have a Microsoft MCE 2005 remote keyboard I am attempting to use with mythbuntu.  The remote control buttons are currently working under lirc_mceusb2, but the keyboard and mouse buttons are not.  When I use irrecord I am able to detect all the keyboard buttons, but I don't know how to translate the resulting file into something usefull.  Instead, II am attempting to install lirc_mod_mce ([http://mod-mce.sourceforge.net/](http://mod-mce.sourceforge.net/)) in Intrepid beta (8.10) per these instructions:

[http://ubuntuforums.org/showthread.php?t=466997](http://ubuntuforums.org/showthread.php?t=466997)
[http://www.backports.ubuntuforums.org/showthread.php?t=592057&highlight=lirc_mod_mce](http://www.backports.ubuntuforums.org/showthread.php?t=592057&highlight=lirc_mod_mce)
[http://www.backports.ubuntuforums.org/showthread.php?p=4253958](http://www.backports.ubuntuforums.org/showthread.php?p=4253958)
[https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)
[http://www.mythtv.org/wiki/index.php/MCE_Remote](http://www.mythtv.org/wiki/index.php/MCE_Remote)

Specifically (from bkmiller):

1. Turn off lirc.
2. Followed this guide [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) to get the lirc_mceusb2 drivers built. I stopped following the guide at "Create a lircd.conf". I used the lircd.conf and lircrc files located here: [http://www.hauppauge.co.uk/board/showthread.php?t=8048](http://www.hauppauge.co.uk/board/showthread.php?t=8048).
3. Download the lirc_mod_mce source from [http://mod-mce.sourceforge.net/](http://mod-mce.sourceforge.net/).
4. Copy over /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.h into the directory with your lirc_mod_mce source files in. 
5. Go to the source for lirc_mod_mce and type 'make' to build the module.
6. Type 'insmod lirc_mod_mce.ko' to test the module to see if it inserts.
7. If all goes well in 6, then copy lirc_mod_mce.ko to /lib/modules/$YOURKERNEL/misc
8. depmod -a
9. Restart, unplug & plug back in, or modprobe lirc_mod_mce.
10. You probably need to update your /etc/lirc/hardware.conf, and then start lirc and test with IRW. The mouse and keyboard will be working at this point without LIRC on.

When I attempt step 5 with the Makefile that comes with the tarball, I receive the following error:

family@MediaCenter:/usr/src/lirc-0.8.3/drivers/lirc_mod_mce$ sudo make
make -C /lib/modules/2.6.27-6-generic/build SUBDIRS=/usr/src/lirc-0.8.3/drivers/lirc_mod_mce modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-6-generic'
  CC [M]  /usr/src/lirc-0.8.3/drivers/lirc_mod_mce/lirc_mod_mce.o
/usr/src/lirc-0.8.3/drivers/lirc_mod_mce/lirc_mod_mce.c: In function &#8216;usb_remote_probe&#8217;:
/usr/src/lirc-0.8.3/drivers/lirc_mod_mce/lirc_mod_mce.c:1301: error: &#8216;struct input_dev&#8217; has no member named &#8216;cdev&#8217;
make[2]: *** [/usr/src/lirc-0.8.3/drivers/lirc_mod_mce/lirc_mod_mce.o] Error 1
make[1]: *** [_module_/usr/src/lirc-0.8.3/drivers/lirc_mod_mce] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-6-generic'
make: *** [default] Error 2

When I do make after copying the Makefile from /usr/src/lirc-0.8.3 down into /usr/src/lirc-0.8.3/lirc_mod_mce, I get the following:
family@MediaCenter:/usr/src/lirc-0.8.3/drivers/lirc_mod_mce$ sudo make
make[1]: Entering directory `/usr/src/lirc-0.8.3/drivers/lirc_mod_mce'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/usr/src/lirc-0.8.3/drivers/lirc_mod_mce'

Does anyone have any ideas, or know what I'm doing wrong?  After reading through all the different posts on how to install lirc modules, I really don't understand how ubuntu manages modules, all the different places the parts are stored, or the DKMS system.  With lirc and this IR keyboard, I don't understand the divisions of labor between the lirc_mod_mce.ko module and the lirc.conf file.  

Thanks in advance for the help.  Does anyone know why this keyboard/remote hasn't been mainlined with the other mce remotes?

---

### Post by ruminant1 on 2008-12-20
Not claiming to understand the underlying structure very well, I was able to (I think) figure out what was going on.  It looks like cdev was deprecated some time ago and it must have been finally deleted in Intrepid.  

If you replace line 1301 in lirc_mod_mce.c:

 input_dev->cdev.dev = &dev->dev

with:

 input_dev->dev.parent = &dev->dev;

it compiles and runs just fine (typing this from my mce keyboard). 


As to why the keyboard isn't natively supported while ubuntu supports the remote, I've scratched my head on that one too.

---

### Post by ruminant1 on 2008-12-20
Two more things you may want to know (realized while cross-posting)

First, I usually delete lirc_mod_mceusb2 from /etc/lirc/hardware.conf and replace it with lirc_mod_mce. The two packages historically conflicted, though I haven't confirmed that's the case under Intrepid.

Second, the instructions tell you to copy the kernel module into /lib/modules/$YOURKERNEL/misc, but that directory didn't exist so the copy turned my module into a file called 'misc'. This caused some serious head scratching when I couldn't load a module I just created.

I put it in, /lib/modules/`uname -r`/updates/dkms , but you can mkdir misc if you like instead.

---

### Post by ruminant1 on 2008-12-20
OK, I just rebooted and discovered that lirc_mod_mce and lirc_mceusb2 still don't get along.  You have to blacklist lirc_mceusb2 (add "blacklist lirc_mceusb2" to /etc/modprobe.d/blacklist) in addition to replacing it in  /etc/lirc/hardware.conf

---

### Post by BroadArrow on 2009-01-08
How have you been getting on? Is it still working OK?

I followed the MCE Remote instructions on the Myth TV website for a [install from a CVS snapshot]("http://www.mythtv.org/wiki/index.php/MCE_Remote#Download_a_lirc_CVS_SnapShot") as I hit the problem described in the guide.

My remote now seems to be working OK but only things working on the keyboard are the clones of the remote buttons (play, stop, volume, &c). None of the alphabetic keypad works. Is that the same problem you had?

---

### Post by BroadArrow on 2009-01-16
I've managed to get my keyboard working following the above instructions --although it took a few attempts to get everything right! It really shouldn't be this hard!

Anyway, I have one outstanding issue with periodic repeat key presses. They show up in irw but the remote receiver light defintely isn't showing them so I think it must be a problem with my config rather than the hardware?

(Yes, I've checked the batteries!)

Any ideas?

---

### Post by mikeklein on 2009-01-25
How do you get around dmesg error:

```
[  435.472898] lirc_mod_mce: Unknown symbol lirc_get_pdata
[  435.472988] lirc_mod_mce: Unknown symbol lirc_unregister_plugin
[  435.473312] lirc_mod_mce: Unknown symbol lirc_register_plugin
```

From poster of last year a link is given to build lirc_mceusb2 (already built) but link is bad.

I have pulled lirc and lirc-modules-src to rebuild for custom iguanair transceiver.

---

### Post by big_red_23 on 2009-02-04
i've been playing around with this driver for a week now and i've found a kludge: the key repeat issue can be worked around by stopping lirc, removing the module, then restarting lirc. Here's a script.

lirc_tweak.sh
```

#!/bin/sh
/etc/init.d/lirc stop	
modprobe -r lirc_mod_mce
modprobe -r lirc_mceusb2
/etc/init.d/lirc start

```

This script needs to be run in a terminal as root after the desktop has come up, unfortunately the shift key seems to stick still and a few keystrokes are missed if you type too fast.

The only part of /etc/lirc/hardware.conf I modified was the remote bit
```

REMOTE="Custom"
REMOTE_MODULES="lirc_mod_mce"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes"
REMOTE_LIRCD_ARGS=""

```

btw: i'm running mythbuntu 8.10.

---

### Post by BroadArrow on 2009-03-04
> **BroadArrow said:**
> My remote now seems to be working OK but only things working on the keyboard are the clones of the remote buttons (play, stop, volume, &c). None of the alphabetic keypad works. Is that the same problem you had?

Has anyone found a solution to this? 

I've got the keyboard working (except the clones of the remote buttons) using lirc_mod_mce but really need the remote (and the clones on the keyboard) working as I'm using the box as a media centre.

I can't seem to find a solution or HowTo anywhere...

---

### Post by ruminant1 on 2009-03-12
> My remote now seems to be working OK but only things working on the keyboard are the clones of the remote buttons (play, stop, volume, &c). None of the alphabetic keypad works. Is that the same problem you had?


I think this happens when lirc_mceusb2 is running.

Try:

[FONT="Courier New"]sudo modprobe -r lirc_mceusb2[/FONT]

---

### Post by mike909 on 2009-04-10
> **ruminant1 said:**
> 
First, I usually delete lirc_mod_mceusb2 from /etc/lirc/hardware.conf and replace it with lirc_mod_mce. The two packages historically conflicted, 
I don't see lirc_mod_mceusb2 in /etc/lirc/hardware.conf. This process has caused my system to not boot (crashes during lirc loading). 
Link 2 in Step 2 doesn't work. 
I'm starting with a working remote (but not keyboard). Is there any way someone could fix the links, or explain this in a more understandable way?
Thanks.

---

### Post by north_pole on 2009-04-26
Anyone who have suceeded with this in Jaunty Jackalope 9.04?

---

### Post by mike909 on 2009-04-27
I too have upgraded to 9.04, though i doubt it will be any easier to get the mce keyboard working.

---

### Post by north_pole on 2009-04-29
I've tried to follow these german instructions, which were the best i could find on the internet right now: [http://www.chris-klein.de/2008/02/01/microsoft-mce-tastatur-vs-ubuntu-gutsy-lirc_mod_mce/]("http://http//www.chris-klein.de/2008/02/01/microsoft-mce-tastatur-vs-ubuntu-gutsy-lirc_mod_mce/")
 
The first steps about the configuration of lirc-modules-source were not needed anymore because they were now automated, but I had to change line 1301 ("input_dev->dev.parent = &dev->dev;" instead of "input_dev->cdev.dev = &dev->dev;") in the "lirc_mod_mce.c" file in order to get the "sudo make" command executed. Then it worked well until I tried to run the insmod command, which said "-1 file exists". What's wrong?

---

### Post by mike909 on 2009-04-29
corrected the link...
[http://www.chris-klein.de/2008/02/01/microsoft-mce-tastatur-vs-ubuntu-gutsy-lirc_mod_mce/]("http://www.chris-klein.de/2008/02/01/microsoft-mce-tastatur-vs-ubuntu-gutsy-lirc_mod_mce/")

---

### Post by north_pole on 2009-04-29
YEEES! Finally I've made it all work. Here's an HOW-TO for Ubuntu Jaunty Jackalope 9.04:
 
1. Install some required modules with
 
```
$ sudo apt-get install lirc lirc-modules-source module-assistant 
```2. and then run the following command
 
```
$ sudo dpkg-reconfigure lirc-modules-source 
```3. Open the the hardware.conf file with this command
 
```
$ sudo gedit /etc/lirc/hardware.conf 
```4. Change two of the lines so they look like this:
 
```
REMOTE_MODULES="lirc_mod_mce"
 
LOAD_MODULES="true" 
```Save and exit.
 
5. Run the following commands
 
```
$ sudo m-a update,prepare
 
$ sudo m-a clean lirc
 
$ sudo m-a a-i -f lirc    (if this one fails, choose "skip and continue with the next operation")
 
$ sudo depmod -a
```6. Download and unpack the attached files "lircd.conf" and "lircrc". Put them in /etc/lirc.
 
7. Now download the lirc_mod_mce v.0.1.5 file from [http://sourceforge.net/project/showf...kage_id=203215]("http://sourceforge.net/project/showfiles.php?group_id=171688&package_id=203215"), but be sure to download version 0.1.5 and NOT the v0.2.0. The later one has the famous "keypress repeats forever"-bug and should be avoided. Unpack the archive on e.g. your desktop.
 
8. Replace the "lirc_dev.h" file with the one located in "/usr/src/%YOUR_LIRC_VERSION%/drivers/lirc_dev"
 
9. In the file named "lirc_mod_mce.c", you have to change one of the lines:
 
```
input_dev->cdev.dev = &dev->dev;
 
to
 
input_dev->dev.parent = &dev->dev; 
```Save and exit.
 
10. Now, execute
 
```
$ sudo make 
```11. Create a new directory in "/lib/modules/%YOUR_CURRENT_KERNEL%" and name it "misc".
 
12. Some extra files have been created in the "lirc_mod_mce" directory.
One of them is "lirc_mod_mce.ko". Copy it to the new directory you just created.
 
13. Run
 
```
sudo depmod -a
 
modprobe lirc_mod_mce 
```14. At last we have to blacklist the "lirc_mceusb2" module. Otherwise it will
interfere with the "lirc_mod_mce" one and make all of our work useless. Execute:
 
```
$ sudo gedit /etc/modprobe.d/blacklist.conf 
```and add the line
 
```
blacklist lirc_mceusb2
```on an own row e.g. in the bottom of the file. Save and close.
 
15. Reboot
 
16. And VOILA! Your MCE Keyboard should be working!

---

### Post by mike909 on 2009-04-29
north,
Congrats. I look forward to giving this a shot (much of it looks similiar to steps Ive tried already). Hopefully it continues to work for you. 
I did have one clarification request:
> 8. Now copy the file "lirc_dev.h" located in "/usr/src/%YOUR_LIRC_VERSION%/drivers/lirc_dev" to the map you've just extracted ("lirc_mod_mce") and swap the existing file.
> 11. Create a new map in "/lib/modules/%YOUR_CURRENT_KERNEL%" and name it "misc".
When you use the term "map" you are referring to a directory, correct? For example, just replace the file in the extracted "lirc_mod" directory, with the one from the "/usr/src/%YOUR_LIRC_VERSION%/drivers/lirc_dev"

Thanks for sharing...will post back with my results.

---

### Post by mike909 on 2009-04-30
Success! North Pole, thank you for sharing.
I only have this to add...for those using "mythbuntu 9.04" distro be aware of the following:
step 5: fails on sudo m-a a-i -f lirc
says: 
> Module-assistant, interactive mode
Build of the package lirc-modules-source failed! How do you wish to proceed?
choices are:
view...examine the build log file
continue...skip and continue with the next operation
stop...stop processing the build commands.

So I hit "view" and it sais the file is "/var/chace/modass/lirc-modules-source.buildlog.2" but that file does not exist.
ls /var/cache/modass/:
mike@mike-desktop:~$ ls /var/cache/modass/
alsa-source.avail_version
bcm5700-source.avail_version
cdfs-src.avail_version
comedi-source.avail_version
cpad-kernel-source.avail_version
device3dfx-source.avail_version
drbd0.7-module-source.avail_version
em8300-source.avail_version
exmap-modules-source.avail_version
fglrx-kernel-source.avail_version
gpib-modules-source.avail_version
ivtv-source.avail_version
kqemu-source.avail_version
linux-wlan-ng-source.avail_version
lirc-modules-source.avail_version
lirc-modules-source.buildlog.2.6.28-11-generic.1241054121
lirc-modules-source.buildlog.2.6.28-11-generic.1241054326
lirc-modules-source.cur_version
loop-aes-source.avail_version
mga-vid-source.avail_version
openafs-modules-source.avail_version
openswan-modules-source.avail_version
qc-usb-source.avail_version
rt2400-source.avail_version
rt2500-source.avail_version
rt2570-source.avail_version
rtai-source.apt_policy
rtai-source.avail_version
sl-modem-source.avail_version
squashfs-source.avail_version
sysprof-module-source.avail_version
zaptel-source.avail_version

Just hit "continue" and follow the rest of north_pole's steps and it will work.

Oh, also north_pole, are you recieving any segfaults like the following? I am getting the following in kern.log:
> Apr 29 21:14:58 mike-desktop kernel: [ 9542.722620] xfce4-keyboard-[11193]: segfault at 18 ip b7cc4fca sp bfd52970 error 4 in libgtk-x11-2.0.so.0.1600.1[b7ab2000+3a9000]

Keyboard still works though...and i'm happy about that.

---

### Post by north_pole on 2009-04-30
>  
When you use the term "map" you are referring to a directory, correct? For example, just replace the file in the extracted "lirc_mod" directory, with the one from the "/usr/src/%YOUR_LIRC_VERSION%/drivers/lirc_dev"

I've now edited the post. "Map" is a false friend swedish<->english.
 
>  
step 5: fails on sudo m-a a-i -f lirc

I got that error too, but apparently it didn't matter. Maybe the whole command is unnecessary?
 
>  
Oh, also north_pole, are you recieving any segfaults like the following? I am getting the following in kern.log:

I haven't watched my log, but you seem to use XFCE instead of GNOME, which may be the problem?

---

### Post by mike909 on 2009-04-30
XFCE is the desktop environment of the Mythbuntu distro. The segfaults don't seem to matter, as the keyboard still works.

---

### Post by GuiGuy on 2009-07-19
> **north_pole said:**
> YEEES! Finally I've made it all work. Here's an HOW-TO for Ubuntu Jaunty Jackalope 9.04:
<snip>
16. And VOILA! Your MCE Keyboard should be working!

Many thanks. It worked a treat.

However, I'm finding that more often than not the last key pressed on my MCE keyboard keeps autorepeating even after being released :(

Any ideas?

UPDATE: Nevermind, I see what I did... :(

---

### Post by adambomb42x on 2009-07-28
Help!
Warning: This user is a linux noob.

I followed the instructions with on my Mythbuntu 9.04 and now when I boot with the IR receiver plugged in I get an error when trying to "Load hardware drivers". It shows "udevd-event [847]; '/sbin/modprobe-b usb: (bunch of characters) abnormal exit". I checked my boot log but did not find the error in it. Please help.

---

### Post by Studio37 on 2009-09-06
Hi All ;)

I've do all but I can't use my Microsoft Remote Keyboard on my Ubuntu 9.04.
Receiver is see on lsusb : Philips eHome ...
module is up but not used : lirc_mod__mce 0
My receiver blink red when I press key ... but nothing on my screen.

All run on a Windows XP computer :s

Any Idea ?

Thx by advance ;)

---

### Post by ryanolf on 2009-10-14
Compilation of lirc_mod_mce seems to be broken in 9.10. Can anyone else verify this? See my new thread: [http://ubuntuforums.org/showthread.php?t=1290902](http://ubuntuforums.org/showthread.php?t=1290902)

---

### Post by java-jim on 2009-11-04
Hi ryanolf,

got the same error in 9.10 like your post in: [http://ubuntuforums.org/showthread.php?t=1290902](http://ubuntuforums.org/showthread.php?t=1290902)

---

### Post by ryanolf on 2009-11-25
Has anyone gotten lirc_mod_mce to work in Karmic 9.10?

---

### Post by leeko on 2009-11-27
not as far as I can tell. I have the same problem...

Lee

---

### Post by GuiGuy on 2010-02-23
> **ryanolf said:**
> Has anyone gotten lirc_mod_mce to work in Karmic 9.10?

[This thread]("http://swiss.ubuntuforums.org/showthread.php?t=661795&page=4") may help, particularly wunschkandidat13 posts towards the end of the current thread. 

I haven't tried it yet but will this coming weekend.

Cheers

---

### Post by ryanolf on 2010-03-01
That thread almost solves my problem. Everything "works," though my IR receiver (TopSeed) is not supported by 0.1.5, and 0.2.1 makes the keys behave as if they are held down, even when they are not. Anyone know how to add the TopSeed devices to 0.1.5 or work around the infinite repeat bug in 0.2.1?

---

### Post by jon47 on 2010-07-23
> **ryanolf said:**
> Has anyone gotten lirc_mod_mce to work in Karmic 9.10?

Yes :-)  and in lucid, 10.04

see [http://wwww.ubuntuforums.org/showthread.php?p=9628326#post9628326](http://wwww.ubuntuforums.org/showthread.php?p=9628326#post9628326)

(ok, yes, I'm cross-posting all over the place, but I'm feeling pleased with myself because I might finally be able to put something back into the community for once ... ;-))

Cheers
Jon

---

