---
title: "Lost Video on 8.10 upgrade"
date: 2008-11-16
forum: Mythbuntu
---

### Post by Grandma_DOG on 2008-11-16
The upgrade appeared to go smoothly.  But upon reboot, I discovered that the TV goes blank after the "mythbuntu' logo shows its fully loaded.

Having the foresight to use VNC, I remoted into it.  It looks fine, but it just won't show any video to the TV.  The TV is a new 54" phillips and it says 'unsupported video format'.

I checked the resolution to be 1960x1080

I then went into grub and booted to recovery mode.  Told it to fix x server.  It then booted and the TV shows the mythbuntu GUI, but if I try to watch TV, I get black screen.

Any ideas?

---

### Post by jMon54 on 2008-11-17
I had the same experience or at least similar.  Mine did work after several reboots but last night suddenly the symptom recurred.  Bummer!  I hope someone has an answer or at least some good trouble shooting advice.  In the meantime, I'm going to check out re-installing the nVidia driver as soon as I get a chance.

---

### Post by jMon54 on 2008-11-18
Last night I tried something I found on another post: I copied over the xorg.conf with the failsafe version in the same folder.  Then I downloaded Envy and ran it and let it install the recommended nVidia driver.  It got me going again but I did have a few hiccups.  So I'm not totally there yet.

---

### Post by dmfrey on 2008-11-18
I had a similar issue with my upgrade...Looks like it goes through downloading and installing the packages, but it seemed to fail a lot on cleanup.  After reboot, I got a black screen.  XOrg prompted me to try to fix it, or go to safe graphics view.  When I got into a desktop, the Hardware Drivers applet let me know a proprietary driver existed.  I selected nvidia 177 (recommended), it installed and rebooted...All was good :)

I was very concerned that the upgrade seemed to have failed, but it was able to recover.  I am guessing some cleanup will still need to be done, but haven't had a chance to go in and look at it.

Grandma_dog, if you can ssh in and remove your xorg.conf, or use one that got backed up when the upgrade took place, replace it with that one.  Then reboot and you should be prompted to fix it or go into safe graphics mode.  Select safe graphics mode and follow what I did above.  That should get you by the problem.

---

### Post by jMon54 on 2008-11-19
I went with the recommended nVidia 177 driver too and though it works it's not as good as before the upgrade.  I get some jittery movement when watching hi-def programming particularly when the camera is scanning across a room for example.  I am using the "slim" configuration just like I had previously.  I may go back and try some other driver(s) when I get a chance.

---

### Post by dmfrey on 2008-11-19
Before you do that, be sure that XvMC is enabled for your NVIDIA card and try some of the other recording profiles.  My HD content looks great in cpu-- profile where it is attempting to offload as much as possible to the NVIDIA card.  You can find out how to do this on the MythTV Wiki for both XvMC and Playback Profiles.

---

### Post by jMon54 on 2008-11-19
Thanks for the tip.  I thought XvMC was enabled by default in the slim profile but I will double check to make sure.  That would definitely make a difference!

---

### Post by dmfrey on 2008-11-19
Also, by default, the NVIDIA XvMC is not enabled.  All you need to do is update /etc/X11/XvMCConfig to use libXvMCNVIDIA_dynamic.so.1.

See [http://www.mythtv.org/wiki/index.php/XvMC](http://www.mythtv.org/wiki/index.php/XvMC) for more details.  

I recently did this on my upgraded and it improved the video greatly.

I am also going to update my playback profiles to be more like the defaults listed on [http://www.mythtv.org/wiki/index.php/Playback_profiles](http://www.mythtv.org/wiki/index.php/Playback_profiles), since i noticed mine were no longer like the default values.

---

### Post by jMon54 on 2008-11-19
Thanks tons for the info on configuring my nVidia 6200 card.  What puzzles me though is my system was working nearly flawlessly before I upgraded to 8.10 from 8.04.  And I don't recall having done all of this tweaking.  All I did was choose the slim profile and it just worked.

---

### Post by dmfrey on 2008-11-19
Ah...the woes of an upgrade.  Mine was working fine as well, aside from a few issues with my remote control.  But I gave it a go anyway with the upgrade hoping that all the latest bug fixes, etc. would make it even better :)

I am actually going to have to go through this whole thing again because i want to put a larger hard drive in that box.  I am still trying to determine what needs to be backed up.  Obviously, the db needs to be backed up to some location I can access after the upgrade.  However, I don't necessarily want to retain everything other than my recording schedules and history.  I have no issue going back in and setting up the cards all over again and my videos and music are stored on a server and mounted through nfs.  Then there is the recordings, they should be accessible from my drive if i mount it in a usb external enclosure.  

My ideal solution would be to store the db on my server, store the recordings on there as well (it has a raid-mirror configuration so I am somewhat isolated to drive failures :) ).  However, this doesn't necessarily work if I want to throw some more frontends around the house and set them up in the same manner.  At some point I am going to go the LinuxMCE route, but its version of Myth and the underlying Kubuntu is too old for some of my hardware.  It would be nice if they got LinuxMCE up to Kubuntu 8.10.

I am glad everything worked out for you.  Good luck with the rest of it.

---

### Post by jMon54 on 2008-11-20
Well I got my XvMC working on my nVidia 6200... Thanks!  Only prolbem is I had previously downgraded the driver and now have the dreaded stuttering while the OSD is up but that's no biggie and I plan on upgrading the driver tonight to see if that cures it.

Another problem I got after my upgrade was I lost the ability to VNC into the box.  I was able to do so before and see exactly what I would see if I were sitting in front of the monitor.  I have reconfigured VNC several times in the Mythbuntu setup but still no joy.

---

### Post by dmfrey on 2008-11-20
Do you see anything in the logs?  What about the Xorg logs?

I don't use VNC as my office sits at the back of my entertainment center and, if you look at it at just the right level, my hdtv becomes a third screen in my dual monitor setup at my desk :)

I did use this a while back and I thought I had to go in an manually configure the password for vnc.

I would do a google search to see if others have had issues with vnc, nvidia, and xvmc.

---

