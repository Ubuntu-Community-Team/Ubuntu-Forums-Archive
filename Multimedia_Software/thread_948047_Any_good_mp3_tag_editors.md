---
title: "Any good mp3 tag editors?"
date: 2008-10-14
forum: Multimedia Software
---

### Post by morbid_bean on 2008-10-14
Just looking at my large collection of music and only see it as a mess and want to get some organization going, know of any good mp3 tag editors please post them here..   THANKS!:KS

---

### Post by MarCustomized on 2008-10-14
"Quod Libet" comes with an excellent tag editor.

---

### Post by Gamjaevel on 2008-10-28
I've also been looking for one, hopefully this one will do the job :) thanks

---

### Post by gandaran on 2008-10-28
easytag and cowbell, you can find both in synaptic

---

### Post by BB88 on 2008-10-28
I personally use Mp3tag through Wine. It works great to be honest.

Screenshot of it running under Wine on my machine [http://files.mint-space.com/files/20081028122318/Screenshot.png]("http://files.mint-space.com/files/20081028122318/Screenshot.png")

Here is a download link [http://www.mp3tag.de/en/download.html]("http://www.mp3tag.de/en/download.html")

Enjoy.

---

### Post by hardysmiles on 2008-10-28
I use EasyTag exclusively, and have been able to super-organize my music with it.

---

### Post by bvanaerde on 2008-10-28
When coming from Windows, it's quite difficult to try to forget Tag and Rename.
It takes a while to get used to **easytag**, but it's worth trying this program.

---

### Post by krendar on 2008-10-28
> **MarCustomized said:**
> "Quod Libet" comes with an excellent tag editor.

Nods.

Install **Exfalso** via apt-get. I guess its what was mentioned in the quote above.

When its installed I recommend you get the CDDB and Musicbrainz plugin for Exfalso and you have a very powerful tagger.

Here's is how to do it:

> sudo apt-get install subversion exfalso python-cddb python-musicbrainz 

Now start exfalso from the "Sound & Video" menu. Reason is we need it to create the ".quodlibet" folder. Enter the plugins menu in exfalso to make sure the folder is created. Now exit exfalso.

Do this:

> cd ~/.quodlibet
svn co [http://svn.sacredchao.net/svn/quodlibet/trunk/plugins/](http://svn.sacredchao.net/svn/quodlibet/trunk/plugins/)

Now you just installed a lot of plugins. What you need to enable in exfalso is the CDDB and Musicbrainz plugin.

---

### Post by lunarcloud on 2008-10-28
[Amarok]("http://amarok.kde.org/") is really good for organizing and tagging.

It even has [musicbrainz]("http://musicbrainz.org/") built into it.

---

### Post by txGreg on 2008-11-28
> **BB88 said:**
> I personally use Mp3tag through Wine. It works great to be honest. <snip>
OK - just curious... how did you get it to install?  When I try, it errors out saying OS not supported, and quits. 

Did you just copy a working install from a Windows box?  Or something else?

_*update*_
Never mind - turns out it was a hardware problem - loose nut behind the keyboard.

My Wine install was configured to emulate Win2K for some reason.  I updated it to the XP level of self-description, and Mp3tag installed just fine!

---

### Post by Cyhawk on 2008-11-28
Odd, no one has mentioned tagtool. Its small, efficient, and can easily mass re-tag mp3s. I use it all the time to fix albums that don't come out right =)

[http://pwp.netcabo.pt/paol/tagtool/](http://pwp.netcabo.pt/paol/tagtool/)

Its in the 8.10 repository as well under 'tagtool'

---

### Post by uvdevnull on 2009-01-21
> **bvanaerde said:**
> When coming from Windows, it's quite difficult to try to forget Tag and Rename.
It takes a while to get used to **easytag**, but it's worth trying this program.

I'm in that boat man... Spent so many hours with Tag&Rename before Linux, nothing I tried after that could take its place unfortunately.  EasyTag is probably closest, but since I'm able to run the newest Tag&Rename (in portable mode) via Wine, I'm sticking with it for now.

---

### Post by bvanaerde on 2009-01-23
> **uvdevnull said:**
> the newest Tag&Rename (in portable mode) via Wine

Ahh, didn't know it was working so well in Wine.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10703](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10703)
Thanks for the update:p

---

### Post by mistaWAC on 2009-01-23
If you feel like setting up a Windows VM or if you have Windows running somewhere, I strongly suggest something called 'Tag&Rename'.  It's amazing.  I was able to reorganize about 10,000 songs in about a week with it (has bulk editing features).

---

### Post by uvdevnull on 2009-01-23
> **mistaWAC said:**
> If you feel like setting up a Windows VM or if you have Windows running somewhere, I strongly suggest something called 'Tag&Rename'.  It's amazing.  I was able to reorganize about 10,000 songs in about a week with it (has bulk editing features).

Like we said above, Tag&Rename works through Wine, no need for a VM! :)

---

### Post by morbid_bean on 2009-01-24
wow, 3 months later and im still getting replys to my thread..thanks!...i seem to be happy with EasyTAG   I will however try out Tag&Rename

---

