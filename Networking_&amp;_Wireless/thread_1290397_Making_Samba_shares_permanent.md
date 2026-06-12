---
title: "Making Samba shares permanent"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by PaulHeywood on 2009-10-13
Hi there,

I've successfully shared a partition on my linux desktop so my xp netbook can see it - but I've noticed that after a reboot of the ubuntu desktop the share is lost.

Is this because I'm only using Nautilus to set the shares up ?  Should I be doing something different to make sure the shares are permanent?

Any help would be appreciated,

Paul.

---

### Post by i.r.id10t on 2009-10-13
You'll need samba server packages and to create a smb.conf file - swat is a good tool for doing this.

---

### Post by PaulHeywood on 2009-10-13
The Samba server packages are all installed and working fine - the xp netbook can see the share prior to the reboot of the desktop, but I'll see what Swat gives me, thanks.

---

### Post by doas777 on 2009-10-13
jsut to confirm, after reboot, are you logging back into the ubu host before trying to access the share? 

if so, and it still does not work, try running this on the ubu host:
```
sudo /etc/init.d/samba restart
```
does it work now?

with network-manager, you don't have a net connection until after login, so boot time services like samba fail (since there is no IP to bind to). you need samba to start up after the network connection is established.

just a though. good luck

---

### Post by PaulHeywood on 2009-10-13
Thanks for the thoughts - I'm probably not explaining the problem as well as I could:  

Yes, I'm logging back in to the Ub host, but I noticed that when I looked at the properties of the shared partition through Nautilus it had no sharing check boxes ticked which was sort of proved by the xp box not being able to access them.  As soon as I re-checked and applied the share check boxes (again through Nautilus) all was well.

---

### Post by doas777 on 2009-10-13
> **PaulHeywood said:**
> Thanks for the thoughts - I'm probably not explaining the problem as well as I could:  

Yes, I'm logging back in to the Ub host, but I noticed that when I looked at the properties of the shared partition through Nautilus it had no sharing check boxes ticked which was sort of proved by the xp box not being able to access them.  As soon as I re-checked and applied the share check boxes (again through Nautilus) all was well.


after a reboot/login, run this in a terminal:
```
ps -ef | grep samba
```

what is the output? does it look like samba is running?

also do you use network-manager, or are you configuring your IP settings in your /etc/interfaces file?

---

### Post by PaulHeywood on 2009-10-13
Nope, no samba processes running - and once again when I go to places and take a look at my previously shared folders they haven't got the share notification against them, and as always if I right click on the folder (in Nautilus) I have to recheck the "Share this folder" check box.

---

### Post by PaulHeywood on 2009-10-13
A bit more searching discovered this :

[https://bugzilla.gnome.org/show_bug.cgi?id=577796](https://bugzilla.gnome.org/show_bug.cgi?id=577796)

looks like a bug, doesn't seem much activity on the bug, I'll turn to Swat and get the shares written to the conf file.

---

### Post by doas777 on 2009-10-13
well, the bug is not related because it regards mounting on the client, not sharing on the server.

do you use network-manager to configure your network access? if so, try configuring your /etc/interfaces file instead of using network-manager. if you need network-manager (for wifi or whatever) then just add the samba restart line above to System -> Preferences -> Startup applications.

---

