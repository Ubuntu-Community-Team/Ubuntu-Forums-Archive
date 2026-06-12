---
title: "netfilter units of measure"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by KirbySmith on 2013-02-17
Please, what are the units for the time parameters in /proc/sys/net/netfilter: seconds, milliseconds, dec jiffys, ...?  

Thanks

kirby

---

### Post by KirbySmith on 2013-02-19
[www.iptables.info/en/connection-state.html]("http://www.iptables.info/en/connection-stat.html") asserts that the present units are seconds and the very long times for some parameters are intended, although the reason is not specified.    :confused:

k

---

### Post by Doug S on 2013-02-19
The link you gave does not work for me.
Did you mean: [http://www.iptables.info/en/connection-state.html](http://www.iptables.info/en/connection-state.html) ?
 
I think the default CLOSE_WAIT time is now 60 seconds and not 12 hours (used to be even longer (I think)). I make it 3600 seconds on my system, as I found it reduced the number of confused session terminations without the conntrack table getting excessively large.
 
In general I accept the reasons for the default times given: "The default values should, however, be fairly well established in practice."

---

### Post by KirbySmith on 2013-02-20
Sorry, a typo.  I did mean "state."

The issue with long time parameters is that Bit Torrent connections rarely close properly, leaving hanging sessions.  In routers, these can end up filling the state table and causing lockups and other degraded modes.  On a PC with probably a lot more memory, large numbers of hanging states may not be so noticeable, but they surely aren't helpful.

I just can't imagine a need for 5 days for TCP_established.  The image that comes to mind is a 300 baud modem on a noisy telephone line used for uploading the latest netfilter build.  ;)

kirby

---

### Post by Doug S on 2013-02-20
On my system, it is very rare that I get a hung session in the ESTABLISHED state. Failure to complete from a CLOSE_WAIT state is more common. While it may seem odd, I do check. I suppose you could change it from the default time.
 
As a side note, on my system right now I have a many days old ssh session that seems to have stopped down counting at 299 seconds, regardless of use. Yet, I have another, as far as I know identical, ssh session that is also days old that resets the counter upon use:```
doug@doug-64:~$ w
 08:01:35 up 8 days, 14:58,  5 users,  load average: 0.00, 0.01, 0.05
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
doug     tty2                      11Feb13  8days  5:57   0.41s -bash
doug     tty3                      11Feb13  8days  0.44s  0.41s -bash
doug     tty1                      11Feb13  8days  6:04   0.45s -bash
doug     [COLOR=red]pts/0    doug-xps2.smythi 11Feb13[/COLOR] 12:28   1.12s  1.12s -bash
doug     [COLOR=red]pts/1    doug-xps2.smythi 12Feb13[/COLOR]  0.00s  0.64s  0.00s w
``````
doug@doug-64:~/bin$ sudo cat /proc/net/ip_conntrack | grep "port=22"
[sudo] password for doug:
tcp      6 [COLOR=red]299 ESTABLISHED[/COLOR] src=192.168.111.101 dst=192.168.111.1 sport=65398 dport=22 src=192.168.111.1 dst=192.168.111.101 sport=22 dport=65398 [ASSURED] mark=0 use=2
tcp      6 [COLOR=red]431991 ESTABLISHED[/COLOR] src=192.168.111.101 dst=192.168.111.1 sport=4244 dport=22 src=192.168.111.1 dst=192.168.111.101 sport=22 dport=4244 [ASSURED] mark=0 use=2
```

---

### Post by KirbySmith on 2013-02-21
Pardon my late response, Doug, but I seem to have forgotten where I found the timeouts I want to compare with those I use on my router.  I thought they were somewhere in /proc/net/.  (I'm looking at Mint 14 from Ubuntu 12.10 at present.)   I'll get back with a real response when I find it.

kirby

---

### Post by Doug S on 2013-02-21
They should be here:```
doug@doug-64:~/init$ [COLOR=red]ls -l /proc/sys/net/ipv4/netfilter | grep timeout[/COLOR]
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_generic_timeout
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_icmp_timeout
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_tcp_timeout_close
-rw-r--r-- 1 root root 0 Feb 20 16:54 ip_conntrack_tcp_timeout_close_wait
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_tcp_timeout_established
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_tcp_timeout_fin_wait
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_tcp_timeout_last_ack
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_tcp_timeout_max_retrans
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_tcp_timeout_syn_recv
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_tcp_timeout_syn_sent
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_tcp_timeout_syn_sent2
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_tcp_timeout_time_wait
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_udp_timeout
-rw-r--r-- 1 root root 0 Feb 19 23:37 ip_conntrack_udp_timeout_stream

``````
doug@doug-64:~/init$ cat /proc/sys/net/ipv4/netfilter/ip_conntrack_tcp_timeout_established
432000

```I mentioned I change my close_wait. I did not do it with persistence, but rather do it as part of my firewall script:```
echo 3600 >/proc/sys/net/ipv4/netfilter/ip_conntrack_tcp_timeout_close_wait
```(note: the command will not work fromthe command line, even if preceeded by "sudo" because the "sudo" part would ony apply to the "echo" command.) If I wanted to make the change persistent, I would do this:```
sudo sysctl -w net.ipv4.netfilter.ip_conntrack_tcp_timeout_close_wait=3600
```EDIT: Important note: Those files will only be there if the kernel module is loaded. If one has no iptables rule set, the files might not exist.

---

### Post by KirbySmith on 2013-02-22
OK, Doug, here are comparative values between the referenced document, Linux Mint 14 Cinnamon, and the default for my router, which is built around iptables.  The parenthetical values in the router column represent my present settings to keep the state table small with Bit Torrent.  I have not seriously experimented with other values to determine the derivative of broken states with timeouts, so other values could prove adequately benign.

In Mint, the timeout values are in a single folder,  /proc/sys/net/netfilter/, and not in separate ipv4 and ipv6 folders, which still exist with other parameters.

```
[FONT=Courier New]
[SIZE=2]Parameter       iptables.info    Linux Mint 14    [SIZE=2]Z[/SIZE]yXEL 
                                (Ubuntu 12.10)    USG 50
TCP
None                    1800          ---          [SIZE=2]-[/SIZE]--
Established           432000       432000         9000(1800)
Syn_Sent                 120          120          120
Syn_Recv                  60           60           60
Fin_Wait                 120          120          120
Time_Wait                120          120            5
Close                     10           10           10
Close_Wait             43200           60           60
Last_Ack                  30           30           30
Listen                   120          ---          ---
Unacknowledged           ---          300          ---

UDP
Connect/Timeout           30           30            9
Deliver/Timeout_Stream   180          180          300 (30)[/SIZE][/FONT]

```In any case, the "established" value for iptables in Linux still seems to me to be unnecessarily long.

And thanks for the command to change the parameter values.  The parameters in /netfilter seem semi-permanent because the text files' time stamps are more recent than the build.  I'll have to pay attention to the conntrack list when there are enough torrents to see if the PC state table size is very large or not.  It may be the router minimizes PC states also by timing out sessions and then resetting the PC connections.

kirby

---

