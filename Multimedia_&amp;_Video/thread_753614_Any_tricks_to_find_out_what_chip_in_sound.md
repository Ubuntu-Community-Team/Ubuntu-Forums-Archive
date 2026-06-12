---
title: "Any tricks to find out what chip in sound?"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by delta_charlie on 2008-04-12
Hi all, after a lot of searching and trying lots of things it looks like I will not be able to get the sound to work on my MSI P6NGM-FD MOBO.

The MSI site lists the audio as:
  	  	
High Definition 7.1 Azalia Audio
• 	Audio codec Realtek 888
• 	Compliance with Azalia 1.0 spec
• 	Flexible 7.1 Ch. audio with jack sensing

Output of $ aplay -l
aplay: device_list:205: no soundcards found...

Output of $ lspci -v
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7366
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
        Memory at feb78000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-

Anybody know of anything I should try to get the sound working.

Thanks, DC

---

### Post by kidders on 2008-04-14
Hi there,

You may be interested in this thread. A quick google search turned it up ... [https://answers.launchpad.net/ubuntu/+question/22924](https://answers.launchpad.net/ubuntu/+question/22924)

---

