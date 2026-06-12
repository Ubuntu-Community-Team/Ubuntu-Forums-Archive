---
title: "Choosing a graphics card: price vs performance"
date: 2011-03-11
forum: Multimedia Software
---

### Post by Gaba_p on 2011-03-11
Hi all,

I have an ATI Radeon x1550 (pretty old, I know) graphics card which worked perfectly under Windows 7. I recently read that ATI appears to have dropped support for this card installed on recent Ubuntu distributions (I'm using Ubuntu 10.10 + KDE 4.6.1)
The thing is, when I'm watching something on Youtube or playing a movie through VLC, the image looks jittery (random horizontal lines that break the image, it's pretty subtle but it's there...)
I'm new to Ubuntu (switched from Windows 7 a couple of months ago) and what I'm looking for is one of two:

-either a solution to my drivers problem so I can use this card with full 2D and 3D support (like I used to in Windows) or,

- a recommendation of which graphic card I should switch to (my motherboard has a 'PCI Express x16' slot).

I've searched countless forums and sites but I can't reach a final conclusion: Am I supposed to have good 2D and 3D acceleration with this card (with the right drivers installed)?
If the answer is 'yes' then I would appreciate a how-to guide because I'm pretty lost...

If the answer is 'no', then I'd like to know what I should buy. For what I've read, apparently I should stay away from ATI and Intel and look for Nvidia.
I'm not a gamer so I really don't need an incredible 3D acceleration (although *some* would be nice, just in case) What I really need is for my system to be snappy (I work with my computer) and most of all good support for multimedia apps (I would like to be able to use XBMC smoothly for instance)
I'd like to know which is the cheapest graphics card that I can get that will meet my needs (the ones I just listed above)


Anyway, I'll appreciate your comments/suggestions/answers.

Cheers,
Gabriel

---

### Post by Breambutt on 2011-03-11
Tricky question. Especially since I've never owned an ATI card.

I'm always tempted to recommend people an NVIDIA 7900GT (or another old high-end card) if you can find a cheap used one, it's still relatively powerful and perfectly capable of running even more recent games (just lacking the latest DirectX eye candy crap) and only uses around 20W in regular desktop use.

However, I've understood that the 8-series NVIDIAs are the earliest with HD video hardware decoding - and not even all of those - not to mention the vdpau library wasn't perfect the last time I checked.

Generally speaking NVIDIA seemed to be a little more Linux compatible until recently, but now ATI's hooked up with AMD and to me it seems like all solutions are equally bad at the moment when getting a brand new machine.

Either way, NVIDIA's always worked out of the box for me, everything from age-old to up-to-date cards. So, in case nobody can help with your ATI, consider a few years old mid-high end NVIDIA.

---

### Post by Gaba_p on 2011-03-15
Hi,

thanks for your answer Breambutt. I'll look into some old Nvidia graphics cards then.

Meanwhile I would still like an answer to my initial question:

[COLOR="Red"]**Am I supposed to have good 2D and 3D acceleration with this card (with the right drivers installed)?**[/COLOR]

The card is an ATI Radeon X1550 by the way.

Also, some clarification on the differences between the '**xserver-xorg-video-radeon**', '**fglrx**' and '**ATI Catalyst 9.3**' original drivers from their site ([http://goo.gl/wFXq](http://goo.gl/wFXq)) would be REALLY appreciated.
Which one should I install to get a better performance?

Thanks again,
Gabriel

---

### Post by Yellow Pasque on 2011-03-16
fglrx=Catalyst
ATI Catalyst 9.3 is the last version of Catalyst to support your card. It does not work on modern Ubuntu releases (>= 9.04).

xserver-xorg-video-radeon is the default open-source driver, installed by default.

> Am I supposed to have good 2D and 3D acceleration with this card (with the right drivers installed)?
Good 2D and enough 3D acceleration to run Compiz and some light games. XBMC requires more power and works best with nvidia cards with vdpau.

Nvidia GT220 or GT430 are good cards for video playback.

---

### Post by johntaylor1887 on 2011-03-16
> **Temüjin said:**
> 
Nvidia GT220 or GT430 are good cards for video playback.

I use the GT430, and it's been flawless so far. *And* it was only $85 US.

---

### Post by Gaba_p on 2011-03-16
Thanks for the help everybody, I'm marking this one as solved.

See you around!

---

