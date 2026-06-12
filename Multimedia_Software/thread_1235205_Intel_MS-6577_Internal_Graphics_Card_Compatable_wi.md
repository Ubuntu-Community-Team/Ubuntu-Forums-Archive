---
title: "Intel MS-6577 Internal Graphics Card Compatable with Jaunty ?"
date: 2009-08-08
forum: Multimedia Software
---

### Post by NukeouT on 2009-08-08
Hi

I built a mini ATX computer with Ubuntu. It used to have this ASUS motherboard 

[http://www10.shopping.com/xPF-Asustek-SiS-Chipset-CUSI-FX-20216373](http://www10.shopping.com/xPF-Asustek-SiS-Chipset-CUSI-FX-20216373)

After maxing it out with 2x 512mb 133hrz, PIII 1000hrz processor it is still chugging Jaunty.

So rescently my friend found me a mini intel motherboard with a P4 processor.

[ftp://download.intel.com/support/motherboards/desktop/d865perl/rl_English.pdf](ftp://download.intel.com/support/motherboards/desktop/d865perl/rl_English.pdf)

When I had the ASUS motherboard, I tried running it with an old intel graphics card but I had lots of issues. So now I want to install this mini intel motherboard and run Jaunty with the internal intel graphics card (alhough this is probably a newer card than i was using before).  The motherboard has only pci ports, and i really dont want to buy an additional pci card, while at the same time its not likely i will come across one for free.

is the graphics card in this motherboard compatable with Jaunty or will it have issues?

thanks

---

### Post by pytheas22 on 2009-08-08
Are you positive that motherboard has integrated video?  I skimmed the PDF you linked to and I don't see anything about onboard graphics, only audio.  But I could be missing it.

In any case, I suspect you'd be able to get any Intel video device working on Jaunty without too much trouble.  Although there are major problems with many Intel video cards on Jaunty, most can be solved by [reverting the video driver to an older version]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4").  Or wait for the next release of Ubuntu in October, where most of the Intel graphics problems are supposed to be fixed.  Or use Ubuntu 8.10...

---

### Post by NukeouT on 2009-08-10
this is more correct info on the motherboard I have

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00068983](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00068983)

well if you say that its a main issue they will be fixing in the next update I can wait for it. I am not using that computer all that much atm anyway. Last time I had intel graphics problems i could still see the GUI in ugly 16bit color. 

I just need to put this PC together so I can clean up the spare parts lying around.

---

### Post by Yellow Pasque on 2009-08-10
It's an Intel 845G.

---

