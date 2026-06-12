---
title: "Black-and-White on S-Video (again)"
date: 2010-06-02
forum: Mythbuntu
---

### Post by dsbw on 2010-06-02
My very first problem with my very first MythTV system was that the video came in in black-and-white over S-Video.

Flash-forward a few years and I've got a (much better) system based on the Abit A-N78HD motherboard (onboard Nvidia 8200) and it's been working fine, except for the occasional tendency to just stop at the Abit logo.

I turned on the auto-myth-upgrade which, I think, was not a great idea, and led me to upgrade to the latest mythbuntu. In for a penny, in for a pound, I figured it was a good time to unplug and untangle and clean out, as well.

So, when I plug everything back in, upgraded and shiny, it's--well, there's an assortment of very minor problmes--but the B&W issue (which I never had on this machine before!) reared its ugly head.

There's only one place for the S-Video cable to go, so I don't think that can be the problem. I tried using alternate devices (dev33 instead of dev1, dev25 instead of dev 0--a long persistent issue with this system is MythTV sometimes calling the PVR-150 dev0 and other times dev1). 

I've read that it could be a PAL/NTSC confusion. Not seeing a setting for that anywhere; I suppose the upgrade could have done that.

Any thoughts?

---

### Post by matt06 on 2010-06-02
I am not familiar with the PVR-150, but it sounds like you are using S-Video input from a STB.  Is the myth interface b&w or only your recordings and have you installed any Nvidia driver packages?

---

### Post by alien878 on 2010-06-02
Sounds like xorg.conf problems.... I don't suppose you have a backup of the working xorg.conf?  Even if you didn't make one, check in /etc/X11 to see if maybe mythbuntu made one during upgrade.

If you are out of luck with a backup, the two possible options that may cause this are:

Option "TVOutFormat" "SVIDEO"

(or COMPOSITE if that is what you are using)

and

Option "TVStandard" "PAL-B"

(assuming you are in Europe.... NTSC-M if you are in NA.  If you are elsewhere, google the option)

Note: Some of this may be a bit out of date.... it has been years since I used TV out on my box.

---

### Post by dsbw on 2010-06-03
> **matt06 said:**
> I am not familiar with the PVR-150, but it sounds like you are using S-Video input from a STB.

Yes.

> **matt06 said:**
> Is the myth interface b&w

No.

> **matt06 said:**
> or only your recordings

Yes.

> **matt06 said:**
> and have you installed any Nvidia driver packages?

Just what came with the 10.04 "upgrade" which may have downgraded what I have?

---

### Post by dsbw on 2010-06-03
> **alien878 said:**
> Sounds like xorg.conf problems.... I don't suppose you have a backup of the working xorg.conf?  Even if you didn't make one, check in /etc/X11 to see if maybe mythbuntu made one during upgrade.

I might have a backup. I'll check.

> **alien878 said:**
> Option "TVOutFormat" "SVIDEO"

(or COMPOSITE if that is what you are using)

and

Option "TVStandard" "PAL-B"

(assuming you are in Europe.... NTSC-M if you are in NA.  If you are elsewhere, google the option)

Note: Some of this may be a bit out of date.... it has been years since I used TV out on my box.

I've never had much luck editing XORG, but I'll give it a try.

---

### Post by matt06 on 2010-06-03
dsbw, make sure both S-Video plugs and jacks have the same number of pins in the right orientation or try a different cable.  I had in issue once where I had to jumper 2 of my pins together to get color when using an SVideo to composite adapter.  And I have a video card that has something that looks like S-Video out, but turned out to be [VIVO]("http://www.allpinouts.org/index.php/9_pin_mini-DIN_%28VIVO%29") and required a special adapter for "true" S-Video.

I would leave xorg.conf and video drivers alone since you do have color on screen.

---

### Post by dsbw on 2010-06-04
Yeah. I don't think my Xorg is this. It's been like this for months:

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Hard for me to believe the cable can be an issue. It was fine a few hours earlier. And there's only one place to plug it in and (as far as I know) one way. 

I'll try, though. I may have a spare S-Video cable, too.

---

### Post by dsbw on 2010-06-05
Matt06,

Well, I'll be damned. S-Video cables CAN go in more than one way. And the wrong way makes the signal B&W. 

Thanks, dude!

---

### Post by matt06 on 2010-06-05
Nice fix, glad you got it worked out.  I just know I've seen all different types of plugs, cables, and adapters all claiming to be SVideo and having different numbers of pins or orientation.  And having struggled with the b&w issue with video cards before, I know the pinouts have to be correct.

---

### Post by grahamz on 2010-07-21
Also make sure tat the pins are not loose or broke off in my case :)

---

