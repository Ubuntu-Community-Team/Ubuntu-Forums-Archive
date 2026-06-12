---
title: "Broadcom 4313 on HP dm4 not finding wireless connection"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by goinglinux on 2010-10-18
OK, now I'm just frustrated! 

My HP Pavilion dm4 notebook has the Broadcom bcm4313 and worked with the proprietary Broadcom driver provided with Ubuntu 10.04 but did not work with the corresponding driver provided with Ubuntu 10.10. The solution that worked for me (for a while) was to install "broadcom-sta-common" and its dependencies using Synaptic. After enabling the proprietary driver (System > Administration > Additional Drivers) and rebooting, wireless worked. I even shared this on [this post]("http://ubuntuforums.org/showthread.php?t=1592044&page=3"). My suggestion even seemed to help chargersfan420 get his Broadcom card functional again. 

What changed to break it? Well, wireless had worked for several days, so I felt that I had solved the wireless problem. Now it was time to find a solution to unlock my BIOS settings. I successfully used PCCMOSCleaner to clear the password. After that, no more wireless.  (Note to dm4 users: Apparently HP puts a password on the BIOS settings and makes it available only if you boot into the factory-installed Windows 7 and retrieve it. Of course I never booted into Windows 7 before upgrading the machine to Linux, deleting both the Windows partition and HP's hidden recovery partition.) 

I uninstalled all the Broadcom stuff and reinstalled it all. Now I appear to have wl working, and b43 and ssb blacklisted, but network manager is not seeing any wireless connections available.

My Hardware: HP Pavilion dm4-1063cl
My OS: Ubuntu 10.10 32-bit (clean install)

lspci reports this:
```
$ lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
```dmesg reports this: (MAC address edited out with hash marks.)
```
$ dmesg | grep -e wl -e eth0 -e eth1 -e b43 -e ssb
[    2.551206] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf84c6000, ##:##:##:##:##:##, XID 083000c0 IRQ 43
[   14.171729] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.240994] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.241003] wl 0000:03:00.0: setting latency timer to 64
[   14.287063] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36
[   15.122218] r8169 0000:02:00.0: eth0: link up
[   15.122227] r8169 0000:02:00.0: eth0: link up
[   25.233158] eth0: no IPv6 routers present
[   25.456619] eth1: no IPv6 routers present

```iwconfig reports this:
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated  
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

```ifconfig reports this: (The hash marks have real numbers in them.)
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:## 
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: ####::####:####:####:####/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15472838 (15.4 MB)  TX bytes:908155 (908.1 KB)
          Interrupt:43 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr ##:##:##:##:##:## 
          inet6 addr: ####::####:####:####:####/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2170 (2.1 KB)  TX bytes:2170 (2.1 KB)

```Any ideas?

---

### Post by Mansor on 2010-10-18
Hi! I've got a HP DM4-1063cl notebook with BCM4313 I've installed from proprietary drivers STA Broadcom and works fine.
I did a 10.10 fresh installation.
I'm trying to make it work the bluetooth on the same hw but I didn't find anything yet.

---

### Post by johnnytm on 2010-10-18
I would suggest going here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) download the 32 or 64 bit driver. also download the readme file. It has instructions to completely remove all the older versions of broadcom drivers and build/install the new driver from the packages you download. NIce thing is once u have the downloads, no need for internet connection while installing, u can also save a copy of the driver so u have it if needed after.

---

### Post by goinglinux on 2010-10-20
> **johnnytm said:**
> I would suggest going here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) download the 32 or 64 bit driver. also download the readme file. It has instructions to completely remove all the older versions of broadcom drivers and build/install the new driver from the packages you download. NIce thing is once u have the downloads, no need for internet connection while installing, u can also save a copy of the driver so u have it if needed after.

Thanks for the suggestion. the driver would not compile because of one missing component or another. I even spent time (rare for me) walking step-by-step through each instruction to ensure that I wasn't missing anything. Still no-go.

At this point I'm thinking, "OK, it was working when I first installed it. Maybe it would take less time to just re-install Ubuntu 10.10 and get a fresh run at it." An hour later (after backup and re-install) still a no-go. 

Alright, nothing to lose now. I know Ubuntu 10.04 worked. Fresh install and like magic - up and running with the proprietary drivers. I wonder... Let's try **upgrading** to Ubuntu 10.10. Ran the upgrade. Crossed fingers. Held breath. Rebooted. SUCCESS! I now have Ubuntu 10.10 running with proprietary Broadcom drivers on my HP Pavilion dm4! 

Thanks to everyone who made suggestions. I learned a lot in the process, but I do feel a little cheap that I wasn't able to fix the problem by fixing the driver installation. Oh well, I'm a bit pragmatic in that I just want it to work -- quickly. This way worked for me.

---

### Post by bakunin_yo on 2010-10-24
This worked for me:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I just disabled the broadcom drivers and stopped at installing ndisgtk.  I'm assuming this means the other packages are already on 10.10.

I did have one issue though, after restarting the screen randomly went to login then gave an error output necessitating reboot.  I didn't write down the message, but after rebooting it went to the normal vs. recovery mode screen and I was able to start up no problem afterwards.  Not sure if it was related, but just thought I'd mention.

Dell 1501 with broadcom BCM 4311

---

### Post by Mansor on 2010-10-28
Have you make bluetooth work on the dm4?

---

### Post by goinglinux on 2010-10-31
I have the dm4-1063cl, which does not come with a bluetooth adapter installed. I don't have any bluetooth accessories, so I really have no experience with this on the dm4.

---

