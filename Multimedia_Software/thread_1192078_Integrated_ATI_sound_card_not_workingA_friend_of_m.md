---
title: "Integrated ATI sound card not workingA friend of mine installed on his old P4 ubuntu."
date: 2009-06-19
forum: Multimedia Software
---

### Post by refdoc on 2009-06-19
A friend of mine installed on his old P4 ubuntu (jaunty). He is delighted with the speed gain and the features - so far so good.

Problem - the motherboard integrated sound card does not work.

I am not even remotely near the computer and have no ability to access it via ssh.

I asked him to test via System->Preferences->Sound the various sound options ALSA, OSS etc: none worked.

I then asked him to do lspci -v and email it to me. I got following from him:

Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
Subsystem: Foxconn International, Inc. Device 0c81
Flags: 66MHz, slow devsel, IRQ 17
Memory at fdff9000 (32-bit, non-prefetchable) [size=256]
Capabilities: [access denied]
Kernel modules: snd-atiixp

What I note is that my laptop's Intel sound card has as the last two lines:

Kernel driver in use: Intel ICH
Kernel modules: snd-intel8x0


The line Kernel driver... is missing in his printout.

Any clever ideas?

---

### Post by markbuntu on 2009-06-19
A lot of people have reported problems with Jaunty and their AC'97 sound chips. It seems the alsa driver/kernel has a serious regression in regards to these.

---

