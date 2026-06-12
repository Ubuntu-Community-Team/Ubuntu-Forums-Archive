---
title: "Problems connecting to WPA2 Wireless network."
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by Cadders on 2011-07-07
Hi Guys,

Hoping someone can shed some light for me..... I've recently re-installed Ubuntu 11.04 and I can't seem to get my wireless connected......... I 'know' it can work with my laptop and hardware as I have previously had it up and running. I had to format the laptop and lend it to a family member who's laptop had died. The wireless is built into the laptop and it appears to be a PrismGT - Intersil3886 card.



I've done plenty of googling and the first thing I've tried is to load the linux nonfree package.. This enabled Network Manager to actually see the card. I can see the Access Point in Network Manager, just can't connect to it.. It continually asks for the WPA/WPA2 password (Which I'm entering correctly)

The output of dmesg continually contains wlan0: direct probe to <MAC ADDRESS> timed out

If anyone can enlighten me then I'd be very grateful - Oh, one more thing, If I install puppy linux from a live cd then it works 'out of the box' suggesting it is an Ubuntu issue

Kind Regards,

Cadders

---

### Post by chili555 on 2011-07-07
> If I install puppy linux from a live cd then it works 'out of the box' suggesting it is an Ubuntu issueIndirectly, in my opinion. I think it is a yet undiscovered interaction between your driver, Network Manager and wpa_supplicant. I don't know which versions of all these that the Pup uses or even if it uses NM. I strongly suspect that if the Pup progresses to the same versions, or regresses, who knows, the same problem will crop up.

However, that doesn't help us here and now. I think the problem is aggravated by WPA and WPA2 mixed networks. Is your router such? Can you please reset it to WPA2 only and give us your report?

---

### Post by Cadders on 2011-07-07
Hi Chili, 

Appreciate your quick response... I've tried setting the router to WPA2 mode only but it's still the same output from dmesg wlan0: direct probe to <MAC ADDRESS> timed out.

It's bizarre because it was working flawlessly until I had to install XP on it for my sister. Perhaps I'll ask her for a new laptop - Heheh

Kind Regards,



Cadders

---

### Post by chili555 on 2011-07-07
You might check this thread, especially post #36 and following. I'm still a little puzzled by what he did. That device uses your same driver p54pci. I think I might wait a bit and see if he reports more about the solution.

[http://ubuntuforums.org/showthread.php?t=1694350&page=4](http://ubuntuforums.org/showthread.php?t=1694350&page=4)

---

### Post by Cadders on 2011-07-07
Chili,

Selected the backports but update manager says everything is up to date.....

Kind Regards,



Cadders

---

### Post by chili555 on 2011-07-07
But did you:> and selected the box "Pre-released updates"DISCLAIMER: Some pre-release updates may be buggy, crash, troublesome, maddening, etc. Some may be fine. Proceed with caution and remove if necessary.

---

### Post by Cadders on 2011-07-07
Yay, Chili - Thankyou!!!

In update manager I selected all four options in the Updates tab...

and behold, tis working..

Many many thanks Chili - Your help is greatly appreciated. Sending you a 'virtual beer'

Kind Regards,



Cadders

---

### Post by chili555 on 2011-07-07
So we can all learn, in Synaptic > File > History, what does it say was updated?

---

### Post by Cadders on 2011-07-07
Errm, nothing apart from the linux-firmware-nonfree earlier on this afternoon....

Thanks again Chili - Hope you enjoy the virtual beer..;-)

Kind Regards



Cadders

---

### Post by chili555 on 2011-07-07
What does this tell us about the four mystery packages that got updated?```
sudo cat /var/log/apt/history.log
```What brand of beer do you suggest? I may have one in Beer Fridge in the garage.

---

### Post by Cadders on 2011-07-07
Chili, I have to go to work, but I'll post the required info first thing tomorrow..... I suggest a refreshing bottle of bud should sort you out!! Treat yourself........ It's on me fella :D



Kind Regards,



Cadders

---

