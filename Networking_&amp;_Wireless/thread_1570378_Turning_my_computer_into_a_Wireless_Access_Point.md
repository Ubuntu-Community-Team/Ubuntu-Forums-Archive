---
title: "Turning my computer into a Wireless Access Point"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by gallifrey on 2010-09-08
Hello, 
        I am in a situation at the moment which means I am going to be without an ISp for a week or two, and I can't survive that long without the intenet!!! What's more, I have 8 computers that need to connect, though not necessarily at the same time, but certainly more than one at a time. 

Anyway, I came up with an idea to buy a Mobile Broadband Dongle, and then share the connection via my PC. Problem is, I don't know how I would go about setting my PC to be a Wireless Access Point/makeshift Wireless Router, and sharing the connection. 

Any ideas/suggestions/solutions would be gratefully accepted!

Thank you kindly.

---

### Post by BkkBonanza on 2010-09-08
To do this your Wifi adapter must support **master mode**. Most common ones don't have driver support under Linux. The Atheros Atk9k driver is one that does. A few others do as well, though some of them are quite old now.

If you have master mode support then you need to install and configure **[hostapd]("http://hostap.epitest.fi/hostapd/")** and **[dnsmasq]("http://www.thekelleys.org.uk/dnsmasq/doc.html")** to do the most common AP functions (auth, dhcp, dns fwd). And then add some forwarding rules for routing.

(I've personally used an Atheros AR9281 from eBay for $19 inc.shpg. It works well and supports N mode. But it's miniPCIe card for notebooks so in a desktop you need a PCIe adapter. Mine is tucked inside a little mini-itx system.)

---

### Post by Sub101 on 2010-09-08
Many mobile phones can now be turned into wireless access points so you could look into that with your existing phone. I know Android can and a quick Google shows the IPhone can although I havent done so myself.

One thing to add, if your connecting 8 computers to a mobile network then it would be very slow! Not to mention the extreme cost.

---

### Post by gallifrey on 2010-09-08
> **BkkBonaza said:**
> To do this your Wifi adapter must support **master mode**. Most common ones don't have driver support under Linux. The Atheros Atk9k driver is one that does. A few others do as well, though some of them are quite old now.

If you have master mode support then you need to install and configure **[hostapd]("http://hostap.epitest.fi/hostapd/")** and **[dnsmasq]("http://www.thekelleys.org.uk/dnsmasq/doc.html")** to do the most common AP functions (auth, dhcp, dns fwd). And then add some forwarding rules for routing.

(I've personally used an Atheros AR9281 from eBay for $19 inc.shpg. It works well and supports N mode. But it's miniPCIe card for notebooks so in a desktop you need a PCIe adapter. Mine is tucked inside a little mini-itx system.)

Hi!

Thanks for the quick reply. Do you know if this is possible with either a broadcom b43 (4315, I believe) adapter or a Ralink RT2870? How would I find out? 

Many thanks.

---

### Post by gallifrey on 2010-09-08
> **Sub101 said:**
> Many mobile phones can now be turned into wireless access points so you could look into that with your existing phone. I know Android can and a quick Google shows the IPhone can although I havent done so myself.

One thing to add, if your connecting 8 computers to a mobile network then it would be very slow! Not to mention the extreme cost.

Alas, I only have a dongle. But this is only temporary, and I only need to be able to update and surf, so it's no biggie. It's just setting it up that is problematic.

---

### Post by Mammut1492 on 2010-09-08
try this one
 
