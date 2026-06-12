---
title: "Can't connect to FIOS when wired"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by Gooddad56 on 2010-07-21
New to Linux/Ubuntu, I have searched and tried a number of suggested solutions posted here and on other Ubuntu forums.
My son received a computer with Xubuntu 9.04 already installed. We first tried a wireless adapter for internet connection, but got no results so I have run a cable directly to the Verizon Router 9100EM, but it connected to google.com and then disconnected.
As I said, I tried a few things and now cannot get even an initial connection.
 
using ifconfig, this is the result:
 
eth0    Link encap:Ethernet HWaddr 00:50:ba:d7:6d:70
          inet6 addr : fe80::250:baff:fed7:6d70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          Rx packets:32 errors:71 dropped:0 overruns:0 frame:0
          Tx packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          Rx bytes:2449 (2.4 Kb)  Tx bytes:1836 (1.8 Kb)
          Interupt:10  Base Address:0x9400
 
lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr:  ::1/128  Scope:Host
         UP LOOPBACK RUNNING MTU:16436  Metric:1
         Rx packets:12 errors:0 dropped:0 overruns:0 frame:0
         Tx packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
         Rx bytes:840 (840.0 B)  Tx bytes:840 (840.0 B)
 
I tried to find a way to ping, using SYSTEM->ADMINISTRATION->NETWORK TOOLS but the choice of ADMINISTRATION does not exist.
 
Any guidance would be helpful.

---

### Post by Fire_Chief on 2010-07-21
It would appear that your eth0 interface (wired LAN) either lost or did not get an IPv4 address from the router. Do you know if you are using just IPv6 on your LAN (not common)? Are there other computers that can get to the Internet? If so, you may want to compare the IP settings. Might be worth trying a static IP address assignment for the workstation instead of allowing DHCP to give it an address.

Cheers!

---

