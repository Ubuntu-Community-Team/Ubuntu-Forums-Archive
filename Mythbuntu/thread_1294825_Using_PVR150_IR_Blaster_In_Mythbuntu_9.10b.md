---
title: "Using PVR150 IR Blaster In Mythbuntu 9.10b"
date: 2009-10-18
forum: Mythbuntu
---

### Post by sentinel23 on 2009-10-18
Working on setting up a new box with Mythbuntu 9.10 beta.

Everything's working pretty well so far - including my remote - but I can't get the blaster to work on my PVR150. (The vanilla 3.5mm blaster, not the MCE USB one.)

I won't go on about what I've done, but basically I think I just need the LIRC_PVR150 kernel module.

Where do I get that?  How do I load it?
Do I have to recompile the kernel?  Or LIRC?

Almost everything I've found on this references this page: [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)
That would be a great help, but the pre-patched version of LIRC he provides won't compile with the new kernel.

I feel like I'm just missing something simple, but I can't figure out what.  Any help would be great!

---

### Post by bsntech on 2009-10-18
This won't help you much, but I could get the Hauppauge HVR-1600 remote to even be found in Ubuntu 9.10 with all of the updates as of today.  I had to put the old Hauppauge PVR-150 card in and it is now - at least found.

dmesg | grep lirc

[   13.477963] lirc_dev: IR Remote Control driver registered, major 61 
[   13.824620] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
[   13.824623] lirc_dev: lirc_register_driver: sample_rate: 10

Still not finding the HVR-1600 but at least the remote for me now works.

In your case, try to run "sudo dpkg-reconfigure lirc" and ensure that when it asks on the second page about the IR transmitter, choose the correct one you will be using it with.

---

### Post by sentinel23 on 2009-10-18
Unfortunately, the Hauppauge transmitter doesn't appear to be an option when I run "dpkg-reconfigure lirc".

I'm pretty sure it was there in at least one of the earlier Mythbuntu versions, but it's not in 9.10.

Thanks though.

---

### Post by bsntech on 2009-10-19
Wow, that is strange.  I am running Ubuntu 9.10 (instead of Mythbuntu) and when I do the "sudo dpkg-reconfigure lirc" command, the first page that comes up is the information for the IR receiver.  It lists many different cards - and there should be an entry (in alphabetical order) where it says "Hauppauge TV Card".

---

### Post by sentinel23 on 2009-10-19
Oh yeah, the Hauppage card is there on the first screen, under Receivers.  But it's the Transmitter I need (the next screen), and I don't see it there.

---

### Post by bsntech on 2009-10-19
Yes, you will not see the Hauppauge TV Card under the transmitter.  In that list, you need to select the box that the transmitter will control - this would be the make/model of the device that your cable company or satellite company provided you.

---

### Post by mars76 on 2009-10-19
Hi All,

  Could some one point to the info reg setting up the IR Blaster ( MCE USB Version) with PVR-150 in 9.0.4 version.

Thanks
mars

---

### Post by sentinel23 on 2009-10-20
> **bsntech said:**
> Yes, you will not see the Hauppauge TV Card under the transmitter.  In that list, you need to select the box that the transmitter will control - this would be the make/model of the device that your cable company or satellite company provided you.

I don't think that's it.  It asks you to select the combination of transmitter and STB.  
I do have a Motorola Cable box, but I'm pretty sure my transmitter doesn't fit in to any of the options provided.
If I were to choose the wrong one, */etc/lirc/hardware.conf* is filled in incorrectly, and it doesn't work.  Choosing "None" or "Custom" just creates a blank hardware.conf.

> None
Custom
Command IR : Direct TV Receiver  
Command IR : Dish Receiver
Command IR : Motorola Cable box  
Command IR : Pioneer Cable box
Command IR : Scientific Atlanta Cable box  
Command IR : Sky Satellite Receiver 
Microsoft Windows Media Center V2 (usb) : Direct TV Receiver 
Microsoft Windows Media Center V2 (usb) : Dish Receiver  
Microsoft Windows Media Center V2 (usb) : Motorola Cable box  
Microsoft Windows Media Center V2 (usb) : Pioneer Cable box  
Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box
Microsoft Windows Media Center V2 (usb) : Sky Satellite Receiver
Serial Port (UART) : Direct TV Receiver 
Serial Port (UART) : Dish Receiver
Serial Port (UART) : Motorola Cable box
Serial Port (UART) : Pioneer Cable box
Serial Port (UART) : Scientific Atlanta Cable box
Serial Port (UART) : Sky Satellite Receiver
USB-UIRT2 : Direct TV Receiver
USB-UIRT2 : Dish Receiver
USB-UIRT2 : Motorola Cable box
USB-UIRT2 : Pioneer Cable box
USB-UIRT2 : Scientific Atlanta Cable box
USB-UIRT2 : Sky Satellite Receiver


---

### Post by stong98 on 2009-10-24
> **sentinel23 said:**
> 
Where do I get that?  How do I load it?
Do I have to recompile the kernel?  Or LIRC?

Almost everything I've found on this references this page: [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)
That would be a great help, but the pre-patched version of LIRC he provides won't compile with the new kernel.

I feel like I'm just missing something simple, but I can't figure out what.  Any help would be great!


I am in the same situation and it appears I have tried the same steps as you.  Has anyone been able to figure this out yet?

---

### Post by sentinel23 on 2009-10-24
> **stong98 said:**
> I am in the same situation and it appears I have tried the same steps as you.  Has anyone been able to figure this out yet?

Thanks for posting... I knew I couldn't possibly be alone on this.

No solution yet.  I'm thinking we just need someone (smarter than me, apparently) to patch LIRC the same way that that guy Mark did in that link.

Please let us know if you find anything.

---

### Post by jimmybondo on 2009-10-28
Someone filed a bug against this:

