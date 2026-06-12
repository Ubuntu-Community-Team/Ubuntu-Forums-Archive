---
title: "Does anyone know what program i can use for my iphone?"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by toughcookie508 on 2007-09-26
I dunno what program i can use i have gtkpod but it wont support it. i wasted $600 i want some music on it. 

also how can i take my songs off my ipod video n put em on  my computer?i  heard you can use gtkpod but i can figure it out.

thanxs:KS

---

### Post by gwoodard on 2007-09-27
Heres something, since the "iPhone" came out after this distro (7.04) u will probably have to wait for 7.10 sorry

---

### Post by carlosjoan91 on 2007-09-28
According to this site [http://oregonstate.edu/~bettse/?q=node/24](http://oregonstate.edu/~bettse/?q=node/24) you can use ssh to mount it and then gtk-pod would recognize it as an iPod, hope this helps ^^ 
ps:im just forwarding what i read at that site, i have no experience in the subject, but maybe someone who knows more about ssh coud help you should you get stuck)

---

### Post by wireless on 2007-09-29
in google search 'ubuntu iphone ssh' and the first link should be a guide on how to ssh to ur iphone, very easy and very nice

---

### Post by theskunkydog on 2007-10-09
> **wireless said:**
> in google search 'ubuntu iphone ssh' and the first link should be a guide on how to ssh to ur iphone, very easy and very nice

Huh, the first link is this thread. :p
But, thanks, that did help.  

I used Installer.app beta from windows xp ([http://iphone.nullriver.com/beta/](http://iphone.nullriver.com/beta/)) to set up Community Sources, BSD Subsystem, and OpenSSH.  I can mount my iPhone (firmware 1.0.2) by following [http://www.fsckin.com/2007/09/23/how-to-mount-your-iphone-filesystem-on-your-desktop-in-ubuntu/](http://www.fsckin.com/2007/09/23/how-to-mount-your-iphone-filesystem-on-your-desktop-in-ubuntu/)

sshfs works better i thnk: [http://oregonstate.edu/~bettse/?q=node/25](http://oregonstate.edu/~bettse/?q=node/25)

then i tried both gtkpod and amarok, but i can't get any mp3s or m4v videos to play on the iphone! they copy over and show up in the menu on the iphone, but the mp3s dont play and it complains that the m4vs are corrupt.  

got the latest svn etc.  to be continued...

btw, wifi syncing is great!

---

### Post by tgalati4 on 2007-10-10
If you hand over another $2,400 to Steve Jobs, you will get a shiny new Mac that will talk to your $600 iPhone just perfectly.  You just don't understand the Mac way.

---

### Post by xer0x on 2008-01-16
Check out this page:

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

