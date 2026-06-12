---
title: "Sound Not Getting Through Mixer for TV"
date: 2008-03-10
forum: Mythbuntu
---

### Post by johnelle on 2008-03-10
I am trying to set-up a new 7.10 system.  I have sound coming out the ATI TV Wonder Card (I plugged the speaker in directly).  I can play audio cds so I know that the basic sound is working.  When I watch live tv the sound is dead.  I have it turned up to 90% on the controls.  I brought up the ALSA text mixer and near as I can tell line-in is enabled.  I tried an update and that didn't help anything.  Sound chip is a CMI 8738.

Any suggestions on debugging steps?  I get the feeling this is a simple problem but I can't even find a GUI sound mixer on this setup.

John:confused:

---

### Post by milton1 on 2008-03-10
This may be a driver bug; I seem to recall reading that the ati all-in-wonder cards had difficulty with mythTV. You might try searching for mythTV issues/fixes for your card. Sorry I can't be of more help.

---

### Post by johnelle on 2008-03-10
Its a TV Wonder card.  They actually work with MythTV.  The video is working fine.  The Sound is coming in on an external jumper from the Sound Out to the Line-In on the sound card so it would be somewhere in the sound system.

---

### Post by rickyble on 2008-03-10
sorry wrong thread post

---

### Post by johnelle on 2008-03-10
Additional Info.

I can go to amixer through the terminal and if I can turn line "on" which gets the sound coming out but the sound always comes out no  matter where I am in mythtv and the volume can only be controlled by the amixer.  Its as if the Myth controls are not linked to the system mixer.  Is there some hidden setting to control line-in from Myth that I missed?

---

### Post by Al_Vampyre on 2008-03-10
I'm having a similar problem after updating this morning, I now have no sound in LiveTV and volume controls/mute button do not function or produce an on screen display although the IR receiver for my Microsoft MCE remote (Phillips) does flash to register the key press. The default Vol Up/Down on the keyboard also do not function or produce the corresponding OSD.

This is on Alpha 3 and MythTV 0.21

---

### Post by johnelle on 2008-03-11
I thought I could fix it by going through the Sound Config section of the install HOW TO and setting the mixer up manually.  This didn't help on MythBuntu but I didn't know the root password so I couldn't save the settings.  When I tried this on Mythdora4 it solved the same problem there.  

If you know the root password for the box I would recommend trying the commands in Section 7 of the install how to.

---

### Post by Al_Vampyre on 2008-03-11
Mine seems to be sorted now after whatever updates went through today :)

---

### Post by ppeetteerr on 2008-05-26
I'm having this same problem.  What did you guys do to fix it?  What's page 7 in sound setup?

---

