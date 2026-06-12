---
title: "sshd and hosts.allow"
date: 2012-11-22
forum: Networking &amp; Wireless
---

### Post by Statia on 2012-11-22
I am trying to make my lubuntu 12.10 box accessible from my phone.
sshd is run with inetd (openbsd-inetd  0.20091229-2ubuntu2) and uses tcpwrappers:

```
ssh     stream  tcp     nowait  root    /usr/bin/tcpd  sshd -i
```I have enabled my domain while on mobile data:

```
sshd: 192.168.178., .xs4all.nl, .kpn-gprs.nl
```(hosts.allow)

This does not let me in, I think because reverse DNS might not be set up by my provider. 
So:
```
echo 'UseDns no' >> /etc/ssh/sshd_config 
```sshd and inetd have been restarted, but I still can't get in:

```
Nov 22 14:27:55 possum sshd[8839]: warning: /etc/hosts.allow, line 14: can't verify hostname: getaddrinfo(host-62-133-64-14.kpn-gprs.nl, AF_INET) failed
Nov 22 14:27:55 possum sshd[8839]: refused connect from 62.133.64.14 (62.133.64.14)
```If I add the exact IP address of my mobile connection to hosts.allow I am able to connect. Connecting via the local network (192.168.178.x) also works.
Any ideas?
(And I just realise for the next step I need to import the keys to my phone, as password authentication has been disabled)

---

### Post by Lars Noodén on 2012-11-22
Shouldn't [hosts.allow](http://manpages.ubuntu.com/manpages/precise/en/man5/hosts.allow.5.html) be using * for the matching?

```

sshd: 192.168.178.*, *.xs4all.nl, *.kpn-gprs.nl

```

---

### Post by Statia on 2012-11-22
Not according to the manpage on my system, but I can give it a try.

