---
title: "Sharing Files Between Ubuntu &amp; Windows 7"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by Night-Shurai on 2010-09-11
So I followed these steps to try and connect my Desktop(Ubuntu) and Laptop(Win 7) together so they could share files.

```
sudo apt-get install samba

sudo su

cp /etc/samba/smb.conf /etc/samba/smb.comf_default

gedit /etc/samba/smb.conf

Global Settings Section:
Set workgroup name: setworkgroupame
Undernaeth type: netbios name = yourservernamehere

Shared Definition Section:
type:
[Myshare]
comment = Myshare
path = /myshare
read only = no
guest ok = yes

Authentication Section:
Remove # sign infront of security = user
replace user to share
Save & Exit

Return to Terminal
sudo mkdir /myshare
sudo chmod 0755 /myshare
sudo /etc/init.d/samba restart
```

sudo su was not originally in the steps but it wouldn't give me permission to edit the samba file unless I did.

Also at the end it said command not found or something like that when I tried to restart samba, so I just logged out and then back in.

So now I can identify Ubuntu and Win 7 from on each other, but I can not access either of them. Ubuntu goes into windows network, then workgroup, shows the computers on the network but when I try to access one this comes up:

[IMG]http://img821.imageshack.us/img821/4867/screenshotnlf.png[/IMG]

When windows tries to access Ubuntu it request for username and password. I type it in but it does not recognize it.

So help would be much appreciated.

Night

P.S. I allowed the Documents folder on Ubunto to share across the Network, and while it shows up in along with myshare on Win 7, it still requests for username and password.

---

### Post by borth92 on 2010-09-11
i am not familiar with this issue, but there is a way to create a partition that both Windows and Ubuntu recognizes and mounts. you could try giving that a go

---

