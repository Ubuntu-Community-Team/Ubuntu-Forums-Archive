---
title: "No Sound Coming From Amarok"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by 5thape on 2007-05-18
Hello everyone, I'm very new to Linux (just installed yesterday).  I want to get Amarok to play my mp3's but for some reason it won't.  I've followed all the documentation and installed the appropriate packages but Amarok "plays" the songs, as in I see the bars move but no sound comes out.  I CAN play mp3's in Totem Movie Player though.  I don't know if this makes any difference but VLC Media Player will open my video files and play the video but no sound comes out either but everything works in Totem as well.  Thanks!

---

### Post by hardyn on 2007-05-18
install the libxine-extracodecs though synaptic.

cheers.

---

### Post by 5thape on 2007-05-18
I just did that but still no sound :(

---

### Post by dabl on 2007-05-18
Open Amarok (but don't play anything), right click the little speaker icon in the upper right corner of your desktop, choose "Edit Preferences", and then start turning off "modules" or whatever the components are, and each time you turn one off, give Amarok a try.  If you get to where they're all turned off, start turning them back on, beginning with "front", and "pcm", and so forth.

p.s. make sure "mute" is off too!  :)

---

### Post by 5thape on 2007-05-18
I tried that and it didn't work.  I use a Chaintech AV-710 sound card when I opened up the Volume Control Preferences it was set to an ATI IXP (Alsa Mixer), should I change it to the Chaintech AV-710 (Alsa Mixer)?  Also after I installed Ubuntu I had no sound but I figured out that it was because I had to change all the Sound Preferences to ICE1724 from Autodetect.  But in Volume Control Preferences there is no ICE1724 option only the Chaintech and ATI.

---

### Post by dabl on 2007-05-18
Is there an integrated sound circuit on your motherboard -- is it turned off in BIOS?

Also, in Amarok, did you go to the "Configure Amarok" menu and make sure the "engine" that is selected makes some sense, vs. what you see in the mixer?

Yes, you're going to have to play around with the Chaintech as the ALSA and/or OSS output device -- one of those combinations should work.  Takes a while to run through all the combinations ...

---

### Post by [xteam] on 2007-05-19
> **dabl said:**
>  right click the little speaker icon in the upper right corner of your desktop,
What is this icon?

---

### Post by doruktuna on 2007-06-22
Hi, I am also very new to linux and I was having the same problem. (No sound in Amarok, but there was with Totem Movie Player and Rhytmbox)

So after searching for a while I thought that maybe Amarok is using the default sound card, so I changed the default sound card as described in [[COLOR="DarkOrange"]here[/COLOR]]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

In a terminal type: sudo asoundconf list
If you have more than one sound card, you should see several entries (You need to know which card produces sound. If you don't know then try the next step for all the entries)

Now type this in a terminal: sudo asoundconf set-default-card ENTER_NAME_OF_CARD_HERE
Example:
...~$ sudo asoundconf list
Names of available sound cards:
nForce2
UART
Live
...~$ sudo asoundconf set-default-card Live

Now when I run alsamixer it shows my Sound Blaster Live Card (before then it was showing on board card) and sound is now working for both Amarok and other applications. Hope it works for you too.

---

