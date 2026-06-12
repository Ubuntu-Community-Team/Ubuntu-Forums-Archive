---
title: "old isa card activation problem"
date: 2006-01-12
forum: Multimedia &amp; Video
---

### Post by macsimski on 2006-01-12
the onboard sound of my computer has a serious static problem so I placed a isa soundcard in stead. its a old PAS16 card with a extra scsi connector.

for that i had to relocate a pci ethernet card which generated another problem:
[http://ubuntuforums.org/showthread.php?p=651174#post651174]("http://ubuntuforums.org/showthread.php?p=651174#post651174")

anyway, there is a howto for old cards on the wiki. but it worked not for me


but after 
```
sudo modprobe pas2
``` (The code for the PAS16 card)
i get a error:
```
fatal: Eror inserting pas2 (/lib/modules/2.6.12.-10-387/kernel/sound/oss/pas2.ko): Invalid Argument
```

what went wrong? and how to fix it?

---

### Post by FarEast on 2006-01-12
Hi macsimski:) ,

I found a web with a description regarding your sound chip.
[http://public.planetmirror.com/pub/peanut/Peanut-Linux-9.2/](http://public.planetmirror.com/pub/peanut/Peanut-Linux-9.2/)

Give a try;) 

Describe the following in /etc/modprobe.d/sound
```
options pas2 io=0x388 irq=7 dma=1 dma16=10
```

Then
```
$ sudo update-modules
$ sudo modprobe pas2
$ cd /usr/share/sound/
$ cat startup.wav > /dev/dsp
```

Regards

---

