---
title: "Wireless Linux to Windows Sharing"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by AeroCross on 2009-09-07
Hello everyone. I'm having some issues with sharing folders "the other way around" (usually, is having a shared windows folder and view it in linux, as a workgroup - no problems there).

I have a Linksys WRT54G2 Wireless Router set up like this:

Modem -> Router (Connected to 1 Bold, 1 iPhone, and 2 Laptops, perfectly) -> Desktop (XP)

I have, on my Desktop, a Shared Folder "Files", on the Workgroup "WG", I can see it from my Ubuntu 9.04 Laptop - everything works fine.

I wanna share my home folder with the WG Workgroup - I can't do that. I installed SAMBA and shared the folder in properties, but it does nothing.

What am I missing here?

---

### Post by sloppyc on 2009-09-07
Did you remember to run smbpasswd to create the user accounts for the samba server?

```
sudo smbpasswd -a *username*
```

Also, it's probably easiest to share the home directories by editing the smb.conf file manually:
```
sudo nano /etc/samba/smb.conf
```
...Ctrl+V down until you see "[homes]"...uncomment the relevant lines in that section (should be fairly straightforward when you read the comments that precede each line), restart Samba:
```
/etc/init.d/samba restart
```
...and you're all set.

---

### Post by AeroCross on 2009-09-08
Well, I must say "you're the man" -says it-

Yet, there's another "problem" - OK, now my home directory is shared. But there's a "homes" and an "aerocross" folder, both pointing the same way (my home directory), so what can I do to eliminate that duplication?

Also, what if I want to share another, not home, folder?
And last, but not least, how can I edit my network details? Such as computer name, current workgroup, etc. The current computer name is "laptop" and I want to change it.

Sorry for my n00bness, but hey, I guess we're all here to learn =)

UPDATE: The "dupes" was setting the "browseable" option to yes. When set to "no", it only shows the name of the user, and his respective home folder. I still don't understand SAMBA, but I'm getting the hang of it. If there's a GUI for setting up SAMBA, please share.

---

### Post by sloppyc on 2009-09-08
All here to learn indeed, so no worries at all.

As for sharing other folders, I'd really suggest [reading up on the smb.conf file]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  I'm by no means an expert with Linux, but it helped me quite a bit.

Basically, at the end of your smb.conf file, you'll declarea  new share by typing "[newsharename]" just like you currently have "[homes]."  Then, below that, you'll add "path=/path/to/shared/dir" followed by permissions (ie. valid users, create mask, directory mask, writable, etc.)all on their own lines.

EG.
```

[newshare]
comment = new share
path = /path/to/share
valid users = you, someone, else
writable = yes
...etc.

```

As for that duplicate "aerocross" folder... is that possibly left over from when you tried to share a folder via the GUI somewhere?  Look for "[aerocross]" in your smb.conf file to make sure you're not sharing it twice; I don't know what effect conflicting permissions for the same share might have.

Near the top of your smb.conf file you can find your workgroup name.  Edit that and it's changed.

Note that you'll have to restart Samba (or just reboot) whenever you make changes.

To edit the hostname:
[http://ubuntuforums.org/showthread.php?t=31852](http://ubuntuforums.org/showthread.php?t=31852)

---

### Post by AeroCross on 2009-09-08
That's what I wasn't totally getting - but now I understand. I'll try creating other shares.

Thanks a lot for all the replies, you were really helpful!

---

