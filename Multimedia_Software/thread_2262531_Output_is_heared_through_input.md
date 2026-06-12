---
title: "Output is heared through input"
date: 2015-01-25
forum: Multimedia Software
---

### Post by o-l-lewinsohn on 2015-01-25
Hey guys, I'm using Ubuntu 14.10 though the problem is sadly a lot older. 

My headphones have a microphone connected to them but they are connected to the computer with one cable, so no one cord for input and one for output, these are new ones I bought recently from Philips but I had some others from Meelelectronics before and the problem was the same, they were with the same one cable build as well. 

My problem is when I for example skype with someone, he will hear the music I'm hearing in the background or anything which is played on my computer, which maybe in some cases preferred, but is mainly a bother for me and I'd like to disable that, meaning i'd like to prevent from the sound to be automatically redirected from output to input. 

My configuration is analog stereo duplex in pavucontrol, the computer is the New Samsung 9, and the problem occurs even when I use the laptop builtin microphone (configured through pavucontrol) and the headphones only as headphones. 

Anyone have any idea how to achieve the wished behavior ?

---

### Post by ajgreeny on 2015-01-25
Why does it seem wrong to you that when you are using skype, presumably to talk to somebody, they are able to hear music that you can hear?
Surely this is to be expected as the mic will pick up what you're hearing just as much as your voice.

Sorry if I've misunderstood what you mean, but your explanation is not clear to me.  It should, however, be possible to set different levels for microphones (usually 2 of them, front and back) and headphones in pavucontrol, and/or in alsamixer.

---

### Post by o-l-lewinsohn on 2015-01-26
So I'll put it in simpler words (hopefully, I find it sometimes hard to define stuff), when I skype with you and hearing a music clip on youtube at the background, I wouldn't in most cases like you to hear it as well, as it may bother you during our conversation. 
Or let's say we play an online game together you'd like to skype with me through but not hear the noises of my game, you have your's after all and they are enough, anything more is just a distraction.

I suspect it shouldn't be like that as I was using Skype since its early versions on Linux and that didn't happen, moreover even if it were the default expected settings, there must be a way to change it, probably a command or two through the command line playing with the sound channels, though I never done that so I'll be happy for any help.

---

### Post by ajgreeny on 2015-01-26
OK, I think I now follow you better; there is some leakage of the sound you are hearing through your headphones into the microphone which is plugged in using the same cable, being a dual purpose item; am I correct?

Regrettably I am not sure I have an answer for you other than new separate hardware, or at least hardware with separate input and output cables.

Sorry!

---

### Post by o-l-lewinsohn on 2015-01-26
[SIZE=2][FONT=arial]I still appreciate u taking the time.
 
[/FONT][FONT=arial]I suspect the headphones one cord build up isn't the problem, as it does persist even when I only hear using the headphones but as microphone use the built in microphone which sits next to the webcam on the monitor of my laptop and has nothing directly to do with my headphones. My headphones are not noisy so when they are not in my ears I can't hear any music produced by them, which means the laptop microphone can't as well, which then mean it "hears" the background music internally through the computer itself which hints to some settings fixable problem. [/FONT][/SIZE]

---

### Post by ajgreeny on 2015-01-27
One more try!
Have a look in pulseaudio sound settings, which you get to from the volume icon on your panel, and in the Input Devices tab see if you can mute the "Monitor of Built-in Anlogue stereo" which will show if you set the app to "Show all input devices".  That uses any sound that is going through your sound card as input and can be very useful when recording sounds, but is definitely not needed in your particular situation.

If that shows any output where my screenshot is showing mute, that may be your problem, so just move the sliders fully left or click on the volume icon to the right of the sliders to mute it.

---

### Post by o-l-lewinsohn on 2015-01-27
Yup the the monitor's microphone is muted so that's sadly not the problem.

---

