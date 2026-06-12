---
title: "DJ Software"
date: 2010-06-11
forum: Multimedia Software
---

### Post by wesleybishop on 2010-06-11
Does anyone know of any free software comparable to virtual dj? I used Virtual DJ a lot when before I got Ubuntu and have not been able to find something comparable as of yet any tips would be apprciated. :guitar:

---

### Post by cchhrriiss121212 on 2010-06-11
Try out Mixxx, haven't used it myself but it has a few proponents on the studio sub-forum. If you want to produce and mix seriously with low latency then the jack sound server is something you should also look in to.

---

### Post by wesleybishop on 2010-06-14
Checked out some videos on youtube I am going to try the program out and post back about it later. THANKS!

---

### Post by wesleybishop on 2010-06-20
not easy to get up and running any other ideas?

---

### Post by wesleybishop on 2010-06-24
bump

---

### Post by wesleybishop on 2010-06-28
bump

---

### Post by cchhrriiss121212 on 2010-06-28
What was your trouble with Mixxx? I could help you set it up unless you have given up on it. You should be able to use it without installing jack BTW.
You could also try out terminatorX (the software, not the guy).

---

### Post by wesleybishop on 2010-07-01
> **cchhrriiss121212 said:**
> What was your trouble with Mixxx? I could help you set it up unless you have given up on it. You should be able to use it without installing jack BTW.
You could also try out terminatorX (the software, not the guy).

This is one of the errors I get 

 p, li { white-space: pre-wrap; }  QFileSystemWatcher: failed to add paths: /home/wesley/.config/ibus/bus

This is the other error

 p, li { white-space: pre-wrap; }  Mixxx cannot access the sound device 8, default. Another application is using the sound device or it is not plugged in.
 
[LIST]
[*]Retry after closing the other application or reconnecting the sound device
[*]Reconfigure Mixxx to use another sound device.
[*]Get Help from the Mixxx Wiki.
[*]Exit without saving your settings.
[/LIST]

---

### Post by wesleybishop on 2010-07-01
Found a workaround to the second error I go into reconfigure and change it to default and channel 1-2 for the master and 3-4 for the headphones it errors out then I do it again and it works.

Thanks again [cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514") for your quick responses.

---

### Post by wesleybishop on 2010-07-01
Is there a way to make it so that music comes out of the speakers and through the head phones when I plug them into the front?

---

### Post by cespinal on 2010-07-01
nopes.... unless you have dual soundcards on a mixer... 
with standard laptops, the sound channels will go either to your deadphones or to the speakers...

---

### Post by cchhrriiss121212 on 2010-07-01
> **wesleybishop said:**
> Is there a way to make it so that music comes out of the speakers and through the head phones when I plug them into the front?
You can do this with jack, which will also give you complete control of where sounds are being routed to and from.

---

### Post by wesleybishop on 2010-07-01
> **cespinal said:**
> nopes.... unless you have dual soundcards on a mixer... 
with standard laptops, the sound channels will go either to your deadphones or to the speakers...

I am using a desktop not a laptop

---

### Post by wesleybishop on 2010-07-01
> **cchhrriiss121212 said:**
> You can do this with jack, which will  also give you complete control of where sounds are being routed to and  from.

I am not very familiar with jack do you know of a tutorial or could you give me a walk-through?

---

### Post by kinsago on 2010-07-01
If I remember correctly, PCDJ runs under wine quite nicely. I know this doesn't exactly answer your question - just a thought, have you tried running virtual dj under wine?

---

### Post by wesleybishop on 2010-07-01
> **cchhrriiss121212 said:**
> You can do this with jack, which will also give you complete control of where sounds are being routed to and from.

> **kinsago said:**
> If I remember correctly, PCDJ runs under wine quite nicely. I know this doesn't exactly answer your question - just a thought, have you tried running virtual dj under wine?

I will give it a try

---

### Post by cchhrriiss121212 on 2010-07-02
> **wesleybishop said:**
> I am not very familiar with jack do you know of a tutorial or could you give me a walk-through?
Download jackd, qjackctl and patchage packages from synaptic.
Add yourself to the audio group in Users & Groups

Put this into a terminal:
```
sudo gedit /etc/security/limits.d/audio.conf
```and paste these lines:
> @audio - rtprio 99
@audio - memlock unlimited

Open up jack from the sound and video menu, press start, check message window to see whether it runs OK. Open up patchage to connect up the audio chain.

---