> PATTERNS
       The  access  control  language  implements the following pat&#8208;
       terns:

       ·      A string that begins with a `.´ character. A host name
              is  matched  if  the last components of its name match
              the  specified  pattern.   For  example,  the  pattern
              `.tue.nl´ matches the host name `wzv.win.tue.nl´.

       ·      A  string  that  ends  with  a  `.´  character. A host
              address is matched if its first numeric  fields  match
              the given string.  For example, the pattern `131.155.´
              matches the address of  (almost)  every  host  on  the
              Eindhoven University network (131.155.x.x).


EDIT:
Scrolling further down I see wildcards may be used also, but I don't think there is a difference between .foo.com and *.foo.com.

---

### Post by Statia on 2012-11-27
This is strange. I had my NAS connected via Ethernet cable to a wireless bridge that connects (wireless obviously) to my router downstairs ([http://ubuntuforums.org/showthread.php?t=2058205](http://ubuntuforums.org/showthread.php?t=2058205)). Since this is slow (it's an old Linksys WRT54GL), I moved the NAS downstairs and connected it with one of the Gigabit ports on the router. Transfer speeds are 5 to 6 times faster now, but I can't connect by hostname any more:

```
statia@quokka:~$ ssh -Y possum
ssh_exchange_identification: Connection closed by remote host
statia@quokka:~$ ssh -Y 192.168.178.35
Lubuntu 12.10 on EEEPC 701
Enter passphrase for key '/home/statia/.ssh/id_rsa': 
Last login: Tue Nov 27 09:48:22 2012 from 192.168.178.31
```Might this be related to not getting in when connecting over GPRS?

---

### Post by Statia on 2012-11-27
OK, this is now in hosts.allow:

```
sshd: *.kpn.net, *.fritz.box, 192.168.178., *.xs4all.nl, *.kpn-gprs.nl
```

When I let inetd reread its configuration (kill -1 $PID), I see this in syslog:

```
Nov 27 11:19:01 possum inetd[4254]: ssh/tcp: bind: Address already in use
Nov 27 11:21:37 possum inetd[4254]: ssh/tcp: bind: Address already in use
Nov 27 11:25:03 possum inetd[4254]: ssh/tcp: bind: Address already in use
```

Maybe because I am connected via ssh?

Anyway, even with the asterisks no access from kpn-gprs.nl.
No access with hostname possum, only by IP.

---

### Post by efflandt on 2012-11-28
sshd normally runs as a daemon, so maybe also configuring it inetd is the reason for "bind: Address already in use" errors.

What resolves the "possum" name?  My 2wire modem/router uses local IP to set port forwarding, but uses MAC address to keep track of it in case IP changes, and same for manual name/IP entries for DNS.  My desktop, old laptop, and BluRay were using a Zyxel router configured as wireless client bridge.  After accessing the Zyxel router by name the modem/router that does DNS suddenly associated traffic from my desktop as Zyxel instead of the name I gave my IP, because it saw traffic from me as coming from the Zyxel MAC.  So now I use my desktop's wireless, I just need to have security key handy when installing a new Linux version.

 Maybe whatever resolved possum behind the wireless bridge cannot find it by that name directly on the main LAN because from the router point of view, its MAC address is now different.

BTW you could use:```
sshd: LOCAL, .xs4all.nl, .kpn-gprs.nl
```however, if sshd is using ipv6 that may throw a wrench into using ipv4 addresses in hosts.allow.  I gave up on that many years ago due to that issue and simply use keys only and **ALL: UNKNOWN** in hosts.deny so password crack attempts are futile, and nameless IPs are totally ignored for anything.

---

### Post by Statia on 2012-11-30
> **efflandt said:**
> 
BTW you could use:```
sshd: LOCAL, .xs4all.nl, .kpn-gprs.nl
```


If I use LOCAL, I can't get in at all. Reverted to 192.168.178.* and now at least I can connect from "inside" again,  but still not on GPRs. 
Any further ideas?

---

### Post by Statia on 2012-11-30
> **Statia said:**
> 

```
ssh     stream  tcp     nowait  root    /usr/bin/tcpd  sshd -i
```

Since Openssh is compiled with tcpwrappers, I think I don't have to call inetd / tcpd separately?

I could change this to:

```
ssh     stream  tcp     nowait  root    /usr/sbin/sshd -4

```Would that be correct?

(Added the -4 option to only allow IPv4, to not further complicate matters)

---

### Post by Lars Noodén on 2012-11-30
> **Statia said:**
> Since Openssh is compiled with tcpwrappers, I think I don't have to call inetd / tcpd separately?

I could change this to:

```
ssh     stream  tcp     nowait  root    /usr/sbin/sshd -4

```Would that be correct?

(Added the -4 option to only allow IPv4, to not further complicate matters)

You'd still need the [-i option](http://manpages.ubuntu.com/manpages/precise/en/man8/sshd.8.html) if it is being called by inetd or xinetd.

---

### Post by Statia on 2012-12-01
> **Lars Noodén said:**
> You'd still need the [-i option]("http://manpages.ubuntu.com/manpages/precise/en/man8/sshd.8.html") if it is being called by inetd or xinetd.

No. It works now :-)
I have all the access rules on separate lines, like this:

```
sshd: 192.168.178.* 
sshd: *.kpn.net
sshd: *.xs4all.nl
sshd: *.kpn-gprs.nl
sshd: xx.xxx.xx.xxx # specific IP that is allowed access

```And sshd is called only with -4, not with -i.

---

### Post by Lars Noodén on 2012-12-01
It will start up and run without the -i option, but with xinetd/inetd  it is more efficient to take advantage of -i.

---

### Post by Statia on 2012-12-03
I thought it worked, it doesn't.

So to recoup:

/etc/hosts.allow:

```
sshd: 192.168.178.* 
sshd: *.kpn.net
sshd: *.xs4all.nl
sshd: *.kpn-gprs.nl
sshd: xx.xxx.xx.xxx
```/etc/inetd.conf:

```
ssh     stream  tcp     nowait  root    /usr/sbin/sshd -4 -i
```/etc/ssh/sshd_config:

```

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no 

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no 


