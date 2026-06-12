---
title: "How to record audio card output and mic input gtk-recordmydesktop"
date: 2011-02-13
forum: Multimedia Software
---

### Post by FWW on 2011-02-13
Hello, I am currently trying to start doing some screen casting and having a problem with audio recording in gtk-recordmydesktop. The problem is that I need to record both; my computers audio card output, and my mic input at the same time. 

As of now I am able to record one or the other.

thank you,
Freedom

---

### Post by perspectoff on 2011-02-13
If I'm not mistaken, that's why PulseAudio was created. 

Try playing around with PulseAudio -- I think you can mix multiple inputs with it.

---

### Post by FWW on 2011-02-13
I have been playing with all the different Pulse Audio mixers and none of them seem to be able to mix the multiple inputs. Unless I am just completely blind

---

### Post by yours-truly on 2011-02-19
Moin moin, (Northgerman for Hello)

I've got the same problem. 
I try to record the PCM (output / soundmix / "what you heare" )Sound with gtk-recordmydesktop but with no success.

Everything else is working fine.
I could switch Output from stereo to 5.1 or 
switch the Input to on of the different USB Microphones.

Of course there is one very simple and stupid way, ... I could short-circuit the line out with line in, but obviously, without a Y-Wire theres no way to hear anything anymore and of course I like to know the other way ....

Any Help is Welcome. Im running Ubuntu 10.10  Gnome Defaults with no Jack installed. (I hope I don't have to, because it looks much more complicated)
Sure I'm forward to find a solution on my own, and will post as soon as I got one.

With best regards from good old Germany,
yt

---

### Post by yours-truly on 2011-02-19
Solved for me Ubuntu 10.10

in gtk-recordmydesktop configure the Audio Device by typing "pulse" instead of "DEFAULT"



Install pavucontrol if you don't have already.
Start your Applications (that should playback a sound), and start recording 
even if you don't hear anything or it don't work at the moment
**It is important that your Record Application is running while configuring!**

now open the pulseaudio device control

choose volume control -> the record *tab
You should see something like
ALSA plugin-in [recordmydesktop]: Alsa Capture from {xyz abc}

If you don't see this - look at the bottom on the right
choose from the dropdown "ALL / all applications" (depending on your language)

If your application is running you should see 
ALSA plugin-in [recordmydesktop]: Alsa Capture from {xyz abc}

There you can switch from {xyz abc} your different devices to internal.

Now you should see the peakmeter showing your output from the source that your are listening.

I hope it works for you too. 

With nice greatings,
yt

---

### Post by xtiano77 on 2012-06-03
Kubuntu 12.04
ATI Video/Sound

This worked for me also. I downloaded the "Pulse Audio" and "Audacity" and started to record with Audacity. Then, I started "Pulse Audio" and went to the record tab and chose to monitor the internal stream and "presto", Audacity started to record audio from Pandora.

---

