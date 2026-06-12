---
title: "unable to access shares"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Forbees on 2009-12-06
just upgraded my netbook to unr 8.10 and i can't access my desktops 1.5tb driver that i have shared on my home network

i can PING my desktop, but when i'm in the network folder it doesn't display anything

tried a few things that work w/ windows and got nothing (manually typing my ip address in, using the computers name etc)

in 8.4 i had no problems, but upgrading did something.


i'm connected to my router, i can ping my desktop, can't access desktop to get to shared files

---

### Post by sedawk on 2009-12-07
There is a command line tool called "smbclient" that
you can use to connect to further debug the problem.
The syntax can be tricky, check the internet for examples I 
do not have the setup to create working examples currently ...

---

### Post by Forbees on 2009-12-07
well i looked a little and tried entering my desktops IP to connect
```

$ smbclient -L 192.168.1.100
Enter forbees's password:
session request to 192.168.1.100 failed (Called name not present)
session setup failed" NT_STATUS_LOGON_FAILURE

```

having trouble figuring out how to fix that

---

### Post by Forbees on 2009-12-07
also, if i login w/o a password i get a sucesful "anonymous login" which than displays that my desktop is running windows 7 than proceeding to the setup failure

---

### Post by Forbees on 2009-12-08
```

forbees@forbees-laptop:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.104   FORBEES-LAPTOP [WORKGROUP] [Unix] [Samba 3.4.0]

```

so i can ping my desktop, but samba can't find it

wtf

---

### Post by Forbees on 2009-12-08
```

forbees@forbees-laptop:~$ smbtree
Enter forbees's password: 
WORKGROUP
	\\XION           		
cli_start_connection: failed to connect to XION<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\JADEPUNK89     		
cli_start_connection: failed to connect to JADEPUNK89<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\FORBEES-LAPTOP 		forbees-laptop server (Samba, Ubuntu)
		\\FORBEES-LAPTOP\downloads      	
		\\FORBEES-LAPTOP\IPC$           	IPC Service (forbees-laptop server (Samba, Ubuntu))
		\\FORBEES-LAPTOP\print$         	Printer Drivers
	\\APRIL-MD805    		
cli_start_connection: failed to connect to APRIL-MD805<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\ANONYMOUS      		
cli_start_connection: failed to connect to ANONYMOUS<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

```

getting more confused lol findsmb does nothing but smbtree admits the existence of other computers?

---

### Post by Forbees on 2009-12-08
smb://192.168.1.100/ works . . . . 

so by removing one " / " i can now get to my windows 7 machine manualy. but samba is just messed from this newer version

i've been noticing alot of people having this problem and it took me forever to find anything useful

UBUNTU, FIX SAMBA

it was working fine in 9.04, but why not  9.10?

apparently alot of people have been having this problem since 8.04

i'll be waiting for an update/patch to fix it

---

### Post by Goatrancer on 2010-02-08
I'm having similar problems (the Error NT_Status_Unsucessful message), also with netbook remix 9.10), I hope a solution comes soon! The smb server I am trying to connect to is on a mac (which is sharing via smb)

---

### Post by l.clayton.parker on 2010-05-03
Same problem more or less with a few caveats. This is a problem that sporadically goes away. As in MOST of the time I cannot see computers or printers on the Windows network. However, sometimes I can, although only briefly and very sporadically.

For instance, after trying a variety of things such as smbtree etc, it suddenly and without any change in configuration suddenly went past the Windows Network icon to show me the actual machines on said network, but it would NOT let me connect to or even view the shares on said machines. Just went back to the "Unable to mount location, Failed to retrieve share list from server" error message.

Attempting to install a network connected printer suddenly began showing the machines on the network at the same time. It also would not let you see or connect to an actual shared printer. Curiously, typing in the full smb://domain/server/printername path actually printed a test page, verifying that it was able to connect to the device, but it still generates the usual "Connection failed: NT_STATUS_UNSUCCESSFUL" message while attempting to print the test page, and the test page actually only prints 10 to 15 minutes after the job is submitted.

This is an HP laptop with an AMD Turion64, 4 GB of RAM, 500 GB HD, currently running Ubuntu 10.04 LTS. The problem occurred first under Ubuntu 9.10 (9.04 worked) and continues under 10.04. Solutions that invlove hard coding IP addresses for any of the clients, most especially the laptop are not acceptable. The network uses DHCP, all addresses must remain dynamic, assigning a static address is out of the question.

