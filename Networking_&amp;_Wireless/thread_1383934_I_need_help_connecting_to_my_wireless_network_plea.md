---
title: "I need help connecting to my wireless network please"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by Theoutdoorsman on 2010-01-17
I am an absolute beginner who needs help connecting my Ubuntu 9.10 box to my network using a linksys usb network adapter. I have absolutely NO idea where to begin and would appreciate any and all help anyone can offer.

---

### Post by sgosnell on 2010-01-17
You should be able to click on the network icon in the panel, see the network, and connect to it.  If it's a hidden network, not broadcasting the SSID, you can click on "Connect to hidden network" and fill in the information and connect.

---

### Post by Theoutdoorsman on 2010-01-17
Ok.... you lost me already...... please define "panel"? I know nothing about Ubuntu. Where can I find this "panel" icon you speak of? Thanks.

---

### Post by Cabs21 on 2010-01-17
go to system at the top left of your screen.  Then go to administration then go to hardware drivers and make sure your drivers are up to date and if they are not click on the one that matches your hardware in questions (your case its the wireless card)  Also if you could give some more information on your card and computer that would help us.

Enter this in your terminal (in applications at top left under accessories tab)

```
ifconfig
```

post what the output is from this code.

---

### Post by sgosnell on 2010-01-18
The panel is the taskbar in Windows.  By default it's at the top, and the network icon should be on the right end of it somewhere, looking like the signal strength bars on a cell phone.  Click on the bars, and you can select the network you want to connect to.  Obviously you'll need to enter the security information such as password, etc.

---

### Post by Theoutdoorsman on 2010-01-18
Here is the information you've requested:

ubuntu@ubuntu:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:40:ca:46:75:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


=====================================================


Also:

System>Administration>Hardware Drivers  =  "No proprietory drivers installed".



The USB Networking Hardware in question is a Linksys USB Network Adapter (model #: WUSB54GCV3). 
Thank you soooo much for helping me with this! It is MUCH appreciated! Also, I am using the Live CD
to boot from. I'm not sure if this will cause a problem, so I just needed to make you aware of that. Thanks
again.

---

### Post by Cabs21 on 2010-01-18
Ok what does

```
iwconfig
```

output

---

### Post by Theoutdoorsman on 2010-01-18
ubuntu@ubuntu:~$ iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



Sorry for the delay's. I have to work from another computer while correcting this problem.
Also, I have been examining this thread for a possible solution:

[http://ubuntuforums.org/showthread.php?t=1155941](http://ubuntuforums.org/showthread.php?t=1155941)

I have made no moves toward fixing via that link. I've just been reading. Opinions?

---

### Post by stars on 2010-01-18
after googling, i may have found a solution for you - though i cannot test it. hopefully the link below will help.

[http://old.nabble.com/Linksys-WUSB54GCV3-USB-WiFi-stick-td26273580.html](http://old.nabble.com/Linksys-WUSB54GCV3-USB-WiFi-stick-td26273580.html)

---

### Post by Theoutdoorsman on 2010-01-18
Thanks Stars, but my adapter is version 3. The thread you are referring to is for v1 and v4.

---

### Post by Theoutdoorsman on 2010-01-18
... bump ...

---

### Post by b k on 2010-01-18
> **Theoutdoorsman said:**
> ... bump ...
 
Hi, go to this link [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044) 
 
The write up is for the Linksys Wusb54gc v3 usb wireless dongle/stick.
 
Hope it helps you.

---

### Post by Cabs21 on 2010-01-19
By the way when you went to check your Hardware Drivers were you connected to the internet with a LAN cable or no.  Cause if you were not then your computer will not find any drivers since it can not even reach them.  Try connecting to the internet via LAN and update your drivers then.  See if that helps

---

### Post by Theoutdoorsman on 2010-01-19
Excellent! I will definitely be trying that out. Many thanks for providing the link. Hopefully this solves my woes.

---

### Post by Theoutdoorsman on 2010-01-19
> **Cabs21 said:**
> By the way when you went to check your Hardware Drivers were you connected to the internet with a LAN cable or no.  Cause if you were not then your computer will not find any drivers since it can not even reach them.  Try connecting to the internet via LAN and update your drivers then.  See if that helps



I will do this first. Thanks.

---

