---
title: "sound to usb audio device cuts out after a few minutes"
date: 2010-03-27
forum: Multimedia Software
---

### Post by b33tfr33kr on 2010-03-27
i am using ubuntu studio karmic and i have a digitech vx400 audio effects pedal which serves as an audio in/out midi in/out device via usb. i can sucessfully set it as the system sound device in system>preferences>sound for both input and output. but, when i play audio through it it only works for a few minutes before the sound stops completely. if i leave the system settings set to the internal sound card and configure jack audio connection kit to go to the usb device, i get the same results on the usb sound. a few minutes of playback at the most. i can restart sound with either "pulseaudio --kill && pulseaudio --start" or "alsactl init" in either situation.  just requires restarting the programs. same results after restarting. i think this is alsa related as i have both the system sound and jack using the alsa driver, but i don't truly understand the relationship between pulseaudio and alsa. any thoughts?

---

### Post by cchhrriiss121212 on 2010-03-27
Does jack give any messages when the sound cuts out?
It could be that you are getting interrupted by other hardware that is plugged in to your input ports, try unplugging all other things.

---

### Post by b33tfr33kr on 2010-03-27
no messages from jack. it just keeps trucking along as if nothing's wrong. just no sound. level meter registers the attempted output just before connecting to the playback port in patchage. tried unplugging my usb mouse to leave the audio device alone on the usb controller, no change.

---

### Post by b33tfr33kr on 2010-04-02
update: am able to restart sound by stopping and restarting jack from jack control , then closing and restarting audacious (set to use jack output plugin) but with same results.

---

### Post by cchhrriiss121212 on 2010-04-03
I'm out of ideas already on this, but I found a link that seems to suggest this is functional under 64 studio, so I'd imagine you could get this working eventually:
[http://www.linuxmao.org/tikiwiki/tiki-index.php?page=Digitech+Vx400](http://www.linuxmao.org/tikiwiki/tiki-index.php?page=Digitech+Vx400)

Try posting a thread in the Ubuntu studio section.

---

### Post by elgordo123 on 2010-04-14
I have the exact same problem.  I'm using 64bit 9.10.   I've removed pulse but still have the same problem.   Have you found any fixes for this?  I used to use 32bit on an older computer and did not have this problem. 
It is driving me nuts.  I dont want to give up 64bit Ubuntu, but this is a must as I use skype-out all the time for work.

---

