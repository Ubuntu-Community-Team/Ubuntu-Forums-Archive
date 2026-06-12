---
title: "Samba problem"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by decrepit on 2011-01-06
I have 2 computers on my local network, percy has the internet connection and last week I installed 10.04 on it. charlie has an old version of centos.

percy and charlie have been talking to each other for many years with different flavours of linux.

I set up samba on percy and it worked as always, when "network" is selected
percy and charlie come up and both computers can be browsed.

I then followed the instructions for masquerading, and charlie could then use the internet.

But, that killed samba, figured that the firewall was to blame, sure enough turn firewall off and samba was back to normal.
So after some research I added this to /etc/rc.local 
```
iptables -A INPUT -p ALL -i eth1 -s 10.0.1.0/30 -j ACCEPT
iptables -A INPUT -p ALL -i eth1 -d 10.0.1.255 -j ACCEPT
```

Now I've got half samba back, percy can see charlie but charlie can't see percy, and strangely when selecting "network" from percy only charlie appears.
But from percy if I
```
michael@Percy:~$ nautilus smb://10.0.1.1
michael@Percy:~$ nautilus smb://10.0.1.2
```

I get both sets of shares, however if I do the same from charlie I get a message saying "sorry couldn't display 10.0.1.1"

I had a look at smb.conf and at the bottom there was these lines.

```
[michael]
	comment = mike's home
	path = /home/michael

;	browseable = yes
	guest ok = yes
	available = no
	writeable = yes
```

So I changed the "no" to "yes"
but that hasn't made any difference.

Any ideas, anybody?

---

### Post by decrepit on 2011-01-08
I've been thinking about this, and I don't think this has anything to do with the firewall.
If I turn the firewall off, the problem is still there, "percy" does not appear on either computer.

I had 2 goes at installing samba, the first time through synaptic package manager, didn't install the gui, I had a go at set up with smb.conf but when I went to System > Preferences > Personal File Sharing, I got an error message saying "This feature cannot be enabled because the required packages are not installed"

So I did an "apt get samba" from the command line, that installed another 2 packages, 1 of them the gui.
That may have been when the problem started.

So should this computer's name appear in the gui?

There's a line labeled "description" under "workgroup" that has

%h server (Samba, Ubuntu)

in it. Is this where "percy" should be?

---

### Post by dandnsmith on 2011-01-08
I'd be looking at the routes set on each machine, but especially percy.
I suspect that all traffic is being routed to the internet (I use route print in a terminal window, being 'old school').
Also a simple ping test from charlie to percy (using IP address?) might be interesting.

---

### Post by decrepit on 2011-01-08
> **dandnsmith said:**
> I'd be looking at the routes set on each machine, but especially percy.
I suspect that all traffic is being routed to the internet (I use route print in a terminal window, being 'old school').
Also a simple ping test from charlie to percy (using IP address?) might be interesting.

Thanks Derek,

I tried "route print" but that didn't work, came up with a list of options I didn't understand.

And ping works both ways, charlie can see percy and percy can see charlie.

Samba also works fine from percy, in that it has full access to charlie's shares. But unlike before, "percy" doesn't show up on either network.

---

### Post by dandnsmith on 2011-01-09
Sorry, gave the wrong version there - should just be *route* (the route print is the Windows version).

Next, after the ping, I'd look in the log files for smbd and nmbd, having first established that the processes are running, especially on percy (where the trouble is centred).

---

### Post by decrepit on 2011-01-09
Thanks Derek,
OK that did it.

```
michael@Percy:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
nexthop.wa.iine *               255.255.255.255 UH    0      0        0 eth0
10.0.1.0        *               255.255.255.252 U     1      0        0 eth1
124.150.52.0    *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         nexthop.wa.iine 0.0.0.0         UG    0      0        0 eth0

```

Doesn't mean much to me I'm afraid. except the 2nd line, that's my lan.

Not sure how to check if smb and nmb are running.
In fedora, you can check every service from a gui and turn it on or off. 
But I can't find that in ubuntu. The closest is "start up applications", but that doesn't mention either of those.

But if they weren't running, would I be able to browse charlie's shares from percy?

---

