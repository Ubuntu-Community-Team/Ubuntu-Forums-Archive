---
title: "Jaunty and iBurst USB"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by onegreenparker on 2009-09-08
Hi There,
Has anyone managed to get the iBurst USB modem working on 9.04?
I had success from 6.06 to 8.04 (if memory serves).
Absolutely no luck on 9.04 :confused:

---

### Post by onegreenparker on 2009-09-10
Success!

Below are the steps I used to get my USB iBurst modem up and running on my 64bit Jaunty:

0) USe Synaptic to add Live/Install CD as a repo and Reload Package Information
1) Install build-essential_11.4amd64.deb from the CD
2) Download ibdriver-1.3.4-linux-2.6.28 from [here]("http://sourceforge.net/projects/ibdriver/files/linux-2.6.ibdriver-1.3/ibdriver-1.3.4/ibdriver-1.3.4-linux-2.6.28-rc2.tar.gz/download")
3) Unpack the downloaded file to a suitable location
4) In Makefile, comment out *obj-m += ib-pcmcia.o*
4) Open shell and go to parent directory of the unpacked files
4) $ *make -C ibdriver-1.3.4-linux-2.6.28*
5) $ *sudo make -C ibdriver-1.3.4-linux-2.6.28 install*
6) Once those worked, I ran *sudo pppoeconf* and followed instructions

And connected...

---

### Post by onegreenparker on 2009-09-11
Sadly, on the second attempt at this after a clean install, the above did not work......

