---
title: "Broadcom 4353 wifi help on ubuntu 9.04 on my HP Mini 5101"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by wily6 on 2009-09-11
Hey I've been trying to get wireless on my new HP Mini 5101 netbook for quite a while now...
i've tried using the b43 / ndiswrapper but nothing has worked thus far and i've been just doing a fresh install after each successive fail :confused:

here's some info:

08:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
20:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 10)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:b3:7f:54:99  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:b3ff:fe7f:5499/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2084349 (2.0 MB)  TX bytes:227018 (227.0 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions


i can post any other information too. i'm pretty new to this so any help is greatly appreciated. thanks in advance =]



FIXED 

follow this guide 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction)

but use


[ftp://ftp.hp.com/pub/softpaq/sp44001-44500/sp44185.exe](ftp://ftp.hp.com/pub/softpaq/sp44001-44500/sp44185.exe)

at the wget part

---

### Post by misha680 on 2009-09-16
I just posted this as a HOWTO but it has to be approved. Though I would post here:

Here are some notes. Adapted from [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/) very helpful.

1. Download here:
[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

Follow instructions to install on flash (1GB or larger):
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

2. Boot up your system. On boot press F10 to go into configuration

Go to System Configuration -> Device Configuration -> Dual Core CPU and disable

[http://ubuntuforums.org/showthread.php?t=1115691](http://ubuntuforums.org/showthread.php?t=1115691)

the N280 Atom only has one core anyway
[http://ark.intel.com/Product.aspx?id=41411](http://ark.intel.com/Product.aspx?id=41411)

Personally, I prefer the Function Key Switch to be Enabled as well, but that is personal preference.

3. Go to File -> Save Changes and Exit and press F10.

4. Now when the computer boots up (make sure your flash is inserted) press F9 and select USB Flash Drive. Boot off of it and
install Ubuntu Netbook Remix (I will leave a gap here - plenty of info about this).

5. Once installed:

You want an updated version of the wl driver that supports the broadcom 4353 module (there is an NDISwrapper alternative here but that did not seem to work for me:
[http://ubuntuforums.org/showthread.php?t=1263730](http://ubuntuforums.org/showthread.php?t=1263730)
)

I adapted this from (rather copy & pasted)
[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

"This is easy — you just need to install the driver back-ported from the next Ubuntu release.

First, enable the backports repository: Administration > Software Sources > Updates and enable “Unsupported Updates (jaunty-backports)”.

Then, open Synaptic Package Manager, find the package linux-backports-modules-jaunty, and install it."

Also, you will need to install linux-restricted-modules if you haven't. I am not sure if this is automatic or not.

Finally, you might need to go to System -> Administration -> Hardware Drivers and enable the Broadcom Wireless chipset. Enjoy!

p.s. More info:

2gb RAM modules
[http://www.hpminiguide.com/forums/viewtopic.php?p=16430](http://www.hpminiguide.com/forums/viewtopic.php?p=16430)

This ebay seller seems to have compatible keyboard covers:
[http://myworld.ebay.com/komazys?ssPageName=ADME:X:CEM:US:1181](http://myworld.ebay.com/komazys?ssPageName=ADME:X:CEM:US:1181)

radtech will cut ScreenSaverz for this netbook
Nushield will make screen protectors

still looking for a cover for the whole thing a la
[http://stores.shop.ebay.com/3acp__W0QQ_armrsZ1QQ_fsubZ487078016](http://stores.shop.ebay.com/3acp__W0QQ_armrsZ1QQ_fsubZ487078016)

will ask if this works


Misha

---

### Post by freackout on 2009-09-16
> **misha680 said:**
> I just posted this as a HOWTO but it has to be approved. Though I would post here:

Here are some notes. Adapted from [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/) very helpful.

1. Download here:
[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

Follow instructions to install on flash (1GB or larger):
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

2. Boot up your system. On boot press F10 to go into configuration

Go to System Configuration -> Device Configuration -> Dual Core CPU and disable

[http://ubuntuforums.org/showthread.php?t=1115691](http://ubuntuforums.org/showthread.php?t=1115691)

the N280 Atom only has one core anyway
[http://ark.intel.com/Product.aspx?id=41411](http://ark.intel.com/Product.aspx?id=41411)

Personally, I prefer the Function Key Switch to be Enabled as well, but that is personal preference.

3. Go to File -> Save Changes and Exit and press F10.

4. Now when the computer boots up (make sure your flash is inserted) press F9 and select USB Flash Drive. Boot off of it and
install Ubuntu Netbook Remix (I will leave a gap here - plenty of info about this).

5. Once installed:

You want an updated version of the wl driver that supports the broadcom 4353 module (there is an NDISwrapper alternative here but that did not seem to work for me:
[http://ubuntuforums.org/showthread.php?t=1263730](http://ubuntuforums.org/showthread.php?t=1263730)
)

I adapted this from (rather copy & pasted)
[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

"This is easy — you just need to install the driver back-ported from the next Ubuntu release.

First, enable the backports repository: Administration > Software Sources > Updates and enable “Unsupported Updates (jaunty-backports)”.

Then, open Synaptic Package Manager, find the package linux-backports-modules-jaunty, and install it."

Also, you will need to install linux-restricted-modules if you haven't. I am not sure if this is automatic or not.

Finally, you might need to go to System -> Administration -> Hardware Drivers and enable the Broadcom Wireless chipset. Enjoy!

p.s. More info:

2gb RAM modules
[http://www.hpminiguide.com/forums/viewtopic.php?p=16430](http://www.hpminiguide.com/forums/viewtopic.php?p=16430)

This ebay seller seems to have compatible keyboard covers:
[http://myworld.ebay.com/komazys?ssPageName=ADME:X:CEM:US:1181](http://myworld.ebay.com/komazys?ssPageName=ADME:X:CEM:US:1181)

radtech will cut ScreenSaverz for this netbook
Nushield will make screen protectors

still looking for a cover for the whole thing a la
[http://stores.shop.ebay.com/3acp__W0QQ_armrsZ1QQ_fsubZ487078016](http://stores.shop.ebay.com/3acp__W0QQ_armrsZ1QQ_fsubZ487078016)

will ask if this works


Misha

sounds bit long winded well i found an easy solution to this upon my bad habit of keep re-installing stuff ect 32/64 bit changing distros to find out an easy solution with this model i used many ways with differing results most worked eventually but some distros are easier than others like mint linux hit the wireless tab on the menu as long as your on the net wired it will download and setup automatically for you, mint is completely compatible with ubuntu. i first noticed this two years ago with sam linux on broardcom devices

---

### Post by donghui86 on 2010-04-07
Maybe it's good to do this,but a new one is better

---

