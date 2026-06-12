---
title: "sound isnt working right"
date: 2009-05-18
forum: Multimedia Software
---

### Post by mr_gourami on 2009-05-18
Ok this is odd. i just put ubuntu on my dell desktop. 
when i go system sound thing i click test and i hear noise out of my speakers i plugged in. however when i run programs (firefox) it comes out of a speaker built into the computer. nothing comes out my speakers. no idea how this works. amorok works. everything works. but firefox doesnt use the speakers..

is there something in firefox i have to set?

---

### Post by frankzhu on 2009-05-18
I had similar problem with ubuntu 9.04. I upgrade from 8.10 a months ago and it has been working fine. Recently I had my partition table corrupted and I rebuilt it and system is now back. But I can only hear some noise from the speaker. My sound card is nVidia-Realtek. I don't think it's a hardware problem because I find the sound working if I use ubuntu 8.10 live DVD.  And I tried 
sudo touch /forcefsck  
sudo apt-get update
sudo apt-get install --fix-missing

which haven't helped.

Worse case I have to reinstall the system.

---

### Post by kostkon on 2009-05-18
It seems that you have two soundcards and I assume the onboard one has the PC built-in speaker as its default output (only when there isn't anything connected to its output ports, that is). Install the *PulseAudio Device Chooser* utility using *Synaptic*, run it (its menu entry in *Application &#8594; Sound & Video*) and left-click on its icon in your system tray and select *Volume Control*.

Put a *Flash* video playing on *Firefox* and then in the volume control select the *Playback* tab. You should see the audio stream of *Flash* listed there (in the form of Firefox[ALSA] or something similar). Right-click on it and select *Move Stream...* and in the list that will appear select the sound card that your speakers are connected to. *PulseAudio* will remember your choice from now on.

For more info check [this helpful thread]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by mr_gourami on 2009-05-18
well it works. i know it works. it works with amarok, xine all other programs. everything except the internet.

---

### Post by mr_gourami on 2009-05-18
> **kostkon said:**
> It seems that you have two soundcards and I assume the onboard one has the PC built-in speaker as its default output (only when there isn't anything connected to its output ports, that is). Install the *PulseAudio Device Chooser* utility using *Synaptic*, run it (its menu entry in *Application &#8594; Sound & Video*) and left-click on its icon in your system tray and select *Volume Control*.

Put a *Flash* video playing on *Firefox* and then in the volume control select the *Playback* tab. You should see the audio stream of *Flash* listed there (in the form of Firefox[ALSA] or something similar). Right-click on it and select *Move Stream...* and in the list that will appear select the sound card that your speakers are connected to. *PulseAudio* will remember your choice from now on.

For more info check [this helpful thread]("http://ubuntuforums.org/showthread.php?t=1130384").

it worked! thank ou!

---

