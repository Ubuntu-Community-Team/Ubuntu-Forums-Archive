---
title: "Sharing files with Windows and LInux computers"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by jcd29 on 2010-09-04
Still pretty new to Ubuntu, so I apologize if my questions seem a little basic or obvious.

I know Samba is installed by default on Ubuntu 10.04. From what I understand, it'll allow you to share files between Linux and Windows (etc) users. Does it also allow you to share between Linux and Linux, or would that be NFS?

Whenever I right click a file, and enable sharing, is that enabling sharing through samba, or only for other Linux machines to see it?

I'm guessing right now under Network, Windows Network I can see two workgroups since those are the ones that are currently in my house. So basically Ubuntu/Samba sees all of them even if it doesn't have the same workgroup name? (It seems I can't access them, though).

I have a few other questions, but I'll have a better idea about them after knowing the answer to these.

---

### Post by sikander3786 on 2010-09-04
I think only Samba Client is installed by default not the Samba Server in Ubuntu.

Whenever you click a folder and enable sharing, the first time it will ask to install some packages, let it do so, then log out and then back again. Now try to share the folders. 

Alternatively you can install samba by

```

sudo apt-get update && sudo apt-get install samba

```

They will definitely be shared via Samba, the shortcut is called nautilus-share. Alternatively the folders can be shared  by listing them in

```

/etc/samba/smb.conf

```

But I will suggest you use nautilus-share, it is easier. Post any further queries.

EDIT: And Samba is capable of sharing files from Linux ---> Windows, Linux ---> Linux, Linux ---> Mac.

---

### Post by jcd29 on 2010-09-04
> **sikander3786 said:**
> I think only Samba Client is installed by default not the Samba Server in Ubuntu.

Whenever you click a folder and enable sharing, the first time it will ask to install some packages, let it do so, then log out and then back again. Now try to share the folders. 

Alternatively you can install samba by

```

sudo apt-get update && sudo apt-get install samba

```

They will definitely be shared via Samba, the shortcut is called nautilus-share. Alternatively the folders can be shared  by listing them in

```

/etc/samba/smb.conf

```

But I will suggest you use nautilus-share, it is easier. Post any further queries.

EDIT: And Samba is capable of sharing files from Linux ---> Windows, Linux ---> Linux, Linux ---> Mac.

Thanks, it was already installed after all.

Ok, so I did the following test:
I shared a folder called test in /home/username/Documents by right clicking it, choosing Sharing Options, and choosing "Share this folder" and "allow others to create and delete files in this folder".

Then I edited smb.conf, adding this
```
[test2test]
comment = test folder
path = /home/username/Documents/test2
public = yes
writeable = yes

```

So that's two different test folders, each with a different way of sharing.

I went to the XP machine, and checked that I could see both of them, test1 and test2test, under the Network. However, I could easily access test2test, but not test1. It asked for a username and password, for some reason.

---

### Post by sikander3786 on 2010-09-04
I think it is happening because you have set public = yes on test2test, and not allowed guest access to test1 in nautilus share. Tick the Allow guest access checkbox and check again.

---

### Post by jcd29 on 2010-09-05
> **sikander3786 said:**
> I think it is happening because you have set public = yes on test2test, and not allowed guest access to test1 in nautilus share. Tick the Allow guest access checkbox and check again.

Yup, worked! Thanks.

I'm still a little puzzled about sharing with Linux computers.

Say you were in a completely Linux environment. What would you use to share files between computers, and how would you set it up?

Samba with a common workgroup, or another thing?

---

### Post by sikander3786 on 2010-09-06
[NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") is an option.

[http://ubuntuforums.org/showthread.php?t=193408](http://ubuntuforums.org/showthread.php?t=193408)

There are some others out there still I use Samba for file sharing on my network which is a mix of Ubuntu and Windows XP + Windows 7 computers.

---

### Post by jcd29 on 2010-09-06
> **sikander3786 said:**
> [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") is an option.

[http://ubuntuforums.org/showthread.php?t=193408](http://ubuntuforums.org/showthread.php?t=193408)

There are some others out there still I use Samba for file sharing on my network which is a mix of Ubuntu and Windows XP + Windows 7 computers.

Just having both computers in the same workgroup in Samba would do the trick for sharing files in Linux to Linux right?

---

### Post by sikander3786 on 2010-09-07
> **jcd29 said:**
> Just having both computers in the same workgroup in Samba would do the trick for sharing files in Linux to Linux right?

Yes that does it for me. Have you tried it yet?

Followup, some people use NFS, others use to mount their Linux shares on another Linux machine in /etc/fstab. Many many options...

---

### Post by jcd29 on 2010-09-10
> **sikander3786 said:**
> Yes that does it for me. Have you tried it yet?

Followup, some people use NFS, others use to mount their Linux shares on another Linux machine in /etc/fstab. Many many options...

It works, I just can't access the laptop

Places, Network. Click on username-laptop, and I get this message:

Unable to mount location
Failed to retrieve share list from server

Of course I haven't shared any files there yet, could be that. I'm gonna go try it.

---

### Post by sikander3786 on 2010-09-11
Share a folder and then see if Ubuntu is able to mount the location.

---

### Post by jcd29 on 2010-09-15
That didn't work. It's weird, because I can see the laptop from my computer, I just can't mount it. But the laptop can't really see the desktop.

What I mean is, when I enter the Network under Places in the Desktop, I see the following:

- user-desktop (with a computer or rack icon. If I go inside I can see my shared files)
- user-laptop (with a computer or rack icon. Can't go inside)
- WORKGROUP (where if I go inside, I can see my shared files under user-desktop)

In the laptop I see:

- WORKGROUP and that's it. I can see the files shared in the desktop when I enter the workgroup folder, but I don't see the rack icons outside, and again I can't access the laptop's shared files with my desktop.

---

### Post by Iowan on 2010-09-15
I frequently have better luck with the "Connect to Server" option. :)

---

### Post by jcd29 on 2010-09-15
> **Iowan said:**
> I frequently have better luck with the "Connect to Server" option. :)

Which option would I choose though, since it's a Linux to Linux share? 

Even if it works, I'd prefer the simple way to still work of course.

Edit: OK that works, but still, I wanna fix the other way.

---

### Post by Iowan on 2010-09-15
I haven't tried NFS yet, so I'm connecting to my Samba server from this Ubuntu workstation. I think I have SSHFS set up - but generally just use Samba.

---

### Post by dmizer on 2010-09-16
There are many different ways of sharing files between computers on a local network. Each of them has both advantages and disadvantages, so which one you use would depend on your needs.

Samba is used almost universally so it's a good choice for mixed environments. There's really nothing wrong with using Samba when all the computers in the network are Linux either. As you've already discovered, Samba can be finicky and difficult to maintain. It also tends to cause a lot more unnecessary traffic on the LAN which could be a problem on larger networks. Since Samba is more widely used, it tends to be the focus of exploits as well.

NFS is good for Linux to Linux computers. It can also work with Macs. It uses very few system resources and offers extremely speedy file transfers. NFS can be made to work with Windows, but it's not easy and my experience with NFS on Windows has been less than satisfactory. NFS is designed for networks with a central file server and can cause some problems if you have many NFS servers which join and leave the network regularly. NFS security is handled at the Linux file system level, so you'll need to be familiar with Linux file permissions if you have a server on an untrusted network.

Many people don't realize that FTP also makes a perfectly good method for sharing files on a LAN. Just because it's generally thought of as a way of transferring files on the internet doesn't mean that it can't be used on a LAN. FTP is used universally, and I have never used an OS that does not support FTP either by default or through freely available software so it can be a good choice in some environments. However, FTP doesn't integrate into the XP Windows file system as well as it does in Linux.

SFTP is another option that offers a great deal of security by utilizing the encrypted SSH protocol. If you have an environment where security is an issue, this could be a good choice. There are clients freely available for Windows as well, but SFTP servers can be a pain to set up on Windows machines.

There are many other options as well. The point is, that you should simply use what works best for your environment, and something that is easy for you to maintain.

---

### Post by CharlesA on 2010-09-16
I've transfered files over SSH as well, which I think it called SSHFS (Connect to > SSH > Server, etc).

Works great.

---

### Post by dmizer on 2010-09-16
> **CharlesA said:**
> I've transfered files over SSH as well, which I think it called SSHFS (Connect to > SSH > Server, etc).

Works great.

It's actually referred to in a variety of ways. SFTP or SCP are the most common. SCP (secure copy) is the file transfer protocol packaged with SSH. I believe SSHFS is a fuse file system that uses SCP. I don't think that the Places > connect to server uses fuse to soft mount SFTP shares. The only time you would use SSHFS with fuse is if you want a hard mount in /etc/fstab.

---

### Post by jcd29 on 2010-09-18
**Update:**

I edited the following into my smb.conf 

```
netbios name = user-desktop
```

Right below the workgroup, and this

```
# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts host wins bcast
```

Without the ";" it had. This was following instructions from another guide I found.

Then I entered /etc/nsswitch.conf and edited:

```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

I added the "wins".

And installed winbind 

```
sudo apt-get install winbind
```

Now I can easily view files from my desktop to my laptop, and from my laptop to my desktop. I mean, I could see them before, I just couldn't browse them through the Network interface (I had to use Go, Location, smb://ipaddress before, but now I don't).

There's still two problems:

[LIST]
[*]I can't see my own files from my laptop. What I mean by this is the following: When I click on Network from my desktop, I see three things. One is the Windows Network folder, the other is user-desktop (with the rack icon) and the other is user-laptop (w/ rack icon). I can easily browse my own files here which is pretty comfortable. However from my laptop I only see the Windows Network folder, and user-desktop. I can't see user-laptop which is where my files would be grouped together. To be able to go there I have to click on Windows Network, then the workgroup, and THEN user-laptop and open one of the shared folders. And because of doing it this way, the folders get mounted whenever I click them, which is not what I want. I'd like to be able to browse my shared files easily like I do from my laptop. Any ideas?

[*]I have two drives in my desktop. I can share anything from my main HDD with the laptop, however I can't share anything, not a file or folder, from my data drive. It's automatically mounted by default in fstab so that's not the problem, however I get "Unable to mount Windows share" whenever I try to open one of those shared folders from my laptop. Why could this be?
[/LIST]

---

### Post by jcd29 on 2010-09-20
Solved the second problem. It was just a matter of setting the permissions :) I had them so only I could see that HDD.

Still can't figure out the first problem.

---

### Post by soldier1st on 2010-10-01
there is another possible way but you will need to decide if you want it or not. you could set up dropbox on the pc's that you want to share info with but of course you need an account.

---

