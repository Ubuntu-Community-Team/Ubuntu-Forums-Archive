---
title: "can't ssh into new server using a password"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by t93ha07 on 2010-03-03
I am working on a 9.0.4 jaunty server.  I am trying to ssh into from another also linux on the same network. I am unable:

OpenSSH_5.2p1, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /root/.ssh/config
debug1: Applying options for *
debug1: Reading configuration data /usr/local/etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Executing proxy command: exec corkscrew nyproxy 80 172.29.36.255 22
debug1: permanently_drop_suid: 0
debug1: permanently_set_uid: 0/0
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /root/.ssh/id_rsa type 1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /root/.ssh/id_dsa type 2
ssh_exchange_identification: Connection closed by remote host

I am able to ssh on the box itself to other servers and itself.
I have password authentication set to 'yes' and the server is LISTENing to port :22.

I have restart the ssh daemon (/etc/init.d/ssh restart) many times and the machine itself.

I am using DHCP and getting the IP address from ifconfig eth0.

Any ideas?

---

### Post by Iowan on 2010-03-03
The BEGIN/END stuff (for key type) looks a bit ominous...
My SSH connection starts looking different at the line:> Executing proxy command:

---

### Post by t93ha07 on 2010-03-03
Any idea what could be causing that Begin/End stuff?

---

### Post by Iowan on 2010-03-03
Not quite sure how/why it becomes a problem, but the ssh_host_rsa_key and ssh_host_dsa_key files both begin/end with those lines - the .pub files do not...
Since I'm not using a proxy, I'm not sure what that line means...

---

### Post by t93ha07 on 2010-03-03
Thanks Dude.  That was info I needed.  I just tried ssh in from putty on my local PC and I got in. I think you are right with corkscrew or the proxy server being involved with my sshing from my OEL server.  

I consider this issue resolved.  Thanks so much!!!

---

### Post by Iowan on 2010-03-03
Wow... you're welcome... I guess :confused:
Glad it works - for whatever reason...

---

