---
title: "Need Audio Help"
date: 2008-11-20
forum: Multimedia Software
---

### Post by fullerama on 2008-11-20
OK, so it seems I'm not alone in needing audio help. I have Intrepid and cannot seem to find any way to record streaming audio. Tried Audacity, tried MHWaveEdit, tried sound recorder... all to no avail.  I don't need to do a whole lot on my computer, but one thing I do need to be able to do is record and edit a stream.  Why is this so difficult?

I've read so many "how to"s and threads about audio problems that I don't even know what I'm looking at anymore.

Where I stand right now: removed pulse audio (didn't help), set everything back to ALSA, all the tests work except for "capture", which is where I presume my problem is.

I may not be making any sense because it's late and I'm tired, but if you need any further info in order to make a suggestion, I'll be happy to tell you what I can!

---

### Post by psyke83 on 2008-11-20
> **fullerama said:**
> OK, so it seems I'm not alone in needing audio help. I have Intrepid and cannot seem to find any way to record streaming audio. Tried Audacity, tried MHWaveEdit, tried sound recorder... all to no avail.  I don't need to do a whole lot on my computer, but one thing I do need to be able to do is record and edit a stream.  Why is this so difficult?

I've read so many "how to"s and threads about audio problems that I don't even know what I'm looking at anymore.

Where I stand right now: removed pulse audio (didn't help), set everything back to ALSA, all the tests work except for "capture", which is where I presume my problem is.

I may not be making any sense because it's late and I'm tired, but if you need any further info in order to make a suggestion, I'll be happy to tell you what I can!

You shouldn't have removed PulseAudio. Well, assuming you can re-install PulseAudio properly, this is what to do:

1. Follow [this]("http://ubuntuforums.org/showthread.php?t=789578") guide completely, with particular emphasis on Steps 4 & 5 of Part A.
2. Open the GNOME Sound Recorder, and with your microphone plugged, begin recording.
3. Open the "PulseAudio Volume Meter (Recording):
```
$ pavumeter --record
```
4. Check your volume levels. The GNOME volume control applet sometimes hides vital switches or mixers, so go directly to the source instead:
```
$ alsamixer -Dhw
```
[COLOR="Blue"]**Note:** Press "tab" once to switch to the Capture view.[/COLOR]

5. Experiment with all the volume sliders and switches, while keeping an eye on the Sound Recorder's volume indicator *and* the PulseAudio Volume Meter.

Once you enable the right switch or mixer, you'll see activity on both of those applications.

---

### Post by fullerama on 2008-11-20
Thanks, pskye83.  I'll be back at my computer later today and I'll try your steps then.  I have not used a microphone yet in trying to get the recording set up (I think I have one) because it's stream recording I'm most interested in.  I saw another post recommending the removal of pulseaudio, and that's why I did that.  It seemed to cause some problems, though, beyond the audio issue. I was not able to log on this morning, and had to go to a failsafe log in.

Would I be OK to perform your steps in failsafe?

---

### Post by fullerama on 2008-11-20
pskye83- I reinstalled pulseaudio and my system is back to booting up properly now. Audio sounds good, but I still have the problem of not getting a stream into a recording device (Audacity, MHWaveEdit and Sound Recorder). All the record levels seem to be set properly, but nothing gets recorded.  Any ideas on what I might be doing wrong?

---

### Post by fullerama on 2008-11-20
Very nice tutorial, BTW.

---

