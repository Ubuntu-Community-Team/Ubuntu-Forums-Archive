---
title: "network connection problem"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by Alan.Brown on 2013-04-07
I have 3 computers networked together.  They are called HP, ACER and TOWER.
From HP I can connect to ACER and TOWER OK and exchange files.
From ACER I can connect to TOWER but NOT to HP
From TOWER I can connect to ACER but NOT to HP

Using **findsmb **on HP I get
>                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.6     TOWER          [WORKGROUP] [Unix] [Samba 3.6.6]


This is incorrect for HP - the IP address for HP on the router is 192.168.0.2 and the name is HP.  I reason that this error stops the other computers from connecting.

**ifconfig** on HP shows the correct iP address on the router

The other two computers show their correct IP addresses and NETBIOS NAMEs.

On HP the **smb.conf** file has the netbios name HP which is correct.

How can I change settings so that **findsmb** gives the correct address

On ACER the output from **smbtree** is 
> smbtree
Enter user's password: 

WORKGROUP
    
\\TOWER                  tower server (Samba, Ubuntu)
        \\TOWER\IPC$               IPC Service (tower server (Samba, Ubuntu))
        \\TOWER\user               Tower
        \\TOWER\print$             Printer Drivers

    \\READYSHARE             readyshare
        \\READYSHARE\ADMIN$             IPC Service (readyshare)
        \\READYSHARE\IPC$               IPC Service (readyshare)
        \\READYSHARE\USB                read:all-no password;write:all-no password
    
\\HP                     hp server (Samba, Ubuntu)
        \\HP\.Crypt             
        \\HP\print$             Printer Drivers
        \\HP\user               Acer Laptop
        \\HP\IPC$               IPC Service (acer server (Samba, Ubuntu))
    
\\ACER                   acer server (Samba, Ubuntu)
        \\ACER\.Crypt             
        \\ACER\print$             Printer Drivers
        \\ACER\user               Acer Laptop
        \\ACER\IPC$               IPC Service (acer server (Samba, Ubuntu))



You will note that **\\HP\user** points to **Acer Laptop.**  It should be **HP**.  All the rest is OK. If I try to connect to HP from ACER I get the ACER directories not the HP ones.
Similarly on the TOWER computer.

The output of **smbtree** on HP is OK.

Sorry that this may be a bit confusing.  I hae tried to provide as much information as I think necessary.

TIA

Alan

---

### Post by dmizer on 2013-04-07
First, on all of your Ubuntu boxes, run this command:
```
sudo apt-get install cifs-utils
```
Then, have a look at this post for troubleshooting options: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by Alan.Brown on 2013-04-07
I have already got **cifs-utils** on all 3 computers.  I needed that because in **fstab** I mount an external **ntfs** hard drive which is connected to my modem/router and shared by all computers.   This has worked for a couple of years.

Also my workgroup is already named **WORKGROUP** on all computers.  The fact that two of the three computers are working OK show that I have set them up correctly.

The problem I have at the moment is only very recent - everything was working OK for a year or so.  I have changed a setting somewhere that I cannot find now.

What concerns me, and what is the real problem I believe is that **findsmb** shows the incorrect **IP address** and **NETBIOS** name on the one computer only.   In **smb.conf** the netbios name is **HP** as it should be.

Thanks for your reply.   I have checked out your link which covers most of what I have done already.  I am not using Wndows - just Xubuntu and Kubuntu.

TIA

---

