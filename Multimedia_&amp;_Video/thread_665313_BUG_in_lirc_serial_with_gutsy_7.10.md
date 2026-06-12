---
title: "BUG in lirc_serial with gutsy 7.10 ??"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by kdeiss on 2008-01-12
I'am using gutsy 7.10 and I think there is a bug in lirc_serial in combination with 2.6.22-14-generic kernel.

I started with

lirc-0.8.2-0ubuntu8 from universe
and
lirc-modules-source from universe

Modul compilation worked fine with module-assistant, but after loading the modules and running lircd irw/irrecord don't work, similar to the problems other user reported here:

[http://ubuntuforums.org/showthread.php?t=662991&highlight=lirc_serial](http://ubuntuforums.org/showthread.php?t=662991&highlight=lirc_serial)
[http://ubuntuforums.org/showthread.php?t=600239&highlight=lirc_serial](http://ubuntuforums.org/showthread.php?t=600239&highlight=lirc_serial)
[http://ubuntuforums.org/showthread.php?t=663952&highlight=lirc](http://ubuntuforums.org/showthread.php?t=663952&highlight=lirc)

In short terms:

irw starts, but pressing any key on the remote does not show anything!

irrecord -d /dev/lirc0 /tmp/lirc.test

If I now press any key on the remote, irrecord immediatly stops:

irrecord: no data for 10 secs, aborting
irrecord: gap not found, can't continue


Next I got the source for lirc-0.8.2-0ubuntu8, and built my own lirc-modules-source. Modul compilation worked fine, but same result in running applications.

Next I loaded lirc_0.8.3~pre1-0ubuntu5.dsc (with dget) from [http://archive.ubuntu.com/ubuntu/pool/main/l/lirc/](http://archive.ubuntu.com/ubuntu/pool/main/l/lirc/), Compilation and Modul compilation again without any problem, but same result in running applications.

Next I wrote a small script to use lirc_serial's parameters systematically, i.e. the type parameter:

```


##################################################################
killall -9 lircmd
sleep 1
killall -9 lircd
ps -e | grep lirc


setserial /dev/ttyS0 uart none
setserial /dev/ttyS1 uart none

modprobe -r lirc_serial
sleep 1
echo lirc_serial unloaded ?  - press any key
lsmod | grep lirc_serial
read x

modprobe lirc_serial io=0x3f8 irq=4 debug=1 type=1
#modprobe lirc_serial io=0x2f8 irq=3 debug=1 type=4
sleep 1
echo lirc_serial loaded ?  - press any key
lsmod | grep lirc_serial
ps -e | grep lirc
read x

#dmesg

#driver load seems to activate the lircd in daemon mode !
killall -9 lircd
sleep 1

echo lircd -n --driver=default --device=/dev/lirc0
lircd -n --driver=default --device=/dev/lirc0
##################################################################


```

I checked out nearly all possible combinations, nothing brings a useable result.

Next I've connected annother serial lirc transmitter to ttyS0 and did all tests again, same result: nothing !

Next I've connected a second hard disk to the machine (via epia MIII 12000), there I had installed a debian system with

lirc 0.8.0-pre4 0
2.6.19

This works fine on both ports (ttyS0 and ttyS1), so I think that the hardware is OK.

This is my first post here, I have to apologize if there is something missing. Please let me know.

Klaus

---

### Post by kdeiss on 2008-01-12
additional information

Next I've compiled older source package lirc_0.8.1+cvs20070310-0ubuntu2.dsc. 

Directly after compiling and installing these package (and of course its corresponding kernel modules) it is possible to run irw succesfully. But after some keypresses (maybe 10-15) it stops processing. Removing all from memory and restarting lirc daemon does not help, it does not come back. 

Next I removed all patches from lirc_0.8.1, building again, installing again ....
Same behaviour: it runs exactly 1x !!!

strange very strange .....

klaus

---

### Post by kdeiss on 2008-01-12
Next and finally I updated kernel to 2.6.24 from hardys repository. With this kernel it is only possible to use lirc_0.8.3 (older versions fail during module compilation).

But also no luck with this kernel, irw does not show up any remote event. 

At this point I don't have any idea what I could change to bring my serial lirc to work. 

klaus

---

### Post by RawMustard on 2008-01-12
I think lirc is completely broken in gutsy, I can't even get it to install correctly.  I've been stuffing around with it for the last 3 hours and can't even get gutsy to build the modules :(  Gutsy is becoming a huge pain in the butt!

---

### Post by kdeiss on 2008-01-12
> **RawMustard said:**
> I think lirc is completely broken in gutsy, I can't even get it to install correctly.  I've been stuffing around with it for the last 3 hours and can't even get gutsy to build the modules :(  Gutsy is becoming a huge pain in the butt!

I'am not sure if it is totally broken - on my side I don't have any problem to compile and install it. And: it's running (ps -e), but it does not act as it should ....

Maybe you've got annother problem.

klaus

---

### Post by WhyWontThisWork on 2008-01-12
any luck? when i run irrecord it tells me 

```

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```
-J

---

### Post by kdeiss on 2008-01-12
> **WhyWontThisWork said:**
> any luck? when i run irrecord it tells me 

```

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```
-J

a) try with /dev/lirc0

b) if this does not help try to kill the lircmd before running irrecord.

klaus

---

### Post by WhyWontThisWork on 2008-01-12
no luck, under dev theres only those devices and useing that it didn't work...

```

J:~$ ls /dev/l*
/dev/lircd  /dev/log  /dev/loop0  /dev/lp0

```

```


J@myth:~$ irrecord -d /dev/lircd
irrecord: invalid argument count
J@mythR:~$ irrecord -d /dev/lircd ~\lirc

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not connect to unix socket /dev/lircd
irrecord: default_init(): Connection refused
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
##TIRED TO KILL HERE, I think it was the right way to kill it anyway...##
J@myth:~$ lircmd
lircmd: could not connect to socket
lircmd: Connection refused
J@myth:~$ sudo lircmd
[sudo] password
lircmd: could not connect to socket
lircmd: Connection refused
J@mythR:~$



```

---

### Post by kdeiss on 2008-01-13
@whywontthiswork

I think lirc isn't configured as it should. Which kernel modul did you choose ? (serial, sir, atisubetc etc?)

Did you check this document: [https://help.ubuntu.com/community/InstallLirc/Gutsy?highlight=%28lirc%29](https://help.ubuntu.com/community/InstallLirc/Gutsy?highlight=%28lirc%29) ?

You have to provide this information to /etc/lirc/lirc-modules-source.conf BEFORE you build the modules. Try to load the kernel-module "by hand" (look at my script above).

Check out if all is loaded fine with:

ps -e | grep lirc
lsmod | grep lirc

Post the output.

Klaus

---

### Post by kdeiss on 2008-01-13
I think now it is 99% a bug in 2.6.22/2.6.24 kernel.
I've installed feisty (7.04)  with 2.6.20 Kernel, and lirc is running much or less out of the box, same hardware !! Maybe it depends on specific hardware ....

I will report a bug in launchpad

klaus

---

### Post by pete-woods on 2008-01-13
I think that's a good idea. I had no trouble setting mine up in Feisty at all (even though it requires compiling kernel modules). In Gutsy no matter what I try I have no luck.

Update: When I was running Feisty I had installed kernel 2.6.22 from the Gutsy repository for driver support for my DVB stick and Lirc still worked like under 2.6.20.

---

### Post by elp99jcm on 2008-01-17
I am having all the same problems mentioned in this post. I have configured lirc to work with a homebrew transmitter several times in the past and it worked fine. As soon as I upgraded to Gutsy it stopped working. 

I have freshly reinstalled mythbuntu 7.10 and setup the IR as I did before (I actually have two instances of lirc, one for the lirc_pvr150 and one for lirc_serial - the blaster on the pvr150 does not contain codes for my remote).

Receive works fine. Transmit appears to work (I have optical LED in series with IR LED and this flashes) but the digibox will not change channel.

I have read in other posts that you need to re-record the remote and generate a new lircd.conf but when I try to do this I have the same problems as in the first post.

Has anyone got anywhere with this?

---

### Post by thebazilian on 2008-01-23
[CENTER]**Lirc Steps with serial receiver**[/CENTER]

Hi, had a lot of problems getting this to work also but finally cracked it with help from this forum.  Thanx to:
kdeiss
pete-woods
Alecj

Got in all kind of kerfuffle using source code and repository stuff.
Finally worked using repositories with fresh install of GUTSY.
These are my notes...

1) Install software (need lirc, lirc-x, setserial, dialog)
sudo apt-get install lirc lirc-x setserial dialog
	[lirc=remote s/w, lirc-x=graphical output for mode2 ]			
	[setserial lets you release serial port from system]

(mode2 irrecord are included with lirc)
(xmode2 is included with lirc-x)

Stop the lircd daemon if started
sudo /etc/init.d/lirc stop

2) Prepare and test serial port IR receiver in serial port.

sudo setserial /dev/ttyS0 uart none		
	[release serial port from system]
sudo update-modules
sudo depmod -ae
sudo modprobe lirc_serial **_[U][COLOR="Orange"]type=4[/COLOR]_[/U]**
sudo modprobe lirc_dev

lsmod | grep lirc
	lirc_serial            15620  0 
	lirc_dev               15860  1 lirc_serial

start lirc daemon
sudo /usr/sbin/lircd -d /dev/lirc0

sudo xmode2 -d /dev/lirc0			
	[start graphical display of IR reception]

Point IR remote ([COLOR="Orange"]any[/COLOR] IR remote) at receiver and press buttons
Should see waveforms displayed in graphical window


3) Record button presses for your remote control 	
	[[COLOR="Orange"]do not rely on **any** downloaded lircd.conf files[/COLOR]]

