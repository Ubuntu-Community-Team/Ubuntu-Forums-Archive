---
title: "Audio interface issue"
date: 2011-12-02
forum: Multimedia Software
---

### Post by tbear2500 on 2011-12-02
I must first apologize for the non-descriptive title.  I don't know exactly how to summarize my problem.

A while back I made some changes to my computer's sound software, trying to make it so that I could record the system output to Audacity.  I installed pulseaudio and used its utility to send monitor of stereo out (or whatever it was called) to Audacity, either under 10.04 or 11.04.  I believe my system was previously configured to use ALSA.  Around that time I also installed a new graphics card with HDMI out, which for a while tried taking over my sound output (nVidia 460 GTX).  Sometime around both of these changes, I lost the ability to use my keyboard's volume control.  The system receives the signal and shows the volume slider in the upper right, but the output volume does not actually change.  Under System Settings->Sound the only listed output device is the HDMI from the nVidia card.  If I run alsamixer (which I also started using to enable my computer to act as a sort of amplifier for my electric bass) I can change actual output volume using the Master control or the specific output device control (headphones/speakers).

Is there any way to get the system to realize that it is sending sound to a different card and make the keyboard control work again?

I apologize for the sketchy details, but it was long ago that I did most of this and I should have posted this then when I remembered everything.

---

