---
title: "Unable to share files with others"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by elkingrey on 2011-08-28
Hello,

I live in an apartment that is shared with others. We all connect to the internet through the same router. I have files I would like to share with others but have been unable to figure out how to make folders public, or how to view public folders of others and get their files. Can somebody help this noob?

---

### Post by papibe on 2011-08-28
Do this:
[INDENT]Right click on the folder you want to share.
Select Share Folder.
You'll be asked to install Samba (maybe called Windows network support, or SMB). Accept it.
[/INDENT]
After that you'll have the option "Sharing Options" if you right click the folder. There you choose the name and the permitions (for example: read and write for all). After that it should be available from other machines when they browse the network.

You can see more details and pics [here]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/") (the tutorial is a bit old the should help).

Regards.

---

### Post by elkingrey on 2011-08-28
Well, I didn't need to install anything else for the sharing options to be available. And I've tried this before. I make the folder shared and yet other people cannot see my folder in the list of public folders in the network. Also, how do I find other people's folders in the network?

---

### Post by Morbius1 on 2011-08-28
What would help is if you post some info about how you are set up. Please post the output of each of the following commands:
```
testparm -s
net uershare info --long
hostname
smbtree
```

---

### Post by elkingrey on 2011-08-28
```
seth@seth-Dimension-8400:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
seth@seth-Dimension-8400:~$ 
```

```
seth@seth-Dimension-8400:~$ net usershare info --long
[seth's shared files]
path=/home/seth/Public
comment=
usershare_acl=Everyone:R,SETH-DIMENSION-8400\seth:F,
guest_ok=n

seth@seth-Dimension-8400:~$ 

```

```
seth@seth-Dimension-8400:~$ hostname
seth-Dimension-8400
seth@seth-Dimension-8400:~$ 

```

```
seth@seth-Dimension-8400:~$ smbtree
Enter seth's password: 
seth@seth-Dimension-8400:~$ 
```

---

### Post by Morbius1 on 2011-08-28
Very first thing you need to fix is this:
> hostname
seth-Dimension-8400Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following to the [global] section - right under the "workgroup" line:
```
netbios name = seth-8400
```[COLOR=Blue]*It doesn't have to be that exact name but it has to be 15 characters or less in length. Anything longer and your machine becomes invisible.*[/COLOR]

Then restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down and see if you can now see the shares.

---

### Post by elkingrey on 2011-08-28
Okay. Did that and I'm still not showing up. 

Two questions. Can I change the name of my computer, that is, instead of seth-Dimention-8400 to something a little less lame?

Also, how do I view publicly shared folders?

---

### Post by Morbius1 on 2011-08-28
> Okay. Did that and I'm still not showing up.
Also, how do I view publicly shared folders?     Those 2 statements contradict one another.
Open a terminal and type:
```
 nautilus smb://seth-8400
```Do you not see a list of your shares?

---

### Post by elkingrey on 2011-08-28
Error: Failed to retrieve share list from server
Please select another viewer and try again.

```
seth@seth-Dimension-8400:~$ nautilus smb://seth-8400
seth@seth-Dimension-8400:~$ 

```What I meant to say is how do I view the folders that OTHER people are sharing?

---

### Post by Morbius1 on 2011-08-28
Nautilus > Network > Windows Network > Hostname > Share-name

---

### Post by elkingrey on 2011-08-28
When I try to open Windows Network I get

UNABLE TO MOUNT

Failed to retrieve share list from server

---

### Post by Morbius1 on 2011-08-28
We need to make sure that you can access your own share before you can access someone else's.

(1) If you did something with the firewall on your machine disable it.

(2) If that doesn't fix it outright then rearrange the order of discovery:
Add another line to smb.conf in the [global] section:
```
 name resolve order = bcast host lmhosts wins
```Then restart samba again.

---

### Post by elkingrey on 2011-08-28
I notice that in the files there is this line

;   name resolve order = lmhosts host wins bcast

I just pasted the line you gave me below it. Should I have uncommented that line out?

Also, I am still getting the same error when trying to open Windows Network.

---

### Post by Morbius1 on 2011-08-28
The line I gave you should be uncommented.

Install the following package:
```
sudo apt-get install nmap
```And run the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Change 192.168.0.100 to the ip address of your machine.

You need the following ports to be open:
> PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm[COLOR=Blue]EDIT: Damn[/COLOR] - I'm forgetting the obvious. Do you have nmbd running:
```
 sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```

---

### Post by elkingrey on 2011-08-28
Before I do these next things I should clarify.

I did keep the line you gave me uncommented. What I meant to ask is should I have just uncommented the OTHER line and not use the one you gave me, or should I just keep the original line commented and use yours instead?

Second, I don't know how to find the ip address of my computer. 

Last, the last code box you gave me, are those commands to issue? If so, in order? Not sure what to do with that last box.

---

### Post by elkingrey on 2011-08-28
```
seth@seth-Dimension-8400:~$ sudo service nmbd status
[sudo] password for seth: 
nmbd start/running, process 1739
seth@seth-Dimension-8400:~$ 

```

---

