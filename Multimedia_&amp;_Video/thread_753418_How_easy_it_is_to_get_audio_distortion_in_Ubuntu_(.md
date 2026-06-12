---
title: "How easy it is to get audio distortion in Ubuntu (and how to avoid it)..."
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by caljohnsmith on 2008-04-12
When listening to music in Ubuntu, I am suprised at how easy it is to get distorted sounding music, i.e. music that has been "software amplified" or "digitally amplified", and thus the time-domain waveform  is clipped. In other words, it means distortion that can be heard even when playing back at low volumes over the speakers.

So I did some tests, and here is what I came up with:
**1)** First I created a perfect 1 kHz sinusoidal waveform in Audacity with a peak level of +/-1, or the maximum possible amplitude without being clipped. I then saved it as a .wav file. 1 kHz is somewhat arbitrary; I chose it because it is basically "midrange", so it should be an "easy" tone for the PC to play and record thru the soundcard. This is to avoid frequency effects.
**2)** I then played back the tone with a sound player (more details below), and recorded the tone thru the soundcard with Audacity (not thru my mic of course!). In case anyone wants to replicate this, go to the ubuntu sound control (right click the system tray icon), and under preferences make sure "Mix", "PCM", and "Capture" are checked on. Then make sure that "MIx" is selected under the "switches" tab in the Ubuntu volume control, and you must enable and set volumes for Capture under the recording tab. 

**Here's the results**: adjusting the ubuntu "master" volume has no effect on the recording level (and thus will not cause distortion), but both "PCM" volume and the "Capture" recording volume level do. PCM and Capture can be traded off to avoid distortion, but if for instance you set the Capture volume at 100%, you have to set PCM to 25% or less to avoid distortion! Any amount of distortion is easily detected with Audacity, because the recorded sinusoidal waveform will appear "clipped".

**BOTTOM LINE:**
Using this insight, I found that when I'm playing back music, it is best to set the Master volume at 100%, and then adjust the "PCM" volume for the overall desired sound level in order to avoid any distortion. This seems totally counter-intuitive to me--seems like it should be the other way around!

Based on these findings, I think that Ubuntu should have volume controls set so there is NO digital/software amplification unless the user enables it. This would avoid all these distortion problems that have nothing to do with overdriving my speakers. What does everyone else think?

============================================= 
**An important note on using VLC Media Player for music playing**: if you set the volume in VLC 0.8.6c for anything higher than 50% you WILL get distortion/clipping of any waveform that uses the full dynamic range (i.e. +/-1 amplitude in Audacity). That means distortion regardless of how you set your Ubuntu volume controls! Not many people who use VLC realize this. I've raised this issue with the VLC authors, and they have agreed to improve this in the next major release.

---

### Post by theuninvitedguest on 2008-04-12
Usually I keep my PCM level at about 70% to avoid the effect described above. 70% equals about 1/squareroot(2) , which is the RMS (Root Mean Square) value of a sinosoidal signal with an peak apitude of 1. I suppose the problem lies somewhere there (volume level in respect to RMS or peak value). Just my 2 Euro cents...

Alex

---

### Post by caljohnsmith on 2008-04-12
> **theuninvitedguest said:**
> Usually I keep my PCM level at about 70% to avoid the effect described above. 70% equals about 1/squareroot(2) , which is the RMS (Root Mean Square) value of a sinosoidal signal with an peak apitude of 1. I suppose the problem lies somewhere there (volume level in respect to RMS or peak value). Just my 2 Euro cents...

Alex

I think you hit the nail on the head, Alex, because I did some further testing with Audacity, and it seems that there is no distortion/clipping as long as the PCM volume is kept less than about 70% for playback. You can easily hear the results too when the single tone starts to clip, because of the harmonics produced. Thanks for that insight. :-)

I would still argue that Ubuntu's volume controls should only control the analog amplification by default, and shouldn't do any digital amplification unless the user delliberately uses that feature. That way there's no chance for distortion. In reality, how many people who just start using Ubuntu are going to know that setting the PCM volume>70% could mean distortion? Anybody else have opinions about this?

---

