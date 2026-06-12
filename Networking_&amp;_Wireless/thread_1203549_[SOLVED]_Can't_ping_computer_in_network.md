---
title: "[SOLVED] Can't ping computer in network"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by f.constantino on 2009-07-03
Hello,

I am new to this forum (and forums in general) so I hope I'm not making any mistake posting this new thread.

I have searched the forum for a similar problem but was unable to find a suitable post, thus, I'm posting my own.

In my house I have 3 computers, my laptop, my mother's pc and my father's pc. My computer is connected to the internet through my modem/router but since my house has 2 floors (me being in the bottom one) my father decided to put a new router upstairs to manage the internet connection of the 2 computers there (the only ethernet cable connecting to my modem/router from upstairs is the ethernet cable of this other router).

Currently I am running ubuntu and both my parents are running windows xp and I can't seem to access their shared folders. When I tried to ping those computers I found out that I can't. I can ping my modem/router and my parents can ping the modem/router, if I access the router through the browser, he recognises all the pcs connected to it without any problem. (I have also disabled the firewall, AV in those computers, flushed my iptables and put their policies to ACCEPT. With all os these allowing anything I still can't ping from one computer to the other.

I have also tried to run "nmap -sP 192.168.1.0/24" (my ip being 192.168.1.64, my father's 192.168.1.65 and my modem/router 192.168.1.254) and all I get is:

> Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-07-03 19:07 WEST
Host fabio-laptop.lan (192.168.1.64) appears to be up.
Host dsldevice.lan (192.168.1.254) appears to be up.
MAC Address: xx:xx:xx:xx:xx:xx (Thomson Telecom Belgium)
Nmap done: 256 IP addresses (2 hosts up) scanned in 4.16 secondsAlso, if I run "ping carlos" (carlos being the computer name of my father's pc) I get:

> PING carlos.lan (192.168.1.65) 56(84) bytes of data.
^C
--- carlos.lan ping statistics ---
11 packets transmitted, 0 received, 100% packet loss, time 10040mswhich means the router is resolving the name correctly...

Surely I am doing something wrong, so any help would be appreciated.

Best regards,
Fábio Constantino

---

### Post by rocket777 on 2009-07-03
Well, many things can be a problem here. We would need to know how you setup your routers, both physically and config wise.

But here's a few items to consider (pretty wordy I see, but there's many details here), based on what does (and didn't originally) work for me.

1. I also have 2 routers, with all computers to my wireless router (wireless for laptop, but wired for all my desktop computers). Then this one router wan output goes to my 2nd router, a vonage router, which has the wan output gong to my cable modem.

2. Each of my 2 routers uses a separate subnet. My wireless router uses 192.168.1.1. My second one, a vonage voip router was setup to use 192.168.15.1 out of the box so I kept that. So the first router (farther from cable modem) specifies that the other router is it's default gateway and dns server. The vonage router, next to the cable modem, gets a dynamic setup from the cable box.

I don't know what happens if you have the same subnet for both, all I know is this method works for me.

3. In my local lan, however, I have setup all wired connections to be static ips. Since you almost certainly are NOT running a local dns server, then you probably won't be able to locate the windows file shares using names - UNLESS they are included in the ubuntu /etc/hosts file. You don't need static ip's for this, technically, since using dhcp USUALLY (but not always) assigns the same ip addresses to each computer on boot up. (The computer remembers it's last ip address and can request to keep using it on boot up - BUT this is not a guarantee).

This dhcp issue is why I use mostly static ip's on my lan. With my laptop, that still uses dhcp, it always gets the same address, so I just put that address (192.168.1.100) in the ubuntu hosts table. But - if I ever boot up some new system, and the laptop is currently not running ,that ip address might be assigned - especially if I have reset the routers recently. So, on occasion I have to go back and re-edit the ubuntu hosts file.

I don't know if it's really needed, but I also added all my static ip address into the windows hosts file (usually found under the drivers\etc directory on the system disk).

4. Windows file share tunnels over ip (the netbios stuff) and if you don't have a hosts entry, it will use an internet dns for lookup. I had a strange case where the name I use for my windows systems (e.g. dog, cat, mouse, etc.) would get looked up on the internet and it returned a value for these as though they were say, [www.dog.com](www.dog.com), etc.  

Thus when I tried to connect to a local windows file share, the connection went out to the internet instead and tried to connect to some unknown computer - which simply ignored the request - and so I would get a timeout error.

My ubuntu system DID see names on the local lan, and so I could actually see the computers in the network places window, but the lack of a hosts table entry led to the wrong ip address being used on the actual connection attempt.  Bottom line is that it's possible for ubuntu to see network names, but then not be able to resolve their ip address and so fail to connect.


5. When I first installed ubuntu, it must have discovered the host/ip of one of my windows systems and during the install added that to my hosts file. However, my other computers, not running at that instant, did not get setup with host table entries. So, I added them myself and things began to work. Before I added these, only the one computer that had been setup was connectible.

Hope this rambling helps some :)

---

### Post by swerdna on 2009-07-03
Here's a left-field thought: try enabling wins in the file /etc/nsswitch.conf. Locate this line:> hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4and add wins like this:> hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

---

### Post by f.constantino on 2009-07-03
Hello,

first of all, thank you for replying to my thread :)

