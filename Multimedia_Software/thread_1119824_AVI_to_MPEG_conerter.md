---
title: "AVI to MPEG conerter"
date: 2009-04-08
forum: Multimedia Software
---

### Post by nikhilneela on 2009-04-08
Hi everyone...I want Avi to MPEG converter(A GUI BASED)...I have searched forums for this but nothing given is working properly...So please help me....Thanks in advance

---

### Post by SuperSonic4 on 2009-04-08
Avidemux?

I just tested it and all seems perfect. You may need ffmpeg or mencoder as a backend

---

### Post by nikhilneela on 2009-04-08
ok...please tell me how to install it....i am getting error while installing...please tell me a way

---

### Post by xc3RnbFO8P on 2009-04-08
**Devede** in Add/Remove (all available application)

---

### Post by nikhilneela on 2009-04-08
Sorry to trouble you.....The program DEVEdE doesnot have an option to convert AVI to MPEG...it only shows options of output format to be PAL/SECAM and NTSC

---

### Post by SuperSonic4 on 2009-04-08
```
sudo apt-get avidemux
``` or you can use Add/Remove or Synaptic and search for avidemux

---

### Post by nikhilneela on 2009-04-08
I get the following error


nikhil@nikhil-desktop:~$ sudo apt-get avidemux
[sudo] password for nikhil: 
E: Invalid operation avidemux

---

### Post by SuperSonic4 on 2009-04-08
feck, I always make that typo >.<. It should be

```
sudo apt-get install avidemux
```

---

### Post by nikhilneela on 2009-04-08
Thank you....That solved by problem

---

### Post by xc3RnbFO8P on 2009-04-08
> **nikhilneela said:**
> Sorry to trouble you.....The program DEVEdE doesnot have an option to convert AVI to MPEG...it only shows options of output format to be PAL/SECAM and NTSC
Choose Video DVD
Look in **Advance Option**> only convert film files compliant MPEG files

---

### Post by andrew.46 on 2009-04-08
Hi nikhilneela,

Although you are keen to avoid commandline converters like FFmpeg and MEncoder do you realise that almost all of the gui converters are in fact using these programs for their converting? So what you will be doing in using these programs is very similar to the old idea of 'using a broomstick to turn on a light switch' :-).

I would suggest certainly use the gui programs but perhaps experiment a little with the FFmpeg commandline?

All the best,

Andrew

---

