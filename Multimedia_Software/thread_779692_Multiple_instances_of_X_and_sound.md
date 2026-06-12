---
title: "Multiple instances of X and sound"
date: 2008-05-02
forum: Multimedia Software
---

### Post by mb12345 on 2008-05-02
I'm using kubuntu 7.10 and here's my dilemma.  I have two instances of X (kde) running concurrently.  The first instance (:0) is my primary desktop, where I work.    Then on virtual terminal 2 (ctrl-alt-f2/f9) I run a 2nd instance of X (:1) that runs a MythTV frontend.  

My issue is that after I've switched over to MythTV and watched a show, I no longer get audio in my primary X session.  I rarely use audio on my primary instance except for things like YouTube, so what I'm looking for is some method to reset the sound system such that my primary instance of X (and thus KDE 3.5) can use the sound, but without locking the card such that my MythTV setup cannot use it (it's more important for Myth to have immediate access to the card).  Prior to using MythTV after a reboot, my primary instance's sound works fine.  And MythTV has never had any trouble grabbing the sound card for playing back shows.  

Does anyone have any suggestions along these lines?  I'm happy to post any additional information that might be helpful in figuring this out.

Thanks!

Mike

---

### Post by Teloid on 2008-05-03
What sound system you are use? And did you enable sound mixering? Look at System->Prefernces->Sound and System->Preferences->Sound system.

---

### Post by Zorael on 2008-05-03
You could strive towards getting pulseaudio running to get userspace sound. So, if you play X in :0 and Y in :1, changing between them also changes whatever's playing in your speakers.

---

### Post by mb12345 on 2008-05-03
> What sound system you are use? And did you enable sound mixering? Look at 
> System->Prefernces->Sound and System->Preferences->Sound system

Well, I don't exactly have that menu directory structure you listed.  But I do have System Settings / Sound System, in which I am running Alsa in both KDE sesions on :0 and :1.  Both have the exact same settings in Audio.  I don't see any options for "sound mixering."  I attached screenshots of the sound preferences screens (forgive the poor quality -- size limits of the forum).

---

### Post by mb12345 on 2008-05-03
Pulse Audio looks like an intriguing option.  Right now, I'm looking for a quicker solution than figuring out how to get a new daemon working with both my setups, but I'll definitely keep it in mind for the future.  Thanks for the suggestion!

---

### Post by Teloid on 2008-05-04
I have non-english version, therefore I tried to translate menu items names. My bad - I'm using Gnome, not KDE, Gnome path invalid for you.

---

