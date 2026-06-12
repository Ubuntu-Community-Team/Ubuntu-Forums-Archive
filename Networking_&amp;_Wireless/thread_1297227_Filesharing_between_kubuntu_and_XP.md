---
title: "Filesharing between kubuntu and XP"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by matyd on 2009-10-21
I have installed samba and smbfs... I read through the tutorial provided on the ubuntu website and still haven't figured out exactly how to get this working. As of right now, i can see my kubuntu desktop on my xp machine, I am not able to login into it however. "Windows cannot access \\MATT-DESKTOP" is all it says... I'm a newbie at this just tbh... If anyone could lend their time to help me out i would really appreciate it.

My network is on a wireless router if that is relevant to getting help.
Matt

/*If there is any more information that is needed to help you help me with this problem please let me know, thanks.*\

---

### Post by matyd on 2009-10-21
I have no idea why I told you all XP... I am in fact running Vista on my laptop... Sorry

---

### Post by matyd on 2009-10-21
okay so i'm able to ping both my internal ips (vista and kubuntu) and when doing the samba manual configuration... i get this....

Desktop:
```
matt@matt-desktop:~$ smbclient -L //192.168.2.2 -U user            
Enter user's password:
Domain=[MATT-DESKTOP] OS=[Unix] Server=[Samba 3.3.2]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (matt-desktop server (Samba, Ubuntu))
        PSC-1500-series2 Printer   HP PSC 1500 series
        PSC-1500-series Printer   HP PSC 1500 series
Domain=[MATT-DESKTOP] OS=[Unix] Server=[Samba 3.3.2]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        WORKGROUP            MATT-DESKTOP

```From desktop to laptop:
```
matt@matt-desktop:~$ smbclient -L //192.168.2.3 -U user
Enter user's password:
Domain=[ARROYO] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        D$              Disk      Default share
        IPC$            IPC       Remote IPC
        Public          Disk
        Users           Disk
session request to 192.168.2.3 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

Another weird thing, I can see 'Matt-Desktop' on Vista but i can't see my laptop in remote:/ in dolphin...

---

### Post by swerdna on 2009-10-22
In vista, enable netbios over tcpip


In Kubuntu, temporarily disable the Ubuntu firewall with this command: ```
sudo ufw disable
```

FFI on firewall: [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

Then see if it improves

---

