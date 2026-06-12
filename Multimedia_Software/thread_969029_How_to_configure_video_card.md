---
title: "How to configure video card?"
date: 2008-11-03
forum: Multimedia Software
---

### Post by sloboda on 2008-11-03
Hi!
I've installed ubuntu intrepid on my pc, that has a intel gm950.
I want to configure it, to change same configuration, but xorg.org is this:
```
Section "Device" 	
Identifier	"Configured Video Device" 
EndSection  

Section "Monitor" 	
Identifier	"Configured Monitor" 
EndSection  Section "Screen" 	

Identifier	"Default Screen" 	Monitor		"Configured Monitor" 	
Device		"Configured Video Device" 
EndSection
```
And dpkg-reconfigure xserver-xorg doesn't ask me about my video card.
How can I configure it? Is there a program??
I think that is very useful have a tool ti configure video card...

Thanks,
Sergej

---

### Post by bscbrit on 2008-11-03
Quite a few people have had a problem with this.  The software that is used to configure xorg.conf automatically has been changed.  The previous tools for fixing the display do not behave the way they once did, and the graphical tool, displayconfig-gtk, has been removed from the distro.  So, in short, you are left with no easy way to configure xorg.conf.

I had similar problems but resolved them by this method:

[http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

It is UNSUPPORTED and I take no responsibility for any unwanted side effects.  But, it gave me a usable displayconfig-gtk and allowed me to get my computer working again.  It is your decision. Good Luck.

---

### Post by sloboda on 2008-11-03
[QUOTE=bscbrit;6094571]I had similar problems but resolved them by this method:
[http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)/QUOTE]
Thanks a lot, I'll try it as soon as possible.
The intel driver for my video card isn't "beautiful", so I would to disable some option..

Sergej

---

