---
title: "Forward SMB over SSH"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by bforbes on 2009-12-20
I want to forward SMB from my local Linux box over a SSH tunnel to a Windows XP machine behind a firewall. Everything I try just times out.

Here's the first thing I tried:
ssh -L 2222:WINDOWSMACHINE:139 USER@FIREWALL_SERVER

Then I attempted:
smbclient //WINDOWSMACHINE/SHARENAME/ -U USER -I 127.0.0.1 -p 2222

It timed out with this message:
> 
Receiving SMB: Server stopped responding
session request to WINDOWSMACHINE failed (Call timed out: server did not respond after 20000 milliseconds)
Receiving SMB: Server stopped responding
session request to *SMBSERVER failed (Call timed out: server did not respond after 20000 milliseconds)

In the terminal where the ssh tunnel command was executed, after a while I see messages like this:
> 
channel 3: open failed: connect failed: Connection timed out

In verbose mode ssh says this:
> 
debug1: Connection to port 2222 forwarding to pazuzu port 139 requested.
debug2: fd 9 setting TCP_NODELAY
debug2: fd 9 setting O_NONBLOCK
debug3: fd 9 is O_NONBLOCK
debug1: channel 3: new [direct-tcpip]
debug1: Connection to port 2222 forwarding to pazuzu port 139 requested.
debug2: fd 10 setting TCP_NODELAY
debug2: fd 10 setting O_NONBLOCK
debug3: fd 10 is O_NONBLOCK
debug1: channel 4: new [direct-tcpip]


I also tried:
sudo ssh -L 139:WINDOWSMACHINE:139 -L 445:WINDOWSMACHINE:445 USER@FIREWALL_SERVER

But no luck.

I have confirmed that smbclient can access that share from another linux box behind the firewall.

---

### Post by Lars Noodén on 2009-12-20
Have you enabled port forwarding in the server's configuration, /etc/ssh/sshd_config ?  Check that file or try forwarding to another service that you know works to verify that forwarding is working at all before looking further.

---

### Post by bforbes on 2009-12-20
Thanks for the suggestion. Yes, I can forward fine with other protocols. I checked that config file; TCP forwarding is enabled and there doesn't appear to be any exceptions in there that would affect this issue.

Any other ideas?

---

### Post by bforbes on 2009-12-26
bump

---

### Post by Irregular Joe on 2010-01-22
sshfs is the utility to install to get access to files (not just Samba mounts) over ssh.  

I found the documentation here:
  [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

Very simple and straightforward, and nothing to install on the remote machine (if it is running an ssh server).  I had it working in 2 minutes!

---

