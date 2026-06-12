---
title: "gtk-recordmydesktop"
date: 2010-03-17
forum: Multimedia Software
---

### Post by salamandaar on 2010-03-17
Is there a way to record my systems sound output (what comes out the speakers) while i'm recording whats happening onscreen?

The only way i can make it work is by using a microphone to capture the audio from the speakers, which doesn't result in good quality.

Cheers

---

### Post by hazelnut on 2010-03-17
I have never used gtk-recordmydesktop, but I have had success with this:

```
pacat --record --rate 48000 --fix-format --fix-channels | \
ffmpeg -f s16le -ar 48000 -ac 2 -i - -f x11grab -s 800x600 -r 29.976 \
-i :0.0+0,0 -s 720x480 -r 29.976 -sameq -aspect 1.333 \
-ab 256k -ac 2 -ar 48000 \
-y outputfilename.mpg 
```

The pacat command will pipe the pulse audio to ffmpeg for capture.  If gtk-recordmydesktop can accept piped audio, maybe this will help you.

The command line I gave above presumes an 800x600 display resolution. On my system, I have to reset that low to get non-jerky capture  at 29.976 frame rate...but you asked about audio :-)

---

### Post by hxcobd on 2010-03-17
salamander, a much easier way of doing this without needing command line wizardry:

1.) Download the PulseAudio volume manager (Pulseaudio Volume Control) package from the repo

2.) Run it, go to Input Devices, in the bottom right drop-down, select "Show Monitors"

3.) Click the Fallback icon/button for the output device you use to listen to audio

4.) Open a sound recording program like Audacity, in the Preferences, select Pulseaudio driver for input and output

All sound played through your sound card should now play into Audacity as well.

Those are the steps from memory, let me know if it doesn't work for you.

---

