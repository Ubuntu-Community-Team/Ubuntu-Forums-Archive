---
title: "Wine and my DVDRom drive not detected"
date: 2011-04-30
forum: Multimedia Software
---

### Post by BULLIT22 on 2011-04-30
Hey Guy and Gals,

Got a little bit of a problem with Wine not seeing my DVDRom drive and will not let progs run under Wine to open DVD's. On another machine the BDRom drive sees and works fine with Wine progs. Looks like I'm missing a D:: link to a block device and D: which looks like a symlink. Anyone know an easy fix for this. Thanks,

BULLIT

---

### Post by mc4man on 2011-04-30
There are probably several ways - had a bug on this last year I could look up if you want
To me the easiest way is just to go back to using  a static mountpoint and  the typical fstab entry for cd/dvd drives

To do that - Ex. for drive at /dev/sr0
```
sudo mkdir /media/cdrom0
```
```
sudo gedit /etc/fstab
```
Add this line at bottom on a new line
```
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0
```

restart

Edit: if needed - to check what /dev/sr[COLOR="Red"]X[/COLOR] the drive is 
```
sudo lshw -C disk
```
look for drive in *-cdrom section

---

### Post by BULLIT22 on 2011-04-30
You da Boss. Thanks. That worked, All that was left was for me to add the D: drive in Wine and point it to the created directory. Thanks again.

---

### Post by mc4man on 2011-04-30
The other side advantage here, while there were workarounds, is that there will be no security bit issues with any .exe on a cd or dvd, the mount options in fstab take care of that (,exec

---

### Post by BULLIT22 on 2011-04-30
Good to know, Thanks.

---

### Post by rickyrockrat on 2011-09-16
Here's a simpler way, and a few more steps. You do *NOT* need to reboot- that's a Windows problem.

```
sudo mkdir /media/cdrom0
```
```
echo "/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0" |sudo tee -a /etc/fstab
```
```
cd ~/.wine/dosdevices
ln -s /media/cdrom0 e:
```
```
mount /media/cdrom
```

---

