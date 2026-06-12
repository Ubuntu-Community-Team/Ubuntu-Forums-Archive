---
title: "Accessing virtual machine from Ubuntu"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by Almeida1 on 2012-08-22
Hi,

I am currently running Ubuntu on my laptop and in the office we have a Windows server with a virtual machine that has Ubuntu installed. I want to have access to the virtual machine and mount it to my laptop so that I can work on it from my laptop and so that other colleagues can do the same.

Can someone explain what I need to do to mount it to my laptop? I've already got a few directories from the Windows server mounted to my laptop using fstab but unsure how to access the virtual machine?

Any help is much appreciated.

---

### Post by CharlesA on 2012-08-22
You would be better off talking to the person responsible for the server and VM.

They may have it set up to allow remote access.

---

### Post by cbanakis on 2012-08-22
Are you talking about a "Virtual Machine", or "Remote Desktop"?

I use Remmina (In the software center) for remote desktop, seems to work great.

---

### Post by Almeida1 on 2012-08-22
> **CharlesA said:**
> You would be better off talking to the person responsible for the server and VM.

They may have it set up to allow remote access.

I've spoke to him but he doesn't know anything about linux! :mad:

---

### Post by Almeida1 on 2012-08-22
> **cbanakis said:**
> Are you talking about a "Virtual Machine", or "Remote Desktop"?

I use Remmina (In the software center) for remote desktop, seems to work great.

I'm pretty sure it's a virtual machine but I'll double check. I simply want to add another entry to fstab so that I can have access to the server automatically when I logon to my laptop in work and so that my other colleagues (who also use Ubuntu) can do the same.

---

### Post by Almeida1 on 2012-08-22
I've been told that it's a virtual machine. I can access it using Vmware sphere client on Windows using a username and password that was given to me but I want to mount it to my Ubuntu operating system and work from it.

Thanks

---

### Post by CharlesA on 2012-08-22
Again, check with who is responsible for that VM to see what sort of remote access they have in place already, then get their OK to make modifications to the VM.

If you are just wanting to access it from another Linux box, go with NFS.

---

### Post by Almeida1 on 2012-08-22
> **CharlesA said:**
> Again, check with who is responsible for that VM to see what sort of remote access they have in place already, then get their OK to make modifications to the VM.

If you are just wanting to access it from another Linux box, go with NFS.

Yes I do just want to access it from another Linux box, therefore I was hoping to simply add it to /etc/fstab but it doesn't connect. Do you know how to check the remote access on the VM? Will I find it on the Ubuntu system that is on the VM or on the Windows server? 

Thanks for your help.

---

### Post by CharlesA on 2012-08-22
You would have to check the Ubuntu VM itself.

---

### Post by cbanakis on 2012-08-22
> **Almeida1 said:**
> I've been told that it's a virtual machine. I can access it using Vmware sphere client on Windows using a username and password that was given to me but I want to mount it to my Ubuntu operating system and work from it.

Thanks

You should be able to connect with remmina then.
(The result should be the same as what you had using windows)

Are you just trying to connect and access files? 
Or are you trying to operate the computer as if you were sitting in front of it?

---

### Post by Almeida1 on 2012-08-23
> **cbanakis said:**
> You should be able to connect with remmina then.
(The result should be the same as what you had using windows)

Are you just trying to connect and access files? 
Or are you trying to operate the computer as if you were sitting in front of it?

Basically operate it as though I am infront of it. There will be 2 or 3 of us working on a website that we are building, therefore I want to install the website on the server so that all of us will be able to work on it from our individual machines.

---

### Post by Almeida1 on 2012-08-23
I'll try and explain the steps I have taken so far following [this]("https://help.ubuntu.com/community/SettingUpNFSHowTo") tutorial.

I am looking to mount the /export/www/ folder from the Ubuntu VM (server) to my local machine (client)

I have done the following on the Ubuntu server: (IP - 192.168.xx.xxx)

[LIST]
[*]apt-get install nfs-kernel-server
[*]mkdir /mnt/www
[*]mkdir /export
[*]mkdir /export/www
[*]mount –bind /mnt/www /export/www
[*]Edit /etc/fstab
```
/mnt/www      /export/www none bind 0 0
```
[*]Edit /etc/default/ns-kernel-server
```
NEED_SVCGSSD=no #no is default
```
[*]Edit /etc/default/nfs-common
```
NEED_IDMAPD=yes (added this because it didn't exist)
NEED_GSSD=n #no is default
```

[*]Edit /etc/exports
```
/export 192.168.xx.xxx(rw,fsid=0,no_subtree_check,sync)
/export/www 192.168.xx.xxx(rw,nohide,insecure,no_subtree_check,sync) 192.168.yy.yyy(rw,nohide,insecure,no_subtree_check,sync)
```
[*]/etc/init.d/nfs-kernel-server restart
[*]service idmapd restart
[/LIST]

I have done the following on the Ubuntu Client (IP - 192.168.yy.yy):

[LIST]
[*]apt-get install nfs-common 
[*]Edit /etc/fstab
```
192.168.xx.xxx:/export/www     /mnt/Ubuntu     nfs4    _netdev,auto 0 0
```
[*]Edit /etc/default/nfs-common
```
NEED_GSSD=no
NEED_IDMAPD=yes (added this because it didn't exist)
```
[/LIST]

I've managed to moun /mnt/www to /mnt/exports on the Ubuntu server (192.168.xx.xxx) but still can't connect from the Ubuntu client (192.168.yy.yy)

Can someone point me in the right direction?

Thanks

---

### Post by Almeida1 on 2012-08-23
Anyone? :confused:

---

### Post by Almeida1 on 2012-08-23
I've made my post (#12) more clear now using the code tags so hopefully this will help someone understand what I'm trying to do.

---

### Post by Almeida1 on 2012-08-23
Bump

---

### Post by CharlesA on 2012-08-23
Try this one:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

Also: Please don't bump threads until at least 24 hours have passed from your previous post.

---

### Post by Almeida1 on 2012-08-28
> **CharlesA said:**
> Try this one:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

Also: Please don't bump threads until at least 24 hours have passed from your previous post.

Hi, sorry but that link doesn't seem to work for me, does it work for anyone else?

---

### Post by SJR Dorset on 2012-08-28
The link works for me:

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

### Post by Almeida1 on 2012-08-28
> **SJR Dorset said:**
> The link works for me:

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

Hmm, seems to work now, thanks. I'll go through it now and see if I can get it working. By the way, when granting access on the server to an IP do I need to use the IP address of my individual client (laptop) that is found in ifconfig or the IP of the network (office) which is found when I go to whatismyip.com?

Thanks

---

### Post by Almeida1 on 2012-08-28
OK I've been through that link but still having no luck! The only thing I haven't done is set the firewall to open ports 32771, 111 and 2049. Is this the firewall on the server? Is this something you can do via Ubuntu or will the network administrator have to configure it?

---

### Post by Almeida1 on 2012-08-28
> **henrycmurray said:**
> Hi Friends,
          *my* current setup, I *have* a 10.6.8 *Server* and 10.7 clients.This means *my* users *can* take any *computer* and *get* their own account.

:confused:

---

### Post by Almeida1 on 2012-08-28
OK, I've now opened the ports on the server but still having the same problem: mount.nfs: Connection timed out

---

### Post by Almeida1 on 2012-08-28
Anything else that anyone recommends? How do I check the error logs on the server and client so I can get further information?

---

### Post by Almeida1 on 2012-08-28
Really sorry, this was a problem our end, I was given the incorrect IP address! :mad:

---

