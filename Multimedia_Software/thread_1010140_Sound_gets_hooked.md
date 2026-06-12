---
title: "Sound gets hooked"
date: 2008-12-13
forum: Multimedia Software
---

### Post by DenKain on 2008-12-13
I am not sure how to explain it any better then I am about. 

If I open Firefox and go to somewhere like oh lets say pandora.com (this issue happens with any website that plays sound at all) and listen to some music then at the time everything is fine. Now lets say I download the latest episode of Hak5 to my desktop. I open the video (it does not matter what file format or what I use to listen/watch it[vlc, movie player, etc]) and there is no sound at all. If I close Firefox and then reopen the video then the sound plays. 

On the flip side lets say I am watching the Hak5 video and then I decided to open Firefox to follow a link they give in the video. Well then I can not hear any sound that Firefox would play on any website. I have to close the video and restart Firefox. 

Its almost like my programs are hooking some "sound thread" somewhere and not releasing the hook after the audio is finished and there does not seem to be multiple "sound threads".

Sorry the programmer in me keeps seeing this like threads and hooks.

Any ideas?

-DenKain

---

### Post by DenKain on 2008-12-21
bump

---

### Post by ZeroTruths on 2008-12-21
Strange problem. It does seem like the applications are being greedy with the "sound thread". Just an idea, but maybe you don't have sound mixing properly enabled? (Just an idea. I've only barely gotten a grasp on this kind of understanding a few hours ago)
Perhaps some info on you're sound settings? Alsa? OSS? PulseAudio?

---

### Post by DenKain on 2009-02-11
***_*Sound Preferences*_***

_***Devices***_
**Sound Events:** 
Auto
**Music and Movies:** 
Auto
**Audio Conferencing:** 
Sound playback:
Auto
Sound Capture:
ALSA
**Default Mixer Tracks:**
HDA Intel (Alsa mixer)

_***Sounds***_
check box enabled
check box enabled
All sounds set to "No Sound"

_***System Beep***_
Nothing is checked

---

