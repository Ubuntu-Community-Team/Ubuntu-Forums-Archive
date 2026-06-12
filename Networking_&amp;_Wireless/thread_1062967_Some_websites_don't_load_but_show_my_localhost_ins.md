---
title: "Some websites don't load but show my localhost instead."
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by MadnessRed on 2009-02-07
When I load a certain website, board.ogame.org, it for some reason redirects to [http://localhost/](http://localhost/), whilst the adress bar remains the same it takes me to my local host index page.

Very weird. it is in both flock and firefox.
Also my localhost shows the ip adress of the visitor and its 127.0.0.1

---

### Post by Til_Valhall_vi_drar! on 2009-02-07
i looked that address up, its 127.0.0.1 for me to, i think the dns servers have bound that name to the localhost ip, indeed its weird.

---

### Post by MadnessRed on 2009-02-07
oh, so its not jsut me then?

ok, I though it was me because my localhost page and that page were identical. That's an odd co-incidence.

edit:oh, you mean that 127.0.0.1 is localhost? yes, computers have up to 3 ips. Which, generally are.

127.0.0.1 or localhost - is this computer,
192.168.*.* or computer-name - is this computer on the network
***.***.***.*** or [www.xyz.com](www.xyz.com) - is this network to the world.

---

### Post by MadnessRed on 2009-02-07
edit: I found this, anyone have any idea of a linux equivelent where I should look?

[http://www.webmasterworld.com/forum47/1738.htm](http://www.webmasterworld.com/forum47/1738.htm)


hwere is my /ect/hosts file...
> 127.0.0.1 localhost
127.0.1.1 anthony-desktop.barbarians

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

the files hostname hosts.conf hants.allow and hosts.deny don't show anything unexpected either.
I have the same problem in Flock, Firefox and Opera. So its not the browser.



I pinged board.ogame.org and got this...
> madnessred@anthony-desktop:~$ ping board.ogame.org
PING board.ogame.org ([COLOR="Red"]127.0.0.1[/COLOR]) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.028 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.032 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.032 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.033 ms
...
64 bytes from localhost (127.0.0.1): icmp_seq=50 ttl=64 time=0.036 ms
64 bytes from localhost (127.0.0.1): icmp_seq=51 ttl=64 time=0.033 ms
64 bytes from localhost (127.0.0.1): icmp_seq=52 ttl=64 time=0.034 ms
64 bytes from localhost (127.0.0.1): icmp_seq=53 ttl=64 time=0.035 ms

--- board.ogame.org ping statistics ---
53 packets transmitted, 53 received, 0% packet loss, time 52001ms
rtt min/avg/max/mdev = 0.026/0.033/0.038/0.006 ms


As you can see its goes to 127.0.0.1 (localhost)

It should be doing something like this I think
> madnessred@anthony-desktop:~$ ping ogame.org
PING ogame.org (87.106.178.66) 56(84) bytes of data.
64 bytes from s15267193.onlinehome-server.info (87.106.178.66): icmp_seq=1 ttl=55 time=56.8 ms
64 bytes from s15267193.onlinehome-server.info (87.106.178.66): icmp_seq=2 ttl=55 time=56.1 ms
64 bytes from s15267193.onlinehome-server.info (87.106.178.66): icmp_seq=3 ttl=55 time=58.8 ms
64 bytes from s15267193.onlinehome-server.info (87.106.178.66): icmp_seq=4 ttl=55 time=62.7 ms
64 bytes from s15267193.onlinehome-server.info (87.106.178.66): icmp_seq=5 ttl=55 time=56.5 ms
...


What is interesting is that it is only board.ogame.org thats the problem

someone please help!!

---

### Post by ugm6hr on 2009-02-08
Unfortunately, that website has an IP identical to the default localhost in Linux.

Check here: [http://www.opendns.com/support/cache/](http://www.opendns.com/support/cache/)

```
dig board.ogame.org

; <<>> DiG 9.4.2-P1 <<>> board.ogame.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17593
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;board.ogame.org.		IN	A

;; ANSWER SECTION:
board.ogame.org.	174	IN	A	**127.0.0.1**

;; Query time: 28 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sun Feb  8 08:59:19 2009
;; MSG SIZE  rcvd: 49

```

I cannot think of any easy solution to this.

I *think* changing the order of DNS resolution might work, but could equally create a mess of your networking (so make backups of the file to restore).  I'm too scared to try it out myself!

```
gksudo gedit /etc/nsswitch.conf
```

Find the line: 
```
hosts:          files mdns4_minimal dns mdns4
```

And move dns to the start (i.e. ahead of files).

Ref: [http://www.faqs.org/docs/securing/chap6sec71.html](http://www.faqs.org/docs/securing/chap6sec71.html)

---

### Post by night_fox on 2009-07-26
Whenever I go to a certain website I get redirected to 127.0.0.1. It only happens on my laptop, no other computer, and only this one website. Did you find a solution?

---

### Post by MadnessRed on 2009-07-26
> **night_fox said:**
> Whenever I go to a certain website I get redirected to 127.0.0.1. It only happens on my laptop, no other computer, and only this one website. Did you find a solution?

ping the website, see what you get.
eg, in terminal type
ping google.com

also try posting this following file
/ect/hosts

finally posting the url may help. With me the problem was server side, not client side so I just waited for them to sort it. may be the case with you too.

---

### Post by redmk2 on 2009-07-26
> **MadnessRed said:**
> ping the website...

finally posting the url may help. With me the problem was server side, not client side so I just waited for them to sort it. may be the case with you too.

The 127.0.0.0 subnet is reserved for the local machine (the one you are sitting at).  It does not matter whether is is 127.0.0.1 or 127.0.1.1 etc.  They all point to the virtual interface (loopback) lo.

Pinging board.ogame.org reveals

```
ping board.ogame.org
PING board.ogame.org (79.110.90.246) 56(84) bytes of data.
64 bytes from s518.gfsrv.net (79.110.90.246): icmp_seq=1 ttl=50 time=194 ms
64 bytes from s518.gfsrv.net (79.110.90.246): icmp_seq=2 ttl=50 time=194 ms
64 bytes from s518.gfsrv.net (79.110.90.246): icmp_seq=3 ttl=50 time=193 ms
64 bytes from s518.gfsrv.net (79.110.90.246): icmp_seq=4 ttl=50 time=195 ms

--- board.ogame.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 193.577/194.690/195.654/0.866 ms

```

Using whois get us```
whois 79.110.90.246
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See http://www.ripe.net/db/support/db-terms-conditions.pdf

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '79.110.80.0 - 79.110.95.255'

inetnum:        79.110.80.0 - 79.110.95.255
netname:        GAMEFORGE-NET
descr:          Gameforge Productions GmbH
country:        DE
org:            ORG-GF5-RIPE
admin-c:        GAME-RIPE
tech-c:         GAME-RIPE
status:         ASSIGNED PI
mnt-by:         RIPE-NCC-HM-PI-MNT
mnt-lower:      RIPE-NCC-HM-PI-MNT
mnt-by:         GF-MNT
mnt-routes:     GF-MNT
mnt-domains:    GF-MNT
source:         RIPE # Filtered

organisation:   ORG-GF5-RIPE
org-name:       Gameforge Productions GmbH
org-type:       OTHER
address:        Gameforge Productions GmbH
                Albert-Nestler-Str. 8
                76131 Karlsruhe
                DE
phone:          +49-721-354808-0
fax-no:         +49-721-354808-152
e-mail:         info@gameforge.de
admin-c:        AR5322-RIPE
tech-c:         GAME-RIPE
mnt-ref:        GF-MNT
mnt-by:         GF-MNT
source:         RIPE # Filtered

role:           Gameforge Productions Hostmaster
address:        Gameforge Productions GmbH
                Albert-Nestler-Str. 8
                76131 Karlsruhe
                DE

```

It appears that your local DNS settings (maybe /etc/hosts) is misconfigured.

I am able to bring up the site in my FF browser with no problems.

---

### Post by redmk2 on 2009-07-26
> **ugm6hr said:**
> Unfortunately, that website has an IP identical to the default localhost in Linux.

No website ever has a 127.0.0.0 /24 address.  This is by IP addressing standard.> 

Check here: [http://www.opendns.com/support/cache/](http://www.opendns.com/support/cache/)

```
dig board.ogame.org

; <<>> DiG 9.4.2-P1 <<>> board.ogame.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17593
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;board.ogame.org.		IN	A

;; ANSWER SECTION:
board.ogame.org.	174	IN	A	**127.0.0.1**

;; Query time: 28 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sun Feb  8 08:59:19 2009
;; MSG SIZE  rcvd: 49

```

I cannot think of any easy solution to this.

I'm not sure what you are getting at in the above.  When I "dig" the address I get```
dig board.ogame.org

; <<>> DiG 9.4.2-P2 <<>> board.ogame.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38118
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;board.ogame.org.		IN	A

;; ANSWER SECTION:
board.ogame.org.	300	IN	A	79.110.90.246

;; Query time: 206 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Jul 26 17:47:59 2009
;; MSG SIZE  rcvd: 49

```It looks correct to me.  I feel the misconfiguration is on the client side.> 

I *think* changing the order of DNS resolution might work, but could equally create a mess of your networking (so make backups of the file to restore).  I'm too scared to try it out myself!

```
gksudo gedit /etc/nsswitch.conf
```

Find the line: 
```
hosts:          files mdns4_minimal dns mdns4
```

And move dns to the start (i.e. ahead of files).

I feel this should not be done.  Local DNS via host files should hold precedent over Internet provided DNS.

---

### Post by shredkingj on 2009-07-27
It's possible the website messed something up on their authoritative name  servers, and caching DNS servers now have a bad RR.  Of course, this problem would eventually disappear as the caching servers refresh their cache.  Hard to say what this problem is without more details, like whether this problem is still continuing, what website this is, and the contents of your /etc/hosts and /etc/resolv.conf files.

---

### Post by MadnessRed on 2009-07-31
whoah lol you are answering an already answered question.

nightfox said:
> Whenever I go to a certain website I get redirected to 127.0.0.1. It only happens on my laptop, no other computer, and only this one website. Did you find a solution?

the board.goame.org was long since sorted and i not related to this new question.

---

### Post by mvalviar on 2010-06-12
I'm getting the same problem. [http://mvalviar.co.cc](http://mvalviar.co.cc) takes me to 127.0.0.1. Have anyone solved this?

---

### Post by MadnessRed on 2010-06-13
> **mvalviar said:**
> I'm getting the same problem. [http://mvalviar.co.cc](http://mvalviar.co.cc) takes me to 127.0.0.1. Have anyone solved this?

I just left it an it sorted itself out after a while, sorry I can't be of more help. Do a system update, that may sort it.

---

