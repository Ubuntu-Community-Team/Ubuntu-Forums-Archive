---
title: "connecting to Microsoft volumes"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by rjani1 on 2012-11-20
Hi,

I recently downloaded Ubuntu 12.10 from their website. I am in a Microsoft domain environment and would like to know how I can connect to the Microsoft volumes. 

Do I necessarily need to have my Ubuntu connected to the domain to have access to these? 

I know the gid,uid,server details and credentials to map my volumes but do not know how to do this on Ubuntu.

Any suggestions/ideas much appreciated.

rjani1

---

### Post by dannyboy79 on 2012-11-20
here's a gudie I found
[http://www.ghacks.net/2010/04/21/join-a-ubuntu-machine-to-a-windows-domain/](http://www.ghacks.net/2010/04/21/join-a-ubuntu-machine-to-a-windows-domain/)

---

### Post by apollothethird on 2012-11-20
> **rjani1 said:**
> Hi,

I recently downloaded Ubuntu 12.10 from their website. I am in a Microsoft domain environment and would like to know how I can connect to the Microsoft volumes. 

Do I necessarily need to have my Ubuntu connected to the domain to have access to these? 

I know the gid,uid,server details and credentials to map my volumes but do not know how to do this on Ubuntu.

Any suggestions/ideas much appreciated.

rjani1

First make a directory for the mounted volume.

```

$ sudo mkdir /mnt/microsoftshare

```

(Of course the directory and name is a matter of your choosing.)

Eneter the following command to mount (map) the volume:
```

$ sudo mount -o username=[user id] //server/volume /mnt/microsoftshare

```

You'll be prompted for the server password.
You should then be able to see the content of the volume with:

```

$ ls /mnt/microsoftshare

```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by rjani1 on 2012-11-20
> **apollothethird said:**
> First make a directory for the mounted volume.

```

$ sudo mkdir /mnt/microsoftshare

```

(Of course the directory and name is a matter of your choosing.)

Eneter the following command to mount (map) the volume:
```

$ sudo mount -o username=[user id] //server/volume /mnt/microsoftshare

```

You'll be prompted for the server password.
You should then be able to see the content of the volume with:

```

$ ls /mnt/microsoftshare

```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

Hi L.James,

Here is the message I got from the command line:

```
mount: wrong fs type, bad option, bad superblock on //volume_name/folder,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)

```

Looking at dmesg | tail shows me the following:

```
[41223.796259] FS-Cache: Netfs 'cifs' registered for caching
[41223.796610] Key type cifs.spnego registered
[41223.796644] Key type cifs.idmap registered
[41223.796813] CIFS: no cache= option specified, using "cache=loose". This default will change to "cache=strict" in 3.7.
[41223.807076] CIFS VFS: Connecting to DFS root not implemented yet
[41223.807196] CIFS VFS: cifs_mount failed w/return code = -22

```

---

### Post by apollothethird on 2012-11-20
Install the following then run the mount command:

```

$ sudo apt-get install samba cifs-utils

```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by dannyboy79 on 2012-11-20
you won't be able to do this until you're part of the domain. If it's a true windows active directory domain anyway.

if you didn't like the last link, here's another. [https://help.ubuntu.com/10.04/serverguide/samba-ad-integration.html](https://help.ubuntu.com/10.04/serverguide/samba-ad-integration.html)

---

### Post by rjani1 on 2012-11-20
> **apollothethird said:**
> Install the following then run the mount command:

```

$ sudo apt-get install samba cifs-utils

```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

Hi L James,

I have got the drives mounted but I cannot seem to write to them. I tried this and got the same
result:
```
mount -rw -o username= ...
```

Any suggestions?

rjani1

---

### Post by dannyboy79 on 2012-11-20
> **rjani1 said:**
> Hi L James,

I have got the drives mounted but I cannot seem to write to them. I tried this and got the same
result:
```
mount -rw -o username= ...
```

Any suggestions?

rjani1I have already explained why you can't write to them, are you not reading my responses? WOW........

---

### Post by apollothethird on 2012-11-20
> **rjani1 said:**
> Hi L James,

I have got the drives mounted but I cannot seem to write to them. I tried this and got the same
result:
```
mount -rw -o username= ...
```

Any suggestions?

rjani1

You can use the option to specific group and user id for the files in the mount command.  Unmount the volume and use something similar to this:

```

$ sudo mount -o username=[user id],uid=[uid] //server/volume /mnt/microsoftshare

```

You can also specify group id with "gid=[gid]" if you need it.

There are also modes that you can specific for creating files and directories (ie.file=mode=0660,dir_mode=0775).  The latter is kind of technical and might not be needed for simple directory access.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2012-11-20
> **dannyboy79 said:**
> I have already explained why you can't write to them, are you not reading my responses? WOW........

Hi, Dannyboy.  I can't decipher the answer from the links you provided.  I'm pretty experienced.  The user is very novice.  If I can't, I can imagine how cryptic it appears to him.

I don't believe he'll have problems with the simple commandlines I provided.  If you have some better commandlines, I'd appreciate seeing them.  I'm always glad to learn.

Again, I don't think he's ignoring you... and I'm sure he sees your message.  But the examples I provided is easy for him to test and I'm sure they will suffice for his needs.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by dannyboy79 on 2012-11-20
ok, well first we need to learn whether he trying to authenticate against a TRUE ACTIVE DIRECTORY DOMAIN or just a windows workgroup.

---

### Post by apollothethird on 2012-11-20
> **dannyboy79 said:**
> if it's a true active directory domain he won't be able to simply mount the share and write to it. He has to add his ubuntu machine to the DOMAIN as per the links I provided.

I don't recall him specifying a "true active directory".  He just wants to mount a windows share.

He has already mounted the share.  It was mounded under root.  He could use "sudo" to write to the share, or he can mount it as a different user.  Once he mounts it as a different user, he shouldn't have any problems reading and writing to the share by that user.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by dannyboy79 on 2012-11-20
read the first thread, it states, "I am in a Microsoft **domain** environment"

---

### Post by apollothethird on 2012-11-20
> **dannyboy79 said:**
> read the first thread, it states, "I am in a Microsoft **domain** environment"

Hi, Dannyboy.  I work with windows domains often.  The commands I gave him works flawless.

I hope the user will come back after typing the commands and mark this topic as solved.

I'm sure the system administrator who gave him the userID has given him access to the shares.  If he has problems with the commands I gave him, the next step would be to have the Windows System's administrator give him access.  The commands I gave him will suffice on this end as they already have for the mounting.

The only way you can tell, since many users don't come back unless they experience problems, is that the commands resolved the OP's issue.  That's why he isn't gack.

Again, hopefully he'll mark the thread solved so that others can benefit, who has similar questions.

Personally, I really appreciate your contributions.  I'm sure the OP does to, but as I mentioned, he probably didn't fully understand what you were providing... as it was a little deeper than what he needed.

Both he and I would have stayed on your track if the other simple steps didn't work.  I would have been very interested in how to resolve the issue.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by rjani1 on 2012-11-20
Hi DannyBoy,

     I am not ignoring you. I have seen both of the links that you provided and I really appreciate your input.

However, L James responded soon after and since his solution did not require joining my Ubuntu to the domain I was more inclined to follow it first. This is partly because one of my colleagues at work told me that joining to the domain was not necessary to mount the shares. This is why in my first thread I asked this question.

When I was working with Ubuntu 10 sometime back, I had used Centrify Express to join my client to the domain. But I have been told that Centrify no longer provides an updated client for the later versions. This is a shame since we use Centrify to connect our macs to AD.

I am in a Active Directory Domain environment and my shares are based on a Microsoft cluster. I do have full rights to the shares that I want to connect to and know my relevant uid and gid information.

I am not at work at the moment but will let you know how I get on tomorrow. I hope this clears up any misunderstandings.

Regards,

rjani1

---

### Post by rjani1 on 2012-11-21
Hi 

Just to let you know that I have resolved the issue by creating a local account with the same hid/gid combination and mount under this resolved the issue.

Many thanks for all your help.

rjani1

---

### Post by apollothethird on 2012-11-21
> **rjani1 said:**
> Hi 

Just to let you know that I have resolved the issue by creating a local account with the same hid/gid combination and mount under this resolved the issue.

Many thanks for all your help.

rjani1

You didn't have to create a userID for that purpose.  All was necessary was to use the proper combination of "uid=" and "cid=" for the access.  The resolution is easy if you decide to access another server.  You won't have to create 10 different users for access to 10 different servers.

I'm glad you have your immediate issue resolved.

Also, thanks for marking the thread solved.  I check my subscribed threads frequently to add new information when the topic is not solved.  I can let this one go unless you develop problems down the road and can use more assistance.

Have a nice Turkey Day!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by ramancentrify on 2012-11-21
Hi , In Ref to Centrify not providing updates to the express version I would like to say that we do update our Express version to support new platforms. With the current release of Centrify Express we do support version 11.04, 11.10 and 12.04 for Ubuntu. For a complete list please review the link - [http://www.centrify.com/express/centrify-express-supported-platforms.asp](http://www.centrify.com/express/centrify-express-supported-platforms.asp)
thanks
Raman

---

