---
title: "Configure ALSA to accept multiple applications"
date: 2009-12-19
forum: Multimedia Software
---

### Post by caiocc12 on 2009-12-19
I am using Karmic.

I am trying to break free from PulseAudio. Unfortunately, ALSA in Ubuntu works only for one application at a time. Edubuntu documentation (I think that applies to Ubuntu too) states: 

> On the lowest level, only one application can use the sound card at a time. To enable multiple applications to use the sound card simultaneously,** you need a sound server**, and most Ubuntu editions use PulseAudio as sound server. However, if an application manages to grab the sound card before PulseAudio does, sound will not work. 

Which is simply NOT TRUE, because I have Debian Lenny installed here too, it uses ALSA and works flawlessly with multiple applications.

So I guess it is some configuration set to lock the card to one app only (maybe Ubuntu devs trying to force PulseAudio down our throats :lolflag:) or I need to recompile the kernel with some "multiple application" option set in ALSA.

Can somebody shine a light on this?

---

### Post by me13221 on 2010-02-27
There seems to have been a design decision to go with Pulse Audio in ubuntu and deprecate others.  I have not been able to get mpd to work with pulseaudio so I switched it to alsa, but now I'm discovering that the sound support I loved on my debian system isn't here.  or maybe it is and I just don't know how to turn it on.

In any case, I'm in the same boat as you.

---

### Post by amrypma on 2010-02-27
We'll here is my very dirty hack.

[LIST=1]
[*]Uninstall Pulseaudio
[*]replace /usr/bin/pulseaudio
[/LIST]

Replace it with a bash script.
```
#!/bin/bash
exit 0
```

It'll generate loooong errors but it keeps my sound working.

---

### Post by caiocc12 on 2010-02-27
> **amrypma said:**
> We'll here is my very dirty hack.

[LIST=1]
[*]Uninstall Pulseaudio
[*]replace /usr/bin/pulseaudio
[/LIST]

Replace it with a bash script.
```
#!/bin/bash
exit 0
```

It'll generate loooong errors but it keeps my sound working.

But does it work for multiple applications? I. e. can you listen to music while playing a game ?

---

### Post by Jose Catre-Vandis on 2010-02-27
You need to create an ~/.asoundrc

Look [here]("http://ubuntuforums.org/showthread.php?p=8630834#post8630834") and read on, and [here]("http://ubuntuforums.org/showthread.php?p=8667623#post8667623") for what to do

---

### Post by amrypma on 2010-02-28
> **caiocc12 said:**
> But does it work for multiple applications? I. e. can you listen to music while playing a game ?

play games, listen music, watch video... sure it works fine.

I've never been sure why you needed a sound daemon. As far as i can tell the only feature it adds is being able te stream music to an other system. I'd rather ssh to that box and run mocp it's much simpler.

---

