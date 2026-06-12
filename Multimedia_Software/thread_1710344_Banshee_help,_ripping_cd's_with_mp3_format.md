---
title: "Banshee help, ripping cd's with mp3 format"
date: 2011-03-19
forum: Multimedia Software
---

### Post by Biciclettapc on 2011-03-19
I have banshee installed and starting to rip cd's inside Ubu using Banshee.

I am unable to change the rip file format from anything but ogg.  I need to rip to a mp3 to suit the players, phones, etc.

I have no audio cd preference in the edit menu.  

Maybe banshee is out of date and needs updates, but I am unable to find banshee team ppa in the synaptic.

Thanks
Paul

---

### Post by handy on 2011-03-19
I don't use Ubuntu, or Banshee. So this is a shot in the dark.

Have you installed all of the extra files that include the codecs & libdvdcss & the like that Ubuntu can't distribute due to licensing issues (in some countries at least)?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

As it is possible that this is the cause of your problem.

---

### Post by Biciclettapc on 2011-03-19
> **handy said:**
> I don't use Ubuntu, or Banshee. So this is a shot in the dark.

Have you installed all of the extra files that include the codecs & libdvdcss & the like that Ubuntu can't distribute due to licensing issues (in some countries at least)?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

As it is possible that this is the cause of your problem.

Thanks, installed, but I still see no options for importing in banshee.

I am open to other music players that will allow me to synch up with non apple players

---

### Post by Biciclettapc on 2011-03-19
Got it, read where sound juicer is used.

Working ,thanks.

Paul

---

### Post by handy on 2011-03-20
> **Biciclettapc said:**
> Got it, read where sound juicer is used.

Working ,thanks.

Paul

Cool. I like it when shots in the dark get somewhere near the target. :)

---

### Post by TokyoYank on 2012-01-08
For others on 11.10 googling in, I found a fix within Banshee:

Install (for example through Software Center) 'GStreamer extra plugins', or perhaps more conveniently, 'Ubuntu restricted extras'

(To be fair, I have many of these packages installed, but AFAIK the above are all you need)

Within Banshee:
[B]Edit > Preferences > Source Specific > Source:  Audio CDs > Import format
[/B]
On my machine, '**MP3 (LAME Encoder)**' is an option.  I also toggle other settings I like.

---

