---
title: "Severe alsa sound jitter with RME HDSP 9632"
date: 2009-07-10
forum: Multimedia Software
---

### Post by zob on 2009-07-10
Hi.

In the process of getting my RME HDSP 9632 work with my ubuntu installation (without having to reinstall) I've had to uninstall pulseaudio, which apparently can't recognize the RME HDSP sound card.

Now I'm left with just alsa which would be ok, if it wasn't for a terrible jitter when I play back.

Well, not always. VLC works fine (I'm starting to think that I could drop my computer in the ocean and VLC would still play). Audacity also works great.

Flash, to my big surprise, also works just fine.

So actually it's just my beloved rhythmbox that doesn't and, seemingly, any other audio player with a good library function.

I've tried rhythmbox (jitter), exaile (jitter), amarok (doesn't play), audacious (doesn't play), xmms (jitter), songbird (jitter) well quite a lot.

I would like to know if it's a gstreamer thing, a hardware thing or another thing. I've reinstalled alsa, and installed latest version. Everything is apparently okay (hardware found, recognized, modules loaded, etc.), except from the sound.

By the way. Just as an example. This is the error from audacious
```
** (audacious:8784): WARNING **: Failed to connect to server: Connection refused
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin
```

Rhythmbox doesn't report any errors, and happily plays away with an unbearable result. It seems like just an application problem that some apps have. I would be happy if just rhythmbox would work or songbird for that matter.

Oh. And also. I installed ubuntu-studio on a usb-device from scratch. And sound works just fine after removing pulseaudio. So I could fix it by reinstalling from scratch, but I'd rather not. There must be a quicker fix.

What to do from here? I'd appreciate any help I can get from you guys.

---

### Post by zob on 2009-07-10
OK. Solved.

I just installed the same real-time kernel that ubuntu-studio uses (2.6.28-3-rt). That solved it.

So if anyone with is having trouble with a RME HDSP sound card, the solution is to:
1. Uninstall pulseaudio (as it obviously doesn't support this card).
2. Install latest real-time kernel.

And you will have the best sounding machine ever.

---

