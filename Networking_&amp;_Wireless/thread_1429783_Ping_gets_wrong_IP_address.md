---
title: "Ping gets wrong IP address"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by ForgivenByJC on 2010-03-14
Hello, my network expertise is tenuous at best.  This started because one computer on my network is having trouble updating Google Toolbar information.  This is a laptop which joins other wifi networks outside of the house.```
BROKEN:~$ ping toolbar.google.com
PING toolbar.google.com (208.68.139.89) 56(84) bytes of data.
^C
--- toolbar.google.com ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7054ms
``````
BROKEN:~$ dig toolbar.google.com

; <<>> DiG 9.6.1-P2 <<>> toolbar.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4752
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;toolbar.google.com.		IN	A

;; ANSWER SECTION:
toolbar.google.com.	193	IN	CNAME	tools.l.google.com.
tools.l.google.com.	292	IN	A	74.125.45.113
tools.l.google.com.	292	IN	A	74.125.45.138
tools.l.google.com.	292	IN	A	74.125.45.139
tools.l.google.com.	292	IN	A	74.125.45.101
tools.l.google.com.	292	IN	A	74.125.45.102

;; Query time: 16 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Mar 14 14:52:10 2010
;; MSG SIZE  rcvd: 138
``````
BROKEN:~$ nslookup toolbar.google.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
toolbar.google.com	canonical name = tools.l.google.com.
Name:	tools.l.google.com
Address: 74.125.45.102
Name:	tools.l.google.com
Address: 74.125.45.101
Name:	tools.l.google.com
Address: 74.125.45.139
Name:	tools.l.google.com
Address: 74.125.45.138
Name:	tools.l.google.com
Address: 74.125.45.113
``````
BROKEN:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:8d:d4:df  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3523624 (3.5 MB)  TX bytes:3523624 (3.5 MB)

virbr0    Link encap:Ethernet  HWaddr 62:06:d9:f3:b3:33  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:104440 (104.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:e7:c2:74  
          inet addr:192.168.1.41  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fee7:c274/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1942701 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1059693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2757203086 (2.7 GB)  TX bytes:94433373 (94.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-E7-C2-74-65-37-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
So, why would ping get 208.68.139.89 on this laptop, but not the other computers behind the same gateway-firewall-router server?

/etc/resolv.conf, /etc/networks/interfaces, /etc/host.conf, /etc/hosts, /etc/hosts.allow, /etc/hosts.deny seem to be correct according to other Ubuntu computers which are working correctly.

I am at such a loss on this one, I am not even certain how to Google for solutions.  I have tried "ping wrong ip" and several others, but no real answer I can find.  Please, add some light as to why this might be happening and/or solutions.  Thanks!

---

### Post by sanderj on 2010-03-14
You said the BROKEN laptop is on a different network, didn't you?

I would say one DNS along the way (in the router, or at the ISP) is replacing the DNS request for toolbar.google.com with it's own search site [http://twcsearch.fastsearch.net/](http://twcsearch.fastsearch.net/) . I would expect this would then also happen for other *.google.com request, so check "ping google.com".

This can also be done by infected PCs on which some "helpful" program reroutes to other sites.

One way to check my hypothesis, is to put 8.8.8.8 as the *only* nameserver in /etc/resolv.conf, and then try the ping again.

HTH


de Kameel

---

### Post by ForgivenByJC on 2010-03-16
> **sanderj said:**
> You said the BROKEN laptop is on a different network, didn't you?BROKEN computer is currently on the same network, however, occasionally it connects to unsecured networks (coffee shops, friends' houses, etc.).
> **sanderj said:**
> I would say one DNS along the way (in the router, or at the ISP) is replacing the DNS request for toolbar.google.com with it's own search site [http://twcsearch.fastsearch.net/](http://twcsearch.fastsearch.net/) . I would expect this would then also happen for other *.google.com request, so check "ping google.com".Pinging google.com and tools.l.google.com from BROKEN gets the right responses.> **sanderj said:**
> This can also be done by infected PCs on which some "helpful" program reroutes to other sites.
One way to check my hypothesis, is to put 8.8.8.8 as the *only* nameserver in /etc/resolv.conf, and then try the ping again.Because BROKEN visits unsecured networks, it maybe "infected" somehow.  Is there a way to remove networking and reinstall it?  Or is there a means to trace down what "helpful" program is rerouting to other sites?
/etc/resolv.conf is generated by NetworkManager and updated each time connections are established.  Did this:
[LIST=1]
[*]Connected to the network
[*]Changed nameserver to 8.8.8.8 in /etc/resolv.conf
[*]Pinged toolbar.google.com and tools.l.google.com
[*]Double checked /etc/resolv.conf to ensure nameserver was not changed
[/LIST]The results are the same unfortunately.  It seems like the issue is with BROKEN and not the DNS or local router/nameserver.

---

### Post by CharlesA on 2010-03-16
Does the same thing happen when you have booted to a livecd?

---

### Post by ForgivenByJC on 2010-03-16
Also tried this on both wireless and ethernet connections to the network.

---

### Post by ForgivenByJC on 2010-03-16
> **CharlesA said:**
> Does the same thing happen when you have booted to a livecd?No, this does not happen when booted from LiveCD.

---

### Post by teward on 2010-03-16
Sounds like your DNS is screwed.  Did you try putting 8.8.8.8 in as the only IP address in that file that someone above said to do?

---

### Post by sanderj on 2010-03-16
> **TrekCaptainUSA said:**
> Sounds like your DNS is screwed.  Did you try putting 8.8.8.8 in as the only IP address in that file that someone above said to do?

... and post the full output of "dig toolbar.google.com" to make sure 8.8.8.8 is queried.


```


