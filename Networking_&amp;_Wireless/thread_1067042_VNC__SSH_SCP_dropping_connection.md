---
title: "VNC / SSH /SCP dropping connection"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by H.Callahan on 2009-02-11
Ok, I am pulling out my hair again!

I scrounged a new set of hardware to make another machine and decided to go 100% Ubuntu on it.  It is basically a Dell 1.8 Ghz P4 with 1Gb RAM (soon to be upgrade to 1.5GB) and an NVidia 7800 GS AGP video card (probably a bit of overkill for the CPU, but it is what I had).  I pulled teeth trying to get the video to display anything over 800x600 resolution.  Finally got it to 1280x1024, but still can't get Compiz to work, but that is a "later" issue.

What is driving me nuts now, is that I have setup the box for remote administration using VNC.  I have gotten to work with out a whole lot of trouble.  I have also set up SSH and a tunnel so that I can VNC through the Internet somewhat securely and also SSH into the box for a command line if I want it.

It all works except for the fact that after about 30 seconds to several minutes, I lose the connection.  This happens whether I am VNCing in through the internet via SSH, VNCing through the Internet without SSH (for testing purposes, I don't intend actually use it that way), VNCing in from another machine on the same LAN (either with or without SSH) inside the firewall/router and when I am using just a vanilla SSH connection or trying to SCP files.  From the new machine itself, it does not appear to be generically loosing the network as I have been able to browse on it and download both through the browser and via bittorrent without interruptions that I can see.

The messages that I have seen when directly VNCing in (without tunneling through SSH) have been "ReadExact: Socket error while reading" and "Error while waiting for server message".  When SSH has been thrown into the mix (either using SSH directly, trying to SCP something or tunneling with VNC), the message has been "Network error: Software caused connection abort".  If I wait a few moments, it will recover and I can reestablish the connection and log in again -- only to be dropped again shortly thereafter.

I have searched on those phrases and found a lot of mention them, but no answers or discussion of what is actually happening with those messages.  Does anyone have any ideas on where to go to next?

---

### Post by unixeducation on 2009-02-11
Sounds like the NIC may be the issue. Try putting a spare PCI NIC in the box and see if you have better luck with it. In the past, I've had issues with two onboard NICs.

---

### Post by H.Callahan on 2009-02-11
I can dig up a different NIC (it is not on-board) to put in it and will try that.  

That said, wouldn't dropping the network show up during sessions when I am actually at the box using it directly?  I am not having dropping when surfing or downloading or bittorrenting when I am at the actual console.

---

### Post by Peter09 on 2009-02-11
Check that the machine is not sleeping or a screen saver or other lump of software is coming in and using your resources. What is the specification of the machine? The fact that its happening when the console is idle may be a clue.

---

### Post by JK3mp on 2009-02-11
A program that spikes resources could very well be the reason....

---

### Post by H.Callahan on 2009-02-11
> **Peter09 said:**
> What is the specification of the machine? As I said in the OP,
> **H.Callahan said:**
> Ok,It is basically a Dell 1.8 Ghz P4 with 1Gb RAM (soon to be upgrade to 1.5GB) and an NVidia 7800 GS AGP video card (probably a bit of overkill for the CPU, but it is what I had).

> **Peter09 said:**
> Check that the machine is not sleeping or a screen saver or other lump of software is coming in and using your resources. What is the specification of the machine? The fact that its happening when the console is idle may be a clue.
> **JK3mp said:**
> A program that spikes resources could very well be the reason....It is not a the screen saver.  It has been disabled for the time being.

How would I tell if this is happening?  This is a brand new install.  I have added nothing (yet) to it other than Envy and whatever drivers it loaded for the NVidia card as the built-in restricted drivers would not allow any resolution above 640x480.  I've also added the VNC server and SSH.  That is it at this point.  Oh yes... I have done the updates when they have appeared.

---

### Post by jimcooncat on 2009-02-11
Try adding the following line to /etc/ssh/ssh_config :
ServerAliveInterval 300

You may have to play with the number some. Here it's set at 300 seconds (5 minutes). If you're still getting dropped, lower the number some.

For more info, see this article:
[http://ubuntu.wordpress.com/2006/02/03/keeping-ssh-sessions-alive/](http://ubuntu.wordpress.com/2006/02/03/keeping-ssh-sessions-alive/)

---

### Post by Peter09 on 2009-02-11
The other thing to consider is something doing a large network transfer, may be not connected to the target machine. Things like firefox and download programs do not need an open connection to be continuously responsive. SSH will most probably expect a response from a server within a certain time limit which is quite short (seconds may be). Anything interrupting that may be a problem.

Its difficult to really see what is causing it.

---

### Post by jimcooncat on 2009-02-11
> **Peter09 said:**
> The other thing to consider is something doing a large network transfer, may be not connected to the target machine. Things like firefox and download programs do not need an open connection to be continuously responsive. SSH will most probably expect a response from a server within a certain time limit which is quite short (seconds may be). Anything interrupting that may be a problem.

Its difficult to really see what is causing it.

If it's a problem initially connecting, slow DNS might be at fault. If practical, use an ip address for the host instead of a domain name.

If that isn't the answer, ionice might be useful.

---

### Post by H.Callahan on 2009-02-11
Ok, I tried the "ServerAliveInterval 300", with no change.  (I actually changed it both on the affected machine and also in (Windows) Putty since it sounded more like a client side tweak)

Also, remember, this is happening with "naked" VNC as well -- not just with SSH.

What is ionice?

---

### Post by jimcooncat on 2009-02-12
I may have been wrong about ionice, it looks as if that's mainly for hard disk traffic, not TCP.

Are you experiencing a high volume of overall traffic over the NIC? You can see it by using the System Monitor applet, attached to the Gnome toolbar.

With this also failing with plain VNC connections, some further guesses would be faulty cabling, switch, or hub. Or if you're using a hub, rather than a switch, too much traffic running through it at a time (girlfriend watching YouTube) might cause you to timeout. I'd double-check the wiring first, though. Especially if you have pets.

---

### Post by H.Callahan on 2009-02-12
There SHOULDN'T be much traffic on the NIC.  I will take a look at it to verify though.

I am using a switch.  Two other machines are attached to the same switch are exhibiting no problems at all (one of them is also an Ubuntu box).  Two other machines are intermittently attached to the LAN via wireless.  The wiring from the affected box and the switch is a brand new CAT-6 patch cable.

---

### Post by H.Callahan on 2009-02-12
A little more information:

I just VNC'ed over SSH to both Ubuntu boxs -- the one that is having the problem and one that is a much older box (but still with 8.04).  Both machines are physically hooked to the same switch (different port, obviously).  Over a 15 minute period, the affected machine dropped off about 20 times, requiring a relogin.  The other, older, established machine was rock solid the entire time.

This leads me to believe that the problem is somewhere downstream of the switch -- the wire, the NIC, or the software.  Would that sound right?

---

### Post by Peter09 on 2009-02-12
If this is a desktop machine without a wireless connection then try removing network manager using synaptic (you do not need it). I have seen cases where network manager will keep trying to reconfigure the network every so often - its worth a try.

---

### Post by H.Callahan on 2009-02-12
> **Peter09 said:**
> If this is a desktop machine without a wireless connection then try removing network manager using synaptic (you do not need it). I have seen cases where network manager will keep trying to reconfigure the network every so often - its worth a try.
Removed network manager, rebooted (just to be sure).  No change in the situation.

---

### Post by Peter09 on 2009-02-13
Have you looked through syslog, see if the is any thing showing?

```
gnome-system-log
```

---

### Post by HermanAB on 2009-02-13
An old El'Cheapo router with little RAM somewhere in the link can cause SSH to drop out when it flushes its tables every five to 20 minutes.  The solution is to buy a new El'Cheapo router and toss the old one away.

BTW, if you already have SSH, then you don't need VNC.  

Try this:
$ ssh user@server gnome-panel

Cheers,

Herman

---

### Post by H.Callahan on 2009-02-13
> **Peter09 said:**
> Have you looked through syslog, see if the is any thing showing?

```
gnome-system-log
```

Nothing other than a bunch of MARKs, which I assume some sort of heartbeat.  I recorded the times that I got disconnects and there is nothing at or around the timeframe that it occurred.

> **HermanAB said:**
> BTW, if you already have SSH, then you don't need VNC.  

Try this:
$ ssh user@server gnome-panel

Except for the fact that this disconnect is occurring with SSH independent of VNC.  It disconnects when just SSHing; it disconnects when just VNCing; and it disconnects when VNCing by tunneling with SSH.  It also disconnects when doing an SCP.

---

### Post by H.Callahan on 2009-02-14
Update:

I think I have minimized the possiblity that the problem is with hardware.  I have changed the switch, replaced the NIC and changed the cable -- all to known working examples -- and the problem still persists.

I feel that the problem is, at this point, more likely to be either the software or the configuration that is causing the problem.  Does anyone have any clue what the error messages in the OP actually mean?

I need to have this box working with remote access.  Either that, or I go back to Windows. (yuck!)

---

### Post by H.Callahan on 2009-02-16
Is this a situation that would be improved by nuking and paving the machine?

---

### Post by H.Callahan on 2009-02-19
Still have not gotten a solution to this.  (a.k.a. bump)

---

### Post by Peter09 on 2009-02-19
This is a long shot in the dark,

I've seen machines behaving strangely when they have an IP number issue. If you have a machine with the same ip address on the network you can get intermittent conflicts .... other than that - I'm at a loss.

---

### Post by H.Callahan on 2009-02-19
I am certain that the IP address is unique.  I static IP all the machines on the LAN and have verified that everyone is still unique and seperate.

Thanks for the help so far.

---

### Post by H.Callahan on 2009-02-26
So far, I have not found a solution, or even a good explaination, for this.  Any help would be appreciated.

---

### Post by dmizer on 2009-03-02
Moved to Networking & Wireless. Closed your duplicate thread.

If you want to continue your discussion in a new section of the forums, please use the "report post" feature and we will move it for you. It's easier for people to keep track of one thread rather than multiple threads. :)

Edit:
Someone suggested that you try a different NIC, have you, and what were the results?

Never mind, just found this ...
> **H.Callahan said:**
> Update:

I think I have minimized the possiblity that the problem is with hardware.  I have changed the switch, replaced the NIC and changed the cable -- all to known working examples -- and the problem still persists.

I feel that the problem is, at this point, more likely to be either the software or the configuration that is causing the problem.  Does anyone have any clue what the error messages in the OP actually mean?

I need to have this box working with remote access.  Either that, or I go back to Windows. (yuck!)
You say you tried a different switch, what about your router? What kind of switch hardware are you using? Which version of Ubuntu are you using?

Please post the output of the following commands:
```
sudo ifconfig
```
and
```
lshw -C network
```

---

### Post by H.Callahan on 2009-03-03
My apoligies, I was not aware of the protocol regarding placing a post in a different section.  Thank you for the heads-up.

Yes, I have replaced everything network related.  The original switch was just the switch that came as part of the router -- a Linksys WRT54G.  I replaced it with a 3COM Baseline Switch 2024.  The router was replaced with the same model Linksys, but loaded with DD-WRT software.  All of this resulted in no change.

The version of Ubuntu was Hardy, but since I was getting no results, I nuked that installation and have just put on Intrepid.  Again, no change.  And, the only thing I have done with the new installation was to set the static address in /etc/network/interfaces.  I haven't even done the wrestling match with the NVidia card to get it to work at anything better than 800x600 that I had to do to Hardy.

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:c0:a8:7d:2a:2a  
          inet addr:192.168.1.171  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fe7d:2a2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3908565 (3.9 MB)  TX bytes:16952788 (16.9 MB)
          Interrupt:18 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7532 (7.5 KB)  TX bytes:7532 (7.5 KB)

```
**lshw -C network**
```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:a8:7d:2a:2a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.171 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:2e:08:82:00:bd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
p
```
The network card that is in the machine now is the original one.  The replacement was a 3COM 3C905B-TX.  When this showed no improvement, I switched back to the original.

Again, this problem only seems to be with remote access -- either VNC or SSH.  If I am on the machine locally, I do not see any network interruptions while browsing or downloading or bittorrenting (actually, I can only speak to the Hardy installation on that, as I have not configured the Intrepid install enough to actually do much on the machine.  I want to keep the machine as virgin as possible until I get this solved, so that I don't add complications to the problem.)

---

### Post by dmizer on 2009-03-03
Are you using DHCP on the local network? Is it possible that you are getting dropped because your server's DHCP lease has expired and grabs a new IP? Is the server wired or wireless (sorry if I missed this answer in an earlier post).

On the ssh client, try bumping the ServerAliveInterval to something much less ... around 10 is what I use. That doesn't help VNC though.

---

### Post by H.Callahan on 2009-03-04
DHCP is being used on the LAN, but not on this particular machine.  I have it as a static IP and out of the range that the DHCP server passes out.  The machine is wired.  The route is a CAT 6 patch to the 3Com switch, out of the switch with CAT 6 cable to the router, CAT 6 cable from the router to the modem and then RG6 to the cable head.

Also, note that there is another, older machine running Hardy (the initial install was Gutsy, and then upgraded with the upgrade utility) that is essentially hooked up the same way (different port on the switch, obviously, but I HAVE switched ports between the two machines to make sure that I didn't have a bad port on the switch) that has absolutely no problem at all.

I have previously tried the ServerAliveInterval, with no change.

---

### Post by dmizer on 2009-03-04
> **H.Callahan said:**
> I have previously tried the ServerAliveInterval, with no change.
According to this:

> **jimcooncat said:**
> Try adding the following line to /etc/ssh/ssh_config :
ServerAliveInterval 300
You tried an interval of 300 which may have been too high. I was merely suggesting that you try a shorter interval.

Frankly I'm not confident that this will work but it is worth a try.

> **H.Callahan said:**
> DHCP is being used on the LAN, but not on this particular machine.  I have it as a static IP and out of the range that the DHCP server passes out.  The machine is wired.  The route is a CAT 6 patch to the 3Com switch, out of the switch with CAT 6 cable to the router, CAT 6 cable from the router to the modem and then RG6 to the cable head.

Also, note that there is another, older machine running Hardy (the initial install was Gutsy, and then upgraded with the upgrade utility) that is essentially hooked up the same way (different port on the switch, obviously, but I HAVE switched ports between the two machines to make sure that I didn't have a bad port on the switch) that has absolutely no problem at all.
Have you tried removing NetworkManager? It's been a couple days since I've read through this entire thread. If not, try removing it ... that's about the only suggestion I have left.

---

### Post by H.Callahan on 2009-03-05
Ok, I tried the ServerAliveInterval at various settings around 10 (1, 5, 10, 15, 20...) with no change.

I had not tried removing NetworkManager on the Hardy installation, but I could not get a static IP with it running on Intrepid, so I have already removed it on the current (8.10) install.

> **dmizer said:**
> Frankly I'm not confident that this will work but it is worth a try.

Feel free to suggest anything.  I am going crazy with this one.  Particularly since I have another machine running 8.04 physically sitting right next to it that runs VNC and SSH with no problem at all.  I could believe a hardware problem, but I have changed everything on the network from the NIC card in the machine clear through to the ISP's modem, including the cabling with no improvement.  I just can't get a handle on it.  It acts like it is some sort of connection disconnect, but I don't see it when I am physically at the machine doing other things like web surfing, bittorrenting and downloading.

---

### Post by H.Callahan on 2009-03-08
Ok, here is a little interesting information on this problem.  I don't know if it sheds any light on anything, but it was interesting.

Yesterday, just for giggles, I fired up an SCP from the affected box to a Windows box sitting in close physical proximity (using WinSCP).  As expected, about a minute or so into the copy, I got the message on the windows machine that the connection had been disconnected and that it was retrying the connection.

I jumped on the Ubuntu box and did some pings to see if the network was down on that machine.  I was able to successfully ping to a couple of machines on the network and to Internet sites like Google and Yahoo.  I could not, however, ping to the machine that was doing the SCP.  After a minute or two, WinSCP was able to reestablish the connection and I was immediately able to ping the WinSCP machine from the Ubuntu machine.

I tried the experiment with a remotely located machine and had essentially the same results. 

Whatever this problem is, it seems to be disconnecting ONLY the machine doing the SSH, SCP or VNC -- but it is not limited to just one machine.  Any machine that SSHs, SCPs or VNCs is being treated the same way.

Does that shed any more light on the problem or just muddle the waters further?

---

### Post by dmizer on 2009-03-08
I am completely out of ideas. You'll probably need to break out some network tracing tools which I don't know much about.

---

### Post by Peter09 on 2009-03-10
Been following this but not had more to add.

One thought did cross my mind.

Have you tried using the machine with only the 'target' machine on the network, this will exclude interference by any other system. 

My thinking is that having changed most of the H/W and S/W its worth considering that the fault may lie elsewhere.

P.S. Are you sub netting your network?

---

### Post by H.Callahan on 2009-03-10
I have tried to access the problem machine with three different machines; A Windows machine located on the same switch as the problem machine, a laptop that is connected wirelessly to the router on the same LAN as the problem machine, and a totally remote machine (my work machine) via an Internet connection.  I have tried all three with VNC, SSH and SCP (and combinations thereof) and all exhibit the same problem.

All three of these machines can succesfully access another (albeit, older/slower/less memory) machine running 8.04 that is sitting physically right next to the problem machine and is hooked to the same switch as the problem machine and the one Windows machine.

Is there any way to monitor actually what is going on with the network connections?

---

### Post by Peter09 on 2009-03-10
Hi, yes but were there other machines on the network at the same time. Are you able to set-up a network which consists of the router, a switch the problem machine and a target machine. This then excludes any outside interference.

Edit - actually you do not even need the router, although then you couldn't use DHCP.

---

### Post by H.Callahan on 2009-03-10
> **Peter09 said:**
> Hi, yes but were there other machines on the network at the same time. Are you able to set-up a network which consists of the router, a switch the problem machine and a target machine. This then excludes any outside interference.

Edit - actually you do not even need the router, although then you couldn't use DHCP.
You may be on to something here.  I didn't have long to test, but I was able to disconnect the rest of the network and hooked just the two machines together for about 15 minutes.  The connection remained solid for the entire session.  Now I will have to troubleshoot what is actually causing the problem.  Weird, though, as I have totally replaced everything in the entire network at one point or another (other than the actual machines, of course).

I'll have to find time when I can take everything down for a while to play with things.

---

### Post by Peter09 on 2009-03-11
I would suspect that one of the other machines on the network has some sort of configuration error which interferes with the 'problem' machine. 

As a said in an earlier post I have seen a similar problem with two machines with the same IP address. I'm not suggesting that this is the problem here, but something similar could be happening. 

Adding the machines back one by one would be a good start, see if any particular machine is involved with the inducing problem.

---

### Post by H.Callahan on 2009-03-13
It'll probably be this weekend before I can get some "quality time" with the machines.  I'll let you know what happens!

---

### Post by Peter09 on 2009-03-13
Be interested to find out what was causing the problem.

---

### Post by H.Callahan on 2009-03-16
Well, it was an interesting experiment.

If I hooked the problem machine together with the wired Windows machine only , I could keep everything connected for quite a while (longer than my patience without the Internet to peruse while waiting).  As soon as I hooked in the Internet (the path being a patch cable from the switch where the two machines are connected to the router and then a patch cable from the router to the cable modem), the problem cropped up.  I replaced the router (again) with another router with no improvement.  I updated the firmware to the absolute latest version of the manufacturer's firmware -- no improvement.  I even replaced the manufacturer's firmware with a 3rd party firmware (DD-WRT) with no improvement.  The cable company tells me that there is no problem with the cable modem (I tend to believe this as the entire connection never goes down, only the VNC/SSH/SCP connection to that one machine.) and they will not replace it.

I'm not sure where, exactly, to go from here.  I don't think going out and throwing money away on yet another router will solve anything.

---

### Post by Peter09 on 2009-03-16
Does your router also do the DHCP bit and name serving? Could there be some confusion in routing once the router is connected, i.e with two machines, well theres only one place to go, but connect the router and your machines will be asking for routing information.......

What happens with the router connected but not the modem?

Have you looked at your router logs?

---

### Post by Peter09 on 2009-03-16
Hey,
I have always been a bit confused by the IP number that you have shown

192.168.1.171 is a Class B address, however the mask you show, 255.255.255.0 is a class C mask. Unless you have more thqan 255 machines on your LAN you should be using an address like.

192.168.0.xxx

Whats more if I ping 192.168.1.171 I get this

> pc@toshlaptop:~$ ping 192.168.1.171
PING 192.168.1.171 (192.168.1.171) 56(84) bytes of data.
From 194.159.161.35 icmp_seq=1 Packet filtered
From 194.159.161.35 icmp_seq=2 Packet filtered
From 194.159.161.35 icmp_seq=3 Packet filtered
From 194.159.161.35 icmp_seq=4 Packet filtered
From 194.159.161.35 icmp_seq=5 Packet filtered
From 194.159.161.35 icmp_seq=6 Packet filtered
From 194.159.161.35 icmp_seq=7 Packet filtered
From 194.159.161.35 icmp_seq=8 Packet filtered
From 194.159.161.35 icmp_seq=9 Packet filtered
From 194.159.161.35 icmp_seq=10 Packet filtered
From 194.159.161.35 icmp_seq=11 Packet filtered
From 194.159.161.35 icmp_seq=12 Packet filtered


and doing a whois gives me

> pc@toshlaptop:~$ whois 192.168.1.171

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   192.168.0.0 - 192.168.255.255 
CIDR:       192.168.0.0/16 
NetName:    IANA-CBLK1
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:    [http://www.arin.net/reference/rfc/rfc1918.txt](http://www.arin.net/reference/rfc/rfc1918.txt)
RegDate:    1994-03-15
Updated:    2007-11-27

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  [email]abuse@iana.org[/email]

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  [email]abuse@iana.org[/email]

# ARIN WHOIS database, last updated 2009-03-15 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.


I think you have an invalid LAN domain.


Edit: Having second thoughts on this conclusion ... may be an artifact of routing from my domain..

---

### Post by dmizer on 2009-03-16
Do you still have the same problem if you just remove the switch and go directly through the router?

---

### Post by H.Callahan on 2009-03-17
Due to the way the wiring is set up, that would be difficult to do.  The machines that are hooked to the switch are physically located away from the router and the physicality makes it difficult to run additional wiring to go direct to the router.  I have replaced the switch with 3 different units

The wiring of the network is basically:
```

INTERNET
/\
||
\/
Modem <-> Router <-------> Switch <------> Windows XP Desktop
             \                |<---------> Working Ubuntu Desktop
             /                |<---------> Problem Ubuntu Desktop
             \
   Wireless WinXP Laptop 1
   Wireless Vista Laptop 2
```

---

### Post by Peter09 on 2009-03-17
Do you get the problem if you disconnect the router from the mode, so that you have no Internet connection.

---

### Post by H.Callahan on 2009-03-17
Haven't tried that yet.  I get yelled at by the two laptop users if I disable the Internet.  I'll have to wait until they are off (rarely) to try that.

---

### Post by dmizer on 2009-03-17
I'm positive there are better ways to troubleshoot this, I simply don't know them.

Is your switch (and all connected computers) gigabit? If so, you could try bumping your MTU to something larger than 1500. Check your switch documentation to determine what the ideal MTU is.

---

### Post by H.Callahan on 2009-03-18
The switch is 10/100, as are the connections on the router.  I only have one machine (the wired Windows machine) currently capable of gigabit, so the itch to upgrade has been marginal.

---

### Post by simonfogliato on 2009-03-25
Hey I have had this exact same issue with a similar network!

My Network:
 DLink Router ) ) ) )Wireless) ) ) Client VNC
   |
   |Ethernet
   |
 Ubuntu[With VNC Server]

Now my issue is, no matter what client I use XP, Vista, or Ubuntu when I am logged in over wireless to my server PC. After some time it seems that I will loose my connection to my VNC server. I can always continue to ping the server and even samba will still work but VNC will no longer respond. I suspect that it has something to do with Ubuntu updates on my server that might be closing my VNC connection.

---

### Post by H.Callahan on 2009-03-26
There is no easy way for me to reconfigure to totally run without the router.  However, I have tried 2 separate routers, each with 3 firmware loads (the original that came with the router, the latest updated firmware from the manufacturer, and the latest version of DD-WRT (24sp1, IIRC)) all with no change.

I think I am close to done with this and am about to go back to Windows.  I can't seem to make any headway with this problem and it is frustrating particularly when I have an OLD generation machine sitting right next to it running without a single hickup.  This machine was intended to be a replacement for the older machine.  Having it be a Windows machine is going to complicate life a bit, but I have to be able to get to the desktop remotely and reliably.

*sigh*

---

### Post by loy on 2009-03-30
Do you use standard firewall (UFW)? If yes, try to turn off it.

If it helps see similar problem solution: [http://ubuntuforums.org/showthread.php?t=1071999](http://ubuntuforums.org/showthread.php?t=1071999)

---

### Post by coutts99 on 2009-03-30
> **Peter09 said:**
> Hey,
I have always been a bit confused by the IP number that you have shown

192.168.1.171 is a Class B address, however the mask you show, 255.255.255.0 is a class C mask. Unless you have more thqan 255 machines on your LAN you should be using an address like.


I think you have an invalid LAN domain.

His network is perfectly valid.

---

### Post by H.Callahan on 2009-03-30
> **loy said:**
> Do you use standard firewall (UFW)? If yes, try to turn off it.

If it helps see similar problem solution: [http://ubuntuforums.org/showthread.php?t=1071999](http://ubuntuforums.org/showthread.php?t=1071999)

I am using whatever the default firewall is on the router.  I have not played with the Linux capabilities of the DD-WRT firmware.  All the configuration I have done is through the supplied web interface.  I am not sure I am comfortable in turning it off (at least as a permanent solution).  I don't quite understand the CLI solution that you provided on the last post.  Can you elaborate a little?

---

### Post by edthefox on 2009-03-30
Have you tried to run wireshark? 
```
sudo apt-get install wireshark
```
then
```
su-to-root -X -c /usr/bin/wireshark
```

That will give you a pretty good idea of what's going on.

 Also, I haven't seen any mention of your wiring. Are you plugging into a network jack in the wall/patch pannel? I have found a bad connection in a patch panel to cause problems before. In fact, I have one machine that refuses to work without errors at 100mbps I have to force it to run at 10mbps because of crappy wiring!!

---

### Post by Iceman_B on 2009-03-30
Wow, I have a surprisingly similar problem.
First my setup:
```

[laptop]-[switch]-----[router]-[server]
          | |           |
          | |           \---[Modem]=====>Internet
          |  \---[Housemate's PC]
           \---[Xbox360]
```

Everything CAT5, except the cable between router and server, that's a CAT6, apaprantly came with a PS3.
The router is a WRT54GL is flashed with DD-WRT v24SP1.

The server is an old Dell Dimension 8200.
P4 1,6 Ghz, 256 MB ram.
I replaced the 20GB Harddrive with a 160GB one.
On the old drive, I had Ubuntu 8.10 Desktop installed.
I installed OpenSSH server on it and never had a dropping connection, neither from the local network, nor from over the internet.

After I switched the harddrive, I installed Ubuntu 8.10 server on it. It uses only half of my RAM so I though that was good.
I have NO gui and I have no monitor, only a HDtv that is incapable of displaying text-mode resolutions :(
So working on the machine locally will be a problem, I'd have to borrow a monitor and a keyb. or something.

The problem is that my server drops SSH connections randomly.
Either when I connect via putty from this laptop(eth or wifi).
I can ssh into my router, and then from my router into my server.
Even THAT drops.

Nothing else changed with my configuration, hardware wise.
I have no idea where to start looking for this problem.
I have a tcpdump capture uploaded(90Kb):
[http://members.chello.nl/r.bhikhie/tcpdump_30mar](http://members.chello.nl/r.bhikhie/tcpdump_30mar)

The stray UDP packets are because I was running rTorrent on port 59999, on 8.10 Desktop.

Anyone have a clue what to look for? It;s frustrating me to no end.
I'm close to just giving up and returning to Windows.

---

### Post by dmizer on 2009-03-30
@Iceman_B, can you bypass the switch? In other words, run everything through the router for testing? Or, at least run the target computer and client through the router.

H.Callahan indicated that all network equipment was replaced except the switch as it was impossible to do so. I have suspected for a while that the switch might be the culprit. If you can test this, it might be another step in pinpointing the trouble.

---

### Post by loy on 2009-03-31
> **H.Callahan said:**
> I am using whatever the default firewall is on the router.  I have not played with the Linux capabilities of the DD-WRT firmware.  All the configuration I have done is through the supplied web interface.  I am not sure I am comfortable in turning it off (at least as a permanent solution).  I don't quite understand the CLI solution that you provided on the last post.  Can you elaborate a little?

Hi
I had similar problem. My SSH connection hanged randomly.
I had activated standard firewall (UFW) and there was the problem with following rule line:
[INDENT]**-A ufw-before-input -m conntrack --ctstate INVALID -j DROP**[/INDENT]

Check it and try to run following commands on your Ubuntu server:
**```
sudo iptables-save | grep -i invalid
```** If mentioned rule line is listed probably you have UFW activated. Try to comment this rule in **/etc/ufw/before.rules** file and restart UFW.

I commented it on my Ubuntu server (v8.04) and suddenly my connections became reliable.

---

### Post by Iceman_B on 2009-03-31
> **dmizer said:**
> @Iceman_B, can you bypass the switch? In other words, run everything through the router for testing? Or, at least run the target computer and client through the router.

H.Callahan indicated that all network equipment was replaced except the switch as it was impossible to do so. I have suspected for a while that the switch might be the culprit. If you can test this, it might be another step in pinpointing the trouble.

I can SSH over WiFi from my laptop to my router(has no hickups), and then ssh from my router to my server. Will this do?
The link between router and server SEEMS to be more stable, but it loses connection just as random.

I can also replace the CAT-6 between router and server with a long factory made CAT5 that reads 568-A but is seemingly wired up as 568-B. Both ends have the same wiring though, so that should be good.
Also, I think I turned off the firewall in my router but that shouldnt be an issue since everything is on the LAN side.
I haven't touched the Router security config. DD-WRT is some form of busybox, aka very stripped down version of Linux.
If needed I can get data from my router through the commandline, but someone will have to tell me what to type.

I still have the problem today.
Oh more more edit: Whenever I can't SSH to my server immediately after a drop pings dont work either.

---

### Post by H.Callahan on 2009-03-31
edthefox, I posted this a couple of pages ago:
> **H.Callahan said:**
> 
The wiring of the network is basically:
```

INTERNET
/\
||
\/
Modem <-> Router <-------> Switch <------> Windows XP Desktop
             \                |<---------> Working Ubuntu Desktop
             /                |<---------> Problem Ubuntu Desktop
             \
   Wireless WinXP Laptop 1
   Wireless Vista Laptop 2
```

> **dmizer said:**
> H.Callahan indicated that all network equipment was replaced except the switch as it was impossible to do so.
Not true.  The switch was replaced.  What I can't do is run the problem Ubuntu Desktop and/or the Windows XP desktop and/or the working Ubuntu desktop at the same time off the router.  The reason for this is that the line between the Router and the Switch is a single Cat 6 cable that has a difficult routing.  I can disconnect it from the switch and attach it to any of the three machines downstream from the switch, but I can not connect multiple machines to that single Cat 6 cable without some sort of switch or hub.  Running additional cables from the router to the switch would be problematic.

---

### Post by Iceman_B on 2009-04-01
Small updates:
I tried another Kernel on suggestion:

Linux Rin-chan 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

I also switched the Cat6 cable with an old Cat5 one. No difference.
No clue what it could be, it might be a hardware problem after all...
Update:

I FIGURED IT OUT.
Turned out my Nintendo Wii was configured with the same IP address as my server >_<.
The Reason it wasn't a problem until now was that I has left it on total standby.
A few days ago I turned it on and off again, and then it remained in standby with the Wiiconnect24 service running.
Meaning it checks in with Nintendo every now and then to see if new notifications have arrived.
That would explain the dropping connections.

This line from Wireshark pointed me towards it.
Ethernet II, Src: QuantaCo_27:26:f4 (00:c0:9f:27:26:f4), Dst: Nintendo_cc:da:c5 (00:17:ab:cc:da:c5)

I even had it written down in my configuration text file....

So if you have inexplicable network drops people, please check all your hardware for their IP.
Or be clever and use DHCP.

---

### Post by H.Callahan on 2009-04-02
What I can't wrap my head around is that if it is a piece of network equipment that is causing the problem, then why isn't it causing a problem with the other connected machines, particularly the Ubuntu machine that seems to operate correctly?  I have changed the NIC in the bad computer with no help.  I think it is probably not hardware, so I get back to thinking that it has to be something in the configuration of the bad machine.  As I have tried 3 releases of Ubuntu, I don't think it is something inherient in a specific version, either.

---

### Post by Iceman_B on 2009-04-03
I have no other suggesstion than a possible IP conflict.
While I was trying to hunt down the problem I had, multple people suggested a possible IP conflict. I was too stubborn to actually consider it but it turned out that I had forgotten something in a game console, which I configured a long time ago, manually.

Other than that, try running programs like tshark and/or tcpdump, see what that uncovers. That's about all I can think of.

---

### Post by H.Callahan on 2009-04-06
I have (re)verified that IP address are correct and non-conflicting.

---

### Post by chrysler on 2009-04-28
I have the same problem as well. I remember that there is no such problem when I use ubuntu 8.04 or before. This problem occurs at ubuntu 8.10 and 9.04.

I tried several scenarios.

First, I mount remote path by sshfs
$ sshfs [email]xxxx@xxx.xxx.xxx.xxx[/email] /media/xxx

Then, I copy the local files to remote will be failed. Like this:
$ cp ~/Desktop/xxx.mp3 /media/xxx/
cp: writing `./xxx.mp3': Software caused connection abort
cp: closing `./xxx.mp3': Transport endpoint is not connected

The connection is also dropped.
However, it is all right if I copy the remote file to local disk.

I also tried NFS. The same problem occurs too. The local files can not copy to remote storage, but the remote files can be "download" normally.

I tried to find the solution by google, but I never get a solution so far.

---

### Post by H.Callahan on 2009-05-04
I have found nothing that works either.  I have kind of abandoned the machine for now.  It will probably get wiped and have Windows put on it.  I have to be able to get to the machine remotely (reliably).

---

### Post by jimcooncat on 2009-05-05
Reminds me of the last Dell I bought, a few years ago, at work. Didn't boot out of the box. Replaced the RAM, the CPU, then the motherboard with another new CPU, network cards, and all the drives. D*mn thing still didn't work. My time cost the company more than the thing was worth, and it went in the trash. Next time, I'll replace the case first!

---

### Post by H.Callahan on 2010-04-30
I am resurrecting this thread for an update.  I continued to have problems with this even over a couple of upgrades of Ubuntu -- until recently, when I switched the Windows VNC viewer from TightVNC to UltraVNC.  I now seem to be able to stay connected to the machine for extended periods of time.

So it seems either UltraVNC or an Ubuntu update that correspond  with the time that I switched viewers, seems to have cleared up the problem.

---

