---
title: "Half an audio problem"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by EvilMarshmallow on 2007-06-30
Hey all,  I've been reading forum posts all afternoon trying to figure out what's up with my sound.
I have an intel onboard audio chipset which I disabled in the blacklist.
I installed a Creative SoundBlaster Audigy SE (uses snd-ca0106).

If I open VLC Media player and choose a music file, it plays, I hear it perfectly.
If I double-click the file to open, it's automatically opened in Totem but I can't hear a thing.

If I choose System -> Preferences -> Sound, all are set to AutoDetect.

The weird part is, my CA0106 shows up 4 TIMES in this list, and none of them work (I get an error message when I test):
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

Here are the results of aplay -l :
> **** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Here are the results of aplay:
> ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:547: audio open error: No such file or directory

What have I done, and how can I fix it?  My guess is that my ALSA installation has corrupted somehow, but reinstalling it from Synaptic does nothing.

---

### Post by samuraiCat on 2007-07-01
> **EvilMarshmallow said:**
> Hey all,  I've been reading forum posts all afternoon trying to figure out what's up with my sound.
I have an intel onboard audio chipset which I disabled in the blacklist.
I installed a Creative SoundBlaster Audigy SE (uses snd-ca0106).

If I open VLC Media player and choose a music file, it plays, I hear it perfectly.
If I double-click the file to open, it's automatically opened in Totem but I can't hear a thing.

If I choose System -> Preferences -> Sound, all are set to AutoDetect.

The weird part is, my CA0106 shows up 4 TIMES in this list, and none of them work (I get an error message when I test):


Here are the results of aplay -l :


Here are the results of aplay:


What have I done, and how can I fix it?  My guess is that my ALSA installation has corrupted somehow, but reinstalling it from Synaptic does nothing.

Yep! I have exactly the same thing going on. Or, I should say, had the same thing going on, because I had to abandon ship and go back to XP until I could figure it out. I still haven't.

---

### Post by RobMBaker on 2007-07-07
Same thing here ...

---

### Post by DaveBentham on 2007-07-13
Yep and me...

Everything was fine with Edgy.... I pressed the Feisty upgrade button in the Update Manager, and I (half) lost sound on my SB card.

---

### Post by DaveBentham on 2007-07-21
Seems to me, ~/.asoundrc.asoundconf is incomplete, i.e. from this error "ALSA lib confmisc.c:1286: (snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'"

After trawling around, I found this: [http://www.stchman.com/mult_sound.html](http://www.stchman.com/mult_sound.html) and I did the 2 commands for my system...

dave@outland:~$ sudo asoundconf list
Password:
Names of available sound cards:
CA0106
VT82xx
dave@outland:~$ sudo asoundconf set-default-card CA0106

And lo! ~/.asoundrc.asoundconf was filled out with more defaults.pcm.stuff and I appear to have full sound now, no more of them errors.

---

### Post by RobMBaker on 2007-07-21
Good work! I'll give it a go myself tomorrow morning, and see if it's a general fix.

---

### Post by DaveBentham on 2007-07-22
I dont believe you *need* to do those commands as 'sudo' because .asoundrc.asoundconf is in $HOME...

And also because of that, it needs doing for every user who wants ALSA sound through the same sound card. And on my system, not every user is a 'sudoer' anyway, so I did it for my son's account without 'sudo' which also now works.

---

### Post by RobMBaker on 2007-07-22
Brilliant - it now works as I wanted! Well spotted, Dave, and thanks.

I did it as 'sudo' just in case, because sound wasn't working on start-up; i.e. before anyone has logged in, it wouldn't play the little GNOME-Login-screen music (the drums/bongos).
edit: you're right though, the Login bongos still don't play; but as soon as I log in, I get the Login .wav and everything works fine from then on. I don't suppose there's a root version of that asoundconf file for me to find and fix?

---

### Post by DaveBentham on 2007-07-24
Im not sure about that Rob, my power-up drums always played ok...

---

### Post by RobMBaker on 2007-07-25
Oh well ... a minor issue for me; at least it all works after log-in :)

---

