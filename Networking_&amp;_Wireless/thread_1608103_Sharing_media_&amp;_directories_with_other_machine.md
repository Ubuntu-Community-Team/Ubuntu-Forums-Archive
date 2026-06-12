---
title: "Sharing media &amp; directories with other machines on a LAN"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by Jonners59 on 2010-10-28
I am running 10.4 on a number of machines but can not create a network and share media and directories between them.  I can not find any machines on my network.  I know smb is installed because I used it when running windows...  I have not used Ubuntu or any other Linux OS to run a network before, so all help welcome.

Please advise what info you require to help me...

---

### Post by Morbius1 on 2010-10-28
I don't know if I can help you but if you can provide the output of the following commands the good folks here can asses how you are set up:
Choose just one machine:

```
 net usershare info -list
```
```
testparm -s
``````
smbtree
```

---

### Post by Jonners59 on 2010-10-28
> **Morbius1 said:**
> I don't know if I can help you but if you can provide the output of the following commands the good folks here can asses how you are set up:
Choose just one machine:

```
 net usershare info -list
```
```
testparm -s
``````
smbtree
```

Thank you for your reply.  I did as requested from one of the laptops, not any of the main machines.  I noted it found "Server", this is a PC that is always on and where we keep our shared media and the most important to access by ALL machines.  the reports:

root@jonathan-laptop:/home/jonathan# net usershare info -list
info_fn: file /var/lib/samba/usershares/music is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/dcim is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/dropbox is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[public]
path=/home/jonathan/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

[sanderstead ltc]
path=/home/jonathan/Dropbox/Sanderstead LTC
comment=
usershare_acl=Everyone:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/templates is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/share is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[documents]
path=/home/jonathan/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/videos is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[desktop]
path=/home/jonathan/Desktop
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/pictures is not a well formed usershare file.
info_fn: Error was Path is not a directory.
root@jonathan-laptop:/home/jonathan# testparm -s
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
	force user = jonathan

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
root@jonathan-laptop:/home/jonathan# smbtree
Enter root's password: 
JONATHANECHIARA
	\\SERVER         		server server (Samba, Ubuntu)
cli_start_connection: failed to connect to SERVER<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\JONATHAN-LAPTOP		jonathan-laptop server (Samba, Ubuntu)
		\\JONATHAN-LAPTOP\public         	
		\\JONATHAN-LAPTOP\sanderstead ltc	
		\\JONATHAN-LAPTOP\documents      	
		\\JONATHAN-LAPTOP\desktop        	
		\\JONATHAN-LAPTOP\IPC$           	IPC Service (jonathan-laptop server (Samba, Ubuntu))
		\\JONATHAN-LAPTOP\print$         	Printer Drivers

---

### Post by Morbius1 on 2010-10-28
From the laptop, can you access the server by doing this:

In a terminal:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the server*[/COLOR]

---

### Post by Jonners59 on 2010-10-28
> **Morbius1 said:**
> From the laptop, can you access the server by doing this:

In a terminal:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the server*[/COLOR]

No.  It says unable to mount smb://192..... and then opens the ROOT directory

I then changed to mount smb://192.168.1.50 which is the SERVER  That did exactly the same

---

### Post by Morbius1 on 2010-10-28
My guess is the firewall is in the way on the server. If you are using UFW then disable it:
```
sudo ufw disable
```
IF you haven't touched the firewall or didn't install some other firewall app or havent played around with app armor then at the moment I don't know.

---

### Post by Jonners59 on 2010-10-28
> **Morbius1 said:**
> My guess is the firewall is in the way on the server. If you are using UFW then disable it:
```
sudo ufw disable
```
IF you haven't touched the firewall or didn't install some other firewall app or havent played around with app armor then at the moment I don't know.

I tried the code, and it did not work with either 192.168.0.100 or 192.168.1.50...

I have not touched the firewall at all.  Not sure where to find it to be honest and have not done any of the other things you mentioned.

Should I run ```
sudo ufw disable
``` on all machines?

---

### Post by Morbius1 on 2010-10-28
You know somethings been bothering me about an earlier response:
> No.  It says unable to mount smb://192..... and then opens the ROOT directoryIt could have said " Cannot Find ...." or "Could not display ....". But it said "could not mount". We're not asking it to mount anything all we are asking for it to do is diplay the servers shares. 