[https://bugs.launchpad.net/ubuntu/+s...rc/+bug/454843](https://bugs.launchpad.net/ubuntu/+s...rc/+bug/454843)

So it seems like pvr150 will not compile against the 2.6.31 (which I confirmed). I emailed the original pvr150 driver author, but am not holding my breath for an answer.

I am going to continue procrastinating and try to get it working, but I do not have high hopes.

---

### Post by sentinel23 on 2009-10-28
> **jimmybondo said:**
> Someone filed a bug against this:

[https://bugs.launchpad.net/ubuntu/+s...rc/+bug/454843](https://bugs.launchpad.net/ubuntu/+s...rc/+bug/454843)

So it seems like pvr150 will not compile against the 2.6.31 (which I confirmed). I emailed the original pvr150 driver author, but am not holding my breath for an answer.

I am going to continue procrastinating and try to get it working, but I do not have high hopes.

Thanks!

Interesting...

If it helps at all, I was able to determine that "lirc_pvr150" was re-released as "lirc_zilog", and Jarod Wilson created a kernel patch for .31 that apparently gets it working. (Sorry, don't have the links handy ATM.)

I haven't tried it, but it might be something to look at.

---

### Post by roob85 on 2009-10-28
Im having the same issue using ubuntu 9.10 RC1. Ive always installed lirc then put the haup-ir-blaster.bin file in /lib/firmware then modprobed lirc_dev and lirc_pvr150...but now im getting the error of 

FATAL: Module lirc_pvr150 not found.

or if i try to load what sentinel23 suggested

FATAL: Module lirc_zilog not found.


I *really* need to get my blaster working as soon as possible. If anyone has any other ideas please jump in....as if this is not resolved ill have to revert back to 9.04 until the corrections are made to fix this. :icon_frown:

---

### Post by jimmybondo on 2009-10-31
It looks like lirc_zilog would work. However, I cannot figure out how to compile it and get it working on Ubuntu. All mentions of the module only reference a kernel patch that I cannot figure out how to apply.

Any suggestions?
Thanks,
Jim

---

### Post by Kheops_74 on 2009-10-31
Just upgrade to 9.10. Same here the IR blaster is not working on my pvr150. Is somebody find a way to get it work?

About lirc_zilog, is it work? What are the steps?

Thanks

---

### Post by Kheops_74 on 2009-10-31
I tried to compile the driver here ([http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)). I get an error when i try to do make && make install.

Some people think that this is the solution but i can't make it work

---

### Post by yfaykya on 2009-11-01
I patched lirc-modules-sorce and got it to compile and install but I have not upgraded my backend yet so cannot test it. Patch is at [http://www.skynet.ie/~shabba/zilog.diff](http://www.skynet.ie/~shabba/zilog.diff)

Let me know if this works. I think Mario is going to create a PPA of it or include it in lirc-modules-source

D.

---

### Post by Kheops_74 on 2009-11-01
Maybe you can put the steps to patch lirc-module-source here. I will try to figure it out.

Thanks

---

### Post by dherman on 2009-11-01
I am a long time user of the PVR150 (for just IR Blasting).. It would be nice to get this fixed, as I may not live out the week cuz, myth can't change channels...

Dave

---

### Post by jimmybondo on 2009-11-01
The patch fails to apply correctly:

/usr/src/lirc-0.8.4a$ sudo patch -p0 < ~/Downloads/zilog.diff 
patching file lirc-modules-source.conf
Hunk #1 FAILED at 2.
1 out of 1 hunk FAILED -- saving rejects to file lirc-modules-source.conf.rej
patching file dkms.conf
Hunk #1 FAILED at 63.
1 out of 1 hunk FAILED -- saving rejects to file dkms.conf.rej
patching file Makefile
Hunk #1 FAILED at 28.
Hunk #2 succeeded at 555 with fuzz 2 (offset 431 lines).
1 out of 2 hunks FAILED -- saving rejects to file Makefile.rej
patching file drivers/lirc_zilog/.deps/lirc_zilog.Po
patching file drivers/lirc_zilog/Makefile
patching file drivers/lirc_zilog/lirc_zilog.c
patching file drivers/Makefile
Hunk #1 FAILED at 136.
1 out of 1 hunk FAILED -- saving rejects to file drivers/Makefile.rej

Any ideas?
Jim

---

### Post by yfaykya on 2009-11-01
The lirc I have installed is 0.8.6 (0.8.6-0ubuntu2)

---

### Post by Kheops_74 on 2009-11-01
I try this sudo patch -p0 < ~/Downloads/zilog.diff . it works on the version 0.8.6.

What are the next step?

Can you provide your lircd.conf and hardware.conf

Thanks

---

### Post by yfaykya on 2009-11-01
Try :

sudo dkms remove -m lirc -v 0.8.6 --all
sudo dkms add -m lirc -v 0.8.6
sudo dkms build -m lirc -v 0.8.6

sudo depmod -a
sudo modprobe lirc_zilog

That should be it. Make sure f/w is in right place.

---

### Post by jimmybondo on 2009-11-01
Ah yes, my mistake, I was on the wrong machine! I have successfully built lirc_zilog with the patch from yfaykya:

```
sudo apt-get install lirc-modules-source
cd /usr/src/lirc-0.8.6
sudo patch -p0 < ~/Downloads/zilog.diff
sudo dpkg-reconfigure lirc-modules-source
```

That did a reconfigure and I verified that it is loaded with dmsg:
```
$ dmesg | grep lirc_zilog
[   29.816772] lirc_zilog: Zilog/Hauppauge IR driver initializing
[   29.819735] lirc_zilog: chip found with RX and TX
[   29.905432] lirc_zilog: Zilog/Hauppauge IR blaster firmware version 1.3.0 loaded
[   29.905505] lirc_zilog: initialization complete
```

I fixed the config files to use lirc_zilog but it seems now I have a configuration problem with lirc:
```
$ irsend SEND_ONCE DCT700 power
irsend: command failed: SEND_ONCE DCT700 power
irsend: hardware does not support sending
```

I will keep working on it, but any help is appreciated!
Jim

---

### Post by dherman on 2009-11-01
Thanks... I have it working now too... Be sure to place the firmware in /lib/firmware

There is an issue though.. I had to patch the daemons/config_file.c to allow the longer id's for the dishnetwork remotes... I used the file my .85 patched lirc source. It compiled in just fine in the newer one's place

---

### Post by jimmybondo on 2009-11-01
> **dherman said:**
> Thanks... I have it working now too... Be sure to place the firmware in /lib/firmware

You mean putting [http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin](http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin) in /lib/firmware? I did that, but still no luck.
Jim

---

### Post by dherman on 2009-11-01
check you /var/log/syslog and /var/log/messages

anything interesting??

---

### Post by jimmybondo on 2009-11-01
I got it working! The problem was that my hardware.conf was pointing to /dev/lirc1 and not /dev/lirc0.

So to recap the steps I took to get everything working:

```
sudo apt-get install lirc-modules-source
cd /usr/src/lirc-0.8.6
sudo patch -p0 < ~/Downloads/zilog.diff
sudo dpkg-reconfigure lirc-modules-source
```

then open /etc/lirc/hardware.conf and modify TRANSMITTER_MODULES to this:
```
TRANSMITTER_MODULES="lirc_dev lirc_zilog"
```

Then I followed [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24), steps 6, 8-13

Now everything is great and my life is sane.
Thanks everyone!
Jim

---

### Post by Kheops_74 on 2009-11-01
Can you provide your lircd.conf and hardware.conf. I still have the "irsend: hardware does not support sending" message. I think, i'm not far away.

Thanks

---

### Post by jimmybondo on 2009-11-01
> **Kheops_74 said:**
> Can you provide your lircd.conf and hardware.conf. I still have the "irsend: hardware does not support sending" message. I think, i'm not far away.

Thanks

hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_zilog"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
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

lircd.conf:
```

begin remote

  name          blaster
  bits          32
  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0
  begin raw_codes
    name 0_82_KEY_0
    5373952
    name 0_82_KEY_1
    5373953
    name 0_82_KEY_2
    5373954
    name 0_82_KEY_3
    5373955
    name 0_82_KEY_4
    5373956
    name 0_82_KEY_5
    5373957
    name 0_82_KEY_6
    5373958
    name 0_82_KEY_7
    5373959
    name 0_82_KEY_8
    5373960
    name 0_82_KEY_9
    5373961
    name 0_82_KEY_POWER
    5373962
    name 0_82_KEY_CH_UP
    5373967
    name 0_82_KEY_CH_DOWN
    5373968
    name 0_82_KEY_MUTE
    5373969
    name 0_82_KEY_VOL_DOWN
    5373970
    name 0_82_KEY_VOL_UP
    5373972
    name 0_82_KEY_MNSELECT
    5373975
    name 0_82_KEY_ENTER
    5373995
    name 0_82_KEY_MENU
    5373999
    name 0_82_KEY_MUP
    5374000
    name 0_82_KEY_MDOWN
    5374001
    name 0_82_KEY_MLEFT
    5374002
    name 0_82_KEY_MRIGHT
    5374003
  end raw_codes
end remote
```

look at syslog if you run into problems:
```
tail /var/log/syslog
```

---

### Post by Kheops_74 on 2009-11-01
Give up for tonight. I use your lircd.conf and hardware.conf and i still have this message in /var/log/syslog

Nov  1 22:01:20 pvr-desktop lircd-0.8.6[15220]: accepted new client on /var/run/lirc/lircd
Nov  1 22:01:21 pvr-desktop lircd-0.8.6[15220]: error processing command: SEND_ONCE blaster 750
Nov  1 22:01:21 pvr-desktop lircd-0.8.6[15220]: hardware does not support sending
Nov  1 22:01:21 pvr-desktop lircd-0.8.6[15220]: removed client

---

### Post by jimmybondo on 2009-11-01
Did you restart lirc?

```
sudo service lirc restart
```

---

### Post by Kheops_74 on 2009-11-01
Finally it's working. I unpluged the computer and it work after. The other thing that i had to figure out is the codeset of my decoder. it was 106 and not 82.

Thanks

---

### Post by vbsaltydog on 2009-11-05
I am having some trouble here and could use some help. I am running mythbuntu 9.10 with a PVR-150

I have the remote working for controlling myth but am trying to enable the irblaster too. I have a decent understanding of *nix so help me out here please.

I downloaded the bin file from earlier in the thread to the proper directory and made it executable, I downloaded the patch file to my home directory, I downloaded the lirc source, patched the source, and reconfigured the source after patching it.

I downloaded the script that sends the power command to every code set and was getting the irsend error about send not supported, then I changed the device in the hardware.conf to /dev/lircd vs. /dev/lirc0 and the irsend error went away and the script appeared to be doing what it was meant to do however the blaster was not blinking when I checked it.

I am going to provide my file contents below, please try to help me get my remote working for use with the myth frontend as well as changing the channels on my directv receiver.

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#TRANSMITTER="Command IR : Direct TV Receiver"
#TRANSMITTER_MODULES="lirc_dev lirc_zilog"
#TRANSMITTER_DRIVER=""
#TRANSMITTER_DEVICE="/dev/lircd"
#TRANSMITTER_SOCKET=""
#TRANSMITTER_LIRCD_CONF="directtv/general.conf"
#TRANSMITTER_LIRCD_ARGS=""

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

```

/etc/lirc/lircd.conf

#Configuration for the Hauppauge TV card remote:
# I have commented and uncommented the following line and restarted lirc with no effect 
# on the ability for the remote to control the myth frontend.
#include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"

#I added the content of the example file http://www.blushingpenguin.com/mark/lmilk/lircd.conf below but I am not listing it here because it is too long.

```

```

lirc related devices in /dev directory:
lirc0
lircd

```

Any help is appreciated.

---

### Post by gleepwurp on 2009-11-14
Hi Saltydog,

looking at your configuration file (hardware.conf), your "TRANSMITTER" entries are commented out (# ...).

Try Uncommenting and restarting the service  (ie: sudo service lirc restart)

and TRANSMITTER_DEVICE you either be empty or = /dev/lirc0

but I might be mistaken. My lirc was working fine with no TRANSMITTER_DEVICE defined until this morning where everything IR Blaster-related went to hell...

Gleepwurp.

---

### Post by vbsaltydog on 2009-11-14
I have gotten my pvr remote working and although the concept is easy once you decipher all of the cryptic documentation and outdated threads, you have to suffer through the process first because nobody seems to know how to write a how to that a normal person can comprehend. I bet I could teach a chimp to set one up if the proper documentation was available. Here is a taste of how easy it is to setup the pvr remote to control the myth front end. I am leaving the IR Blaster part out as you should save yourself the headache and just use a serial cable to the cable/satellite receiver.

(1) plug your ir receiver into the port on the pvr card and make sure the ir eye accessible to see the remote signal.

(2) sudo apt-get install lirc
(If lirc is already installed, it renames the old files and runs from the newly installed files).

Follow the on screen prompts to setup lirc. Choose the Hauppauge TV card for the remote type. This will setup the /etc/lirc/lircd.conf file and the file to hold your remote config, probably /usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge.

(3) run the command irw from the shell (this is going to show codes as you press buttons on the remote.

(4) press the play button on the remote and watch for the code at the shell output.

(5) make a note somewhere of the name on the remote button that you press and the corresponding code that shows up in the shell output. This will be a mapping of the remote button code to the remote button human readable name and you will need this later.

(6) once you have pressed all of the buttons on the remote, one by one, and mapped the code for each button to the name of the button as the code appears in the shell, you need to change the codes in /usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge or whatever include file is listed in /etc/lirc/lircd.conf to match the remote button code/ remote button name mapping that you created in the previous step.

(7) Make sure that your /etc/lirc/hardware.conf file shows the correct remote device.

(8) sudo service lirc restart

(9) Setup a lircrc file under /home/mythtv/.mythtv/
(This file tells myth what to do when remote buttons are received by lirc. Ex.
You press the play button -> lirc receives code 0000x4 -> your /usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge file tells lirc that 0000x4 = play -> lircrc tells mythtv what to do when the play button is pressed.)

(10) Restart the machine so that the mythfrontend , mythbackend, lirc, etc are all restarted and you should be able to control your mythtv frontend with your pvr remote.

---

### Post by sentinel23 on 2009-11-16
> **vbsaltydog said:**
> I have gotten my pvr remote working and although the concept is easy once you decipher all of the cryptic documentation and outdated threads, you have to suffer through the process first because nobody seems to know how to write a how to that a normal person can comprehend. I bet I could teach a chimp to set one up if the proper documentation was available. Here is a taste of how easy it is to setup the pvr remote to control the myth front end. I am leaving the IR Blaster part out as you should save yourself the headache and just use a serial cable to the cable/satellite receiver.

Oddly, my 150 remote worked out of the box with Mythbuntu.

I wish I could just use a serial or firewire cable for my STB, but unfortunately my DCT700 doesn't have those options, so I'm stuck fighting with this blaster...

---

### Post by vbsaltydog on 2009-11-17
Your STB doesnt support Tivo ? If there is a a usb port on the STB you might be able to use a usb to serial converter cable from the STB to the serial port on your Myth box.

---

### Post by sentinel23 on 2009-11-17
> **vbsaltydog said:**
> Your STB doesnt support Tivo ? If there is a a usb port on the STB you might be able to use a usb to serial converter cable from the STB to the serial port on your Myth box.

Nope.
[[IMG]http://developer.motorola.com/products/settops/dct700/images/large/[/IMG]]("http://www.motorola.com/Business/US-EN/Business+Product+and+Services/TV+Video+Distribution/Customer+Premises+Equipment+%28Set-tops%29/All-Digital+QAM+Set-tops/DCT700_US-EN")

---

### Post by vbsaltydog on 2009-11-17
I would get a new STB due to the fact that I have heard that the ir blasters are problematic even if you do get it working.

---

### Post by sentinel23 on 2009-11-17
> **vbsaltydog said:**
> I would get a new STB due to the fact that I have heard that the ir blasters are problematic even if you do get it working.

Just got it, and that's all my provider would give me unless I went HD, or found an old one 2nd-hand (which they may not even support).

**That's the whole point of this thread.**

I appreciate your input, but we need to keep this discussion on topic in order to get anywhere.


On that note, thanks to everyone that's been contributing.  I finally have some time to take another look at it, but I don't know if I'll have any luck... :-?

---

### Post by bblboy54 on 2009-11-19
> **jimmybondo said:**
> I got it working! The problem was that my hardware.conf was pointing to /dev/lirc1 and not /dev/lirc0.

So to recap the steps I took to get everything working:

```
sudo apt-get install lirc-modules-source
cd /usr/src/lirc-0.8.6
sudo patch -p0 < ~/Downloads/zilog.diff
sudo dpkg-reconfigure lirc-modules-source
```

then open /etc/lirc/hardware.conf and modify TRANSMITTER_MODULES to this:
```
TRANSMITTER_MODULES="lirc_dev lirc_zilog"
```

Then I followed [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24), steps 6, 8-13

Now everything is great and my life is sane.
Thanks everyone!
Jim

Thank you so much!  This worked perfectly!

---

### Post by charbofranck on 2009-11-26
Bonjour !

I don't know for you guys but I get the brilliant idea to get an hauppage WinTV-HVR 1600 Model 1199. I try Since a month ago to got install that p@in in th @ss card. Everything goes well until you start to play with the famous LIRC thing ! What an amazing thing. Short story maybe some peoples are lucky and I'm not but I follow at least 10 differents procedures with the same result still stuck at the same point.
 
dmesg

 14.133272] lirc_zilog: Zilog/Hauppauge IR driver initializing
[   14.135346] lirc_zilog: no device found
[   14.135362] lirc_zilog: no device found
[   14.135404] lirc_zilog: initialization complete

If I try IRW and tail my syslog I see 

Nov 26 20:23:05 pvrpc lircd-0.8.6[1054]: accepted new client on /var/run/lirc/lircd
Nov 26 20:23:05 pvrpc lircd-0.8.6[1054]: could not get file information for /dev/lirc0
Nov 26 20:23:05 pvrpc lircd-0.8.6[1054]: default_init(): No such file or directory
Nov 26 20:23:05 pvrpc lircd-0.8.6[1054]: Failed to initialize hardware
Nov 26 20:23:10 pvrpc lircd-0.8.6[1054]: removed client

lsmod 

frank@pvrpc:/var/log$ lsmod
Module                  Size  Used by
lirc_zilog             15504  0 
lirc_dev               10804  1 lirc_zilog

Anybody have similar issue ??

Thank and don't give up !

---

### Post by doudar on 2009-11-27
Everything seems to be working for me other than it doesn't work. The firmware is getting loaded, and send commands don't return any errors, but I'm not getting a response on the dishtv box. 
 
I copied my lircd.conf that was working on 9.04(and had been made with blushing penguins instructions). Did the remote codes change from the old pvr_150 module to the new lirc_zilog module?  
 
I'm doing this upgrade remotely so this one might be a bit harder!
 
EDIT:
The codes didn't change. Out of frustration I used the worthless mythbuntu GUI blaster config and then after manually changing lircd.conf and hardware.conf back to what they were it started working.

---

### Post by deadland on 2009-11-29
Hi there,

I already did a lot of things to get until that point, but I have no luck with the ir blaster of the Hauppauge HVR 1950, everything seems to work fine:

```
[   17.139693] lirc_dev: IR Remote Control driver registered, major 61 
[   18.455327] lirc_i2c: chip 0x0 found @ 0x71 (Hauppauge HVR1300)
[   18.455337] lirc_dev: lirc_register_driver: sample_rate: 10
[   18.781922] lirc_zilog: Zilog/Hauppauge IR driver initializing
[   18.789595] lirc_zilog: initialization complete

```

but when I try to send a command, I get the following error:

```
[   17.139693] lsudo irsend -d /dev/lirc0 SEND_ONCE DCT700 1
irsend: could not connect to socket
irsend: Connection refused
```

I already installed the latest v4l-dvb to get the latest pvrusb2, which fix the following problem:

```
Bind I2C address 0x71 for Zilog IR devices (needed specifically for HVR-1950)
```

But it doesn't help.

Some additional infos:

```
cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1300"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES="lirc_zilog"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

```

I already have months trying to get mythbuntu 9.10 working, please help me!

Thanks in advanced

---

### Post by daveriser on 2009-12-05
this thread has been really helpful for me... but i'm still stuck with the "**irsend: hardware does not support sending**" error... although i think i've done everything mentioned here.

i'm using lirc_zilog and my lircd.conf is this: [http://www.blushingpenguin.com/mark/lmilk/lircd.conf](http://www.blushingpenguin.com/mark/lmilk/lircd.conf)
plus i've copied the firmware file to /lib/firmware.

can anyone help? huge huge thanks in advance, already been stuck on this for days!!

/etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_zilog"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
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

```tail /var/log/syslog
```

Dec  5 19:27:50 livingroomtv lircd-0.8.6[15477]: accepted new client on /var/run/lirc/lircd
Dec  5 19:27:50 livingroomtv lircd-0.8.6[15477]: error processing command: SEND_ONCE blaster power
Dec  5 19:27:50 livingroomtv lircd-0.8.6[15477]: hardware does not support sending
Dec  5 19:27:50 livingroomtv lircd-0.8.6[15477]: removed client

```dmesg | grep lirc
```

[    7.720812] lirc_dev: IR Remote Control driver registered, major 61 
[    7.893628] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
[    7.893631] lirc_dev: lirc_register_driver: sample_rate: 10
[    7.959409] lirc_zilog: Zilog/Hauppauge IR driver initializing
[    8.055736] lirc_zilog: initialization complete

```

---

### Post by Kheops_74 on 2009-12-05
Try to only configure the transmitter (no remote) and reboot. Works for me. 
I try to add both and in this case the transmitter doesn't work. 

K

---

### Post by daveriser on 2009-12-06
It works!! thanks! :)

must have missed that in the other configs in this thread. this is now my hardware.conf:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE=""
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_zilog"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
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

```although i'm pretty sure i don't need the TRANSMITTER_LIRCD_CONF line as this is specified in the 'catch all' lircd.conf ...

---

### Post by Kheops_74 on 2009-12-06
So it's working without the remote like my config. The real question is why? I really don't understand why it works remote only, transmitter only but not both as in 9.04.

I hope they will correct this. My remote get dusty.

K

---

### Post by Chewiesw on 2009-12-07
what am i doing wrong now ....??

I can change the channels on my stb box using commandline either via irsend or calling the script. Mythtv really believes that it is changing channels ( I have creatd a error log for the script --No errors logged)
. The blaster does not flash thereofre the channels don't change.

---

### Post by ale99 on 2009-12-17
There is something I don't understand about the lirc_zilog drivers. I have HVR-1950 and I have been successful compiling the patched drivers. However, the drivers cannot find my device. Please find an output of dmesg:

root@mythtv:~# dmesg | grep lirc
[   13.825455] lirc_dev: IR Remote Control driver registered, major 61
[   14.001912] lirc_i2c: chip 0x0 found @ 0x71 (Hauppauge HVR1300)
[   14.001916] lirc_dev: lirc_register_driver: sample_rate: 10
[   14.041084] lirc_zilog: Zilog/Hauppauge IR driver initializing
[   14.042631] lirc_zilog: initialization complete
[   86.451222] lirc_zilog: Zilog/Hauppauge IR driver unloaded
[  107.214681] lirc_dev: IR Remote Control driver registered, major 61
[  107.219376] lirc_zilog: Zilog/Hauppauge IR driver initializing
[  107.221957] lirc_zilog: ir_probe: adapter id=0x0, client addr=0x71
[  107.221963] **lirc_zilog: no device found**
[  107.222016] lirc_zilog: initialization complete
[  118.292653] lirc_zilog: Zilog/Hauppauge IR driver unloaded
[  136.504779] lirc_dev: IR Remote Control driver registered, major 61
[  136.509413] lirc_zilog: Zilog/Hauppauge IR driver initializing
[  136.511777] lirc_zilog: ir_probe: adapter id=0x0, client addr=0x71
[  136.511782] **lirc_zilog: no device found**
[  136.511836] lirc_zilog: initialization complete

Could someone suggest why the driver fail to see the device?
BTW, I am using the latest pvrusb2 drivers. 
OS is Mythbuntu 9.10 kernel 2.6.31-16-generic

Thanks,
Ale99

---

### Post by TheHilikus on 2009-12-24
> **sentinel23 said:**
> Thanks!

Interesting...

If it helps at all, I was able to determine that "lirc_pvr150" was re-released as "lirc_zilog", and Jarod Wilson created a kernel patch for .31 that apparently gets it working. (Sorry, don't have the links handy ATM.)

I haven't tried it, but it might be something to look at.

can you please find that link?
i'm trying to do this too and it would help me or someone else to have that link you mention

---

### Post by sentinel23 on 2009-12-24
> **TheHilikus said:**
> can you please find that link?
i'm trying to do this too and it would help me or someone else to have that link you mention

See if these help:
[URL="http://old.nabble.com/PVR-150-IR-blaster-with-2.6.31-Karmic-Koala-kernel-td26144394.html"]
http://old.nabble.com/PVR-150-IR-blaster-with-2.6.31-Karmic-Koala-kernel-td26144394.html[/URL]
[http://wilsonet.com/jarod/junk/hdpvr-ir/]("http://wilsonet.com/jarod/junk/hdpvr-ir/")
[http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=408217;page=1;mh=-1;list=mythtv;sb=post_latest_reply;so=ASC]("http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=408217;page=1;mh=-1;list=mythtv;sb=post_latest_reply;so=ASC")
[http://www.gossamer-threads.com/lists/engine?list=mythtv&do=search_results&search_forum=all&search_string=lirc_zilog&search_type=AND&search_fields=sb&search_time=&search_user_username=jarod%40wilsonet.com&sb=post_time&mh=50]("http://www.gossamer-threads.com/lists/engine?list=mythtv&do=search_results&search_forum=all&search_string=lirc_zilog&search_type=AND&search_fields=sb&search_time=&search_user_username=jarod%40wilsonet.com&sb=post_time&mh=50")

---

### Post by TheHilikus on 2009-12-25
ok, i got it working! both RC and IR Blaster work
i really don't understand why though. There's nothing in my hardware.conf that says that my RC is what it is, it only says what the IR Blaster should map to, so i don't know where the RC mapping is coming from. I don't know if it's a luck bug where lirc just remembers the last mapping that worked but if it is that, i am thinking it won't survive an update 

this is my hardware.conf. notice everything about the RC is commented out, only the IR Blaster section is active

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="Hauppauge TV card"
#REMOTE_MODULES="lirc_dev lirc_i2c"
#REMOTE_DRIVER=""
#REMOTE_DEVICE="/dev/lirc0"
#REMOTE_SOCKET=""
#REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
#REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_zilog"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
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

also, in case someone is trying to do this. The only modules i have loaded are lirc_dev and lirc_zilog. so it seems that lirc_zilog works not only for the Blaster but for the RC as well

---

### Post by aseriesoftubes on 2009-12-26
I followed the steps listed by jimmybondo in post #28 of this thread, but I still get the "hardware does not support sending" error. 

From the comments [here]("http://notepad.bobkmertz.com/2009/11/pvr-150-ir-blaster-on-mythbuntu-910.html"), it sounds like this technique does not work for 64-bit kernels. I am using Mythbuntu 9.10 64-bit, so I guess that explains the problems I'm having.

Has anybody been able to make this work using a 64-bit kernel? If so, a brief howto would be very much appreciated.

tail /var/log/syslog:
```
Dec 26 17:02:06 Reggie ntpd[1468]: synchronized to 91.189.94.4, stratum 2
Dec 26 17:03:38 Reggie lircd-0.8.6[2613]: caught signal
Dec 26 17:03:38 Reggie lircd-0.8.6[2653]: lircd(default) ready, using /var/run/lirc/lircd
Dec 26 17:03:41 Reggie lircd-0.8.6[2653]: accepted new client on /var/run/lirc/lircd
Dec 26 17:03:41 Reggie lircd-0.8.6[2653]: could not get file information for /dev/lirc0
Dec 26 17:03:41 Reggie lircd-0.8.6[2653]: default_init(): No such file or directory
Dec 26 17:03:41 Reggie lircd-0.8.6[2653]: Failed to initialize hardware
Dec 26 17:03:41 Reggie lircd-0.8.6[2653]: error processing command: SEND_ONCE DCT2000 1
Dec 26 17:03:41 Reggie lircd-0.8.6[2653]: hardware does not support sending
Dec 26 17:03:41 Reggie lircd-0.8.6[2653]: removed client

```

dmesg | grep lirc:
```
[    8.302861] lirc_dev: IR Remote Control driver registered, major 61 
[    8.328943] lirc_zilog: Zilog/Hauppauge IR driver initializing
[    8.330292] lirc_zilog: initialization complete
```

hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_zilog"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
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

---

### Post by diskmaster23 on 2010-01-30
Does your remote work? Because when I upgraded from 9.04 to 9.10, my remote stopped working. My hardware.conf is exactly the same, but I get nothing out of irw.

---

### Post by bloodqc on 2010-02-21
I don't know if someone already made a PPA for it, but if not, I made one: [https://launchpad.net/~brunoqc/+archive/lirc-pvr-150](https://launchpad.net/~brunoqc/+archive/lirc-pvr-150)

Here's how I made it, using [the patch from yfaykya]("http://www.skynet.ie/~shabba/zilog.diff").

Get the deb sources
```
apt-get source lirc-modules-source
cd lirc-0.8.6
```

Since the deb already use [Quilt]("http://savannah.nongnu.org/projects/quilt") to manage patches we can use that.

(note, lines beginning with # are comments, no need to type that)
```
# set Quilt's path
export QUILT_PATCHES=debian/patches

# apply every existing patches
quilt push -a

# create a new patch
quilt new zilog.diff
```

```
# add every files that will be created or modified so Quilt will be able to create a patch by tracking the changes (note that some files are not the exact same name from the diff since the patch was made to apply on the installed files).
quilt add debian/modules-source/lirc-modules-source.conf debian/dkms.conf.in debian/modules-source/Makefile drivers/Makefile.in drivers/lirc_zilog/.deps/lirc_zilog.Po drivers/lirc_zilog/Makefile drivers/lirc_zilog/lirc_zilog.c
```

The patch we got from yfaykya is supposed to be applied on installed files from the installed deb. The patch will apply cleanly but we will need to give the path of each file.

```
patch -p0 < /home/bruno/zilog.diff
```

Here's the paths for the files(in the same order) :
```
debian/modules-source/lirc-modules-source.conf
debian/dkms.conf.in
debian/modules-source/Makefile
drivers/Makefile.in
```

```
#update the patch
quilt refresh
```

The last command complain about trailing whitespaces, we could ignore that but while we are at it :

```
#destroy the trailin whitespaces
sed -i 's/ *$//' drivers/lirc_zilog/Makefile
#update the patch
quilt refresh
```

everything's fine now.

```
#removes all the applied patches
quilt pop -a
```


Create an updated deb
```
# set my personnal info
export DEBFULLNAME='My name'
export DEBEMAIL='my@email'

# update the version number (I also added a ~ppa0 at the end of '0.8.6-0ubuntu3' since I'm planning to upload it to my ppa)
dch -i
```

Upload the package source to my ppa
```
# build the needed file for the upload
debuild -S

# upload to my ppa
dput ppa:brunoqc/lirc-pvr-150 ../lirc_0.8.6-0ubuntu3~ppa0_source.changes
```


I could also build the package locally
```
# Install the required dependencies
sudo apt-get build-dep lirc-modules-source

# build the package
dpkg-buildpackage -us -uc

# install
sudo dpkg -i ../lirc-modules-source_0.8.6-0ubuntu3~ppa0_all.deb
```

Now we have a nice deb using a [quilt patch]("http://pastebin.com/f1aaabc89") so it's easier to maintain.

We could also send a diff to the package maintainers using :
```
debdiff lirc_0.8.6-0ubuntu2.dsc lirc_0.8.6-0ubuntu3~ppa0.dsc > difftosend.diff
```
I'm not sure if it would be accepted since the patch name (zilog.diff) may not follow a naming convention and also I guess "new feature" may only go in the lucid.

[PackagingGuide/Howtos/Quilt]("https://wiki.ubuntu.com/PackagingGuide/Howtos/Quilt")

---

### Post by bloodqc on 2010-02-21
I got a WinTV-HVR 1600 and I don't see any chip found or that the firmware is getting loaded. I only have 'lircd' in /dev. Any ideas?

I have haup-ir-blaster.bin in /lib/firmware. I'm using mythbuntu 9.10 (32 bits).

```
[  822.169377] lirc_zilog: Zilog/Hauppauge IR driver initializing
[  822.174097] lirc_zilog: initialization complete
```

---

### Post by TrevorBradley on 2010-03-27
I came upon this thread after getting stuck doing research.  Apparently I'm not the only frustrated user with an PVR-150. 

I've been using lirc_zilog successfully with ubuntu for since October 2009.  I got an version from Jarod Wilson that seemed to work great.  I still had to go through a dozen hoops every time I upgraded my kernel, but it was at least do-able.

Today I came to my system and noticed that it was no longer able to change channels.  I hadn't rebooted the machine with a kernel upgrade, but I was suddenly getting the error:

irsend: command failed: SEND_ONCE blaster DISPLAY
irsend: hardware does not support sending

Digging deeper into syslog I found:

Mar 27 00:32:33 pergamon lircd-0.8.6[7464]: accepted new client on /var/run/lirc/lircd
Mar 27 00:32:33 pergamon lircd-0.8.6[7464]: could not get file information for /dev/lirc0
Mar 27 00:32:33 pergamon lircd-0.8.6[7464]: default_init(): No such file or directory
Mar 27 00:32:33 pergamon lircd-0.8.6[7464]: Failed to initialize hardware
Mar 27 00:32:33 pergamon lircd-0.8.6[7464]: error processing command: SEND_ONCE blaster DISPLAY
Mar 27 00:32:33 pergamon lircd-0.8.6[7464]: hardware does not support sending
Mar 27 00:32:33 pergamon lircd-0.8.6[7464]: removed client

And lo an behold /dev/lirc0 was completely missing.

I reinstalled the drivers, lirc_dev and lirc_zilog were starting up without error:

$ sudo rmmod lirc_zilog lirc_dev
$ sudo modprobe lirc_dev
$ sudo modprobe lirc_zilog
$ sudo pkill lircd
$ sudo /usr/local/sbin/lircd --device=/dev/lirc0

Generated a syslog of:

Mar 27 00:42:36 pergamon kernel: [ 2309.926826] lirc_zilog: Zilog/Hauppauge IR driver unloaded
Mar 27 00:42:36 pergamon kernel: [ 2309.926826] lirc_zilog: Zilog/Hauppauge IR driver unloaded
Mar 27 00:42:46 pergamon kernel: [ 2319.945691] lirc_dev: IR Remote Control driver registered, major 61 
Mar 27 00:42:46 pergamon kernel: [ 2319.945691] lirc_dev: IR Remote Control driver registered, major 61 
Mar 27 00:42:51 pergamon kernel: [ 2325.274382] lirc_zilog: Zilog/Hauppauge IR driver initializing
Mar 27 00:42:51 pergamon kernel: [ 2325.275654] lirc_zilog: initialization complete
Mar 27 00:42:51 pergamon kernel: [ 2325.274382] lirc_zilog: Zilog/Hauppauge IR driver initializing
Mar 27 00:42:51 pergamon kernel: [ 2325.275654] lirc_zilog: initialization complete

I don't see a single error in the logs (double and triple checked, I promise!) and lircd seems to start up perfectly, and yet /dev/lirc* doesn't exist.

I have no idea why the system spontaneously decided it couldn't change channels.  I'm wondering if the card has gotten too old, or if something changed in a latest non-kernal ubuntu update.

I know I'm missing something, I'm out of ideas on where to look.

Help!

EDIT: Just to clarify, I'm using a PVR-150 in Ubuntu 9.10 and an externally mounted IR blaster.  I've got a DCT terminal and this really has been working great for months.  No clue why it's stopped.

Trevor Bradley

---

### Post by TrevorBradley on 2010-03-27
OK, that last post was just too vague for me not to dig deeper.

If the system spontaneously stopped working, the logs would show it if I dug back far enough.

Low and behold at 7pm this evening (about 6 hours ago) my syslog started spitting out this:

Mar 26 16:59:56 pergamon lircd-0.8.6[3691]: accepted new client on /var/run/lirc/lircd
Mar 26 16:59:58 pergamon kernel: [6057235.488118] lirc_zilog: IR TX chip never got ready: last i2c_master_send failed with -121
Mar 26 16:59:58 pergamon kernel: [6057235.488122] lirc_zilog: sending to the IR transmitter chip failed, trying reset
Mar 26 16:59:58 pergamon kernel: [6057235.600855] lirc_zilog: i2c_master_send failed with -121
Mar 26 16:59:58 pergamon kernel: [6057235.600859] lirc_zilog: sending to the IR transmitter chip failed, trying reset
Mar 26 16:59:58 pergamon kernel: [6057235.716540] lirc_zilog: i2c_master_send failed with -121
Mar 26 16:59:58 pergamon kernel: [6057235.716544] lirc_zilog: sending to the IR transmitter chip failed, trying reset
Mar 26 16:59:58 pergamon kernel: [6057235.823289] lirc_zilog: i2c_master_send failed with -121
Mar 26 16:59:58 pergamon lircd-0.8.6[3691]: write failed
Mar 26 16:59:58 pergamon kernel: [6057235.823293] lirc_zilog: sending to the IR transmitter chip failed, trying reset
Mar 26 16:59:58 pergamon kernel: [6057235.823294] lirc_zilog: unable to send to the IR chip after 3 resets, giving up
Mar 26 16:59:56 pergamon lircd-0.8.6[3691]: accepted new client on /var/run/lirc/lircd
Mar 26 16:59:58 pergamon kernel: [6057235.488118] lirc_zilog: IR TX chip never got ready: last i2c_master_send failed with -121
Mar 26 16:59:58 pergamon kernel: [6057235.488122] lirc_zilog: sending to the IR transmitter chip failed, trying reset
Mar 26 16:59:58 pergamon kernel: [6057235.600855] lirc_zilog: i2c_master_send failed with -121
Mar 26 16:59:58 pergamon kernel: [6057235.600859] lirc_zilog: sending to the IR transmitter chip failed, trying reset
Mar 26 16:59:58 pergamon kernel: [6057235.716540] lirc_zilog: i2c_master_send failed with -121
Mar 26 16:59:58 pergamon kernel: [6057235.716544] lirc_zilog: sending to the IR transmitter chip failed, trying reset
Mar 26 16:59:58 pergamon kernel: [6057235.823289] lirc_zilog: i2c_master_send failed with -121
Mar 26 16:59:58 pergamon lircd-0.8.6[3691]: write failed
Mar 26 16:59:58 pergamon kernel: [6057235.823293] lirc_zilog: sending to the IR transmitter chip failed, trying reset
Mar 26 16:59:58 pergamon kernel: [6057235.823294] lirc_zilog: unable to send to the IR chip after 3 resets, giving up

Before this time there were no errors of this type.  Afterward they repeat for a while, and then stop when I try to reinstall my drivers.

I checked my symantec logs, I updated about 8 hours before this, and had recordings with proper lirc channel changes an hour before.  The update  wasn't the source of the fault.

I'm starting to seriously wonder if the transmitter is burned out on the PVR card...  "i2c_master_send failed with -121" sounds suspicious to me...

---

### Post by TrevorBradley on 2010-03-27
UPDATE: I've given up and went with a Phillips/Microsoft USBMCE remote.  Works great without any tweaking.

---

### Post by diskmaster23 on 2010-03-29
> **TrevorBradley said:**
> UPDATE: I've given up and went with a Phillips/Microsoft USBMCE remote.  Works great without any tweaking.

I actually just stopped using 9.10 and stayed with 9.04.

---

### Post by bloodqc on 2010-03-29
> **TrevorBradley said:**
> UPDATE: I've given up and went with a Phillips/Microsoft USBMCE remote.  Works great without any tweaking.

Does it come with a blaster? If so, do you know where I can get one?

---

### Post by mrplow on 2010-05-01
I updated the [SIZE="4"][[COLOR="Blue"]zilog.diff[/COLOR]]("http://pastebin.com/raw.php?i=sWwzYDeL")[/SIZE] patch to work in 10.04, its just a copy of the old diff with the changes from Jarod's lirc [[COLOR="Blue"]kernel driver git tree[/COLOR]]("http://git.kernel.org/?p=linux/kernel/git/jarod/linux-2.6-lirc.git;a=tree;f=drivers/input/lirc;hb=HEAD"), but with the includes from the old patch

```
sudo apt-get install lirc-modules-source
cd /usr/src/lirc-0.8.6/
sudo patch -p0 < ~/zilog.diff
sudo dpkg-reconfigure lirc-modules-source
```

---

### Post by Kheops_74 on 2010-05-02
I try your patch. i did the command + sudo modprobe lirc_zilog

Everything look good 

lsmod |grep lirc
lirc_zilog             13245  0 
lirc_i2c                5845  1 
lirc_dev                8890  4 lirc_zilog,lirc_i2c

ls -l lirc*
crw-rw---- 1 root root 61, 0 2010-05-02 10:43 lirc0
lrwxrwxrwx 1 root root    19 2010-05-02 10:43 lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    20 2010-05-02 10:43 lircd1 -> /var/run/lirc/lircd1


I still have this error:

irsend: command failed: SEND_ONCE blaster 1
irsend: hardware does not support sending

Do you know the problem? is it hardware.conf, lircd.conf or something else?

---

### Post by mrplow on 2010-05-02
> **Kheops_74 said:**
> ...
I still have this error:

irsend: command failed: SEND_ONCE blaster 1
irsend: hardware does not support sending

Do you know the problem? is it hardware.conf, lircd.conf or something else?

I could be your hardware.conf or lirc_zilog isn't working properly. Check which devices are created after you load lirc_zilog as well.
```
ls /dev/lirc*
```
If you load zilog with debug=1 what is your syslog output? Using the original patch I would get lirc_zilog: no device found messages.

```
tail -f /var/log/syslog
```
open a second terminal
```
sudo rmmod lirc_zilog
sudo modprobe lirc_zilog debug=1

```

relevant part of my hardware.conf
```
TRANSMITTER_MODULES="lirc_zilog"
TRANSMITTER_DEVICE="/dev/lirc0"
```

I only use lirc for blasting so I don't have lirc_i2c loaded

---

### Post by Kheops_74 on 2010-05-03
Ok. i unload lirc_i2c (sudo rmmod lirc_i2c) and modify the hardware.conf to remove lirc_i2c. I rebooted and it seems to work. 

What is the use of lirc_i2c?

Thanks MrPlow

---

### Post by Kheops_74 on 2010-05-14
Lirc was updated tonight. Guess what, it doesn't work anymore :-( I hate this soooo much.

I think the patch for lirc-zilog is not up to date for the new version. MrPlow, can you confirm???

When i did sudo dpkg-reconfigure lirc-modules-source i receive an error (bad something)

Thanks

---

### Post by tim273 on 2010-05-15
Same here, something was updated and it no longer works for me either.

---

### Post by mrplow on 2010-05-15
ya mine broke yesturday as well, on my other machine as well which doesn't have zilog but that was a slightly different reason.

 I had to remove the lirc source
sudo sudo apt-get install lirc-modules-source
sudo rm -rf /usr/src/lirc-0.8.6/

then reinstall it and apply the patch like before, the patch needed no changes

---

### Post by Kheops_74 on 2010-05-15
MrPlow, you're right. I forgot after uninstalling the module-source to do this command : sudo rm -rf /usr/src/lirc-0.8.6/

The hardware.conf and lircd.conf was screwed too by yesterday update.

Works again. You save Ubuntu again.

Thanks

K

---

### Post by TheHilikus on 2010-06-18
i can confirm also that this (mr plow's) method still works with 10.04
i had to change the IR Blaster mapping and the RC mapping: the ones specified in /etc/lirc/lircd.conf since the ones in the package don't work

---

### Post by WhiteHairedGeek on 2010-06-23
I just tried mrplow's instructions to get the PVR-150 IR Blaster working under 10.04: 

sudo apt-get install lirc-modules-source
cd /usr/src/lirc-0.8.6/
sudo patch -p0 < ~/zilog.diff
sudo dpkg-reconfigure lirc-modules-source

but I get these errors in my log file when I try to load it:

lirc_zilog: disagrees about version of symbol lirc_register_driver
lirc_zilog: Unknown symbol lirc_register_driver
lirc_zilog: disagrees about version of symbol lirc_register_driver

my kernel is:
Linux mythtv-dvr 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

and lirc version is:
0.8.6-0ubuntu4.1

Did something change between the post from TheHilikus and today? (June 23/10)

-----

OK Never mind - turns out my PVR-150 had hardware problems as well (old age I guess), so I replaced it with an HD-PVR and the recording and IR blasting work great in 10.04.

---

### Post by xternal on 2010-07-01
> **WhiteHairedGeek said:**
>  OK Never mind - turns out my PVR-150 had hardware problems as well (old age I guess), so I replaced it with an HD-PVR and the recording and IR blasting work great in 10.04.

How did you get the HD-PVR to work in 10.04. I cant get the IR-Blaster to work?

---

### Post by WhiteHairedGeek on 2010-07-01
xternal,

I followed these directions [http://www.mythtv.org/wiki/HD-PVR](http://www.mythtv.org/wiki/HD-PVR) and also had to d/l & rebuild the lirc_atiusb driver as well for my ATI Remote Wonder, so you'll need to rebuild the driver for any remote that you use with lirc.

---

### Post by xternal on 2010-07-09
I can't get the zilog drive to load in 10.04 Did you get the hd-pvr ir blaster working? 

Well the zilog driver loads, but it seems to not load properly.   Everyone else seems to get:
[ 234.267482] lirc_dev: IR  Remote Control driver registered, major 250 
[ 234.445062] lirc_zilog: Zilog/Hauppauge IR driver initializing
[ 234.455942] lirc_zilog: chip found with RX and TX 
[ 234.458513] lirc_dev: lirc_register_driver: sample_rate: 0 
[ 235.547832] lirc_zilog: Zilog/Hauppauge IR blaster firmware version 2.1.0 loaded 
[ 235.547870] lirc_zilog: initialization complete   

or something similar. All i get is:  

[ 4783.825105] lirc_dev: IR Remote Control driver registered, major 61 
[ 4783.827673] lirc_zilog: Zilog/Hauppauge IR driver initializing
[ 4783.829328] lirc_zilog: initialization complete  

And no /dev/lirc0 is created :(

---

### Post by Kheops_74 on 2010-10-16
Where i can find the lirc_zilog patch for Maverick 10.10?

---

### Post by Kheops_74 on 2010-10-21
Ok i solve my problem ([http://ubuntuforums.org/showthread.php?t=1598968](http://ubuntuforums.org/showthread.php?t=1598968)). Thanks

---

### Post by cctsurf on 2011-04-01
Is anyone looking at natty to see what is necessary to use our blasters when it is released?  I can only assume that we will need a patch for the lirc-modules-source, though I wonder if it may not even be that different, because the lirc version in natty is essentially the same as it is in maverick.
Thanks,
cctsurf

---

### Post by Kheops_74 on 2011-04-04
I don't try the Beta but i'm pretty sure it will be a mess again. Anybody tried it?

---

### Post by cctsurf on 2011-04-29
:D:DI haven't had the opportunity to try it, but I noticed that the zilog.ko driver was in the staging area of the modules for natty, so I'm hopeful that we may not need to fight so hard to have our blasters work!  :confused: I know my xbox remote is going to need some figuring out though.

---

### Post by Kheops_74 on 2011-04-29
I'm too afraid to update my box. Please let us know if it works.

---

### Post by Kheops_74 on 2011-04-30
Ok i did it. I move to Natty. Same problem with Lirc. I had to do the same thing. It works but it took time.

---

### Post by Dave M G on 2011-05-10
Kheops_74, can you be more explicit about the steps you took to get it to work in 11.04?

For me, whenever I try to patch zilog.diff, I get this error:

```
patching file drivers/lirc_zilog/lirc_zilog.c
(Stripping trailing CRs from patch.)
patching file drivers/Makefile
patch unexpectedly ends in middle of line
Hunk #1 FAILED at 136.
1 out of 1 hunk FAILED -- saving rejects to file drivers/Makefile.rej
```

---

