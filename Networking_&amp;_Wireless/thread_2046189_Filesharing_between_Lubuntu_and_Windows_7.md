---
title: "Filesharing between Lubuntu and Windows 7"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by Faraday92 on 2012-08-22
Hello,

I have a windows 7 system and a lubuntu netbook set up. I would like to share my files on lubutu with my windows 7 machine but so far nothing has worked. i tried multiples guides with samba and nothing has worked. I can see the netbook on another linux system i have, but i can't see it on windows. what am i doing wrong?

Faraday

---

### Post by Faraday92 on 2012-08-22
Hey some more info i forgot to add to this is that i also have sabnzbd and sickbeared insatlled on the system and i also can't connect to them from my windows machine. and i updated the linux kernel

---

### Post by blackmail on 2012-08-22
could it be that the windows system is designed in such a way that it is a pain in the back side to connect to other platforms, portability and inter platform communication was never a priority at MS. and also i have tried to make some computers see each other, and i have had extreme success with windows xp and almost any linux distro, but i tried for one week and did not succeed...

isn't there a tool for windows, like total commander with the help of which you could connect to the linux system?

---

### Post by marinara on 2012-08-22
try browsing by ip

---

### Post by Faraday92 on 2012-08-22
not just see but also just to get to the files of the netbook. i can access them over the network

I tried with //xxx.xxx.xxx.xx but it gives me an unspecified error and when i click diagnose it says the windows PC is okay but lubuntu isn't configured correctly

---

### Post by critin on 2012-08-22
> **Faraday92 said:**
> Hello,

I have a windows 7 system and a lubuntu netbook set up. I would like to share my files on lubutu with my windows 7 machine but so far nothing has worked. i tried multiples guides with samba and nothing has worked. I can see the netbook on another linux system i have, but i can't see it on windows. what am i doing wrong?

Faraday

Is lubuntu new to you, Faraday?   I just installed it for the first time and I too, cannot find a Network.  Ubuntus always connect to Windows and others.  mine will see linux partitions on the same hd, but no reference to linux and windows on other machines.  Other machines can see lubuntu.

Lubuntu apparently networks in a different way than ubuntu which is always in Places in file manager.    I hope someone solves this issue for you (and me)

---

### Post by marinara on 2012-08-22
shouldn't it be backslashes?

---

### Post by Faraday92 on 2012-08-23
sorry yeah i did use that. i just installed gadmin-samba and will see if i can set it up with that. worth a shot maybe i did not set it up properly. also does anyone know if a 64 bit windows 7 install will work with a lubuntu 32 bit system? and do i need to do anything for my windows install to get to my files?

---

