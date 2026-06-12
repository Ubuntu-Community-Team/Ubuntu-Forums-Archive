---
title: "Copying tru wired network is really slow ubuntu 8.10"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by climmax on 2009-02-01
I have tried finding a solution on here but nothing looks like my problem.
I installed ubuntu 8.10 today. At first my network was good. After installing all the updates my network is damn slow. Its taking me 34 min to copy 314MB. Even when i try using ftp. It takes forever.

I login to the ubuntu pc with my xp machine browse the file i need and copy it to my xp machine

What can i do to fix this problem?

First computer (server)
running ubuntu 8.10 desktop
P4 core 2 E6750
4 gig mem
gb lan   

second pc
running windows xp 
P4 core 2 T5500
1 gig mem
gb lan

smb config:
[global]
	workgroup = WANKER
	netbios name = MAIN
	security = SHARE
	preferred master = yes
	smb passwd file = /etc/samba/smbpasswd

[1tb]
	path = /home/wanker/1tb/
	comment = jos's home directory
	public = yes
	guest ok = yes
	writeable = yes
	browseable = yes
	read only = no

---

