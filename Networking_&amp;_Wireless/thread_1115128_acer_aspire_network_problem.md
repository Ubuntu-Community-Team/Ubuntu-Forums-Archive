---
title: "acer aspire network problem"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by ombpro on 2009-04-03
I know this has been posted a lot and people are probably getting tired of seeing this problem, but I could really use some help and any would be appreciated and thank you in advance.

My problem:

I have an acer aspire 4720z laptop with the atheros ar242 wireless card and I can't get it working.  I just did a fresh install of the os and tried simply running a software update with the default atheros wireless support enabled under hardware drivers.  I had seen this on a post and thought I would try it, but after rebooting it didn't work and I installed wifi-radar only for it to tell me (via terminal) that no wifi device is present.

I have previously tried using ndiswrapper, both with the graphical front end and without.  I know that the windows driver is net5211.inf which can be found online and I have it.  Using the graphical front end I previoulsy loaded the driver and the interface would show the hardware was present, which I then verified through the terminal (I forget the command I used).  I then selected the driver and tried using the configure network button and it then told me that no network configuration utility could be found (odd).  So I made sure that I had all the network utilities found in the package manager, and I did.  I also tried blacklisting the linux drivers as well.  I have had no success with any of these methods.

I also tried to use madwifi with no success.

All of this sounds so strange to me because others have had success with the above methods on the same model laptop.

Any help with this would be awesome, thanks!!:)

---

### Post by Cotopaxi on 2009-04-03
give "wicd" a try. It is in your repositories, so if you tipe "wicd" into adept or synaptic, it shows up. wicd will remove any other network manager, but it is the only way I got connected to WLAN's!

One important thing: Once wicd got connected to a network, you will only realize it because the clickable icon changes from "connect" to "disconnect"! Until I found that one out, I was half way mad!;)

---

### Post by ombpro on 2009-04-03
cool, I recall seeing that in a post somewhere but I haven't tried it yet . . .

one question, did you use it with ndiswrapper when you did it or not

I'm going to try without, and if I don't here anything and it doesn't work, I guess I'll try it with ndiswrapper and see what happens . .

also, you said it would remove any other network manager, so does that mean that ethernet will no longer work?


Thanks a bunch!!:)

---

### Post by ombpro on 2009-04-03
ok, so I tried wicd, very cool, I like it better than the regular network manager

except there is a problem, still no wifi

when I installed wicd, I had to remove wifi-radar and network manager, which sounds normal as per your post.

I had already updated the software via update manager so that was not a problem.  I first tried running the linux atheros wireless support available under hardware drivers and could not connect with wicd to any wireless networks.  when I would open the manager applet and click refresh, no networks would come up.

So I tried blacklisting the atheros driver and running ndiswrapper.  except now, with wicd installed the driver which used to be correct comes back as invalid.

arggg, this seems kind of strange to me . . .  but still, thanks for the help

---

### Post by ombpro on 2009-04-03
well, for anyone who is paying attention . . 

I have now tried wicd, wifi radar, ndiswrapper and a number of other methods that I've found posted on the internet to get the wifi up on this acer aspire 4720z laptop.  All of these methods claim to work and do not!!!  The methods are clearly described and the commands are clear and are supposed to work for this exact model and I have found that to not be true.  Thanks anyway, guess I'll just stick with windows

---

