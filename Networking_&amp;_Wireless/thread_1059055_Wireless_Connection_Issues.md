---
title: "Wireless Connection Issues"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by bigjames on 2009-02-03
I read the "how to" on this topic, but I am posting in Windows because I cannot connect using Ubuntu right now so I will include all the information I can about my install and hardware.

Laptop: ACER TravelMate 5720
Wireless: Intel 4965 AG(N)
Network: NETGEAR Wireless Router with WPA turned on. I can connect through Windows.

Ubuntu is installed "within" Windows (Wubi install).

I ran this code: (sudo lshw -C network) when I had Ubuntu booted and it showed that the device was there, but "disabled".  The switch on the front of the laptop was "on" and the "on light" was lit as well on the laptop.

I clicked the help built into Ubuntu and tried to follow the directions, but the directions did not match the menu options.  For example: it told me to go to the Network Manager, but it was no where to be found.  There were a couple of other options with "Network" in the name, but neither had any sort of "search for wireless networks" button.

Any assistance would be appreciated.  Right now I cannot connect to the internet while booted in Ubuntu and I am at a loss as to how to make it work.

Thanks

---

### Post by ioannou.alexandros on 2009-02-03
I have the same card as yours which is built-in into my laptop.

This work just fine for me.

If you try to type iwconfig in the terminal window what comes up?

---

### Post by bigjames on 2009-02-03
Apparently I am an idiot.  I did not see the Network Manager in the top right corner next to the time and date.  This time I was watching the screen when the OS booted up and saw the Network Manager pop up.  All good now.  Thanks!

---

