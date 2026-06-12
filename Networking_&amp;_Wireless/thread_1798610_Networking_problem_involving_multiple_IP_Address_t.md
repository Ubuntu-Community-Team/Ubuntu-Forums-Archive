---
title: "Networking problem involving multiple IP Address types - 192 and 172"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by nef131 on 2011-07-06
I have one router, a linksys. It allows wireless and wired connections, as is normal. I have two XP machines connected by wire to the router and three linux machines connected wirelessly. The XP machines both have IP addresses beginning with 192.168. while my three linux machines have IP addresses that all begin with 172. None of the machines is connected with a static IP address. All are automatic DHCP.

I am told that the above scenario makes no sense. However, such is what I have so, I trust, the theory and the fact do not gel. I would not care except that I cannot see - using the nautilus network servers program, all of the XP computers with some of my linux boxes.

Is there a way to solve my problem? And, am I simply wrong in thinking my home network has both 192 and 172 type IP addresses via one router?

Any help would be appreciated.

---

### Post by smurphy_it on 2011-07-06
I guess that depends on what your are running for firmware in your router.  If you run something like dd-wrt for example, you can seperate the Wireless and Wired connections onto seperate vlans.

---

### Post by capscrew on 2011-07-06
> **nef131 said:**
> I have one router, a linksys. It allows wireless and wired connections, as is normal. I have two XP machines connected by wire to the router and three linux machines connected wirelessly. The XP machines both have IP addresses beginning with 192.168. while my three linux machines have IP addresses that all begin with 172. None of the machines is connected with a static IP address. All are automatic DHCP.

I am told that the above scenario makes no sense. However, such is what I have so, I trust, the theory and the fact do not gel. I would not care except that I cannot see - using the nautilus network servers program, all of the XP computers with some of my linux boxes.

Is there a way to solve my problem? And, am I simply wrong in thinking my home network has both 192 and 172 type IP addresses via one router?

Any help would be appreciated.
For some types of applications your machines need to be on the same network to work properly.  The two numbers represent different IP address ranges (i.e. different networks).  

The numbering scheme is fully configurable.  I believe you can configure your Linksys to provide addressing for both wireless and wired in the same range.

What model Linksys do you have?  Has it been updated with FOSS firmware as @smurphy_it mentioned?

---

### Post by nef131 on 2011-07-06
I am writing from work so, to note, there is the possibility that my memory is mistaken about the name of the router. However, I believe it is a WRT54G. I have never - and on this I am sure - consciously updated the firmware.

---

### Post by capscrew on 2011-07-06
> **nef131 said:**
> I am writing from work so, to note, there is the possibility that my memory is mistaken about the name of the router. However, I believe it is a WRT54G. I have never - and on this I am sure - consciously updated the firmware.
I have to believe that your wireless clients are **_not_** using the DHCP services of *your *router.  If you look at the tab for *DHCP *on the setup page for you router you will see that the range is for 1 network only.  It can be 192.168.0.0 /24 or or 172.16.0.0 /24 or some such, but not both.  In other words the the IP range is contiguous.

If this is true (confirm later), I'll bet your wired hosts are the only hosts on the default network that Linksys sets (i.e 192.168.?.?).  The 172.16.?.? is definitely not the default setting for any Linksys device.  It is however a legitimate alternative.

I have to wonder where your wireless clients are getting their DHCP assigned IP addresses from.  Do you have a wireless AP too?

---

### Post by nef131 on 2011-07-06
capscrew,

> I have to wonder where your wireless clients are getting their DHCP assigned IP addresses from. Do you have a wireless AP too?

I have no idea about this. I have no special applications running. As I noted, my linux machines, all of which have 172 IP addresses, are all wirelessly connected. My XP machines are all wired to the router.

I note that while I have some remote knowledge about computers, I tend only to use defaults, most especially on Linux, of which my knowledge runs back to April, 2011. As for XP, I have been using it for many years. As for the router, it is several years old and I have not really fussed with it, once it was set up; except at one point, my son wanted a slingbox, which required some minor tweaking of the router.

---

