---
title: "enabling WLAN doesn't work :/"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by Necro-File on 2006-05-07
After a little bit of toying with the ndiswrapper I got Breezy to recognize my onboard wireless lan card (yay!) but, when I go to enable it from the network setup, it just immediatly disables it again. It does this for both my USB adapters as well. Is there any 
way to get around this?

Edit: after fiddling around and checking configs out, I saw that my card was set to use channel 11, while my router was on channel 1, as well as the fact that the ESSID is case sensitive in Linux (which I am constantly forgetting that many things on *NIX systems are CaSe SeNsItIvE). So now the network lists say it is enabled. However, I noticed that I have to "sudo modprobe ndiswrapper" every time I reboot, so now I am just trying to get a script that will do this for me on boot.

---

### Post by K2712 on 2006-05-08
just open your /etc/modules file as root and add 'ndiswrapper' to the end of the file

or

sudo ndiswrapper -m

---

