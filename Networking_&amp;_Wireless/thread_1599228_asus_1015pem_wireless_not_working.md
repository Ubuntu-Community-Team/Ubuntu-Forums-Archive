---
title: "asus 1015pem wireless not working"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by kraylus on 2010-10-17
i installed ubuntu on my netbook after having a successful install on my asus g51 laptop.

everything works fine except the wireless. for some reason the netbook wont pick up internet via the ethernet connection so i went and got the drivers via synaptic and copied the packages plus the dependencies required (just needed one - dkms). dkms installed fine, but there was an error when i tried to install bcmwl-kernel-source. ubuntu still sees it as installed tho looking in ubuntu software center.

i rebooted just for shits and giggles, cuz it still didnt work. no dice. then i tried to check in that section that shows drivers that arent allowed in a default install as per another thread. its not in there.

my situation doesnt let me connect this netbook via wire and the only way i can get software for it is to download it via my ubuntu connection on my laptop.

please help. kinda wish i had left windows 7 starter on here so i could at least use this netbook :( shoudna wiped the the whole damn thing!

thanks everyone for your time,

ryan

---

### Post by Dragath on 2010-10-17
I am having the same problems with my new Asus 1015PEM. I recently installed Ubuntu Netbook remix 10.10 and I can't seem to get it to work, I've tried various things, installed various software. I think it has to do with needing a driver for atheros ar8132.

Connects fine with the cable, but cannot see any wireless networks. I'm used to using windows and this is my first time using ubuntu. Any help would be appreciated!

---

### Post by trombino on 2010-10-20
The Broadcom STA Wireless Driver, Additional Drivers (jockey package) works properly.
The only limitation is that you cannot put wifi on monitor mode.

Broadcom STA Wireless: These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

---

### Post by paulscode on 2010-11-06
How do you get Broadcom STA Wireless Driver to appear in the Additional Drivers section?

I have the same notebook, and running Ubuntu 10.10 64-bit.  I can't get wireless to work on it (tried both g and n networks).  I can see the networks and enter the password, but it never connects.  Everywhere I read says the same thing, so I assume I need to use that proprietary Broadcom driver, but it doesn't show up..  Anyone else able to figure this out?

---

### Post by maedelo on 2010-11-06
I'm in the same boat as you Paulscode...

I've tried installing the driver from both the repository and through Terminal without any luck. You said you were able to see the networks? I didn't get that far...

This post is opposite of help to you, but I'm hoping we can signal to others that a conclusive solution is desperately needed!

---

### Post by paulscode on 2010-11-07
Sorry to double-post, but I want to make sure anyone who arrives at this post as I did for the same problem is able to see the solution that worked for me.

Turns out my particular 1015PEM has a Ralink  RT3090 wireless card, not a Broadcom as most others seem to (so it is important to note that if you don't see the Broadcom STA Wireless driver in Additional Drivers, perhaps your particular machine has a different wireless card installed).  This is  easy to figure out by running the command "lspci" from the terminal and  look for the "wireless ethernet" entry.

I found a repository that has  both 32 bit and 64 bit drivers for the RT3090.  It doesn't currently support Ubuntu  10.10, but it works fine for 10.04.  Ralink's website has the source  code for the driver, so theoretically one could compile it themselves  for Maverick rather than acquiring it through Synaptic, but I'm happy to  use Lucid for a while until Maverick is supported by the repository.

For anyone who finds that they have Ralink RT3090 instead of a Broadcom card, the repository is:
**ppa:markus-tisoft/rt3090**

This can be added via:
**System->Administration->Synaptic->Settings->Repositories->Other->Add**

Then Reload Synaptic, search for** rt3090**, mark for installation, apply, and reboot.  Voila, the wireless card works!

---

### Post by burukuru on 2010-12-16
This might be a long shot as as solution but is what happened with me.

Make sure that the wireless adapter is enabled in BIOS and the wifi LED at the front is on!

If you installed the drivers and Ubuntu just doesn't seem to pick up any networks around you then that might be the issue.

---

### Post by bixejo on 2010-12-18
> **paulscode said:**
> [...]
For anyone who finds that they have Ralink RT3090 instead of a Broadcom card, the repository is:
**ppa:markus-tisoft/rt3090**
[...]
Thanks, paulscode, works like a charm! =D>
And no need to reboot, by the way...

Regards, and thank you again,

---

### Post by Arsic on 2011-01-17
> **paulscode said:**
> 
For anyone who finds that they have Ralink RT3090 instead of a Broadcom card, the repository is:
**ppa:markus-tisoft/rt3090**

This can be added via:
**System->Administration->Synaptic->Settings->Repositories->Other->Add**

Then Reload Synaptic, search for** rt3090**, mark for installation, apply, and reboot.  Voila, the wireless card works!
Repository doesn't seem to be working anymore.

---

### Post by elhrac on 2011-01-22
I downloaded the files individually from the launchpad site without ppa, and it worked.

---

### Post by redfox646 on 2011-03-29
I know I'm a couple months late for this thread, but I tried installing the rt3090 driver from that repository, and it still isn't working for me.  Is there anything else I may be forgetting?

---

### Post by Marcos.Rufino on 2011-07-22
paulscode,
I've installed the rt3090 driver following your instructions, but when I open the Additional Drivers app it says the driver is activated but not in use. Do you know how could I put it in use?

Thank you.

---

