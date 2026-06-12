---
title: "Ubuntu causes router to crash"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by luckydem001 on 2013-04-22
I am running ubuntu 12.04 on my old desktop and would like to set it up as a file sharing server as well as a HTPC using xbmc.
All seemed to work fine at first but the internet connection goes down every time i connected the ubuntu machine to my router.
the Router crashes and i lose internet on the other computers on the network.
after disconnecting the Ubuntu machine, the internet works once again.

I tried everything suggested on this link: [http://ubuntuforums.org/showthread.php?t=1803037&page=2](http://ubuntuforums.org/showthread.php?t=1803037&page=2)

But the problem persists.

Please help, and let me know what information you need from me!
the router is a Mega 200vwr
the motherboard on the ubuntu box is an asrock g31m-vs2.

Thank you - all suggestions will be greatly appreciated

Regards - a new and eager ubuntu user

---

### Post by gordintoronto on 2013-04-22
Ethernet connection or wireless? And the other computers? How old is the router?

The quick solution might be to just replace the router, since it should not operate the way you  describe.

---

### Post by tgalati4 on 2013-04-22
Are you using DHCP or a manual IP address for your PC?  Many times routers will crash if there is an IP conflict with another device because they don't know how to handle it.  Go into your router's administrative webpage and set the DHCP range from 2 to 150.  Set your PC to a manual IP with 192.168.1.151, netmask 255.255.255.0, gateway 192.168.1.1, DNS server 8.8.8.8, 2nd DNS server 8.8.4.4.  Adjust your IP addresses if you are not using the 192.168.1.xx network.

---

### Post by luckydem001 on 2013-04-23
thank you for your replies!
I am connecting the Ubuntu box to the router with an ethernet cable.
I set my Ubuntu box to have a manual ip address, but the problem still persists.
As soon as i connect it, I cannot access the internet from any computer on the network.
As soon as i unplug the ethernet cable from the ubuntu box, internet access on the other computers comes back.

**I tried my older Router (Mega 105wr) and there were no problems connecting the ubuntu box to the internet, and it did not cause the router to crash and the other computers did not lose connection. ****Must be something with the router?**

---

### Post by tgalati4 on 2013-04-23
Is the cable a normal Cat5 cable or a Patch (crossover) cable.  Some routers can detect a crossover cable and automatically flip the Rx and Tx lines so that it works correctly.  Look at the clear ends of the cable and if some of the colors are crossed, then you have a crossover cable.

Typical Pinouts:  [http://webpages.charter.net/ttworld/Tech/Lan/lan_pinouts.htm](http://webpages.charter.net/ttworld/Tech/Lan/lan_pinouts.htm)

The other possiblity is Power-over-Ethernet (PoE).  If one or more of your ports have PoE and your network card on your PC is not isolated (to strip off the power), then that would create a hard electrical short and cause the router some distress.

---

### Post by luckydem001 on 2013-04-25
Okay I haven't checked the Ethernet cable yet since its running smoothly with my old router at the moment, but when I do I will get back to you.
Thanks for your interest!

Regards

---

