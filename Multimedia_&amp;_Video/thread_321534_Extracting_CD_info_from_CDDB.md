---
title: "Extracting CD info from CDDB"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by cnayak on 2006-12-19
Hello peeps,

  I've been trying to convert my CD collection into .flac using Sound Juicer. The problem is that it always fails to fetch Cd info from cddb servers. And my CDs are of no obscure artist/band, WMP 11 had easily detected them.

  I guess the problem is because I'm behind a proxy server and need to authenicate every outgoing request. However, I've filled up the relevant information in the Systems>Preferences>Network Proxy thing.

 I'm almost frustated at the thought of manually entering the info. Is there any way out?

](*,) ](*,) ](*,)

---

### Post by cnayak on 2006-12-19
Ok, Grip manages to fetch the required info, but the ripping process is very very slow. Can I speed it up? I remember WMP finishing the entire process in less than five minutes

---

### Post by logos34 on 2006-12-21
You can disable (partially or completely) cdparanoia error detection.  Turning off scratch repair roughly equals sound juicer's cdparanoia default setting ('8').  Or throw caution to the wind and use cdd2wav (->dropdown box).

But unless the cds are in fairly good condition, you're risking read errors, missing samples, jitter and whatnot. 

alternatively, try ripperX

---

