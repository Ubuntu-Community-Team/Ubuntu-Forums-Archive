---
title: "Ethernet dropping"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by chrisinspace on 2009-07-24
I recently built an Ubuntu server for secure FTP transmission.  I got it up and running and it works great.  I have been testing it over the last couple of days and I started to notice a problem.  The network interface sporadically drops without warning.  

I thought maybe there was something going on with the firewall, but if I reboot the server, everything resumes as normal for a time.  I checked the syslog, but I don't see an error corresponding to the time when the connection dropped.  

I have tried to do ifconfig eth0 down and then back up, but that didn't help.  This server is running in VMWare.  I have installed the VMWare tools, but that didn't seem to affect it.  I have another Ubuntu server running on the same VMWare host and I have never had this issue before.  Once the machine goes into this state, I cannot connect FTP clients to it, I cannot open any of its shared folders, and I cannot connect to the outside world from the server, but the weird thing is, I can ping the server from other computers on my network. :confused:

Does anyone have any ideas?  I looked through the forums for dropping connections, but everything I found was for wireless.

---

### Post by chrisinspace on 2009-07-24
Ok...it gets even more strange.  It just came back by itself.  I'm sure it will go back down again soon.

Also, a little more info.  I'm using static IP, not DHCP.

---

### Post by chrisinspace on 2009-07-25
More info:

If I use 'ifup' and 'ifdown' instead of 'ifconfig eth0 down' and 'ifconfig eth0 up' it restores the connection.

Has anyone seen anything like this?  Do you think it's related to VMWare?  The problem with that theory is that I have another Ubuntu server in the same VMWare environment and it has never had this issue.

---

### Post by chrisinspace on 2009-07-27
Anyone?

I could really use some help with this...

I've continued to troubleshoot and I've found if I log into the server while its network connections are down and initiate a ping to [www.google.com](www.google.com), there is a couple second's delay and then I start getting responses.  After that I can connect to it again from remote machines.  It's like it brings the NIC back online or something.  Do you think the NIC could be going into some kind of power-saving mode?

---

### Post by chrisinspace on 2009-07-28
Man, I'm desperate here and not a single response.  I'm not the only one having this problem.  I have found other threads describing similar issues, but no solutions:

