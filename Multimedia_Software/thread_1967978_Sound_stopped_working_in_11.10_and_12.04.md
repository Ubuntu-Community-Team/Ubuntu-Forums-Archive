---
title: "Sound stopped working in 11.10 and 12.04"
date: 2012-04-28
forum: Multimedia Software
---

### Post by francoj11 on 2012-04-28
Hi there, about a month ago I did a fresh install of Kubuntu 11.10,  did the updates that the systems recommended and everything was ok with the sound, but suddenly one day I turned on my computer and there was no sound at all (this happened like  2 weeks ago).

Yesterday I upgraded to Kubuntu 12.04 to see if sound would magically start working again, but nothing happened, so I decided to do a fresh Install of it, and sound worked great. Once again, I updated some packages that were recommended, reboot a couple of times and sound worked fine. But today I turned on my computer and found that there was no sound again.

This is what I have tried so far (in kubuntu 11.10, and 12.04):
- There is nothing muted, kmix and alsamixer are both no-muted
- Sound works great in Windows, and in a live cd of kubuntu 12.04
- I remove ~/.pulse and ~/.pulse-cookie and then reboot, but nothing happens
- I have a soundblaster audigy SE
- In Kubuntu 11.11 I tried using olders kernels that were listed in grub, but none had sound (in Kubuntu 12.04 I only see one kernel)
- This is my alsa information: [http://www.alsa-project.org/db/?f=d963a86e1865c79068e1f38fa544a1503a5fa015]("http://www.alsa-project.org/db/?f=d963a86e1865c79068e1f38fa544a1503a5fa015")
- I have an onboard sound card, but its not ativated (I deactivated in the BIOS)
- I tried to reload alsa with
```
sudo alsa force-reload
```
     but still no sound.

Any ideas of how to start troubleshooting my problem?

---

### Post by SeijiSensei on 2012-04-28
Make sure that the right output devices are being used in System Settings > Multimedia > Phonon.

---

### Post by francoj11 on 2012-04-29
They are ok, they are the exact same as used in the live cd.
With the live cd I do have sound, but still no sound in the installation of my hard-drive..

Any other ideas?

---

### Post by francoj11 on 2012-04-29
I algo forgot to mention that I installed pavucontrol, and whenever I try to play a sound (like a song, or a video), there is a bar moving like if there were sound, but no sound come out from speakers.

---

### Post by AxxE on 2012-04-30
I think following the steps in the comprehensive troublehsooting guide at [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure), for your ubuntu version, should help you resolve the problem...

---

### Post by francoj11 on 2012-04-30
Thank you for passing by AxxE. I did follow that guide, and still no sound.
One thing that I noticed before and after doing that guide is that when I ran the alsa_info.sh script, this are the versions of Alsa:
> !!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25

I don't know if this may be a problem or not (different versions of driver, and libraries/utilities).
I want to remind that I did have sound when I did the fresh Install of Kubuntu 12.04, then I did the suggested updates, reboot a couple of times and there was still sound. But on saturday I turned of my computer and there was no sound at all, not even between reboots and log-in.

---

### Post by francoj11 on 2012-04-30
Well, its seems to be that the versions of Alsa are not the problem, I boot from the live Cd of Kubuntu 12.04, and ran the alsa_info script, this was the output.
[http://www.alsa-project.org/db/?f=223cf89b9db2cb6b006f86773e3d4a17b21fa8ed](http://www.alsa-project.org/db/?f=223cf89b9db2cb6b006f86773e3d4a17b21fa8ed)

---

### Post by francoj11 on 2012-04-30
Wow I finally figure it out!
In Alsamixer I had S/PDIF unmuted, and I had to mute it! I dont understand what is that, but that was how it was in the live-cd, and it worked ok in my installation!
Now sound is back, I don't know how that could happend. Hope this works for someone else!

---

### Post by PJW9779 on 2012-07-31
WTF!! francoj11 is correct!! :KS to you, my sound is back.
I'll figure out S/PDIF later.

---