[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

---

### Post by BkkBonanza on 2010-09-08
> Do you know if this is possible with either a broadcom b43 (4315, I believe) adapter or a Ralink RT2870? How would I find out? 

Probably not. Though if you have a windows machine then they might work there because Windows wifi drivers are often more functional. Hardly anyone bothers adding master mode to the linux ones (big thanks due to the Atheros groupies who are working that one). There are a couple AP programs for Windows.

Also, if you have a good router like the Linksys WRT54GL with open firmware, they support bridge mode which would allow you to pick up a wifi AP from somewhere else and relay it onto your own LAN. I've done that before. (Point antenna at Starbucks and drink lots of coffee...)

PS. I own both a Zydas ZD1211 and RT8180 and both wouldn't do master mode last time I tried a year ago.

---

### Post by gallifrey on 2010-09-08
Thank you all for your help. It would seem I don't have a single card that supports master mode, so I have been exploring an alternative; I have a wireless router. If I hard wire the computer with the 3G connection to it, could I set it up to share the connection through the router?? Somehow get the router to recognise that computer as the internet access point, rather than a phone line?

---

### Post by BkkBonanza on 2010-09-08
Yes, you can do that. It depends on a few things how you set that up.
What OS is the system with the 3G?
Does you router have a ethernet uplink port or a DSL uplink port?

---

### Post by gallifrey on 2010-09-08
> **BkkBonaza said:**
> Yes, you can do that. It depends on a few things how you set that up.
What OS is the system with the 3G?
Does you router have a ethernet uplink port or a DSL uplink port?

The system with the 3G is running Ubuntu, 10.04 with the 2.6.35 kernel. 

The router is a Belkin-N router. It normally connects to the internet via DSL, and has 4 ethernet ports in addition to wi-fi and the DSL port. What is the difference between a port and an uplink port??

---

### Post by BkkBonanza on 2010-09-08
The uplink port is a separate ethernet port from the normal 4 (which are tied together as a switch attached to 1 internal port). The uplink is the bridge to the internet usually, ie. the gateway outside vs. the LAN inside.

So with no ethernet uplink you will need to config the router to tell the LAN that the gateway is your 3G box - check if it allows setting the gateway different than it's own dsl port. Without seeing the functions in the router it's hard to know. 

Ideally you want it to still do DHCP but it tells the LAN the 3G box is the gateway.

Then on the 3G box you add some rules to do routing to the 3G interface.

---

### Post by gallifrey on 2010-09-08
> **BkkBonaza said:**
> The uplink port is a separate ethernet port from the normal 4 (which are tied together as a switch attached to 1 internal port). The uplink is the bridge to the internet usually, ie. the gateway outside vs. the LAN inside.

So with no ethernet uplink you will need to config the router to tell the LAN that the gateway is your 3G box - check if it allows setting the gateway different than it's own dsl port. Without seeing the functions in the router it's hard to know. 

Ideally you want it to still do DHCP but it tells the LAN the 3G box is the gateway.

Then on the 3G box you add some rules to do routing to the 3G interface.

Sounds good. I'll give it a go. Thank you. On a side note, I have found that my BCM4312 card (not 4315 as I thought) does not support master mode, but does support ad-hoc mode. Would I be able to work something with that??

---

### Post by BkkBonanza on 2010-09-08
Not really. Ad-hoc mode is for associating in a peer-peer fashion with another computer directly (no network). It isn't useful for networking as far as I know.

I can try to help with the 3G routing if needed. It's done with iptables.

---

### Post by gallifrey on 2010-09-08
That would be great. Any help is always appreciated. The router I have is a Belkin F5D8633-4, if that is any help. I have had a quick glance at the interface on 192.168.2.1, but I can't find anything obvious which I could do. Tried to telnet into it, but the connection was refused, as I suspect I am using the wrong port.

---

### Post by BkkBonanza on 2010-09-08
Looking at your manual I think your best bet is to disable DHCP on the router and just use it as a switch. You can install **dnsmasq** easily on the 3G machine and use it to do DHCP with itself as gateway. The router DHCP only supports broadcasting itself as gateway and that won't work.

1. Disable DHCP on router. 
2. On machine connected to 3G **sudo apt-get install dnsmasq**
3. A few config settings in /etc/dnsmasq.conf
4. Restart dnsmasq **sudo service dnsmasq restart**
5. See if other machines are pingable and visible on LAN with new DHCP settings
6. Add some iptables rules to setup forwarding to 3G interface.

What is **ifconfig** output on 3G machine? Will indicate how to write rules.

---

### Post by gallifrey on 2010-09-08
> **BkkBonaza said:**
> Looking at your manual I think your best bet is to disable DHCP on the router and just use it as a switch. You can install **dnsmasq** easily on the 3G machine and use it to do DHCP with itself as gateway. The router DHCP only supports broadcasting itself as gateway and that won't work.

1. Disable DHCP on router. 
2. On machine connected to 3G **sudo apt-get install dnsmasq**
3. A few config settings in /etc/dnsmasq.conf
4. Restart dnsmasq **sudo service dnsmasq restart**
5. See if other machines are pingable and visible on LAN with new DHCP settings
6. Add some iptables rules to setup forwarding to 3G interface.

What is **ifconfig** output on 3G machine? Will indicate how to write rules.

My ISP cut-off, so I was left without internet for a while :o Wasn't expecting it until tomorrow! 

Anyway, I saw your instructions just before my connection went down, but didn't print them out or save them! So I did what I could with what I could remember and a few educated guesses, and it seems it is working...albeit slowly, as is to be expected...
But I have two machines connected (3 if you count the 3G one), so it is looking good. :)

Thank you so very much for your help! It is much appreciated.

---

### Post by J3 Remy on 2011-10-28
I am currently trying to make an Acer Aspire One (model ZG5) a wireless access point.  The Ethernet controller is a Atheros Communications AR5001.  Currently there is not an installed OS, I am running Ubuntu 10.04 live on a USB.  Can someone explain to me how I can go about achieving this?  

Thank you,
J3

---

