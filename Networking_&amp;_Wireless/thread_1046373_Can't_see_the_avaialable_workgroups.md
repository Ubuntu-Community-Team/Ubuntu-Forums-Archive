---
title: "Can't see the avaialable workgroups"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by ravi.xolve on 2009-01-21
My lan topology is:

1. My pc running ubuntu 8.10
2. Two computers running windows vista

These two computers using windows file sharing. However, in nautilus or in dolphin I can't even see the workgroup or the icons of the corresponding names of the computers.

I used the command smbclient -L <ip of the computer> and got the following output:

```
Enter ravi's password:
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Ultimate 6000] Server=[Windows Vista (TM) Ultimate 6.0]

        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.1.3.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.3 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
```

Here ravi is my local user name of linux.
Why is this happening. Please help me.

---

### Post by carrett on 2009-01-21
How are you trying to view the shares? Have you tried typing

```
smb:///
```into the address bar?

---

### Post by Coreigh on 2009-01-21
Do you have Samba installed? (smbclient if the Linux box is not the server) I think it is default on the main Ubuntu install. 

And have you tried "Connect to server" from the Places menu? In my experience this works best when the Windows share is NOT a hidden or default share but a folder shared explicitly or intentionally. Oh and also on XP and Vista you have to open the share permissions. Even on an intentionally shared folder the default permission is read only. This can be tricky to find on the "home" versions.

Here are a couple links about Windows sharing;

- [http://technet.microsoft.com/en-us/library/bb727037.aspx](http://technet.microsoft.com/en-us/library/bb727037.aspx)
- [http://www.howtogeek.com/howto/windows-vista/how-to-share-a-folder-the-xp-way-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/how-to-share-a-folder-the-xp-way-in-windows-vista/)

---

### Post by ravi.xolve on 2009-01-22
@ carret
Yes I tried "smb://" in nautilus as well as dolphin

@ Coreigh
Yes I have samba installed and running.
I tried the Network option in Places. My question is I can't see the workgroups or computers. Accessing them is different thing.

---

### Post by ravi.xolve on 2009-02-04
To an extent it worked:

Windows Vista doesn't allow anonymous login. I have to use an existing user and password (of windows vista) to gain access. Here is an example:

```
$ smbclient -L 192.168.1.3 -U User
Enter User's password:
Domain=[SUNIL-PC] OS=[Windows 7 Ultimate 6956] Server=[Windows 7 Ultimate 6.1]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        D$              Disk      Default share
        E$              Disk      Default share
        F               Disk
        F$              Disk      Default share
        IPC$            IPC       Remote IPC
        Public          Disk
session request to 192.168.1.3 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
```

Still there is error in last four lines. I can't see the available workgroups and computers in Dolphin or Nautilus. But at least I can use smbmount and use command line to transfer files.

Now the problem is how to view workgroups and use the computer names assigned in Vista rather than using IP.

NOTE: My friend upgraded to windows 7. but still its the same core (at least in the networking).

---

