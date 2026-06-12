---
title: "Evdo installation"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by dravit on 2012-08-02
Hello,

I am new to UBUNTU 12.0.4, just downloaded and installed it. I am trying to install my "ZTE BSNL EVDO" modem to connect it to internet but unfortunately its not working. Please, help me from basic steps as I am new to UBUNTU. Also not having any wvdial.conf file in /etc
Please reply asap.

Thanks-
Dravit Gupta

---

### Post by praseodym on 2012-08-02
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:

```
lsusb
lsmod
usb-devices
dmesg | egrep 'option|usb'
```
Check also this list:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by dravit on 2012-08-03
> **praseodym said:**
> Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:

```
lsusb
lsmod
usb-devices
dmesg | egrep 'option|usb'
```
Check also this list:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)



Hello,
First of all thanks for the reply.
I have attached a text file showing all the result please find the same and try to help me out as soon as possible.

---

### Post by praseodym on 2012-08-03
Did you install "usb-modeswitch"? Checked the "checklist"?

---

### Post by dravit on 2012-08-04
> **praseodym said:**
> Did you install "usb-modeswitch"? Checked the "checklist"?

No, I didn't and I also don't know how to do that.
I had downloaded (wvdial_1.61-4build1_i386.deb) package on my windows machine and than put it my ubuntu machine and double clicked it. And i think that it is executable on ubuntu.

---

### Post by praseodym on 2012-08-04
Via cable connection or wireless. Open the software center for installing "usb-modwswitch".

Check also here:

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by dravit on 2012-08-04
> **praseodym said:**
> Via cable connection or wireless. Open the software center for installing "usb-modwswitch".

Check also here:

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Sorry to say I don't have any option to connect that machine to internet. Please tell me the option to download packages/softwares on windows machine and than run those packages via command line on UBUNTU machine.

---

### Post by praseodym on 2012-08-04
For 32bit:

[http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_1.2.3+repack0-1ubuntu2_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_1.2.3+repack0-1ubuntu2_i386.deb)

For 64bit:

[http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_1.2.3+repack0-1ubuntu2_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_1.2.3+repack0-1ubuntu2_amd64.deb)

For both necessary:

[http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20120120-0ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20120120-0ubuntu1_all.deb)

Save them in "Downloads" and install via terminal

```
sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by dravit on 2012-08-04
> **praseodym said:**
> For 32bit:

[http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_1.2.3+repack0-1ubuntu2_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_1.2.3+repack0-1ubuntu2_i386.deb)

For 64bit:

[http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_1.2.3+repack0-1ubuntu2_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_1.2.3+repack0-1ubuntu2_amd64.deb)

For both necessary:

[http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20120120-0ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20120120-0ubuntu1_all.deb)

Save them in "Downloads" and install via terminal

```
sudo dpkg -i ~/Downloads/*.deb
```

Done with that. Shall I try using my modem?

---

### Post by dravit on 2012-08-04
> **dravit said:**
> Done with that. Shall I try using my modem?
Hey, Thanks a lot it was a great support from your side. My Internet Connection has started working but its speed is not as good as it was giving on windows on same machine.. Is there any way to improve it.

---

### Post by praseodym on 2012-08-04
Please check:
> 
ifconfig -a
cat /etc/resolv.conf
cat /etc/network/interfaces

---

