---
title: "MediaMVP Frontend Boot Problems"
date: 2008-06-28
forum: Mythbuntu
---

### Post by klyndt on 2008-06-28
I currently have a MediaMVP Rev D3A.  From my research, this is an old version that is non-flash based.  As such, I think this is what is leading to my problems.  I first went through the community documents that cover MediaMVP as a front end and I couldn't even get the atftp server to respond. Using WireShark, I was able to find out that the port the MediaMVP was looking for was 16867 (not 16869).  So, after that change in etc/rc.local, the server was at least responding.  Now I get an error that says (from syslog): 

<time> HomeComputer atftpd[5982]: Invalid request <0> from 192.168.0.102

192.168.0.102 is the IP of the MediaMVP.  I'm wondering if anyone knows what to do about this invalid request error? Does this have something to do with permissions or an incorrect dongle.bin file?  Maybe this is a red herring and something else is not quite right with the atftpd daemon yet?

Thanks for your help,
Klyndt

---

### Post by klyndt on 2008-06-29
Does no one have a working D3A MediaMVP frontend?

Klyndt

---

### Post by mnemonic76 on 2009-01-02
I have a D3A MediaMVP and just got it to boot the the mvpmc.org splashscreen... still working on getting it to do something useful.

mnemonic76

---

### Post by stefanlasiewski on 2009-11-30
I'm trying this right now, following the directions at [https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend](https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend) .

Thanks for the tip about the incorrect port. 

Did you ever fix this issue?

For me, the MediaMVP device seems to be looping. I also see the error message "Invalid request <0> from 0.0.0.0" over and over. I believe this means that the device is sending a NULL ("<0>") request to the tftpport, but I'm not why this happens or what to do about it.

Here's what my logs say, for the record:

```
Nov 29 23:47:34 host1 atftpd[29006]: socket may listen on any address, including broadcast
Nov 29 23:47:34 host1 atftpd[29006]: Creating new socket: 255.255.255.255:55885
Nov 29 23:47:34 host1 atftpd[29006]: Invalid request <0> from 0.0.0.0
Nov 29 23:47:34 host1 atftpd[29006]: Server thread exiting
Nov 29 23:47:43 host1 atftpd[29006]: socket may listen on any address, including broadcast
Nov 29 23:47:43 host1 atftpd[29006]: Creating new socket: 255.255.255.255:33686
Nov 29 23:47:43 host1 atftpd[29006]: Invalid request <0> from 0.0.0.0
Nov 29 23:47:43 host1 atftpd[29006]: Server thread exiting
Nov 29 23:50:24 host1 atftpd[29006]: socket may listen on any address, including broadcast
Nov 29 23:50:24 host1 atftpd[29006]: Creating new socket: 255.255.255.255:56992
Nov 29 23:50:24 host1 atftpd[29006]: Invalid request <0> from 0.0.0.0
Nov 29 23:50:24 host1 atftpd[29006]: Server thread exiting
Nov 29 23:50:33 host1 atftpd[29006]: socket may listen on any address, including broadcast
Nov 29 23:50:33 host1 atftpd[29006]: Creating new socket: 255.255.255.255:40743
Nov 29 23:50:33 host1 atftpd[29006]: Invalid request <0> from 0.0.0.0
Nov 29 23:50:33 host1 atftpd[29006]: Server thread exiting

```

---

