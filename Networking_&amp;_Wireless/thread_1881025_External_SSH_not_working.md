---
title: "External SSH not working"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by kaspar_silas on 2011-11-14
Erm bit baffled maybe someone can see what I am missing. 

I use ssh to log into my home computer from work. When I upgraded to 11.10 I seem to have lost this functionality.

I can ssh in from within my home network 
eg: 
 ssh [myname]@[localhost]
or:
 ssh [myname]@[LAN-ip]

however if I google and get my external ip:
and do:
 ssh [myname]@[my-true-ip]

it gives no response. If I debug it just hangs at
debug1: Connecting to [my-ip] ["[my-ip]"]

now if I boot up in my old 10.04 
and repeat the above I can log in as normal
which somewhat suggests to me it's not the router.


But if I can log on locally and the router
is port forwarding okay then I am sort of
lost as to what to check next.


Did 11.10 maybe add some sort of 
"block ssh response from sources outside the LAN option" 
somewhere? 

Any hints greatly appreciated

---

### Post by RedSingularity on 2011-11-15
Can you attach some terminal output here in the forums when I ask for it?  Do you have a GUI installed with a browser on the ssh server is what I am getting at :)?

---

### Post by kaspar_silas on 2011-11-15
"Can you attach some terminal output here in the forums when I ask for it? Do you have a GUI installed with a browser on the ssh server is what I am getting at ?"

Yip what output do you want?

---

### Post by RedSingularity on 2011-11-15
Lol.  I forgot what I was going to ask.  Well how about the port number in the application itself?  Is ssh configured for the default port 22 on the server under the 11.10 install?

---

### Post by jonobr on 2011-11-16
Hi there

Just curious, when you run 
When this is not working , if you go to the target machine and run
```
sudo tcpdump -vvv -s 1600 -i any port 22
```
and then ssh
Do you see anything?

Im thinking you will and there is something else going on, but no harm checking your packets are getting there in the first place

Ciao!

---

### Post by boast on 2011-11-16
maybe the config for your sshd changed, and it now only listens to local address ranges?

---

### Post by kaspar_silas on 2011-11-17
Hi Cheers for the responses,

I open two ports (22 and 7800) and going through both is fine locally. Only the latter is port forwarded on the router. When I try to connect externally I am using 7800 and your quite right that 22 would not and never did work.

I next tried the (very useful to know) screen dumping command and whilst all is well locally there is no response when the ssh is external as you might expect from the ssh debug line.   

So finally the suggestion that the config for my sshd changed so it now only listens to local. This seems a distinct possibility but browsing /etc/ssh/sshd_config reveals it to be the standard release (barring the port addition) with no obvious issue. 

If someone with an externally accessible working ssh could compare with their config I'd be very thankful 

Note: I removed comment lines 
```

Port 22
Port 7800
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication no
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes
AllowUsers [myname]

```

---

### Post by kaspar_silas on 2011-11-17
Hurray!!!

I discovered a new firewall had been installed namely ufw.
Popped in the applicable exceptions and voila I can connect externally!

Strangely I don't seem to be able to actually connect 
from the LAN through the web back to the LAN ie:
ssh -p7800 [myname]@[external-ip]
I suspect this looping back is blocked possibly as a security feature. Anyway there is no reason to do this so I guess I can ignore the minor mystery.

Thanks for the help.

---

### Post by CharlesA on 2011-11-17
Most routers don't support NAT redirection, so that's normal.

---

