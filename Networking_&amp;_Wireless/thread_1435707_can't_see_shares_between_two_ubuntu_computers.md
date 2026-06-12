---
title: "can't see shares between two ubuntu computers?"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by heiNey on 2010-03-21
as the title states.  both are running 9.04

i have samba installed on both, each computer can ping the other, they each have a folder that is being shared, and they each can see a third computer that has windowsxp on it.  however, they cannot see each other.

not really sure what is going on.  went to places/network and nothing shows up except the windows workgroup/computer.

help please.

---

### Post by Iowan on 2010-03-21
You can try the "Connect to Server" option in Places - I've had better luck with it, but you may need to know how to get to the share (browsing doesn't seem to work as well).

---

### Post by heiNey on 2010-03-21
that requires setting up some sort of SSH or FTP daemon right?  I just wanted to set up a simple share.  

It has worked before with different computers, i just cant seem to figure out what's wrong this time since both computers are new installs.

---

### Post by garvinrick4 on 2010-03-21
> **heiNey said:**
> as the title states.  both are running 9.04

i have samba installed on both, each computer can ping the other, they each have a folder that is being shared, and they each can see a third computer that has windowsxp on it.  however, they cannot see each other.

not really sure what is going on.  went to places/network and nothing shows up except the windows workgroup/computer.

help please.So in the XP network both karmics show up and your router and you can print from any computer it is just both the karmics do not see each other in the Workgroup. Is that the situation?

---

### Post by heiNey on 2010-03-22
well, i did some testing and now they can see each other, but they can't access the shared folders.  I have to allow guest access (which i dont want to do) in order for access to be granted.  i typed in the password and it wouldn't accept it.  i'm not sure what the problem is now.

---

### Post by Morbius1 on 2010-03-22
There are two sets of passwords involved. You need to create a local account on the server for the remote user and then create a samba password for that user.

Consider the following setup: 

Ubuntu1 - has a share created by user **john**
Ubuntu2 - has a user ( **mary** ) that wants access to john's share.

* [] To have mary access john's share using john's username and password:*

Open **Terminal**
Type [B]sudo smbpasswd -a john
[/B][COLOR=#0000ff]*This will add AND enable a "john" samba account/password.*[/COLOR]

After asking you for sudo's password it will ask you what samba password you want to give john. It does not have to match john's login password.

* [] To have mary access john's share using mary's username and password:*

You need to create a local "mary" account on john's machine first and then create a samba password:

Open **Terminal**
Type **sudo useradd -s /bin/true mary**
[COLOR=#0000ff]*This will create a "mary" user on john's machine that has no local logon capability and no home directory.*[/COLOR]
Type **sudo smbpasswd -a mary**
[COLOR=#0000ff][I]This will add AND enable a "mary" samba account/password.
[/I][/COLOR]

---

### Post by SR_ELPIRATA on 2010-03-24
Sharing folders was soooo easy with 7.10.....

---

### Post by Iowan on 2010-03-24
> **SR_ELPIRATA said:**
> Sharing folders was soooo easy with 7.10.....Don't get me feeling nostalgic... there's no going back (for me at least) - even though I agree...:roll:

---

