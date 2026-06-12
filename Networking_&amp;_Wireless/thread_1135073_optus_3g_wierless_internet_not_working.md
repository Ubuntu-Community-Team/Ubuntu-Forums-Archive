---
title: "optus 3g wierless internet not working"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by jarrah-95 on 2009-04-24
when i run ubuntu 9.04 the first time i pluged in my modem it gave me the same wisard as 8.10 but when i try to connect it connects but the internet dosent work (no pages appear add\remmove dosent load) but the blue light is still on 
im using the huewei e220 with optus

---

### Post by Peter.Kostin on 2009-04-25
The same problem, in Ubuntu 8.10 my 3g modem (Nokia N82) was working correctly, but after update to 9.10 NM connects, but no pages can be open. Though smartphone shows that connection is on. And yes I can use internet (Opera mini) in Nokia without problems, that`s mean that errors are in Ubuntu.

This is my syslog:
Apr 25 10:34:51 peter-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_421_71_noserial_if0_0_serial_unknown_0, iface: (null)): iface not found
Apr 25 10:34:51 peter-laptop NetworkManager: <info>  (ttyACM0): found serial port (udev:GSM  hal:GSM) 
Apr 25 10:34:51 peter-laptop NetworkManager: <info>  (ttyACM0): new Modem device (driver: 'cdc_acm') 
Apr 25 10:34:51 peter-laptop NetworkManager: <info>  (ttyACM0): exported as /org/freedesktop/Hal/devices/usb_device_421_71_noserial_if0_0_serial_unknown_0 
Apr 25 10:34:52 peter-laptop chipcardd[2970]: devicemanager.c: 3373: Changes in hardware list
Apr 25 10:34:56 peter-laptop NetworkManager: <info>  (ttyACM0): device state change: 1 -> 2 
Apr 25 10:34:56 peter-laptop NetworkManager: <info>  (ttyACM0): deactivating device (reason: 2). 
Apr 25 10:34:56 peter-laptop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Apr 25 10:34:56 peter-laptop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Apr 25 10:34:56 peter-laptop NetworkManager: <info>  (ttyACM0): device state change: 2 -> 3 
Apr 25 10:35:01 peter-laptop NetworkManager: <info>  Activation (ttyACM0) starting connection 'Megafon (nw)' 
Apr 25 10:35:01 peter-laptop NetworkManager: <info>  (ttyACM0): device state change: 3 -> 4 
Apr 25 10:35:01 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 25 10:35:01 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started... 
Apr 25 10:35:01 peter-laptop NetworkManager: <debug> [1240641301.382145] nm_serial_device_open(): (ttyACM0) opening device... 
Apr 25 10:35:01 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete. 
Apr 25 10:35:01 peter-laptop NetworkManager: <info>  (ttyACM0): powering up... 
Apr 25 10:35:01 peter-laptop NetworkManager: <info>  Registered on Home network 
Apr 25 10:35:01 peter-laptop NetworkManager: <info>  Associated with network: +COPS: 0,2,"25002",2 
Apr 25 10:35:03 peter-laptop NetworkManager: <info>  Connected, Woo! 
Apr 25 10:35:03 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 25 10:35:03 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 2 of 5 (Device Configure) starting... 
Apr 25 10:35:03 peter-laptop NetworkManager: <info>  (ttyACM0): device state change: 4 -> 5 
Apr 25 10:35:03 peter-laptop NetworkManager: <info>  Starting pppd connection 
Apr 25 10:35:03 peter-laptop NetworkManager: <debug> [1240641303.689150] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyACM0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/2 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Apr 25 10:35:03 peter-laptop NetworkManager: <debug> [1240641303.690946] nm_ppp_manager_start(): ppp started with pid 7531 
Apr 25 10:35:03 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 2 of 5 (Device Configure) complete. 
Apr 25 10:35:03 peter-laptop pppd[7531]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Apr 25 10:35:03 peter-laptop pppd[7531]: pppd 2.4.5 started by root, uid 0
Apr 25 10:35:03 peter-laptop pppd[7531]: Using interface ppp0
Apr 25 10:35:03 peter-laptop pppd[7531]: Connect: ppp0 <--> /dev/ttyACM0
Apr 25 10:35:04 peter-laptop NetworkManager: <info>  (ttyACM0): device state change: 5 -> 6 
Apr 25 10:35:04 peter-laptop pppd[7531]: PAP authentication succeeded
Apr 25 10:35:04 peter-laptop NetworkManager: <info>  (ttyACM0): device state change: 6 -> 7 
Apr 25 10:35:05 peter-laptop pppd[7531]: Cannot determine ethernet address for proxy ARP
Apr 25 10:35:05 peter-laptop pppd[7531]: local  IP address 10.231.251.152
Apr 25 10:35:05 peter-laptop pppd[7531]: remote IP address 10.6.6.6
Apr 25 10:35:05 peter-laptop pppd[7531]: primary   DNS address 10.78.72.12
Apr 25 10:35:05 peter-laptop pppd[7531]: secondary DNS address 10.78.72.4
Apr 25 10:35:05 peter-laptop NetworkManager: <info>  PPP manager(IP Config Get) reply received. 
Apr 25 10:35:05 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 25 10:35:05 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 4 of 5 (IP Configure Get) started... 
Apr 25 10:35:05 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 25 10:35:05 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 25 10:35:05 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 25 10:35:06 peter-laptop NetworkManager: <info>  (ttyACM0): device state change: 7 -> 8 
Apr 25 10:35:06 peter-laptop NetworkManager: <info>  Policy set 'Megafon (nw)' (ppp0) as default for routing and DNS. 
Apr 25 10:35:06 peter-laptop NetworkManager: <info>  Activation (ttyACM0) successful, device activated. 
Apr 25 10:35:06 peter-laptop NetworkManager: <info>  Activation (ttyACM0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 25 10:35:38 peter-laptop ntpdate[7623]: can't find host ntp.ubuntu.com 
Apr 25 10:35:38 peter-laptop ntpdate[7623]: no servers can be used, exiting
Apr 25 10:40:01 peter-laptop /USR/SBIN/CRON[7891]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

Please Help! Let`s prove that Ubuntu Community is the best!

