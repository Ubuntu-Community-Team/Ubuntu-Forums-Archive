---
title: "No Wireless Card Detected"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by zanknits on 2010-05-13
Hi all! I upgraded to Lucid, and my wireless icon dissapeared (again). This time, though, it took my sound with it. I have the 'notification area' added to the panel, and my battery life/keyboard settings show up, just not the wireless or sound. When I run:
> nm-applet --sm-disable
I get this:
> An instance of nm-applet is already running.

** (nm-applet:2186): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.


So, how can I fix this? Alternately, is there a way to access a list of the available wireless networks without going through the drop down menu?

...unrelated, does anyone else have to restart their computer after plugging in their ethernet cable to get the computer to recognize it? If I boot up without the cable plugged in, I have to restart to get internet.

---

### Post by blazemore on 2010-05-13
The applet you need to add is called "Application Indicator" or "indicator panel" or something like that. It also includes the new mail notification icon.

---

### Post by ubunterooster on 2010-05-13
I think is listed as "indicator applet"

---

### Post by blazemore on 2010-05-13
> **ubunterooster said:**
> I think is listed as "indicator applet"

Yep, that's the one!

---

### Post by zanknits on 2010-05-13
Awesome! Thank you! That brought up my mail and sound icons. My wireless icon still won't show up, though. I'll try a reboot and see if it pops up.

---

### Post by zanknits on 2010-05-13
Rebooting didn't work. I just now noticed that during the restart, a black line pops up where the wireless icon would be...I've tried to click on it, but no dice. It flickers out pretty quickly.

---

### Post by ubunterooster on 2010-05-13
try in the terminal : "ifconfig"  and paste results Then "iwconfig" paste that as well

---

### Post by zanknits on 2010-05-13
ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:1e:ec:f9:5b:e7  
          inet addr:192.168.100.200  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fef9:5be7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6797 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9817767 (9.8 MB)  TX bytes:1095450 (1.0 MB)
          Interrupt:29 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:93:c5:9d  
          inet6 addr: fe80::221:ff:fe93:c59d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


Hardware-wise, my wireless did work with hardy/jaunty/intrepid.

---

### Post by ubunterooster on 2010-05-13
That's what I was afraid of.  I don't know a whole lot about wireless so I'll ask a mod to move it to the wireless section.

---

### Post by zanknits on 2010-05-13
thank you! Every debug just gives me the opportunity to learn more about Ubuntu, I guess :)

---

### Post by zanknits on 2010-05-14
bumpity bump

---

