---
title: "Sound stopped working yesterday"
date: 2008-11-30
forum: Multimedia Software
---

### Post by utherpendragonfly on 2008-11-30
I've been using Ubuntu for about six weeks, and I've had no problems until yesterday when after a reboot my sound didn't work. The panel volume control was muted, and I unmuted it and can't get any sound. Also after the reboot there was a error message about timevault which I didn't understand. I rebooted again and the sound control was muted again. I decided to uninstall TimeVault, hoping that was the problem, but no luck. Since then I have checked out the Comprehensive Sound Problem Solutions Guide v0.5e on this forum. My sound card shows up when I enter (aplay -l) in terminal:

(davey@davey-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0)

and I uninstalled & then reinstalled alsa using:
(sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils)
and restarted and still no sound. Everything in sound preferences looks like it should be enabled & working, but nothing has helped. I even tried using other speakers. Does anyone have another suggestion, besides reinstalling Ubuntu?

Ubuntu 8.10
Asus A8N-SLI Deluxe - Bios Ver. 5.1.39
Processor: AMD Athlon 3500+  2.2 Ghz.
RAM: PC 3200  2 GB
Video: (Winfast) Nvidea Gforce PX6800 TDH 256 Mb

---

### Post by Good_Newz on 2008-11-30
Same problem here. There was a kernel update and after restart no sound! I am thinking it has to do something with that. I tried resetup on pulse no luck.

---

### Post by Good_Newz on 2008-11-30
Ok i was able to fix it...not sure exactly what did it but this is what i did:

1.Follow this guide [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) - this worked last time but it didnt work this time...but follow it anyway
2.Install asoundconf-gtk, libao-pulse, vlc-plugin-pulse(i dont think you need the last one i included it couse i use vlc)
3.After install go to System->Preference->default sound card and make sure pulse is selected.Quit
4.goto System->administration->users and groups and click manage groups. For each of the following groups pulse, pulse-access,pulse-rt add yourself and root to the group. (very important to include root as well, i think thats what did it for me) 
5. Restart!

Good Luck

---

### Post by alwayshere on 2008-11-30
yes welcome to ubuntu 8.10 crazy world of sound troubles i to have had alot of sound troubles it seems a random hard to come and easy to go thing ,i still dont have sound everywhere i want it but i got it most places so im not gona touch it till something gets done about this sound madness .iv put alot of hours into getting my sound going and have no idea what iv done to get it to work one thing works one time and not the next ???

all i can say is keep at it ,or go back to a version that worked

---

### Post by markbuntu on 2008-11-30
I have made a new post for getting Intrepid sound set up properly now that I finally got it to work:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by utherpendragonfly on 2008-11-30
> **markbuntu said:**
> I have made a new post for getting Intrepid sound set up properly now that I finally got it to work:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
Wow! I have tried about 4 different ways that other people have used to get audio back, but none of them has worked for me. The more I read the more overwhelmed I have become with the complexity of this problem! I just don't have the time or knowledge to wade through all of this. Maybe if I wait for a few days or weeks(?) another software update might fix this? I don't think I have the patience. Can I possibly reinstall hardy without destroying all my files/music/bookmarks/email etc? I made a cd with APTonCD and a backup copy of my home folder. Is that sufficient if I have to wipe the HD and reinstall everything again? I'm just really frustrated and feel like getting a new HD for my 6 year old Mac G4 and going back to using that!

---

### Post by utherpendragonfly on 2008-12-01
Hello! I just found a new post this morning from Racer-X that suggested this:

Right-click on your speaker icon in the tray, select preferences. A window will pop up. Select your Alsa mixer; mine is: HDA Intel (Alsa Mixer). From there select PCM. If you look back up at your speaker icon, it should not be zeroed out. If it is, turn it up and you should have sound again.

...and my sound is back! I can't believe how simple that was!
Thanks for the advice everyone. Without these forums there is no way I would be able to use Ubuntu.

---

### Post by Dansaycool on 2008-12-01
I think I'm suffering from this problem/bu/error whatever it be! Installed some updates, restarted the computer and couldn't think for the life of me why my sound has stopped working?

My sound didn't stop completely though as it can play anything AC3 fine.. when you play a DVD through the optical out.. but can't hear anything played none AC3?

I tried the suggestions of this thread but still haven't got the bugger working?

& it was all working so well :(

---

