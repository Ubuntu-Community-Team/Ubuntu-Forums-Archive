---
title: "Firewall blocked for samba"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by swerdna on 2009-07-28
Hi I have Ubuntu 9.04 installed and a healthy Samba installation.

If I have the firewall, UFW, activated I cannot see my network and get this error message in Nautilus when I click "Windows Network"> failed to retrieve share list from server.

I have enabled samba by running this UFW command:```
sudo ufw allow samba
```. In the GUI GUFW I then see that these rules have been added:> 137,138/udp (samba) ALLOW anywhere
139,445/tcp (samba) ALLOW anywhere
I have edited the file /etc/default/ufw, in particular I added nf_conntrack_netbios_ns so the relevant line becomes like so:```
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"
```

Despite all that, Samba only works if I turn UFW off.

What have I missed?

Thanks
swerdna

---

### Post by ericab on 2009-07-28
did you set workgroup to "WORKGROUP" ?

install this for setting up samba options.

[http://gadmintools.flippedweb.com/index.php?option=com_content&task=view&id=16&Itemid=30](http://gadmintools.flippedweb.com/index.php?option=com_content&task=view&id=16&Itemid=30)

if you dont know how to compile from source or dont want to, you can install 'alien' and use the rpm package for install.

---

### Post by swerdna on 2009-07-28
> **ericab said:**
> did you set workgroup to "WORKGROUP" ?
I set workgroup = SWERDNA to match the other four workstations on the LAN
> install this for setting up samba options.

[http://gadmintools.flippedweb.com/index.php?option=com_content&task=view&id=16&Itemid=30](http://gadmintools.flippedweb.com/index.php?option=com_content&task=view&id=16&Itemid=30)
But I don't need to adjust samba, it works great when UFW is disabled. I configure Samba from the CLI and am an expert at it. The problem is with UFW which I have enabled for samba by using ```
sudo ufw allow  samba
```as recommended variously elsewhere. But that advice seems to be erroneous. Can you give me the correct method for configuring for Samba the UFW firewall? (The problem is that UFW is effectively the default recommended firewall and the advice out there isn't working)


> if you dont know how to compile from source or dont want to, you can install 'alien' and use the rpm package for install.No thanks, I'm good for configuring samba.

---

### Post by Iowan on 2009-07-28
I doubt it's as simple as restarting "something"...

---

### Post by swerdna on 2009-07-28
OK here's the answer:

Remove the much vaunted service-based rule for Samba with this command:```
sudo ufw delete samba
```
Replace it with port-based rules for the trusted network:
```
sudo ufw allow proto udp to any port 137 from 192.168.29.0/24
sudo ufw allow proto udp to any port 138 from 192.168.29.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.29.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.29.0/24
```
Adjusting the IP mask for individual LANs.

Sadly, the UFW fails on a service-based rule, which is probably a bug. I suppose that UFW is fairly new and is mostly left turned off, so this problem will take some time to be noticed by the bug-fixers. All will come good in time :)

---

### Post by Iowan on 2009-07-28
Well, at least there is now a workaround... Thanks for posting (hope I can remember it if/when another thread mentions a similar problem.)

---

### Post by dmizer on 2009-07-28
> **swerdna said:**
> Sadly, the UFW fails on a service-based rule, which is probably a bug. I suppose that UFW is fairly new and is mostly left turned off, so this problem will take some time to be noticed by the bug-fixers. All will come good in time :)

Please file a bug report :)

I've added your findings to my Fix Windows share browsing howto (6th link in my sig).

---

### Post by swerdna on 2009-07-29
> **dmizer said:**
> Please file a bug report :)

I've added your findings to my Fix Windows share browsing howto (6th link in my sig).
Terrific.

I've also got a write up of my Samba experiences and have [included the findings there too]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall").

---

### Post by dmizer on 2009-08-19
Per this post: [http://ubuntuforums.org/showpost.php?p=7811922&postcount=133](http://ubuntuforums.org/showpost.php?p=7811922&postcount=133) the rules posted above are reversed. They should read:

```
sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
sudo ufw allow proto udp from 192.168.1.0/24 to any port 138
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 139
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 445
```

Confirmed here: [http://ubuntuforums.org/showthread.php?t=806000](http://ubuntuforums.org/showthread.php?t=806000)

---

### Post by swerdna on 2009-08-19
> **dmizer said:**
> Per this post: [http://ubuntuforums.org/showpost.php?p=7811922&postcount=133](http://ubuntuforums.org/showpost.php?p=7811922&postcount=133) the rules posted above are reversed. They should read:

```
sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
sudo ufw allow proto udp from 192.168.1.0/24 to any port 138
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 139
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 445
```

Confirmed here: [http://ubuntuforums.org/showthread.php?t=806000](http://ubuntuforums.org/showthread.php?t=806000)
Thank you very much -- this stuff is so confusing.

Don't hese two mean exactly the same thing:
[LIST=1]
[*]sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
[*]sudo ufw allow proto udp to any port 137 from 192.168.29.0/24
[/LIST]

as per this ref: [http://log.logfish.net/node/31](http://log.logfish.net/node/31)
and this [http://www.mypcsupport.de/net/linux/ubuntu-ufw/](http://www.mypcsupport.de/net/linux/ubuntu-ufw/)
and this (#4) [http://somethinggnu.blogspot.com/2008/11/samba-and-ufw.html](http://somethinggnu.blogspot.com/2008/11/samba-and-ufw.html)
and this [http://ubuntuforums.org/showpost.php?p=6924891&postcount=4](http://ubuntuforums.org/showpost.php?p=6924891&postcount=4)

So I think probably either is valid.

Or am I missing something?

---

### Post by dmizer on 2009-08-19
No, they are not the same.

This:
sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
is an inbound rule.

This:
sudo ufw allow proto udp to any port 137 from 192.168.29.0/24
is an outbound rule.

You can confirm this yourself by looking at the configuration in gufw.

---

### Post by swerdna on 2009-08-19
AHA -- I see the difference, thank  you

---

### Post by swerdna on 2009-09-08
> **dmizer said:**
> No, they are not the same.

This:
sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
is an inbound rule.

This:
sudo ufw allow proto udp to any port 137 from 192.168.29.0/24
is an outbound rule.

You can confirm this yourself by looking at the configuration in gufw.
I've been puzzling over this. Something seemed wrong to me. 

So, with respect:

If I type your "outbound" version and take a screenshot in GUFW. Then delete the rule. Then type your "inbound" and take a screenshot. Then the two screenshots are identical.

Further, if I start with no rules and type one of the variants I get a response "rule added". Then if I type the other variant I get the response "skipping adding existing rule".

So one is not an outbound rule and the other an inbound rule. They are the same rule.

What do you think, is that right?

---

### Post by dmizer on 2009-09-08
> **swerdna said:**
> I've been puzzling over this. Something seemed wrong to me. 

So, with respect:

If I type your "outbound" version and take a screenshot in GUFW. Then delete the rule. Then type your "inbound" and take a screenshot. Then the two screenshots are identical.

Further, if I start with no rules and type one of the variants I get a response "rule added". Then if I type the other variant I get the response "skipping adding existing rule".

So one is not an outbound rule and the other an inbound rule. They are the same rule.

What do you think, is that right?

You're quite right. After quite a bit of fiddling, I think I've finally found it.

This seems to be a correct outbound rule:
```
sudo ufw allow proto udp to 192.168.1.0/24 port 137 from any
```

This seems to be a correct inbound rule:
```
sudo ufw allow proto udp from 192.168.1.0/24 port 137 to any
```

Care to confirm with some testing?

---

### Post by srivo on 2009-09-10
Thanks Swerdna I was having the same problem! Now it works. I will follow the rest of the issue.

---

### Post by swerdna on 2009-09-15
edit in progress -- and some more testing

---

### Post by swerdna on 2009-09-15
> **dmizer said:**
> You're quite right. After quite a bit of fiddling, I think I've finally found it.

This seems to be a correct outbound rule:
```
sudo ufw allow proto udp to 192.168.1.0/24 port 137 from any
```

This seems to be a correct inbound rule:
```
sudo ufw allow proto udp from 192.168.1.0/24 port 137 to any
```

Care to confirm with some testing?

OK I've got some free time and checked somewhat extensively.
For all of the following I had the connection tracking module enabled (important for other readers [see this tutorial for that module]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")).

These rules below allow Samba shares on the Ubuntu server to be seen from the server itself and from a client on the LAN:
[COLOR="Blue"]sudo ufw allow proto udp to any port 137 from 192.168.1.0/24
sudo ufw allow proto udp to any port 138 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.1.0/24[/COLOR]

These "inbound" rules (next) allow the shares to be seen from the server but not from the client:
sudo ufw allow proto udp from 192.168.1.0/24 port 137 to any
plus three more, one each for 138, 139,445

Finally, these "outbound" rules allow the shares to be seen from the server but not from the client:
sudo ufw allow proto udp to 192.168.1.0/24 port 137 from any
plus three more, one each for 138, 139,445

So I conclude that the rules in blue are correct and that the rules labelled "inbound" and "outbound" are not. The blue rules are the only ones that I can get to work that include a "trusted" network (192.168.etc.etc).

I've written them up here (for the time being, pending agreement from dmizer): [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

Do you agree dmizer?

---

### Post by uncle-c on 2009-09-15
> **swerdna said:**
> 

These rules below allow Samba shares on the Ubuntu server to be seen from the server itself and from a client on the LAN:
[COLOR="Blue"]sudo ufw allow proto udp to any port 137 from 192.168.1.0/24
sudo ufw allow proto udp to any port 138 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.1.0/24[/COLOR]


So what  do these four lines look  in the "iptables" format ? Something like this :

```


ACCEPT     udp  --  192.168.1.0/24       anywhere            state NEW udp dpts:netbios-ns:netbios-dgm 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            state NEW tcp dpt:netbios-ssn 
ACCEPT     tcp  --  windows              anywhere            state NEW tcp dpt:microsoft-ds 


```


I have Samba as a separate server but cannot view the share on my Ubuntu client's "Network Browser" even though I have no trouble accessing the share from the Ubuntu client. I have iptables on my Samba server. 

c

---

### Post by swerdna on 2009-09-15
> **uncle-c said:**
> So what  do these four lines look  in the "iptables" format ? Something like this :

```


ACCEPT     udp  --  192.168.1.0/24       anywhere            state NEW udp dpts:netbios-ns:netbios-dgm 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            state NEW tcp dpt:netbios-ssn 
ACCEPT     tcp  --  windows              anywhere            state NEW tcp dpt:microsoft-ds 


```


I have Samba as a separate server but cannot view the share on my Ubuntu client's "Network Browser" even though I have no trouble accessing the share from the Ubuntu client. I have iptables on my Samba server. 

c

I'm too much of a newbie to attempt to speak the lingo of iptables. I'm flat out getting the hang of the device they wrote to simplify the whole process (UFW).

---

### Post by dmizer on 2009-09-15
> **swerdna said:**
> I'm too much of a newbie to attempt to speak the lingo of iptables. I'm flat out getting the hang of the device they wrote to simplify the whole process (UFW).

Even though you've configured your firewall with UFW, you can still see the iptables version by looking at the output of:
```
sudo iptables -L
```

Your testing looks good to me. It will be a while before I'll be able to test this on my own, but I'm going to update my tutorial with your suggestions.

---

### Post by dmizer on 2009-09-15
Humm, just for clarification ...

> **swerdna said:**
> These "inbound" rules (next) allow the shares to be seen from the server but [COLOR="Red"]not from the client[/COLOR]:
sudo ufw allow proto udp from 192.168.1.0/24 port 137 to any
plus three more, one each for 138, 139,445

Finally, these "outbound" rules allow the shares to be seen from the server but [COLOR="Red"]not from the client[/COLOR]:
sudo ufw allow proto udp to 192.168.1.0/24 port 137 from any
plus three more, one each for 138, 139,445

Do you mean that neither of the rules I gave earlier allow the server to be seen from any clients?

---

### Post by swerdna on 2009-09-15
> **dmizer said:**
> Even though you've configured your firewall with UFW, you can still see the iptables version by looking at the output of:
```
sudo iptables -L
```

@uncle-c: here are some lines I've extracted from iptables -L:
```
Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpt:netbios-dgm 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:netbios-ssn 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpt:netbios-ns 
```

Edit: FWIW I spotted these too:
```
Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
```

---

### Post by uncle-c on 2009-09-15
Thanks. The first table is identical to my iptables firewall rules. So can you see your Samba shares from the "Network Browser" on your samba client machine ?

c

---

### Post by swerdna on 2009-09-15
> **dmizer said:**
> Humm, just for clarification ...



Do you mean that neither of the rules I gave earlier allow the server to be seen from any clients?

I can't remember any more. It was quick, no resetting of Samba and so on. So I'll do this controlled test and then report back:

your "outbound" rules
your "inbound" rules
my blue rules

After each removal of old rules and setting of the next set of rules I will reboot before testing the visibility of the server from Nautilus in the server and from Nautilus in the client.

---

### Post by swerdna on 2009-09-15
> **uncle-c said:**
> Thanks. The first table is identical to my iptables firewall rules. So can you see your Samba shares from the "Network Browser" on your samba client machine ?

c
Yes

---

### Post by swerdna on 2009-09-15
OK I've finished that test, this time with booting to re-zero everything. Results are:


Your outbound rules
sudo ufw allow proto udp to 192.168.1.0/24 port 137 from any
sudo ufw allow proto udp to 192.168.1.0/24 port 138 from any
sudo ufw allow proto tcp to 192.168.1.0/24 port 139 from any
sudo ufw allow proto tcp to 192.168.1.0/24 port 445 from any

sudo ufw status gives
To                         Action  From
--                         ------  ----
192.168.1.0/24 137/udp     ALLOW   Anywhere
192.168.1.0/24 138/udp     ALLOW   Anywhere
192.168.1.0/24 139/tcp     ALLOW   Anywhere
192.168.1.0/24 445/tcp     ALLOW   Anywhere

server is visible and shares can be opened from Nautilus in the Ubuntu server
server is visible and shares can be opened from Nautilus in the openSUSE client

============================================================

Your inbound rules
sudo ufw allow proto udp from 192.168.1.0/24 port 137 to any
sudo ufw allow proto udp from 192.168.1.0/24 port 138 to any
sudo ufw allow proto tcp from 192.168.1.0/24 port 139 to any
sudo ufw allow proto tcp from 192.168.1.0/24 port 445 to any

sudo ufw status gives
To                         Action  From
--                         ------  ----
Anywhere                   ALLOW   192.168.1.0/24 137/udp
Anywhere                   ALLOW   192.168.1.0/24 138/udp
Anywhere                   ALLOW   192.168.1.0/24 139/tcp
Anywhere                   ALLOW   192.168.1.0/24 445/tcp

server is not visible from Nautilus in the Ubuntu server
server is not visible from Nautilus in the openSUSE client

============================================================

My blue rules
[COLOR="Blue"]sudo ufw allow proto udp to any port 137 from 192.168.1.0/24
sudo ufw allow proto udp to any port 138 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.1.0/24[/COLOR]

sudo ufw status gives
To                         Action  From
--                         ------  ----
137/udp                    ALLOW   192.168.1.0/24
138/udp                    ALLOW   192.168.1.0/24
139/tcp                    ALLOW   192.168.1.0/24
445/tcp                    ALLOW   192.168.1.0/24

server is visible and shares can be opened from Nautilus in the Ubuntu server
server is visible and shares can be opened from Nautilus in the openSUSE client

============================================================

The two sets of rules that work are dmizer's outbound rules and my blue rules.

BUT dmizer's "outbound" rules  appear to allow from "anywhere" which to me means all IP networks, whereas the "blue" rules restrict to one "trusted" subnet. (maybe -- I'm really confused by all of this now).

---

### Post by GrzesiekC on 2010-06-10
Hi,

I had same issue - can not browse windows network from Ubuntu 10.04 with ufw/gufw enabled. I have added this to /etc/default/ufw:

> # The nf_contrack_netbios_ns has been added
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"

and restart IPTABLES.

I do not have any other rules for samba. Everything seams to work now.

PS. Tip source:
[http://ubuntuforums.org/showpost.php?p=6924891&postcount=4](http://ubuntuforums.org/showpost.php?p=6924891&postcount=4)

Cheers all

---

### Post by djpemberton on 2010-07-01
I followed[COLOR=Black] [GrzesiekC]("http://ubuntuforums.org/member.php?u=1092819")'s[/COLOR] post and it worked, without any rules being made for ufw. I'm ignorant though. What did it do?

---

### Post by w_barnes on 2011-02-19
Hi, I'm also having problems with the firewall blocking netbios. I've read through the thread and set up my firewall as recommended. Here is the output of "ufw status verbose":

```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
137/udp                    ALLOW IN    10.0.0.0/24
138/udp                    ALLOW IN    10.0.0.0/24
139/tcp                    ALLOW IN    10.0.0.0/24
445/tcp                    ALLOW IN    10.0.0.0/24
```I use "mount -t cifs" to mount my windows share and if the firewall is off it works fine and I can ping the netbios name too. With the firewall active the mount fails unless I include "ip=10.0.0.3" in the mount options and ping returns with "unknown host".

I took a look at my UFW log file and it appears every time there is an attempt to resolve the windows netbios name, Windows sends its reply to a different, random port:

```
[UFW BLOCK] IN=eth0 OUT= MAC=00:07:95:da:8e:81:00:26:f2:56:a0:fc:08:00 [COLOR=Black]SRC=10.0.0.3[/COLOR] DST=10.0.0.2 LEN=90 TOS=0x00 PREC=0x00 TTL=128 ID=19692 PROTO=UDP [COLOR=Black]SPT=137[/COLOR] [COLOR=Red]DPT=56352[/COLOR] LEN=70 
[UFW BLOCK] IN=eth0 OUT= MAC=00:07:95:da:8e:81:00:26:f2:56:a0:fc:08:00 [COLOR=Black]SRC=10.0.0.3[/COLOR] DST=10.0.0.2 LEN=90 TOS=0x00 PREC=0x00 TTL=128 ID=23091 PROTO=UDP [COLOR=Black]SPT=137[/COLOR] [COLOR=Red]DPT=57116[/COLOR] LEN=70 

```I'd rather not open up the firewall to accept any UDP connection from 10.0.0.0/24 so how do I tell windows to always use the correct port?

---