### Post by Gooddad56 on 2010-07-21
I have 2 other machines running Win XP that connect fine (except for Verizon's woeful communication speeds). I do not know how to check for IPv6.
I assume from reading other posts that when you talk of the static IP I would have to access my router at 192.168.1.1 and establish a static IP that only this machine would use, correct? How would I establish the same static IP within Xubuntu?
 
Thanks

---

### Post by Gooddad56 on 2010-07-21
Also, one of the other machines is wired and the other is wireless.

---

### Post by Iowan on 2010-07-21
DHCP quit working on my Jaunty (9.04 Ubuntu) laptop. [Here]("http://ubuntuforums.org/showthread.php?t=1156441") is how I fixed it.  Hope it'll work for you...

---

### Post by Gooddad56 on 2010-07-21
As one not familiar with using Terminal that well, how would I go about "Commenting out"    /etc/dhcp3/dhclient.conf ?

---

### Post by Iowan on 2010-07-21
Terminal is Applications->Accessories->Terminal (on my Ubuntu box).
First, I'd make a copy of the original for goof-proofing:```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.bak
```
I'm not familiar with which editors come in Xubuntu - I use **nano**.
```
sudo nano /etc/dhcp3/dhclient.conf
```
Arrow down to the line that begins "option rfc3442". With the "o" highlighted, hit the # key to "comment out" the line (any line beginning with a # is a comment). Below the "request" line, highlight the "r" in "rfc3442" and delete through the comma - the line will look something like```
     ntp-servers;
```Save the file by hitting CTRL-O - **nano** will ask for name of file to write - [ENTER] will save it to original name. then CTRL-X will quit **nano**. You can use ```
less /etc/dhcp3/dhclient.conf
``` to verify that the changes are there, then restart networking (or reboot).

---

### Post by Gooddad56 on 2010-07-23
Thanks for the procedure. Pretty straightforward when you are actually doing it. Unfortunately there is still no connection. I am going to try the cable again tomorrow by bringing an XP box upstairs to connect to the internet. It was working at one time, but just to be sure I'll test again.
 
In the meantime, do you have next troubleshooting steps?

---

### Post by Gooddad56 on 2010-07-24
OK - connected a Windows XP machine to the cable and it works fine. So now I'm back to square one - how to get Xubuntu 9.04 to connect to the internet?
 
Any ideas from anyone?

---

### Post by Iowan on 2010-07-25
From a terminal, check **sudo dhclient eth0**. On Ubuntu, the terminal is under Applications->Accessories->Terminal... I'm not sure about Xubuntu. You'll *probably* something like:```
Listening on LPF/eth0/00:23:54:.......
Sending on LPF/eth0/00:23:54:.......
Sending on Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by Gooddad56 on 2010-07-25
Results of sudo dhclient eth0 are-
 
Listening on LPF/eth0/00:50:ba:d7:6d:70
Sending on LPF/eth0/00:50:ba:d7:6d:70
Sending on Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11

No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 
Then tried sudo lshx -C network
results -
 
* -network
description: Ethernet interface
product: RTL-8139/8139C/8139c+
vendor: Realtek ......
physical ID: d
bus info: [EMAIL="pci@0000:00:0d.0"]pci@0000:00:0d.0[/EMAIL]
logical name: eth0
version: 10
serial: 00:50:ba:d7:6d:70
size: 100 Mb/s
capacity: 100 Mb/s
width: 32 bits
clock: 33 Mhz
capabilities: pm bus_master cap_list ethernet physicaltp mii 10bt 10bt-fd 100bt-fd autonegotiation
  configuration: autonegotiation=off broadcast = yes driver = 8139too driver version = 0.9.28 duplex=full latency=32 link = yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100 ml/sec
 
*-network DISABLED
            description: Ethernet interface
            physical ID: 1
           logical name: pan0
            serial: 6a:5e:e3:ec:16:56
            capabilities: ethernet physicla
            configuration: broadcast=yes driver=bridge driverversion=2.3 firmware= N/A 
            link=yes multicast=yes
 
then tried
sudo service network-manager stop but it did not recognize the service or said the service wasn't there.
 
 
Next Steps?

---

### Post by Iowan on 2010-07-25
When I had the DHCP problem, before I "discovered" the rfc3442 problem, I set up a static address (outside the range of my DHCP server). You can use Network Manager to set up a static address, but you'll need to get the DHCP range from your server (router?). 
Failing that, you can *probably* set up a static address via */etc/network/interfaces*. You will also need to manually set the address of your nameserver in */etc/resolv.conf*

---

### Post by Gooddad56 on 2010-07-25
So **IF** I can access Network Manager (I have concerns) then I could set up a DHCP address like 192.168.1.105, assuming my range went to .100. How might I find the range of the router? Use ipconfig on the Windows machines?
 
Failing that, what are the steps to set up a static using *etc/network/interfaces* (do I use *sudo* with a command?)? How would I set up the address for the *nameserver* (is that a phrase to use when one doesn't know if there is a name on the server?)? I have a router from Verizon, so I don't know how it is named unless it is the same name as my wireless connection.

---

### Post by oldfred on 2010-07-26
You cannot assign a fixed address within the range that the router assigns DHCP addresses (typicall 100 to 150).

I attached the settings I used in system, preferences, network connections. If you show eth0 click on it & edit it or if not add one. Under ipv4 settings you can edit.

You can in windows use a terminal and ipconfig to show settings and in Ubuntu it is ifconfig. Listing are similiar.

---

### Post by Gooddad56 on 2010-07-26
OK - so now the Network Manager icon says I have a network connection. Thank you for the details that got me this far.
I still cannot access a webpage, however. No Google, no MSN, no Ubuntu, nothing.
 
When reading some Ubuntu documentation on troubleshooting, a way to check a wired connection is to *ping *from System -> Administration -> Network Tools but I do not have Administration as a choice in 9.04 nor can I find Network Tools anywhere as well. I tried pinging from Terminal but with no success. it could not locate the webpage.
 
Next Steps?

---

### Post by Iowan on 2010-07-26
Did you ping by name or address? Try 74.125.95.106 or 8.8.8.8
What is in */etc/resolv.conf*? Network Manager should let you manually input a DNS server. You can use whatever the rest of the machines use, or Google's (8.8.8.8).

---

### Post by Gooddad56 on 2010-07-26
I tried to ping by address and name (ubuntu.com or 192.168.1.1).
 
The DNS sserver I used is the one suggested by **oldfred** above - 192.168.1.1 and I was able to "get connected".
 
I'll report what is in /etc/resolve.conf - once I figure out how to access the information (sudo or ?).

---

### Post by Iowan on 2010-07-26
> **Gooddad56 said:**
> I'll report what is in /etc/resolve.conf - once I figure out how to access the information (sudo or ?).Either of these should work:
```
cat /etc/resolv.conf
less /etc/resolv.conf
```
(Notice the missing "e" in resolv )

---

### Post by Gooddad56 on 2010-07-26
Pinging to either address returns: Network is Unreachable
 
typing /etc/resolv.conf  returns command not found
 
Wait for next results please

---

### Post by Gooddad56 on 2010-07-26
Typing *cat /etc/resolv.conf* returns:
 
Generated by Network Manager
nameserver 8.8.8.8
 
Which is the address I just put into Network Manager per your suggestion.
 
Next?

---

### Post by oldfred on 2010-07-26
With my router the DNS is managed by the router's DHCP. My resolv.conf is set just to go to the router. Can you check your router's settings?

fred@fred-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
fred@fred-desktop:~$

---

### Post by Gooddad56 on 2010-07-26
Oldfred,
 
I just set my DNS server to 8.8.8.8 (I guess it's Google) then when I typed cat /etc/resolv.conf I get
Generated by NetworkManager
nameserver 8.8.8.8
 
So if I left it at 192.168.1.1 which is what you have, then I would get that address as the nameserver.
 
Next Steps?

---

### Post by oldfred on 2010-07-27
My name servers are Comcast's and I set them in the router on the router management page. I am sure you can use googles, but Verizon may have their own also.

I have a linksys router and bookmark this to get into my router.

[http://192.168.1.1/index.asp](http://192.168.1.1/index.asp)

---

### Post by Gooddad56 on 2010-07-27
This is the results of ipconfig on my wireless XP machine. Does it tell you anything that can help? 
 
Windows IP Configuration
        Host Name . . . . . . . . . . . . : OfficeT3504
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : home
Ethernet adapter Wireless Network Connection:
        Connection-specific DNS Suffix  . : home
        Description . . . . . . . . . . . : Dynex Enhanced G Desktop Card
        Physical Address. . . . . . . . . : 00-1C-DF-4E-BA-17
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
                                            68.238.64.12
        Lease Obtained. . . . . . . . . . : Monday, July 26, 2010 3:16:43 PM
        Lease Expires . . . . . . . . . . : Tuesday, July 27, 2010 3:16:43 PM

---

### Post by Gooddad56 on 2010-07-27
Just tried the user name and password that Verizon Tech gave me to log into the router but it doesn't work. I have to call them in the morning to get the info and try tomorrow. If the prior post gives anyone hints to help me, I appreciate it.
 
Thanks

---

### Post by Fire_Chief on 2010-07-27
> **Gooddad56 said:**
> This is the results of ipconfig on my wireless XP machine. Does it tell you anything that can help? 
 
Windows IP Configuration
        Host Name . . . . . . . . . . . . : OfficeT3504
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : home
Ethernet adapter Wireless Network Connection:
        Connection-specific DNS Suffix  . : home
        Description . . . . . . . . . . . : Dynex Enhanced G Desktop Card
        Physical Address. . . . . . . . . : 00-1C-DF-4E-BA-17
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
                                            68.238.64.12
        Lease Obtained. . . . . . . . . . : Monday, July 26, 2010 3:16:43 PM
        Lease Expires . . . . . . . . . . : Tuesday, July 27, 2010 3:16:43 PM

Yes, this tells us a good bit actually.

Your router is able to handle DNS lookups so you *should* be able to resolve names using 192.168.1.1 but you also have a Verizon DNS server configured as secondary (68.238.64.12). 

DHCP appears to be working properly from the router as well. Though why Xubuntu is not getting an address is a bit strange. If you still wanted to set a static IP address in NetworkManager, I would suggest using one between 192.168.1.200 and 192.168.1.250. This would pretty much guarantee that you would not have a conflict with the addresses DHCP is offering. Your other static settings would mirror those above for subnet mask, default gateway, and DNS servers.

Cheers!

---

### Post by Gooddad56 on 2010-07-27
Thanks - so would I change the address in NetworkManager as well as the DNS server address? There are 2 places where that would make sense.

---

### Post by Gooddad56 on 2010-07-27
I just had my son change the address portion of the network connection to 192.168.1.210 and the DNS Server to 192.168.1.1 but when he tried to reach Google in Firefox it said "Address not found".
 
I then had him change the DNS Server to 192.168.1.210 and the same results.
 
I talked to Verizon and they recently changed the passwords to the router, so I will have to wait until tonight to reach the router. I am still a little unclear as to what I am going to find there and what I am supposed to do once I am there. Add a static address that matches the Xubuntu NetworkManager address?
 
Thanks

---

### Post by Iowan on 2010-07-27
If you start getting conflicting information, ignore me. ;)
You *shouldn't* need to tell the router about the static address... but you could configure a static lease (based on MAC address). Then you'd set the machine back to DHCP . For some reason, some routers seem to have problems with Ubuntu :confused:  I'm confused why 192.168.1.1 doesn't work for DNS.
 Network Manager is capable of using multiple DNS servers - I don't remember what the separation character is - I *thought* there was a post that suggested [space] [comma] [space], but I'll need to look for it...

---

### Post by Gooddad56 on 2010-07-28
In this screenshot there are other tabs: Wired, 802.1 Security, IPv6 
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164542&stc=1&thumb=1&d=1280117288[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=164542&d=1280117288")
Do I need to have specific entries on these other tabs?
 
On this tab, do I need to have something in *Search Domains*?
 
Thanks

---

### Post by Fire_Chief on 2010-07-28
All of that info looks good and *should* be working. :(

You could try changing the DNS addresses to any of the following

68.238.64.12  (verizon)
4.2.2.1   (AT&T)
208.67.222.222   (OpenDNS)
208.67.220.220   (OpenDNS)

Those should all work for resolving names on the Internet.

Cheers!

---

### Post by Gooddad56 on 2010-07-28
I've asked this before: there are two locations for addresses to be entered, as the connection address and the DNS server address. See this image:
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164542&stc=1&thumb=1&d=1280117288[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=164542&d=1280117288")
 
Do I enter your suggestions in both locations, in more than two locations?
 
Still not clear, so  little more detail please.
 
Thanks

---

### Post by Fire_Chief on 2010-07-28
The DNS server addresses should only be entered in the field labeled DNS Servers. The rest of the information above that looks fine.

---

### Post by Gooddad56 on 2010-07-28
Well - tried all 4 suggestions for DNS Server addresses and no luck.
 
Next steps or other places to look?

---

### Post by Gooddad56 on 2010-07-29
If I open Terminal, can I ping to an address that would give us some clues? I tried pinging 192.168.1.1 but that is just the router, if I'm not mistaken. It came back with results that kept coming and coming, changing just the "sequence" number, but filling the whole page.
 
What else can I check?

---

### Post by Gooddad56 on 2010-08-02
Fire Chief or Iowan - Any updates?

---

### Post by Iowan on 2010-08-02
Sorry - didn't mean to leave you hanging...
I need to do a quick review...
I usually just use **ping <address>** and CTRL-C to stop results, but the "better" way (I never remember) is to use **ping -c3 <address>** (c is for "count") to get only 3 "pings".

You've restarted networking - or rebooted after changing DNS servers?

---

### Post by Gooddad56 on 2010-08-03
How would I **restart** networking? I have not rebooted after every DNS attempt. 
Another curious thing: When I go to edit connections, the name is auto eth0 but at the right of that line is the word "never". What does that mean?

---

### Post by Gooddad56 on 2010-08-03
I think I figured out restarting - you click on the NetworkManager icon and it goes off, but then it re-connects automatically really quickly.
 
I pinged from Terminal using Ping <address> -c4 and I used every DNS address I could think of. I get anywhere from 25% dropped (a Verizon address) to mostly 75% dropped.
 
We reset the modem/router today, I get a green light on the wired port, indicting the linux box is connected (as NetworkManager tells me), but I cannot get any internet communication.
 
Next Steps?

---

### Post by Fire_Chief on 2010-08-03
> **Gooddad56 said:**
> How would I **restart** networking? I have not rebooted after every DNS attempt. 
Another curious thing: When I go to edit connections, the name is auto eth0 but at the right of that line is the word "never". What does that mean?

The "never" that you see is usually the time since you last used the connection. Not much to worry about with wired but sometimes handy with wireless connections.

So if you were pinging the DNS server IP address a la```
ping -c3 4.2.2.1
```
and still seeing between 25% and 75% loss, then either the Internet connection is inconsistent or you may have a bad hardware component in the mix.

Internet connection upstream (at the ISP). Possible. If you can ping your router (192.168.1.1) with no packet loss, then we can probably assume the hardware is good on your end. I would run a tracepath to one of the DNS servers (doesn't really matter which one)```
tracepath 4.2.2.1
```This is similar to traceroute which shows you the steps that your computer takes to reach a remote IP address. The first one you'll see should be your router (192.168.1.1). The next one and the one after that are what we want to focus on here. See if you can ping the second hop IP address with no packet loss and do the same with the third. If you have packet loss at either of those ping attempts, then there is a problem with the Verizon FIOS and they need to do service on the line.
As for hardware...if there were no problems reaching the above addresses with ping and tracepath, then your hardware is probably fine. However I'll list the aspects here just to be thorough.
Router/modem? Not likely since it seems to work well for you on your XP box.
Network cable? Possible. You could swap the cable with another one to test that easily.
Network Card? Also Possible. You could try a different network card or make an attempt with the wireless again.

Cheers!

---

