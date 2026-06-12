---
title: "Wireless not so automatic"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by talon_card on 2013-01-28
Hello Everyone,

I picked up from Ebay a Viliv N7. Great device but tricky to get everything working (for an amateur it's tricky)

I've installed Xubuntu 12.04 on the unit (It's only got a 1.33ghz cpu with 1gb of ram) it can't come out of hibernate of standby, but that's no big issue

Everything on the device currently works after battling with it for a day, but Wireless is having problems.

Wireless is always off when the computer is powered on, this can't be changed at the moment because there's no BIOS option to have it on by default.

After using the FN keyboard combination to enable the Wireless Interface I need to run "sudo ifconfig wlan0 up" or else the interface never comes up, once the interface is up the connection seems to be stable.

What I need to know is, where can I insert a line to bring the interface up that has administrative privillages and will be executed when the keyboard combination (FN+F4) is pressed. I'm fairly sure that I'll also need to set some sort of delay before the command is run so that the wireless hardware has time to power on.


Is there a better method to fix this, or am I on the right track?

I'm not too worried about having the most elegant solution, so if  putting the line to bring the Interface up into the keyboard shortcut config would work, I'll give it a shot.

I was also unable to get any useful info from lspci to tell you what the Wifi card is

Thanks in advance anyone and everyone who takes a look at my problem

---