sudo irrecord -d /dev/lirc0 tempfile.conf	
	[follow interactive instructions]
Copy/paste information from tempfile.conf to /etc/lirc/lircd.conf


4)  IRW
This seems to require the [COLOR="Orange"]CORRECT[/COLOR] lircd.conf file for your remote and prints to screen the codes in lircd.conf that correspond to the buttons pressed on your remote.

I found a substantial difference from the pre loaded / downloaded files and what I got from irrecord.
5) Misc
hardware.conf		Seems not to matter what is placed inside this file.
lircd.conf			Best to record own file with irrecord.

Background Info:
Been using Linux/Ubuntu for a few years - still a bit of a numpty.
Hardware used successfully with lirc:
IBM X20 Laptop
Various Dell PCs GX270/GX260.
MythTV.

---

### Post by pete-woods on 2008-01-31
I've tried a fresh install of Hardy Alpha 3 now. The setup has improved (it does the setserial stuff for you), but it still doesn't work :(

---

### Post by elp99jcm on 2008-01-31
Right, I have a serial transmitter working now in 7.10. I hope it can solve some of the problems listed on this forum.

I started with a fresh install of mythbuntu 7.10 for ia64. 

I have a pvr-150 card and use the ir receiver from this card. I also have a homebrew serial ir transmitter (of the very simple resistor, IR diode, diode type, with an optical diode in series with ir diode to see when it flashes).

I followed the guide here to get lirc up and running for the two devices.
[https://help.ubuntu.com/community/InstallLirc/Gutsy?highlight=%28lirc%29%7C%28gutsy%29]("https://help.ubuntu.com/community/InstallLirc/Gutsy?highlight=%28lirc%29%7C%28gutsy%29")

With feisty, at this point the ir transmitter worked and changed the channels on my digibox. As mentioned previously, as soon as I upgraded to gutsy the transmitter stopped changing channels. The optical LED was blinking, as it did before, but was clearly not sending the correct signals for the digibox to understand.

To get the transmitter to work under 7.10 I followed this guide:
[http://http://www.backports.ubuntuforums.org/showthread.php?t=592415]("http://http://www.backports.ubuntuforums.org/showthread.php?t=592415")

The ir transmitter now works correctly. So it seems the lirc package in gutsy is broken.

On boot, dmesg reports:
[   78.293078] lirc_dev: IR Remote Control driver registered, at major 61 
[   78.610669] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
[   78.610735] lirc_dev: lirc_register_plugin: sample_rate: 10
[   78.719624] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[   79.219956] lirc_serial: auto-detected active high receiver
[   79.219964] lirc_dev: lirc_register_plugin: sample_rate: 0

Not sure what "kernel tainted" means but will take a look into it.

---

