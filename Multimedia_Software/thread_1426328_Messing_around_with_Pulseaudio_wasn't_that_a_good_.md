---
title: "Messing around with Pulseaudio wasn't that a good idea"
date: 2010-03-10
forum: Multimedia Software
---

### Post by Desim on 2010-03-10
Hi,

I recently installed Ubuntu Karmic 64 bits on my computer from scratch (meaning it's no upgrade or anything).
I had some trouble configuring my sound options (on skype particularly), having two soundcards and a quickcam with mic, it didn't give me the option to chose which one was giving  (and recording) sound during a call.

I found esound which appeared to give much more control over the sound in applications. I replaced pulseaudio with it and it rocked for a minute... But as you guessed it, the problems started there. I didn't have acces to sound preferences anymore and so tried rolling back to pulseaudio. Installation wasn't a problem but I couldn't get any sound out of my jacks. Worse, putting esound back didn't work anymore either. Alsamixer isn't muting any stream so it's not that simple to solve.

I've tried a few guides on the forums and elsewhere but they didn't help, and I better stop with them before I make it worse. I'm hoping someone over here with good knowledge of what's happening in Ubuntu's sound drawers will help me get things back like they were after a fresh installation.

Any help will be greatly appreciated.

Misc. info:
Ubuntu 9.10 64-bits
Alsa v 1.0.21
Hardware:
AMD Athlon 64 X2
Soundblaster Audigy
Nvidia CK804 AC'97 controller

---

### Post by kostkon on 2010-03-10
> **Desim said:**
> Hi,

I recently installed Ubuntu Karmic 64 bits on my computer from scratch (meaning it's no upgrade or anything).
I had some trouble configuring my sound options (on skype particularly), having two soundcards and a quickcam with mic, it didn't give me the option to chose which one was giving  (and recording) sound during a call.

It was a bad idea to remove PulseAudio, yes. Actually the only thing you had to do is to install the *PulseAudio Device Chooser* utility and specify the input and output device for Skype. 
> **Desim said:**
> 
I found esound which appeared to give much more control over the sound in applications. I replaced pulseaudio with it and it rocked for a minute... But as you guessed it, the problems started there. I didn't have acces to sound preferences anymore and so tried rolling back to pulseaudio. Installation wasn't a problem but I couldn't get any sound out of my jacks. Worse, putting esound back didn't work anymore either. Alsamixer isn't muting any stream so it's not that simple to solve.

I've tried a few guides on the forums and elsewhere but they didn't help, and I better stop with them before I make it worse. I'm hoping someone over here with good knowledge of what's happening in Ubuntu's sound drawers will help me get things back like they were after a fresh installation.

Any help will be greatly appreciated.

Misc. info:
Ubuntu 9.10 64-bits
Alsa v 1.0.21
Hardware:
AMD Athlon 64 X2
Soundblaster Audigy
Nvidia CK804 AC'97 controller
When you rolled back to PulseAudio, did you check your sound prefs afterwards? Also, and since you have an Audigy, did you try to toggle the *Analog/Digital* switch in alsamixer?

---

### Post by Desim on 2010-03-10
> **kostkon said:**
> It was a bad idea to remove PulseAudio, yes. Actually the only thing you had to do is to install the *PulseAudio Device Chooser* utility and specify the input and output device for Skype.  That didn't do a thing, I make a fresh install of the same operating system, left PA alone and installed padevchooser, restarted Ubuntu, installed skype, and still only pulseaudio server (local) as the only listed device. (I have faint audio on my onboard nvidia card though, instead of on my SB).

> **kostkon said:**
> When you rolled back to PulseAudio, did you check your sound prefs afterwards? Yes, everything said OK there too...
> **kostkon said:**
> Also, and since you have an Audigy, did you try to toggle the *Analog/Digital* switch in alsamixer?
Uh, how do you do that? :-D
It's detected as SB Audigy 1 ES [SB0160] by alsamixer, if that helps figure out what i have on my screen. I have a big amount of sliders, i don't see which one could be the switch between analog/digital

Thanks for the reply

---

