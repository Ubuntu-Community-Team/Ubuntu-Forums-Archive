---
title: "How do I make pulseaudio STOP copying mic input to main output?"
date: 2010-11-26
forum: Multimedia Software
---

### Post by dewdrop_world on 2010-11-26
I have a headset microphone plugged into the built-in audio input. The output is plugged into an amplifier > speakers.

Pulseaudio is "helpfully" routing the microphone input signal to the speaker output. I do not want this. I go to pavucontrol and disable the "monitor of the internal audio analog stereo" -- and what I say into the microphone is still coming out of the speakers.

Google gives a lot of information about how to live-stream mic input over the Internet. And, I found this here (that's for karmic, I'm running lucid):

[http://ubuntuforums.org/showthread.php?t=1324135](http://ubuntuforums.org/showthread.php?t=1324135)

... but that's about how to ENABLE loopback. It says loopback should not be enabled by default, but I very clearly hear that something is doing the same thing as loopback.

(Of course, I need to hear sound from applications that are playing, and when I'm dictating text into NaturallySpeaking running under virtual box, I need sound input to go there -- so turning the mic all the way down to zero is not the solution.)

I'm fairly sure I remember hearing this behavior ever since installing Ubuntu, and I didn't do anything to turn it on. I can't imagine most users would prefer this behavior -- if it's the default behavior, why? It makes absolutely no sense to me. (Sorry. It's one of those piddly little configuration things that costs a couple of hours of web searching time, and after a while I just have to give up, but not before becoming much more frustrated than I should have to.)

So, to be clear, here's what I want:

- Applications playing audio should send sound to the main output.
- Applications receiving audio input should hear the microphone.
- Microphone sound should not EVER go to the main output *unless I have explicitly launched an application making the connection*. (The signal goes input -> output *even when NO application is open* - hence my consternation.)

Thanks in advance,
James

---

### Post by dewdrop_world on 2010-11-27
OK, finally found out, it wasn't pulseaudio at all. Somehow, the default alsamixer configuration was pumping the mic input to the output. I set those to 0 and now it's stopped.

That's begging the question of how it got set up this way... I never opened alsamixer before, suggesting that the default Ubuntu configuration pipes the audio this way. Huh??? That's kind of dumb. I guess later on I'll log a bug over at launchpad.

James

---

