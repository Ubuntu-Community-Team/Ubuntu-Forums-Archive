---
title: "Xserver 1.10 final in Natty repos"
date: 2011-03-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-03-18
The final version of xserver 1.10 (1.10.0-0ubuntu1) has arrived into natty repositories:
[https://launchpad.net/ubuntu/natty/+source/xorg-server/2:1.10.0-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/xorg-server/2:1.10.0-0ubuntu1)

When upgrading Natty's xserver 1.10rc2 to this final version, be sure to upgrade graphics drivers too.
The minimum you need to upgrade is this:
_For xserver:_
xserver-xorg-core_1.10.0-0ubuntu1
xserver-common-1.10.0-0ubuntu1

_For graphics drivers:_
xserver-xorg-video-intel_2.14.0-4ubuntu3 (for Intel i8xx and i9xx cards)
For Nvidia cards only this is OK for both 32-bit nad 64-bit setups.
- xserver-xorg-video-nouveau_0.0.16+git20110107+b795ca6e-0ubuntu6
For 64-bit setups with nvidia cards the proprietary driver is OK:
- nvidia-current_270.30-0ubuntu2

For ATI cards, no suitable driver yet, the xserver-xorg-video-ati_6.14.0-0ubuntu3 is faulty.

_For failsafe boot:_
xserver-xorg-video-vesa_2.3.0-4ubuntu3


Note 1: fglrx will not work with xserver 1.10 so stick to xserver-xorg-video-ati
Note 2: do not install the superseded package nvidia-current_270.30-0ubuntu1, it has an errraneus video ABI dependency (9 instead of 10).
            Also 32-bit nvidia-current_270.30-0ubuntu2 is faulty, 64-bit is OK.


EDIT: ati, intel and nouveau, nvidia-current and vesa do work fine (all ABI 10).

---

### Post by kansasnoob on 2011-03-18
I think the xorg updates are behind this:

> ubuntu-desktop will be removed
xorg will be removed
xserver-xorg will be removed
xserver-xorg-video-all will be removed
xserver-xorg-video-apm will be removed
xserver-xorg-video-ark will be removed
xserver-xorg-video-ati will be removed
xserver-xorg-video-chips will be removed
xserver-xorg-video-cirrus will be removed
xserver-xorg-video-fbdev will be removed
xserver-xorg-video-geode will be removed
xserver-xorg-video-i128 will be removed
xserver-xorg-video-i740 will be removed
xserver-xorg-video-intel will be removed
xserver-xorg-video-mach64 will be removed
xserver-xorg-video-mga will be removed
xserver-xorg-video-neomagic will be removed
xserver-xorg-video-nouveau will be removed
xserver-xorg-video-nv will be removed
xserver-xorg-video-openchrome will be removed
xserver-xorg-video-r128 will be removed
xserver-xorg-video-radeon will be removed
xserver-xorg-video-rendition will be removed
xserver-xorg-video-s3 will be removed
xserver-xorg-video-s3virge will be removed
xserver-xorg-video-savage will be removed
xserver-xorg-video-siliconmotion will be removed
xserver-xorg-video-sis will be removed
xserver-xorg-video-sisusb will be removed
xserver-xorg-video-tdfx will be removed
xserver-xorg-video-trident will be removed
xserver-xorg-video-tseng will be removed
xserver-xorg-video-v4l will be removed
xserver-xorg-video-vesa will be removed
xserver-xorg-video-vmware will be removed
xserver-xorg-video-voodoo will be removed
exiv2 (version 0.21.1-0ubuntu1) will be upgraded to version 0.21.1-0ubuntu2
gir1.2-atk-1.0 (version 1.33.6-0ubuntu1) will be upgraded to version 1.33.6-0ubuntu2
libatk1.0-0 (version 1.33.6-0ubuntu1) will be upgraded to version 1.33.6-0ubuntu2
libatk1.0-data (version 1.33.6-0ubuntu1) will be upgraded to version 1.33.6-0ubuntu2
libexiv2-10 (version 0.21.1-0ubuntu1) will be upgraded to version 0.21.1-0ubuntu2
libpam-modules (version 1.1.2-2ubuntu3) will be upgraded to version 1.1.2-2ubuntu4
libpam-runtime (version 1.1.2-2ubuntu3) will be upgraded to version 1.1.2-2ubuntu4
libpam0g (version 1.1.2-2ubuntu3) will be upgraded to version 1.1.2-2ubuntu4
xserver-common (version 2:1.9.99.902-2ubuntu2) will be upgraded to version 2:1.10.0-0ubuntu1
xserver-xorg-core (version 2:1.9.99.902-2ubuntu2) will be upgraded to version 2:1.10.0-0ubuntu1
libpam-modules-bin (version 1.1.2-2ubuntu4) will be installed


I'm on the US server so I'm just waiting to see if it doesn't resolve itself. That's why I always check closely before updating ;)

