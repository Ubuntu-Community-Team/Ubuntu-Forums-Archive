---
title: "Tv Out with ATI 9800 on 9.04"
date: 2009-08-18
forum: Multimedia Software
---

### Post by GuruMadMat on 2009-08-18
Hi

I would like to enable tv out on my pc:
I use ubuntu 9.04 and have a ATI 9800 
```

01:00.0 VGA compatible controller: ATI Technologies Inc R360 NJ [Radeon 9800 XT]

```

Tv out is with a scart cable.
Everything is working fine on crt screen but not on tv screen.
I just want it to clone everything.

I already tried to install the new drivers from ati, but I think my graphics card isn't supported. I'm not sure...
But when I did it was showing all vertical lines.

Can someone help me in the right direction?

---

### Post by penguinchrissy on 2009-08-18
I don't know if I can point you in the RIGHT direction tell you what I tired to do with a similar card. I have a ATI 9800Pro All in Wonder that I tried to get the tv-output to work with. I got close using two different sites one with the Ubuntu wiki page that gave steps on how to install the drives for the ATI card but I had the same problem you had the screen would freeze with lines just after boot. I tired adding it to the basic driver by editing the xorg that worked but it would be blowin' up on the screen and was just blue. I found a site ([http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/](http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/)) that showed how to downgrade to Xorg 1.5 and install the drivers that way because Xorg was the reason it seemed our drivers where unsupported. I could get Catalyst running and all that but it wouldn't see the tv-out no matter how I configured it. 

I found all this in the forums after doing some hard searching. I'll try and go back and find the exact links and if I find them I'll edit my post here.

A big suggestion that I do have is to install envyng. The reason I suggest this is it makes it real easy to install and uninstall the drivers from the command line if your xorg fails to boot. All you will have to do is type 

sudo envyng -t

then follow the prompts. 

Sorry I can't be of a positive help but just thought it would be nice to know your not the only one looking for support for this and maybe you can learn from my mistakes.

GOOD LUCK!

---

### Post by GuruMadMat on 2009-08-18
I've done it!

I started to follow the guide on how to downgrade from xserver 1.6 to 1.5, but even before I restarted I had tv out enabled.

If someone needs a config file, just ask...

---

