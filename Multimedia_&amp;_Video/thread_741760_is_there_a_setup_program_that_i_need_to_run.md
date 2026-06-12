---
title: "is there a setup program that i need to run?"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by Mick8882003 on 2008-04-01
I swapped out my cd/dvd reader for a burner.

I cannot play dvds, is there a setup program that i need to run?

---

### Post by xc3RnbFO8P on 2008-04-01
Can you see the Dvd burner in: Places> Computer
gedit /etc/hdparm.conf
Check if DMA is on
> #/dev/cdroms/cdrom0 {
# dma = on
# interrupt_unmask = on
# io32_support = 0
#}

If it is region problem:
[http://ubuntuforums.org/showthread.php?t=712164&highlight=regionset]("http://ubuntuforums.org/showthread.php?t=712164&highlight=regionset")

---

