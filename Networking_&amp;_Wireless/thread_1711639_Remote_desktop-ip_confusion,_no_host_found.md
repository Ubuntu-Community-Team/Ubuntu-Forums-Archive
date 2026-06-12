---
title: "Remote desktop-ip confusion, no host found"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by u-noob-tu on 2011-03-21
a month ago my remote desktop worked with my ipod touch running a vnc app. after not using it for about a week, it doesnt work anymore. on my computer in the remote desktop settings, there is no longer an ip displayed, now it just says localhost. i found out that localhost means the computer on the local network, which typically means an ip of 127.0.0.1. tried that and it didnt work. then i found this archived thread: [http://ubuntuforums.org/archive/index.php/t-1212109.html](http://ubuntuforums.org/archive/index.php/t-1212109.html), which mentions a few fixes. it says that when ifconfig is run in the terminal, you should see you ip, which should not start with 127 or 169. mine does not, its 192.168.1.7. using that doesnt work either. my ipod just keeps saying "no host-check network". as far as i know, my dad hasnt changed any network settings in our house. any ideas?

---

### Post by conneco on 2011-03-21
localhost is used to refer to the computer your currently sat at, 127.0.0.1 is a loopback ip address which is again the computer your sat at,  

Does you ipod have an IP address in the same range as your Ubuntu box, you say the ubuntu box is on 192.168.1.7 then your ipod should be on the same network if you want to remote into it,

Check that your ipod is on the 192.168.1 network

---

### Post by u-noob-tu on 2011-03-21
iPods ip is 192.168.1.6, only one number different.

---

