---
title: "File sharing with random networks"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by billaboard on 2009-06-02
I have had several attempts at Linux before, but always given up. However, I've just invested a small amount in a Toshiba NB100 netbook and am trying to use it 'out of the box' to force myself to stick with it. It came with pre-installed Ubuntu.

I have a small network here with various Windows machines including a Vista64, 2 XP, a Win7 and W2k, all cabled, plus 5 laptops with Vista32, XP etc. Finally there is a Windows Home server used for backup of the workgroup (ie not as a real server). I want to work solely in workgroup mode.

What I want to be able to do is fire up the netbook and hook into the network to transfer files between the two systems. Mine is a trial system that represents the sort of network found on small radio stations, so I must be able to join a network without altering the Windows network in any way. I would just be told the name of the workgroup, router details and a username and password.  

I have set up the Ubuntu netbook with wep, and it works via the router and sees the internet. I have set the workgroup name correctly (not sure how a beginner would ever navigate their way to this with the information supplied with the machine), and the netbook can see the Windows machines by name on the network. Every Windows machine can also see the netbook join the network. Now the queries.
The netbook can see files on only the W2k machine, none of the others. Where I would expect there to be a list of shared directories, there is just a blank.
The Windows machines can see the netbook, but attempting to look at its shared directories just gives a message about the machine not being available on the network.

The Windows machines all autologon with a standard username and password, the netbook is logged on (as a machine - is this reflected across to the network username and password?). Is this the area that need looking at?

Is there a simple guide to the structure of Windows and Linux networks anywhere?

I can't say I'm very impressed by the Toshiba's default Ubuntu installation. I seem to spend my time with unexpected errors, including some that seem to interfere with the ability to shutdown and/or reboot. I'm not averse to operating from a command line and I had to to get this far, but really would like to be able to work from the gui interface to set this up.

---

### Post by dmizer on 2009-06-02
You'll need to take a look at the 6th link in my sig.

The only way I'm aware of to change the workgroup is by manually editing /etc/samba/smb.conf. Once everything else is done according to my howto, you can change workgroups as needed by performing this edit. It's admittedly less than ideal, but functional.

