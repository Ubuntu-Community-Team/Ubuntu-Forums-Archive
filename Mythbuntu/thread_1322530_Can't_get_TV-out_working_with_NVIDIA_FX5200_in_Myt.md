---
title: "Can't get TV-out working with NVIDIA FX5200 in MythTV"
date: 2009-11-11
forum: Mythbuntu
---

### Post by bglaze1 on 2009-11-11
I have been banging my head against the wall off and on for a couple of months now, I have been trying to get the TV Out function to work on my NVIDIA FX5200 that I have running Mythbuntu but to no avail.  If anyone has experience getting this working, I would love to hear from you.  Maybe you can point me in the right direction.  As I said I am struggling here.  I have the NVIDIA proprietary drivers installed, (I got started using the configuring TV Output wiki page then I moved to the running MythTV dual-headed and got a little over my head.) When I connect the S-Video output to the TV, I get a black screen no matter how many different things I try.  I tried playing around with my xorg.conf file, and the instructions I followed weren't cutting it, I was a little confused and my normal playback on the monitor became all choppy, so I dropped all my changes and reverted back to the original.  So any thoughts, a good how-to, or help you can offer would be greatly appreciated.  Thanks.

---

### Post by SiHa on 2009-11-11
You need something like:```
set "UseDisplayDevice" "TV"
set "TVStandard" "PAL"
set "TVOutFormat" "SVIDEO"
```
In one of the sections of your xorg.conf. I can't remember where, I'm afraid, but if you google it you'll probably find the right place.

Are you using the correct cable? My first Myth setup was with an FX5200, which I bought off ebay without the special cable that comes with it. Assuming your card is the same, you'll find the plug on the card isn't actually an S-Video plug, but a combination connector that can do S-Vid, Composite and Component.

---

### Post by fussler on 2009-11-11
in Mythtv 0.22. At installation it asks if i want TV-OUT with nvidia.
The first time i installed I did select this option but then my monitor did now give output.
As it is harder to configure the whole Mythtv on a normal TV, i choose no.
The Option is quite good but why cant i select this after i have done the installation?!
It would be so much easier than fiddling around with Xorg configs...
Can anyone point me out before i spend hours in Xconfig?

My GFcard: EN8400GS Geforce.
wanting normal tv-output

Thanks for any help.

---

### Post by novellahub on 2009-11-11
When doing the install, leave the TV out option alone (disabled state).  Doing this makes the Nvidia driver automatically select the input type during boot up. 

My Nvidia 5200 card came with a true S-video adapter right on the card and did not need a separate break out box.

---

### Post by fussler on 2009-11-11
Hello.
Yes, I did this, left alone and now i would like to send output to my TV with the svideo out on the Nvidia card.
But i can't see any options or easy way to do this.
It looks like i really do have to write a xorg config which really is a tricky task as i know from the past...
what did you do to get tv-out working?

Thanks for the reply

---

### Post by novellahub on 2009-11-11
I will post my xorg.conf file later today.  Hopefully that will help you out.

---

### Post by fussler on 2009-11-11
That would be fantastic...!
I'm so close to getting this finished after over 2 weeks of working on it...
Ithink that could work i only have to change to PAL-B and the resolution to tv..
Thank you

---

### Post by novellahub on 2009-11-11
Here is the contents of my xorg.conf file:

```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "UseEvents"     "1"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
EndSection


```

---

### Post by bglaze1 on 2009-11-22
So do I need to use the section novellahub posted, or do I need to use the section that SiHa posted, or do I need both?
SiHa, the connector on my video card is an actual S-Video out.  So that isn't an issue.
Also, does it matter at all where in my xorg.conf I add the new section?  
Thanks again for all your help.  I still don't quite understand how this file works?

---

### Post by SiHa on 2009-11-23
I was doing things from memory, but I've just done a quick Google, and I think you need:
```
Section "Screen"
       Identifier     "Default Screen"
       Option     "ConnectedMonitor" "TV"
       Option     "TvOutFormat" "SVIDEO"
       Option     "TVStandard" "PAL"
End Section


```
You should already have a default screen section, so just add the lines in there.

The ConnectedMonitor line should tell it to push the signal out of the S-Video port, and the other two will set the standard.

I definitely needed these three to get the stuff out of the S-Video port, and displayed correctly.

---

### Post by stevecartermo on 2009-11-25
My 5200's .... I am using 3 of them display the BIOS boot messages on the TV when the computer starts up. If the TV does not display them it is probably the cable or the card malfunctioning

---

### Post by bglaze1 on 2009-11-27
SiHa, I tried what you said, and it worked great!! Thanks so much!! I am really excited! I have been trying to get this working for so long.  I guess my trouble was just trying to get it out to another monitor as well.  It only displays out to my TV now. Which is good, is there a simple way to make it work to both my monitor and my TV, so I can surf online, etc., from the monitor while watching a show on the TV?

---