### Post by decrepit on 2011-01-09
Just checked with "system monitor", doesn't show either of them running.
I tried double clicking on "windows network" and with charlie turned off, I just get, 
"unable to mount location.  Failed to retrieve share list from server"

And still system monitor shows no activity from smb or nmb

Also if I try to use "system" > preferences > personal file sharing, it tells me I don't have the right software installed.
Could this be another indication samba isn't running?

How do I make sure it is?

---

### Post by decrepit on 2011-01-09
OK, found the command on another thread.

```
michael@Percy:~$ sudo service smbd start
start: Job is already running: smbd
michael@Percy:~$ sudo service nmbd start
start: Job is already running: nmbd
```

So looks like they are both running.

---

### Post by dandnsmith on 2011-01-09
You may get some mileage out of 
*smbclient -L machinename* putting in percy or charlie
also
*nmblookup* (check man pages?)

samba.org/docs contains links to sources of testing docs.

The route printout looked OK to me - not really surprised after pings reported working both ways.

In /var/log you should find lots of logs - including those from smbd and nmbd. Might be something there.

---

### Post by decrepit on 2011-01-10
Thanks Derek,
Had a quick look thru the logs, this looks significant, from the log.nmbd

> [2011/01/09 22:53:54,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name PANDC<1b> for the workgroup PANDC.
  Unable to sync browse lists in this workgroup.
[2011/01/09 22:53:54,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name PANDC<1b> for the workgroup PANDC.
  Unable to sync browse lists in this workgroup.
[2011/01/09 22:59:30,  0] nmbd/nmbd.c:71(terminate)
  Got SIGTERM: going down...
[2011/01/10 18:42:17,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2011/01/10 18:42:42,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 10.0.1.1
  
  *****
[2011/01/10 18:42:45,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name PANDC<1b> for the workgroup PANDC.
  Unable to sync browse lists in this workgroup.
[2011/01/10 18:47:51,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 124.148.192.64
  
  *****
[2011/01/10 18:48:02,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name PANDC<1b> for the workgroup PANDC.
  Unable to sync browse lists in this workgroup.

So do I need to set master browser in smb.conf?

---

### Post by dandnsmith on 2011-01-10
Looks like it would be a good idea, judging by those messages - I'd certainly set it in percy's smb.conf

Did you try the effect of smbclient -
I'd do it from percy to both charlie and percy,
and then from charlie to both - sometimes you get a little more info from it (and should get confirmation of where any shares are seen)

---

### Post by decrepit on 2011-01-10
Some interesting developments. I cheated, renamed smb.conf and copied an old fedora smb.conf into /etc/samba. Bingo Percy appears again, had to change a few things, as I was mike on fedora and michael on ubuntu.

Opened up the samba configuration gui, and lost percy again. 
Seems when you start the gui smb.conf losses it's settings and gets the default gui settings.

I think I'll just go back to the fedora file and configure it manually.

I'll get back later with any progress.

---

### Post by decrepit on 2011-01-10
woops sorry derek, didn't see your reply.

didn't have much luck with smbclient, got an error message, with a list of options, none of them machinename.
I've had enough tonight, I'll try again tomorrow.
Mike

---

### Post by dandnsmith on 2011-01-10
> **decrepit said:**
> 
Opened up the samba configuration gui, and lost percy again. 
Seems when you start the gui smb.conf losses it's settings and gets the default gui settings.


I think I noticed some behaviour like that at one point - after the initial attempt (my latest setup with Ub 10.04) I too copied an old file and hand-edited that 'til it worked.

---

### Post by decrepit on 2011-01-12
Well it's looking better, log.nmbd shows.

[> 2011/01/11 22:44:11,  0] nmbd/nmbd.c:71(terminate)
  Got SIGTERM: going down...
[2011/01/12 14:44:22,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2011/01/12 14:44:55,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 10.0.1.1
  
  *****
[2011/01/12 14:50:14,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 203.206.93.154
  
  *****

But log.smbd shows

> [2011/01/12 14:44:20,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2011/01/12 14:44:20,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2011/01/12 14:44:20,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use

And percy is still not showing on the network, although he did appear for a while the other day.

I'll keep plugging away, but in the meantime, any idea what the above socket and address is?

---

### Post by decrepit on 2011-01-12
OK another development, I noticed this.

> Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 10.0.1.1
  
  *****
[2011/01/12 20:41:27,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 58.7.148.22

Seems samba uses an address of it's own, the 58.7.22. and it's different every time it starts.
I haven't enabled these addresses in the firewall. So I turned firewall off, and up pops percy.
Trouble is without the firewall there's no masquerading and charlie can't access the net. So it's back to the firewall again.

---

### Post by dandnsmith on 2011-01-12
Those 2 IP addresses which aren't 10.0. must be getting assigned somewhere.

You have 2 network ports on percy - one will be to talk to charlie (10.0.x.y), the other for the internet. The latter I suggest is being assigned by your ISP to your internet connection (something to check when its running).

The firewall and masquerade may be tied up with the routing I mentioned previously - a problem getting the traffic to go to the right interfaces.
I seem to remember getting a problem like this a long time ago (but don't remember if I got the resolution). There is an equivalent problem using windows PCs - and this could usually be fixed with the correct proxy (for which I know no equivalent - that is where the masquerading comes in).

With my own systems, there is no such problem, as it is all taken care of by a hardware modem/router.

I think if you tried the smbclient, you should (rationally) get results when you disable the firewall.

---

### Post by dandnsmith on 2011-01-12
Something amiss with the forum there - told me I had to wait 20 secs between posts before any notification that I'd posted (the first time)

---

### Post by decrepit on 2011-01-13
> **dandnsmith said:**
> Those 2 IP addresses which aren't 10.0. must be getting assigned somewhere.

You have 2 network ports on percy - one will be to talk to charlie (10.0.x.y), the other for the internet. The latter I suggest is being assigned by your ISP to your internet connection (something to check when its running).

The firewall and masquerade may be tied up with the routing I mentioned previously - a problem getting the traffic to go to the right interfaces.
I seem to remember getting a problem like this a long time ago >>>>>>l.

OK thanks again Derek, I realised my hypothesis about samba using the 58.7---- was rubbish, then wondered about your earlier "route theory".
I also wondered about the 127 loopback thing, as I didn't rember setting it.
So first theing I tried was this from a fedora firewall.

```
iptables -A INPUT -p ALL -i lo -s 127.0.0.1 -j ACCEPT
iptables -A INPUT -p ALL -i lo -s 10.0.1.1 -j ACCEPT
``` 

This so far has done the trick!!!

percy now appears on both computers.

But, log.nmbd still has this.
> 
[2011/01/13 21:01:07,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 124.169.186.240
  
  *****
[2011/01/13 21:16:43,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 10.0.1.1
  
  *****
Does this mean I'm broadcasting percy's shares on the net as well as on the lan?

Sorry for anybody else trying to make sense of this, I may have had 2 problems. I'm suspicious of the samba gui, but I'm not going to turn it on to test the theory.
The main problem was a badly set up firewall.

---

### Post by dandnsmith on 2011-01-13
I think, after your earlier comment and my experience you do well to avoid the samba gui.
The 127.0.0.1, in case you wondered, is the loopback interface which you will find on any networked computer, and is taken account of in the firewall for various reasons.
Your shares aren't being broadcast on the internet, as 10.0. is a 'private' address which doesn't get routed to the outside world. Further, you can safeguard it by by only allowing samba to accept on 127.0.0 and 10.0.1. interfaces

HTH

---

### Post by decrepit on 2011-01-14
Thanks Derek for all your help.

Did I say it was fixed??????

Start up today, and Percy won't appear unless the firewall is off.

I'll study up on smbclient and see if I can fix it that way.

---

### Post by ripat on 2011-01-14
On the firewalled machine give the result of:
```
$ sudo iptables-save
```

---

### Post by decrepit on 2011-01-15
Thanks ripat.

> # Generated by iptables-save v1.4.4 on Sat Jan 15 21:17:12 2011
*filter
:INPUT ACCEPT [2026:1578091]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [2005:270594]
-A INPUT -s 10.0.1.0/30 -i eth1 -j ACCEPT 
-A INPUT -d 10.0.1.255/32 -i eth1 -j ACCEPT 
-A INPUT -s 127.0.0.1/32 -i lo -j ACCEPT 
-A INPUT -s 10.0.1.1/32 -i lo -j ACCEPT 
COMMIT
# Completed on Sat Jan 15 21:17:12 2011

---

### Post by ripat on 2011-01-16
As you suspected above, the firewall is not blocking anything.

From the client, run:
```
$ smbtree -N
```or
```
$ smbclient -NL ip_samba_server
```

If no luck with that, drop your samba security level by using a basic conf file like this one:

```
[global]
	workgroup = YOUR_WORKGROUP
	security = share
[test] 
	comment = Test Samba
	path = /whatever/
	read only = no
	guest ok = yes

```

And try again the browse commands above.

---

### Post by decrepit on 2011-01-16
Woops, last night I had the firewall turned off, this is what happens with it on.

> 
michael@Percy:~$ sudo iptables-save
# Generated by iptables-save v1.4.4 on Sun Jan 16 19:40:25 2011
*nat
:PREROUTING ACCEPT [4:213]
:POSTROUTING ACCEPT [54:5879]
:OUTPUT ACCEPT [54:5879]
-A POSTROUTING -s 10.0.1.0/30 -o eth0 -j MASQUERADE 
COMMIT
# Completed on Sun Jan 16 19:40:25 2011
# Generated by iptables-save v1.4.4 on Sun Jan 16 19:40:25 2011
*filter
:INPUT DROP [3:152]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:ufw-after-forward - [0:0]
:ufw-after-input - [0:0]
:ufw-after-logging-forward - [0:0]
:ufw-after-logging-input - [0:0]
:ufw-after-logging-output - [0:0]
:ufw-after-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-before-input - [0:0]
:ufw-before-logging-forward - [0:0]
:ufw-before-logging-input - [0:0]
:ufw-before-logging-output - [0:0]
:ufw-before-output - [0:0]
:ufw-logging-allow - [0:0]
:ufw-logging-deny - [0:0]
:ufw-not-local - [0:0]
:ufw-reject-forward - [0:0]
:ufw-reject-input - [0:0]
:ufw-reject-output - [0:0]
:ufw-skip-to-policy-forward - [0:0]
:ufw-skip-to-policy-input - [0:0]
:ufw-skip-to-policy-output - [0:0]
:ufw-track-input - [0:0]
:ufw-track-output - [0:0]
:ufw-user-forward - [0:0]
:ufw-user-input - [0:0]
:ufw-user-limit - [0:0]
:ufw-user-limit-accept - [0:0]
:ufw-user-logging-forward - [0:0]
:ufw-user-logging-input - [0:0]
:ufw-user-logging-output - [0:0]
:ufw-user-output - [0:0]
-A INPUT -s 10.0.1.0/30 -i eth1 -j ACCEPT 
-A INPUT -d 10.0.1.255/32 -i eth1 -j ACCEPT 
-A INPUT -s 127.0.0.1/32 -i lo -j ACCEPT 
-A INPUT -s 10.0.1.1/32 -i lo -j ACCEPT 
-A INPUT -j ufw-before-logging-input 
-A INPUT -j ufw-before-input 
-A INPUT -j ufw-after-input 
-A INPUT -j ufw-after-logging-input 
-A INPUT -j ufw-reject-input 
-A INPUT -j ufw-track-input 
-A FORWARD -j ufw-before-logging-forward 
-A FORWARD -j ufw-before-forward 
-A FORWARD -j ufw-after-forward 
-A FORWARD -j ufw-after-logging-forward 
-A FORWARD -j ufw-reject-forward 
-A OUTPUT -j ufw-before-logging-output 
-A OUTPUT -j ufw-before-output 
-A OUTPUT -j ufw-after-output 
-A OUTPUT -j ufw-after-logging-output 
-A OUTPUT -j ufw-reject-output 
-A OUTPUT -j ufw-track-output 
-A ufw-after-input -p udp -m udp --dport 137 -j ufw-skip-to-policy-input 
-A ufw-after-input -p udp -m udp --dport 138 -j ufw-skip-to-policy-input 
-A ufw-after-input -p tcp -m tcp --dport 139 -j ufw-skip-to-policy-input 
-A ufw-after-input -p tcp -m tcp --dport 445 -j ufw-skip-to-policy-input 
-A ufw-after-input -p udp -m udp --dport 67 -j ufw-skip-to-policy-input 
-A ufw-after-input -p udp -m udp --dport 68 -j ufw-skip-to-policy-input 
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input 
-A ufw-after-logging-input -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-before-forward -j ufw-user-forward 
-A ufw-before-input -i lo -j ACCEPT 
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny 
-A ufw-before-input -m state --state INVALID -j DROP 
-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 4 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT 
-A ufw-before-input -p udp -m udp --sport 67 --dport 68 -j ACCEPT 
-A ufw-before-input -j ufw-not-local 
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT 
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT 
-A ufw-before-input -j ufw-user-input 
-A ufw-before-output -o lo -j ACCEPT 
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A ufw-before-output -j ufw-user-output 
-A ufw-logging-allow -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW ALLOW] " 
-A ufw-logging-deny -m state --state INVALID -m limit --limit 3/min --limit-burst 10 -j RETURN 
-A ufw-logging-deny -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN 
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN 
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN 
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny 
-A ufw-not-local -j DROP 
-A ufw-skip-to-policy-forward -j ACCEPT 
-A ufw-skip-to-policy-input -j DROP 
-A ufw-skip-to-policy-output -j ACCEPT 
-A ufw-track-output -p tcp -m state --state NEW -j ACCEPT 
-A ufw-track-output -p udp -m state --state NEW -j ACCEPT 
-A ufw-user-limit -m limit --limit 3/min -j LOG --log-prefix "[UFW LIMIT BLOCK] " 
-A ufw-user-limit -j REJECT --reject-with icmp-port-unreachable 
-A ufw-user-limit-accept -j ACCEPT 
COMMIT
# Completed on Sun Jan 16 19:40:25 2011
michael@Percy:~$ 


And for some reason it's decide to work properly this evening.
so both smbclient and smbtree come up with percy's expected shares.

Strange thing is log.nmd shows this.

> [2011/01/16 19:39:38,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 124.148.222.120
  
  *****
This is the internet connection not the lan.

---

### Post by decrepit on 2011-01-16
OK rebooted with firewall on.
log.nmbd now has this.

```
[2011/01/16 20:15:04,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 10.0.1.1
  
  *****
```

It's now on the lan not the net, but percy has disappeared again.

smbtree comes up with nothing.

I'll reboot with firewall just to see what happens.

---

### Post by decrepit on 2011-01-16
Yep, boot up with firewall off, then turn firewall on, system works ok.

Boot up with firewall on, percy's gone.

And nmb is back on the net not the lan

>  *****
[2011/01/16 20:33:09,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server PERCY is now a local master browser for workgroup PANDC on subnet 124.148.222.120
  
  *****

Makes no sense to me.

---

### Post by ripat on 2011-01-16
So it is a firewall issue apparently. You can start with simple rules:

```
iptables -I INPUT -p tcp --dport 135 -j ACCEPT
iptables -I INPUT -p udp --dport 137 -j ACCEPT
iptables -I INPUT -p udp --dport 138 -j ACCEPT
iptables -I INPUT -p tcp --dport 139 -j ACCEPT
iptables -I INPUT -p tcp --dport 445 -j ACCEPT

```

If it works we will fine tune the rules to tighten security.

---

### Post by decrepit on 2011-01-17
Thanks ripat, that's got it working.

I'd booted with firewall on, and couldn't see percy, entered your commands, and up it came immediately.

---

### Post by ripat on 2011-01-17
Well done!

Now you just have to add a *--source* option to tighten your security and you are set.

```
iptables -I INPUT -p xxx --source 10.0.1.0/30 --dport xxx -j ACCEPT
```

---

### Post by decrepit on 2011-01-18
OK I've added 

```
iptables -I INPUT -p tcp --source 10.0.1.0/30 --dport 135 -j ACCEPT
iptables -I INPUT -p udp --source 10.0.1.0/30 --dport 137 -j ACCEPT
iptables -I INPUT -p udp --source 10.0.1.0/30 --dport 138 -j ACCEPT
iptables -I INPUT -p tcp --source 10.0.1.0/30 --dport 139 -j ACCEPT
iptables -I INPUT -p tcp --source 10.0.1.0/30 --dport 445 -j ACCEPT
```

to /etc/rc.local

And everything now works, thanks a lot ripat.

---

