---
title: "Network manager strange behaviour"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by Kostis on 2009-12-16
Hi all!
I have been an Ubuntu user for about 2 years, and I face the following problem for the last 2 weeks. I have searched the forums, but I haven't found any similar problem with the one I am facing...

Network manager says that my wireless card and my mobile broadband card are disconnected. 

A temporary solution to my problem consists on running the following commands:
```
sudo apt-get remove network-manager
```
```
sudo apt-get install network-manager
```
Afterwards, I reboot and everything works perfectly.

When I reboot one more time, network manager reports again that my wireless card and the mobile broadband card are disconnected. However, the wlan0 interface seems to be up...

I am running Ubuntu 9.10 64 biton a Dell E6400, my wireless card is Intel WiFi Link 5300 and my mobile broadband card is Dell 5530 (I believe this is Ericsson MBM F3705g).

What should I do?
Thanks in advance for your help!

---

### Post by dimamali on 2009-12-16
Hello patrida!!!
Kostis, i had similar problems with Network Manager in Ubuntu and unfortunately i had many more than that. I would strongly recommend you to give wicd a try. It's on the repos, you can install it from synaptic in no time and afert restart it takes the place of Network Manager which you can easily reinstall if you are not satisfied with wicd.
If you decide to do it please post your results.
:-)

---

### Post by Kostis on 2009-12-17
I replaced the network-manager with wicd, and it works, but I am not happy with this workaround. Mainly because network-manager has integrated VPN support and because wicd requires gksudo (some non-sudoer users use this laptop).

I cannot understand why network-manager works fine when I install it and reboot my computer, and it seem to be broken on the next reboot...

Any suggestions?

Y.G. Telika mallon isxyei oti opoia petra ki' an sikwseis tha vreis enan ellina apo katw :P

---

### Post by dimamali on 2009-12-17
I'm not a wicd expert but are you sure that non-priviledged users can't use it? I just checked my unpriviledged users in my laptop and wicd seems to work fine.
You have a point about the VPN integration but i have been having problems with that since 9.04 so i don't use network manager for vpn anymore.
Unfortunately i can't help you in understanding the probelm. At least you do have a workaround until you fix that.

PS: Be careful with those Greeklish...i think there is a ban policy for not using English...gmt. ;-)
PS: And Ubuntu is a large stone. You'll find plenty of us around.

---

### Post by Kostis on 2009-12-17
Wicd is working for non-privileged users as well. My bad.
I filed a bug report, and I will use wicd for the time being.

Thanks!

P.S. I wasn't aware of the non-english ban policy. Make sense though...

---

### Post by Kostis on 2009-12-17
I think I found the answer.
Dell have issued recently many BIOS firmware updates for the E6400 and E6500 laptops since there are many complaints regarding ([http://en.community.dell.com/forums/t/19247293.aspx]("http://en.community.dell.com/forums/t/19247293.aspx")). I have installed the most recent bios (A19) and ubuntu seems to have problems recognizing the state of a hardware switch that controls the bluetooth, wireless and 3g cards (configurable from bios). 

Ubuntu does not recognize the state of the switch, but is able to recognize changes of the switch's state, and by default it recognizes that the switch is off. 

So I have to be careful to boot with the switch turned off, and I turn it on afterwards...

Not the desirable behavior, but I believe that it will be fixed soon!

Cheers!

P.S. I found this bug [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/430809]("https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/430809"), but it doesn't seem to work for my Dell E6400 :(

**P.S.2 I just updated to kernel 2.6.31-17 and the problem is solved!!!**

---

