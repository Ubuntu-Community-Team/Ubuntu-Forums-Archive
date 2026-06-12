---
title: "Guitar/Pod/Transcribe"
date: 2010-06-12
forum: Multimedia Software
---

### Post by CarlWalters on 2010-06-12
I'm currently running Ubuntu 10.04 and would like a way to play my guitar via my PC so that I can play along to sample tracks that are running in Transcribe. I normally just have Transcribe running and the PC output goes via my HiFi Amp/Speakers while my guitar goes via my Line6 Pod 2.0 and into my guitar amp (Orange Crush 30R).

I though it would be good to be able to take the guitar output from the Pod 2.0 straight into the PC somehow and take the combined output back out to the HiFi Amp/Speakers. 

I son't think I want to mess around with Jack and all that stuff as it seems horribly complicated. Is it simply a matter of

Guitar -> Pod -> PC Line-In -> HiFi Amp?

---

### Post by cchhrriiss121212 on 2010-06-13
If you are just going to play along with the music, then why put it through the computer?
You will be trading the sound quality of a decent guitar amp for the crummy (in comparison) quality of your onboard sound card.

Jack is a great tool for recording, if you ever want to do that, but it would also allow you to use realtime amp simulators and effects. I could show you a painless way of installing and running it if you change your mind.

---

### Post by CarlWalters on 2010-06-13
Thanks for the reply. I know I'd lose some sound quality but I wanted to put the guitar through the Computer so that I could then get both the backing track (usually an mp3 slowed down using Transcribe) and the my guitar both coming through the same amp/speakers. I could just plug in my headphones and practice without waking up the rest of the house :)

If there is a painless way of installing Jack then I'd be very interested to know about it as I spent a couple of hours yesterday wading through articles and I wasn't any the wiser at the end of it.

---

### Post by cchhrriiss121212 on 2010-06-13
I have just been trying to look up transcribe, but can't find out much about it. Does it have jack as a selectable audio output?

Installing jack is fairly simple: download it from synaptic, open up qjackctl and uncheck realtime in the setup window, then press start.

---

### Post by CarlWalters on 2010-06-13
Transcribe is at [http://www.seventhstring.com/](http://www.seventhstring.com/)
very useful for practice, can't see anything about it working with Jack though.

---

### Post by cchhrriiss121212 on 2010-06-14
OK then I would forget about jack for now. What you need to do first is check your line in is working, so put alsamixer into a terminal and press f4 to see your capture channels, then raise up the level to something audible.
Then open up audacity and go to Edit>Preferences and check software playthrough. Add a new track and monitor the track to hear what you are playing. Depending on your card the latency (gap between when you play a note and when you hear it) might need to be adjusted.
There is likely a way to do this without using audacity or any other program but I don't know how, and audacity shouldn't use up too much resources anyway.

---

### Post by sites on 2010-06-14
gnome-sound-recorder

It's in your Apps menu already: Applications > Sound & Video > Sound Recorder.  I like Audacity, but if you don't want to install it try this instead.  You could also avoid all the headache which is often associated with making Pulse/ALSA/Jack work right by getting one of these...

[http://pro-audio.musiciansfriend.com/product/Behringer-MICROMIX-MX400-4Channel-Line-Mixer?sku=621108]("http://pro-audio.musiciansfriend.com/product/Behringer-MICROMIX-MX400-4Channel-Line-Mixer?sku=621108")

or one of these...

[http://pro-audio.musiciansfriend.com/product/Nady-MM141-4Channel-Mini-Mixer?sku=630433]("http://pro-audio.musiciansfriend.com/product/Nady-MM141-4Channel-Mini-Mixer?sku=630433")

Thirty bucks isn't bad.

---

