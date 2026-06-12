---
title: "newbie help"
date: 2010-08-07
forum: Mythbuntu
---

### Post by banff2010 on 2010-08-07
This is what I have as a TV tuner card
> 
00:0c.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
Can I use this?

---

### Post by ian dobson on 2010-08-07
Hi,

OK your card looks like a Analog tuner card with a Hardware MPEG encoder so it could be a PVR150 or PVR250.

The card should be detected automaticaly by linux. Just run myth-setup, and create a mpeg tuner card.

Note: Analog TV is being switched off slowly in most parts of the world.

Regards
Ian Dobson

---

### Post by banff2010 on 2010-08-07
Thanks.

---

### Post by banff2010 on 2010-08-08
I installed it on  a desktop with 10.04, have two problems.
I tried both setting for my card  in backend, but after scanning it does not find any channels. So, I manually set 3 channels, there is are blue Icon on those. But then when I tried to connect frontend on the same machine it gives errors, says backend is not activated, check ip address etc.


Help please. I googled, but none of the suggestions seems to work.

---

### Post by banff2010 on 2010-08-08
Ian, I went to your homepage and downloaded your mythdatabase checker and I am quoting part of it.
> 
[OK].Found 2 video sources
[OK].Videosource 1 '' has a EPG source defined (schedulesdirect1)
[OK].Videosource 2 'Shaw co-axial cable' has a EPG source defined (/bin/true)
[!!].Videoinput 1 does not have any card inputs defined
[OK].Videoinput 2 has 1 card inputs defined
[--].Checking start channel for each cardinput
[--].Checking channel change script for each cardinput
[OK].All InputCards are linked to a videosource
[!!].Videosource 1 does not appear to have any channels defined
[OK].Videosource 2 has 3 visible and 0 invisible channels defined
[!!].cardinput 1 does not appear to exist as a device
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[OK].All dtv_multiplex entries have a valid channel


---

### Post by ian dobson on 2010-08-09
Hi,

OK, when you defined the card input as what did you define it? /dev/video? MPEG hardware encoder.

Are you using the external IP address of the backend or "localhost". Go though the control-center setup again checking that everything is configured correctly, then run myth-setup and check the tuner card configuration.

Regards
Ian Dobson

---

