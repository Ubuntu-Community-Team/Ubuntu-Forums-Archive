---
title: "Sending Audio over LAN"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by booljayj on 2007-06-22
What I really want to know is if this is even possible with existing software. I have heard many things about streaming media over a network, but that's not quite what I want. Instead of audio data being piped through to my sound card, I want it to be sent over my network to another PC's sound card. In other words: I want to open up Rhythmbox on my laptop, play a song, and hear it being played on the other computer's speakers. Is this sort of thing possible?

---

### Post by yabbadabbadont on 2007-06-22
```
p   nas                                                     - The Network Audio System (NAS). (local server)                   
p   nas-bin                                                 - The Network Audio System (NAS). (client binaries)                
v   nas-dev                                                 -                                                                  
p   nas-doc                                                 - The Network Audio System (NAS). (extra documentation)            
v   nas-lib                                                 -                                                                  

```
I've never used it, but I knew that it existed.  You'll need too do some research to see if it fits your needs.

Edit: Here is the homepage for it: [http://radscan.com/nas.html](http://radscan.com/nas.html)

---

### Post by dasunst3r on 2007-06-22
You could also try PulseAudio.  [www.pulseaudio.org](www.pulseaudio.org)

---

### Post by booljayj on 2007-06-22
Pulseaudio looked promising, but it turned out just too confusing. I have to install five different programs and set up everything perfectly. I'm not good at networks, so I have no idea what is supposed to be a server or sink or source.

Nas doesn't have much documentation. How exactly does it work? I installed nas and nas-bin from synaptic, and started nasd -aa like was suggested at [http://radscan.com/nas/docs/nas-README.txt](http://radscan.com/nas/docs/nas-README.txt). The output of this command is:
```
$ @(#)Network Audio System Release 1.8
Error binding unix socket: /tmp/.sockets/audio0
: Address already in use

Fatal server error:
Cannot establish unix listening socket



```
notice that it didn't actually end, meaning take me back to $ where I could enter other commands, but pressing enter gives me
```
[1]+  Exit 1                  nasd -aa
$ 

```

Yeah, I'm not good enough at this stuff to figure this out. If someone could easily explain how to install and run pulseaudio correctly I would greatly appreciate it. Until then, it's kind of messing with my system, so I'm going to uninstall it.

---

### Post by Monicker on 2008-05-02
> **booljayj said:**
> What I really want to know is if this is even possible with existing software. I have heard many things about streaming media over a network, but that's not quite what I want. Instead of audio data being piped through to my sound card, I want it to be sent over my network to another PC's sound card. In other words: I want to open up Rhythmbox on my laptop, play a song, and hear it being played on the other computer's speakers. Is this sort of thing possible?

Pulseaudio, which is included with 8.04 seems to have such capabilities.  I could not find any gui controls for it, but looking at the man page for pacat was interesting.

```

 pacat - Play back or record raw audio streams on a PulseAudio sound server
```


Might be worth investigating further.

---

