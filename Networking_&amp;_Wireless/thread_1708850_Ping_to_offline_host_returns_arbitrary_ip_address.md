---
title: "Ping to offline host returns arbitrary ip address"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by frio on 2011-03-17
Here is my dilemma. I have been trying to resolve this for quite some time now and have yet to find a solution.

_A brief description of my network:_
It is a small home network consisting of an Ubuntu 10.04LTS server edition, an Iomega ix2 NAS, a WinXP pro server and several family laptops. This is all routed through a Netgear WNDR3300 home router. All are assigned IP's via DHCP and all but the laptops are static (via DHCP though). The WAN address/DNS is assigned via DHCP from my ISP.

_The problem:_
When one of the machines is offline, Ubuntu does not resolve the netbios name correctly. No surprise here. But what is happening is that it is finding some arbitrary machine on another network. Below is what a ping to an offline host reveals:

```
ping -c3 hostname
PING hostname (204.232.162.92) 56(84) bytes of data.
64 bytes from 204.232.162.92: icmp_seq=1 ttl=116 time=27.0 ms
64 bytes from 204.232.162.92: icmp_seq=2 ttl=116 time=26.8 ms
64 bytes from 204.232.162.92: icmp_seq=3 ttl=116 time=25.7 ms

--- hostname ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10123ms
rtt min/avg/max/mdev = 25.776/26.540/27.012/0.545 ms
```This is obviously very wrong since my local network is 192.168.1.0/24. I have no idea why this IP is being returned. It is not one of my ISP's DNS servers nor does a reverse lookup find any domain associated with this IP.

_Some more info:_
I can ping, without issue, any online host, internal or external. I can share/browse files between Windows and Ubuntu without issue.  No other issues that I am aware of exist, just this anomaly. Winbind is installed - found much conflicting info on this one since I am not using a real domain but it is the only way I could get netbios name resolution to work at all.

_The question:_
Why is Ubuntu simply not saying the host cannot be found?


