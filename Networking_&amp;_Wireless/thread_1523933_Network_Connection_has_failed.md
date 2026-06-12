---
title: "Network Connection has failed"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by Jonners59 on 2010-07-04
I installed Ubuntu 10.4 side by side with my Vista.  This is on a PC I leave on permanently and use as a sort of Sever, so Security and Network connection are VERY important on this device.

I use it for documents and IP PBX (telephone system).  I currently use Vista and 3CX, but I plan to roll it over to Unbuntu full time once its up and runnng correctly - I will just need to change the Grub2 conf priority.

After install, all was fine and I managed to make many changes to settings, apps and updates, but I have noticed in the past week when going in to make further changes the network has suddenly stopped working!  According to Network Manager  and the icon on the panel it is connected and I can not see anything obvious that is not correct.  I tried doing a PING (192.168.1.1) from Network Manager to the main router, but it failed.

I know that there is nothing wrong with the network nor the card or PC it all sits on...  It's working now with Vista and my other machines.  It must be a config some-where...

Can anyone help me please.

---

### Post by Morbius1 on 2010-07-07
Since you asked for my help in someone else's thread I'll respond here. The reason no one's responding to this post is probably the reference to PBX and 3CX. I for one know nothing of these so I'm afraid I can't be of any help. You did post this output of smbtree in that other post:
> onathan@jonathan-laptop:~$ smbtree
Enter jonathan's password: 
WORKGROUP
JONATHANECHIARA
    \\SERVER                 server
cli_start_connection: failed to connect to SERVER<20> (0.0.0.0).  Error NT_STATUS_BAD_NETWORK_NAME
    \\LOCALHOST              Vigor 2820 Samba Server
        \\LOCALHOST\music              
        \\LOCALHOST\dcim               
        \\LOCALHOST\share              
        \\LOCALHOST\documents          
        \\LOCALHOST\videos             
        \\LOCALHOST\desktop            
        \\LOCALHOST\pictures           
        \\LOCALHOST\IPC$               IPC Service (jonathan-laptop  server (Samba, Ubuntu))
        \\LOCALHOST\print$             Printer Drivers
    \\JONATHAN-LAPTOP        jonathan-laptop server (Samba, Ubuntu)
        \\JONATHAN-LAPTOP\music              
        \\JONATHAN-LAPTOP\dcim               
        \\JONATHAN-LAPTOP\share              
        \\JONATHAN-LAPTOP\documents          
        \\JONATHAN-LAPTOP\videos             
        \\JONATHAN-LAPTOP\desktop            
        \\JONATHAN-LAPTOP\pictures           
        \\JONATHAN-LAPTOP\IPC$               IPC Service  (jonathan-laptop server (Samba, Ubuntu))
        \\JONATHAN-LAPTOP\print$             Printer Drivers
    \\CHIARAPC               Chiara'sPC
cli_start_connection: failed to connect to CHIARAPC<20> (0.0.0.0).  Error NT_STATUS_UNSUCCESSFUL                      > NT_STATUS_BAD_NETWORK_NAMEThis usually means the server name is more than 15 characters long, has spaces in it's name, or has wierd characters.
> \\LOCALHOST              Vigor 2820 Samba ServerI'm not sure what that is but you can't have localhost as a netbios name. You need to go into the smb.conf of that box and give it a name by adding the following to the [global] section:
```
netbios name = something other than localhost
```> cli_start_connection: failed to connect to CHIARAPC<20> (0.0.0.0).  Error NT_STATUS_UNSUCCESSFUL                        Unfortunately that error message is intended to be read literally. From one of the Samba developers:
> NT_STATUS_UNSUCCESSFUL
is the generic "something went wrong" we use in Samba we we aren't given a specific error back from the server.Samba itself has no clue what's wrong and neither do I.

Sorry I could not be of any help.

---

### Post by Jonners59 on 2010-07-07
Thanks Morbius1
Not sure why the PBX/3CX is a problem for people picking up, I was just trying to explain what I use the PC for, not for help with these.  The issue is that "server" does not connect to the network...

[HTML]You did post this output of smbtree in that other post:
 	Quote: 	 	 		 			 				onathan@jonathan-laptop:~$ smbtree[/HTML]
The report you are referring too was in fact a different machine.  It is  my Laptop which was working at the start of the thread, then suddenly  stopped, so I fed back my smbtree and other info to get a quick fix  there.  It was related as you will note they (the originator) are BOTH with  the same problem and BOTH are Toshiba Laptops...  It did get up and  running again, as per my follow on note when I did the things you  suggested to the smb.conf file.  I also do not understand why I have "Localhost"...  I did not create it, it just appeared.  It is in fact the DSL router!!!