---

### Post by jarrah-95 on 2009-04-25
im looking at an idear that might work i think its eather the way ubuntu 9.04 treats the encryption or the fact that the wvdial package is missing so if you find out about eather can you please post it hare
i am at the moment trying to find a wvdial package that will work at the moment so if i do i will post the link and the code that runs it here

---

### Post by Peter.Kostin on 2009-04-25
Thank you for your work. I added a bug at [https://bugs.launchpad.net/ubuntu/+bug/366565](https://bugs.launchpad.net/ubuntu/+bug/366565)

---

### Post by jarrah-95 on 2009-04-25
dose yours look like it connects but doset actualy work when you say 9.10 nm what do you mean

---

### Post by Peter.Kostin on 2009-04-25
9.10 - Ubuntu 9.10 / NM - Network Manager / I mean - NM shows that it has connected to the 3g network, but pages cant load.

---

### Post by jarrah-95 on 2009-04-25
i think ive got a temp solution ive downloaded tthe .deb files for wvdial and wvstream and with some work and serching they worked but you have to make the wvdial.conf (in /ect/wvdial.conf) have 

[Dialer hsdpa]

Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ  Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0 
Modem Type = Analog Modem
the links to the .deb files are:
[http://ftp.nz.debian.org/debian/pool/main/w/wvstreams/libwvstreams4.4-base_4.4.1-1.1_i386.deb](http://ftp.nz.debian.org/debian/pool/main/w/wvstreams/libwvstreams4.4-base_4.4.1-1.1_i386.deb)
[http://ftp.nz.debian.org/debian/pool/main/x/xplc/libxplc0.3.13_0.3.13-2_i386.deb](http://ftp.nz.debian.org/debian/pool/main/x/xplc/libxplc0.3.13_0.3.13-2_i386.deb)
[http://ftp.nz.debian.org/debian/pool/main/w/wvdial/wvdial_1.60.1+nmu2_mips.deb](http://ftp.nz.debian.org/debian/pool/main/w/wvdial/wvdial_1.60.1+nmu2_mips.deb)
[http://nz2.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.4_4.4.1-0ubuntu2_i386.deb](http://nz2.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.4_4.4.1-0ubuntu2_i386.deb)
[http://nz2.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-extras_4.4.1-0ubuntu2_i386.deb](http://nz2.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-extras_4.4.1-0ubuntu2_i386.deb)

some of those might not be needed but thats what i found in my history
hope it works 
btw that diler might not work so if it dosent look up the model of your modem/phone and someone might have found the code and other parts you might know
thanks

---

### Post by jarrah-95 on 2009-04-25
if your stuck like i was with wvdial read this these guys helped me get mine to work 
[http://ubuntuforums.org/showthread.php?p=7146577#post7146577](http://ubuntuforums.org/showthread.php?p=7146577#post7146577)
thanks for the help good luck

---

### Post by Peter.Kostin on 2009-04-30
The problem was with settings in NetworkManager after upgrade they changed from Auto PPP to Auto PPP (addresses only). Developers of ubuntu must be more accurate, because of this small error I was going to migrate to windows.

---

### Post by bdimonstr on 2009-05-01
I found that this was a simple DNS fix for me.

Choosing the Optus (not Optus 3G) profile makes the connection - but unable to do anything..

The Optus profile appears to be using the wrong dns servers - 202.139.124.225 works.. Found via another site

Connecting via Samsung u700..

---

### Post by alfielee on 2009-05-11
> **bdimonstr said:**
> I found that this was a simple DNS fix for me.

Choosing the Optus (not Optus 3G) profile makes the connection - but unable to do anything..

The Optus profile appears to be using the wrong dns servers - 202.139.124.225 works.. Found via another site

Connecting via Samsung u700..
By the sound of what I've just read it looks like **ppp**now requires **sudo**. The other thing I know is that if you have a prepaid with OPTUS 3G then the key word is not **connect** or **internet** but **preconnect**

---

### Post by alfielee on 2009-05-11
My Optus 3G connects fine. I have a **prepaid** USB Huawei (some number) which Network Manager recognised immediately. All of the **APNs** I found didn't work but by running the setup with **wine** I found out that **OPTUS prepaid** expects **preconnect**. It connected immediately & I was running **Ubuntu 8.10**. I upgraded & can no longer browse the web. I can browse OPTUS & I managed to upgrade my system using both wireless at home & continued with the 3G here at work whilst not expecting it to work at all.

My problem is that I still can't browse the Internet even when I can browse OPTUS & update software. Why not browse the Internet? I can on Windows XP, mine is dual-boot but generally hardly ever use Windows these days.

**Any ideas?**:popcorn:

---

### Post by jarrah-95 on 2009-05-14
only a few tips:
1 if you use network manager than set methord to auto ppp in ipv6 menu (edit connections (right click the applet))
2 take firefox off offline (simple but easy to miss)
3 otherwise download (tar/deb) from windows or add/remmove

---

### Post by iMick on 2009-08-06
Worked for me by changing the DNS on 9.04 with a brand new black optus dongle.  Its a Huawei Model E1762.  

Impressed that it almost "just works"!   Shocked that i didn't have to touch a terminal to do a normal thing for a change :)

---

### Post by robbie d on 2009-08-12
I'm with iMick, changed the DNS and bingo. Hope my sis likes the new OS :)

---

### Post by mgml01 on 2010-05-13
I can confirm that the DNS setting is wrong in the Optus 3G profile. As suggested I right clicked on the 

1 - connection icon
2 - edit connections
3 - Mobile broadband tab
4 - select Optus 3G 
5 - Click Edit
6 - Click on IPv4 Settings
7 - in the DNS server field enter 202.139.124.225

I'm writing this connected via the HUAWEI E180 Optus 3G network :P

---

