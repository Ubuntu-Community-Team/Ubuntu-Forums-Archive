---
title: "Wireless Problem with Intel 3945ABG and Linksys WPC54G"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by mdawg414 on 2008-12-15
Currently running Ubuntu 8.10 but the problem started during 8.04. I thought the upgrade to Intrepid might fix it but no luck.

I have a Sony Vaio that came with an integrated Intel PRO/Wireless 3945ABG card. That card worked for about 2 years and then pooped out on me. Started acting sporadically and would turn off and on. I was just using the default network utility that runs in the taskbar of Ubuntu. I know it was the card and not the operating system because the same thing was happening on my Windows partition. 

I decided to buy a PCMCIA wireless card which happened to be the Linksys WPC54G. I downloaded the drivers, tossed them into ndiswrapper and it found the hardware no problem. However, the default network utility was saying the card was disabled. It got configured as wlan1 (wlan0 is the old Intel card) and when I click the icon (that has a red x through it since there is no connection) I see both networks but they say "wireless is disabled." 

So then I tried downloading wifi-radar and installing that. For some reason, it must be run as root (via sudo of course) and it runs extremely slow. As in I wait about 5 seconds after every click on the screen before it actually does something. However, after I set it to use wlan1 as the default network, it works....sometimes (I'll explain later). I can see all the networks in range and connect to the one I want. I obtain an IP address and the internet works fine. However, the icon on the status bar still shows an x through it and says both networks are disabled, even though I can browse the internet and have an IP address.

Now back to the "sometimes" part. When I start up my computer, the network doesn't work right away. What I have found that does work is this:

Turn on computer (wireless Power LED blinks but not teh activity LED)
Start Wifi-Radar (15 seconds later, no networks found)
Take out wireless card (a bunch of warnings start showing up on the terminal saying the wlan1 device couldnt be found...this is correct!)
Put wireless card back in (activity LED starts working and networks appear)

So there appear to be a bunch of problems here but they seem to be related so I am guessing fixing one thing may help. Let me know if you need more information like kernel version, lspci output, my astrological sign, etc. Thanks in advance for any advice/ideas!

---

### Post by adriant42 on 2008-12-19
I have Linksys wpc54g v3.1 and was able to connect. Hope this helps

Original document: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
Kernel: Linux-2.6.25 and newer, compat-wireless-2.6 package, current GIT trees
Firmware: 4.150.10.5

----
SUMMARY:
- Download [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
- Download [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

- Open Terminal

tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

export FIRMWARE_INSTALL_DIR="/lib/firmware"
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

- VOILA!!

---

