---
title: "Pulseaudio e Jack"
date: 2008-11-01
forum: Multimedia Software
---

### Post by minghio on 2008-11-01
Good afternoon to everyone.
I'm the owner of a that I manage to use only through the Jack audio server.
Every application with jack support works nice.
I can't hear nothing with the application without Jack support.
How can I manage to route every sound to jack?
Do you have some advice about Pulseaudio?

---

### Post by markbuntu on 2008-11-01
Go here. Near the end of the OP there is a section on getting pulseaudio and jack working together so there are pulseaudio connections in the jack connection box and jack sinks and sources in pulseaudio:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by minghio on 2008-11-03
Thanks, I'm going to read it

---

### Post by minghio on 2008-11-09
I've read a lot of tread I tried but it doesn't work.
I'll try to explain better my situation: I've a firewire card that works nice with jack, but I would like to route the sound of every application to jack.

If I do 
```
pactl load-module module-jack-sink
pactl load-module module-jack-source
```

I receive this message error: Connection failure: Connection refused

---

### Post by markbuntu on 2008-11-09
Are pulseaudio and jack both running when you do the commands?

---

### Post by minghio on 2008-11-09
Yes they are both running.
Then after I run the command, Pulseaudio stops.

---

### Post by minghio on 2008-11-10
I'm sorry.. it was my mistake.
With the command I've pasted it's all ok.
Thanks

---

