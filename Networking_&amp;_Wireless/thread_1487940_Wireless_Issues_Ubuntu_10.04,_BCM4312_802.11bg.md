---
title: "Wireless Issues: Ubuntu 10.04, BCM4312 802.11b/g"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by mattierocks on 2010-05-19
Hello all, sorry to be the millionth person to a question like this, but I'm having issues with my wireless connection. I should mention I'm a TOTAL Linux noob. I'm using Ubuntu 10.04 and this is the first time I've ever, ever used it.

I hooked up a wired connection to install the STA driver for the Broadcom wireless card that was installed in my Dell Inspiron 1545. As referenced above, the card is a BCM4312. The computer shows that the wireless has a connection, but when I open up Firefox, it acts like it's not connected at all.

Any thoughts? 

Thanks so much.

---

### Post by bredman on 2010-05-19
Can you post the output from the following commands?

ifconfig
iwconfig
route

---

### Post by mattierocks on 2010-05-19
ifconfig:
 Link encap:Ethernet  HWaddr 00:25:64:6e:1c:0b  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe6e:1c0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10042725 (10.0 MB)  TX bytes:1574580 (1.5 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 70:1a:04:6d:a5:2c  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe6d:a52c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:627
          TX packets:11 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2909 (2.9 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:269168 (269.1 KB)  TX bytes:269168 (269.1 KB)

iwconfig: [COLOR=Red](This looks like it could be a problem!)[/COLOR]

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      *               255.255.255.0   U     2      0        0 eth1
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         dslrouter.weste 0.0.0.0         UG    0      0        0 eth0

Thanks for taking a look bredman.

---

### Post by HT Gearhead on 2010-05-20
I have similar issue with my HP pavillion laptop. It has the  same wlan chipset.
I can connect but it disconnects after a few seconds. I'm using my LAN to access the internet for now.

---

### Post by ChadBargo on 2010-05-26
> **mattierocks said:**
> Hello all, sorry to be the millionth person to a question like this, but I'm having issues with my wireless connection. I should mention I'm a TOTAL Linux noob. I'm using Ubuntu 10.04 and this is the first time I've ever, ever used it.

I hooked up a wired connection to install the STA driver for the Broadcom wireless card that was installed in my Dell Inspiron 1545. As referenced above, the card is a BCM4312. The computer shows that the wireless has a connection, but when I open up Firefox, it acts like it's not connected at all.

Any thoughts? 

Thanks so much.
Hey mattie, I have the same laptop as you with the same issue :mad: . Did you get yours fixed? I tried the STA and the BCM43 driver,neither worked. Both will say they are activated,but I still can not get the wireless enabled either.

---

### Post by mattierocks on 2010-05-27
Hey Chad,

Ok, here's what happened...

I had originally been trying to install the drivers myself (which I really don't have the knowledge/skills for at this point) without an internet connection.

When that didn't work, I gave up and plugged it into a wired connection (which connected right away, incidentally...).

From there, I went System > Administration > Hardware Drivers, then the system did the update for me, installed the correct driver and I've been wireless ever since.

This may be so painfully obvious that you've already tried it, but this is what worked for me. Best of luck!

Mattie

---

### Post by HT Gearhead on 2010-06-01
For some reason mine started working on it's own. :confused:
Must have updated itself without my knowing. :confused::confused:

---

### Post by EuriskoXP on 2010-07-18
unfortunately for me i spilt vodka on my laptop (a dell latitude d820 with a Broadcom 4312) and the usb, vga, and ethernet ports no longer work. It is dual booting XP and Ubuntu (and yes the wifi card works under windows- not hardware problem), but my desktop is vista only... how could i go about getting the drivers ont the lappie (i do have flash drives, but no disc drive in the laptop as i opted for a second battery instead) thanks

---

