---
title: "Bug in runlevel editors, can't stop SSH &amp; CUPS - Meerkat"
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by musketballdan on 2010-10-04
I've tried all the following to no avail, this is the RC1 - Maverick Meerkat release 10:10, I couldn't figure out how to submit the bug to launchpad so thought I would share the problem here instead.

I've tried the following methods,

chkconfig
bum - runlevel editior
rcconf

All three of the above are supposed to be able to start and stop services in inti.d

The problem is ssh is running by default when you install OpenSSH server and then run nmap -v -A localhost you'll see both CUPS and SSH running, when you attempt to switch them off with any of the above or even using the good old fashioned method of typing the command like: service ssh stop

It will look like its stopped the service, until you run nmap again or worse when you reboot the service has then re-started itself all over again. :(

rcconf pasted something about LBS conf problems and refered me to the Wiki which was unhelpful as I am not a guru. :) (yet)  Bug reporting needs work, its not so easy to submit a problem of this nature to the launchpad as the launchpad is not newb friendly.

Other than that it looks like a very nice release as I am using a netbook with broadcom b43xx drivers and they are working with an added poke (no drivers are included in the release) you have to install manually with the restricted drivers manager and that's if you use another wireless interface (luckily I have a linksys USB) and the pubkey is missing from APT && synaptic but thats not so hard to fix if you issue the command.

sudo apt-get install --reinstall ubuntu-extras-keyring

Just wish I knew how to turn off SSH as I dont really want that running if I cant stop and start it when I want to, so I guess apt-get remove is the short term fix.:guitar:

Output from chkconfig

root@inspiron:/home/vader# chkconfig
[COLOR=Red]cups                       off[/COLOR]
[COLOR=Red]ssh                         off[/COLOR]

But output from nmap

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2010-10-04 14:09 BST
NSE: Loaded 36 scripts for scanning.
Initiating SYN Stealth Scan at 14:09
Scanning localhost (127.0.0.1) [1000 ports]
Discovered open port 22/tcp on 127.0.0.1
Discovered open port 631/tcp on 127.0.0.1
Completed SYN Stealth Scan at 14:09, 0.08s elapsed (1000 total ports)
Initiating Service scan at 14:09
Scanning 2 services on localhost (127.0.0.1)
Completed Service scan at 14:09, 6.13s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against localhost (127.0.0.1)
NSE: Script scanning 127.0.0.1.
NSE: Starting runlevel 1 (of 1) scan.
Initiating NSE at 14:10
Completed NSE at 14:10, 0.25s elapsed
NSE: Script Scanning completed.
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000043s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 998 closed ports
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 5.5p1 Debian 4ubuntu4 (protocol 2.0)
| ssh-hostkey: 1024 18:2e:4c:a8:a2:be:54:21:09:7e:be:5b:7c:1f:a9:ae (DSA)
|_2048 f8:2d:e6:fa:6c:31:b4:1c:55:36:12:0f:0e:ac:57:2d (RSA)
631/tcp open  ipp     CUPS 1.4
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.19 - 2.6.31
Uptime guess: 197.263 days (since Sun Mar 21 06:51:52 2010)
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=192 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux

ORLY chkconfig?? ORLY!! :confused:

---

### Post by sisco311 on 2010-10-04
Ubuntu uses [Upstart]("http://upstart.ubuntu.com/"). In order to disable ssh, edit its job file in /etc/init and change the line **stop on runlevel [016]** to **stop on runlevel[01*2*6]**.

---

### Post by musketballdan on 2010-10-04
Thank you v.much that did it, it's gone.. :) Side note run-level was shown as !2345 on both CUPS & SSH finally bug free.. (i think! (hope))

---

