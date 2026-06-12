---
title: "SSH, firestarter problem -  SSH link works for all but one PC"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by jwvraets on 2010-01-05
I am having problems getting ssh to work properly across between one specific computer and three others on an small internal network. The LAN is behind a router. Two PCs are virtually identical, both running Ubuntu 91.0, differing only in one having slightly more Ram and slightly more disk capacity and one is set to a fixed IP address. Briefly:
 

 Atilla: IP Address: - Fixed IP, ubuntu 9.10, 4 gig RAM, 1.5 gig disk capacity and otherwise identical to:
 Fourpak: IP Address – DHCP, ubuntu 9.10, 8 gig RAM, 2 gig disk capacity
 Tophat: IP Address – DHCP, Fedora 12
 Traveller: IP Address -DHCP, Windows Vista
 

 Using ssh, Atilla can log into Fourpak, Tophat and Traveller.
 Using ssh, Fourpak can log into Tophat and Traveller.
 Using ssh, Tophat can log into Fourpak and Traveller
 Using ssh, Traveller can log into Fourpak and Tophat.
 Attempts use ssh to log into Atilla from any other PC however always result in a message “Connection refused by server”.
 

 Atilla and Fourpak are running Firestarter (yes it is running) as a firewall. Both have identical setups with SSH allowed for everyone on port 22 for inbound traffic and outbound traffic set to permissive with no entries for denied for either hosts or service.
 

 I have googled and read but cannot see what might be the problem after about a day of messing around. Frankly I am puzzled and going in circles now and would appreciate some help since this area is relatively new to me.  
 

 I want o be able to ssh reliably between any PC and Atilla but want to focus my attention on the 2 ubuntu machines Atilla and Fourpak on the assumption the problem lies in some configuration issue in atilla that makes it behave differently from Fourpak. So far I can not find anything but this is new area for me so any help/guidance would be very much appreciated.
 

 What do I need to look for?
 Is the issue related to Atilla being a fixed IP address machine and Fourpak being set by DHCP?
 Where do I start looking since the firewalls seem to be set up the same?
 

 Thanks for taking the time to read and all help/suggestions appreciated.
 

 JW

---

### Post by johnson.d on 2010-01-06
To sort out this problem, you can use the following steps.

1)Compare /etc/ssh/sshd_config on Atilla and Fourpak for any differences in the access control options. (man sshd_config for more details)

2)Check for the tcpwrappers settings like /etc/hosts.deny and /etc/hosts.allow files

3)Disable Firewall for testing purpose and check ssh connection to Atilla.

4) Use a packet sniffer like wire shark on Atilla to check the state of the ssh connection

Let me know if any of these steps help

---

### Post by Loosewheel on 2010-01-06
I think you may have a problem with the static IP of Atilla. If the name doesn't resolve, you wont connect. Try using the IP Addr. ie; 'ssh 192.168.x.x'
If that works, add an entry to the '/etc/hosts' file on Fourpack, Tophat, and Traveller.

---

### Post by jwvraets on 2010-01-06
To johnson.d:
  Thanks for your message and sugestion. Your suggestion for a process was
 -----------
  To sort out this problem, you can use the following steps.

1)Compare /etc/ssh/sshd_config on Atilla and Fourpak for any differences in the access control options. (man sshd_config for more details)

2)Check for the tcpwrappers settings like /etc/hosts.deny and /etc/hosts.allow files

3)Disable Firewall for testing purpose and check ssh connection to Atilla.

4) Use a packet sniffer like wire shark on Atilla to check the state of the ssh connection

Let me know if any of these steps help
 The corresponding results are:
 

 
