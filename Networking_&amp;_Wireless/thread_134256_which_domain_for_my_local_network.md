---
title: "which domain for my local network?"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by fm1234 on 2006-02-21
Hi,

which domain should I use in my internal network? Do I have to define a domain? do I have to configure a DNS server for my local network?

somehow, my windows and Ubuntu machine see each other by name, but I don't know what is making it possible.

TIA for clarifications or pointers on this matter.

Fernando

---

### Post by spd106 on 2006-02-22
Domains aren't necessary for a small network. Unless you have a domain controller, you will be using what Micro$oft calls a workgroup, basically every PC is a peer. You will need to give the workgroup a name, default on windows is mshome. Samba allows you to share files easily with a windows network.
Have a look at this wiki page for more info on [samba]("https://wiki.ubuntu.com/SettingUpSamba").

---

