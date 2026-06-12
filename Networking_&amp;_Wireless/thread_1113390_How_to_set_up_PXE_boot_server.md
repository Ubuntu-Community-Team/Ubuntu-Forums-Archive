---
title: "How to set up PXE boot server"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by ChodeOfDoom on 2009-04-01
hey,
i am a linux novice and a networking novice, so as to expand my knowledge in both and at the same time have some fun, I decided to set up a PXE boot server... i just don't know how.  I am installing Server 8.10 on a Dell PowerEdge 500sc right now and am going to do my best to get this working.  The only limitations I have are that I need the server's ip adress to be 192.168.0.2 because I have an IPcop server as 192.168.0.1.  Thanks!:p

EDIT:
i would like it to boot WIn XP if possible, but if not I will settle for Ubuntu.

---

### Post by Iowan on 2009-04-01
[Here]("http://www.howtoforge.com/ubuntu_pxe_install_server") is a How-To - but it's a couple of versions old...
[Another ]("http://ubuntu-tutorials.com/2007/10/11/how-to-configure-pxe-network-booting-on-ubuntu-for-network-based-installations/") but might be for Ubuntu client.

---

### Post by ChodeOfDoom on 2009-04-01
I saw the first page that you gave the link for already and decided that that was my best bet for doing this.  however, I really cannot do much as my comp does not seem to be connected to the internet and I am incapable of doing anything without a GUI. and with no internet connect, i dont get a GUI.  so if you have a way to do this using win2k (i have a bootleg copy of the 4-in-1 cd) i would be greatful! (that is if i can PXE boot win XP)
and just to make myself clear to all who see my thread, i want to PXE BOOT not INSTALL!!!

---

### Post by capscrew on 2009-04-01
> **ChodeOfDoom said:**
> I saw the first page that you gave the link for already and decided that that was my best bet for doing this.  however, I really cannot do much as my comp does not seem to be connected to the internet and I am incapable of doing anything without a GUI. and with no internet connect, i dont get a GUI. 

You don't need need to connect to the Internet to have a GUI interface on your computer.  If you mean that you can't download the complete install, that's another issue.  Are you having problems connecting to the internet and installing? 

>  so if you have a way to do this using win2k (i have a bootleg copy of the 4-in-1 cd) i would be greatful! (that is if i can PXE boot win XP)
and just to make myself clear to all who see my thread, i want to PXE BOOT not INSTALL!!!

PXE is used to install an OS on a bare iron box over the local network (LAN).  What is it that you are attempting to do?

---

### Post by ChodeOfDoom on 2009-04-21
i have seen people boot the actual os from the network like when using an ubuntu live cd.  I assure you that if you search through youtube, you will find a handful of videos of people doing this

---

