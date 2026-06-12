---
title: "system volume problem"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by le_vainqueur on 2006-12-12
I'm having a problem with my system volume.  Actually I have a couple of sound-related problems

1. Ubuntu isn't consistent in which sound device it recognizes.  Sometimes it chooses the chipset, but other times it choses the sound card.  This problems seems to have worked itself out the past week or so.  It has consistently picked the sound card.  I'm really posting this just in case it has an effect on problem #2.

2. This is the real reason for my post.  My system volume seems to have no effect on the volume of whatever program I'm using.  The system can be completely muted, and the same volume level comes out.  The individual program volume controls work fine.  If I'm in a media player, I can decrease the volume within that program without a problem.  

Any tips?

---

### Post by neemz on 2006-12-12
Chances are that is always detects both but only displays one on the volume control.

Try this

Right click the little speaker icon in the taskbar
Then click on Preferences

You may be given the option to chose from more then one device, select the other and you may have the ability to adjust the volume :)

---

### Post by Zelut on 2006-12-12
Do you have an option to disable one of the devices in the BIOS?  I had a similar problem a while ago and ended up disabling the onboard audio in the BIOS.  This way there is only one card to work with and you avoid any conflicts.

---

### Post by le_vainqueur on 2006-12-12
> You may be given the option to chose from more then one device, select the other and you may have the ability to adjust the volume 

OK, I have three devices listed in my audio preferences.  They are:

Intel 82801DB-ICH4 (Alsa Mixer)
Ensoniq AudioPCI (Alsa Mixer)
Analog Devices AD1981B (OSS Mixer)

I'm guessing the Intel one is my chipset, and the AdioPCI one is my sound card (Sound Blaster).  I selected each of them, and sound comes through my sound card for all of them, and my chipset for none of them...weird.  

I then went into sound preferences and clicked varios drop-down menues for sound devices.  Each of them had six or so selections.  Here the sound would no longer work if I selected the Intel option.  They system volume in the tray worked in test mode for each, but the keyboard option didn't.  They keyboard volume control would show up as if it were effecting the sound, but it was no longer the same volume as that displayed in the system tray.  Until now they have always been the same.

> Do you have an option to disable one of the devices in the BIOS? I had a similar problem a while ago and ended up disabling the onboard audio in the BIOS. This way there is only one card to work with and you avoid any conflicts.

I went into BIOS, and found no option to disable a specific device.  The only audio option I found was had only "enable" and "disable" as selections with no mention of either device.  Where did you find the option to disable just one?

---

### Post by neemz on 2006-12-12
Interestingly I have a similar problem to you, by changing arround which device the volume control works I can alter the volume, but my keyboard volume control affects something else.

(The volume slider effects most of my programs but some others only listen to my keyboard volume controls!)

---

### Post by Zelut on 2006-12-12
the BIOS most likely only is aware of the onboard audio.  If you disable that it should take the Intel out of the picture.  Give it a try & see if it helps.. you can always turn it back on :)

---

### Post by le_vainqueur on 2006-12-12
> the BIOS most likely only is aware of the onboard audio. If you disable that it should take the Intel out of the picture. Give it a try & see if it helps.. you can always turn it back on 

Brilliant...it works perfectly.  Thanks for the help!

> Interestingly I have a similar problem to you, by changing arround which device the volume control works I can alter the volume, but my keyboard volume control affects something else.

(The volume slider effects most of my programs but some others only listen to my keyboard volume controls!)

I fixed this problem.  Here is what was wrong for me.  In my system volume preferences I accidentally changed what the volume icon was controling.  Go back into your system volume, and make sure your selected device is the one you want.  Then highlight master in the box below.

---

### Post by NJC on 2007-11-15
> **le_vainqueur said:**
> I fixed this problem.  Here is what was wrong for me.  In my system volume preferences I accidentally changed what the volume icon was controling.  Go back into your system volume, and make sure your selected device is the one you want.  Then highlight master in the box below.

THANKS #142 for the Ubuntu forum users! I've been [censored] around with sound for awhile in Gutsy with an Ensoniq ... I was finally able to get Audacity 1.3.3 working properly from the mic but erroneously killed my keyboard volume. 

Ensuring "Master" was selected under Default Mixer Tracks (System/Preferences/Sound) fixed the problem.

---

