---
title: "Microphone problem"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by foxure on 2006-09-30
Hello.


i buy'd a mic a few days ago, it does not work in TeamSpeak and Skype. the people im skyping to is only hearing a little little voice in the background.


if i try to rec from the mic i get a good voice volume and everthing works nice. 

so i thought i would be that Skype and TeamSpeak is capturing from the wrong device (eg. its capturing from another port on the sound card. and the backgroung voice is only some leek) so i started the sound recorder and did a  

```
lsof | grep /dev/
```

and this looking interesting

```
gnome-sou 5284     markus  mem       CHR     116,24               9764 /dev/snd/pcmC0D0c
gnome-sou 5284     markus    0r      CHR        1,3               5620 /dev/null
gnome-sou 5284     markus   15u      CHR      116,0               9776 /dev/snd/controlC0
gnome-sou 5284     markus   16u      CHR     116,24               9764 /dev/snd/pcmC0D0c

```


A quickly look in TeamSpeak tells me that its using /dev/dsp as sound device.  the problem is that either /dev/snd/pcmC0D0c or /dev/snd/controlC0 ca is working when i specify that in Skype or TeamSpeak.


im think im on the right way. but doing wrong. can anybody help me?

---

### Post by foxure on 2006-09-30
hmm.. it was possible to change menu in alsamixer trought tab.. didn't know that.. 

now its working find.. =)

---

