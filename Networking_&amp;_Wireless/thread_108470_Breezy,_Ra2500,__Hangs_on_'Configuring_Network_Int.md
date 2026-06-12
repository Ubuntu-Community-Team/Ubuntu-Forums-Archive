---
title: "Breezy, Ra2500,  Hangs on 'Configuring Network Interface'"
date: 2005-12-26
forum: Networking &amp; Wireless
---

### Post by Who on 2005-12-26
Hi,
I did a fresh install of Breezy on a 500Mhz P3, with a CNet 802.11G card using a RaLink Ra2500 chipset. This model of card card works on my computer, but does take a long time to get past the 'Congiguring Network Interface' stage. This PC (My brother's) does not get past this stage at all. In recovery mode the final stage I see before it hangs is: "NET: Registered Protocol Family 17", and the step before that it disables IRQ 11...

It doesn't hang _completely_ because it still responds to SysReq commands (but after two hours it still wont finish booting)

Crucially, this install booted fine before I had 'Activated' the card using Gnome Network Manager'. We are using WEP with a hidden SSID. When I put in all the information originally (WEP KEY, SSID) (befire rebooting) I couldn't ping the router, so I think it is likely the setup is wrong - perhaps a mistyped WEP key or something - but I thought a reboot wouldn't cause a problem,so I tried that first - perhaps ann error :P. before rebooting iwconfig showed a correct SSID and a 'connection speed (between 32 and 48Mbps), but zero activity - bytes sent/recieved. which seemed to suggest the device thought itr was connected but nothing else did....!? Would iwconfig show that if the WEP key was wrong? lo was the default netwrok device originally. even after I had activated Ra0 (the wireless card) it wasn't selectable in the network status panel applet - I don't know what that indicates, but it may help...)

The position I am in is this: I don't know whether this _exact_ card is faulty or not, it was a christmas present to my brother. I know an identical card works on my PC,  but I use WPA at my house so I installed the RaConfig 2500 software. 

**I want to 'unconfigure' the network somehow without booting -I.E using a live CD, so I can boot and reconfigure from there - as that seems to me to be the only option. I don't know how to do that though, can someone help? another option would be a bios tweak or two, if anyone knows of any settings that may cause this...?**

Any help would be greatly appreciated

Who (and his borther :P)

---

### Post by ingo on 2005-12-28
I got the same prob with my RA2500 card. Activation means sure death of the system. Similarly, if you activate it on boot, boot will hang.

I'm still very much looking for an answer to this and would be grateful for any hints, etc.

In the meantime you might want to check your /etc/network/interfaces and comment out (put a # in front of the row) any lines pertaining to ra0.

HTH

---

### Post by earth_walker on 2006-02-08
I had trouble getting my wireless to work with a shared WEP key. Unsecured networks and open WEP keys work fine, but it took me ages to figure that out.

I suggest you try to turn off all security on your wireless network first, then try to connect to the unsecured network, and then build up to the security you want once you know it works.

Also, installing "gtkwifi" (search these forums) is very helpful, as it'll actually tell you if the wifi is picking up signals, even if they are not connecting.

Finally, the command 'iwconfig' will tell you whether the card is being detected, whether it is on or not, etc.

---

### Post by rama on 2006-02-09
I had the same problem so I removed the RT2570 driver and tried the linux-wlan-ng driver. I still have some [problems]("http://ubuntuforums.org/showthread.php?p=719195#post719195") but I intend to try all the available drivers/solutions before I stay with linux-wlan-ng.

EDIT: Scratch that ... rt2570 seems to work fine, after I deleted the lines in /etc/network/interfaces like ingo suggested.

---

