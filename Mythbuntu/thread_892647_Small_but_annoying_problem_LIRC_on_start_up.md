---
title: "Small but annoying problem LIRC on start up"
date: 2008-08-17
forum: Mythbuntu
---

### Post by roundhay on 2008-08-17
I have managed to get a working installation of Mythbuntu 8.04, every seems to be working but I have one small issue that I would like to sort out.

When MythTv first opens the remote control does not work, I have to close MythTV go to the Myth Control Center and untick the remote option from inrared devices and uninstall the infra red device. I then have to reinstall the infra red device. Once this is done and I reopen the front end the remote control works.

Any idea how I can get the remote to work from start up?

Cheers!

---

### Post by Neon Dusk on 2008-08-17
Have you got more than 1 lirc device (ls /dev/lirc*). If you have then maybe the device order is changing on startup - udev should be able to fix this.

---

### Post by roundhay on 2008-08-17
the output from ls /dev/lirc* is

/dev/lirc0 /dev/lircd

looks like I just have the one device?

---

### Post by Neon Dusk on 2008-08-17
Yes it does - looks like it's a different problem to the one I had.

---

### Post by superm1 on 2008-08-17
> **roundhay said:**
> I have managed to get a working installation of Mythbuntu 8.04, every seems to be working but I have one small issue that I would like to sort out.

When MythTv first opens the remote control does not work, I have to close MythTV go to the Myth Control Center and untick the remote option from inrared devices and uninstall the infra red device. I then have to reinstall the infra red device. Once this is done and I reopen the front end the remote control works.

Any idea how I can get the remote to work from start up?

Cheers!
Post some more details about your setup, particularly:

1) /etc/lirc/hardware.conf
2) /etc/lirc/lircd.conf
3) If it's not apparent already, what remote you are intending on using.

---

### Post by roundhay on 2008-08-17
I am using the 'Windows Media centre remotes (new version Philipis et al.)

I have attached copies of my hardware.conf & lircd.conf files.

I have also noticed that when shut down Mythbuntu I see some scripts, the first two lines are:

Loading Modules                   [OK]
Starting Remote Control Deamons   [Fail]

Not sure if this is relevant?

Hope you can help

---

### Post by roundhay on 2008-08-18
Hope someone can help me figure this out?

---

### Post by superm1 on 2008-08-18
Those configs look pristine.  Have you modified anything by hand that might be causing multiple lirc instances to start?

You might have to just start modifying the lirc init script (/etc/init.d/lirc) to figure out where it's failing.

---

### Post by roundhay on 2008-08-18
Ok I remembered that I ran ls /dev/lirc* yesterday after i had uninstalled and reinstalled the IR device in Mythbuntu control center.

After I switched on the HTPC this evening I ran ls /dev/lirc* before the unistall / reinstall and I got the following output:

  /dev/lirc0  /dev/lirc1  /dev/lircd

It looks like i have 2 devices after initial start up, one my be the IR receiver of the silverstone case I have, can with an imon

if this is the problem how can i fix it?

---

### Post by superm1 on 2008-08-19
> **roundhay said:**
> Ok I remembered that I ran ls /dev/lirc* yesterday after i had uninstalled and reinstalled the IR device in Mythbuntu control center.

After I switched on the HTPC this evening I ran ls /dev/lirc* before the unistall / reinstall and I got the following output:

  /dev/lirc0  /dev/lirc1  /dev/lircd

It looks like i have 2 devices after initial start up, one my be the IR receiver of the silverstone case I have, can with an imon

if this is the problem how can i fix it?
Well this is the exact cause of your problem.  You've got a handful of possible solutions.

If you aren't planning on using that IR receiver at all, go and blacklist it's module.  I believe it's lirc_imon, but you'll have to verify on startup.

---

### Post by Neon Dusk on 2008-08-19
If you don't want to blacklist the imon module (I never tried as I thought it would stop my Antec VFD from working) then the following may help.

