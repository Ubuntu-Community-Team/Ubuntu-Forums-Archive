---
title: "lost the windows shares on network after update"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by sgian on 2012-05-31
Hello,

A couple of weeks ago I lost the ability to access my windows machines from my ubuntu machines.  Windows computers don't even show up anymore.  It was after some update, I don't remember which one and I'm not sure if it was a windows or ubuntu update that made me lose access to windows machines.  Here are the computers I have:

hp laptop with ubuntu 12.04
emachines desktop with windows 7
hp slimpc desktop with dual boot windows 7 and ubuntu 12.04

I've tried searching for this problem, but I haven't found any solutions that worked.  Like I said, it used to work accessing windows from ubuntu over the network.  However, I never bothered setting up ubuntu to be accessed from windows since I didn't feel the need.

I was using smb/cifs to access windows over the network from ubuntu, which worked fine until a couple of weeks ago.  This week, I installed Samba also, but I still don't see any windows machines on the network.

I do have a wireless printer that still prints over the network from ubuntu, but I had to remove it from the windows computer and set it up on the wireless network to work again.

---

### Post by sgian on 2012-05-31
update:

I did an update on the ubuntu computers.  The hp slimpc with dual boot windows 7 and ubuntu 12.04 is now seeing and accessing windows machines.  However, the hp laptop with ubuntu 12.04 still does not see or access windows machines.  So it must be some problem with this laptop.

---

### Post by sgian on 2012-05-31
still working on it.

I've tried to delete and reload samba, but I keep getting errors.  Then when I reboot between deleting and reinstalling samba, ubuntu freezes up while shutting down. The most recent error while trying to reinstall samba is below:

> 
Errors were encountered while processing:
 samba
Setting up samba (2:3.6.3-2ubuntu2.2) ...
start: Job failed to start
invoke-rc.d: initscript nmbd, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess installed post-installation script returned error exit status 1


All I understand of this is that something failed to start.

---

### Post by sgian on 2012-05-31
After deleting and reloading samba multiple times, it finally started working.

---

