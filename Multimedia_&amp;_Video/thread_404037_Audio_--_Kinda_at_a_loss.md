---
title: "Audio -- Kinda at a loss"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by mohnkern on 2007-04-07
I've got a fair amount of unix experience, except when it comes to audio, and Kubuntu is giving me fits.

I've got Amarok installed, and it plays mp3's just fine.  However, whenever I open any other player or creator (Like going into cinellera and opening up an mp3) it appears to play, but no audio comes out).  and Totem keeps giving me an error about Not being able to open a resource for writing, even when all other multimedia applications  could be closed.

I'm not sure what the Sound settings should be in Kubuntu, here's what they are now:

Sound System -- Enabled
Enable Networked Sound -- Enabled
Run with Highest Possible Priority -- enabled
Sound buffer -- 278 ms
Auto suspend if Idle after 0 seconds.
Audio Device -- ALSA
Full Duplex
Quality -- 16 bits.


I'm running on board audio, and not a sound card.  

I've got both a sound card, and a USB headset, and for the life of me, I can't see where to select these either (I guess I'm just way to used to the way Windows handles audio devices, rrrr.)

Is there a guide to setting up audio stuff in Kubuntu/Ubuntu somewhere?  I keep seeing bits and pieces.

---

### Post by deadgobby on 2007-04-07
Have you go into your BIOS and disable the on board sound. This all play will go through your sound card. To disable all sound when you system does give you this error. Open up the terminal and type in

killall esd

gobby

---

### Post by mohnkern on 2007-04-08
I don't have a sound card in the machine.

---

### Post by sgx on 2007-04-08
Try installing alsamixergui and alsaoss, and in the now extended mixer, you may well find some things need to be turned up...alsaoss seems to just fix some issues various apps have with competing sound systems...so try rebooting with kde sound system off after installing the above, and then
with it on, and take notes...also install avidemux and kino, video editors on
smaller scale, and test audio there too...I tend  to use xmms for all the ogg/mp3 sounds...tons of plugins for many formats, plus skins and stability...don't give up!

---

