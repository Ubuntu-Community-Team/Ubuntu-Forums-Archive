---
title: "Buffalo NAS autopower"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by oscar69 on 2010-02-18
It works for me, and I like to know if it can be usefull to someone else.

[SIZE="3"]**_Obviously, use it at your own risk!_**[/SIZE]

_Background_
Some Buffalo NAS systems have an "Auto Power" mode: the NAS stays up&running while the (windows) pc is running. It's done with a (windows) service, always running, that send 3 (why 3?) wake-on-lan packets to the NAS every (about) 30 seconds.
When you shutdown the pc, the NAS stops receiving w-o-l packets, wait about 3 minutes, then shutdown itself.
The NAS will listen for incoming w-o-l packets: when it arrives, the NAS will go back up&running.
My Linkstation Quad needs about 3 or 4 minutes to go back on line. 

Thus, to replicate (and improve ...) this behavior, I used:
- autofs5 
- smbfs
- wakeonlan
- netcat
- a script (attached)

It will keep "live" the NAS on a per-use basis, rather than a pc-power basis:
autofs will do the dirt job of follow the user's needs of mount points, and the script I wrote will send the w-o-l packet when the mount points are used.

I used autofs5 because I cannot make working the installed version (autofs4): it never umount the unused share.

Here is what I did, not exactly a step-by-step guide, because I'm writing by memory...

- remove autofs4
- install autofs5
- install wakeonlan
- install smbfs
- install netcat (I don't remember if it is installe by default...)

- edit /etc/auto.master:
[INDENT]- comment out the line "+auto.master" (because of bug [bug #488696]("https://bugs.launchpad.net/ubuntu/+source/autofs5/+bug/488696"))
- add a line "/mnt/nas        /etc/auto.nas" 
```
#  +auto.master
/mnt/nas        /etc/auto.nas 
```
where the first is the mount point and the second is your configuration script
[/INDENT]


- edit /etc/default/autofs
  [INDENT]- set the TIMEOUT
    **** BE CAREFUL ABOUT TIMEOUT ****
    The only problem I had was relate to a very short timeout (about 10 seconds). While I was trying all configuration, and to speed up tests (:() I did a long series of powerup, timeout, powerup, timeout. I got an array corruption. I didn't loss data, but I needed to copy all data away, destroy array, and so on.
    So, I suggest you to set a very high timeout, not less than 10 minutes.
[/INDENT]


- copy auto.nas 
  [INDENT]- set parameters in top of file, and in last line of the script (YOUR_USERNAME,YOUR_GROUP,USER,PASSWORD). The last are used by autofs and smbclient to mount the share (look at man autofs....)
  This file sends the wol packets while the NAS is booting; it stop sending wol packets asap the share is available, not waiting more than the startup timeout you defined, if something goes wrong.[/INDENT]


  Then, mount the share.


- copy keep_alive.sh (I put it in /usr/local/sbin)
  [INDENT]- set parameters in top of file, just like in auto.nas file
  This script sends wol packets while the share is mounted. It must be started at startup of your pc. 
  I think I'll insert the correct call (start & stop) inside the autofs init script: it is needed running just while autofs is running, so...[/INDENT]


Now, start the keep_alive.sh, and start autofs.

My NAS have 2 shares: "SHARE" and "USBDISK"; I defined /mnt/nas as mountpoint.
Now, if all is correctly running, I can access /mnt/nas/share or /mnt/nas/usbdisk: after the NAS boot process (about 3-4 minutes) I'll see it.
After 10 minutes (or the timeout you set in /etc/default/autofs), the shares disappears.

I did it on Ubuntu 9.10, with Buffalo Linkstation Quad, but I think that all this can be used on other system and with other NAS (if them are wol capable...)

Any comment is appreciated!

Giulio

---

### Post by themadmax on 2011-03-16
Like windows service provied by Buffalo I do that

Download script
$ wget [http://themadmax.free.fr/nas/boulette](http://themadmax.free.fr/nas/boulette)
Copy script
$ sudo cp boulette /etc/init.d/
Download wake on lan script
$ wget [http://themadmax.free.fr/nas/wol.sh](http://themadmax.free.fr/nas/wol.sh)
Edit it, change MAC adresse
$ vim wol.sh
Copy it
$ sudo cp wol.sh /usr/bin
Install wakeonlan package
$ sudo apt-get install wakeonlan
If you want to start service to wake up NAS
$ sudo /etc/init.d/boulette start
If you want to start service automaticaly at start up
$ cd /etc/init.d
$ sudo update-rc.d boulette defaults

I'm do too a Android App for wake up NAS [http://bliquid.fr/2010/08/nas-wake-on-lan/](http://bliquid.fr/2010/08/nas-wake-on-lan/)

Et voila

---

### Post by Vincgofresh on 2011-08-16
Great job themadmax !!
I test your script on my buffalo linkstation, it's work great !
I'd just correct some things (**in bold**) :

$ wget [http://themadmax.free.fr/nas/boulette](http://themadmax.free.fr/nas/boulette)
Copy script
$ sudo cp boulette /etc/init.d/
**$ sudo chmod +x /etc/init.d/boulette**
Download wake on lan script
$ wget [http://themadmax.free.fr/nas/wol.sh](http://themadmax.free.fr/nas/wol.sh)
Edit it, change MAC adresse **and -i boulette by -i NAS_IP_ADDRESS**
$ vim wol.sh
Copy it
$ sudo cp wol.sh /usr/bin
**$ sudo chmod +x /etc/init.d/wol.sh**
Install wakeonlan package
....

Thanks a lot from a french guy !! :)

---

