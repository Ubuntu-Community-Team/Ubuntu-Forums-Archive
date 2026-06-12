---
title: "Mounting NFS Shares Hit or Miss On Linux Box Running Ubuntu"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by shalamigri on 2013-08-30
I'm having problems mounting NFS shares to my Linux PC. I'm having the same issues in Ubuntu 13.4 and Linux Mint 15. My NSF server is running on a ReadyNAS Ultra 4. My Linux PC has a static IP and I've assigned that ip address in the "root privilege-enabled hosts" field for all of my shares.


I've successfully mounted a couple of shares at one point, but I did some playing around and unmounted those shares and haven't been able to mount any shares since. I must also add that I had shares mounted with cifs and NFS at the same time. I just wanted to point that out just in case there may have been some sort of conflict that led me to my current problem.


I'm now getting the following error when attempting to mount ANY NFS share:
**"mount.nfs: access denied by server while mounting"**


I also used the following command to install the necessary client files before attempting to connect to my NFS server:
**apt-get install nfs-common**


I'm using the following structure to mount shares:
**sudo mount ServerIP:/folder/already/setup/to/be/shared /home/username/folder/in/your/local/computer**


I've restarted the NFS server on my ReadyNAS Ultra 4 device, rebooted it and have also restared my linux box as well with no luck.


I've also used the following command to successfully show my NFS server's export list:
**showmount -e (NFSserver ip)**

I also posted this in the Readynas forum as well.


Any help on why I'm getting the error I'm getting would be appreciated.


Thanks in advance.

---

### Post by steeldriver on 2013-08-30
Are these public shares or user (home) shares? if the latter what are your UIDs on the NAS versus the client box?

---

### Post by shalamigri on 2013-08-30
Thanks for the reply. It seems to be working ok now under Ubuntu. Not sure what the issue with Linux Mint 15 was.

The answer to your question though.

I'm assuming these are public shares. I'm guessing the user(home) shares are shares that would be in this format:
serverip:/c/home/user1
serverip:/c/home/user2

If so, then no, I was not trying to mount those shares.

Shares I'm attempting to mount are in this format:
serverip:/music
serverip:/video
serverip:/pictures

I have the shares disabled by default on the ReadyNAS device, but I've given root access on those shares to the ip on the Linux machine I'm trying to connect from.

I can connect to the shares if I set the default access on the to "read/write" or "read-only"
___________________________________________________________________________

It seems to be working now though. Thanks for replying back so soon.

---