(little correction on my previous post, the "router" I said my parents used is actually a switch.)
[swerdna]("http://ubuntuforums.org/member.php?u=326305"), I have done as you suggested, but the problem still exists.

as for rocket777, when I try to lookup my father's computer on the browser ("\\carlos") I also get redirected to a site on the internet, in this case wikipedia. I went to my etc/hosts file and I had this:

> 127.0.0.1    localhost
127.0.1.1    fabio-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhostsand added my father's computer in here:

> 127.0.0.1    localhost
127.0.1.1    fabio-laptop
192.168.1.65    carlos

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhostshowever, nothing has changed.

as for looking up the name I do this:

> root@fabio-laptop:/# nslookup carlos
Server:        192.168.1.254
Address:    192.168.1.254#53

Name:    carlos.lan
Address: 192.168.1.65and the IP is correct (I also got this result before changing the etc/hosts file).
As for the router configs, about 2 days ago I reset the router so I assume it went back to factory defaults (which I think it also had before because I never messed around it's configs.), all I did was set the username and password my ISP gave me to have internet access. (Before the reset was made, I was able to access my father's windows shared folders, could the problem come from the reset?)

Regards,

Fábio Constantino.

---

### Post by Iowan on 2009-07-03
Problem *could* be result of reset... Depending on router setup, each (router) port *could* be a separate subnet.  Can your parents' computers ping each other? Can they ping your machine? Is your network set up with static or DHCP addresses?  (If DHCP, is your modem/router also the server?

---

### Post by f.constantino on 2009-07-03
Both my parent's computers can ping each other, but they cannot ping mine. I believe all IP's are DHCP adresses and after checking my router's config, I have checked that he is the one acting as dhcp server and all of the ip's he offers are in the same subnet. I was wondering if it could be the little switch my parent's have (though I doubt it, since it was working before and I never touched it).

---

### Post by Iowan on 2009-07-04
Though not likely, I wonder if the Windows boxes are just keeping the last address they had. Can your parent's machines ping the router? (I presume yours can, too.) If they cannot ping the router, it *might* be the connection between the switch and router needs to be a different type of cable (crossover?)

---

### Post by dmizer on 2009-07-04
Please open [a terminal](https://help.ubuntu.com/community/UsingTheTerminal), run the following two commands, and post the output here.
```
sudo ufw status
```
and 
```
sudo iptables -L
```

---

### Post by f.constantino on 2009-07-04
Iowan, yes both my parent's computers can ping the router.
dmizer, 
> root@fabio-laptop:/# ufw status
Status: inactive> root@fabio-laptop:/# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhereiptables corresponds to my custom firewall:
> iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

#rules
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

iptables -A FORWARD -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -o wlan0 -m state --state RELATED,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -o eth0 -j ACCEPT
iptables -A OUTPUT -o wlan0 -j ACCEPTin this config I do not allow any computer to ping mine unless it is a reply to a request that I sent but I should still be able to ping their computers, anyway, I also tried with iptables flushed and policies ACCEPT:
> root@fabio-laptop:/# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destinationand still I get the same result, all ping the router, my parents ping each other, I cannot ping them, they cannot ping me. I really can't seem to understand where the problem is coming from, never had a situation like this before ](*,).

---

### Post by dmizer on 2009-07-04
Are you connected wirelessly? If so, are you absolutely 100% positive you're connected to your own wireless network and not a neighbors (with the same IP range).

Edit:
The following command may shed light on the above question.
```
sudo iwconfig
```

---

### Post by f.constantino on 2009-07-04
I'm using a wired connection.

---

### Post by dmizer on 2009-07-04
Please post a graphical reprsentation of how your network is physically layed out. Provide information like which computers are where, what IP they have, connection type (wireless/wired), and any other relevant information you can think of.

Something like

---

### Post by f.constantino on 2009-07-04
I made a textual description on my first post, but I'll try and make a rough picture of how things are setup and post it here in a bit.

Here it goes:
[IMG]http://h.imagehost.org/0898/homeNetworkLayout.jpg[/IMG]
I apologize for the bad quality of the picture, I don't have visio currently installed.

---

### Post by dmizer on 2009-07-05
That was perfect. Okay, which device (your laptop, or the router) is connected to the modem?

---

### Post by f.constantino on 2009-07-05
The router is a modem/router.

---

### Post by dmizer on 2009-07-05
Then, if all firewalls on all machines are disabled and you still can't ping, I haven't a clue.

---

### Post by f.constantino on 2009-07-05
I was thinking maybe some kind of ACL in the switch (though I think by default these come disabled).. dunno, I'll keep trying to find the "why" this isn't working. Thanks for the help everyone :) If I manage to fix it I'll post the problem/solution.

