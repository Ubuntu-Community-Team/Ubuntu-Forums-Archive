---
title: "[SOLVED] Nvidia and 8.04"
date: 2009-01-06
forum: Multimedia Software
---

### Post by sbentjies on 2009-01-06
This is a new post of an old theme but I think I'm not asking the right question. I have a GEForce chipset on an eVGA FX-5200. I am running 8.04 out of the box and I can't get higher than 800x600 resolution. I've heard everything from use Envy to compile a new kernel. I am a n00b to Linux in particular but not to computing. I need the correct approach to this. Do I use nvidia drivers, beta drivers, an older binary driver, what? The restricted drivers made the resolution worse. I am a month into this and getting no further ahead. I really appreciate all the help from the dedicated posters on this forum.

Jim

---

### Post by Chris_Hookey on 2009-01-07
i had the same problem with a geforce 5600. i tried everything you mentioned. what i ended up doing is at the grub menu selecting the recovery option and when it redetected my hardware, i then had the option to up the resolution to 1024x768. give that a shot. 
                                    Chris

---

### Post by sbentjies on 2009-01-07
The only options I had were to fix the x problems but it never had a place to set the resolution. I'll try it without x broken. There has got to be a standard way to fix this, or an AGP card that will work with Ubuntu.

---

### Post by sbentjies on 2009-01-07
No go on that. No menu to change video resolutions, just to Fix X or fix broken packages, both happen behind the scenes.  I'm lost.

---

### Post by lamikins on 2009-01-07
sbentjies, I may be in a similar situation to you (and have had very minimal success in resolving the issue).  Just to clarify:

-  you intall the restricted driver (through System -> Hardware Drivers, or Envy, or apt-get install nvidia-"some version like 177 or whatnot"
-  you reboot X (ctrl alt backspace)
-  when you return to login to your session, the resolution is massively out of whack and (now here is the kicker) the text settings are all cockeyed (odd font)
- finally, the only way to read or do anything useful is to disable the responsible driver or boot in low-graphics mode?

Just wanted to see if this is in fact your situation (it is mine).  

If it is, the general suggestion seems (obviously) to be to install the restricted driver, then edit /etc/X11xorg.config as root to change the resolution settings to 1024x786 or whatever you want.

Alternately, to edit the X config to the relevant graphics driver (ie change it from "nv", if it is set to this, to "nvidia" in the Display section).

These attempts were fruitless on my end, but there are reports of some success.

---

### Post by sbentjies on 2009-01-07
I get the same thing you do. I get the feeling this IS a restricted driver and I have to first install it, then allow the restricted drivers in hardware manangement. I have and nVidia NV34 [GeForce FX 5200] according to lspci | grep -i nvidia. I just don't know whether it's glx, glx new, or glx legacy. I wish I could get a straight steer on this.

---

### Post by lamikins on 2009-01-07
You and me both RE the straight steer.  As for allowing restricted hardware - you just need to enable that through Synaptic (for one), I believe.  I'm quite sure it being "restricted" has little to do with our problem.

I'll post any progress I have!  Good luck

---

### Post by sbentjies on 2009-01-07
Do you happen to know where in synaptics to enable it, ie which package?

Thanks,

---

### Post by lamikins on 2009-01-07
I'm not exactly sure what you mean.  Implementation of third party and restricted packages is quite nearly the default!  

You can go into Synaptic --> Preferences --> Repositories, and make sure you have "main", "universe", "restricted" and "multiverse" all enabled.  From memory your distro should prompt you for authorisation to not only download/search, but actually use third party software packages.

---

### Post by sbentjies on 2009-01-07
I got some packages but I still don't know what drivers I need to use for this card. Could someone steer me in the right direction? It's an EVGA FX-5200 (nvidia chipset). I don't know whether it's a glx, glx new, or glx restricted. Do I get the driver from nvidia? I don't even know where to start now. I've loaded certain drivers from Nvidia but they have broken X every time.

---

### Post by CHaoSlayeR on 2009-01-10
What display do you have? If it is an LCD which native resolution does it have? If not what resolution do you want to have on your display?

I just saw that you tried the 180.xx.xx driver. That one doesn't support your card as you experienced the hard way, although it fixes a lot of problems. But that's the way of commercial life. They always want you to buy something new... :)

> **sbentjies said:**
> Because I can learn, because my machine runs twice as fast with Ubuntu as it does XP, and because it's FUN and FREE.

...well... no comment.

