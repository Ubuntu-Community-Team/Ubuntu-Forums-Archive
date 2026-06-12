---
title: "lucid wireless issues"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by maclenin on 2010-09-21
Equipment - 

Laptop: HP 6910p
Wireless Card: BCM4312

Background - 

* NO issues with wireless in 8.10 (intrepid) - fwcutter driver.
* Performed clean install of 10.04 (lucid) onto a brand new hard drive (July 2010) - fwcutter driver.
* NO issues with wireless in 10.04 (lucid) until a few days ago, when...

...(first) my laptop shutdown because the battery died

and

...(second) I safe-upgraded to 2.6.32-24-generic

Currently - 

1. I have chronic wireless connectivity issues - slow to non-existent.
2. Ping tests (ping -c6 google.com or ping -c6 4.2.2.1) sometimes reveal 0% loss, sometimes 100% loss, sometimes "unknown host" - within 5 minutes of each other.
3. Regardless of ping results, web pages are consistently slow to load.
4. Skype will also cut out from time to time as the wireless connection vacillates.
5. I have a MacBook Pro which I am using as my (wireless and consistently well-connected) control - and from which I am currently forced to draft this note....
6. I am connecting via proxy (hotspot)....

Thanks for any thoughts!

---

### Post by samuel.faith on 2010-09-21
This probably might be a fix for you. I encountered different but vaguely similar problem like yours.

[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx]("http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx")

---

### Post by maclenin on 2010-09-22
Thanks, Samuel for the suggestion. I am currently using the fwcutter driver, which I think is diff. from the one you are suggesting I try (STA) to "back-date"...moreover, I don't have access to a network cable - so, I am not so anxious to swap / re-install wireless drivers at this stage....

Is there anyone else out there who saw a MARKED decline in wireless performance with the "upgrade" to the 2.6.32-24-generic kernel?

---

### Post by maclenin on 2010-09-23
And another quick note: ALL ELSE SEEMS FINE with regard to wireless operations - the signal strength is in the 70% range (3 out of 4 bars) - I am being assigned an IP address by the router - speed indicated at 54 Mb/s - just SLUGGISH (at best) to non-existent page-loading...very inconsistent / sporadic performance...

...hmmm....

---

### Post by maclenin on 2010-09-24
Any trouble-shooting suggestions? Again, I am connecting via proxy - all signs point to strong connectivity, however, actual performance is very poor - for all network functions, including: web / skype / software updates and upgrades via the terminal / ftp....

---

### Post by maclenin on 2010-09-25
Any ideas? It's a shame that there is ZERO "official" / timely response regarding these kinds of issues - clearly, a large number of folks are having wireless difficulties. Why silence on the wireless issue? Is there just no incentive to make it right? Why has my daughter's MAC not had ANY wireless issues - as I battle with mine? Any thoughts? In so many other ways linux is SO MUCH "better" then any other os - why toss out the baby (linux os) with the bathwater (wireless issues)? Beuller?

---

### Post by SeijiSensei on 2010-09-25
When you boot, are there older kernels listed that you can choose?  Try one of those and see if your performance is any better.

---

### Post by maclenin on 2010-09-26
SeijiSensei - thanks for the suggestion. I was able load an earlier kernel, however, there was no improvement in wireless performance....

Any other thoughts?

---

### Post by maclenin on 2010-09-27
Still sluggish - any other ideas? The MAC's tireless and consistently POTENT wireless performance (as compared to lucid's) is crushing my linux ego....

---

### Post by maclenin on 2010-09-28
I just updated to the latest kernel in lucid - 2.6.32-25-generic...

...and (as with the previous kernel) experienced this currently typical wireless scenario:

I "enjoy" a few moments of sluggish wireless connectivity, after restart...

The connection then seems to fade (from sluggish to dead) as the browser gets hung up on the "Loading" of a web page.

Skype disconnects.

The little red circular warning symbol appears at the bottom left of my mail watcher icon.

My wireless connection seems lost.

I then run these next few commands to try and suss out the "state" of my wireless connection:

A. nm-tool (1st run)
```
laptop@laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto My target AP] ----------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TALKTALK-CDD7DF: Infra, 00:26:B6:CD:D7:DF, Freq 2422 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    claude:          Infra, 00:24:B2:B6:15:DA, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA
    NETGEAR:         Infra, 00:0F:B5:CE:E2:B4, Freq 2462 MHz, Rate 54 Mb/s, Strength 41 WEP
    My target AP:    Infra, 00:14:A8:25:5D:90, Freq 2437 MHz, Rate 54 Mb/s, Strength 41
    SKY24619:        Infra, 00:26:91:38:60:2C, Freq 2462 MHz, Rate 54 Mb/s, Strength 41 WPA
    pentangle:       Infra, 00:24:B2:B1:25:11, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    *My target AP:   Infra, 00:1A:2F:80:27:30, Freq 2462 MHz, Rate 54 Mb/s, Strength 75
    crawfordcreative:Infra, 1C:AF:F7:47:D0:B6, Freq 2462 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2

  IPv4 Settings:
    Address:         10.0.251.119
    Prefix:          16 (255.255.0.0)
    Gateway:         10.0.0.1

    DNS:             10.0.0.1
```

B. ping (1st run)
```
laptop@laptop:~$ ping -c 4 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
```

C. nm-tool (2nd run)
```
Results identical to nm-tool (1st run) results.
```

D. ping (2nd run - not more than 2 minutes later)
```
laptop@laptop:~$ ping -c 4 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (173.194.37.104) 56(84) bytes of data.
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=1 ttl=56 time=503 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=2 ttl=56 time=300 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=3 ttl=56 time=369 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=4 ttl=56 time=247 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 247.022/355.197/503.809/96.107 ms

laptop@laptop:~$
```

The cycle repeats itself....

Any ideas?

---

### Post by maclenin on 2010-09-29
Might anyone be able to explain how/why I can get these results within seconds of each other?

I run: 1. nm-tool showing I am connected, wirelessly, at full strength - with IP assigned - etc.

Then, I immediately run: 2. ping test (to google) showing unknown host

Then, again, I run: 3. nm-tool showing I am connected at full strength - with IP assigned - etc.

Then, I immediately run: 4. ping test (to google) showing unknown host

I cannot open web pages or use skype or ftp or....

Baffled. Help?

---

### Post by maclenin on 2010-09-29
...and dmesg produces this:

**[35624.072287] wlan0: deauthenticated from 00:1a:2f:80:27:30 (Reason: 2)**
[35625.220580] wlan0: direct probe to AP 00:1a:2f:80:27:30 (try 1)
[35625.223155] wlan0: direct probe responded
[35625.223164] wlan0: authenticate with AP 00:1a:2f:80:27:30 (try 1)
[35625.224557] wlan0: authenticated
[35625.224590] wlan0: associate with AP 00:1a:2f:80:27:30 (try 1)
[35625.226487] wlan0: RX AssocResp from 00:1a:2f:80:27:30 (capab=0x421 status=0 aid=50)
[35625.226494] wlan0: associated

...curiouser and curiouser....

Any ideas?

The Lucid wireless connection comes and goes - my "control" MAC NEVER looses connectivity...hmmm....

...again, I am connecting via proxy...installed Lucid and first used it (and wireless with nothing but joy) in the US. Problems surfaced in the UK (which is where I am now) - might this being playing a role? Doesn't seem to be affecting the MAC - AT ALL - which also hails from the US....

Hmmm?

---

### Post by maclenin on 2010-09-29
Wireless has died again....

Streaming video is a thing of the past - even when "connected"....

"Server is not responding"....

Oi....

Hilfe!

---

### Post by maclenin on 2010-09-30
...rather: "The connection has timed out"
...then: "Server not found"

slow when connected / frequent loss of connection / ?

---

### Post by petersielje on 2010-09-30
I have the same problem in normal ubuntu lucid with rtl8180 and the native driver. Get connected to the wlan, connection seems fine. If I ping google.com constantly I get over 50% packet loss. Sites loading very slowly, often time out.
If I boot to windows everything works fine.

---

### Post by maclenin on 2010-10-01
Doesn't seem we're alone!

