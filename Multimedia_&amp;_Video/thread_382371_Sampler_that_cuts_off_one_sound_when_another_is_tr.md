---
title: "Sampler that cuts off one sound when another is triggered"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by bgryderclock on 2007-03-12
Is there a Linux application that plays and groups samples so if one sound is cut off when another sound is played?

(ie. something that will allow me to play an A# on my MIDI keyboard to play a sample of a piano loop and then play a C# to cut off the piano drum loop and play a guitar  loop.

This is the last obstacle to finally converting to Linux for music creation and live performance!  :mrgreen:

---

### Post by bgryderclock on 2007-03-16
> **bgryderclock said:**
> Is there a Linux application that plays and groups samples so if one sound is cut off when another sound is played?

(ie. something that will allow me to play an A# on my MIDI keyboard to play a sample of a piano loop and then play a C# to cut off the piano drum loop and play a guitar  loop.

This is the last obstacle to finally converting to Linux for music creation and live performance!  :mrgreen:[/I]


Woo-hoo!!!1  \\:D/ 

**_ANSWER:_**

SooperLooper does it!  
You can set it up to act just like Native Instrument's Battery Sampler Program.


1) Get connectivity between your Midi device and your computer. I have an **M-Audio oxygen 8 **so I used this thread:

[http://www.ubuntuforums.org/showthread.php?t=96506 ]("http://www.ubuntuforums.org/showthread.php?t=96506")

2) Start Jack. I used an app called **qjackctl** to start it.

3) Start **SooperLooper.**

4)  Connect your keyboard  to the SooperLooper app in **qjackctl**. I used the **Connect button** and then dragged and dropped my 'readable' midi client to the 'writable' SooperLooper client. see the attached pic below.

5) In SoopLooper click **Session > Preferences > MIDI bindings ** 

6) This part is a little weird. the controllers on the SooperLooper are midi controllable but that work  like toggles, so it you try to mute a already muted note. it will play it.  so to get one MIDI note to cut off a playing sample and not restart it you have to assign two 'silencing functions' like MUTE and SCRATCH MODE 

To get the loops starting and cutting off the way I wanted i sat up my SooperLooper preferences as show in the Pic below.

***please reply if you know of an easier way to get a midi note to kill a playing samples without restarting them if you play the MIDI note twice.*

---

### Post by bgryderclock on 2007-11-14
This still works in Gutsy 7.10 :mrgreen:

---