sander@quirinius:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
domain lan
search lan
# nameserver 192.168.2.254
nameserver 8.8.8.8

sander@quirinius:~$ dig toolbar.google.com

; <<>> DiG 9.6.1-P2 <<>> toolbar.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27633
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;toolbar.google.com.		IN	A

;; ANSWER SECTION:
toolbar.google.com.	187	IN	CNAME	tools.l.google.com.
tools.l.google.com.	187	IN	A	74.125.79.102
tools.l.google.com.	187	IN	A	74.125.79.101
tools.l.google.com.	187	IN	A	74.125.79.100

;; Query time: 53 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Tue Mar 16 18:47:09 2010
;; MSG SIZE  rcvd: 106

sander@quirinius:~$ 

```

---

### Post by ForgivenByJC on 2010-03-16
```
BROKEN:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
domain lan
search lan
nameserver 8.8.8.8
BROKEN:~$ ping toolbar.google.com
PING toolbar.google.com (208.68.139.89) 56(84) bytes of data.
^C
--- toolbar.google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

BROKEN:~$ dig toolbar.google.com

; <<>> DiG 9.6.1-P2 <<>> toolbar.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27722
;; flags: qr rd ra; QUERY: 1, ANSWER: 7, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;toolbar.google.com.		IN	A

;; ANSWER SECTION:
toolbar.google.com.	18	IN	CNAME	tools.l.google.com.
tools.l.google.com.	260	IN	A	74.125.93.138
tools.l.google.com.	260	IN	A	74.125.93.101
tools.l.google.com.	260	IN	A	74.125.93.100
tools.l.google.com.	260	IN	A	74.125.93.139
tools.l.google.com.	260	IN	A	74.125.93.113
tools.l.google.com.	260	IN	A	74.125.93.102

;; Query time: 176 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Tue Mar 16 14:33:22 2010
;; MSG SIZE  rcvd: 154

BROKEN:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
domain lan
search lan
nameserver 8.8.8.8

