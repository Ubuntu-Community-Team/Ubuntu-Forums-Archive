---
title: "Window borders in Gnome Shell"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by thezood on 2011-04-13
Hi,

I'm trying the new Gnome3 PPA and fell fast in love with Gnome Shell. However, the window borders of the programs seem to be of some old ugly standard sort and the Adwaita theme is nowhere to be found on my system. I can't find any repo package for it, nor installation files. Also, only a few people has had the same problems and I haven't seen a solution for it. Does anyone have a clue?

I can't really get into my Natty beta partition anymore (blank screen with mouse pointer after login) after messing about with this and I thought I'd reinstall it when the beta image is released tomorrow. Still, it would be interesting to know what happened to the theme...


Anders.

---

### Post by Visceral Monkey on 2011-04-13
Hey zood, I had the same problem and someone kindly helped me so I'm here to pass the info on:

Post number 86 on the following link has the missing theme and instructions how to quickly install it. It worked for me.

[http://ubuntuforums.org/showthread.php?t=1722627&page=9](http://ubuntuforums.org/showthread.php?t=1722627&page=9)

---

### Post by Harry33 on 2011-04-13
> **thezood said:**
> Hi,
I'm trying the new Gnome3 PPA and fell fast in love with Gnome Shell. However, the window borders of the programs seem to be of some old ugly standard sort and the Adwaita theme is nowhere to be found on my system. I can't find any repo package for it, nor installation files. Also, only a few people has had the same problems and I haven't seen a solution for it. Does anyone have a clue?
I can't really get into my Natty beta partition anymore (blank screen with mouse pointer after login) after messing about with this and I thought I'd reinstall it when the beta image is released tomorrow. Still, it would be interesting to know what happened to the theme...
Anders.

Do you have this Gnome3 package installed:
 - gnome-themes-standard (3.0.0-1~~build1)
That contains the Adwaita theme.

---

### Post by Visceral Monkey on 2011-04-13
> **Harry33 said:**
> Do you have this Gnome3 package installed:
 - gnome-themes-standard (3.0.0-1~~build1)
That contains the Adwaita theme.

Interestingly enough, that package would not install for me so I had to install Adwaita manually. Weird. Additionally, the theme directory was write protected to only allow a root user to put anything in there, which might explain why it fails when I try via software center. I had to open nautilus via "gksudo nautilus" so I could drop the the Adwaita folder in there.

---

### Post by thezood on 2011-04-13
I'll try these things if the same problems appear after reinstalling Ubuntu. Damn, it would be sweet to have Gnome Shell working. :)

Thanks for your fast replies.

---

### Post by Harry33 on 2011-04-13
> **Visceral Monkey said:**
> Interestingly enough, that package would not install for me so I had to install Adwaita manually. Weird. Additionally, the theme directory was write protected to only allow a root user to put anything in there, which might explain why it fails when I try via software center. I had to open nautilus via "gksudo nautilus" so I could drop the the Adwaita folder in there.

You mean the directory /.themes had permission only for root?
If so, you can easily change that with "gksu nautilus".
And of course only root has permission to /usr/share/themes.

---

### Post by Visceral Monkey on 2011-04-13
> **Harry33 said:**
> You mean the directory /.themes had permission only for root?
If so, you can easily change that with "gksu nautilus".
And of course only root has permission to /usr/share/themes.

Show hidden files didn't reveal the .themes dir for me for some reason so I used /usr/share/themes which did require root. A small work around, but it appears to have worked. Maybe I looked in the wrong place for .themes?

---

### Post by Harry33 on 2011-04-13
> **Visceral Monkey said:**
> Show hidden files didn't reveal the .themes dir for me for some reason so I used /usr/share/themes which did require root. A small work around, but it appears to have worked. Maybe I looked in the wrong place for .themes?

It is here:
/home/"username"/.themes
and it is hidden.

However, /usr/share/themes should require root priviledges.

---

### Post by linux_wannabe on 2011-04-14
I tried the solution in post #86 of the thread above (manually installing the Adwaita theme).  That worked to get the general window decoration (buttons, etc), but Nautilus still looks old and ugly, especially the breadcrumbs - they're just boxy buttons.  Anyone got an idea of how to fix that?

Thanks!

---

### Post by 23dornot23d on 2011-04-14
Show us a screen shot of what you have ......... ;) ....... there are a few links to tweaks .....

