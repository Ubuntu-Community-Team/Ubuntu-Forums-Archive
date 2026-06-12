---
title: "No sound after upgrade to 13.10"
date: 2013-11-16
forum: Multimedia Software
---

### Post by justinhamsley on 2013-11-16
I've been running Ubuntu Server 13.04 for about six months, using an HDMI connection from my video card (NVidia) to a TV.  Originally I had some issues with sound not working, but at the time an upgrade to a new kernel fixed it (I can't remember the version, though).

I upgraded to 13.10 a couple of weeks ago and my sound broke again.  I played around with all kinds of things, from updating video drivers to NVidia 331, to using daily alsa packages, to updating the kernel to 3.12.  Still, no improvements.  Today I finally reinstalled the OS in an effort to cleanup any mess I've made.  So I have:

1) Fresh install of Ubuntu Server 13.10.
2) Update kernel to 3.12
3) Update video drivers to nvidia-331

I tried installing alsa dailies, but they complain that they won't build for this kernel.

**aplay -l **shows the HDMI audio devices, but **aplay -D** doesn't play anything on any of them.  I've verified the card isn't muted in **alsamixer**.  The motherboard audio is also disabled in BIOS (always has been).  It's like everything recognizes the sound card is there, just won't play through it.  I'm lost what to do next.

I've ran alsa-info.sh already, here's the link: [http://www.alsa-project.org/db/?f=9d8375e80a2ccc98237d556c2b10bfc899efef49](http://www.alsa-project.org/db/?f=9d8375e80a2ccc98237d556c2b10bfc899efef49)

Any help would be greatly appreciated.

---

### Post by progressnerd on 2013-11-17
Sounds like we're in a similar boat, though I don't have an Nvidia video card:
[http://ubuntuforums.org/showthread.php?t=2188393](http://ubuntuforums.org/showthread.php?t=2188393)

Does this combo work for you?
[FONT=Courier New]sudo killall pulseaudio
sudo alsa force-reload[/FONT]

You may have to repeat it on every login, though, like I do, which I'm trying to fix.

Anything in /var/log/syslog related to alsa?
[FONT=Courier New]cat /var/log/syslog | grep alsa[/FONT]

---

### Post by justinhamsley on 2013-11-17
Running those commands has no impact.  I didn't even have PulseAudio installed when I first tried them.  I have since installed it; no difference.

** alsa** does not appear in my **/var/log/syslog**&#8203;.

---

### Post by justinhamsley on 2013-11-21
No ideas?  Does anyone know of a different forum I could try?  The only thing I can think to try now is switch to a Radeon based card and cross my fingers that it works.

---

### Post by progressnerd on 2013-11-21
How about anything in /var/log/syslog related to pulseaudio?
[FONT=Courier New]cat /var/log/syslog | grep pulseaudio[/FONT]

---

### Post by justinhamsley on 2013-11-21
Neither **pulseaudio** or even **pulse** appears in my **/var/log/syslog**&#8203; file.

---

### Post by progressnerd on 2013-11-21
pulseaudio normally writes a lot to the syslog, even when it is completely successful. Are you sure you actually installed it?

---

### Post by justinhamsley on 2013-11-21
**dpkg -l pulseaudio**&#8203; shows that I have 4.0-0ubuntu6 of it installed.

---

### Post by RayDeCampo on 2013-11-21
I experienced the same issue when I upgraded a working machine from 13.04 to 13.10 - no sound via HDMI.  I can get sound from the analog output (after selecting it via Sound Settings in the GUI).  No solution here unfortunately.

---

### Post by justinhamsley on 2013-12-02
Well, some success.  One step forward and another back.  I tried a Radeon card and still did not only not get sound, but developed some other issues.  This morning it crossed my mind that maybe I should try a different HDMI cable (even though it worked in 13.04).  I put the NVidia card back it and switched to a HDMI cable I verified only a few minutes prior.  Anyway, after fiddling I found that the **nouveau** drivers are producing sound, but the **nvidia****-331** drivers aren't. Both cables work fine.  **nouveau** has an entirely different set of issues, though (graphical).  I'll try to work on them separately.

---