### Post by capscrew on 2011-07-06
> **nef131 said:**
> capscrew,

I have no idea about this. I have no special applications running. 
Were we talking about special applications?  What do you call Slingbox?> 
As I noted, my linux machines, all of which have 172 IP addresses, are all wirelessly connected. My XP machines are all wired to the router.

This is why I feel your Linux hosts are either have the IP addresses assigned manually (doubtful) or they are assigned via someone else's router (DHCP service (most probably).  The wired hosts (XP) have no choice as they are physically connected to the router and can only request addressing from that source or they are manually configured.> 

I note that while I have some remote knowledge about computers, I tend only to use defaults, most especially on Linux, of which my knowledge runs back to April, 2011. As for XP, I have been using it for many years. As for the router, it is several years old and I have not really fussed with it, once it was set up; except at one point, my son wanted a slingbox, which required some minor tweaking of the router.

I wonder what minor tweaking really means.

---

### Post by nef131 on 2011-07-06
Minor tweaks are adding programs that run on wine, using avant, etc. That is all that I mean.

---

### Post by nef131 on 2011-07-06
I forgot to answer your question regarding slingbox. I merely had to turn off the firewall and to list the slingbox IP address as a special address (or something of the sort).

---

### Post by capscrew on 2011-07-06
> **nef131 said:**
> I forgot to answer your question regarding slingbox. I merely had to turn off the firewall and to list the slingbox IP address as a special address (or something of the sort).

Yikes!  You have left the Linksys firewall off?

What address did you give the slingbox?

---

### Post by nef131 on 2011-07-06
I do not recall. In any event, I long ago turned the firewall back on.

By the way, how can I deal with the issues you mentioned previously? i.e., "This is why I feel your Linux hosts are either have the IP addresses assigned manually (doubtful) or they are assigned via someone else's router (DHCP service (most probably)."

---

### Post by perspectoff on 2011-07-06
.

---

### Post by capscrew on 2011-07-06
> **nef131 said:**
> I do not recall. In any event, I long ago turned the firewall back on.

By the way, how can I deal with the issues you mentioned previously? i.e., "This is why I feel your Linux hosts are either have the IP addresses assigned manually (doubtful) or they are assigned via someone else's router (DHCP service (most probably)."

Ah yes, the reason for the thread.  Here is what I would do:
[LIST]
[*]Determine what IP address range the DHCP server is set to (my bet is 192.168.?.?)
[*]Make sure you have enough addresses in the DHCP pool available
[*]Determine what network the wireless hosts are connecting to (not yours is my 2nd bet)
[*]Forceably have the wireless hosts join your network (your SSID)
[/LIST]

FYI -- that is why I asked what the IP address the slingbox was.  All of my questions were to determine what subnet your network resides on.

---

### Post by nef131 on 2011-07-06
capscrew,

Your assistance is truly appreciated. When I get home this evening, I shall check what is going on, so far as settings for slingbox. I wish I could recall off the top of my head.

As for your suggestions, I shall attempt to follow them, although I am not sure I know the procedure to do any of them.

In any event, I am truly grateful for your help.

---

### Post by capscrew on 2011-07-06
> **nef131 said:**
> capscrew,

Your assistance is truly appreciated. When I get home this evening, I shall check what is going on, so far as settings for slingbox. I wish I could recall off the top of my head.

As for your suggestions, I shall attempt to follow them, although I am not sure I know the procedure to do any of them.

In any event, I am truly grateful for your help.

I'm here most of the time.  :-)  

As far as my suggestions:
[LIST]
[*]The first two items are available in your Linksys device.  
[*]The third may be available in Network Manager.  
[*]The forth item is also a Network Manager item.
[/LIST]

The slingbox should be shown in the Linksys listings.

---

### Post by nef131 on 2011-07-06
Thanks!!!

---

### Post by nef131 on 2011-07-06
capscrew,

The slingbox has an IP address of 192.168.1.107 and a port range starting and ending at 5001.

As for the answer to your questions: 

> Determine what IP address range the DHCP server is set to

192.168.1.100

> Make sure you have enough addresses in the DHCP pool available