someone posted these not so long back - [LINK Location Bmbaker]("http://ubuntuforums.org/showpost.php?p=10674822&postcount=340")

[http://blog.fpmurphy.com/2011/03/cus...e-3-shell.html]("http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html")
[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)
[http://gnome-shell.deviantart.com/](http://gnome-shell.deviantart.com/)


for changing things ......

I am also trying to keep a thread and link where what I try to do I record >>> [**the LINK is here**]("https://sites.google.com/site/000menu/home/gnome---3")

( If I fine anything new I will try to keep this up to date and post to it ...... as there are a few threads now )

---

### Post by linux_wannabe on 2011-04-14
Good point!  Here's a screen shot.  I suspect there are other things not working yet, I just don't know what they are supposed to look like (for example, the battery icon seems different on some screenshots than mine, don't know if that's 'cause they changed it?).  I haven't made any modifications (at least, not intentionally).

---

### Post by 23dornot23d on 2011-04-14
That screen shot looks good to me ......

Would not be worried just yet ...... do you have any applications that crash .....

Do you have any problems with getting to files .....

Do you use photo editing software like gimp or shotwell ..... do they run ok .....

Do you do videos or watch online TV ......

At the moment I am finding it hard to crash Gnome Shell ..... and believe me I am trying hard.


( UNITY ..... I just boot into it and the borders to windows do not appear. [[COLOR=Red] >>> SCREENSHOT[/COLOR]]("http://img33.imageshack.us/img33/6949/screenshot2nl.png") )

---

### Post by thezood on 2011-04-14
I'm also having issues but it's not the window borders that's the problem, it's the GTK theme of buttons etc. It seems different programs is being rendered in different ways. See screenshot, Firefox doesn't look like Nautilus at all.

---

### Post by 23dornot23d on 2011-04-14
I get that too ..... but you are running Gnome-shell there .... and its still in early development 

I think as time progresses these things will hopefully get ironed out ..... 

I changed mine to two with the tweak tool as I like to just click minimize as well .....

Less keystrokes to me is always better ...... that to me is progress .....

Its easy to make things more complicated and not to add more keystrokes to options we already have
that work so fast and easily .

---

### Post by linux_wannabe on 2011-04-14
thezood -- that's exactly what I've got, too. After you ID'd it as a GTK theme issue, I used the gnome-tweak-tool and found that my GTK theme and icon theme were set to some random other thing.  I changed both to Adwaita and it looks much better now.

Out of curiosity, can you create documents on your desktop, or delete files from nautilus using the "del" key?  Those are things I could do in 10.10 and can't do now, and I don't know if they're Gnome Shell issues or 11.04 issues.

Hope that helps!

---

### Post by linux_wannabe on 2011-04-16
> **linux_wannabe said:**
> thezood -- that's exactly what I've got, too. After you ID'd it as a GTK theme issue, I used the gnome-tweak-tool and found that my GTK theme and icon theme were set to some random other thing.  I changed both to Adwaita and it looks much better now.

Out of curiosity, can you create documents on your desktop, or delete files from nautilus using the "del" key?  Those are things I could do in 10.10 and can't do now, and I don't know if they're Gnome Shell issues or 11.04 issues.

Hope that helps!
I solved the files on the desktop issue... in the gnome-tweak-tool there's a "allow file manager to manager desktop" option (that's not verbatim).  Turning it on allows files to be placed on the desktop.

---

### Post by thezood on 2011-04-17
> **linux_wannabe said:**
> thezood -- that's exactly what I've got, too. After you ID'd it as a GTK theme issue, I used the gnome-tweak-tool and found that my GTK theme and icon theme were set to some random other thing.  I changed both to Adwaita and it looks much better now.

Out of curiosity, can you create documents on your desktop, or delete files from nautilus using the "del" key?  Those are things I could do in 10.10 and can't do now, and I don't know if they're Gnome Shell issues or 11.04 issues.

Hope that helps!

I have reinstalled Natty and right now I can't even install gnome3 due to a missing dependency. The PPA is only a couple of days old, so I think I'll leave it for a few days and let the master control programs do their magic first. ;)

---

