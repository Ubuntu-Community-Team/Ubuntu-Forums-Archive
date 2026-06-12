---
title: "Sound disappeared from Mplayer, Amarok, Rhythmbox, but works in Firefox"
date: 2010-09-21
forum: Multimedia Software
---

### Post by AlexOslo on 2010-09-21
I am uncertain what could have caused these players, Movie player, Amarok and Rhythmbox to lose their sound output. You can see them playing, but no sound comes out.
Sound works fine in Firefox (YouTube, Flash etc), however.
Any advice would be appreciated on how one might get it back!

---

### Post by AlexOslo on 2010-09-22
Wondering what kind of solution there might be for this problem.

---

### Post by lee13se on 2010-09-22
I am having the same problem.

First I lost sound completely, I changed a setting in Sound Preference and regained sound on VLC and Rhythmbox but not Flash or Adobe Air.  I reinstalled Flash and now have sound on Flash and Adobe Air, but not VLC, Rhythmbox, Ubuntu System Testing, or Movie Player.

I am using 10.04 64-bit.

---

### Post by AlexOslo on 2010-09-25
I wonder if anyone knows what could have cause this!

---

### Post by lee13se on 2010-10-09
I just upgraded to 10.10 (Maverick Meerkat) Release Candidate and my sound is working again.  I would suggest upgrading after the final release tomorrow (Oct 10th) and see if that resolves your issue.

---

### Post by P4man on 2010-10-09
I would advice against a distro upgrade to solve what could be a trivial issue. 10.10 might cause bigger problems and there is no way back. I always test a new distro from a livecd before committing.

Anyway, back to the sound issue. If you go in the sound preferences and application tab, do you see the apps (if they should be playing sound) ? Make sure they not muted.

If that doesnt help, try this:

```
sudo apt-get install paman
```

Then go to applications > sound and video > pulseaudio volume control 
This app should be part of a default install IMHO.  Make sure the streams are played on the correct audio card, and not for instance, to your HDMI.

---

### Post by vsperez on 2010-10-16
I don't know if it will help you...any way...For a while I lost sound in Amarok, but I could use other applications. Today I was searching for similar problems and I end here.Well, playing with the configuration, I found that changing to pulseaudio to  top of the list in "system->preference->system settings" on multimedia menu, audio output,  music, Amarok sounds again.

Regards.

---

