---
title: "Small Problem with sounds"
date: 2008-01-30
forum: Multimedia Production
---

### Post by DeeBoo on 2008-01-30
Hi guys ..


I have problem with my labtop with sounds 

I installed Ubuntu 7.10 everything worked fine but the only problem is that no sound works at all even login sound 

what is the problem and how I can solve it plz ? 

I have LG LS70 labtop

---

### Post by Creative2 on 2008-01-31
:) this board is for multimedia PRODUCTION 
there is multimedia board for that (only laptop)

[http://ubuntuforums.org/forumdisplay.php?f=135](http://ubuntuforums.org/forumdisplay.php?f=135)
or this for generic video\sound card
[http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)

---

### Post by polmir on 2008-01-31
Connect your computer to internet and type in terminal:
```
sudo update-pciids
```
 and post info out of this command
```
lspci | grep audio
```

---

### Post by DeeBoo on 2008-01-31
karkoom@karkoom-laptop:~$ sudo update-pciids
--07:03:19--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 129,826 (127K) [text/plain]

100%[====================================>] 129,826       58.23K/s             

07:03:21 (58.05 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [129826/129826]

Done.
karkoom@karkoom-laptop:~$ lspci | grep audio
karkoom@karkoom-laptop:~$ 



this what happened when I typed that tow lines

---

### Post by polmir on 2008-02-01
> **DeeBoo said:**
> 
```
 lspci | grep audio
```
this what happened when I typed that tow lines

This info about your audio controller.

---

