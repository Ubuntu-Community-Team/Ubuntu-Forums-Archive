---
title: "Best way to share folders between two Linux computers."
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by glore2002 on 2009-09-22
I have two linux computers (one is running ubuntu 9.04 and the other Debian Lenny and Slackware64).

I would like to share a folder between these computers. 

What's the best way to do this and What are the steps I should follow? What should I install on both computers?

Thank you!

---

### Post by Iowan on 2009-09-22
NFS is native to Linux, but SSH(FS) is another option. 
[Here]("http://ubuntuforums.org/showthread.php?t=249889") is a How-To for NFS, and for [SSH]("https://help.ubuntu.com/community/SSH") and [SSHFS]("https://help.ubuntu.com/community/SSHFS"). 
[FTP]("http://ubuntuforums.org/showthread.php?t=79588") is still an option.

---

### Post by badger_fruit on 2009-09-22
samba or ssh

install on both computers

as for how, Mr Google will advise for the other distros and a forum search here will show for Ubuntu :)

---

### Post by i.r.id10t on 2009-09-22
ssh server (openssh-server) and then use eihter the "places" menu to connect or use sshfs

---

### Post by bogdan.veringioiu on 2009-09-22
You already have ssh installed (most probably).

Open nautilus, ctrl+l, then type
ssh://user@debian_machine
and voila, you have a file browser on the remote machine.
:)
Bogdan

---

### Post by glore2002 on 2009-09-23
> **bogdan.veringioiu said:**
> You already have ssh installed (most probably).

Open nautilus, ctrl+l, then type
ssh://user@debian_machine
and voila, you have a file browser on the remote machine.
:)
Bogdan

Thanks for your help my friends!

#1 Where do I get user and debian_machine info in Ubuntu?
#2 How can I access the folder without user and password?
#3 Does this work on any Linux computer (Slackware, for instance)?

---

### Post by bogdan.veringioiu on 2009-09-23
Hi.
:)
1)-debian_machine is the hostname of your Debian server (the one that you try to access).
You can use also the ip address.
-user is the username you use to login on that machine...
2)if you set ssh key authentication, probably the access it will work without passwords.

[http://www.debian-administration.org/article/SSH_with_authentication_key_instead_of_password](http://www.debian-administration.org/article/SSH_with_authentication_key_instead_of_password)

However, you might want to look at nfs, if you want a permanent share between the 2 computers.
3)It works on any linux distro with openssh server/client installed.

Cheers.
Bogdan

---

### Post by krisztian_andre on 2009-09-23
For me the most convenient way is via samba in nautilus: right click on the shared folder and sharing option. 
And on the client machine go to networks and you'll find the share, click on it and it will be mounted by gvfs.
BUT there is a serious problem with gvfs mounts sshfs or samba: 
Often when I suspend my laptop or the network connection is interrupted, I cant browse or unmount my gvfs share therefore I cant remount it again leaving me with no choice but to reboot the client machine.
How can I go around this? Permanent mounts are not an option for me bacause I move around a lot. 
One Idea was to write a script that unmounts all my gvfs mounts before suspending and then remounts them when wakeing but maybe unmount wont work if lets say a movieplayer is open and playing a file from the share when I suspend.
What say you to this?

---

### Post by rafemonkey on 2009-09-23
I used to be a big proponent of Samba, but it requires too much fiddling, as well as administering a whole new set of users and passwords and shares. If all you need to do is make folders available to other linux boxes NFS is the easiest as long as you don't mind using the shell. Anyway, here's how to setup a simple share for a whole range of machines.

First: install NFS and make sure its working.
```
sudo aptitude install nfs-kernel-server
rpcinfo -p
``` 
If everything installed correctly you should see something like this...
```
  program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32958  status
    100024    1   tcp  60095  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  40723  nlockmgr
    100021    3   udp  40723  nlockmgr
    100021    4   udp  40723  nlockmgr
    100021    1   tcp  46826  nlockmgr
    100021    3   tcp  46826  nlockmgr
    100021    4   tcp  46826  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  41613  mountd
    100005    1   tcp  50417  mountd
    100005    2   udp  41613  mountd
    100005    2   tcp  50417  mountd
    100005    3   udp  41613  mountd
    100005    3   tcp  50417  mountd

```
Next set up your shares. You need to edit '/etc/exports' I used 'sudo vim /etc/exports' but if you prefer an editor from this century you could do 'gksudo gedit /etc/exports'

Since I have a closed network, I decided to share my '/home' directory with every machine on the network to do so I added the line 
```
/home 192.168.0.0/255.255.255.0(rw)
```
to the end of '/etc/exports'. The format is 
```
{path to share} {network number}/{netmask}{access(rw) or (ro)}
```
You can also choose to share only with specific machines by doing something like:
```
/home 192.168.0.142(rw)
```
Save the file and then restart the NFS server with the command:
```
sudo /etc/init.d/nfs-kernel-server restart
```

You'll also need to install NFS on the client machine, then you can mount the share like so...
```
sudo mount 192.168.0.101:/home /mnt/home
```
which has the format...
```
sudo mount {server ip}:{share name} {path you want it mounted to}
``` Finally, you can edit '/etc/fstab' to make the client connect to the share at boot time.

See [http://tldp.org/HOWTO/NFS-HOWTO/]("http://tldp.org/HOWTO/NFS-HOWTO/") for more info.

Hmm maybe that's a bit more complex than I thought... ;) But, Samba always seemed pretty arcane to me. NFS, on the other hand, seems pretty straightforward.

Ohh yeah, don't forget to make a back up of any files you change before you start messing around...

---

### Post by rafemonkey on 2009-09-23
One thought, you can use aptitude to install NFS on Ubuntu and Debian. But, for slackware you might have to play around abit... (does slackware have a package manager these days?)

Also, I don't know if slackware uses init.d, but rebooting the machine will do the trick whatever distro you have...

And, by "the trick" I mean restarting the NFS server.

---

### Post by glore2002 on 2009-09-23
> **rafemonkey said:**
> One thought, you can use aptitude to install NFS on Ubuntu and Debian. But, for slackware you might have to play around abit... (does slackware have a package manager these days?)

Also, I don't know if slackware uses init.d, but rebooting the machine will do the trick whatever distro you have...

And, by "the trick" I mean restarting the NFS server.

Thanks for such a clear explanation!

Slackware does not solve dependencies alone but you can use things such as sbopkg to download and install packages and that will let you know all the needed dependencies.

I use both (Debian and Slackware). Both are great distributions. Stable and fast. Ubuntu -as you know- is based on Debian so they are very similar. 

I will give samba and nfs a try and then I tell you what happened.

Thanks again,

---

### Post by glore2002 on 2009-09-23
Today I shared linux folders through samba and it worked OK. Now, I would like to be able to print from one computer to the other. So How do I add a network printer in Linux?

Thanks again,

---

