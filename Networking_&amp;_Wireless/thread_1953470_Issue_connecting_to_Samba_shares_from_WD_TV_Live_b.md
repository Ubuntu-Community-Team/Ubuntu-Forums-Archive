---
title: "Issue connecting to Samba shares from WD TV Live box"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by welshy20 on 2012-04-06
I have an issue that's been bugging me for a couple of days, I've had it working in the past so I know it CAN be solved but I'm getting to my wits end trying to work it out.

I have a server which I've had to rebuild from scratch due to disk failure, running Ubuntu Server 10.4 w/Samba.

The server primarily hosts music for streaming to other PCs or to my WD HD TV Live box which is downstairs. I have imported the smb.conf and interfaces files from my previous installation so there are no changes, the server is configured with a static IP @ 192.168.1.4/24 with the WD box @ 192.168.1.12/24. All machines are in a workground config named WIFITEST, no domain config is in use.

I am able to connect to shares fine using IP but not host name, first thoughts are that this is of course a DNS issue but the problem is that I've NEVER had a stand alone DNS server on the network to handle host records so there was clearly something else in use, maybe a NetBIOS implementation but I can't for the life of me remember what I'd been using.

The WD box has no means of direct connection via IP (it can only pick up hosts which advertise on the network) so I'm stuck until I can get this working. Likewise there is no hosts file I can edit on the WD box to use the usual hosts workaround where proper DNS isn't available.

I've read around that the issue may very well be caused by a problem with nmbd (which is running) but I don't know where to start and reading the comments in the conf file isn't getting my any further, has anyone any ideas how I can get the server to broadcast it's host/NetBIOS name? I have a Windows 7 laptop which does show up on the WD box and I have had this config working fine up until the rebuild so it's totally possible.

I've attatched my interfaces, resolv .conf and smb.conf files for info. smb.conf is the new conf that I've tried to write from scratch, smb.conf.old is the old file which I've also attempted to use.

Thanks in advance,

---

### Post by capscrew on 2012-04-07
> **welshy20 said:**
> I have an issue that's been bugging me for a couple of days, I've had it working in the past so I know it CAN be solved but I'm getting to my wits end trying to work it out.

I have a server which I've had to rebuild from scratch due to disk failure, running Ubuntu Server 10.4 w/Samba.

The server primarily hosts music for streaming to other PCs or to my WD HD TV Live box which is downstairs. I have imported the smb.conf and interfaces files from my previous installation so there are no changes, the server is configured with a static IP @ 192.168.1.4/24 with the WD box @ 192.168.1.12/24. All machines are in a workground config named WIFITEST, no domain config is in use.

I am able to connect to shares fine using IP but not host name, first thoughts are that this is of course a DNS issue but the problem is that I've NEVER had a stand alone DNS server on the network to handle host records so there was clearly something else in use, maybe a NetBIOS implementation but I can't for the life of me remember what I'd been using.

The WD box has no means of direct connection via IP (it can only pick up hosts which advertise on the network) so I'm stuck until I can get this working. Likewise there is no hosts file I can edit on the WD box to use the usual hosts workaround where proper DNS isn't available.

I've read around that the issue may very well be caused by a problem with nmbd (which is running) but I don't know where to start and reading the comments in the conf file isn't getting my any further, has anyone any ideas how I can get the server to broadcast it's host/NetBIOS name? I have a Windows 7 laptop which does show up on the WD box and I have had this config working fine up until the rebuild so it's totally possible.

I've attached my interfaces, resolv .conf and smb.conf files for info. smb.conf is the new conf that I've tried to write from scratch, smb.conf.old is the old file which I've also attempted to use.

Thanks in advance,
I think the WD media player uses netbios to find the different hosts (computers).  

I see a couple of things that I would change and I have some questions.  The questions first: a. What version of Ubuntu are you using?  b. have you installed winbind?.  Before anyone starts to complain; winbind is NOT needed for most home networking situations and I would remove it if you have it installed.

