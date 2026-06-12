---
title: "Network sharing Ubuntu - Vista"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by Orian90 on 2009-07-21
Hey,

I'm trying to make it possible to share my music and other files between my Ubuntu laptop and Vista desktop. At first, this worked great with Samba. However, after some time (about an hour I guess) it just stopped working. I did not change anything at all.

What I did to set Samba up:
Go to my music folder, select share and when asked install samba. Restart, and edit samba's workgroup to "HOME" (my own) by using the command "sudo gedit /etc/samba/smb.conf" (I followed a guide on internet).
As I said, at first it worked perfectly, but now no more.

When I try to acces the map now it says a code (on windows): 0x80070005, and after restarting a few times it also said "you're not allowed to enter this map", while I DO allow him to open the map and even let guests enter (I do not allow others to write in the map, but changing it did not make a difference).

When I try to enter the Ubuntu pc from the ubuntu pc (through networking) I get: "DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered". I have no idea what this means :confused:. 

I tried to reinstall Samba, hoping that would make a difference, however, I can't delete everything. Because when I want to uninstall everything that has a connection to Samba, it also wants to uninstall (through synaptic) my "Ubuntu desktop". I don't want that to happen :P. And when I just uninstall Samba, and not all other files with samba in it, I keep something, because my workgroup already is changed when I reinstall samba. So the file that saves my workgroup does not get deleted.

I really have no idea how to fix this, and hope someone can help. I am a totall Ubuntu noob (moved 4 days ago) but love it already. However, I would like to ask you to explain it as clear as possible, because with a lot of tutorials I have no idea what they are talking about :P

BTW: I use ubuntu 9.04 (32 bits) and vista Home premium (64 bits).

Edit: nvm, for some reason it just works again

---

