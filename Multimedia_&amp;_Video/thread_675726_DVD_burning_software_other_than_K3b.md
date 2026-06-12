---
title: "DVD burning software other than K3b?"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by darkstar8 on 2008-01-23
Hi,

This has most likely been asked before, but can anyone recommend CD/DVD burning software other than K3b?
I like K3b but whenever I try to install it in Synaptics it tries to uninstall a bunch of seemingly unrelated stuff, Blender (!?), mplayer, and a couple of codecs being the prime examples (I dabble in Blender and watch live video streams using mozilla-mplayer).
Also, it requires transcode which for some reason won't install, since about a dozen dependencies aren't satisfied and aren't available through synaptics.

I've burned CDs/DVDs with Nautilus's built-in feature but I can't find a way to erase CD-RW's or DVD-RWs. If someone could tell me how that'd work just as well (it'll probably be one of those slap-in-the-forehead solutions...).
I've also tried Gnome CD Master but it seems to only have support for CD-Rs and CD-RWs.

I'm using Feisty on a laptop, and I'd really rather not learn all the ins-and-outs of the command-line options.
Especially if I ever want to show off to my friends the GUI portion of Linux.

If no one has a suggestion I might have to buy Nero...which wouldn't be all bad but I'm more interested in free software.

Sorry for the long rambling post.

---

### Post by DarkDancer on 2008-01-23
Brasero seems pretty good. It's in the repos.

---

### Post by logos34 on 2008-01-23
> **darkstar8 said:**
> I've burned CDs/DVDs with Nautilus's built-in feature but I can't find a way to erase CD-RW's or DVD-RWs. If someone could tell me how that'd work just as well (it'll probably be one of those slap-in-the-forehead solutions...).
I've also tried Gnome CD Master but it seems to only have support for CD-Rs and CD-RWs.

I'm using Feisty on a laptop, and I'd really rather not learn all the ins-and-outs of the command-line options.
Especially if I ever want to show off to my friends the GUI portion of Linux.

If no one has a suggestion I might have to buy Nero...which wouldn't be all bad but I'm more interested in free software.

Brasero or** Gnomebaker** is your best bet.

If you must use nero: don't pay for it!  Use the trial version (I think it's still avail)... But it's my default cd/dvd app in windows XP, that version has a LOT more features).  

command line isn't all that bad:

> sudo umount /dev/cdrom

cdrecord dev=/dev/cdrom blank=fast

---

### Post by disturbed1 on 2008-01-23
> **logos34 said:**
> 
If you must use nero: don't pay for it!  Use the trial version (I think it's still avail)...But it's my default cd/dvd app in windows XP, that version has a LOT more features).  


We need software companies such as Ahead to further the development of software and the Linux community as a whole.

---

### Post by logos34 on 2008-01-23
> **disturbed1 said:**
> We need software companies such as Ahead to further the development of software and the Linux community as a whole. 

Maybe Ahead should be fair and include the linux version in their bundled Nero burning software that comes with retail CD/DVD drives (which we are paying for after all)--then there wouldn't be an issue.  That's how I got my mine (only the windows version, that is).  They're cheating linux users.  

Have a nice day!

---

### Post by asmiller-ke6seh on 2008-01-23
Using the NERO software, even a trial version, outside of the license use as permitted is piracy. No Ifs, Ands, or Buts about it.

That's why I limit myself to Open Systems solutions.

*[COLOR="Blue"]In a world without walls, who needs Gates and Windows (and restrictive license agreements, and pay as you go software which seem to require that you pay for an upgrade every year.[/COLOR]*

---

