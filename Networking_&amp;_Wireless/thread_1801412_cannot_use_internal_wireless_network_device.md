---
title: "cannot use internal wireless network device"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by Themiband on 2011-07-10
Hi guys

It's been ages since I've been on here I've been messing around with BackTrack. I've come back to Ubuntu but seem to be having  some problems getting my wireless network thingy working. Here are the specs of my system. Any advice on fixing this would be very very apprciated.

02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

On another note I'm trying to run debain I've got no startx on there or anything like that it's feeling very basic atm. I want to keep startx outta there but I can't connect to the Internet and run apt-get install to grab handy things.

I'm hoping whatever I am gonna do to solve this on Ubuntu will let me connect up to my wireless network with the internal network thingy. However if it doesn't I'm guessin I can just connect up physically to the router. Any tips on doing this from the command line?

thanks guys

---

### Post by chili555 on 2011-07-10
There is really nothing you can do to your Ubuntu install to just magically enable the driver. Broadcoms require proprietary firmware that is not included by default. Now we could use a USB key and transfer things and struggle for ten posts, but if you have the ability to walk over to the router and get a wired ethernet connection, then why struggle?

Walk over to the router, steal the ethernet cable from your sibling/spouse/partner and hook it up. Issue these commands:```
sudo dhclient eth0
```That gets us an IP address, hopefully. Now we grab the firmware:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```It will find the firmware, extract it and install it in the right place. If successful, now do:```
sudo ifconfig eth0 down
```We're done with the ethernet; disconnect it and tell your sibling/spouse/partner, "Thanks, you're a peach!" Now, do:```
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
sudo modprobe ssb
sudo iwlist wlan0 scan
```Do you get scan results? If so, your wireless is working.

What kind of encryption do you have on the network? WEP or WPA or what? Are you ready to set up a permanent connection configuration?

---

### Post by Themiband on 2011-07-10
Thanks man, I'm shattered so think I'll attempt this in the morning. I'm definitely going to be using WPA2 (I've been fooling around with wifite.py on Backtrack, its made me stupidly paranoid so I don't think I'll use WEP again tbh). 

 quick question is 

b43-fwcutter firmware-b43-installer
simply the driver (please correct me if thats the wrong term) for my laptop and you can tell from the specs I posted or will that work across the board for Broadcoms (I'm guessin broadcoms are like this funky wireless thing I've got in my pc)

Thanks again anyhow I'll let you know if it works out

---

### Post by chili555 on 2011-07-10
Broadcom is the specific wireless device in your computer:> Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
Some wireless cards require a firmware file in addition to the actual driver. Some do not. Broadcom makes their firmware proprietary; that is, it is available for use by you and me, but not for resale or redistribution. 

On the other hand, Ubuntu is distributed under the GPL: [http://en.wikipedia.org/wiki/Gpl](http://en.wikipedia.org/wiki/Gpl)> The GPL is the first copyleft license for general use, which means that derived works can only be distributed under the same license terms. Under this philosophy, the GPL grants the recipients of a computer program the rights of the free software definition and uses copyleft to ensure the freedoms are preserved, even when the work is changed or added to. The developers of Ubuntu are unwilling to distribute both free and proprietary software. Therefor, we must get the firmware files after installation.

To complicate matters, Broadcom makes a new chipset more often than my granny makes cookies. Just when we think we have a handle on Broadcoms, a new one comes out and we're lost again. There are currently four variants:

#b43, ssb and firmware

#wl, also known as STA driver

#brcm80211

#not supported no way no how.

Part of the challenge I face, as well as the other module monkeys here, is to figure out which is which and suggest the solution that works fastest, easiest and reliably.

---

### Post by Themiband on 2011-07-11
Thanks man worked a treat I owe you.

what exactly am I doing when I type 

sudo rmmod -f b43 sudo rmmod -f ssb sudo modprobe b43 sudo modprobe ssb


 -f (or --force) forces a module unload, and may crash your
    machine.  This requires the Forced Module Removal option
    when the kernel was compiled.

So I'm forcing the modules I've just downloaded to unload? I've not got a clue what a module really is or what I'm doing by un-loading it? and whats the dealio with modprobe?

Thanks again dude, its like getting my arms back being able to connect wirelessly again

---

### Post by chili555 on 2011-07-11
You are removing the module that's already loaded but not working and loading up the modules that will now recognize and use the firmware that just got installed. -f does indeed mean force. In this context it means remove it even if the system thinks its unwise; we know the currently loaded module has no necessary firmware and when we reload, the modules b43 and ssb will wake up and say, "Oh, now you have firmware for me! Now I can get to work on those torrents, mp3s, Youtube, etc." In effect, we asked the mechanic with no tools to leave the garage and come back in with his toolbox.

modprobe loads the module but also check for other required modules and checks configuration files, /etc/modprobe.d for example. It brings every possible tool to the garage and checks everything carefully.

Glad it's working. Please use Thread Tools at the top and Mark Solved.

---

### Post by Themiband on 2011-07-11
ok few more questions sorry dude (I really want to understand what I'm doing I don't like that my PC has turned into a magic box the workings of which I just can't comprehend). I think I kind of misunderstood exactly what I was doing when I was typing sudo apt-get install b43-fwcutter firmware-b43-installerAt the risk of over extending a metaphor I thought this command was saying to go out and get the mechanics & tool boxes and that b43-fwcutter and firmware-b43-installer were simply not on my laptop

but actually the mechanic was always there (b43 & ssb) and the "b43-fwcutter and firmware-b43-installer" command was about grabbing the right tools i.e. updating these modules. 

I feel I'd just like to get my head around this a little better. Initially get-apt install has just seemed like a magic wand, you type and you get whatever you want. I guess however its a bit more complicated than that thou.

Man I am torrenting like crazy, I move house wednesday and have just packed up my PC and all the good media so I'm trying to grab something good to watch with dinner

---

### Post by chili555 on 2011-07-11
> the "b43-fwcutter and firmware-b43-installer" command was about grabbing the right tools i.e. updating these modules.It goes out on the internet and grabs the needed firmware. It's a bit more complex than that, but not much.> Initially get-apt install has just seemed like a magic wand, you type and you get whatever you want.It is, pretty much. It depends on Ubuntu sources called repositories. It figures out what architecture you have, 32- or 64-bit, etc., and what version you have, 11.04 or 10.10 or 8.04 or whatever you need and installs it. If the package depends on other things, it figures that out and installs them, too. Once installed, when updates are released, they are automagically updated, too. Pretty neat.

There is a graphical front-end to apt-get called Synaptic. I urge you to open it up and look around. 

Almost as magical, if you issue a command for which the package is not installed, it tells you how to get it!!! Here's an example:> $ enblend --help
The program 'enblend' is currently not installed.  You can install it by typing:
sudo apt-get install enblendHave fun!

---

