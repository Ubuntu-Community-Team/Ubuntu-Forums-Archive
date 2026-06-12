---
title: "can ping through firewire interface, but cant ssh"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by erjoalgo on 2010-07-12
These are the steps I've taken:
```

sudo modprobe eth1394
sudo ifconfig eth1 123.123.123.1 netmask 255.255.255.0 up 

```After doing this in the other box (with different ip), the 2 can ping each other.
```
user@desktop:~$ ping -c 3 123.123.123
PING 123.123.123.3 (123.123.123.3) 56(84) bytes of
64 bytes from 123.123.123.3: icmp_seq=1 ttl=64 tim
64 bytes from 123.123.123.3: icmp_seq=2 ttl=64 tim
64 bytes from 123.123.123.3: icmp_seq=3 ttl=64 tim

--- 123.123.123.3 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss,
rtt min/avg/max/mdev = 0.260/0.292/0.324/0.032 ms

```But ssh connection times out:
```

user@desktop:~$ ssh 123.123.123.3
ssh: connect to host 123.123.123.3 port 22: Connection timed out 

```Samba doesnt work either.
As suggested in [this]("http://ubuntuforums.org/showthread.php?t=965249") thread, I tried adding each of these lines to the file, /etc/samba/smb.conf
```

interfaces eth0 lo eth1
;interfaces eth0 lo eth1 123.123.123.3
;interfaces eth0 lo eth1 123.123.123.3 255.255.255.0
 
```Then
sudo smbcontrol smbd reload-config
And nothing. If pinging works, then I SHOULD be able to transfer  files, what am I missing?

---

### Post by sedawk on 2010-07-12
First step would be to debug the services are available
locally, e.g. try
```

ssh localhost

```

You can also test samba locally using the smbclient tool.

If stuff works locally you can try to use it over the
network. For generic debugging of network problems (e.g.
do packages arrive on the server) you can use wireshark
or tcpdump. If packages are properly travelling through
the network it is time for debugging the protocols themselves.

---

### Post by erjoalgo on 2010-07-14
ssh works fine. samba works fine, everything works fine under a different network interface. There seems to be something blocking this eth1394 interface. 
Pinging works, no errors, dropped packets or anything.

I appreciate your response but I have no idea even where to start to "debug the protocol", I am a noob and this would take me way too long, maybe someone else had this problem and can help? Any other ideas?

---

### Post by erjoalgo on 2010-07-15
bump it up

---

### Post by erjoalgo on 2010-07-16
damn it, how do I never get help from this forum?

---

### Post by Azyx on 2011-06-01
How did you get eth1394 to work? What did you unblacklist in /etc/modprobe.d/ ?

Cheers

---

