---
title: "Lucid Lynx Java sound question"
date: 2010-04-29
forum: Multimedia Software
---

### Post by SRTS on 2010-04-29
Hi, I'm looking forward to 10.04, but before installing it, I'd like to know if it'll actually fix the sound problems that have been plaguing this otherwise good system for the last 3 years I've been trying it out:
Java applications will grab the audio exclusively, or, if any other app is playing audio, they'll run muted without any sound.
Since this is a very well known and common problem, persisting in both, ALSA and PulseAudio, I'm hoping they finally found a way to fix it? (Happens if the soundchip can't hardware-mix, so they'd need to add proper software-mixing, I guess, but I'm no expert.)
I use Java applications with sound output a lot, so Ubuntu has been absolutely defunct so far, for those purposes.
(Edit: I also tried padsp etc, but those just cease working after a medium while, like, 15 minutes, and then every further sound that would've been outputted will cause Java to freeze for a short period of time, while remaining muted. It has basically been like this for 3 years now through all Ubuntus I tried.)

thanks in advance

---

### Post by kostkon on 2010-04-29
OpenJDK works fine, on the other hand Sun Java still tries to access the sound device directly.

---

### Post by SRTS on 2010-05-03
I did a fresh installation of 10.04, and openjdk isn't giving me sound output, except for a 'ding' sound that happens at some point in the program. Now I wonder why it would play at least that sound, while not playing any of the other sounds... but anyway, it doesn't really work :(

---

### Post by SRTS on 2010-05-03
HELP pleeeease, my java app doesn't give sound output, in this OpenJDK! This is in a fresh installation OUT OF THE BOX!

I already tried editing sound.properties and switching

#javax.sound.sampled.Clip=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
#javax.sound.sampled.Port=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
#javax.sound.sampled.SourceDataLine=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
#javax.sound.sampled.TargetDataLine=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider

to

javax.sound.sampled.Clip=com.sun.media.sound.DirectAudioDeviceProvider
javax.sound.sampled.Port=com.sun.media.sound.PortMixerProvider
javax.sound.sampled.SourceDataLine=com.sun.media.sound.DirectAudioDeviceProvider
javax.sound.sampled.TargetDataLine=com.sun.media.sound.DirectAudioDeviceProvider

but it didn't help.

---