Error below (same as always)::(

```

$ make -C ibdriver-1.3.4-linux-2.6.28
make: Entering directory `/home/ian/Documents/ibdriver-1.3.4-linux-2.6.28'
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/ian/Documents/ibdriver-1.3.4-linux-2.6.28 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/ian/Documents/ibdriver-1.3.4-linux-2.6.28/ib-net.o
/home/ian/Documents/ibdriver-1.3.4-linux-2.6.28/ib-net.c: In function ‘ib_net_setup’:
/home/ian/Documents/ibdriver-1.3.4-linux-2.6.28/ib-net.c:509: warning: statement with no effect
  CC [M]  /home/ian/Documents/ibdriver-1.3.4-linux-2.6.28/ib-usb.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/ian/Documents/ibdriver-1.3.4-linux-2.6.28/ib-net.mod.o
  LD [M]  /home/ian/Documents/ibdriver-1.3.4-linux-2.6.28/ib-net.ko
  CC      /home/ian/Documents/ibdriver-1.3.4-linux-2.6.28/ib-usb.mod.o
  LD [M]  /home/ian/Documents/ibdriver-1.3.4-linux-2.6.28/ib-usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: Leaving directory `/home/ian/Documents/ibdriver-1.3.4-linux-2.6.28'

```

---

### Post by zairol79 on 2009-10-24
HI there, i managed to install the driver but the problem is, once i restart the pc, i have to disconnect my modem, reinstalling the driver and make a new connection using pppoeconfig. How i want to make it permenantly connect like my previously ubuntu 8.10? :confused: huhu

---

### Post by roach33 on 2009-11-02
any tricks to get the usb modem and 8.04 communicating like they should? I had them working fine with Jaunty - sourceforge driver and roaringpenguin dialler - and then the install on Heron (reverted for the graphics support) failed following the system updates.

---

### Post by zairol79 on 2009-11-02
Hi roach33

I beleive you have to use old driver rather than version ibdriver-1.3.4-linux-2.6.28. Like my laptop is using ibdriver-1.3.4-linux-2.6.20 on ubuntu Intrepid 8.10 and my dekstop using latest version ibdriver-1.3.4-linux-2.6.28 on ubuntu 9.04 Jaunty

---

### Post by onegreenparker on 2009-11-03
I have compiled ibdriver-1.3.4-linux-2.6.28 on 9.04 successfully and connected using all the defaults when running pppoeconf....

All working! 

Sadly, I still had to connect via office LAN to get all required packages. :(

---

### Post by onegreenparker on 2009-11-03
FYI, after running updates for 9.04 available as of today (3 Nov 09), ib0 was no longer available.
Recompiled ibdriver-1.3.4-linux-2.6.28 and restarted, all OK.

---

### Post by zairol79 on 2009-11-03
Yup... we need to recompile and reinstall driver everytime  after upgrading kernel.

---

### Post by karel_debruin on 2010-02-13
I installed the iBurst driver (ibdriver-1.3.4-linux-2.6.28) on Jaunty, and configured the connection successfully using pppoeconf, as described above. However, after updating, I also have the problem that requires me to reinstall iBurst drivers after I reboot! Has anybody figured out how to solve this?

By the way, any luck getting USB iBurst working on Karmic?

---

### Post by roach33 on 2010-02-14
iBurst working, albeit slow, on Karmic. I tried every trick the www could offer without success, then started going through roaring penguin dialler's readme in detail. Without much intent or hope I tried the gui dialler rather than command line in terminal - and lo and behold - instant success!

I don't know much about programming to be able to figure out what the difference is, but for now I'm very content. Eventually I might even get the speed thing sorted out.

---

### Post by karel_debruin on 2010-03-04
Hi Roach, just a follow up: 
 
Got iBurst USB modem working in karmic. I see no notable speed difference, so perhaps you'd also like to try it. Tested in 32 and 64 bit karmic.
 
This link is from a guy called michaeltrim, part of the sourceforge iBurst project.
Get the driver:
 
```
git clone git://[feanor.sssup.it/ibdriver.git]("http://feanor.sssup.it/ibdriver.git")
```

In the sourceforge forum they talk about changing the "ARCH :=" line in the Makefile.
However I did not need to change anything -> tested in 32 and 64 bit systems.
 
Anyway, then do your normal make and make install. 
After confirming the modem is installed by plugging it in and running lsusb, I then use the bundled pppoe dialer: 
```
 
sudo pppoeconf

```
 
All default settings, just enter username and password.
 
Also works after updating karmic (you do however need to reinstall the driver and the dialling stuff - remember to unplug the modem when installing the driver).
 
Cheers

---

### Post by vistar111 on 2010-07-21
Hi.. NOOB here.. any idea / suggestion on Ubunto 10.04 

root@ubuntu:/tmp/glibc-2.7# lsusb
Bus 002 Device 003: ID 0482:0204 Kyocera Corp. iBurst Terminal
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ubuntu:/tmp/glibc-2.7#


sudo tail -f /var/log/messages

Jul 21 05:46:10 ubuntu pppd[6994]: Exit
Jul 21 05:46:15 ubuntu pppd[7010]: pppd 2.4.5 started by root, uid 0
Jul 21 05:46:15 ubuntu pppd[7010]: Using interface ppp0
Jul 21 05:46:15 ubuntu pppd[7010]: Connect: ppp0 <--> /dev/pts/4
Jul 21 05:46:16 ubuntu pppd[7010]: CHAP authentication failed: Rejected^J^M
Jul 21 05:46:16 ubuntu pppd[7010]: Connection terminated.
Jul 21 05:46:16 ubuntu pppd[7010]: Exit.

---

### Post by onegreenparker on 2010-07-21
Hi There,
I haven't tried on 10.04 yet... but it is in the pipeline.

Did you follow the same steps as outlined for 9.04?

I have had some issues with 64bit.... But perhaps this would be sorted using info from karel_debruin's post above.

Rgds
Ian

---

### Post by karel_debruin on 2010-07-21
Hi there,
 
I have tested the "michaeltrim" driver in the git repository that I mentioned in my previous post on 10.04, 64-bit, and can confirm that it works. 
 
I followed exactly the same procedure as in my previous post, using pppoeconf after installing the driver.
 
Cheers

---

### Post by laylow45 on 2010-11-08
> **karel_debruin said:**
> Hi there,
 
I have tested the "michaeltrim" driver in the git repository that I mentioned in my previous post on 10.04, 64-bit, and can confirm that it works. 
 
I followed exactly the same procedure as in my previous post, using pppoeconf after installing the driver.
 
Cheers
Hi Guys
Really battling with the iBurst driver...reinstall after every update in 10.04.  I use ibriver-2.6.31. and after the umpteenth update/re-install it now ceased to work completely. does ([http://feanor.sssup.it/ibdriver.git)still](http://feanor.sssup.it/ibdriver.git)still) exist, cause cant find it...The requested URL /ibdriver.git was not found on this server
please help!

---

### Post by laylow45 on 2010-11-12
> **vistar111 said:**
> Hi.. NOOB here.. any idea / suggestion on Ubunto 10.04 

see this thread re iBurst, pppoeconf etc. etc.
[http://ubuntuforums.org/showthread.php?p=10092931#post10092931](http://ubuntuforums.org/showthread.php?p=10092931#post10092931)

---

