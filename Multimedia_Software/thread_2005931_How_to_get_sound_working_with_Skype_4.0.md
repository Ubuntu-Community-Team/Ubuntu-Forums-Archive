---
title: "How to get sound working with Skype 4.0"
date: 2012-06-18
forum: Multimedia Software
---

### Post by geovino on 2012-06-18
I just installed Skype 4.0 and the video works but no the audio. In settings it has Pulse audio listed. Maybe that's the problem, Seems like Alsa works better most of the time. Has anyone else had this problem? If Pluse audio is the problem how do I set it to Alsa?

Thanks

running Ubuntu 12.04 64bit

---

### Post by MonsterTrimble on 2012-06-18
I found PulseAudio a nightmare for working with Skype. You have to practically sacrifice a chicken to make it work. My solution was to purse Pulse and install Alsa. It just worked.

---

### Post by firekage on 2012-06-18
> **MonsterTrimble said:**
> I found PulseAudio a nightmare for working with Skype. You have to practically sacrifice a chicken to make it work. My solution was to purse Pulse and install Alsa. It just worked.

Purse or purge?

---

### Post by geovino on 2012-06-18
> **MonsterTrimble said:**
> I found PulseAudio a nightmare for working with Skype. You have to practically sacrifice a chicken to make it work. My solution was to purse Pulse and install Alsa. It just worked.

Had a feeling it was PulseAudio... I checked Synaptic and both alsa and pulse files are installed. Do I have to delete Pulse or can I just find a way to select Alsa for Skype?

Also I can use Google Talk/video instead. What do you think?

---

### Post by Steeperton on 2012-06-19
Do you mean that no-one can hear you,or you can't hear them?

---

### Post by geovino on 2012-06-19
> **Steeperton said:**
> Do you mean that no-one can hear you,or you can't hear them?

No sound during the test call. 

Too bad Pulse audio is a problem. I may use Google Talk/Video instead. I've heard from a friend that its more reliable than Skype.

---

### Post by SoFl W on 2012-06-19
I had the same problem, you need to click on sound preferences and make some adjustments.  Make sure the correct mic/sound device is selected. (and not muted)

---

### Post by Dwigatjel on 2012-06-30
I have found the solution which worked for me! ;)
Go to PulseAudio settings (if you don't have this installed install it)
Find "Played" (I'm using polish Ubuntu so don't know the English name) but it's near "recorded" (or other name) on the left and there will be Skype but it'll be muted so just unmute it and here we go:D

---

### Post by MZ250Supa5 on 2012-09-03
Tried all of the above with Skype 4.0 on Ubuntu 10.04 and no joy... video works well, as does written text, but sound is a no-go. Is this yet another example of the lousy implementation of PulseAudio in Ubuntu? I think I'll go back to the older version, as though that had issues, at least it worked using a workaround.

---

### Post by Lupi on 2012-09-13
I had the same audio problem. What forked for the audio was uninstalling Pulse and installed Alsa. Then, I changed the settings in Skype. That worked. Regrettably, now the image freezes after about 20-30 seconds and I have no idea what to do. My girlfriend absolutely needs Skype and I'm even thinking about dual booting just to use Skype.

---

