---
title: "Networking Troubles."
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by MAFoElffen on 2010-07-28
Help!

Problem:  I cannot connect my Ubuntu 10.04.1 LTS PC with other PC's on my hone LAN...  My PC will connect to everthing in my LAN using any other OS (Win7, Windows Vista, OpenSolaris), but not with Ubuntu.

 I have a small home network.  I have 3 PC's networked together into a Linksys WRT-54G Wireless/Wired Router.  That router, in turn, is wired to a DSL Modem.  This router is wireless and has 4 additional ethernet ports.  2 of the PC's are getting their internet connection via wireless, 1 via wired.   There is also a wireless printer, a wireless connected PDA Smartphone and a PSP'.  There are occasionally 2 other test Franken-PC's up on this as well.  The Windows PC's are running Windows Vista and WIN7 and see and share with each other under the WORKGROUP Group.

My PC is multi-boot with Ubuntu 10.04.1 LTS Desktop, WIN7, Windows Vista and OpenSolaris (plus a few other OS'es)...   This PC has 2 Ethernet Ports and a Wireless card.  The wireless card works on this PC under the Window's OS'es... but maybe somewhat "suspect" under Ubuntu.  (Has been since I started with Ubuntu 9.10.)

From any other OS on my PC, I can see other PC's and their shared folders, get into my router through a browser... From Ubuntu, I cannot.  I can not even get to my router setup from Firefox!  But using another PC, I can see the Ubuntu PC in the LAN router table.  From that PC, My Ubuntu PC doesn't show up as a "PC" on the network- but when I tried to see if it was there by putting the IP address into a browser it said: 
```
"IT WORKS! 
This is the default web page for this server. 
The web server software is running but no content has been added yet."
```Ok, this is "different"...

I think the following are additional problems, but I'm still not sure they are related to my MAIN problem: 

When I boot or shutdown Ubuntu, I get "ath5k floor calliibration failure" messages flashing across the screen when in a text or tty mode.  "ath5k" is the driver that the D-Link AirPlus Xtreme G DWL-G520 wireless card is using- But I can still get to the internet in Ubuntu by either Eth0, Eth1 or Wlan.

Next, the other PC's are connecting to my router wirelessly to the LAN- My PC is connected ethernet..  If I try to connect to this via Wireless from my Ubuntu PC, it says it successfully connects, then less than a minute later disconnects. (on-off-on-off...)


I need help.  I'm a little lost.

---

### Post by MAFoElffen on 2010-07-31
Since the intial post had gone unanswered, I've been following other threads here for "any" ideas.  I've not really gotten anywhere on this problem.  Some things I tried, I thought helped- but later found got me nowhere.  It has just confirmed to me that I really need additional help and information.

It's just so strange!  I can see my Ubuntu PC in the LAN Router Table using the IP addres and it's named services.  If I try to connect using it's named service, I get an "unknown server" error,  When I try to use the IP address, it says it's there- but that it's a "web server."

I've had a few questions that might help me find what's going on:  

Where in Ubuntu do I change making this PC a network discoverable device? Could this be my problem?

Could it be that I have some packages installed that are masking my local network services?  Could "web services" be masking my "local network" services?  It's all a "network"- but I seem to have some "option" flagged somewhere, that's not letting me to tie everything here together.

Maybe something I have configured in Ubuntu is not talking the same language...  I seem to be learning enough about Ubuntu, to know that is "is" very configurable and adaptable- and there are so many options that I don't know where they are at or that I don't fully understand because of a differing nomenclature.

I'm sorry, I'm just a little frustrated and am thinking out loud.  Does anyone out there have any ideas on what to try?  What to check?  What to do?  Please!?! Anyone?

---

### Post by MAFoElffen on 2010-07-31
If it's any help to anyone, this is a report from my Ubuntu PC to what I have running and what it can see:[HTML]--------------------------------------------------------------------

nmap -sT -sV -T4 -n -v 127.0.0.1

127.0.0.1
80/tcp   open  http        Apache httpd 2.2.14 ((Ubuntu))
139/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
631/tcp  open  ipp         CUPS 1.4
3306/tcp open  mysql       MySQL 5.1.41-3ubuntu12.3
Initiating Ping Scan at 20:33
Completed Ping Scan at 20:33, 0.00s elapsed (1 total hosts)
Nmap done: 1 IP address (1 host up) scanned in 11.24 seconds
--------------------------------------------------------------------
--------------------------------------------------------------------

nmap -sT -sV -T4 -n -v 196.168.2.1

196.168.2.1
Initiating Ping Scan at 20:35
Completed Ping Scan at 20:35, 2.00s elapsed (1 total hosts)
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.11 seconds
--------------------------------------------------------------------
--------------------------------------------------------------------

nmap -sT -sV -T4 -n -v FerreiraFarms

FerreiraFarms
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.16 seconds
--------------------------------------------------------------------
--------------------------------------------------------------------

nmap -sT -sV -T4 -n -v 196.168.1.1

196.168.1.1
Initiating Ping Scan at 20:36
Completed Ping Scan at 20:36, 2.00s elapsed (1 total hosts)
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.09 seconds
--------------------------------------------------------------------
--------------------------------------------------------------------

nmap -sT -sV -T4 -n -v maferr-laptop

maferr-laptop
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.25 seconds
--------------------------------------------------------------------
--------------------------------------------------------------------

nmap -sT -sV -T4 -n -v maferr-laptop

maferr-laptop
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.24 seconds
--------------------------------------------------------------------
--------------------------------------------------------------------

nmap -sT -sV -T4 -n -v 192.168.2.101

192.168.2.101
Initiating Ping Scan at 11:44
Completed Ping Scan at 11:44, 2.00s elapsed (1 total hosts)
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.12 seconds
--------------------------------------------------------------------
--------------------------------------------------------------------

nmap -sT -sV -T4 -n -v 192.168.2.1

192.168.2.1
20/tcp   closed ftp-data
21/tcp   closed ftp
23/tcp   closed telnet
80/tcp   open   http     Intoto httpd 1.0
2869/tcp open   http     Intoto httpd 1.1
Initiating Ping Scan at 11:45
Completed Ping Scan at 11:45, 1.20s elapsed (1 total hosts)
Nmap done: 1 IP address (1 host up) scanned in 11.97 seconds
--------------------------------------------------------------------[/HTML]"maferr-laptop" and "192.168.2.101" are the same PC.  They were in the routier table as such during this test...

---

### Post by MAFoElffen on 2010-07-31
Strange update- This morning I can get into my router from Ubuntu's Firefox browser.  Last night I couldn't.  I still cannot connect to anythtng other than the router and internet from within Ubuntu.

The normal Ubuntu "connection tools" don't see anything.

---

### Post by drdos2006 on 2010-07-31
I had an issue with 2 NICs in my Gigabyte motherboard. Ubuntu 9.10 64 bit. Try removing one NIC, it cured my problem. The problem did not exist with other OSes.

regards

---

### Post by MAFoElffen on 2010-07-31
> **drdos2006 said:**
> I had an issue with 2 NICs in my Gigabyte motherboard. Ubuntu 9.10 64 bit. Try removing one NIC, it cured my problem. The problem did not exist with other OSes.

regards
I'm not sure that's the problem here...  It's an ASUS A8N32-SLI Deluxe motherboard.  The two Ethernet ports on my PC are "onboard" controlled with the onboard nVidia nForce4 chipset as the network controller...  They show up as Marvell Yukon II'es.  Eth0 and Eth1 show as with no confilcts and test out fine.   (Unlike Ubuntu 10.04 LiveCD and the 10.04 Server Edition's issues/dislike of my my two bridged-SLI video cards.)

I think if I had a NIC problem, I wouldn't have access to my router or to the internet.  I seem to have some services, but not others.  That's the confusing part.

Edit: No. Disabled the second ethernet port in the BIOS and it does the same.

---

### Post by new newb bie know none on 2010-07-31
This may be too simplistic for your troubles, but it helped me see a windows network here at home.  It takes about two minutes.  Cold reboot your router (unplug it).   Under the <Places> menu goto <Connect To Server>  select <Windows Share> in the drop box.  Fill in your Workgroup name into the <Server> space. Select connect tab.  Restart Ubuntu. 

I tried this and it worked.  The next day it stopped working.  I restarted and it works again.  I'm sure there is some code to fix my problem, but, right now,restarting is easier than learning how to program.

---

### Post by MAFoElffen on 2010-08-01
> This may be too simplistic for your troubles, but it helped me see a  windows network here at home.  It takes about two minutes.  Cold reboot  your router (unplug it).   Under the <Places> menu goto  <Connect To Server>  select <Windows Share> in the drop box.   Fill in your Workgroup name into the <Server> space. Select  connect tab.  Restart Ubuntu.Putting "Workgroup" into the <Server> box starts the Ubuntu Windows workgroup applet... and doesn't connect me to the Windows PC...

Cold booting the router clears the LAN Dhcp Client Table in my router.  I have an online option within it's setup to do this.... But I did as you suggested/Didn't help.

Somehow I'm not getting past the gateway from Ubuntu.  The Gateway "is" the router, using the DHCP table.  Looking from the Firefox Browser at my router's DCHP Table, I can see all the other PC's- their names and their IP addresses.  But I cannot ping any of them from Ubuntu.

I just tried the same from this PC under OpenSolaris and it has the same issues, except under it, it does see my network printer.  I don't see my network printer under Ubuntu.  If I come up under Windows Vista or Win7 with this PC and I can "touch" everything on the network.

I can see the "Gateway" IP address under my ethernet card's info... The "gateway" is my router. And the DSL modem comes up as a domain.  I "see" lots of info, but I'm lost where the disconnect is.  I tried to manually enter "smb://192.168.2.101/WORKGROUP" into a custom connection dialog... errors out also.

---

### Post by new newb bie know none on 2010-08-01
[QUOTE=MAFoElffen;9666122]Putting "Workgroup" into the <Server> box starts the Ubuntu Windows workgroup applet... and doesn't connect me to the Windows PC...


"Windows workgroup applet"????

It should connect you to: 
Windows shares on "Workgroup"-File Browser,
with an icon of each computer on your "workgroup" network.

Can you confirm this?

---

### Post by MAFoElffen on 2010-08-02
> **new newb bie know none said:**
> "Windows workgroup applet"????

It should connect you to: 
Windows shares on "Workgroup"-File Browser,
with an icon of each computer on your "workgroup" network.

Can you confirm this?
Yes it does-My Bad+Meant "folder" not "applet."  (Doing that would be the same as going tp Places>Network...)   But My Winows PCs are not showing in this folder browser.  In the network folder- I see my Network Printer (wireless), my Ubuntu Desktop PC and a Windows Network folder.  Inside the Windows Network folder is the WORKGROUP folder.  Inside the Workgroup folder (with your instructions 'sortcuts to') is only my Ubuntu Desktop PC/not seeing the other 2 windows PC's- my notebook and my roommate's PC).

From those 2 PC's, using Window's Start>Networks, they see each other, but not the Ubuntu PC ...unless I reboot that PC and come up using Win7 or Vista.  I get the same thing if I boot this same PC using OPenSolaris.  

Everyone's instructions on "how it should work'  and "how to share between them" I've read and followed for both these OS'es... But something "more basic" is going wrong here.  Physically, the connections are there.  The router is setup correctly, as far as I and others can tell.  It works if you tried to connect using Windows-to-Windows... But not Linux-to-Windows or Unix-to-Windows.  I can't even ping the other IP addresses of these 2 PC's "if" I'm under linux or unix.

That gives me an idea.  I'll try coming up on my laptop using the Ubuntu LiveCD and see if I can see my Ubuntu Desktop PC(?)  The should at least see if it's discoverable right?  Wait one...

---

### Post by MAFoElffen on 2010-08-02
Wait more than one... LOL  Laptop won't run 64bit.  Downloading 32bit LiveCD now.  In meanwhile, I have 9.10 installed on the laptop under VirtualBox... Not sure if that's going to do as that's still going through Vista....

Found a 9.10 32bit iso image on the laptop- burning to CD.  Will try that while 10.04 32bit is downloading.

---

### Post by Hopalong on 2010-08-02
Hi everyone having trouble with net connections in Ubuntu. There's a major problem in Firefox. I'm using Ubuntu Lucid, and a couple of weeks ago (? or thereabouts) my net connection stopped conecting. On my Asus PC1005P if I run Windows, explorer is fine. But if I run Ubuntu netbook remix it won't connect.
  Bearing kn mind this came about practically overnight, I went back to the Lucid installation DVD (Linux Format July 2010) and reinstalled it. It works fine. Obviously, somewhere along the online Firefox updates there's a catastrophic bug.
  The Firefox forums are no help. The problem is labelled 'solved', but the solution does not work for me. Given that I'm successfully using Firefox 3.6 of June/July (and carefully cancelling all online updates to it since) where do I go now? Has anyone the patience to discover which particular update turned it all of? Or do we have to wait until a new releaso of Firefox overcomes it?

---

### Post by MAFoElffen on 2010-08-02
Okay, new news.

I can not "see" the Ubuntu PC from Windows "Network" from my Windows Laptop.  I can connect to it by going to "Start>Run>\\192.168.2.102".  (or to 192.168.2.103, which is the wireless card in that PC)  But I cannot connect from it using "maf-ubuntu-desktop" (which I do see in the router's DHCP client table for both those IP's).

From the Ubuntu PC, I still do not see any "other" window shares except itself.

If I bring the laptop up on an Ubuntu LiveCD and go to Places>Network, I see the Ubuntu PC (maf-ubuntu-desktop) and I see it again in the "Windows Shares" folder...   

Now what? ](*,)

