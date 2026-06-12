---
title: "Mono output with Pulseaudio?"
date: 2009-01-24
forum: Multimedia Software
---

### Post by picpak on 2009-01-24
I'm using Ubuntu 8.04 and I want to know if there's a way to output my audio down to one channel in PulseAudio. My right headphone speaker is toast and I want something to tide me over until I get new ones.;)

[COLOR="#FF0000"][SIZE=3]Please see here : [http://ubuntuforums.org/showthread.php?t=2264711]("http://ubuntuforums.org/showthread.php?t=2264711")[/SIZE][/COLOR]

---

### Post by razvanab on 2009-02-05
Come on guys !

tell us how to output audio down to one channel with  pulseaudio

---

### Post by markbuntu on 2009-02-05
You can try this, I am not sure if it will work. Open the /etc/pulse/daemon.conf file as sudo

sudo gedit /etc/pulse/daemon.conf

find the line

;default-sample-channels = 2

change it to

default-sample-channels = 1

restart pulseaudio or just logout and login

Like I said, I am not sure if this will work but it should resample all your audio to mono. If you could let us know if this works or not it would be appreciated.

If something goes drastically wrong just reedit the file back the way it was etc.

---

### Post by lukepadawan on 2009-04-23
If you're only looking for mono output with ubuntu, you could also try edit ~/.asoundrc (if you're using alsa):

[FONT=Times New Roman]#version 1
pcm.mono {
   type route
   slave.pcm  "cards.pcm.default"
   ttable.0.1 1
   ttable.1.1 1
}
pcm.!default pcm.mono

[/FONT]or...

[FONT=Times New Roman]#version 2
pcm.mono {
   type route
   slave.pcm  "cards.pcm.default"
   ttable.0.0 1
   ttable.1.0 1
}
pcm.!default pcm.mono
[/FONT]

---

### Post by razvanab on 2009-05-22
doesn't work sorry 

[picpak] install wine and use foobar2000 which have a stereo 2 mono plug-in 

works perfect with ubuntu...

---

### Post by pablojavier on 2009-10-12
> **lukepadawan said:**
> If you're only looking for mono output with ubuntu, you could also try edit ~/.asoundrc (if you're using alsa):

[FONT=Times New Roman]#version 1
pcm.mono {
   type route
   slave.pcm  "cards.pcm.default"
   ttable.0.1 1
   ttable.1.1 1
}
pcm.!default pcm.mono

[/FONT]or...


lukepadawan, this worked perfectly for me! I am using ALSA in jaunty and I needed something like this because I have a MONO cassette adapter to connect to an old amplifier.

Thanks a lot!!

---

### Post by jARLAXL on 2010-02-20
> **pablojavier said:**
> lukepadawan, this worked perfectly for me! I am using ALSA in jaunty and I needed something like this because I have a MONO cassette adapter to connect to an old amplifier.

Thanks a lot!!

+1 :guitar:

one of my soundboxes is out of order therefore needed mono desperately but i dont know of a clickable way to do this. maybe apps like rythmbox or amarok should have such an option?

---

### Post by jARLAXL on 2010-02-20
However!

doing this modification will not make it possible to listen to multiple sound outputs simultaneously.

---

