---
title: "configuring X for ATI video card"
date: 2009-01-18
forum: Multimedia Software
---

### Post by Craig_DT on 2009-01-18
I just installed the ATI binary driver from the buntu repositories for my card, an ATI Radeon Xpress 1100 but in xorg.conf it's not there or when I ran "fglrxinfo"
I tried running aticonfig but received the error message that told me the driver line was empty in xorg.conf

I'm pretty average on the command line and have no clue what to do next, but I really want my graphics card to work!!

I'm running 8.04 on an Acer Aspire 5101 laptop,AMD turion processor 2.0Ghz, 1.5Gb Ram (128 of which is dedicated to the graphics card I can't use) 

btw, I have Catalyst control centre installed but it doesn't recognise the installed driver and the error window says "try aticonfig"

So I'm kinda lost now, any advice would be really appreciated, thanks.


-Craig.

---

### Post by markbuntu on 2009-01-18
You need to run

aticonfig --initial -f

and then reboot to initialize the driver.

---

### Post by Craig_DT on 2009-01-20
Hey, 

thanks for the reply. I tried that and I receive the same error message, but twice, it says found unitialised file, configuring but then still fails, saying segmentation fault in xorg.conf.

---

