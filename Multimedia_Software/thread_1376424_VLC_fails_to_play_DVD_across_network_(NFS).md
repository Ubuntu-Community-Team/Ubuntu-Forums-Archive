---
title: "VLC fails to play DVD across network (NFS)"
date: 2010-01-09
forum: Multimedia Software
---

### Post by zcacogp on 2010-01-09
Chaps, 

I'm struggling with this one. And I think I'm going a little mad(!)

I have a desktop computer with a DVD drive in it. 

I have two laptops, neither of which have a DVD drive, but all of them are on a wireless network at home. 

I have the DVD drive shared across the laptops using NFS. (I can post the etc/exports and the fstab files if need be, but I don't *think *they are the problem). 

Two days ago, I put a DVD in the desktop machine, fired up the first laptop (x61s), opened VLC on the laptop and watched the DVD fine across the network. Very good it all was too. 

Yesterday, I tried exactly the same, and it failed. The DVD fails to open on VLC. It doesn't buffer, it doesn't show the length of the disk, it just goes back to the 'no media loaded' state. 

It's doing the same now. If I run VLC from the command line, it gives the following: 

```
ogp@ogp-x61s:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x945d9c0] main interface error: no interface module matched "globalhotkeys,none"
[0x945d9c0] main interface error: no suitable interface module
[0x93b6140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x93b6140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device 192.168.10.2:/media/cdrom0 mounted on /media/cdrom0 for CSS authentication
libdvdread: Could not open 192.168.10.2:/media/cdrom0 with libdvdcss.
libdvdread: Can't open 192.168.10.2:/media/cdrom0 for reading
libdvdread: Device 192.168.10.2:/media/cdrom0 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ogp/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
[0xb73016f0] main input error: ES_OUT_RESET_PCR called
[0xb73016f0] main input error: ES_OUT_RESET_PCR called
[0xb73016f0] main input error: ES_OUT_RESET_PCR called
[0xb73016f0] main input error: ES_OUT_RESET_PCR called
```

The same thing happens from the other laptop (X31), and when I do the same I get this set of messages in the terminal: 

```
 
ogp@x31:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x97ad8e0] main interface error: no interface module matched "globalhotkeys,none"
[0x97ad8e0] main interface error: no suitable interface module
[0x9712140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9712140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device 192.168.10.2:/media/cdrom0 mounted on /media/cdrom0 for CSS authentication
libdvdread: Could not open 192.168.10.2:/media/cdrom0 with libdvdcss.
libdvdread: Can't open 192.168.10.2:/media/cdrom0 for reading
libdvdread: Device 192.168.10.2:/media/cdrom0 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ogp/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
[0x99add20] main input error: ES_OUT_RESET_PCR called
[0x99add20] main input error: ES_OUT_RESET_PCR called
[0x99add20] main input error: ES_OUT_RESET_PCR called
[0x99add20] main input error: ES_OUT_RESET_PCR called

```

This doesn't mean a lot to me, but it looks like there is some problem accessing the disk in the desktop machine. BUT it plays fine if I open VLC on the desktop machine, so it works that far. 

The funny thing is that it worked across the network fine on the first laptop (x61s) a couple of days ago, and I don't think I have changed anything on either machine since then. (I suspect it worked fine on the second laptop - X31 - but don't recall trying it.) 

What's wrong, and what can I do to fix it? 

All help welcomed, thanks. (Do ask if you need more details - I'll try and post them) 


Oli.

---

### Post by zcacogp on 2010-01-09
Bump ... anyone have any ideas? 

Thanks. 


Oli.

---

### Post by Ubu_Fester on 2010-02-13
I'm not sure it's network related.  I am getting an identical error log when trying to play a DVD on a single desktop.

---

