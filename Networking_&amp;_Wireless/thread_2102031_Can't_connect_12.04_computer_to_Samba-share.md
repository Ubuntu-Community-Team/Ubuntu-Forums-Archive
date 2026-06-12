---
title: "Can't connect 12.04 computer to Samba-share"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by Azyx on 2013-01-06
I have a samba-server on my **Media PC** (Ubuntu **12.04**) and i mount the shares on my **Desktop** (Ubuntu **10.04**) on a wired network with no problems. But when I connect a additional **Laptop** (Ubuntu 12.04) to a switch connected to a Netgear router with DHPC server and further out to internet. I can not connect to the samba-network. My laptop get an local ip-adress and have internet access.

On my desktop (10.04) I can see under Go --> Network:
** 'Media PC' 'Desktop' and '**Windows network**' **[COLOR=Red]<-- Laptop missing[/COLOR]
if I then go to 'Windows network' --> 'WORKGROUP'I can see:
**'Media PC' 'Desktop' and 'Laptop'**

On my '**Media PC**' (12.04) I choose 'Browse Network'-->'WORKGROUP' I get a popup window withh the message:
[COLOR=SlateGray][I][B]___
[COLOR=DarkSlateBlue]Unable to mount location[/COLOR][/B][/I][/COLOR][COLOR=DarkSlateBlue] 
Failed to retrieve share list from server[/COLOR]
___

The same thing happens with **Laptop** (12.04)

I have shared folder on my **Media PC **(12.04) with a config in /etc/samba/smb.config and not trough  Nautilus sharings options because I wanted to share the sa[SIZE=2]me folder booth as guest with no w[SIZE=2]r[/SIZE]i[SIZE=2]te[/SIZE][/SIZE][SIZE=2][SIZE=2]-[/SIZE]permission and with write permission[SIZE=2], [/SIZE]If I add a password.
[/SIZE]
It seems like **Ubuntu 10.04** can retrieve a share list from server, but not **Ubuntu 12.04**

Something new according to samba-shares between 10.04 and 12.04?

By the way, my **Media PC** also have a VNC-server and I can connect to it with VNC-client  from booth **Desktop** and **Laptop**, so the problem seems to only affect Samba and 12.04

/Cheers

---

