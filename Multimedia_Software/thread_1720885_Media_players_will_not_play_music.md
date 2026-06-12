---
title: "Media players will not play music"
date: 2011-04-03
forum: Multimedia Software
---

### Post by colombdawg on 2011-04-03
Okay, so I have recently done a dual OS on my laptop running ubuntu 10.10.  My issue is that any media player I use will not play the sound.  It plays, you see the track moving the time going....the little nub that moves as the song progresses...it moves.  But no sound comes out.  So for the past two days I've been doing a lot of research on the internet to figure out HOW to fix this and everything I've tried is just an epic failure.  SO, with all this being said, can someone help me out?  I've tried Banshee, Rhythmbox, and I don't know if this means anything, but I am importing my music folder into the media players, but they are on the partition where windows is stored...this doesn't seem to be an issue as I've copied and pasted some music files to experiment with this and all is the same results....does anyone know how to rectify this situation?

---

### Post by colombdawg on 2011-04-04
bump....anyone has any solutions?

---

### Post by wolfen69 on 2011-04-04
Right click your sound icon and go to properties and see if all the sound levels are turned up.

---

### Post by colombdawg on 2011-04-04
I've done that...everything is installed, all the drivers, all my plugins, system sounds work.....Just won't play my music

---

### Post by Kirboosy on 2011-04-04
Welcome to the Forums! :)

Did you install the "ubuntu-restricted-extras" package? 


~Caboose

---

### Post by colombdawg on 2011-04-04
Yes, I did.  And it still doesn't work.  I dunno what to do.

---

### Post by Kirboosy on 2011-04-04
Try running this command in terminal
```
sudo apt-get install libflashsupport
```

I found that from an older topic but it still might be relevant to fix the issue...


What kind of laptop do you have?


~Caboose

---

### Post by wolfen69 on 2011-04-04
> **Caboose885 said:**
> Try running this command in terminal
```
sudo apt-get install libflashsupport
```

I found that from an older topic but it still might be relevant to fix the issue...


What kind of laptop do you have?


~Caboose

libflashsupport is not available anymore, and the issues it fixed is a long gone thing.

How did you install flash? Via what?

---

### Post by colombdawg on 2011-04-04
Well everything I installed was already preinstalled.  I also installed the restricted package one.  I'm using a Gateway NV53 laptop.  Any other possibilities?  Youtube doesn't work for me either, no sound from there.  The weird thing is when I logon to ubuntu it gives me the initial sound log of when ubuntu starts up.  That...three or four beat drum sound.  I also did a sound test with my speakers and the sounds played with the sound test, just not with any form of media or the internet.

---

### Post by Kirboosy on 2011-04-05
Hmmm I did a google search on your laptop for ubuntu on it. The only complaint I have seen is the Touchpad and Mic acting up. 

Did you install 64 bit on your computer? Also is your computer fully updated?

If you LiveCD Ubuntu does all your sound work?

---

### Post by Soulcage on 2011-04-05
Open a terminal and typing in "alsamixer" you might be able to use that fix your problem. Also check System > preferences > sound > hardware then setting the profile to analog stereo duplex if it isn't already.

---

### Post by slooksterpsv on 2011-04-06
I have a Gateway NV53, haven't had any big issues with sound except for the headphone jack, which was fixed by doing the following

```

echo "options snd_hda_intel model=laptop" | gksudo tee -a /etc/modprobe.d/alsa-base.conf
echo "options snd-hda-intel position_fix=1 enable=yes" | gksudo tee -a /etc/modprobe.d/alsa-base.conf

```

Other than that, on other distros, I've found that the main mixer is set to HDMI and not the Internal Audio, but where the system sounds work, hmmm... I'm not sure.

---

### Post by colombdawg on 2011-04-06
I got it to work!!  Thank you all.   RHythmbox still won't work, but I Got it to work on Banshee

---

