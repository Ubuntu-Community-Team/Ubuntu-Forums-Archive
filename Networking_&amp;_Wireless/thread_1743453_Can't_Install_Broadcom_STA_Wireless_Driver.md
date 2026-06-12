---
title: "Can't Install Broadcom STA Wireless Driver"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by arroyocallejas on 2011-04-29
In Ubuntu 11.04 32-bit
Dell Studio 1558

Everytime I want to active it I got the following:

Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

I don't know if this is related to Software Sources, I only have Canonical Partners and Independent.

I installed Ubuntu 11.04 from an ISO file and used the whole disk

---

### Post by KegHead on 2011-04-29
Hi!

Have you tried;

system...admin..additional drivers?

KegHead

---

### Post by arroyocallejas on 2011-04-29
Yes I tried to no avail. It seems it's a bug but now It's fixed!
Here is what a did:

sudo apt-get clean

sudo apt-get autoremove --purge bcmwl-kernel-source

sudo apt-get update

sudo apt-get install --reinstall bcmwl-kernel-source

*Sometimes before the last command it's necessary to add this one too:

sudo apt-get -f install

After that I install the drivers via Additional Drivers and everything works fine.

---

### Post by KegHead on 2011-04-29
Congrats!

Please mark your thread as "solved"

KegHead

---

### Post by Pablulu on 2012-06-07
Thank you so much for your help, 

I did it, and it works perfectly.

No I have my computer totally functional again, thanks.

;)

---

### Post by Pablulu on 2012-06-07
Sorry, I forgot giving a bit of information of my particular case.

I've solved my wireless problem with this solution in a Dell Vostro 1320, with a Broadcom Wireless. I'm using Ubuntu 12.04 Precise Pangolin, so it works too for this OS.

Thank you!

---

### Post by daniela9488b on 2012-08-03
Finally something helpful. Thank you arroyocallejas!

---

### Post by wildmanne39 on 2012-08-03
Old thread closed.

---

