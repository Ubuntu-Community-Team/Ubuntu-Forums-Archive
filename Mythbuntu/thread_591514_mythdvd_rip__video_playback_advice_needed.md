---
title: "mythdvd rip / video playback advice needed"
date: 2007-10-25
forum: Mythbuntu
---

### Post by andy-roo on 2007-10-25
Hi all, I've been ripping dvds for about a week now since I've installed and upgraded to 7.10.  I noticed on some anamorphic 2.35:1 discs that after ripping they are stretched vertically during playback on a 4:3 lcd monitor.  I've observed that the rip resolution is 720x480 with the dvd built in black bars and when I manually open it in vlc and set it's aspect ratio to 16:9 the proportions are correct again.  I've read man pages on mplayer to try and change the aspect ratio for the frontend gui playback but that yielded no results.

1) So, I was wondering how do you all deal with movies in different aspect ratios?

Another thing I noticed was ripping 6ch audio tracks doesn't work out too well.  Pl ayback of 6ch results in dialogue being excessively quiet.  I normally just go with the 2ch tracks but on some discs there is only 6ch.

2) I was wondering  if there is a way to get mplayer to mix 6ch into 2ch during playback?  Alternatively, how to configure the transcoder to mix 6ch into 2ch during ripping?

3) Is there any way to edit the ripping profiles (Excellent, Good, med, etc) in MythDVD?
I'm assuming there isn't since it is in the mythtv wiki feature wishlist.
[http://www.mythtv.org/wiki/index.php/Feature_Wishlist_%28Plugin_Addons%29#MythDVD](http://www.mythtv.org/wiki/index.php/Feature_Wishlist_%28Plugin_Addons%29#MythDVD)

----------------
In case you were curious about my hardware...

To my surprise all the hardware works, as drivers used to hard to come by in my previous linux installs.  I haven't tried burning any disks yet though, gulp... All I've had to do is tweak prefs, install fusesmb, and change fstab to mount my external hd.

My installation:
Mythbuntu 7.10 on an old Dell Precision 330 Workstation
P4 1.4
512mb PC800
Nvidia Quadro 4 700xgl (the darn thing doesn't have svideo and will be replaced by an old GeForce 3 soon)
Sound Fusion something...? (heck it works)
Dlink DWL-520 (the thing never even worked in windows but works in linux)
Some generic 100base eth NIC
16x DVD RW
48x CD RW
WD Caviar 120gb
Seagate 400gb external usb2 (the motherboard is usb1 which makes me want to cry during large transfers)
Plan on a PVR-150 or 500.  Probably the 150 since I'm cheap.

---

### Post by gumperoncini on 2007-10-31
are you sure they are ripped incorrectly? try hitting w on your keyboard during playback, this should cycle through different aspect ratios until you find one that fits your hardware.

---

### Post by andy-roo on 2007-11-02
Yeah I've tried hitting "w" during playback but all it does is zoom in and does not change the aspect ratio.  Although, that is in mplayer, so maybe I'll try getting mythfrontend to use a different player...  When you are referring to the "w" keystroke are you running the internal DVD player?

I'm still trying to figure out the sound problem.  Can anyone tell me how they rip DVDs with 6ch audio for 2ch playback?

Thanks for the reply.  I thought the post was fade away.

---

