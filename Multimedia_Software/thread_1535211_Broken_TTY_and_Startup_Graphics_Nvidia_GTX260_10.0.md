---
title: "Broken TTY and Startup Graphics Nvidia GTX260 10.04"
date: 2010-07-20
forum: Multimedia Software
---

### Post by atomp on 2010-07-20
Hello,

On my upgrade to 10.04 I have gained a certain unwelcome problem with non-Xserver graphics on my machine. I am using the official Nvidia drivers from the Nvidia site (although I'd prefer not to be) and have been for some time as when I built this computer other drivers were not available for the card.

Anyway, upon upgrading I notice that there is an issue with all graphics prior to the login screen as well as with all consoles (tty1, tty2, tty3, etc). The display shows a garbled band of distorted colours about an inch in height from the top of the monitor. Input makes the band change pattern but at no point does it become readable in any sense of the word.

I have conducted some tests and I have found that the recovery boot does not suffer from this problem (thankfully) so whatever is causing this, it is not started when the recovery boot loads.

My attempted to fix this problem have mostly been down in modifying graphics drivers and xconf, however nothing that I managed to get working provided much of a fix or a satisfactory working condition compared to the official Nvidia drivers.

Any suggestions would be greatly appreciated. Having no access to consoles without a reboot into the recovery mode or having no boot up loading screens and feedback isn't OS breaking, but it is an irritation, especially when Ubuntu requires some form of booting task such as fsck.

Details:
Ubuntu 10.04
Nvidia Linux x86 256.25 driver on a Nvidia GTX260

---

### Post by ajgreeny on 2010-07-20
Have you read the sticky note at [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) which talks about many of the known bugs in 10.04, including what sounds like your problem of plymouth displaying wrongly.

I had a similar problem and removed all the plymouth themes except **plymouth-theme-text** and now it is much better.

---

### Post by atomp on 2010-07-21
Many thanks to you for pointing me to that thread and my apologies for not finding it and starting this thread somewhat pointlessly.

On a side note, it was the FRAMEBUFFER=y in /etc/initramfs-tools/conf.d/splash solution that fixed the problem.

Once again many thanks.

---

### Post by AndyCinDallas on 2010-07-23
That helped me tremendously, thank you - my graphics were terrible when booting up and I couldn't see anything in the virtual consoles at all with my Nvidia card.

I followed the directions at [How to Fix the Big and Ugly Plymouth Logo in Ubuntu 10.04](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml) and the splash is visible on boot and all my tty consoles work now as well :D

---

