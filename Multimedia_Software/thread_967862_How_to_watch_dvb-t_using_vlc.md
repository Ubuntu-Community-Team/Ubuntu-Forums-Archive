---
title: "How to watch dvb-t using vlc"
date: 2008-11-02
forum: Multimedia Software
---

### Post by ansicplusplus on 2008-11-02
Hy, for a long time I wondered how to access my dvb-t card using vlc. Recently I stumbled about the answer. It's amazingly simple yet undokumented therefore I want to share my knowledge. 
```
vlc .tzap/channels.conf
```
opens vlc and presents all channels in a play list. That's it -- you don't need to juggle with frequencies and transponders. 

If you don't have a channels.conf, check with linuxtv.org and [use scan in the dvb-apps package to create a channels.conf]("http://www.linuxtv.org/wiki/index.php/Scan").

I guess it works the same for dvb-s and dvb-c but I have not the equipment to verify that.

Yours ansicplusplus

---

### Post by marcellux on 2010-01-29
hi! what do you mean with "code"? you put that in a terminal or what?

cheers

---

### Post by marcellux on 2010-01-29
I tried it with a terminal and this is what I got;

 vlc .tzap/channels.conf
VLC media player 1.0.2 Goldeneye
[0x8b20140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat .tzap/channels.conf
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[0x8e29818] access_file access error: cannot open file .tzap/channels.conf (No such file or directory)
[0x8e36cc0] main input error: open of `.tzap/channels.conf' failed: no suitable access module

are you using ubuntu 9.10?

cheers

---

### Post by raymurph on 2010-07-05
Thanks marcellux that worked for me!


ansicplusplus:

your error output when you ran the command contains:

libdvdread: Can't stat .tzap/channels.conf
No such file or directory

so vlc couldn't find a file called channels.conf at that location.  So you need to tell vlc to look  wherever you saved your channels.conf file and it should work, ie: 

vlc /path/to/folder/containing/channels.conf

---

