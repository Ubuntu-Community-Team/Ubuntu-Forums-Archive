---
title: "NFS necessary for SSH networking?"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2010-06-29
Hi all,

I am guessing I know the answer to my thread title but before I do anything best to check with the experts! ;)

I battled away with trying networking our three computers on the home network on and off for quite some time. I eventually settled with NFS through SSH. It worked! And is pretty secure. Not using remote networking although guess I could set that up easily enough.

The other night I realised just how easy it is! I should have done this first up. 
Places->Connect to Server. Set to SSH, put in the IP of the machine you want to connect to, and whap! You're there! I love it and now I can see all the other machines from any machine, if you know what I mean! Something that was a problem with NFS as everything seemed to revolve around having an NFS server. The server had to be on and that was not the set up I was after in the first place, one reason being we don't have a dedicated 'real' server so one of the local machines needed to be on, not ideal because even then, both machines can see the server but not each other. You could only see all three machines if you were working on the server.

So I set up permanent links to folders on each machine and now can go to 'Places' and there are links to the other two machines. Perfect and easy for other users. They don't need to enter or know IPs (my wife has no interest in that!), just a password. Add them as a user on the machines you want them to be able to access. Easy.

Question1 : Can I now remove all things NFS and the SSH networking will be fine?

I have hashed out the mount lines in fstab for mounting NFS shares at boot so not using NFS anyhow. I'm figuring this is fine to remove NFS but probably need to leave a couple of other things related; portmap, etc.

Question 2: Can anyone get specific about what should stay if I remove NFS?

Looking forward to your thoughts. :)

* PS: SSH works great. My studio box is Xubuntu with the Ubuntu Studio AV packages installed so doesn't have 'Connect to Server'. Easy. [Filezilla]("http://filezilla-project.org/") rules! I'd only every used it for working on the web server. Putty: don't like working in the terminal for that stuff. Easier to drag and drop.

---

### Post by iponeverything on 2010-06-29
nfs is not required for mounting a fs via ssh. 

removing nfs is not really necessary, it does not take up much space and it is quite easy to turn off the service.


To remove it just do:

```
dpkg -l |grep nfs
```

then use:

```
sudo dpkg -e <package name> 
```

to remove them..

you might also consider shutting down portmapper.

---

### Post by Bucky Ball on 2010-06-29
```
ii  libnfsidmap2                               0.20-0build1                                         An nfs idmapping library
ii  nfs-common                                 1:1.1.2-2ubuntu2.4                                   NFS support files common to client and serve
```... is the result from your first command.

Doesn't take up much space but NFS does start at boot. Don't want that, don't need NFS, so may as well remove it. I removed both the files I show above, restarted and all seems fine. Haven't attempted network with another machine yet but imagine that will be fine too. Cheers.

---

