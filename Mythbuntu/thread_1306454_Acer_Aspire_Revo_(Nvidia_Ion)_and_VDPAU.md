---
title: "Acer Aspire Revo (Nvidia Ion) and VDPAU"
date: 2009-10-30
forum: Mythbuntu
---

### Post by terp4life2001 on 2009-10-30
Hello,

   I have a new Revo that I've installed Mythbuntu 9.10 on. I've been trying to get 1080p playback using VDPAU. I've disabled the real-time threads and video plays. It looks great, but it stutters. 'top' reports the CPU(s) are running around 18% for mythfrontend.

   I've seen some posts about changing the CPU frequency scaling, but I don't think it's supported by my processor. The CPU frequency applets fail and when I try to run 'cpufreq-selector' from the command line it just reports, "No cpufreq support."

   I did disable OpenGL vertical sync, which maybe I should re-enable. Are there any other suggestions?

Thanks in advance,

//Rob

---

### Post by ZedThou on 2009-10-30
I've been playing around with mythbuntu on an ionitx-a (atom 330) the last few days, and have learned a few things. On the initial install, 1080p was stuttering a good bit. When I added

Option         "TripleBuffer" "True"

as recommended at [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU) it seemed to help (although
I also had to disable composite and useevents, if I recall). But the thing that really ironed it all out was overclocking! My BIOS allowed me to increase the CPU clock from 1.6 GHz up to 2.0 GHz, and the IGP clock from 450 MHz to 600 MHz. I didn't have to mess with voltages or anything, I just set the new speeds and kept an eye on temps and everything is stable for now. I've also installed the latest nvidia 190.42 driver, but cannot tell that it has made a difference over 185.

Have you also tried using a vdpau-enabled player to view straight from the tuner stream, to see if there's a marked difference as opposed to reading and writing to disk and playing at the same time? The single-core cpu would make me a little bit concerned here, maybe without justification though.

I should also add that I'm using the VDPAU Slim (bob, 2x hw) playback profile, haven't yet gotten around to trying others, I have enabled sync on vblank, and I also have realtime priority enabled, but a message in the mythfrontend log seems to indicate that it needs to be running suid root to actually use that option.

---

### Post by terp4life2001 on 2009-10-30
I do have TrippleBuffer set to True.

root@lefteye:~# cat /etc/X11/xorg.conf
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
        Option  "TripleBuffer" "True"
EndSection

Section "Extensions"
        Option         "Composite" "Disable"
EndSection

I'll check my BIOS settings for overclocking. I'm suprised that the ION allows it. I did look in my BIOS earlier becuase I was looking for some "CPU frequency scaling" settings. I didn't find any and I didn't notice anything about overclocking, but I'll double check.

I've tried both the in-repo NVIDIA drivers 185(?) (I don't remember the exact version) and now I have the 190.42 drivers installed. I didn't see a difference.

I tried using mplayer but it was having issues. It was complaining about not knowing what '-vo vdpau' was. It made me nervous that the stock mplayer didn't have VDPAU support. I have to follow up on this more.

Do you know if I need to turn on OpenGL vertical sync in nvidia-settings as well as mythtv? I think I might only have it on in mythtv.

I just read something about disabling "Aggressive audio buffering" so I'll try that this afternoon.

---

### Post by ZedThou on 2009-10-30
While you're digging around in the BIOS, you might also try to maximize the memory allocated to the IGP. Mine is set at 512MB.

---

### Post by spotspot on 2010-01-17
Hey I got a revo with ion and am also trying to get it to work with VDPAU and mplayer (i have MPlayer SVN-r29237-4.4.1 the default).  I started with the 185 drivers and have upgraded to 190.  I can play some files with "mplayer -fs -vo vdpau -vc ffh264vdpau" but with files from x264 it crashes the driver with weird triangles and memory goo splattered on the screen.  Any advice?

---

### Post by RichardK3 on 2010-01-18
Some of the information in this thread might help:

[http://www.gossamer-threads.com/lists/mythtv/users/418325?page=unread#unread]("http://www.gossamer-threads.com/lists/mythtv/users/418325?page=unread#unread")

---

