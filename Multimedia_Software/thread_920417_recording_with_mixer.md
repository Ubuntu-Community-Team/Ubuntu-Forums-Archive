---
title: "recording with mixer"
date: 2008-09-15
forum: Multimedia Software
---

### Post by vwbug on 2008-09-15
Problem: No selection to record from the mixer.
In volume control, under options, I only have
mic, front mic, line and CD.  I have recorded from line in from a cassette player, but can't record from just whatever goes through the sound card. I'm using Ubuntu 8.04.
Thanks for any help.

---

### Post by vwbug on 2008-09-17
Well, I put an old sound card in that I had. Now it give me the option of recording with "mix". It works just fine! Still would like to know why I was not given the option with the onboard sound.
The onboard sound on my gigabyte motherboard is a realtek alc888. Has anyone else had this problem?

---

### Post by paulg on 2008-09-17
So if I understand you correctly if you can hear it, you want to be able to record it?

What is your 'old' card? It probably comes down to available features/drivers for the different cards/chipsets.

---

### Post by vwbug on 2008-09-17
> **paulg said:**
> So if I understand you correctly if you can hear it, you want to be able to record it?

What is your 'old' card? It probably comes down to available features/drivers for the different cards/chipsets.

Yes, if I can hear it, then be able to record it, which I can now do with the old card. Its a Aureal Votex Au8820. Also says Turtle Beach on it.  Just would like to know if anyone else has this problem with the ALC888 and if they were able to fix it.

---

### Post by markbuntu on 2008-09-17
There is some info here on  setting up the ALC888 that may be helpful:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by Ramaddan on 2008-11-22
This worked on Intrepid.

First set all devices to **_PulseAudio Sound Server_** in:
> System->Preferences->Sound

Make sure at least the following are installed by running the following line in a terminal:

> sudo apt-get install pavucontrol pavumeter

After finishing the installation, run the following in Alt+F2:
> pavumeter

Keep this running, and it might help to choose the option of keeping it always on top.

Then run the following in Alt+F2:
> pavucontrol

In pavucontrol (PulseAudio Volume control), go to the following tab:
> Recording

All programs that can be recorded will show in this tab, and they will not show unless they are running.

If pavumeter (PulseAudio Volume Meter) is still running, you should see it in the "Recording" tab in Volume Control.

Play something with Totem or any other program (as long as it uses PulseAudio), and then click on the right arrow next to PulseAudio Volume Meter in the "Recording" Tab.

> A drop down list should come up, choose "Move Stream" then "Monitor Source (something)".

If you are playing something, then the bar should be moving in PulseAudio Volume Meter.

If that works, then you know that PulseAudio is monitoring the audio you are playing.

Now go to:
> Application->Sound and Video->Sound Recorder

You will notice that "Sound Recorder" will still not show in the "Recording" tab.

If you press "Record" in "Sound Recorder" though, it will show up in the the "Recording" Tab in Volume Control.

> Choose the right arrow next to "Record Stream", then choose "Move Stream" and then "Monitor Source (something)".

You should now see the record level in "Sound Recorder" change properly.

This setting will save for "Sound Recorder" every time you run it, and you should be able to record anything you hear on it.

You will need to do the same for any program you use to record sound, by choosing the sound stream for it in Volume Control recording tab.

Hope this helps

**Note: Only works for programs that go through PulseAudio**

---

