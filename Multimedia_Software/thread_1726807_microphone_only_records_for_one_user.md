---
title: "microphone only records for one user?"
date: 2011-04-11
forum: Multimedia Software
---

### Post by tlroche on 2011-04-11
summary: 2 users, both admin, on a netbook running 32-bit maverick/10.10. The built-in mic only works for one user. How to fix?

details:

I'm trying to setup Skype for multiple users on a [Starling](http://www.system76.com/product_info.php?cPath=28&products_id=105), but it only works for me. In debugging I believe I've isolated the problem. If I login as me and do

```
me@it ~ $ arecord -f cd /tmp/junk.wav
Recording WAVE '/tmp/junk.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
# speak in the direction of the mic
^CAborted by signal Interrupt...
me@it ~ $ totem /tmp/junk.wav &

```

I get playback of what I spoke. I then restart and login as another user (who is also in group=admin), but

```
gf@it ~ $ arecord -f cd /tmp/junk.wav
Recording WAVE '/tmp/junk.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
# speak in the direction of the mic
^CAborted by signal Interrupt...
gf@it ~ $ totem /tmp/junk.wav &

```

produces no sound. When logged in as the other user,

[LIST=1]
[*]I can play sounds, so I believe this is not an output problem.
[*]In Preferences>Sound>Hardware, profile="Analog Stereo Duplex".
[*]In Preferences>Sound>Input, there is only one device="Internal Audio Analog Stereo", and it is selected.
[*]In Administration>Users and Groups, both users have Account type=Administrator.
[/LIST]

How can I ensure all users can use the microphone (e.g., for skype) or debug the problem further?

---

### Post by tlroche on 2011-04-13
> **tlroche said:**
> 2 users, both admin, on a netbook running 32-bit maverick/10.10. The built-in mic only works for one user. How to fix?

Any ideas? Note both users have identical/correct alsamixer settings.

---

