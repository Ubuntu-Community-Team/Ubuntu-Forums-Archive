---
title: "netgear ndiswrapper not working"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by parts-man73 on 2009-03-03
I finally got a family member to give Ubuntu a test drive. Now I'm afraid if I can't get it to work properly, she'll go back to Windows. 

I installed 8.10 via WUBI on my daughter's computer. I put a wireless card in her desktop computer because routing an ethernet cable to her room would've been difficult. 

I used a Netgear wireless PCI card - WG311v3 - I searched and found this tutorial to guide me through the process. [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")

Everything worked fine - when I type "ndiswrapper -l" I receive the message
```
WG311v3 : driver installed
    device (11AB:1FAA) present
```

I did the "sudo modprobe ndiswapper" , but when I run "iwconfig" I have no wlan0

one note - when I ran the "sudo ndiswrapper -m" I get a "depreciated" error - but I manually added ndiswrapper to /etc/modules with gedit

Any ideas on how to get this wireless working ?

---

### Post by Mauser1891 on 2009-03-03
Hello...


You have the .inf & .sys, but did you delete the .cat file before installing using the .inf?

---

### Post by parts-man73 on 2009-03-03
no, didn't delete the .cat file, do I need to? 

that step wasn't mentioned in the wifidocs

---

