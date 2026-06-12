---
title: "Windows 7 and Samba Server Not  Showing"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by Timesoarer on 2013-02-11
I wanted to try and post some comments about a problem I had with Window 7 and Samba Server not showing in Network Neighborhood.

1.) check your smb config this is  part of mine just the global settings..  I like to use the samba webadim tool swat to reboot my samba server when I make changes. 
[global]
        workgroup = EVERYONE
        netbios name = Blade
        server string = Samba Server Proliant
        interfaces = lo eth0
        bind interfaces only = yes
        name resolve order = bcast lmhosts host wins
        domain logons = Yes
        preferred master = Yes
        domain master = Yes
        guest ok = Yes
        hosts allow = 127.0.0.1 192.168.1.0/255.255.255.0

2.) check your smb.conf for errors.

# testparm -s

3.) Things to check for in your smb.conf make sure netbios name is different from your server name.  In windows check your firewall settings. A very important setting in windows was to Enable NetBios over tc/ip in your network properties settings.
Also make sure your windows workgroup name is the same as your samba server.

4.) Check your sambaserver client list and some very usefull commands to help troubleshoot your samba server.
 

# smbclient -L yourservers IP

My Output was:
Domain=[EVERYONE] OS=[Unix] Server=[Samba 3.4.7]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (Samba Server Proliant)
        ROOT            Disk      Admin Root Dir
        ebook           Disk
        SERVER          Disk
        MP3             Disk
        TERA            Disk
        HLDS            Disk      hl server dir
        print$          Disk      Printer Drivers
        HP_2710         Printer   HP_2710
        HP_HP_Photosmart_2700_series Printer   HP HP Photosmart 2700 series
Domain=[EVERYONE] OS=[Unix] Server=[Samba 3.4.7]

        Server               Comment
        ---------            -------
        BLADE                Samba Server Proliant
        MIDDLEMAN
        STORMY

        Workgroup            Master
        ---------            -------
        EVERYONE             BLADE

# findsmb

My output was:
root@proliant:/etc/samba# findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION
---------------------------------------------------------------------
192.168.1.115   BLADE         *[EVERYONE] [Unix] [Samba 3.4.7]

#smbtree

My Partial output was and all the other computers in my network and their shared folders.
EVERYONE
        \\STORMY


Let me know if this helps resolve windows 7 and your Samba server.
you can email me here also.  I'm no expert in posting help filess but these are some of things that really helped me resolve the problem.   I prefer the Network Neighborhood Icon over mounting it by the ip and share name.

---

