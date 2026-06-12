---
title: "Microphone recording with annoying noise"
date: 2010-07-12
forum: Multimedia Software
---

### Post by Shangir on 2010-07-12
Hello everyone.

I'm running Ubuntu Lucid 64 Bit along with Windows 7 on my machine. My onboard sound chip, a Realtek ALC889A codec (HD audio), works fine under both operating systems - well, at least the sound output does. Recording does work great under Windows, but not so well under Ubuntu.

With Ubuntu I always get an extremely annoying popping noise when recording. It repeats in a very steady 1 second interval and does never stop, even if I unplug my headset (and therefore my microphone). Only if I mute the mic in the system's sound settings does the noise stop playing.

When I actually have the mic plugged in and it picks up my voice, the output consists of said popping noise - with a very faint, distorted and elongated echo of my voice talking.

What I already tried:
- Playing around with the settings in alsamixer: All input channels are muted in the output section, both mic boost and volume are tuned up in the input section (if I tune one or both of them down, the popping doesn't stop, it just gets fainter)
- Plugging the headphones into the rear mic jack as well as into the front panel jack - there's no difference
- Searching on both Google and these forums for possible solutions, but didn't find anything addressing my problem

Possible causes:
- My chassis doesn't support HD audio; it was built during the AC'97 area. The panel connectors on the mainboard do fit the ones on the chassis, however. On Windows, the Realtek drivers come with a control panel that can enable or disable the front panel jack detection; disabling this solves any sound problems occuring due to the chassis not supporting HD.
- Driver problems? As far as I know, the latest Linux drivers from Realtek are installed on my system.

Unlikely causes:
- Defective hardware. The headphones work just fine under Windows; same  goes for the sound chip.

Sorry for the wall of text. I still would appreciate if you actually read all this stuff and help me solve this annoying problem that forces me to always switch into Windows if I want to talk to people in Skype or Teamspeak.

I'm not an experienced Linux user - if you need additional information about my system to help me with this, just tell me, please.

Neither am I a native English speaker. Any mistakes in this and any further posts can be blamed on that fact.

---

