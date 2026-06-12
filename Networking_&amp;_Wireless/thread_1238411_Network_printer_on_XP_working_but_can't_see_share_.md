---
title: "Network printer on XP working but can't see share on same windows pc"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by alleycatuk on 2009-08-12
I've tried a load of things from various threads but still can't see the shares on my XP machine when going through the nautilus file browser. 

The browser shows all the shares and will show new ones added but when I click on one, it says "Unable to mount location" "Failed to retrieve share list from server".

The xp machine can see the shares I've set up on the Ubuntu machine and the Ubuntu machine can print to the xp machine's shared printer.

I've tried switching both firewalls off and have disabled ufw too but still no luck.

if I do a ```
findsmb
```it shows
[COLOR=Blue]                               *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.213   UBSERVER       +[NETWKGRP] [Unix] [Samba 3.3.2][/COLOR]

which is the ubuntu machine but no sign of the xp one.

If I do ```
smbclient -L xpdesk
```it shows
[COLOR=Blue]Domain=[XPDESK] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Sharename       Type      Comment
    ---------       ----      -------
    hppsc217        Printer   hp psc 2170 series
    D$              Disk      Default share
    print$          Disk      Printer Drivers
    C$              Disk      Default share
Domain=[XPDESK] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------
[/COLOR]
so it can see all the shares on the XP machine

finally, if I try
```
smbtree
```is gives
[COLOR=Blue]NETWKGRP
    \\UBSERVER            ubserver server (Samba, Ubuntu)
        \\UB\HP-PSC-2170        HP PSC 2170
        \\UBSERVER\print$             Printer Drivers
        \\UBSERVER\www                
        \\UBSERVER\IPC$               IPC Service (ubserver server (Samba, Ubuntu))
    \\XPDESK              Alleycat
        \\[/COLOR][COLOR=Blue]XPDESK[/COLOR][COLOR=Blue]\C$                 Default share
        \\[/COLOR][COLOR=Blue]XPDESK[/COLOR][COLOR=Blue]\print$             Printer Drivers
        \\[/COLOR][COLOR=Blue]XPDESK[/COLOR][COLOR=Blue]\D$                 Default share
        \\[/COLOR][COLOR=Blue]XPDESK[/COLOR][COLOR=Blue]\hppsc217           hp psc 2170 series[/COLOR]

Does the xp machine need a user/password sending and, if it does, where do I set it?

If not, can anyone else help? I can get it to work if I do "Connect to Server" but not as part of the file browser!

Thanks.

Update:
I just found out that Dolphin can see the share so maybe it's a nautilus funny?

---

### Post by superprash2003 on 2009-08-12
try accessing via ip instead of hostname like smb://x.x.x.x 

for reference : [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

