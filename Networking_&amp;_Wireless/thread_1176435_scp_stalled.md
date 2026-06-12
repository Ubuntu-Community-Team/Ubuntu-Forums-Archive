---
title: "scp stalled"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by blake1024 on 2009-06-02
Like many others I've googled, I too am experiencing the "scp stalled"
problem.  After spending many hours on the problem, with no solution,
I thought I'd add my observations to the mix.

I have/had several hosted servers connected to reasonably fast Internet
connections.  I also have a bunch of machines at my home-office
connected through a DSL connection.

Scp from fast connection to fast connection works fine in any
direction.  Scp from a fast connection to my slower DSL connection
works fine too.  I get the "scp stalled" message only when I attempt
to transfer a large file (20MB) from a machine on the DSL to one of
the fast connected machines.  In fact, the issue is so pronounced that
I am totally unable to transfer the large file at all in this
direction.

When attempting to transfer a file from a DSL connection (uploading),
the DSL transfer initially starts off very fast (for DSL) at about
1MB/sec and then it constantly reduces until it ultimately hangs with
the scp "-stalled-" message.

Interestingly, when I try scp on a Mac or on Windows/Cygwin with the
same file and from/to the same networks, scp works reliably every
time!!  The upload speed stabilizes at 30 to 50 KB/sec.  I also have
several machines with various versions of Ubuntu installed and none of
them can scp the sample file I am using.

I have googled and tried many things suggested on the net.  None of
them helped me.  I often see someone say a suggestion fixed the
problem only to see them recant later.  I think this is because if
your connection speed is not too bad the issue appears to work
sometime and not work others.  In my instance, however, given my speed
situation, I am able to reliably produce the issue.  None of the
suggested responses fixes the problem.

I have had this issue with Ubuntu 9.04, 8.10 & 8.04.  I was hoping
9.04 would fix the problem but it didn't.

This issue is extremely significant for me.  I am trying to run a
company and the ability to upload new releases of my product to my
customers is required.  Most of my programmers are pulling the company
towards the Mac.  I have been pulling towards Ubuntu Linux.  I can't win
without a working scp.

Thank you.

Blake McBride

---

### Post by detroit/zero on 2009-06-02
I have the same problem with two laptops behind the same NAT router on a small home network. It's not just limited to SSH&SCP, either. My NFS connections work like crap, as well.

By any chance, have you noticed any difficulties in doing USB file transfers - say, to an external HDD or thumbdrive? I have a big problem writing to USB devices that started around the same time as my network problems, and it's almost the same problem - speeds that start out fine; stop & start, stop & start; and rapidly degrade over time. 

I think the two bugs are related. I could be wrong. 

I'd be interested in seeing what there is to learn about the SSH/SCP thing, even if it isn't related.

---

### Post by blake1024 on 2009-06-02
I haven't experienced any USB issues.  Also, I have a bunch of different machines running different versions of Ubuntu and they all experience the same scp issue.  I don't think the issue is related to my machine or configuration since virgin installs on different machine don't work.

---

### Post by detroit/zero on 2009-06-02
I'm in a similar boat with my problem - two laptops, one running hardy and one recently upgraded with a fresh install of Jaunty.

---

### Post by blake1024 on 2009-06-02
I see the problem all over the net.  I'd think it would be considered a high priority issue.  Mum is the word from the higher ups.

---

### Post by detroit/zero on 2009-06-02
I've been seeing problems in my google searches going back to 2005 that talk about this problem. One temporary fix I've run across (you may also have seen it) is to add the following to the */etc/sysctl.conf* files of your computers:```
zero@zero-laptop:~/Desktop$ cat /etc/sysctl.conf
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.  (Added in kernel 2.6.22.)
kernel.maps_protect = 1

# Increase inotify availability
fs.inotify.max_user_watches = 524288

# protect bottom 64k of memory from mmap to prevent NULL-dereference
# attacks against potential future kernel security vulnerabilities.
# (Added in kernel 2.6.23.)
vm.mmap_min_addr = 65536

##############################################################3
# Functions previously found in netbase
#

# Comment the next two lines to disable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling (http://lkml.org/lkml/2008/2/5/167)
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net/ipv4/icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net/ipv4/icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net/ipv4/conf/all/accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net/ipv4/conf/all/secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net/ipv4/conf/all/send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net/ipv4/conf/all/accept_source_route = 0
#
# Log Martian Packets
#net/ipv4/conf/all/log_martians = 1
#
# Always defragment packets
#net/ipv4/ip_always_defrag = 1
[B]
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1[/B]
```
To test it out, on your primary host, issue ```
sudo sysctl -p
```at a terminal, then ssh into a test client and do the same. For me, it stops the constant stopping/starting and outright stalling. But it seems to have some drawbacks on speed. Maybe it's just me.

I guess there's a way to add sysctl to your modules at startup, but you have to add another module to load before sysctl does. You'll want to read up on that to see the specifics. I'd point you in a direction, but I found it in a google search somewhere along the line. If I remember right (and judging by the options entered in the sysctl.conf file), this is for disabling IPV6 addressing, which enabled by default (and harder than hell to get rid of) in Jaunty.

Side question: Do you use NFS to share folders? Can you confirm the same stopping/starting and stalling when transferring files via NFS?

