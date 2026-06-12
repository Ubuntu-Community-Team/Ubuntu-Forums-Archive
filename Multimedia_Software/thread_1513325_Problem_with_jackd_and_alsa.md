---
title: "Problem with jackd and alsa"
date: 2010-06-19
forum: Multimedia Software
---

### Post by VH-BIL on 2010-06-19
I have been trying to set up jack using the jack audio connection kit and have been able to record and playback in oss but can only get playback in alsa working with plughw:0 and can not record. I have my external midi interface working.

I would just like to be able to use jackd with alsa and midi to record and playback.



**I have added to my limits.conf:**
```

@audio - rtprio 100
@audio - nice -10
@audio - memlock 452192
```

**jackd settings:**
```

Realtime = True
No Memory Lock  = False
Unlocak Memory = False
Soft Mode = False
Monitor = False
Force 16bit False
H/W Monitor = False
H/W Meter = False
Verbose Messages = False
Priority = (default)
Frames/Period = 2048
Sample Rate = 48000
Periods/Buffer = 3
Port Maximum 256
Timeout (msec) = 500
Interface = (default)
Dither = None
Audio = Duplex
Input Device = (default)
Output Device = plughw:0
Input Channels = (default)
Output Channels = (default)
Input Latency = (default)
Output Latencey = (default)
```


*I have attached a list of my current hardware*

---

### Post by VH-BIL on 2010-06-20
*bump*

---

### Post by cchhrriiss121212 on 2010-06-20
A bit more info please:
What are you trying to record with? ie what does your jack connection chain look like?
What is the output of aplay -l and arecord -l?
To record midi you need a midi sequencer like Rosegarden or Qtractor

---

### Post by VH-BIL on 2010-06-21
> **cchhrriiss121212 said:**
> A bit more info please:
What are you trying to record with? ie what does your jack connection chain look like?
What is the output of aplay -l and arecord -l?
To record midi you need a midi sequencer like Rosegarden or Qtractor

Thank you for your reply.

I use Rosegarden to record my midi and that is working fine. I am trying to record audio with Ardour. It is working fine with oss with default settings but I can not get alsa to work.

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**arecord -l**
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2

---

### Post by cchhrriiss121212 on 2010-06-21
You know you need a synth or soundfont in order to record audio from midi? If so which synth are you using?
When you say Ardour doesn't record with alsa, what do you mean? Do you get a signal through the monitoring level on armed tracks, or are you getting some kind of error message?

---

### Post by VH-BIL on 2010-06-21
> **cchhrriiss121212 said:**
> You know you need a synth or soundfont in order to record audio from midi? If so which synth are you using?
When you say Ardour doesn't record with alsa, what do you mean? Do you get a signal through the monitoring level on armed tracks, or are you getting some kind of error message?

I have real hardware synths and modules. What I tried is connecting my Korg Triton into the Line In or Mic In (I think Mic) of my sound card.

What I mean about alsa is I dont get a level. If I create a bus to just send audio out to the speakers it works using jackd oss but if I try with jackd alsa it does not. I am trying to playback midi using Rosegarden and record the hardware synths using Ardour.

Thanks again for your reply.

---

### Post by VH-BIL on 2010-06-21
I managed to be able to be able to get it working. My Korg was plugged into the mic, I moved it to line in and jackd found it when using alsa.

I had Hydrogen connected to Rosegarden via midi and my Korg. I had Rosegarden, Hydrogen, and my Korg connected to Ardour via Jack and it all worked great.

Rosegarden crashed a few times, and there was some timing issues when recording live keyboards and using software synths but other then that I managed to produce an 8 bar test song. I was going to attach it but didn't know if it was appropriate in this forum.

---

### Post by cchhrriiss121212 on 2010-06-22
Good that you got things working, you should be able to see all three of your inputs if you use patchage to connect things up. I don't use much midi editing but you may find greater stability using [qtractor]("http://en.wikipedia.org/wiki/Qtractor") over rosegarden, it will also handle audio output so there's no need to use Ardour.

Your timing issue is probably down to high latency (see jack setup window) as anything over 10ms will sound off, and yours seems to be in the 80ms range. You can get latency down by lowering  the frames/period value, but onboard sound can only do so much. An investment in a quality sound card would give you great latency and improve the capture of your hardware synths, I use an M-audio delta44.

PS posting your songs here is fine as long as it is not the main point of the thread

---

### Post by AutoStatic on 2010-06-22
Most modern onboard cards can run at <10ms latencies also nowadays. It takes some tweaking but it's feasible.

---

### Post by VH-BIL on 2010-06-22
> **cchhrriiss121212 said:**
> 
PS posting your songs here is fine as long as it is not the main point of the thread

It is not really a song :) just a test to connect hydrogen, rosegarden, software synths (the strings) and record live midi keyboards using a hardware syth (the piano). Then to record all the audio into seperate tracks in Ardour and mixed down to a audio file.

Tell me what you think...

---

### Post by VH-BIL on 2010-06-22
> **AutoStatic said:**
> Most modern onboard cards can run at <10ms latencies also nowadays. It takes some tweaking but it's feasible.

I had to adjust the Frames/Period and Periods/Buffer. I am not sure what they do but I can get the latency as low as 0.667 using 16 frames/period and 2 periods/buffer, is that ok to use these settings?

[EDIT]
It sounded terrible :p I had to change frames/period to 64 which moves the latency to 2.67 and it sounds normal now.

---

### Post by cchhrriiss121212 on 2010-06-22
> **AutoStatic said:**
> Most modern onboard cards can run at <10ms latencies also nowadays. It takes some tweaking but it's feasible.
Thats news to me, how much tweaking does it take? I'm just curious so I won't ask you for step by step instructions.
My 4 years old inspiron 6400 could manage around 15ms, while still being stable, this was with a 9.04 studio install.

---

### Post by VH-BIL on 2010-06-22
> **cchhrriiss121212 said:**
> Thats news to me, how much tweaking does it take? I'm just curious so I won't ask you for step by step instructions.
My 4 years old inspiron 6400 could manage around 15ms, while still being stable, this was with a 9.04 studio install.

I just played with Frames/Period, and Periods/Buffer in Jack Audio Connection Kit until it sounded nice and am now at 2.67ms

---

### Post by cchhrriiss121212 on 2010-06-23
> **VH-BIL said:**
> I just played with Frames/Period, and Periods/Buffer in Jack Audio Connection Kit until it sounded nice and am now at 2.67ms
Is it stable like that when running a few programs? If so I guess nvidia make better onboard sound cards than intel do. Your test track sounded like a good start to me, and with jack you can always run things like drum loops into equalisers or fx to liven them up.

---

