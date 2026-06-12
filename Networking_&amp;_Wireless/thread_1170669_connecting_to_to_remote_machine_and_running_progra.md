---
title: "connecting to to remote machine and running programs"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by tevang on 2009-05-26
Dear Ubuntu users,

I have 2 laptops, the new one at the office which has Kubuntu 9.04 installed, and the old one which I leave at home with Kubuntu 7.10. Apart from accessing files and directories from one another I would also like to run remotely Unix commands and programs installed on each machine. Is there a way to do that? Is remote desktop relevant with that kind of operation?

thanks in advance,
Tom

---

### Post by fld on 2009-05-26
Yes.

To run programs you have two possibilities:
if programs without GUI, use ssh
if with GUI, your solution is vino (server) and vinagre (client).

Configure the server, then access the machine from the other one.

Or try a mixed solution like ssh -X which tunnels the GUI (sort of..) but you may be proficient on the shell first :p

bye,
fld

---

### Post by superprash2003 on 2009-05-27
+1 for ssh

---

### Post by tevang on 2009-05-28
I found this cool tutorial:

[http://www.linuxjournal.com/video/access-remote-gui-programs-using-ssh-forwarding](http://www.linuxjournal.com/video/access-remote-gui-programs-using-ssh-forwarding)

I suppose this is what you mean by ssh -X.

But what about KDE remote desktop? It pops up every time I reboot and I'm wondering if it's up to the task.

PS: fld I use KDE and don't think vino would work without problems there.

---

