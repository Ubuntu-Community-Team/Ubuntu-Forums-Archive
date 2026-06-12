---
title: "Need a stable nvidia video driver"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2006-12-28
I need a reliable video driver for a Geforce 6200 Turbocache for Kubuntu Edgy 64-bit on an AMD-64 3400+.
Currently using 1.0-9631, but it's not working for me, hangs and crashes several times a day and colours are all washed out every time I reboot.

---

### Post by tseliot on 2006-12-28
> **pickarooney said:**
> I need a reliable video driver for a Geforce 6200 Turbocache for Kubuntu Edgy 64-bit on an AMD-64 3400+.
Currently using 1.0-9631, but it's not working for me, hangs and crashes several times a day and colours are all washed out every time I reboot.
Did you try driver 9629?

It worked well on my father's card (a 6200 PCI-E Turbocache).

You can find in this "old" version of envy:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.2-0ubuntu1_all.deb)

download this file and follow the instruction on this page:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by pickarooney on 2006-12-28
OK, trying that now. I'll let you know tomorrow if it's more stable.
Cheers,
P

---

### Post by pickarooney on 2006-12-29
Ach, no :( It only took two hours for the system to freeze up and die again.
Back to the drawing board

---

### Post by pickarooney on 2007-01-04
I've found I can provoke the crash at will by using google earth for ten seconds. I could live without google earth, but the crashes still occur at random moments every day - even a sed command seemed to freeze the whole system yesterday. Still not sure if this is a gfx issue or not.

Has anyone any tips for narrowing down the possibilities? I've pretty much ruled out a memory issue by testing with each of the two 512MB sticks on its own and in turn, and I don't think it's overheating.

---

### Post by pickarooney on 2007-01-05
Turns out there was a bug in the nvidia driver used for 6200 Turbocache cards in conjunction with an [ATI RS480](http://www.nvnews.net/vbulletin/showthread.php?t=64682) chipset. Nvidia included a workaround in their latest driver, 9746. I installed it and am testing it now. So far so good :)

---

### Post by tseliot on 2007-01-05
> **pickarooney said:**
> Turns out there was a bug in the nvidia driver used for 6200 Turbocache cards in conjunction with an [ATI RS480](http://www.nvnews.net/vbulletin/showthread.php?t=64682) chipset. Nvidia included a workaround in their latest driver, 9746. I installed it and am testing it now. So far so good :)

Thanks for reporting

---

### Post by Cope57 on 2007-01-05
I had a issue similar to this, but it ended up being the video card fan dying out and stopping which overheated the video card.
I reinstalled different drivers, reinstalled different OS's and it was driving me crazy until I opened the case to do some weekly cleaning.
That is when I found the problem with the video card fan not doing its job.  ](*,)

---

