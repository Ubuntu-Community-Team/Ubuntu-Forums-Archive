---
title: "Mount ISO without root priveledges?"
date: 2009-04-29
forum: Multimedia Software
---

### Post by dbsoundman on 2009-04-29
I'm wondering if there's a way to perhaps write a script where a non-sudo-capable user (in my case, "guest") can mount an ISO image as a regular CD-ROM. I found some scripts on ubuntu geek which allow me to mount it with the click of a button, but I still have to be root in able to do it. I was hoping to have this functionality on my communal "media station" in the living room, where the regular user does not have root privileges (not that they would know what to do with them if they had them). Is there a way to do this?

Thanks,
Dan

---

### Post by FakeOutdoorsman on 2009-04-30
You can edit your suders file to give a user privilege to mount and umount without requiring a password.  First open the sudoers file using visudo:
```
sudo visudo
```
Now at the end of the file add the following (replace *proffrink* with your username):
```
proffrink   ALL=NOPASSWD:/sbin/mount,/sbin/umount
```

---

### Post by ed-koala on 2009-04-30
Install gmount, simple easy way to mount iso

---

### Post by dbsoundman on 2009-04-30
> **FakeOutdoorsman said:**
> You can edit your suders file to give a user privilege to mount and umount without requiring a password.  First open the sudoers file using visudo:
```
sudo visudo
```
Now at the end of the file add the following (replace *proffrink* with your username):
```
proffrink   ALL=NOPASSWD:/sbin/mount,/sbin/umount
```

Thanks, I tried this just now but it isn't working yet. I'm not using the regular mount and umount protocol though; I'm trying to use it using the nautilus script I downloaded and installed, so instead of pointing it to /sbin/mount, I pointed it to /home/guest/.gnome2/nautilus-scripts/mount.sh. Can I do this or is this not the way to go about it?

I may have to look into gmount as well...we'll see.

-Dan

---

