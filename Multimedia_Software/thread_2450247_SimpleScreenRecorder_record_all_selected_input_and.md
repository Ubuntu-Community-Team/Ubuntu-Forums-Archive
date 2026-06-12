---
title: "SimpleScreenRecorder record all selected input and output with the video"
date: 2020-09-10
forum: Multimedia Software
---

### Post by sr712 on 2020-09-10
Since COVID-19 I  give a lot of online trainings to my customers. But I like to record the screen and sound.
I use SimpleScreenRecorder which works good. Except for the sound. 
I like to create a new virtual output that combines the standard sound output (Speaker or Headset) and standard input (Micorphone).
If all would be combined speaker, headset and Microphone it would also be ok. Because I can only select one source in SSR.

I tried with pactl but somehow I does not understand it well. I  had to reset the whole config  for the audio devices after I didn't hear any sound anymore.

Help and/or explaination would be really welcome.

---

### Post by TheFu on 2020-09-10
I think you'll need OBS which can switch, mix, mux audio and video inputs in more ways than most people need.

I use SSR for some recordings, but have never tried to capture my voice. Have you looked at the settings in **pavucontrol** to control which audio device is the default for each program? Make certain that the microphone you want to use isn't disabled in the "configuration" tab.  When I try to tell SSR to use the microphone, it doesn't list that as an option in the audio source list.  

When I'm doing training videos, I need 2-3 video inputs and 2 audio inputs, so perhaps that's different from your needs?  

I'm positive that OBS can do this. [https://obsproject.com/wiki/install-instructions#linux](https://obsproject.com/wiki/install-instructions#linux) lists the dependencies. The program has a package in the Canonical repos or there is a PPA.  Package Name is: **obs-studio**

Learning OSB isn't intuitively obvious for normal people. At least it wasn't for me.  I had to watch a few YT tutorials before anything made sense.

Update:  I killed the pulseaudio daemon, restarted pulse and restarted SSR. Then the list of audio input options showed 3 possible inputs. Only 1 can be used, which may be sufficient for your needs.
Kill:  **pulseaudio -k**
Restart: **/usr/bin/pulseaudio --start --log-target=syslog &**

Maybe this will work? IDK.

---

### Post by sr712 on 2020-09-10
Good hint, I already had OBS installed to try out green screen for some training videos I created.
I didn't think to use it for screen capture. Worked after a minute. Now I have to figure out how to
shrink the recorded videos.

---

