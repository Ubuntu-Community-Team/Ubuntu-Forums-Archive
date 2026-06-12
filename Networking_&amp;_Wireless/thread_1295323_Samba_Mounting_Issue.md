---
title: "Samba Mounting Issue"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by CCKrause on 2009-10-19
Can someone explain an "issue" I'm having with Samba?

I have set up two Samba servers, both running on server versions of Ubuntu 9.04

One is running in VirtualBox on top of an Ubuntu 9.04 desktop laptop, the other on actual hardware a Windows workgroup LAN.

I have no problems what-so-ever with the version running in VirtualBox. I can connect to it with my laptop boot version of Ubuntu, a VirtualBox installation of Windows XP, and an XP laptop sitting out on the network.

I can copy, add, edit, and save files with all systems.

The versions sitting on the server hardware, I can access fine with windows XP.

I have problems using it as myself on my Ubuntu laptop (which is the host for the virtual Samba server as well).

If I launch Nautilus as my user account, I can copy files from the server version of samba, but I cannot create, edit, or replace files.

If I launch Nautilus as super-user, I can use it perfectly well - just as I can the samba server on the VirtualBox server.

All three systems (laptop, virtual server, and actual server) have the same account names and passwords. Even the same Samba passwords.

What am I missing here? 

I can't access the mount because I don't own it? I'm mounting the shares from the command line using sudo.

Why do the two systems act differently?

---

### Post by CCKrause on 2009-10-19
Doesn't seem to be a Samba server problem - testing it out from multiple systems on the network (windows and mac) I can access the shares just fine. It seems to be an ownership/permissions issue under Ubuntu with the local connection/mount point.

I'm mounting via:

```

sudo mkdir ~/local_directory
sudo mount -t cifs //server_ip_address/userName ~/local_directory -o user=userName
```If I don't access it via

```
sudo nautilus
```or
```
sudo cd ~/local_directory
```I get permission errors when trying to update files, or replace files.

What could I be doing wrong here?

---