[Link - Device Filenames and udev](http://www.mythtv.org/wiki/index.php/Device_Filenames_and_udev)

Basically you would use :-
sudo udevinfo -a -p $(udevinfo -q path -n /dev/lirc0)
sudo udevinfo -a -p $(udevinfo -q path -n /dev/lirc1)

to find unique differences between the lirc devices and then get udev to create a consistent symlink

For my Antec Fusion case (imon) and using the Microsoft IR receiver I created the following rule in /etc/udev/rules.d/10-local.rules 
```

#lirc
# imon - Lirc
KERNEL=="lirc[0-9]*", SUBSYSTEMS=="usb", ATTRS{idVendor}=="15c2", ATTRS{idProduct}=="ffdc", SYMLINK+="lirc101"

#mceusb - Lirc
KERNEL=="lirc[0-9]*", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0471", ATTRS{idProduct}=="0815", SYMLINK+="lirc102"

```

Then changed /etc/lirc/hardware.conf to use 
REMOTE_DEVICE="/dev/lirc102"

---

### Post by roundhay on 2008-08-19
Thanks this worked perfectly!

I even had the same identifiers as you!!!

Very useful.....

---

### Post by Neon Dusk on 2008-08-22
If your IR receiver is the same as the one on the Antec then it's possible to use MCE remote with it and do away with the mceusb receiver (I just got this set-up the other day). 

You need to make a new lirc remote file but if you let me know I'll pass on the one I created.

Edit: The imon IR receiver isn't as sensitive as the mceusb but it works fine for me.

---

### Post by davidstoll on 2009-10-15
For those that don't have udevinfo...

"udevadm info" should do the same thing for you.

sudo udevadm info -a -p $(udevadm info -q path -n /dev/lirc0)
sudo udevadm info -a -p $(udevadm info -q path -n /dev/lirc1)

---

### Post by ddolympia on 2009-10-20
> **Neon Dusk said:**
> If your IR receiver is the same as the one on the Antec then it's possible to use MCE remote with it and do away with the mceusb receiver (I just got this set-up the other day). 

You need to make a new lirc remote file but if you let me know I'll pass on the one I created.

Edit: The imon IR receiver isn't as sensitive as the mceusb but it works fine for me.

Hi, Neon Dusk,

I'm trying to set up my system with Antec case the same as you mentioned above.  I don't really care to have a USB IR receiver sitting beside my case, when the iMon should work fine with the MCE remote.  I know its been over a year since you added this thread, but if you still have the remote file, I would love to see a copy of it.

I'm currently at Mythbuntu 9.04 with the trunk to myth 0.22 installed.  This version is supposed to properly recognize the iMon receiver (which it does), but I still haven't gotten the MCE remote to work with it yet.

I will greatly appreciate any help you can provide.

Don D.

---

### Post by djroketboy on 2009-11-24
I'm in a similar boat, but i just start 2 instances of lirc. I actually came here to see if there was an easy way to have them run at startup (i know how in RedHat, but not Ubuntu)

I manually stop lirc
```
sudo /etc/init.d/lirc stop
```
and run
```
sudo /usr/sbin/lircd --driver=default --device=/dev/lirc0 --pidfile=/var/run/lirc0.pid --listen=8765
sudo /usr/sbin/lircd --driver=default --device=/dev/lirc1 --pidfile=/var/run/lirc1.pid --output=/dev/lircd --connect=localhost:8765
```

If anyone know's how I can get these to run at startup, this possibly might help the OP getting both his MCE remote and VFD running at the same time as well.

EDIT:
Ok, well I guess all I had to do was post here for me to figure it out.
Create a file called "lirc.custom" (or whatever you want) /etc/init.d/ directory; add the 2 lines from above.

$ sudo update-rc.d lirc.custom defaults

$ sudo chmod +x lirc.custom

This last part, i'm not sure if it's a good idea, but I removed the old lirc startup
$ sudo update-rc.d lirc remove

---

### Post by Neon Dusk on 2009-11-26
@ddolympia

I missed this post but I've put the config I use [thread=1337815]here[/thread].

---

