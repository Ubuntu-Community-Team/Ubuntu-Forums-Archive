---
title: "Nvidia drivers sometimes work on Maverick"
date: 2011-03-15
forum: Multimedia Software
---

### Post by sharq1 on 2011-03-15
I installed Maverick, then updates, and then nvidia-current (with nvidia-current-modaliases and nvidia-settings). Then reboot, system loads, i can see Nvidia logo, log in and everything's fine till reboot - then there's no X at all, only console. xorg.conf is on place, unchanged, bud nvidia-current.ko disappears from /lib/modules/2.6.35-27-generic/updates/dkms/. Removing nvidia-* packages and installing them again helped - for next reboot. After second time reinstalling nvidia didn't help - nvidia-current.ko is on place, but i can't start X (no screens found), and when i try to load nvidia-current with modprobe i get: No such device. I tried with nvidia packages from ppa:ubuntu-x-swat/x-updates, but it's still the same. I also reinstalled system few times, but always same happen. My nvidia card is 8600M GT and Ubuntu is 10.10 x64. What can i do with it? I'm desperate - first time since few years I'm thinking about switching to Windows - don't let it happen :)

---

### Post by sharq1 on 2011-03-15
Update: Installed system again, and without installing any updates installed nvidia. It worked, but... It was quite laggy with compiz + docky. So I updated xorg related packages. And guess what? Same problem as before - no X. Please, help...

---

### Post by sharq1 on 2011-03-15
I believe i finally fixed this - by adding ignoreABI True to xorg.conf :D

So if anyone has similar problems, here's what worked for me:

kernel: 2.6.35-23.41
driver: nvidia 270.29
xorg update to 1.9.0
xorg.conf:
```
...
Section "ServerFlags"
    Option "ignoreABI" "True"
EndSection
```

---

### Post by sharq1 on 2011-03-18
Ok, it's getting really annoying - it was ok for a while, but it still happens from time to time. xorg.conf stays unchanged, what helps for next few reboots is:
```
apt-get --purge remove nvidia-*
```
and then
```
apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```
Before reboot i didn't mess up with configuration (only installed three python-wxtools related packages and thunderbird, but those shouldn't have any influence on nvidia). What can i do to make it stop?

---

### Post by sharq1 on 2011-03-25
bump

---

### Post by sharq1 on 2011-03-29
It still happens... Anyone?

---

