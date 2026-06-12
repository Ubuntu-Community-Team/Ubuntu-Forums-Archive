---
title: "samba / smbd / apache / port scanning?"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by vik_2010 on 2010-11-21
Hey guys. Quick question:

I was trying to learn a little about samba, and I ran into this discrepancy that I hope someone can clarify.

I was trying to scan the ports programs are listening on on my computer, and nmap printed this:

[PHP]
name@host: ~$ nmap 127.0.0.1

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-21 00:17 PST
Interesting ports on localhost (127.0.0.1):
Not shown: 992 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
587/tcp  open  submission
631/tcp  open  ipp
6667/tcp open  irc
[/PHP]A number of things ran through my mind when I saw this:

1)  I installed apache a short while ago, but I thought I shut down the server. Does it start up automatically after a reboot? Other than nmap, how else could I have known this. I'm assuming its running right now.

2) By default, do I have to restart smbd after every reboot to get a samba server working? According to this list, I don't have a smbd instance running. However, if I run
[PHP]pidof smbd[/PHP]I get 
[PHP]1182  1151[/PHP],
which correlates (in part), with the contents of /var/run/samba/smbd.pid, which is just:

[PHP]1151[/PHP].

How come nmap doesn't show a running instance of smbd, but pidof does?

Best,

-Vikram

---

### Post by spiky001 on 2010-11-21
They are on local network what happens if you scan external ip [http://nmap-online.com/](http://nmap-online.com/)

---

### Post by vik_2010 on 2010-11-21
I'm not sure what you mean.

I ran:

[PHP]nmap nmap-online.com[/PHP]

and got:

[PHP]Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-21 01:01 PST
Interesting ports on n1nlhg30c055.shr.prod.ams1.secureserver.net (188.121.47.1):
Not shown: 987 filtered ports
PORT      STATE  SERVICE
22/tcp    open   ssh
80/tcp    open   http
443/tcp   open   https
50000/tcp closed iiimsf
50001/tcp closed unknown
50002/tcp closed iiimsf
50003/tcp closed unknown
50006/tcp closed unknown
50300/tcp closed unknown
50389/tcp closed unknown
50500/tcp closed unknown
50636/tcp closed unknown
50800/tcp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 11.66 seconds
[/PHP]

What does that tell you?

---

### Post by vik_2010 on 2010-11-21
Alright:

nmap mos def isn't printing a full list of servers on my box.

When  I start a gimp server instance on port 10008, nothing shows:
[PHP]
vikram@vikram-laptop:~$ nmap 127.0.0.1

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-21 01:18 PST
Interesting ports on localhost (127.0.0.1):
Not shown: 993 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
587/tcp  open  submission
631/tcp  open  ipp
6667/tcp open  irc
[/PHP]

HOWEVER, if I try to scan only ports within an interval overlapping with my POI (port of interest), I get it.

[PHP]
vikram@vikram-laptop:~$ nmap 127.0.0.1 -p 10000-10010

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-21 01:20 PST
Interesting ports on localhost (127.0.0.1):
PORT      STATE  SERVICE
10000/tcp closed snet-sensor-mgmt
10001/tcp closed unknown
10002/tcp closed unknown
10003/tcp closed unknown
10004/tcp closed unknown
10005/tcp closed stel
10006/tcp closed unknown
10007/tcp closed unknown
10008/tcp open   unknown
10009/tcp closed unknown
10010/tcp closed unknown
[/PHP]

Two things I thought are interesting:

1) Nmap doesn't recognize the name of the service 
2) You don't have to be root to set up the gimp server. I thought you had to be to do that! Maybe the server functions normally under restricted privileges, and can handle a non-root startup, but services like apache have to be root to operate?

---

### Post by spiky001 on 2010-11-21
The 3 ports that were open are the 1,s visible to the internet because you used outside source when you use nmap on 127 that the local lan, you can block them with a firewall if you dont need them I,m not great at all the ports just learning hope i have shed some light on this, [http://www.techimo.com/forum/security-privacy-issues/154521-ports-80-443-open.html](http://www.techimo.com/forum/security-privacy-issues/154521-ports-80-443-open.html)
that explains port 80/443 port 22 is ssh

---

### Post by vik_2010 on 2010-11-21
Lol,

is this a joke? nmap only scans ports less than 10005. Here is the output when I start a bunch of gimp servers from ports 9998 to 10005:
[PHP]Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-21 01:35 PST
Interesting ports on localhost (127.0.0.1):
Not shown: 987 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
587/tcp   open  submission
631/tcp   open  ipp
6667/tcp  open  irc
9998/tcp  open  unknown
9999/tcp  open  abyss
10000/tcp open  snet-sensor-mgmt
10002/tcp open  unknown
10003/tcp open  unknown
10004/tcp open  unknown
 [/PHP]

I don't know if calling the service "abyss" at port 9999 is a joke or just an app failure.

---

### Post by spiky001 on 2010-11-21
abyss webserver, you can google all the port numbers [http://www.google.co.uk/#hl=en&source=hp&biw=1254&bih=659&q=port+9999+abyss&aq=1&aqi=g4g-m4&aql=&oq=port+9999&gs_rfai=&pbx=1&fp=917f5e54d6136359](http://www.google.co.uk/#hl=en&source=hp&biw=1254&bih=659&q=port+9999+abyss&aq=1&aqi=g4g-m4&aql=&oq=port+9999&gs_rfai=&pbx=1&fp=917f5e54d6136359)

---

### Post by bashologist on 2010-11-21
I was once wondering what kinda networking stuff was going on too and found this great thread.
[http://ubuntuforums.org/showthread.php?t=1614853](http://ubuntuforums.org/showthread.php?t=1614853)

For example one of the commands in that thread is this.
```

sudo lsof -i -n -P

```

---

### Post by vik_2010 on 2010-11-21
ah ic

---

### Post by SeijiSensei on 2010-11-21
Since no one answered the original question, I will.  smbd listens on TCP port 139 and provides the "netbios-ssn" service.  Neither "Samba" nor "SMB" are themselves the protocol involved; it's something called [NetBIOS]("http://en.wikipedia.org/wiki/NetBIOS_over_TCP/IP").

By default, nmap doesn't scan every one of the 65,000+ ports on a target computer.  Instead it scans about a thousand of the most commonly-used ports.  If you want it to scan every port on a machine use the '-p 1-65535' option in the command.

Scanning localhost doesn't tell you whether services are visible outside the box itself.  Many services are bound to localhost by default so they are available for use by programs running on the server but not visible to someone outside.  If you want to see what outsiders can view, you need to scan from another machine outside your network, or use a service like nmap-online mentioned above.

Finally, the names nmap assigns to various ports are based on lists of services.  I don't believe nmap looks for "signatures" on every port it scans.  There's a list of "official" service assignments in the file /etc/services which comes on every Linux computer.  nmap uses an expanded list that includes things like well-known trojan programs that attach to particular ports.  That list is stored as /usr/share/nmap/nmap-services.

---

