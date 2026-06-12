---
title: "[Pulseaudio] change audio balance in terminal"
date: 2010-11-18
forum: Multimedia Software
---

### Post by Guidoo on 2010-11-18
Hello people,

I'm looking for a way to change the balance of my audio in the terminal. (i.e. setting a different volume for the left and the right speaker).

I can set the volume level for both channels at once with a command like:
```
pacmd set-sink-volume 1 32768
```
But I'd like to do something like
```
pacmd set-balance 1 -0.2 
```
to shift the balance towards the left speaker.

Can anyone help me with that? Or any other command?
If you've got a non-pulseaudio solution, I'm interested too :)

Thanks in advance!

---

### Post by Guidoo on 2010-11-25
*bump*

Isn't this possible at all?

---

### Post by kortas on 2011-09-16
I found it! It works for me.

you can change balance using alsamixer:

```
amixer sset Master 80%,20%
```


[http://superuser.com/questions/317296/setting-audio-balance-from-command-line](http://superuser.com/questions/317296/setting-audio-balance-from-command-line)

---

### Post by nilsja on 2011-11-02
the syntax is 100% for each side - not like the usual balance control

---

