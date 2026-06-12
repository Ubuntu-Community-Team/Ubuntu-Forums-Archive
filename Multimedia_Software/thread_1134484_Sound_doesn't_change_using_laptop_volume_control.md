---
title: "Sound doesn't change using laptop volume control"
date: 2009-04-23
forum: Multimedia Software
---

### Post by JA518 on 2009-04-23
I recently updated 9.04 and realized my laptop's volume wheel no longer controls my laptops volume. If I spin the wheel, the notification with the speaker appears and it will change the image (from mute to sound to max, etc), but the actually volume doesn't change at all. The only way I can change the sound is if I click the speaker button on my panel and slide it with my mouse.

Anybody know how to fix this?

---

### Post by JA518 on 2009-04-24
Anyone?

---

### Post by m_2009 on 2009-04-24
In order to help you I will need you to tell me which device and track the volume contrl is using (the one u use with your mouse by clicking)

TO do this, right click on the volume control speaker and then click preferences....

Then tell me What the device listed is showing as (The one that is already listed in the drop down list.

And then in the next bit down which one is selected as the track, so for example in the screenshot of mine i have attached my device is Intel ICH6 (ALSA mixer) and the track is Master Control.

---

### Post by JA518 on 2009-04-25
Device:HDA Intel (Alsa Mixer)
Track:Master Control

---

### Post by m_2009 on 2009-04-25
Ok. so what you need to do now is the following..

go to SYSTEM > PREFERENCES > SOUND

Make sure you are in the tab which is labeled Devices.

At the bottom you should see a section called "Default Mixer Tracks"

You need to match these up with the device/track you found in the main volume control preferences.
Click the "Device" drop down menu list and select "HDA Intel (Alsa Mixer)

Then in the box underneath click on "Master"

The volume control on the laptop should now be working.

Let me know if that helps.

---

### Post by JA518 on 2009-04-25
Thanks for helping me so quickly. I am in the middle of exams and this has been driving me nuts. I really appreciate it. m(_ _)m

---

### Post by deepnum09 on 2009-04-28
thanks a lot. i had the same problem. that fixed it though! my problem had been lingering from 8.10 but i never got around to fixing it. muito obrigado

---

### Post by alkamid on 2009-04-29
Same problem here (on 8.10, it's been annoying me since last update of software). Thank you very much m_2009!

---

### Post by Hilko on 2009-05-08
Thanks a lot m_2009 !!! Thanks thanks thanks !

---

### Post by Shekibobo on 2009-05-11
Huge help! I've been stressing about this for a week.

---

### Post by CooksWithFire on 2009-05-18
The volume control icon next to the date in the top task bar does not control my spdif output. Does anyone have any idea what I can do?
Thanks, Joe

---

