---
title: "gigabyte wireless ubuntu 8.10"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by captaino on 2009-03-02
I am having trouble setting up my new wireless card in Ubuntu.  I just got a Gigabyte GN-WP01GS PCI Card.  I had bought it off of newegg.com and several customers said that it worked with ubuntu 8.10 but I cant seem to get it working.  I have a custom built computer with an MSI 7093 motherboard, 1.8 mhz AMD processor and a gig of ram.  Plenty of help would be appreciated.

---

### Post by Crafty Kisses on 2009-03-02
Hey there, first try reading [this]("http://ubuntuforums.org/showthread.php?t=296822") thread. Be aware that thread is a little old, but it should still work, follow those steps. If that tutorial doesn't work, than can you please post the results of this command?
```
sudo cat /etc/network/interfaces
```
Then from there I or someone else can assist you getting this wireless card up and running.

---

### Post by captaino on 2009-03-03
The tutorial did not work.  Switched the file name with the appropriate updated driver still didnt work.  But here is what terminal said.

> gary@CaptainObvious:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


---

### Post by NoobBiscUiT on 2009-03-28
what does the output of sudo lshw -C network show?

also, sudo lspci -v show you?

if you post them here maybe we can help more.

---

