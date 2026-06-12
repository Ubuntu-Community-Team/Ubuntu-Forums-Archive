---
title: "Audio Through Both Speakers and Headphones"
date: 2009-10-29
forum: Multimedia Software
---

### Post by MikeWanDo on 2009-10-29
I just installed Ubuntu 9.10 Karmic Koala hoping this would be fixed, but I still seem to have the same issue I had in 9.04, but now I can't even temporarily fix it.

Basically I have two green audio plugs, one in the back of my computer and one on top. The plug in the back is plugged into my monitor which has built in speakers and my headphones are plugged into the plug on top.

The current behavior is that if my monitor speakers are plugged in, sound always plays through them, regardless of whether my headphones are plugged in.

The behavior that I want is that audio *only* comes out of my monitor speakers if my headphones are not plugged in. But if my headphones are plugged in, then audio *only* comes out of my headphones.

I was able to at least manually change whether audio came out of both or only my headphones in 9.04, through the speaker icon on the panel and flipping some combination of switches, but now the speaker icon behavior has changed and I can't fix it that way either (maybe I could, but I don't know what program was used for the settings before, hence the simplistic description of 'speaker icon').

I have tried searching around at least somewhat and I noticed that basically every response asked for this output, so here you go:
> 00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Device 82ea
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fb9f8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

Edit: I at least found how to manually switch between my speakers and headphones. In the output tab of the sound preferences I changed the connector to analog headphones. It didn't work at first but then I opened alsamixer and turned up Front which for some reason gets set to 0 when I change to Analog Headphones (and also when I reboot).

Obviously this is not perfect, and if someone could suggest something to make it work more like my desired behavior, I'd appreciate it.

Edit 2: As a side note: Why can I turn the Output volume over 100% in the output tab but not anywhere else? Also how is going over 100 different, because it sounds louder than 100 so why is going from 90 to 100 different from going to 100 to 110?

---

### Post by dizee on 2009-10-30
I am having the same problem from the Karmic live cd, which is better than the Jaunty one which gave me no sound at all. ;) Have to see if I can fix it in the full install.

Anyway this is most likely fixed here:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Try out the options for your machine or similar, if you can find them.

If it helps I have a very similar soundcard, 82801I (ICH9 family) and the settings for that (in Jaunty) are> 
options snd-hda-intel model=dell-m4-1

---

### Post by GSF on 2009-11-01
i also have this problem with 9.10 :(

edit: im using 5.1 output in alsa, and what i want is when i plug in headphones to mute speakers... for some reason i think ubuntu thinks it only outputs sound through headphones because if i try to mute headphones all sound is muted... !! :(

edit: lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

---

