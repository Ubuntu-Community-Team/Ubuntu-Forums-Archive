---
title: "rsync - transfer files across network"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by Alan.Brown on 2012-02-28
I have two computers each running Xubuntu.    I have full read/write file sharing using Dolphin and Thunar - with Samba.

I now want to use **rsync** to sync the files from one directory on the first computer to the second.

I have tried **rsync** but had problems.   The host name of the first computer is **HP  **and on the other is **ASUS**.   The directory I am copying from is **/Common/Documents**  and the destination is **/home/user/Share**.  Both directories are set to share.

> 
[B]rsync -auv --progress /Common/Documents ASUS:/Share
[/B]

ssh: connect to host ASUS port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.8]

> 
[B]rsync -auv --progress /Common/Documents ASUS:/home/user/Share
[/B]

ssh: connect to host ASUS port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.8]
I get the same errors when using **sudo**.

**rsync** works OK on each computer without using the network.

Any help please

TIA

Alan

---

### Post by linux6994 on 2012-02-28
Check to see if you can manually acsess eachothers files from either direction? Perhaps add 'force user = yourname' to smb.conf?

---

### Post by Alan.Brown on 2012-02-28
I can access each others files through Dolphin and Thunar.  Is this what you mean?

Alan

---

### Post by jacob.david on 2012-02-28
Looks like the ssh daemon is not running. Could you check the below.

/etc/init.d/sshd status

and check the status.

Also under what user are trying to copy the files. Is the user same on both machines. You didn't specify the username in the target so it will use the existing user id. Is this available in the target host.

---

### Post by Alan.Brown on 2012-02-28
@jacob

**/etc/init.d/sshd status **gives me
[B]bash: /etc/init.d/sshd: No such file or directory
[/B] 
I have three computers each running Xubuntu and Kubuntu.   Being lazy and unimaginative all installations have the same user - **user**  :P.  Also the same password.   So the target name and the existing names are the same.

I have tried **ftp** and **filezilla** and each time I try to connect I get **permission denied**.

There must be some way that I can change the target computer to allow connection.

Thank for your reply

Alan

---

### Post by Alan.Brown on 2012-02-29
Done it!!!    I am SOOOO happy!!  :P:P:P

First I used **ssh** on each computer to establish passwords (this may have been unnecessary - I was guessing)

Then from the modem's DHCP client list I got the IP Address.  If I use the  target hostname (ASUS) the files are written to the **SOURCE** directory!!

So this works (for me at least)
> **rsync -auv --progress -s /Common/Documents user@192.168.2.3:/home/user/Share**This is exactly what I want but I would like to know why I have to use the IP address and not the target host name.

Thanks for help

Alan

---

