---
title: "Need Help Creating a Wireless Interface"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by SoulMazer on 2009-08-05
So, I have a wireless card in my laptop and I would like to get it working. It has an Atheros chipset, so I downloaded and installed madwifi. I have already done a "modprobe ath_pci", and now I am wondering why I still can't see my available wireless networks. A simple "iwconfig" returns "lo", "eth0", and "pan0", none of which have wireless extensions.

In order to get connected to a wireless network, do I have to create an interface myself? If so, how would I go about doing this?

Thanks in advance.

---

### Post by slakkie on 2009-08-05
What is the exact card you are using?

And btw: [https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

Also mentioning the Ubuntu version you are running will help others to help you :)

---

### Post by t0mppa on 2009-08-05
No, you don't have to create an interface yourself. Just open up a terminal and run **lshw -C network** and post back with the output, it will show what state your card is in and what driver is associated with it and will likely find the reason why there's no wireless interface on ifconfig.

---

### Post by SoulMazer on 2009-08-05
> **slakkie said:**
> What is the exact card you are using?
Sorry, I am using a "Atheros Communications Inc. AR9285 Wireless Network Adapted (PCI_Express) (rev 01).
> And btw: [https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)
Ok, well near the end of the procedure I noticed and tried this:
> With the new -ng module things work differently. An interface has to be created.```
wlanconfig ath0 create wlandev wifi0 wlanmode sta
```
When I tried running this line of code, I get the following error: "wlanconfig: ioctl: No such device"
> Also mentioning the Ubuntu version you are running will help others to help you :)
Sorry again, I was in a rush when posting this. But I'm running 32 bit 9.04.

> No, you don't have to create an interface yourself. Just open up a terminal and run lshw -C network and post back with the output, it will show what state your card is in and what driver is associated with it and will likely find the reason why there's no wireless interface on ifconfig.
Ok, well the output of the command pertaining to my wireless card is the following:
> 
*-network UNCLAIMED
description: Network controller
product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@000:08:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0

Thank you for all the replies. Now what is it that I have to do to solve this problem?

---

### Post by t0mppa on 2009-08-06
> **SoulMazer said:**
> Sorry, I am using a "Atheros Communications Inc. AR9285 Wireless Network Adapted (PCI_Express) (rev 01).

Have you tried ath9k with this card? It's a new driver that's completely free (doesn't depend on a proprietary Hardware Abstraction Layer like madwifi), works with mac80211 (instead of the old ieee80211 like madwifi) and it has 802.11n support.

> **SoulMazer said:**
> Ok, well near the end of the procedure I noticed and tried this:

```
wlanconfig ath0 create wlandev wifi0 wlanmode sta
```

When I tried running this line of code, I get the following error: "wlanconfig: ioctl: No such device"

If you check the Madwifi site that's linked into the Wiki page, you'll find that it says:

> If your svn snapshot is more recent than the 23rd January 2006, (r1407) than you can skip the following step:

If not, then follow these instructions to make a normal station mode interface. Type (as root):

wlanconfig ath0 create wlandev wifi0 wlanmode sta

I'm fairly sure your snapshot isn't over 3.5 years old, so you don't have to do that anymore.

> **SoulMazer said:**
> Ok, well the output of the command pertaining to my wireless card is the following:

> *-network UNCLAIMED
...


Unclaimed means that no driver is getting associated with your interface and that's why there's no ath0 or wifi0 to be found. Did the driver compile without errors? It should get associated when you run the modprobe that loads it. One thing you can check is running **lsmod | grep ath** and see which driver modules are currently loaded.

---

### Post by SoulMazer on 2009-08-06
First, thank you for the excellent feedback t0mppa.

Output from "lsmod | grep ath":
> ath_pci                  215096   0
wlan                     240368   1  ath_pci
ath_hal                  371488   1  ath_pci

> Have you tried ath9k with this card?
Well, I just tried a "sudo modprobe ath9k" and receieved no error and a "lsmod | grep ath" now additionally showed the following 3 things, along with the 3 above.
> ath9k                263352  0
mac80211             217592  ath9k
led_class             12036  ath9k, leds_hp_disk

> Did the driver compile without errors?
Just for the heck of it, I just re-compiled it and I received no errors.

> Unclaimed means that no driver is getting associated with your interface and that's why there's no ath0 or wifi0 to be found.
Ok, well I think I must be most of the way there. But what can I do to associate my driver to an interface?

Thanks again.

---

### Post by t0mppa on 2009-08-07
Ok, there shouldn't be any conflicts, as no other ath drivers are loaded. The interface should get associated with the drivers when you run the modprobe command, I'm not sure if you can bypass that in any way. Maybe the ath_pci simply doesn't support your chipset, I can't think of any other reason why it would function this way (feel free to get a second opinion on this though).

If you're going to try ath9k, you'll have to unload ath_pci first with **sudo modprobe -r ath_pci** and then make sure with lsmod that all the dependencies are gone as well. [Linux wireless]("http://linuxwireless.org/en/users/Drivers/ath9k") claims that it won't support your chip on a kernel older than 2.6.29 though, in which case you'd have to compile a new kernel for that as Jaunty is using 2.6.27.xx.

Then there's always ndiswrapper and using the Windows drivers, which usually works with just about any card, but since it means using proprietary software, I tend to favor the other options.

---

### Post by SoulMazer on 2009-08-07
> **t0mppa said:**
> Ok, there shouldn't be any conflicts, as no other ath drivers are loaded. The interface should get associated with the drivers when you run the modprobe command, I'm not sure if you can bypass that in any way. Maybe the ath_pci simply doesn't support your chipset, I can't think of any other reason why it would function this way (feel free to get a second opinion on this though).

If you're going to try ath9k, you'll have to unload ath_pci first with **sudo modprobe -r ath_pci** and then make sure with lsmod that all the dependencies are gone as well. [Linux wireless]("http://linuxwireless.org/en/users/Drivers/ath9k") claims that it won't support your chip on a kernel older than 2.6.29 though, in which case you'd have to compile a new kernel for that as Jaunty is using 2.6.27.xx.

Then there's always ndiswrapper and using the Windows drivers, which usually works with just about any card, but since it means using proprietary software, I tend to favor the other options.

Ok, well actually MadHatter21 just PM'd me and his instructions solved the problem. The instructions sent me to [http://linuxwireless.org/en/users/Download/stable/]("http://linuxwireless.org/en/users/Download/stable/") and I found that I had to update my kernel. However, after I updated my kernel to 2.6.30, my system would refuse to boot under that kernel version. So, I went back to my old kernel and tried to install the package there. It worked. I just compiled it, restarted and my card worked.

So, thank you everybody for your support, and most specifically MadHatter21 and t0mppa. Thanks again guys.

---

