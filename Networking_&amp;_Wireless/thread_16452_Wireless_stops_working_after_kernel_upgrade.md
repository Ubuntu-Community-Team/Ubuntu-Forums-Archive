---
title: "Wireless stops working after kernel upgrade"
date: 2005-02-21
forum: Networking &amp; Wireless
---

### Post by chrisw on 2005-02-21
Hi Guys

Wirless works out the box when I install with the warty 386 image but when I try updating to kernel:

linux-image-2.6.8.1-5-686

everything goes OK and system boots but the wireless card is not longer works, works OK if I boot off the old 386 kernel image.

Am I going to have to role my own or is there somthing else I can do ??

Going to the 686 build of the kernel is not really needed but would be nice.

---

### Post by chrisw on 2005-02-21
I also got the same problem when playing with the latest release of hoary hmmmm

New to Ubuntu but pretty happy ;)

---

### Post by Mac-D on 2005-02-21
Yea it happened to me too, very frustrating, maybe hoary will fix all my problems.




PS: chrisw, you replied to your own post

---

### Post by alastair on 2005-02-22
This is probably just a module versions vs kernel version issue - a guess anyway. Upgrade the kernel - and you probably need to look for (or build) an updated kernel module for your wireless card. However - maybe not if the wireless device is buillt in. 

Details on the wireless device needed.

The syslog or dmesg log might help - see the logs on wireless device initialisation i.e. look in :

/var/log/syslog
/var/log/dmesg

Any problems reported?

---

### Post by Mac-D on 2005-02-23
I went and was playing with the Synaptic package manager and noticed my modules for my wireless card were behind, i installed new ones(located here:  [http://higgs.djpig.de/ubuntu/www/warty/misc/](http://higgs.djpig.de/ubuntu/www/warty/misc/)   ). works great now!
heres how i did it:
download the .deb file that fits your needs
for example i needed--- linux-restricted-modules-2.6.8.1-5-386
go to terminal
type: 
            sudo dpkg -i /**location**/**of**/**file**.deb
and the terminal takes it from there
after it installs, reboot and then:
go to network setup utility and setup your network connection(wireless card should now be properly recognized)
follow the instructions and you are set and ready to go.


Thanks Alastair, for your insight into the matter.

---

