---
title: "Sound Blaster issues with microphone, other apps"
date: 2006-03-03
forum: Multimedia &amp; Video
---

### Post by Preserved Killick on 2006-03-03
Hi.  I'm having sound card headaches and I hope someone here can help.

I've got a sound blaster Live! 24 bit sound card installed.  When I run 'lspci' it's listed.  I'm running Breezy Bagder, btw.

I've followed the instructions on the Wiki for getting my card running with ALSA (advanced Linux Sound Something), but apparently that's not enough, as some applications are still using OSS, (older sound system).  

For example, when I click a panel item with Gnome, it makes a sound.  I can play an ogg vorbis file using Helix.

But Totem won't start, saying "The audio output is in use by another application.  Please select another audio output in the Multimedia Systems Selector.  You may want to consider using a sound server.  OK."

If I start BZFlag (a game), I get no audio UNLESS, I first use 'System > Preferences > Sound' and uncheck "Enable sound server startup", then start the game, waiting 10 seconds before touching any keys.   This may be superstitious behavior on my part, but I believe waiting allows BZFlag to grab control of sound.

When I try to use Gizmo (a VOIP program) I get sound out of my speakers but not through my headset, and I can't send sound through my headset mic.

When I go to 'System > Preferences > Multimedia Systems Selector' I see that my output is ALSA and my input is OSS, but neither can pass the "Test" button.  I'm a little shy of messing with these settings because I have sound running now in most applications.

Does anyone know what's going on here?  How can I get my headset/mic to work?

I'm willing to do other diagnostic things if that will help you to help me, but I'm not sure what to try.  My alsa-source is 1.0.10+1.0.11rc3-1.

Thanks,:) 

-- Damon

---

### Post by KansasJoe on 2006-03-03
I had a similar problem with alsamixer just going to my integrated card the comp came with so after trying a few things with no luck I went into my bios and turned off that sound card and all of a sudden my soundblaster live was the primary sound and worked with internet and games...may give this a shot and I use teamspeak so i found you have to go into alsamixer and turn on the mic boost (push m when u scroll over to mic boost selection)

---

### Post by Preserved Killick on 2006-03-03
Sorry, KansasJoe, but I'm not sure I understand what to do with alsamixer.  When I open the mixer the mic is the first item selected.  Pressing M seems to have no impact.  

I've not looked at the bios sound settings, but I'm reasonably sure my sound card is detected, in that I have sound sometimes, and the card I have shows up in the Sounds dialog.

So what do I do in alsamixer to get the mic working?

Thanks!

-- Damon

---

### Post by KansasJoe on 2006-03-03
when u go over with left arrow key it will say mic boost...when ur on that section push m...as far as the bios i had to turn off my integrated card....ubuntu still showed my soundblaster but i couldn't get it up on alsamixer because of my integrated (until i took it off in the bios)

---

### Post by Preserved Killick on 2006-03-03
Thanks, Joe.  I'll poke around in my BIOS tomorrow when I boot up and see what's what with sound.  I appreciate your help.  What will I see in alsamixer when I press 'm'?  At the moment nothing happens onscreen at all.

-- Damon

---

### Post by KansasJoe on 2006-03-03
on the alsamixer you can scroll left and right with the arrow keys...once you get on mic boost then push m - make sure the sound card you want to use is selected

---

### Post by Preserved Killick on 2006-03-04
Hi Joe.  This morning at boot I went into BIOS and disabled onboard sound (the soundblaster card is one I added, not the onboard card).

[QUOTE=KansasJoe]on the alsamixer you can scroll left and right with the arrow keys...once you get on mic boost then push m - make sure the sound card you want to use is selected[/QUOTE]

My alsamixer doesn't have a 'mic boost'.  I've got a column labeled <Mic/Line> and I can toggle it between [Line in] and [Mic in] using the up and down keys.  When I press 'm' I see no changes at all.

The second column is <IEC958> and above the label there is a box with MM inside.  If I press 'm' on this column, I get an infinity symbol.  I've googled alsamixer but I can't learn what this does.  I did learn that IEC958 is the name of an output spec, so I'm guessing it's not going to help with input issues, but that's a guess.

If pressing 'm' is toggling something, then I don't know which state I've left it in because there's no reflection on the alsamixer screen.

Are we running the same program?  I've got v1.0.9a.  I appreciate your help with this.

Thanks,

-- Damon

---

### Post by KansasJoe on 2006-03-04
I've got 1.09 as well....you need to open terminal and type in alsamixer (you may be doing it by clicking on sound which does not give you this option)...there are a lot of options so keep hitting the right arrow key til you get to the mic boost and push m when you're on mic boost....make sure the alsamixer is actually showing your soundblaster card and not another one

---