---

### Post by Quackers on 2011-03-18
I just checked and the only available nvidia-current is 270.30-0ubuntu1
So I'll be waiting for further developments then :-)
Thanks for the heads-up Harry33

---

### Post by VinDSL on 2011-03-18
Oh, joy!

I really need to stop doing this, 10 minutes before going to bed.  LoL!  :D

I did the "update"  and it hosed Xorg (see kansasnoob's post above).

Sooooo, I took a stroll down Recovery Lane...

[LIST]
[*]sudo apt-get remove --purge xserver-xorg
[*]sudo apt-get update
[*]sudo apt-get install xserver-xorg
[*]reboot
[/LIST]

... got Natty up n' running, but no Unity.

Aha!  That's right! I need to install nvidia-current_270.30-0ubuntu2 (yes, it was in the repo).

But, wait...

Synaptic says it depends on ABI 9 (uninstallable).

Bwahahahaha!  And, it isn't even April Fool's Day!

Oh, well, I'll worry about it in the morning...

---

### Post by Quackers on 2011-03-18
Oh dear, you'll have to stop going to bed in the middle of the day! :wink:
nvidia-current_270.30-0ubuntu2 not in the repo yet, for me, only nvidia-current_270.30-0ubuntu1, which is no good.
Sleep well :-)

---

### Post by zika on 2011-03-18
> **kansasnoob said:**
> I think the xorg updates are behind this:



I'm on the US server so I'm just waiting to see if it doesn't resolve itself. That's why I always check closely before updating ;)With **aptitude upgrade** no problems, so far, and it trickle slowly, several at a time...
No problems with **apt-get upgrade** either...
(*Déjà vu)*

---

### Post by Harry33 on 2011-03-18
> **Quackers said:**
> Oh dear, you'll have to stop going to bed in the middle of the day! :wink:
nvidia-current_270.30-0ubuntu2 not in the repo yet, for me, only nvidia-current_270.30-0ubuntu1, which is no good.
Sleep well :-)

And now I see that the 32-bit nvidia-current_270.30-0ubuntu2 is faulty.
This depends on the video ABI 9.
Installing it will remove xserver 1.10 final.
Xserver 1.10 final provides the video ABI 10.

Then at least xserver-xorg-video-ati_6.14.0-0ubuntu3 is also faulty.
That depends on video ABI 9 too.

So do not upgrade yet.

```
Nvidia-current_270.30-0ubuntu1:
Depends on:
acpid
dkms
libc6 (>= 2.3.6-6~)
libc6-dev
libgcc1 (>= 1:4.1.1)
libx11-6
libxext6
libxv1
libxvmc1
linux-headers-generic
linux-libc-dev
make
patch
sed (>> 3.0)
x11-common (>= 1:7.0.0)
**xorg-video-abi-9**
xserver-xorg-core (>= 2:1.9.99.902-2ubuntu1~)
zlib1g (>= 1:1.1.4)
```

---

### Post by Quackers on 2011-03-18
Oh no! Going downhill fast!

---

### Post by dino99 on 2011-03-18
yeah, xorg-video-abi-9 is missing, removing nvidia-current (i386) if you try to upgrade.

---

### Post by PelPix on 2011-03-18
Just updated.  I hope nothing knocks me out of my session.  Xorg won't work it it restarts. :popcorn:

---

### Post by Harry33 on 2011-03-18
So I have tested new xserver 1.10 (1.10.0-0ubuntu1) from Natty repos.
It works fine in my intel setup.

This means you can upgrade these (all video ABI 10):
- xserver-xorg-core_1.10.0-0ubuntu1
- xserver-common-1.10.0-0ubuntu1
- xserver-xorg-video-intel_2.14.0-4ubuntu3 (for Intel i8xx and i9xx cards)
- xserver-xorg-video-vesa_2.3.0-4ubuntu3

