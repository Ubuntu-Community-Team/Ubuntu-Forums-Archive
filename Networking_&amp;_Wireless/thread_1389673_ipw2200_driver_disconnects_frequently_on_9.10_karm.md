---
title: "ipw2200 driver disconnects frequently on 9.10 karmic koala"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Hoobes1 on 2010-01-24
Hi, recently, my ipw2200 w-lan driver's been disconnecting frequently and I've done some research on it, while seeing that it's been a frequent problem, in the past. However, I can't seem to find a tutorial that I can understand, for fixing this issue. 
Any help is greatly appreciated! 
Thanks =)

---

### Post by mikitz on 2010-02-28
If you have a Linksys router, try installing the [tomato firmware]("http://www.polarcloud.com/tomato"). I have heard reports this fixes the problem. I could not get the ipw2200 working reliably with a dlink router.


Go to a terminal and type in:
```
dmesg|grep error
```
Do you see a line that says: ipw2200: Firmware error detected. Restarting.
?
If so I suspect it is the same problem as [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352150")

It seems that IBM is aware of this problem if you go to [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/) under the heading "diversity algorithm causing disassocaition"... I think this is the same issue.

---

### Post by Hoobes1 on 2010-03-01
thanks for the reply! This is what I've gotten out of the command. 
```

[    0.811089] ahci: probe of 0000:00:1f.2 failed with error -22
[   36.625872] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   36.771186] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   38.256187] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   38.315074] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   38.340140] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   38.411224] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00

```

---

### Post by Majino on 2010-03-01
> **Hoobes1 said:**
> Hi, recently, my ipw2200 w-lan driver's been disconnecting frequently and I've done some research on it, while seeing that it's been a frequent problem, in the past. However, I can't seem to find a tutorial that I can understand, for fixing this issue. 
Any help is greatly appreciated! 
Thanks =)

got the same problem... with network manager i can connect but i get disconnected randomly... it's strange, sometimes i can connect for hours, sometimes for minutes... 
Wireless Card: Intel 2200/BG with ipw2200 driver and ubuntu karmic 9.10

edit: with dmesg|grep error i get no output...

---

### Post by Majino on 2010-03-02
anyone knows if in the 10.4 alpha3 the problem is solved?? :)

---

### Post by tomerzz on 2010-05-28
this problem is not solved and has been going on for ages :(
i've had this issue since a kernel upgrade on 8.10 (was ages ago, can't remember which) and it continues on 10.04 . i've also tried using Fedora live CD versions 12 & 13 and got the same message. 
this must be an issue with the linux kernel & ipw2200 driver . 
running on T42

---

### Post by Hoobes1 on 2010-05-28
oh, that sucks. Oh well, thanks for telling me this :)

---

### Post by Hoobes1 on 2010-05-28
> **tomerzz said:**
> this problem is not solved and has been going on for ages :(
i've had this issue since a kernel upgrade on 8.10 (was ages ago, can't remember which) and it continues on 10.04 . i've also tried using Fedora live CD versions 12 & 13 and got the same message. 
this must be an issue with the linux kernel & ipw2200 driver . 
running on T42

that's too bad. Thanks for telling me though! :)

---

### Post by tomerzz on 2010-05-28
i can confirm that on kernel 2.6.27-7 , running Ubuntu 8.10 
i did not have this problem. I've checked and double checked all ipw2200 pararmeters on both versions (8.10 and 10.04) and they are exactly the same, using the same ipw2200. It must be something with the newer kernel

---

### Post by tomerzz on 2010-06-04
couldn't stand it anymore. downgraded to 8.10 , no more errors & network freeze

---

### Post by kingmoffa on 2011-09-25
Does anyone know if this issue has been fixed in any recent ubuntu? (or other distro)

Its driving me up the wall.

---

### Post by tomerzz on 2011-09-25
after trying various linux distributions, i could only conclude this has to do with the kernel. 
this hardly happens with kernel 3.0.0-0300rc2 . give it a try

---

### Post by kingmoffa on 2011-09-26
thanks for the reply. 

Did you install the new kernel via PPA or compile yourself?

---

### Post by tomerzz on 2011-09-26
PPA. give it a try

---

