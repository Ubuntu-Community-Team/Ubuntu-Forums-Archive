---
title: "WiFi issue in Ubuntu 10.10"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by binilbenjamin on 2010-10-13
Hi.

I'm facing a strange problem after upgrading my Ubuntu to 10.10.
After I start up the system, the wifi is not getting connected by default ( which was getting connected automatically in the earlier version). So I right click on network manager and click on 'Enable Wireless' option and it gets connected. So far so good. Now I close the laptop lid - it goes to sleep mode and after it wakes up, the wifi never gets connected. When I right click on the network manager icon, the 'Enable Wireless' option is disabled! I have to reboot my machine to get connected!
Here are the details:
```
Laptop : Lenovo U330
lshw -C network output:
*-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:0b:08:d6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=8.24.2.12 ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:e4500000-e4501fff
```

Could someone guide me to fix this please. Thanks in advance.

---

### Post by Forte125 on 2010-10-14
Exact same problem here.

---

### Post by Forte125 on 2010-10-14
I think I found a solution:

sudo rfkill unblock wifi

---

### Post by binilbenjamin on 2010-10-14
Hey, that worked! Thanks for that command
But isn't there any permanent fix for these two issues:
1. Enable wireless automatically on startup
2. Automatically connect to wireless rather than running the above command everytime system is back from sleep mode. (even after running the command, I've to right click on network manager icon and click on Enable Wireless option to get connected)

---

### Post by maymann on 2010-10-16
Same problem for me - I'm running on a Lenovo IdeaPad S12 with proprietary driver enabled - this is my lshw:
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth1
                version: 01
                serial: 00:26:82:2f:cb:45
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.14 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:19 memory:c2200000-c2203fff

anyone with a solution ?

---

### Post by maleki on 2010-10-16
Same problem here and also I can't connect to the wireless networks that I create !!!

Running 10.10 on a Lenovo IdeaPad Z560 , didn't have this problem in 10.04.

           *-network
                description: Wireless interface
                product: BCM4313 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth1
                version: 01
                serial: 00:26:82:9b:d7:fd
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:d9100000-d9103fff

---

### Post by jimrothstein on 2010-10-17
I'm also having wifi problem after 10.10 upgrade

Worked fine with 10.04
Sees various wifi signals; can not get IP 
Nothing seems to fix.

> 
Acer Aspire 5102
Atheros AR2413



> 
/etc/modprobe.d/blacklist-ath_pci.conf
#blacklist ath5k


> 
 $sudo lshw -C network

  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:66:5d:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:d0200000-d020ffff


> 
$sudo iwconfig

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off



---

### Post by rmtatum on 2010-10-17
Try what's mentioned at the following url:

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9134074&postcount=6]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9134074&postcount=6")

---

### Post by Forte125 on 2010-10-17
Still having the problem.  Lenovo ideapad V460...

---

### Post by sritacco on 2010-10-18
Looks like we lost something from 10.04...

Lenovo U series with Intel 5100 AGN

Once enabled again (from link above) Wireless N connections are locking up
after a while.  This device was working perfectly in current 10.04 with all
updates.  It seems stable on G connections.  I saw this exact behavior on
earlier versions of 10.04

Anyone know if there is a "backports" package that will fix it for now?

---

### Post by kennymchansen on 2010-10-18
I am having the exact same problem! 
I'm on a Lenovo 3000 v200 with 4965AGN wireless adapter. Perhaps it is related to this bug: [https://bugs.launchpad.net/bugs/630748](https://bugs.launchpad.net/bugs/630748) ?

---

### Post by jolla on 2010-10-18
> **sritacco said:**
> Looks like we lost something from 10.04...

Lenovo U series with Intel 5100 AGN

Once enabled again (from link above) Wireless N connections are locking up
after a while.  This device was working perfectly in current 10.04 with all
updates.  It seems stable on G connections.  I saw this exact behavior on
earlier versions of 10.04

Anyone know if there is a "backports" package that will fix it for now?


