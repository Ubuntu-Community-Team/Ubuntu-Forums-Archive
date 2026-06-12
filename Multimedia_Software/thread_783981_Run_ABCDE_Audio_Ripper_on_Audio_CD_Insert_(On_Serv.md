---
title: "Run ABCDE Audio Ripper on Audio CD Insert (On Server)"
date: 2008-05-06
forum: Multimedia Software
---

### Post by HornedBeast on 2008-05-06
Hello All,

I would like to setup my Ubuntu Server (no monitor, all administered remotely) to be able to rip audio CD's using ABCDE when you put any audio-cd into the drive. I have ABCDE setup already, but I have to type ABCDE over SSH to get it to start ripping. I would like this to be automated.

Does anyone know how to do this? Detect that the disc is audio and then run the program ABCDE?

Thanks in advance.

HB

---

### Post by sudocode on 2009-06-05
You can use ivman to detect when an audio CD is inserted and configure it to run abcde when that happens. I got ivman+abcde working on my server and it works great. More details [here]("http://sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html").

---

