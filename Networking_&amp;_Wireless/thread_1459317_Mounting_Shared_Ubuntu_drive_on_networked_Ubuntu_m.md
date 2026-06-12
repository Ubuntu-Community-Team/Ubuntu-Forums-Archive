---
title: "Mounting Shared Ubuntu drive on networked Ubuntu machine [wubi]"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by majikwah on 2010-04-21
I am stumped and have scoured the forums but not found a solution. 
I have a machine running Ubuntu 9.10 that has an external HD with shared folders music folder and media downloads folder).  I have set up SAMBA on that machine. 

On my laptop I am running a dual boot system with Windows Vista and using wubi install, Ubuntu 9.10. 

In Windows, I am able to wirelessly connect to the shared folder and access the music folder and the media downloads folder on my Desktop Ubuntu machine. All is good. 

When I boot in Ubuntu, I am unable to connect to the shared folder under Places > Network I can negotiate to the MSHOME (the name of my work group).  Once selected  I get the error Failed to retrieve Shared List from server error message. 

Any assistance would be greatly appreciated.

---

### Post by garvinrick4 on 2010-04-21
> **majikwah said:**
> I am stumped and have scoured the forums but not found a solution. 
I have a machine running Ubuntu 9.10 that has an external HD with shared folders music folder and media downloads folder).  I have set up SAMBA on that machine. 

On my laptop I am running a dual boot system with Windows Vista and using wubi install, Ubuntu 9.10. 

In Windows, I am able to wirelessly connect to the shared folder and access the bmusic folder and the media downloads folder on my Desktop Ubuntu machine. All is good. 

When I boot in Ubuntu, I am unable to connect to the shared folder under Places > Network I can negotiate to the MSHOME (the name of my work group).  Once selected  I get the error Failed to retrieve Shared List from server error message. 

Any assistance would be greatly appreciated. I just went in to a machine that had Vista and wubi 9.10 and I had to set up samba and add my home folder with rick (me)
and root as owners. Used the Samba in Ubuntu software center. system-config-samba
It works to my workgroup now, never use the wubi anymore but samba did work after I set up. Was in Administration after installed. Just hit browse and add what you want.

---

### Post by Morbius1 on 2010-04-21
I know nothing of wubi and how that would or would not complicate this situation but can you access the share by ip address:

Open **Terminal**
Type **nautilus smb://192.168.0.100**
Change 192.168.0.100 to the ip address of the machine that has the share.

---

