---
title: "Huawei E180 (&amp; possibly others) in Intrepid Ibex"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by JC Cheloven on 2008-12-15
Hi, I want to share my findings and experiences with Huawei modems on Ubuntu, specially for the E180, which is seldom mentioned in these forums. 

I tested several combinations (but not all) of the following:
-> Modems: Huawei E220 and E180
-> Computers: HP pavilion 9000, toshiba A50, Dell inspiron mini9, Dell inspiron 1525, carillon computer. 
-> OSs: Ubuntu 8.04 and 8.10

**E220 in Intrepid**
It is recognized by Network Manager 7 out of the box every time I tested, so no pain here :-)

**E220 and E180 in Hardy**
It has been reported that the "Basic procedure" (see below) works for E220 in Hardy, but I was unsuccessful at it. It didn't work for E180 in Hardy either. The "Extended procedure", and some of its variants, didn't work for me either, except for one and only time, which I was unable to reproduce (if you find uncomfortable with this inconsistency, just keep reading...). To sum up, these modems didn't work in Hardy Heron for me.

**E180 in Intrepid**
This is the main concern of this post, as everything else, either works, or refers to hardy (which is not the current ubuntu version). I've seen Huawei E180 reported as "to work out of the box" under Intrepid (for example in (5), second post), but again, it didn't for me. It simply recognized a 1Gb empty disk. I tried the _"Basic procedure"_ with these results:
-> It worked fine the first time. It was a 8.10 install with several months of use. Many packages installed/uninstalled, but the installation wasn't tweaked for internet in any way.
-> It didn't work on a fresher install  of 8.10 on the same machine (HP9000) !!!!!!!!!!  This installation had been simply updated and provided with some proprietary codecs that were also in the previous install.
-> I noticed that it worked running wvdial as root (sudo wvdial). So it should be a problem of permissions. The hunting started. NOTE: I DON'T RECOMMEND RUNNING WVDIAL AS ROOT ON A PERMANENT BASIS. IT IS A SECURITY RISK. I WAS ONLY TRYING.
-> I found that /usr/bin/wvdial calls /usr/sbin/pppd, which in turn uses the files /etc/ppp/pap-secrets and /etc/ppp/chap-secrets. The permissions of these were rw for root, nothing for the rest. I changed the permissions of these, as well as the ones for wvdial and pppd, but it didn't work either. Nevertheless, this gave a clue: "error3: pppd is not setuid-root and the invoking user is not root". 
-> Thus, pppd expects to be run as root, either directly or via setuid, as far as I understand. So I setuid-ed pppd for root (sudo chmod 4775 /usr/sbin/pppd), and then wvdial worked when called from a non-root user. 

Well, I'm unsure if to setuid pppd is a security risk as well, but this is the best I've found so far to get Huawei E180 running on Intrepid. The "Extended procedure" didn't help either. 
Further advice will be welcome.

--------------------------------------------------
APPENDICES

_Basic procedure_
This basic procedure is potentially useful for any gprs modem, as standalone, or as an "ingredient" of a broader procedure. It has been explained enough elsewhere (1). To sum up:
[INDENT]Disable the card's pin (with a regular cellular phone). Plug in the USB modem. Create the configuration file (sudo wvdialconf /etc/wvdial.conf). Edit the file as suitable for you (password, user, tf. number... depending on your isp). Type "wvdial" to connect, and ctrl-C to disconnect, leaving the terminal open in the meanwhile.
Once it woks, you can optionally install gnome-ppp as a graphic frontend.[/INDENT]

_Extended procedure _
This procedure is explained in (2), and consists of some additions to the "basic procedure". The following also includes some additional hints provided in (3). Hope it will help someone:
[INDENT]Plug the usb modem (pin disabled). If the device is identified as a cd or whatever, umount/eject it. Stop all internet activity (ifconfig eth0 down, ifconfig eth1 down ...). Remove this module from the kernel (rmmod usb-storage). List the usb devices (lsusb). You should see something as
Bus 004 Device 003: ID 12d1:1003
Mount the corresponding module in the kernel (modprobe usbserial vendor=0x12d1 product=0x1003, in this example), and list the available devices (ls -al /dev/ttyUSB*). You should see three of them, similar to this:
> crw-rw---- 1 root dialout 188, 0 2007-09-17 11:55 /dev/ttyUSB0
> crw-rw---- 1 root dialout 188, 1 2007-09-17 09:45 /dev/ttyUSB1
> crw-rw---- 1 root dialout 188, 2 2007-09-17 09:45 /dev/ttyUSB2
Now edit /etc/wvdial.config, in principle as in the "Basic procedure", although you can try to add some of the things suggested in (4), namely "Stupid Mode = 1", "Baud = 460800", or whiping "New PPPD = yes". If you want to complicate yourself a bit, you can add a dialer other than "Defaults" in this file (procedures are explained in the links). 
Now, again stop internet activity ( /etc/init.d/networking stop), and finally type "wvdial" as in the "Basic procedure".[/INDENT]

(1) HowTo from Fingers & Thumbs. [http://ubuntuforums.org/showthread.php?t=843973](http://ubuntuforums.org/showthread.php?t=843973)
(2) [http://www.fk21.co.uk/cgi-bin/fk21.cgi?sub=tmobile](http://www.fk21.co.uk/cgi-bin/fk21.cgi?sub=tmobile)
(3) [http://www.ubuntu-es.org/index.php?q=node/33041](http://www.ubuntu-es.org/index.php?q=node/33041)
(4) [http://www.fk21.co.uk/tmobilelinux/wvdial.txt](http://www.fk21.co.uk/tmobilelinux/wvdial.txt)
(5) [http://ubuntuforums.org/showthread.php?t=1009121&highlight=huawei](http://ubuntuforums.org/showthread.php?t=1009121&highlight=huawei)

---

### Post by Nevon on 2008-12-15
I have an E180, and it works perfectly as long as I plug it in before booting my computer.

---

### Post by JC Cheloven on 2008-12-15
> **Nevon said:**
> I have an E180, and it works perfectly as long as I plug it in before booting my computer.

Thank you for answering my call ;-)
I didn't figure out that plugging it before booting would make a difference. I'll try that, thank you very much.

---

### Post by adbennet on 2009-01-13
Hi,
Re the wvdial security.
Matt Jones said, to run wvdial, first make sure your user account is in the dip group. [https://answers.launchpad.net/ubuntu/+source/wvdial/+question/52455]("https://answers.launchpad.net/ubuntu/+source/wvdial/+question/52455")

---

### Post by blackest_knight on 2009-04-21
have you tried connection sharing with the Huawei modems, 
consider the following setup 

laptop with ppp0 eth0 and ath0.
 ppp0 is the modem 

eth0 connects to wan on a router (although perhaps it might be easier via a lan port) laptop forwards ppp0 to eth0 the router distributes packets to the lan and acts as a dhcp server. 

laptop uses ath0 assigned ip address from router to join the lan and connect to printers ect on the lan. 

I don't know if this is possible to route but i'm going to give it a good try

---

