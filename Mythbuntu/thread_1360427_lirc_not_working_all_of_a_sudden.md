---
title: "lirc not working all of a sudden"
date: 2009-12-20
forum: Mythbuntu
---

### Post by davidstoll on 2009-12-20
I use a keyboard quite a bit, so I can't say for sure when it stopped working, but probably within the last week.

I noticed that in the Mythbuntu control panel, the option for the MCE remote is now "all mce remotes" rather than separate mce entries for "new" and "old" (for mce remotes).

Also my MCE transmitter isn't working.

I tried to stop and restart lirc.  I tried to reboot.  I checked the hardware.conf and lircd.conf and both seem fine.

When I run irw, I get command feedback.

Any suggestions?

---

### Post by newlinux on 2009-12-21
anything with your frontend logs around lirc? tried using your lirc with another app, like mplayer? has anything happened to .lirc config file?

I do know that later versions of LIRC combined the drivers for the old and new mce remotes into driver - so that may be why mythbuntu control panel only shows one option for MCE remotes - I know that doesn't help fix your problem, just a possible explanation.

---

### Post by davidstoll on 2009-12-21
Good idea.  I tried with vlc and mplayer and I got no response.  They did work before.

As far as the logs go...I'm not exactly sure what I'm looking for (inside the files).  It seems as though everything is still in ~/.lirc, but I can't be sure.  hardware.conf and lircd.conf seem to be intact.

Here is a pastebin of my mythfrontend.log (at least the most recent file).  1.5mb
[http://pastebin.com/m373765ba](http://pastebin.com/m373765ba)

Notice on line 3847, before this, lircd loaded successfully...
2009-12-20 13:08:09.064 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)

/dev/lircd exists, and so does /dev/lircd1
I also noticed that all of my ~/.lirc/* files are replaced and the old ones are backed up to *.old.  The originals have all of my customizations.  Moving them back doesn't help, but that shows that some update got me good.

What should I do next?

Thank you for your help!


> **newlinux said:**
> anything with your frontend logs around lirc? tried using your lirc with another app, like mplayer? has anything happened to .lirc config file?

I do know that later versions of LIRC combined the drivers for the old and new mce remotes into driver - so that may be why mythbuntu control panel only shows one option for MCE remotes - I know that doesn't help fix your problem, just a possible explanation.

---

### Post by newlinux on 2009-12-21
hmm, has me stumped.  what are the permissions on /dev/lircd?

```

ls -l /dev/lirc*

```

---

### Post by davidstoll on 2009-12-21
crw-rw---- 1 root root 61, 0 2009-12-20 03:39 /dev/lirc0
lrwxrwxrwx 1 root root    19 2009-12-20 22:22 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    19 2009-12-20 22:22 /dev/lircd1 -> /var/run/lirc/lircd




> **newlinux said:**
> hmm, has me stumped.  what are the permissions on /dev/lircd?

```

ls -l /dev/lirc*

```

---

### Post by newlinux on 2009-12-22
can you post the contents of your hardware.conf file? I'm curious what your REMOTE_DEVICE line is equal to...

---

### Post by kadafi69 on 2009-12-22
oddly, mine has been randomly working, some days i'll turn on the pc and the remote will work fine, then other times there is just nothing.

---

### Post by davidstoll on 2009-12-22
My transmitter and remote both don't work.  Here is my hardware.conf

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="dish/general.conf"
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


> **newlinux said:**
> can you post the contents of your hardware.conf file? I'm curious what your REMOTE_DEVICE line is equal to...

---

### Post by newlinux on 2009-12-22
I'm afraid I'm out of ideas. And all of my machines using LIRC are on 8.04 so I can't investigate quite as much. But hopefully this post will provide a useful bump.

---

### Post by azmyth on 2009-12-22
I'd check your dmesg

dmesg | grep lirc

Also, try ircat

ircat mythtv

and then start hitting keys on the remote. If this works, then it's an issue with myth. If it doesn't work then try irw

---

### Post by bgiannes on 2009-12-23
this just happen to me?

the remote works with other programs xbmc, even the mythbackend but not the myth-frontend??

and when i try and exit frontend gets stuck on the exit screen?  lirc settings seem good.


EDIT:  it just started working??  after 45minutes it just fixed itself

---

### Post by bgiannes on 2009-12-24
well, after a reboot no remote again, but after using the ircat mythtv command mythtv remote starts working.

Why? help please.

---

### Post by davidstoll on 2010-01-02
Quick question, does your remote start working again after you exit the myth frontend and restart it?  If so, then you need to change the boot order of the frontend.  You need to put it towards the end so all the other processes (including lirc) can be fully initialized before the backend loads.

You do this by increasing the number of the myth backend process in the one of the /etc/rc#.d  Where # is some number.  I don't fully understand the system, but a linux friend of mine helped me do it.

Maybe someone here can explain it better, but...

If the myth process is in /etc/rc0.d and is named S20whatever, if you rename it to S99whatever, it will load later in the boot process...thus allowing lirc to fully load first.

I wonder if this didn't change in 9.10 because I'm not seeing that process in any of my rc#.d folders.  I did this back in 8.04.


> **bgiannes said:**
> well, after a reboot no remote again, but after using the ircat mythtv command mythtv remote starts working.

Why? help please.

---

### Post by gfowler on 2010-01-03
> **davidstoll said:**
> crw-rw---- 1 root root 61, 0 2009-12-20 03:39 /dev/lirc0
lrwxrwxrwx 1 root root    19 2009-12-20 22:22 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    19 2009-12-20 22:22 /dev/lircd1 -> /var/run/lirc/lircd

It looks as if both devices (lircd, lircd1) are pointing to the same devices, which is incorrect.  A change to /etc/init.d/lirc needs be made or install Jeremy Yoder's patch. See the thread below"

[http://ubuntuforums.org/showthread.php?p=8464899](http://ubuntuforums.org/showthread.php?p=8464899)

Of course the standard disclaimer applies, YMMV :)

Jerry

---

### Post by 1nsomnia on 2010-04-07
What is the solution? I have the same problem

---

### Post by MythKiller on 2012-09-15
I was able to fix the problem by unloading then reloading the lirc modules before starting mythfrontend.

```

sudo rmmod lirc_streamzap
sudo rmmod lirc_dev
sleep 1
sudo modprobe lirc_dev
sudo modprobe lirc_streamzap
mythfrontend

```Replace lirc_streamzap with whatever driver  you are using (ie, lirc_mce, etc.).  You can find out the name of your driver by running 'lsmod |grep lirc' from a shell.

---

