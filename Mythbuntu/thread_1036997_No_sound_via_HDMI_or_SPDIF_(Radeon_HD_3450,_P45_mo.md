---
title: "No sound via HDMI or S/PDIF (Radeon HD 3450, P45 mobo)"
date: 2009-01-11
forum: Mythbuntu
---

### Post by gungfujoe on 2009-01-11
I'm quite new to Linux, so I'm probably missing something obvious here, but I can't seem to get any sound from this system at all.  Initially, I tried getting audio via the Asus EAH3450 video card's HDMI output.  When I couldn't seem to get that working (tried disabling the MoBo's onboard audio in BIOS, unmuted in alsamixer...), I decided to fall back on the Gigabyte GA-EP45-DS3L's S/PDIF output

I made sure everything except the microphones were unmuted in alsamixer, and I made sure Alsa:SPDIF was the audio source defined in the MythTV settings via the frontend.  I tried testing sound by playing an Apple movie trailer (my only option right now because I also can't seem to "watch TV" with the tuner, but that's for a separate thread).  No sound.

Obviously, I'd strongly prefer audio via HDMI, but S/PDIF would be an acceptable workaround.  Any help getting either of these working would be greatly appreciated.

I'm running Mythbuntu 8.10 with the aforementioned Intel-based motherboard and ATI/AMD video card.

---

### Post by bimbot on 2009-01-23
I have the same vid card chip; different manufacturer.  If I get it working, I'll definitely post back in here.

So far, I've only done the basics:  unmute in alsamixer, update alsa to 1.0.19....still, no sound.....will update as I go along.

---

### Post by zim2dive on 2009-02-03
> **bimbot said:**
> I have the same vid card chip; different manufacturer.  If I get it working, I'll definitely post back in here.

So far, I've only done the basics:  unmute in alsamixer, update alsa to 1.0.19....still, no sound.....will update as I go along.

I just got a 3450 hoping to work around a bug in the nvidia 8200 IGP on my mobo.

I have sound working over the 3450 HDMI for everything EXCEPT Flash (go figure).

What does aplay -l tell you? My .asoundrc is > pcm.!default {
type hw
card 0
device 3
}

also, not sure if needed, but debugging lots of sound issues with my 8200, I started to always run alsaconf, then alsamixer.

---

### Post by gungfujoe on 2009-02-15
aplay -l lists my HDMI output:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


However, while I get sound fine via S/PDIF, I get nothing over HDMI.  I'd like to get rid of the extra audio cable, but all said and done, this is the least of my problems with Linux.  Even if I solve this problems, the other problems that keep the OS from being usable persist. :(

---

### Post by konadad on 2009-02-15
In the audio setup in the Frontend, try hand typing the following into the Audio Output Device field:

```
ALSA:hwplug:1,3
```

Based on your aplay -l output this stands a chance of driving the audio through your HDMI.

---

### Post by gungfujoe on 2009-02-19
> **konadad said:**
> In the audio setup in the Frontend, try hand typing the following into the Audio Output Device field:

```
ALSA:hwplug:1,3
```
No such luck.  Not only does it not send audio through HDMI, but it continues to send audio through S/PDIF.  I'd have expected it to at least turn the audio off entirely.

---

### Post by allene222 on 2009-02-19
I put this together for digital audio via spdif.  I have gotten a number of inputs on the hdmi part and think it might help you.
[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto)

Please let me know if you find parts either work or don't so I can improve it for the next person.

Allen

---

