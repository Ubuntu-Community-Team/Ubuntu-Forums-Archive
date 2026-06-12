---
title: "Personal File Sharing problem"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by BillybobT on 2011-01-10
I recently built a new machine based on i3-550 processor, an upgrade from a Pentium-D; quite a performance difference!

I use personal file sharing to use files on this machine with other Linux boxes in the house, mostly videos. Everything was working fine before, but now I get the following error when I try to connect to the new machine:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I even get the same message when I attempt to connect from the host.

The only big(?) difference I can see between the old and new machines is that the i3 loaded the generic-pae kernel (I use 32-bit Ubuntu 10.10 on both boxes)

---

### Post by PatchesTheCaveman on 2011-01-11
What are you using for file sharing?  Samba?

What exactly do you do to trigger that error?  A screenshot might be helpful.

That's a very strange error to be receiving when attempting to access a file share.

---

### Post by Morbius1 on 2011-01-11
By personal file sharing I'm assuming you mean "gnome-user-share"?

You might want to make sure avahi is running on the host:
```
sudo service avahi-daemon status
```
If it's not running start it:
```
sudo service avahi-daemon start
```

[COLOR=Blue]**EDIT: Looks like a bug:**[/COLOR]
[https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/582542](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/582542)

---

### Post by BillybobT on 2011-01-11
> **Morbius1 said:**
> By personal file sharing I'm assuming you mean "gnome-user-share"?

You might want to make sure avahi is running on the host:
```
sudo service avahi-daemon status
```If it's not running start it:
```
sudo service avahi-daemon start
```[COLOR=Blue]**EDIT: Looks like a bug:**[/COLOR]
[https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/582542](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/582542)

Yes, it is gnome-user-share and the results of the command is:

```
avahi-daemon start/running, process 1209
```I looked at the bug and I will add my case, adding 10.10 to the list. I'm thinking the pae has nothing to do with it, but I'll include it.

---

