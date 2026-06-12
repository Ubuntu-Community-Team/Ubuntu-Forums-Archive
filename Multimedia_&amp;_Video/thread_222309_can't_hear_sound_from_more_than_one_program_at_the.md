---
title: "can't hear sound from more than one program at the time"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by loukasmaki on 2006-07-24
I can't hear sound from more than one program at the time (meaning if I for example listen to music I can't have a voice chat with anyone or hear the sound from a movieclip I would be watching)

I can't open alsamixer. I get the following: > alsamixer: function snd_ctl_open failed for default: No such device

I can't hear any sound at all when trying to play Caesar 3 through wine

I can't change the Audio settings in winecfg. Wine crashes:

> petri@ubuntu:~/.wine/c/Programme/Caesar3$ winecfg
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/petri/.kde/socket-ubuntu.
can't create mcop directory


I get the feeling that all these problems are connected. but the top complaint is the main issue for me.


I have this computor: Compaq nx6110 Laptop from Hp. Ubuntu 6.06 is installed.
lspci says this about my sound device:

> 0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company nx6110
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at 2100 [size=256]
        I/O ports at 2200 [size=64]
        Memory at d0581000 (32-bit, non-prefetchable) [size=512]
        Memory at d0582000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2


I thought this[http://www.ubuntuforums.org/showthread.php?t=31871&highlight=%2Fdev%2Fsnd%2Fseq+missing]("http://www.ubuntuforums.org/showthread.php?t=31871&highlight=%2Fdev%2Fsnd%2Fseq+missing") described my problem but I got --ignore-install unknown flag (or something similiar since I use ubuntu in swedish so I have to translate some stuff)

A friend of mine said I was missing /dev/snd/seq (whatever that means)

Please oh pretty please help ](*,)

---

### Post by gmatt on 2006-07-24
Hmm, are you missing /dev/snd/seq? Or is it there. The first line you wrote indicates you're alsa maybe configured incorrectly.

---

### Post by loukasmaki on 2006-07-25
> petri@ubuntu:~$ /dev/snd/seq
bash: /dev/snd/seq: File or directory doesn't exist
petri@ubuntu:~$


configured incorrectly?

---

### Post by loukasmaki on 2006-07-25
The earlier mentioned friend said now that my sound device probably isn't multiplexing as it should?

---

