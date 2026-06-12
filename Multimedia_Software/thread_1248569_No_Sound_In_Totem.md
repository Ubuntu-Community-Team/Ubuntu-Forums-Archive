---
title: "No Sound In Totem"
date: 2009-08-24
forum: Multimedia Software
---

### Post by spikoley on 2009-08-24
I have no sound in Totem, but I do have sound with every other application I tested.  Recently, I fixed the sound for flash with this [guide]("http://ubuntuforums.org/showpost.php?p=7205818&postcount=6") and I believe that killed the sound for Totem.  I am guessing that I just need to change the source where Totem gets its sound from.  Anybody know where that is at or have another idea?

---

### Post by starcraft.man on 2009-08-24
> **spikoley said:**
> I have no sound in Totem, but I do have sound with every other application I tested.  Recently, I fixed the sound for flash with this [guide]("http://ubuntuforums.org/showpost.php?p=7205818&postcount=6") and I believe that killed the sound for Totem.  I am guessing that I just need to change the source where Totem gets its sound from.  Anybody know where that is at or have another idea?

Totem uses the gstreamer backend, which has it's own configuration app.

Open a terminal or run dialog (alt + f2) and then type in and run:

```
gstreamer-properties
```

Configure as ya like.

---

### Post by spikoley on 2009-08-24
> **starcraft.man said:**
> Totem uses the gstreamer backend, which has it's own configuration app.

Open a terminal or run dialog (alt + f2) and then type in and run:

```
gstreamer-properties
```

Configure as ya like.

Thanks for the reply.  I switched it but it didn't work.  The test button gives me the tone, but still no sound.  Any other ideas?  I am trying to get it to work through a USB headset.

---

### Post by starcraft.man on 2009-08-24
> **spikoley said:**
> Thanks for the reply.  I switched it but it didn't work.  The test button gives me the tone, but still no sound.  Any other ideas?  I am trying to get it to work through a USB headset.

Oh going through front panel out eh? Gets finicky when trying to do headests and mic. Go to volume control panel, go preferences and add in all the microphone ones related to playback. Make sure they are all set to maximum and not muted. Really takes trial and error. Volume panel is one ya get by right clicking the sound icon then going to control panel.

---

### Post by tictacman on 2009-08-24
Are you able to hear sound from any other application such as rhythmbox?

I have a similar problem with totem on my toshiba laptop using front jacks. Volume buttons are greyed on totem and there's no sound.  Sound work fine in rhythmbox and skype.

Looks like the problem was to do with altering the sound settings in in system > preferences > sound

I changed music & movies and sound events playback to pulse audio restarted totem and lo there was sound.

---

### Post by spikoley on 2009-08-24
> **tictacman said:**
> Are you able to hear sound from any other application such as rhythmbox?

I have a similar problem with totem on my toshiba laptop using front jacks. Volume buttons are greyed on totem and there's no sound.  Sound work fine in rhythmbox and skype.

Looks like the problem was to do with altering the sound settings in in system > preferences > sound

I changed music & movies and sound events playback to pulse audio restarted totem and lo there was sound.

No dice.

> **starcraft.man said:**
> Oh going through front panel out eh? Gets finicky when trying to do headests and mic. Go to volume control panel, go preferences and add in all the microphone ones related to playback. Make sure they are all set to maximum and not muted. Really takes trial and error. Volume panel is one ya get by right clicking the sound icon then going to control panel.

I played around with the settings and could not get it to work.  I have the device set to Playback: USB Device 0x47f:0xad01 - USB Audio (PulseAudio Mixer).  The only option that shows up is Master.  Everything under System> Preferences> Sound are set to PulseAudio Sound Server.  I am not sure what else to try.

Sound works everywhere else, but not in Totem.  It makes me think this is Totem related.

---

### Post by spikoley on 2009-08-24
Got it working!!!  


```
sudo apt-get install padevchooser
```

1.  Open Totem
2.  Alt + F2 and enter padevchooser to open PulseAudio Device Chooser utility
3.  Left click on the system tray icon
4.  Volume Control
5.  Playback tab
6.  Click the down arrow for Totem
7.  Move Stream
8.  Select USB Audio and it worked!

---

### Post by starcraft.man on 2009-08-24
> **spikoley said:**
> Got it working!!!  


1.  Open Totem
2.  Alt + F2 and enter gstreamer-properties to open PulseAudio Device Chooser utility
3.  Left click on the system tray icon
4.  Volume Control
5.  Playback tab
6.  Click the down arrow for Totem
7.  Move Stream
8.  Select USB Audio and it worked!

Like I said, fiddle with audio long enough and it works. I'm glad :)

---