---

### Post by Morbius1 on 2010-08-02
You may have any number of problems but this one for sure is a show stopper:
> But I cannot connect from it using "[COLOR=Blue]maf-ubuntu-desktop[/COLOR]" (which I do see in the router's DHCP client table for both those IP's).
Netbios names have to be 15 characters long or less, that's 18.

By far the easiest way to change it is in smb.conf itself:

```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section:
```
netbios name = something-15-characters-or-less
```Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```

---

### Post by MAFoElffen on 2010-08-02
> **Morbius1 said:**
> You may have any number of problems but this one for sure is a show stopper:
Netbios names have to be 15 characters long or less, that's 18.

By far the easiest way to change it is in smb.conf itself:

```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section:
```
netbios name = something-15-characters-or-less
```Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```
Thanks Morbius1. Didn't find "netbios name =" in my smb.conf
[HTML][global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes
[/HTML]It was easier just to change the hostname via
```
gksudo gedit /etc/hostname
```Should I add an "netbios name" to alias that PC or possiblity use a "DNS proxy=yes" (under "Browsing Identification") to tell Ssmba  to look for a netbios translation at my router?

---

### Post by Morbius1 on 2010-08-02
> Thanks Morbius1. Didn't find "netbios name =" in my smb.confShould have followed my advice. "netbios name" doesn't exist by default in smb.conf. By default samba uses the host name. My way is safer since you have to change two files to change the hostname in linux and I can never remember what they are so I always recommend smb.conf.

[COLOR=Blue]EDIT: Why not publish the output of the following commands so we can see how things are set up:[/COLOR]
```
 net usershare info
``````
 testparm -s
```

---

### Post by MAFoElffen on 2010-08-02
> **Morbius1 said:**
> 
[COLOR=Blue]EDIT: Why not publish the output of the following commands so we can see how things are set up:[/COLOR]```
 net usershare info
``````
 testparm -s
```
Heres the output:[HTML]mafoelffen@maf-ubuntu-01:~$ net usershare info
[shared files]
path=/home/mafoelffen/Shared Files
comment=
usershare_acl=Everyone:F,
guest_ok=y

[documents]
path=/home/mafoelffen/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y
mafoelffen@maf-ubuntu-01:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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
mafoelffen@maf-ubuntu-01:~$ \
[/HTML]

---

### Post by Morbius1 on 2010-08-02
OK, there's nothing wrong with your smb.conf file and there's nothing wrong with your shares. 

If you do the following command from that machine do you get any errors:
```
smbtree
```

---

### Post by MAFoElffen on 2010-08-02
Soory for pause... Resolved host name in file "/etc/hosts" and rebooted.  Here is:
[HTML]mafoelffen@maf-ubuntu-01:~$ smbtree
Enter mafoelffen's password: 
WORKGROUP
    \\MAF-UBUNTU-01          maf-ubuntu-01 server (Samba, Ubuntu)
        \\MAF-UBUNTU-01\shared files       
        \\MAF-UBUNTU-01\documents          
        \\MAF-UBUNTU-01\IPC$               IPC Service (maf-ubuntu-01 server (Samba, Ubuntu))
        \\MAF-UBUNTU-01\print$             Printer Drivers
mafoelffen@maf-ubuntu-01:~$ 
[/HTML]

---

### Post by Morbius1 on 2010-08-02
First, there nothing wrong with samba on MAF-UBUNTU-01 but where is everyone else? smbtree should have displayed all the shares on itself ( which it did without error ) but also for every other box on your network.

Is everyone else connected to the network?

[COLOR=Blue]EDIT: This is late in the day for me so let me leave you for toady with this - this looks like a networking problem that goes beyond the normal netbios name resolution error. smbtree should hav given you errors for those that machines it had problems with. You might want to look at this post for a methodical way of assessing your problem. capscrew very good at that sort of analysis. [http://ubuntuforums.org/showthread.php?t=1533545](http://ubuntuforums.org/showthread.php?t=1533545)
[/COLOR]

---

### Post by MAFoElffen on 2010-08-02
Both of us were following that "other" thread, but capscrew went to pm.  Here's some additional information...
```
mafoelffen@maf-ubuntu-01:~$ ps -ef | grep mbd
root       929     1  0 15:13 ?        00:00:00 smbd -F
root       956   929  0 15:13 ?        00:00:00 smbd -F
root      2197     1  0 15:13 ?        00:00:00 nmbd -D
1000      2736  2470  0 15:41 pts/0    00:00:00 grep --color=auto mbd

``````
mafoelffen@maf-ubuntu-01:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:22:35:f3  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe22:35f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:259338521 (259.3 MB)  TX bytes:8001439 (8.0 MB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:17:31:22:48:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13699 (13.6 KB)  TX bytes:13699 (13.6 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0d:88:8b:b5:e3  
          inet6 addr: fe80::20d:88ff:fe8b:b5e3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2408 (2.4 KB)  TX bytes:4076 (4.0 KB)
``````
mafoelffen@maf-ubuntu-01:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain westell.com
search westell.com
nameserver 192.168.1.1

``````
mafoelffen@maf-ubuntu-01:~$ cat /etc/hosts
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.1.103 maf-ubuntu-01
192.168.2.101 maferr-laptop

```Where as adding the last line with the IP address worked in that "other" thread, it didn't work for me... and they went to PM to.

Now (interestly enough) this info I had saved to a file on the windows laptop... From the laptop I connected via IP address and copied folder-to-folder.  (Wouldn't let me save to...) 
[HTML]c:\Users\Mike Ferreira>ipconfig /all 
 
Windows IP Configuration 
 
   Host Name . . . . . . . . . . . . : maferr-laptop 
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Mixed 
   IP Routing Enabled. . . . . . . . : No 
   WINS Proxy Enabled. . . . . . . . : No 
   DNS Suffix Search List. . . . . . : westell.com 
 
Wireless LAN adapter Wireless Network Connection: 
 
   Connection-specific DNS Suffix  . : westell.com 
   Description . . . . . . . . . . . : Atheros AR5007EG Wireless Network Adapter 
 
   Physical Address. . . . . . . . . : 00-19-7E-7E-71-5C 
   DHCP Enabled. . . . . . . . . . . : Yes 
   Autoconfiguration Enabled . . . . : Yes 
   Link-local IPv6 Address . . . . . : fe80::1569:e717:9b17:733e%9(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.2.101(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0 
   Lease Obtained. . . . . . . . . . : Monday, August 02, 2010 9:48:38 PM 
   Lease Expires . . . . . . . . . . : Tuesday, August 03, 2010 9:51:59 PM 
   Default Gateway . . . . . . . . . : 192.168.2.1 
   DHCP Server . . . . . . . . . . . : 192.168.2.1 
   DHCPv6 IAID . . . . . . . . . . . : 251664766 
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-0D-EE-69-3F-00-1B-24-45-53-16 
 
   DNS Servers . . . . . . . . . . . : 192.168.1.1 
   NetBIOS over Tcpip. . . . . . . . : Enabled 
 
Ethernet adapter Local Area Connection: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Marvell Yukon 88E8038 PCI-E Fast Ethernet 
 Controller 
   Physical Address. . . . . . . . . : 00-1B-24-45-53-16 
   DHCP Enabled. . . . . . . . . . . : Yes 
   Autoconfiguration Enabled . . . . : Yes 
 
Ethernet adapter VirtualBox Host-Only Network: 
 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter 
   Physical Address. . . . . . . . . : 08-00-27-00-9C-39 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes 
   Link-local IPv6 Address . . . . . : fe80::3cdc:da6b:ad05:3f98%36(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.56.1(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0 
   Default Gateway . . . . . . . . . : 
   DHCPv6 IAID . . . . . . . . . . . : 805830695 
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-0D-EE-69-3F-00-1B-24-45-53-16 
 
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1 
                                       fec0:0:0:ffff::2%1 
                                       fec0:0:0:ffff::3%1 
   NetBIOS over Tcpip. . . . . . . . : Enabled 
 
Tunnel adapter Local Area Connection* 6: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : isatap.{5BF7951B-3745-44D4-B3B5-48AE2BD14 
5C4} 
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes 
 
Tunnel adapter Local Area Connection* 10: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface 
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes 
 
Tunnel adapter Local Area Connection* 29: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : isatap.{3A39E39E-9FA7-4209-9BB9-4F463412A 
D5D} 
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes 
 
Tunnel adapter Local Area Connection* 12: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #4 
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes 
 
Tunnel adapter Local Area Connection* 30: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : 6TO4 Adapter 
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes 
 
Tunnel adapter Local Area Connection* 31: 
 
   Media State . . . . . . . . . . . : Media disconnected 
   Connection-specific DNS Suffix  . : westell.com 
   Description . . . . . . . . . . . : isatap.westell.com 
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0 
   DHCP Enabled. . . . . . . . . . . : No 
   Autoconfiguration Enabled . . . . : Yes[/HTML]

---

### Post by Morbius1 on 2010-08-03
Let me be honest here. Sharing files requires two parts - Samba and Networking. I'm comfortable resolving a lot of things on the samba end of things but I'm not very knowledgeable about the networking part of things. Knowing that, something doesn't look right in all of this:

You have a DSL modem that is attached to a separate router.

On both the Windows and Linux boxes you have the DNS servers = 192.168.1.1
That's the default ip address of a Linksys router.

But your DHCP servers as well as your gateways are both set to 192.168.2.1
That's the default ip address of an SMC or Belkin router.

I think(?) that those two ip address constitute two different subnets. By default samba uses broadcast to resolve host names and broadcast doesn't work across subnets. I have a similar setup except that I have a dsl modem (only) attached to a router. In my setup the gateway, dns server, and dhcp all point to the router.


Is the DSL modem a modem / router combination? I think that the modem has to set to "bridge mode" - something I've never done. See if these links seem relevant in your situation:

[http://workbench.cadenhead.org/news/3375/setting-up-westell-modems-linksys](http://workbench.cadenhead.org/news/3375/setting-up-westell-modems-linksys)
[http://discussions.virtualdr.com/showthread.php?t=210346](http://discussions.virtualdr.com/showthread.php?t=210346)

---

### Post by MAFoElffen on 2010-08-04
Okay, I must have confused you.  I see everything "here" everyday, and I assume by seeing the info...  I need to "tie" the info together so you can understand that's it's a lot more basic that you think.  You hava all the info:
> **Morbius1 said:**
> Let me be honest here. Sharing files requires two parts - Samba and Networking. I'm comfortable resolving a lot of things on the samba end of things but I'm not very knowledgeable about the networking part of things. Knowing that, something doesn't look right in all of this:

You have a DSL modem that is attached to a separate router.

On both the Windows and Linux boxes you have the DNS servers = 192.168.1.1
That's the default ip address of a Linksys router.

But your DHCP servers as well as your gateways are both set to 192.168.2.1
That's the default ip address of an SMC or Belkin router.

I think(?) that those two ip address constitute two different subnets. By default samba uses broadcast to resolve host names and broadcast doesn't work across subnets. I have a similar setup except that I have a dsl modem (only) attached to a router. In my setup the gateway, dns server, and dhcp all point to the router.


Is the DSL modem a modem / router combination? I think that the modem has to set to "bridge mode" - something I've never done. See if these links seem relevant in your situation:

[http://workbench.cadenhead.org/news/3375/setting-up-westell-modems-linksys](http://workbench.cadenhead.org/news/3375/setting-up-westell-modems-linksys)
[http://discussions.virtualdr.com/showthread.php?t=210346](http://discussions.virtualdr.com/showthread.php?t=210346)
Here goes:  
Primary default (private) addresses for routers, modems, bridges, etc is 192.168.1.1

1. I have a DSL Connection that has a default address of 196.168.1.1, that connects me to the outside world through my ISP westell.com, which is my primary DNS (invisible to me) to the outside world.  Phone cord from wall jack to modem...  I didn't set it up as the DNS server manually in Ubuntu as the DHS server, That's just how it "sees" it.

2. I have a Linksys (Cysco) Router, WRT54G.  It has a wireless transceiver and 4 ethernet ports.  When you connect an ethernet cable to it port 1 to the DSL ethernet port, it bridges to it. I had to get help from Cysco to walk me through setting this router up for this DSL Modem (and my ISP)...  
a.) Unfortunately, it's default IP address is also "102.168.1.1".  You have to manually reset the IP address to resolve the conflict.  Since the TCP/IP numbering scheme for a subnet gets assigned after the second "." such as "192.168.1,1xx" and it is a subnet behind would be a "bridge", I assign this router as 192.168.2.1... Thats why everything in my LAN is coming up "192.168.2.1.1xx".  Internally to this router, it keeps it's own DHCP client table.  Browsing this table, I can see that every device on my network is passing it's hostname, it's IP address, it's MAC address, etc.  
b.)  The router is set as "Gateway", "Wireless & LAN" (vs WAN).
c.)  The hostname and domain name in the router setup are blank. The pc's are getting this from the DSL Modem.
d.)  My wireless network is named "FerreiraFarms" in my router.
e.) The router is set at Autoconfiguration/DCHP, which is it's default.
e.)  Cysco confirms that whether "wireless" or "wired," this router sees both them as one LAN/network... and it's just a mater of symantics.  Basically, it's transparent (on the surface) except the medium it's going over.  
 
3.  All the PC's are "connected" to my router, either via wireles, or my pc which is connected ethernet (plugged directly into port 2) into the router.  All these PC's see the router as a "gateway" becuase that's what mode it's set as (Router or Gateway).  

My PC "also" has a wireless card (and Bluetooth) but I rarely use these except to do things with some of my PDA Smartphones (both over wireless and bluetooth).  I cook Winmo ROMs.  Because I care about the performance on this development and testing platform, I mainly keep it just "wired."
---------------------------------------------------------------------------------
I'm not a doctor... I'm not an "expert."  I come with some experience, am learning and gaining more experience.  I spent half the night reading info that "capscrew" hinted into as "suggest reading" in the thread we were following that lead to another, that lead to an article and a book.  Great sources for learning that will keep me busy for about a month, but... that it not getting me anywhere fast in the meanwhile. 

What's frustrating on "this problem" is that this PC is "multi-boot"- meaning from this "same PC," when I boot up a Windows OS (both Vista and Win7)- I can see everything on the network.  The physical network is there and working from this node to every other node.  

When I boot up in linux (Ubuntu) or unix (OpenSolaris), I see the router, my printer, the DSL modem, my ISP and beyond, but nothing else locally(my LAN) .  Ubuntu has the samba-client and wins installed.  OpenSolaris has samba-client, wins and cifs installed.  I figure if I can get it working in Ubuntu, I can work it out for Opensolaris later... They "are" having the same issues.  I even don't "want" to boot up and try this in Solaris 10...  If I bring these up and connect to the wireless networt/no change.  With these- I seem to have a oneway pipe from the Windows PC's to it, not the other way around... and the windows PC's are seeing the IP, but not their hostname.  I can mount the Ubuntu shares at that PC from my Vista laptop via IP address, open the shares folders and copy files to it.  The permissions are set and I can confirm that I am reading, writing and deleting on that network share.  

I manually added my router address as a DNS server into Ubuntu (thinking it would use the router table. It  didn't make a difference.  I manually added my windows laptop into Ubuntu as a host.  Also no change.

It "is" not showing up as "Windows shares" at this time.  While that network drive is mounted, a windows application isnt "directly" (from within that application) seeing that mount to open or save a file.  It just shows up as a network folder in the File Explorer.  I can open it as a folder.  Almost reminds me of early Novell shares in DOS!!! (lol)

IMHO- It seems either to be in how these non-windows hosts are talking with the windows hosts- or that the router is not passing something on that the Ubuntu PC needs to complete the translation.  What that "is." at the moment, I am at a loss.  

Although- I don't know if this means anything... My Router's setup info does say this about what happens when you select the Gateway Operating Mode: "```
Dynamic Routing (RIP)
      
          Note: This feature is not available in Gateway mode.
      
     Dynamic  Routing enables the Router to automatically adjust to physical changes  in the network layout and exchange routing tables with other  routers. The Router determines the network packets route based on  the fewest number of hops between the source and destination. 
      
          To enable the Dynamic Routing feature for the WAN side, select WAN. To enable this feature for the LAN and wireless side, select LAN & Wireless. To enable the feature for both the WAN and LAN, select Both. To disable the Dynamic Routing feature for all data transmissions, keep the default setting, Disable.      

```But for the Gateway Operating Mode it says:  ```
Choose the correct working mode. Keep the default setting,               Gateway, if the Router is hosting your network connection to the Internet (Gateway mode is recommended for most users). Select               Router if the Router exists on a network with other routers.
```
I'll follow your links and read them tonight...

---

### Post by MAFoElffen on 2010-08-04
The first link I read 2 nights ago... 
 
But the second- **[SIZE=2]You are right on the money!!![/SIZE]** Same equipment/but different ISP. Didn't know that particular modem was also a router doing DHCP. My router in Gateway Operating Mode doesn't pass on the router table. ...And it's getting a double "NAT" as described where you referred me.
 
Set the router to "Router" operating mode and the windows PC's are now seeing the hostname of the Ubuntu PC. All the windows PC's are seeing ISP (internet), but the Ubuntu PC lost internet access. 
 
I will have to reconfig the modem to "Bridged ethernet" and see what happens. I have to get with my ISP tonight to do that. (I have a few things I need to do today.) My ISP sets the ID up in the modem and passes it via DHCP to it's host. The modem is secured and I forgot the modem's ID/PW to access it. It has been a couple years since I set that up... and I can't find my logs on it.
 
So it seems it might have been the second scheme- that the router(s) weren't passing the required info between to the nodes. That's the current "guess." We will see.

---

### Post by MAFoElffen on 2010-08-05
Okay... Set the DSL modem as an Ethernet bridge.  Is is now just a dumb modem = no router functions and no DHCP server funstions, just pass through. 

Reset my router up in PPPoE protocol to connect with my ISP.  My router is "now" the only router/gateway mode/DHCP server.  DNS is still at ISP.  Internet working great on all...

But been with Tech support from Centurylink then Cisco most of the afternoon:

Windows   <--> Windows        = see each other/join into WORKGROUP.
Linux SMB <--> Windows SMB = still failure. Don't see or talk to each other.
Linux IP     --->  Windows IP    = no connect, not even ping to.
Windows IP ---> Linux IP         = Pings & Connects as "network" share.
Me             ---> Exhausted...

---

### Post by MAFoElffen on 2010-08-05
This morning-same.  This "PM," will spend some time at the Cisco Forums and see if they have any ideas...  Still "strange."

---

### Post by MAFoElffen on 2010-08-06
But for that to work, I still am researching the more basic "problem"  that is preventing that transport level and acknowledgement to be  facilitated.  

I still have a "one way pipe" kind of filter effect going on somewhere  between the Linux and Windows clients... or between the linux ethernet  client and the Wireless Windows clients!  I can ping my Linux PC from my  Windows Laptop using it's DHCP assigned IP adress, but I cannot do the  same going the other way!!!
](*,)

---

### Post by capscrew on 2010-08-07
> **MAFoElffen said:**
> But for that to work, I still am researching the more basic "problem"  that is preventing that transport level and acknowledgement to be  facilitated.  

I still have a "one way pipe" kind of filter effect going on somewhere  between the Linux and Windows clients... or between the linux ethernet  client and the Wireless Windows clients!  I can ping my Linux PC from my  Windows Laptop using it's DHCP assigned IP adress, but I cannot do the  same going the other way!!!
](*,)

When you have all the hosts (computers) on the same subnet, you should be able to ping any of those hosts from any host in the network. This is basic TCP/IP networking.  Are all the hosts directly connected to the Linksys?

Tell me the IP address and subnet mask for each host in the network.  Also provide me with the default gateway IP address along with your current DNS settings.  I want you to tell me.  Don't post the output of the various commands.

---

### Post by MAFoElffen on 2010-08-07
> **capscrew said:**
> When you have all the hosts (computers) on the same subnet, you should be able to ping any of those hosts from any host in the network. This is basic TCP/IP networking. Are all the hosts directly connected to the Linksys?
 
Tell me the IP address and subnet mask for each host in the network. Also provide me with the default gateway IP address along with your current DNS settings. I want you to tell me. Don't post the output of the various commands.
Thanks "capscrew."
 
The router is the central character: static IP address "192.168.2.1".
- It is setup Gateway mode to use PPPoE protocol to login to my ISP thru my DSL modem.
- My ISP is the DNL server.
- It is (now) the only DHCP server, assigning "192.168.2.100" through "192.168.2.149"
- Is is setup with a wireless network the option to "NOT" isolate the wireless clients from other users on the network.
- It has both the wireless network and switched ethernet ports.
 
The DSL modem is now set to act as a dumb modem and is bridged ethernet... It originally was also router and DHCP server//Now disabled. It's static IP address is "192.168.1.1". It is connected to the linksys ethernet port 1.
 
My network printer is wireless, but is set with a static IP and MAC address...
 
All the clients are connected to the linksys router. All are connected to the wireless network, except my desktop PC (which is switched ethernet port 2.) All clients are setup as DHCP clients. Their Ip's usually are between 192.168.2.100 through 192.168.2.106
---------------------------------------------------------------------------------------------
This is where I appologize. I assumed that since my desktop was connected to the network last that this is where the problem was. I assumed since my laptop connected to everything, that there was no problem there. I assumed that since my my desktop could see the laptop shares and MAP it using it's Windows OS'es that it old also connect to it (I could connect to it from my laptop...) All those assumptions were wrong. I did not have access to the other 2 windows clients until last night. They cannot connect with my laptop either!!!
 
Even though I could connect to everything with my laptop, I could not ping my laptop from my desktop nor my router. I booted up the laptop on an Ubuntu 10.10 Desktop Edition LiveCD. I let it autocongiure the wireless adapter and connect to the same Wireless network... I could then ping to it from my desktop PC and from the router!
 
That sort of rules out the router, the network and the other devices... Pointing to the real culpret- the Laptop. At present, it is within Windows Vista; it's device drivers, netwrok drivers, settings, services... somewhere, somehow.
 
It is useless to see how my Ubuntu "network shares" work with my laptop, until I get underlying problem worked out on the laptop. If it was up to me, I would just replace Vista on my laptop with Ubuntu... My fiance has adopted my laptop to unwind... Has a bunch of windows games loaded up on it. Have to keep the lady happy. She doesn't do well with "change."
 
This is not resolved- but the current issues are not presently an Ubuntu problem.

---

### Post by Morbius1 on 2010-08-08
I have been absolutely no help to you on this problem, and to reduce further confusion I should just stay out of this and let capscrew guide you out of this. He knows more about this than I ever will, but this just doesn't sound right:
> [COLOR=Blue]The DSL modem[/COLOR] is now set to act as a dumb modem and is bridged  ethernet... It originally was also router and DHCP server//Now disabled.  It's static IP address is "192.168.1.1". It [COLOR=Blue]is connected to the linksys  ethernet port 1.[/COLOR]
 
All the clients are connected to the linksys router. All are connected  to the wireless network, except my desktop PC (which is switched  ethernet port 2.)[COLOR=DarkGreen] All clients are setup as DHCP clients. Their Ip's  usually are between 192.168.2.100 through 192.168.2.106[/COLOR]Maybe it's something unique about the Westell modem/router. Maybe it's something the help desk told you to do, but in a typical setup the modem should be connected to the WAN or Internet port of the Linksys router not an Ethernet port. In fact if everything is physically connected correctly you should no longer be able to connect to the configuration pages of the modem any longer - at least not through the router.

Again maybe I'm looking at the wrong manual (Model No: WRT54G) but that modem should be handing out ip addresses in the 192.168.1.100 - 192.168.1.253 range not in the 192.168.2.xxx range

---

### Post by capscrew on 2010-08-08
> **Morbius1 said:**
> I have been absolutely no help to you on this problem, and to reduce further confusion I should just stay out of this and let capscrew guide you out of this. He knows more about this than I ever will, but this just doesn't sound right:
Maybe it's something unique about the Westell modem/router. Maybe it's something the help desk told you to do, but in a typical setup the modem should be connected to the WAN or Internet port of the Linksys router not an Ethernet port. In fact if everything is physically connected correctly you should no longer be able to connect to the configuration pages of the modem any longer - at least not through the router.

Again maybe I'm looking at the wrong manual (Model No: WRT54G) but that modem should be handing out ip addresses in the 192.168.1.100 - 192.168.1.253 range not in the 192.168.2.xxx range

Most residential gateways have two modes of operation (e.g. routing or bridged).  I most installations folks use the device  in the routing mode, as it is the only device between the LAN and the wider internet.  I have a Westell in my home network that serves as my router/DHCP/DNS device. In MAFoElffen's case he is using the Linksys between the LAN and the Westell.  So he has two devices that ***can *** function as routers.  

This this creates a situation where you must have two subnets to manage (Westell and Linksys).  This can be done, but it is not the only way.  If you put the the Westell in bridged mode it now has no *"inside interface" *, rather, it holds only the WAN side interface and a 1 port switched interface (no private IP address).  This can now be plugged into the Linksys and the LAN has only one subnet.

The Linksys can be configured for any private subnet.  192.168.2.0/24 is just as usable as 192.168.1.0/24.  In fact you can use 10.0.0.0/24 if you wish.  Linksys just uses 192.168.1./24 as a default subnet.

---

### Post by Morbius1 on 2010-08-08
capscrew, I'm glad you're taking care of this guy because I'm clueless.
> So he has two devices that ***can *** function as routers.  

This this creates a situation where you must have two subnets to manage  (Westell and Linksys).  This can be done, but it is not the only way.   If you put the the Westell in bridged mode it now has no *"inside interface" *,  rather, it holds only the WAN side interface and a 1 port switched  interface (no private IP address).  This can now be plugged into the  Linksys and the LAN has only one subnet.
Isn't that what he has done:
> [COLOR=Black]The DSL modem[/COLOR] is now set to act as a dumb modem and is bridged  ethernet... It originally was also router and DHCP server//Now disabled.But he has it connected to the wrong port of the Linksys router, to an "ethernet port" and not the "WAN port":
> It [COLOR=Black]is connected to the linksys Ethernet port 1[/COLOR]

---

### Post by capscrew on 2010-08-08
> **Morbius1 said:**
> capscrew, I'm glad you're taking care of this guy because I'm clueless.
Isn't that what he has done[?]

Yes, he just described it using the wrong terms.  I was addressing you and your questions about how it works.
> 
But he has it connected to the wrong port of the Linksys router, to an "ethernet port" and not the "WAN port":

He may well have the MODEM plugged in the wrong side.  I have trouble following what the problem is.  :-)

---

### Post by MAFoElffen on 2010-08-08
ROTFLMAO!!!  Okay you two! You two are funny.  Stop for a moment... 

As an aside:
RFC 1918 defines address allocation for private network (subnet ranges),  10.0.0.0 thru 10.255.255.255; 172.16.0.0 thru 172.31.255.255; 192.168.0.0 thru 192.168.255.255 (and subsequent submask addresses)... for "anyone" to use in a subnet.  In my case, 192.168.1.1 was my modem and so was my router as  their defaults out-of-the-box.  They conflicted with each other.

In my case I have one subnet... (Yes, the modem is outside it now-bridged to the router, which is the gateway for my subnet, but thats semantics.)  Where as when I first started, trying to do a "generic" install as per the instructions of my ISP, I ended up with two.  I had big problems!  I had two gateways, two conflicting DHCP servers on diiferent subnets.  Because both were setup as gateways, they were not passing the router tables to the other.  They both had the same IP address <> so devices were really "confused."  I had a mess.  I first had to give each a unique IP address.

Out of the box, the Westel 6100 is a DSL Modem, but ISP's don't tell you that it's also (as a default): a router, gateway and DHCP server.  Fine if you only have one PC, as it only has one ethernet port.  (Some models also have a USB port.)  The westel is not smart enough to do DNS server functions, thats out at the ISP.  In my case there are two at my ISP that my devices see dynamically.  Yes, we get DNS services "through" it either way it's set up.

"My" Linksys WRT54G modem is Wireless and has one port that is labeled "Internet"...  On some other revisions and models of the same router this port is labeled "WAN".  I connect my "link to the outside" to this port.  Whatever want to call it, it is just a WAN port.  Mine has 4 additional switched ethernet ports.  And yes, they are numbered 1-4.  Some revisions have 5.  My Desktop PC is connected to the second of these additional ports.  Default out-of-the-box it's set in Gateway mode, does routing and DHCP server...  There is a mode in the Wireless section that will partition/isolate the wireless clients from each other (not see each other), but this is not a default and that was not what was going on with this laptop...

The linksys does routing, gateway, DHCP, diagnostics and administration so much better than this little modem does.  Performance wise and sanity wise, it wasn't a hard decision.  Yes, I could put it in Router mode and turn off the DHCP server services and let the westell do it... then it would have passed on it's router table and not ended up with a conflicting devices.  At first, that's how I did it, then later reconfigured to how I have it not.  Performance and load seems much better this way (much better!).

That's why I had assigned the westel as static 192.168.1.1 and the Linksys as static 192.168.2.1.  They were on the same net but had unique static addresses.  I can get to the config, status and diagnostics of either from a browser from any PC on my network.  Since everthing now "is" setup in the linksys and the westel, I can easily switch to either network configuration...  But with the Westell acting as the gateway, It's a device config switch-then finish with an internet config for the AccountID and Password.  Much easier keeping that all at my router.

On the old net config, I had the Westell (192.168.1.1) assigning addresses starting at 192.168.1.100 thru 192.168.1.149.  On the new net config, I have the Linksys (192.168.2.1) assigning addresses 192.168.2.100 thru 192.168.2.149.  Just easier for my to keep track of things.  I do a lot of trouble-shooting, development and software testing... where I'm running things in Virtual PC and VirtualBox- the virtual machines end up with an assigned address through the loopback interfaces starting at 10.0.0.0+

The clients don't know how the network "changed" and don't care as long as all the required services are there, working together and functioning.  They still get their resources dynamically and it still "looks" the same to them.

=== 
Enough about that explanation.  The network works and that was not the problem. 
===
The culprit was the laptop!!!  I used to have a 3rd party Virus protection sofftware loaded on this.  First McAfee... then later on Norton Internet.  I uninstalled the first (McAfee). I later turned off the second and just used the Windows Firewall. ... or at least I thought Norton was turned off!@#$%!!!  Even though it wasn't showing up on the surface, it was still running in the background.

I started up WinDebug to check it's processes and threads ...and presto- there was a Norton Internet firewall intercepting and blocking data from one of the UDP ports it needed for filesharing... I disabled the aplication from autostarting... I could then ping to this device.  Evrything started working with the other Windows PC's, Ubuntu with samba-client, OpeSolaris with Samba and CIFS serivices ...and Solaris 10 with Samba services.  I turned the Windows Firewall back on and evrything is still working.

To Morbuis1 and capscrew- Thank you guys!! Morbius1, I learned allot about Samba configuration from you and your referals.  "capscrew," I'm about a quarter way through that book you recommended. (lol)  You taught me allot about diagnostics- thinking about how things are supposed to work, breaking down what services it needs to do that and then tracing down those routes and layers...  You both might not think so, but I got through this with both of your help and guidance.  I now consider you both as friends and mentors.  Many thanks and blessings.
:popcorn:

---

### Post by MAFoElffen on 2010-08-08
:-D Notes:
The turning point in all this was me not being able to ping this laptop...  That kept "bothering" me and "others."  (Frustrating as it was- that it had some services.)

I booted it up on an Ubuntu 10.10 Desktop Edition LiveCD and let it autoconfigure the wireless device and connect to the same wireless network.  I could then ping to it from my desktop and from the router.

From there, I confirmed that the network was working properly and that the hardware on the laptop was working... That also confirmed that was something wrong within Windows Vista's drivers, services, privileges and rights.  It was not doing the same things somehow.

If my fiance hadn't adopted my laptop as her own to "unwind," I would have just replaced the OS with Ubuntu.  I have to keep this woman happy.

---

