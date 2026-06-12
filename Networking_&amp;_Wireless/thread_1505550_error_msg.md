---
title: "error msg"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by ikenna on 2010-06-09
Hi

Want to run some cmds on Marc Greis Tutorial but always gets an error msg- "can't find ns: no such command. How can I resolve it?

Also do not know how to edit on the terminal Have to start afresh anytime I notice a mistake. I need help

How can I successfully run a file to get a result. Have not been able to reproduce the result in Marc Greis tutorials.


Thank you as I await your v.urgent reply

Ikenna

---

### Post by cariboo on 2010-06-09
Could you give us a link to the tutorial, so that we know what it is that you are having a problem with?

---

### Post by ikenna on 2010-06-09
hi
the link is below

[http://www.isi.edu/nsnam/ns/tutorial/](http://www.isi.edu/nsnam/ns/tutorial/)

Jst get bk to me imm.

I'm waiting

ikenna

---

### Post by lisati on 2010-06-09
The tutorial is hosted on another website: this thread might be better served in another section of our forum.
[LIST=1]
[*]Where in the forums is the tutorial linked to?
[*]Have you actually downloaded and installed ns according to the instructions in the tutorial?
[/LIST]

---

### Post by cariboo on 2010-06-09
It looks like you would be better off using the instructions [here]("http:///nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04").

This really isn't the best place for this thread, moved to Networking & Wireless

---

### Post by cariboo on 2010-06-09
I found an error on the wiki, it says to edit ~/.bashrc, but the file isn't locate in your home directory, it is now located in /etc/skel, so the command would be, press Alt-F2 and type:

```
gksu gedit /etc/skel/.bashrc
```

---