I have a problem with the N drivers as well (max speed 54Mb/s). Lenovo Thinkpad T400 with Intel 5100 AGN. No solution.

---

### Post by TBABill on 2010-10-18
My Realtek RTL8111 does not connect to networks it can see either. Works fine in 10.04.

---

### Post by ibnuyahya on 2010-10-21
I'm also facing wifi problem with my lenovo z360. I can connect to my wifi but it will disconnect frequently. Sometime it's freeze my router and i need to restart my router.I'm not facing this problem with 10.04.

I'm sure this is 10.10 problem since I have no problem when I use 10.04 and windows 7.

---

### Post by David802 on 2010-10-25
I had this same problem. The command worked great for me. Just thought I'd suggest one thing to those that are having trouble getting it to auto-connect on reboot. Before finding this post I read about using Wicd to try connect instead of the network manager thing that Gnome comes with. 

Theres a box that can be checked in the main Wicd screen underneath the wireless network you're currently connected to that says "Automatically connect to this network" After I checked that box my laptop automatically connects to my network when returning from sleep mode as well as after restarts. 

XD idk if this will help anybody but....

Thanks to forte125 for the fix! you are the BOMB!!!!!!


:P:P:P:P

---

### Post by invisiblemonki on 2010-10-25
I had this problem. very frustrating. I have to keep switching to 802.11G every time i want to use the ps3 or my bf's phone, so i tried that. bam, worked. i guess no 802.11N in 10.10 until something gets fixed.

---

### Post by agrisv on 2010-10-26
may lapot too are lenovo 3000 v200.. same problem with N type network and do not automaticaly enable addapter. need to pushing fn+f5 2x then i coud enable after sleep...

to enable N type in iwi4965:

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=0

but every time you restart pc you need to do this again.

---

### Post by mk500 on 2010-10-28
I'm also experiencing this problem with my Lenovo S12. On a clean install of 10.10, I have to do the following at each boot to get wireless up:

- rt click Network Manager Applet and select Enable Wireless
- click Network Manager Applet and click "Connect to Hidden Wireless Network" (my network is not hidden, but none are shown in list, so I have to do this)
- Choose my saved wireless network from Connection: dropdown
- Click connect on the window that pops up with all my grayed out settings

After every sleep/wake, I have to:

sudo rfkill unblock wifi
then do all of the above again

I've tried applying all the updates via Update Manager, but no help.

This is pretty frustrating. I tried installing Wicd, but it didn't benefit me (still had to go through all the above steps every time).

```
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:03:70:5e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.10.10.193 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f8000000-f8003fff
```

---

### Post by Carl.Spackler on 2010-10-28
> **agrisv said:**
> may lapot too are lenovo 3000 v200.. same problem with N type network and do not automaticaly enable addapter. need to pushing fn+f5 2x then i coud enable after sleep...

to enable N type in iwi4965:

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=0

but every time you restart pc you need to do this again.


Not sure if this has already been mentioned somewhere else. Look in /etc/modprobe.d/ for iwlagn or some variant filename and you should find a line that looks like this:

options iwlagn 11n_disable=1

change it to 

options iwlagn 11n_disable=0

and save. restart.

---

### Post by birkopf on 2010-11-02
> **Carl.Spackler said:**
> Not sure if this has already been mentioned somewhere else. Look in /etc/modprobe.d/ for iwlagn or some variant filename and you should find a line that looks like this:

options iwlagn 11n_disable=1

change it to 

options iwlagn 11n_disable=0

and save. restart.

Did you solved your problem with wifi? maybe madwifi drivers would help ?

I have Acer Aspire 7520 with Atheros chipset, and I'm not sure if I should update... 

PS - how is internet by wire working?

---

### Post by scotiangold on 2010-11-02
I just resolved a problem getting a wireless connection from my Acer  Aspire Netbook with Atheros AR5XXXX wireless adapter to my D-Link  DIR-625 Router that I want to share if it saves someone the wasted time  it took me to figure it out.

