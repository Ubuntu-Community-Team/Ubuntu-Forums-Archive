---
title: "Beatquantizer"
date: 2006-03-23
forum: Multimedia &amp; Video
---

### Post by efflux on 2006-03-23
I can confirm that Beatquantizer runs in Ubuntu 5.10 distribution with Ubuntu Wine package.  Beatquantizer has so far operated flawlessly. This program is kind of like Recycle on steriods if you haven't used it.

I use a Mac with Logic Pro for music but I'm ditching my PCs to move to Linux. Mainly for graphics but being able to simply run Beatquantizer has been a great bonus.

I will be following what happens here because any added music capabilities on Linux Ubuntu will be great. I want to keep using Ubuntu because it's the best distribution I have tried.

I'm using an M-Audio Delta 44 by the way.

I have another PC which is still infected with XP. It has a Layla 3G audio card. I have tried getting this to work on various Linux distributions but it is a lot of hastle. You need proprietary firmware for a start. Compiling various versions of ALSA etc - too much hastle for the average user. If any Ubuntu music version can be easily set up with this card that would be cool. It's a much better soundcard than the M-Audio. I get some minor problems with groudloops in my studio when using M-Audio meaning my only easy alternative is RME but these are expensive. Getting a distribution to work with Echo Audio (Layla 3G) soundcards would be great because they are good value cards. I know closed source firmware can't be supplied but anything that helps wiht these cards would be a bonus.

---

### Post by efflux on 2006-03-23
Slight mistake in my previous message. I meant to say that I'm ditching XP on my PCs to move them to Linux. Of course I'm not "ditching my PCs"

---

### Post by ssavelan on 2006-12-07
I am trying to get a Echo Layla 24/96 PCI working with 6.10 i386.  no luck yet.  I agree that the Echo's are good value cards.  They're ***** for not hooking up a Debian driver, though.  I saw somewhere that they have no plans for a Linux driver.

I got the generic source code.  No luck yet.  gui-ALSA-utils has 'echomixer' but that doesn't sense the layla.

Seems like Echo and Ubuntu would be great partners... echo's products are very straightforward and could be very powerful in the context of the ubuntu/debian world of applications.

---

### Post by luneo on 2006-12-08
Have you guys read the Alsa-project documentation on Layla 3G? [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Layla+3G.&chip=Motorola+56361%2C+FPGA&module=echo3g](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Layla+3G.&chip=Motorola+56361%2C+FPGA&module=echo3g)

Layla24:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Layla24-CARDBUS.&chip=Motorola+56361%2C+FPGA&module=layla24](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Layla24-CARDBUS.&chip=Motorola+56361%2C+FPGA&module=layla24)

And just Layla:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Layla.&chip=Motorola+56301%2C+FPGA&module=layla20](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Layla.&chip=Motorola+56301%2C+FPGA&module=layla20)

'cause those boards are supported by alsa...

---

### Post by luneo on 2006-12-08
And another site... teaching how to compile everything..
[http://www.webalice.it/g_pochini/ead/](http://www.webalice.it/g_pochini/ead/)

---