X11Forwarding yes
X11DisplayOffset 10
PrintMotd yes
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM no 
UseDns no

```What works:
- local logins
- external logins specified by IP

What does not work:
- pattern matching, i.e. letting me in while on *.kpn-gprs.nl or *.kpn.net:

```
Dec  3 14:58:59 possum sshd[22925]: warning: /etc/hosts.allow, line 14: can't verify hostname: getaddrinfo(static.kpn.net, AF_INET) failed
```So, back on square one. 
Who should I give the floor?

---

### Post by vasa1 on 2012-12-03
I don't know if this is relevant to this thread but here's something that indicates that hosts.allow and hosts.deny are "deprecated": [http://askubuntu.com/a/23225/25656](http://askubuntu.com/a/23225/25656)

---

### Post by Statia on 2012-12-03
> **vasa1 said:**
> I don't know if this is relevant to this thread but here's something that indicates that hosts.allow and hosts.deny are "deprecated": [http://askubuntu.com/a/23225/25656](http://askubuntu.com/a/23225/25656)

```
statia@quokka:~$ ldd `which sshd` | grep wrap
        libwrap.so.0 => /lib/x86_64-linux-gnu/libwrap.so.0 (0x00007f982b712000)
``````
statia@possum:/var/log$ ldd `which sshd` | grep wrap
        libwrap.so.0 => /lib/i386-linux-gnu/libwrap.so.0 (0xb76b1000)
```Sorry, no extra credits for vasa1 ;-)
Who wants to try next?

---

### Post by Lars Noodén on 2012-12-03
Shouldn't the hosts.allow entry be all on one line?

```

sshd: 192.168.178.*, *.kpn.net, *.xs4all.nl, *.kpn-gprs.nl, xx.xxx.xx.xxx

```

---

### Post by Statia on 2012-12-03
> **Lars Noodén said:**
> Shouldn't the hosts.allow entry be all on one line?


It looks like both work.
If I add a line with my exact IP while on GPRS, I can get in.
I got the idea of multiple lines from some other link posted here.

---

### Post by Statia on 2012-12-04
OK, I am really at my wits end. Thinking something went wrong with reverse DNS, I figured out the IP-ranges my provider uses and put them in hosts.allow, like so:

```
sshd: 192.168.178.* 
sshd: *.kpn.net
sshd: *.xs4all.nl
sshd: *.kpn-gprs.nl
sshd: 188.207.0.0/0.0.127.255 
sshd: 62.133.64.0/0.0.63.255
```Also tried with one line:

```
sshd: 192.168.178.* , 62.133.64.0/0.0.63.255
```After every modification sent a KILL -1 to inetd and did a "service ssh restart"

But still: 

```
Dec  4 09:55:59 possum sshd[29736]: warning: /etc/hosts.allow, line 14: can't verify hostname: getaddrinfo(host-62-133-64-23.kpn-gprs.nl, AF_INET) failed
Dec  4 09:55:59 possum sshd[29736]: refused connect from 62.133.64.23 (62.133.64.23)
```

---

### Post by Statia on 2012-12-04
Apparently sending inetd a SIGHUP and restarting sshd is not enough.
After a reboot it works.

Leaves me with the question: how should I reread hosts.allow after a change has been made?

---

### Post by Lars Noodén on 2012-12-04
> **Statia said:**
> Apparently sending inetd a SIGHUP and restarting sshd is not enough.
After a reboot it works.

Leaves me with the question: how should I reread hosts.allow after a change has been made?

That sounds like a bug.  For many services, SIGHUP is enough.

---

### Post by Statia on 2012-12-04
> **Lars Noodén said:**
> That sounds like a bug. 

That does not surprise me.
I am a living corollary to Murphy's Law:

If there is a bug _**I**_ will encounter it.

---

### Post by Statia on 2012-12-04
Something else is weird.
In syslog I see this:

```
Dec  4 11:19:59 possum inetd[1049]: ssh/tcp: bind: Address already in use
Dec  4 11:29:59 possum inetd[1049]: ssh/tcp: bind: Address already in use
Dec  4 11:39:59 possum inetd[1049]: ssh/tcp: bind: Address already in use
Dec  4 11:49:59 possum inetd[1049]: ssh/tcp: bind: Address already in use
Dec  4 11:59:59 possum inetd[1049]: ssh/tcp: bind: Address already in use
Dec  4 12:09:59 possum inetd[1049]: ssh/tcp: bind: Address already in use
Dec  4 12:17:01 possum CRON[2623]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  4 12:19:59 possum inetd[1049]: ssh/tcp: bind: Address already in use
Dec  4 12:29:59 possum inetd[1049]: ssh/tcp: bind: Address already in use
Dec  4 12:39:59 possum inetd[1049]: ssh/tcp: bind: Address already in use

