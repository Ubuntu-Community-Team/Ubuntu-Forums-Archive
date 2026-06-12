---
title: "The share is completely corrupted"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by saidbakr on 2009-09-11
Hello,

I submited several posts about my troubles with Samba and I tried to install and remove some componentes related with Samba. Now I have got the ultimate foolish by there is no share options appeared on right click over the folder icon.

I noticed also, clicking on Windows Network, give out the same error message, either Samba installed, removed, stopped or even running, In other word, It is the only thing that I have got from clicking on Windows Network.
> 
**Unable to mount location**
Failed to retrieve share list from server


The problems with Samba drive me to be crazy!. So I need to understand what's " mount lcation "? and where this location? Where this server and what's port it use?

If there is talk about server, so could I understand that there are client and should every client have the server too in-order to make his share on his local machine?

I noticed another bug in remove Samba, Samba remove does not remove the /etc/samba/smb.conf file and the new installation uses the old configuration file.

I'm totally get lost!

---

### Post by lensman3 on 2009-09-11
From a command line: what happens when you run "smbclient -L <ip number of windows machine>.  It will ask you for a password, just hit enter.  You should see the disk/printers/etc the windows machine is "sharing".  It should look very much like a windows network query when you are looking at a remote machine and seeing what that remote machine is offering up.

The server is the remote windows machine (and you want to mount those folders on your local (client) machine).

The client is the Linux.  On the Linux machine you have to mount the folders someplace.  That someplace is called the mount point.  

Hope this helps a little.

---

### Post by saidbakr on 2009-09-12
I write my reply after removing samba-common and installing the share service again. The command you regarded does not works because I removed all what we could call " contaminations " by remoiving samba and samba-common to get fresh smb.conf.

It takes long time to be able get the WORKGROUP in Windows Network, after several Unable to mount location error message. After this time the workgroup computers in my LAN appear but the same message I get when trying to open the shared file from the remote computer.

Now I'm afraid to install smbclient, to get back inside the dilemma of conflicted packages that may corrupt the work of Samba. What do you think? could I able to install smbclient and everything will not go to the worth?

---

### Post by saidbakr on 2009-09-12
However, I installed smbclient and this the output of the remote computer in the LAN:

> 
Domain=[NANCY-DESKTOP] OS=[Unix] Server=[Samba 3.3.2]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    IPC$            IPC       IPC Service (nancy-desktop server (Samba, Ubuntu))
    &#1589;&#1608;&#1585;          Disk      
Domain=[NANCY-DESKTOP] OS=[Unix] Server=[Samba 3.3.2]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------
    WORKGROUP            NANCY-DESKTOP



---

