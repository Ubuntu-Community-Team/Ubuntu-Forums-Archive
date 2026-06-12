---
title: "Mounting an NFS with read/write access"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by almikul on 2012-04-24
Hi Ubuntu experts,

I hope you can help me figure out how to mount a network location to have full access to the files. When I login to my work server and type 'df .', I get this:
```
Filesystem              1K-blocks     Used  Available Use% Mounted on
host:/directory        2108016352 42982560 2065033792   3% /mount_directory
```

When I type 'df -T', here is the relevant part:
```
host:/directory          nfs    2108016384    42982528 2065033856   3% /mount_directory
```

I can mount this location on my laptop by typing:
```
sudo mount -t nfs host:/directory /mnt/directory
```

It mounts, and I can see the files, but I have no writing privileges because the owner of these files is shown as 18303 (I guess it is a userid?). On the network, my user name is the same as on my laptop. 

Here is my question: how do I login to my network location, so that I have full access to all my files? What options do I have to use with mount.nfs to be able to do that? 

Your input would be greatly appreciated.

---

### Post by drdos2006 on 2012-04-24
Check your server file, /etc/exports
It should read something like this.

```

/media/shared-directory		192.168.0.0/24(rw,fsid=0,sync,crossmnt,no_subtree_check)
/media/www-directory		192.168.0.0/24(ro,fsid=1,sync,crossmnt,no_subtree_check)

```


/media/shared-directory is the shared directory,  192.168.0.0/24 is the network and sub-addresses able to connect to the shared-directory.
rw is for read and write, fsid=0 because the shared directory is the first in the list of shared directories.

The network and sub-address can also be in the format of 192.168.0.0/255.255.255.0 but if you only want 1 workstation to access the shared directory then you can nominate that single IP address such as 192.168.0.2/24.

regards

---

### Post by almikul on 2012-04-24
I did some quick research and realised that I do not have full access because of the mismatch between my local uid and gid and those on the network. Just to test this hypothesis, I created a new user on my laptop with the same uid and gid as those on the network, and indeed this new user had full access to the files (seems like a possible security breach, does it not?) 

Now, one option would be to permanently assign new uid and gid to my main username and usergroup, but then I would have to change the ownership of all my files and my folders, and I don't feel my Linux knowledge permits to embark on such a mission. 

Another method would be to login to a new user account and access the network drive from there, but it does not seem right because I need to do all my work from my main account. 

Is it possible to mount a network drive with specific uid and gid (mapping different usernames to different user IDs)? Windows allows such mapping, so I believe Linux should have the same capabilities? I hope I am not being too cumbersome ;)

---

### Post by almikul on 2012-04-24
> **drdos2006 said:**
> Check your server file, /etc/exports
I checked it, and the file was empty.

---

### Post by _sebastian_ on 2012-06-11
Hi there,

I've got similar problems though I've decided that I would edit my UID and GID on the NAS to match my main Ubuntu user´s, see [here]("http://ubuntuforums.org/showthread.php?p=12016883#post12016883").

My problem is that I'm not sure if the NAS handles it without problems or if what I intend to do is correct.

Cheers seb

---

### Post by almikul on 2012-07-11
> **_sebastian_ said:**
> I've got similar problems though I've decided that I would edit my UID and GID on the NAS to match my main Ubuntu user´s, see [here]("http://ubuntuforums.org/showthread.php?p=12016883#post12016883").
I would rather do it this way too, but I have no administrative privileges on the remote work server what-so-ever. So, I ended up changing uid and gid locally in Ubuntu to match those on the remote server. This was not very complicated anyway. 

> My problem is that I'm not sure if the NAS handles it without problems or if what I intend to do is correct.
I am sorry, I cannot help you on this one.

---

### Post by Merrattic on 2012-07-11
> **almikul said:**
> I checked it, and the file was empty.

Was that on the server or on your client? (I think you checked the latter)

The important /etc/exports file is located on the server. it needs to be exporting to your IP address range and also to have "rw" (read/write) as one of the options.

As you indicate you do not have admin access to the server, you are stuck, unless you match the UIDs for the user

---

### Post by almikul on 2012-07-11
> **Merrattic said:**
> Was that on the server or on your client? (I think you checked the latter)
Yes, you are right - I checked on my local machine. Well, it was silly... had to know better. 

I checked the server-side /etc/exports, and the relevant line reads something like:
```
/vol/DIR1/DIR2      -sec=sys,rw,root=nasadmin:fsmon1:fsmon2
```
My home directory is located in /vol/DIR1/DIR2/ . So, what does it mean in terms of access exactly? I have no way of changing the content of this file, just asking out of curiosity.

---

