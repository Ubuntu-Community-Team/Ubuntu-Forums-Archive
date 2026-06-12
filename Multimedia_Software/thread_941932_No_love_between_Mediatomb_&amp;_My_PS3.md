---
title: "No love between Mediatomb &amp; My PS3"
date: 2008-10-08
forum: Multimedia Software
---

### Post by pkman1 on 2008-10-08
So here's my problem.  I'm running Hardy Heron, on my PC, and I have a PS3 upstairs.  I've installed Mediatomb on my Linux box, and I must be missing something.  My PS3 sees/connects to me media server fine.  I can browse the database w/out a problem.  The only issue I have is that all of the formats that are natively support by the PS3 are showing up as "unsupported data" .  All of my mp3s, wma's, wmv's are all showing up the same.  I can see all my photo's (jpegs) no problem.

---

### Post by anton_pm on 2008-10-17
Make sure you change this line:

<protocolInfo extend="no"/><!-- For PS3 support change to "yes" -->

so that the "no" reads as "yes"

also this line:

<extension-mimetype ignore-unknown="no"> 

make sure that is set to "no" too. 

you may have to add some mime types too

---

