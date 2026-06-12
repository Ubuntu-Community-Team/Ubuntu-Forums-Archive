---
title: "Dual displays"
date: 2008-12-28
forum: Mythbuntu
---

### Post by NautiusMaximus on 2008-12-28
Hi All

I have built an HTPC around a Silverstone GD02-MT case, which has an LCD display on the front. It connects up via a standard VGA connection cable which comes rather inelegantly out of the back of the PC and connects back into the VGA connector.

However, if I have it connected, then nothing appears on my TV, which is connected via HDMI. If I disconnect the LCD display, the output appears on the TV without any problems.

I'm using the onboard graphics on my motherboard, a Gigabyte GA-M78SM-S2H, which should be cable of running 2 displays.

Is it possible to get both displays working under Mythbuntu 8.10. If so, how? 

Obviously I don't want both displays to show the same thing, but I'll worry about the precise configuration of what appears on the LCD display once I've got it working at all.

Thanks
NM

---

### Post by ian dobson on 2008-12-28
Hi,

With both displays attached try enabling twin-view (I think that's what it's called for NVidia) in the control center/NVidia settings.

I've never used it myself but I imagine you'll have to tell mythtv which display you need to use.

Regards
Ian Dobson

---

### Post by newlinux on 2008-12-28
[http://www.mythtv.org/wiki/index.php/Running_MythTV_Dual_Headed](http://www.mythtv.org/wiki/index.php/Running_MythTV_Dual_Headed)

I use  the one X server, two separate displays, no twinview/xinerama involved. You can just use nvidia-settings to set it up.

---

### Post by NautiusMaximus on 2009-01-11
Perhaps I'm missing something obvious here, but I can't figure out how to set this up in NVIDIA settings.

This is what I've tried:
With only the HDMI connection to my TV connected, I boot up the computer and can see everything fine on the TV. The LCD screen isn't connected at this point, so naturally is blank. When I connect up the LCD screen and then click on "Detect displays" in the NVIDIA settings, it finds it. At this stage, it is disable,d but by clicking on "configure" I can set it as a separate X screen, which I gather is what I want. It tells me that a restart is required, so I restart the computer, and when it comes back up the HDMI connection is disabled. I can go back into the NVIDIA settings and tell it to set it as a separate X screen, but this seems to be ignored after a reboot: it's disabled again.

Any ideas what I'm doing wrong here? How can I tell it that I really do want to use both screens?

Thanks
NM

---

### Post by newlinux on 2009-01-11
Backup your existing /etc/X11/xorg.conf. Set it up in nvidia-settings as you want and save it to your xorg.conf (should be a button in there). You probably don't need to reboot, just restart X (Ctrl-alt-Backspace). If that doesn't work reboot (doubt it makes much difference) and post your xorg.conf. Also, make sure you are running nvidia-settings with gksudo or sudo priveleges.

---

### Post by NautiusMaximus on 2009-01-17
Thanks for that: I'll give it a try this weekend and post back with the results...

---

### Post by NautiusMaximus on 2009-02-15
Hurrah! That seems to have done the trick. I think the crucial thing was opening the Nvidia settings screen via gksudo, which I wasn't doing before.

Now, I have a very nice looking screen on the front of the PC with a nice little picture of a mouse on it. Any idea how I can get it to display more than that? Time, CPU temperature, name of music track that's currently playing, that sort of thing?

Thanks
NM

---

### Post by newlinux on 2009-02-15
you might want to look into using conky and some of its plugins.

---