The closest I could get to your error was to to this:
gksu nautilus smb://192.168.0.100
It gave me a "Could not display" error and did in fact open at /root.


You running as root by any chance?

---

### Post by Morbius1 on 2010-10-28
I'm an idiot:
> **[COLOR=Blue]root[/COLOR]**@jonathan-laptop:/home/jonathan# net usershare info -list
info_fn: file /var/lib/samba/usershares/music is not a well formed usershare file.You are running as root. 

Even in my SuSE days I never ran as root but based on 6 seconds of attempting to access my own network via Nautilus as root ( i.e., gksu nautilus ) I don't think it can be done. Or if it can I certainly don't want to know how. :wink: Do you have a normal user account on that system?

---

### Post by Jonners59 on 2010-10-29
> **Morbius1 said:**
> You know somethings been bothering me about an earlier response:
It could have said " Cannot Find ...." or "Could not display ....". But it said "could not mount". We're not asking it to mount anything all we are asking for it to do is diplay the servers shares. 

The closest I could get to your error was to to this:
gksu nautilus smb://192.168.0.100
It gave me a "Could not display" error and did in fact open at /root.


You running as root by any chance?

Yes....

Tried in normal Terminal and got.
Message saying "nautilus can not handle "smb" locations" and in the terminal it said
"jonathan@jonathan-laptop:~$ gksu nautilus smb://192.168.0.100
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.6"

It also opened the root directory

I then tried the server's IP address 192.168.1.50 and got....
the same message and root open, but terminal said
"jonathan@jonathan-laptop:~$ gksu nautilus smb://192.168.1.50
jonathan@jonathan-laptop:~$ "

"" are my additions as quotes.
Does this help?

---

### Post by Morbius1 on 2010-10-29
```
nautilus smb://192.168.1.50
```

What does this do?

---

### Post by Jonners59 on 2010-10-29
> **Morbius1 said:**
> ```
nautilus smb://192.168.1.50
```

What does this do?

Sorry about the delay...

I get a message

"Could not display "smb://192.168.1.50/".
Error: Failed to retrieve share list from server
Please select another viewer and try again."

PS:  After inputting "sudo ufw disable" on the server, do I need to re-boot it?

---

### Post by Ninja-Penguin on 2010-10-29
Jonners the first step to any network issue is to make sure everything is in the same domain/workgroup. Also make sure you can talk between each device on the network. 

You will want to ping from the server and all other devices to make sure they can all be reached. 

In Ubuntu and most distros running Gnome you can use the network browser and see if you see the other devices on the network as well. 

If you do not see the other devices there is something going on with your network set up. 

If you see the other devices click on them and you should be prompted with a login window. 

Once connection is verified to all devices then moving on to the next step is best.

---

### Post by Morbius1 on 2010-10-29
>  "Could not display "smb://192.168.1.50/".Just to make sure you are doing what I think you are doing:

You logged off as root.
Then you logged on as jonathan.
Then you ran:
```
 nautilus smb://192.168.1.50
```And then you got that error message?

Is 192.168.1.50 the correct ip address for the server?

If you've done all that and the ip address is correct then I want you to install the following package:
```
gvfs-backends
```

---

### Post by Jonners59 on 2010-10-29
> **Morbius1 said:**
> Just to make sure you are doing what I think you are doing:

You logged off as root.
Then you logged on as jonathan.
Then you ran:
```
 nautilus smb://192.168.1.50
```And then you got that error message?

Is 192.168.1.50 the correct ip address for the server?

If you've done all that and the ip address is correct then I want you to install the following package:
```
gvfs-backends
```

Yes
Yes
and I tried the gvfs-backends and got
"jonathan@jonathan-laptop:~$ gvfs-backends
gvfs-backends: command not found"

Am I putting in the command correctly?

PS that was on my laptop.  I don't have access to the central PC at this moment

---

### Post by Morbius1 on 2010-10-29
You need to install it:
```
sudo apt-get install gvfs-backends
```>  PS that was on my laptop.  I don't have access to the central PC at this moment     Then why are you trying to access it with:
```
nautilus smb://192.168.1.50
```I'm lost as to what you're trying to do. If you don't have any other machines on your network what are you trying to connect to? Did you change 192.168.1.50 to the ip address of the laptop?

