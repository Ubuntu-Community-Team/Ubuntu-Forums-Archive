---
title: "IPv6: smbclient ok, nautilus not OK with litteral IPv6 address"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by sanderj on 2009-12-04
Hi,

I want to know how I can point Nautilus to a SMB share with a litteral IPv6 address. Nautilus' SMB works good with *names* that resolve to IPv6 addresses and works good with litteral IPv4 addresses, but Nautilus does not understand something like "smb://::1/" or "smb://[::1]/"; this results in errors.

The CLI tool smbclient works very well with litteral IPv6 addresses. See example below.

Tips welcome.



```

sander@quirinius:~$ smbclient -N -L ::1
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    IPC$            IPC       IPC Service (quirinius server (Samba, Ubuntu))
    Brother-HL-2030-series Printer   Brother HL-2030 series
    sharing         Disk     
::1 is an IPv6 address -- no workgroup available
sander@quirinius:~$ 


sander@quirinius:~$ smbclient '\\::1\sharing'
Enter sander's password:
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]
smb: \> dir
  .                                   D        0  Sat Dec  5 00:25:08 2009
  ..                                  D        0  Sat Dec  5 00:24:44 2009
  blabla.txt                                   0  Sat Dec  5 00:25:05 2009

        50040 blocks of size 1048576. 23568 blocks available

smb: \> exit
sander@quirinius:~$ 


```

---

