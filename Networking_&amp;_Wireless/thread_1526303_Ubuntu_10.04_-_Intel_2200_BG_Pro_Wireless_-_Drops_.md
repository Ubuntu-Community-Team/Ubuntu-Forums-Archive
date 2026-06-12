---
title: "Ubuntu 10.04 - Intel 2200 BG Pro Wireless - Drops Connection After A Few Minutes."
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-07-07
I had some wireless issues with a laptop I put an Intel 2200 Pro Wireless BG card in. I realized I was losing connection, even though it would still say I was connected to the network. I pinged 8.8.8.8 (Google's DNS server) continuously. After about 5 minutes, I began getting dropped. I ran dmesg | tail and got this:

[ 2838.570290] ipw2200: No space for Tx
[ 2838.570300] ipw2200: Failed to send SSID: Reason -16
[ 2873.605561] ipw2200: No space for Tx
[ 2873.605573] ipw2200: Failed to send SCAN_REQUEST_EXT: Reason -16
[ 2908.635436] ipw2200: No space for Tx
[ 2908.635449] ipw2200: Failed to send SSID: Reason -16
[ 2943.670696] ipw2200: No space for Tx
[ 2943.670706] ipw2200: Failed to send SCAN_REQUEST_EXT: Reason -16
[ 2958.570617] ipw2200: No space for Tx
[ 2958.570627] ipw2200: Failed to send SSID: Reason -16

---

### Post by Roasted on 2010-07-08
Is it a bad sign if my wireless card comes up as eth0?

For what it's worth, I don't have a wired ethernet port in the laptop. (Long story, but it just doesn't work. it's disabled. wireless only)

---

### Post by Roasted on 2010-07-12
up

---

### Post by Roasted on 2010-07-13
Aight. Sick of this.

Someone help me out. I'm looking for a new wireless card. I'd like it to be an Intel, NOT a 2200, and have a PCI form factor for laptops, such as:

[http://www.laptoprepair101.com/wp-images/wi-fi-card/laptop-wireless-card.jpg](http://www.laptoprepair101.com/wp-images/wi-fi-card/laptop-wireless-card.jpg)

Thoughts?

---

### Post by Roasted on 2010-07-16
upppppppppppp

---

### Post by dca on 2010-07-16
FWIW, I thought Intel (I use a 4965ABGN with no issues) wireless was pretty well supported.  Is there any way you can go to alternate wireless location to make sure it's not an issue with your router?

---

### Post by dca on 2010-07-16
If you can guarantee that it works elsewhere than the only thing I can think of to root out the cause is to try removing network manager and installing WICD (*[http://wicd.sourceforge.net](http://wicd.sourceforge.net)*). See if you get the same results, if the problem goes away that will confirm the glitch is with network manager not working well w/ the iwl2200 firmware & kernel mods versus overall issue w/ firmware & mods...

---

### Post by dca on 2010-07-16
...one more and I'll shut up...  In the Windows XP world on the IBM t & R series lappies that have the ol' 2200, there was an issue where all of a sudden it would drop wireless connection.  The way people would get it back is to jack in via CAT5 cable and woila' [sic] that wireless would reconnect shortly after.  The root cause was the Intel driver was outdated.  Going to Intel site and running the update tool updated to latest version.  If someone else can confirm beyond a doubt that this is in Linux world a driver issue (hopefully doubt) and others are experiencing than maybe using 'ndiswrapper' with latest driver from Intel will solve issue?
 
Does this sound like your issue?
 
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg383287.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg383287.html)
 
By putting this in Google generates a few hits...
 
*ipw2200: Failed to send SCAN_REQUEST_EXT: Reason -16*

---

### Post by Roasted on 2010-07-16
The 2200 has quite a few bugs filed against it for the exact same issue, so once I ran into the issue with it and found the bugs, I didn't feel the need to try it at other access points. The same laptop with the Broadcom does not exhibit this, so that kind of narrows it down significantly.

My only problem is I need to find a "laptop pci" form factor card. The most common one I found was the 2200... It's an older laptop, so it's not a pci-e or pci-e half card like a lot of newer laptops...

EDIT - google shopping shows all of the results from that wifi card you suggested to be a pci-e half card...

---

### Post by Roasted on 2010-07-28
Up. Anybody know of any PCI laptop wireless cards I can get that work flawlessly without these ridiculous problems the 2200 exhibited?

Broadcom is completely out. I've always had bad luck with them.

Any suggestions?

---

### Post by sarloth on 2010-07-28
Hey Roasted, I have an ipw2200 as well and have noticed similar issues, though I just assumed it was a bad connection to the network. (It is a complex-wide shared wifi.) Have you tried WICD? It actually helped me A LOT on one of my older installs, I plan to try it when I get home today.

Since I am not at my laptop, would you mind posting the output of:

```
$sudo dmesg | grep ipw
```

So that I can see the driver version we are using in Lucid?

Thanks!

---

### Post by Roasted on 2010-08-11
Okay. I'm pissed.

I just got a new wireless card in. Atheros AR5001.

It works unsecured.
It does not work secured.

What can I do? I cannot believe I've been through 3 wireless cards with this ****ing laptop and I have yet to find one that works. 

Can anybody help before I boot to Windows for the remaining life of this device?

---

### Post by Roasted on 2010-08-12
upppppp

---

### Post by georgemc on 2010-08-13
Hi,

my olde laptop uses the Intel 2200bg.  On the surface it appears to stay connected however in the dmesg log I see numerous times where it looses connection and then immediately reconnects using wpa, about 5-6 times an hour.  The ping to 8.8.8.8 showed ~25ms most of the time and ~500ms when it reconnected.  I am within 10 feet of the wireless AP.

I goggled around and came across this bug report:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/295414](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/295414)

Now I did check and I am using the network manager currently. Also I m using Lucid 10.04.1LTS and Gnome.

Not sure if this is any help.

George

---

### Post by Roasted on 2010-08-13
Up again. I need this laptop WORKING. Been through 3 wireless cards. Broadcom, Intel, Atheros. I thought Intel and Atheros were the two big guns that are supposed to work?

I have an AR5001. I need info on how to get it working...

---

### Post by Roasted on 2010-08-19
hi

---

### Post by oldunixguy on 2010-09-11
I am having a slightly different problem with this- Completely new installation of Ubuntu 10.04.1 and Intel 2200bg pro wireless.

I have a WAP that has SSID broadcast disabled and WPA2 encryption. With a Win XP computer (running Intel's wireless pro drivers) I can create a profile and it works flawlessly. The laptop is assigned thru DHCP a 192.168.2.x address. I have also proved it is correctly working the same for a 2nd win xp laptop.

When I create the wireless profile on Ubuntu it seems to successfully complete the setup and reports connected.

However, the ifconfig indicates that it is enet1 AND it shows an address of 10.43.42.1 AND absolutely no traffic exists for any app I try.

I am positive the WAP is handing out 192.168.2.x

So, this is very messed up.

Any ideas?

thanks.

PS if this should be posted elsewhere please let me know.

---

### Post by edubski on 2010-12-20
I'm having somewhat of a similar issue with Intel 2200bg Pro/Wireless.  Ever since I upgraded to Lucid, my wireless works everywhere except at my dad's place.  Network Manager states my wireless is connected, but I can't get any web pages to load.  

What's weird is that we both have the same Netgear wireless routers.  His router is not secure and he's using DSL.  My router is WEP secured and using cable.  Now when i plug in the ethernet cable at my dad's place, it works fine. 

I was over there last night, and here is the post of the following command:

sudo cat /var/log/syslog.1 | grep -i error > errorlog

Dec 18 08:22:51 bigbrother NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 18 16:06:00 bigbrother NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 18 16:44:06 bigbrother kernel: [ 2304.345242] ipw2200: Firmware error detected.  Restarting.
Dec 18 17:20:14 bigbrother kernel: [ 4472.575041] [drm:subconnector_show] *ERROR* Unable to find subconnector property
Dec 18 17:20:14 bigbrother kernel: [ 4472.575110] [drm:select_subconnector_show] *ERROR* Unable to find select subconnector property
Dec 18 17:39:17 bigbrother NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 18 17:43:12 bigbrother NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 18 17:43:55 bigbrother NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 18 17:47:36 bigbrother NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 18 17:52:07 bigbrother NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 18 17:54:18 bigbrother NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 18 17:54:42 bigbrother NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 19 19:33:57 bigbrother NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files

Any suggestions would be appreciated.

Thanks

---

### Post by Roasted on 2011-10-25
Has anybody tried a newer version of Ubuntu with this card?

I just fired up Ubuntu 11.10 on this very same laptop that I posted about originally having issues. I decided to take this opportunity to dig out the Intel 2200 card I had and put it back in. Previously I had been using a Broadcom card in it (ick) and with 11.10 I was fighting with it a bit more than I cared to, so I yanked it and now I'm test driving the Intel.

So far I've been pinging a local news web site in 3 second intervals for over 700 intervals with no issues. That calculates out to over a half hour, which suggests it MIGHT actually be fixed in newer versions?

For what it's worth I'm using WPA Personal on my wireless security.

I'm going to let this laptop run overnight (disabling sleep, hibernate, etc) and see how it is in the morning. Meanwhile I figured I'd post and see if anybody else was still having issues with this card.

EDIT - Damnit... still acting up in 11.10 too...

---