The mac address for the Atheros wireless device actually sent to the  router is different from that reported by the network manager in Ubuntu 10.04 on the Netbook. I only clued in when checking the router logs. Once I  configured the router to accept this mac address no problem connecting.

---

### Post by LostBits on 2010-11-03
I'm running into the same issue since my upgrade to Ubuntu 10.10 with my Encore ENLWI-N wireless adapter.

I haven't been able to find a good solution for this so I have installed a copy of Debian 5 on the machine and it works like a charm.  I would love to go back to Ubuntu though assuming this gets resolved quickly.

---

### Post by birkopf on 2010-11-04
> **LostBits said:**
> I'm running into the same issue since my upgrade to Ubuntu 10.10 with my Encore ENLWI-N wireless adapter.

I haven't been able to find a good solution for this so I have installed a copy of Debian 5 on the machine and it works like a charm.  I would love to go back to Ubuntu though assuming this gets resolved quickly.

Sometimes I think there shouldn't be another distribution like Ubuntu. If all thos developers would focus on Debian - Ubuntu will never be created but how good will be Debian by now ? 
We wouldn't have half of our current problems :-D

---

### Post by non-prophet on 2010-11-04
> **Forte125 said:**
> I think I found a solution:

sudo rfkill unblock wifi

Thanks a lot.  This worked for me - after much hair-pulling. :P:P

---

### Post by sritacco on 2010-11-05
On the lenovo's with the Intel 5100 the rfkill command does not help when
the n network connection locks.  I also looked into the suggestion about the MAC
address somehow changing and I don't believe my router is seeing that behavior
either.  Very frustrating, this laptop and Intel card was functioning reliably in 10.04.
I still have one machine I didn't upgrade to 10.10 and it works perfectly connected
to the n network.

---

### Post by maymann on 2010-11-06
Has anyone found the solution to the "disable wireless" problem that is in 10.10 but not 10.04 ?

Thanks in advance :-) !
~Maymann

---

### Post by SmoothFreeze on 2010-11-06
> **Forte125 said:**
> I think I found a solution:

sudo rfkill unblock wifi

omg thanks!!!!!!!!!!!!!

---

### Post by sailor420 on 2010-11-08
I've got this same issue. Lenovo IdeaPad U330 with Broadcom BCM4312 running the Broadcom STA driver. Have to reboot everytime my machine comes back from sleeping. Quite annoying. Didn't do this in 10.04.

---

### Post by sailor420 on 2010-11-11
Does anyone know if there is a bug in launchpad open for this?

---

### Post by Forte125 on 2010-11-11
It's possible.  I still am encountering the issue.  It seems the issue has to do with the broadcom driver though...

---

### Post by Def_101 on 2010-11-11
This worked for me.

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by Forte125 on 2010-11-12
No dice.  Still having the issue...

---

### Post by kaldor on 2010-11-17
I can confirm this with the Intel Pro Wireless 4965. Same issue on Fedora 14.

I never had wireless issues until this "wave" of distros.

---

### Post by kiki298 on 2010-11-17
Omg, thank you so much! Worked perfectly!

---

### Post by kiki298 on 2010-11-17
> **Forte125 said:**
> I think I found a solution:

sudo rfkill unblock wifi

OMG thanks SO much, worked perfectly :D

---

### Post by Forte125 on 2010-11-21
I fixed it! I FIXED IT!!!!

Hooray!

Try this first:

sudo rfkill unblock wifi

