---
title: "Building my own custom router?"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by shaggy999 on 2009-10-27
I am looking into building a headless Mini ITX or Flex ATX-sized server this Christmas that I will stick in a corner or closet that will do some basic server tasks like file server, print server, ssh, torrentbox, svn, etc. But what I was thinking is tossing a wireless card into the server and also making it a router to replace my current Linksys router and had a couple questions about this.

1) How feasible is it to do this? Do I need a special kind of wifi card to broadcast a network? Can I just use peer-2-peer settings + encryption?

2) I know you can bridge two network connections together, but can you bridge 3? I am thinking I would need dual NICS (one to connect to cable modem, one to a wired switch) plus a wireless card to connect the wireless clients. Would my server be able to hand out IP addresses on the same subnet to both wireless clients and clients connected via the NIC or would they be two seperate networks? My concern is making sure every system can "see" every other system on my network and all be able to get out to the internet through this server.

3) How BAD of an idea is this? I know it's generally recommended to keep servers behind a firewall or router to minimize attacks and also I don't know how hard it would be to set up this type of configuration. But it seems like if I set services up right, it should be generally safe.

My main compulsion for wanting to do this is because A) I think it would be a cool and fun project and B) I absolutely hate my router. It has very few settings and constantly needs to be rebooted. I have to admit that although I'm pretty good with computers I absolutely suck at doing complex networking configurations.

So what's the consensus? Should I just scrap this idea and buy a better router on top of the server compnents or is this actually doable?

---

### Post by carcar1 on 2009-10-28
I think it should work.  Look around of "ICS" or internet connection sharing.  You are most likely going to need to mess around with iptables.  

```
sudo apt-get install firestarter
```

That's a simple gui for iptables with input/output and does ICS.  Give that a try.  Tell me if it works!

---

### Post by t0mppa on 2009-10-28
> **shaggy999 said:**
> 1) How feasible is it to do this? Do I need a special kind of wifi card to broadcast a network? Can I just use peer-2-peer settings + encryption?

A bit of a yes and no. All wifi cards should support broadcasting a network (master mode), but not all wifi cards have Linux drivers that support it, thanks to not all hardware manufacturers warming up to the whole FOSS movement. For instance any 802.11n cards with a Broadcom chip on them aren't supported by the open drivers and the closed drivers from Broadcom only support the simpler modes. Atheros chips at least are well supported, check the [Wiki]("https://help.ubuntu.com/community/WifiDocs/MasterMode") for more information.

Of course the problem is that resellers likely aren't interested/educated on what chips the wireless cards they're selling use, so you'll probably have to do the research yourself.

> **shaggy999 said:**
> 2) I know you can bridge two network connections together, but can you bridge 3? I am thinking I would need dual NICS (one to connect to cable modem, one to a wired switch) plus a wireless card to connect the wireless clients.

As far as I know, no, bridging three is not possible. However, since you're going to be playing with firewall rules anyway, you can actually do a more elegant setup and just use firewall rules for forwarding specific traffic from any of the interfaces to the others.

> **shaggy999 said:**
> Would my server be able to hand out IP addresses on the same subnet to both wireless clients and clients connected via the NIC or would they be two seperate networks? My concern is making sure every system can "see" every other system on my network and all be able to get out to the internet through this server.

Yes it's possible to have them in the same subnet, not how I'd recommend you to do it though. It is very simple have them both on different subnets and then just create an extra route to any devices on either network that tells them they can access the other network with the router as a gateway. This way the IP always tells how a device is connected, you won't have to worry about overlapping DHCP ranges and it will make the router routing tables quite a bit easier to setup, since you don't have to make rules about what traffic to the same subnet goes through which interface.

> **shaggy999 said:**
> 3) How BAD of an idea is this? I know it's generally recommended to keep servers behind a firewall or router to minimize attacks and also I don't know how hard it would be to set up this type of configuration. But it seems like if I set services up right, it should be generally safe.

Personally I don't see that big of a problem with this, if you're using your server for sharing services on the local network and aren't worried about your local users trying to do something malicious. If you start setting up all sorts of services that are open to Internet, then you'd probably want to add an extra layer of security.

> **shaggy999 said:**
> So what's the consensus? Should I just scrap this idea and buy a better router on top of the server compnents or is this actually doable?

Sounds like a nice and educational project. It's really a question of motivation, time & budget. If you're in a hurry and don't want to spend a day reading specs, just go and buy a new router. :)

---

### Post by shaggy999 on 2009-10-28
Thanks for the input, I will probably try this if I can find the right hardware for the right price. That's good info on the wireless drivers. Is there a way to 'query' a wireless card that's plugged into a linux system and is recognized by ubuntu to see if it supports this master mode? I have one right now that I use in my desktop machine and it works out-of-the-box with no fuss. I would like to see if that one supports this mode. If it does I could just get an identical one for the other machine.

---

### Post by Iowan on 2009-10-28
I built/used a [FREESCO]("http://en.wikipedia.org/wiki/FREESCO") router (on a '486) until I upgraded to DSL.

---

### Post by t0mppa on 2009-10-28
You can run **lshw -C network** to find out what chip and driver the wireless card is using. [Here]("http://en.wikipedia.org/wiki/Comparison_of_open_source_wireless_drivers#Driver_capabilities")'s a listing of open source drivers for Linux that should be somewhat up-to-date and show whether or not they support master mode. Windows drivers through NDISwrapper don't support it. Then the other option is to do searches by driver or chip name with the help of our good friend Google.

---

### Post by shaggy999 on 2009-10-30
So I ran that command and got this:

> 
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wmaster0
       version: 00
       serial: 00:1a:ef:04:99:3c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=rt61pci** ip=192.168.1.2 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:e9200000-e9207fff



So it looks like it uses the rt61 driver. I checked that list and it didn't list rt61 in the driver capabilities section, so I did an lsmod and grepped for 'rt' and got:

> 
xt_multiport            3552  1 
rt61pci                23556  0 
crc_itu_t               2336  2 udf,rt61pci
rt2x00pci               9216  1 rt61pci
rt2x00lib              34624  2 rt61pci,rt2x00pci
led_class               5256  1 rt2x00lib
input_polldev           4720  1 rt2x00lib
mac80211              210104  2 rt2x00pci,rt2x00lib
cfg80211              109144  2 rt2x00lib,mac80211
eeprom_93cx6            2528  1 rt61pci
parport                40528  2 ppdev,lp
x_tables               25832  2 xt_multiport,ip_tables


It mentions the rt2x00 as well as the rt61 driver. What does that mean? The only other network device I have is an RTL8111/8168B Gig-E onboard ethernet, which I don't think is driven by that driver.

Anyway, I will probably have to get an ath9k card I think if I do this.

---

### Post by t0mppa on 2009-10-31
As you can see, the Wiki page lists the rt2x00 though. Apparently it's a common unit that's used by drivers for all 2400, 2500 & 2800 series of chips (the name suddenly starts making a lot of sense). Anyway, it appears like your card & driver should be perfectly compliant, as can be seen from [here]("http://my.opera.com/CrazyTerabyte/blog/2009/10/23/wi-fi-with-master-mode-finally") for instance.

---

### Post by shaggy999 on 2009-11-02
cool. thanks

---

