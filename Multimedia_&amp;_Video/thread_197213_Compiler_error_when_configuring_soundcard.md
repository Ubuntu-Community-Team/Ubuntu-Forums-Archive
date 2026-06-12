---
title: "Compiler error when configuring soundcard"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by codesplice on 2006-06-15
Hey all,
I'm working off a fresh install of Ubuntu, and I'm loving it.  I am having some trouble configuring my Creative SoundBlaster Audigy2 ZS Notebook (PCMCIA).  I found a HOWTO on the ALSA project page, I've downloaded all the necessary source files, and I'm trying desperately to get them installed. 

When trying to compile the alsa-driver-xxx, I get the following error:

```
csplice@HAL9000:/usr/src/alsa/alsa-driver-1.0.11rc5$ sudo ./configure
Password:
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
csplice@HAL9000:/usr/src/alsa/alsa-driver-1.0.11rc5$

```

I've reconfirmed that I have the latest version of gcc installed, and I've tried just about everything I can think of.  I'll of course post the config.log if you think it would help, but I'm hoping that someone can shed some light on this difficulty and point out what tiny detail I've overlooked.

Thanks in advance,
John

---

### Post by Crazy_Guitar on 2006-06-15
Well... where did you get those files? Have you managed to solve that problem already?

I have that soundcard and I would like to load my PC with that card and Rosegarden so I can manage samples and stuff...

---

### Post by codesplice on 2006-06-15
I got the instructions [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+2+ZS+Notebook+PCMCIA.&chip=Tina2&module=emu10k1")

and the files from the ALSA project main page, [http://www.alsa-project.org](http://www.alsa-project.org)

Now, any ideas why my gcc hates me?

---

### Post by jsnelli2 on 2007-02-20
Do you have build essential installed?

---

