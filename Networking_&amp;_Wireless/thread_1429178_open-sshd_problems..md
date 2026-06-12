---
title: "open-sshd problems."
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by adro on 2010-03-13
I am running ubuntu in sun virtual box. Everything works pretty well except I am unable to connect via ssh from anywhere besides ubuntu terminal. I cant ssh in from the win7 host machine nor an outside shell i have. Its a connection refused. Ive tried ssh localhost. doesnt work. Ive tried. ssh 192.168.1.100 from the host machine doesnt work. "connection refused" ive tried ssh from outside shell to "machinename.housemartin.org" which i have dnsed. and still get connection refused. Im sure that i have ports forward correctly in the router because ircd is working fine on the host win7 and recieves connections to machinename.housemartin.org and i have port 22 forwarded the same way as i have 6667 
does anyone have any idea what the problem is? does the guest ubuntu machine possibly grab a different router ip than does the host machine? if it does how could i find out.

appreciate any help.
adrian

---

### Post by Iowan on 2010-03-14
I'm not familiar with virtual boxes yet, so I'm not sure if **ifconfig -a** would help...
Probably silly question - but you DID install the SSH server?

---

### Post by adro on 2010-03-16
yea openssh is installed and running. i can ssh from term just no where else

---

