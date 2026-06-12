---
title: "For anyone having trouble upgrading linksys firmware..."
date: 2006-01-12
forum: Networking &amp; Wireless
---

### Post by woedend on 2006-01-12
After calling tech support, trying to install the router firmware via downloading the .bin file and installing from firefox and getting nowhere, I finally dug around linksys and found an answer but had to be slightly modified.  This is the only method that worked for me hopefully it helps you guys out.  **This assumes the name of the firmware update is code.bin and is in your home folder, if not its easiest to rename it as such** 

sudo apt-get install tftp

after installing that type...
tftp 192.168.1.1  <enter>
binary <enter>
put code.bin <enter>

your only confirmation will say "sent x amount of data in x seconds".  simply type "quit" and push enter.
youll notice the router has reset and youll be finished.

---

### Post by wook on 2006-02-13
Thanks, I needed this info to setup OpenWrt using ubuntu.

---

### Post by woedend on 2006-02-13
glad it helped someone out but i feel i left out one important piece.  you must set router password to blank, nothing, nada. hehe before using those commands so it says.  not sure if it works without it.  btw what is openwrt?

---

### Post by thk on 2006-02-13
I seem to remember that the windows installer runs fine under wine. Also, later versions of the builtin firmware update (via the web interface) also worked for me.

---

### Post by Soarer on 2007-06-22
It just goes to show how useful a search can be. I've been trying to upgrade the firmware in my (excellent) Vigor router with tftp. That router password clue was the bit I was missing. Worked fine after that. Thanks everyone, if you are still on here :)

---

