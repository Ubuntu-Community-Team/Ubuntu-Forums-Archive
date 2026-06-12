---
title: "Jack xruns with modern hardware"
date: 2014-11-18
forum: Multimedia Software
---

### Post by Ck.asdf on 2014-11-18
I run a desktop that provides multiple functions - it's my server, media production & general playback machine, email, browser (YouTube), whatev.

Because it performs many different functions, especially flash playback, Jack alone isn't enough, so I set up Pulse Over Jack.  I got it running very well so that I could play media that preferred Pulse, and use my Jack-enabled apps such as Ardour, etc.

Fast forward to some recent system updates, and I had no sound, and I believe I had some on-screen notice about Jack issues.  Restarted the computer, opened qjackctrl and immediately xrun callbacks started flowing.  I could get sound, but it occasionally clips.

I had set the following Jack settings:
> 
*Realtime
Priority: default
Frames/Period: 16
Sample Rate: 48000
Periods/Buffer: 2
Port Maximum: 256
Timeout: 500
Driver: alsa
Dither: None
Audio: Duplex
Several other settings - default or unchecked


My computer:

Ubuntu 14.04 LTS
Intel Core i7-3770 @ 3.4GHz x 8
14.6GiB RAM
Intel HD Graphics 4000
120GB Mushkin SSD (Ubuntu & applications)
750GB Western Digital Black HDD (/home & data)


```

uname -a
Linux ck-serv 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```

ulimit -r -l
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited

```

```

cat /proc/asound/cards
 0 [M66            ]: ICE1712 - M Audio Delta 66
                      M Audio Delta 66 at 0xd040, irq 17

```

While a YouTube video plays:
```

[ ... ]
23:48:18.143 XRUN callback (28497).
23:48:20.210 XRUN callback (28498).
23:48:20.992 XRUN callback (2 skipped).
23:48:22.993 XRUN callback (3 skipped).
23:48:24.994 XRUN callback (2 skipped).
23:48:25.561 XRUN callback (28508).
23:48:26.598 XRUN callback (28509).
23:48:26.996 XRUN callback (1 skipped).
23:48:28.897 XRUN callback (28510).
23:48:30.636 XRUN callback (28513).
23:48:30.999 XRUN callback (2 skipped).
23:48:31.706 XRUN callback (28514).
[ ... ]

```

Snippets of /etc/cpufreqd.conf
```

[Profile]
name=Performance High
minfreq=100%
maxfreq=100%
policy=performance
[/Profile]

[Rule]
name=AC Rule
ac=on                    # (on/off)
profile=Performance High
[/Rule]

[Rule]
name=CPU Too Hot
acpi_temperature=55-100
cpu_interval=50-100
profile=Performance Low
[/Rule]

```

This being a desktop, it's always on AC.

My CPU temperature ranges from 30*C to 60*C, so could it be possible the "Too Hot" rule could be affecting things?

---

### Post by erwin13 on 2015-06-13
I've almost the same configuration. And somehow I also get these horrible xrun errors. I have Ubuntu studio but it is basically unusable for creating music. I've tried everything but even with a latency in jack of 46 mS I still get xruns.

---

### Post by Ck.asdf on 2015-06-13
I've moved to Debian Wheezy now, as beyond the issues described above, Ubuntu seemed to be too unstable.  I currently have no sound at all, but that's because I'm working toward mixing PulseAudio & Jack again, and haven't gotten a moment to do it yet.   I'll update on how it goes once I've done that, but if anyone has any thoughts here, I'd love to know in case it comes up again, plus I'm sure erwin13 would like to get back to creation. :)

---

