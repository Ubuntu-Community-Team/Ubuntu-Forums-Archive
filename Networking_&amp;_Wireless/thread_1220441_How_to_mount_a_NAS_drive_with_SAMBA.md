---
title: "How to mount a NAS drive with SAMBA?"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by fisheater on 2009-07-22
How to mount a NAS drive with SAMBA?		

Hi,

I need some real low technical advise on how to mount a NAS hard drive so I can do a backup via rsync (Grsync really).

Ubuntu 9.04 64 bit.

I have tried to follow the directions on here ([http://tldp.org/HOWTO/SMB-HOWTO-8.html](http://tldp.org/HOWTO/SMB-HOWTO-8.html)) and I can only get to the window that displays the samba share info:

This is the example text from the website:
Server time is Sat Aug 10 15:58:27 1996
Timezone is UTC+10.0
Password: 
Domain=[WORKGROUP] OS=[Windows NT 3.51] Server=[NT LAN Manager 3.51]

Server=[ZIMMERMAN] User=[] Workgroup=[WORKGROUP] Domain=[]

        Sharename      Type      Comment
        ---------      ----      -------
        ADMIN$         Disk      Remote Admin
        public         Disk      Public 
        C$             Disk      Default share
        IPC$           IPC       Remote IPC
        OReilly        Printer   OReilly
        print$         Disk      Printer Drivers


This machine has a browse list:

        Server               Comment
        ---------            -------
        HOPPER               Samba 1.9.15p8
        KERNIGAN             Samba 1.9.15p8
        LOVELACE             Samba 1.9.15p8
        RITCHIE              Samba 1.9.15p8
        ZIMMERMAN            
From here I am stuck!

Plan:
1.Mount NAS harddrive
2.Use Grsync to back up my files.
3.Live happily ever after.

Thanks!

FE

---

### Post by cariboo on 2009-07-22
Can you see all the shares when you run:

```
smbclient -L <server> -U%
```

I my system when I run the aboe command the results look like this:

```
mbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	images          Disk      mounted iso images
	stuff           Disk      whatever fits
	documents       Disk      documents and such
	music           Disk      tunes
	movies          Disk      Movies and TV
	print$          Disk      Printer Drivers
	HPLaserjet      Printer   laser printer
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------
	WILLY                willy server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

If you get the same sort of result you should just be able to set the backup dir for grsync with something like:

```
/server/mountpoint/
```

in my case I use:

```
/willy/media/stuff/restore
```

---

