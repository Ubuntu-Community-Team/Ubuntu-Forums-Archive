---
title: "Sound Problem"
date: 2008-05-03
forum: Multimedia Software
---

### Post by locolbd on 2008-05-03
Hello  I am running on Ubuntu 8.04 however i have a problem, i can play mp3 and other music types, plus my video and sound works fine.  Except when i log in, i dont hear the login on sound, when i shut down or log out i dont hear those sounds either.  I went to the sounds options and made sure all these operations had a sound file entitled to it, but when i click on play i dont hear anything.

Another thing when i go to the login window option and there are three sound options there when i click on play on the sound files i hear them.  When i log out and my pc buts up i hear the "Question File" if i type in a wrong password I hear the question sound, but when i log in or shut down no sound is heard.  

Can anyone help??

---

### Post by Yellow Pasque on 2008-05-03
Go to System->Preferences->Sound
Which sound architecture are you using for Sound Events?

---

### Post by cmike2 on 2008-05-05
I too have this problem.

in System->Preferences->Sound I have set everything to PulseAudio Sound Server. (Actually, I made everything but login/logout sounds play through pulseaudio just now).

I'm not sure if this is relevant, but my sound card is not "device 0" which seems to be the default device that pulseaudio plays through. I had to switch some streams to the proper device to get them to play, so I was thinking login sounds are playing on the wrong device.

edit: Found the default device option in PulseAudio, but it doesn't solve the problem. It's in PulseAUdio volume control, go to output devices tab, and right click the device you want to be default.

edit2: I got just "log in" sound to play now. I opened up system->preferences->sound, clicked the test button for sound events, opened up pulseaudio volume control, right clicked the stream, and set the proper device. I don't get a log out sound, however.

---

