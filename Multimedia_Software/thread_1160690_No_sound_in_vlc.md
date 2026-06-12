---
title: "No sound in vlc"
date: 2009-05-15
forum: Multimedia Software
---

### Post by mgtech on 2009-05-15
I am running Ubuntu 9.04 w/ all current updates and codec libraries.

I have and audigy sound card. In my system>pref.>sound> I have the audigy selected. It is in ALSA and performs the tests.

Audio plays fine in mplayer and not at all in vlc, regardless of if they are both running. In vlc tolls>pref.>audio> I have ALSA selected, but it isn't detecting the device, only allowing the selection of default. Audio has never worked for any file type in vlc. When I play a .avi file I can go in tools>media info.> the audio is running, but still no sound.

Feel free to ask q's.

---

### Post by michael37 on 2009-05-15
> **mgtech said:**
> I am running Ubuntu 9.04 w/ all current updates and codec libraries.

I have and audigy sound card. In my system>pref.>sound> I have the audigy selected. It is in ALSA and performs the tests.

Audio plays fine in mplayer and not at all in vlc, regardless of if they are both running. In vlc tolls>pref.>audio> I have ALSA selected, but it isn't detecting the device, only allowing the selection of default. Audio has never worked for any file type in vlc. When I play a .avi file I can go in tools>media info.> the audio is running, but still no sound.

Feel free to ask q's.

Start VLC

Open Settings/Preferences

Open Audio tree on the left panel

Open "Output modules" tree

Notice the blank panel on the right with a small "Advanced Options" checkbox on the bottom right.

Select it.

Now, select Audio Output Module: ALSA audio output

Select ALSA in the left panel.

Click on Refresh List.

You should see your devices in the drop down.  Under absolute majority of cases, leave the drop-down at "Default".

Click Save on the bottom left and enjoy sound in VLC.

---

### Post by mgtech on 2009-05-15
I seem to have found it, we'' see if it works. 1 sec.

Thnx a bunch for the help!!!!!!!

---

### Post by semano on 2009-11-04
Dear bro,
I have got similar problem like yours. I mean i can watch movie and listen to music with mplayer but cant hear any sound in vlc though the audio track moves on. 

Have you found any solution? If yes, I would really appreciate your suggestions through [email]shoman_bhuiyan@yahoo.com[/email].

regards,
semano

---

