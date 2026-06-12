---
title: "troubleshoot: remote access to ubuntu desktop"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by snorkytheweasel on 2011-02-19
I have two Windows XP computers and one Linux computer. The Linux box is running Maverick Meercat server with a gnome desktop. I'm having a problem connecting from Windows to Ubuntu.

The usual way to do this is to use VNC. I've set up and used various flavors of VNC for years, without problems.... until now. 

On this Ubuntu box I've tried vnc, tightvnc, x11vnc, xtightvnc, xvnc - all in various combinations of ports and protocols. I've ensured that each those configurations matches on each end of the communication. All of that said, whenever I try to connect from Windows to Ubuntu I get the same error:
**Failed To Connect To Server**.

When I use Putty - or a Windows CMD Window - to ssh (or telnet) into ubuntu I get 
**Connection Refused**

I can ping from each of the 3 machines to the others. I can access both of the Windows machines from Ubuntu, in each case using RDP and vnc.

Using Webmin I can access the Ubuntu machine from itself and from both of the remotes with no problems.

In everything I'm doing I'm using IP addresses instead of hostnames.

FWIW, I tried to install freenx server, but hit a wall during the configuration(that is one nasty task). The Windows freenx client installed without any problems.

And... I installed vino, but can't figure out how to launch it. After installing (and even rebooting), there is no vino service running. There's no executable file in any of the /bin directories. There are vino-passwd and vino-preferences, but nothing to launch vino itself.

I need help troubleshooting these **Failed To Connect To Server** and  **Connection Refused** errors. If there's something besides VNC, I'm open to suggestions.

Note: I'm not interested in debating the merits of one protocol over another. All I want to do is get *something* to work. Plus, I outgrew flame wars years ago.

I appreciate any help you can give.

---

### Post by snorkytheweasel on 2011-02-19
Added info: I tried the Windows SSVNC client. It's more verbose than other vnc clients. It showed, in sequential windows, 
[B]Access granted 
Connection Established
Opened Channel for Session
Connection Closed[/B]

> **snorkytheweasel said:**
> I have two Windows XP computers and one Linux computer. The Linux box is running Maverick Meercat server with a gnome desktop. I'm having a problem connecting from Windows to Ubuntu.

The usual way to do this is to use VNC. I've set up and used various flavors of VNC for years, without problems.... until now. 

On this Ubuntu box I've tried vnc, tightvnc, x11vnc, xtightvnc, xvnc - all in various combinations of ports and protocols. I've ensured that each those configurations matches on each end of the communication. All of that said, whenever I try to connect from Windows to Ubuntu I get the same error:
**Failed To Connect To Server**.

When I use Putty - or a Windows CMD Window - to ssh (or telnet) into ubuntu I get 
**Connection Refused**

I can ping from each of the 3 machines to the others. I can access both of the Windows machines from Ubuntu, in each case using RDP and vnc.

Using Webmin I can access the Ubuntu machine from itself and from both of the remotes with no problems.

In everything I'm doing I'm using IP addresses instead of hostnames.

FWIW, I tried to install freenx server, but hit a wall during the configuration(that is one nasty task). The Windows freenx client installed without any problems.

And... I installed vino, but can't figure out how to launch it. After installing (and even rebooting), there is no vino service running. There's no executable file in any of the /bin directories. There are vino-passwd and vino-preferences, but nothing to launch vino itself.

I need help troubleshooting these **Failed To Connect To Server** and  **Connection Refused** errors. If there's something besides VNC, I'm open to suggestions.

Note: I'm not interested in debating the merits of one protocol over another. All I want to do is get *something* to work. Plus, I outgrew flame wars years ago.

I appreciate any help you can give.

---

### Post by krunge on 2011-02-19
Is there a firewall blocking access?  You can check the system/firewall logs.

Does "netstat -antpe" show the vnc server process listening on a port? (the port number is usually in the range 5900-5910)

(Then) What happens if you telnet(1) to that port from a different machine?

In the case of x11vnc, collect the log in a file (-o option) then try connecting to its port via one or more VNC viewers and also telnet(1).  Attach the full output to this thread or send to me as pm and I will have a look at it.  Also attach vncviewer and telnet messages.

---

### Post by snorkytheweasel on 2011-02-20
Is there a firewall blocking access?  You can check the system/firewall logs.

**iptables (ufw) disabled (and rebooted to make sure).**

Does "netstat -antpe" show the vnc server process listening on a port? (the port number is usually in the range 5900-5910)

```
snorky@ubuntu-srv-1010:~$ netstat -antpe
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      1000       11787       1635/vino-server
tcp6       0      0 :::5900                 :::*                    LISTEN      1000       11786       1635/vino-server

```
[B]Note: after reboot, vino runs and x11vnc doesn't. Go figure.
[/B]

