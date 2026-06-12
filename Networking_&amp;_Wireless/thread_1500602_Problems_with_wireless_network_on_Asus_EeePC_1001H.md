---
title: "Problems with wireless network on Asus EeePC 1001HA"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by darmok1 on 2010-06-03
Hi everyone,

I know that there have posts about this before, but I have tried to follow all the advice and can't seem to get this to work.
I have just purchased an Asus EeePC 1001HA netbook and I would like to install Ubuntu Netbook Edition 9.10 (love the look and the brilliant interface), but I can't get the wireless network to work.
I am currently running from a 4Gb USB stick that has the LiveCD on it with a 1Gb persistence.
The network notification area only shows wired and VPN connections.  I have tried installing the Ralink 3090 driver but I have had no luck in getting the wireless to work.
Any help for this Linux novice would be greatly appreciated.
Thanks in advance

---

### Post by spotted zebra on 2010-06-03
administration>hardware drivers  

make sure you are connected via LAN. it will search for available drivers, select one and install it.

if you have already tried this with all the possible driver options available in the above program let me know and i will think of something else. if you have not tried all the available options try them all and see if you can get one to work. 

hope this helps.

---

### Post by darmok1 on 2010-06-03
Hi Spotted Zebra,
I will give that a try.  Will let you know the outcome.

Thanks

Darmok

---

### Post by darmok1 on 2010-06-04
Hello again,
I tried to search for the drivers as suggested, however the application does do the search but then when it's finished the list is blank and the message "No proprietry drivers are in use on this system"

Thanks again for any assistance

---

### Post by spotted zebra on 2010-06-04
Have you tried right clicking on the wireless configuration icon and enabling wireless connection? Is you wireless card turned on? I know these are simple but need to be checked.

---

### Post by darmok1 on 2010-06-04
If it is the icon on the status bar at the top, then yes I have.  The options I have are, Enable Networking, Connection Information, Edit Connections & About.  I have tried manually entering my network information, but that didn't work either.
The blue light above the wireless symbol on the PC casing is on and wireless works in XP (Ugh!) so I am pretty sure it's on.  Sorry I should have said.
Again, thanks for the your time.

---

### Post by clydeseal on 2010-06-04
[FONT=Arial]Hello I had the same problem with a Lenovo laptop. I went to system>administration>hardware drivers and I found that the drivers for the wireless card were deactivated. I activated them and immediately [/FONT]I found 3 wireless networks and I was able to connect. Thanks for your help. :)

---

### Post by bkratz on 2010-06-04
You might want to take some time and go through this. Especially the later posts.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

---

### Post by spotted zebra on 2010-06-08
^^^ not sure what this is but based on his/her number of posts prolly know what they are talking about give that a shot and see what it does for you.

---

