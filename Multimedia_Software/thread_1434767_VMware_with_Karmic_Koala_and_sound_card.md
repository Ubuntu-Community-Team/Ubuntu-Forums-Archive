---
title: "VMware with Karmic Koala and sound card"
date: 2010-03-20
forum: Multimedia Software
---

### Post by gtmeloney on 2010-03-20
I am running 64-bit (version 9.10) on a VMWare workstation. I am having an issue with my sound card.
 
This is the message that I get when I start the VM:
[INDENT]A device ID has been used that is out of range for your system. Sound will be disconnected
[/INDENT]I am running Vista-64 as my host OS. I know it might be easy to blame this on Windows, but I also have an XP guest OS and sound works fine there, so it is definitely an Ubuntu related issue. Any idea how to fix it?
 
Thanks

---

### Post by JimInAtl on 2010-05-08
I have a similar problem with any vervsion of Ubuntu and host OS 64-bit Windows 7. I think the problem could be related to the combination of 64-bit architecture and sound drivers. What motherboard and sound system are you using? I have ASUS P6X58D, which comes with Realtek audio on-board.
 
My XP guest OS works perfectly, except certain NetMeeting audio options will cause the sound to disconnect in the VM. I can restart the VM and all is well. The only thing common here is the VM and 64-bit environment.

---