Here is the global section of my smb.conf:
```
[global]
    log file = /var/log/samba/log.%m
    load printers = No
    name resolve order = hosts bcast wins lmhosts
    smb ports = 139
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
    obey pam restrictions = Yes
    deadtime = 30
    passwd program = /usr/bin/passwd %u
    dns proxy = No
    netbios name = linux1
    usershare max shares = 0
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    workgroup = HOMENET
    os level = 65
    syslog = 0
    security = user
    panic action = /usr/share/samba/panic-action %d
    bind interfaces only = Yes
    max log size = 1000
    pam password change = Yes
```resolv.conf contains (the router):
    ```
nameserver 192.168.1.1
```nsswitch.conf (I've tried all kinds of combinations for hosts below): 
    ```
passwd:         compat
    group:          compat
    shadow:         compat


    hosts:          files dns wins mdns4_minimal [NOTFOUND=return] mdns4
    networks:       files

    protocols:      db files
    services:       db files
    ethers:         db files
    rpc:            db files

    netgroup:       nis
```Thanks in advance to any and all that can help with this one. I have searched high and low, tried everything I can find or think of. I am stumped.

Frio

---

### Post by BkkBonanza on 2011-03-17
Most immediate thing that comes to mind is to **traceroute hostname** and see what path the trace brings back. It should work if pings are working.

At 27ms it can't be too many hops.

---

### Post by frio on 2011-03-17
A new development. I realized I had the three static machines listed in the hosts file from earlier tests a while ago. This is why the three machines that are always on seemed to work. Without them listed in the hosts file, they all return the same IP now. Below is the output of the traceroute. It is the same on all machines.

One of the servers that is online right now (after removing it from the hosts file):
```
**> traceroute svr3**
traceroute to svr3 (204.232.162.92), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  0.370 ms  0.534 ms  0.475 ms
 2  10.184.192.1 (10.184.192.1)  19.275 ms  19.184 ms  19.089 ms
 3  96-34-65-34.static.unas.sc.charter.com (96.34.65.34)  20.307 ms  25.090 ms  27.931 ms
 4  96-34-65-128.static.unas.sc.charter.com (96.34.65.128)  32.772 ms  32.755 ms  33.925 ms
 5  96-34-65-143.static.unas.sc.charter.com (96.34.65.143)  38.923 ms  39.419 ms  40.583 ms
 6  96-34-2-110.static.unas.mo.charter.com (96.34.2.110)  39.188 ms bbr01spbgsc-tge-0-1-0-0.spbg.sc.charter.com (96.34.2.50)  15.909 ms 96-34-2-110.static.unas.mo.charter.com (96.34.2.110)  18.480 ms
 7  xe-7-0-0.edge3.Washington1.Level3.net (4.59.144.5)  32.859 ms  25.502 ms  28.297 ms
 8  ae-4-90.edge1.Washington4.Level3.net (4.69.149.207)  33.846 ms ae-3-80.edge1.Washington4.Level3.net (4.69.149.143)  37.912 ms ae-4-90.edge1.Washington4.Level3.net (4.69.149.207)  40.601 ms
 9  RACKSPACE-M.edge1.Washington4.Level3.net (4.53.112.46)  44.623 ms  49.036 ms  49.572 ms
10  vlan905.core5.iad2.rackspace.net (72.4.122.10)  50.644 ms  50.542 ms  49.302 ms
11  aggr301a-2-core5.iad2.rackspace.net (72.4.122.125)  50.441 ms  51.631 ms  24.436 ms
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```...and one for an offline machine (one of the laptops). Actually, it doesn;t matter what I try here. I get the same thing.

```
**> traceroute del1**
traceroute to del1 (204.232.162.92), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  0.535 ms  0.432 ms  1.700 ms
 2  10.184.192.1 (10.184.192.1)  17.961 ms  17.917 ms  19.263 ms
 3  96-34-65-34.static.unas.sc.charter.com (96.34.65.34)  175.545 ms  175.492 ms  175.422 ms
 4  96-34-65-128.static.unas.sc.charter.com (96.34.65.128)  32.089 ms  32.444 ms  32.381 ms
 5  96-34-65-143.static.unas.sc.charter.com (96.34.65.143)  38.863 ms  40.192 ms  40.146 ms
 6  96-34-2-106.static.unas.mo.charter.com (96.34.2.106)  38.650 ms  20.025 ms bbr01spbgsc-tge-0-1-0-0.spbg.sc.charter.com (96.34.2.50)  21.797 ms
 7  xe-7-0-0.edge3.Washington1.Level3.net (4.59.144.5)  26.232 ms  29.043 ms  34.758 ms
 8  ae-1-60.edge1.Washington4.Level3.net (4.69.149.15)  37.951 ms  42.487 ms ae-2-70.edge1.Washington4.Level3.net (4.69.149.79)  92.050 ms
 9  RACKSPACE-M.edge1.Washington4.Level3.net (4.53.112.46)  49.993 ms  50.407 ms  49.398 ms
10  vlan905.core5.iad2.rackspace.net (72.4.122.10)  49.729 ms  50.139 ms  50.039 ms
11  aggr301a-2-core5.iad2.rackspace.net (72.4.122.125)  59.735 ms  34.383 ms  31.491 ms
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```Could this be a router issue? Why would the router be routing it outside the local network?

---

### Post by BkkBonanza on 2011-03-17
Actually this has to be a DNS config error. When you say traceroute **svr3** the first thing it does is DNS lookup on **svr3**. That lookup is returning the IP that is then used for the traceroute. 

Whatever DNS server or relay is being used should be detecting that there is no TLD and rejecting the request (or looking it up in a local DNS table). It must be appending a TLD and sending the request out to an external DNS server. The IP you get back (eg. 204.232.162.92) is not a private address so it's probably the right IP for **some** real domain name.

Here is the dig query I just did:

```
$ dig svr3

; <<>> DiG 9.7.1-P2 <<>> svr3
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 51682
;; flags: qr rd ra; QUERY: 1, **ANSWER: 0**, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;svr3.				IN	A

;; Query time: 0 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Thu Mar 17 22:11:01 2011
;; MSG SIZE  rcvd: 22
```

No valid record returned. However, when I try svr3.com an svr3.net I get no response. Hinting that your DNS server is mixing something up and ending up at some bizarre result. 

The reverse lookup for 204.232.162.92 is:

```
dig -x 204.232.162.92

; <<>> DiG 9.7.1-P2 <<>> -x 204.232.162.92
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 39434
;; flags: qr rd ra; QUERY: 1, **ANSWER: 0**, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;92.162.232.204.in-addr.arpa.	IN	PTR

;; AUTHORITY SECTION:
162.232.204.in-addr.arpa. 300	IN	SOA	ns.rackspace.com. hostmaster.rackspace.com. 1269287812 3600 300 1814400 300

;; Query time: 458 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Thu Mar 17 22:13:52 2011
;; MSG SIZE  rcvd: 108

```

Which is returned NXDOMAIN (meaning invalid domain) and it returns the network that has authority for the IP range it's located on. So bottom line... something is misconfigured in the DNS server.

Or your DNS relay (DHCP servers often behave as relays) perhaps. For name lookups with no TLD (.com, .net etc) it should only do local lookup. But if your local LAN domain is set to some global name eg. rackspace.net then perhaps the DHCP server assumes that is your local LAN domain too. Just a guess here.

---

### Post by psusi on 2011-03-17
Bingo.

---

### Post by frio on 2011-03-17
I agree that it is a DNS issue and I may be making a fatal error in thinking that the router is providing DNS name resolution for the local network when in fact it may not be. I suppose what got me thinking along these lines is that in resolve.conf the router's IP is listed and this is set automatically when the machine get it's info via DHCP.

So with all this in mind, would you agree that my best path forward would be to use the linux box as a WINS server and set all the windows clients to use it as such? Or... would turning DHCP off on the router and using the linux box as the all inclusive name resolution solution (DHCP, DNS) be best?

Any other solutions you would suggest?

Also, I want to thank you for all the help and the quick replies. It is very much appreciated.

Frio

---

### Post by BkkBonanza on 2011-03-17
Your router no doubt is doing relaying for DNS. So either it has a problem or the upstream DNS server (your ISP?). I would look carefully over any DHCP/DNS related settings in the router for anything that may affect how it handles local domains.

I would try setting your router to use an external DNS like google or easydns, eg. 8.8.8.8 / 8.8.4.4 This bypasses using your ISP. See how that affects lookups. You can also just put these IPs in your resolv.conf to see if bybpassing the router completely helps. You can try to deduce where the problem is.

If the problem is the router and you don't mind running a different DHCP/DNS server then sure, **dnsmasq** is an excellent, easy, low overhead program to do both on a linux box.

I don't know anything about WINS so won't comment on what to do there.

---

### Post by frio on 2011-03-17
I think I found the answer and it has to do with nsswitch.conf. The line:
```
hosts:          files dns wins mdns4_minimal [NOTFOUND=return] mdns4

```
needed changed to:
```
hosts:    files wins dns mdns4_minimal [NOTFOUND=return] mdns4

```.

The big difference is that wins is now BEFORE dns. Since I now realize that my router is not a dns, having dns before wins seems to be causing the problem. I still don't really understand why I was getting some arbitrary ip address but it works. As proof (and for my sanity) it tried putting dns first on the line and sure enough, nothing worked. I couldn't even ping a host that was listed in the hosts file. I know I said earlier that I had tried all kinds of combinations for hosts in nsswitch.conf but I guess I wasn't very methodical about it.

I'm going to see what happens over the next few days but I am confident this is it. After I am positive this is the fix, I'll mark the thread as SOLVED. Maybe it will save someone else the headache.

Thanks again for the help!

---

### Post by BkkBonanza on 2011-03-17
I'd assume there is still some problem with DNS but by hitting WINS first you avoid the issue. Since WINS handles local names they don't get passed onto DNS. But I'd wonder what happens with an unknown local name, if WINS can't find it, does it still get passed onto DNS? Or is it definitive and return "unknown"?

(I've always used google/easydns name servers anyway since I've found my own ISP DNS to be pretty flaky and personally I just don't trust them from a security viewpoint. I'm in Thailand and often tech staff just aren't too reliable. Not only that but the google ones are faster than the ISP DNS - which is just pathetic really.)

---

### Post by frio on 2011-03-17
Good point. I just tried it and you are correct, Here is the results (nas2 does not exist):
```
john@linux1:~$ ping -c3 nas1
PING nas1 (192.168.1.102) 56(84) bytes of data.
64 bytes from nas1.local (192.168.1.102): icmp_seq=1 ttl=64 time=0.301 ms
64 bytes from nas1.local (192.168.1.102): icmp_seq=2 ttl=64 time=1.40 ms
64 bytes from nas1.local (192.168.1.102): icmp_seq=3 ttl=64 time=0.238 ms

--- nas1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.238/0.646/1.401/0.534 ms
john@linux1:~$ ping -c3 nas2
PING nas2 (204.232.162.92) 56(84) bytes of data.
64 bytes from 204.232.162.92: icmp_seq=1 ttl=116 time=28.7 ms
64 bytes from 204.232.162.92: icmp_seq=2 ttl=116 time=25.0 ms
64 bytes from 204.232.162.92: icmp_seq=3 ttl=116 time=24.1 ms

--- nas2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10086ms
rtt min/avg/max/mdev = 24.131/25.999/28.796/2.014 ms

```I'm going to try your suggestion of using different DNS servers. I'll be back with the results.

---

### Post by frio on 2011-03-17
Using OpenDNS, I now get this:

```
john@linux1:~$ ping -c3 nas1
PING nas1 (192.168.1.102) 56(84) bytes of data.
64 bytes from nas1.local (192.168.1.102): icmp_seq=1 ttl=64 time=1.46 ms
64 bytes from nas1.local (192.168.1.102): icmp_seq=2 ttl=64 time=1.40 ms
64 bytes from nas1.local (192.168.1.102): icmp_seq=3 ttl=64 time=0.238 ms

--- nas1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 0.238/1.036/1.468/0.566 ms
john@linux1:~$ ping -c3 nas2
PING nas2 (67.215.65.132) 56(84) bytes of data.
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=1 ttl=55 time=26.8 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=2 ttl=55 time=24.4 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=3 ttl=55 time=23.9 ms

```I guess the reasoning may be that once the local lookup fails, dns is then the next order of business. I get the same results even after moving dns to the end of the line. If I remove dns then nothing outside the local network gets resolved.

---

### Post by BkkBonanza on 2011-03-17
Interesting. Did you put OpenDNS in the router or in your local machine resolv.conf. If in the router then it points towards ISP issues. But if in your local machine then it's still possible either the router or ISP.

I see OpenDNS doesn't return NXDOMAIN but rather points to their NXDOMAIN server (which I'm guessing returns search results in a browser).

(I got mixed up between OpenDNS and EasyDNS - I seem to always get them confused but it's OpenDNS I meant to refer to before)

---

### Post by frio on 2011-03-18
I put OpenDNS' IP's in the router. Using DHCP, I can't enter them in resolve.conf. It gets overwritten as soon as the network comes up.

---

### Post by psusi on 2011-03-18
> **frio said:**
> I put OpenDNS' IP's in the router. Using DHCP, I can't enter them in resolve.conf. It gets overwritten as soon as the network comes up.

And did it fix the problem?

---

### Post by matt_symes on 2011-03-18
Hi

> I put OpenDNS' IP's in the router. Using DHCP, I can't enter them in resolve.conf. It gets overwritten as soon as the network comes up.

There is a fix for this. Make your changes in the resolv.conf file and change its attributes to immutable

```
sudo chattr +i /etc/resolv.conf
```

you can then change it back after testing to

```
sudo chattr -i /etc/resolv.conf
```

List attributes using

```
lsattr /etc/resolv.conf
```

Great thread BTW.

Kind regards

---

### Post by frio on 2011-03-18
[psusi]("http://ubuntuforums.org/member.php?u=41311"), See post 11

---

### Post by frio on 2011-03-18
Matt. Thanks for the new command. I learn something new about linux every day.

Here are the results and I think we may have found a possible solution albeit a somewhat sloppy one in my opinion.

When my resolve.conf looks like this:

```

nameserver 208.67.222.222
nameserver 208.67.220.220

```I get the same results as before, an arbitrary IP. I've added a ping to a public domain now since it has entered the issue. Also, remember that nas2 does not exist on the local network.

```
**> ping -c3 nas1**
PING nas1 (192.168.1.102) 56(84) bytes of data.
64 bytes from nas1.local (192.168.1.102): icmp_seq=1 ttl=64 time=0.249 ms
64 bytes from nas1.local (192.168.1.102): icmp_seq=2 ttl=64 time=1.39 ms
64 bytes from nas1.local (192.168.1.102): icmp_seq=3 ttl=64 time=0.242 ms

--- nas1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.242/0.628/1.395/0.542 ms
**> ping -c3 nas2**
PING nas2 (67.215.65.132) 56(84) bytes of data.
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=1 ttl=55 time=25.8 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=2 ttl=55 time=24.2 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_seq=3 ttl=55 time=25.1 ms

--- nas2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10113ms
rtt min/avg/max/mdev = 24.295/25.084/25.829/0.653 ms
**> ping -c3 ubuntuforums.org**
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=47 time=100 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=47 time=97.9 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=47 time=99.4 ms

--- ubuntuforums.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10262ms
rtt min/avg/max/mdev = 97.951/99.245/100.354/0.989 ms

```But... if I change resolve.conf to:

```
search .local
nameserver 208.67.222.222
nameserver 208.67.220.220

```I get...
```

**> ping -c3 nas1**
PING nas1 (192.168.1.102) 56(84) bytes of data.
64 bytes from nas1.local (192.168.1.102): icmp_seq=1 ttl=64 time=0.251 ms
64 bytes from nas1.local (192.168.1.102): icmp_seq=2 ttl=64 time=1.39 ms
64 bytes from nas1.local (192.168.1.102): icmp_seq=3 ttl=64 time=0.222 ms

--- nas1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 0.222/0.623/1.398/0.548 ms
**> ping -c3 nas2**
ping: unknown host nas2
**> ping -c3 ubuntuforums.org**
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=47 time=103 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=47 time=99.6 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=47 time=100 ms

--- ubuntuforums.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10264ms
rtt min/avg/max/mdev = 99.626/101.213/103.480/1.665 ms


```Yeah!!! I never thought I would be so happy to get an unknown host message.

I really don;t like the fact that I have to lock down the resolve.conf file but I will if it works. Anyone got any more ideas to try or a definitive reason why things are this way?

---

### Post by psusi on 2011-03-18
It isn't an arbitrary IP address.  Both your ISP and the opendns servers are configured to return the address of a web server they have set up instead of not found, so that users trying to go to an invalid web site get directed there instead.  I personally can't stand DNS servers that do this crap, and refuse to use them.

---

### Post by BkkBonanza on 2011-03-18
That seems about right. It's terrible that they would take over an unknown local name  and really the **router** relaying the DNS request should know it's not public and cut it short. I know **dnsmasq** has options for this (as I run it on my Ubuntu router).

You can actually verify that by putting the 204.232.162.92 into your browser and see that the resolved address is actually a search result page. My guess of the day is that your ISP is "Charter Communications"...

They have a message on that page about disabling the search option. Try that and see if it returns NXDOMAIN.

---

### Post by frio on 2011-03-18
BkkBonanza, yes Charter Communications is my ISP.

A couple questions before we wrap this up.

[LIST]
[*]What DNS servers would you recommend? I am in South Carolina.
[*]Would you agree that this thread should be marked as SOLVED?
[/LIST]
Once again, thanks for the help. This is the kind of thing that keeps me interested in Ubuntu and without people willing to help who know more about a subject, I'm pretty sure I wouldn't be here.

---

### Post by BkkBonanza on 2011-03-18
I usually use the google ones. 8.8.8.8 & 8.8.4.4

I guess that's mostly because they are so easy to remember. They are fast too. But I also have an OpenDNS in the mix in case google goes down. I know that google returns NXDOMAIN for my unknowns. I trust them more than my ISP here (DNS is pretty critical security wise as some employee who has access could poison the DNS lookups and force site spoofing).

It's pretty clear what's happening now. Seems like your ISP has an option to turn off the "not found" redirect feature so that may be the way to "fix" it. If you're happy then you should mark it solved.

---

### Post by frio on 2011-03-18
You are correct. Using Google's DNS servers, I get a host not found when pinging a non-existent local host. Not sure I would have ever figured that out. I do agree with what was mentioned earlier in that the router should not be allowing the request to go public.

Google DNS is the way I am going to go as I believe it to be the cleanest. I may look into the 'turn-off' redirect for my ISP's DNS to see if I can get the same results but right now I'm just thrilled I have a solution.

I now understand what is happening and know how to address it. Many thanks!

---

### Post by frio on 2011-04-01
Just a followup about Charter's so called "Charter Web Helper". Here's what the page states:

> "Charter has partnered with Yahoo! and other industry leaders to bring  you useful and relevant results whenever a "Page Not Found" or similar  error occurs.  You may disable it below."It does fix the issue once disabled BUT... once I click update I get a message stating the settings are only good for one year. What a crock of bs.

---

