---
title: "&lt;repost&gt; ureadahead broken in Maverick, can't fix with LiveCD"
date: 2010-12-10
forum: Multimedia Software
---

### Post by bkapps on 2010-12-10
Hello, this is my first post to the forums, so far I haven't needed to start a new thread, but this one's a puzzler.

I recently tried to upgrade my graphics card. I had an Intel GMA 950, and upgraded to a PNY Nvidia GEForce 8400GS with 512 DDR

I installed the card, and was unsuccessful in getting it to work, but while using the onboard graphics I updated the drivers in ubuntu to use the Nvidia proprietary drivers. I went into a cycle of rebooting and fiddling. booting into Ubuntu was successful with the onboard card, however I only got a command line. I used nano to change my xorg.conf from saying 

Driver "nvidia". I simply deleted this portion in the hope that X11 would simply think on its feet. Onboard graphics wouldn't deliver any X session after that.


I eventually got the card to work after futzing with the BIOS settings, however once I tried to boot, I got the error 
"init : ureadahead main process (264) terminated with status 5"

after numerous upgrades, my GRUB menu has several kernels, however none of them would boot properly, including recovery sessions.

I decided to boot into a livecd to edit my xorg.conf in a Live environment, but I was unsuccessful, the LiveCD (simply Maverick Meerkat, after trying Karmic Koala) got stuck in a loop of not being able to detect media in /dev/sr0, which is very puzzling.

So now I'm stuck with a computer with a functioning video card and nothing else.

Please help.

---

### Post by magnatron on 2011-03-09
Do you have more than one hard-disk drive like PATA & SATA disks? I had a similar problem when I installed x2 PATA and x2 SATA without disabling the IDE channels in the BIOS, so the LiveCD could never decide which HDD it wanted to install onto. By default it should be the SATA disk's with the IDE or PATA disk's setup as RAID in the BIOS. Hope that helps!

---