The following is what I would change in your smb.conf file: 1. I would comment out the following (put a # at the beginning) ```
wins support = yes
[COLOR="Red"]# wins support = yes <---like this[/COLOR]
```The net result is this changes the setting to *wins support = no* (the default).  You do not need to run a WINS server for a small network.  2. Add this line to the [global] section```
name resolve order = bcast
```This forces the broadcast of netbios names on the network.

This should not change your ability to connect via IP addresses as you do now.  It only adds the ability to browse and connect via netbios names.  FYI:  Samba uses the DNS name (hostname actually) to convert to netbios names.  I think the real problem is the broadcasting and that is what the name resolve order line explicitly provides.

---

### Post by welshy20 on 2012-04-09
Hi,

First of all thanks for the advice, I think you're correct in saying that the WD box does resolve using NetBIOS names, going from the fact that it picks up the NB names of Windows boxes rather than hostnames.

I did install winbind on someones advice (despite having never needed it for anything ever in the past) but I removed it about 2 minutes later realizing that I was barking up the wrong tree.

I have already tried hashing out wins support from the conf and restarting the same service, same problem, I have also tried to just use broadcast resolution using "name resolve order = bcast" as suggested (sorry I really should have said that first). Just tried them both again and restarted smbd and nmbd, same problem.

I also attempted to create an lmhosts file and use that for resolution but I think I've probably got teh wrong end of the stick (guessing that's for outgoing resolution rather than broadcast).

I've just noticed something rather odd however, broadcasts appear to be failing for DHCP too, the server is currently configured with a static IP using the broadcast address 192.168.1.255 and cannot contact the DHCP server, there's only one subnet and I can communicate with the DHCP server (via ping) but as soon as I change the config to use DHCP it gets as fare as sending out a discover packet and then times out after a while. Wonder if this actually boils down to broadcast being the problem, any ideas?

---

### Post by capscrew on 2012-04-09
> **welshy20 said:**
> Hi,

First of all thanks for the advice, I think you're correct in saying that the WD box does resolve using NetBIOS names, going from the fact that it picks up the NB names of Windows boxes rather than hostnames.

I did install winbind on someones advice (despite having never needed it for anything ever in the past) but I removed it about 2 minutes later realizing that I was barking up the wrong tree.

I have already tried hashing out wins support from the conf and restarting the same service, same problem, I have also tried to just use broadcast resolution using "name resolve order = bcast" as suggested (sorry I really should have said that first). Just tried them both again and restarted smbd and nmbd, same problem.

I also attempted to create an lmhosts file and use that for resolution but I think I've probably got teh wrong end of the stick (guessing that's for outgoing resolution rather than broadcast).

I've just noticed something rather odd however, broadcasts appear to be failing for DHCP too, the server is currently configured with a static IP using the broadcast address 192.168.1.255 and cannot contact the DHCP server, there's only one subnet and I can communicate with the DHCP server (via ping) but as soon as I change the config to use DHCP it gets as fare as sending out a discover packet and then times out after a while. Wonder if this actually boils down to broadcast being the problem, any ideas?

But of course.  You **do not assign** the broadcast address to any specific machine.  It is to allow messages for all machines.  In other in other words broadcast to not from all.  Assign another IP address for the DHCP server.

Edit:  Now that I have replied to the first problem I will read the post again for a complete solution.

---

### Post by welshy20 on 2012-04-09
Solved. Problem was in fact down to broadcasts being blocked by a dodgy switch, my whole network is on a static subnet so I've never got any need for using broadcast for DHCP either, no wonder it went un noticed.

Thanks for the advice, guess I should have remembered to turn it on and off again!

---

### Post by capscrew on 2012-04-09
> **welshy20 said:**
> Solved. Problem was in fact down to broadcasts being blocked by a dodgy switch, my whole network is on a static subnet so I've never got any need for using broadcast for DHCP either, no wonder it went un noticed.

Thanks for the advice, guess I should have remembered to turn it on and off again!

The broadcasts are to be received by all hosts in the subnet.  You should not have to turn this off or on.

Edit: In a correctly configured subnet there are 2 IP addresses that are not to be assigned to any particular host.  These are the NET ID 192.168.1.0/24 (i.e. 192.168.1.0) and the b'cast address (192.168.1.255).

---

### Post by welshy20 on 2012-04-10
Yes I understand that, the host ip is 1.4/24, I know you don't use 0 or 255 in host IPs, that's just the broadcast entry I've got in interfaces conf file.

---

### Post by railz68 on 2012-06-01
> **welshy20 said:**
> Solved. Problem was in fact down to broadcasts being blocked by a dodgy switch, my whole network is on a static subnet so I've never got any need for using broadcast for DHCP either, no wonder it went un noticed.

Thanks for the advice, guess I should have remembered to turn it on and off again!


Can you tell me what you changed to get it working if you should ever check back in.
I have samba working for everything except this new WD live tv. So i don't wanna ruin my shares just to find out tv live still won't see shares.

thanks

---

### Post by capscrew on 2012-06-02
> **railz68 said:**
> Can you tell me what you changed to get it working if you should ever check back in.
I have samba working for everything except this new WD live tv. So i don't wanna ruin my shares just to find out tv live still won't see shares.

thanks
This was a physical hardware problem.  The switch he had in the network was bad.  If you want help, the best thing for you to do is start a new thread explaining your specific problem.

---

