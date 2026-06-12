---
title: "Kernel Panic, Missing Keyword, I/O Errors on 11.04 beta USB Install"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jackelope on 2011-04-02
Hi guys,

I've tried to install the 11.04 beta multiple times. I've used the USB Creator tool and Unetbootin under Windows to load the ISO onto a flash drive. 

The first time I tried it, it booted into a live environment from the USB drive, but gave me an I/O error (bad disk) half way through the install. Tried it agian, same result. Install dies at about 70%.

So I downloaded a fresh copy of the ISO, burned it to a new USB drive, and booted it again. It now gives me a kernel panic on boot. Something about not finding the right boot sector. Sorry, I don't remember exactly what it said.

So I tried formatting the whole drive (minus my Windows partition) with ext3, and then loaded another USB drive with the ISO image. This time I boot up from the USB drive and get a "Unknown keyword in configuration file." error. 

Gave up, and...

I installed Linux Mint (had a Mint CD lying around). It installed with no trouble, and the Windows partition is working fine as well. I can't find anyone else having these issues. Any idea what's going on?

Could it have something to do with my last Ubuntu install (10.10) having an encrypted home folder?

Thanks for any help! I was really excited to try out Unity, and now this =(

---

### Post by Perfect Storm on 2011-04-02
Moved to Development & Testing Forum.

---

### Post by Jackelope on 2011-04-05
"Solved" all these issues by using the alternate install CD.

---

