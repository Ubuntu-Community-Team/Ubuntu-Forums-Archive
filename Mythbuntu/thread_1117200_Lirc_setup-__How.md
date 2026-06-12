---
title: "Lirc setup-  How?"
date: 2009-04-05
forum: Mythbuntu
---

### Post by itlarson on 2009-04-05
I am attempting once again to get my Home Electronics tira-2 usb Ir receiver to work.  I first tried it over a year ago with a suse myth box.  Now I am running mythbuntu, and thought I would try it again, since the forums are better.  My goal is to use my Sony universal remote.  It can be set to emulate a Sony DVD remote, for which a config file exists. 
   Heres what I have so far:  It is installed, and shows up as "Bus 001 Device 004: ID 0403:fa78 Future Technology Devices International, Ltd"  when I use lsmod.  There is no /dev/lirc, though.  That's basicly it.  No good documentation for lirc seems to exist, so I am hoping someone knows enough about it to help me.

---

### Post by AlecJ on 2009-04-05
read this thread
[http://ubuntuforums.org/search.php?searchid=57568066](http://ubuntuforums.org/search.php?searchid=57568066)

But I think as it's USB input it will be seen as a keyboard, you may have to select a remote that uses a usb like the MCE Philips in Myth Control Centre, then if you run "irw" in a terminal and can see codes appear when you press a button on the remote, then you can map the codes to the files.

---

### Post by boof1988 on 2009-04-05
If you're not able to get it working using one of the pre-installed configurations, maybe try [*mythbuntu-lirc-generator*](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mythbuntu-lirc-generator)

---

### Post by itlarson on 2009-04-06
I'll need way more info than that.  What does mythbuntu-lirc-generator do?  I still don't have /dev/lirc, which seems to be the first prerequisite.

---

### Post by azmyth on 2009-04-06
There's actually some information in the PDF manual to at least get you started.

[http://www.mythbuntu.org/documentation/mythbuntu_8.10_installation.pdf](http://www.mythbuntu.org/documentation/mythbuntu_8.10_installation.pdf)

---

### Post by newlinux on 2009-04-06
post your /etc/lirc/hardware.conf file. I think it should be using the "tira" driver, and from what I've seen you will want to make the device "/dev/ttyUSB0"

Then restart lirc and hopefully you'll be able to use irrecord at that point to generate an lircd.conf for that remote.

---

### Post by newlinux on 2009-04-06
I should add that you should confirm your device - I guess it could be /dev/ttyUSB1 or something.

```

ls -l /dev/ttyUSB*

```

The irrecord line you'll could try is:
```

irrecord --driver=tira --device=/dev/ttyUSB0 lircd.conf

```

replacing device with the appropriate device... if you want to generate a config file or just copy over the one you have and hopefully irw will give you output after restarting lirc.

---

### Post by schmidtbag on 2009-04-06
I don't use a USB receiver but I had a similar issue with my TV tuner.  I don't have a lirc device either, and none of the tty* stuff works.  For me, my remote is considered /dev/input/event6.  This didn't add full functionality to mine (I'm actually on the forums looking for an answer) but it got me more progress than anything else has.  Maybe yours is an event too.  I found this out using "lshal |less".  Try finding the name of your remote and it will show what device it is.

---

### Post by itlarson on 2009-04-06
Thanks for the tips, they seem like they might help.  I will look into this when I get home tonight.  How do you restart lirc?

---

### Post by schmidtbag on 2009-04-06
I just realized I'm wrong about my post, it turns out installing "inputlirc" is what made the difference for me but it still doesn't help.

I couldn't figure out how to restart lic.  I know you can kill it, but its a background process.  I know you can start it by doing "sudo lircd", but I just retart it by restarting the computer.

---

### Post by newlinux on 2009-04-06
```

sudo /etc/init.d/lirc restart

```

should restart lirc.

---

### Post by itlarson on 2009-04-06
Darn, I had it, but I lost it.  I got "sudo irrecord --driver=tira --device=/dev/ttyUSB0 lircd.conf"  to work for a few key presses, then exited because I wanted to start over.  The key presses had been recorded in lircd.conf.  But when I started it again, I just got an error message:

[HTML]itl@mythbox:~/Config$ sudo irrecord --driver=tira --device=/dev/ttyUSB0 lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: unexpected response from device
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
itl@mythbox:~/Config$ 
[/HTML] 

restarting lirc with "sudo /etc/init.d/lirc restart" has no effect.  What permissions should I check? 


Here's  /etc/lirc/hardware.conf:

[HTML]# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="tira"
REMOTE_MODULES=""
REMOTE_DRIVER="tira"
REMOTE_DEVICE="/dev/ttyUSB0"
REMOTE_LIRCD_CONF=""
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
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""
[/HTML]

---

### Post by newlinux on 2009-04-06
try stopping lirc first

```

sudo /etc/init.d/lirc stop

```
then run irrecord.

After you are done, you can copy lircd.conf file into the right place and then start lirc

```

sudo /etc/init.d/lirc start

```

then you can test the key presses using irw. If that checks out, then all you need to do is make a lircrc file...

---

### Post by itlarson on 2009-04-07
It's still doing the same thing, even after a reboot.  Not convinced that this hardware is working right.  Maybe I'll stop at Microcenter on the way home, and look at remotes.

---

### Post by newlinux on 2009-04-07
Hmmm... you might want to verify that it is still on /dev/ttyUSB0 (it could move). Also you might want to make sure LIRC isn't running even after the stop command (maybe something stopped it from stopping? :) You may need to explicitely kill the process (although I don't have to on my machine). or maybe some other program has grabbed the remote input (irxevent or something or other)...  Unfortunately that's about the end of my knowledge on this...

---

### Post by itlarson on 2009-04-08
To update- I have given up on the tira.  I purchased an off brand mce remote, and it pretty much just works.  The only problem is the receiver hangs when I reboot-  it's indicator light is constantly on, and it doesn't receive.  It needs to be plugged in after the computer starts, and mythfrontend must be re-started.  Anyway- thanks for all the help.

---

