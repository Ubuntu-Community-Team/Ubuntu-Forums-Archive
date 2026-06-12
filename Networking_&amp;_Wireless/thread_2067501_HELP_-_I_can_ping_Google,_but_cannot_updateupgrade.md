---
title: "HELP - I can ping Google, but cannot update/upgrade Ubuntu"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by n9nlu on 2012-10-07
The system is a Dell PE 1950 running Ubuntu Server 12.04.1 x86_64 (64 bit)

It was running just fine, running BOINC 24-7. I went to check for updates using the sudo apt-get update command. It lists err messages - as if I wasn't connected to the internet.

All cables are connected, I connected to the server via Putty on a different PC and pinged google at 8.8.8.8 with the server which gave me successful pings in the 34ms range. But still I cannot update/upgrade with the sudo apt-get command.

Guessing that maybe the ubuntu server is down, I used a 12.04 LTS Desktop x86 32 bit system , in terminal, used sudo apt-get- update and successfully received the updates.

Now I'm dumbfounded...

Question 1)  Does Ubuntu have different servers ( for updates/upgrades) for 32bit and for 64bit?

Question 2)  What else should I check on the Dell PE1950 server? I mean, it is connecting to the internet ( pinging google ) but not communicating with Ubuntu? What am I overlooking?

Thank you

Dave in Kewaskum, WI

---

### Post by Guilden_NL on 2012-10-07
Can you reply with a little more detail on the errors?

For instance, if you're getting something like: 
Temporary failure resolving ‘security.ubuntu.com’

it could mean a DNS issue.

But that's just one of very many possibilities, and we can't help without some examples of the error messages.

Oh yeah, "Go Packers!" \\:D/

---

### Post by slooksterpsv on 2012-10-07
Try to ping some other sites; if you use CenturyLink you can manually enter your DNS servers as:
205.171.3.25
205.171.2.25

Otherwise you can use google's DNS servers: 8.8.4.4 or 4.4.2.2

If that doesn't fix it. See if you can get on other sites. If you can't, it's a DNS issue. If you can, could need a 
sudo apt-get update
ran to fetch updates for the apt-get system.

---

### Post by n9nlu on 2012-10-07
Ok, here is the ifconfig output and the error messages I get when I run the sudo apt-get update:
-------------------------------------------
boinc1950@BOINC1950:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1d:09:6f:9c:b9
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe6f:9cb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1552 errors:1 dropped:0 overruns:0 frame:1
          TX packets:2152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:132255 (132.2 KB)  TX bytes:314963 (314.9 KB)
          Interrupt:16 Memory:f8000000-f8012800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:378688 (378.6 KB)  TX bytes:378688 (378.6 KB)


-------------------------------------------

boinc1950@BOINC1950:~$ sudo apt-get update

Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease

Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by n9nlu on 2012-10-07
Ping for 8.8.4.4
--------------------------------------

boinc1950@BOINC1950:~$ ping 8.8.4.4
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.
64 bytes from 8.8.4.4: icmp_req=1 ttl=44 time=40.2 ms
64 bytes from 8.8.4.4: icmp_req=2 ttl=44 time=36.7 ms
64 bytes from 8.8.4.4: icmp_req=3 ttl=44 time=37.1 ms
64 bytes from 8.8.4.4: icmp_req=4 ttl=44 time=37.8 ms
64 bytes from 8.8.4.4: icmp_req=5 ttl=44 time=38.0 ms
64 bytes from 8.8.4.4: icmp_req=6 ttl=44 time=37.1 ms
64 bytes from 8.8.4.4: icmp_req=7 ttl=44 time=39.8 ms
^C
--- 8.8.4.4 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6008ms
rtt min/avg/max/mdev = 36.725/38.142/40.219/1.305 ms

---

### Post by n9nlu on 2012-10-07
My /etc/network/interfaces 

((( Note, this is only for eth0 ... I have a redundant nic , eth1, but I cannot figure out how to give it a static IP address of 192.168.1.111 -- Help needed with this also )))

------------------------------------

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
                address         192.168.1.110
                netmask         255.255.255.0
                network         192.168.1.0
                broadcast       192.168.1.255
                gateway         192.168.1.1

---

### Post by n9nlu on 2012-10-07
Ok, after a little more fiddling, I managed to get it to connect, download and update/upgrade the Ubuntu 12.04.1 64bit system.

Being a server, I need a static IP address... how I got it to work was going into --- /etc/network/interfaces --- and changing back to --- auto eth0 inet dhcp --- 

I ran the --- sudo apt-get update -- and it worked, I was able to update/upgrade and the BOINC software was able to connect and download more work to be processed. So I changed back to the --- auto eth0 inet static --- exactly as I posted last night to see if it would work with a static IP address again, but nope, it does not work properly.

It was working properly with how I have the --- /etc/network/interfaces --- file set up. Somehow, a couple days ago, it just went nutz... totally un attended.

So, any sugestions on what could be the problem? Something got corrupted somewhere. 

Thank you

---

