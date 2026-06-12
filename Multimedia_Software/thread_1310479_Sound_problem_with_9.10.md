---
title: "Sound problem with 9.10"
date: 2009-11-01
forum: Multimedia Software
---

### Post by m0rbidpercepti0ns on 2009-11-01
Ok so ive just updated from 9.04 to 9.10. in 9.04 my sound was messed up,i use an Audigy2 card. I finally got it to work by clicking digital input/output box on under sound settings,although i could hardly hear sound over the crackling and popping that i wasnt ever able to fix. So ive just updated,hoping to see improvements,and although i dont hear idle popping and crackling,my sound no longer works whatsoever. Ive searched the forums,and no one seems to have the same problem,yet at least. Also ive poked around in sound preferences and settings,and i havent been able to find anything helpful.If anyone has any ideas,or theres any information i can provide to help you help me,please let me know,thanks in advance to anyone who takes time to help:)

---

### Post by m0rbidpercepti0ns on 2009-11-02
Ok so my issue was that since 9.10 the Audigy Analog/Digital Output Jack box that had previously been in Sound preferences menu *right click from the speaker icon* Is now in the gnome ALSA manager menu under preferences>sound. The Gnome ALSA also wasnt loading correctly,but a quick purge and reinstall solved that,the box is at the bottom.

---

### Post by kennethtb on 2009-11-06
Hi I have 9.10 and I'm sitting here reading this forum listening to an ongoing intermittent crackling sound.  cannot follow your directions .. where for instance under system/preferences/sound is ALSA or a speaker icon?
I would love to clear up this problem as its becoming rather annoying - any further comments or suggestions would be most welcome.

---

### Post by shanknbake on 2009-11-06
I'm having a similar issue. I keep hearing random popping sounds -- I'll hear it when i adjust my volume or a sound starts to play.

I'm running ubuntu 9.10 -- what can I do to fix this?

Additional info:
%>aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by shanknbake on 2009-11-06
So I found a temporary solution to this on the net: [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442463")

Basically you need to modify /etc/modprobe.d/alsa-base.conf, 
changing** power_save=10** to **power_save=0**

---

### Post by kennethtb on 2009-11-06
Hi please explain for an average skill user how to modify /etc/modprobe.d/alsa-base.conf,
my experience of using the terminal is limited but this popping noise is driving me crazy so I need to try. thanks     have 9.10 HP laptop

---

### Post by kennethtb on 2009-11-06
Hi posted my thread today and already I'm forgotten back on page four! and I'm glad I never posted under installation problems ...     Can someone please provide a solucion to the internal speaker clicking sound using the recommended terminal code but explaining in rookie step by step manner.
thanks again

---

### Post by shanknbake on 2009-11-07
Sure kenneth,
Basically you need to modify /etc/modprobe.d/alsa-base.conf, 

Do this by typing sudo gedit /etc/modprobe.d/alsa-base.conf  [you'll be prompted to enter your password]

next you'll want to scroll down to where you see the line that contains "** power_save=10** " and simply change the 10 to 0 thus yielding: **power_save=0**

I'm pretty sure this isn't a permenant solution but it will work until you find something better. -- when you do let me know too :)

---

### Post by setiamon on 2009-11-07
that never worked for me.i tried everything

X-fi Xtreme music 

No matter what i do i can't fix it,horriable audio distortions in movie players,like mp3s.

flash is staticy and echos when it suddenly stops.

frankly i am considering going back to jaunty because of this.but removing pulse audio doesn't work,updated alsa,uninstalled it,reinstalled it didn't work


In other words nothing works.

---

### Post by ZeeGee on 2009-11-07
I'm using a Creative E-MU 0404 USB, actually I've been using 9.10a for half a year now, and the crackling problem has been on and off from update to update, now the final release seem to have a broken one :( And I have no idea what changed between those updates...

---

### Post by ZeeGee on 2009-11-07
hmmm, by digging old threads, I found that the root cause for me is that my E-MU 0404 USB has a default sample rate of 48KHz while PulseAudio has that set to 44.1KHz.

I know for sure that E-MU 0404 USB supports 44.1KHz, but somehow they two failed to talk to each other...

I modified default sample rate in /etc/pulse/daemon.conf to 48 and solved the problem.

---

### Post by shanknbake on 2009-11-07
well hang in there, hopefully someone will come along with the answer. -- like ZeeGee

---

### Post by setiamon on 2009-11-07
> **ZeeGee said:**
> hmmm, by digging old threads, I found that the root cause for me is that my E-MU 0404 USB has a default sample rate of 48KHz while PulseAudio has that set to 44.1KHz.

I know for sure that E-MU 0404 USB supports 44.1KHz, but somehow they two failed to talk to each other...

I modified default sample rate in /etc/pulse/daemon.conf to 48 and solved the problem.



Sadly this did not work for me :(

---

### Post by brianfriedkin on 2009-11-18
I have an Audigy 2 sound card and tried the recommended things above --" power_save=10 " and simply change the 10 to 0 thus yielding: power_save=0" -- It was all to no avail. I still had the irritating static/crackle.

This is what I did that was successful to get rid of the static: I went into the BIOS and disabled the on board audio. Everything sounds clear now.

---

### Post by grimey44 on 2010-01-02
> **m0rbidpercepti0ns said:**
> Ok so ive just updated from 9.04 to 9.10. in 9.04 my sound was messed up,i use an Audigy2 card. I finally got it to work by clicking digital input/output box on under sound settings,although i could hardly hear sound over the crackling and popping that i wasnt ever able to fix. So ive just updated,hoping to see improvements,and although i dont hear idle popping and crackling,my sound no longer works whatsoever. Ive searched the forums,and no one seems to have the same problem,yet at least. Also ive poked around in sound preferences and settings,and i havent been able to find anything helpful.If anyone has any ideas,or theres any information i can provide to help you help me,please let me know,thanks in advance to anyone who takes time to help:)


i have the exact same problem. tried fixing the sound popping problem and then all my audio stopped working. could you explain more how you fixed this?

---

