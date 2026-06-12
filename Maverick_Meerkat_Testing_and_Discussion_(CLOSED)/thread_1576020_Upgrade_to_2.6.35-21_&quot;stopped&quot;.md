---
title: "Upgrade to 2.6.35-21 &quot;stopped&quot;"
date: 2010-09-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2010-09-16
Maverick Beta running fine at 2.6.35-20 kernel level. Did sudo apt-get update, went O.K. sudo apt-get dist-upgrade ran along fine and then messages stopped appearing. Here's last few lines still on screen:

Setting up libvala-0.10-0 (0.9.8-1ubuntu1) ...
Setting up samba-common-bin (2:3.5.4~dfsg-1ubuntu6) ...
update-alternatives: using /usr/bin/nmblookup.samba3 to provide /usr/bin/nmblookup (nmblookup) in auto mode.
update-alternatives: using /usr/bin/net.samba3 to provide /usr/bin/net (net) in auto mode.
update-alternatives: using /usr/bin/testparm.samba3 to provide /usr/bin/testparm (testparm) in auto mode.
Setting up samba (2:3.5.4~dfsg-1ubuntu6) ...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
[cursor blinking here]

Hours later still at same state:

Trying to start synaptic results in: Unable to get exclusive lock
Same lock message if I try to do a dpkg --configure -a from another terminal session.

It's sitting there stuck, what do I do to end it gracefully? Same problem yesterday with same Maverick Beta levels. I killed the process and had a bad time getting it to boot again see bug #(will look it up later) where totally wrong screen resolution was used.

I tried ubuntu-bug aptitude because ubuntu-bug upgrade wouldn't work neither would ubuntu-bug update or ubuntu-bug apt-get.  Bug #for the upgrade stopping without finishing is 640733.

It's still sitting there, other things run but upgrade won't finish.

Jerry

---

### Post by cariboo on 2010-09-16
From the looks of your output, it's getting stuck installing the samba packages, so it probably isn't an apt/aptitude problem.

---

### Post by xebian on 2010-09-16
Boot back to terminal and then redo apt-get update && apt-get dist-upgrade.  It will start where it left off.  You might need to do apt-get -f install also.

---

### Post by MacUntu on 2010-09-16
Yeah, samba is an idiot.

---

### Post by jerrylamos on 2010-09-17
> **xebian said:**
> Boot back to terminal and then redo apt-get update && apt-get dist-upgrade.  It will start where it left off.  You might need to do apt-get -f install also.

Closed the "stuck" upgrade by selecting the X in the corner, shut down normally.

Rebooted in recovery mode.  Boot stops at:

Begin: Running/scripts/init-bottom ... done

as nearly as I can remember the line.  Nothing works except Ctrl-Alt-Del.

Will try to chroot in from this partition, another Maverick which hasn't been upgraded to 2.6.35-21 so it is still running.

Jerry

---

### Post by ronacc on 2010-09-17
try booting recovery mode or an earlier kernel and update again , the kernel is up to -22 now -21 didn't last long .

---

### Post by jerrylamos on 2010-09-17
> **ronacc said:**
> try booting recovery mode or an earlier kernel and update again , the kernel is up to -22 now -21 didn't last long .

I tried booting up -21, -20, -19 all stop at the same place, see previous note. Recovery mode or not, quiet or not, splash or not.  Can't run any update or get any command line or anything else.  Not being a developer it seems to me that whatever the stalled update had locked is still locked.

Other partitions work as usual.  On the launchpad bug #640733, someone found where in the scripts the failure occurs since they had the same thing.  They thought it was in apt-get.  No fix yet...

Hmmm.  Thanks anyway,

Jerry

---

### Post by wilee-nilee on 2010-09-17
From grub with the ethernet plugged in choose recovery then net-root at the menu and run these commands.

```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```      

This should get the packages loading again, I don't remember if you actually need the sudo I don't think so, but I posted the commands that would normally be run in a regular terminal.

Now this net-root needs the ethernet plugged in if you want web access.

---

### Post by jerrylamos on 2010-09-17
> **wilee-nilee said:**
> From grub with the ethernet plugged in choose recovery then net-root at the menu and run these commands.

O.K., I chose recovery, never ever gets to the menu because boot hangs before it ever gets there.  As far as it goes is:

Begin: Running/scripts/init-bottom ... done

So I had a script from Starks to chroot from another partition:
#!/bin/bash
mount --bind /dev /media/MeerkatBeta/dev
mount --bind /proc /media/MeerkatBeta/proc
mount --bind /sys /media/MeerkatBeta/sys
mount --bind /dev/pts /media/MeerkatBeta/dev/pts
cp /etc/resolv.conf /media/MeerkatBeta/etc/resolv.conf
chroot /media/MeerkatBeta
exit #
which worked so I did a sudo dpkg --configure -a which ran and ran and ran, got failures with software center and ubuntu-desktop and AppArmor.

However I'm booted up now O.K.

Thanks for the hints, everyone.

Jerry

---

### Post by jerrylamos on 2010-09-17
Tried the next update to -22 using Update Manager.  It worked.  No stops.

Jerry

---