(Then) What happens if you telnet(1) to that port from a different machine?

**RFB 003.007 - eventually returns **
```
Connection to host lost.
```

In the case of x11vnc, collect the log in a file (-o option) then try connecting to its port via one or more VNC viewers and also telnet(1).  Attach the full output to this thread or send to me as pm and I will have a look at it.  Also attach vncviewer and telnet messages.[/QUOTE]
[B]
since vino is running and x11vnc is not running, here is vino.log:[/B]
```

20/02/2011 07:50:32 PM Autoprobing TCP port in (all) network interface
20/02/2011 07:50:32 PM Listening IPv6://[::]:5900
20/02/2011 07:50:32 PM Listening IPv4://0.0.0.0:5900
20/02/2011 07:50:32 PM Autoprobing selected port 5900
20/02/2011 07:50:32 PM Advertising security type: 'TLS' (18)
20/02/2011 07:50:32 PM Advertising authentication type: 'No Authentication' (1)
20/02/2011 07:50:32 PM Advertising security type: 'No Authentication' (1)
20/02/2011 07:53:04 PM [IPv4] Got connection from client 10.4.23.66
20/02/2011 07:53:04 PM   other clients:
20/02/2011 07:54:33 PM rfbProcessClientProtocolVersion: read: Connection timed out
20/02/2011 07:54:33 PM Client 10.4.23.66 gone
20/02/2011 07:54:33 PM Statistics:
20/02/2011 07:54:33 PM   framebuffer updates 0, rectangles 0, bytes 0
```
[B]
VNCviewer message is the same as always: [/B]
```
Failed to connect to server
```

---

### Post by krunge on 2011-02-21
Well, I can help you with x11vnc but not vino.

You can run x11vnc with "-rfbport 5901" to make him use a different port since vino is already using 5900.  Then connect your vnc viewer to vnc display :1 instead of :0 and see what happens.

---

### Post by snorkytheweasel on 2011-02-22
I uninstalled vino and reinstalled x11vncserver.

If I launch x11vncserver from the command line 
```
x11vnc -rfbport 5901 
```
it appears to work. That is to say, 
[LIST=1]
[*]it returns **PORT=5901** 
[*]there are no error messages
[*]a process is launched, i.e.,
```
ps -A | grep vnc 
```
returns
```
16444 ?        00:00:00 x11vnc
```
[/LIST]

However, when connecting from the windows vncclient using
```
vncviewer 10.4.23.69:5901
```
I get my nemesis, that all-to-frequent error,  
```
Failed to connect to server
```

If I launch x11vnxserver from the main menu (command installed by apt-get install) ... the command is 
```
x11vnc -gui tray=setpass -rfbport PROMPT -bg -o %%HOME/.x11vnc.log.%%VNCDISPLAY 
```
I get this error (on the ubuntu vncserver):
```
tail: cannot watch `/tmp/x11vnc.tray.sJo83D': No such file or directory
tail: cannot watch `/tmp/x11vnc.tray.sJo83D': No such file or directory
    while executing
"close $channel"
    (procedure "read_client_info" line 25)
    invoked from within
"read_client_info $client_tail"
    (procedure "read_client_tail" line 5)
    invoked from within
"read_client_tail"
```

Actually, I get variants of that error dialog in which "sJo83D" changes to a different seemingly random string AND the listening port increments by 1, i.e., 5901 increments to 5902 the next time I launch, then 5903, then 5904, and so on. And each launches a new process, which I kill before trying anything else.

---

### Post by gigaferz on 2011-02-22
hey, forget about that, 
im using teamviewer for local and remote support
i used to use reverse vnc (ultravnc and x11vnc)
not anymore no port configuration needed (so far)

---

### Post by krunge on 2011-02-22
> However, when connecting from the windows vncclient using
```
vncviewer 10.4.23.69:5901
```I get my nemesis, that all-to-frequent error,  
```
Failed to connect to server
```
It should be:
```
vncviewer 10.4.23.69:1
```

---

### Post by snorkytheweasel on 2011-02-23
Same result .... "Failed to connect to server" .... <sigh> ....

---

### Post by snorkytheweasel on 2011-02-23
> **gigaferz said:**
> hey, forget about that, 
im using teamviewer for local and remote support
i used to use reverse vnc (ultravnc and x11vnc)
not anymore no port configuration needed (so far)

If I recall correctly, teamviewer's connections are made through teamviewer's remote server. If my age-addled brain does recall correctly, then that means each packet goes from my remote through my gateway & router to my ISP to who-knows-how-many-hops to teamviewer's server, and then back through all those intermediate steps ... hops, ISP, router, gateway to my server ... ad nauseum.