50 users listed as the maximum number of DHCP users. Not sure if that is what you are looking for.

Below is the Status summary (with my true IP X'd out):

```
 Firmware Version:     v3.03.9, Apr. 27, 2005            
                  Current Time:     Wed, 06 Jul 2011 20:34:34            
                  MAC Address:     00:10:18:09:BC:7E            
                  Router Name:     WRT54G             
                  Host Name:     FamilyComputer             
                  Domain Name:     hsd1.ma.comcast.net.            

Internet
                 

Configuration Type
                Login Type:     Automatic Configuration - DHCP            
                  IP Address:     24.xx.xx.xx            
                Subnet Mask:     255.255.252.0           
                Default Gateway:     24.xx.x.x           
                  DNS 1:     68.87.xx.xxx            
                  DNS 2:     68.87.xx.xxx            
                  DNS 3:                
                  MTU:     1500
```

I was not sure if the DNS 1 and 2 contain info which would compromise my security. So, I blotted out the last two sets of digits. If that is not an issue, let me know if it is something helpful to dealing with the problem at hand. The numbers are different for each.

> Determine what network the wireless hosts are connecting to

The linux machine in issue thinks it belongs to the same network as my other computers.

Lastly, forcibly making the machine have a 192.168 IP address caused the computer to act strangely.

---

### Post by nef131 on 2011-07-06
Correcting myself, strike: "The linux machine in issue thinks it belongs to the same network as my other computers."

What I meant is that the computer identifies itself as being connected through the same router name which my XP computers believe themselves to be connected to. They both claim to be the named network. However, the network servers part of naulilus do not show them as being on the same named network. In fact, the linux machine in issue does not see the XP machines at all.

---

### Post by capscrew on 2011-07-06
> **nef131 said:**
> capscrew,

The slingbox has an IP address of 192.168.1.107 and a port range starting and ending at 5001.

As for the answer to your questions: 



192.168.1.100



50 users listed as the maximum number of DHCP users. Not sure if that is what you are looking for.

This is consistent with your 2 wired machines.> 

Below is the Status summary (with my true IP X'd out):

```
 Firmware Version:     v3.03.9, Apr. 27, 2005            
                  Current Time:     Wed, 06 Jul 2011 20:34:34            
                  MAC Address:     00:10:18:09:BC:7E            
                  Router Name:     WRT54G             
                  Host Name:     FamilyComputer             
                  Domain Name:     hsd1.ma.comcast.net.            

Internet
                 

Configuration Type
                Login Type:     Automatic Configuration - DHCP            
                  IP Address:     24.xx.xx.xx            
                Subnet Mask:     255.255.252.0           
                Default Gateway:     24.xx.x.x           
                  DNS 1:     68.87.xx.xxx            
                  DNS 2:     68.87.xx.xxx            
                  DNS 3:                
                  MTU:     1500
```

I was not sure if the DNS 1 and 2 contain info which would compromise my security. So, I blotted out the last two sets of digits. If that is not an issue, let me know if it is something helpful to dealing with the problem at hand. The numbers are different for each.

This is the public (Internet) facing side of the router (i.e. configured by/for the IS.  The DNS servers are public.  Their addresses are well known (not secret). 

The side we are interested in is the LAN side (your network).  This most probably is```
[COLOR="Blue"]**192.168.1**[/COLOR].0 /24 = network ID
[COLOR="Blue"]**255.255.255**[/COLOR].0   = Subnet mask
192.168.1.255   = Broadcast address
192.168.1.1     = Default gateway
```

Please provide the information to confirm this.  Use this terminal command for XP```
ipconfig /all
```
You can use this terminal command for Ubuntu ```
ifconfig -a
``` 
> 

The linux machine in issue thinks it belongs to the same network as my other computers.

Lastly, forcibly making the machine have a 192.168 IP address caused the computer to act strangely.

What did it do?  What error messages?

---

### Post by capscrew on 2011-07-06
> **nef131 said:**
> Correcting myself, strike: "The linux machine in issue thinks it belongs to the same network as my other computers."

What I meant is that the computer identifies itself as being connected through the same router name which my XP computers believe themselves to be connected to. They both claim to be the named network. However, the network servers part of naulilus do not show them as being on the same named network. In fact, the linux machine in issue does not see the XP machines at all.

The named network?  The network is defined by an IP address range.  What name are we talking about?  Posting the info from the commands I mentioned above should help me.  Can you post the info you are referring to as *"the named network" *that the Linksys router provides.  Are you referring to the WORKGROUP here?

---

### Post by hsoulen on 2011-07-07
Wow! This is a very strange issue to be sure.

But I have to say, two pages worth of discussion with very little result.

I think the issue is as described probably a very simple one. Your wireless clients are probably NOT on your own network but picking up IPs from a neighbor.

Older Linksys routers do not offer separate DHCP ranges or VLANs for wireless clients vs. wired clients, unless you are using 3rd party firmware (dd-wrt/tomato etc.).

Fist things first:

[LIST]
[*]Log into your Linksys router from a browser on a wired not wireless client (probably 192.68.1.1)
[*]Check your DCHP leases and see what IPs have been assigned to what hosts, if you do not see your wireless clients you have your answer
[*]Check the routers SSID and Security, I am guessing the SSID is probably "linksys" in which case if you have a neighbor with the same defaults again you have your answer
[/LIST]

BTW, can you ping any of your 192.168.x.x wired computers from your wireless clients? If not, you are simply not on the same network.

Cheers,

Hank

---

### Post by nef131 on 2011-07-07
Hi capscrew,

Here is what comes up, first for the XP machine and then for the Linux machine:

  	 	 	 	 	 	  Windows IP Configuration
> 

         Host Name . . . . . . . . . . . . : FamilyComputer
         Primary Dns Suffix  . . . . . . . :
         Node Type . . . . . . . . . . . . : Hybrid
         IP Routing Enabled. . . . . . . . : No
         WINS Proxy Enabled. . . . . . . . : No
         DNS Suffix Search List. . . . . . : hsd1.ma.comcast.net.
 

 Ethernet adapter Local Area Connection:
 

         Connection-specific DNS Suffix  . : hsd1.ma.comcast.net.
         Description . . . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet
         Physical Address. . . . . . . . . : 00-10-18-09-BC-7E
         Dhcp Enabled. . . . . . . . . . . : Yes
         Autoconfiguration Enabled . . . . : Yes
         IP Address. . . . . . . . . . . . : 192.168.1.100
         Subnet Mask . . . . . . . . . . . : 255.255.255.0
         Default Gateway . . . . . . . . . : 192.168.1.1
         DHCP Server . . . . . . . . . . . : 192.168.1.1
         DNS Servers . . . . . . . . . . . : 68.87.71.230
                                             68.87.73.246
         Lease Obtained. . . . . . . . . . : Wednesday, July 06, 2011 10:12:58 PM
 

         Lease Expires . . . . . . . . . . : Thursday, July 07, 2011 10:12:58 PM
 

 Ethernet adapter Local Area Connection 2:
 

         Media State . . . . . . . . . . . : Media disconnected
         Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
 roller
         Physical Address. . . . . . . . . : 00-0D-56-1E-2D-36



> eth0      Link encap:Ethernet  HWaddr 78:2b:cb:f3:e7:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41354 (41.3 KB)  TX bytes:41354 (41.3 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.207.1  Bcast:172.16.207.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.145.1  Bcast:192.168.145.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr c0:f8:da:80:2c:62  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c2f8:daff:fe80:2c62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2321612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1425013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3302107050 (3.3 GB)  TX bytes:123648763 (123.6 MB)

When I set the IP address manually, the machine acts up and things start to freeze. There was no error message.

What I meant by saying that both machines are on the same network is that I log on automatically to a network of the same name.

---

### Post by nef131 on 2011-07-07
hsoulen,

The SSID is the same everywhere. It is NGAK followed by some numbers. That is the SSID I set up for the network.

The router lists all of my machines and gives them a separate 192 IP address.

---

### Post by spynappels on 2011-07-07
Your Linux machine is on the 192.168.1.0 network using its wireless adaptor.

Are you using the Linux box as a VM host, maybe using VirtualBox?
The 172.16.207.0 network is a virtual LAN which your virtual machines are connected to.

If you ping 192.168.1.102 from the XP machine, you should get replies from the Linux box.

---

### Post by nef131 on 2011-07-07
spynappels,

I am definitely not using Linux as a VMware or Virtualbox guest. I do have VMware on my machine but that is not what I am using to run Linux.

I was able to ping my Linux machine with no issues. 

Please note. I can connect to and view files on my XP machine manually, typing in the appropriate command and IP address. I have a shortcut on my Linux desktop, which works fine. However, my XP machine does not show as part of my network (or any other network) in nautilus (unless I use the shortcut I created). On my XP machine, I show two workgroups (not intentionally, mind you). It shows my XP group under the NGAK name and my workgroup under the WORKGROUP name. My linux machine shows only the WORKGROUP name and, were I to try to want to add a printer (which, when I first set up this linux box I was able to do but no longer by this means), the XP boxes, where the printers are attached, would not show up in windows printers via Samba, only the WORKGROUP workgroup.

---

### Post by nef131 on 2011-07-07
spynappels,

As an interesting aside, I decided to start up my VMWare, on which I have run XP. XP sees both workgroups. I have it set up with a "bridge" connection and had it adopt the settings of my Linux machine - which, to  note, I had set up back when I had no issues (and I do not know whether that is significant). In any event, such seems to rule out my theory that the router is the issue, since my VMware running of XP runs via the wireless.

I hope this is useful information,  somehow.

---

### Post by spynappels on 2011-07-07
> **nef131 said:**
> spynappels,

I am definitely not using Linux as a VMware or Virtualbox guest. I do have VMware on my machine but that is not what I am using to run Linux.

I was able to ping my Linux machine with no issues. 

Please note. I can connect to and view files on my XP machine manually, typing in the appropriate command and IP address. I have a shortcut on my Linux desktop, which works fine. However, my XP machine does not show as part of my network (or any other network) in nautilus (unless I use the shortcut I created). On my XP machine, I show two workgroups (not intentionally, mind you). It shows my XP group under the NGAK name and my workgroup under the WORKGROUP name. My linux machine shows only the WORKGROUP name and, were I to try to want to add a printer (which, when I first set up this linux box I was able to do but no longer by this means), the XP boxes, where the printers are attached, would not show up in windows printers via Samba, only the WORKGROUP workgroup.

Ok, I should have been clearer. The 172.16.x.x subnet is created by VMware which is running on the Linux box, the Linux box is a host, not a guest. The vmnet1 and vmnet8 entries in the ifconfig output are created by VMware Server when it is installed and running.

What I was trying to say was that this is not a networking problem per se, but rather looks like a Samba configuration issue, as I'd bet that all the boxes, Linux or Windows, are all on the 192.168.1.0 network. What we need to work out now is why the share browsing is not doing what is required, which means getting some Samba (or Nautilus) specific help.

I'm afraid I'm not so hot on either of those though....

---

### Post by nef131 on 2011-07-07
spynappels,

> Samba configuration issue

Anything you or anyone else can do to help me on this would be appreciated. And, I thank you for the help you have so far given.

---

### Post by capscrew on 2011-07-07
> **nef131 said:**
> spynappels,



Anything you or anyone else can do to help me on this would be appreciated. And, I thank you for the help you have so far given.

Yes the problem is revealed by Samba use, but it is a name services issue (DNS).  It can be solved simply by editing the /etc/hosts files on each Ubuntu host.

This explains why you can view the shares via IP address but not browse to them by the GUI.

---

### Post by nef131 on 2011-07-07
capscrew,


> Yes the problem is revealed by Samba use, but it is a name services issue. It can be solved simply by editing the /etc/hosts files on each Ubuntu host.

I also thank you for all the help you have given me. If possible, could you explain the procedure for how to correct the problem that you now see.

---

### Post by nef131 on 2011-07-07
I opened up my /etc/hosts file for my below noted linux machine and it shows as follows:

> 127.0.0.1    localhost
127.0.1.1    neal-Inspiron-N5010

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by capscrew on 2011-07-07
> **nef131 said:**
> capscrew,




I also thank you for all the help you have given me. If possible, could you explain the procedure for how to correct the problem that you now see.

Before I do that I need some more information.  The Ubuntu hosts that serve shares I need you to post the output of these terminal commands (2)```

# Provides the hostname
hostname

# Lists the samba server config
testparm -s

```

What do the XP hosts use as a WORKGROUP?

---

### Post by nef131 on 2011-07-07
hostname
neal-Inspiron-N5010

testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = NEAL-N5010
    server string = %h server (Samba, LinuxMint)
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

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by capscrew on 2011-07-07
> **nef131 said:**
> I opened up my /etc/hosts file for my below noted linux machine and it shows as follows:```
127.0.0.1 localhost
127.0.1.1 neal-Inspiron-N5010
...
```

We have a problem straight away here with the hostname.  Samba can't correctly convert hostnames that are larger than 15 characters.  The hostname on this machine is 19 characters long.  :-(

---

### Post by nef131 on 2011-07-07
capscrew,

I note that the "netbios name" is set as follows: netbios name = NEAL-N5010 .

Does that not help the problem?

---

### Post by capscrew on 2011-07-07
> **nef131 said:**
> capscrew,

I note that the "netbios name" is set as follows: netbios name = NEAL-N5010 .

Does that not help the problem?
Maybe...

---

### Post by capscrew on 2011-07-07
> **nef131 said:**
> hostname
neal-Inspiron-N5010

testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = NEAL-N5010
    server string = %h server (Samba, LinuxMint)
    map to guest = Bad User
...

I want to try something.  I can't guarantee it will work, but it might and it is simple.  There is no WORKGROUP listed in your samba configuration.  You will need to edit the /etc/samba/smb.conf file to add a line under the* netbios name = NEAL-N5010* parameter.  This should read  ```
	workgroup = <WHATEVER_NAME_YOU_CHOOSE>

```

This will create a workgroup for that host.  You should add all the other machines that have shares to the same workgroup.  This way they are grouped together visually when browsing.

---

### Post by nef131 on 2011-07-07
capscrew,

You are really high up, at this point, on my list of linux friends.

I have, thus far, only made the change on one of my linux machines. Here is the result. When I go to network servers, it sees, without any assistance, both of the XP machines. It does not - and, presumably, this is because I am no longer part of the "WORKGROUP" workgroup, sees the other linux boxes.

One last thing. If I want to add a printer - which I tested to see what workgroup computers would be seen -, the correct workgroup is seen but I only see the linux machine we are dealing with. So, is there anything else to touch or will this, I hope, resolve itself once the network change sets into the system? Also, when I take my machine to my office - as was the case yesterday and will be the case tomorrow -, will the changes I made remain? I assume they will but, nonetheless, would appreciate your views, which are, to say the least, highly respected by me.

---

### Post by nef131 on 2011-07-07
Correction,

I now can "add" - if I had a new printer - a printer from one of my XP machines. So, this is something which appears to resolve itself.

capscrew, you are a genius!!!

---

### Post by nef131 on 2011-07-07
capscrew,

One last question. Should I edit my "hostname" - which you indicated is a problem - and give it the same name as my netbios name?

---

### Post by nef131 on 2011-07-07
Not that I care as much at this point, but interestingly, if I type the command findsmb, I get the following, which, as you can see, still shows my IP address beginning with 172 (but also shows the correct workgroup). So long as I am part of my homenetwork's workgroup, I do not much care. But, I thought you would find it interesting.

> neal@neal-Inspiron-N5010 ~ $ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
172.16.207.1    NEAL-N5010    +[NGAK56598892] [Unix] [Samba 3.5.8]

---

### Post by capscrew on 2011-07-07
> **nef131 said:**
> capscrew,

You are really high up, at this point, on my list of linux friends.

Thanks :-)> 

I have, thus far, only made the change on one of my linux machines. Here is the result. When I go to network servers, it sees, without any assistance, both of the XP machines. It does not - and, presumably, this is because I am no longer part of the "WORKGROUP" workgroup, sees the other linux boxes.
The workgroup parameter only groups the shares visually.  You can have multiple workgroups and see them all.  You could have a workgroup named FLORA and another named FAUNA.  You would see both groups when browsing Networks. Try clicking on *"Windows Network"*. The **lack of any workgroup **will hide the shares.

Do the other Ubuntu hosts share files to the rest of the network.  Are those Ubuntu hosts Samba servers or just clients?> 

One last thing. If I want to add a printer - which I tested to see what workgroup computers would be seen -, the correct workgroup is seen but I only see the linux machine we are dealing with. So, is there anything else to touch or will this, I hope, resolve itself once the network change sets into the system? 
Not exactly sure what you mean here.   ????> 
Also, when I take my machine to my office - as was the case yesterday and will be the case tomorrow -, will the changes I made remain? I assume they will but, nonetheless, would appreciate your views, which are, to say the least, highly respected by me.
The settings you set in the /etc/samba/smb.conf file won't change unless you change them.  How did the netbios name get set?  By you I hope.

I'm sure that with just a few changes to the configuration we can have a consistent view of the shares on your network.  

I have to say that you were your own worst enemy with the reference to the 172 network.  In fact the title has nothing to do with your problems.  What made you frame the problem in that way?

Once again, thanks for the compliments.

---

### Post by capscrew on 2011-07-07
> **nef131 said:**
> Not that I care as much at this point, but interestingly, if I type the command findsmb, I get the following, which, as you can see, still shows my IP address beginning with 172 (but also shows the correct workgroup). So long as I am part of my homenetwork's workgroup, I do not much care. But, I thought you would find it interesting.
So many questions...  I'm happy to answer them all, but you will have to give me some time.  

It is interesting that you get the 172 address using findsmb.  The Samba deamon by default does listen on all interfaces.  We can change that too if you wish.

---

### Post by nef131 on 2011-07-07
> Do the other Ubuntu hosts share files to the rest of the network. Are those Ubuntu hosts Samba servers or just clients?

One of the other linux machines sees both workgroups and can share files. I shall add it to the same workgroup as the XP and my machine. Another linux box had the identical problem that my machine has but that is not that important at this point because it will be going on an extended trip (i.e. a son going for a semester abroad out of the country - and bankrupting me!!!). I shall, however, fix the workgroup name, as occurred for my machine. 

My machine, which you fixed - and, again, thank you - sees both of the XP machines when I open network servers. It does not see the old workgroup machines because it does not see the WORKGROUP workgroup and, if I look at things by opening up my NGAK workgroup directly in network servers, it shows only my machine and the main XP machine which is the primary machine for the router. I have, in the past, had occasional problems seeing the other XP machine from my main XP machine and then, after a while, the second machine reappears - so, I assume, the same will happen with my linux box. Am I wrong?

PRINTERS.

If I were to open the printers program, it lists my printers, which one on each of my two XP machines. If I go to Add a printer, and then, on that program, go to network and then, under network, windows printers via SAMBA - which I used, before the problem with not "seeing" XP machines began, to setup so that I could print - it now sees the NGAK workgroup but only the XP machine that is the main machine. I assume that this corresponds with what I described for going to "network servers" in nautilus. And, I hope - assume? - that problems fixes itself. I have, to see if anything improves, restarted the "2nd" XP machine. 

I hope that explanation makes sense.
> 
How did the netbios name get set? By you I hope.

By me. I was told that the initial netbios name was too long and that changing it would solve my problem. So, I changed it. The problem persisted, though - until you, thankfully, came along and helped.

The reason I mentioned the 172 was that I was told that I what I described could not be so. I wanted to know, in addition to fixing my machine, what caused the 172 and I wanted to know that I was not nuts for reporting the information I saw.
> 
It is interesting that you get the 172 address using findsmb. The Samba deamon by default does listen on all interfaces. We can change that too if you wish.

It would be appreciated. This issue exists on all of the linux boxes.

---