Getting back to the point:  The PC **this Thread is about** is called "server" as that is how we use it.  I have created a report this AM (I shut down Vista and re booted in to Ubuntu and then ran the commands you suggested to create the reports, and then rebooted back in to Vista before going out - I need to past the results in here).

[HTML]\\SERVER                 server
cli_start_connection: failed to connect to SERVER<20> (0.0.0.0).   Error NT_STATUS_BAD_NETWORK_NAME[/HTML]
[HTML]cli_start_connection: failed to connect to CHIARAPC<20> (0.0.0.0).   Error NT_STATUS_UNSUCCESSFUL 			 		[/HTML]
As for name length, "server" is the name of the central PC and the other one is "ChiaraPC" (my wife's).  Neither has odd characters or are over 15 ch long, so I am confused.[IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG]

As I have mentioned in the other thread, this is very flaky, and I have found the NT Status message comes and goes.  I have to try repeatedly to connect to any devices or the LAN and sometimes it works first click.  Any way, That's not the point.  This machine to which I refer "server", does not see the LAN, even though it says it is connected.  If I run it in Vista, it works fine.  I want to move away from Windows, so I need to fix this problem.
[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]
Reports to follow.

So any leads are welcome, please.

---

### Post by Jonners59 on 2010-07-07
Report as promissed:
  	 	 	 	 	[HTML]root@server:/home/server# ls -dl /home/server  
 drwxr-xr-x 42 server server 4096 2010-07-07 09:00 /home/server  
 root@server:/home/server# net usershare info  
 root@server:/home/server# sudo net usershare info  
 root@server:/home/server# testparm –s  
 Load smb config files from –s  
 rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)  
 params.c:OpenConfFile() - Unable to open configuration file "–s":  
 	No such file or directory  
 Error loading services. 
 root@server:/home/server# net usershare info  
 root@server:/home/server# sudo net usershare info  
 root@server:/home/server# testparm -s  
 Load smb config files from /etc/samba/smb.conf  
 rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)  
 Processing section "[printers]"  
 Processing section "[print$]"  
 Loaded services file OK.  
 Server role: ROLE_STANDALONE  
 [global]  
 	workgroup = JONATHANECHIARA  
 	server string = %h server (Samba, Ubuntu)  
 	map to guest = Bad User  
 	obey pam restrictions = Yes  
 	pam password change = Yes  
 	passwd program = /usr/bin/passwd %u  
 	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .  
 	unix password sync = Yes  
 	syslog = 0  
 	log file = /var/log/samba/log.%m  
 	max log size = 1000  
 	dns proxy = No  
 	usershare allow guests = Yes  
 	panic action = /usr/share/samba/panic-action %d  
 	force user = server  
 

 [printers]  
 	comment = All Printers 
 	path = /var/spool/samba  
 	create mask = 0700  
 	printable = Yes  
 	browseable = No  
 	browsable = No  
 

 [print$]  
 	comment = Printer Drivers  
 	path = /var/lib/samba/printers  
 root@server:/home/server# ls -dl /home/server/Documents  
 drwxr-xr-x 5 server server 4096 2010-05-17 21:35 /home/server/Documents  
 root@server:/home/server# 
 [/HTML]

I have just found that I can find the "server" PC from my other PCs, but the "server" PC itself can not see the outside world nor can it see the other PCs on my LAN.

