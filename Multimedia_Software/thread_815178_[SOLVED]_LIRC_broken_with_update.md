---
title: "[SOLVED] LIRC broken with update"
date: 2008-06-01
forum: Multimedia Software
---

### Post by Vonagio on 2008-06-01
I updated Mythbuntu to 8.04 today. Everything works well (the same as before) except LIRC.

Using irw gives me:
```
connect: Connection refused
```Using dmsg | grep -i lirc gives me:
```
[ 34.230439] lirc_dev: IR Remote Control driver registered, major 61
[ 34.248565] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[ 34.249173] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
[ 34.249176] lirc_mceusb2: Daniel Melander , Martin Blatter
[ 34.258936] usbcore: registered new interface driver lirc_mceusb2
```Before I added lirc_mceusb2 and lirc_dev to /etc/modules grep wouldn't show anything.

I have checked my hardware.conf and lircd.conf and they appear to be correct (and the same as many other examples around the forums.)

I am using the correct modules, as these were the ones in use when i had a working remote in 7.10.


SOLVED: I switched to mythdora 5.0, Mythbuntu or LIRC on mythbuntu is broken. The remote now works perfectly. I would actually recommend Mythdora over Mythbuntu for a new setup.

---

### Post by Vonagio on 2008-06-02
I was looking around in the /lib/modules/2.6.24.17-generic/ubuntu/media/lirc/lirc_mceusb2 and there is nothing in it, I thought that this is where the lirc_mceusb2.ko driver was...

I found a copy of the driver in my lirc-0.8.3 download dir and copied it over, with no more success.

---

### Post by Vonagio on 2008-06-03
I reinstalled Mythbuntu, for other reasons I managed to keep my recordings and schedules). I am at this stage now:

I have a Philips (SRM5100) MCE remote control (mceusb2), with a USB receiver. I have Mythbuntu 8.04 fully up to date (clean install).

I had trouble setting up the remote with lirc when I had 7.10, the solution was to include an argument in REMOTE_LIRCD_ARGS in hardware.conf. However, after updating, this has gone, and I cannot remember what the command was! (It was something like "-d /dev/lircX --output=/dev/lircX --listen=XXX").

irw returns to the command prompt (crashing lircd), showing the message "could not get file information for /dev/lirc" when I run lircd with -n.

The modules (lirc_mceusb2 and lirc_dev) are loaded, ls /dev/lirc* gives /dev/lirc0 /dev/lircd. If you would like to see any other information, I'll happily provide it.

I have tried running dpkg-reconfigure lirc and selscting "None" to clean hardware.conf but this had no effect. I am pretty sure that I need the LIRCD_ARGS to sort it out, I've been hunting round for the initial thread that explained it with no luck.

---

### Post by superm1 on 2008-06-03
Well first off:

The format of hardware.conf has changed.   I've got a mceusb2, and this exact config works for me:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

The important parts are the REMOTE_DEVICE, REMOTE_MODULES, and REMOTE_LIRCD_CONF.  If all of those are correct (which they would be after a dpkg-reconfigure lirc), then check your /etc/lirc/lircd.conf.

This is what's in mine:

```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

```
Again, i've got a mceusb2 so yours probably shouldn't deviate much.

As a fallback option can you try to cat /dev/lirc0?  See if you get output when you are pressing buttons.

---

### Post by superm1 on 2008-06-03
Also: 

re-read your post.... don't put stuff in /etc/modules.   don't start lircd on it's own without the init script.

If you need to start lircd, ```
/etc/init.d/lirc restart
```  You can easily be masking the real problem otherwise.

---

### Post by superm1 on 2008-06-03
If you really want to start it on its own for debugging purposes, start it from the init script once, and then  ```
ps aux | cat
```  to find out the entire command line used.  Use that one with the -n parameter.

---

### Post by Vonagio on 2008-06-03
I've checked my hardware.conf and lircd.conf and they match yours.

cat /dev/lirc0 (and lirc, lirc/0, lircd) returned with "No such file or directory".

i found the command for launching lirc with ps aux | cat (it was /usr/sbin/lircd --device=/dev/lirc0 -n). That brings back the same error as earlier when launching irw.

I can also rule out any conflicts with imon ir receivers on the motherboard, I've checked the manual and a visual check of the board itself and there is no built in receiver.

I am beginning to wonder if the problem is that the USB receiver doesn't power up when the computer starts, I have to reinsert it once the machine has powered on (it works/worked even re inserting during POST). If it doesn't have anything to do with this (I don't think it does because I've had the remote/receiver working before), then is there a solution to this? [its a secondary issue, that I can live with, and i suspect its hardware related]

