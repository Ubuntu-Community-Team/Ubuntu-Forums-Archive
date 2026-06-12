---
title: "Can I network connect 2 Ubuntu machines easily?"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by jonobe on 2008-12-13
I've recently got my own Ubuntu Ibex machine, and managed to interest my place of work in getting one running as well.  I have never networked before, but would like to get them directly connected.  I have a crossover cable.  If anyone could describe simple steps (if there are any) to connect the two of them,bearing in mind i'm a newbie?

---

### Post by Iowan on 2008-12-13
"Easily" is the key word.  By "connect" I presume you mean "[share files]("https://help.ubuntu.com/8.04/internet/C/networking-shares.html")".  Most Linux filesharing seems to be on a client-server basis.  One machine serves files, the other receives them.  To go both ways, both machines must be configured as client *and* server.
The default *nix system is [NFS]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html"), but sharing files with Windows systems generally requires [Samba]("https://help.ubuntu.com/community/SettingUpSamba")... although it can also be used between Linux machines.  Another method uses [SSH]("https://help.ubuntu.com/community/SSHFS") for secure file transfers. [Printer]("https://help.ubuntu.com/community/Printers") sharing is another option.

It's an easy choice if you have only one option, but the buffet complicates things somewhat.  Hope I haven't muddied the waters - too much.

Perhaps this [networking]("https://help.ubuntu.com/8.04/serverguide/C/networking.html") help page will be useful (although it's for servers).

---

### Post by jonobe on 2008-12-13
Thanks, i'll check out your links - i am looking to share files, so as client and server on both, but would like the choice.  Is the client the one 'in control'? - is there an administrative hierarchy, so to speak?

---

### Post by Iowan on 2008-12-13
> **jonobe said:**
>   Is the client the one 'in control'? - is there an administrative hierarchy, so to speak? :? Who controls the bank account - the client or the banker? The server can limit access, but I'm not sure that's what you're asking.

---