```

---

### Post by sanderj on 2010-03-16
Post the output of "cat /etc/hosts"

> 
sander@quirinius:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	quirinius

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
sander@quirinius:~$ 


---

### Post by ForgivenByJC on 2010-03-16
```
BROKEN:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```*Note: "laptop" is fictitious and is changed from the proper hostname of the BROKEN computer.  This is just to try and avoid security issues from hackers--is this too paranoid?  Don't know the capabilities of network hacks.

---

### Post by sanderj on 2010-03-16
So your /etc/hosts is not the cause; it does not contain an entry for toolbar.google.com

I'm out of ideas now. You could read "man host.conf" for more hints. And/or you could add toolbar.google.com to /etc/hosts to workaround the problem. And if all that does not help, and you really need the problem to go away, you could do a fresh install.

---

### Post by ForgivenByJC on 2010-03-16
Hmmm, is there a means to figure where it is pulling the wrong information from?

---

### Post by sanderj on 2010-03-17
Maybe with 'strace ping -c 1 toolbar.google.com'

---

### Post by ForgivenByJC on 2010-03-17
```
BROKEN:~$ strace ping -c 1 toolbar.google.com
execve("/bin/ping", ["ping", "-c", "1", "toolbar.google.com"], [/* 44 vars */]) = 0
brk(0)                                  = 0x8104000
fcntl64(0, F_GETFD)                     = 0
fcntl64(1, F_GETFD)                     = 0
fcntl64(2, F_GETFD)                     = 0
access("/etc/suid-debug", F_OK)         = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7752000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=117535, ...}) = 0
mmap2(NULL, 117535, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7735000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libresolv.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000&\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=71432, ...}) = 0
mmap2(NULL, 79944, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xcdd000
mmap2(0xced000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x10) = 0xced000
mmap2(0xcef000, 6216, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xcef000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260l\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1319364, ...}) = 0
mmap2(NULL, 1329512, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x51f000
mprotect(0x65d000, 4096, PROT_NONE)     = 0
mmap2(0x65e000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13e) = 0x65e000
mmap2(0x661000, 10600, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x661000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7734000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7733000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7734b10, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0x65e000, 8192, PROT_READ)     = 0
mprotect(0xced000, 4096, PROT_READ)     = 0
mprotect(0x8050000, 4096, PROT_READ)    = 0
mprotect(0x7de000, 4096, PROT_READ)     = 0
munmap(0xb7735000, 117535)              = 0
socket(PF_INET, SOCK_RAW, IPPROTO_ICMP) = -1 EPERM (Operation not permitted)
getuid32()                              = 1000
setuid32(1000)                          = 0
brk(0)                                  = 0x8104000
brk(0x8125000)                          = 0x8125000
getpid()                                = 17614
open("/etc/resolv.conf", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7751000
read(3, "# Generated by NetworkManager\ndo"..., 4096) = 155
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7751000, 4096)                = 0
stat64("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
open("/etc/resolv.conf", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7751000
read(3, "# Generated by NetworkManager\ndo"..., 4096) = 155
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7751000, 4096)                = 0
socket(PF_FILE, 0x80801 /* SOCK_??? */, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(PF_FILE, 0x80801 /* SOCK_??? */, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=518, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7751000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 518
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7751000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=117535, ...}) = 0
mmap2(NULL, 117535, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7735000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_files.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \32\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=42572, ...}) = 0
mmap2(NULL, 45772, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xa99000
mmap2(0xaa3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0xaa3000
close(3)                                = 0
mprotect(0xaa3000, 4096, PROT_READ)     = 0
munmap(0xb7735000, 117535)              = 0
open("/etc/host.conf", O_RDONLY)        = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=92, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7751000
read(3, "# The \"order\" line is only used "..., 4096) = 92
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7751000, 4096)                = 0
open("/etc/hosts", O_RDONLY|O_CLOEXEC)  = 3
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
fstat64(3, {st_mode=S_IFREG|0644, st_size=463, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7751000
read(3, "127.0.0.1\tlocalhost\n127.0.1.1\tbd"..., 4096) = 463
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7751000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=117535, ...}) = 0
mmap2(NULL, 117535, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7735000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnss_wins.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\16\4\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=2460424, ...}) = 0
mmap2(NULL, 2466316, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x110000
mmap2(0x360000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x24f) = 0x360000
mmap2(0x36a000, 524, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x36a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libldap_r-2.4.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\245\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=297020, ...}) = 0
mmap2(NULL, 304416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x36b000
mprotect(0x3b2000, 4096, PROT_NONE)     = 0
mmap2(0x3b3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x47) = 0x3b3000
mmap2(0x3b5000, 1312, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x3b5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/liblber-2.4.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P$\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=54712, ...}) = 0
mmap2(NULL, 57532, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x3b6000
mmap2(0x3c3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc) = 0x3c3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgssapi_krb5.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@J\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=166512, ...}) = 0
mmap2(NULL, 169416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x3c5000
mmap2(0x3ed000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x27) = 0x3ed000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkrb5.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\341\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=675424, ...}) = 0
mmap2(NULL, 678556, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb8c000
mprotect(0xc2b000, 4096, PROT_NONE)     = 0
mmap2(0xc2c000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9f) = 0xc2c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libk5crypto.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\3207\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=161312, ...}) = 0
mmap2(NULL, 164832, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x466000
mprotect(0x48c000, 4096, PROT_NONE)     = 0
mmap2(0x48d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x26) = 0x48d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libcom_err.so.2", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\16\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9632, ...}) = 0
mmap2(NULL, 12464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xe06000
mmap2(0xe08000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xe08000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libcap.so.2", O_RDONLY)      = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\16\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=17912, ...}) = 0
mmap2(NULL, 20752, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x3ef000
mmap2(0x3f3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0x3f3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2201\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=79676, ...}) = 0
mmap2(NULL, 92136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb3a000
mmap2(0xb4d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12) = 0xb4d000
mmap2(0xb4f000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb4f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9736, ...}) = 0
mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x501000
mmap2(0x503000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x503000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libtalloc.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\25\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=38360, ...}) = 0
mmap2(NULL, 41440, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x4a1000
mmap2(0x4aa000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0x4aa000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libsasl2.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0203\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=100136, ...}) = 0
mmap2(NULL, 102956, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xf39000
mmap2(0xf51000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17) = 0xf51000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgnutls.so.26", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\333\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=682548, ...}) = 0
mmap2(NULL, 685272, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x6b8000
mmap2(0x75b000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa2) = 0x75b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0PI\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=116920, ...}) = 0
mmap2(NULL, 98792, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x3f5000
mmap2(0x40a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0x40a000
mmap2(0x40c000, 4584, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x40c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkrb5support.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\32\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=26160, ...}) = 0
mmap2(NULL, 29020, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x881000
mmap2(0x887000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5) = 0x887000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libkeyutils.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\t\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9492, ...}) = 0
mmap2(NULL, 12324, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x40e000
mmap2(0x410000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x410000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libtasn1.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\21\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=67028, ...}) = 0
mmap2(NULL, 70276, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb64000
mmap2(0xb74000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf) = 0xb74000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libz.so.1", O_RDONLY)        = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\31\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=83608, ...}) = 0
mmap2(NULL, 86284, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xd57000
mmap2(0xd6b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xd6b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcrypt.so.11", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300M\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=503740, ...}) = 0
mmap2(NULL, 507212, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fe000
mmap2(0x877000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x78) = 0x877000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgpg-error.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\6\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=13600, ...}) = 0
mmap2(NULL, 16432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x87b000
mmap2(0x87e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2) = 0x87e000
close(3)                                = 0
mprotect(0x87e000, 4096, PROT_READ)     = 0
mprotect(0x877000, 4096, PROT_READ)     = 0
mprotect(0xd6b000, 4096, PROT_READ)     = 0
mprotect(0xb74000, 4096, PROT_READ)     = 0
mprotect(0x410000, 4096, PROT_READ)     = 0
mprotect(0x887000, 4096, PROT_READ)     = 0
mprotect(0x40a000, 4096, PROT_READ)     = 0
mprotect(0x75b000, 16384, PROT_READ)    = 0
mprotect(0xf51000, 4096, PROT_READ)     = 0
mprotect(0x4aa000, 4096, PROT_READ)     = 0
mprotect(0x503000, 4096, PROT_READ)     = 0
mprotect(0xb4d000, 4096, PROT_READ)     = 0
mprotect(0x3f3000, 4096, PROT_READ)     = 0
mprotect(0xe08000, 4096, PROT_READ)     = 0
mprotect(0x48d000, 4096, PROT_READ)     = 0
mprotect(0xc2c000, 20480, PROT_READ)    = 0
mprotect(0x3ed000, 4096, PROT_READ)     = 0
mprotect(0x3c3000, 4096, PROT_READ)     = 0
mprotect(0x3b3000, 4096, PROT_READ)     = 0
mprotect(0x360000, 20480, PROT_READ)    = 0
set_tid_address(0xb7734b78)             = 17614
set_robust_list(0xb7734b80, 0xc)        = 0
futex(0xbfa7ecc0, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0xbfa7ecc0, 0x189 /* FUTEX_??? */, 1, NULL, bfa7ecd0) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0x3f9340, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0x3f9820, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="laptop", ...}) = 0
munmap(0xb7735000, 117535)              = 0
time(NULL)                              = 1268809271
open("/etc/localtime", O_RDONLY)        = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7751000
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\4\0\0\0\4\0\0\0\0"..., 4096) = 3519
_llseek(3, -24, [3495], SEEK_CUR)       = 0
read(3, "\nEST5EDT,M3.2.0,M11.1.0\n", 4096) = 24
close(3)                                = 0
munmap(0xb7751000, 4096)                = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
gettimeofday({1268809271, 72388}, NULL) = 0
open("/usr/share/samba/upcase.dat", O_RDONLY|O_LARGEFILE) = 3
mmap2(NULL, 131072, PROT_READ, MAP_SHARED, 3, 0) = 0xb7713000
close(3)                                = 0
open("/usr/share/samba/lowcase.dat", O_RDONLY|O_LARGEFILE) = 3
mmap2(NULL, 131072, PROT_READ, MAP_SHARED, 3, 0) = 0xb76f3000
close(3)                                = 0
uname({sys="Linux", node="laptop", ...}) = 0
getrlimit(RLIMIT_NOFILE, {rlim_cur=1024, rlim_max=1024}) = 0
stat64("/etc/samba/smb.conf", {st_mode=S_IFREG|0644, st_size=12525, ...}) = 0
open("/etc/samba/smb.conf", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=12525, ...}) = 0
read(3, "#\n# Sample configuration file fo"..., 12525) = 12525
close(3)                                = 0
time(NULL)                              = 1268809271
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb76f2000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb76f2000, 4096)                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=373, ...}) = 0
mmap2(NULL, 373, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb76f2000
close(3)                                = 0
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=26048, ...}) = 0
mmap2(NULL, 26048, PROT_READ, MAP_SHARED, 3, 0) = 0xb76eb000
close(3)                                = 0
futex(0x660a6c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap2(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb76ea000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
mmap2(NULL, 59, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb76e9000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
mmap2(NULL, 155, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb76e8000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
mmap2(NULL, 77, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb76e7000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap2(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb76e6000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
close(3)                                = 0
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=52, ...}) = 0
mmap2(NULL, 52, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb76e5000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0
mmap2(NULL, 286, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb76e4000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=966938, ...}) = 0
mmap2(NULL, 966938, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb75f7000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2454, ...}) = 0
mmap2(NULL, 2454, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb75f6000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap2(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb75f5000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=256316, ...}) = 0
mmap2(NULL, 256316, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb75b6000
close(3)                                = 0
open("/usr/lib/gconv/UTF-16.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\4\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9540, ...}) = 0
mmap2(NULL, 12328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfe0000
mmap2(0xfe2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xfe2000
close(3)                                = 0
mprotect(0xfe2000, 4096, PROT_READ)     = 0
open("/usr/lib/gconv/IBM850.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\3\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9528, ...}) = 0
mmap2(NULL, 12316, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x412000
mmap2(0x414000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x414000
close(3)                                = 0
mprotect(0x414000, 4096, PROT_READ)     = 0
brk(0x814a000)                          = 0x814a000
brk(0x816b000)                          = 0x816b000
brk(0x8193000)                          = 0x8193000
open("/usr/share/samba/valid.dat", O_RDONLY|O_LARGEFILE) = 3
mmap2(NULL, 65536, PROT_READ, MAP_SHARED, 3, 0) = 0xb75a6000
close(3)                                = 0
socket(PF_NETLINK, SOCK_RAW, 0)         = 3
bind(3, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(3, {sa_family=AF_NETLINK, pid=17614, groups=00000000}, [12]) = 0
time(NULL)                              = 1268809271
sendto(3, "\24\0\0\0\22\0\1\0037~\240K\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\354\0\0\0\20\0\2\0007~\240K\316D\0\0\0\0\4\3\1\0\0\0I\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 1212
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0007~\240K\316D\0\0\0\0\0\0\1\0\0\0I\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
sendto(3, "\24\0\0\0\26\0\1\0038~\240K\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"0\0\0\0\24\0\2\0008~\240K\316D\0\0\2\10\200\376\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 228
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"@\0\0\0\24\0\2\0008~\240K\316D\0\0\n\200\200\376\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 192
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0008~\240K\316D\0\0\0\0\0\0\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(3)                                = 0
socket(PF_NETLINK, SOCK_RAW, 0)         = 3
bind(3, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(3, {sa_family=AF_NETLINK, pid=17614, groups=00000000}, [12]) = 0
time(NULL)                              = 1268809271
sendto(3, "\24\0\0\0\26\0\1\0037~\240K\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"0\0\0\0\24\0\2\0007~\240K\316D\0\0\2\10\200\376\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 228
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"@\0\0\0\24\0\2\0007~\240K\316D\0\0\n\200\200\376\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 192
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0007~\240K\316D\0\0\0\0\0\0\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(3)                                = 0
stat64("/var/run/samba", {st_mode=S_IFDIR|0755, st_size=140, ...}) = 0
open("/var/run/samba/gencache.tdb", O_RDWR|O_CREAT|O_LARGEFILE, 0644) = -1 EACCES (Permission denied)
open("/usr/share/locale/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/var/run/samba/gencache.tdb", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_GETFD)                     = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
read(3, "TDB file\n\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 168) = 168
fstat64(3, {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
mmap2(NULL, 696, PROT_READ, MAP_SHARED, 3, 0) = 0xb75a5000
socket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = 4
setsockopt(4, SOL_SOCKET, SO_REUSEADDR, [1], 4) = 0
bind(4, {sa_family=AF_INET, sin_port=htons(0), sin_addr=inet_addr("0.0.0.0")}, 16) = 0
open("/dev/urandom", O_RDONLY|O_LARGEFILE) = 5
read(5, "\213\255", 2)                  = 2
time(NULL)                              = 1268809271
gettimeofday({1268809271, 90233}, NULL) = 0
sendto(4, "-\214\1\0\0\1\0\0\0\0\0\0 FEEPEPEMECEBFCCOEHE"..., 50, 0, {sa_family=AF_INET, sin_port=htons(137), sin_addr=inet_addr("192.168.1.1")}, 16) = 50
gettimeofday({1268809271, 90392}, NULL) = 0
gettimeofday({1268809271, 90426}, NULL) = 0
select(5, [4], NULL, NULL, {0, 90000})  = 1 (in [4], left {0, 78536})
recvfrom(4, "-\214\205\200\0\0\0\1\0\0\0\0 FEEPEPEMECEBFCCOEHE"..., 576, 0, {sa_family=AF_INET, sin_port=htons(137), sin_addr=inet_addr("192.168.1.1")}, [16]) = 62
time(NULL)                              = 1268809271
close(4)                                = 0
socket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = 4
connect(4, {sa_family=AF_INET, sin_port=htons(1025), sin_addr=inet_addr("208.68.139.89")}, 16) = 0
getsockname(4, {sa_family=AF_INET, sin_port=htons(43816), sin_addr=inet_addr("192.168.1.42")}, [16]) = 0
close(4)                                = 0
dup(2)                                  = 4
fcntl64(4, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(4, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75a4000
_llseek(4, 0, 0xbfa7f048, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(4, "ping: icmp open socket: Operatio"..., 48ping: icmp open socket: Operation not permitted
) = 48
close(4)                                = 0
munmap(0xb75a4000, 4096)                = 0
exit_group(2)                           = ?
``````
BROKEN:~$ sudo strace ping -c 1 toolbar.google.com
execve("/bin/ping", ["ping", "-c", "1", "toolbar.google.com"], [/* 17 vars */]) = 0
brk(0)                                  = 0x8b12000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7773000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=117535, ...}) = 0
mmap2(NULL, 117535, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7756000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libresolv.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000&\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=71432, ...}) = 0
mmap2(NULL, 79944, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x85a000
mmap2(0x86a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x10) = 0x86a000
mmap2(0x86c000, 6216, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x86c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260l\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1319364, ...}) = 0
mmap2(NULL, 1329512, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x110000
mprotect(0x24e000, 4096, PROT_NONE)     = 0
mmap2(0x24f000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13e) = 0x24f000
mmap2(0x252000, 10600, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x252000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7755000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7754000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7755b10, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0x24f000, 8192, PROT_READ)     = 0
mprotect(0x86a000, 4096, PROT_READ)     = 0
mprotect(0x8050000, 4096, PROT_READ)    = 0
mprotect(0x7bb000, 4096, PROT_READ)     = 0
munmap(0xb7756000, 117535)              = 0
socket(PF_INET, SOCK_RAW, IPPROTO_ICMP) = 3
getuid32()                              = 0
setuid32(0)                             = 0
brk(0)                                  = 0x8b12000
brk(0x8b33000)                          = 0x8b33000
getpid()                                = 18717
open("/etc/resolv.conf", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7772000
read(4, "# Generated by NetworkManager\ndo"..., 4096) = 155
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb7772000, 4096)                = 0
stat64("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
open("/etc/resolv.conf", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7772000
read(4, "# Generated by NetworkManager\ndo"..., 4096) = 155
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb7772000, 4096)                = 0
socket(PF_FILE, 0x80801 /* SOCK_??? */, 0) = 4
connect(4, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(4)                                = 0
socket(PF_FILE, 0x80801 /* SOCK_??? */, 0) = 4
connect(4, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(4)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=518, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7772000
read(4, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 518
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb7772000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=117535, ...}) = 0
mmap2(NULL, 117535, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7756000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_files.so.2", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \32\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=42572, ...}) = 0
mmap2(NULL, 45772, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xc7c000
mmap2(0xc86000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x9) = 0xc86000
close(4)                                = 0
mprotect(0xc86000, 4096, PROT_READ)     = 0
munmap(0xb7756000, 117535)              = 0
open("/etc/host.conf", O_RDONLY)        = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=92, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7772000
read(4, "# The \"order\" line is only used "..., 4096) = 92
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb7772000, 4096)                = 0
open("/etc/hosts", O_RDONLY|O_CLOEXEC)  = 4
fcntl64(4, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
fstat64(4, {st_mode=S_IFREG|0644, st_size=463, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7772000
read(4, "127.0.0.1\tlocalhost\n127.0.1.1\tbd"..., 4096) = 463
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb7772000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=117535, ...}) = 0
mmap2(NULL, 117535, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7756000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnss_wins.so.2", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\16\4\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=2460424, ...}) = 0
mmap2(NULL, 2466316, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x255000
mmap2(0x4a5000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x24f) = 0x4a5000
mmap2(0x4af000, 524, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x4af000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libldap_r-2.4.so.2", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\245\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=297020, ...}) = 0
mmap2(NULL, 304416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x947000
mprotect(0x98e000, 4096, PROT_NONE)     = 0
mmap2(0x98f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x47) = 0x98f000
mmap2(0x991000, 1312, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x991000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/liblber-2.4.so.2", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P$\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=54712, ...}) = 0
mmap2(NULL, 57532, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xe00000
mmap2(0xe0d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xc) = 0xe0d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgssapi_krb5.so.2", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@J\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=166512, ...}) = 0
mmap2(NULL, 169416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x6d4000
mmap2(0x6fc000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x27) = 0x6fc000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkrb5.so.3", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\341\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=675424, ...}) = 0
mmap2(NULL, 678556, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x4ea000
mprotect(0x589000, 4096, PROT_NONE)     = 0
mmap2(0x58a000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x9f) = 0x58a000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libk5crypto.so.3", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\3207\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=161312, ...}) = 0
mmap2(NULL, 164832, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xf6c000
mprotect(0xf92000, 4096, PROT_NONE)     = 0
mmap2(0xf93000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x26) = 0xf93000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libcom_err.so.2", O_RDONLY)  = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\16\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=9632, ...}) = 0
mmap2(NULL, 12464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x73f000
mmap2(0x741000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1) = 0x741000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libcap.so.2", O_RDONLY)      = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\16\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=17912, ...}) = 0
mmap2(NULL, 20752, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7eb000
mmap2(0x7ef000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x3) = 0x7ef000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2201\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=79676, ...}) = 0
mmap2(NULL, 92136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x928000
mmap2(0x93b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x12) = 0x93b000
mmap2(0x93d000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x93d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\n\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=9736, ...}) = 0
mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x4b0000
mmap2(0x4b2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1) = 0x4b2000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libtalloc.so.1", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\25\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=38360, ...}) = 0
mmap2(NULL, 41440, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xd37000
mmap2(0xd40000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x8) = 0xd40000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libsasl2.so.2", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0203\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=100136, ...}) = 0
mmap2(NULL, 102956, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x63a000
mmap2(0x652000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x17) = 0x652000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgnutls.so.26", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\333\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=682548, ...}) = 0
mmap2(NULL, 685272, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x590000
mmap2(0x633000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xa2) = 0x633000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0PI\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0755, st_size=116920, ...}) = 0
mmap2(NULL, 98792, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xce1000
mmap2(0xcf6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x14) = 0xcf6000
mmap2(0xcf8000, 4584, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xcf8000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkrb5support.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\32\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=26160, ...}) = 0
mmap2(NULL, 29020, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x4b4000
mmap2(0x4ba000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x5) = 0x4ba000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libkeyutils.so.1", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\t\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=9492, ...}) = 0
mmap2(NULL, 12324, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x4bc000
mmap2(0x4be000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1) = 0x4be000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libtasn1.so.3", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\21\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=67028, ...}) = 0
mmap2(NULL, 70276, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xa44000
mmap2(0xa54000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xf) = 0xa54000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libz.so.1", O_RDONLY)        = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\31\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=83608, ...}) = 0
mmap2(NULL, 86284, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x87b000
mmap2(0x88f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x13) = 0x88f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcrypt.so.11", O_RDONLY)  = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300M\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=503740, ...}) = 0
mmap2(NULL, 507212, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x654000
mmap2(0x6cd000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x78) = 0x6cd000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgpg-error.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\6\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=13600, ...}) = 0
mmap2(NULL, 16432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x4c0000
mmap2(0x4c3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2) = 0x4c3000
close(4)                                = 0
mprotect(0x4c3000, 4096, PROT_READ)     = 0
mprotect(0x6cd000, 4096, PROT_READ)     = 0
mprotect(0x88f000, 4096, PROT_READ)     = 0
mprotect(0xa54000, 4096, PROT_READ)     = 0
mprotect(0x4be000, 4096, PROT_READ)     = 0
mprotect(0x4ba000, 4096, PROT_READ)     = 0
mprotect(0xcf6000, 4096, PROT_READ)     = 0
mprotect(0x633000, 16384, PROT_READ)    = 0
mprotect(0x652000, 4096, PROT_READ)     = 0
mprotect(0xd40000, 4096, PROT_READ)     = 0
mprotect(0x4b2000, 4096, PROT_READ)     = 0
mprotect(0x93b000, 4096, PROT_READ)     = 0
mprotect(0x7ef000, 4096, PROT_READ)     = 0
mprotect(0x741000, 4096, PROT_READ)     = 0
mprotect(0xf93000, 4096, PROT_READ)     = 0
mprotect(0x58a000, 20480, PROT_READ)    = 0
mprotect(0x6fc000, 4096, PROT_READ)     = 0
mprotect(0xe0d000, 4096, PROT_READ)     = 0
mprotect(0x98f000, 4096, PROT_READ)     = 0
mprotect(0x4a5000, 20480, PROT_READ)    = 0
set_tid_address(0xb7755b78)             = 18717
set_robust_list(0xb7755b80, 0xc)        = 0
futex(0xbfc89480, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0xbfc89480, 0x189 /* FUTEX_??? */, 1, NULL, bfc89490) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0xce5340, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xce5820, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="laptop", ...}) = 0
munmap(0xb7756000, 117535)              = 0
time(NULL)                              = 1268809379
open("/etc/localtime", O_RDONLY)        = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7772000
read(4, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\4\0\0\0\4\0\0\0\0"..., 4096) = 3519
_llseek(4, -24, [3495], SEEK_CUR)       = 0
read(4, "\nEST5EDT,M3.2.0,M11.1.0\n", 4096) = 24
close(4)                                = 0
munmap(0xb7772000, 4096)                = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
gettimeofday({1268809379, 810506}, NULL) = 0
open("/usr/share/samba/upcase.dat", O_RDONLY|O_LARGEFILE) = 4
mmap2(NULL, 131072, PROT_READ, MAP_SHARED, 4, 0) = 0xb7734000
close(4)                                = 0
open("/usr/share/samba/lowcase.dat", O_RDONLY|O_LARGEFILE) = 4
mmap2(NULL, 131072, PROT_READ, MAP_SHARED, 4, 0) = 0xb7714000
close(4)                                = 0
uname({sys="Linux", node="laptop", ...}) = 0
getrlimit(RLIMIT_NOFILE, {rlim_cur=1024, rlim_max=1024}) = 0
stat64("/etc/samba/smb.conf", {st_mode=S_IFREG|0644, st_size=12525, ...}) = 0
open("/etc/samba/smb.conf", O_RDONLY|O_LARGEFILE) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=12525, ...}) = 0
read(4, "#\n# Sample configuration file fo"..., 12525) = 12525
close(4)                                = 0
time(NULL)                              = 1268809379
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7713000
read(4, "# Locale name alias data base.\n#"..., 4096) = 2570
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb7713000, 4096)                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=373, ...}) = 0
mmap2(NULL, 373, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7713000
close(4)                                = 0
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=26048, ...}) = 0
mmap2(NULL, 26048, PROT_READ, MAP_SHARED, 4, 0) = 0xb770c000
close(4)                                = 0
futex(0x251a6c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap2(NULL, 23, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb770b000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
mmap2(NULL, 59, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb770a000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
mmap2(NULL, 155, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7709000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
mmap2(NULL, 77, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7708000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap2(NULL, 34, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7707000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
close(4)                                = 0
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=52, ...}) = 0
mmap2(NULL, 52, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7706000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0
mmap2(NULL, 286, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7705000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=966938, ...}) = 0
mmap2(NULL, 966938, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7618000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=2454, ...}) = 0
mmap2(NULL, 2454, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7617000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap2(NULL, 54, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7616000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=256316, ...}) = 0
mmap2(NULL, 256316, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb75d7000
close(4)                                = 0
open("/usr/lib/gconv/UTF-16.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\4\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=9540, ...}) = 0
mmap2(NULL, 12328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x4c5000
mmap2(0x4c7000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1) = 0x4c7000
close(4)                                = 0
mprotect(0x4c7000, 4096, PROT_READ)     = 0
open("/usr/lib/gconv/IBM850.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\3\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=9528, ...}) = 0
mmap2(NULL, 12316, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x4c9000
mmap2(0x4cb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1) = 0x4cb000
close(4)                                = 0
mprotect(0x4cb000, 4096, PROT_READ)     = 0
brk(0x8b58000)                          = 0x8b58000
brk(0x8b79000)                          = 0x8b79000
brk(0x8ba1000)                          = 0x8ba1000
open("/usr/share/samba/valid.dat", O_RDONLY|O_LARGEFILE) = 4
mmap2(NULL, 65536, PROT_READ, MAP_SHARED, 4, 0) = 0xb75c7000
close(4)                                = 0
socket(PF_NETLINK, SOCK_RAW, 0)         = 4
bind(4, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(4, {sa_family=AF_NETLINK, pid=18717, groups=00000000}, [12]) = 0
time(NULL)                              = 1268809379
sendto(4, "\24\0\0\0\22\0\1\3\243~\240K\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\354\0\0\0\20\0\2\0\243~\240K\35I\0\0\0\0\4\3\1\0\0\0I\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 1212
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0\243~\240K\35I\0\0\0\0\0\0\1\0\0\0I\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
sendto(4, "\24\0\0\0\26\0\1\3\244~\240K\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"0\0\0\0\24\0\2\0\244~\240K\35I\0\0\2\10\200\376\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 228
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"@\0\0\0\24\0\2\0\244~\240K\35I\0\0\n\200\200\376\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 192
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0\244~\240K\35I\0\0\0\0\0\0\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(4)                                = 0
socket(PF_NETLINK, SOCK_RAW, 0)         = 4
bind(4, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(4, {sa_family=AF_NETLINK, pid=18717, groups=00000000}, [12]) = 0
time(NULL)                              = 1268809379
sendto(4, "\24\0\0\0\26\0\1\3\243~\240K\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"0\0\0\0\24\0\2\0\243~\240K\35I\0\0\2\10\200\376\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 228
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"@\0\0\0\24\0\2\0\243~\240K\35I\0\0\n\200\200\376\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 192
recvmsg(4, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0\243~\240K\35I\0\0\0\0\0\0\1\0\0\0\24\0\1\0\0\0\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(4)                                = 0
stat64("/var/run/samba", {st_mode=S_IFDIR|0755, st_size=140, ...}) = 0
open("/var/run/samba/gencache.tdb", O_RDWR|O_CREAT|O_LARGEFILE, 0644) = 4
fcntl64(4, F_GETFD)                     = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(4, F_SETLKW64, {type=F_WRLCK, whence=SEEK_SET, start=0, len=1}, 0xbfc8903c) = 0
read(4, "TDB file\n\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 168) = 168
fstat64(4, {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
mmap2(NULL, 696, PROT_READ|PROT_WRITE, MAP_SHARED, 4, 0) = 0xb75c6000
fcntl64(4, F_SETLKW64, {type=F_UNLCK, whence=SEEK_SET, start=0, len=1}, 0xbfc8903c) = 0
fcntl64(4, F_SETLKW64, {type=F_RDLCK, whence=SEEK_SET, start=460, len=1}, 0xbfc8900c) = 0
fcntl64(4, F_SETLKW64, {type=F_UNLCK, whence=SEEK_SET, start=460, len=1}, 0xbfc8906c) = 0
fcntl64(4, F_SETLKW64, {type=F_RDLCK, whence=SEEK_SET, start=460, len=1}, 0xbfc8926c) = 0
fcntl64(4, F_SETLKW64, {type=F_UNLCK, whence=SEEK_SET, start=460, len=1}, 0xbfc892cc) = 0
socket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = 5
setsockopt(5, SOL_SOCKET, SO_REUSEADDR, [1], 4) = 0
bind(5, {sa_family=AF_INET, sin_port=htons(0), sin_addr=inet_addr("0.0.0.0")}, 16) = 0
open("/dev/urandom", O_RDONLY|O_LARGEFILE) = 6
read(6, "\223\266", 2)                  = 2
time(NULL)                              = 1268809379
gettimeofday({1268809379, 827533}, NULL) = 0
sendto(5, "6\224\1\0\0\1\0\0\0\0\0\0 FEEPEPEMECEBFCCOEHE"..., 50, 0, {sa_family=AF_INET, sin_port=htons(137), sin_addr=inet_addr("192.168.1.1")}, 16) = 50
gettimeofday({1268809379, 827695}, NULL) = 0
gettimeofday({1268809379, 827728}, NULL) = 0
select(6, [5], NULL, NULL, {0, 90000})  = 1 (in [5], left {0, 77347})
recvfrom(5, "6\224\205\200\0\0\0\1\0\0\0\0 FEEPEPEMECEBFCCOEHE"..., 576, 0, {sa_family=AF_INET, sin_port=htons(137), sin_addr=inet_addr("192.168.1.1")}, [16]) = 62
time(NULL)                              = 1268809379
close(5)                                = 0
socket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = 5
connect(5, {sa_family=AF_INET, sin_port=htons(1025), sin_addr=inet_addr("208.68.139.89")}, 16) = 0
getsockname(5, {sa_family=AF_INET, sin_port=htons(40659), sin_addr=inet_addr("192.168.1.42")}, [16]) = 0
close(5)                                = 0
setsockopt(3, SOL_RAW, ICMP_FILTER, ~(ICMP_ECHOREPLY|ICMP_DEST_UNREACH|ICMP_SOURCE_QUENCH|ICMP_REDIRECT|ICMP_TIME_EXCEEDED|ICMP_PARAMETERPROB), 4) = 0
setsockopt(3, SOL_IP, IP_RECVERR, [1], 4) = 0
setsockopt(3, SOL_SOCKET, SO_SNDBUF, [324], 4) = 0
setsockopt(3, SOL_SOCKET, SO_RCVBUF, [65536], 4) = 0
getsockopt(3, SOL_SOCKET, SO_RCVBUF, [131072], [4]) = 0
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75c5000
write(1, "PING toolbar.google.com (208.68."..., 62PING toolbar.google.com (208.68.139.89) 56(84) bytes of data.
) = 62
setsockopt(3, SOL_SOCKET, SO_TIMESTAMP, [1], 4) = 0
setsockopt(3, SOL_SOCKET, SO_SNDTIMEO, "\1\0\0\0\0\0\0\0", 8) = 0
setsockopt(3, SOL_SOCKET, SO_RCVTIMEO, "\1\0\0\0\0\0\0\0", 8) = 0
rt_sigaction(SIGINT, {0x804b860, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGALRM, {0x804b860, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGQUIT, {0x804b870, [], SA_INTERRUPT}, NULL, 8) = 0
gettimeofday({1268809379, 841521}, NULL) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=45, ws_col=157, ws_xpixel=0, ws_ypixel=0}) = 0
gettimeofday({1268809379, 841642}, NULL) = 0
gettimeofday({1268809379, 841673}, NULL) = 0
sendmsg(3, {msg_name(16)={sa_family=AF_INET, sin_port=htons(0), sin_addr=inet_addr("208.68.139.89")}, msg_iov(1)=[{"\10\0\326\20\35I\0\1\243~\240K\311\327\f\0\10\t\n\v\f\r\16\17\20\21\22\23\24\25\26\27"..., 64}], msg_controllen=0, msg_flags=0}, 0) = 64
setitimer(ITIMER_REAL, {it_interval={0, 0}, it_value={10, 0}}, NULL) = 0
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(3, 0xbfc88898, 0)               = -1 EINTR (Interrupted system call)
--- SIGALRM (Alarm clock) @ 0 (0) ---
sigreturn()                             = ? (mask now [])
write(1, "\n", 1
)                       = 1
write(1, "--- toolbar.google.com ping stat"..., 43--- toolbar.google.com ping statistics ---
) = 43
write(1, "1 packets transmitted, 0 receive"..., 621 packets transmitted, 0 received, 100% packet loss, time 0ms
) = 62
write(1, "\n", 1
)                       = 1
exit_group(1)                           = ?
```Does anything look out of place?  Where to focus?

---

### Post by ForgivenByJC on 2010-04-13
Just as a follow up.  I reinstalled the OS.  Trying to avoid having the same issue, I only imported back in my home directory.  It now functions as expected.  Thanks for the help.

---

