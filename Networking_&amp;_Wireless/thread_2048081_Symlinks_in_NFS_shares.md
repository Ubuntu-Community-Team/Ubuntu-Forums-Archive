---
title: "Symlinks in NFS shares?"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by Bazon on 2012-08-26
Hello!

I'd like to have an easy and flexible NFS-share system that keeps me from editing /etc/exports and /etc/fstab every time I add or remove a shared folder. For that, I tried to set up one central shared folder (which works) In which I add symlinks to the folders I actually want to share. That doesn't work. On the other device, these symlinks are only showed as broken symlinks.

So is there another way to achieve my initial goal?

---

### Post by SeijiSensei on 2012-08-26
Is there some reason you cannot simply group all the new folders under the exported share?  Wouldn't that be easier to manage than a system where the folders are scattered across the remote filesystem?

You can use symlinks if the remote filesystem has the same structure as the mounted export.  For instance, if you export /home, and mount it as /home locally, then symlinks within the remote's /home will map correctly on the local machine.  

As you observe, though, symlinks to locations outside the exported directory will not work.  That's as it should be to preserve the security of the remote server.  You wouldn't want a user on the client machine to be able to create a symlink to some random location on the remote server and potentially wreak havoc if the permissions are not limited correctly.

---

### Post by tidewatcher on 2012-10-23
No, it is not easier. In my case, some of the content I am exporting is on mounted filesystems.

It worked fine until recently. After an update on the client (Ubuntu 12.04.1 LTS), the exported symlinks are interpreted as local. Nothing has changed on the server since the last time I saw it work

---

### Post by LewisTM on 2012-10-24
NFSv4 allows for the creation of an exported virtual filesystem that is populated by bind mounts, which act like directory symlinks.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2059482") and this [HOWTO]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

Briefly, you have to :
1) Create bind mounts on your virtual filesystem and specify them in fstab
2) Export the root filesystem, (e.g. /export) with parameter **fsid=0**
3) Explicitly export those mounts and any child bind mount with parameter **nohide**. That is the security measure: the user still cannot create symlinks that point elsewhere in the server. Instead, the server has bind mounts that have to be individually exported.

Cheers!

---

