---
title: "Wireless cards"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by ercolino on 2011-07-22
Hi Guys!

I'm a newbie in Linux so I apologise in advance if my questions are redundant.
I've got a HP pavilion dv2530ea in which I recently installed ubuntu 11.4.

I also recently bought an external usb wireless antenna to be able to connect to distant wifi connections.

I want to disable the internal wireless card of my laptop, so I just have the usb antenna transmitting. The laptop has a button to disable manually the wireless, but each time I switch it off it also stops my usb wireless antenna.

Any insights on this matter. The output is highly appreciated.

---

### Post by thefasterblueone on 2011-07-22
You could try this:

[http://ubuntuforums.org/showthread.php?t=1609611]("http://ubuntuforums.org/showthread.php?t=1609611")

---

### Post by dagamant on 2011-07-22
first you will need to find out what interface is assigned to the card. you can go into a terminal and run 'ifconfig' and it will show you all the interfaces, wifi adapters are normally wlan# or ath# but you should unplug the usb one before hand so you dont get them mixed up. after you find the adapter you can use 'iwconfig wlan# down' to disable it and 'iwconfig wlan# up' to bring it back if needed. another option is to see if you can disable the internal wifi card in the BIOS of the computer.

---

### Post by ercolino on 2011-07-22
Fellas!
Thanks for the inputs.
@thefasterblueone: after applying the line sudo gedit... I got a weird  error so I couldn't complete the rest of the instructions.
@dagamant: Mate I'm attaching the screenshot for ifconfig, I did exactly  as you instructed me, unplug the usb, run ifconfig wlan# down and it  worked, but once you connect the usb cable there is no way you can make  it appear as running if you don't undo disabling wlan0.

---

### Post by bkratz on 2011-07-22
> **ercolino said:**
> Fellas!
Thanks for the inputs.
@thefasterblueone: after applying the line sudo gedit... I got a weird  error so I couldn't complete the rest of the instructions.
@dagamant: Mate I'm attaching the screenshot for ifconfig, I did exactly  as you instructed me, unplug the usb, run ifconfig wlan# down and it  worked, but once you connect the usb cable there is no way you can make  it appear as running if you don't undo disabling wlan0.


can you tell which one of the two interfaces is the internal one. I suspect that when you disconnected the usb one the internal one may have been renumbered from wlan1 to wlan0 which would then require your undo step. Perhaps you can blacklist the driver for the internal one so that no active modules are available (hopefully it doesn't use the same modules as the usb!).

---

### Post by ercolino on 2011-07-22
Bkratz:

I'm attaching screenshot of ifconfig with usb cable unplugged. This might be the internal wifi card of my laptop.

---

### Post by bkratz on 2011-07-22
> **ercolino said:**
> Bkratz:

I'm attaching screenshot of ifconfig with usb cable unplugged. This might be the internal wifi card of my laptop.



With all cards plugged in can you post the outputs (or at least determine the wireless cards) from the following terminal commands:

```
lshw -C Network
lspci | grep Network
lsusb
lsmod

```

those are L lowerecase, not 1's

---

### Post by ercolino on 2011-07-22
Here it goes

---

### Post by bkratz on 2011-07-22
> **ercolino said:**
> Here it goes



Well your internal wireless is the Intel 3945 and uses the driver module iwl3945. The usb one is the Ralink. I am really not sure if this will work so we will just try to disable the internal temporarily ( it will return next boot) just to see what happens.

sudo modprobe -r iwl3945

Try your wireless usb then. If it works we can blacklist the driver and make it more permanent.

---

### Post by ercolino on 2011-07-22
Mate:

sudo modprobe -r iwl3945 worked wonderfully.

I blacklisted the drivers to prevent you more school teaching for today.

Thank you very much for your help. I never thought ubuntu forums were better than any customer service in the world.

Have a look to the screenshot. I love Ubuntu

---

### Post by bkratz on 2011-07-22
> **ercolino said:**
> Mate:

sudo modprobe -r iwl3945 worked wonderfully.

I blacklisted the drivers to prevent you more school teaching for today.

Thank you very much for your help. I never thought ubuntu forums were better than any customer service in the world.

Have a look to the screenshot. I love Ubuntu



Sure am glad it worked! (Wasn't really sure it would) I have seen others try so you could help them too by going to the thread tools and mark the thread solved.

---

