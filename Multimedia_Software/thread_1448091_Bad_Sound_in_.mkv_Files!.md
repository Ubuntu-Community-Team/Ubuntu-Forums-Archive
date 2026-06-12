---
title: "Bad Sound in .mkv Files!"
date: 2010-04-06
forum: Multimedia Software
---

### Post by wqawasmi on 2010-04-06
Hello,

I seem to be getting some issues with the sound in .mkv files.

I hear the sound, but certain sounds are missing. 

Example:

Fight Club .mkv movie, I cannot hear the dialog but I can hear everything else perfectly. 

Tried in Windows and it worked great. 

Doesn't work with the default movie player, or VLC.

Thanks,

-Will Qawasmi

---

### Post by cchhrriiss121212 on 2010-04-06
Sounds like the mkv has a surround sound setup and you are listening in stereo speakers. Try changing the sound settings in preferences in vlc.

---

### Post by mcduck on 2010-04-06
> **cchhrriiss121212 said:**
> Sounds like the mkv has a surround sound setup and you are listening in stereo speakers. Try changing the sound settings in preferences in vlc.

+1 to this, sounds like only listening to front left & right channels while most of the speech in a movie would be in center channel.

Most video players have the option to downmix surround sound into stereo sound.

---

### Post by wqawasmi on 2010-04-06
> **cchhrriiss121212 said:**
> Sounds like the mkv has a surround sound setup and you are listening in stereo speakers. Try changing the sound settings in preferences in vlc.

Sorry, I couldn't find that option. 

Also, if that was the case, how come it can work perfectly in Windows? (VLC in Windows)

---

### Post by cchhrriiss121212 on 2010-04-06
You may have not heard the phrase "Linux is not Windows" before then. Ubuntu uses pulse audio by default which is not always functional. 
Open vlc go to tools>preferences>audio and there is an option about dolby surround, try changing it. You could also try switching the sound output to alsa.

---

### Post by wqawasmi on 2010-04-06
> **cchhrriiss121212 said:**
> You may have not heard the phrase "Linux is not Windows" before then. Ubuntu uses pulse audio by default which is not always functional. 
Open vlc go to tools>preferences>audio and there is an option about dolby surround, try changing it. You could also try switching the sound output to alsa.


Alright so far I:

Tried switching the dolby surround option from Auto, To Off. Then tried turning it On. No change.

Then changed the output to ALSA, I received no sound. 

Then I tried changing the output to Pulse Audio, I received sound but got the same problem as before.

---

### Post by cchhrriiss121212 on 2010-04-06
Try out a different player, smplayer is what I use and it handles 5.1 to stereo OK. In order to use pure alsa you might need to change it in the preferences>sound menu. I removed pulse from my system after getting a lot of similar annoyances.

---

### Post by mcduck on 2010-04-06
> **wqawasmi said:**
> Sorry, I couldn't find that option. 

Also, if that was the case, how come it can work perfectly in Windows? (VLC in Windows)

Actually it works perfectly in Ubuntu (Video with surround sound is played back using surround sound since you clearly have a sound card capable of doing that). The only problem is that you clearly don't have a surround amplifier/speakers connected. ;)

Anyway, first go to System/Preferences/Sound and make your sound card is set to stereo mode. Then, for Totem (the default video player), the option to downmix sound into Stereo is in *Edit/Preferences/Audio*, just set the "*Audio Output type*" to "*Stereo*".

What comes to VLC, I only have it installed on OSX at the moment and the options are bit different so you'll have to wait for somebody who uses it in Ubuntu to tell where the setting is.

Edit: By the way, the "Dolby Surround"-option in VLC is completely irrelevant to this, as Dolby Surround is just stereo audio and would thus sound completely normal on your stereo setup.

---

