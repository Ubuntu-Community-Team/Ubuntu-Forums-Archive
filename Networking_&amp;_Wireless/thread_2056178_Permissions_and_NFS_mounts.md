---
title: "Permissions and NFS mounts"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by gellpak on 2012-09-10
I've created an NFS share on my ubuntu 12.04 machine and am now trying to properly set up permissions on it. I want to allow access to the share only to members of a specific group, in this case *cerberusaccess*

I got it working on the ubuntu machine by creating the group, adding the proper users to it, and then changing the group of the directory to *cerberusaccess* and setting its permissions to rwxrwx---, which (as I understand it) makes it read/writable by the owner and group members, but no one else.

Now I want to have the same privileges from my os x laptop, but I just get permission denied errors. I matched up the UIDs of my laptop account and the ubuntu account of the same name. I also created a group on os x with the same GID and name and added my mac user id to it. Still no luck.

According to OS X, I am connected to mediacenter as NFS (not the correct user), which is probably the problem. Any ideas for commands to change who I connect as? Currently I'm using this reference to connect to the share:

nfs://mediacenter/media/cerberus

I tried nfs://user@mediacenter/media/cerberus and it had no effect.

---

### Post by LewisTM on 2012-09-11
What does the export entry look like?
If it's the same as your previous thread, you'll need to remove the [FONT="Courier New"]all_squash[/FONT] option.

Cheers!

---

### Post by gellpak on 2012-09-11
It was, and that worked. Thanks!

---

