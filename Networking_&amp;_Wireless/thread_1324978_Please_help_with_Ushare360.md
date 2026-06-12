---
title: "Please help with Ushare/360"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by tyler2time on 2009-11-13
Well I was excited to learn that I didnt have to boot into windows to be able to connect to my 360.  But now I am having troubles getting it to connect.  Fairly new to Ubuntu and not big on networking, but heres what I got.

I installed ushare and edited the ushare.conf file to this (edited for readability:)

# Configuration file for uShare

USHARE_NAME=Ubuntu_Media_Server
USHARE_IFACE=eth0
USHARE_PORT=49200
USHARE_TELNET_PORT=1337
USHARE_DIR=/ty/downloads
USHARE_OVERRIDE_ICONV_ERR=yes
ENABLE_WEB=no
ENABLE_TELNET=
USHARE_ENABLE_XBOX=yes
ENABLE_DLNA=no

when I run ushare -x I get this:

Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
bind: Address already in use

I'm sure I am just over complicating it somehow but any help would be great, thanks

---

### Post by flathampster on 2009-11-13
Im having exactly the same problem. Funny thing is that it was working before I restarted the system. I have stopped and started eth0. Also re-installed ushare. Im using 9.10 64bit. There are no events listed in Firestarter.

---

### Post by Jose Catre-Vandis on 2009-11-13
> **tyler2time said:**
> Well I was excited to learn that I didnt have to boot into windows to be able to connect to my 360.  But now I am having troubles getting it to connect.  Fairly new to Ubuntu and not big on networking, but heres what I got.

I installed ushare and edited the ushare.conf file to this (edited for readability:)

# Configuration file for uShare

USHARE_NAME=Ubuntu_Media_Server
USHARE_IFACE=eth0
USHARE_PORT=49200
USHARE_TELNET_PORT=1337
USHARE_DIR=/ty/downloads
USHARE_OVERRIDE_ICONV_ERR=yes
ENABLE_WEB=no
ENABLE_TELNET=
USHARE_ENABLE_XBOX=yes
ENABLE_DLNA=no

when I run ushare -x I get this:

Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
bind: Address already in use

I'm sure I am just over complicating it somehow but any help would be great, thanks

To some extent you can ignore the "error" messages, it should still work? Mine does work OK, but is a bit flaky.

Works very well with GeexBox though :)

---

### Post by flathampster on 2009-11-13
I have resolved the problem on my machine.

There is a conflicting application called MediaTomb which bound the ip address on startup. I removed it using the "Ubuntu Software Centre" and restarted the PC. Then uShare worked fine.

---

### Post by tyler2time on 2009-11-13
> **Jose Catre-Vandis said:**
> To some extent you can ignore the "error" messages, it should still work? Mine does work OK, but is a bit flaky.

Works very well with GeexBox though :)

Unfortunately thats not the case with mine, I cant get it to connect at all.


> **flathampster said:**
> I have resolved the problem on my machine.

There is a conflicting application called MediaTomb which bound the ip address on startup. I removed it using the "Ubuntu Software Centre" and restarted the PC. Then uShare worked fine.

Yea I don't have MediaTomb installed but I think you are right something is blocking my IP and keeping it from connecting to the xbox.  I dont have firewall enabled.  I am stuck

---

### Post by xinate_dogix on 2009-11-13
im having the same problem. though i was wondering if it might have something to do with the ip tables. since everytime i manage to get my ps3 connected to the server im left without internet access.

---

### Post by sdowney717 on 2009-11-14
try minidlna
[http://minidlna.sourceforge.net/](http://minidlna.sourceforge.net/)
[http://sourceforge.net/projects/minidlna/](http://sourceforge.net/projects/minidlna/)

works great with my DSM 320

---

### Post by ask21900 on 2009-12-15
I had this problem, but resolved it...

sudo /etc/init.d/ushare stop

sudo ushare -x


This resolved the bind error.  Unfortunately (in my install, at least) the service still hangs while creating the metafile (adding files).  The service is still accessable via the Xbox, all media is present, so everything seems to be working fine, except that I have a shell "stuck".  Ctrl+C gets my shell back, but kills the server.

I'm not sure if this is related to my install, my media, or a ushare issue yet.  Either way, this should get you one step closer.


Regards,

David

---