---

### Post by Jonners59 on 2010-10-29
> **Morbius1 said:**
> You need to install it:
```
sudo apt-get install gvfs-backends
```Then why are you trying to access it with:
```
nautilus smb://192.168.1.50
```I'm lost as to what you're trying to do. If you don't have any other machines on your network what are you trying to connect to? Did you change 192.168.1.50 to the ip address of the laptop?

I looked in Synaptic manager and it (gvfs-backends) was already there.  I have tried to install using terminal and the cmd you just gave and it conformed it is the most up to date version.

Pt 2.  I can not get physical access to the machine, 192.168.1.50.  I am trying to access the directories from my laptop.  The laptop is IP address 192.168.1.75 and I am trying to access the PC we store most of our docs and pics on which is 192.168.1.50

FYI and to cover a message from someone else in the thread.

I started by using Windows on all 7 PCs and Laptops on our LAN, and had no problems, even managed to get a VPN working.  I changed to Ubuntu on all the PCs and Laptops, with the central PC still on Windows and it still worked.  I changed the OS to Ubuntu on this central PC and have found that non of the PCs and Laptops can access it now.  Hence the thread.

---

### Post by Morbius1 on 2010-10-29
I was involved once in a thread that had someone else send private messages for fear of peer review I guess. It didn't turn out well because we ended up taking the OP on entirely different paths and he ended up with a mess.

What looked at first as a  name resolution problem ( converting a machine name to ip address ) has now turned into something else. Part of the problem seemed to be that you were running as root but it appears you are now not doing that. 

Let me leave you with an observation. There are ways to deal with name resolution  - WINS and hosts file for example - but they depend on one machine accessing the other by ip address and you cannot do that. It may be that your network configuration involves multiple routers or switches that is causing this problem. But in a normal network ( i.e., one router ) the usual suspect is a firewall getting in the way.

---

### Post by Jonners59 on 2010-10-30
> **Morbius1 said:**
> I was involved once in a thread that had someone else send private messages for fear of peer review I guess. It didn't turn out well because we ended up taking the OP on entirely different paths and he ended up with a mess.

What looked at first as a  name resolution problem ( converting a machine name to ip address ) has now turned into something else. Part of the problem seemed to be that you were running as root but it appears you are now not doing that. 

Let me leave you with an observation. There are ways to deal with name resolution  - WINS and hosts file for example - but they depend on one machine accessing the other by ip address and you cannot do that. It may be that your network configuration involves multiple routers or switches that is causing this problem. But in a normal network ( i.e., one router ) the usual suspect is a firewall getting in the way.

Hi Morbius
I really appreciate the support.  I am on the boarder of my competence here.

I had no issues in Windows, but now the storage PC, we call the server is on Ubuntu we have a problem.

I do use two routers, but one is setup as just a repeater and it has a config tick in the box to allow this.  There are two LAN switches (8 x 1Gb) but they are dumb with no configs...  So in one way the idea of the Firewall works, but then it was not an issue in Windows, so why now.

The machine does have "Share" options on the folders under "Preferences", but it refuses to setup.  I tick the boxes but nothing happens.  This is on the "server" PC (192.168.1.50) of course.

I am open to step by step help

---

### Post by Jonners59 on 2010-10-31
Managed to get on to the server and ran the package install:
[HTML]server@server:~$ sudo apt-get install gvfs-backends
[sudo] password for server: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gvfs-backends is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up oss4-dkms (4.2-build2002-2) ...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cp /lib/modules/2.6.32-25-generic-pae/source/include/linux/limits.h /var/lib/dkms/oss4/4.2-build2002/build/core && make -C /lib/modules/2.6.32-25-generic-pae/build SUBDIRS=/var/lib/dkms/oss4/4.2-build2002/build/core modules && make -C /var/lib/dkms/oss4/4.2-build2002/build/drivers osscore_symbols.inc && make -C /lib/modules/2.6.32-25-generic-pae/build SUBDIRS=/var/lib/dkms/oss4/4.2-build2002/build/drivers modules....(bad exit status: 1)

