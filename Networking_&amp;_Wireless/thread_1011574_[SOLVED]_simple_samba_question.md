---
title: "[SOLVED] simple samba question"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by pshootr on 2008-12-14
Running samba on ubuntu 8.10 (server) no gui

Where in the samba.conf file do I add the directory I want to share? Also how should the entry look? Thanks

---

### Post by crwmike on 2008-12-14
The Samba config file...

**/etc/samba/smb.conf**

There are instructions and sample in the file.

Here is a sample of one of mine...


[Documents on flatcat]
path = /home/crwmike/Documents
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by pshootr on 2008-12-14
> **crwmike said:**
> The Samba config file...

**/etc/samba/smb.conf**

There are instructions and sample in the file.

Here is a sample of one of mine...


[Documents on flatcat]
path = /home/crwmike/Documents
available = yes
browsable = yes
public = yes
writable = yes

I seen an example only for cdrom in the smb.conf. I wasn' sure if I should go off of that though. Anyway thanks for your sample.

---

### Post by pshootr on 2008-12-14
> **crwmike said:**
> The Samba config file...

**/etc/samba/smb.conf**

There are instructions and sample in the file.

Here is a sample of one of mine...


[Documents on flatcat]
path = /home/crwmike/Documents
available = yes
browsable = yes
public = yes
writable = yes

I used your example to make my entry, and tat worked like a charm. Thank you very much.

---

