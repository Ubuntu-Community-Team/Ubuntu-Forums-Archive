---
title: "nVidia Driver Advice Needed - Twinview Hell!"
date: 2012-01-29
forum: Multimedia Software
---

### Post by jdholman on 2012-01-29
I am using the Ubuntu 11.10 provided nVidia proprietary drivers in my 64-bit install.  My graphics card is an nVidia Corporation G92 [Quadro FX 3700M].  Unity 3D is on.

Since I upgraded, I struggle like crazy to get an external display - ANY external display to work.  It normally takes me 10 to 12 attempts of applying settings, trying again, restarting X, rebooting, etc. before I get this to work.  Frankly, it’s embarrassing as I need to frequently demo software (running in VMWare) on a client’s projector which can be of any shape or resolution.

Here is my question: nVidia has driver version 290 for 64 bit Linux.  I am on version 280 (or 173 depending on where I look).  Should I load the newer driver manually from nVidia?  It a bit of a risk as if I trash my system I’d be up the creek.  

The problems in getting nVidia to do Twinview is driving me NUTS and I need a more reliable way to use external displays.

Any advice appreciated here.

Thanks,

Jim

---

### Post by wolfen69 on 2012-01-29
Did you upgrade or fresh install? Removing the nvidia driver before upgrading may have helped. Unfortunately, I don't have any more insight to the problem.

---

### Post by jdholman on 2012-01-29
I'm generally terrified about uninstalling nVidia drivers, especially before an upgrade.  I wouldn't mind uninstalling all the nVidia stuff reverting to Unity 2D and then trying the nVidia-provided drivers, but in the past I have had a struggle to get Compiz working again.

If I knew the nVidia provided drivers would "fix" Twinview, I'd risk a bit of hacking.

---

### Post by inobe on 2012-01-29
> It a bit of a risk as if I trash my system I’d be up the creek

in that case, why did you upgrade?

you should always be prepared for anything to go terribly wrong when upgrading.

quite frankly i think it's better doing a full install on every new release, this only requires a backup of personal data.

or simply stay within the boundaries of an Lts distro version where nothing changes but security.

> Here is my question: nVidia has driver version 290 for 64 bit Linux. I am on version 280 (or 173 depending on where I look). Should I load the newer driver manually from nVidia?

it's possible to get the latest driver using this ppa

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

use the filter and grab the ppa for your distro version.

add ppa to your package manager.

then in terminal

```
sudo apt-get update
```

then 

```
sudo apt-get upgrade
```

you should see nvidia and other stuff listed, type **Y** for yes and hit enter, when done restart system.

---

### Post by jdholman on 2012-01-29
Hi Inobe,

Thanks for the reply.  Check the "attitude" next time, or read my opening sentence a bit more closely.  I said that I didn't want to break my system by manually loading the nVidia-provided drivers if there was another way to do it.  I always try to upgrade and since I have good backups, if the upgrade craters I can do a fresh install.  Plus, I upgraded last fall and this is the only thing that gives me problems in 11.10.

Since you have suggested another way to get more current drivers for nVidia, I'll thank you for that advice and give it a try.

Thanks again,

Jim

---

### Post by inobe on 2012-01-29
jim no attitude intended, it was a completely friendly comment with no offense intended.

simply forgot the smiley:)

i stand by the advice, upgrading can be disastrous, i would suggest full installs every six months.

two reasons why.

1) you can actually see some differences in the ui and know what's changed because your desktop settings won't follow to the newer upgrade.

2) if some things go wrong, you could go back for another six months to the previous version and rule out it being a distro problem instead of an upgrade conflict issue, you will know what's going on.

---

### Post by jdholman on 2012-01-30
Agreed. So as I don't want to hijack my own thread, are there any war stories out there regarding these Twinview difficulties and overcoming them by either:

1. A fresh install of 11.10 and use Ubuntu provided nVidia proprietary drivers.
2. Existing install: Removing Ubuntu provided nVidia proprietary drivers and reverting to Nouveau permanently.
3. Existing install: Removing Ubuntu provided nVidia proprietary drivers and changing to nVidia provided proprietary drivers.
4. Existing install: Removing existing Ubuntu provided nVidia proprietary drivers and use alternate or newer Ubuntu provided nVidia proprietary drivers.

Or perhaps something else?

Thanks,

Jim

---

### Post by redbook4574 on 2012-01-31
> **inobe said:**
> jim no attitude intended, it was a completely friendly comment with no offense intended.

simply forgot the smiley:)

i stand by the advice, upgrading can be disastrous, i would suggest full installs every six months.

two reasons why.

1) you can actually see some differences in the ui and know what's changed because your desktop settings won't follow to the newer upgrade.

2) if some things go wrong, you could go back for another six months to the previous version and rule out it being a distro problem instead of an upgrade conflict issue, you will know what's going on.

Very reason why I use a removable drive and try the new version whilst keeping the previous (working) version in reserve.B-) :D

---

### Post by jdholman on 2012-01-31
All good advice.  I'll do a complete reinstall of 11.10 "fresh" on a removable drive and try it without the proprietary drivers and see how if goes.

I have a new laptop (a much lower spec model) with an ATI chipset and it is running Nouveau and has zero problems using Twinview on 2nd displays.

Thanks,

Jim

---

