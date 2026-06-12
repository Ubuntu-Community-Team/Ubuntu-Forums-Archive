---
title: "Dual Monitor - Extended not Clone"
date: 2008-08-05
forum: Multimedia Software
---

### Post by obsaysditto on 2008-08-05
I currently have a Dell D610 Laptop with ATI card and a monitor connected. Currently, the laptop screen and monitor are showing the same thing. I would like have the monitor as an extension of the laptop screen.

I followed this tutorial to get the second monitor to work:
[http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitors+cloned](http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitors+cloned)


Also, in System->Preferences->Screen resolution, both displays are detected and the "Clone Screens" option is unchecked.

Thanks.

---

### Post by markbuntu on 2008-08-05
If you have the restricted driver enabled you can get amdcccle from the repositories with synaptic and then type:

```

amdcccle

```

in a terminal and you will get the ati Catalyst Control Center which has a display section that will allow you to set up your displays. xorgconfig is being deprecated and the ati driver does not read it. 

You can also type:

```

aticonfig --help 

```

to get a list of command line options to use with the aticonfig command to set up your desktop.

---

### Post by obsaysditto on 2008-08-05
OK. the restricted driver was not enabled. I enabled it and the Catalyst Control Center. In Catalyst Control Center, The display monitor showed the analalog monitor(CRT) and Digital Monitor (laptop). However, during testing "Big Picture" and then cancelling it, the laptop screen is not on and the CRT is on. 

I have reverted to my original xorg.conf file, disabled then renable restricted driver. When I start the laptop without the CRT plugged in, the laptop screen will show normal function. When I start the laptop with the CRT plugged in, the CRT will show but the laptop screen will be off.

Thanks

---

### Post by markbuntu on 2008-08-05
In the display manager of Catalyst in the Display modes section there is a little box Enable Display. If that is not on (grey, indented) then the display outlined in red will be turned off. Make sure you have both displays enabled.

Also, for some reason, when you choose big desktop/apply the display will not change to big desktop but the box will come up "keep these settings" or something like that. You should just say OK if you can see the box and then reboot with the crt on and it should work. What that is for basically is a failsafe in case you get a black screen or something and it will automatically revert to the old setting in 15 seconds or so.

---

### Post by obsaysditto on 2008-08-05
ok perfect.

After some messing around, I got both monitors enabled and big picture worked. So I never had to edit my xorg.conf. I'm guessing ubuntu is progressing well.

Thanks for your help. I was making it more complicated than it needed to be.

---

### Post by obsaysditto on 2008-08-06
and now when I try to turn on Extra Visual Effects it says "Desktop effects can not be enabled"

should i start a new thread?

---

### Post by markbuntu on 2008-08-06
No, we can stay here, they are sort of related. Look in your X0rg.0.log which you can get to in System/Administration/System Log and look for any messages that start with (EE), more specifically something about unable to intitialize dri or DRI Fail or something like that. 

Post all the EE messages here.
btw, which ati card are you using?

---

### Post by obsaysditto on 2008-08-06
No EE messages in the system log after trying to put on desktop effects. When I filterd the log with DRI this is what was displayed:

```
/var/log$ cat Xorg.0.log | grep DRI
(II) Loading extension XFree86-DRI
(==) fglrx(0): NoDRI = NO
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete
(II) GLX: Initialized DRI GL provider for screen 0

```


also i believe this is my video card:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
```

---

### Post by markbuntu on 2008-08-07
Some cards are just not powerful enough to run compiz on that large of a screen. You can look in the compiz forums about that problem and about setting up your card for best operation with compiz:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

The rest of the compiz forums are here:

[http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

Please come back and post what you find out.

---

### Post by obsaysditto on 2008-08-07
I think my card cant handle 3D effects past a resolution of 2048. Well, it'll have to wait.

---

### Post by matteosistisette on 2011-02-10
Hi,

I have the exact opposite problem. I can easily setup the extended desktop (i.e. one big desktop spanning the two screens) or "separate X screens", but I don't see any "clone" option that would allow me to have the same desktop cloned on both screens.

I have an Nvidia card and the Nvidia restricted drivers enabled and am using the nvidia-settings utility.

How do I select clone?? There doesn't seem to be such an option!!

---

