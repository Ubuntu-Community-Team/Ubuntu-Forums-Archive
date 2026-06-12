---
title: "Manually setting up monitor and video"
date: 2008-08-21
forum: Multimedia Software
---

### Post by the_nite_owl on 2008-08-21
Hi All,
I have been fighting my nVidia resolution problems for a while and hope someone can answer a few questions.

My monitor is apparently not auto-detected and the xorg.conf has invalid data for it.
I managed to install the nVidia drivers for my GEForce 6100 and it gave me a long list of resolution options and 3D acceleration is working but the refresh rates appear to be incorrect.
When I select 1280x1024 it sets the refresh to 51 and my monitor only supports down to 56.  Consequently I get a thin line of light at the top of the screen as the only output.

I edited the xorg.conf file to change my monitor frequencies to 
Horizontal:30~79KHz
Vertical :56~75Hz
It does not seem to have had any impact so I assume there are settings for the nVidia driver that need tweaking or at least for the resolutions that Ubuntu (8.10 i386) offers me.

What file/section would I modify for the video resolution options?
What entries in xorg.conf would I setup to set the logon screen resolution?  Currently I get the same thin line for video but after I enter my id/password it loads the desktop and changes to the desktop resolution.

I am close to getting this working, just have to alter the resolution/refresh rates to match what the monitor and video processor actually support.

Thanks.

---

### Post by NT4usB on 2008-08-21
You're on the right track. xorg is where you would configure it. Sintax is important though.
Post your xorg.conf.
Resolution on bootup is a pita (for me, anyway) so I disabled the graphic. I find it more entertaining to watch the terminal printout while it's booting anyway...

---