### Post by Morbius1 on 2011-08-28
> I did keep the line you gave me uncommented. What I meant to ask is  should I have just uncommented the OTHER line and not use the one you  gave me, or should I just keep the original line commented and use yours  instead?Leave the original line as it is and just add mine.
>  Second, I don't know how to find the ip address of my computer. ```
ifconfig
```> Last, the last code box you gave me, are those commands to issue? If so, in order? Not sure what to do with that last box.     
```
sudo nmap -sS -sU -T4 192.168.0.100
```That's the whole command but with your ip address instead of 192.168.0.100

---

### Post by elkingrey on 2011-08-28
```
seth@seth-Dimension-8400:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:a3:92:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20126 (20.1 KB)  TX bytes:20126 (20.1 KB)

ra0       Link encap:Ethernet  HWaddr 68:7f:74:ec:ba:61  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6a7f:74ff:feec:ba61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:501483 errors:3 dropped:0 overruns:0 frame:0
          TX packets:150805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:292193223 (292.1 MB)  TX bytes:29802010 (29.8 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.10  P-t-P:10.8.0.9  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:117873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:132854621 (132.8 MB)  TX bytes:8662196 (8.6 MB)

seth@seth-Dimension-8400:~$ 

```

Whoops, what I meant to say wasn't last code box but QUOTE box. You're talking about making sure the ports were open. I don't know how to do that. Also, I'm not sure which of the many ipaddresses in the output was mine.

---

### Post by Morbius1 on 2011-08-28
> ra0       Link encap:Ethernet  HWaddr 68:7f:74:ec:ba:61  
          [COLOR=Blue]inet addr:192.168.1.113[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0I'm going to guess that 192.168.1.113 is the correct one although I have no idea what an "ra0" is. And isn't tun0 a vpn tunnel?

You may have exceeded my level of knowledge if your network is this complex.

Anyway try the command with that ip address:
```
 sudo nmap -sS -sU -T4 192.168.1.113
```

---

### Post by elkingrey on 2011-08-28
Should I disconnect from my VPN before doing this?

---

### Post by Morbius1 on 2011-08-28
> **elkingrey said:**
> Should I disconnect from my VPN before doing this?
The command is a simple port scanner so I don't think it should matter but I honestly don't know.

---

### Post by elkingrey on 2011-08-28
```
seth@seth-Dimension-8400:~$ sudo nmap -sS -sU -T4 192.168.1.113
[sudo] password for seth: 
sudo: nmap: command not found
seth@seth-Dimension-8400:~$ 

```

---

### Post by Morbius1 on 2011-08-28
Then you didn't install nmap:
```
sudo apt-get install nmap
```

---

### Post by elkingrey on 2011-08-28
```
seth@seth-Dimension-8400:~$ sudo nmap -sS -sU -T4 192.168.1.113

Starting Nmap 5.21 ( http://nmap.org ) at 2011-08-28 19:39 EDT
Nmap scan report for 192.168.1.113
Host is up (0.0082s latency).
Not shown: 1993 closed ports
PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
3689/tcp open          rendezvous
68/udp   open|filtered dhcpc
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.36 seconds
seth@seth-Dimension-8400:~$ 

```

Whoops. My bad. I currently have my VPN to tunnel all internet traffic through to the VPN. I'm assuming that if I want to share files with others in my home network, I will have to disconnect from the VPN, yes?

---

### Post by Morbius1 on 2011-08-28
That would be my guess but my knowledge of VPN is zero.

All I can tell you is that your smb.conf is textbook correct, your firewall is not in the way, and your netbios name is now the correct length so I don't know what else to tell you.

---

### Post by elkingrey on 2011-08-28
Well, I disconnected from the VPN and still cannot open the Windows Server. :(

---

### Post by elkingrey on 2011-08-28
I opened the properties of Windows Network and went to permissions. It said:

The permissions of "smb" could not be determined. Does this help at all?

---

### Post by terrydiehard on 2011-09-03
How to share files on your desktop in Ubuntu 10.04

Create a folder on your desktop called "sharetest". Please leave out the inverted commas.
let us say you want to share a folder called "sharetest" on your desktop. You will have to go to the SAMBA configuration file. This configuration file is found in, /etc/samba/smb.conf. To edit the SAMBA configuration file, ie. the smb.conf, PRESS alt+F2 at the same time. Type the command gksudo gedit/etc/samba/smb.conf. The SAMBA configuration file will open up. If you get a black page, something went wrong.

Now at the end of the SAMBA configuration file, that is the "samba.conf". Insert these lines.
______________________________________________
[sharetest]
   comment = testing the share
   path = /home/gavaskar/Desktop/sharetest
   browseable = yes
   read only = no
   guest ok = no
   force user = gavaskar
_______________________________________________

I have an account called gavaskar, so my force user = gavaskar. In my global settings I have this as well as "guest = force user", without inverted commas. In my global settings I also have this, "usershare owner only = false", without inverted commas.

---

### Post by elkingrey on 2011-09-04
> **elkingrey said:**
> Error: Failed to retrieve share list from server
Please select another viewer and try again.

```
seth@seth-Dimension-8400:~$ nautilus smb://seth-8400
seth@seth-Dimension-8400:~$ 

```What I meant to say is how do I view the folders that OTHER people are sharing?

So, I decided to go back and put seth-Dimension-8400 under the global settings instead of what you recommended which was just seth-8400. Then I did the command above and it worked. It asked me for my password and then showed me a couple of different folders. One of them was a music folder, which I think I remember messing around with a while ago, but my entire music collection was not available despite having made it so, or so I thought.

---

