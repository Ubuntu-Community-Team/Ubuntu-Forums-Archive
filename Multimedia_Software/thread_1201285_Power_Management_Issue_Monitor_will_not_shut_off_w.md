---
title: "Power Management Issue: Monitor will not shut off when computer sleeps"
date: 2009-06-30
forum: Multimedia Software
---

### Post by HD Chang on 2009-06-30
I wasn't sure where to post this but I believe it is a video card driver problem so thats why I'm putting it in here.

[COLOR="Red"]Setup[/COLOR]:
Jaunty 9.04
Sapphire GeForce 9400 GT (Nvidia 180.44 3rd party drivers)
Monitor: Asus VW246H FlatPanel hooked up via HDMI

[COLOR="Red"]Problem[/COLOR]: Hooked up via DVI/VGA the monitor sleeps with the computer.  Hooked up via HDMI when the computer sleeps, the monitor blares an extremely annoying bright blue screen asking for an input on the HDMI port.

According to some folks on the forums over at Asus, the monitor isn't getting the information from the video card that it is 'bedtime' and to shut off when the computer goes off.  I suppose if i had this monitor hooked up to my cable tv it would just go on forever displaying that annoying blue screen asking for some HDMI input (give the cable box was off)

[COLOR="Red"]Things I tried[/COLOR]:
1)edit /etc/X11/xorg.vonf
added DPMS
checked with xset & its enabled.
went into system/screensaver set my stuff up to sleep
everything works great until the computer shuts down to sleep mode and then the blue screen hits!

2) manually ran xset and forced the monitor to Sleep/Suspend/Off, let the comp. go to sleep after the monitor was in one of these modes: blue screen again.

3) Dont know what else to do...

Can someone please help me?

PS: The same problem occurs in Windows 7

The more things I try the more I start to think its a flaw in the monitor itself.

Thanks

---

### Post by HD Chang on 2009-07-01
I found this piece of information on an Nvidia forum from a user who had fixed his problem in windows:

> Just in case your interested, this problem happens because the Nvidia driver thinks your monitor is a TV (as far as I know this only happens on HDMI monitors, hence just switching monitors can induce this problem.) This problem is not limited to just Hanns-g HDMI monitors - at least some HDMI monitors by other manufacturers have the same problem (you can google & verify this). Of course Nvidia blames the manufacturers and they blame Nvidia (what else is new). Nvidia will not post this fix (obvious legal reasons) but assured me if done correctly was perfectly safe. They also said they plan on eventually fixing this in the drivers.

Above Quote--> [http://forums.nvidia.com/index.php?showtopic=82031&st=0&p=480551&#entry480551]("http://forums.nvidia.com/index.php?showtopic=82031&st=0&p=480551&#entry480551")

They are fixing it via a regedit but I have no idea where to do something similar in ubuntu.  It would mean screwing around with those third party nvidia drivers would it not?

---

### Post by HD Chang on 2009-07-01
Ok, I hope I am on the right track but I may have narrowed it down to needing to specify the "custom" EDID of my monitor and using nvidia-xconfig to set it.

If anyone has any experience in this area I would appreciate your help and continue to search for the answer.

I have my EDID information.

---

### Post by HD Chang on 2009-07-01
To hell with it.

There is a bug in Nvidias driver somewhere, i dont know enough about this crap to figure it out.

Switched to DVI and it works fine, good thing im not totally reliant on HDMI to carry my sound...

---

### Post by zurcherart on 2009-07-03
I just found your post.  I am having the same issue.  And I will try the same solution as you.  I have a canonical support contract and they've been aggressive in denying an issue even exists--but if it exists it's not something they support.

So I'm ready to say to hell with it to.  (Though I'd love a proper solution.)  How did you revert to DVI?  My system detects my monitor is HDMI capable and automatically goes to HDMI mode. 

How do you force your system back to DVI?

---

### Post by HD Chang on 2009-07-03
> **zurcherart said:**
> I just found your post.  I am having the same issue.  And I will try the same solution as you.  I have a canonical support contract and they've been aggressive in denying an issue even exists--but if it exists it's not something they support.

So I'm ready to say to hell with it to.  (Though I'd love a proper solution.)  How did you revert to DVI?  My system detects my monitor is HDMI capable and automatically goes to HDMI mode. 

How do you force your system back to DVI?

Mine worked automatically:  Shutdown..switch cables..boot up.
On my monitor (if you have the same one) you have to manually change the input to DVI with the button on the face of the monitor.

If you have unplugged the HDMI cables it shouldn't be reverting to HDMI.

---

### Post by zurcherart on 2009-07-04
Ok.  Seems obvious.

Thanks for the feedback and suggestions.

Unfortunately, the only digital input on the back of my monitor is HDMI.  My cable is a dvi->hdmi cable.  Until the Nvidia driver is installed the system uses DVI signalling (the monitor indicates anyway that it's being driven by a DVI signal).  After the Nvidia drivers install/or are loaded the signalling switches automatically to HDMI and I have the standby problem you describe.

It does seem like a setting on the monitor should force the monitor to report that it wants DVI signalling.  But I don't find it.

So it looks like I'm still searching for a solution.I hope someone is able to tell me how to configure the drivers on the LINUX side to use DVI signalling (no matter what the monitor is capable of)...because so far that appears to be my only work around.

---