As I said in another topic I'm currently running the open source driver on my Dell notebook and as long as you don't require 3D acceleration or dual head setups you could give it a second try too. If you want to try with that one again I could help you out a bit. But I'm for sure not one of those hackers over at X. And even over there noone knows all aspects of the X. So I may be able to tell you some basics and provide you with some configurations and if all went well you should finally be where you want to be.

C]-[aoZ

---

### Post by sbentjies on 2009-01-10
I have a Sony Vivitron (branded for gateway) CPD-17F13 and I'm trying to get 1024x768. Not a big want.

---

### Post by CHaoSlayeR on 2009-01-10
OK thanks for that,

now we have to get to know if the graphics driver already detects the capabilities of the monitor correctly. Could you post your Xorg.0.log please? Don't cut it and please use either the attach file option or post it inside code tags.

---

### Post by sbentjies on 2009-01-10
I hope the attached file is there. Thanks for your help.  JP

---

### Post by CHaoSlayeR on 2009-01-11
Thanx for that info. Now I have the reason why you can't get a resolution more than 800x600:

The monitor does not provide enough information about itself (the graphics driver asks it for so called EDID and DDC information). So the capabilities are not available to the driver and it falls back to a very standard mode that usually work on all displays.

To override this behavior we now have to add so called modelines for your monitor to the xorg.conf. That way we can manually specify resolutions that the driver can choose from. But first we will try something less intrusive. By manually specifying some capabilities of the monitor the driver may choose a better mode itself. Please add the following information to your monitor section:
```
     HorizSync   31.5-64
     VertRefresh 50-120
```

Then we add the following to the 'SubSection "Display"' inside the "Screen" section:
```
        Modes       "1024x768"
        Virtual    1024 768
```

If that doesn't help we will have to add at least one modeline. From the data I found onthe web for your monitor I calculated some modelines. So if the previous method doesn't work you can try this:

Make a backup of your xorg.conf!
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.fallback
```

Add the following to the "Monitor" section:
```
        Modeline "1024x768@85" 100.94 1024 1056 1432 1464 768 782 793 807
        Modeline "1024x768@80" 93.08 1024 1056 1408 1440 768 782 792 807
        Modeline "1024x768@85i" 42.91 1024 1056 1216 1248 768 784 790 807 interlace
```

Replace the "Modes" line in sub section "Display" in the "Screen" section with the following:
```
        Modes       "1024x768@85" "1024x768@80" "1024x768@85i"
```

Remove the "Virtual" line below that.

This should enforce the resolution. If you experience any bad behavior (screen garbled, going blank, etc.) please switch to a console (CTRL+ALT+F1), make a copy of the Xorg.0.log (cp /var/log/Xorg.0.log ~/Xorg.0.log.error) and provide it here again.

The specs of that monitor are very low and it doesn't seem to be a good choice to use that one. Even at 1024x768 the vertical frequency is very limited because the horizontal frequency is limiting the drawing speed of the pixels.

In addition there may be better modelines available for your monitor but it seems that detailed information is no longer available for your monitor so I generated them using safe guessing for unknown values. If you want to generate yourself some more modelines go [here]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl"), fill the values and hit "calculate modeline". The data I used are as follows:
```
horizontal sync: 31.5 to  64 KHz
  vertical sync: 50   to 120 Hz
```

That being said I hope it fixes your problem. If not I really recommend getting a better monitor.

C]-[aoZ

---

### Post by sbentjies on 2009-01-11
I will give that a shot. I do have a more modern CRT monitor that I could use if it would make things easier

---

### Post by CHaoSlayeR on 2009-01-11
Before you try another monitor make sure you remove all specific things from the xorg.conf, especially the **HorizSync**, **VertRefresh** and **Modeline**s from the **Monitor** section and **Modes** and **Virtual** from **Screen** sub section **Display**.

I hope we finally get what you want.

C]-[aoZ

---

### Post by sbentjies on 2009-01-11
I tried those resolution additions-no go, it broke X so I switched to the newer Mitsubishi Diamond monitor and it WORKED! Your take on the old monitor was dead on! I don't care about 3d acceleration and I've got 1024x768. I'm happy. Big thanks to you, Liberty Shadow, and everyone else on this forum who contributed.I can't thank you enough.

---

### Post by CHaoSlayeR on 2009-01-12
Nice to hear that it worked with the other monitor. :)

Please mark this thread as "solved" using the "thread tools" at the top.

C]-[aoZ

---