---

### Post by CaseSensative on 2009-07-05
I am not very good with Networks but..is Samba installed on your laptop?

---

### Post by dmizer on 2009-07-05
> **f.constantino said:**
> I was thinking maybe some kind of ACL in the switch (though I think by default these come disabled).. dunno, I'll keep trying to find the "why" this isn't working. Thanks for the help everyone :) If I manage to fix it I'll post the problem/solution.

Try plugging the laptop directly into the switch and see if that changes things.

---

### Post by Brandon Williams on 2009-07-05
Can all three of the user machines ping 192.168.1.254? And do they all have 192.168.1.254 listed as the default gateway? Check this with 'route -n', which will show the default route with 0.0.0.0 as the destination.

Next, check to make sure that you are getting arp responses for the other addresses. Run the ping command and then execute 'arp -n' to see if there is a valid mac address displayed, or if it says unresolved for the hardware address.

---

### Post by rocket777 on 2009-07-05
I don't suppose you have access to a HUB instead of that switch. When I was trying to debug my setup, I went to Frys and bought a cheap hub (though hubs, ironically can now cost more than switches). Then I hooked 2 of my computers (the 2 I was having problems communicating between) to the hub and ran ethereal on the windows machine. It could then see all the traffic in and out of the ubuntu machine. (I believe ethereal is now called wireshark).

This is how I discovered that my ubuntu machine was getting an ip address from an internet dns instead of locally.

I realize this could be difficult, and learning to use a sniffer can have a steep learning curve, but at this point, the only things I can think of involve either sniffing out what is going on or trying more combinations to get more data points.

Try all combination of hookups. As previously posted, try hooking the laptop to the switch, and also try hooking one of the xp machines to the router/modem in place of the laptop. And if all else fails, try a different switch if you can.

BTW, what is the brand/model of that modem/router?

---

