---
title: "Monitor detection problem with nvidia-settings..."
date: 2012-10-14
forum: Multimedia Software
---

### Post by TropicalStarfish on 2012-10-14
Steps taken:

1-installed ubuntu

2-Ubuntu handles the monitor detection and allows for certain settings based on what it thinks is safe (my guess)

3-isntall proprietary hardware drivers -nvidia's latest

4-Now from what I can tell nvidia is unable to detect the currently used monitors proper range of settings.  It is as if it thinks whatever monitor you are using is the one ubuntu sets the default resolution/refresh rates for, etc...  It feels like a default fail safe profile is linked with the installation monitor.  Which in that case nvidia assumes it to be what it is rather than redetecting it's properties and building a new profile.  In my case, having only one monitor, it seems it would be impossible to accomplish all the tasks necessary to re-detect the installation monitor, which even if this was doable, would not matter because a profile for that monitor has already been created and would probably be loaded up first before a re-detection effort.  So this is how I worked around it...Although I feel there should be a better way...


Now when I plugged in my other monitor it detected exactly what model it was right away and all it's available resolutions and refresh rates were able to be set from nvidia settings.  The catch is... had I installed ubuntu and the proprietary drivers using this monitor, it would not have detected all that.

Basically my set up is that I have 2 monitors.  Whichever monitor I install Ubuntu with and the proprietary drivers with, does not get detected properly and gets unfairly labeled as ubuntu's default plug n play monitor settings.

I would not care if I had a cheap crappy extra monitor laying around for installs, then when things were set up I could plug in the monitors I intended to use and the proper range of settings and info would be detected properly and I could stop using the monitor used to install, but, as things are this is not doable.

I know what is going on here, but I can't seem to fix it from a software stand point.  I've tried editing xorg.conf manually with no success.  The problem is a hardware driver issue and I'm just wondering if there is a work around?

I fixed the problem by using the monitor I did not install the system with.  I plugged it in, things were detected properly, then I disabled the installation monitor, turned off the computer and unplugged the installation monitor.  restarted the computer with the other monitor still plugged in.  Turned the computer off again and unplugged all monitors.  Turned it on again.  Turned it off again and plugged back in the installation monitor.

Now my installation monitor has all the available settings of the post installation properly detected monitor, but...  I should not have had to do things this way.

If any of this keyboard pounding and giberish makes any sense.  Any ideas would be helpful.  I "know" what's going on, but I lack the proper language to describe it.

If I'm right this is a driver issue.  Nvidia-settings is working off ubuntu's default monitor handling profile and for some reason labels the installation monitor with all the default fail safes of a plug n play generic CRT, then because of this can not properly re-detect that monitor as it already is given a profile.

I'm sure there has to be a way around this, but...  I have no idea of how to delete a profile and rebuild one without using a monitor.  The nvidia-settings (detect displays) buttons is, I'm sure, designed to detect the presence of new devices, not destroy old profiles and completely redetect all available inputs and display them, yablahblah.

My apologies for this mess of words.  Any input is greatly appreciated.

---

