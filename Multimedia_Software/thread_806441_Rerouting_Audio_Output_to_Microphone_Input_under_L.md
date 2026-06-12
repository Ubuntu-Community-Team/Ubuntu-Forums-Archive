---
title: "Rerouting Audio Output to Microphone Input under Linux."
date: 2008-05-24
forum: Multimedia Software
---

### Post by PObserver on 2008-05-24
Hello all.

When I was once a Windows user, I use to be able to utilize third party applications like Audacity to take my computer's audio output and convert it to a microphone input so I could broadcast on Skype/TeamSpeak/Stickam. I've tried the Audacity Linux version, and this is not possible. How can I reroute my computer's audio output to microphone input under Linux? Thanks in advance.

---

### Post by wrongopinions on 2008-06-23
Hello all,
  I am trying to figure this exact same thing out. Anyone have any ideas?? I know theres got to be a way to do this.

thanks,
Paul

---

### Post by Sawyer_ on 2008-06-24
I believe you can use something like alsamixer or gamix to select such things, if you are using the ALSA system.

Make sure ALSA is selected for necessary devices to use in 
System->Preferences->Multimedia Systems Selector and
System->Preferences->Sound.

---

### Post by wrongopinions on 2008-06-25
I am still unsure of the strange details. I seem to now have lost all microphone support (it used to work). 
As a secondary solution, is there any way to pipe an audio file to the mic without tricking it to feed from the speakers? For my purposes I wouldnt mind just feeding through a program (or even writing a program that would accomplish it).

Thanks,
Paul

---

### Post by wrongopinions on 2008-07-01
Alright. I do not know how to do this even with the alsa mixer. Anyone know how to specific redirect an audio file sample into the microphone?

---

### Post by markbuntu on 2008-07-01
You can do that with jack but I don't know if you really want to open that can of worms. 

I don't use skype but I am guessing that you can change the audio input device from the mic to the mixer or your sound card. You can do this in Ekiga.

---

### Post by Joseph Schwenker on 2011-11-24
[This guy]("http://www.kirsle.net/blog/kirsle/redirect-audio-out-to-mic-in--linux-") wrote a nice guide on how to do this, in case you still have this problem.

---