That's OK as an ad hoc VPN tunnel, but it seems to be a bit much for day-in-day-out use over a local network.

OTOH, I've made a career out of being wrong.

Your move...  

:D :D :D

---

### Post by krunge on 2011-02-23
> **snorkytheweasel said:**
> Same result .... "Failed to connect to server" .... <sigh> ....
I can't believe you are having so much trouble.  I wish I had access to your machines, I'd have it all figured out in 2 mins.

---

### Post by gordintoronto on 2011-02-23
"vncviewer 10.4.23.69:5901"

I would have expected an IP address such as 192.168.1.102, but perhaps I don't understand how your network is configured.

---

### Post by gigaferz on 2011-02-23
why dont you reinstall, looks to me you made a mess and there is no way to track all the changes youve done so far. well, and at least with teamviwer you would be getting things done by now.

if you installed properly it shouldnt be a big deal.

note aside, im trying to forward x11 to my win pc , and i know theres waay too many other options, im doing it because i want to learn.

---

### Post by snorkytheweasel on 2011-02-24
> **gordintoronto said:**
> "vncviewer 10.4.23.69:5901"

I would have expected an IP address such as 192.168.1.102, but perhaps I don't understand how your network is configured.

The block of 192.168.xxx.xxx is reserved for internal networks. Likewise, the following are reserved for internal networks: 
10.xxx.xxx.xxx
127.xxx.xxx.xxx (special case - google "loopback" + "network")
169.254.xxx.xxx
172.16.0.0 - 172.31.255.255
192.168.xxx.xxx

There might be others, but it's been so long since I took the exam, and I don't remember things I don't have to remember (I'm surprised that I could recall the 172 series).

I use 10.xxx.xxx.xxx for commercial networks that I set up & manage, just in case I need more than 64000 nodes.:rolleyes:

In the case of my home network, some of the octets have a special meaning for me. The 2nd octet had to be "4", and the 10 series was the only one that would work as xxx.4.xxx.xxx 

In most normal internal networks 192.168.xxx.xxx works just fine, but I've never been accused of being normal.

---

### Post by snorkytheweasel on 2011-02-24
> **gigaferz said:**
> why dont you reinstall, looks to me you made a mess and there is no way to track all the changes youve done so far. well, and at least with teamviwer you would be getting things done by now.

if you installed properly it shouldnt be a big deal.

note aside, im trying to forward x11 to my win pc , and i know theres waay too many other options, im doing it because i want to learn.

For now I'm using Teamviewer. Thanks for the tip.

---

### Post by Mark M. on 2011-07-05
FWIW, I ran into this problem (almost identical error message) when installing X11VNC and starting it on Ubuntu 9.10 with Xfce Desktop installed.

I removed the application, re-installed and changed the port back to 5900 (for some reason, it had kicked over to port 5902).  This seems to have done the trick and I've been able to remote into my box.

---

### Post by francisv@comcast.net on 2011-10-05
I'm in agreement that I shouldn't have to resort to Team Player just to have VNC on my LAN and have also had no success getting any of the versions of VNC to run.
(with the exception of Gitso which is supposed to be using xtightVNC but I think is going
thru Google to run. Just downloaded the code for it last night and will take a look.

The Ubuntu favoured X11VNC server produces:

tail: cannot watch `/tmp/x11vnc.tray.JeYrNc': No such file or directory
tail: cannot watch `/tmp/x11vnc.tray.JeYrNc': No such file or directory
    while executing
"close $channel"
    (procedure "read_client_info" line 25)
    invoked from within
"read_client_info $client_tail"
    (procedure "read_client_tail" line 5)
    invoked from within
"read_client_tail"

It does appear to be running but no other machine can connect to it.

tcp        0      0 127.0.0.1:57222         127.0.0.1:13037         ESTABLISHED 1000       15784       2029/x11vnc     

I've turned UFW off for testing, my router firewall does not impede LAN traffic, removed and reloaded X11VNC Server and tried numerous command line variants but still can't get a working VNC server or even viewer -listen to work. The best I can get is for a viewer to report "connecting" but no window ever opens and it times out.

After spending days trying Real VNC , TightVNC without Gitso, X11VNC, and multiple
viewers and configurations I'm pretty frustrated. It looks from this error message that
the start up script may be wrong since /tmp.. should be root and I don't think the application has permissons to write to it so the install didn't go correctly or x11vnc.tray gets written on startup . Just guessing but .."/tmp/x11vnc.tray.JeYrNc': No such file or directory" does not exist probably because /temp is owned by root:root.

I'm still going to spend some time trying to figure this out but wow.. what a lot of time
to do something that use to be relatively simple.  Seems to go against using a third party
.deb to resolve a need.

---