For 32-bit systems with nvidia cards, only open source drivers work:
- xserver-xorg-video-nouveau_0.0.16+git20110107+b795ca6e-0ubuntu6
In 64-bit setups nvidia-current_270.30-0ubuntu2 works just fine.

Then for ati cards, the open source driver in Natty repos is faulty (for now).
And so is 32-bit nvidia-current_270.30-0ubuntu2 in Natty repos too.
You can of course download those from xorg-edgers.
They depend on video ABI 10 and do work fine.

---

### Post by coffeecat on 2011-03-18
> **Harry33 said:**
> For ATI cards, no suitable driver yet, the xserver-xorg-video-ati_6.14.0-0ubuntu3 is faulty.

Thanks for the warning, Harry33!

Synaptic wants to remove xserver-xorg-video-ati_6.14.0-0ubuntu2, and aptitude safe-upgrade want to upgrade it to 0ubuntu3. I think I'll lay off upgrades for a bit - at least on this machine. As one of only seemingly 4 members of this forum who actually prefers using an ATI card, and with the ATI driver no less, this is a subject close to my heart. :-s

---

### Post by Harry33 on 2011-03-18
> **coffeecat said:**
> Thanks for the warning, Harry33!

Synaptic wants to remove xserver-xorg-video-ati_6.14.0-0ubuntu2, and aptitude safe-upgrade want to upgrade it to 0ubuntu3. I think I'll lay off upgrades for a bit - at least on this machine. As one of only seemingly 4 members of this forum who actually prefers using an ATI card, and with the ATI driver no less, this is a subject close to my heart. :-s

Right, for ATI it is better to wait for a new update.
This one does not work:
- xserver-xorg-video-ati_6.14.0-0ubuntu3

---

### Post by zika on 2011-03-18
XE ppa is OK. New ati and server work with each other OK...

---

### Post by dino99 on 2011-03-18
i386: nvidia-current cant be installed even with XE ppa, nvidia-settings not updated too

---

### Post by Harry33 on 2011-03-18
The fact that some of the new xserver video drivers
(like xserver-xorg-video-ati and 32-bit nvidia-current) are faulty
is due to the fact that they were built too early,
just before xserver-xorg-dev_1.10.0-0ubuntu1_amd64.deb was uploaded into Natty repos.
This lead the build dependency to the earlier xserver-xorg-dev 1.10 rc2 version and the video ABI 9.

We have to wait until those have been rebuild against
xserver-xorg-dev_1.10.0-0ubuntu1.

---

### Post by kansasnoob on 2011-03-18
I'm on Intel so based on this I'm going for it:

