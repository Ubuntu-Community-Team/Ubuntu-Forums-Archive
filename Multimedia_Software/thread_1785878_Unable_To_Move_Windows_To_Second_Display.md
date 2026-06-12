---
title: "Unable To Move Windows To Second Display"
date: 2011-06-18
forum: Multimedia Software
---

### Post by Medic-5150 on 2011-06-18
Hey guys,

I'm brand new to this whole Ubuntu thing.  I love it so far, but I am having some issue.  I installed Ubuntu a week ago and had no problems getting anything on my second display.  Sadly I had to reformat since then and I have been unable to get anything to work.  My background displays on the second monitor (42" phillips TV) and the cursor will move over.  However, if I try to move a video or anything else over, it just wants to dock on the ride side of my Samsung SynMaster 2053.  I have activated the Nvidia driver for my Nvidia 8800GT graphics card.  I went into the Nvidia X server settings and it recognises there are two screens.  when I go through Ubuntu and into monitor preferences it shows one monitor and it is "unknown".  Detect monitors does nothing, nor does a restart.  doesn't seem to help by switching workstations either.  Any suggestions?

Thanks,
Andrew

---

### Post by BicyclerBoy on 2011-06-18
You can not use the gnome display preference when running the nvidia driver.
Just use nvidia-settings.

The way your screens are working is normal "separate X screens" as set in nvidia-settings.
This allows completely independent resolution refresh rate (video modes) etc.
This is my preferred configuration for full screen video (on 1 screen).
You can not drag anything between screens. You can not make icons/shortcut launchers on 2nd screen (you could in 8.04).

You can direct apps to launch on either screen (can edit the launcher properties &/or run script).
Most apps stay on the screen they are launched on (via menu or terminal)..

Twinview is the other option..your desktop becomes a meta-mode of both screens video modes. This allows dragging etc..

---

### Post by Medic-5150 on 2011-06-18
> **BicyclerBoy said:**
> You can not use the gnome display preference when running the nvidia driver.
Just use nvidia-settings.

The way your screens are working is normal "separate X screens" as set in nvidia-settings.
This allows completely independent resolution refresh rate (video modes) etc.
This is my preferred configuration for full screen video (on 1 screen).
You can not drag anything between screens. You can not make icons/shortcut launchers on 2nd screen (you could in 8.04).

You can direct apps to launch on either screen (can edit the launcher properties &/or run script).
Most apps stay on the screen they are launched on (via menu or terminal)..

Twinview is the other option..your desktop becomes a meta-mode of both screens video modes. This allows dragging etc..


I was originally using unity with the driver and having a bunch of issues.  I just reverted back to gnome and disable the nVidia driver and it works just fine.  I guess I'll stick with gnome!  Thanks for your help!

---

### Post by BicyclerBoy on 2011-06-18
Just for completeness. (with separate X screens)

 export DISPLAY=:0.1 && mythfrontend

would launch mythfrontend on the second monitor.
Can use this code in script or terminal or launcher properties.

Without the nvidia driver your video playback performance (the 42" TV) will be underwhelming.

---

