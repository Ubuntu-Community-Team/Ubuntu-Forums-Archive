---
title: "how to watch tv"
date: 2008-05-01
forum: Multimedia Software
---

### Post by odindio on 2008-05-01
how to watch tv

---

### Post by tamoneya on 2008-05-01
you didnt really give much a description but if you are trying to watch tv on your computer you need something called a TV tuner card.  Then you can install MythTV and record TV shows.  If you are trying to watch tv on you tv you should try to find the remote and turn it on.

---

### Post by odindio on 2008-05-01
I've got the tv tuner - the remote does nothing.  I'm not sure how to set up mythtv....or is it still really difficult to deal with mythtv?  I don't thing it detects the right tv tuner.

I've struggled with mythtv in the past.  I just finally gave up.  I thought that maybe it might be realistic to try to use it again.

And yes I've got mythtv installed and I've got ubuntu 8.04.

---

### Post by tamoneya on 2008-05-01
first of all you should research the compatibility of your TVtuner.  Some tv tuners have drivers for linux and some don't.  Then you can start with ```
sudo apt-get install mythtv
```

---

### Post by fenian on 2008-05-01
post the output of this command...

> lspci

---

### Post by odindio on 2008-05-01
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:03.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
02:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

---

### Post by fenian on 2008-05-01
Okay ubuntu sees your card (02:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

Lets see if it  we can watch tv,first install mplayer and ivtv-utils...

> sudo apt-get install mplayer ivtv-utils 

Next run mplayer with the command to use the capture device (TVcard)...

> mplayer /dev/video0

this may only be static ,thats ok we just need to tune it to a channel with a signal.Open a seperate terminal window and enter...

> ivtv-tune -c # -d /dev/video0 

replace # with the channel number you want (if you are connecting to a cable box it would be 3 if you are using a direct connection or antennae use the channel number).

---

### Post by odindio on 2008-05-01
I tried to install mplayer and I got this message

dan@lori-desktop:~$ sudo apt-get install mplayer ivtv-utils 
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate

---

### Post by odindio on 2008-05-01
I managed to install through synaptic.  And I got it running.  But I tried the tune command and got.

ivtv-tune -c # -d /dev/video0 
ivtv-tune: option requires an argument -- c

I tried --c insted of -c, but that did not work

---

### Post by fenian on 2008-05-02
You need to replace the # sign with the number of the channel you want to watch.

---

### Post by drsox1899 on 2008-05-02
Try TVTime.  Works fine.

---

### Post by fenian on 2008-05-02
TVTme doesn't work with cards that do hardware encoding (mpeg2 cards like the op has)

---

### Post by odindio on 2008-05-02
who or what is op!

---

### Post by ubuntu27 on 2008-05-27
> **odindio said:**
> who or what is op!

OP means "Original Poster", it is the person who created the thread or topic. In this case, it will be you :)

---

### Post by ubuntu27 on 2008-05-27
EDIT: How did it become a double post!?

---

### Post by saedelaere on 2008-05-29
Hi,

since your card seems to work with the ivtv driver you could try [this]("http://ubuntuforums.org/showthread.php?t=763698") frontend.

Bye
Saedelaere

---

