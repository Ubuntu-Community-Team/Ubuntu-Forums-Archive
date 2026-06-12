---
title: "Unable to ssh out of my ubuntu laptop"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by ade4krist on 2012-11-01
On my Fijitsu system with intel processor, I could not ssh out from  my Ubuntu 12.04 partition.

The remote machine I was trying to access can be accessed using other desktop computers in my office except my laptop.

I have tried to follow several comments but none has worked for me.

Here below are the output of diagnostic commands:

..................
Here is the ouput of "dig sun.chpc.ac.za"

; <<>> DiG 9.8.1-P1 <<>> sun.chpc.ac.za

;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55409

;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:

;sun.chpc.ac.za. IN A

;; ANSWER SECTION:

sun.chpc.ac.za. 2598 IN A 196.24.44.62

;; Query time: 1 msec

;; SERVER: 127.0.0.1#53(127.0.0.1)

;; WHEN: Tue Oct 30 21:40:35 2012

;; MSG SIZE rcvd: 48

"nslookup sun.chpc.ac.za" Server: 127.0.0.1 Address: 127.0.0.1#53

Non-authoritative answer: Name: sun.chpc.ac.za Address: 196.24.44.62

...................

I stopped the Firewire and try to ssh, yet it still connection refused


....................
When I run: "nmap sun.chpc.ac.za"

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-10-30 22:24 SAST 

Nmap scan report for sun.chpc.ac.za (196.24.44.62) 

Host is up (0.0044s latency). 

Not shown: 998 closed ports 

PORT STATE SERVICE 

1863/tcp filtered msnp 

2000/tcp filtered cisco-sccp

Nmap done: 1 IP address (1 host up) scanned in 2.81 seconds

.........................
Here is the output of the coommand: ssh -vvv [email]user@sun.chpc.ac.za[/email]

OpenSSH_5.9p1 Debian-5ubuntu1, 

OpenSSL 1.0.1 14 Mar 2012

debug1: Reading configuration data /etc/ssh/ssh_config 

debug1: /etc/ssh/ssh_config line 19: Applying options for *

debug2: ssh_connect: needpriv 0

debug1: Connecting to sun.chpc.ac.za [196.24.44.62] port 22.

debug1: connect to address 196.24.44.62 port 22: Connection refused

ssh: connect to host sun.chpc.ac.za port 22: Connection refused

---

### Post by Lars Noodén on 2012-11-01
> **ade4krist said:**
> 
debug1: Connecting to sun.chpc.ac.za [196.24.44.62] port 22.
debug1: connect to address 196.24.44.62 port 22: Connection refused
ssh: connect to host sun.chpc.ac.za port 22: Connection refused

Either there is not an SSH server running at that address (not installed or not running) at port 22.  Or there is a firewall blocking access to port 22.  

Are you sure that particular machine has an SSH server running?
Have you been able to log in from other networks?

---

### Post by sanderj on 2012-11-01
I do get an ssh login prompt (altough a bit slow):

```
sander@R540:~$ ssh user@sun.chpc.ac.za
user@sun.chpc.ac.za's password: 
Permission denied, please try again.
user@sun.chpc.ac.za's password: 

sander@R540:~$ 

```

---

### Post by teward on 2012-11-01
Then the issue is not one of not being able to SSH out, but rather you not having access on the remote SSH server.  Either you are not entering the passcode correctly, or you are not authorized to login (which would suggest you don't know the pw).

Are you certain you can SSH in from other systems?  They may be restricting access too by machine, i.e. your laptop may not be authorized to SSH into that system.

---

### Post by sanderj on 2012-11-01
> **Lord of Time said:**
> Then the issue is not one of not being able to SSH out, but rather you not having access on the remote SSH server.  Either you are not entering the passcode correctly, or you are not authorized to login (which would suggest you don't know the pw).

Are you certain you can SSH in from other systems?  They may be restricting access too by machine, i.e. your laptop may not be authorized to SSH into that system.

I have the feeling your following up to my post ... but I'm not the OP ...

---

### Post by teward on 2012-11-01
> **sanderj said:**
> I have the feeling your following up to my post ... but I'm not the OP ...

Ah yeah, sorry bout that.  The statement on restrictions by machine is still valid.  Even if it resolves, and there's a server running there, their machine may be blocked from accessing it, either by firewall or some other restrictions

---