> apport (version 1.19-0ubuntu3) will be upgraded to version 1.20-0ubuntu1
apport-gtk (version 1.19-0ubuntu3) will be upgraded to version 1.20-0ubuntu1
binutils (version 2.21.0.20110302-2ubuntu1) will be upgraded to version 2.21.0.20110302-2ubuntu2
console-setup (version 1.57ubuntu11) will be upgraded to version 1.57ubuntu12
exiv2 (version 0.21.1-0ubuntu1) will be upgraded to version 0.21.1-0ubuntu2
gir1.2-atk-1.0 (version 1.33.6-0ubuntu1) will be upgraded to version 1.33.6-0ubuntu2
gtk2-engines-murrine (version 0.98.1.1-0ubuntu2) will be upgraded to version 0.98.1.1-0ubuntu3
keyboard-configuration (version 1.57ubuntu11) will be upgraded to version 1.57ubuntu12
language-pack-en (version 1:11.04+20110314) will be upgraded to version 1:11.04+20110317
language-pack-gnome-en (version 1:11.04+20110314) will be upgraded to version 1:11.04+20110317
libatk1.0-0 (version 1.33.6-0ubuntu1) will be upgraded to version 1.33.6-0ubuntu2
libatk1.0-data (version 1.33.6-0ubuntu1) will be upgraded to version 1.33.6-0ubuntu2
libexiv2-10 (version 0.21.1-0ubuntu1) will be upgraded to version 0.21.1-0ubuntu2
libmusicbrainz4c2a (version 2.1.5-4) will be upgraded to version 2.1.5-4ubuntu1
libpam-modules (version 1.1.2-2ubuntu3) will be upgraded to version 1.1.2-2ubuntu4
libpam-runtime (version 1.1.2-2ubuntu3) will be upgraded to version 1.1.2-2ubuntu4
libpam0g (version 1.1.2-2ubuntu3) will be upgraded to version 1.1.2-2ubuntu4
libportaudio2 (version 19+svn20110302-1) will be upgraded to version 19+svn20110317-1
libqtdee2 (version 0.2.1-0ubuntu1) will be upgraded to version 0.2.1-0ubuntu2~bzr35
libunity-2d-private0 (version 3.6.2-0ubuntu1) will be upgraded to version 3.6.2-0ubuntu3~bzr461
python-apport (version 1.19-0ubuntu3) will be upgraded to version 1.20-0ubuntu1
python-problem-report (version 1.19-0ubuntu3) will be upgraded to version 1.20-0ubuntu1
unity-2d (version 3.6.2-0ubuntu1) will be upgraded to version 3.6.2-0ubuntu3~bzr461
unity-2d-launcher (version 3.6.2-0ubuntu1) will be upgraded to version 3.6.2-0ubuntu3~bzr461
unity-2d-panel (version 3.6.2-0ubuntu1) will be upgraded to version 3.6.2-0ubuntu3~bzr461
unity-2d-places (version 3.6.2-0ubuntu1) will be upgraded to version 3.6.2-0ubuntu3~bzr461
unity-2d-spread (version 3.6.2-0ubuntu1) will be upgraded to version 3.6.2-0ubuntu3~bzr461
xserver-common (version 2:1.9.99.902-2ubuntu2) will be upgraded to version 2:1.10.0-0ubuntu1
xserver-xorg-core (version 2:1.9.99.902-2ubuntu2) will be upgraded to version 2:1.10.0-0ubuntu1
xserver-xorg-video-apm (version 1:1.2.3-0ubuntu4) will be upgraded to version 1:1.2.3-0ubuntu5
xserver-xorg-video-ark (version 1:0.7.3-1ubuntu2) will be upgraded to version 1:0.7.3-1ubuntu3
xserver-xorg-video-ati (version 1:6.14.0-0ubuntu2) will be upgraded to version 1:6.14.0-0ubuntu4
xserver-xorg-video-chips (version 1:1.2.3-2ubuntu4) will be upgraded to version 1:1.2.3-2ubuntu5
xserver-xorg-video-cirrus (version 1:1.3.2-2ubuntu6) will be upgraded to version 1:1.3.2-2ubuntu7
xserver-xorg-video-fbdev (version 1:0.4.2-3ubuntu5) will be upgraded to version 1:0.4.2-3ubuntu6
xserver-xorg-video-geode (version 2.11.12-1build1) will be upgraded to version 2.11.12-1build2
xserver-xorg-video-i128 (version 1:1.3.4-1ubuntu2) will be upgraded to version 1:1.3.4-1ubuntu3
xserver-xorg-video-i740 (version 1:1.3.2-3ubuntu2) will be upgraded to version 1:1.3.2-3ubuntu3
xserver-xorg-video-intel (version 2:2.14.0-4ubuntu2) will be upgraded to version 2:2.14.0-4ubuntu3
xserver-xorg-video-mach64 (version 6.8.2+git20101202.d60087f0-4ubuntu2) will be upgraded to version 6.8.2+git20101202.d60087f0-4ubuntu3
xserver-xorg-video-mga (version 1:1.4.13.dfsg-3) will be upgraded to version 1:1.4.13.dfsg-3build1
xserver-xorg-video-neomagic (version 1:1.2.5-1ubuntu2) will be upgraded to version 1:1.2.5-1ubuntu3
xserver-xorg-video-nouveau (version 1:0.0.16+git20110107+b795ca6e-0ubuntu5) will be upgraded to version 1:0.0.16+git20110107+b795ca6e-0ubuntu6
xserver-xorg-video-nv (version 1:2.1.17-3ubuntu6) will be upgraded to version 1:2.1.17-3ubuntu7
xserver-xorg-video-openchrome (version 1:0.2.904+svn916-1) will be upgraded to version 1:0.2.904+svn916-1build1
xserver-xorg-video-r128 (version 6.8.1-4ubuntu2) will be upgraded to version 6.8.1-4ubuntu3
xserver-xorg-video-radeon (version 1:6.14.0-0ubuntu2) will be upgraded to version 1:6.14.0-0ubuntu4
xserver-xorg-video-rendition (version 1:4.2.4-0ubuntu4) will be upgraded to version 1:4.2.4-0ubuntu5
xserver-xorg-video-s3 (version 1:0.6.3-3ubuntu2) will be upgraded to version 1:0.6.3-3ubuntu3
xserver-xorg-video-s3virge (version 1:1.10.4-3ubuntu2) will be upgraded to version 1:1.10.4-3ubuntu3
xserver-xorg-video-savage (version 1:2.3.2-3ubuntu1) will be upgraded to version 1:2.3.2-3ubuntu2
xserver-xorg-video-siliconmotion (version 1:1.7.4-0ubuntu6) will be upgraded to version 1:1.7.4-0ubuntu7
xserver-xorg-video-sis (version 1:0.10.3-2ubuntu2) will be upgraded to version 1:0.10.3-2ubuntu3
xserver-xorg-video-sisusb (version 1:0.9.4-0ubuntu4) will be upgraded to version 1:0.9.4-0ubuntu5
xserver-xorg-video-tdfx (version 1:1.4.3-3ubuntu2) will be upgraded to version 1:1.4.3-3ubuntu3
xserver-xorg-video-trident (version 1:1.3.4-0ubuntu4) will be upgraded to version 1:1.3.4-0ubuntu5
xserver-xorg-video-tseng (version 1:1.2.4-0ubuntu4) will be upgraded to version 1:1.2.4-0ubuntu5
xserver-xorg-video-v4l (version 1:0.2.0-5build1) will be upgraded to version 1:0.2.0-5build2
xserver-xorg-video-vesa (version 1:2.3.0-4ubuntu2) will be upgraded to version 1:2.3.0-4ubuntu3
xserver-xorg-video-vmware (version 1:11.0.3-1ubuntu2) will be upgraded to version 1:11.0.3-1ubuntu3
xserver-xorg-video-voodoo (version 1:1.2.4-0ubuntu4) will be upgraded to version 1:1.2.4-0ubuntu5
libpam-modules-bin (version 1.1.2-2ubuntu4) will be installed


