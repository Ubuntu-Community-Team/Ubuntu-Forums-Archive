---
title: "No sound from Mic"
date: 2009-11-24
forum: Multimedia Software
---

### Post by Robbyx on 2009-11-24
I would appreciate help on testing a mic. 

I bought a cheap mic for IM. Plugged it into the mic socket. Ran the sound recorder in applications and played back: nothing. 

Sound prefs:

Playback OSS
Music & Video playback: HDA INtel ALC888 (ALSA)
Audio Conferencing: Autodetect
Sound Capture Pulse

Default mixer tracks HDA ALsa

Robin
Intrepid.
Gigabyte GA-EP35 mother board

---

### Post by Senuf on 2009-11-24
Hiya.
Let me stand in the same queue for (I guess) the same problem.

I have Karmic Koala too, and my motherboard is a Gigabyte G31M-ES2C (Rev. 1.x).

Two different microphones (I thought it was a faulty mic, so I borrowed another one)  and no results so far.

Any hint would be much appreciated (not to mention a *solution*!).


Senuf

---

### Post by r0n1n0x47 on 2009-11-24
I was experiencing a similar problem with my external microphone. Fortunately my fix was quick and simple. Anyway here's what I did, hope it helps. Before anything, make sure that the microphone is not muted in sound preferences. If everything is okay there try this.

1. open a terminal window
2. type in alsamixer
3. arrow over to <digital>
4. toggle the option to Analog I

After doing this I was able to record no problem.

---

### Post by Senuf on 2009-11-24
> **Senuf said:**
> Hiya.
Let me stand in the same queue for (I guess) the same problem.

I have Karmic Koala too, and my motherboard is a Gigabyte G31M-ES2C (Rev. 1.x).

Two different microphones (I thought it was a faulty mic, so I borrowed another one)  and no results so far.

Any hint would be much appreciated (not to mention a *solution*!).


Senuf


Solved for me.
Found solution here:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=alc883]("http://ubuntuforums.org/showthread.php?t=789578&highlight=alc883")

Perhaps it's a good thread for you too.

---

### Post by Robbyx on 2009-11-24
> **r0n1n0x47 said:**
> I was experiencing a similar problem with my external microphone. Fortunately my fix was quick and simple. Anyway here's what I did, hope it helps. Before anything, make sure that the microphone is not muted in sound preferences. If everything is okay there try this.

1. open a terminal window
2. type in alsamixer
3. arrow over to <digital>
4. toggle the option to Analog I

After doing this I was able to record no problem.

I have followed the above but I can not see an option to toggle to analog. Under Mic is says 00, 61<>61. Nothing about either analog or digital.

---

### Post by r0n1n0x47 on 2009-11-24
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

this is my mixer, the digital option is third to the last. For my configuration, my external mic worked when this option was changed to anolog I

---

### Post by chute on 2009-11-25
I had similar problems on an MSI based laptop. Since the recent updates to 2.6.31-15 the external microphone now works as microphone 1 and the internal one as microphone 2. Before the above update, I couldn't connect the external Mic port at all.

---

