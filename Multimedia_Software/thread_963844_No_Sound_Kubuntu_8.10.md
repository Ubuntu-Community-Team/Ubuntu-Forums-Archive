---
title: "No Sound Kubuntu 8.10"
date: 2008-10-30
forum: Multimedia Software
---

### Post by domentarion on 2008-10-30
Hello 

I installed on my laptop (acer aspire 8930g) kubuntu 8.10 but now i don't have sound.

The command lspci gives 

Audi device : Intel Corporation 82801I (ICH9 Family) HD Audio controller.

Can somebody help me with that ? I really want to have sound on my laptop

---

### Post by KjetilK on 2008-10-30
I don't know too much about this, but I've noticed that my mixer settings have sometimes been reset without me noticing. Have you checked that? I.e. run

alsamixer 

and have a look at the levels.

---

### Post by domentarion on 2008-10-30
> **KjetilK said:**
> I don't know too much about this, but I've noticed that my mixer settings have sometimes been reset without me noticing. Have you checked that? I.e. run

alsamixer 

and have a look at the levels.

Thats the first thing that i checked.

---

### Post by DevNull11 on 2008-11-01
domentarion, do you have sound on KDE Bootup/Shutdown. I'm running into the same issue. I'm using KUbuntu X64

---

### Post by domentarion on 2008-11-02
> **DevNull11 said:**
> domentarion, do you have sound on KDE Bootup/Shutdown. I'm running into the same issue. I'm using KUbuntu X64

No i do not have any sound at all. I think that i now my problem . 

On this site : 

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

There is no ICH9 so i think my sound card is not supported yet

---

