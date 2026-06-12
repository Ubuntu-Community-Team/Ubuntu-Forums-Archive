---
title: "I'm stumped! (vnc with ssh tunnel)"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by gjaffe on 2009-04-15
Hi everyone --

I have been using vnc through a ssh tunnel for years successfully, that is until about a week ago.  I changed ISPs and routers, and it stopped working.  So the next day, I changed back to the original ISP and router, and it still didn't work.  Huh?!?  After days of trying to figure this out, I'm stuck.

Here's what I do.  Let's say my vncserver is running on host 'abc'.  From my remote system, I run an expect script which basically does the following.

ssh -L 5901:abc:5901 abc

and then it issues the following command

vncviewer localhost:5901

Again, this has worked for years, even before ubuntu (on Redhat 7).  But now all I get is

---------------------------------------------------------------------
VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed Apr 15 20:05:57 2009
 CConn:       connected to host localhost port 5901
----------------------------------------------------------------------

and it just sits there.  I CAN do

vncviewer abc:5907

and this does work.  It's just not encrypted.  :(

I've tried different remote systems, different versions of vncserver and vncviewer.  I even reinstalled the vncserver on abc.  I've turned off the firewall and disabled the hosts.allow system on both abc and the remote system.  I did port forwarding of port 5901 on the router on both ends.  Nothing helps.  Any suggestion would be appreciated.

Thanks
Gary

---

### Post by Worp8d on 2010-05-22
I'm having a similar problem with ssh.  Have been using it for years and then I started to play around with vnc - installed various vnc servers (tightvnc, x11vnc etc.) and then went back to the original vino/vinagre configuration.  Now I can't use the standard ```
ssh <user>@<host-name>
``` command but instead have to use ```
ssh <ip.addr> -l <user>
```  It wouldn't bother me except that it's stuffed up my rsh auto-backup and I really don't want to have to set everything up again.

Sorry, go nothing helpful to say, I'll let you know if I find anything out.  :)

---

### Post by krunge on 2010-05-22
> **gjaffe said:**
> 
ssh -L 5901:abc:5901 abc

It is safer to use:
```

ssh -L 5901:localhost:5901 abc

```
And perhaps that will also solve your problem (e.g. 'abc' doesn't resolve properly on host 'abc'; or maybe something with ssh -L redirs has changed.)

See if 'localhost' works.  If it doesn't I have some other ideas.

---

