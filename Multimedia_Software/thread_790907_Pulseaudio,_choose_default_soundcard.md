---
title: "Pulseaudio, choose default soundcard"
date: 2008-05-11
forum: Multimedia Software
---

### Post by zhark1 on 2008-05-11
Does anyone know how to set the default soundcard in pulseaudio?
My M-Audio card is always loaded up as the secondary card, but I want it to be the primary.

---

### Post by wolfen69 on 2008-05-11
i take it you have onboard sound? if so, just disable it in bios and ubuntu will only see 1 card.

---

### Post by zhark1 on 2008-05-13
Yeah, I've got onboard sound + the M-Audio PCI card.
The thing is that I need the microphone input on the onboard card in some applications, like VoIP. It would then be best to set the M-Audio card as the primary card, and then just configure individual applications that need the microphone to use the onboard card. This wasn't a problem before (in Gutsy) with Alsa, but I've googled, and searched this forums, but can't seem to find any direct way to do this in Pulseaudio, surely it must exist an option, or a way to do it, somewhere?

---

### Post by zhark1 on 2008-05-18
Problem solved by installing and configuring using the padevchooser!

---