---

### Post by Vonagio on 2008-06-08
Bump. I've been away, and Mythbuntu hasn't magically fixed my remote control!

Can anyone help any more with this issue?

---

### Post by superm1 on 2008-06-09
Okay, well if all of your conf files are identical, it is sounding like you really might have a hardware issue going on.

First off, is it showing up in lsusb?

Next, would you be able to try the receiver on a different PC?  Doesn't need to have Ubuntu on it, you can always boot a mythbuntu live disk and configure it in live mode.  All the lirc stuff is included, so it should logically work.

If it does work on that other machine, i'd consider investing in a new USB controller.  If it's not in lsusb and doesn't work, invest in a new receiver.

---

### Post by superm1 on 2008-06-09
Another diagnostic step that you can consider is even using a 7.10 live disk on this same computer.  You can easily rule out faulty hardware without a costly reinstall.

---

### Post by bthoward on 2008-06-13
Actually I've got this exact same issue although a slightly more complex setup.  All was working fine until recent updates and then video went wonky and LIRC was dead. 

I have a thread here where I mentioned this:
[http://ubuntuforums.org/showthread.php?t=826770](http://ubuntuforums.org/showthread.php?t=826770)

Here is the meat of my lircd.conf
```
#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

#Configuration for the Command IR : Motorola Cable box transmitter:
include /usr/share/lirc/transmitters/motorola/DCT700.conf

```

Entire contents of hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes"
REMOTE_LIRCD_ARGS="-d /dev/lirc0 --output=/dev/lircd --listen"

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES="lirc_dev lirc_cmdir"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="/usr/share/lirc/transmitters"
TRANSMITTER_LIRCD_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

```

I've made some custom mods to /home/brett/.lirc/mythtv for some personal preferences on button choice and what not but that shouldn't cause much issue....  

Also it should be noted that if I restart the lirc daemon and restart mythfrontend.real that all works as normal but just not if its a fresh boot.  All the messages in dmesg seem normal and both IR devices are showing up in lsusb just fine.  I have more info on the setup and what happened over at the other thread.

---

### Post by Vonagio on 2008-06-22
The hardware is most definetely not faulty, I had it working under 7.10 perfectly. The **only** change in the system is the move to 8.04 which lost my custom hardware.conf.

Is there any documentation on the LIRCD_ARGS section of the hardware.conf file? The argument I had originally was something along the lines of linking one device (maybe lircd) to another (lirc0). I didn't/don't really understand why this had to be done, except that maybe the IR receivers on my dvb cards may be getting in the way.

Thanks

---

### Post by bthoward on 2008-06-22
See the LIRCD manual and my file above.

 --connect=localhost:8765  do a search for ubuntu LIRCD and the string to the left and you'll find all sorts of goodies for multiple IR nuggets...  I finally figured out that in order for my stuff to work I just had to restart the server and then restart mythfrontend.real....

---

### Post by Vonagio on 2008-07-26
I've tried lots of things involving connect=localhost:8765 and have tried googling as you suggested. I'm not really sure what I'm looking for.

I think that the issue could be to do with the TV cards I have installed having their own IR receivers onboard, and these receivers might be interfering with the usb receiver in some way... If anyone has any ideas how I can disable the TV card receivers that might go someway towards resolving my LIRC woes (I have two of the same TV card installed, a KWorld DVB-T100, with cx88 drivers/chips).

Thanks


EDIT: I have been messing around with the hardware.conf all evening, I am now at a stage where irw doesn't crash, but it won't recognise my ir commands, (it doesn't show any output when I press buttons on the remote). mode2 doesn't work at all, it says it cannot open /dev/lirc : no such file. I have got this far by creating a symbolic link from /dev/lircd to /dev/lirc0, and not having any arguments in the hardware.conf. Any help getting irw to respond to my key presses would be a great help!

---

### Post by Clint_E on 2008-07-27
Hi !!

I just purchased a philips mce remote (srm 5100)..  I have no luck getting this to work with ubuntu 8.04 based distros.. I have tried Mythbuntu and eAR OS... but the remote works with mythdora and geexbox without any problems at all, I'm an ubuntu fan and I would really like this remote to work in ubuntu...

All configs seems OK but the /dev/lirc or lirc0 isn't created and irw does not work...

Clint_E

---

### Post by Vonagio on 2008-07-27
It sounds like you are having the same problems as I have. I got irw to work by creating a symbolic link from /dev/lircd to /dev/lirc0 then using lirc0 as the device.

With lirc running (use init to (re)start it) do:
```
ls /dev/lirc*
```
It shows /dev/lircd on my machine, according to any guides to setting up lirc this should be what you enter into hardware.conf as the device, but this doesn't work on mine, I get an error saying that lircd cannot connect to itself.

I created the sym link by doing:
```
sudo ln -s /dev/lircd /dev/lirc0
```

Now irw doesn't crash, but I get no output. I guess it might be on the way to working again, I'll have a play around with the lircd.conf (well the one that 8.04 uses is somewhere different, and lircd.conf only includes it...), I saw something while hunting the forums/google saying that you can find the device (the usb receiver) code and adding it to the end of the mceusb2 module, but I'm not sure if this is relevant to getting my remote to show an output in irw.

Also, mode2 doesn't work, I will have a try at using irrecord to make my own lircd.conf, however it didn't work on my first try yesterday...

I'll keep you updated on my progress, its good to know i'm not the only person with problems using this remote. I love the style of the remote and the 4-in-1 features, and it worked perfectly with 7.10...I might even downgrade the OS to make it work again, even though I like the new myth more.

---

### Post by Clint_E on 2008-07-29
Thanx Vonagio!

I agree it's to bad it doesn't work..  it's a great remote..  due to the fact that this remote works perfekt in other distros and even in ubuntu 7.10... the problem is most certenly the lirc version in 8.04....

Please keep me updated!

/Clint_E

---

### Post by Vonagio on 2008-07-29
I have again tried the remote with a 7.10 live disc. It works without fail the first time...

I saw that 8.04 has been updated to 8.04.1 with one of the bug fixes being a broken lirc upon upgrade to 8.04, I have installed this upgrade and it didn't make any difference. Maybe I have tinkered with lirc and associated settings too much now, I don't really want to do a clean install though, even though I have my recordings backed up and can easily restore my database.

I'll keep at it for a few more evenings then it might be my only option. I'll keep you posted Clint.

---

### Post by venzen on 2008-07-29
Please post what is output to /var/log/daemon.log when you do:

```
sudo /etc/init.d/lircd restart
```

---

### Post by Vonagio on 2008-07-29
I cannot init lircd, it says it doesnt exist, I used:
```
sudo /etc/init.d/lirc restart
```
instead...

The relevant output from the log file of the machine booting is:
```
Jul 29 22:51:33 MythBox lircd-0.8.3pre1[5782]: accepted new client on /dev/lircd
Jul 29 22:51:33 MythBox lircd-0.8.3pre1[5782]: could not get file information for /dev/lirc0
Jul 29 22:51:33 MythBox lircd-0.8.3pre1[5782]: default_init(): No such file or directory
Jul 29 22:51:33 MythBox lircd-0.8.3pre1[5782]: caught signal
```

I tried restarting lirc once, and it failed to stop the process, but successfully started it again. I restarted again and it did manage to stop and start lirc as normal, the output from both these restarts was the same, the most recent one is this:
```
Jul 29 22:54:14 MythBox lircd-0.8.3pre1[6405]: lircd(userspace) ready
Jul 29 22:55:26 MythBox lircd-0.8.3pre1[6405]: caught signal
Jul 29 22:55:27 MythBox lircd-0.8.3pre1[6459]: lircd(userspace) ready
```

Thanks

---

### Post by Clint_E on 2008-08-01
I have no luck at all getting the Philips SRM-5100 MCE remote to work, so could some one help me and describe how I can upgrade lirc from 0.8.3pre1 to the latest lirc 0.8.3 in ubuntu....

/Clint_E

---

### Post by Vonagio on 2008-08-06
I have solved the problems by installing Mythdora 5.0. The Philips SRM-5100 remote works perfectly with the standard MCE USB Remote configuration (it was called the all black controller in set up). I edited the lircrc to suit myself, but aside from that it was a seamless setup.

It is evident that Mythbuntu is broken with regards to my remote control. I think that there is a different version of LIRC installed with mythdora and mythbuntu, I'm not overly bothered now, as Mythdora works equally well to mythbuntu, if not better as it was a lot easier to set up (the install correctly configured my graphics driver and xorg without ANY input from me!).

---

### Post by nstenz on 2009-02-13
Can an somebody please rename this topic title to have something other than "[SOLVED]" in it? I don't consider "uninstall Ubuntu" to be a solution and just wasted 5 minutes going through this topic only to find out that nothing worked for me either.

---

### Post by bthoward on 2009-02-13
I got mine working again...  My files are posted in here.

---

