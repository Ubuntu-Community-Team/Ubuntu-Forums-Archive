---
title: "Jerky Video in every player except VCL"
date: 2009-06-07
forum: Multimedia Software
---

### Post by Saganite on 2009-06-07
This is driving my crazy, I'm about to chuck ubuntu out the window and try windows media center instead as I know that will work right out of the box, so to say.   I've searched here and eveywhere but nobody seems to have a good answer to why ubuntu sucks for playing video (9.04 x64)  There's numerous posts about jerky playback but answers are all over the place.

Yes, I have the nvidia drivers enabled (180)

System is a bit old, but is running a AMD 6000+ proc, 4G of memory and 2 GF 6800GTS in SLI mode and should be plenty powerfull enough to be a media PC.

Mplayer and XBMC playback is jerky.  Mplayer, on a certain HD file is so slow it's literally 2-3 FPS.  XBMC on the same file plays okay but is still too jerky to watch.   Doesn't seem to matter what codec the file is although, oddly enough, mplayer does play some files okay, but XMBC has been pretty constant poor performance no matter what the file it is.

Resoloution makes no difference.  It's as Jerky at 1024X768 as it is at 1900X1200.  Full screen flash is also jerky (Hulu - but setting the flash to low quality seems to help that a lot...hard to tell with flash since it's stuch a hog) But in XBMC when the video is minimized when you're moving around the menus it plays fine in the little window.

However... VCL player works just fine.  Smooth as can be.

I've run top and watched the CPU ultilization and XBMC runs it up to the mid 60s and VCL in the 70s so the CPU is not the bottle neck.   I've tried the VPADU option in XBMC to no effect.

The fact VCL works fine should be a big clue, but being a linux noob I have no idea as to what.  I'm about to be an ex-linux noob if I can't get this thing working properly.   Help!

---

### Post by lidex on 2009-06-07
I had many of the same issues. Tried a lot of things so not sure exactly what fixed it. Try enabling this repository:[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") and installing version 180.53 of "nvidia-180-libvdpau", "nvidia-180-kernel-source", nvidia-180-modaliases, and "nvidia-glx-180". Before doing that though go to "System > Administration > Hardware Drivers" and disable version active there and reboot. Just in case go ahead and upgrade "xserver-xorg-video-nv" to "xup" version as well.

If not sure how to add repositories, now is a good time to learn. Page referenced above has links to help with that. Let us know results.

---

### Post by Saganite on 2009-06-07
Thanks!   I'll give that a try.  I know how to add the repositories, had to figure that out when installing XBMC, but I'm not sue how to go about that last bit "upgrade "xserver-xorg-video-nv" to "xup" "

---

### Post by Saganite on 2009-06-07
Well, so far no love.   180.53 is running but no change.   Still do not know what you mean by updating to xup..are you talking about kermel mode setting??

---

### Post by Saganite on 2009-06-07
*facepalm* Now I've done it...

I thought I would be brave and install the 185 drivers from Nvidia directly.  That part went fine....except I neglected to deactivate the restricted drivers before doing so....and now in the kernel logs it's complaining about having mixed/mismatched driver levels.

Tried to put it in vesa mode but that just gets me a blank screen now when it boots.   How do I get rid of or reset the drivers?    Not even sure if I can now.  I may just reinstall the whole thing and start over as it does not take that long to install.

---

### Post by lidex on 2009-06-07
Sorry, was out of touch for awhile. The 180.53 drivers worked for me with some diligence. Can you boot into desktop? Or access terminal?

---

### Post by Saganite on 2009-06-07
No problem :)  Best way to learn is to just keep at it!  I actually buckled and bought a new video card for the system... the 6800s are pretty long in the tooth and a new 9500 with a gig of ram on it was only 75 bucks.    However, I don't think the new card is what fixed it, and I do seem to have it fixed.

Not sure what did it, but I suspect the 185 drivers are it.   I was a bit stuck for a while as all I would get a black screen.   After replacing the card, however, that issue went away... the SLI config seemed to be adding to the problem along with my messed up xorg.conf and drivers etc.    

I was able to clean up the drivers and install the 185s from Nvidia and since then things have been much better.   Mplayer still sucks, this one HD file I have it just drags on at about 2-3 FPS for some strange reason, but now XBMC is working like a champ...almost.  Some tearing issues if I do not have it in complete fullscreen mode, which is fine as that's going to be it's primary function in the first place....just having some issues with getting XBMC to stay in full screen mode..have not had time to mess with it since that point but it's all looking much better.   Ooo...need to test Hulu again too.

Thanks for the help!   I may not be out of the woods just yet but it's looking like I am...for now! :)

---

