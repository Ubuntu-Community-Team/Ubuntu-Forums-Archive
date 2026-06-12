---
title: "Video resolution confusion"
date: 2008-12-21
forum: Multimedia Software
---

### Post by rhartma4 on 2008-12-21
I'm going on my 3rd weekend trying to figure out this video resolution issue, and I think it's time to finally ask for help! So... HELP!!  I'm an engineer, and thought I would be able to figure this stuff out - but pretty much feel like a newbie/noob at the command prompt (so please be specific).  

I have a Dell Dimension 2350 with an integrated Intel 82845G/GL video adapter.  I want a dedicated PVR, so I installed Mythbuntu 8.10.  However, upon reading that the video resolution control methods have changed for this version (and the amount of information on how to fix it seemed more limited) - I opted to go back to version 8.04 - which is where I presently am.

I want to connect the PC to my Toshiba 65HM157 via the VGA/PC Input.  It has limited resolution capability, the highest of which is 1024x768@60 Hz.  

The issue is that I installed the software when connected to a monitor (an old Dell M57).  I setup the resolution to 1024x768 @ 60 Hz, shutdown the PC, carried it over to the TV, plug it in and get "Unsupported Video" from my TV.  Huh?  

So, I carry the monitor to where the TV is.  Plug the monitor back in, get it back to 1024x768, plug the TV in (w/o rebooting), and it works on the TV!  Reboot.  It's messed up again (in fact the system seems to hang).  I'm quite certain this is due to improper auto-detection of the TV set (by the PC OS).  I can reconnect to montior, reboot, and it seems OK again.

The generic question is - what is the best/easiest way to lock-in the resolution at the setting that I want, regardless of what display is connected???

I've seen other forum posts to this link:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

So, I first tried modifying /etc/gdm/gdm.conf-custom.  At the prompt, I found the proper syntax of xrandr to get it in the proper display mode.  But for whatever reason, adding this to the end of the gdm file did not seem to work upon reboot.  

Next, I tried modifying xorg.conf.  First, only to add the resolution/refresh.  No luck.  Then, I tried to turn off the autodetection, although I'm not sure if the Option I should be using is NoEdidModes or NoDDC (I tried both).  I also tried using Modelines, using the calculator on this page:

[http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html](http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html)

Lets see, I also tried "gksudo display-config gtk" and "sudo dpkg-reconifigure -phigh xserver-xorg."

I've tried both the "Intel" and the "i810" driver.  I see other drivers on the web, which I could install from tar files, but I can't believe that is the problem.  After all, I can get the resolution on my monitor - just not on the TV!

I saw a synaptic package (i915resolution or something?) for modifying the video BIOS, but the docs suggest that newer intel drivers should not need to use that.

You know, there is just so much information out there.  I find it difficult to find relevant posts that give specifics. I bought a couple of books also, which were good for background info - but seem outdated.

ANYWHO...  is one of these the "right" way to do it?  Maybe I just have the wrong syntax.  Why can't you just use the "Settings Manager -> Display" to choose and keep the resolution you want?  Or in the MCC, there is a "Launch Xorg Config" button.  Which of these controls has precedence?  There are no GUI tools out there?  Argh!

Sorry if I've been too wordy, and thanks to anyone who takes the time to reply!

---

