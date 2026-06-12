---
title: "Need help configuring MCE compatible Remote and Myhtbuntu"
date: 2012-07-15
forum: Mythbuntu
---

### Post by SuperFreak on 2012-07-15
I am setting up a Mythubuntu HTPC on my HP Pavillion DV-7 laptop. I thought that my Harmony 650 remote configured as a MCE remote in conjunction with a MCE compatible receiver would work out of thew box but Mythbuntu is not responding to the remote. I am out of my depth doing this on my own could someone please help. Here is out put of lsusb:


$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 064e:e258 Suyin Corp. 
Bus 004 Device 002: ID 138a:0018 Validity Sensors, Inc. 
Bus 007 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver



I should point out that the remote and receiver work in Windows 7 for MCE and XBMC

Additional info: I found Mythbuntu Control center and enabled MCE remote/tranceiver. the receiver blinks red when i send a command but Mythbuntu does not respond

---

### Post by anonymousdog on 2012-07-15
Start with irw and see how lirc is interpreting the remote's signals.

---

### Post by SuperFreak on 2012-07-15
Thanks,

It produces no out put in terminal . I presume that means that I have to put a Lirc file in /etc directory. I will have a look at this this afternoon.

Edit: Had a look at lircd.conf on my laptop and it is basically empty no commands just comments. There is a file called hardware.conf that appears to have code in it but I am not sure what this means

---

### Post by SuperFreak on 2012-07-15
I read the instructions at [http://www.mythtv.org/docs/mythtv-HOWTO-8.html](http://www.mythtv.org/docs/mythtv-HOWTO-8.html)  about using ```
irrecord myremote
```  but I am not sure where to go from there. Here is output:


```
david@david-HP-Pavilion-dv7-Notebook-PC:~$ irrecord myremote

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
david@david-HP-Pavilion-dv7-Notebook-PC:~$ 
```

---

### Post by anonymousdog on 2012-07-15
So, you're basically trying to engineer an IR repeater?

To generate the config file, try 'irrecord -d /dev/lircd mce_device.conf'

When complete, you'll want to copy the conf file created to 
/usr/share/lirc/extras/transmitters/ and include it into your existing /etc/lirc/lircd.conf file by adding something like:
```
#Configuration for the MCE compatible devices:
include "/usr/share/lirc/extras/transmitters/mce_device.conf"

```
to the bottom.

Now, restart lirc: 'sudo service lirc restart'.

If you, prior to these changes, you really DID follow through all the steps in the MCC to setup normal MCE use (including setting up any STB transmitter) and hit Apply (in the MCC), you should have a working transmitter for whatever MCE-compatible device it is you're controlling.

You'll still have to setup scripts to actually *use* it (i.e. irsend, irexec, etc.).

---

### Post by SuperFreak on 2012-07-15
@anonymousdog
> So, you're basically trying to engineer an IR repeater?


I am a novice, I really just wanted to get my remote to control Mythubuntu and had thought that if I selected "Enable Remote Control" under Myth Control Center>Infrared Remotes and Transmitters and selected "Windows Media Center Tranceivers and Remotes " it might just work from those settings. I am at this point quite lost although I appreciate your encouragement .


I had originally followed thse instructions from [http://forums.whirlpool.net.au/archive/1362578]("http://forums.whirlpool.net.au/archive/1362578")

> All I did was go to the Mythbuntu Control Center --> InfraRed, enabled the remote and set it to be a Windows Media Center Transceiver. I then enabled the IR Transmitter and set it to be a Windows Media Center V2 USB.

Thanks. It seems to be just what I needed. I was trying to use the Hauppage options.
cheers

I am unclear on the last part of enabling IR TRansmitter as there are several entries for "Windows Media Center V2 USB" but they all seem to be cable or satelletite Set Top Boxes. I tried them all to no avail

---

### Post by anonymousdog on 2012-07-15
I see.  Forget all my prior advice, then.  You aren't trying to control any 3rd party devices (like satellite receiver set top boxes or similar)?

So, the Logitech *itself* has options in the firmware to emulate an MCE-compatible remote?  If that doesn't work "out of the box" with the MCC-produced 'Windows Media Center remotes' setup, either you're not doing it right, or the remote is not 100% emulating the MCE remotes.

If you use the Logitech's standard firmware profile, I *think* you'd have a hybrid setup where you'd want to use the mceusb and lirc_dev drivers (as per the typical setup produced by the MCC with a 'Windows Media Center' remote setup) but will have to use the hardware configuration file for the Logitech in at least one of or both the configuration files in /etc/lirc/.  I'd start by adding it to the /etc/lirc/lircd.conf file (as suggested above):
```
#Configuration file to use a Logitech remote
include "/usr/share/lirc/remotes/logitech/lircd.conf.logitech"
```
Restart lirc and try irw (and some key presses) again.

If that doesn't work, I'd change the
```
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
```
line in /etc/lirc/hardware.conf to
```
REMOTE_LIRCD_CONF="logitech/lircd.conf.logitech"
```

That *should* do it, but it's really just an educated guess.  Either way, just make sure to backup any config files you might change before making edits, and there's nothing you can't undo...low risk.

If it gets to be an "issue" the whole MCE remote/transceiver/blaster packages are pretty cheap online.

---

### Post by SuperFreak on 2012-07-16
Sorry to be dense about this , but to > use the hardware configuration file for the Logitech in at least one of or both the configuration files in /etc/lirc/. I'd start by adding it to the /etc/lirc/lircd.conf file  do I just copy and paste your code ```
#Configuration file to use a Logitech remote
include "/usr/share/lirc/remotes/logitech/lircd.conf.logitech"
``` into my terminal.

---

### Post by anonymousdog on 2012-07-16
Yes....well, no.  It looks like that's a config file for a very old Logitech remote.  We'd need a config file for the Logitech remote you have.  I think the process is the same as above.

---

### Post by SuperFreak on 2012-07-16
I appreciate your help. This problem perplexes me as other Mythbuntu users appear  to be using the Harmony 650 remote using MCEUSB setting in Mythbuntu and the remote device setup. I will search the internet a little longer for an answer. I originally was going to wipe my Win 7 install and use only Mythbuntu I'm glad it's a dual boot as I can still use XBMC on Win 7 and the remote works with no issues

---

### Post by anonymousdog on 2012-07-16
It looks like some folks have successfully used it with a standard MCEUSB lirc setup (as in what the MCC would produce) and the 650 setup with a MCE SE 'profile'.  I've never setup one of these Harmony remotes, but it looks workable if not perfect.  That said, it's not one of the preferred or popular solutions.  [http://www.mythtv.org/pipermail/mythtv-users/2012-March/328985.html](http://www.mythtv.org/pipermail/mythtv-users/2012-March/328985.html)

---

### Post by SuperFreak on 2012-07-16
I am probably going to give up on Mythbuntu and reformat that partition to NTFS. I had problems in other areas including audio output. I realize that with enough tinkering I could get it to work but Win MCE and XBMC under Win 7 worked fairly easily with few if any  of the problems I encountered with Myth.

---