Could this merely be a driver (b43) issue?

Any thoughts? I wish I were in a position to test other drivers - would like to be able to just tweak the one I've got - won't have access to a wired connection for at least another month....

I would like to blame the network / router - but the MAC (and it's steely wireless stability) keeps me from slipping down that slippery slope....

Any other clues?

---

### Post by petersielje on 2010-10-01
I do not have a Broadcom-Card, so it seems to me that it has nothing to do with a specific driver but is a genereal problem with the wireless in lucid or at least with a set of cards. If you try searching for 'lucid packet loss' you will find other people having the problem with different cards but I did not find a solution.

card:
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
```Long time I was not sure if the packet loss comes from the wlan or is related to my computer. But when I ping the gateway (100% connection) I get packet loss between 10-20% in lucid. In windows I get zero. So this must be an issue with the kernel I guess. I tried the generic and 386 kernel (2.6.32-24-386) with both the same results. Also installed the backported wireless drivers without any change of the issue.

Tried ndiswrapper too which worked flawlessly in the past but loses the connection all the time now with these error messages:

```
ndiswrapper (iw_set_auth:1602): invalid cmd 12 
Association request to the driver failed
```Could not solve that issue. Too bad that I do not have any option other than using wlan here ;(

---

### Post by SeijiSensei on 2010-10-02
I'm one of those whose wireless connectivity went down the tubes with an upgrade to the Lucid kernel though I have an Ralink rt2500 chipset.  That's why I originally suggested selecting the older version at boot to see if that helped.  

There's apparently been a lot of changes going on in the kernel wireless code so I've moved to Maverick to use the newer kernels.  Might I suggest you download the current daily build of Maverick, burn it to a CD, and boot from that.  See if your wireless performance improves.

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

For Kubuntu:
[http://cdimage.ubuntu.com/kubuntu/daily-live/](http://cdimage.ubuntu.com/kubuntu/daily-live/)

---

### Post by petersielje on 2010-10-02
Thank you for that remark. Will just wait a week for the official release and hope things will be better there.

---

### Post by maclenin on 2010-10-02
If it's just that Lucid is faulty (in the wireless department) - I am surprised there aren't more folks "chiming in" re: lucid wireless issues....

I will test my wireless performance in a few other places - then when I have access to a wired connection will decide how to proceed. More details as a solution presents itself.... 

Thanks, as always, for the comments / suggestions / ideas....

---

### Post by TBABill on 2010-10-04
Coming at this from another angle, could this possibly be a conflict rather than a driver issue? If you assume the driver is good, what other issues could cause similar results? I read and re-read this thread and is it possible you have something like iced tea plugin AND Sun Java plugin enabled? Or do you have IPV6 enabled? That's huge in causing problems with "no server found" on many sites. 
 
I just threw these out because I was trying to think of something non-wireless that could cause the same problem. Something with Firefox or Chromium, or whatever browser you use. Or any other issue that could have had something installed during an update that caused a conflict with already installed items. I had that happen when I upgraded to 10.10 (from 10.04)...had to remove the iced tea plugin (AGAIN!) because it caused Chromium to not even open.
 
I know these are off on a tangent, but I am curious if the problem is not the wireless, but something that makes the wireless performance fail. I have the Broadcom 4312 and it is flawless in both 10.04 and 10.10 so it makes me wonder why another machine with the same chip/driver would not work. However, I do use the STA for mine.

---

### Post by pytheas22 on 2010-10-04
I'd need to see the output of "lspci -nn" to know for sure, but I'm pretty certain the Broadcom STA driver should support your device, and would probably work better than b43, which you are currently using.  This is the solution alluded to in the second post of this thread.

You can download and try the STA driver with no risk by running these commands (the first of which requires an Internet connection; hopefully your current connection will work well enough to grab what you need):

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-sources bcmwl-modaliases # download and install STA driver files
sudo rmmod b43 # deactivate b43
sudo rmmod ssb # deactivate ssb, b43's parent
sudo rmmod wl # remove the STA driver if it's inserted (probably not necessary, but doesn't hurt)
sudo modprobe wl # insert the STA driver so it becomes active

```
At this point, if all has gone as expected, you should have a wireless interface up using the STA driver (whose module is named "wl" on Ubuntu).  Try connecting and see if it works better.

If this doesn't work, you can revert to the b43 driver by typing these commands (you don't need an Internet connection for these to work):
```

sudo rmmod wl # deactivate STA
sudo modprobe b43 # insert b43
```

This works because you can have both b43 and the STA driver "installed" at the same time, but only one of them can be active and controlling your device.  I've labeled the commands above (everything right of the # can be typed into the terminal, as it's a comment and will be ignored); hopefully it's clear what this all does.

---

### Post by jshoor on 2010-10-04
I just thought that I would add that I am having similar issues. The network connects, performance is great for a while, then eventually it degrades and stops.  Sometimes it reconnects itself again after 5 to 20 minutes; otherwise, /etc/init.d/networking restart fixes the problem.

I am running 2.6.32-24-generic. I thought it might be a problem with the rt61pci driver; so I went out and got an atheros card instead; now after a few days I am seeing the same thing with the new card.  

Interestingly, I see others reporting similar issues in the driver support mailing lists. 

Can anyone suggest a rock-solid wireless card/driver on lucid?

If its not the card choice, Im not sure what options I have since I havent heard upgrades or downgrades be very sucessful.
 
-J

---

### Post by pytheas22 on 2010-10-05
> Can anyone suggest a rock-solid wireless card/driver on lucid?

Intel-based wireless cards are probably the most hassle-free (but they're not available as USB dongles, so you have to install them internally, which can be difficult if you have a laptop).  And in general, you're better off going with a device that's been out for a few years: it might not have all the latest features, but driver support will probably be better.

> If its not the card choice, Im not sure what options I have since I havent heard upgrades or downgrades be very sucessful.


Sometimes it can also help to change the wireless channel (choose one with the least interference from other routers in your area) of your router or try a different encryption scheme (e.g., WPA1 instead of WPA2--both are equally secure; they just do things a little bit differently).  Neither of these things is a solution to a driver problem, but they're general tips for improving wireless performance and may be especially handy in a situation where you have a flaky driver.

---

### Post by maclenin on 2010-10-05
Thanks for the comments.

I did revisit the earlier post (and subsequent references) by way of the suggestion to modprobe STA - and confronted the same "poor"formance with STA as I'd experienced with b43.

[Incidentally, when I "tabbed" in the "install bcmwl-kernel-sources" command it gave me "-source" vs. -sources....]

To re-cap briefly:

1. I installed lucid in July 2010 and had flawless wireless performance (with b43) until a kernel upgrade in early September 2010.

2. I had also been using b43 with intrepid (and the same broadcom 4312 wireless card) with great joy for the last 2 yearsish.

3. I have (as of 10 minutes ago) tried BOTH b43 and STA with similarly poor results with kernel 2.6.32-25-generic.

4. Here is my lspci -nn #just in case....
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M64-S [Mobility Radeon X2300] [1002:7188]
02:06.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b9)
02:06.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b9)
02:06.2 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 03)
02:06.3 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 20)
02:06.4 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev ff)
10:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
```
Any other thoughts?

Could the wireless issue be related to non-wireless issues as TBABill suggests?

Again - this post was written - in the majority - via wireless MAC - the lspci results were dropped in quickly through a 20 second window of passable penguin wireless performance....

---

### Post by maclenin on 2010-10-05
Seems lots of folks are suffering similarly....

---

### Post by pytheas22 on 2010-10-05
Don't mean to sound pedantic, but are you positive the STA driver was actually activated?  b43 may still have been claiming the device for some reason.  You can check by running:
```

