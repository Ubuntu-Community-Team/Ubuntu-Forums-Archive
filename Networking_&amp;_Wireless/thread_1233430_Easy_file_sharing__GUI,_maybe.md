---
title: "Easy file sharing?  GUI, maybe?"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by antonius on 2009-08-06
Is there still not a "simple" GUI for noobs to arrange a file sharing, heck, any resource sharing on a LAN?  If not, anyone recommend a simple technique?  I really would appreciate the help.  One computer is using Ubuntu 9 and the other is using gentoo, which I know, shouldn't matter one bit.  Thanks in advance!

antonius

---

### Post by NotJustANewbie on 2009-08-06
ssh is probably the easiest way to do this.
[http://p25ext.lanl.gov/ssh/ssh-howto.html](http://p25ext.lanl.gov/ssh/ssh-howto.html)

---

### Post by antonius on 2009-08-06
I guess that's a "no" on the GUI.  I've used nfs integrated into Nautilus before, but it was quite a pain to set up.  This is really what I want to achieve.  All the computers on my network to be recognized by nautilus.

---

### Post by NotJustANewbie on 2009-08-07
Have you tried samba with nautilus? I've managed to do that before with the connect to server program from the menu.

---

### Post by dmizer on 2009-08-07
So ... right click on the folder, select "Sharing options" and making sure all three boxes are checked ... is not sufficient?

If not, then you might want to check this post: [http://ubuntuforums.org/showpost.php?p=7737180&postcount=98](http://ubuntuforums.org/showpost.php?p=7737180&postcount=98)

Just because you see lots of directions on how to do things with the CLI, doesn't mean that there aren't GUI tools. It just means that text translates perfectly to text.

If you're talking about an NFS server, I'm not aware of any GUI configuration tools, but it's [not really that difficult](http://www.ubuntuforums.org/showthread.php?t=249889) to configure an NFS server and client via the CLI.

---

### Post by SlugSlug on 2009-08-07
install ssh on the pcs then got to places > connect to server > ssh server and add it to book marks

it will just be like browsing folders on a local machine

---

### Post by NotJustANewbie on 2009-08-07
> **SlugSlug said:**
> install ssh on the pcs then got to places > connect to server > ssh server and add it to book marks

it will just be like browsing folders on a local machine

thats exactly what I meant, but with nicer words ;)

---

