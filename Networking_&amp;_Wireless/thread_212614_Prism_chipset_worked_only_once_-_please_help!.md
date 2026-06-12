---
title: "Prism chipset worked only once - please help!"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by timefortea on 2006-07-10
I don't understand what is going on here, so any help would be greatly appreciated:
- I booted Xubuntu 6.06 from the CD, on an IBM T21 laptop with a Netgear MA401 PCMCIA card. It detected the card (installed drivers) but didn't connect to the network (I didn't set up the security).
- I installed the system on the hard disk and rebooted. Now it doesn't detect the card (anyone know why?). I went into Synaptic and installed some extra things - wlan-ng-utils, pcmcia-cs, basically some things Wireless or PCMCIA related that I thought might help.
- I rebooted and now the card is working (light is flashing and I can see in dmesg that it has been found). 
- I couldn't get it to connect to the network but after some playing around I discovered I had to put the keyword 'restricted' in the /etc/network/interfaces file eg.
wireless-key restricted xxxxxxxxxx
- Then I ran /etc/init.d/networking restart - hey presto, I am connected via wireless. I surfed a bit, then I thought I would reboot, to make sure it still works...
- And of course it doesn't. According to iwconfig, everything looks fine. But it's not getting a DHCP response (I tried setting a static IP but it doesn't work either). My wired connection works ok but the wireless just won't connect, no matter what I try. 

So, how come it worked once, but not after a reboot? I haven't got NetworkManager installed. I have tried bringing the interface up and down many times but to no avail. I am pulling my hair out - it worked once, so I know it can work! 

Any clues or ideas I could try out?

---

### Post by timefortea on 2006-07-13
I wanted to post an update to this issue, in case anyone else has the same problem. I noticed that both the hostap_cs and orinoco_cs drivers were being loaded, so I tried blacklisting the first, rebooting and it worked. Then I rebooted again and it didn't work. The same thing happens for either driver - when you blacklisted the other, it worked after reboot, then didn't after the next reboot, and it alternates like that ad-infinitum!

So then I noticed that IrDA is causing a crash in the kernel on startup, see 
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46947](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46947)
Since I don't use IR, I blacklisted all the IR-related modules and restarted. The result? Wireless is now working flawlessly (I'm using orinoco_cs, I haven't bothered trying hostap_cs yet). Strange, but true...

---

### Post by roguetrick on 2006-07-14
I'm working on mine right now.  I tried blacklisting something or another, but now I'm trying to actually get hostap_cs working so I can run Kismet. I wonder if I have to do something special to install the driver.

---

### Post by tturrisi on 2006-07-14
> **roguetrick said:**
> I'm working on mine right now.  I tried blacklisting something or another, but now I'm trying to actually get hostap_cs working so I can run Kismet. I wonder if I have to do something special to install the driver.
what card (model-chipset) do you have that you want to work w/ kismet?

---

### Post by roguetrick on 2006-07-14
Haha right now I'm trying to get it work period, as it decided not to work out of the box. Its a NL-2511 CD Plus EXT2 with the Intersil Prism 2.5 chipset.  Manufacturer seems to reccomend HostAp so thats what I'm trying to figure out.  I just hope I don't screw things up enough to be forced to do a reinstall.

---

### Post by roguetrick on 2006-07-14
Haha, now it says it doesn't even have a driver but its connected and I have some phantom new connection on here.  Man I really don't have an idea what I'm doing but I'm having fun.

---

