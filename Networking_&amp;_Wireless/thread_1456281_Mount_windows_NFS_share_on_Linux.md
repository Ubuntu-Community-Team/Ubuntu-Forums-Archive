---
title: "Mount windows NFS share on Linux"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by dE_logics on 2010-04-16
I'm using Unix services for windows on a windows system and shared a few folders using it; now how can I mount it on Linux?

There's no way you can search for this question online. These search terms - 

"mount windows NFS share linux"

Also mean - 

"mount linux NFS share windows"

and - 

"mount share windows linux NFS"

Which actually means NFS 4 which supports SMB protocol.

So actually it's IMPOSSIBLE to search for this and so this will be a good sticky.

---

### Post by dE_logics on 2010-04-17
Bump.

---

### Post by dE_logics on 2010-04-18
Bump

---

### Post by dE_logics on 2010-04-18
This forum has turned into complete crap...

---

### Post by Roasted on 2010-04-19
> **dE_logics said:**
> This forum has turned into complete crap...

Why is that? Because the users that happened to look at your thread didn't know an answer? 

If I had an answer, I'd gladly help you out. But I do not know enough about your issue to begin to help.

To correct your statement, the forums are not complete crap, but the users whom have read this thread simply do not know the answer.

---

### Post by dE_logics on 2010-04-19
> **Roasted said:**
> Why is that? Because the users that happened to look at your thread didn't know an answer? 

If I had an answer, I'd gladly help you out. But I do not know enough about your issue to begin to help.

To correct your statement, the forums are not complete crap, but the users whom have read this thread simply do not know the answer.

This place has turned to a complete newbie havoc. It's only suited for new users now! We need to split the forums to diverge traffic. Until then, I think I'll try linuxforums.

---

### Post by Roasted on 2010-04-19
> **dE_logics said:**
> This place has turned to a complete newbie havoc. It's only suited for new users now! We need to split the forums to diverge traffic. Until then, I think I'll try linuxforums.

Have at it. Ironically, I'm able to get a ton of help in regard to core functions that I utilize Linux for... things beyond the realm of newbie usage. Didn't mean to take a stab at your comment about it being newbie havoc, but that's not the reality of it.

---

### Post by dE_logics on 2010-04-19
Ok ok...my fault. It was an easy question and this thing has been utilized by many, but I'm not getting the answers.

I posted here cause this is a windows-linux enviourment, so I expect people to know a bit of both.

---

### Post by dwarfolo on 2010-04-19
The correct syntax would be

```
mount -t nfs xxx.xxx.xxx.xxx:/sfu_sharename /mount/point
```
where xxx.xxx.xxx.xxx is the IP address of the Win box.

Inside Win you should share the directory as follow

```
nfsshare sfu_sharename=x:\path\to\your\share -o anon=yes anonuid=0 anongid=0 rw=yyy.yyy.yyy.yyy
```
being yyy.yyy.yyy.yyy the IP address of your Linux box.

It's been a while since I have used SFU under Windows last time, and I cannot recall more details on the matter than the above commands, but if memory serves you should also manage to configure the Username Mapping Service on the windows side, otherwise you'll be stuck on authentication issues, even if you're using anonymous acces.

[http://support.microsoft.com/kb/324073/EN-US/](http://support.microsoft.com/kb/324073/EN-US/)

---

### Post by dE_logics on 2010-04-20
My main question here is what is this sfu_sharename? Suppose I've shared D:\music, then will it be D:\music?

This is weird cause Unix doesn't know what's a drive.

Actually I did try this but it didn't work. So are you sure that this is the right format?

---

### Post by dwarfolo on 2010-04-20
> **dE_logics said:**
> My main question here is what is this sfu_sharename? Suppose I've shared D:\music, then will it be D:\music?

This is weird cause Unix doesn't know what's a drive.

Actually I did try this but it didn't work. So are you sure that this is the right format?

sfu_sharename is the name you have used to create the share itself.
It can be any name you like.

```
nfsshare music=d:\music -o anon=yes ....
```

```
mount -t nfs ipaddress:/music /mount/point
```

I'm quite confident that this is the correct syntax. Anyway if I recall correctly this may fail to work.
I recall to have got many troubles setting up permission and anonimous access, because windows and UNIX don't use the same naming for users. I bet you'll end up having to set up Username Mapping Service on the Windows side.
Sorry ... it's been a very long time since I've used SFU last time and as you said there's not much documentation around.

---

### Post by dE_logics on 2010-04-21
Thanks, I'm trying it out.

---

### Post by dE_logics on 2010-04-22
Absolutely no use - 

```
mount -t nfs 192.168.1.2:/temp /media/ubuntu/
mount.nfs: mount system call failed
```

---

### Post by dE_logics on 2010-04-22
Ah... this is ****ing ****!! First the tons of blue screens, and then the broken implementation of NFS by MS. To top that off you gotta reboot after every god damn change!

windows is already polluted...now they're gonna pollute NFS too!

---

### Post by dwarfolo on 2010-04-22
> **dE_logics said:**
> Ah... this is ****ing ****!! First the tons of blue screens, and then the broken implementation of NFS by MS. To top that off you gotta reboot after every god damn change!

windows is already polluted...now they're gonna pollute NFS too!

Well, I'm not much surprised. 
I think that, unless you're absolutely forced to use NFS, you had better to quit wasting time with SFU. There's always Samba if you can use it. At least now you know in advance that Linux is much better at doing M$ things than M$ at doing the opposite. :P

---

### Post by dE_logics on 2010-04-22
I failed to configure SAMBA...that's why I was using SFU.

---