Error! Bad return status for module build on kernel: 2.6.32-25-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/oss4/4.2-build2002/build/ for more information.
0
0
dpkg: error processing oss4-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 oss4-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
server@server:~$ [/HTML]

Seems was already installed, but interesting error message - what does this mean?

I have installed a number of network management tools, non help.

I noticed that Personal File Sharing in System, Preferences does not allow changes and says can not work as it is missing packages - no assistance on what and how to get these packages.

---

### Post by Jonners59 on 2010-11-03
Any help please.

---

### Post by Morbius1 on 2010-11-04
Since you are unable to access the other machines by ip address this is not a Samba issue this is a networking issue.
> I do use two routers, but one is setup as just a repeater and it has a  config tick in the box to allow this.  There are two LAN switches (8 x  1Gb) but they are dumb with no configs...  Since you have so much networking hardware in the way all I can suggest is to post the output of the the following commands - once for the server and again for the client - and wait for the networking folks to comment.
```
ifconfig
route -n
cat /etc/resolv.conf
cat /var/lib/dhcp3/dhclient.leases

```The commands above is the functional equivalent of running "ipconfig" on Windows.

---

### Post by Jonners59 on 2010-11-05
> **Morbius1 said:**
> Since you are unable to access the other machines by ip address this is not a Samba issue this is a networking issue.
Since you have so much networking hardware in the way all I can suggest is to post the output of the the following commands - once for the server and again for the client - and wait for the networking folks to comment.
```
ifconfig
route -n
cat /etc/resolv.conf
cat /var/lib/dhcp3/dhclient.leases

```The commands above is the functional equivalent of running "ipconfig" on Windows.

I have run PING tests and I can PING all machines from all machines....

OK, here it is:

