---
title: "Intel PRO100/VE - Dying when disconnected?"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by br0adband on 2010-05-02
Hi there,

I've been dabbling with Lucid the past few weeks, and while the final release has resolved most of the issues I've encountered using the betas and RC builds, I have one issue that still remains and I hope someone can help. I've done research (at least the best I can do presently) and found nothing of substance in terms of a solution. So here it is:

I have a Toshiba Satellite U205 laptop, Core 2 Duo powered, Intel 945GM chipset. It uses the Intel PRO100/VE network adapter for the standard Ethernet (Lucid sees it as eth0 so pretty standard). Now, it works fine as long as it's enabled and operational, but for some testing I decided to disconnect it to check something using the Intel 3945ABG wireless card instead. The issue I'm about to describe happened during the betas, the RC build, and still remains with the final release.

The first time I did this, I merely used the networking applet in the Taskbar panel to disable wired networking (unchecked). At that point the wired networking was now dead/disconnected, and I switched on the 3945ABC using the laptop's wireless switch. It was picked up after a few moments, and I used the same networking applet to connect to my wireless router, no issues.

However, when I was done with that testing part, I disconnected from the router, then disabled the 3945ABG by switching it off with the physical switch, and then I went back to the networking applet to enable the wired connection which was still plugged in.

And that's where I noticed that it was dead, totally dead, no activity, no power to the NIC at all. No activity lights lit on the jack at all. I unplugged the cable, plugged it back in, still nothing. Pulled up Terminal, tried ifconfig and it lists the eth0 interface but I cannot bring it up with the proper command(s) nor shut it down. It's like it's there but won't respond at all.

Here's the worst part:

Even after a reboot, the NIC is still dead, totally and absolutely. Even rebooting into Windows (I'm using Lucid with Wubi) shows the NIC is dead; Windows can't see it anymore, it doesn't even show up in Device Manager.

I have no idea what the hell is going on but it only happens in Linux/Lucid because I can enable/disable and plug/unplug the NIC as much as I want in Windows - when it's working - and it's never an issue at all.

I have to:

- Shut down
- Disconnect the NIC/network cable
- Disconnect the AC adapter
- Disconnect the laptop battery
- Wait about 2 minutes
- Press the power button for 5 seconds or so to get rid of any residual charge in the circuits
- Plug everything back in and power up again...

before the NIC comes back to life.

Can someone clue me in on just what the hell is going on here? I mean, no I don't disable or disconnect the NIC constantly, this was just in testing, but since I caught it, now I have to find out why this is happening so that my NIC doesn't get toasted on me completely.

Is Linux/Lucid breaking something in the NIC that I should be aware and cautious of?

Any help is greatly appreciated.

Thanks...

---

### Post by br0adband on 2010-05-06
*bump*

Nobody? Nobody? Anybody? Bueller? Bueller? ;)

---

