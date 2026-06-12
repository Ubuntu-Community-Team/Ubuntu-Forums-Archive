---
title: "Broadcom wireless crashing router?"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by Sylos on 2012-01-07
Hello all.

I have a perplexing problem that Im not really sure about how to diagnose. I have a BtHomehub wireless router that I have been using for my PS3 and laptop wireless connections for a couple of years now without any unusual issues. However, I recently bought another laptop and issues have begun to occur.

The new laptop is a packard bell easy note with a broadcom wireless adapter (I'll come onto the specifics later). The perplexing part is that my ps3 and old laptop still seem fine. But when I connect to the router with the new packard bell the router seems to crash quite often. It will be working fine for hours and then suddenly it just boots all of the wireless connections and I am unable to reconnect any of them. I have to restart the router than I can reconnect all devices again. Now, besides the expected once in a blue moon crashes we all get this never happens unless I am connected with the packard bell.

I know nothing about wireless and networking so I dont see how it is possible for the laptop to crash the router. I suppose thats my first question - can it?

Now, onto the specifics:

Im using ubuntu 10.04 LTS 64. I have installed/activated the STA driver from the Restricted Drivers app. Now info on the card:

```
lshw -C network
...
*-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 68:a3:c4:2f:b6:b2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.66 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:b2400000-b2403fff


```

```
lspci
...
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)


```

I know there is an alternative b43fwcutter driver for these cards but I have heard that it is worse than the STA. I would be grateful for any suggestions.

Cheers

EDIT: Also (dont know if this matters) ny router has been set up to give my ps3 a static address to allow easy connection of media server. The router is also set up to broadcast only on WPA (i think) NOT WPA/WPA2 as my old usb dongle for my desktop wouldnt work when both are selected.

---

### Post by chili555 on 2012-01-07
I love a mystery!

> I know there is an alternative b43fwcutter driver for these cards but I have heard that it is worse than the STA. That depends on your exact device. May we see:```
lspci -nn | grep 0280
```> ny router has been set up to give my ps3 a static address to allow easy connection of media server. I am, shall we say, suspicious. What is the address for the PS3? Is it inside or outside the range used by the DHCP server? For example, if your router is set to give DHCP addresses from 192.168.1.2 to 192.168.1.50, is the PS3 in that range or is it outside, perhaps 192.168.1.75?

I am thinking that it's maybe not the Broadcom wireless driver, but the relatively cheap (free?) router/modem has exceeded its ability to juggle devices.

---

### Post by Sylos on 2012-01-07
Hello and thank you for your time.

Heres the output:

```
lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)

```

Im not sure about the range for the ps3. It has been set this way for almost a year now. I believe I was in the advanced settings and there was an option along the lines of 'always use this address' which I selected. Would it make a big difference?

I did wonder if it was the router struggling to juggle too many balls but the crash happens irrespective of whether all devices are on and connected. Sometimes it does it with only two devices - other times with everything connected.

I'll see if I can get into my router settings and check the ranges. Is it safe security wise to post the static ip address here - seems like it could be used for bad things if someone impersonates a whitelisted device.

Cheers

---

### Post by chili555 on 2012-01-07
It should be safe to post an internal, private IP address. 90% of all the routers in the world have 192.168.x.x addresses, however, you may certainly disguise it.

I would not post a MAC address nor your public IP address issued by your ISP, which is certainly not 192.168.anything.

I'm not sure I really know the answer to your issue; the DHCP range just looked like a logical place to look. I'd set the PS3 outside the DHCP range to start.> Broadcom Corporation Device [14e4:4357]I believe STA is correct for your device.

Are there any clues here when the router caves in?```
sudo cat /var/log/syslog | grep -e wl -e etwork | tail -n25
```

---

### Post by Sylos on 2012-01-07
Thanks for the prompt reply.

I have just checked the DHCP range and the ps3 appears to be the first value in the range. Would moving to just outside the range help in some way?

I cant get my head around the problem. The house has the ps3, old laptop and infrequently used old desktop, and now the new laptop all running on wireless as well as my primary desktop running on ethernet cable. Using the old laptop, ps3 and old desktop on the wireless never gave issues. Now, when the old desktop hasnt been used for months, the new laptop seems to be the trigger (it never happens when this new laptop isnt on).I would have thought if the problem was the router itself it would have shown issues when running the old 3 wireless devices. The situation is basically the same - 3 wireless devices - just swap old desktop for new laptop. Hence I kinda decided to look at the new laptop as the cause.

I assume the code you have suggested there is to be entered at the terminal next time it craps out on me? I will give it a shot when it happens.

For clarity I should correct myself and state that the router is set to broadcst on WPA2 only NOT WPA only. Doubt it matters but who knows.

Any other ideas?

Cheers

---

### Post by chili555 on 2012-01-07
That's the fun of Linux and this forum. The interesting problems are very hard to get ones head around. That's what makes them interesting and rewarding to solve.> I have just checked the DHCP range and the ps3 appears to be the first value in the range. Would moving to just outside the range help in some way?We won't know until we try. The DHCP range is where the router will give out an address to anyone who asks for one and who has the correct WPA2 password. In your case, the router is told, except for one or more reserved addresses that are nonetheless inside the pool. I just wondered if we took the reservation exception out of the hands of the router, it might help. > I assume the code you have suggested there is to be entered at the terminal next time it craps out on me? Exactly. It will produce some lines of output that may or may not assist us to see what the wireless card was doing. So that we can compare the timestamps in the syslog file, it will be helpful to immediately also run:```
date
```If the last noted activity of the wireless card, Network Manager, et al was many minutes before the cave-in, then we will wonder if the wireless card is actually the culprit.

Do you see any logging in the administration pages of the router? Anything interesting there?

---

### Post by Sylos on 2012-01-09
Thanks for the advice.

Unfortunately I have not had the opportunity to try and catch any errors (connection has remained up). I am also having trouble trying to alter the static IP of the ps3. With this router you cant specify the IP address by typing it in - it just says the current addresss and has buttons for 'always use this address' - yes or no.

So I tried altering the dhcp range to start at a value above this - 66 instead of 65 - but that just returns an error from the router saying invalid range.

Im out in the uncharted territory here - I dont know if its usual for the router to not like that kind of setting chnage or if its just a lame router.

For now Im going to try another tactic - assign the laptop a static address and see if that makes any difference.

As soon as it fails again Im gonna get any info I can and post it up here.

Cheers

---

### Post by Sylos on 2012-01-15
Details from laptop:

```
Jan 14 10:39:16 saric-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-NMW3'.
Jan 14 10:39:27 saric-laptop avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Jan 14 21:58:13 saric-laptop kernel: [   14.417166] wl: module license 'MIXED/Proprietary' taints kernel.
Jan 14 21:58:13 saric-laptop kernel: [   14.421469] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 14 21:58:13 saric-laptop kernel: [   14.421480] wl 0000:02:00.0: setting latency timer to 64
Jan 14 21:58:13 saric-laptop NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Jan 14 21:58:50 saric-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-NMW3'.
Jan 15 10:44:23 saric-laptop kernel: [   15.027376] wl: module license 'MIXED/Proprietary' taints kernel.
Jan 15 10:44:23 saric-laptop kernel: [   15.084774] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 15 10:44:23 saric-laptop kernel: [   15.084784] wl 0000:02:00.0: setting latency timer to 64
Jan 15 10:44:23 saric-laptop NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Jan 15 10:44:59 saric-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-NMW3'.



Sun Jan 15 10:54:36 GMT 2012

```

Router log to follow

---

### Post by Sylos on 2012-01-15
PANTS!  Restarted the router to get connection bakc and the event log from the router doesnt seem to have anything in it from around that time. It skips form 1st jan to today (15th).  Will have to try again next time.

It seems there is nothing in the laptop output to suggest failure (to me the uneducated at least).

---

### Post by Sylos on 2012-01-15
Another crash.

Time on PC is 11:36.

Heres the router log:

```

11:36:08  15 Jan	LOGIN User admin logged in on [HTTP] (from 192.168.1.71)
11:36:02  15 Jan	LOGIN User Basic logged in on [HTTP] (from 192.168.1.71)
11:27:10  15 Jan	FIREWALL icmp check (1 of 2): Protocol: ICMP Src ip: 95.79.7.175 Dst ip: 86.134.68.228 Type: Destination Unreachable Code: Host Unreacheable
11:25:01  15 Jan	FIREWALL icmp check (1 of 5): Protocol: ICMP Src ip: 95.79.7.175 Dst ip: 86.134.68.228 Type: Destination Unreachable Code: Host Unreacheable
11:19:50  15 Jan	VOIP: [2.0A] [441353770722] [FXS DECT1 DECT2 DECT3 DECT4 DECT5] 200 OK - SIP message received
11:19:50  15 Jan	VOIP: [2.0A] [441353770722] [FXS DECT1 DECT2 DECT3 DECT4 DECT5] REGISTER - SIP message sent
11:19:06  15 Jan	VOIP: [2.0A] [admin12345] [] 501 Not Implemented - SIP message sent
```

---

### Post by chili555 on 2012-01-15
Frankly, I don't see much that's alarming here. The syslog shows a pretty normal connection. The only thing a bit mysterious is here:> avahi: Avahi disabled itself. If you want to use Avahi in this network, pleaseYou might Google this subject and try to fix it. I am not sure it's a fault that could cause your problem. You might try to gather more data with:```
sudo cat /var/log/syslog | grep -i avahi
```

As a start, I looked here: [http://ubuntuforums.org/showthread.php?t=1482573](http://ubuntuforums.org/showthread.php?t=1482573)

I am a bit confused here:> Another crash.

Time on PC is 11:36.

Heres the router log:
```
11:36:08  15 Jan	LOGIN User admin logged in on [HTTP] (from 192.168.1.71)
11:36:02  15 Jan	LOGIN User Basic logged in on [HTTP] (from 192.168.1.71)
11:27:10  15 Jan	FIREWALL icmp check (1 of 2): Protocol: ICMP Src ip: 95.79.7.175 Dst ip: 86.134.68.228 Type: Destination Unreachable Code: Host Unreacheable
11:25:01  15 Jan	FIREWALL icmp check (1 of 5): Protocol: ICMP Src ip: 95.79.7.175 Dst ip: 86.134.68.228 Type: Destination Unreachable Code: Host Unreacheable
11:19:50  15 Jan	VOIP: [2.0A] [441353770722] [FXS DECT1 DECT2 DECT3 DECT4 DECT5] 200 OK - SIP message received
11:19:50  15 Jan	VOIP: [2.0A] [441353770722] [FXS DECT1 DECT2 DECT3 DECT4 DECT5] REGISTER - SIP message sent
11:19:06  15 Jan	VOIP: [2.0A] [admin12345] [] 501 Not Implemented - SIP message sent
```Did the crash occur at 11:36? The only thing we see at 11:36 is a log-in; evidently to check the logs! I see nothing at all alarming.

---

### Post by Sylos on 2012-01-15
Hello Chilli. Thanks for checking the thread again.

The crash was maybe a minute before - say 11:35. And yes - I cant see anything at all happening on the log.


As for the AVAHI I am going to look into that but it appears to be from the day before so I assume is unconnected to the crash.

I have called my ISP and spoken to their 'tech' staff. They dont support linux (of course) but the kind man has apparently turned up the strength of the wireless signal (all the way to 11 according to him). Cant honestly think that it will solve the issue but might as well try. Sounds like somebody reading a cue sheet to me. Low signal strength could cause one or more devices to loose connection but for all to loose it at the same time and be unable to reconnect until router restarted - sounds more than jut signal strength. And the devices dont sure poor signal either.

Hey ho.

---

### Post by chili555 on 2012-01-15
> I have called my ISP and spoken to their 'tech' staff. They dont support linux (of course) Of course.

I have heard this lame excuse many times from my own ISP. I always tell them I am not asking for their support of my operating system; I am asking for a reliable connection at my DSL modem and since the cost of the modem is included in my service, I expect it to work as expected as well. After that, it doesn't matter if I use Windows, Mac, Linux, BSD, OS/2, RISC, etc. Either the service and the modem work or they don't.

I also threaten to drop in a Windows harddrive and call them back and then I ask if they just want to save us all trouble and fix it now.

Let me see, where is that Windows drive?...hmmm...I know I had one once...do y'all still use Windows 95?

---

### Post by Sylos on 2012-01-15
> **chili555 said:**
> Of course.

I have heard this lame excuse many times from my own ISP. I always tell them I am not asking for their support of my operating system; I am asking for a reliable connection at my DSL modem and since the cost of the modem is included in my service, I expect it to work as expected as well. After that, it doesn't matter if I use Windows, Mac, Linux, BSD, OS/2, RISC, etc. Either the service and the modem work or they don't.

I also threaten to drop in a Windows harddrive and call them back and then I ask if they just want to save us all trouble and fix it now.

Let me see, where is that Windows drive?...hmmm...I know I had one once...do y'all still use Windows 95?

I like your style.... ;):lolflag:

They are supposed to ring me back soon to see if it worked. Connection is still up - its an intermittent problem so could be fixed or not - only time will tell. Only problem is - since he 'fixed' it - the hub shows no wireless devices connected (even though they are) and subsequently wont forward the connection from PC to PS3 for my media server. Frying Pan -> Fire!

Gotta love it!

Cheers

---

