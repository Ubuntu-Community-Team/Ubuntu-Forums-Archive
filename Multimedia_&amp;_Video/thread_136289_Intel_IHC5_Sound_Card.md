---
title: "Intel IHC5 Sound Card"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by Tedd on 2006-02-25
Hello. I started running Breezy a while ago with it dual-booted- Breezy/Windows.   I have an Intel IHC5 sound card, four speakers and a subwoofer. In Windows everything is fine, but unfortunately, in Breezy, only two speakers and the subwoofer work. 

I've played around with Alsa all week, to no avail, can anybody help me?

---

### Post by oneTime on 2006-02-25
Post your ALSA settings along with a better description of your hardware and you might get some help. Are you using a laptop with the other 2 speakers behind an external amplifier? If yes, issue [COLOR=Blue]*alsamixer*[/COLOR] at command line and make sure you unmute IEC958 and set the enumeration state of IEC958 Playback AC97-SPSA to zero. This doesn't solve your sound problem for every application though. You might have to explicitly reconfigure some applications to use ALSA. Skype for instance is still trying to figure out how ALSA works. It is a shame that dsp_hijacker is recommended by Skype! They should release their code under GPL and see what the linux community will make out of it.

Onetime

---

### Post by Tedd on 2006-02-25
Sorry.

Using a Dell desktop with four speakers and the subwoofer. I've played around quite a bit with Alsa, but so far what I have right now is:

Master
Master Mono
Master Surround
PCM
Surround
Center
LFE
Line-In
CD
Microphone
Phone
Aux
Capture

---

