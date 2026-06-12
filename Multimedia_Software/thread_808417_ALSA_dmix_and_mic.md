---
title: "ALSA dmix and mic"
date: 2008-05-26
forum: Multimedia Software
---

### Post by bagm on 2008-05-26
Hi,

I've got a problem. If I enable software mixing via ALSA dmix plugin, my mic stops being able to capture sound. Can I fix this ?

This is my ~/.asoundrc file:

   pcm.!default {
 type plug
 slave.pcm "dmixer"
   }


   pcm.dmixer  {
 type dmix
 ipc_key 1024
 slave {
     pcm "hw:0,0"
     period_time 0
     period_size 1024
     buffer_size 4096
     rate 44100
 }
 bindings {
     0 0
     1 1
 }
   }

   ctl.dmixer {
 type hw
 card 0
   }

Any help will be greatly appreciated.
Thanks in advance.

---

### Post by bagm on 2008-05-26
I forgot to tell:
Sound card: Cirrus Logic CS4281
Ubuntu: 8.04

---

### Post by bagm on 2008-05-26
Nevermind.

[http://sourceforge.net/mailarchive/forum.php?thread_name=8b17778e0805261502s7b9a089di2ea29945f1586b50%40mail.gmail.com&forum_name=alsa-user](http://sourceforge.net/mailarchive/forum.php?thread_name=8b17778e0805261502s7b9a089di2ea29945f1586b50%40mail.gmail.com&forum_name=alsa-user)

---

