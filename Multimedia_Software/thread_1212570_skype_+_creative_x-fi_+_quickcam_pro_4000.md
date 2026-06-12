---
title: "skype + creative x-fi + quickcam pro 4000"
date: 2009-07-13
forum: Multimedia Software
---

### Post by fcuk112 on 2009-07-13
i have used the quickcam pro 4000 on another jaunty machine without any problems.

on this machine, it took me some fiddling around with the settings to get the xi-fi sound to work, but skype is still not working for me.  under video devices, i click "test" and i get a picture OK.

the problem is with the sound devices, i set both sound out and ringing to pulse, but not sure what to set my sound in to.  the only options i have are:

default device (default)
Creative X-Fi (hw:XFi,0)
Creative X-Fi (plughw:XFi,0)
hdmi
headset
pulse

i have tried all of them and for none of them i can get the test call working correctly (it does not playback my voice).

any ideas?

thanks.

---

### Post by fcuk112 on 2009-07-14
bump

---

### Post by bluestix on 2009-08-31
I think I just figured this out.


I had problems with no microphone on Skype 64 on 9.04


To fix it I had to:


1. In Skype options set all sound devices to 'Creative X-Fi (hw:XFi,0)'. Uncheck 'Allow skype to automatically adjust my mixer levels'.

2. Go to System > Preferences > Sound. Change Default Mixer Tracks Device to 'Creative X-Fi (Alsa mixer)'

3. Under Default Mixer Tracks, in the list, hold down shift and select the whole list. Then close Sound Preferences.

4. Open Volume Control. Make sure Device is 'Creative X-Fi (Alsa mixer)'. Make sure Microphone is unmuted and turned all the way up. Click the Recording tab and make sure Master, Line-In, and Microphone are all unmuted. Turn Microphone and Master most of the way up.




I think that was all I had to do.

I haven't restarted yet so I am not sure it will still work when I do.

---

### Post by bluestix on 2009-09-06
Ok. I was wrong.


That only worked until I restarted.


Now its back to not working again.


I guess disabling the soundcard drivers and restarting then re-enabling them is the only way to get it to work.

---

### Post by xfyler on 2009-09-22
same problem...

so i am going back to Windows... basic thing as microphone doesnt work in linux... so why use linux?

---

