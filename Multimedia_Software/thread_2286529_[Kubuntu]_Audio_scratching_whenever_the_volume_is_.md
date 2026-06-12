---
title: "[Kubuntu] Audio scratching whenever the volume is altered."
date: 2015-07-12
forum: Multimedia Software
---

### Post by Hamish_Claxton on 2015-07-12
Hey Guys

Recently I got audio working with Wine by modifying the following two lines in ```
/etc/pulse/daemon.conf
```:
```

 default-fragments = 5
 default-fragment-size-msec = 2

```

Shortly after I started getting audio scratching whenever I alter the volume for any application. Tried changing the above settings to default however no change.
I'm at a loss of what to do next. If anyone could help, it would be greatly appreciated.

Thanks in Advance,
Hamish

---

### Post by Bucky Ball on 2015-07-13
Welcome. How do you mean you got audio working with Wine? Working with programs you are using in Wine or you installed some third-party audio driver intended for Windows using Wine? If the latter, which and why?

---

### Post by Hamish_Claxton on 2015-07-13
Well I wanted to play some Windows only games, and when they ran the audio was fast, crackling, popping etc. Changing the above settings fixed those issues. However afterwards I started to get audio scratching whenever I altered the volume for any application.

---

### Post by Bucky Ball on 2015-07-13
Are you sure these games are fully functional in Wine? Many aren't. Do a search for them [here]("https://appdb.winehq.org/") and find out if you haven't already.

---

### Post by Hamish_Claxton on 2015-07-13
Yes they are fully functional. I was playing Star Trek Online through steam, for quite a few hours and no crashes. Everything worked fine. Same with Homebrew - Vehicle Sandbox. Only issue is the audio scratching in all applications and not limited to Wine.

---

### Post by Bucky Ball on 2015-07-13
Odd. So this is global? Happens in Ubuntu sound also? Just playing music or a video non-Wine? Not specific to Wine?

If you change the two lines you altered back to what they were, does sound stop in Wine but is fixed in Ubuntu au naturale? I would say it has something to do with that. Is this machine fairly new with decent specs and RAM? Maybe you are increasing the sample rate or something else as that would cause sound to break and crash if the machine can't handle to rate.

---

### Post by Hamish_Claxton on 2015-07-13
Yes, that is correct. Sorry if I didn't make it clear before.
Audio scratching still occurs even when I changed them back, and yes the Wine audio goes haywire again.

I'm running a Dell Precision M4800:
Intel i7-4800MQ
NVIDIA Quadro K1100M
16GB Ram

Here's a Hardinfo report: [HTML]https://mega.nz/#!RZRRFSRI!jgwFQRTLugJQsx6J4jHciwviSK6BlVME1UcDgRbOHu0[/HTML]

---

### Post by Bucky Ball on 2015-07-13
In that case:

*Thread moved to **Multimedia**.*

Also, I added something to last post you may have missed. Sample rate. Machine specs.

---

### Post by Hamish_Claxton on 2015-07-13
Yep, as well just in case you missed it, I added the machine info to my previous post.

---

### Post by Bucky Ball on 2015-07-13
Hmm, well those specs should handle anything you can dish out re. sample/bit rates ... :-k

You've probably checked, but in Pulseaudio Volume Control, can you get an audio stream happening and check Output and Playback tabs. Is the correct device being used?

---

### Post by Hamish_Claxton on 2015-07-13
Yeah correct device is being used.

---

### Post by Hamish_Claxton on 2015-07-15
Any other suggestions?

---

### Post by Yellow Pasque on 2015-07-15
Try resetting user's pulseaudio configuration:
```
rm -r ~/.config/pulse*
```
Log out/in

---

### Post by Hamish_Claxton on 2015-07-16
Unfortunately didn't help, I downgraded to 14.04 from 15.04 and the Audio issue is still there even on a clean install. Some incompatibility with my sound card?

---

### Post by Hamish_Claxton on 2015-07-16
Are there any other audio drivers I could try apart from PulseAudio?

---

### Post by Hamish_Claxton on 2015-07-16
Disabling the Volume Feedback in KMix fixed the issue. Still a slight bit of audio scratching when using the Wine ALSA Plugin, however I guess that's just one of the many issues when using Wine.

---

