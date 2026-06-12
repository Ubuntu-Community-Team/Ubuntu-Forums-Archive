---
title: "Building a home server."
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by ChrisML123 on 2009-12-13
I'm planning on building a home file server.

I have one big need:

I want a machine that will sit there quietly, monitoring the network, and when my laptop, or my wife's laptop, or my desktop joins the LAN, quietly assessing any changes or new files that have been made, and updating the backup on the server hard disk.

I don't want it to take up a lot of processing power, or completely control the other PC hard drives the whole time. 

I don't want it to need a client program on the PCs either.

Finally, i want it to save up to date copies of all the files, so that it can either be used as a backup to restore later, or be accessed by FTP when the PCs are turned off.

Is this doable?

---

### Post by SaintDanBert on 2009-12-13
If your "server" is going to watch all of your clients and then cause work to happen on those clients, you will need some sort of software on both ends. I suspect from your remarks that you are thinking about software in the "windows application" sense of the word.

Let me suggest that you use SAMBA and NFS file sharing.  Samba will enable the linux server to read and write "shared files" and "shared folders" on your Windows(tm) clients.  NFS (network file services) is the linux or unix (*nix) way for one computer to mount remote file systems as if they were local drives. You can use Samba on *nix workstations if you want. There are also NFS utilities for WinXX.

One approach might create a folder tree on your server -- one folder for each of your remote client workstations.  In each of these folders is another folder for each remote folder on that client. The server would then mount the remote using **smbmount** for windows shares and **mount -F nfs** for *nix shares.

You need to decide if you want these connections all of the time or only when you are running the backup processing. There is network traffic associated with each "mounted share" over and above the traffic during read and write activity. 

There is *nix software called **automount** [http://www.linux.com/learn/docs/ldp/433-automount](http://www.linux.com/learn/docs/ldp/433-automount) that watches for applications to request access to remote files, accomplishes mount processing, and unmounts when the need for access ends. Also, mounting shares takes some time. If you do several for each client at boot time, it will slow things down significantly.
Automount shifts these delays from boot time to an as-needed or on-demand time frame. So now you have several options:
[list]
[*]mount your shares when each client boots
[*]have the server mount shares by script before backup processing
[*]have the server mount shares by automount on-demand
[/list]

There is another side to this coin. Clients may mount shares on the server for repositories or network archives or similar. I suggest that you avoid having clients mount shares on other clients.

I hope this helps,
~~~ 0;-Dan

---

