---
title: "How to connect mp3-player?"
date: 2015-03-15
forum: Multimedia Software
---

### Post by xtf on 2015-03-15
Ubuntu-guru.  Can you give advice how to mount mp3-player in Ubuntu 14.04. I connect  player to notebook by using usb-cable but no reaction from Ubuntu.  Gparted when launched does not see usb-memory.

---

### Post by SeijiSensei on 2015-03-15
Make sure the player is set to use "mass storage" mode.  Linux should detect it when connected and mount it as an external drive.

Not all such devices play nicely with Linux.

For debugging purposes, I suggest opening a terminal window and running the command "sudo tail -f /var/log/syslog" before plugging in the device.  When you connect it, the log should show it being detected and configured.

---