---

### Post by blake1024 on 2009-06-02
I tried that on 8.10 with no luck.  I just tried it on 9.04 with no luck still.  I don't think that fixes anything.  Some people say it fixed the problem only to say it stopped working again.  I think some people have marginal speed issues that actually work sometimes so it is hard to tell if you have a fix.  My situation is completly reproducable.

Thanks anyway.

Blake McBride

---

### Post by abhayani on 2009-09-10
Hi Guys, I am on ubuntu 9.04 and also face same problem. Have tried everything that's posted on this thread but no luck so far. Any help is highly appreciated. I will try with my soalris machine tomorrow. Thanks

---

### Post by kenm_uk on 2010-09-01
I am having a similar problem...any solutions in the last year?

---

### Post by r.osmanov on 2010-09-06
> **kenm_uk said:**
> I am having a similar problem...any solutions in the last year?

Mine stalled on about 100K. And I've occasionally fixed it just now:
[LIST=1]
[*] removed ```
vm.swappiness=10
``` from /etc/sysctl.conf
[*] ```
sudo sysctl -p
```
[/LIST]

My /etc/sysctl.conf:
```
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
```

---

### Post by kenm_uk on 2010-09-06
Thanks for your reply.  However, I don't have a vm.swappiness line on my client machine (although I thought I did).
cat /proc/sys/vm/swappiness
returns the value 60.

I already had the lines you posted in my /etc/sysctl.conf file.

Also I have tried sudo swapoff -a

But with or without the swap, scp still falls from 2MB/s to 10-30KB/s after a few minutes of attempting to copy a large file within my home network.

Any other suggestions?

Thanks.

---

### Post by hedgehock on 2010-12-10
I've got an identical problem and all the fixes mentioned here don't work either. I wonder whether this could have something to do with my network card running on top of a b43 driver. What steps could I take in order to diagnose this? Also someone mentioned in a post elsewhere to remove Firestarter. I did so, yet no luck. My Ubuntu is 10.10 64-bit. I've got all the latest updates intact.

Quite frankly I couldn't really imagine a more serious issue. This should be taken care of. Also I'd be glad for some explanation as to what is it exactly, that is/might be causing the problem.

EDIT: Ok, not sure what happened, but the problem seems over. I removed all the patches from the sysctl file. Firestarter is still removed. One think to note is that, scp still has this weird kick-start where it looks like it instantly uploaded a few M during the first second of transfer. However after a while it slows down, but continues at a sensible pace.

---

### Post by r.osmanov on 2010-12-11
> **hedgehock said:**
> 
EDIT: Ok, not sure what happened, but the problem seems over. I removed all the patches from the sysctl file. Firestarter is still removed. One think to note is that, scp still has this weird kick-start where it looks like it instantly uploaded a few M during the first second of transfer. However after a while it slows down, but continues at a sensible pace.

I haven't Firestarter on my new 64-bit Ubuntu 10.10. However, problem had place. I wonder, it seems, installing Firestarter made things better this time:). Nevertheless, I'm using the following alias instead of scp now:
```
$ grep scp ~/.bash_aliases
alias myscp='rsync --progress --partial --rsh="ssh -p 8322"'
```
It allows to resume a stalled operation.

---

### Post by kenm_uk on 2010-12-19
I eventually found the problem. I had dome something really silly!  I am running DD-WRT on a router for a few of my machines (sort of a sub-network).  I set some QoS settings and used parameters reasonable for my broadband connection.  However, when transferring files internally at home these values were too low and resulted in the slow/stalled scp speeds.  So, in my case, the problem was my own silly human error! ](*,)

---

### Post by r.osmanov on 2010-12-21
Found interesting thing. It seems, my ISP blocks connection on fast rates. When I limit bandwidth (--bwlimit=KBPS for rsync and -l Kbit/s for scp), it works without stalls :o

Yep, I've got rates even over the bandwidth limit(that I should have according to agreement with ISP) on some ports(e.g. 22, 8322). But, as it turns, those connections are simply dropped, when ISP considers that it is too fast for me... 8-[

---

### Post by seventeener on 2010-12-27
Had the same problem when copying files over a wireless network. The problem has been partially solved by turning OFF the "WMM Enable: (Wireless QoS)" on my D-LINK DIR-300 wireless router (it was ON in the default configuration). Now the scp speed varies around 500KB/s with no stalls. The new bottleneck seems to be the Atom CPU of my netbook.

UPD: I've updated the wireless driver using compat-wireless, this has improved the over-the-air scp speed to approx. 800KB/s.

---

### Post by diwan on 2011-08-28
I have problem with stalled scp and intermittent connection with scp. I don't know where the error, either at router or at isp (comcast). The strange thing is when I use winscp the process is smooth. Now,I installed wine and run winscp portable with wine and running smoothly !!

My guess is always not trusting isp. when scp stalled all internet is stalled (cannot connect with firefox browser, etc), network activity up and down..i can see download run 30 sec and stop for 1 minute or more but the longest burst with scp is 30 sec.

With other isp, att or other local provider, it runs smoothly ! but of course it on different router. 

Is it router problem or isp problem ? but why winscp consistently better ??

Thanks for your input !

diwan

---

