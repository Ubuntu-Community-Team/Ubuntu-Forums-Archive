---
title: "What wifi driver should I be using?"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by michiganitis on 2011-05-07
Alright...so I'm one of those people that is experiencing ridiculously slow wifi speeds after installing 11.04. I read some people had to load the latest ath5k or ath9k drivers. Which should I be using?

I'm on a Acer Aspire 5742-6674. In Windows, it's running with the Atheros AR5B95 drivers.

Also...after I determine which driver I should be using, how do I actually make my Ubuntu use them?

---

### Post by ajgreeny on 2011-05-07
That adapter should be fine with the standard kernel wifi drivers.  I have a netbook with that same adapter and have never had a problem with connecting, right up to the new 11.04.

---

### Post by michiganitis on 2011-05-07
> **ajgreeny said:**
> That adapter should be fine with the standard kernel wifi drivers.  I have a netbook with that same adapter and have never had a problem with connecting, right up to the new 11.04.

what else do you think could be the problem? i did not have this issue with 10.10. i have no problem right now with my wireless or wired on my windows 7 partition. and i have no problems with 11.04 when wired. but the wireless is SLOW!!!! and eventually stops working, at which point i have to restart the computer.

i've read dozens of threads of other people having slow wifi issues with 11.04 but no adequate fixes for me.

what do i do?

---

### Post by garvinrick4 on 2011-05-07
Here is a link that gives you the code for your driver issue: Copy and paste it in your terminal and reboot it seems:

[http://ubuntuforums.org/showthread.php?t=1746326](http://ubuntuforums.org/showthread.php?t=1746326)

[http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en](http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en)

---

### Post by michiganitis on 2011-05-07
> **garvinrick4 said:**
> Here is a link that gives you the code for your driver issue: Copy and paste it in your terminal and reboot it seems:

[http://ubuntuforums.org/showthread.php?t=1746326](http://ubuntuforums.org/showthread.php?t=1746326)

[http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en](http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en)

it looks like this is if i'm using either the ath5k or ath9k driver right now. i'm guessing that's what i'm using. how can i find out for sure?

thanks!

---

### Post by garvinrick4 on 2011-05-07
Run this code below: And look where I have red marked:

rick@rick-HP:~$ sudo lshw -C network
[sudo] password for rick: 
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:48:8f:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR=Red]iwlagn[/COLOR] driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 ip=xxxxxxxx latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:45 memory:d3500000-d3501fff

---

