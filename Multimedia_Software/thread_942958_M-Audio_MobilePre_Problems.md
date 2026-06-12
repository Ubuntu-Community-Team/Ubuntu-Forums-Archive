---
title: "M-Audio MobilePre Problems"
date: 2008-10-09
forum: Multimedia Software
---

### Post by d.justins on 2008-10-09
I have tried following the other post to install my MobilePre USB sound device. 

This one
[http://ubuntuforums.org/showthread.php?p=5300948](http://ubuntuforums.org/showthread.php?p=5300948)

But have failed. I think i'm missing something because i'm too new. I followed the instructions, but i'm not sure if the firmware was actually installed. 

Here's what i know:

When i issue the lsusb command i get,
> 
Bus 007 Device 003: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 0763:2804 Midiman 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c51a Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Which, i can see it as Midiman... I thought it was supposed to be MobilePre, not sure.

When i issue the asoundconf list command i get,

> Names of available sound cards:
Intel


I'm not sure where to go from here. Alsa is up to date. Just trying to get this working for my home studio, no rush.

---

### Post by d.justins on 2008-10-12
Anyone have any ideas on this?

---

### Post by paulg on 2008-10-23
What have you tried so far? What version of Ubuntu are you running (7.04, 7.10, 8.04...)? First suggestion, did you try selecting the card in the sound properties?

It helps if you post at the other thread because I'm subscribed there and will get an email. I do periodically search 'mobilepre' for posts such as yours but I'll be able to respond quicker at the main post.

---

### Post by markbuntu on 2008-10-23
The mobile-pre shows as a midiman device because that is what driver it uses so it is being recognized.

---

