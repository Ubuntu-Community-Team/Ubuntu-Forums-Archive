---
title: "Cannot get sound to work in Mplayer"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by innoBy on 2008-01-20
Sound Events: Autodetect
Music and Movies
Sound Playback: MultiChannel
Conferencing
Sound Playback: Autodetect
Sound Capture: ALSA: Advanced Linux Sound Architecture

Default Mixer Tracks:
Device: Audigy 4 [SB0610]: ALSA mixer

Now sound works in the default Ubuntu media player, but playback is a bit choppy.
Does anyone know how to get sound to work in MPlayer? or does anyone know of a good media player and can tell me how to get it installed. I'm a Windows User recently converted to Ubuntu, if you've seen any of my other posts I've had issues. Since I am primarily watching video media in formats such as MKV and mp4 I need a powerful video player that can handle these formats without chopping.
In windows I was used to using CCCP it was just too easy to use.

Again, any help is appreciated

---

### Post by innoBy on 2008-01-20
VLC has the same issue, but it as well will play video files sans chop.

No audio and good image or good audio and choppy video. plz halp.

I can't have my games and it's looking like I might have to live with choppy video.

(Windows install cd no longer works on my PC I'm stuck with Ubuntu.)

---

### Post by kko1 on 2008-01-20
Hello.

I'd like to help, but not sure I can.

I do have at least one suggestion though. I'm not sure if you run *mplayer* from the command line or from the graphical UI. You could try running *mplayer* from the command line, and specify the additional parameter "*-ao help*". (The "ao" stands for "audio output (driver)".) So, try different ao drivers and see if one of them works for you.

```
mplayer -ao help
```
...will show you the options available, and...
```
mplayer -ao XXX yourfile.ogg
```
...where XXX is the selected driver, will let you test if the driver works with your setup.

If you find one that works, you can make it the default by adding "ao=XXX" to *mplayer*'s config file at *~/.mplayer/config*.

Hope this helps.

kko1

---

### Post by innoBy on 2008-01-20
Well, right now alsamixer seems to be detecting my onboard sound card...so how do I get that to change? Oh, and sound works when I plug into my onboard sound, but that's not the sound card I want to use

---

### Post by innoBy on 2008-01-20
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 4 [SB0610]], device 3: emu10k1 [Multichannel Playback]
```

and when I open up ALSAMIXER using -c 1 I can't unmute my sound card.
So what the problem is right now is disabling my onboard sound, and enabling only my audigy....how do I do that?

---

### Post by kko1 on 2008-01-20
Haha, I was just going to suggest using *alsamixer -c 1* - but you tried that already.

One crude but effective solution, for the moment, and one that I'm using myself, actually. If you don't need the onboard sound for anything at all, you should be able to turn it off from your computer's *BIOS*, which you can usually access by pressing *DEL* when the computer is just starting up.

This way you'll be left with your Audigy as the only sound card, and Ubuntu will most probably automatically use that.

Later on, if you want something special, like movies through Audigy (and speakers) and IP telephony through the on-board card (and headphones), you can always reactivate the onboard card. (I'd like something like that myself, occasionally.) You'll have to explore the settings for different cards in that case. ;)

Again, HTH.

kko1

---

### Post by innoBy on 2008-01-20
I actually just finished doing that with a slight detour into reinitializing my video drivers, I rebooted and got stuck with an 800x600 desktop :-P that's evil and impossible to work with when you're used to 1400x900.

---

### Post by kko1 on 2008-01-22
Nice to see you apparently got the issue solved. May I suggest marking the thread "solved" (from the thread tools), so it shows right in the listings and forum searches. :)

Enjoy your *buntu.

kko1

---

