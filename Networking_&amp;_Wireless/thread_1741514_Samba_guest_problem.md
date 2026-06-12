---
title: "Samba guest problem"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by new_tolinux on 2011-04-28
Hi,

I have a server (running 10.04 desktop) and a computer currently running 10.10.
On the server I have some shares (samba), which works great, on a Windows client at least.....

On my 10.10 pc, I can connect, but it says the files are owned by root, so read-only.
Any ideas how to solve that? 
I tried mounting them without sudo, but that also failed.
I also tried to chown the folders where they're mounted (inside ~), but that also failed.

---

### Post by Morbius1 on 2011-04-28
Please post the output of the following command:
```
testparm -s
```

---

### Post by new_tolinux on 2011-04-28
10.04 (samba server) :
```
*removed output*
```As said, from a windows PC it's writeable, only from my 10.10 workstation it's read-only because owned by root.

Therefore I guess there's probably something wrong with the mount-command itself instead of something wrong on the serverside.

```
sudo smbmount //myserver/www ~/Netwerk/www -o username=newtolinux
```

---

### Post by Morbius1 on 2011-04-28
If you're accessing this from an Ubuntu desktop why not use "Network" under Places?

Anyway, try this mount:
```
 sudo mount -t cifs -o username=newtolinux,password=some-password,uid=1000 //myserver/www ~/Netwerk/www
```
uid=1000 will make you ( not root ) the owner of the mounted share.

---

### Post by new_tolinux on 2011-04-28
> **Morbius1 said:**
> If you're accessing this from an Ubuntu desktop why not use "Network" under Places?

Anyway, try this mount:
```
 sudo mount -t cifs -o username=newtolinux,password=some-password,uid=1000 //myserver/www ~/Netwerk/www
```uid=1000 will make you ( not root ) the owner of the mounted share.
That did the job, thanks.

For security-reasons I also tried not specifying my password, which results in an password-prompt (without the typed password being displayed).

---

