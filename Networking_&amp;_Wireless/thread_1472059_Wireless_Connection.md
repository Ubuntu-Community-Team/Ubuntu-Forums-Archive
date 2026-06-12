---
title: "Wireless Connection"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by artilluer on 2010-05-04
hey guys, i have a di-524 wireless router and it seems i need to download a .inf file to install into ubuntu and i was wondering if anyone knew where to get this file, i believe that is the only problem im having right now the rest seems to be straight forward, i installed wrong firmware so it didnt work for my router, i also got a quick question, if i install the firmware will the wirless network appear automatically on wireless networks tab in network connections window? 
any help will be greatly appreciated thanks :)

---

### Post by LasloHollyfeld on 2010-05-04
> **artilluer said:**
> hey guys, i have a di-524 wireless router and it seems i need to download a .inf file to install into ubuntu and i was wondering if anyone knew where to get this file, i believe that is the only problem im having right now the rest seems to be straight forward, i installed wrong firmware so it didnt work for my router, i also got a quick question, if i install the firmware will the wirless network appear automatically on wireless networks tab in network connections window? 
any help will be greatly appreciated thanks :)

Hi artilluer, if you think you need a .inf file, it sounds like you've already decided you need to use NDISwrapper to use your wireless networking adapter. NDISwrapper is a way of using a Windows XP driver in Linux to control the wireless networking adapter. If there's a native Linux driver available for your WiFi adapter, that's usually preferable. Do you know for sure that you need to use NDISwrapper? Before you go down that route, what kind of wireless networking adapter is in the computer itself (as opposed to the router)? Do you have a laptop with an internal wireless adapter? Or do you plug a WiFi adapter into your computer through a USB port or a card? And if so, what kind is it? Is it also a D-Link like the wireless router is? The more information you can supply, the better. Depending on what kind of adapter you have, there might be a simpler/better solution to getting it working than using NDISwrapper.

Once we know a little more about the adapter, there are commands you can run that will help identify exactly what kind of wireless adapter you have, and then we'll know if you really need to use NDISwrapper.

If you do need to use NDISwrapper, the .inf file (and the .sys file, you need both) will probably be on the CD that came with the wireless adapter, or you may be able to get them by downloading the driver for it from the manufacturer's website.

To answer your other question, once you have the right driver for your WiFi adapter configured for Ubuntu, you should automatically see a list of available networks in the in the Wireless tab of the Network Connections window. If your network is broadcasting its name, it should be in the list. You may still need to provide security key or passphrase before you can actually use it, though.

---

### Post by artilluer on 2010-05-04
I have a laptop with a built in wireless adapter, i thought i need firmware from the wireless router instead the adapter?

---

### Post by LasloHollyfeld on 2010-05-04
> **artilluer said:**
> I have a laptop with a built in wireless adapter, i thought i need firmware from the wireless router instead the adapter?

Perhaps you can start at the beginning, what problem are you trying to solve? Can your laptop see other wireless networks, but just not the DI-524? Or, can you not see any wireless networks at all?

---

### Post by artilluer on 2010-05-04
I cant see any networks at all

---

### Post by LasloHollyfeld on 2010-05-05
> **artilluer said:**
> I cant see any networks at all

I suspect, then, that you need to get the wireless adapter in the laptop to work. Try running the following commands in a terminal, and post the output back here:
```

iwconfig
rfkill list

```
The first will list all of the network adapters Ubuntu knows about, and whether any of them have "wireless extensions". If a driver has matched your wireless adapter, it should be obvious from that output. The second command will show if any wireless adapters have been "turned off" by switches.

---

### Post by artilluer on 2010-05-05
The output was:

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ubuntu@ubuntu:~$ rfkill list

---

### Post by artilluer on 2010-05-05
nothing came from rfkill list command

---

### Post by artilluer on 2010-05-06
new output on dif laptop im trying to use:

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power= 0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          
ubuntu@ubuntu:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy3: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by artilluer on 2010-05-06
now it says device not ready under wireless connections

---

### Post by LasloHollyfeld on 2010-05-07
The first laptop didn't seem to be loading any driver for the wireless network adapter. If you decide to go back to that one, we'll have to scan the buses and find out what kind of adapter it has. But, since you've gone to the second laptop, we can address that instead. It looks like a driver has definitely loaded for the wireless there, since wlan0 is showing up in the iwconfig output. That's good! Did any networks show up in the network connections window?

Here's a list of commands to run that will provide the info we can use to get it working: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by artilluer on 2010-05-07
actually i got the first one to work today, i found the driver needed and installed it so it all good for seeing the adapter :) but im having same prob on both that neither wanna see any wireless networks, they don't show anything in the wirless networks window

---

