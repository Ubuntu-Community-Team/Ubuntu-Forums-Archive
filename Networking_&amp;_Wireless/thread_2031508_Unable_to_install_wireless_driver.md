---
title: "Unable to install wireless driver"
date: 2012-07-22
forum: Networking &amp; Wireless
---

### Post by hrjanardhan on 2012-07-22
I am using Dell Inspiron 15R 5520, using ubuntu 12.04
The additional driver shows only ATI  FGXLR proritary driver, and no broadcom drivers.
HOw to enable wireless in my device?

---

### Post by Bucky Ball on 2012-07-22
Plug in with a cable, do an update, check Additional Drivers again. If that doesn't work, with the cable in, make sure you have these two installed:

b43-fwcutter
firmware-b43-installer

After installation you may need a reboot. 

If neither works, please provide the output of this, from your terminal (Applications>Accessories>Terminal, then copy/paste the text below and hit enter, then copy/paste the output here):
```

sudo lshw -C network
```

That will tell us your card. Cheers and welcome to the forums. ;)

---

### Post by hrjanardhan on 2012-07-22
[sudo] password for hrjanardhan: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 05
       serial: d4:be:d9:2d:d1:ab
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
 bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c1500000-c1507fff
THIS IS WHAT I GOT......I TRIED EVERYTHING U HV SAID BEFORE

---

### Post by bkratz on 2012-07-22
the following terminal  commands would help determine what card you have (what type of Broadcom)


lspci -nnk | grep -iA2 net

 rfkill list all

---

### Post by hrjanardhan on 2012-07-22
hrjanardhan@ubuntu:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:056a]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
    Subsystem: Dell Device [1028:0016]
hrjanardhan@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
THIS IS WHAT I GOT

---

### Post by Bucky Ball on 2012-07-23
> **bkratz said:**
> the following terminal  commands would help determine what card you have (what type of Broadcom)


lspci -nnk | grep -iA2 net

 rfkill list all

It's already determined in the ouput in post #3. It is a Broadcom card but, for some reason, there is a Realtek driver installed. Was this installed manually???

```
description: Network controller
[B]product: Broadcom Corporation
vendor: Broadcom Corporation[/B]
physical id: 0
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
*-network UNCLAIMED
```

There are two network controllers, both Broadcoms according to your output. The ouput of the one above looks like it's installed, connected at 100Mbps, and ready to go; just needs some configuring. The other isn't installed and I suspect you are trying to connect with that. Recognised but no drivers. I imagine these two entries are somehow one in the same card???

Open Network Manager, delete both wireless connections, restart. What happens? Run 'sudo lshw -C network' again and post back, please. ;)

---

### Post by hrjanardhan on 2012-07-23
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 05
       serial: d4:be:d9:2d:d1:ab
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c1500000-c1507fff


NOW ITS BIT DIFFERENT FROM PREVIOUS OUTPUT, I HAD ACTUALLY INSTALLD A DRIVER FROM SOFTWARE CENTRE(DIDNT WORK).. NOW UNINSTALLED IT!!!!!!

---

### Post by Bucky Ball on 2012-07-23
Okay, good. Broadcom generally play nice with Linux so hopefully your card should be fairly easy to get up. Can you get online with a cable and do an update then check 'Additional Drivers', please? Is there a b43 or STA driver disabled in there or was your card detected during the updates?

If that gives you no joy, while still online, install these two from Synaptics or Software Centre:

b43-fwcutter
firmware-b43-installer

Reboot. Anything? Run the 'sudo lshw -C network' command again and see if the Network Controller is 'Claimed'.

---

### Post by hrjanardhan on 2012-07-23
Well, the first case didnt work.
And b43-fwcutter and firmware-b43-installer are already installed. Nothing happened.

---

### Post by bkratz on 2012-07-23
> **hrjanardhan said:**
> Well, the first case didnt work.
And b43-fwcutter and firmware-b43-installer are already installed. Nothing happened.



Well, b43 is not the right one for your device when we found out what Broadcom you actually have (back in post 5)

08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)

a quick search shows no good news.  If you read this thread (three pages) esp. post 13

