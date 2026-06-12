---
title: "Ways to record audio from the desktop?"
date: 2015-12-26
forum: Multimedia Software
---

### Post by AGTG on 2015-12-26
I tried Pulse Audio with Audacity, but then I lost all audio. Are there other ways to record audio from the desktop? Perhaps a program or something? 

Thanks in advance.

---

### Post by TheFu on 2015-12-26
I use audacity for microphone things.
SimpleScreenRecorder is another option.
OBS is the last, most complex option.

But all of these use either pulse or alsa for the audio, so it is unlikely any will work any better if the pulse settings on the system aren't working.

---

### Post by deadflowr on 2015-12-26
I've used [pavucontrol]("https://apps.ubuntu.com/cat/applications/pavucontrol/") , go to the input devices section, then go down to *Show:* and change it from *all except monitors* to either *monitors* or *all input devices*.
Then you should be able to record from the desktop.

Here's a reference on how to do it with audacity:
[http://manual.audacityteam.org/o/man/tutorial_recording_computer_playback_on_linux.html](http://manual.audacityteam.org/o/man/tutorial_recording_computer_playback_on_linux.html)
The trick is you need to start the recording in audacity first, in order to apply the settings in the recording section of pavucontrol.
I simply start the recording and pause it, then apply the settings and then unpause when ready.

---

### Post by Dennis N on 2015-12-26
If you mean record the output of your sound card, try Audio Recorder:

[https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)

(In case you didn't see post #5 on your previous thread)

---

### Post by AGTG on 2015-12-26
> **Dennis N said:**
> If you mean record the output of your sound card, try Audio Recorder:

[https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)

(In case you didn't see post #5 on your previous thread)

How can I get this program into my software center (it isn't currently listed).

---

### Post by Vladlenin5000 on 2015-12-27
> **AGTG said:**
> How can I get this program into my software center (it isn't currently listed).

It won't be until you add the aforementioned PPA.

```
sudo add-apt-repository **ppa:audio-recorder/ppa**
sudo apt-get update
```

Now it is and you can install it with the usual GUI tools or simply
```
sudo apt-get install audio-recorder
```

---

### Post by shantiq on 2015-12-27
using command-line [SoX]("http://ubuntuforums.org/showthread.php?t=1710642&p=11053351#post11053351") fairly easy

---

### Post by yoshii on 2015-12-27
There's a console command "rec" (for record) which is a part of SoX.  It's pretty easy to use.  Just press Ctrl-Z to stop.  I forget the main syntax, but type "rec" and it will list it's syntax.

---

### Post by shantiq on 2015-12-27
hi Yoshi yes it the one [here]("http://ubuntuforums.org/showthread.php?t=1710642&p=11053351#post11053351")

---

### Post by AGTG on 2015-12-27
I appreciate everyone's input, but I stumbled upon a tutorial which references a blog with a few lines to copy and paste to load up Audio Recorder, and yes, Dennis, it's an awesome option. Very simple. It's exactly what I need. 

thanks! 

[https://www.youtube.com/watch?v=lZ3qRwM1lcE](https://www.youtube.com/watch?v=lZ3qRwM1lcE)

---