The PC that does not work at all (Server) = 
[HTML]server@server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:58:4c:2b  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe58:4c2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3186481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1977194 errors:0 dropped:92 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:958369868 (958.3 MB)  TX bytes:306039833 (306.0 MB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4994442 (4.9 MB)  TX bytes:4994442 (4.9 MB)

server@server:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
server@server:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 4.2.2.2
nameserver 208.67.220.220
server@server:~$ cat /var/lib/dhcp3/dhclient.leases
server@server:~$ 
[/HTML]

And here are two more from other PCs on the LAN that do work.  The former works best of all:

PC 1
[HTML]jonathan@jonathan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:f9:5a:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1999173 (1.9 MB)  TX bytes:1999173 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:19:f7:83  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe19:f783/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38100075 (38.1 MB)  TX bytes:6225868 (6.2 MB)

jonathan@jonathan-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
jonathan@jonathan-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 4.2.2.2
nameserver 208.67.220.220
jonathan@jonathan-laptop:~$ cat /var/lib/dhcp3/dhclient.leases[/HTML]


PC 2
[HTML]baronipc@baronipc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:26:9c:03  
          inet addr:192.168.1.62  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe26:9c03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45958901 (45.9 MB)  TX bytes:51811415 (51.8 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25099 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4225729 (4.2 MB)  TX bytes:4225729 (4.2 MB)

baronipc@baronipc:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
baronipc@baronipc:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 4.2.2.2
nameserver 208.67.220.220
baronipc@baronipc:~$ cat /var/lib/dhcp3/dhclient.leases[/HTML]

As everything worked OK when this was a Vista machine I am certain this has something to do with it now being Ubuntu, not the network.

I have taken a screen shot of the troubled PC with the Places - Network - Windows Network window open and the comment "Unable to Mount Location" and the PING results to another machine on the network and the "Personal File Sharing" window open stating it needs other packages to work...  This is where my gut feel is the problem

---

### Post by Morbius1 on 2010-11-05
Until the networking folks chime in let me take care of the easy one:
> and the "Personal File Sharing" window open stating it needs other packages to work...  This is where my gut feel is the problem     Personal File Sharing is not Samba - has nothing to do with Samba. Since nothing else seems to be working though you might give it a shot. To enable it you need to install two packages:
```
apache2.2-bin
libapache2-mod-dnssd
```It sets up a baby apache server and announces it's share using avahi. Note that it will only share one folder: /home/username/Public

> And here are two more from other PCs on the LAN that do work.  The former works best of all:You're going to have to explain that statement. Some PC's can access the server and some cannot? 

I may be wrong but I really don't think this is a Samba issue because you cannot access the server from some pc's by ip address. And by that I mean you cannot access the server's shares using:
```
 nautilus smb://192.168.1.50
```

---

### Post by Jonners59 on 2010-11-05
> **Morbius1 said:**
> Until the networking folks chime in let me take care of the easy one:
Personal File Sharing is not Samba - has nothing to do with Samba. Since nothing else seems to be working though you might give it a shot. To enable it you need to install two packages:
```
apache2.2-bin
libapache2-mod-dnssd
```It sets up a baby apache server and announces it's share using avahi. Note that it will only share one folder: /home/username/Public

I may be wrong but I really don't think this is a Samba issue because you cannot access the server from some pc's by ip address. And by that I mean you cannot access the server's shares using:
```
 nautilus smb://192.168.1.50
```

OK, installed the two packages.  Got an error message:
"E: oss4-dkms: subprocess installed post-installation script returned error exit status 10"


> **Morbius1 said:**
> You're going to have to explain that statement. Some PC's can access the server and some cannot?   The Laptop seems to work better, quicker in finding the other PCs.  None finds the server.

That said I was tinkering earlier and set up an FTP to the server from one machine and that worked, but it does not give me access to the media I am after... and for what I want pointless, but it did work.

> **Morbius1 said:**
> 
I may be wrong but I really don't think this is a Samba issue because you cannot access the server from some pc's by ip address. And by that I mean you cannot access the server's shares using:
```
 nautilus smb://192.168.1.50
```

I'll test this another time, I am being instructed to take care of the kids!!!!!!

---

### Post by Morbius1 on 2010-11-05
Every time you post you keep going further and further into uncharted territory for me.

Doing this:
> Personal File Sharing is not Samba - has nothing to do with Samba. Since nothing else seems to be working though you might give it a shot. To enable it you need to install two packages:
```
apache2.2-bin
libapache2-mod-dnssd

```Results in this?
> "E: oss4-dkms: subprocess installed post-installation script returned error exit status 10"I had to go into synaptic to find out what oss4 was and it doesn't seem related or even have common dependencies so I have no idea.

---

### Post by Jonners59 on 2010-11-05
I like to keep you on your toes...  Keep the little grey cells working!

I could create the shared folder, but still not visible.

I'm tiered of all this I just want to get on.  It is so easy in Windows, disappointed to have these issues in Ubuntu.

---

### Post by Morbius1 on 2010-11-06
>  I'm tiered of all this I just want to get on.  It is so easy in Windows, disappointed to have these issues in Ubuntu.Based on your posts it's easy in Ubuntu as well:
> And here are two more from other PCs on the LAN that do work.  The former works best of all:I'm going to guess that you didn't have to resort to a soldering iron to make that work. The problem is your server. 

If you haven't explored NFS by now and are considering a reinstall I would suggest doing it in steps:

Install Ubuntu, update your install for the latest packages and then stop. Don't start adding oss4 or any other software just make a simple guest share and see if your clients can connect.

---

### Post by Jonners59 on 2010-11-06
> **Morbius1 said:**
> Based on your posts it's easy in Ubuntu as well:
I'm going to guess that you didn't have to resort to a soldering iron to make that work. The problem is your server. 

If you haven't explored NFS by now and are considering a reinstall I would suggest doing it in steps:

It's just that to do fine tuning and get stuff going one always has to add a package here and there.  Like playing DVDs, I have had to keep a list of extra stuff needed to play them.  Why not out of the box.

This is no exception.  I built a VPN in Windows, which has not worked in Ubuntu (next job)..

Re the other PCs/Laptops.  There was some jiggery pockery, and all were different, but they were all upgrades from 9.4 to 9.10 to 10.4, so all the settings carried forward.  So I do not know what I did to make them work, but NONE were as bad as this.  But all are different in performance it has to be said.

NFS?  I doubt it.  What would I need to do and what is it?

> **Morbius1 said:**
> 
Install Ubuntu, update your install for the latest packages and then stop. Don't start adding oss4 or any other software just make a simple guest share and see if your clients can connect.

That's a big job.  I'd have to recreate my Virtual Machines too.  Need to get some brownie points off the wife first.

---

### Post by Jonners59 on 2010-11-19
Is there any more help on this, please?

I updated my wife's pink (yes, it really is pink) Sony Vaio laptop and now that too will not play.

On both machines I can install and set up sharing on folders and directories.  There are 2 issues:  the first issue comes in these machines being able to see other machines via Places-Network....  and Windows Network.

I note that the Windows Network icon does not look like those on other machines where everything is fine.  See photo.

Also the machine in question can not see or open it's own shared repositories, folders, directories via this route, though listed, also see same screen shot

Then, the other issue is; other machines on the network can not see these 2 machines, yet the good machines have a clear view of each other.  Also note the virtual machine on one of the two not working can be seen on the network.

I am sure it is a package or config somewhere.

---

### Post by Jonners59 on 2010-11-21
What a 24hr roller coaster!
I managed to get it working for a while having solved through a different thread for a different issue on another machine.

Simply, I removed old source data and took the machine "back" as a result.  Suddenly the folders/partitions in question appeared, not in smb but via the "Places" - "Connect to Server" route..

[http://ubuntuforums.org/showthread.php?t=1613644]("http://ubuntuforums.org/showthread.php?t=1613644")

So delighted I moved to next phase, back ups.  Left it backing up, came back and the machine was full of memory errors.  Ended rebuilding from scratch including the virtual box with its Windows 7 and 3CX telephone system.  NOT happy.  I refer to my comments fo before, always one step forward and two back.

Now I have visibility of all machines on the "Network", and in "Windows Network".

When I then log on to them only 1 shows its shared folders (the one I am typing on) "Jonathan-Laptop", and works perfectly.  None of the others work.  they may show the printer folder, but that's it.

The worst is "server" as this one has all the documents, videos, pictures, etc and is where I would also like to start using as a media source for the others, maybe even an in-house shooting game....

So where do we go from here?

What reports would show the differences in configs?

And how do I change them

Some screen shots enclosed
PS:  I followed all the tips below.

---

### Post by Jonners59 on 2010-11-22
FYI:
The Hard drive with the partitions I want to share are owned by root.  I can not change the sharing option because of this.  I believe/wonder if this is the problem.

1.  How do I test
2. How do I change ownership.

Typical is /media/WinC/

---

### Post by Jonners59 on 2010-11-23
OK, I don't know what I did, but somehow I got it working.
 
All I can say is I went through all the old threads I had created over the past 12 months and took out all the cmd line and installed and configs suggested and tried them, then bang, it all started working.
 
I shall close the thread as solved.  Thanks to all for your help, especially Morbius1

[HTML]#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = yes
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom[/HTML]

---

### Post by SaintDanBert on 2010-12-18
> **Jonners59 said:**
> I am running 10.4 on a number of machines ...

Ubuntu "version numbers" are actually date strings:
[list]
[*]first digits represent the year
[*]second digits represent the month
[/list]

Some examples:
v8.04 ..... 04 (April) 2008
v9.10 ..... 10 (October) 2009
v10.04 .... 04 (April) 2010
v10.10 .... 10 (October) 2010

Yes, there is a pattern of April and October releases each year.
While not an official Ubuntu resource, you might find this interesting.
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29)

Cheers,
~~~ 0;-Dan

---

### Post by Jonners59 on 2010-12-18
> **SaintDanBert said:**
> Ubuntu "version numbers" are actually date strings:
[LIST]
[*]first digits represent the year
[*]second digits represent the month
[/LIST]

Some examples:
v8.04 ..... 04 (April) 2008
v9.10 ..... 10 (October) 2009
v10.04 .... 04 (April) 2010
v10.10 .... 10 (October) 2010

Yes, there is a pattern of April and October releases each year.
While not an official Ubuntu resource, you might find this interesting.
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29)

Cheers,
~~~ 0;-Dan
Dan
Sorry, but what's this all about.  Doesn't have anything to do with sharing and the thread subject

PS:  I had gathered that about a year ago.

---

### Post by SaintDanBert on 2010-12-20
the original post spoke about "v10.4" so I wrote about that as clarification. I could have been more clear about why I wrote.
Thanks for keeping me honest.

Cheers,
~~~ 0;-Dan

---

