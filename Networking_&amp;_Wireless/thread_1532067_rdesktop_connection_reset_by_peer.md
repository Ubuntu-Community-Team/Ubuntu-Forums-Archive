---
title: "rdesktop connection reset by peer"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by cpudney on 2010-07-15
G'day,

I've happily been using rdesktop to access my MS Vista desktop from Ubuntu (Hardy) for a few months until a couple of days ago when it stopped working.

Now if I try connecting I get the following:

[FONT="Courier New"]$  rdesktop 10.1.1.2 
ERROR: recv: Connection reset by peer[/FONT]

and with strace:

[FONT="Courier New"]socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 4
connect(4, {sa_family=AF_INET, sin_port=htons(3389), sin_addr=inet_addr("10.1.1.2")}, 16) = 0
setsockopt(4, SOL_TCP, TCP_NODELAY, [1], 4) = 0
getsockopt(4, SOL_SOCKET, SO_RCVBUF, [87380], [4]) = 0
send(4, "\3\0\0#\36\340\0\0\0\0\0Cookie: mstshash=chri"..., 35, 0) = 35
read(3, 0x83d5004, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(5, [3 4], [], NULL, {60, 0})     = 1 (in [4], left {60, 0})
gettimeofday({1279249875, 913287}, NULL) = 0
recv(4, 0x83e7788, 4, 0)                = -1 ECONNRESET (Connection reset by peer)[/FONT]

I don't believe anything's changed on the client (Ubuntu) side.  The Vista box is occasionally connected to a corporate intranet via VPN and it was after such a session that rdesktop stopped working, so perhaps a Windows group policy was modified during the session.

I've checked the basics - can ping 10.1.1.2 from Ubuntu, can access port 3389.  Have deleted ~/.rdesktop and ~/.tsclient.

Digging around the Vista client I noticed in Control Panel > System Properties > Remote that in the *Remote Desktop* sub-panel the *Allow connections only from computers running Remote Desktop with Network Level Authentication* setting is enabled and that the other two are greyed out.  Now, I don't know whether this setting has been changed but I suspect that it might be the problem.

Unfortunately, I don't know enough about Windows to know how or even whether I can change this setting to *Allow connections from computers running any version of Remote Desktop (less secure)*

I've poked around the group policy editor (gpedit.msc) but no joy.

Any suggestions on how I can get rdesktop working again?

Thanks,
Chris.

---

### Post by rawat on 2010-08-11
Any solution for the same??

I am facing the same problem. Earlier it was working fine and i never got disconnected. But now something is wrong one either end!!

I can connect but after sometime i get same error. rdesktop window freezes , keyboard too freezes.

I tried to connect to some other windows machine but same behavior :(.

Please do update if any one has got information on this.


Thanks
Rawat

---

### Post by cpudney on 2010-08-11
G'day,

> **rawat said:**
> Any solution for the same??

No joy I'm afraid - I've switch to VNC.  It's not as good though...

> I can connect but after sometime i get same error. rdesktop window freezes , keyboard too freezes.  I tried to connect to some other windows machine but same behavior

Sounds like a different problem, possibly at the client end as you get the same behaviour regardless of the Windows machine you connect to, whereas I can't connect at all...

Good luck,
Chris.

---

### Post by rawat on 2010-08-20
Mine is working fine now.

I disabled the ipv6 thats it.

Connected and now running as smooth as ever without any ttouble.

modified** /etc/default/grub**

added 

**GRUB_CMDLINE_LINUX="ipv6.disable=1**"

rebooted.

Cheers
Rawat

---

### Post by cpudney on 2010-08-22
G'day,

> I disabled the ipv6 thats it

I tried that - no joy :(

Cheers,
Chris.

---

### Post by tmera on 2010-10-18
One more thing that causes this...

If the Remote Settings on the target, in my case Win 7, only allows connections from Remote Desktop with Network Level Auth.  Choose Allow connections from computers running any version of Remote Desktop.

Right Click Computer -> Properties -> Remote Settings.

---

### Post by cpudney on 2010-10-18
G'day,

> **tmera said:**
> Choose Allow connections from computers running any version of Remote Desktop.

Unfortunately, that setting is disabled (see [original post]("http://ubuntuforums.org/showpost.php?p=9595428&postcount=1")) and so can't be selected :(

Do you know how to enable this setting?

Thanks,
Chris.

---

### Post by eelevets on 2010-11-01
Hi guys I'm having the same problem as Chris. I connect through VPN no problem then try to start rdesktop it starts but then closes down. When I run rdesktop in terminal I get the connection reset by peer message. All was working fine until last week and both my Windows set ups (Vista and XP Pro) work ok but I want to use Ubuntu heeeelllpppp!!!

---

### Post by cpudney on 2010-11-01
G'day,

> I want to use Ubuntu

I still haven't solved the original rdesktop problem but like you want/need to use Ubuntu to access Windows desktops, so I'm using VNC instead.  It's not as good as rdesktop but is better than nothing.

On Vista I use [TightVNC]("http://www.tightvnc.com") (server) and on Ubuntu (Lucid) I'm using xvncviewer (client).

HTH,
Chris.

---

### Post by eelevets on 2010-11-08
Hi Chris
 
Not sure I can use VNC as I dont have access to our server at work. I asked our techys for support but they dont support Ubuntu so Im on my own. Still using Windows through VPN and remote desktop ok but want to get away from MS and Windows as much as possible.

---

### Post by eelevets on 2010-12-30
Not sure if anyone is still interested in this but i just updated both my computers with the latest release of LUCID 2.6-32-27 and rdesktop is working ok again

---

### Post by cpudney on 2011-01-10
G'day,

> i just updated both my computers with the latest release of LUCID 2.6-32-27 and rdesktop is working ok again

I'm also running 2.6-32-27 but rdesktop still gives the same error:

ERROR: recv: Connection reset by peer

I'm pretty sure the issue lies with the Vista PC I'm trying to connect to :(

Regards,
Chris.

---

### Post by eelevets on 2011-01-10
Hi, I've moved on a stage following another update rdesktop has stopped working on my laptop but still works on the desktop after loading the same update. I tried removing and re loading rdesktop but still no good.
 
I use redesktop to connect to my work server which runs Windows 2000 server or something to that effect it looks and feels a lot like Windows XP. Clunky but stable(ish)

---

