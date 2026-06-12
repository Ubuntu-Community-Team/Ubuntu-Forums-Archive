---
title: "Internet is not connecting."
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by Timper on 2009-05-14
Hello, I'm Timper, just downloaded Ubuntu last night and I've never used it before.
 
I have a Compaq Presario C300 with a Broadcom STA wireless driver. I have installed the Broadcom driver and activated it, rebooted my computer, and it still will not connect to the internet. I have the ndisgtk & ndiswrapper packages installed, as well as the wpasupplicant. Wireless networks show up and when I click on mine it asks me to enter the network key, which I enter and then instead of 4 gray bars with a red x above them, it turns to two a green and gray dot with a blue dot circling through them. It will do this for about a minute, then a message will come up and ask me to put in the network key again. I do this, and after another minute, it pops up again. It does not stop doing it and I don't know what to do.
 
Note: I have not installed the ndisgtk & ndiswrapper packages to the Windows Driver .inf file as I do not have any idea how to find that file at all.
 
I had a virus and some malware on my computer before I installed Ubuntu on it, I was unable to connect to the internet on that due to the virus blocking the internet but when I installed Ubuntu I said to write over everything and leave no files or settings from Windows that were there previously behind.

---

### Post by Paul41 on 2009-05-14
Can you connect with a wired connection?  From the terminal run the following command and post the output, it may point to something.

```
ifconfig
```

---

### Post by Timper on 2009-05-14
> **Paul41 said:**
> Can you connect with a wired connection? From the terminal run the following command and post the output, it may point to something.
 
```
ifconfig
```
 
eth0 Link encap:Ethernet HWaddr 00:16:d4:45:65:67 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:16 Base address:0x2000 
 
eth1 Link encap:Ethernet HWaddr 00:14:a5:f0:13:ef 
inet6 addr: fe80::214:a5ff:fef0:13ef/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:36 errors:0 dropped:0 overruns:0 frame:393
TX packets:35 errors:6 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:4068 (4.0 KB) TX bytes:5005 (5.0 KB)
Interrupt:18 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 fram
 
 
^ I'm on the internet from my family computer, and it already has enough problems with Vista and the Internet I don't to unplug the chord from it.  I will be able to transer anything I need from computer to computer by flashdrive or disk if needed.

---

### Post by Paul41 on 2009-05-14
See what iwconfig shows.

Also are you able to connect using a wired connection?

---

### Post by Timper on 2009-05-14
> **Paul41 said:**
> See what iwconfig shows.
 
Also are you able to connect using a wired connection?
 
 
I have not tried using a wired connection.  And heres the results form iwconfig.
 
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:201  Noise level:161
          Rx invalid nwid:0  invalid crypt:29  invalid misc:0
 
pan0      no wireless extensions.

---

