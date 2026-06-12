---
title: "why can I not see the rest of my network? this is killing me!"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by fourtyseven on 2009-10-28
Our network at work is a Windows 2003 domain. I however, do not use Windows but rather Ubuntu. Up until recently I could see and browse our network with no problems even though I was not joined to the domain. 
Suddenly one day I could no longer see the network. When I go to Places>Network I get a 'Windows Network' icon as usual but once I click it, a blank screen appears.
This is not the first time this has happened and the only way I was able to solve it previously was to re-install. That worked for a while but now Im back to square one again. Does anyone know why this happens and what I can do to remedy the situation?
Also, if I access the same network from another machine, I can see my computer in the list but when I click on it I get the message: "Unable to mount location. Failed to retrieve share list from server."
Help me please.

:popcorn:

---

### Post by Iowan on 2009-10-28
Do you have **winbind** installed? Dunno if [this]("http://ubuntuforums.org/showthread.php?t=1169149") might help...

---

### Post by fourtyseven on 2009-10-29
Ok well I finally managed to get it working although it only works when I actually type the ip address of the relevant server in the location bar. I cant for the life of me undrestand why though.

---

### Post by darkksyde on 2009-10-29
Instead of having to always enter the ip address, have you tried putting the computers on the same workgroup?

---

### Post by Iowan on 2009-10-29
> **fourtyseven said:**
> ...it only works when I actually type the ip address of the relevant server in the location bar. That used to be a bug -  dunno if it got fixed (thought so...) For a quick/dirty, have you tried setting up address/hostname pair in */etc/hosts*?
... or is address dynamic?

---

### Post by ant2ne on 2009-10-29
I know that in a purely windows domain network, sometimes it takes the windows computers some time after booting to browse the network.

---

### Post by fourtyseven on 2009-10-30
It doesnt really matter anymore. For some reason it only works when I manually type in the address. Its possibly a bug that needs to be addressed.

---

