---
title: "[SOLVED] Help fixing nvidia driver after kernel update? (gutsy)"
date: 2008-06-21
forum: Multimedia Software
---

### Post by chickengirl on 2008-06-21
I got the latest kernel update for Gutsy last night and didn't bother rebooting until this morning. When it came back up it said it couldn't detect my video card (an nvidia geforce card, 6800 I think?) and went to low graphics mode. I tried reinstalling the nvidia packages, reconfiguring x, going back to the old kernel, no joy. Can you help me get my graphics back so I can play WoW again? *snif*

---

### Post by NT4usB on 2008-06-21
Poke around in System Prefs or admin for enable third party or non free or whatever. There's a setting that will detect and install the driver if available and required. 
(My Gutsy box is in the closet atm, or I'd be more specific...)

oops... you said kernel update, not os update. I imagine the third party thing is already enabled then.
When you say reconfigure x, do you mean?```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```

If you rolled back the kernel _and_ dpkg-reconfigured, did it work?
How did you install the drivers originally? envy, hand roll, or Gutsy included drivers, or??

---

### Post by chickengirl on 2008-06-21
> **NT4usB said:**
> 
When you say reconfigure x, do you mean?```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```

Yes, that's what I mean.

> If you rolled back the kernel _and_ dpkg-reconfigured, did it work?
How did you install the drivers originally? envy, hand roll, or Gutsy included drivers, or??

I didn't try rolling back the kernel _and_ reconfiguring at the same time (at least I don't think I did), I'll try that now. I originally installed the drivers from synaptic.

---

### Post by chickengirl on 2008-06-21
Partial success! I got my screen resolution back, but when I ran the reconfigure, the nvidia driver wasn't in the list to choose from. I went with nv instead, and video looks like it's working fine... except I can't play WoW. It says it can't start 3D acceleration. (The exact error message: "World of Warcraft was unable to start up 3D acceleration.")

How do I get the proper nvidia driver back?

---

### Post by NT4usB on 2008-06-21
Not sure why you're not getting it from synaptic..? If it worked before and all that. 
You have universe and multiverse enabled? Did you check that third party thingy to see if it's enabled?

nv is the generic driver. You could try editing your xorg and changing it to nvidia but I'm guessing that it'd just blow up.

Purists would struggle and figure it out. Me, I'd use [Envy]("http://albertomilone.com/nvidia_scripts1.html") and be done with it.
Read the [faqs]("http://albertomilone.com/envyfaq.html") first.
I've had best results using Envy by first selecting #2 (or, is it #6? I don't remember. Do them both! what the heck) to completely uninstall what's there first. Then #1 install. On occasion I've had to resort to the manual install option #5.

Probably go back to the current kernel first, then run envy.

When it works, be sure to thank tseliot, the writer of this wonderful skript and a moderator on these boards.

---

### Post by chickengirl on 2008-06-22
I ran envy and it worked great! WoW is working again, same performance as before (not great, but my computer's not great, what are you gonna do...).

Thanks for your help!

---

### Post by NT4usB on 2008-06-22
Cool. Glad it worked for you.
Be sure to mark the thread solved using Thread Tools above.

ed: Color me dense but I just updated my Feisty box and the new kernel broke my Nvidia.
Running Envy to put it back again...

---

### Post by funkythumb on 2008-06-23
Thanks for the comment (chickengirl) about using the NV driver instead of the Nvidia! Just ran the updates on my Gusty box running Ubuntu Studio, and it broke X! Got a total failure that wouldn't display any GUI at all.

Ran dpkg as per NT4usB, and didn't work using Nvidia driver, but success with NV driver! Don't use any 3D or compiz on this box (strictly a digital video capture system) so I'm a happy camper!

I love the Ubuntu Forum community!

Thanks again!

---

### Post by evil_urna on 2008-06-24
Even after I use envy it still comes back broken. It will boot fine up on the desktop but whenever I try to use the restricted drivers it breaks again. I need those drivers for this system. Is there anyway to get them working again?

Got her!

If your like me and your system seems to be constructed by the devil, made from spare parts from only the most evil computers, this may help you.

First I downloaded the drivers from Nvidia. Easy enough just go to nvidia's webpage and snag them. To install them you must end xserver. Do this with this command

```
 sudo /etc/init.d/gdm stop 
```

This will kick you out to a bare command line interface. The Drivers must be installed from root. So use this command.

```
 sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run 
```

Follow the directions the installer gives you and give the command line a sudo reboot command when you are done and you should be golden.

---

