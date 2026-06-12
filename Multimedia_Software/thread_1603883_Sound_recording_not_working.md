---
title: "Sound recording not working"
date: 2010-10-23
forum: Multimedia Software
---

### Post by Jeroen De Dauw on 2010-10-23
I'm having problems getting my microphone to work on a new Kubuntu 10.10 install. I'm not sure what's wrong, but I can't make Skype calls (in which the other party hears me). Any ideas what might be wrong and how it can be fixed?

---

### Post by coffee412 on 2010-10-23
> **Jeroen De Dauw said:**
> I'm having problems getting my microphone to work on a new Kubuntu 10.10 install. I'm not sure what's wrong, but I can't make Skype calls (in which the other party hears me). Any ideas what might be wrong and how it can be fixed?

There are some programs that I wish were installed by default. But should be added to Ubuntu and its derivatives. I have not tried Kubuntu but I assume from what I have heard its basically Ubuntu. 

I have a webcam with built in mic and had the same problem. I installed the "Device Chooser" and other programs for pulseaudio and went into devices and told pulseaudio to use the mic on my cam rather than my soundcard. Do a search in software center or equivalent for Kubuntu for pulseaudio stuff.

If you just have a sound card you might check alsamixer and see if its turned on. I also understand there is a GUI for alsamixer too. Might install that to make it easier.

Im sure others will chime in with more help :)

---

### Post by Jeroen De Dauw on 2010-10-23
> **coffee412 said:**
> I installed the "Device Chooser" and other programs for pulseaudio and went into devices and told pulseaudio to use the mic on my cam rather than my soundcard.

I installed this app, and was able to get my recording stuff configured correctly using it. Thanks!

---

### Post by rihad on 2011-12-01
> **Jeroen De Dauw said:**
> I installed this app, and was able to get my recording stuff configured correctly using it. Thanks!
Which app exactly did you install? I can't find "Device Chooser" in Apper. I have the same problem, mic's not working.

---

### Post by inobe on 2011-12-01
> **rihad said:**
> Which app exactly did you install? I can't find "Device Chooser" in Apper. I have the same problem, mic's not working.

open terminal and type **alsamixer** use arrow keys to navigate, tab etc, located and highlight your muted mic and press m to un
mute it.

---

### Post by rihad on 2011-12-01
> **inobe said:**
> open terminal and type **alsamixer** use arrow keys to navigate, tab etc, located and highlight your muted mic and press m to un
mute it.

Thanks, I had already tried that, it didn't help. I also opened a topic on kubuntuforums: [http://kubuntuforums.net/forums/index.php?topic=3119536.0](http://kubuntuforums.net/forums/index.php?topic=3119536.0)

---

### Post by inobe on 2011-12-01
> **rihad said:**
> Thanks, I had already tried that, it didn't help. I also opened a topic on kubuntuforums: [http://kubuntuforums.net/forums/index.php?topic=3119536.0](http://kubuntuforums.net/forums/index.php?topic=3119536.0)

that strange noise maybe because mic boost is way too high!

why not start a thread here, you would get better help instead of hijacking this thread?

:)

---

### Post by geoaraujo on 2011-12-01
> **rihad said:**
> Thanks, I had already tried that, it didn't help. I also opened a topic on kubuntuforums: [http://kubuntuforums.net/forums/index.php?topic=3119536.0](http://kubuntuforums.net/forums/index.php?topic=3119536.0)
Hello. Did you try [this]("https://help.ubuntu.com/community/AudioCapture#If_your_microphone_still_does_not_work")?

Maybe the trouble is with the app, not with the os.

---

### Post by rihad on 2011-12-02
> **geoaraujo said:**
> Hello. Did you try [this]("https://help.ubuntu.com/community/AudioCapture#If_your_microphone_still_does_not_work")?

Maybe the trouble is with the app, not with the os.

arecord test.wav - still no sound. Apart from the noise.

---

### Post by rihad on 2011-12-02
> **inobe said:**
> that strange noise maybe because mic boost is way too high!

why not start a thread here, you would get better help instead of hijacking this thread?

:)

I can't see this mic boost setting in alsamixer. OK, so here's the thread, then :)

---

### Post by geoaraujo on 2011-12-02
> **rihad said:**
> I can't see this mic boost setting in alsamixer. OK, so here's the thread, then :)
In alsamixer, look for PCM.

---

### Post by rihad on 2011-12-02
> **geoaraujo said:**
> In alsamixer, look for PCM.

Ah, I see what you meant. In my case the level of noise is controlled by the "Front" gauge, not by "PCM". Muting it eliminates the noise. Coincidentally, it also eliminates any sound :) 

Maybe I should tweak something in /etc/pulse/* to get sound recording to work?

---

### Post by inobe on 2011-12-02
> **rihad said:**
> Ah, I see what you meant. In my case the level of noise is controlled by the "Front" gauge, not by "PCM". Muting it eliminates the noise. Coincidentally, it also eliminates any sound :) 

Maybe I should tweak something in /etc/pulse/* to get sound recording to work?

i had my mic issues too, it's not my first rodeo :lol:

however, my situation was due to very high mic boost which cause undesirable interference.

you should have mic boost, did you scroll all the way, there are hidden channels further to the right side?

---

### Post by rihad on 2011-12-03
> **inobe said:**
> i had my mic issues too, it's not my first rodeo :lol:

however, my situation was due to very high mic boost which cause undesirable interference.

you should have mic boost, did you scroll all the way, there are hidden channels further to the right side?

Well, here's what I got, after pressing F5 (view all).
I've unmuted "Mic" to test sound recording, but there's this noise coming from the speakers when it's on, so I don't normally have it on.

---