Your instability problems may be a result of video. I suggest starting a new thread in the [Multimedia and Video](http://ubuntuforums.org/forumdisplay.php?f=334) section.

---

### Post by billaboard on 2009-06-03
> **dmizer said:**
> You'll need to take a look at the 6th link in my sig.

The only way I'm aware of to change the workgroup is by manually editing /etc/samba/smb.conf. Once everything else is done according to my howto, you can change workgroups as needed by performing this edit. It's admittedly less than ideal, but functional.

Your instability problems may be a result of video. I suggest starting a new thread in the [Multimedia and Video](http://ubuntuforums.org/forumdisplay.php?f=334) section.

Thanks for this. The problem is that I can see the individual machines by name on the network, but can't access the files on any but the older Windows 2000 machine. I can copy files from that machine fine. I have disabled the Windows firewalls on the machines, but that makes no difference.

I am happy with being able to edit the smb.conf file to match the workgroup, but thought it worth asking if there was a more gui way.

I'll have a look at the display situation when I can move files around. Thanks.

The thing I have never been clear about is how a simple, standard Windows workgroup on a wireless router gets and maintains its dns and routing info, and how to hook a Linux machine into this easily. I hear things like WINS (which I suppose I'll have to read up on), but the Linux machine must not do any more than attach itself and make itself visible and available. 

Thanks again

---

### Post by dmizer on 2009-06-03
Unfortunately, I have been unsuccessful at making Windows share browsing functional when name resolution is provided by local DNS. I am unsure as to why this is the case. The only way I've been able to get this to work is by using the wins solution as outlined in the 6th link in my sig.

---

### Post by capscrew on 2009-06-04
> **billaboard said:**
> ...

I am happy with being able to edit the smb.conf file to match the workgroup, but thought it worth asking if there was a more gui way.

I'll have a look at the display situation when I can move files around. Thanks.

The thing I have never been clear about is how a simple, standard Windows workgroup on a wireless router gets and maintains its dns and routing info, and how to hook a Linux machine into this easily. I hear things like WINS (which I suppose I'll have to read up on)...

You can read all the gory details [_**here**_]("http://www.samba.org/samba/docs/using_samba/ch07.html").  This URL is specifically on SAMBA name resolution and browsing.  

This seems to be the most difficult part for most people to understand.  The two are interrelated but not the same thing.  You should have a good idea of how you want to resolve the IP address name.  You can use WINS or DNS.  Both will work.  

I use DNS. There is no WINS server on my network.  This does not mean that there are no WINS broadcasts.  DNS will respond to the broadcasts and resolve the request for resolution.  

As a matter of fact XP requires that NetBIOS over TCP be used.  This means XP specifically asks for a NetBIOS name and is satisfied by my DNS server. 

As far a browsing is concerned this is merely a way to associate the shared resources. The following from the above link states it best
> *[COLOR="Blue"]The basic way browsing works is that one computer in the network takes on the role of the master browser (also called local master browser, browse master, or browse server) and keeps a list of all the computers on the local subnet that are acting as SMB servers. The list of computers is called the browse list and includes all Samba servers, Windows NT/2000/XP systems[/COLOR]*

The biggest drawback to using DNS seems to be the lack of a simple **dynamic** DNS solution.  BIND is too complicated for a small LAN situation.  I would recommend [_DNSmasq_]("http://thekelleys.org.uk/dnsmasq/doc.html").    This is very simple to set up and will do both DHCP and Dynamic DNS

Either way DNS or WINS, name resolution is critical to Windows/Samba browsing.

One last thought; I see more complaints in Jaunty that UFW is by on by default.  I don't know if this is true.  If it is and you are using Jaunty, I would turn off the FW until everything is working correctly.

---

### Post by billaboard on 2009-06-04
Thanks for the replies and references. I am reading, but not getting too far.

I thought that the wireless router acted as the source of DNS info as well as providing the dhcp addresses. I certainly put its address in to the DNS box on at least some of the machines here. Is this wrong?

I remember fiddling about with BrowseMasters on one of my previous forays into Linux (Slackware), but I think I had to end up issuing permanent IP addresses or something. Memory is not my strong point.

What I don't want to do is to affect the Windows workgroup in any way. I don't understand the reference to dynamic DNS, have looked at DNSmasq, but not managed to fathom out whether it takes over from whatever did DNS before or not. I'm not even sure if this is what is holding me up. Why can I see files on the W2k machine but on mothing else.
I've seen the other thread here where it was said that turning Vista machines off made it all work. I've tried this, but to no avail. I did leave the Windows Home server on, though, as that takes a lot of effort to get access.

The thing is that this Toshiba netbook just came with "Ubuntu", with no info whatsoever about what features were enabled, what version it was or anything. Just like a Vista machine, I'm having to guess my way round. I can't see any sign of a firewall, and I have no idea whether I'm using Jaunty or not.

I made the mistake of letting it install the 139 updates, and that broke at least one thing (the sound).

---

### Post by capscrew on 2009-06-04
> **billaboard said:**
> Thanks for the replies and references. I am reading, but not getting too far.

I thought that the wireless router acted as the source of DNS info as well as providing the dhcp addresses. I certainly put its address in to the DNS box on at least some of the machines here. Is this wrong?

The wireless router can provide those services. Since I don't know your setup, I used what I do know works in the example.  DNSmasq is provides the same services.  

> 

I remember fiddling about with BrowseMasters on one of my previous forays into Linux (Slackware), but I think I had to end up issuing permanent IP addresses or something. Memory is not my strong point.

Static addressing what I use for my servers.  I use dhcp only for my laptops.  Whether you use static IP or DHCP served IP, the DNS/netbios name needs to be consistent.

If you have a dynamically served IP address (DHCP), then that address number can change.  Dynamic DNS needs to be able to remap the name to the new address.  This seems to be the sticking point for most people.  Not all routers are equal in the services they provide or the user does not know how to set it up properly.  
> 

What I don't want to do is to affect the Windows workgroup in any way. I don't understand the reference to dynamic DNS,
 If you are using DHCP and DNS together via the router, the DNS should be dynamic DNS.> 
 have looked at DNSmasq, but not managed to fathom out whether it takes over from whatever did DNS before or not. I'm not even sure if this is what is holding me up. Why can I see files on the W2k machine but on mothing else.

Let's start with the basics.  It is important to confirm that all of your hosts (computers) can be pinged from the others by their name *consistently*. 
> 

I've seen the other thread here where it was said that turning Vista machines off made it all work. I've tried this, but to no avail. I did leave the Windows Home server on, though, as that takes a lot of effort to get access.

The thing is that this Toshiba netbook just came with "Ubuntu", with no info whatsoever about what features were enabled, what version it was or anything. Just like a Vista machine, I'm having to guess my way round. I can't see any sign of a firewall, and I have no idea whether I'm using Jaunty or not.
Try this from the CLI to see what version you have --```
lsb_release -a
```> 

I made the mistake of letting it install the 139 updates, and that broke at least one thing (the sound).

---

### Post by billaboard on 2009-06-04
Aha... I have Hardy 8.04.1

I can ping all the windows machines from each other. I can't ping to or from the Ubuntu machine

I will look into my router setup later. It's a bit of a toy from "Zoom".

And I've mended the sound! :-)

---

### Post by capscrew on 2009-06-04
> **billaboard said:**
> Aha... I have Hardy 8.04.1

I can ping all the windows machines from each other. I can't ping to or from the Ubuntu machine

You need to fix this before you work on the file sharing.> 

I will look into my router setup later. It's a bit of a toy from "Zoom".

What model is the router?  Be specific, so I can look up the manual online.> 

And I've mended the sound! :-)
Good deal!

---

### Post by billaboard on 2009-06-04
The router is a Zoom ADSL X6 Model 5590 (with no suffix letter).

The current firmware version is 2.1.3 (the latest is 2.1.5).

---

### Post by capscrew on 2009-06-04
> **billaboard said:**
> The router is a Zoom ADSL X6 Model 5590 (with no suffix letter).

The current firmware version is 2.1.3 (the latest is 2.1.5).

I have the manual now.  I'll look at it in the next hour or so.  Can you give me the network spec's?

---

### Post by dmizer on 2009-06-04
> **billaboard said:**
> Thanks for this. The problem is that I can see the individual machines by name on the network, but can't access the files on any but the older Windows 2000 machine. I can copy files from that machine fine. I have disabled the Windows firewalls on the machines, but that makes no difference.

Regarding the above, I've just learned something relevant to Vista shares that may help things:
[http://ubuntuforums.org/showthread.php?t=1176221](http://ubuntuforums.org/showthread.php?t=1176221)
[http://www.vistax64.com/vista-security/103790-access-denied.html](http://www.vistax64.com/vista-security/103790-access-denied.html)

---

### Post by capscrew on 2009-06-04
I've looked through the manual for the Zoom X6.  Not much to see.  Are you using a 10.0.0.0/24 network?  What is the IP address range for your Windows hosts?  Where are the hostnames setup?

I have some ideas, but I would rather hear from you.  As you say, we should adjust the Ubuntu host for the Windows network.

---

### Post by capscrew on 2009-06-04
> **dmizer said:**
> Regarding the above, I've just learned something relevant to Vista shares that may help things:
[http://ubuntuforums.org/showthread.php?t=1176221](http://ubuntuforums.org/showthread.php?t=1176221)
[http://www.vistax64.com/vista-security/103790-access-denied.html](http://www.vistax64.com/vista-security/103790-access-denied.html)

This will just confuse the situation.  The thread is rather long winded and assumes several items which the OP needs to do before he can share files.  

Rather than pointing to a self referencing thread.  Tell him what he should do specifically to remedy the inability to ping his ubuntu host by name or ping the other hosts by name from his ubuntu host.

---

### Post by dmizer on 2009-06-05
> **capscrew said:**
> Rather than pointing to a self referencing thread.  Tell him what he should do specifically to remedy the inability to ping his ubuntu host by name or ping the other hosts by name from his ubuntu host.

I have addressed solutions to the OP's file sharing issues (including ping) in post 2.

The OP indicates twice:
> The netbook can see files on only the W2k machine, none of the others. Where I would expect there to be a list of shared directories, there is just a blank.
and
> Thanks for this. The problem is that I can see the individual machines by name on the network, but can't access the files on any but the older Windows 2000 machine.
Although I am unsure of what might be causing a problem with XP (UFW/IPtables perhaps?), I have seen this very symptom in Vista shares. The cause is as discussed in the Vista forums and summarized in the Ubuntu forum thread, specifically that: while Vista will allow you to create a share of any directory, if it is protected by UAC, some clients will be unable to browse the contents therein.

---

### Post by billaboard on 2009-06-05
Sorry about the delay, I think we may be at opposite sides of the world.

The router's dhcp server is set to a range from 10.0.0.4 to 10.0.0.24, the router itself is on 10.0.0.2 The subnet mask is set to 255.255.255.0
At the moment all machines appear to be running dhcp, but in the past permanent ip addresses have been set from 10.0.0.25 up.
As far as I know the hostnames are set up on the individual machines themselves. Other laptops come and go on the network on a regular basis, and I have a set of other cabled machines that come on occasionally to check out software on older OS's and with other hardware.

---

### Post by capscrew on 2009-06-05
> **billaboard said:**
> Sorry about the delay, I think we may be at opposite sides of the world.

No problem.  I'm in California, USA. That's GMT -7 time> 

The router's dhcp server is set to a range from 10.0.0.4 to 10.0.0.24, the router itself is on 10.0.0.2 The subnet mask is set to 255.255.255.0


Good deal.  I saw that in the manual.
> 

At the moment all machines appear to be running dhcp, but in the past permanent ip addresses have been set from 10.0.0.25 up.  As far as I know the hostnames are set up on the individual machines themselves.  

So you are saying that all the machines in your network have IP addresses that are between .4 and .24 at this time.   
> 
Other laptops come and go on the network on a regular basis, and I have a set of other cabled machines that come on occasionally to check out software on older OS's and with other hardware.
I assume that they get their IP addresses from the same 4 -24 address pool.

Please post the results of pinging from one Windows host to another. Do the ping by name and by IP address.

This is what it looks like when I ping.  By name (malibu pings rincon).  As you can see this resolves the name rincon to 192.168.1.2```
ping rincon
PING rincon (192.168.1.2) 56(84) bytes of data.
64 bytes from rincon (192.168.1.2): icmp_seq=1 ttl=64 time=1.49 ms
64 bytes from rincon (192.168.1.2): icmp_seq=2 ttl=64 time=0.160 ms
64 bytes from rincon (192.168.1.2): icmp_seq=3 ttl=64 time=0.161 ms
64 bytes from rincon (192.168.1.2): icmp_seq=4 ttl=64 time=0.153 ms

--- rincon ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 0.153/0.492/1.495/0.579 ms

```

When I ping malibu from rincon it resolves the name malibu to 192.168.1.12 ```
ping malibu
PING malibu (192.168.1.12) 56(84) bytes of data.
64 bytes from malibu (192.168.1.12): icmp_seq=1 ttl=64 time=0.194 ms
64 bytes from malibu (192.168.1.12): icmp_seq=2 ttl=64 time=0.183 ms
64 bytes from malibu (192.168.1.12): icmp_seq=3 ttl=64 time=0.179 ms
64 bytes from malibu (192.168.1.12): icmp_seq=4 ttl=64 time=0.184 ms

--- malibu ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.179/0.185/0.194/0.005 ms

```

---

### Post by billaboard on 2009-06-05
I'm not too far from Liverpool, UK

The machines all have ip addresses between 4 and 24 except the Ubuntu machine which is on a static 10.0.0.112 because I couldn't get dhcp to work.

Ping from Vista to XP follows

Pinging 10.0.0.11 with 32 bytes of data:
Reply from 10.0.0.11: bytes=32 time=68ms TTL=128Reply from 10.0.0.11: bytes=32 time=90ms TTL=128
Reply from 10.0.0.11: bytes=32 time=10ms TTL=128
Reply from 10.0.0.11: bytes=32 time=33ms TTL=128
Ping statistics for 10.0.0.11:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),Approximate round trip times in milli-seconds:
    Minimum = 10ms, Maximum = 90ms, Average = 50ms



Pinging abt-lenovo_xp [10.0.0.11] with 32 bytes of data:
Reply from 10.0.0.11: bytes=32 time=71ms TTL=128
Reply from 10.0.0.11: bytes=32 time=84ms TTL=128
Reply from 10.0.0.11: bytes=32 time=107ms TTL=128
Reply from 10.0.0.11: bytes=32 time=38ms TTL=128
Ping statistics for 10.0.0.11:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),Approximate round trip times in milli-seconds:
    Minimum = 38ms, Maximum = 107ms, Average = 75ms

This doesn't mention the name in the reply!

---

### Post by capscrew on 2009-06-05
You did ping by name?  If it doesn't work then we have no name resolution at all.  I expected to have basic connectivity by IP address.

---

### Post by billaboard on 2009-06-05
The second ping above was by name, but the replies didn't quote the name, unlike your example.

---

### Post by capscrew on 2009-06-05
> **billaboard said:**
> The second ping above was by name, but the replies didn't quote the name, unlike your example.

So let me know which ones ping by name.  Do they all respond to pings by name?  I'm not so interested in what they return.  Just that they respond like this:```
Reply from 10.0.0.11: bytes=32 time=68ms TTL=12
```

---