If that does not work (It didn't for me) try what's listed below:


1. Open up software center
2. Download Wicd
3. Go to System -> Preferences -> Startup Applications
4. Disable network manager at startup
5. Reconfigure your network in Wicd
6. restart


Report back if any of you are still having problems.

:D

Saturday night Linux FTW!

---

### Post by Forte125 on 2010-11-21
Bumping for shear joy that I finally found a fix for a problem that has been bothering my for months!

:D

Also, this means the bug is in the Gnome Network manager, so if anyone from the Gnome project stumbles upon this thread, get to it!.  I would, but it is beyond my skill level...

---

### Post by MikeA36 on 2010-11-21
Hey guys, wanted to share what worked for me.  I was having the same problem on my Gateway (ACER) laptop with 10.10.  Drove me nuts, disconnect randomly and completely FROZE up my D-link router.. had to reboot the router to get connected again.  

No solution found, until I changed my router from wpa2 down to wpa.  Has been rock solid ever since.  Didn't need to in 10.04, only 10.10.  You may want to try the same if still having router freezing issues.  

Mike.

Never mind.. after 2 days of stable connection, the problem has returned :(

---

### Post by tduccuong on 2010-11-24
> **non-prophet said:**
> Thanks a lot.  This worked for me - after much hair-pulling. :P:P

Hi, I think I might have found a better solution: First, issue command 'rfkill list'. If you see something like 'acer-wireless', then blacklist 'acer-wmi' module and restart. Thats it!

---

### Post by docrahul on 2010-12-12
hi

I am using HP mini and tried ubuntu 10.10 netbook edition. i am not able to configure my wireless or wired network connection to connect to internet. my system is not able to identify available network connections.

Please help

Thanx

---

### Post by Brian FitzGerald on 2011-02-04
> **Forte125 said:**
> I fixed it! I FIXED IT!!!!
1. Open up software center
2. Download Wicd
3. Go to System -> Preferences -> Startup Applications
4. Disable network manager at startup
5. Reconfigure your network in Wicd
6. restart


Hey, thanks for your help on this.  What are the steps for #5 above "Reconfigure your network in Wicd"?  I opened the Wicd control panel after installing but I'm not sure how to reconfigure my network.

Could you provide a bit of additional detail here?

Thanks,
Brian

---

### Post by Slave2Metal on 2011-02-04
> **Brian FitzGerald said:**
> Hey, thanks for your help on this.  What are the steps for #5 above "Reconfigure your network in Wicd"?  I opened the Wicd control panel after installing but I'm not sure how to reconfigure my network.

Could you provide a bit of additional detail here?

Thanks,
Brian

You need to input your ssid of your network, type of security(ie wep, wpa, wpa2) and security password, then connect.

---

### Post by Brian FitzGerald on 2011-02-05
> **Slave2Metal said:**
> You need to input your ssid of your network, type of security(ie wep, wpa, wpa2) and security password, then connect.

Thank you.  This sounds easy enough, but I'm not sure where I need to input this information.

Right now I am going to:

 - Applications > Internet > Wicd Network Manager
 - from there, under the network tab in the top-left I see an option to "create an ad-hoc network", I guess that's where I should add the information?  I didn't see anything else that looked right.  I tried this, and it asks me for the ESSID (is this the same as SSID?), IP (is this the internal IP address of the router?), Channel (what's this?), and whether or not I want to "activate Internet Connection Sharing" and "Use Encryption (WEP only)".

Am I even looking in the right place here?

Thanks,
Brian

ps, perhaps it's worth noting that the wifi was working fine earlier in the day and randomly stopped working (which led me to this post)

pps, sorry for the basic questions - I'm new to Ubuntu and apparently I suck at networking

---

### Post by Slave2Metal on 2011-02-05
When you open wicd, it should display the wireless networks around you.  If yours isn't showing up, then your ssid is not broadcasting.  Do you know the name of your network, is it encrypted and do you know how to access the router settings?

The ssid is the name that you would have given your network when you set up the router.

---

### Post by myhayserano on 2011-02-07
Gnome Network Manager bugs for the keyring password on login, so install pam-keyring to get around that.

This is a unofficial debian package. Worked for me. Cheers!

---

### Post by andrez1 on 2011-02-07
Forte125, thank you for the information. :)

---

### Post by fivedollar on 2011-02-11
> **tduccuong said:**
> Hi, I think I might have found a better solution: First, issue command 'rfkill list'. If you see something like 'acer-wireless', then blacklist 'acer-wmi' module and restart. Thats it!

So yea, this one worked for me.  I have an ACER netbook with a broadcom wifi card.

here is a good place to get info on how to blacklist modules...
[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

I made a new file: /etc/modprobe.d/blacklist-custom

then added the line: "blacklist acer-wmi", saved then rebooted, and BAM!  Auto-wireless.

---

### Post by secros on 2011-02-12
> **agrisv said:**
> may lapot too are lenovo 3000 v200.. same problem with N type network and do not automaticaly enable addapter. need to pushing fn+f5 2x then i coud enable after sleep...

to enable N type in iwi4965:

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=0

but every time you restart pc you need to do this again.

Just wanna say, this resolved my problem with x61 4965AGN.  To get around the pc restart, I put it in my rc.local file.  We'll see how it goes.

---

### Post by qwertyally on 2011-02-20
I just recently bought a Lenovo z560 and decided to try out Ubuntu since I like to root Android phones. Right off the bat on 10.10 Ubuntu didnt "see" my wifi. After spending hours trying to figure it out, had a buddy of mine help me. We found some links here that ive yet to try but will when i have time. See what you think...

[http://ubuntuforums.org/showthread.php?t=1424280](http://ubuntuforums.org/showthread.php?t=1424280)

[http://ubuntuforums.org/showpost.php?p=10283164&postcount=12](http://ubuntuforums.org/showpost.php?p=10283164&postcount=12)

---

### Post by kelarini on 2011-03-03
There seem to be two problems discussed on this thread:
1. having to explicitly activate/connect wireless upon resuming from sleep
2. when wireless *is* connected, it's intermittent

I've only had problem 2 on 10.10 (never had 1).  I have a Lenovo T61 with the Intel 4965 AG card...

Has anyone found a permanent solution to 2 yet?  I've tried a few of the alternatives here with no luck.

Thanks!!

---

### Post by gcomito11 on 2011-03-04
It seems that this is a reaccuring theme for 10.10 noone as of yet can reach faster than g 54mbps and when they get 54 they are getting intermitent, you would think the ubuntu master with all their forsight would come up with a solution, especially since the standard is now n across the board 300 mbps.  
 
Please ubuntu gods open up your sky and let down the mbps rain, bring floods of 300+mbps unto our lands.

---

### Post by rayansud on 2011-03-11
I just tried Ubuntu 10.10 in my Compaq Presario CQ40 as a LiveCD, and while I was using it, I could not connect to my Wi-Fi network. Is this and issue with the network/router or does LiveCD mode prevent you from using Wi-Fi? Thanks in advance!

---

### Post by conualfy on 2011-05-01
It's been a while since the upgrade to 11.4 and it's not so nice to know  that something basic as a wifi connection that should just work out of  the box it's not actually working.
Reconnecting the wifi connection makes the internet work again, but it's  just a matter of minutes or seconds before I have to do this operation  again.

I have changed the router encryption to none (I've lowered security by  using only the MAC filter) and there is no difference, it's showing that  I'm connected to the router, but the internet is not working at all.

I've just tried disabling the IPv6 and the bug is still here.

I tested the connection with this script:
[http://sourceforge.net/projects/wirelessscript/files/](http://sourceforge.net/projects/wirelessscript/files/)
The results for both the working wifi and the one not working (but showed by the network manager as connected) here:
[http://goo.gl/hyrZg](http://goo.gl/hyrZg) (reconnected, wifi working)
[http://goo.gl/sdgwL](http://goo.gl/sdgwL) (wifi not working)

I would allow some good willing specialist to debug this on my computer  or any other way he/she suggests. If there is anyone interested in  fixing this nasty bug, please send me an email on florin [at] drumliber  [dot] ro

PS: I'm using a laptop (Toshiba Satellite C650 with Atheros wifi card and wifi under Windows 7 work perfectly.

---

### Post by Lil Biscuit on 2012-06-17
Great thx for the help!
Dell Inspiron Duo
Still working on getting the touch screen to work correctly......

---

### Post by wildmanne39 on 2012-06-18
deleted

---