Wish me luck, I'll let you know how it goes :)

---

### Post by coffeecat on 2011-03-18
> **kansasnoob said:**
> Wish me luck, I'll let you know how it goes :)

Since I'm holding back on my ATI machine, I'll be interested in what might happen with  my Intel one.

After you, sir! :wink: I'll await your next post with bated breath.

---

### Post by Harry33 on 2011-03-18
> **coffeecat said:**
> Since I'm holding back on my ATI machine, I'll be interested in what might happen with  my Intel one.

After you, sir! :wink: I'll await your next post with bated breath.

Both ATI and Intel cards work OK now.
I have tested these drivers:
- xserver-xorg-video-ati_6.14.0-0ubuntu4
- xserver-xorg-video-radeon_6.14.0-0ubuntu4
- xserver-xorg-video-mach_6.8.2+git20101202.d60087f0-4ubuntu3
- xserver-xorg-video-r128_6.8.1-4ubuntu3
- xserver-xorg-video-intel_2.14.0-4ubuntu3
- xserver-xorg-video_nouveau_0.0.16+git20110107+b795ca6e-0ubuntu6

Also these nvidia proprieatary drivers work OK (32-bit and 64-bit):
- 270.30-0ubuntu3

---

### Post by kansasnoob on 2011-03-18
Sweet with Intel 82945G/GZ :guitar:

I rebooted and things are marvelous. For quite a while now I've had a few horizontal lines appear very briefly when GDM comes up - not more than 2 or 3 seconds - and then things are fine. But then after I selected my preferred session (I'm still debating between classic w/o effects and unity-2d) the desktop popped up very fast!

I mean really fast - this was to unity-2d - whereas I'd become used to waiting 5 to 10 seconds for the screen to "populate". Cool!

I'm going to try this with different desktop options :)

---

### Post by webme on 2011-03-18
> **Harry33 said:**
> Both ATI and Intel cards work OK now.
I have tested these drivers:
- xserver-xorg-video-ati_6.14.0-0ubuntu4
- xserver-xorg-video-radeon_6.14.0-0ubuntu4
- xserver-xorg-video-mach_6.8.2+git20101202.d60087f0-4ubuntu3
- xserver-xorg-video-r128_6.8.1-4ubuntu3
- xserver-xorg-video-intel_2.14.0-4ubuntu3
- xserver-xorg-video_nouveau_0.0.16+git20110107+b795ca6e-0ubuntu6

