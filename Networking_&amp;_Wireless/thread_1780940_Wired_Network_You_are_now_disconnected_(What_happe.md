---
title: "Wired Network: You are now disconnected (What happened?)"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by airspoon on 2011-06-12
I'm havinmg network problems and I have no idea how to fix it. At first, my internet connection was suffering on all computers on my network (Mac, Windows and Ubuntu 11,04). So, I disconnected my cable-modem and then reconnected. Nothing.... So, I rebooted my Windows machine and the internet came back on that computer.
 
I then went to my Ubuntu computer and clicked on "auto eth0" (thinking that would help, per the way I interpreted instructions from the internet). The symbol turned from the "two arrows" to what looks like a wireless, looking for a signal. I thought that maybe I should just reboot, as I did with Windows. However, when I did reboot, that same wireless symbol was there, then a message came up saying:
```

Wired Network: You are now disconnected

```
 
I can't seem to get my internet connection back on my Ubuntu computer, though it is working on every other computer on my network.
 
Can anyone please help? I'm new to Ubuntu and don't really have any idea on what to do. I have tried to search these forums and the internet for a fix, though that's how I believe it got screwed up in the first place (clicking on "auto eth0").
 
Any help would be greatly appreciated and is very badly needed.

---

### Post by 741Baus on 2011-06-12
Hi airspoon if you are comfortable using a terminal run these codes open a terminal Applications-Accessories-Terminal 
```
sudo service network-manager stop
```
```
sudo rm /var/lib/NetworkManager/NetworkManager.state
```
```
sudo service network-manager start
```
and network services will be restarted this is only for ethernet not wireless as far as I know.

---

