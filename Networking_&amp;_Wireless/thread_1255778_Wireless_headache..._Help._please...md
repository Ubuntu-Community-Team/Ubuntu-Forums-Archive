---
title: "Wireless headache... Help. please.."
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by CerealKiller93 on 2009-09-01
Ok, so my thread title is a little ridiculous.

On to my problem...
I figure i should give some hardware information here...

I've got a SONY VAIO PCG-FRV26 (laptop). I bought it off of ebay back in january, got it home, opened the box, turned it on to make sure it worked, and installed Ubuntu 8.1 on it. I upgraded to 9.04 just last night. 
I got everything working fine on it. (perfectly actually, Ubuntu is great).
Since the model number probably doesn't tell you anything, its a Pentium 4 2.8ghz, 512mb/80 gig hd.

I have a Linksys WPC54G Ver. 3 pcmcia wireless card.  I tried ndiswrapper and could not find a windows driver to work with it. I don't have the original cd for the card, as i was just given the card in as-is shape for free. I read all kinds of manuals and stuff and tried many many different drivers and ndiswrapper just kept telling me that it was the wrong driver. I finally gave up and didn't worry with it for a while. 

Yesterday after i upgraded to 9.04 i figured i'd give it another shot. Still unable to find a suitable windows driver, i went to the "Hardware Drivers" utilityd and (as before) it suggested the Broadcom driver, which wouldn't work before. I figured what the hell i'd try it. 

IT WORKED!  SUCCESS!! i thought... all last night i enjoyed wireless for the first time since i installed ubuntu on my laptop. I take my laptop to work with me and use the network there as we don't have wireless at work. I got back home today and tried to use my wireless card and now it won't work again. It acts like its not even there. The card is lighting up normally. 
i went to terminal and ran
```
corey@corey-laptop:~$ sudo lspci
[sudo] password for corey: 
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02)
00:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
**06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**

```So linux is seeing that the card is there and recognizes it, but when i go to network connections it will not even give me an option to connect to my wireless network.
I know the network is working fine because my girlfriend is using it right now on her laptop, and my desktop is also finding it. 

I went back to "Hardware Drivers" and instead of showing the broadcom driver and suggesting, now it gives me this:
[IMG]http://i657.photobucket.com/albums/uu296/dcwillis87/ubuntu%20screenshots/Screenshot-HardwareDrivers.jpg[/IMG]

I've tried rebooting, i've tried all kinds of things. Any help is appreciated. I really hate having to run a cat5 cable across my living room to use my laptop.

---

### Post by CerealKiller93 on 2009-09-02
No replies? really?

---

### Post by CerealKiller93 on 2009-09-02
well, i searched and searched on the forums here and couldn't find anything. I turned to google and found someone having the same issues i was having.

I had browsed thru the ubuntu wireless manual, it told me how to figure out what my problem was but didn't tell me how to fix it.

I finally found someone on google with the same problem. My problem was that ubuntu had disabled my wireless card with out my permission.

```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
```
from:
[http://tenthblog.com/ubuntu/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/](http://tenthblog.com/ubuntu/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/)

I ran those exact commands and Voila! it worked.


so Thanks to everyone for the help..... or lack there of, i should say.

---

### Post by Bucky Ball on 2009-09-02
Hehe, yea, I have threads that go a long time where I am talking to myself but I get there in the end! 

Sometimes folks just don't know the answer and as you are using 9.04, this is even more probable. 

Good job though and hopefully this might help others in the same boat. Just doesn't look like the b43 driver wasn't sticking. Your modprobe-ing seems to have fixed that. :)

---

### Post by CerealKiller93 on 2009-09-04
yeah, but i've found another problem with it. Everytime is shut down the computer and start back up it is disabling my adapter. It makes no sense to me. 

Could it be that Ndiswrapper is conflicting with it? Even though i'm not even using Ndiswrapper for my card? When I got home today i had to go back through and run the same commands. If all else fails I am just going to write a script to execute the commands for me. At least that way all i will have to do is type one command. I guess i could also make a launcher on the desktop to do it for me. 

I really don't want to have to do that though, i would much rather it just work. 

I've been playing around with Linux for a few years now off and on. I've never really had the patience for it on my desktop, but Ubuntu is perfect for my laptop. It does every possible thing i need it to do, and its very reliable. 

I'm absolutely no expert though. I am, however, extremely good with Windows, and computers in general. I can usually figure anything out. I think that is why i like Linux so much because its actually challenging to take full advantage of it. I tried using Fedora first on this system, but it was a total headache. I went with Fedora first because a few years back i ran Redhat, and was pretty familiar with it.

---

### Post by Bucky Ball on 2009-09-04
Now you know how to make it work I would start another thread specifically asking how to make your changes stick persistently.

Sorry I can't help with that one. ;-(

Could you post this file, please:

nano /etc/network/interfaces

... and let us know what you are using; eg. eth0, wlan0 or whatever?

---