[http://ubuntuforums.org/showthread.php?p=7687532](http://ubuntuforums.org/showthread.php?p=7687532)

[http://ubuntuforums.org/showthread.php?p=7101196](http://ubuntuforums.org/showthread.php?p=7101196)

I'm not going to bump this thread anymore.  I'm sorry if I'm violating etiquette, but I really need to fix this issue and I thought I would have gotten some kind of response by now.  If anyone has any ideas, please post a reply...I have subscribed to this thread so I'll be notified.  I would be extremely grateful for any assistance.

---

### Post by ZhuaSD on 2009-07-29
I don't think this has anything to do with VM, and the links you provide indicate you agree.

Yes, this is a problem, I have exactly the same symptoms you do, but no one seems to have a fix.

Your idea about it is the connection going to sleep makes sense, as the connection almost always drops when I am not using it.  Sometimes, it is still working when I get back from whatever, but then it drops right after I get back and start using the network again, so its sort of the same thing.

Could it be hardware? I am on an intel board (8180 or something) but I put in another card to fix this problem.  Which didn't work.

I can 

```
sudo poff dsl-provider
sudo pon dsl-provider
```

and get online, 90% of the time. The other 10% I have to try a few more offs and ons, and that takes care of it.

I guess this is similar to your *'ifup' and 'ifdown' instead of 'ifconfig eth0 down' and 'ifconfig eth0 up'*  but I don't know the difference.

Also, when I need to poff and pon, (meaning when my connection is messed up) 'plog' returns no data.  Which is interesting.

Can you use [crontab to schedule regular quick re-starts]("http://ubuntuforums.org/showthread.php?t=1223395") of the network?  That is the only solution I have at this time.

---

### Post by chrisinspace on 2009-07-29
I can't use a cron job to restart my network periodically because this is an FTP server.  If I restart the network while someone is in the middle of a transmission, it could disrupt it.  Instead, I created a cron job to send a ping every 5 minutes and it seems to be helping.  It still drops for a couple of minutes every once in a while, but the next ping wakes it up.  This only happens after a period of inactivity, so it doesn't bother FTP transmissions that are in progress.  I have been regularly connecting to the server with only minor issues.  I just don't like that it's a band-aid fix.  I would like to address the underlying problem.

You're right...I don't think it's hardware.  I have another Ubuntu server running on the same VMWare host and I have never had a problem with it.

I was reading about [this bug]("https://bugs.launchpad.net/ubuntu/+bug/296162").  I see some similarities, but the symptoms are somewhat different.  I wonder if they are related, though.  I have read about several people experiencing our problem and similar issues with their ethernet connections dropping in this and other forums, but none of them have ended in a permanent fix.

---

### Post by ZhuaSD on 2009-07-30
Yeah that other bug is like the exact opposite of this one.  Same symptoms and fix but completely different triggering event.

I didn't mean to say that hardware has nothing to do with it, I am not sure about that.

I don't really have much left to suggest.  So this ping workaround seems to work well?

---

### Post by chrisinspace on 2009-07-30
Yeah...I copied it from a post in [this thread]("http://ubuntuforums.org/showthread.php?p=7687532").

Login as root or sudo for following:

```
crontab -e
```

Following line pings external site once every 5 minutes

```
*/5 * * * * ping -c 1 externalSite.com
```

Logs for cron are available in /var/log/syslog

*Credit to [mzr]("http://ubuntuforums.org/member.php?u=865088").*

---

### Post by stoneg64 on 2009-07-30
I have the same symptoms.  For now I just restart networking and it seems to fix it but it is very annoying.

---

### Post by stoneg64 on 2009-08-12
I think I've solved my problem by updating my driver which was for realtek RTL8101E

---

### Post by SolarOnline on 2009-08-12
So it's a driver issue?

Can anyone else replicate and confirm this fix?

---

### Post by ZhuaSD on 2009-08-27
On a tip, I installed wicd, which uninstalls nm and nm-gnome.

Then just go through pppoeconf once and that was it.  A restart and the icon is there.

Its only been six hours, but so far so good.  its got its own icon up there, but I do have to manually start it up with pon dsl-provider.

I am going on a trip so it will be a good chance to see if it really works.

Apparently there is some bug between nm and pppoeconf.

---

### Post by ZhuaSD on 2009-08-27
Ehh...

Didn't work. Same results.

---

### Post by ThomWilhelm on 2009-08-27
Same bug here, no idea what the problem is... I've got other servers on the network running Ubuntu 9.04 and don't have the same problem.

When it happens I run ifconfig -a and notice I have TX packets showing overrun errors, anyone else noticing this?

Think I might just go back to 8.04 for now, I need this server to be up...

---

### Post by ThomWilhelm on 2009-08-27
OK actually what I'm going to do for now is enter into a crontab:

* * * * * ifconfig eth0 up

I know for certain that /etc/init.d/networking restart solves the problem when it happens, does anyone know it ifconfig eth0 up works?

---

### Post by ZhuaSD on 2009-08-28
I am calling this a hardware-specific problem.

Intel north bridge, anyone else? I bought a realtek card to try and solve this problem as well.

But I had the same problem on 8.04...

---

### Post by ThomWilhelm on 2009-08-28
Now you mention it, I think I never had 8.04 or 8.10 on this machine, so I'm not certain downgrading would sort the problem. You're probably right with it being hardware, for what its worth heres my lspci:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:07.0 Ethernet controller: Belkin Wireless PCI Card - F5D6001 (rev 20)
03:08.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IP1000 Family Gigabit Ethernet (rev 41)

---

### Post by ThomWilhelm on 2009-08-28
Ok my cronjob above hasn't solved the problem, however running:

 * * * * * ifconfig eth0 down; ifconfig eth0 up

Will work as a temporary fix if you need the server to be active. So its as if the eth0 connection doesn't get shutdown, its just needs restarting the become available again.

---

### Post by band-aid on 2009-08-28
Are you guys by chance using an onboard network card? I have had nothing but trouble with them. I recommend you use a dedicated NIC which can be picked up from most computer repair shops used for about 10 USD.

---

### Post by ThomWilhelm on 2009-08-29
Nope, I have a Nvidia chipset with onboard ethernet but can't get it working in Ubuntu, so I have my eth0 setup using this card:

03:08.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IP1000 Family Gigabit Ethernet (rev 41)

For now at least my cron workaround has meant the server is staying accessible, but not solved the root cause.

---

### Post by ThomWilhelm on 2009-08-30
Right Ok, I've just purchased a Realtek RTL-8169 Gigabit Ethernet card, which is listed as supported on:

[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek)

I will try this card in a couple of days and hopefully it will resolve my problem. If not then I will have to move the MySQL server to another machine.

---

### Post by mdntepoet on 2009-09-12
Similar problem

I set up a game server, as long as I leave the game server (ut3) running the machine stays up. If the box was sitting idle It would randomly just die and I could no longer ssh to it. (it's in a data center controlling remotely from home)

If I left a putty terminal open to the machine, and had top running, the machine would stay up for days. Problem ONLY occurs after idle for periods of time. I suspected hardware (onboard nic)

I tried another nic (same results)
another hard drive (no change) as I suspected it might be spinning down and not returning to service

I swapped motherboards, again with a second nic, and another fresh install.

To date i've had the same problem with all of the following hardware:

2.2 gig dual core opteron
3.1 dual fx

amd 790 northbridge with integrated nic
marvell nic
nvidia integrated nic
realtek nic

two different installs.

In fact the ONLY thing that has stayed constant is that I have used ubuntu 9.04 amd64 bit on every machine.

I do not believe this is hardware. I believe it is a software issue with the software shutting down and not responding to network requests.

I have removed network manager and set it all up manually since day one with static IP's running to a fully managed switch, core switch cisco router and firewall.  It's not network as this is a pretty big data center operation and no other machines have this issue even on the same path.

If anyone spots what would cause a network device to go to sleep after idle periods I would LOVE to know!

---

### Post by chrisinspace on 2009-09-14
My issue turned out to be an IP conflict.  I had de-commissioned a test VM that I was using to play around with some FTP software, but someone turned it back on.  So I had 2 machines with the same IP.  It would work for while, but then periodically choke.  I completely deleted the old VM and the problem has not recurred.

---

### Post by ZhuaSD on 2009-09-18
Ok thanks for the resolution.

---

### Post by ZhuaSD on 2009-09-20
Chris I would like some advice.

It seems my connection is being dropped when 192.168.1.2 contacts 192.168.1.1 for a DHCPREQUEST

But I have no virtual machine.  

Is this anything like what you were seeing?

---

### Post by chrisinspace on 2009-09-21
My issue just happened to involve VMs, but the same problem would have occurred if I had been running 2 physical servers w/ the same IP.  My connection was getting cut off due to the conflict.

Try using a static address and see if the problem continues.  If it does, try a different IP and see if that helps.

---

### Post by chandubaba on 2009-11-11
I dont know about vmware... but if we are running in one machine... then we must not run "sudo pon-dsl provider" everytime we login cause the connection gets started automatically everytime we login.

---

