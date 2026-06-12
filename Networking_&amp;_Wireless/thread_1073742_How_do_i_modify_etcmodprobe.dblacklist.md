---
title: "How do i modify /etc/modprobe.d/blacklist"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Snypercell on 2009-02-18
Ubuntu 8.04.2 64Bit
  
new to Ubuntu. 
i need to disable the packaged driver because i have an Arethos internal card. How do i get to the file to blacklist it???

---

### Post by 505 on 2009-02-18
Press alt+F2 and type 'gksu /etc/modprobe.d/blacklist' Enter your password when asked.

---

### Post by Snypercell on 2009-02-18
nothing happened

---

### Post by deepclutch on 2009-02-18
hmm.blacklist seems not obeying your rules :D
--
make a file /etc/modprobe.d/00local and content as:
```
install module_name /bin/true
```
If you are new to GNU/Linux :
1)press ALT+F2 :enter without quotes :     _**gksudo gedit /etc/modprobe.d/00local **_
2)write the content with the module name.
3)save and exit.
for eg: I use nvidia proprietary 3D driver for graphics.I would like to blacklist "intel_agp" module.what I do is , "install intel_agp /bin/true" in 00.local file in /etc/modprobe.d and reboot to see if it is working.(you can check by invoking rmmod intel_agp for eg here).
from NEXT boot ,the module will not be loaded.

--
[http://wiki.debian.org/KernelModuleBlacklisting](http://wiki.debian.org/KernelModuleBlacklisting)

---

### Post by Snypercell on 2009-02-18
okay, so what do i put for module name, if i'm trying to get my wireless driver to not load? where do i put the file, so that it will allow me to name it with slashes, and do i just use text editor to content the file?
sorry to sound so stupid. just been trying for a while to get my wireless card working.

---

### Post by trepid666 on 2009-02-18
Hey, what wireless card do you have?

---

### Post by Snypercell on 2009-02-18
Atheros 802.11

---

### Post by Snypercell on 2009-02-18
> **Snypercell said:**
> Atheros 802.11

sorry Atheros 242x 802.11abg

---

### Post by trepid666 on 2009-02-18
have u checked this out? [http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

or this [http://ubuntuforums.org/showthread.php?t=795984&page=4](http://ubuntuforums.org/showthread.php?t=795984&page=4)

---

### Post by Snypercell on 2009-02-18
no thanks, i'll check it out really quick

---

### Post by smc18 on 2009-02-18
If you just want to open the file with a text editor, you can use vi (however I wouldn't recommend it to you at the moment) or you can use gedit

```
sudo gedit /etc/modprobe.d/blacklist
```

That should work if you just want to edit it.

---

### Post by cariboo on 2009-02-18
For graphical apps that need to be run as root use gksu. Press Alt-F2 then type:

```
gksu gedit /etc/modprobe.d/blacklist
```

If you are starting a graphical app from a terminal then you can use sudo.

Jim

---

### Post by trepid666 on 2009-02-18
All I need to do to edit modprobe.d/blacklist is type:

```
sudo gedit /etc/modprobe.d/blacklist
```

---

### Post by Snypercell on 2009-02-22
thanks guys. i think i blacklisted one too many times when setting up my wireless driver, so i was having to enable everytime i loaded. all good now.

oh and hey Trep,  Reverend Maynard ftw!!!!

---

### Post by viniosity on 2009-12-19
> **deepclutch said:**
> hmm.blacklist seems not obeying your rules :D
--
make a file /etc/modprobe.d/00local and content as:
```
install module_name /bin/true
```
If you are new to GNU/Linux :
1)press ALT+F2 :enter without quotes :     _**gksudo gedit /etc/modprobe.d/00local **_
2)write the content with the module name.
3)save and exit.
for eg: I use nvidia proprietary 3D driver for graphics.I would like to blacklist "intel_agp" module.what I do is , "install intel_agp /bin/true" in 00.local file in /etc/modprobe.d and reboot to see if it is working.(you can check by invoking rmmod intel_agp for eg here).
from NEXT boot ,the module will not be loaded.

--
[http://wiki.debian.org/KernelModuleBlacklisting](http://wiki.debian.org/KernelModuleBlacklisting)

Out of curiosity is there anything else you do to get your nvidia to work other than blacklisting intel_agp? I've successfully blacklisted the intel_agp module but I still can't get the nvidia driver to load.

Hardware is an Asus UL30VT-X1 with switchable graphics (intel/nvidia G210M)  Tried the latest nvidia driver, plus the beta driver, plus the cuda driver..

---

