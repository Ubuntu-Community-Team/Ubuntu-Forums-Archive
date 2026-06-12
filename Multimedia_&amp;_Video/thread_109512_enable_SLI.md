---
title: "enable SLI"
date: 2005-12-28
forum: Multimedia &amp; Video
---

### Post by tronica on 2005-12-28
A while back i found here on the forum a way to enable SLI through the command line. But I can't for the life of me find that. Can someone point me to it or give me the command. Thanks.

---

### Post by mrf on 2005-12-28
I'm no expert, but I'm pretty sure the only way to enable it is by adding the option into the device section of your xorg.conf : 

     Option "SLI" "string"

string being yes, no, afr, sfr, or sliaa

It's documented in the readme, at the bottom of this page : [http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-d.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-d.html)

You'll need the latest drivers. but other than that it's fairly simple...

---

### Post by tronica on 2005-12-28
ok i found out what i was thinking of.

 % nvidia-xconfig --sli=on
just type that in the terminal

---

### Post by mrf on 2005-12-28
looks like it just does the edits for you... meh, thanks nvidia, but I think I'd prefer to know whats in my .conf file.

---

### Post by Orylin on 2008-01-16
you can also try

$ sudo nvidia-settings

then from there you should have the option

hope this helps.

---

