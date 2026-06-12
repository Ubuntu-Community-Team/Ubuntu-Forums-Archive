---
title: "no sound in Hydrogen"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by Yvon on 2006-10-30
I'm new to Linux. I just installed it this weekend. (Ubuntu 6.10)
I have sounds no problem. But I can't get any sound out of Hydrogen. 
My sound card is an M-audio 24/96. I tried all the drivers listed in Hydrogen...no result. 

What else should I check?


Thank you

Yvon

---

### Post by CadetD on 2006-10-30
Under File/Preferences/Audio System:
Check what sound card you have selected and what driver.

Also, the volume on your cards can be muted or the wrong mixer settings. 
Try running 
envy24control and double-check your settings. 

Are you running JACK? Did you start jackd with the right card? 

Are any other music composition apps running? 

If you have an onboard sound card, what order is it loading with respect to the M-audio card? 
cat /proc/asound/cards

... can't think of anything else for now. 

Dudley C.

---

### Post by Yvon on 2006-10-31
Thank you. 
I install Jack, I try to run it and nothing happen... 
I don't really how it work. 
FOr the sound card I have this:
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 66
 1 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xcc00, irq 66


I tried all the audio drivers and nothing happend. 

Thank you


Yvon

---

### Post by Yvon on 2006-11-02
I installed Jack correctly today! :)
Finaly. I went on ubuntu france and followed everything. 

It work now. 


Thank you


Yvon


Now I will look for other software. If I can record and use some plug ins, I can officialy throw windows by the....window.

---

### Post by CadetD on 2006-11-02
That's great, Yvon!

Bonne chance avec ta musique. And by all means, throw Window$ out the window. 

Here are a couple of links to Linux music apps:

[http://linux-sound.org/](http://linux-sound.org/)
[http://www.alsa-project.org/applications.php](http://www.alsa-project.org/applications.php)

Dudley C.

---

### Post by Yvon on 2006-11-02
> **CadetD said:**
> That's great, Yvon!

Bonne chance avec ta musique. And by all means, throw Window$ out the window. 

Here are a couple of links to Linux music apps:

[http://linux-sound.org/](http://linux-sound.org/)
[http://www.alsa-project.org/applications.php](http://www.alsa-project.org/applications.php)

Dudley C.


merci, I will check those links this week end!!

---

