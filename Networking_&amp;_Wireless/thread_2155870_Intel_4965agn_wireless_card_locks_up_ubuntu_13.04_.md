---
title: "Intel 4965agn wireless card locks up ubuntu 13.04 on Dell 1521"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by jondin9604 on 2013-06-19
So far, I've managed to find all the Ubuntu help I've needed through general topic browsing and searches, so I first want to thank all the forum contributors for that. 

   Now, I've finally found a problem for which I may need some direct help myself. I'll apologize in advance if this post gets long.    

I'm trying to install an Intel 4965agn MiniPCI card into my Dell Inspiron 1521, but activating wireless completely locks up the computer. I cannot switch to other terminals and the only way out is to reboot the machine.     

To me, it appears that Ubuntu is picking up the card details, as the few commands I've tried so far seem to indicate correct information, but within seconds of turning on the external wireless switch, everything freezes.    

Here is some information which I hope will be useful to get this figured out.    

lspci | grep Wireless  gives  ```
 0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61) 
```  lsmod | grep iwl gives  ```
 iwl4965   112746  0  iwlegacy              100108  1 iwl4965 mac80211              606457  3 b43,iwl4965,iwlegacy cfg80211              510937  4 b43,iwl4965,iwlegacy,mac80211 
```    dmesg | grep less gives  ```
 [   13.204059] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree: [   13.205243] iwl4965 0000:0b:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4 
```    sudo lshw -C network gives ```
   *-network DISABLED              description: Wireless interface        product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection        vendor: Intel Corporation        physical id: 0        bus info: pci@0000:0b:00.0        logical name: wlan2        version: 61        serial: {removed}        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless        configuration: broadcast=yes driver=iwl4965 driverversion=3.8.0-23-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn        resources: irq:43 memory:fe8fe000-fe8fffff   *-network        description: Ethernet interface        product: BCM4401-B0 100Base-TX        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:03:00.0        logical name: eth1        version: 02        serial: {removed}        size: 100Mbit/s        capacity: 100Mbit/s        width: 32 bits        clock: 33MHz        capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.104 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s        resources: irq:21 memory:fe5fe000-fe5fffff 
```  uname -a gives ```
 Linux Johns-Lappy 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux 
```  sudo rfkill list gives ```
 0: phy0: Wireless LAN     Soft blocked: no     Hard blocked: yes 
``` 

I do have the wireless switch turned off now, so I can actually use the laptop.   

I'm sure that I've forgotten to include something, but hopefully this is a start to the debug.  

Again, thanks to anyone who is willing to help me try to get to the bottom of this.

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by jondin9604 on 2013-06-19
Yes, it is a used one I picked up off ebay. The original one (broadcomm  43??) was working fine, but I wanted to take advantage of my N router if  the upgrade cost was reasonable. 

This is the card I purchased.
[http://www.ebay.ca/itm/111085016955?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1497.l2649](http://www.ebay.ca/itm/111085016955?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1497.l2649)

From  what I've researched online, this card can be used in the 1521s. Many  of the parts sites I've seen have it listed as a compatible device for  the 1521. While I'm aware that you can't believe everything you read on  the net, once I find a few examples of different websites saying the  same thing, it makes it somewhat easier to believe. Plus, the cost was  reasonable (<$10), so if it didn't work, it was no big deal. I'd like  to try what I can get get it to work, before cutting my losses and  going back to the previous card, or trying something different.

This is one of the sites that indicated compatibility.
[http://www.parts-people.com/index.php?action=item&id=5063](http://www.parts-people.com/index.php?action=item&id=5063)

I had more examples of the card working, but cannot find the links as easily as I expected.

I  did find an example where the card was thought to be non compatible  with the 1521, but the last post indicates that they got the card  working with a different Windows driver. Windows isn't really an option  at this time, as I'm trying to move away from Windows as much as  possible.

[http://en.community.dell.com/support-forums/laptop/f/3518/p/19241071/19367359.aspx](http://en.community.dell.com/support-forums/laptop/f/3518/p/19241071/19367359.aspx)

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by steeldriver on 2013-06-19
iirc there were some (pre-production?) 4965 cards doing the rounds on ebay which throw an 'unsupported eeprom' error and never seem to work - although you should see that in dmesg I think - the card in this laptop is an original 4965 and that *does* work although on some previous kernels I think I needed to disable n-mode to make it stay connected reliably

---

### Post by jondin9604 on 2013-06-19
The 4965 was pretty much the first one I found that seemed to be compatible with the 1521, so I simply looked for an inexpensive one on ebay that was close to me for shipping. 

The BIOS is the latest one (A06) from what I can find.

From what else I've found so far, there is a MM1 "PRO" version (which I have), and an MM2 "Next Gen" version (which may be the one I need). I'm checking into that now, to see what else I can find out about them.

Thanks for the ideas so far.

---

