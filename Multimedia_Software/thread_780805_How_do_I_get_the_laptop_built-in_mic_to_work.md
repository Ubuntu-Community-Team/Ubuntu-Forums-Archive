---
title: "How do I get the laptop built-in mic to work?"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Th3Professor on 2008-05-03
(Question in subject line.)

Thanks!

---

### Post by linuxwizard on 2008-05-03
Look over this > [http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by Th3Professor on 2008-05-04
That's a helpful thread, it gave me some direction to go with things.

Here's an update:

Manipulating "Volume Control" (multiple settings enabled and turned up) didn't seem to do anything. Not immediately at least.

Using alsamixer made the immediate difference.

On the laptop... alsa mixer "capture" has, from left to right:

Front Mic (set to 100)
Mic Boost (set to 100)
Capture (currently about 50)
Capture (currently about 50)
Digital (currently 50)
Input Source (options: mic or front mic; currently "mic")
Input Source (options: mic or front mic; currently "front mic")
(If the 2nd input source is also set to "mic" there's a high-pitch squeal.)
(If the 2nd input source is set to "front mic" there's a fuzz/distortion.)

I left vumeter -r running during the adjustments made in alsamixer.

Apparently the built-in (front panel, on Toshiba) volume "scrolling" wheel affects the microphone volume as the recording level (in vumeter) goes up or down with the scrolling wheel.

The prob right now is that there's a fuzz/distortion.

Leaving "input source" set to "mic" and the 2nd "input source" to "front mic";
the scrolling-volume (front panel of laptop) adjusts the 1st "capture" bar in alsamixer;
the 2nd "capture" bar increases/decreases the fuzz/distortion as I adjust it within alsamixer.

I try using just 1 "capture" bar, then just the other. Same with "mic" or "front mic";
it looks like both capture bars are required (???). Okay correction, maybe not...

AlsaMixer [Capture] settings appear to work with laptop built-in mic like this, from left to right:
Front Mic - 100
Mic Boost - 100
Capture (1st one) - any level (mic (input) level)
Capture (2nd one) - 0 (this is to avoid the fuzz/distortion)
Digital - 50 (probably could be 0 but leaving it here for now)
Input Source (1st one) - Mic
Input Source (2nd one) - Front Mic

Now to open up a recording app and test the laptop's mic...

Okay, maybe the recording program isn't set up right. (Trying Audacity (am new to it, so going to have to test settings.)) Nope... still no luck.

I amplified the recording and it just played back pulsed fuzz/distortion.

Oh boy... now my front panel volume (scrolling wheel on laptop) is apparently adjusting the mic level... but it is now having absolutely no effect on speaker volume. How do I fix this?

If I go back to the Volume Control, File>ChangeDevice> lists:
0: HDA Intel (Alsa mixer)
1: Realtek ALC268 (OSS Mixer)
2: Playback: ALSA PCM on front:0 (ALC268 Analog) via DMA (PulseAudio Mixer)
3: Capture: Monitor Source of ALSA PCM on front:0 (ALC268 Analog) via DMA (PulseAudio Mixer)
4: Capture: ALSA PCM on front:0 (ALC268 Analog) via DMA (PulseAudio Mixer)

It's a Toshiba Satellite A205-S5855, running Ubuntu Studio (8.04).

(Volume Control is currently at default 0: HDA Intel (Alsa mixer).)

---

### Post by Th3Professor on 2008-05-05
(bump for help if anyone can provide it...)

So far I haven't had luck getting the laptop's built-in mic to properly function. I'm hoping to get it working.

I've also somehow managed to make it so the physical volume control on the laptop now adjusts mic level and not speaker level. I'm hoping to get it back to speaker volume control.

---

### Post by cespinal on 2008-05-06
I had the same problem today... guess you clicked on the wrong place... try going to system>preferences>sound and on the devices tab, refer to DEFAULT MIXER TRACK and choose MASTER...that should bring your media buttons back to normal... 

I am still waiting for a good solution on the non workinh mic tho

---

### Post by Th3Professor on 2008-05-07
> **cespinal said:**
> I had the same problem today... guess you clicked on the wrong place... try going to system>preferences>sound and on the devices tab, refer to DEFAULT MIXER TRACK and choose MASTER...that should bring your media buttons back to normal... 

I am still waiting for a good solution on the non workinh mic tho

Awesome! That fixed it, the volume that is. Very cool.

I'm still having trouble getting the mic to work... will keep experimenting, trial and error I suppose.

---

### Post by R%&amp;92GH&amp; on 2008-08-05
Exactly the same problem here

---

### Post by ross3825 on 2008-08-11
When I go to the Alsamixer window, I can arrow across the bottom to the mic function, but after that, I cannot adjust the volume control.  There is a square above 'mic' with two zeros in it.  

What do I do?

---

### Post by R%&amp;92GH&amp; on 2008-08-11
I think that there is not a way of making the internal micro to work with this soundcard and the current drivers.. 

Meanwhile I am using an external micro plugged to the laptop, and it works well.

I will wait until somebody releases a new version of the drivers..

---

### Post by cdtech on 2008-08-11
Use this command in a terminal to record:
```
arecord -f cd -D hw:0,0 -d 20 test.wav
```
This will create a 20 second wav file in your current directory.
Then playback the recorded sound with:
```
aplay test.wav
```

and see if it recorded any sound.

Let me know..........

**P.S.**
[COLOR="Blue"]see this post for information about how I set mine up[/COLOR]
[http://ubuntuforums.org/showthread.php?p=5567214#post5567214](http://ubuntuforums.org/showthread.php?p=5567214#post5567214)

---

