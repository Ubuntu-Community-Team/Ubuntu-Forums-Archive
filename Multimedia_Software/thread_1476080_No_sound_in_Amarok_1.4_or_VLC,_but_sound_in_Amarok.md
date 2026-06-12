---
title: "No sound in Amarok 1.4 or VLC, but sound in Amarok 2 and Dragon Player?"
date: 2010-05-07
forum: Multimedia Software
---

### Post by clk99 on 2010-05-07
[SEE BELOW]

I just reinstalled my operating system as a way of upgrading to the new Kubuntu 10.4.  I really like it, but I can't seem to get sound in VLC, Amarok 1.4, or in flash.  I'm not sure at all what the problem is because sound works in Dragon Player and Amarok 2.  I don't get any pop-up errors or anything.  Has anyone else experienced this?

---

### Post by clk99 on 2010-05-07
Ah!  Manually setting my sound driver to OSS in VLC and Amarok 1.4 settings fixed those issues.  I still have the flash problem, though.

---

### Post by clk99 on 2010-05-09
Ok, I found out that I don't really want to use OSS, so my problem is that I need to fix ALSA.  What happens when I use the ALSA settings in, say, Amarok, is that it gives me no errors whatsoever.  The music apparently plays (the visualization becomes active), but no sound it outputted.

I have very little experience with sound drivers, so I have no idea where to start.

My soundcard is a Realtek ALC883.

Any ideas?

---

### Post by clk99 on 2010-05-09
I just got a notification today that said something like: "The audio device ALSA is not working properly. Reverting back to ''."

---

### Post by Zorael on 2010-05-09
Messing about with OSS emulation is usually not the way to go, and could be responsible for you getting that message about the ALSA device not working properly.

What you want to do is to open the volume mixer (**kmix**) and raise the PCM volume slider. A common ALSA setup is that you have several volume sliders all affecting output multiplicatively, such as Master, Front and PCM. But not all apps listen to all sliders; notably KDE4 apps (via Phonon) ignore the PCM slider, while Flash and most other non-KDE4 apps obey them all.

So if you have Master at 100%, Front at 100% and PCM at 0%, sound will be at 100% in all KDE4 apps (here Amarok 2 and Dragon Player). Meanwhile Flash will be at 0%, since PCM is at 0%.

My PCM also has a habit of hitting 0% unexpectedly, and I'm not sure why yet. This is one of the things you'd avoid if you use PulseAudio, since it imposes its own single volume slider.

---

### Post by clk99 on 2010-05-09
That did it, thanks.

---