Lee

---

### Post by sikilpaake on 2010-07-17
i still can't understand why they haven't been able to fix this..:-?

i have one freebsd samba server and three client computers on this network. of the three clients, one is a windows xp laptop and the remaining two are ubuntu laptops. the xp laptop and one of the ubuntu laptops *CAN SEE THE FREEBSD SAMBA SERVER JUST FINE*. they connect consistently and quickly. the bandwidth is high. everything runs as expected.

what about the third ubuntu laptop i just installed with 10.04? 

nothing.

-nautilus doesn't see it.
-pyNeighborhood doesn't see it.
-smbclient doesn't see it.
-findsmb doesn't see it.

connecting to it through nautilus by using the server's ip address doesn't work, either. the only time i have managed to connect to it, the bandwidth is ridiculously slow.

WTF???!!!!:confused:

i have had friends come over who connect to the server from macs and windows laptops. but this ubuntu laptop i just installed is NO GO (and yeah, this same laptop had xp before, and i could connect to the laptop from there, as well.. so its *NOT* a hardware issue. i can browse the internet just fine with it, as i'm using it now to post this message).

this kind of thing is totally unacceptable.[-X

sure, ubuntu devs: the non-free video card drivers work great, the security is good, the system updates flawlessly, the repositories are well-populated, i can get all my work done without futzing around.. BUT..

just please get your sh*t together regarding samba. [-o< yes: it's important.

---

### Post by Forbees on 2010-07-18
i'm surprised people are still on this thread

i can't say 10.04 fixed it cause my whole situation has changed

using UNR 10.04 now, not using Ubuntu server anymore, i'm now using a DNS-321 and it works fine

---

### Post by sikilpaake on 2010-07-19
> **sikilpaake said:**
> i still can't understand why they haven't been able to fix this..:-?

i have one freebsd samba server and three client computers on this network. of the three clients, one is a windows xp laptop and the remaining two are ubuntu laptops. the xp laptop and one of the ubuntu laptops *CAN SEE THE FREEBSD SAMBA SERVER JUST FINE*. they connect consistently and quickly. the bandwidth is high. everything runs as expected.

what about the third ubuntu laptop i just installed with 10.04? 

nothing.

-nautilus doesn't see it.
-pyNeighborhood doesn't see it.
-smbclient doesn't see it.
-findsmb doesn't see it.



:^o:-#8-[ I EAT CROW: it seems it *was* a hardware problem after all.. or rather a hardware networking problem

here's what happened:

..i have a cablemodem that pretty much just acts as a bridge, and then  actually share my ethernet/wifi connections through a linksys wrt. the cablemodem still provides dhcp, though, as i couldn't find a way to turn that off. the cable modem's ip is 192.168.0.1.. and the linksyts wrt's ip is 192.168.1.1: the 3rd octet isn't "zero", but "one".. methinks because it's its own subnet, or something like this (i forget the nomenclature, its been a while)..

anyway, while trying to get [synergy]("http://synergy2.sourceforge.net") going, i ran "ifconfig" to learn to learn the problematic ubuntu laptop's ip, and noticed the 3rd octet  was "zero", 192.168.0.3.. meaning, that it was being set up on the cablemodem's network, and not on the linksys wrt's. 

i then ran "sudo dhclient eth0", to confirm my theory that it was the cablemodem giving this machine its ip. sure enough, it was.

so i followed the ethernet cable back to the rack and found that it was connected *not* to the linksys wrt, but to the cablemodem.

connecting it to the linksys solved everything. end of story.

---

### Post by Forbees on 2010-07-19
yeah i wasn't doing anything THAT complex lol

---

### Post by jjthomas on 2011-06-19
Same problem with ubuntu 11.04.  Had Fedora 15 installed and could see the shares.  Installed ubuntu 11.04 on the same computer and have no access to the shares.  

*** :oops: Found my problem.  When I installed Fedora I set my IP address during the installation.  Ubuntu uses DHCP, my network server provides all name resolution and was showing my computer as .5.  With DHCP, it assigned the address .144.  Changed my ubuntu address to .5 and everything is working fine.  

-JJ

---