### Post by f.constantino on 2009-07-05
Hello, my modem/router is a THOMSON ST546v6 [http://www.thomson.net/GlobalEnglish/Deliver/In-Home-Digital-Distribution/Telco-ISP/dsl-modems-gateways/residential_wired/thomson%20st546_v6/Pages/default.aspx]("http://www.thomson.net/GlobalEnglish/Deliver/In-Home-Digital-Distribution/Telco-ISP/dsl-modems-gateways/residential_wired/thomson%20st546_v6/Pages/default.aspx").
When directly connected to the switch, my laptop can ping, however this is not viable since I'dd have to be on the upper floor all the time. 
As suggested I tried to ping and check the arp tables on my computer. Showed this:
> root@fabio-laptop:~# arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.65                     (incomplete)                              eth0
192.168.1.254            ether   00:90:d0:0b:d2:3a   C                     eth0(192.168.1.65 being my father's computer and 192.168.1.254 the modem/router).
I am familiar with sniffers and I use wireshark for that effect. I also used it to see why I didn't receive the arp reply. After checking, I can see my computer sending:
>  Broadcast    ARP    Who has 192.168.1.65?  Tell 192.168.1.64 but no reply is received. When I checked my father's computer, he didn't get any requests for arp. As far as I know, the router only has to broadcast an arp request once since once the target computer replies the router saves that entry for future reference. I also assume the modem/router already knows the mac address of my father's computer since he has internet. Checking my father's computer, I can see periodical arp requests made by the router inquiring who has 192.168.1.65 (my father's computer ip), but I believe this is normal routine. Could there be a problem in the modem/router resolving the arp request ? I have checked it's configurations and can't find anything like that.

Ps: I have also tried to set my father's mac address manually on my laptop so now there is no arp request being sent from this computer, only ping requests, however, no ping reply is received. Modem/router not forwarding correctly ?

Ps2: Don't know if this helps but here is my switch (I don't think it's a hub): [http://www.smc.com/index.cfm?event=viewProduct&cid=6&scid=22&localeCode=EN_USA&pid=1432](http://www.smc.com/index.cfm?event=viewProduct&cid=6&scid=22&localeCode=EN_USA&pid=1432)

---

### Post by rocket777 on 2009-07-05
Well, you seem network savvy, so I will assume you ran a sniffer on your dad's computer to see that it did not in fact get the arp broadcast request. Even with a switch, broadcasts should be seen by every computer. But replies will usually be seen only on the computer that did the request - unless you use a hub instead of a switch - but I think you probably know this.

So, it does seem that the broadcast is not getting across the router. I wonder if you have to enable this on the router. Based on the spec sheet of that router (I couldn't find more than that), I can see that they might block that by default since they call this a multi-user router. However, this is just a guess.

Still, you might want to browse into the router and see if there's a setting that blocks broadcasts going from one connection on the router to another. 

You also might want to cross post at [http://forum.portforward.com/](http://forum.portforward.com/)

---

### Post by f.constantino on 2009-07-05
Well, I must say the problem is now fixed :)
After numerous attempts at getting this thing to work logically (not kicking it :p) I went to the router config page searching for anything that could lead me to the answer... I tried searching for anything like "block broadcast" or any weird firewall config and didn't find anything abnormal. In the process of looking through the router, it started to populate the current firewall table with the same rule a bunch of times (like it had entered a loop) and I decided to reset it again. And there it is... now everything works as it was intended. Don't know why but something in the previous reset (day I started this thread) went wrong...
I'm sorry for wasting everyone's time with such a silly issue (and even worst solution). Thank you for taking the time to help me :-D.

I've learned something with this though! Sometimes it is the machine's fault!

---

### Post by f.constantino on 2009-07-05
btw, (since I'm newbie at the forum I don't know) should I put some kind of tag on the thread name? like [SOLVED] or something?

---

### Post by dmizer on 2009-07-05
> **f.constantino said:**
> btw, (since I'm newbie at the forum I don't know) should I put some kind of tag on the thread name? like [SOLVED] or something?

You can just add a "solved" tag, but I've updated your thread :)

---

### Post by f.constantino on 2009-07-05
ok.
Thank you all again :)

---

### Post by rocket777 on 2009-07-05
We'll probably never know why your router wasn't working, but it sounds like something that it was remembering which was probably wrong, or changed. 

Whenever I have any sticky problems with my network, I reset everything and reboot all the computers. Switches remember mac addresses against physical ports and routers remember arp tables. Computers also remember their previous ip addresses if they use dhcp. A true reset needs to clear all of this, though I think the last dhcp ip address might be difficult to reset - it needs more than simply a reboot.

BTW, did you keep the host table entries? In my case, once I found the problem I temporarily removed the host table entries because I simply "had to know" :)

But we're all glad to hear you finally got it all working!

---

### Post by f.constantino on 2009-07-06
I kept the etc/hosts entry for my father's computer ip but now I tried to remove it and it still works, so it wasn't a problem in the name lookup or resolving the ip adress, just the router not wanting to cooperate :p

---

### Post by rocket777 on 2009-07-07
epilogue:


I had to see if I could also remove my hosts file entries and I finally did. Here's a few things I learned along the way.

1. you did a nslookup and you find a server at 192.168.1.254, which would indicate something on your local lan is serving up names. You also show your computer name as carlos.lan which might be related. My host names are simple, like dog, cat etc.

2. I found that nslookup does NOT use nsswitch.conf and always just uses dns lookups, which makes sense. I was referred to using getent instead. This does go through nsswitch.conf.

But in any case, if I did nslookup on dog, it would always find the internet ip, whereas getent was sensitive to hosts file entries.

3. I found a thread on using wins (with more info from dmizer), and so I added wins (but I put it right after files) and after installing 

apt-get install winbind

I could then remove my host table entries and I could see my windows shares on dog and the others. However, I did have to reboot ubuntu for the changes to be seen. 

So I think I may now understand why mine wasn't working, but I still don't really understand how yours IS working - except that your dns server at 192.168.1.254 seems to be doing what is needed for you, while I have no such service on my lan. Perhaps your router/modem is smarter than mine.


Untangling network configuration reminds me of my 50 foot extension cord's ability to tie itself in knots - that is it mystifies me still.

---

