---
title: "Problem Copying Files Across Wireless"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by Popicas on 2009-07-05
Hello, im new to linux and have a problem. Looked for answers before asking but found nothing.

Recently I got an wireless router. Everything worked fine before with wired router but now I have this problem with wireless:
I can access INTERNET through the wireless connection and  I can access my windows locations with wireless on my network as well. Problem begins as soon as I try to copy files across the network. An window opens like the copy process was about to start but then the copy process freezes immediately and i cant even unmount network place. I have to reboot. Yesterday, after installing my new wireless router i was able to copy for a while, lets say that it would copy 221 mb and then would freeze. But now the copy process wont even start, it will freeze rigth away. What can be the problem? Its strange because it only happens with wireless and with cables it dooes not. I tested the wireless with windows and all is fine so it has to be some kind of configuration on linux for sure...

sorry for the long post and thanks in advance...

---

### Post by superprash2003 on 2009-07-06
does your wireless connection drop in between? does the internet work fine? how about when you download large files?

---

### Post by Popicas on 2009-07-07
After reading your reply I tested more thoroughly according to your instructions:  Internet is not an issue, I can surf with no problem. But downloading large files with the browser also freezes just like when i try to copy across the network.  The connection does not seem to drop because when the copy process freezes i am still able to connect to the web.  Something curious that probably is just a coincidence is that for two times in a row the copy freezes at exactly 231 MB. I have not tested this more than two times.  thank you for the attention, it would be really nice if you could help me sort this problem out,

---

### Post by superprash2003 on 2009-07-07
post output of ifconfig from the terminal , it could be a problem with your MTU values

---

### Post by Popicas on 2009-07-07
I think this is what you asked for - if not tell me more precisely because im new to this 

- two outputs, before and after the problem occured...

BEFORE THE FREEZE

xxxxxxxxxxxxxxxxxxxx-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr XXXXXXXXXXXXXXXXXXXX  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: XXXXXXXXXXXXXXXXXXXX:12be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5764 (5.7 KB)  TX bytes:4640 (4.6 KB)


AFTER THE FREEZE

xxxxxxxxxxxxxxxxx-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr XXXXXXXXXXXXXXXXXXXXX  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: XXXXXXXXXXXXXXXXXX:12be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71781904 (71.7 MB)  TX bytes:2023308 (2.0 MB)

---

### Post by superprash2003 on 2009-07-08
try this [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

---

### Post by Popicas on 2009-07-08
Tried it and it does not solve the problem. Still get a freeze while copying files across my wireless network...

---

