---
title: "Windows 7 shares not showing up"
date: 2012-04-07
forum: Networking &amp; Wireless
---

### Post by Woegjiub on 2012-04-07
Good Day, all.


I have somewhat of a problem.
I have my files shared from kubuntu, and the windows 7 machine can access them perfectly.

However, the files which are being shared from the windows 7 machine are not accessible to the kubuntu machine.

They work fine when the kubuntu machine is booted into windows, but in kubuntu, the computer is not showing up in the network, and "smb://192.168.1.101" does not work, despite "ping 192.168.1.101 " giving the desired results, and that device being indeed the one I want to access.

I tried browsing with pyNeighbourhood, but it only shows the kubuntu machine.
Smb4K was even worse, and did not even show the computer I was on.

Could anyone please help me?

---

### Post by Zorael on 2012-04-07
What is the terminal output of **smbtree**?

(It's in the [**smbclient**](apt://smbclient) package, which I *assume* is part of the default installation...)

---

### Post by Woegjiub on 2012-04-07
> **Zorael said:**
> What is the terminal output of **smbtree**?

(It's in the [**smbclient**]("apt://smbclient") package, which I *assume* is part of the default installation...)
"failed negprot: ERRnomem
failed negprot: ERRnomem"

Incidentally, after unchecking "authenticate with local machine account" in Smb4k, it shows the workgroup, but then fails to scan it.

"Could not connect to server XXXXXXXX Connection failed: NT_STATUS_CONNECTION_RESET"

Also: I added a netbios name (my hostname), as well as following the steps in all the problems on this page: ubuntuforums.org/showthread.php?t=1169149
No dice :(

---

### Post by dandnsmith on 2012-04-08
How is the W7 PC set up?
The 'default' work group stuff for W7 is different from earlier versions (except possibly Vista, of which I have no experience) - and the W7 net group doesn't work except with other W7 PCs.
I cannot remember how exactly I set mine up, but I can see the shares from Ubuntu and Mint installations.

---

### Post by Woegjiub on 2012-04-08
It is set up as default for Windows 7, but with a workgroup instead of that homegroup nonsense Win7 implemented.

---

