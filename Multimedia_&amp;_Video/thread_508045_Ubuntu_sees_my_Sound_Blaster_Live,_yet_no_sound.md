---
title: "Ubuntu sees my Sound Blaster Live, yet no sound"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by kag on 2007-07-23
The sound used to work, I must have changed something in my configuration. Perhaps when I installed the "sensor temperature monitoring with lm-sensors" or something.

When I open the volume control, and move PCM and Master all the way up, I can hear in my headphones the volume is being raised: I hear more "hiss".

When I go in System -> Preferences -> Sound, and I press "Test" next to "Sound playback", I see a popup and I don't hear anything. But when I change the dropdown from "Autodetect" to "Multichannel Playback" and I press "Test" again, I hear a beep sound. When I play with the volume control while that beep sound is playing, it plays louder/softer.

But when I open regular applications that are supposed to play sounds, I don't hear anything at all.

Any ideas?

---

### Post by fredj on 2007-07-24
Open the alsa mixer (double click on the speaker icon in the taskbar. Check the File->Change Device Menu
and make sure that the correct device is selected. Then use the Edit->Preferences Menu and add all the
possible volume control and switches (for both record and playback). Make sure that suitable volume levels
are set and the all the controls are unmuted.

---

### Post by NoSmokingBandit on 2007-08-07
i have the some problem. I opened the mixer and enabled every slider. I played a song in Rhythmbox and adjusted every slider up but heard nothing. I am stuck using my crappy integrated sound now, so i really want my sound blaster to work.

---

### Post by NoSmokingBandit on 2007-08-08
OOOO! Mine works now. In the alsa mixer, set the device to your soundblaster card, then reboot. You may only need to log out and back in, but i rebooted into xp for a minute, and when i came back i had no sound, so i checked the mixer and saw it was on my sound blaster card, so i switched my plug and now it works.

Edit:
Never mind, that doesnt work. It only plays cd's that way. Rhythmbox still can be heard.

---

### Post by kag on 2007-09-10
I still have the problem. All the sliders are all the way up in the Alsa mixer for my SBLive.

The weird thing is that I can hear sound from Totem Movie Player, but not from VLC or Rhythmbox. Firefox doesn't play sound (from a Flash movie) either.

In Skype, it works only if I select "SBLive! Value [CT4832] (hw: Live, 0)". I don't know if it can help.

---

