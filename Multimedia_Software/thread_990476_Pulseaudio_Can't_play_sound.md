---
title: "Pulseaudio: Can't play sound"
date: 2008-11-22
forum: Multimedia Software
---

### Post by peddy on 2008-11-22
When I open PA volume control, I get a message saying: Connection failed: Connection refused. Sound does not work. Could someone please help me? I'm running 0.9.10 with the latest updates.

Cheers

---

### Post by forkandles on 2008-11-23
I assume you mean 8.10.
Look here in the Sound Setting section:

[http://ubuntuforums.org/showthread.php?t=990057&highlight=experiences+8.10+skype+vision+pro](http://ubuntuforums.org/showthread.php?t=990057&highlight=experiences+8.10+skype+vision+pro)

---

### Post by psyke83 on 2008-11-23
See here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by peddy on 2008-11-23
forkandles, I meant Pulseaudio version 0.9.10. I am running 8.10, though. 

psyke83, I've done that and it made no difference. 

Thanks for your help.

---

### Post by peddy on 2008-11-24
Appears to happen only after a resume from suspend.

---

### Post by kostkon on 2008-11-25
Hmmm. It seems that resuming from suspend crashes *PulseAudio*. Check your *syslog* (you can access it from *System &#8594; Administration &#8594; System Log*) after resuming for any messages regarding *PulseAudio*.

---

