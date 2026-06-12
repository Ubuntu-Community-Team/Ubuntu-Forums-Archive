---
title: "Sound configuration trouble."
date: 2008-11-27
forum: Multimedia Software
---

### Post by BeShrewd on 2008-11-27
I'm new to ubuntu, just installed it for the first time.

I run an old *Sound Blaster Live! Platinum 5.1* which is detected and installed automatically by ubuntu. But I can't get sound off it...

My on-board sound card works fine (Intel card) I tried all the test options in *System->Administration->Sound* all those on the *SB Live* option are mute while the Intel ones work when I connect a headset to that front panel.

Can anyone please help?

---

### Post by kpkeerthi on 2008-11-27
1. Open a terminal and run
```
sudo asoundconf list
```

2. The above command prints all detected soundcards. The output might look something like below:
```

Names of available sound cards:
**[COLOR="Red"]Live[/COLOR]**
ICH6

```
3. Now, set your default card, like so
```
sudo asoundconf set-default-card **[COLOR="Red"]Live[/COLOR]**
```
* Note the lines highlighted. Change it as appropriate for you.

4. Reboot.

If you still can't get sound,
1. Open terminal and type
```
alsamixer
```
2. Use the [controls]("http://en.wikipedia.org/wiki/Alsamixer#General_Controls") to unmute and increase volume levels of the channels, especially, Master, PCM, Headphone.

---

### Post by BeShrewd on 2008-11-27
Thanks for the input...
I did all you said, only got *Master* in the alsamixer..

Still no go, though I do think it's trying to use the Sound Blaster Live! since I don't get sound off the on-board card anymore.

So why am I getting only one channel? I guess there's something to do with that and the fact that I'm not getting any sound.

---

### Post by psyke83 on 2008-11-27
Don't use the "asoundconf set-default-card" method, it's obsolete for Hardy and Intrepid (due to PulseAudio).

Follow [this]("http://ubuntuforums.org/showthread.php?t=789578") guide to configure PulseAudio correctly *and* to find out how to select the correct playback device.

P.S. To get access to your real mixer, you need to explicitly define your hardware device, e.g.:```
$ alsamixer -Dhw
```

---

### Post by BeShrewd on 2008-11-27
Ok.. There's progress now.

The alsamixer extention gave me control over the volumes in the SB Live! which is good.

But when I got to step 5 of the tutorial linked in the last post Pulse didn't give me the option of choosing the SB Live! as a sound card, only the onboard card.

And the System->Preference->Sound still shows the SB but the test doesn't give any sound off it.

---

### Post by kostkon on 2008-12-03
> **BeShrewd said:**
> Ok.. There's progress now.

The alsamixer extention gave me control over the volumes in the SB Live! which is good.

But when I got to step 5 of the tutorial linked in the last post Pulse didn't give me the option of choosing the SB Live! as a sound card, only the onboard card.

And the System->Preference->Sound still shows the SB but the test doesn't give any sound off it.
First of all, do you have your sound playbacks in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) set to *Autodetect* (and not to your *SoundBlaster* card)?

Also, do you mean that if you select the *Volume Control* utility from the *PulseAudio Device Chooser* applet you don't actually see your *Soundblaster* listed in the *Output Devices* tab? It will be listed as *ADC Capture/Standard PCM Playback* or something similar and not as *Soundblaster Live*.

---

### Post by BeShrewd on 2008-12-30
> **kostkon said:**
> First of all, do you have your sound playbacks in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) set to *Autodetect* (and not to your *SoundBlaster* card)?

Also, do you mean that if you select the *Volume Control* utility from the *PulseAudio Device Chooser* applet you don't actually see your *Soundblaster* listed in the *Output Devices* tab? It will be listed as *ADC Capture/Standard PCM Playback* or something similar and not as *Soundblaster Live*.

It is set to auto detect.

And now I see I didn't mention that when I try to open the *Volume Control* I get a pop up box "Connection Failed: Connection Refused" and the window closes. -> This is new. I don't think I've changed anything but after one reboot it just began acting that way -_-

Thanks for the help.

---

### Post by markbuntu on 2008-12-30
This will help you figure out how to get your sound dialed in:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

