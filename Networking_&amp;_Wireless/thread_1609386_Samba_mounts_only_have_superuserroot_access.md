---
title: "Samba mounts only have superuser/root access"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by pig_destroyer on 2010-10-30
Hi one and all, 
Backstory: I've used ubuntu for a while now and feel myself reasonably competent with it. I have a samba share on another ubuntu box which was mounted as a removable drive via fstab, and was able to write things to it and so on and so forth using my normal account.
One day after running fslint to get rid of the copious number of duplicate files of stuff I'd amassed, the share for some reason was only accessible as a removable drive to root, who could write and read files with the same privileges I had, in that I couldn't view the files etc etc.

I can read the directory using the nautilus network interface, i.e with the shared folder not mounted as a drive, but not write anything. 

I have tried:
doing:
```

sudo chown -R raminder /media/music 
sudo chmod -R 777 /raminder/music

```various fiddles with fstab (including copying and modifying a line for another share I set up with none of these problems, modifying the entry where necessary (for directories and so on). All this makes me think it's a server-side thing, but where to start I don't know. I've set Chmod 777 for everything pertaining to the directory and drive but even that hasn't done anything. 

Attached for reference are my /etc/fstab, and the remote smb.conf file:
 Could anyone please shed some light on this problem?

Thanks very much for your help.
Regards,

---

### Post by luvshines on 2010-10-30
Noticed that you are using many parameters which should be share specific to the [global] section of smb.conf

Parameters like:
```

## Will force all connected users to given nobody perms
force user = nobody

## Guest account user is generally mapped to nobody. Mapping to root can be a potential security hole
guest account = root

## Although you are overwriting it in each share section
path = /home/

```

I would also recommend switching to default security mode:
```

security = user

```

---

### Post by pig_destroyer on 2010-10-30
Hi, thanks for reading- tried amending smb.conf as advised, still no progress...
I should also have mentioned, I tried mounting the drive on the server with full 777 permissions too?

---

### Post by pig_destroyer on 2010-11-13
bump. Sorry.

---

