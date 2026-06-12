---
title: "lost internet connections after win XP crashed"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by qui8 on 2009-05-10
hallo all,

its a long post, but i feel its necessary.

i am new to Ubuntu and installed it on second partition of my dell inspiron 6000 which was running win XP,with the intention of shifting from windows to ubuntu completely.

ubuntu 8.10 did not have any problems with connecting to wireless as well as ADSL wired connection. while upgrading to 9.4 it showed some errors and did not boot. 

after a while my windows XP also started crashing just at the beginning of booting. 

since then, i started Ubuntu 8.10 and have got it working, but my wireless and wired connections have been lost. ('no network connection' message, though in the wireless tab in 'network connection'it shows both my home and office wireless connections SSID : 15 days ago -last connected-)

i am quite happy with ubuntu the way its functioning, but without internet i cant think of living normal life. is there any way this can be sorted out? one way would be to reinstall windows and start the way it was, but i just dont want to start windows. can i start wireless and network cards through ubuntu only? (i dont even know why they should not function!!)

i did try 'sudo lshw -C network' and the result shows 

------------------------
*-network:0 DISABLED
      description: Ethernet interface
      physical id: 1
      logical name: vboxnet0
      serial: 00:76:62:6e:65:74
      capabilities: ethernet physical
      confuguration: broadcast=yes multicast=yes
*-network:1 DISABLED
      description: Ethernet interface
      physical id: 2
      logical name: pan0
      serial: 3e:88:a7:60:86:79
      capabilities: ethernet physical
      confuguration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

-------------

can anybody tell me whats up and how can i get back to net?

shold i try installing Ubuntu 9.04 and hope it will detect my cards?

p.s. i dont have cd drive, so the solution should be without the use of cd drive.

thanks for patience and for help.

---

