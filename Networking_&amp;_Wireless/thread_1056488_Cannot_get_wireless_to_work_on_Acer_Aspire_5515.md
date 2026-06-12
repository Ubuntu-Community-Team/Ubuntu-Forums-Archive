---
title: "Cannot get wireless to work on Acer Aspire 5515"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by catseye2500 on 2009-01-31
I have bought my daughter an acer aspire 5515 and everything works great except the wireless in Ubuntu 8.10. The restricted driver claims to be working but I typed a ifconfig and get the following:

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:de:75:4a  
          inet addr:192.168.2.33  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fede:754a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4208 errors:0 dropped:587334420 overruns:0 frame:0
          TX packets:3863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4840091 (4.8 MB)  TX bytes:887056 (887.0 KB)
          Interrupt:221 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13904 (13.9 KB)  TX bytes:13904 (13.9 KB)

and when I typed lspci -v | less I get the following:

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Device 0428
        Flags: fast devsel, IRQ 18
        Memory at f0200000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: ath_pci

Can some one please help me get the wireless card to work. thanks in advance.

---

### Post by wvmaniac on 2009-02-03
Same EXACT problem here! Please help us! I bought my computer at Wally World for 348.99 for an extra computer to use when my wifey is using the HP (she is used to Windows and won't even try Linux). My HP interfaced perfectly with Ubuntu and I didn't have to install or "enable" the wireless. I found the .inf file in my ACER drive and installed it via the windows drive wrapper. Thanx in advance!

---

### Post by gzs22 on 2009-02-03
Hey guys! I had the same problem, I even thought there was no wireless in the model at all. But All u hav to do is download the proper driver~

Broadcom 802.11g Network Adapter BCM94312MCG - [http://www.mediafire.com/?ctxvypzdb3d](http://www.mediafire.com/?ctxvypzdb3d)


Peace !

---

### Post by crosenfi on 2009-02-03
[Here is the fix]("http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/") to get the wireless working for the Walmart Acer 5515:

For Ubuntu 8.10:
[LIST=1]
[*]Disable the 2 currently loaded Atheros drivers
[*]In terminal, enter "sudo apt-get install linux-backports-modules-intrepid-generic" (without the quotes)
[*]Reboot
[/LIST]

For Ubuntu 8.04:
[LIST=1]
[*]Disable the 2 currently loaded Atheros drivers
[*]In terminal, enter "sudo apt-get install linux-backports-modules-**hardy**-generic" (without the quotes)
[*]Reboot
[/LIST]

Enjoy!

-Carl

---

### Post by crosenfi on 2009-02-03
Oh, by the way, graphics (Compiz and video playback) performance is MUCH better using 8.04 than 8.10. You can boost it a little more by swapping out the one 1GB PC5200 ram chip for a 2GB chip to enable dual channel (newegg had a 2GB stick for $20+free shipping). 32bit Ubuntu will still only see 3GB total, but memory performance will improve by about 20%. Since the graphics uses main memory, this will help your framerates. I went from about 90fps (single channel) to 105fps (dual channel) in Compiz benchmark using Hardy Heron and 4GB of ram.

By the way, I'm a complete Ubuntu neophyte. 

Can you tell how much I've been tinkering with this fun $348 machine?

-Carl

---

### Post by Ric_NYC on 2009-03-04
> **crosenfi said:**
> [Here is the fix]("http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/") to get the wireless working for the Walmart Acer 5515:

For Ubuntu 8.10:
[LIST=1]
[*]**Disable the 2 currently loaded Atheros drivers**
[*]In terminal, enter "sudo apt-get install linux-backports-modules-intrepid-generic" (without the quotes)
[*]Reboot
[/LIST]

For Ubuntu 8.04:
[LIST=1]
[*]Disable the 2 currently loaded Atheros drivers
[*]In terminal, enter "sudo apt-get install linux-backports-modules-**hardy**-generic" (without the quotes)
[*]Reboot
[/LIST]

Enjoy!

-Carl


I have the same laptop!
I followed your instructions... but it didn't work.
Maybe I didn't "disable the currently loaded Atheros drivers".
How to do that?
Can anyone post step by step the way to disable the loaded Atheros drivers?


Any help is appreciated!

Thanks!

---

### Post by crosenfi on 2009-03-04
Go to System–>Administration–>Hardware Drivers and disable by un-ticking any Atheros options

Then install backports using terminal (in previous post)

Reboot

Then go back to System–>Administration–>Hardware Drivers make sure that “Support for 5xxx series of Atheros 802.11 wireless LAN cards” is enabled.

Reboot.

---

### Post by Ric_NYC on 2009-03-04
> **crosenfi said:**
> Go to System&#8211;>Administration&#8211;>Hardware Drivers and disable by un-ticking any Atheros options

Then install backports using terminal (in previous post)

Reboot

Then go back to System&#8211;>Administration&#8211;>Hardware Drivers make sure that &#8220;Support for 5xxx series of Atheros 802.11 wireless LAN cards&#8221; is enabled.

Reboot.


Hello!

Thanks...
I tried it... It didn't work.
I forgot do mention that I have Wubi instead of the regular Ubuntu installed. I guess the Wubi version has another way to get that fixed!


Thanks anyway.


I'm still trying to fix it!;)

---

### Post by mattl1 on 2009-05-01
I have same problem with aspire 5515... no wireless networking.
I have ubuntu installed on about 10 laptops/pcs and all others work great.
any problems i have had were solved from the boards, but i cant get this one.
To me, it seems there is no power to the wifi card, but i am at a loss, and no clue how to trouble shoot or repair.  The wireless had worked on vista, but i had the installer use the entire drive so for now, its plugged in to the router.

Any advise? 
I am glad to post results of reports or logs or files (?), but would ask for instructions of commands that i could copy paste.
jaunty 9.04
Thanks

---

### Post by catseye2500 on 2009-06-21
Sorry it took so long for me to reply, but i downloaded the latest madwifi drivers and installed them. rebooted and in the restricted drivers it had another option. I picked the other option and it started working.

---

### Post by MARAUDER2003 on 2009-07-08
If your laptop uses the atheros hardware, follow this guide
[https://help.ubuntu.com/community/WifiDocs/Device/AR5007](https://help.ubuntu.com/community/WifiDocs/Device/AR5007)

disable the driver first in the restricted driver setting (if you have one active)
then follow the guide
and then go to the restricted drivers setting and enable it once you reboot.
You will have to reinstall the driver if the kernel gets upgraded.

---

### Post by DaMirrorLink on 2009-07-15
Since this is the first result for google, HERE IS HOW TO GET IT TO WORK ON UBUNTU 8.10 ON ACER ASPIRE 5515.

1. Connect the laptop via ethernet cable, you will need it.
2. Go into System > Administration > Hardware Drivers and deactivate the current drivers.
3. Restart the computer
4. When its back up, open up Terminal and type the following in.

sudo apt-get install linux-backports-modules-intrepid
5. Wait for it to install everything and finish up, afterwards restart again.
6. Enable the new drivers if not already enabled.

---

### Post by bvirgin on 2011-03-14
The following work around actually works for the acer 5515 for ubuntu 10.10
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008/comments/19](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008/comments/19)

When he ask you to type &#8216;echo &#8220;pm-utils hold&#8221; | dpkg &#8211;set-selections&#8217; he made an error and you must use

&#8216;echo &#8220;pm-utils hold&#8221; | dpkg --set-selections&#8217; BTW this line must be typed and you can not use copy paste

---