### Post by Faraday92 on 2012-08-23
yeah it id not work :(

anyone have any ideas?

ohh also i installed SABnzbd on the lubuntu machine and i also can not access it on my windows PC

---

### Post by Faraday92 on 2012-08-23
ohh i also tried to disable the firewall on the windows PC and it did not help

---

### Post by Faraday92 on 2012-08-24
okay i just installed nautilus file manager. When i click on browse network - windows network. when i try too i get the error

unable to mount location
failed to retrive share list from server

can anyone help me out? like what should i do to fix this or what can i do to narrow down where the problem lies.

---

### Post by SteveDee on 2012-08-24
> **Faraday92 said:**
> Hello,

I have a windows 7 system and a lubuntu netbook set up. I would like to share my files on lubutu with my windows 7 machine but so far nothing has worked...

>  ...Lubuntu apparently networks in a different way than ubuntu...


With Lubuntu I suggest you start by following my guide here: [http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba](http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba)

This should allow you to access network folder & file shares between Linux computers.

You should also be able to "see" Windows 7 network computers, but probably not access their files until you change some Win7 network settings. Also, you probably won't see Linux devices on Win7 at this stage.

On Win7 (probably as admin) go to Control Panel > Network and Sharing Centre > Change Advance sharing settings 

Start by selecting "Home or Work" profile and opening up (relaxing) the settings as follows:-
 - Turn on network discovery
 - Turn on file & printer sharing
 - Turn on sharing so anyone with network access can read & write in Public Folders
 - Enable file sharing for devices that use 40 or 56 bit encryption
 - Turn off password protected sharing
 - Allow Windows to manage homegroup

Hopefully now you will see computers in both directions (if not, try rebooting everything)

Create folder & file shares as required on Win7.

Obviously once you have established access this way, you will need to consider your own security requirements and reset any setting as required.

---

### Post by Faraday92 on 2012-08-25
I sitll can't get linux files from windows or even see the machine. and i have changed all my security settings

i am about to give up on linux because this is a real pain to set up

---

### Post by SteveDee on 2012-08-26
> **Faraday92 said:**
> I sitll can't get linux files from windows or even see the machine...

Can you see Windows machines from Linux?

Can you successfully ping Windows from Linux, and ping Linux from Windows?

Can you try temporarily disabling Windows Firewall. Note than when making changes on a Win7 machine, your Network view may be cached (i.e. each time you open explorer > Network you may have the same limited view of devices). So always right click and select Refresh.

Win7 networking with non-Windows devices seems more tricky than WinXP, which in turn was more tricky than Win2000 (I like Win2000). But what you are trying to do is neither impossible or unusual. I've just switched on a Win7 laptop, a Lubuntu netbook and a Debian RaspberryPi, and once I disabled the Win7 firewall they all see one another and play nice.

---

### Post by chuckrp on 2012-08-26
I had a similiar issue using Mythbuntu and a Win 7 computer. The Myth computer is wireless. Was finally able to get it but the ifconfig address will change on me. I can finally talk to both machines.

---

### Post by Faraday92 on 2012-08-26
i use norton and i have tried disabling the firewall on there but it did not help. and no the 2 machines can not ping eachother :(

i tried refresh in windows. and it did not help

since another linux machine i have can see the share on the netbook i am thinking that there must be something wrong with my windows PC

---

### Post by SteveDee on 2012-08-26
> **Faraday92 said:**
> ...the 2 machines can not ping each other ...

Are you pinging with machine name or IP address? If not IP, then try ping with IP address. Obviously both machines should be in the same address range, with the same sub-net mask.

If this is a home network with a router running DHCP, try pinging the router from both Win & Linux machines to establish that they are both on/using the network (e.g. ping 192.168.0.1 or whatever its IP is).

If there are no hardware problems with your network, ping problems on Windows usually means that ICMP is blocked by a firewall.

---

### Post by Faraday92 on 2012-08-26
okay i tried ping with IP no success

i change my norton firewall setting and all  ICMP things are set to allow

the IPs are 192.168.179.38 and 192.168.179.34

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : fritz.box
   Link-local IPv6 Address . . . . . : fe80::601d:347
   IPv4 Address. . . . . . . . . . . : 192.168.179.34
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.179.1

wlan0     Link encap:Ethernet  HWaddr 94:db:c9:a3:4e:7a  
          inet addr:192.168.179.38  Bcast:192.168.179.255  Mask:255.255.255.0
          inet6 addr: fe80::96db:c9ff:fea3:4e7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:559154 (559.1 KB)  TX bytes:187738 (187.7 KB)

ping 192.168.179.38

Pinging 192.168.179.38 with 32 bytes of data:
Reply from 192.168.179.34: Destination host unreachable.
Reply from 192.168.179.34: Destination host unreachable.
Reply from 192.168.179.34: Destination host unreachable.
Reply from 192.168.179.34: Destination host unreachable.

Ping statistics for 192.168.179.38:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

imb-server@IMB-SERVER ~ $ nmap -sP  192.168.0.30-40

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-08-26 22:12 CEST
mass_dns: warning: Unable to open /etc/resolv.conf. Try using --system-dns or specify valid servers with --dns-servers
mass_dns: warning: Unable to determine any DNS servers. Reverse DNS is disabled. Try using --system-dns or specify valid servers with --dns-servers
Nmap done: 11 IP addresses (0 hosts up) scanned in 6.04 seconds

---

### Post by metilly on 2012-11-18
> **chuckrp said:**
> I had a similiar issue using Mythbuntu and a Win 7 computer. The Myth computer is wireless. Was finally able to get it but the ifconfig address will change on me. I can finally talk to both machines.

A lot of modems and routers give you the option to lock an IP address to the computer's MAC address.  A computer or other device when requesting an IP from the DHCP server will often be given the IP address it had previously but not always. Don't forget to save the new settings in case you have to reboot your router/modem.  Not saving the settings may give you more headaches down the track if you forget you needed to do this.  Been there, done that...

---

### Post by SteveDee on 2012-11-19
I find it really useful to have a Lubuntu LiveUSB memory stick with a basic install + the stuff needed for networking.

This can be used to check any machine, thereby eliminating any potential issues caused by additional software packages already loaded to your target machine. It also means you can cross-check the LiveUSB on several machines.

My updated notes for Lubuntu & Win7 are here: [http://captainbodgit.blogspot.co.uk/2012/10/networking-with-lubuntu-win7-and.html](http://captainbodgit.blogspot.co.uk/2012/10/networking-with-lubuntu-win7-and.html)

It looks like additional packages are still required for full networking on Lubuntu 12.10.

---

