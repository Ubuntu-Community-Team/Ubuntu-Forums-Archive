---
title: "USB Wireless Networking (Westell)"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by D3PyroGS on 2009-07-14
My newly-reformatted computer doesn't have a wireless card but used to connect to the internet in Windows XP through a Westell Wireless USB Adapter. I'm now using Linux Mint (identical to Ubuntu in its networking/wireless).

The USB Adapter isn't being recognized and, although I seem to have the Windows driver package, ndiswrapper didn't seem to work.

Does anyone have any idea how to get this to work? There doesn't really seem to be any information about the device. It just says Westell 802.11g Wireless USB Adapter.

---

### Post by Blonddeeni on 2009-07-14
Gidday.
I'm just passing through looking for help myself on another network issue, and experienced your problem with my usb wireless stick (Hantol). IE: Can see the usb wireless, cannot use it.
I managed to get mine working by running the setup.exe program on the cd that came with it via "wine", (the linux program that runs windows programs under it. Can be installed via the synaptic package manager or in a terminal screen using "sudo apt-get install wine").
Mind you, I have tried so many variations of ndiswrapper > driver installs, coupled with wine > setup.exe that i have the feeling that I needed to use them both. 
Ndiswrapper to load the driver, setup.exe to run the thing.
Then run the network manager to configure the ip address, although I'm finding that clicking on the network icon in the top right of the desktop screen helped a lot too. 

As you may guess, I don't really know what I'm doing, (Mr Noobie here using two machines each running a different version of Ubuntu. 8.04 and 9.04), but hope that this may point you in a useful direction.

Good luck.
Blonddeeni.

---

