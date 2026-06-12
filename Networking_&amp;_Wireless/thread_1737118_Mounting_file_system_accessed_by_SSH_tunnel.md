---
title: "Mounting file system accessed by SSH tunnel"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by shefaet on 2011-04-23
Hi there!

I'm a new user, and I've thoroughly enjoyed finding my way around Linux. This is my first time posting; I usually find the answers I need by Googling, but this time nothing I found worked -- so I turn to you fine folks.

I really like being able to mount remote file systems using the Places > Connect to Server ... tool on Ubuntu 10.10 -- it makes transferring files a breeze.

Unfortunately, the only way to access a particular server at work (call it Server A), is by first SSHing into an intermediate (Server B), which is the only one with a public ip.

My process for transferring files from Server A is currently:

myComputer $ ssh serverB
serverB $ ssh serverA
serverA $ scp file to serverB; exit
serverB $ scp file to myComputer

Needless to say, this gets tiring, and multiple transfers are slow.

Is there a way to mount serverA directly on my computer (by tunnelling through serverB in the background)? Failing that, how about using sftp?

Hope my question was clear. Thanks!

---

### Post by Joe of loath on 2011-04-23
Try sshfs. It's pretty simple to set up.

---

### Post by varunendra on 2011-04-23
> **Joe of loath said:**
> Try sshfs. It's pretty simple to set up.

or perhaps NFS :
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

But frankly, by description sshfs seems to be easier and more useful for you. I suggested NFS as an alternative only because I read in some post that NFS was somehow providing the best transfer speeds to the concerned user.

---

