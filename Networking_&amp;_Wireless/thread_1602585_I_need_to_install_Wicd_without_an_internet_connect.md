---
title: "I need to install Wicd without an internet connection"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by Foxblood on 2010-10-21
Hi,


I installed Enlightenment into my machine and, in the course of the installation, Network Manager was removed. I now have no internet connection. I've searched and tried a couple of possible solutions here but I cannot get them to work. When I try to use a downloaded deb file Gdebi cannot install it. It seems that if I re-install Network Manager I'll lose a lot of my Enlightenment installation. What I'd like to do is install Wicd. I dual boot with Win 7 so all is not lost. I understand that there's a way to istall Wicd from the command line without an internet connection but I cannot figure out how to do it. Can anyone please advise? Thanks in advance.

---

### Post by ThatBum on 2010-10-21
If the machine has Ethernet, plug a router with DHCP into it and shut the machine down. Start it while holding down Shift and you will get GRUB's menu. Select the "(recovery mode)" option for your current kernel with the arrow keys and hit Enter. It will boot half-way and present you with another menu. Select netroot. This is a root terminal that runs dhclient, which sets up DHCP for you.  When it's done and gives you a prompt, you should have an Internet connection if your router is set up right. Then just use apt-get to get WiCD. This has saved my bacon many times with a couple of my machines. Of course if you can't move the machine or router and/or you don't have an Ethernet cable long enough, it could be a problem. I never learned how to connect to a wireless network through CLI...something to do with iwconfig and iwlist and things. Give it a shot.

---

### Post by Foxblood on 2010-10-21
Thanks for the speedy reply. I need to go digging around for ethernet cables, I won't get to this until the weekend. I'll let you know.

---

### Post by Foxblood on 2010-10-23
Hi, I did as you suggested. I got to netroot and my root password was rejected. I used Ctrl -D to continue to where I was able to enter my username and pass. I was unable to apt-get install wicd - package not found. I entered sudo gdm which allowed me to use synaptic to install wicd. Thanks for your assistance, now I can put those ethernet cables back under the stairs. Wicd won't connect but that's a problem for another thread.

---

