---
title: "can't resolve hostname for ping/ssh (yes it is in /etc/hosts)"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by kalyp on 2011-01-07
Hello,

I have a weird problem since yesterday that I can't solve. I can't ping / ssh my machine anymore using its hostname... says "unknown host", "network unreachable". I have no idea why - it used to work perfectly. I can still ping / ssh using the IP so it must be a problem of hostname not being resolved. 

I have a dynamic IP (I'm at work...) but that doesn't seem to be the problem - network manager automatically adds a line in /etc/hosts with <mycurrentip> <hostname> (I checked, it's indeed the IP given by ifconfig and that I can use to ping/ssh).

Last thing nslookup <hostname> returns
"*** Can't find <hostname>: No answer"

I have no idea what's going on, so any help appreciated!!! thanks in advance!!!

---
2nd bonus question: another computer has a similar problem but slightly different: the hostname is resolved but points to a wrong IP (seen in ping or nslookup), different from what ifconfig returns. As a result, ping times out and ssh says "no route to host". I'm pretty sure I had that problem before but can't remember how I solved it...

---

### Post by Brandon Williams on 2011-01-08
It's not completely clear how you are expecting the name to be resolved. You refer to both /etc/hosts and nslookup results, but nslookup doesn't use /etc/hosts. Also, are you trying to ping/ssh to the machine you're on? or a remote machine? The value added to /etc/hosts by network-manager is only relevant if you're trying to connect to the machine you're on.

If you're expecting the names to be resolved from /etc/hosts, you should check the setting for "hosts" in /etc/nsswitch.conf. On my system, it's "files dns" so that /etc/hosts will be checked before dns. If it doesn't at least include "files", then /etc/hosts will never be checked.

If you're expecting dns to handle the resolution, then make sure that your nameserver configuration is correct. Do you know the correct IP address for the network's dns server? And if so, does that match the value for "nameserver" in /etc/resolv.conf? If it does not, then try running "nslookup hostname dnsip", where hostname is the one you're looking up and dnsip is the correct IP for the network's dns server. Does that work? If it does, then you'll need to correct the setting in /etc/resolv.conf, and also figure out why it isn't being configured correctly in the first place.

If the correct dns server is unable to resolve the hostname, then there is either a problem with your dhcp client configuration or the network's dhcp server and/or dns server.

---

### Post by kalyp on 2011-01-08
Hi Brandon and thanks a lot for your detailed answer!

I'm at home now so cannot check the machine, I'll look on Monday.
When I said ping/ssh that was from a remote machine. I was testing things at work between 2 machines on the same network, the goal is to be able to ssh/vnc my machine from home (connected through VPN) to launch work job from home if needed. Which used to work perfectly in the past and suddenly not anymore as I cannot connect to the machine using its hotsname anymore.

So I don't know if I'm expecting /etc/hosts or dns to handle the resolution :) I don't know which one did before... I'm pretty sure /etc/nsswitch.conf says 
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

I'll check that, and the /etc/resolv.conf and DNS server IP, on Monday, and will keep you posted.

Thanks again!

---

### Post by Brandon Williams on 2011-01-08
It sounds like you're counting on the enterprise DNS for resolution on the remote machine, which means the content of /etc/hosts on the machine you're trying to connect to won't matter. It also sounds like 1 machine is unable to connect to the enterprise DNS and the other machine is, but that even the machine that can connect to the enterprise DNS is getting a bad answer, probably because the hostname isn't being updated in the enterprise DNS when you get a new address via dhcp. Those are the things to look for first when you get back in to the office next week.

---

### Post by kalyp on 2011-01-08
In that case would that mean the problem comes from the enterprise, not me? That could explain why it appeared suddenly and why I have problems with a 2nd machine too.
How can I check that the hostname is being updated in the enterprise DNS when I get a new address via dhcp?
Thanks again!

---

### Post by Brandon Williams on 2011-01-09
If you know the enterprise dns server's address, then run ```
nslookup hostname <dns address>
``` When you run nslookup this way, the third argument tells it which dns server to ask. If the enterprise dns returns the wrong address, then there's something wrong somewhere. It could be that your dhcp client isn't sending the correct hostname to the dhcp server when it requests an address, or it could be that the dhcp server isn't correctly updating the dns server when it hands out an address. You don't have a hostname specified in your dhclient.conf file do you? If you have the wrong hostname there, it will prevent dns from being updated for the hostname that you expect. dhclient should send the system-wide hostname if no alternate is specified in dhclient.conf, but you could always try explicitly specifying one in dhclient.conf, just to see if the problem clears after that.

Note that this doesn't apply to the machine where the lookup times out, since that machine doesn't appear to be asking the right dns server anyway. But once it starts talking to the right dns server, it might still not be getting the right address for the hostname.

---

### Post by kalyp on 2011-01-10
ok so here is where I am.
resolv.conf has 3 lines with "nameserver", testing the 3 corresponding IP with nslookup give the same answer which is the same as without specifying an IP (ie can't find <hostname>). I'm pretty sure the 1st one is indeed the enterprise dns IP (found it on a google search on the intranet as "DNS server: <name> IP address: <IP I have>" (can't access the page I don't have rights).

I checked dhclient.conf, there wasn't a hostname there, I tried replacing <hostname> in "send host-name "<hostname>";" by my hostname, doesn't change anything.

As for the machine that times out, I think it asks the right dns server as resolv.conf gives the same 3 IP (and nslookup gives the same answer for the 3 IP, and it's a different number than ifconfig and /etc/hosts).

Last thing, I tried a 3rd machine which is not Ubuntu (RHE), on the same network, and resolv.conf is the same, nsswitch is files dns too, /etc/hosts doesn't contain the IP but nslookup and ifconfig give the same answer, which is also the IP being pinged when I ping the hostname from another machine. In other words, it works perfectly so that I'm afraid it's something related to ubuntu (both machines with problems run maverick), not a network problem... 

I have no idea what's going on :(
thanks again...

---

### Post by Brandon Williams on 2011-01-10
Just to be sure I understand, you're saying that you've got three different nameserver addresses, lets say that one of them is 192.168.1.1, and that running "nslookup hostname 192.168.1.1" on two different machines, the RHE machine and a maverick machine, returns different results? What if you run "dig @192.168.1.1 hostname" on the two machines? 

It simply doesn't make sense that asking the same dns server to resolve the same hostname returns different results on two different client machines. When you explicitly specify the dns server on the command line, the local config will have nothing to do with the answer you get back. I could understand the request timing out on one machine due to a bad network config, but you seem to be indicating that you got an incorrect response on the bad machine (as opposed to "connection timed out"). Am I understanding your explanation correctly? And if so, are you absolutely certain that the command lines used on both machines are exactly the same?

Another thing is that you've said that nsswitch.conf is different on the RHE machine and the Ubuntu machines. What happens if you modify nsswitch.conf on the Ubuntu machines so that the "hosts:" line matches what's in the RHE config?

---

### Post by kalyp on 2011-01-10
No I think I wasn't clear sorry. Running "nslookup hostname 192.168.1.1" give the same answer in all machines - simply different hostnames give different types of answers. The machines are anthias (1st ubuntu machine, doesn't resolve at all), poisson (2nd ubuntu machine, points to the wrong IP) and npzd (RHE, works) and nslookup give "*** Can't find anthias: No answer" for anthias, a wrong IP for poisson, and the correct IP for npzd (results are the same when running nslookup on any machine).

Note that when I ping anthias and poisson locally, ping gets the right answer. In other words for poisson for instance, what prints on screen is 
PING poisson.<domain> (<wrongIP>) 56(84) bytes of data from anthias/npzd,
PING poisson.<domain> (<rightIP>) 56(84) bytes of data from poisson.
Although ping from poisson pings the right IP, nslookup from poisson returns the wrong IP.

The "hosts:" line is "files dns" on npzd (RHE), "files dns mdns4_minimal [NOTFOUND=return] mdns4" on anthias and poisson, so it should do the same thing right? 

I sent an email to the network guys asking them to check on their side if something got mixed up, waiting for their answer...

---

### Post by kalyp on 2011-01-10
ok so update! the network guy replied:
"There are two things going on here. The first is that you need to disable IPV6 in you network settings on anthias. anthias's listing in DNS is for an IPV6 address right now. 
The second is that the <wrongIP> address for poisson is the wireless address. You can turn your wireless off to ensure that the DNS entry for poisson is on your wired connection."
He deleted both DNS entries, a restart on poisson with wireless off solves the problem, I haven't tried to disable ipv6 & restart anthias yet as I'm working on it right now - will keep posted and mark the thread as solved if that works.

So in other words, somehow the DNS entry got mixed up for both computers, one being assigned to the wireless connection instead of wired one (wireless not being on the network...), the other one being assigned to ipv6 (I don't know anything about that). 

Is there any setting I could change on the computer to force DNS to be assigned to the wired connection when present? ie. avoid that problem without switching off the wireless and ipv6? I don't know what ipv6 is for (ie. if I won't mind having it off) but I know that when I switch the wireless off I tend to forget about it and wonder for a while why my computer doesn't connect...

Anyway, thanks much Brandon. You made me realize that there was probably something wrong on the network side rather than on my side... the way I was headed I would have searched forever without thinking of asking them.

---

### Post by kalyp on 2011-01-10
Last update. Disabled ipv6 and started anthias, problem solved....
Still interested if there's a way to avoid disabling wireless/ipv6!
Thanks again to Brandon!

---

### Post by kalyp on 2011-01-10
Actually I have one more update... The anthias problem seems to be linked to [http://ubuntuforums.org/showthread.php?t=1471622](http://ubuntuforums.org/showthread.php?t=1471622). I just activated samba before the problem appeared (which I noticed but couldn't find any link). I just noticed that it had been disabled, and couldn't reactivate it through nautilus, I expect it to be because of ipv6 being disabled. (don't ask me why). So maybe activating samba activated ipv6 which lead to one of my problems... 

Now I need to find a way to have samba work without ipv6... not working so far :(

[edit] working now. Not sure how I did it. Reinstalled samba from synaptic, had to reinstall samba-common-bin for some reason, and it seems ok... so far.

---

