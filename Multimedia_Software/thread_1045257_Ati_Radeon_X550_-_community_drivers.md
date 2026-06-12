---
title: "Ati Radeon X550 - community drivers?"
date: 2009-01-20
forum: Multimedia Software
---

### Post by Znupi on 2009-01-20
Hi. I have an Ati Radeon X550 (512MB RAM) graphics card and, as you may or may not know, the official Ati drivers suck (in a metaphorical way). What I'm having most problems with is video: I can't get video acceleration for the life of me. Basically, xvimagesink doesn't work, only ximagesink does. Watching Flash videos on websites uses 100% CPU even though hardware acceleration is enabled in Flash (disabling it makes no difference whatsoever). Watching videos with slightly bigger resolution again uses 100% CPU and is choppy.

So, what I want to try, is to use the Ati community drivers. What I don't know is how to install / activate them. If I simply deactivate the official driver in **System -> Administration -> Hardware Drivers**? Or do I have to also install the community drivers afterwards?

Thanks :)

---

### Post by Bablefish on 2009-01-20
Call this a warning...BE CAREFUL!!! I have and ATI card on the computer I run Ubuntu on and when I tried to install those drivers...at it did was crash my video drivers. I had no choice but to reinstall my OS. So be warned...

---

### Post by Melcar on 2009-01-20
The open source drivers are installed by default.  When you remove fglrx Ubuntu should automatically revert to using those drivers.  Keep in mind that while these drivers will offer 2d/3d support for your particular card, they are only opengl1.3 and are on a good day half as fast as fglrx.  Movie watching and similar should be fine however.

---

### Post by Znupi on 2009-01-20
I came across this: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

So, after removing fglrx and using the opensource drivers, and after tweaking a bit xorg.conf, my first impressions are that it is much faster. Xvimagesink now works, so videos play a bit better (though really hi-res videos are still choppy -- I just downloaded an "HD" trailer from gametrailers.com and played it and after the first 20-30 seconds it became unwatchable). I have a feeling Compiz works faster, too (I didn't use it before because I felt it was too slow).

Flash videos are still horrendously slow. I have Gnash installed, but for some reason the "Manage Content Plug-ins" option in Firefox under Tools is disabled (grayed-out) so I can't try it :(.

---

### Post by Melcar on 2009-01-20
HD videos will chew up your CPU.  I think fglrx can accelerate HD content on some cards, but the open source drivers lack this feature.  My laptop (2GHz Sempron , 200M IGP w/ radeon driver) can play 720p movies rather well, but the CPU is the one that does all the work.

---

### Post by Znupi on 2009-01-20
I have an Intel Pentium DualCore 2.80 Ghz but it still doesn't cope with the 720p movies from gametrailers.com. Oh well, I can do without those, but the super slow Flash plugin still bugs me. And Gnash doesn't work with anything -- not even YouTube. Damn you Ati for not making proper drivers for my card!

---

### Post by Melcar on 2009-01-20
What player are you using?  I always found mplayer the best with its caching feature, specially when viewing large video files online.  As for flash, try uninstalling/re-installing the plugin.

---

### Post by steefjeqv on 2009-01-20
Hi,

Tormod Volden packages the most recent xorg-ati drivers for Ubuntu.

[http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/]("http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/")

[https://wiki.ubuntu.com/XorgOnTheEdge]("https://wiki.ubuntu.com/XorgOnTheEdge")

Enabling EXA will improve video playback.

Greetings,
Steven

---

### Post by Znupi on 2009-01-20
I'm using Ubuntu's default, Totem. But, I find that Totem (Xine) is a lot better than GStreamer. No idea why, but it just works a lot better, videos aren't choppy at all. Also, I did try reinstalling the flash plugin, still painfully slow.

**steefjeqv:** thanks for the advice, but I think I'm going to stick with the stable drivers for now. And yes, I did enable EXA :)

Thanks :)

---

### Post by steefjeqv on 2009-01-21
Hi,

Another thing which may improve video performance is using "Textured Video".

You'll have to edit the config file of .xine in your home folder.

# video display method preference
# { Any  Overlay  Textured Video }, default: 0
video.device.xv_preferred_method:Textured Video

# Xv port number
# numeric, default: 0
video.device.xv_port:yourtexturedportnumber

You can find your Xv port base  number by using your terminal with xvinfo.

Greetings,
Steven

---

### Post by Znupi on 2009-01-21
Thank you, but even with those changes I still can't view HD movies. It does feel a bit faster, though.

I guess I'll just have to be careful next time I buy a desktop PC to buy one with an nVidia graphics card. Too bad, Ati.

---

