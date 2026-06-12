---
title: "Audacity crashes while recording"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by commodore on 2006-10-26
When I click the record button in Audacity, the line just wobbles a bit and then Audacity crashes. I get this error, when starting from CLI: 
"PaHost_WatchDogProc: killing hung audio thread!"

---

### Post by commodore on 2006-10-26
I think it might be called a bug?

Here's what helped: add "@audio          -       rt_priority     100" to /etc/security/limits.conf and restart.

---

### Post by nick122147 on 2006-11-02
this doesnt work for me, it should be like this in Ubuntu Edgy:

@audio - rtprio 99
 
Finally found the answear after 3 days of googling..

---

### Post by dolson on 2006-11-02
It was always "rtprio" on my old UbuntuStudio.com site's tutorial, which is now relocated to here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by nick122147 on 2006-11-02
that was where I found it.. Thanks Dolson

---

### Post by dolson on 2006-11-02
Haha. That's kinda funny, and kinda not. :D

---

### Post by owainsutton on 2006-11-12
I'm having the same problem recording (I can open a wav file and edit it without a problem), and the suggestions above have had no effect.  Any ideas?

---

### Post by nick122147 on 2006-11-13
Have you tried opening from the terminal with "aoss audacity" ?

---

### Post by owainsutton on 2006-11-13
Yes.  And when it crashes, I get the same error as the OP.

---

### Post by txgunslinger on 2006-11-26
I'm having the same issue.  I've been looking for an answer for two days, but nothing so far.

EDIT:  It's actually all audio recording applications that I'm having a problem with.  I decided to give Ardour a go until I could find a fix, but it doesn't work either.  Same with sound recorder.

Ardour error message: 
Segmentation fault (core dumped)

Sound Recorder ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave

---

### Post by sickenmcsluggets on 2007-05-25
I can record my voice perfectly with sound recorder, but Audacity will crash and shut down within two seconds if I press the record button. commodore mentioned  editing a .conf file. Where in the .conf file would I put that line he has...and does it sound like something that would fix this problem? I can't seem to figure this one out.

---

