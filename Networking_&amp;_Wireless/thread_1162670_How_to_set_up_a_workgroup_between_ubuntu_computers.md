---
title: "How to set up a workgroup between ubuntu computers"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by DakabinSHS on 2009-05-17
We are trying to create a work group but we dont know how.
 P.S. No Samba
 
second problem: If we connect using a basic ethernet connection we cannot view the other computers connected to the he network + they both use ubuntu no samba or internet
 
all help is greatly appreciated though

---

### Post by dmizer on 2009-05-17
Try NFS instead of samba. Take a look at the 4th link in my sig for a good howto on that.

---

### Post by Iowan on 2009-05-18
To do file sharing (of almost any kind) will require setting up a server on one/both partners.  Ubuntu generally includes the client portion, but the server part must be installed.

---

### Post by DakabinSHS on 2009-05-19
We have been going through NFS Sever/Client How To and have run into some problems. When we typed sudo vi/etc/export it came up with

*# /etc/exports: the access control list for filesystems which may be exported*
[I]#                      to NFS clients. See exports (5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes             hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4                  gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes      gss/krb5i(rw,sync)

[/I]Is this what we should and can we use you example add to the etc/exports?

Sorry if this sounds like a stupid question but we are knew to ubuntu and unsure if this is right.

---

### Post by dmizer on 2009-05-20
I suggest avoiding vi until you're familiar with how it works. Do take the time to learn it, but until then, a more simplistic text editor is probably better for you. Try this instead:
```
sudo nano /etc/exports
```

Just add your export lines below the commented fields you quoted above. Here's my example /etc/exports (lines I added are marked in red):
```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

[COLOR="Red"]/media/backup           192.168.24.0/24(rw,no_root_squash,async,no_subtree_check)
/home/dmizer/shared     192.168.24.0/24(rw,no_root_squash,async,no_subtree_check)
/home/dmizer/Movies     192.168.24.0/24(rw,no_root_squash,async,no_subtree_check)[/COLOR]
```

---

### Post by DakabinSHS on 2009-05-20
We have run into another problem. we used the sudo nano /etc/exports and added your lines except changing the ip address to 124.254.8.193 and changing the username to deathkarr and saved it. Then we said sudo /etc/init.d/nfs-kernel-server restart and it came up with the following
 
*Stopping NFS kernel daemon                                                       (ok)
*Unexporting directories for NFS kernel daemon                             (ok)
exportfs: Warning: /home/deathkarr/shared does not exist
exportfs: Warning: /home/deathkarr/Movies does not exist
exportfs: Warning: /media/backup does not exist
 
How do we fix this problem
 
Any and all help will be appreciated.

---

### Post by lisati on 2009-05-20
> **DakabinSHS said:**
> We have run into another problem. we used the sudo nano etc/exsports and added your lines except changing the ip address to 124.254.8.193 and changing the username to deathkarr and saved it. Then we said sudo /etc/init.d/nfs-kernel-server restart and it came up with the following
 
*Stopping NFS kernel daemon                                                       (ok)
*Unexporting directories for NFS kernel daemon                             (ok)
exportfs: Warning: /home/deathkarr/shared does not exist
exportfs: Warning: /home/deathkarr/Movies does not exist
exportfs: Warnign: /media/bckup does not exist
 
How do we fix this problem
 
Any and all help will be appreciated.
You probably need to adapt the folder names to the names on your system that you want to share *that actually exist*. And don't forget that *nix is more "case aware" than Windows - "shared" is often treated differently to "Shared"

---

### Post by dmizer on 2009-05-20
This is one line in my /etc/exports:
```
/media/backup           192.168.24.0/24(rw,no_root_squash,async,no_subtree_check)
```
This: [COLOR="Red"]/media/backup[/COLOR] 
is the location of the files you want to share

This: [COLOR="Red"]192.168.24.0/24[/COLOR]
Is the IP address range of the computers allowed to access the share

These: [COLOR="Red"](rw,no_root_squash,async,no_subtree_check)[/COLOR]
are the options, see: man exports for more information about the options.

A final note:
> **DakabinSHS said:**
> sudo nano etc/exsports
While I realize that this is not ACTUALLY what you typed for your command, it's a good idea to get in the habit of including leading "/" in directory path names like so:
```
sudo nano [COLOR="Magenta"]/[/COLOR]etc/exports
```
For example, if your prompt looks like this:
dmizer@shinkansen:~$
and you type sudo nano etc/exports, you will actually be editing: /home/dmizer/etc/exports instead of /etc/exports.

---

### Post by lisati on 2009-05-20
> **DakabinSHS said:**
> sudo nano etc/ex*s*ports 

I spotted this earlier but didn't comment earlier (I put it down to a typo in the post). Shouldn't be something like this: ```
sudo nano /etc/exports
``` (without the extra "s" but with the leading "/" suggested by dmizer)????

---

### Post by dmizer on 2009-05-21
> **lisati said:**
> I spotted this earlier but didn't comment earlier (I put it down to a typo in the post).

I thought it might have been a typo as well until I saw it every time /etc/exports was mentioned. Not sure exactly why the leading "/" is left off, but DakabinSHS appears to have edited the correct file. Otherwise, these errors would not have happened:
```
*Stopping NFS kernel daemon (ok)
*Unexporting directories for NFS kernel daemon (ok)
exportfs: Warning: /home/deathkarr/shared does not exist
exportfs: Warning: /home/deathkarr/Movies does not exist
exportfs: Warnign: /media/bckup does not exist
```
I thought it was something important enough to point out though.

---

### Post by DakabinSHS on 2009-05-21
Sorry For the typos guys. We now have a problem with manually mounting on the client machine in the terminal. The problem is as follows
 
*[COLOR=black]administrator@ubuntu:~$[/COLOR][COLOR=black] cd /[/COLOR]*
*[COLOR=black]administrator@ubuntu:/$[/COLOR][COLOR=black] sudo mkdir files[/COLOR]*
*[COLOR=black]mkdir: cannot create directory 'file': File exists[/COLOR]*
*[COLOR=black]administrator@ubuntu:/$[/COLOR]*
 
Any and all help is appreciated.

---

### Post by dmizer on 2009-05-25
> **DakabinSHS said:**
> 
*[COLOR=black]mkdir: cannot create directory 'file': File exists[/COLOR]*

This is telling you that /file already exists. I HIGHLY suggest that you mount your shares in a more common directory like:
/tmp/files
/media/files
/home/you/files

You can view the contents of a file system with the following command:
```
ls
```
So, if you cd into / and perform an ls, you should be able to see that /file exists.

As has been mentioned before, the tutorial is only giving examples. You should modify your mount points (in this case /files) to suit your own needs. That's the same reason you couldn't use the 192.168.24.0/24 IP range in the example I provided.

If you're still having problems, please post the contents of your exports file.

---

### Post by DakabinSHS on 2009-06-02
Thanks for your help. Your forum said that we need the server container the nfs share. How do we find out what the name of the server containing the NFS share is?
 
 Any and all help will be greatly appreciated.

---

