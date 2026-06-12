---
title: "Creative soundblaster live! does not play core sounds"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by Catalyst2Death on 2007-10-31
Hello,
I've been able to resolve most of the problems on my new Ubuntu setup using the extensive information on these forums.  There is however one problem which I can't figure out.  I can play sound (through mp3) but I do not have system sounds (startup and shutdown) nor do I have sound in videos.  I also installed ubuntu on my laptop, and sound works all around out of the box.  I'm pretty sure that I don't need the win32codecs because if I did, sound wouldn't work on my laptop.  I want to avoid copyright/patent infringement, so installing the win32codecs is out of the question.  Sound worked sporadically in feisty, but it has been mute ever since gutsy.  I have my card set to Mixed channel playback in the sound settings for everything which is giving output.  Anyway, I've searched google up and down for a solution and I haven't been able to find one.  Its not a huge deal really, I just like to listen to radio streams, and I can't when the sound only works for mp3 files...

---

### Post by Catalyst2Death on 2007-11-01
bump/update  I tried a the onboard soundcard and the sound works for everything there (system sounds/videos/mp3s) so I think its a problem with  the ALSA platform.  Can I just uninstall/reinstall the ALSA platform with the synaptic manager to fix the problem?  My card (Sound Blaster Live! 5.1) is supported by ALSA, It just isn't functioning properly.  I also tried a channel by channel test for 5.1 using a PCM wav test, but it didn't work... it said which channel was playing, but no sound came out of my speakers...

---

### Post by Catalyst2Death on 2007-11-04
My sound issues continue to confound me.  I reached a point of desperation and decided to do a clean install of Gutsy (I had simply upgraded before)  while in the live CD I checked the sound, and it worked flawlessly, everything played back normally with no configuration.  I was very happy.  However, when I reinstalled and rebooted, I still have partial sound.  Again, there is sound output and I can play mp3's but thats it, no system sounds, and no sound in videos.  Any insight would be extremely helpful, I have no clue what to do.

---

### Post by RSVampire on 2007-11-04
I've also been having numerous sound problems in Gutsy.

[http://ubuntuforums.org/showthread.php?t=602210](http://ubuntuforums.org/showthread.php?t=602210)

that details my problems, but basically I install Gutsy... everything works... install updates... everything works still. Reboot the computer and still sound works.

Sound will just randomly STOP working all together on a random day and never work again. My sound card is detected correctly and there is no changes to the system between when the sound works and stops working.

My only solution was to completely purge remove the ALSA drivers or reinstall Gutsy altogether. I'm tierd of doing this because sometimes reinstalling the ALSA drivers don't work. So if anyone has a solution that would be great.

---

