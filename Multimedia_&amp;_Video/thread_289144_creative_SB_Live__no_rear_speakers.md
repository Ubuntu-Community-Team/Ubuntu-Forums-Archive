---
title: "creative SB Live  no rear speakers"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by scotty76uk on 2006-10-30
Hi

newbie trying to get some of my basics configured.. please help!:confused: 

I have a creative SB Live soundcard which worked as soon as i installed ubuntu my only problem is that I can only get sound from the front speaker input and not the rear. I normally use the front for my headphones and the rear to play out of my amp. With the windows drivers comes a creative surround sound mixer which you have to tell to use four speakers, obviously this is not an option with in ubuntu. We have an ALSA mixer, I have tried every switch and volume control on the ALSA mixer but no joy. Any ideas please has anyone else had a similer problem

Cheers:cool:   scott

---

### Post by Maintech on 2006-10-30
Make sure your system is using Alsa and not OSS first. Then make sure you have Gnome-Alsa Mixer. Look for "front, surround, and center". Turn center up and surround up. Front will probably already be turned up. Surround will turn the volume up on the "rear" speakers. Center turns up the sub-woofer if you have 5.1 surround speakers. At least, that's the way it works on mine.

---

### Post by Gonzell on 2007-06-18
To get my rear speakers working:

- double clicked the speaker icon in the top-right hand corner
- clicked the "switches" tab
- unchecked "SB Live Analog/Digital Output Jack"

I then had to modify the "Wave" and "Wave Surround" settings to get the right balance of sound coming from the front and rear speakers. To add these controls to your "Playback" tab, just click Edit > Preferences.

My keyboard has volume controls on it, but it controlled "Master Volume" by default which only controlled my front speakers. To fix this, I went into System > Preferences > Sound. Then in the "Default Mixer Tracks" section, I clicked on "Wave" and then held Ctrl and clicked "Wave Surround". This way, when I used my volume control, it controlled those to settings.

Everything works like a charm for me.....so far.

I hope this helps someone because this was bugging me for the longest while.

Gonzell

---

### Post by motang on 2007-06-19
> **Gonzell said:**
> To get my rear speakers working:

- double clicked the speaker icon in the top-right hand corner
- clicked the "switches" tab
- unchecked "SB Live Analog/Digital Output Jack"

I then had to modify the "Wave" and "Wave Surround" settings to get the right balance of sound coming from the front and rear speakers. To add these controls to your "Playback" tab, just click Edit > Preferences.

My keyboard has volume controls on it, but it controlled "Master Volume" by default which only controlled my front speakers. To fix this, I went into System > Preferences > Sound. Then in the "Default Mixer Tracks" section, I clicked on "Wave" and then held Ctrl and clicked "Wave Surround". This way, when I used my volume control, it controlled those to settings.

Everything works like a charm for me.....so far.

I hope this helps someone because this was bugging me for the longest while.

Gonzell

Yep I had to do the same thing and mine worked just fine after wards.

---

### Post by Karnex420 on 2007-08-23
I must have something else missing.  Three of my six speakers still don't work with my Soundblaster Live.

---

### Post by SaMuRaI_777 on 2007-10-04
Thanks, This post has helped me alot

---