sudo lshw -C Network
```

One of the lines towards the bottom of the section for your wireless card will mention a driver.  If it says anything about b43 and ssb, then the STA driver is not activated.

I'm just driving this point home because I'd really expect the STA driver to work better.  Actually, my mom's netbook has some kind of Broadcom chip that only barely worked with b43, but which runs flawlessly under the STA driver, on Lucid.  I don't remember if her chip is also a 4312 and can't check because I'm in another country for the time being, but it may well be.

Another idea for you that would possibly work is to compile b43 yourself using a version of the source code that matches what would have existed in earlier versions of Ubuntu, when it apparently worked for you.  Have you tried that at all?  I can point you in the right direction if you don't know how to go about it.

---

### Post by wanderinwoodsman on 2010-10-05
My wireless died this afternoon after working fine this morning. I do not know exactly when it happened because i have not made the complete transition to Ubuntu from Windows 7. But the wireless works fine in Windows 7. I am going to try to check on the settings suggested by the previous user. 

I am sure glad that I am not the only one. However, I am not a geek so following some of these conversation is quite difficult. It reminds me why the average computer user stays enslaved to the 600 lb NW gorilla

---

### Post by maclenin on 2010-10-06
I hope things work out for you "ww" (and if they do, share your howto)...and if they don't, yes, hopefully, you'll find solace in the fact that you're not suffering alone....

pytheas22:

pedantic is fine - that's how one learns.

after I followed your directions, above, and experienced similar "trouble" with STA, I "rmmoded" and "modprobed" to re-activate b43 - with no change in performance.

after I rmmoded and modprobed back to b43, I restarted the laptop - attempted to browse a bit - and then (instead of "lshw") tried an "lsmod" to see which wireless module was active - and found "wl" listed - neither ssb nor b43 were to be found.

after I lsmoded, I checked applications > system > hardware drivers and found, indeed, that apparently while downloading, installing and rmmoding and modprobing, the STA driver had replaced b43 as the default. I re-activated the b43 driver, at that point, via the hardware drivers screen.

after I re-activated the b43 driver, I've re-started multiple times and I've checked lsmod and, indeed, b43 (and ssb) have returned as the default wireless drivers. wl is nowhere to be found (via lsmod).

b43 is the current default (and also indicated as such via "hardware drivers").

wireless performance is still abysmal.

thanks for learning me!

[written via my daughter's macbook]

---

### Post by maclenin on 2010-10-06
...slow to load.
...changing DNS settings / IPv6 settings does nothing.
...I feel like I've tinkered with everything - to no avail.
...in the morning wireless was virtually dead - this evening I am getting more passable performance - but still WAY WAY WAY BELOW PAR.
...I am unable (via ubuntu or mac) to ping the DNS of the proxy / router.
...I am able to ping google's DNS (8.8.8.8 and 8.8.4.4)
...MAC wireless performance has remained ROCK SOLID.

could it have something to do with the proxy through which I am connecting? Perhaps the interface there is causing a bit of mischief? Is there a way to check?

thanks, as always, for the suggestions....

---

### Post by pytheas22 on 2010-10-06
If you also had issues under the STA driver, then I'd say that looking closer at the proxy would definitely be worth it.

I don't have much experience with proxies other than using a SOCKS proxy over ssh in Firefox, but it sounds like your setup is quite different.  However, hopefully there's still some kind of device that your Ubuntu computer can talk to without the proxy involved.

Are your Ubuntu machine, your wireless router and other computers on your network all on the same subnet?  If so, I would think that you would be able to ping them without having to pass through your proxy.  Can you get steady ping responses over wireless?

Also, have you seen anything in dmesg or /var/log/syslog that looks relevant?  If it's a driver or hardware problem, it should probably be mentioned there somewhere.

The more I think about it, it just doesn't make sense for your wireless drivers to have worked fine earlier in Ubuntu 10.04, but now to have stopped.  The drivers you were using in July should be the same ones you have now (and even if they're a little different because of kernel upgrades, you say you tried booting into an older kernel but still had issues there).

---

### Post by maclenin on 2010-10-07
thanks, pytheas22, for sticking with this...perhaps I should post some additional detail:

1. sudo lshw -C network
```
*-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d8000000-d8003fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:50:10:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.251.119 multicast=yes wireless=IEEE 802.11bg
```
**Question:** Is it typical to have the wireless network detail split into two "groups" this way?

2. while snooping through /var/log/syslog - I picked out what I thought might be some relevant bits and **bolded** what I thought might be relevant errors....
```
NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'b43')
NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
NetworkManager: <info>  (wlan0): now managed
NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (wlan0): bringing up device.
anacron[1203]: Anacron 2.3 started on 2010-10-07
anacron[1203]: Normal exit (0 jobs run)
kernel: [   11.808066] b43 ssb0:0: firmware: requesting b43/ucode13.fw
kernel: [   11.813166] b43 ssb0:0: firmware: requesting b43/b0g0initvals13.fw
kernel: [   11.852207] psmouse serio5: ID: 10 00 64
kernel: [   11.952120] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
kernel: [   12.057212] ADDRCONF(NETDEV_UP): wlan0: link is not ready
NetworkManager: <info>  (wlan0): preparing device.
**NetworkManager: <info>  (wlan0): deactivating device (reason: 2).**
**NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed**
NetworkManager: <info>  modem-manager is now available
**NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files**
NetworkManager: <info>  Trying to start the supplicant...
NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
**wpa_supplicant[1238]: Failed to initiate AP scan.**
wpa_supplicant[1238]: WPS-AP-AVAILABLE 
wpa_supplicant[1238]: WPS-AP-AVAILABLE 
NetworkManager: <info>  Activation (wlan0) starting connection 'Auto PROXY'
NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto PROXY' requires no security.  No secrets needed.
NetworkManager: <info>  Config: added 'ssid' value 'PROXY'
NetworkManager: <info>  Config: added 'scan_ssid' value '1'
NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Config: set interface ap_scan to 1
NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
wpa_supplicant[1238]: WPS-AP-AVAILABLE 
wpa_supplicant[1238]: Trying to associate with 00:1a:2f:80:27:30 (SSID='PROXY' freq=2462 MHz)
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
kernel: [   55.376115] wlan0: deauthenticating from 00:14:a8:25:5d:90 by local choice (reason=3)
**wpa_supplicant[1238]: Association request to the driver failed**
kernel: [   55.388488] wlan0: direct probe to AP 00:1a:2f:80:27:30 (try 1)
kernel: [   55.396525] wlan0: direct probe responded
kernel: [   55.396529] wlan0: authenticate with AP 00:1a:2f:80:27:30 (try 1)
wpa_supplicant[1238]: Associated with 00:1a:2f:80:27:30
wpa_supplicant[1238]: CTRL-EVENT-CONNECTED - Connection to 00:1a:2f:80:27:30 completed (auth) [id=0 id_str=]
NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
kernel: [   55.397930] wlan0: authenticated
NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
kernel: [   55.397944] wlan0: associate with AP 00:1a:2f:80:27:30 (try 1)
NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'PROXY'.
kernel: [   55.399925] wlan0: RX AssocResp from 00:1a:2f:80:27:30 (capab=0x421 status=0 aid=104)
kernel: [   55.399927] wlan0: associated
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
kernel: [   55.400841] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
kernel: [   55.400893] cfg80211: Calling CRDA for country: GB
NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
NetworkManager: <info>  dhclient started with pid 1509
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
dhclient: Internet Systems Consortium DHCP Client V3.1.3
dhclient: Copyright 2004-2009 Internet Systems Consortium.
dhclient: All rights reserved.
dhclient: For info, please visit https://www.isc.org/software/dhcp/
dhclient: 
kernel: [   55.405286] cfg80211: Received country IE:
kernel: [   55.405290] cfg80211: Regulatory domain: GB
kernel: [   55.405292] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
kernel: [   55.405295] 	(2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
kernel: [   55.405297] cfg80211: CRDA thinks this should applied:
kernel: [   55.405299] cfg80211: Regulatory domain: GB
kernel: [   55.405301] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
kernel: [   55.405303] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
kernel: [   55.405306] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
kernel: [   55.405308] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
kernel: [   55.405311] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
kernel: [   55.405313] cfg80211: We intersect both of these and get:
kernel: [   55.405315] cfg80211: Regulatory domain: 98
kernel: [   55.405316] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
kernel: [   55.405319] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
kernel: [   55.405324] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
kernel: [   55.405327] cfg80211: Current regulatory domain updated by AP to: GB
kernel: [   55.405329] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
kernel: [   55.405332] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
dhclient: Listening on LPF/wlan0/00:1a:73:50:10:2b
dhclient: Sending on   LPF/wlan0/00:1a:73:50:10:2b
dhclient: Sending on   Socket/fallback
AptDaemon: INFO: Initializing daemon
avahi-daemon[958]: Registering new address record for fe80::21a:73ff:fe50:102b on wlan0.*.
dhclient: DHCPREQUEST of 10.0.251.119 on wlan0 to 255.255.255.255 port 67
dhclient: DHCPACK of 10.0.251.119 from 10.0.0.1
dhclient: bound to 10.0.251.119 -- renewal in 17797 seconds.
NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
NetworkManager: <info>    address 10.0.251.119
NetworkManager: <info>    prefix 16 (255.255.0.0)
NetworkManager: <info>    gateway 10.0.0.1
NetworkManager: <info>    nameserver '10.0.0.1'
NetworkManager: <info>    domain name 'rieo.csa'
NetworkManager: <info>    wins '127.0.0.1'
NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
avahi-daemon[958]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.251.119.
avahi-daemon[958]: New relevant interface wlan0.IPv4 for mDNS.
avahi-daemon[958]: Registering new address record for 10.0.251.119 on wlan0.IPv4.
NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
NetworkManager: <debug> [1286457988.039870] periodic_update(): Roamed from BSSID 00:14:A8:25:5D:90 (PROXY') to 00:1A:2F:80:27:30 (PROXY)
NetworkManager: <info>  Policy set 'Auto PROXY' (wlan0) as default for routing and DNS.
NetworkManager: <info>  Activation (wlan0) successful, device activated.
NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
**ntpdate[1557]: no server suitable for synchronization found**
kernel: [   65.676052] wlan0: no IPv6 routers present
kernel: [  132.799588] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
**kernel: [ 7547.084276] wlan0: deauthenticated from 00:1a:2f:80:27:30 (Reason: 2)**
**wpa_supplicant[1238]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys**
**NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected**
**NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning**
wpa_supplicant[1238]: WPS-AP-AVAILABLE 
wpa_supplicant[1238]: Trying to associate with 00:1a:2f:80:27:30 (SSID='PROXY' freq=2462 MHz)
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
**wpa_supplicant[1238]: Association request to the driver failed**
kernel: [ 7548.240569] wlan0: direct probe to AP 00:1a:2f:80:27:30 (try 1)
kernel: [ 7548.245121] wlan0: direct probe responded
kernel: [ 7548.245129] wlan0: authenticate with AP 00:1a:2f:80:27:30 (try 1)
kernel: [ 7548.246520] wlan0: authenticated
kernel: [ 7548.246551] wlan0: associate with AP 00:1a:2f:80:27:30 (try 1)
wpa_supplicant[1238]: Associated with 00:1a:2f:80:27:30
wpa_supplicant[1238]: CTRL-EVENT-CONNECTED - Connection to 00:1a:2f:80:27:30 completed (reauth) [id=0 id_str=]
kernel: [ 7548.248403] wlan0: RX AssocResp from 00:1a:2f:80:27:30 (capab=0x421 status=0 aid=108)
kernel: [ 7548.248409] wlan0: associated
NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
kernel: [ 7730.406732] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
kernel: [ 7730.406735] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
kernel: [ 7730.406738] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
**kernel: [ 8027.076295] wlan0: deauthenticated from 00:1a:2f:80:27:30 (Reason: 2)**
**wpa_supplicant[1238]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys**
NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
wpa_supplicant[1238]: WPS-AP-AVAILABLE 
wpa_supplicant[1238]: Trying to associate with 00:1a:2f:80:27:30 (SSID='PROXY' freq=2462 MHz)
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
**wpa_supplicant[1238]: Association request to the driver failed**
kernel: [ 8028.244555] wlan0: direct probe to AP 00:1a:2f:80:27:30 (try 1)
```
**NB:** I am staying in a hotel and have to "authenticate" before I am able to connect to PROXY, which is the AP to which I am "Auto" connecting. PROXY' is the name of a separate AP / router(?) in the same network, I believe, but on a different floor - weaker signal - as you can see in an earlier [post]("http://ubuntuforums.org/showpost.php?p=9898916&postcount=10") where I've included the results of an nm-tool scan. 


3. also, here are the contents of my /etc/resolv.conf
```
domain rieo.csa
search rieo.csa
nameserver 10.0.0.1
```

Thanks. Wireless performance is still WAY below what I've come to expect and enjoy over the past couple of years (from Intrepid and summertime Lucid)!

---

### Post by lcl on 2010-10-07
I have a fresh install of 10.04.  My chipset is the oldie RTL8180L, I remember it worked out of the box and I was very very happy.  Then after some upgrades later it stopped working exactly just like what you described.

I went to realtek.tw and downloaded the 64bit driver for Windows (as I have a 64 distribution, I don't know if it matters).  Get ndiswrapper to work.  And I can tell you it works much better.  It gives more accurate connection information than before, before it indicated very good signal like 126/100 which I found absurd (unless I understood it wrong) now it's more like 68/100 and gives very good fast connection--about 4 or close 5 mbps downstream which is good for my cable.  But at times, there are still difficulties getting the card to see the network in the air, but once it sees and gets WAP it it's good and it doesn't drop.  I know it doesn't sound very scientific, but I have a couple of times while troubleshooting, it doesn't take the Windows 64 bit driver.  But it does.  And I checked all through iwlist, iwconfig and it all says it's using the Windows driver via ndiswrapper.  When I tried using the original Linux r8180 driver, I thought just maybe I upgraded the firmware it might help, so I did.  Or just maybe the WPA isn't quite working for the card as I think the original card doesn't support WPA, so I disabled WPA.  But nothing worked until I switched to ndiswrapper, with the wireless router running WPA TKIP.

The wireless experience on 10.04 is very iffy, at least that's my experience.  (ON A separate note, I still couldn't figure out sometimes, again very unscientific as it's not consistent, sometimes, I just can't shutdown or restart from GNOME's menu, I don't know if it's related to what I have with the wifi difficulties because of authentication issues)

---

### Post by pytheas22 on 2010-10-07
From the snippets of your syslog that you posted, it does look more likely to be a driver issue after all.  And while I'm not positive, I don't ever recall seeing lshw output for a single wireless interface split into two parts like that, either.  That could also be caused by something strange with the driver.

Have you made any attempt previously to try lcl's suggestion of using ndiswrapper?  I thought of that earlier myself, but when switching to the STA driver didn't seem to make a difference, I started thinking that your problem had to do with something other than the driver.  But, again, after seeing your last post, I'm no longer so sure about that.

To use ndiswrapper, you will need to blacklist the modules b43, ssb (ssb is a module that b43 depends on) and wl, if you still have the STA driver installed.  If you don't know how to do that, let me know.

---

### Post by maclenin on 2010-10-08
Ok - so, perhaps it's time to brush the dust off [this]("http://ubuntuforums.org/showthread.php?t=340689")?

I last used ndiswrapper in feisty.

I used b43 in intrepid - without issue.

Assuming it's a driver issue - could a re-install of b43 be a possible solution - not simply rmmod and modprobe - but a re-build / re-compile (assuming I am using those words correctly)?

However, given that BOTH b43 AND STA don't seem to be working well, I am worried something more profound is (not) at work here.

I am willing to give ndiswrapper a re-run. Are there any changes you'd recommend I make to the [guide]("http://ubuntuforums.org/showthread.php?t=340689")? Will I need an ethernet connection to proceed? Or can I sneak in what I need via current wireless and then just restart? It looks like I might be able to sneak what I need via current wireless....

Thanks, again, pytheas22.

---

### Post by pytheas22 on 2010-10-08
> Assuming it's a driver issue - could a re-install of b43 be a possible solution - not simply rmmod and modprobe - but a re-build / re-compile (assuming I am using those words correctly)?

That could help, yes, if the issue is just a bug in the b43 driver code that has since been fixed.  To compile b43 from source, you'll need to download the entire Linux wireless stack from [http://linuxwireless.org](http://linuxwireless.org) and build it.  It's not hard, but it can take a while (maybe half an hour) to compile.
> 
I am willing to give ndiswrapper a re-run. Are there any changes you'd recommend I make to the guide? Will I need an ethernet connection to proceed? Or can I sneak in what I need via current wireless and then just restart? It looks like I might be able to sneak what I need via current wireless....

I'd probably try ndiswrapper before recompiling b43, because it seems more likely to work.  You shouldn't need to download much--just the packages ndiswrapper-common and ndiswrapper-utils-1.9, along with the Windows wireless driver that you'll use--so you should hopefully be able to grab them with your existing connection.  (The two ndiswrapper packages are also on the Ubuntu installation CD, so you can grab them from there without using the Internet if you enable your CD as a repository using the Administration>Software Sources tool.)

As for the guide you wrote (very through and straight-forward, by the way!), a lot has changed since 2007, and the steps you'll need to go through should actually be much simpler.  To get ndiswrapper installed and blacklist the b43 driver (which replaced bcm43xx a few releases ago), you can do:
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

After that, you'll need to get the Windows driver files (at least a .inf file and a .sys file) and load them into ndiswrapper with:
```

sudo ndiswrapper -i /path/to/inf/file.inf
```

Or, if you prefer to use a GUI, you can install a tiny tool called ndisgtk in the Software Center that will allow you to point ndiswrapper to the .inf file graphically.

Of course, if the Windows driver is in a format that doesn't make the .inf and .sys files readily available, you'll need to extract them using a program like cabextract or 7-zip, unzip, or by running the installer in wine and copying the files from wherever it unpacks them once it does.

And finally, you'll also obviously need a different Windows driver file than the one you used for your 4306 chip on Feisty.  I assume you won't have too much trouble locating the right driver, but of course let me know if you do.

> 
However, given that BOTH b43 AND STA don't seem to be working well, I am worried something more profound is (not) at work here.

I thought that too until I saw your syslog output, which suggests a problem specific to b43.  But I'm not entirely convinced that there isn't a larger issue (though it's hard to imagine what it could be).  I'd try ndiswrapper and see what happens.

And it wouldn't hurt to boot to an Ubuntu live CD, install the b43 firmware (you can install it without an Internet connection by copying the /lib/firmware files on your hard drive into the file system of the live system, then rmmoding and modprobing b43 and ssb) and see if it works there, just to make sure there's not an actual hardware problem.

---

### Post by maclenin on 2010-10-10
ndiswrapper provides no relief!

**NB:** I installed sp34152.exe [should I be using a later/diff. driver version? I first tried and uninstalled and re-installed sp45525.exe only to be bombarded by multiple "unknown symbol" error messages in dmesg.]

...and another quick (while ndiswrapper was active) snippet from /var/log/syslog: 
```
wpa_supplicant[1100]: Trying to associate with 00:1a:2f:80:27:30 (SSID='PROXY' freq=2462 MHz)
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
kernel: [  138.501660] ndiswrapper (iw_set_auth:1602): invalid cmd 12
wpa_supplicant[1100]: Association request to the driver failed
```

hmmm...

I tried to make ndiswrapper permanent using ndiswrapper -m, however, after re-start ssb still lingers (as verified via lsmod) - the wireless light comes on but the ndiswrapper module doesn't load (as also verified via lsmod) and the wireless device does not associate with the "PROXY".

sudo lshw -C network (also just after restart) reveals that the wireless card is (still) in the grips of "driver=b43-pci-bridge", which I believe is another name for "ssb"?

I then rmmod ssb and modprobe ndiswrapper to give ndiswrapper control. When I modprobe ndiswrapper, this appears:
```
laptop@laptop:~$ sudo modprobe ndiswrapper 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
laptop@laptop:~$
```

ndiswrapper does take control (via modprobe) - but it's no improvement over b43...

...I have yet to try compiling b43 from source and testing the wireless card via LiveCD (or "LiveUSB")?

...hmmm.

---

### Post by pytheas22 on 2010-10-11
Sorry to hear ndiswrapper doesn't seem to help :(

> I installed sp34152.exe [should I be using a later/diff. driver version? I first tried and uninstalled and re-installed sp45525.exe only to be bombarded by multiple "unknown symbol" error messages in dmesg.]

Yes, it looks like ndiswrapper just disagrees with the Windows driver that you loaded into it.  You might have better luck trying to use a different version of the driver (e.g., use the Windows 2000 version instead of the XP one, or use version 1.0 instead of 2.0).  But it could also just not work.  Ndiswrapper tends to be a touchy thing, unfortunately.

> 
I tried to make ndiswrapper permanent using ndiswrapper -m, however, after re-start ssb still lingers (as verified via lsmod) - the wireless light comes on but the ndiswrapper module doesn't load (as also verified via lsmod) and the wireless device does not associate with the "PROXY".

To allow ndiswrapper to control the device permanently, you'd need to blacklist the b43 and ssb module in your /etc/modprobe.d/blacklist.conf file.  I think "ndiswrapper -m" just writes to /etc/modules to tell the system to load the ndiswrapper at boot, but that's not enough, because the kernel will always give priority to b43/ssb over ndiswrapper if all three are loaded at the same time.

If you're able, you might try creating a live CD/USB for Ubuntu 10.10, which was officially released yesterday, and see if things work any better there.  It would be great if that just solved all of these problems, because I'm still a bit puzzled by the whole thing...

---

### Post by maclenin on 2010-10-11
Thanks, again, pytheas22 for sticking with this....

Just to clarify - yes - I did try to install two diff. drivers - one (sp45525) "unknown symboled" me - the other (sp34152) installed, but performance is yuk.

Also, I blacklisted BOTH b43 AND ssb. b43 "stayed on the blacklist". ssb, even though it was blacklisted still loaded at start-up. After a wee bit of sniffing around, I followed [these instructions]("http://ubuntuforums.org/showpost.php?p=4881538&postcount=6"). Now both ndiswrapper and ssb load at start-up (in that order). The issue had been that if ssb started FIRST it prevented ndiswrapper from loading - solely blacklisting ssb (for me) had no effect.... 

I think - short of a complete re-install - I'll take a peek at 10.10 via USB - to see if that gives me any relief. One question - when you mention copying the firmware files, are you are referring to copying the "b43" folder, only - or are there other files I should be copying over, as well?

**"10.10" Edit:** I am in 10.10 right now - having copied the b43 firmware from lucid to meerkat's live environment...same old pain - just in a diff. setting.... No improvement....

Could my lucid b43 firmware be corrupted? (If so, then STA and ndiswrapper should have brought some relief...?)

Could it be the AP?

Don't know how the AP could be at fault - my daughter's MAC continues to SCREAM (wirelessly)....

---

### Post by pytheas22 on 2010-10-11
Sorry to hear Ubuntu 10.10 doesn't work any better...

I doubt it's the firmware, but I have a clean copy of the b43 firmware at [http://burnthesorbonne.com/files/b43_firmware.tar.gz](http://burnthesorbonne.com/files/b43_firmware.tar.gz) in case you want to try that.  Just extract the file and move the b43 directory to /lib/firmware (so that you get a /lib/firmware/b43 directory).  But as you point out, if the firmware were the issue, ndiswrapper and the STA driver should have performed better.

It could be your AP that's disagreeing with Ubuntu, or something related to the AP (like the type of encryption it is using, if any).  Are you able to connect to any other wireless networks (in a café or university or wherever you have access to) just to see if it works there?  It would be great to know the outcome of that test.

Thanks for all of your patience!

---

### Post by maclenin on 2010-10-11
It's you, pytheas22, who should be thanked...for persevering through my troubled times!

I had acutally tried to connect via public wifi (from a parkbench) - to no avail - I was able to manually (using iwlist) locate the signal and attempt to connect but the "handshake" process timed out....

I'll seek out other sources and report back....

Should you have any other ideas - no matter how outrageous - pass them along - I'll give them a whirl....

Thanks, pytheas22....

---

### Post by pytheas22 on 2010-10-12
> I had acutally tried to connect via public wifi (from a parkbench) - to no avail - I was able to manually (using iwlist) locate the signal and attempt to connect but the "handshake" process timed out....

hmmm, there should be no handshake if you're connecting to a public, unsecured network--handshakes only apply to WPA1 and WPA2 connections.  How were you trying to connect?  It is an outrageous suggestion, but you're not somehow trying to use a password where you don't need one, are you?

---

### Post by maclenin on 2010-10-13
Outrageous!

Nope (re: password) - just checked NM to make certain. The config for the saved "Auto Free Public WiFi" shows no wireless security - so, perhaps my use of the word "handshake" was a tad cavalier.... Rephrased: NM found the connection after I ran iwlist and then attempted to connect (two green lights with spinning blue thing appeared) but the attempt to connect failed....

Other Observations:

*At times I can navigate quickly (as it had once and always been....) to the home page of ubuntuforums - but then when I try to navigate to sub-pages within posts - oi - page loading can be interminable (transferring data from....), with frequent time out errors....

*YouTube videos are a thing of the past - L O N G loading...and when (and if) they do come up - it's a choppy mess....

*Google maps will not load - they try - but never fully resolve. Very very slow....

Might there be some other process getting in the way? Can't put my finger on it....

Still looking for an opportunity to try other wifi APs....

I remain (patiently and optimistically) skeptical (that other wifi APs will "resolve" the problem - especially in light of the MAC performance - side-by-side I should see no diff. in mac vs. penguin wifi - if anything, penguin should be better, not worse!)....

---

### Post by maclenin on 2010-10-14
var/log/syslog snippet of latest (unsuccessful) attempt to connect to "Free Public WiFi"...
```
NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Free Public WiFi'
NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Free Public WiFi' requires no security.  No secrets needed.
NetworkManager: <info>  Config: added 'ssid' value 'Free Public WiFi'
NetworkManager: <info>  Config: added 'mode' value '1'
NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Config: set interface ap_scan to 2
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
wpa_supplicant[1114]: Trying to associate with SSID 'Free Public WiFi'
NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
kernel: [   36.081089] ndiswrapper (iw_set_auth:1602): invalid cmd 12
wpa_supplicant[1114]: Association request to the driver failed
wpa_supplicant[1114]: Associated with a2:2d:ed:2d:d2:d4
NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
wpa_supplicant[1114]: CTRL-EVENT-CONNECTED - Connection to a2:2d:ed:2d:d2:d4 completed (auth) [id=0 id_str=]
kernel: [   36.638812] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Free Public WiFi'.
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
NetworkManager: <info>  dhclient started with pid 1522
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
dhclient: Internet Systems Consortium DHCP Client V3.1.3
dhclient: Copyright 2004-2009 Internet Systems Consortium.
dhclient: All rights reserved.
dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
dhclient: 
NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
dhclient: Listening on LPF/wlan0/00:1a:73:50:10:2b
dhclient: Sending on   LPF/wlan0/00:1a:73:50:10:2b
dhclient: Sending on   Socket/fallback
avahi-daemon[927]: Registering new address record for fe80::21a:73ff:fe50:102b on wlan0.*.
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
kernel: [   46.816204] wlan0: no IPv6 routers present
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1522
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
NetworkManager: <info>  Activation (wlan0) failed for access point (Free Public WiFi)
NetworkManager: <info>  Marking connection 'Auto Free Public WiFi' invalid.
NetworkManager: <info>  Activation (wlan0) failed.
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
wpa_supplicant[1114]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Free Public WiFi'
NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Free Public WiFi' requires no security.  No secrets needed.
NetworkManager: <info>  Config: added 'ssid' value 'Free Public WiFi'
NetworkManager: <info>  Config: added 'mode' value '1'
NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Config: set interface ap_scan to 2
wpa_supplicant[1114]: Trying to associate with SSID 'Free Public WiFi'
NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
kernel: [  100.993554] ndiswrapper (iw_set_auth:1602): invalid cmd 12
wpa_supplicant[1114]: Association request to the driver failed
wpa_supplicant[1114]: Associated with e6:48:74:87:6f:1d
wpa_supplicant[1114]: CTRL-EVENT-CONNECTED - Connection to e6:48:74:87:6f:1d completed (reauth) [id=0 id_str=]
NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Free Public WiFi'.
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
NetworkManager: <info>  dhclient started with pid 1560
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
dhclient: Internet Systems Consortium DHCP Client V3.1.3
dhclient: Copyright 2004-2009 Internet Systems Consortium.
dhclient: All rights reserved.
dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
dhclient: 
NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
dhclient: Listening on LPF/wlan0/00:1a:73:50:10:2b
dhclient: Sending on   LPF/wlan0/00:1a:73:50:10:2b
dhclient: Sending on   Socket/fallback
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
CRON[1571]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1560
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
NetworkManager: <info>  Activation (wlan0) failed for access point (Free Public WiFi)
NetworkManager: <info>  Marking connection 'Auto Free Public WiFi' invalid.
NetworkManager: <info>  Activation (wlan0) failed.
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
wpa_supplicant[1114]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```
...will try MAC tomorrow - hmmm....

---

### Post by pytheas22 on 2010-10-14
That output still confuses me...I wish it were a little more verbose about what's wrong, but instead it just has that bit about "Association request to the driver failed."

My latest and greatest idea for what you might try is to install an older kernel and boot to it.  Since you say that the wireless used to work in earlier Ubuntu releases, this seems like it might work.

At [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) there are packages for kernels going back to February 2009, which would have been Ubuntu 8.10.  If your wireless worked back then, you could in principal install the 2.6.24.7 kernel by downloading the linux-image... package and installing it by double-clicking (if your connection isn't good enough to grab the entire file, you could download it on another machine and transfer it over).  You'd then have to reboot, of course, and make sure to select the older kernel at the grub boot menu.  Once in the older kernel, you'd be using an older version of b43 (assuming you have b43 loaded and the competing drivers unloaded), which might get you online and keep you there; who knows.

You could also of course always compile an older Linux kernel of any version from source, but using Ubuntu's prebuilt packages is the easiest way to go.

I can't guarantee that running an older kernel would work, and it could possibly even screw up your computer in the event that the older kernel disagrees with your installed applications, though in theory that shouldn't happen.  Without any better ideas to offer, though, I'd suggest it as something possibly worth a try.

---

### Post by parmruss on 2010-10-14
Having the same problem with rt2500usb (WUSB54g wireless) on any distro running kernels above the 2.28 series; only solution has been to use ndiswrapper, but that's hit and miss. This is definitely a kernel issue, as it crosses distros from Ubuntu to PCLinuxOS.

---

### Post by maclenin on 2010-10-15
**parmruss** - that's squarely where I fall...using ndiswrapper now - with hit or miss "success" - but the performance, overall, is nowhere near where is was - in August, say - and the two years before with intrepid...

...even minor updates / safe-upgrades are taking many minutes where a month or two ago they would take seconds....

**pytheas22** - I hear you re: trying earlier kernels - and I have tried one just a generation or two prior to where I am now (2.6.32-25-generic) - with the same sluggishness.... I understand that it could be a working wireless vs. not-working wireless question, but I'd rather have all systems go(ing) in their latest and greatest iterations. Moreover, as you point out - it might or might not affect software that I am currently running - and that's a pandora's box of fun I'd rather not fling open.... If the DVD player isn't working - why replace it with a VCR?

Shouldn't wireless just work?

My daughter looked at my monitor this morning - saw the "timed out" message and said - "I've never seen that on my computer."

I use my penguin for work - and require a fast connection (which everyone in this day and age should expect) - and though I hate to ask it - is this is not a worrying statement about the state of this product?

Are you not having any wireless issues?

[**N(not so)B:** my connection timed out / disconnected at least 5 times over the course of my drafting this reply!]

---

### Post by pytheas22 on 2010-10-15
**maclenin**: can't blame you for the reluctance to try a different kernel, especially seeing as you already tried one that used to work, to no avail--I'd forgotten about that.  It would be kind of disappointing anyway if the only solution you could find were to use an obsolete version of the operating system.

I'm afraid I can't report any wireless issues on any of my Ubuntu computers (or the Ubuntu computers of other people that I maintain), which all told account for about a half-dozen wireless cards with different kinds of Intel, Ralink and Broadcom chips.  I wish I could, because I'd love a chance to tackle the problem you're having in a more hands-on manner.

After yet some more googling, I found [this thread]("https://bbs.archlinux.org/viewtopic.php?pid=755038"), which just might be relevant to your situation.  It's people back in the early summer reporting connectivity issues similar to yours, and which seem to transcend chipset/driver categories.  If your troubles are being caused by some underlying problem in the wireless infrastructure, rather than the driver itself, the solution in that thread, which is given in post #7, might apply to you.

I am not positive whether creating an /etc/modprobe.d/b43.conf file as the person in that thread did will work on Ubuntu (probably it would, but the way modprobe configuration files work can vary from distribution to distribution and I'm not sure what Ubuntu's current stance is).  However, I'm sure you can pass those seemingly magic options to the b43 module manually by first unloading it and then reloading it with the options as command line arguments, i.e.:
```

sudo rmmod b43
sudo rmmod ssb (we'll take ssb out too just for good measure; I'm not sure whether it's necessary)
sudo modprobe b43 pio=1 qos=0
```

(Keep in mind the note in that thread about the qos= bit being different depending on which processor you have.)

If this did work, you could write a script to reload b43 with those options each time your machine boots.
> 
I use my penguin for work - and require a fast connection (which everyone in this day and age should expect) - and though I hate to ask it - is this is not a worrying statement about the state of this product?

You're not alone in asking: I sometimes wonder such things myself.  After having been a Linux zealot for a few years, my bubble has gradually burst and I now recognize that Ubuntu has an array of shortcomings that annoy me every day (e.g., Nautilus keeps crashing on my netbook when I open a new folder and I don't know why; it always reloads but the two-second pause is obnoxious).

For me, though, Linux is still less annoying than the alternatives.  As an example, I had to install Adobe Reader the other day in my Windows virtual machine and somehow the "installer" from Adobe's site managed to infest Firefox with some kind of bogus Adobe "download manager" extension, which in turn automatically downloaded more bogus crap that I didn't sanction.  Yet I couldn't figure out how to get the download manager to install the one piece of software I actually wanted, and the one I had come to Adobe's website in search of, Adobe Reader.  In the end I finally found a real .exe file for Reader on a third-party site that I would never have trusted if I hadn't been using a virtual machine that I could roll back to a clean state.

I like that in Ubuntu I don't have to deal with nonsense like that, at least for now.  But I guess that's easy for me to say, with a working wireless card.

---

### Post by johnnytm on 2010-10-15
This is just a thought and I can't say it will work for your case, but I know it has worked for a few other people with the same situation. Broadcom has a website for their linux driver, which is the STA driver, on that webiste they have the tarball files and a help.txt file with procedures fro removing any older versions of drivers and lsmod' ing the the new driver after you build and install it. [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) Like I said, I don't know if you have already been down this road, but I thought it may be worth a try, since the b43 and sta have compatability issues that are hard to work out once both have been installed.

---

### Post by maclenin on 2010-10-18
**johnnytm:** I have tasted (I belive) the full spectrum of broadcom-esque drivers - sta / b43 / ndiswrapper - with the same result: feeling as though I'm "running" through the tar pit in a bad dream....

**pytheas22:** I tried the ArchLinux solution (with no improvement) - thanks for doing my homework for me! I still feel the problem / solution lies deeper than the driver....

The one thing I have yet to find is a CLEAN wireless connection to compare to the experience I am having via proxy. Perhaps that will make a diff. Perhaps not. When I have access to an ethernet cable - then I'll (hopefully) be able to test a bit more aggressively....

I am green with envy re: your wireless bliss.

I am still zealous with regard to linux - even in light of its "foibles" - because (until now) ALL "ISSUES" I HAD EVER CONFRONTED had been either addressable (with reasonable effort), or where they involved "missing features" - vis a vis MAC / WIN - any linux substitute was more than ample (I found)....

This latest wireless issue is lingering longer than any other (linux issue).... 

Thanks, again, for sticking with this!

---

### Post by pytheas22 on 2010-10-18
**maclenin**: hmmm, sorry the ArchLinux solution didn't help.  I had high hopes for that because it really seemed similar to your situation!

I think I might have to admit finally that I'm out of ideas.  My only last thought would be that it's a hardware problem (i.e., your wireless card is just borked), but I assume you ruled that out.  It just seems so bizarre that it would stop working suddenly in the middle of an Ubuntu release (I'd expect it instead to break when you upgrade to a new release), and then even going back to an older kernel doesn't a difference.  So strange...

I'd be delighted to hear you've found a solution, so please keep us updated, especially after you've gotten access to ethernet again.

---

### Post by maclenin on 2010-10-24
...[this person's wireless issue]("http://ubuntuforums.org/showthread.php?t=1604056") struck me as being eerily similar to mine...even down to the "two part listing" of the wireless interface(s)....

...still no solution - on both counts, yet....

---

### Post by pytheas22 on 2010-10-25
Sorry to hear you've still had no good luck.

Someone in post number 2 of the thread you linked to mentions that the issue appears solved with kernel 2.6.36-020636-generic, which is for Ubuntu 11.04.  It would be crazy to upgrade to the 11.04 release at this point, since it's only been in development for a couple of weeks and is guaranteed not to be stable.

However, the 2.6.36 kernel itself is stable, according to [http://kernel.org](http://kernel.org), so you could try installing it either from source or from a PPA and see if it might solve the problem.  I suppose at this point it's hard to be optimistic about any of this, but you never know...

---

### Post by maclenin on 2010-10-25
pytheas22 - outrageous is no longer off-limits (though crazy still might be)...so, I would, certainly, entertain the idea of installing 2.6.36 - however, as I've never tackled a kernel install - a few pointers in the right direction (not that you haven't gone beyond already) would be lovely!

Thanks for all of this!

...wireless still sluggish - painful / tragic - given what once was!!!

---

### Post by pytheas22 on 2010-10-25
No problem.  Here's a basic outline of what you'd need to do to get a variant of the 2.6.36 kernel installed on your Ubuntu 10.10 system.

You have two options for installing the kernel.  The first is to use pre-built packages from a PPA, such as those available at [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  The most up-to-date packages there are the ones at [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-10-25-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-10-25-maverick/) , which provide the 2.6.36 kernel in its most recent form.

To install the kernel from that location, you'd need to download the linux-image file for your architecture (either i386 for 32-bit or amd64 for 64-bit).  It would also not hurt to download the linux-headers package (or, more precisely, the two linux-headers packages: there's one that applies to all architectures, and then a second one built for a specific architecture; you'd need both for your headers to be complete).  You don't need the kernel headers for your computer to work, but they're required in case you want to compile something against the kernel at some point.

After downloading the packages you need, just double-click to install them.  You probably need to install the linux-image package before the linux-headers packages.  You may need to run the "update-grub" command as well to make entries in your boot menu for the new kernel, although I think the package scripts will take care of this for you automatically.

The second option is to compile the kernel from source.  As you might expect, this approach is more complicated, but it can also be fun if you want to learn more about what goes on with your computer behind the scenes.  [This guide]("https://help.ubuntu.com/community/Kernel/Compile") is a good one to follow for compiling a kernel on Ubuntu.  There are also instructions on [this page]("http://christozzi.com/commands.php") that may be simpler if you don't care about customizing the source (which you don't need to, since the default configuration should be fine for what you're hoping to do, namely, make your wireless card work).

Also keep in mind that it could take quite a while for your computer actually to build the kernel.  The last time I did it it took about seven hours, but that was on my netbook, which is relatively weak.  The CPU that the compiler eats up while building the binaries can make it difficult to do other tasks at the same time, so plan accordingly.

Whether you install the 2.6.36 kernel using packages or from source, the b43 wireless driver should come built-in with the kernel (if you install from source, make sure the wireless drivers are enabled in the configuration, but this should be the default).  After that, you just need to boot into your new kernel and see if your device finally works.

---

### Post by maclenin on 2010-10-26
Thanks, pytheas22. I am, certainly, and always up for learning. However, I am also still using 10.04. Will the install of 2.6.36 work under lucid, or will I need to upgrade to 10.10 before installing 2.6.36?

Also, why use aptitude vs. apt-get (or apt-get vs. aptitude)?

---

### Post by pytheas22 on 2010-10-26
> Thanks, pytheas22. I am, certainly, and always up for learning. However, I am also still using 10.04. Will the install of 2.6.36 work under lucid, or will I need to upgrade to 10.10 before installing 2.6.36?

Yes, it should work without a problem.  The only thing that would break would be kernel-dependent packages that are not build along with the new kernel.  That would generally mean drivers that you installed from source code that you downloaded from some website, because the source code for that particular driver is not merged into the kernel itself.  Otherwise, none of your applications should care whether you're using a 2.6.35 or 2.6.36 kernel.
> 
Also, why use aptitude vs. apt-get (or apt-get vs. aptitude)? 

Good question.  I've never quite known myself.  I always just use apt-get.  You piqued my curiosity, however, so I googled it and found [this page]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/"), which offers a decent explanation.

---

### Post by maclenin on 2010-10-27
I have found howtoforge to be pretty good - have you had any experience with howtoforge? I am thinking of using [this guide]("http://www.howtoforge.com/kernel_compilation_ubuntu") as additional reference for the kernel compilation. Though written in 2006, it still seems relevant. Do you agree?

I'll report back as soon as I've carved out a pound of time to compile!

---

### Post by pytheas22 on 2010-10-27
Yes, that certainly looks like a good guide.  The section the grub menu on the second page will be a little different for you, because Ubuntu now uses grub2 instead of grub1, which was the only thing around in 2006.  I also don't know if the part about symlinking /bin/sh to /bin/bash actually matters but in any case it probably won't hurt anything to do it.

Good luck and I really hope this will finally do the trick!

---

### Post by maclenin on 2010-10-28
pytheas22 - a couple of questions before I (acquire access to a wired connection and) leap into kernel compilation:

1. Could (firefox) browser conflicts/issues/performance ([as more specifically described here]("http://ubuntuforums.org/showpost.php?p=9923218&postcount=21")) affect other network-based applications such as skype or ftp? Or do the problems I am experiencing/articulating seem more systemic - i.e. kernel / driver / connection related - and not merely a bad app(le) [firefox] causing others [skype / midnight commander - i.e. the connection, generally] to behave badly?

2. Will this "off piste" kernel install take me out of the "normal" update / safe-upgrade loop? I.e. when the next kernel update comes along will I have to be careful not to "downgrade" the kernel? Similarly, when a later version comes, will I be given the option to safe-upgrade to it, if I so choose?

Thanks, again and again, for your advice!

---

### Post by pytheas22 on 2010-10-29
> 1. Could (firefox) browser conflicts/issues/performance (as more specifically described here) affect other network-based applications such as skype or ftp? Or do the problems I am experiencing/articulating seem more systemic - i.e. kernel / driver / connection related - and not merely a bad app(le) [firefox] causing others [skype / midnight commander - i.e. the connection, generally] to behave badly?

It's worth thinking about those possibilities.  I guess I'd never even considered IPv6 issues because they seem like something you would have checked earlier on, but if you didn't, you could try playinng with the IPv6 settings in Firefox (or whatever you're using) to see if it makes a difference.  In Firefox, you would type about:config in the address bar, then search for ipv6.

You'd probably know if you had the iced tea java plugin installed--you'd have to have installed it yourself--so I assume that can be ruled out.

It might not hurt to try wgetting web pages and files to see if they respond quickly that way.  For instance, open a terminal and type:
```

wget google.com
```

and see how long it takes to download the file.  If it's instantaneous, but in Firefox it takes a long time to load google.com, then that would be interesting--especially if wget always does it quickly.  You could also try wgetting a large file to see how fast it downloads it and whether it flakes out in the process.

> 2. Will this "off piste" kernel install take me out of the "normal" update / safe-upgrade loop? I.e. when the next kernel update comes along will I have to be careful not to "downgrade" the kernel? Similarly, when a later version comes, will I be given the option to safe-upgrade to it, if I so choose?

Ubuntu updates would still give you new kernel packages as they're released, but they should leave your custom-compiled kernel in place and untouched.  The only thing you might have to pay attention to is the grub menu, because the most recently installed kernel would probably go the top of it and become the default.  But if turns out that your custom-compiled kernel works, it's easy to make sure that would always be the default choice in grub.  Let's hope that becomes the worst of your problems :)

---

### Post by maclenin on 2010-11-12
Before 1 week becomes 2 weeks, I wanted to reply with a current (and now seemingly fully-verified and tested) status report....

All systems **GO!**

Though I am, certainly, thrilled to be at full tilt (wirelessly, at a new and permanent location - via a non-proxy route), I am still flummoxed by what was not working properly at the temporary, proxy-served location. I was having issues via proxy for some reason and though the "control" apple did have it's (very occasional) pauses - the penguin was always the one struggling most mightily.

Good to be back at full strength (without need to make any changes to the laptop), but a bit blue to not be able to unveil a situational solution for the team (the [SOLVED] banner must wait).

Thanks, everyone - you, too, **pytheas22** - for your patience and guidance!

---

### Post by TBABill on 2010-11-12
After looking through the entire thread I am a bit unsure of one thing. Why are you using the driver you are currently using and why not just update to the STA driver for the Broadcom BCM4312? Since you already had a (sometimes) stable wireless connection, would it have stayed connected long enough to enable the STA driver? Should have just been a matter of system>admin>hardware (I know you already know that) and when the list comes up just select the other one. Your current connection would have been used to download the other driver, then activate it and reboot.
 
I have 4 laptops with the BCM4312 (2 Dell and 2 Acer) and the STA is always more stable and I get no disconnects or low signal levels. Too many complaints about the other driver from what I have seen.
 
I know you are up and running, but thought I would throw this out since it could happen again. The driver change does not require a hardwired connection, just a connection of any kind, to download and install. Normally someone doesn't have a connection so the only way to get there is wired, but in your case you could have done either (if avail). If you ever encounter symptoms similar to what you had previously, perhaps giving this a shot could save some struggle.

---

### Post by pytheas22 on 2010-11-12
> Before 1 week becomes 2 weeks, I wanted to reply with a current (and now seemingly fully-verified and tested) status report....

All systems GO!

Though I am, certainly, thrilled to be at full tilt (wirelessly, at a new and permanent location - via a non-proxy route), I am still flummoxed by what was not working properly at the temporary, proxy-served location. I was having issues via proxy for some reason and though the "control" apple did have it's (very occasional) pauses - the penguin was always the one struggling most mightily.

Good to be back at full strength (without need to make any changes to the laptop), but a bit blue to not be able to unveil a situational solution for the team (the [SOLVED] banner must wait).

Thanks, everyone - you, too, pytheas22 - for your patience and guidance!

That's good news!  But then this would seem to suggest that it was the proxy that was causing the issues after all, and not the driver, right?  Or am I misinterpreting?  That would make a lot more sense to me, although I was under the impression that we had ruled out the proxy being the source of the issue.

Anyway, the important thing is that it finally works.  Thanks for being so patient through all of the things I suggested you do, all in vain.

---

### Post by maclenin on 2010-11-20
**TBABill**: I did give STA a whirl when I was in wireless purgatory - to no avail - but the circumstances / testing grounds were not optimal. I'll give STA another "taste" to compare performance, now that all is working as it should...great to be back - and thanks for your "throw outs".

**pytheas22**: Yes, you are not misinterpreting re: my experience as the proxy, perhaps, being the source of the issue. However, I don't like the fact that the MAC seemed to be sailing (generally) smoothly while I was struggling - and still being uncertain why this was so...problem unsolved....

Learning and testing and giving things a whirl are NEVER in-vain ventures - they are raison d'etre.... So I am obliged to say thanks to YOU, for your patience and for sticking with me through my walk through the shadow'ed valley...merci, pytheas22....

---

