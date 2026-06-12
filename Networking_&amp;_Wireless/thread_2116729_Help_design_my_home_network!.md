---
title: "Help design my home network!"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by DuncanNZ on 2013-02-16
This has surely been asked many times, but here goes...

I've wanted to do this for years, but a recent hardware failure and the increasing number of computers in this house have now made  it imperative that I make a robust network storage solution with 

* automated backup (on separate physical hdd)
* file storage (backed up like everything else)
* synchronisation (okay that last one isn't so critical).

I have a spare box to play with (low specs) which is connected directly to my router by cable, everything else in the house is on wireless from the same physical router.

I have a mixed Windows (7, soon 8)/ GNU-Linux environment (plus android phones)

I've played with Linux for about 10yrs now, but mostly thought the gui, so cli skills are weak. I'm guessing I want a Samba server so I'll get started with that on an ubuntu-server installation. If I get everything working okay I will then consider buying some newer hardware if needed.

Feel free to post links, I don't expect to be spoon fed, I'm happy to RTFM if you can tell me what chapter I need!

Thanks for reading, I'm excited!

---

### Post by DuncanNZ on 2013-02-16
Oh dear - bad start. According to this page [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server) I can't get ubuntu server 12.10 for 32 bit hardware. 12.04 it is then... might end up with vanilla Debian down the road...

---

### Post by papibe on 2013-02-16
Hi DuncanNZ.

[Here]("http://releases.ubuntu.com/12.10/") you can find all downloads for 12.10, including server 64bits (called amd64).

Let us know how it goes.
Regards.

---

### Post by papibe on 2013-02-16
> **DuncanNZ said:**
> I've played with Linux for about 10yrs now, but mostly thought the gui...
You can run any "server" service on a Ubuntu GUI version. It just takes a little more resources: more RAM, and a bit more disk space.

If you don't feel comfortable using text only interface, by all means install a Desktop version. I would recommend a lighter desktop like Xfce (Xubuntu), or LXDE (Lubuntu).

There are even lighter versions, if you are interested ;)

Let us know how it goes.
Regards.

---

### Post by DuncanNZ on 2013-02-17
Hi papibe, thanks. Do we agree that there is no 32bit version of Ubuntu Server 12.10? As you say I could just install an xfce version...

I've installed a basic (Samba + SSH) 12.04 server. At the moment I'm fighting with SSH keys and the like. The machine will be headless so I need to learn. I seem to have locked myself out from ssh access on one PC while trying to work out how to generate and share the public key. I think the problem is that I was trying to do it with putty from a windows machine, but all the commands I found for copying the public key were for *nix machines - I can't find a terminal inside Putty.

---

### Post by MrKaliman on 2013-02-17
You can use this tutorial if you are working with putty

[http://katsande.com/using-puttygen-to-generate-ssh-private-public-keys](http://katsande.com/using-puttygen-to-generate-ssh-private-public-keys)

---

### Post by coldraven on 2013-02-17
> Do we agree that there is no 32bit version of Ubuntu Server 12.10?No! See here [http://releases.ubuntu.com/12.10/](http://releases.ubuntu.com/12.10/)

Maybe you did not scroll down the page a bit!

---

### Post by papibe on 2013-02-17
> **coldraven said:**
> No! See here [http://releases.ubuntu.com/12.10/](http://releases.ubuntu.com/12.10/)

Maybe you did not scroll down the page a bit!

+1

This is at the bottom of that page:
> ubuntu-12.10-server-i386.iso
ubuntu-12.10-server-i386.iso.torrent
ubuntu-12.10-server-i386.iso.zsync
ubuntu-12.10-server-i386.jigdo
ubuntu-12.10-server-i386.list
ubuntu-12.10-server-i386.metalink
ubuntu-12.10-server-i386.template

---

