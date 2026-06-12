---
title: "Installed Sound Blaster Audigy 24-Bit - Failed"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by Xanderfoxx on 2007-10-22
[COLOR="Navy"][FONT="Franklin Gothic Medium"]Problem: Installation of "Creative Labs Sound Blaster Audigy SE 24-Bit" Failed

This is for my experimental desktop PC. :lolflag:

I bought this card after some research through Alsa Project, and Ubuntu's Campatability List for decent cards that have a penchant for autodetection and successful installation (Just working), but apparently I did not do a thorough enough look into the matter.

The card worked upon first boot. The card successfully autodetected, and just worked without needing me to get down and dirty with my machine. :)

It was apon my second boot that the trouble began.

I was downloading Gutsy via a Torrent on UTD's Mirror, when I noticed my computer was being a little too silent. I checked the mixers and volume controls, and I checked my speakers' connection to the interface to my sound card. They all passed.

I have not yet checked the solidity of the connection to my motherboard, though alsamixer is telling me that it is using my onboard sound, which doesn't work, and even if it did, I would prefer the sound card I bought.

I have no sound from either output jack. :(

If anyone has some advice, I would be most grateful. :guitar:

Please ask me for any outputs via command line, or file contents, so I can make them available. I trust you guys,

Thanks in advance.[/FONT][/COLOR]

---

### Post by georanma on 2007-10-23
figured if post here instead of starting another thread....having issues with my audigy platinum and gutsy. It should be ready to go from what i have read on sites about creative linux drivers...i even checked to see that alsa was install, however i get bad distortion and noise over any audio that i play. 

ideas?

---

### Post by Xanderfoxx on 2007-10-27
Additional info:

I went and tried to do my share, and I came up with this.

> 

**The module options for snd-ca0106:**

description:  	CA0106
author:  	James Courtier-Dutton
license: 	GPL 	
parm: 	index:Index value for the CA0106 soundcard. (array of int)
parm: 	id:ID string for the CA0106 soundcard. (array of charp)
parm: 	enable:Enable the CA0106 soundcard. (array of bool)
parm: 	subsystem:Force card subsystem model. (array of uint)

**Introduction for CA0106 soundcard**

There are two ways of getting Linux drivers to work, you can either compile them into the kernel or build them separately as modules. Read the Kernel-HOWTO for details of how to compile a kernel.

You must turn on the sound support soundcore module. This is in the kernel. Look in the sound drivers directory and it should be the first option. Most people enable the module setting. That way you can load and unload the module manually if you have multiple soundcards/&#8203;devices or if you intend to debug or use cutting edge software which may cause your drivers to halt sometimes. Of course it also means you have more control of your system.



Output from "$ modinfo soundcore"
```


filename:       /lib/modules/2.6.15-28-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.15-28-386 preempt 486 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92


```

I'll be adding to this post as I attempt to make progress on my lonesome.

{3:50 on Sat, Oct 27, 2007} I recently checked the connection, and cleaned the PCI slot on the motherboard. It wasn't that.

---

### Post by Xanderfoxx on 2007-10-27
[COLOR="#CC00FF"][SIZE="7"]SOLVED!!!![/SIZE][/COLOR]

Yes! I manged to fix it on my own! Yay!

I feel a little better about myself, now.

I know now that the desktop it just quiet as heck, so I didn't notice any immediate difference, after I:
[LIST=1]
[*]Cleaned the PCI slot, and carefully reinserted the sound card, and
[*]Adjusted ALSA's volume controls via "$ alsamixer"
[/LIST]

Thank you for your patience.

Thank you for your comments, and

sorry, georanma, about ditching the thread, but if I could help you, I would. I'm just not solid enough in my knowledge of LInux cures and such to be giving advice to people quite possibly quite smarter than myself. If you want help from me, ask. I'd be honored, but don't expect miracles.

---