[http://ubuntuforums.org/showthread.php?t=2014096](http://ubuntuforums.org/showthread.php?t=2014096)

You will see that the only available method is with ndiswrapper (and that is not guaranteed) 

Here is a bug listing about it too.

[https://bugs.launchpad.net/ubuntu/precise/+source/bcmwl/+bug/923809](https://bugs.launchpad.net/ubuntu/precise/+source/bcmwl/+bug/923809)

---

### Post by hrjanardhan on 2012-07-23
Okay!!! Then I will probably go back to 11.10 instead and wait  for this problem to be resolved. Thank You BuckyBall and bkratz fr your time and support. :) But please do let me know if u find its resolved.

---

### Post by bkratz on 2012-07-23
> **hrjanardhan said:**
> Okay!!! Then I will probably go back to 11.10 instead and wait  for this problem to be resolved. Thank You BuckyBall and bkratz fr your time and support. :) But please do let me know if u find its resolved.


Sorry, but good luck--will keep an eye out for a solution.

---

### Post by Bucky Ball on 2012-07-23
Broadcom are friendly so it should only be a matter of time before that card is supported (probably in 12.04 rather than any update to the 11.10 kernel). ;)

@ bkatz: This gives me little idea what we're looking at:

```
Broadcom Corporation Device [14e4:4365] (rev 01)
```

What model is that? Could be anything. If you have some idea please enlighten me ...

---

### Post by hrjanardhan on 2012-07-24
Yeah you r right Bucky. I tried installing previous version of ubuntu and same problem. So the issue is with the Broadcom. Gotta wait till its supported. And I dont know which model it is.
Thank You.

---

### Post by NikTh on 2012-07-24
Hi , 
can you please try this.. 
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
``` 

Reboot your pc and see if wireless work. 

THanks

---

### Post by hrjanardhan on 2012-07-24
Did not work NikTh

---

### Post by NikTh on 2012-07-24
Hi , 
yes i think its not worth to try fix this problem , cause its a known problem , with unsupported device.

I hope developers will fix this soon . 

Maybe another option (that might work OR NOT) its to try install nsidwrapper and driver from windows. (i cannot guide you through) 

Thanks

---

### Post by hrjanardhan on 2012-07-24
ndiswwrapper doesnt work.. tried it already... only option is to wait keeping ma fingers crossed.
Thank you for your time and support.

---

### Post by Bucky Ball on 2012-07-24
You tried ndiswrapper? It is problematic and can, on occasion, cause other drivers not to install as it has something already installed for the card, even if it is a Windows driver that isn't working for you. Are you sure you uninstalled ndiswrapper *completely* before trying anything else?

* Just looking at your output from lshw -C network and there's no driver installed, at least not there.

---

### Post by hrjanardhan on 2012-07-24
Yep BuckyBall.... ndiswrapper was the last effort i made.

---

### Post by Bucky Ball on 2012-07-24
Maybe follow the instructions in Answer 1 here:

[http://askubuntu.com/questions/19013/how-do-i-remove-ndiswrapper-completely](http://askubuntu.com/questions/19013/how-do-i-remove-ndiswrapper-completely)

That will completely kill it. Then reboot. If still nothing, then try the update/additional driver/b43 route. As I mentioned, the b43 might not be loading because ndiswrapper is hogging something. Or your card may really not be supported. This may actually tell us the model though so we can keep digging. ;)

---

### Post by hrjanardhan on 2012-07-25
ndiswrapper is completely removed. No change.

---

### Post by wildmanne39 on 2012-07-25
Hi, the only people that had this device working had 11.10 installed by dell when they bought there computers, here is the bug report from a previous thread that I worked on and there is not a solution at this time unless you have a dell that came with 11.10 installed.
[https://answers.launchpad.net/ubuntu-certification/+question/200767](https://answers.launchpad.net/ubuntu-certification/+question/200767)
Thanks

---

### Post by hrjanardhan on 2012-07-25
I think this wireless card is not supported right now. Gotta wait
Take a look at this
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)
And my wireless card is Dell Wireless 1704 802.11b/g/n(2.4Ghz)

---

### Post by Geda on 2012-09-10
after searching for a day i found this solution [http://wielki.tk/vostro/debs/wlan_amd64.deb](http://wielki.tk/vostro/debs/wlan_amd64.deb)
from this link [https://answers.launchpad.net/ubuntu-certification/+question/200767](https://answers.launchpad.net/ubuntu-certification/+question/200767)

tested and working on inspiron 5520 using 12.04

---

### Post by hrjanardhan on 2012-09-11
Hey Geda... it says wrong architecture 'amd64'

---

