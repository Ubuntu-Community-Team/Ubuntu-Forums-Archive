---
title: "Record Streaming Audio W/O Audacity"
date: 2011-08-12
forum: Multimedia Software
---

### Post by dniMretsaM on 2011-08-12
I like to listen to Internet radio and record it to put on my iPod. I used to use Audacity, but have had a ton of problems, so I've given up on that for recording (I still use it for editing). So what I'm looking for is another program that can record streaming audio. Any suggestions?

Thanks,
dniMretsaM

Edit: I actually am using Kubuntu, I choose the wrong prefix by accident.

---

### Post by dniMretsaM on 2011-08-13
Bump.

---

### Post by ron999 on 2011-08-13
> **dniMretsaM said:**
> ...that can record streaming audio.
Which streaming audio?

---

### Post by dniMretsaM on 2011-08-13
> **ron999 said:**
> Which streaming audio?

Any audio that's playing through the speakers (sound card).

---

### Post by Toz on 2011-08-13
Streamripper/tuner? See: [http://lifehacker.com/263493/record-streaming-radio-with-streamripper-and-streamtuner]("http://lifehacker.com/263493/record-streaming-radio-with-streamripper-and-streamtuner")

---

### Post by dniMretsaM on 2011-08-14
I suppose, but most (if not all) of the stations I like aren't compatible. Plus I sometimes use it for audio other than radio.

---

### Post by Toz on 2011-08-14
Can I ask what problems you had with audacity? I successfully use audacity to record audio streams.

---

### Post by dniMretsaM on 2011-08-14
Well, first I had no recording from the sound card at all. Then the recording quality was horrible. I got that fixed but now I have no control over the input volume. It's stuck very low. Here's the thread about it: [http://ubuntuforums.org/showthread.php?t=1813462](http://ubuntuforums.org/showthread.php?t=1813462)

---

### Post by Toz on 2011-08-14
Hmmm. I use the same setup/procedure as post #2 from that thread and it works. I remember having to fiddle a bit with the Devices options in Edit->Preferences. The current settings are as such:

Devices section:
- Host = ALSA
- Playback->Device = default
- Recording->Device = pulse: Mix:0
- Recording->Channels = 2(stereo)

Recording section:
- Overdub = checked
- Software playthrough = unchecked

---

### Post by dniMretsaM on 2011-08-14
So you have no problems with input volume?

---

### Post by Toz on 2011-08-14
No I don't. Have you had a look at alsamixer - specifically the microphone channel (I have 2 channels, Mic Boost and Internal Mic.

---

### Post by Toz on 2011-08-14
What sound card do you have? Maybe you could post back the Audio sections of:
```
lspci -vnn
```

---

### Post by dniMretsaM on 2011-08-16
> **Toz said:**
> What sound card do you have? Maybe you could post back the Audio sections of:
```
lspci -vnn
```

```
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
        Subsystem: Dell Device [1028:0160]
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
        Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0
```

Old card, this computer is at least 8 years old.

---

### Post by beew on 2011-08-16
[http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)

---

### Post by dniMretsaM on 2011-08-16
> **beew said:**
> [http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)

Thank you very much, I'll give it a try!

---

### Post by baddnady23 on 2011-08-16
Check out the script mentioned in this thread, it worked wonders for me.

[http://ubuntuforums.org/showthread.php?t=1330728]("http://ubuntuforums.org/showthread.php?t=1330728")

---

### Post by hsweet on 2011-08-16
I've done it a few times using Kxstudio.  It should work on any system that has Jack running properly.  

I patch the output back into the recorder (Ardor has worked the best), set my levels,  hit record and start the stream.

---