```

Some cronjob restarting inetd every ten minutes?
How to find out which address is already in use and how to fix that?

---

### Post by Statia on 2012-12-04
And mark as unsolved again, just tried to get in and it does not work any more.

```
Dec  4 13:54:15 possum sshd[3872]: warning: /etc/hosts.allow, line 14: can't verify hostname: getaddrinfo(static.kpn.net, AF_INET) failed
Dec  4 13:54:15 possum sshd[3872]: refused connect from 188.207.102.154 (188.207.102.154)

```/etc/hosts.allow now looks like this:

```
sshd: 192.168.178.*,62.133.64.0/0.0.63.255,188.207.0.0/0.0.127.255,*.xs4all.nl
```

---

### Post by Statia on 2012-12-04
I really don't know what to make of this.
Sometimes it works, sometimes it doesn't.

```
Dec  4 15:34:04 possum sshd[1518]: Accepted publickey for statia from 62.133.64.10 port 60310 ssh2
Dec  4 15:34:31 possum sshd[1520]: Received disconnect from 62.133.64.10: 11: Closed due to user request.
```(This was after I had rebooted again to move /tmp to RAM, so unrelated to networking changes)

---

### Post by Statia on 2012-12-07
OK, so I was missing one more IP-range:  92.69.0.0 - 92.69.255.255
So I added
92.69.0.0/0.0.255.255 to hosts.allow.
kill -HUP inetd: still can't get in.
service ssh restart: still can't get in.
reboot: STILL CAN'T GET IN!

What is going on here?

---

### Post by digitec on 2012-12-08
sshd : 85.80.2.21 : allow
sshd : 80.28.5.2 : allow
sshd : 210.75.24.15 : allow
sshd : 20.67.59. : allow
sshd : 10.8. : allow
sshd : 108.70. : allow
sshd : 121.19. : allow
sshd : 229.4.25.81 : allow
sshd : ALL : deny

Above IP works for me fine however if I add some domain name but not IP than it simply does not work, looking how to do it since one of my server run dyndns.

I tried following add to host.allow one line containing file that carries your DYNDNS IP and the file contents generate by
nslookup as follow:

try 
nslookup yours.dyndns.org |grep "Address: "  | cut -c 10,11,12,13,14,15,16,17,18,19,20,21,22,23,24

do the CRON script - let's say "hhc" stored also into /etc folder

/etc/hhc

rm /etc/hhh.txt
nslookup yours.dyndns.org |grep "Address: "  | cut -c 10,11,12,13,14,15,16,17,18,19,20,21,22,23,24 >> /etc/hhh.txt

as a root make CRON run this script every hour

like:

crontab -e


add:

08  * * * * /etc/hhc 

and finally add the command into your file "hosts.allow"

.
.
sshd : 223.4.205.181 : allow
sshd : echo /etc/hhh.txt : allow
sshd : ALL : deny


it is simple and it works for me now ;-)

---

