---
title: "Ubuntu and Windows XP LAN"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by Robert_P on 2009-04-28
I have set up an ethernet LAN consisting of two Windows XP and one pure (no dual-boot) ubuntu computers via a router. Most everything works...all computers have internet access and the ubuntu computer can look into both XP computers. However, the ubuntu computer is a bit shy and won't appear on either of the XP's network screens. I have tried a number of things without success. As a Linux newbie, I am stonkered.

---

### Post by Iowan on 2009-04-28
Dunno if [this]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html") will help - I suspect that is not the problem.  If Ubuntu gets it's IP address via DHCP, you **might** need to edit */etc/dhcp3/dhclient.conf*. Change the line:```
send host-name "<hostname>";

``` to use your machine's hostname instead. (Uncomment the line if necessary).

---

### Post by Robert_P on 2009-04-29
Thanks for your interest IOWAN. Tried your suggestion without success. Leave it with me for a while. I will try something that has come to mind and if that fails, there is always the revolver in the drawer.
Robert_P
PS. I am using version 9.04

---

