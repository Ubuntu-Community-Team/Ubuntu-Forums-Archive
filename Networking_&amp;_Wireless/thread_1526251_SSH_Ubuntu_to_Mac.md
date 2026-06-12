---
title: "SSH Ubuntu to Mac"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by adamlogan on 2010-07-07
I've been using ssh for a month or two, but I'm stepping up to public keys. Today I was finally able to get a public key working from my mac book pro /w snow leopard at work to my ibm thinkpad /w Ubuntu, but I can't seem to go the other way. I checked the port of my mbp and it is open. 

I think it's something with the configs. There are many configs on the client and the server and I didn't really get it until after all my fussing around today in them trying to get this working. I edited the system wide sshd_configs before coming to realize I should have made a user ssh config in .ssh for everything and left the system wide stuff alone with factory defaults. So now I just want to start with clean server configs on the mac (probably a good idea to do it on Ubuntu too) and start over this time going through the man ssh_config pages.

Regardless I'm suprised I have not been able to connect I've disabled many security features I felt might get in the way =/. Not certain but it might have something to do with the version of the mac ssh server? Makes me want to just substitute apple's implementation with the portable openssh package. It's really messing up with the head to be comparing something like sshd_config between Ubuntu and what is on Snow Leopard.

Anyways here's the verbose output of trying to connect. Note I changed the actual user name & ip address.

One consistent thing is I have not been able to overcome the "ssh_connect: needpriv 0" error.

Before I forget I also consistently get an error connecting to my ibm from my mac, it says something along the lines of "Tunnel could not be established" or something like that. I don't get it cuz I'm looking at my prompt immediately after that error and I'm logged in to the ibm.

```
user@ibm:~$ ssh -vvv macaddress.dyndns.org
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug3: cipher ok: aes128-ctr [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: aes192-ctr [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: aes256-ctr [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: arcfour256 [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: arcfour128 [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: aes128-cbc [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: 3des-cbc [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: ciphers ok: [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug2: mac_setup: found hmac-md5
debug3: mac ok: hmac-md5 [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: mac_setup: found hmac-sha1
debug3: mac ok: hmac-sha1 [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: mac_setup: found umac-64@openssh.com
debug3: mac ok: umac-64@openssh.com [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: mac_setup: found hmac-ripemd160
debug3: mac ok: hmac-ripemd160 [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug3: macs ok: [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: ssh_connect: needpriv 0
debug1: Connecting to macaddress.dyndns.org [69.95.227.19] port 22.
debug1: connect to address 69.95.227.19 port 22: Connection refused
ssh: connect to host macaddress.dyndns.org port 22: Connection refused
```

I guess I really should just wipe the slate clean and start over huh. Would appreciate constructive feedback if you guys know anything about the needpriv 0 error.

---

### Post by kfinity on 2010-07-08
Um... usually if public key authentication fails, it'll say something about it. "Connection refused" sounds more like the port is simply closed somewhere along the line (either dyndns isn't forwarding, or the mac's firewall is running, or something).

If you have nmap installed, you can check pretty quickly with "nmap macaddress.dyndns.org". It should come back with at least "22/tcp open ssh".

p.s. fyi, on my computer, debug2 still says "needpriv 0" even when it connects just fine.

---

### Post by adamlogan on 2010-07-08
@ kfinity

Thanks for mentioning nmap, never used it before; what a great utility! Output does not mention port 22 anywhere. I think I've read somewhere that is that even on a heavily blocked network port 443 is usually open. I guess I should change the ssh port to 433 on the mac then. The mail.workplace.org bit is weird.

```
user@ibm:~$ nmap mac.dyndns.org

Starting Nmap 5.00 ( http://nmap.org ) at 2010-07-08 08:47 EDT
Interesting ports on mail.workplace.org (mac ip):
Not shown: 993 closed ports
PORT      STATE    SERVICE
25/tcp    open     smtp
80/tcp    open     http
139/tcp   filtered netbios-ssn
443/tcp   open     https
1434/tcp  filtered ms-sql-m
12345/tcp filtered netbus
31337/tcp filtered Elite

Nmap done: 1 IP address (1 host up) scanned in 5.67 seconds

```

---