Can anyone help me please?[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by Iowan on 2010-07-07
Check **route -n**
I presume the machine has an address in the 192.168.1.X subnet...
(Check via **ifconfig -a**)

---

### Post by Jonners59 on 2010-07-08
> **Iowan said:**
> Check **route -n**

[HTML]                                  root@server:/home/server# route -n
 Kernel IP routing table
 Destination      Gateway          Genmask                Flags   Metric   Ref      Use   Iface
 192.168.1.0      0.0.0.0           255.255.255.0         U        1             0        0       eth0
 169.254.0.0      0.0.0.0           255.255.0.0             U        1000       0         0      eth0
 0.0.0.0            192.168.1.1     0.0.0.0                   UG       0            0         0      eth0[/HTML]
OK, I am not quite sure what all this means, but I do not think it is correct.  My Gateway and DNS are 192.168.1.1  DNS is also 4.2.2.2, 4.2.2.3


> **Iowan said:**
> I presume the machine has an address in the 192.168.1.X subnet...
(Check via **ifconfig -a**)

[HTML]   	 	 	 	 	 	  root@server:/home/server#  ifconfig -a
 eth0      Link encap:Ethernet  HWaddr 00:1f:d0:58:4c:2b   
           inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
           inet6 addr: fe80::21f:d0ff:fe58:4c2b/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:117 errors:0 dropped:0 overruns:0 frame:0
           TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:36709 (36.7 KB)  TX bytes:23417 (23.4 KB)
           Interrupt:23 Base address:0x2000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:3745 errors:0 dropped:0 overruns:0 frame:0
           TX packets:3745 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0  
           RX bytes:278638 (278.6 KB)  TX bytes:278638 (278.6 KB)
 

 root@server:/home/server[HTML]


Again not sure what this is about, but it looks OK.  In terms of what works in Vista, the gateway is 192.168.1.1  The DNS is 192.168.1..1, 4.2.2.2, 4.2.2.3 and one other...  This may explain why when I boot up Firefox, I get no access to the outside world.  I, also, can not log in to any device via Firefox on the LAN including the router and other LAN devices.


I also can not find any device via "connect to Server" or "Network", yet other PCs and Laptops can see it.


Hope this helps.  Please let me know if there is anything else you need to know or things you need me to do.

---

### Post by Iowan on 2010-07-08
:-k <scratching head>
Hmmm...
**ifconfig** results look OK - machine has address in subnet.
**route** shows gateway as 192.168.1.1.
I presume right-clicking Network Manager icon shows Networking enabled (or the other configuration probably wouldn't have happened.)
**cat /etc/resolv.conf** should show your DNS nameservers... but even without them, you *should* be able to ping 192.168.1.1 (unless there are some firewall rules in place that are doing odd things).

---

### Post by Jonners59 on 2010-07-09
> **Iowan said:**
> :-k <scratching head>
Hmmm...
**ifconfig** results look OK - machine has address in subnet.
**route** shows gateway as 192.168.1.1.
I presume right-clicking Network Manager icon shows Networking enabled (or the other configuration probably wouldn't have happened.).

Yes....  It would have made it easier!

I'm not a techie, and I am lost completely.  It did work to start with, otherwise I could not have installed and got the first updates.  It seemed to have *stopped *(if the Update Manager is to go by) about 40 odd days ago when it did its last update.  I only go into the PC from time to time to work on it because it is disruptive (holds the telephone system and all the family docs etc). 

> **Iowan said:**
> 
 **cat /etc/resolv.conf** should show your DNS nameservers... but even  without them, you *should* be able to ping 192.168.1.1 (unless  there are some firewall rules in place that are doing odd  things). I will try today.  I have to copy and past your comments on a document and save it on one of the media/directories on the PC via another machine (this laptop), and then go into the PC and reboot into Ubuntu (it's currently running on Vista), retrieve and run the tests - it gets messy!!!!!

Is the Kernal routing table correct...?  I mean the Destination should be 192.168.1.1 and so should the Gateway????

But that is also the point.  It did work and it works on Vista, so the cards (MAC Address) and the IP Address are accepted by the router.  What else could there be??????

---

### Post by Jonners59 on 2010-07-09
> **Iowan said:**
> :-k
**cat /etc/resolv.conf** should show your DNS nameservers... but even without them, you *should* be able to ping 192.168.1.1 (unless there are some firewall rules in place that are doing odd things).

This is the out put.

          root@server:/home/server# cat /etc/resolv.conf
 # Generated by NetworkManager
 nameserver 192.168.1.1
 nameserver 4.2.2.2
 nameserver 4.2.2.3
 root@server:/home/server#  
 
It works perfectly in Vista!  And other machines can find it whether Vista or Ubuntu.[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

Here are the same tests off another machine connected to the same router via Ethernet that DOES work.  They are similar, but not the same.  Does this mean anything?

baronipc@baronipc:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
baronipc@baronipc:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:85:26:9c:03  
          inet addr:192.168.1.62  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe26:9c03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:310910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:101172418 (101.1 MB)  TX bytes:34243840 (34.2 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81915 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19724800 (19.7 MB)  TX bytes:19724800 (19.7 MB)

pan0      Link encap:Ethernet  HWaddr b6:2c:af:ff:81:a7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

baronipc@baronipc:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 4.2.2.2
nameserver 208.67.220.220
baronipc@baronipc:~$

---

### Post by Iowan on 2010-07-09
A bit outta my league, but what are results of **iptables -L** ?

---

### Post by Jonners59 on 2010-07-09
> **Iowan said:**
> A bit outta my league, but what are results of **iptables -L** ?

You'll love this.  The enclosed is from the faulty machine - I could not paste into the thread so had to create a PDF - see enclosed.  It is long.

Below is from the PC connected in the same way but works.  I also tried on my Toshiba Laptop that also works and it came out with the same as the above (not the enclosed).  A clue, if you know what it all means?

[HTML]root@baronipc:/home/baronipc# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
root@baronipc:/home/baronipc#[/HTML]

What do you think??????  :icon_frown:

---

### Post by Jonners59 on 2010-07-09
Sorry, forgot attachment

Also to note:

If I select "Network" from "Places", and then select "Windows Network", I get an error message saying "Unable to mount  Failed to get share list from server".

If I go in to "Network Tools" from "System" - "Administration", I can not ping, trace route, Port Scan either this PC or the router (192.168.1.62 and 192.168.1.1).

There is a box ticked somewhere that should not be, me thinks!!!!

---

### Post by Jonners59 on 2010-07-12
Any HELP PLEASE!!!!!!

[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by Iowan on 2010-07-12
I was kinda hoping someone more versed in **iptables** would happen along. What did you use to set up those rules? **sudo iptables -F** will flush the rules - but I'm not sure I wanna suggest that (*might* be hard to put 'em back). That's why I was hoping for more experience to come along...

---

### Post by Jonners59 on 2010-07-13
> **Iowan said:**
> I was kinda hoping someone more versed in **iptables** would happen along. What did you use to set up those rules? **sudo iptables -F** will flush the rules - but I'm not sure I wanna suggest that (*might* be hard to put 'em back). That's why I was hoping for more experience to come along...

It's just not sexy enough to attract anyone.

The bulk were there when I first installed U10.4, The only changes I made at install were in Network Manager.  But I have always found that to be a poor tool.  I then changed the "workgroup" in Configuration Editor. I then also followed some instructions on the previous thread where I came across you., but it was not working before then...

If we can flush the tables, then surely we can config the tables too?  Isn't there a command to do that?  Anyway it does not work now so is there anything to loose?

---

### Post by Jonners59 on 2010-07-23
I did the sudo iptables -F and it made no difference.  I even copied and pasted from a config that worked on another machine......

Can anyone help PLEASE???

---

### Post by Iowan on 2010-07-23
Did you check again to verify that the rules got flushed?

---

### Post by Jonners59 on 2010-07-23
If you mean did I do a re-boot, yes.....  I might give it another go this weekend if I get time..

---

### Post by Iowan on 2010-07-23
Actually, I meant check **iptables -L**. :D

---

### Post by dca on 2010-07-23
If I'm getting this, on your server (this is going to screw up all the workstations that connect to it) can you access interweb using DHCP setting through network manager?  I mean remove the entry for your LAN and re-enter and see the internet that way?

---

### Post by Jonners59 on 2010-07-28
> **dca said:**
> If I'm getting this, on your server (this is going to screw up all the workstations that connect to it) can you access interweb using DHCP setting through network manager?  I mean remove the entry for your LAN and re-enter and see the internet that way?

Sorry about the delay...  I did not get an alert I had a message.

I kinda understand what you are asking, but I need a more idiot proof step by step.  Sorry (again).

The PC I refer to as "server" is just a normal PC that I use for central storage and to host my telephone system on.  That connects to a LAN with dumb (by this I mean I can not configure - cheap) 1G x 8 port LAN switches and out to the www via a Draytek Vigor 2820 ADSL2+ router (192.168.1.1).

All the workstations I have can all see one another and access the PC called "server" whether I use the Windows Vista (which I am trying to move away from) or Ubuntu 10.4.  The "server" PC can see all and access the www when in Vista, but when I cut over to Ubuntu 10.4 it can not see ANY device/workstation (includes the Draytek) nor the www, though, as mentioned the devices can see it.

Interestingly, IF I go in to the DHCP table in Diagnostics on the router the server is listed by name - no other device is, so I do wonder if that is the issue in some way....

See part of the snapshot below - there are actually 19 devices listed
       
[HTML]
Index    IP Add         MAC Add                 Lease Time  Host ID
3    192.168.1.50    00-1F-D0-58-4C-2B    FIXED IP    server
4    192.168.1.60    00-1D-92-08-EB-00    FIXED IP     
5    192.168.1.62    00-14-85-26-9C-03    FIXED IP     
6    192.168.1.63    00-1A-80-42-46-5A    FIXED IP     [/HTML]With this in mind and your query, please advise your thoughts.....

---

### Post by Jonners59 on 2010-07-30
Guys
I could not get it going, and ended up re-installing....  It works now.  Not a real fix, but shows it was not the network at least.

---

### Post by Iowan on 2010-07-30
Sometimes a re-install is required - it's just not the first thing to try ;)
Glad you got the machine functioning...

---

### Post by Jonners59 on 2010-07-30
Yes, but it is not very clever and I am concerned that we do not know what caused it, therefore we still do not know how to prevent it.

It also means I am back to base with the set up issues I had before.

However, I can now move forward.  Thanks for the help.

---

