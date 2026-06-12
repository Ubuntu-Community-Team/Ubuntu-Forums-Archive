---
title: "64-bit Feisty:  NOTHING will play .mkv files"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2007-04-21
I can't get ANY of my multimedia programs to play .mkv files...  Kaffeine, Totem, MPlayer, VLC...nothing.   As near as I can tell, I've got all the recommended packages...

Is this a Feisty thing?   A 64bit thing?   Both?  Neither?   

As I recall, they play fine on my openSuSE 10.2 installation (also 64-bit).

Any ideas?

---

### Post by RomeReactor on 2007-04-21
Hi. Do you have the w64codecs? Perhaps they'll help. You can find them through the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories, in case you don't have them.

---

### Post by wilberfan on 2007-04-22
> **RomeReactor said:**
> Hi. Do you have the w64codecs? Perhaps they'll help. You can find them through the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories, in case you don't have them.

Oooh.   I had no idea there WAS such a thing...   

 I went and installed them--but it didn't help.     Anything else I could try??

---

### Post by wilberfan on 2007-04-22
Well, in one of those mysterious things that only penguins understand...*it's working now!!     *   I have to assume it was the w64codecs??  (I don't understand why it didn't work last night, though...!)

---

### Post by wilberfan on 2007-05-21
OK. I'm having this exact problem again.   Following a clean re-install of Feisty (don't ask) I can no longer play my .mkv files.  (Totem says:  "There is no plugin to handle this movie."  VLC just races though the entire 30 minute file in, like, 4 seconds without any sound or picture.  Kaffeine says there is "...no plugin found to handle this resource."   Etc.)

I've installed the ubuntu-restricted-extras.   I've installed the w64codecs.  I've even tried the Automatix route.   I've rebooted several times...(yes, desperate times call for XP behavior!)  Everything else seems to be playable by everthing else (MPlayer, Kaffeine, etc...)

As you can see from this thread, I had it working under Feisty a month ago!

This is driving me batty...

---

### Post by wilberfan on 2007-05-21
Well, it continues to be quite weird:    As before, I suddenly *was* able to play my .mkv files (after renaming the folder and opening from withing Totem)...and now I can't again.   So it's NOT the lack of codecs that's the problem.   Something more systemic??   File pointers, or....???!

[edit] I HAVE gotten these to work from the Totem 'open' dialogue--sometimes--but not so far from clicking on the file in Nautilus.   I just got it to work through the network (via ssh)on my other Feisty box (32-bit)  so there's something strange/buggy involving feisty and .mkv files (or at least THESE mkv files)?

---

