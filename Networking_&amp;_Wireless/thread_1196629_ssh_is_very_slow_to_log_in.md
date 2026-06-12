---
title: "ssh is very slow to log in"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by tjansson on 2009-06-25
I have a setup of several servers with one master server running a NIS and the clients are authenticated through LDAP running on another server. The main server is also the VNC head through which I connect. When I wish to on a terminal on another server I usual run something like the command:

```

ssh remoteserver "xterm -display vncserver:25 -ls"

```

The problem is that it takes around 0:45-1:30 minutes for the connection to be established. Once it is established it is very responsive. 

**PING**
When I try to ping the remoteserver it responds as quickly as I would expect. 
```

--- remoteserver ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9019ms
rtt min/avg/max/mdev = 0.154/0.188/0.205/0.018 ms, pipe 2

```

**SPEED**
There is also no problem with speed once the connection is established:
```

scp foo.tar remoteserver:/home/tjansson/foo.tar
tjansson@remoteserver's password: 
foo.tar        100%   10MB  16.1MB/s   00:00

```

**DNS**
I tried to run 
```

ssh remoteserver

```
and
```

ssh 192.168.1.52

```
and the results are the same, so do not think it is DNS related. 

**SSH debug**
```

ssh -vvv remoteserver

```
shows nothing unusual but hangs at two places:
```

tjansson@remoteserver's password: 
debug3: packet_send2: adding 48 (len 63 padlen 17 extra_pad 64)
debug2: we sent a password packet, wait for reply

```
it waits for here for around 15 seconds and followingly
```

tjansson@remoteserver's password: 
debug3: packet_send2: adding 48 (len 63 padlen 17 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.

```
it waits here for around 20 more seconds

traceroute shows only on hop and running "netstat -at" on the remote server didn't show anything strange. 

**Question**
Where and how would pursue this problem and does anybody experienced the same problem?

---

### Post by Divider on 2009-06-25
i've been noticing this too. 

Especially with puTTY.

Maybe i should apt-get upgrade :P

---

### Post by prshah on 2009-06-25
> **tjansson said:**
> 
The problem is that it takes around 0:45-1:30 minutes for the connection to be established. Once it is established it is very responsive. 


Have you tried disabling the "reverse" DNS lookup? Edit the /etc/ssh/sshd_config file and add (edit) the line ```
UseDNS  No
```

You will need to restart the ssh daemon for the change to take effect```
sudo /etc/init.d/ssh restart
``` Note the ssh daemon is "ssh" not "sshd"

---

