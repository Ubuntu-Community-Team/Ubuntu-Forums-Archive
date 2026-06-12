---
title: "Audio Problems on Pandaboard"
date: 2011-09-24
forum: Multimedia Software
---

### Post by schwerminator_ on 2011-09-24
Hi. I have a Pandaboard Rev A2 with Ubuntu 10.10 installed, but I am having trouble with the sound, it simply does not work. In the release notes, I found the following hint:

> On the OMAP4 pandaboard the sound initialization does not work properly due to a race condition between udev rules and upstart jobs. Calling "alsaucm set _verb HiFi" and "sudo alsactl store" in a terminal will work around this. An updated alsa-utils package that fixes this issue automatically is being prepared (746023)

So tried to to call the first command, but it says "alsaucm: command not found". What do I have to do to get it work?

Thanks in advance.

---

### Post by schenkelklopfer on 2011-09-29
do you have alsa installed??
for me alsaucm is working..
but the method is wrong:
>  alsaucm set_verb HiFi
but its not working.. because set_verb is a wrong call..
>  alsaucm set verb HiFi
this one says: verb is wrong, hifi ist ok...


if you make:> 
cat /proc/asound/cards

you should get something like:
>  0 [SDP4430        ]: SDP4430 - SDP4430
                      TI OMAP4 SDP4430 Board
 1 [PandaHDMI      ]: PandaHDMI - PandaHDMI
                      TI OMAP4 HDMI Board
if i do:
> sudo alsaucm listcardsi get:
> Im setting defaults
  0: SDP4430
another question: which resolution do you have?
i can only use: 640 x 480
reminds me to the last century ;)

---

### Post by schenkelklopfer on 2011-10-06
try:
alsaucm set _verb HiFi 
sudo alsactl store

---

### Post by schwerminator_ on 2011-10-17
Hi there. Sorry for answering that late.

When I type in "cat /proc/asound/cards", I get:
```
0 [Panda            ]: OMAP4 - Panda
                       TI OMAP4 Board
```

And the whole "alsaucm"-Command doesn't work. It always says "command not found"! Since that command seems elementary: Is there a way install it?!

> another question: which resolution do you have?
i can only use: 640 x 480
reminds me to the last century 
I use full HD resolution. But I had the same problem you have with another screen (Samsung 24"). Try using a different screen, if you have one...

---

