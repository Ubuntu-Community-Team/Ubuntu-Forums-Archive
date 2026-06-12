---
title: "connect to nfs as a specific uid"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by gamblor01 on 2010-08-02
Is it possible to connect to an NFS share and have all files created there belong to a specific uid/gid?  For example, I have the following in /etc/exports:

```

/termite 10.48.204.251(rw,no_root_squash)

```And from my client machine I put this into the /etc/fstab directory:

```

10.48.204.168:/termite    /term    nfs    auto,rw    0    0

```This allows me to mount the directory from my client machine and then write files to the directory using sudo.  However, I am unable to write files as my default user id (named: pip).

I tried adding the "all_squash" and "anonuid" options in /etc/exports and then the "user" option in /etc/fstab:

```

/termite 10.48.204.251(rw,all_squash,anonuid=1000)

```

```

10.48.204.168:/termite    /term    nfs    user,auto,rw    0    0

```

but I couldn't get it to work (note that the uid value for pip on both machines is identical -- 1000).  The directory mounts just fine as pip (without the need for sudo) but I get a permission denied error when I attempt to touch/write a file in the mounted directory.

Is there a way to get this to work?  I just want to be able to have my default user id on the client machine write files to the mounted directory without needing the sudo command.

Cheers!

---

