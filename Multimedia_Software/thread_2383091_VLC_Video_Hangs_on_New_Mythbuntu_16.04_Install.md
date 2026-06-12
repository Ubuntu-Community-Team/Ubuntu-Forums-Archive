---
title: "VLC Video Hangs on New Mythbuntu 16.04 Install"
date: 2018-01-20
forum: Multimedia Software
---

### Post by jamoody on 2018-01-20
I installed Mythbuntu 16.04 on spanking new hardware.  The system comes up and I can start playing video via VLC but have 2 key problems:
* there is no sound across HDMI or the front/rear panel headphone jacks
* after a few (4-6) mins the video locks up.  VLC time stamp and progress bar progress all the way to the end so I think the video is playing but the screen isn't updating.  The mouse moves but selecting anything on the desktop causes Xorg to go to 100% for several mins

My hardware is 
* ASRock Z270 Extreme 4 motherboard
* EVGA GeForce GTX 1050 graphics card
I'm using the graphics card HDMI 2.0 output.

Software levels are up to date as of today:
       Ubuntu    16.04.3
        Mythtv    0.28-2
        nVidia    384.111
        kernel    4.13.0-26

I haven't done the MythTV setup yet as I figure VLC is a simpler test bed.

Anybody have any ideas on either issue?

---

### Post by jamoody on 2018-01-25
I solved the lack of sound issue via pavucontrol.  See [https://ubuntuforums.org/showthread.php?t=2383318](https://ubuntuforums.org/showthread.php?t=2383318)

I still have the video hang condition.  The audio continues so it is a video only problem.  Any ideas where I should look for hints?

---

### Post by Autodave on 2018-01-25
Have you installed any driver for the video card? If so, where did you get it from?

If you have not installed one yet, go to Settings -> Additional Drivers and chose the recommended one to star with. Reboot and report back! :-)

---

### Post by jamoody on 2018-01-25
I'm running Nvidia driver 384.111 which seems to be the latest available.  

But I have made some progress.  I used Nvidia X Server Settings to change the resolution from Auto to 1920x1080 and that seems to have helped.  Instead of locking up the VLC video within 4-6 mins, I'm now able to play an hour long video with the new resolution.  More testing to go, but it's a good step forward.

I'm using a 4K TV and unsure if 1920x1080 is the best resolution to use or not.  Menu pull down text is much too small to be readable.  This is a dedicated MythTV setup for TV broadcast viewing only over HDMI 2, no gaming, no DVD.  Any input on what resolution to use would be appreciated.  Perhaps I can increase the menu font somehow.

The next problem is trying to figure out how to preserve the resolution setting over reboot.  In Nvidia X Server Settings I selected Save to Configuration File and it wrote a new /etc/X11/xorg.conf but the resolution reverts back to the Auto setting after reboot.  Will start researching that tonight.

---

### Post by jamoody on 2018-01-25
I tried the following to preserve nvidia-settings values across a reboot.  Clicking on Save in nvidia-settings updated  /etc/X11/xorg.conf with the selected configuration options
            Option         "metamodes" "3840x2160_60 +0+0"

~/.nvidia-settings-rc was also updated but I don't see the selected resolution in there.  

 ~/.xinitrc didn't exist so I created it as follows:
      nvidia-settings --load-config-only &
      . /etc/X11/xinit/xinitrc

After reboot the original settings persisted.  Any ideas?

After reboot the resolution was back to Auto.  Do you have any other thoughts?

---

### Post by jamoody on 2018-01-25
Manually running 
     nvidia-settings --load-config-only
doesn't seem to change the resolution so my guess is ~/.nvidia-settings-rc doesn't have the desired resolution in it.

---

### Post by jamoody on 2018-01-28
The original VLC video hang is resolved after changing Nvidia X Server Settings resolution from Auto to 1920x1080 as reported above.  I'll open a new problem for nvidia-settings not persistent across reboot even after trying the directions in man nvidia-settings regarding saving across reboot.

---

