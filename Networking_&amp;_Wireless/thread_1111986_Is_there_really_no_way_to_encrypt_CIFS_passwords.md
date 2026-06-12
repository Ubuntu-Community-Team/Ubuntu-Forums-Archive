---
title: "Is there really no way to encrypt CIFS passwords?"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by lumix on 2009-03-31
I've searched extensively, and this seems to be the case.  Credential files don't seem to be an adequate solution, as they are still clear-text.  Booting from a CD, one can still open any Hex editor and read the .credentials file in clear text.

Someone mentioned that this is moot since the password is sent in clear-text anyway; I don't believe that's true, however.

Is there some other secure solution (perhaps not even CIFS based) that admins use?

---

### Post by albandy on 2009-03-31
it's a workstation or a server.?
If it's a workstation you can use pam_mount that will pass your login password to the share, it will be mounted only when you login the machine.

---

### Post by lumix on 2009-03-31
Hmm, what's the difference between the workstation and server implementation, so far as connecting to an smb share is concerned?  I haven't worked much with server distros, but my understanding was that they're very little more than, well, just less.  Is the CIFS client setup different between them?

At present, I'm 8.10 to 8.10 (desktop), but I really like to keep things simple so I avoid any gui-based setups and usually go straight to the config files.

How does using PAM conceal or obfuscate the password, either in storage or in transit?

Thanks for the reply.

---

### Post by albandy on 2009-04-01
No no, I want to know if you're using your computer as a server or as a workstation.
If you're using it as a workstation usually you don't need to mount remote filesystems before login.

So to set a pam_mount configuration to automount the remote filesystem when login.
pam security system don't save your password in any file, it's saved in RAM (but not accessible) so you can use the module pam_mount to read your password and mount the filesystem.

---

### Post by lumix on 2009-04-01
Again, I'm 8.10 to 8.10 (Desktop, not server edition).  I'm not sure if that's what you mean, though.  I have a share on one machine that I want to be automatically available at a certain place in the filesystem.

As for PAM, I'm clearly not too familiar, but definitely interested.  So how did the password get into RAM? I mean, I know I type it in at login (i.e. onto the local machine), but why would it be saved anywhere at all?  If I try to access an object, doesn't the kernel simply need to know that I am Bob, or Alice, or whoever, and whether I have any business accessing that object or not?  Or is there a separate process at login that asks what credentials I'll be using for PAM?

Thanks for the info, btw.

---

### Post by albandy on 2009-04-02
Explanation of what is PAM:
[http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules](http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules)

how to make pam automount your shared resources:
first install pam_mount:
sudo apt-get install libpam-mount
then edit the file /etc/security/pam_mount.conf.xml
add something like this:

<volume fstype="smbfs" server="myserver.mydomain.org" path="shared_folder" mountpoint="/mnt/%(USER)/myremotehome" options="dmask=0700" />

finally add this to the file /etc/pam.d/gdm 
@include common-pammount 
(it should be added after the line which contents @include common-session)



in the file /etc/pam.d/common-pammount you can define how pam_mount should work, by default works ok, but you can modify some restrictions as setting it to required to don't allow login if can't mount the share or optional if you want to login anyway.

---

