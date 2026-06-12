---
title: "ubuntustudio wireless internet help"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by lavasofa on 2009-10-09
I installed ubuntu studio 8.4 and now my computer will not connect to my wireless network. I have configured everything possible and my computer shows that i am getting a signal. I use an hp dv9700 which has the wireless switch on it that only lights up when it has a signal and that lights up. I have ran the hardware detection app and my computer can freely send info to the internet it came back saying i can connect to the internet, but when i try to start up mozilla it shows a the couldnt load screen. (also on the same app when i try to send out the email at the end it comes back saying it couldnt almot immediatly.) I read in another thread that roaming could be enabled in network tools by hitting configuration, but in all 3 tabs (wlan0, wlan0:asci, unknown device (or something of that nature) when i click configure it tells me that there is no such device.

My laptop has the following network devices:
Intel(R) Wireless WiFi Link 4965AGN    -for wireless
Realtek RTL8168B/8111B Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)

Any help would be appreciated

---

### Post by lavasofa on 2009-10-09
found possible fix

[http://ubuntuforums.org/archive/index.php/t-1045560.html](http://ubuntuforums.org/archive/index.php/t-1045560.html)

post by darkpi

testing currently

---

### Post by lavasofa on 2009-10-10
the fix didnt end up working due to the fact that there was no easy way to know which version of the file to use. 

what i have done now is installed ubuntu and put ubuntustudio plugins over it via the synaptic package manager. things seem to be running smooth as butter on Mercury :)

if anyone is intrested in doing this who is as new to linux as i am and finds this thread searching their problem in google all you need to do is go to SYSTEM>ADMIN>SOFTWARE SOURCES then click on update and put a check in the backdoor one. afther that go into SYSTEM>ADMIN>SYNAPTIC PACKAGE MANAGER and type ubuntustudio into the search field and install what you want your system to have. only differance is the lack of real time kernals (which could have been the trouble of finding a driver in the first place, for all i know)

---

