---
title: "Wireshark keeps crashing"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by blueshiftoverwatch on 2009-12-11
I made a [previous thread]("http://ubuntuforums.org/showthread.php?t=1344280") about my problems with getting Wireshark to work. Long story short, I don't think it has anything to do with sudo/root privileges. As I tried logging in as root to run Wireshark and it froze up there as well.

I can use sudo to start up Wireshark and it runs fine. Until I go to select an interface to monitor packets, as soon as I get to that section 9 times out of 10 my entire computer just freezes up, forcing me to perform a hard restart. I can't even access the virtual terminal to kill the offending app.

I tried to compile the newer version of Wireshark from the official website but ran into some problems during the make install phase and was not able to find a debian binary package of version 1.2.4 anywhere.

I also tried to use Etherape as a replacement for Wireshark and when I tried to run that as root it froze up my computer as well.

---

### Post by blueshiftoverwatch on 2009-12-15
Bump.

---

### Post by blueshiftoverwatch on 2009-12-29
I Just did a fresh install of Ubuntu 9.10 and installing Wireshark was one of the first things I did. As soon as I hit the enter button to comfirm my password after trying to access Wireshark through gksudo my entire computer froze up the same as before.

I tried Wireshark out in OpenSUSE 11.2 and it worked just fine on it. But I prefer Ubuntu as I don't like RPM package management.

Am I the only one having these problems?

---

### Post by gsparky2004 on 2010-03-10
I'm also having the exact, same problem.  And I find it interesting that I'm also using an AMD64 quad-core processor.  I even have tried the exact, same solution as you (re-install Ubuntu, install Wireshark as first program).  Now, if I try to run Wireshark as sudo, as soon as I hit "Enter", Wireshark opens and then it locks up my system to such an extent that I have to perform a hard restart.  I'm thinking I may have to go to a different processor (an Intel-based one, for example), because I'm thinking the problem is AMD-based.

---

### Post by RasterBurn on 2010-03-12
well, looks like its a major bug in wireshark, like the 2 of you i am also running an AMD64 quad core processor (Phenom Black Edition 2.5Ghz), i am also running Ubuntu 9.10 64bit, my findings with it are that if i run wireshark as normal user, i can use the program just fine (that is if i dont have the urge to sniff my network) i say that in brackets cause it doesnt detect either my ethernet card or my wireless lan card (go figure) but if i try to load it with gksu then well, guess what, it freezes the computer forcing me to get off my lazy *** and press the reset button :P

---

### Post by blueshiftoverwatch on 2010-03-12
I'm currently running Wireshark 1.2.6 on Debian Testing and it's working fine on here as well. Must be a Ubuntu-specific issue.

---

### Post by RasterBurn on 2010-03-12
well i successfully tested it on UbuntuStudio64 under virtualization, though running it under virtualization is pointless for sniffing unless your virtualmachine is on the network instead of a virtual network

---

### Post by bethnesbitt on 2010-06-11
For me it's flash, although I am running the same thing with a wireless modem.  When i try to run to much flash I get the blank screen as well

---