[LIST=1]
[*]sshd_config on Atilla and Fourpak 	are identical
[*]The hosts.deny and hosts.allow 	files on both Atilla and Fourpak are identical and contaion no 	entries.
[*]Disabling the firewall (I.e 	firestarter) on both machines, yields the same result, i.e. 	“connection refused by server” when trying to ssh from Fourpak 	to Atilla. SSHing from Atilla to Fourpak works properly. The 	firestarter turned on or off has no impact on ssh results, I.e it is 	the same as just described.
[*] 	I used Umit to check on port status and this is the result I get: 	(note also the following:
[/LIST]
  192.168.15.7 is Atilla (fixed IP address)
  192.168.15.103 is Fourpak (DHCP assigned IP adsdress)
  192.168.15.201 is a wireless access point (I.e wireless router with router turned off)
  192.168.15.1 is the router between the internal LAN and the broadband modem
 Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-01-06 09:20 EST 
 NSE: Loaded 0 scripts for scanning. 
 Initiating ARP Ping Scan at 09:20 
 Scanning 7 hosts [1 port/host] 
 Completed ARP Ping Scan at 09:20, 0.26s elapsed (7 total hosts) 
 Initiating Parallel DNS resolution of 7 hosts. at 09:20 
 Completed Parallel DNS resolution of 7 hosts. at 09:20, 5.53s elapsed 
 Initiating Parallel DNS resolution of 1 host. at 09:20 
 Completed Parallel DNS resolution of 1 host. at 09:21, 5.52s elapsed 
 Initiating SYN Stealth Scan at 09:21 
 Scanning 192.168.15.1 [1000 ports] 
 Discovered open port 80/tcp on 192.168.15.1 
 Discovered open port 5678/tcp on 192.168.15.1 
 Completed SYN Stealth Scan at 09:21, 0.47s elapsed (1000 total ports) 
 Host 192.168.15.1 is up (0.0098s latency). 
 Interesting ports on 192.168.15.1: 
 Not shown: 998 closed ports 
 PORT     STATE SERVICE 
 80/tcp   open  http 
 5678/tcp open  unknown 
 MAC Address: 00:14:BF:01:F3:E1 (Cisco-Linksys) 
  
 Initiating ARP Ping Scan at 09:21 
 Scanning 248 hosts [1 port/host] 
 Completed ARP Ping Scan at 09:21, 4.08s elapsed (248 total hosts) 
 Initiating Parallel DNS resolution of 248 hosts. at 09:21 
 Completed Parallel DNS resolution of 248 hosts. at 09:21, 5.53s elapsed 
 Initiating SYN Stealth Scan at 09:21 
 Scanning 192.168.15.7 [1000 ports] 
 Completed SYN Stealth Scan at 09:21, 0.07s elapsed (1000 total ports) 
 Host 192.168.15.7 is up (0.0000080s latency). 
 All 1000 scanned ports on 192.168.15.7 are closed 
  
 Initiating SYN Stealth Scan at 09:21 
 Scanning 2 hosts [1000 ports/host] 
 Discovered open port 22/tcp on 192.168.15.103 
 Discovered open port 80/tcp on 192.168.15.201 
 Completed SYN Stealth Scan against 192.168.15.103 in 0.19s (1 host left) 
 Discovered open port 5678/tcp on 192.168.15.201 
 Completed SYN Stealth Scan at 09:21, 1.91s elapsed (2000 total ports) 
 Host 192.168.15.103 is up (0.000076s latency). 
 Interesting ports on 192.168.15.103: 
 Not shown: 999 closed ports 
 PORT   STATE SERVICE 
 22/tcp open  ssh 
 MAC Address: 00:24:1D:D1:4D:07 (Giga-byte Technology Co.) 
  
 Host 192.168.15.201 is up (0.016s latency). 
 Interesting ports on 192.168.15.201: 
 Not shown: 998 closed ports 
 PORT     STATE SERVICE 
 80/tcp   open  http 
 5678/tcp open  unknown 
 MAC Address: 00:13:46:B7:93:4A (D-Link) 
  
 Read data files from: /usr/share/nmap 
 Nmap done: 256 IP addresses (4 hosts up) scanned in 23.87 seconds 
             Raw packets sent: 4514 (197.602KB) | Rcvd: 5003 (204.146KB) 
 It seems the ports on Atilla are all closed. What am I missing?

---

### Post by jwvraets on 2010-01-06
Loosewheel:
> **Loosewheel said:**
> I think you may have a problem with the static IP of Atilla. If the name doesn't resolve, you wont connect. Try using the IP Addr. ie; 'ssh 192.168.x.x'
If that works, add an entry to the '/etc/hosts' file on Fourpack, Tophat, and Traveller.
-----------------
I have been using dot-quad addressing in the connections attempts to eliminate the hosts contents from the process and the problems are as described using that approach. Thank you for the suggestion however.

---

### Post by jwvraets on 2010-01-06
OK - further examination led me to try something else to see what would happen. I did the following:
      I opened a terminal on Atilla

 
[LIST=1]
[*]issued the command:  ssh localhost
[*]received the response: ssh:     connect to host localhost port 22: Connection refused.
[*]On a whim I did the following:     sudo /etc/init.d/ssh restart
[*]After providing the password, it     proceeded to connect me as I would expect. - Progress
[*]Rebooted.
[*]Repeated step 2 above
[*]Got result in step 3 above.
[*]Did step 4 and 5 above and it     works again.
[/LIST]
 Clearly, the ssh server on Atilla is not starting up after a boot. If I force it to start manually, it does work. So now how do I get it to start automatically on boot?

And why does Fourpak work but not Atilla as far as automatic startup of the ssh server after a reboot given the same install disk was used on both (virtually) identical machines?

---

### Post by jwvraets on 2010-01-06
The plot thickens - and it does not appear to be a problem with ssh or firestarter. Instead it appears it is a bug related to the workings of upstart. This is described well into the following forum thread:

  	 	 	 	 	 	  [http://ubuntuforums.org/showthread.php?t=1305226&highlight=sshd+boot](http://ubuntuforums.org/showthread.php?t=1305226&highlight=sshd+boot)
 
I tried to reinstall openssh_server *** one poster suggested, and the server does work but only until you do a reboot and then you are back to square one. Further in the thread is a suggestion that downgrading the Upstart package using the Synaptic package manager would help. Sad to say it makes no difference.

This appears to be a system bug. That said, I have no clue why two virtually identical systems exhibit this bug in one case (Atilla) and not in the the other (Fourpak). Flashes of brilliance would be appreciated.

JW

---

### Post by jwvraets on 2010-01-06
Not being one to give up too quickly, I dig a bit further and found that the reference for the ssh service in /etc/rc.d was named K84ssh which, I gather means it is shut down. According to the README in that directory, I renamed it to S84ssh which apparently should force it (ssh) to start up as part of the boot sequence. I rebooted and found no change in behavior (still not starting), reread the README file and realized I had forgotten to perform the update and then did this:

jwvraets@atilla:~$ sudo update-rc.d ssh defaults
[sudo] password for jwvraets: 
update-rc.d: warning: ssh stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 System start/stop links for /etc/init.d/ssh already exist.
jwvraets@atilla:~$

no change yet.

---

### Post by jwvraets on 2010-01-07
When I said the two systems were essentially the same, that is true for the hardware but not for the software installation. Fourpak is a dedicated Ubuntu Karmic machine. Atilla, however is a dual boot (XP and Ubuntu Karmic) system. Furthermore, there is a problem with GRUB on Atilla. The timer/countdown does not work and has never worked except for the first reboot after the kernel version update this week to 31-16. No idea if the issues are related but given a likely bug this may be relevant for any others with this problem. Fourpak has a completely normal GRUB behavior and no ssh problems.

Just thought you might like to know.

JW

---

### Post by jwvraets on 2010-01-08
Surprise - the problem has resolved itself. No clue how or why, no new updates no changes - it just works now. If it wasn't already to late for such things I would be trying to pull my hair out. Gotta luv this stuff.

JW

---

### Post by jwvraets on 2010-01-21
A follow up to close this thread as solved (at least viable workarounds)...

I have had multiple issues which included this ssh issue as a subset (as it turns out) of an issue with the failure of Ubuntu 9.10 to start any of my services (i.e. ssh, cups and mysql that I was testing) after an update to the upstart package. The fix to this can be found in

[http://ubuntuforums.org/showthread.php?t=1305226&page=3](http://ubuntuforums.org/showthread.php?t=1305226&page=3)

in message #27 from j23tom

I have tested this and it does reliably start the services.

I also had this as an issue in my thread

[http://ubuntuforums.org/showthread.php?t=1382006](http://ubuntuforums.org/showthread.php?t=1382006)

so if you came across that the solutions are as listed there.

All the best

JW

---

