---
title: "Wired network refusing to connect on boot"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by tyke on 2009-06-22
Hey all.

I'm having a really irritating time with my network connection. Whenever I turn my PC on, the network manager fails to connect to the wired network. Clicking on it in network manager manually just makes it time out. 

However, if I reboot the PC, it connects automatically on boot, no problem. 

I've tried disabling network manager, but no dice. It still won't connect till I reboot it. 

It's not huge problem, but does mean that every time I turn my PC on the boot time is effectively doubled.

I have absolutely no idea how to go about de-bugging this, and no idea what could be causing it. I'm using 9.04, and the router is using DHCP. None of the other PCs connected to it have this problem, whether they're wireless or ethernet.

Does anyone have any ideas?

---

### Post by jhannah on 2009-06-24
Do you perhaps have the interface also configured in /etc/network/interfaces? This might be conflicting with the configuration you have in NetworkManager.

When you said you disabled NetworkManager, how exactly did you do this? You should be able to stop it from starting on boot by removing it from the boot scripts:

```
update-rc.d -f NetworkManager remove
```

If you wish to add it back, simple run:

```
update-rc.d NetworkManager defaults
```

Hope that helps.

---

