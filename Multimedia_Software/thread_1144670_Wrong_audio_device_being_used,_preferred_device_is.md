---
title: "Wrong audio device being used, preferred device is disabled"
date: 2009-04-30
forum: Multimedia Software
---

### Post by mushoku on 2009-04-30
I am new to Linux in general, so I may have missed something, but here is the pertinent information.

lspci -v: (excerpt)
```
08:01.0 Class ffff: Creative Labs SB Audigy (rev ff) (prog-if ff)
    Subsystem: Creative Labs Device 2001
    Flags: medium devsel, IRQ 17
    I/O ports at e000 [disabled] [size=64]
    Kernel modules: snd-emu10k1
```asoundconf list:
```
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
HDMI
```Card I want to use: SoundBlaster Audigy 2 ZS
Output being used: HDMI on graphics card

I have already done everything on the Comprehensive Sound Problems Solutions Guide that appears to be of any potential use, but my sound card is still not available.

Any help will be appreciated.  If you need me to include some other piece of information I will be happy to provide.

Thank you.

---

### Post by psyke83 on 2009-04-30
What version of Ubuntu are you using?

If you're using a recent release, PulseAudio has replaced ALSA's dmix for general audio mixing and playback.

This means that a) "asoundconf set-default" does not work as you expect it to, and b) you need to set the default card through PulseAudio.

See my linked guide.

---

### Post by mushoku on 2009-05-01
> **psyke83 said:**
> What version of Ubuntu are you using?I am running Jaunty, using a fresh install.
> **psyke83 said:**
> See my linked guide.I followed the steps in your guide. All worked well except that when I got to the Pulse Audio Volume Control, the only audio device listed was the virtual device "Null Output."

Thank you for your reply.  I look forward to any further assistance.

---

### Post by mushoku on 2009-05-03
I also have been looking around for a way to enable hardware, but apparently the concept does not exist in Linux - there is disabling, but no enabling.

Seeing as the only method I found for disabling a device was to blacklist its module, I checked the blacklist.  The module for my device was not listed, yet my sound card is still disabled.

Anybody have any further ideas?

---

### Post by mushoku on 2009-05-08
*bump*
Ideas?  I would remove the video card so that the HDMI port would not longer be present, but I do not have another video card to replace it.

---

