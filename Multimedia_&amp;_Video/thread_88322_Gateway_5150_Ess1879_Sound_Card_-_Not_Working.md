---
title: "Gateway 5150 Ess1879 Sound Card - Not Working"
date: 2005-11-10
forum: Multimedia &amp; Video
---

### Post by dczx on 2005-11-10
Hi,

I've installed the newest Ubuntu on my Gateway Solo 5150 laptop. Unfortunately, the sound is not working.

I added snd-es18xx to /etc/modules and it didn't do anything.

It never seems to detect it in system... it shows ESS1879 but doesn't see it as a sound card.

I turned off PnP OS in the BIOS, still nothing....

I tried using ALSA only and turning off ESS, still nothing...

could anyone please help? thank you.

---

### Post by andlinux21 on 2005-11-10
i got my sound working!!!!! thank goodness it took me long enough now my laptop is complete well almost I cant hear anything in MPlayer but i am sure i can fix that too with a little reading. What i did was i added 

sb io=0x220 dma=1 mpu_io=0x330 irq=5

to the module start up file and that did the trick it loaded my soundcard

---

### Post by dczx on 2005-11-10
Well, that sort of worked. I can't get any system event sounds in gnome. It shows them ungreyed but they don't play. Playing stuff in sound and multimedia programs worked though, except when I tried to play CD Audio. Nothing.

I take it this is broken in this release of Ubuntu from an earlier post. Is a new release coming soon?

---

### Post by jthirt on 2005-12-19
I'm a complete newbee for linux and ubuntu. 

I have found this thread that adresses my current problem exactly as I installed 5.10 on a solo 5150 and can't get the sound card (ESS1879) to be recognized. 

I would gladly try what you recommend, but where do I add this ?

sb io=0x220 dma=1 mpu_io=0x330 irq=5

I have no idea where to find the module startup file refered to !

---

### Post by el duderino on 2006-05-02
Hello fellow Solo 5150 users...

here is some almost related work that Thinkpad 600 users have been doing...

[http://ubuntuforums.org/showthread.php?t=96240&highlight=laptop+soundcard](http://ubuntuforums.org/showthread.php?t=96240&highlight=laptop+soundcard)

I could use some clarification on where/what to edit to get my sound working.

Anyone got a wifi PCMCIA card working? I have an SMC 2635W that is giving me a headache...

---