Also these nvidia proprieatary drivers work OK (32-bit and 64-bit):
- 270.30-0ubuntu3
Indeed, NVIDIA 270-3 works great .

---

### Post by coffeecat on 2011-03-18
> **Harry33 said:**
> Both ATI and Intel cards work OK now.

That was quicker than I expected. All updated and working well with a Radeon HD4350 and xserver-xorg-video-ati 1:6.14.0-0ubuntu4.

Excellent work on the part of the dev team.

---

### Post by kansasnoob on 2011-03-18
Well, the regular default desktop session (3d) is no better but no worse. It takes too long for the desktop to "populate" and the responsiveness is notably slower than using 2d, but I think that must be a compiz thing.

But in past versions of Ubuntu I've always right-clicked the desktop and selected "no effects", I mean I'm not running a power-house here! I'm legally blind and I could care less about "effects".

But so far I see no problems with X. I'm happy. I guess I should see where my Lubuntu is at with this.

---

### Post by zika on 2011-03-18
What do You think is the reason I get Unity not to clean screen after any action...? Everything that pops and changes on the screen stays... Windows, notifications, names of icons, everything... No cleaning at all...
ATI...

---

### Post by kansasnoob on 2011-03-18
Oh, many thanks to Harry33 for the heads-up on this :D 

When I saw that initial yucky update string this AM I immediately found your thread, good job.

---

### Post by VinDSL on 2011-03-18
> **webme said:**
> NVIDIA 270-3 works great.
w00t!  That's more like it!

I see the Ubu Elves were busy, while I was asleep.  :D

Awoke, got out of bed, dragged a comb across my head, and installed 270.30-0ubuntu3

This 32-bit nvidia-powered box was looking nice, before the update, but now it's gorgeous!

Plymouth even looked better (no kidding)...  ;)

---

### Post by jahLux on 2011-03-18
> **webme said:**
> Indeed, NVIDIA 270-3 works great .

Thanks to all who contributed to this 'save' - and wow, what speed !!
UBUNTU forever . . . . .

---

### Post by Harry33 on 2011-03-18
> **kansasnoob said:**
> Oh, many thanks to Harry33 for the heads-up on this :D 

When I saw that initial yucky update string this AM I immediately found your thread, good job.

Thank You.

---

### Post by VinDSL on 2011-03-18
> **jahLux said:**
> [...] and wow, what speed !!

UBUNTU forever . . . . .
I was just thinking...

A lot of ppl are irritated by these little bumps in the road, but...

In retrospect, doing the update, hosing Xorg, doing a purge and fresh install, et cetera, was probably the best thing that could have happened. That way, I don't have to worry about any lingering or residual effects from the myriad of daily/hourly updates that I've performed on A3.

I might be assuming too much, but I think this is what drives many ppl crazy, when they're running a dev release -- but, at the same time, a joy for others -- a challenge, to be embraced.

Heh!  Does that make any sense?!?!?

Personally, I l-o-v-e that sinking feeling you get, when you're met with a black screen at boot.  It's like, "Yeah, baby!  Game on!"  It makes the endorphins kick into gear, and the neurotransmitters go into overdrive. 

I just shouldn't do it, 10 minutes before going to bed... that's all!  LoL!

If Ubuntu didn't share their dev releases with us, warts and all, life would be soooo boring!  :D

---

### Post by Quackers on 2011-03-18
> **VinDSL said:**
> 
Personally, I l-o-v-e that sinking feeling you get, when you're met with a black screen at boot.  It's like, "Yeah, baby!  Game on!"  It makes the endorphins kick into gear, and the neurotransmitters go into overdrive. 



VinDSL, If you're not on drugs, you should be! :-)

---

### Post by plun on 2011-03-18
> **VinDSL said:**
> 

Personally, I l-o-v-e that sinking feeling you get, when you're met with a black screen at boot.  It's like, "Yeah, baby!  Game on!"  It makes the endorphins kick into gear, and the neurotransmitters go into overdrive. 

I just shouldn't do it, 10 minutes before going to bed... that's all!  LoL!

If Ubuntu didn't share their dev releases with us, warts and all, life would be soooo boring!  :D

Yeah !!  :D

Just a magic explanation why running a development version....:popcorn:


(up and running without any issues.... 270.30 )

---

### Post by Quackers on 2011-03-18
I'm fully updated now too. All is well with nvidia 8600M GT.

---

