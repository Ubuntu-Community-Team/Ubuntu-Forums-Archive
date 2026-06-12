---
title: "DVD won't Eject"
date: 2010-01-09
forum: Multimedia Software
---

### Post by lotusalive on 2010-01-09
acidrip hangs on this dvd, hangs on crop detect, and on preview, 

also, will not eject without restart.  Will someone please tell me 

what I might do to alleviate this Error Msg ?


```
Unable to eject CD-RW/DVD±RW Drive  DBus error 

org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible 

causes include: the remote application did not send a reply, the 

message bus security policy blocked the reply, the reply timeout 

expired, or the network connection was broken.
```

---

### Post by HappyFeet on 2010-01-09
This will not solve your problem, but
```
eject cdrom
``` will keep you from having to reboot.

---

### Post by lotusalive on 2010-01-09
Thanks Happy Feet, (one of my favorite danceable, singable, conductable, films, the other being the second version of Thomas Crowne Affair :)

```
 lightening@lightening-desktop:~$ eject cdrom
Error: invalid device /media/cdrom0 (must be in /dev/)
eject: unmount of `/media/cdrom0' failed
lightening@lightening-desktop:~$ 
```

Didn't work tho'.  Tried: 

```
lightening@lightening-desktop:~$ eject cdrom /dev/
eject: too many arguments
lightening@lightening-desktop:~$ /dev/ eject cdrom
bash: /dev/: is a directory
lightening@lightening-desktop:~$
```

And tried: 

```
lightening@lightening-desktop:~$ /dev/
bash: /dev/: is a directory
lightening@lightening-desktop:~$ dir /dev/
agpgart		    oldmem	sg1	  tty34		  usbdev1.2_ep00
audio		    parport0	sg2	  tty35		  usbdev1.2_ep02
autofs		    pktcdvd	sg3	  tty36		  usbdev1.2_ep81
block		    port	sg4	  tty37		  usbdev1.3_ep00
bus		    ppp		sg5	  tty38		  usbdev1.3_ep01
cdrom		    psaux	sg6	  tty39		  usbdev1.3_ep82
cdrw		    ptmx	shm	  tty4		  usbdev2.1_ep00
char		    pts		snapshot  tty40		  usbdev2.1_ep81
console		    ram0	snd	  tty41		  usbdev3.1_ep00
core		    ram1	sndstat   tty42		  usbdev3.1_ep81
cpu_dma_latency     ram10	sr0	  tty43		  usbdev4.1_ep00
disk		    ram11	stderr	  tty44		  usbdev4.1_ep81
dri		    ram12	stdin	  tty45		  usbdev5.1_ep00
dsp		    ram13	stdout	  tty46		  usbdev5.1_ep81
dvd		    ram14	tty	  tty47		  usbmon0
dvdrw		    ram15	tty0	  tty48		  usbmon1
ecryptfs	    ram2	tty1	  tty49		  usbmon2
fd		    ram3	tty10	  tty5		  usbmon3
full		    ram4	tty11	  tty50		  usbmon4
fuse		    ram5	tty12	  tty51		  usbmon5
hpet		    ram6	tty13	  tty52		  vcs
initctl		    ram7	tty14	  tty53		  vcs1
input		    ram8	tty15	  tty54		  vcs2
kmem		    ram9	tty16	  tty55		  vcs3
kmsg		    random	tty17	  tty56		  vcs4
log		    rtc		tty18	  tty57		  vcs5
loop0		    rtc0	tty19	  tty58		  vcs6
loop1		    scd0	tty2	  tty59		  vcs7
loop2		    sda		tty20	  tty6		  vcs8
loop3		    sda1	tty21	  tty60		  vcsa
loop4		    sda2	tty22	  tty61		  vcsa1
loop5		    sda5	tty23	  tty62		  vcsa2
loop6		    sda6	tty24	  tty63		  vcsa3
loop7		    sda7	tty25	  tty7		  vcsa4
lp0		    sdb		tty26	  tty8		  vcsa5
MAKEDEV		    sdb1	tty27	  tty9		  vcsa6
mapper		    sdc		tty28	  ttyS0		  vcsa7
mem		    sdd		tty29	  ttyS1		  vcsa8
mixer		    sde		tty3	  ttyS2		  watchdog
net		    sdf		tty30	  ttyS3		  xconsole
network_latency     sequencer	tty31	  urandom	  zero
network_throughput  sequencer2	tty32	  usbdev1.1_ep00
null		    sg0		tty33	  usbdev1.1_ep81
lightening@lightening-desktop:~$ 
```

---

### Post by cosine352 on 2010-01-10
> eject /dev/cdrom:p

---

### Post by lotusalive on 2010-02-21
Thanks all !  Something must have worked, because I'm no longer experiencing this as all with acidrip:D

---

