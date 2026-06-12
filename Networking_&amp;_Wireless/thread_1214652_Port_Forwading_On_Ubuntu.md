---
title: "Port Forwading On Ubuntu"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by r3x on 2009-07-16
hi every body there, i am a windows user form last 8 years, now i want to move
on the linux os as i found it much better then windows. after installing linux 
every thing goes fine bt the problem is with my dsl router port forwading.

i have forword a port for p2p (torrents) in my dsl router's console and it works just fine in windows. 
the torrent applications works fine with that port and if i check online websites,  they say
yes the port is forward.

bt on linux the torrent applications don't accept that port is forward and same online 
websites which give OK report on Windows says that port is not farword on linux.

what's that ? do i have to do some thing extra on linux os. i have tried different ports
as well.

and i have tried on Mandriva, Ubuntu, Fedora both in KDE and Gnome Mode.
please help me to move on to linux. as this is the only problem i am facing
on linux plateform

---

### Post by wojox on 2009-07-16
Do you have ufw enabled? Go to terminal > 

```
sudo ufw status
```

If it's enabled, either disable it or forward the port.

What torrent client are you using?

---

### Post by r3x on 2009-07-16
give me some information about ufw ? what's this ? and i have tried default torrent client of ubuntu 9.04 and kubuntu 9.04

---

### Post by carml on 2009-07-16
UFW stays for Uncomplicated FireWall, it's a command-line interface to iptables the firewall installed by default on every *buntu installation. :)
With the command suggested by the previous user,if a remember correct you can check which ports are enabled and first of all if UFW is active on boot or not.

---

