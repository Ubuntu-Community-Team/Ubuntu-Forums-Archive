---
title: "eeepc 900 update of 8.04 breaks networking?"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by candtalan on 2009-11-18
help!
I have 8.04.3 on an asus eeepc 900 and it was working ok just now on a wired network...... I even did a few updates on it, not many, there were only about 8 I think.

I rebooted for some (unrelated) reason and - gone - no network connection.

fwiw this machine has always been ok with ubuntu, with a wired network

lspci indicates:
ethernet controller atheros AR242x 802.11 abg wireless pci express rev 01
Attansic technology L2 100 Mbit ethernet adapter rev a0

This is LTS and this was the last thing I was expecting

any help please?

---

### Post by candtalan on 2009-11-18
Not understood: 
after an hour or so, running the machine on its original xandros os, I now find that ubuntu has got its network back!
what is going on?

---

### Post by candtalan on 2009-11-21
I think I have found what is happening.

When the eeepc 900 with ubuntu shuts down, it leaves  something still running, and the green power light stays on. This is not new behaviour, nor anything to do with any update (I think). I knew it happened but had not realised the possible significance.

However, to then force a shutdown completion, I need to hold the power button down for some seconds. After this, a restart into ubuntu gives a normally working wired connection.

The lack of complete shutdown before 'restart' was not noticed by me - and the problem occurred when using 'Restart' rather than 'Shutdown', because restart appeared to work but not all (services?) were reset, so - no wired network.

PS 
I am aware that other distro and variants will work more perfectly on eee 900 and have used them. However, this machine is partly used as a demo item, to view Ubuntu.

---

