---
title: "Issues with cupsaddsmb"
date: 2005-12-12
forum: Networking &amp; Wireless
---

### Post by WebsterTrivium on 2005-12-12
Hey guys, I'm trying to get a printer driver served from my Ubuntu linux machine. I believe I've got most of the work done, although I've run up into a wall in the form of cupsaddsmb.

I have this in my /etc/samba/smb.conf file
```

[global]
   printing = cups
   printcap name = cups
   print administrator = [username]

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
   public = yes
   guest ok = yes
   writable = no
   printable = yes
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no


```  Now, when I try the command:

```
cupsaddsmb -a -v
```

I get the result:
```

Running command: smbclient //localhost/print\$ -N -U'[username]%[password]' -c 'mkdir W32X86;put /var/tmp/439d075fc47ac W32X86/PSC-1300.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
Domain=[NARSHE] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]
NT_STATUS_NETWORK_ACCESS_DENIED making remote directory \W32X86
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/PSC-1300.ppd
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/ps5ui.dll
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/pscript.hlp
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/pscript.ntf
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/pscript5.dll
```


Any help would be greatly appreciated, because all I get is an endless loop asking for my password.

Thank you!

---

