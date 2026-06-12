---
title: "A Myriad of problems with Line6 USB device, jack, pulseaudio"
date: 2012-09-13
forum: Multimedia Software
---

### Post by vambop on 2012-09-13
I've tried to attack this from several angles for days now, so I could  certainly use at least a nudge in the right direction. I know there are  similar threads out there but each has slightly different issues, and  most deal with previous versions of Ubuntu. In any case my frustration  level has reached high enough that I throw up my hands and ask for help.

Goal:
Routing guitar through Line6 POD GX to Rakarrack (effects software) via jack and out to speakers.

What does work:
Recording in Audacity (without hearing the sound while playing). So there should be no issue with hardware or drivers.

Problems:
1.  Whenever the Line6 USB device is plugged in at boot time, the system  crashes. It's annoying but I could live with it (just have to remember  to plug it out).

2. Jack is throwing different errors:
 
Initially when starting jack:
```
ALSA: got smaller periods 2 than 4 for capture
```When trying to start it again:
```
Failed to acquire device name : Audio0 error : Cannot allocate memory
```There's probably a few additional ones that I get after a certain combination of events.

In any case, I can only launch jack after running those two commands:

```
pactl load-module module-jack-source
pactl load-module module-jack-sink
```3.  And this is where I am stuck at - Cannot route sound from jack to  rakarrack (or is it from the USB to jack, I am not even sure). Perhaps a good first step would be to route the sound to speakers at least, haven't been able to do that either.

When I've run the 2 commands above, I can open jack (and rakarrack). 

I can see the GX analog input level move in the sound panel:

[IMG]http://i45.tinypic.com/c21w6.png[/IMG]

However  the JACK source below does not contain any output. I Imagine that  system capture should be routed to it? So what follows is my attempt at  routing the things in JACK (what I added are the rakarrack connections,  the rest were in place I believe).

[IMG]http://i50.tinypic.com/o8vu37.png[/IMG]

Jack Setup:

[IMG]http://i45.tinypic.com/20h2ao4.png[/IMG]

The hw:1 Input Device is POD Studio GX (There is a choice between :1 and :1,0 btw)

Sound card and system info.

```

vambo@vambopc:~$ cat /proc/asound/cards 
 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0x7c00 irq 18
 1 [PODStudioGX    ]: line6usb - POD Studio GX
                      Line6 POD Studio GX at USB 2-3:1.0
``````
vambo@vambopc:~$ uname -a
Linux vambopc 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:54:40 UTC 2012 i686 athlon i386 GNU/Linux
```

PS Apologies for the humongous screenshots.

---

