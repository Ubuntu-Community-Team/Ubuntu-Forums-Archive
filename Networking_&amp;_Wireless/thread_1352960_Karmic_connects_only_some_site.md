---
title: "Karmic connects only some site"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by ghoracek on 2009-12-12
I have been using Ubuntu for a while on several machines and just installed 9.10 using wubi on an XP machine (something I've done on other machines). The install hung a long time on configuring apt, but finally completed. Using Firefox, I can only connect to certain sites and not others. I can connect to gmail and google, but not yahoo or the Motley Fool for example. I can ping them using the ping tool in network tools. On Google I can type in a search and get results, but none of the links will open -- they just time out. I can't get to any of the repositories (re: add new applications or update manager). I've uninstalled and installed three times and no joy. I went back to 9.04 (using wubi) and not only got the same behavior, but my display was not properly detected and I couldn't change the resolution (that looked like a hard battle). Any ideas? Give up on wubi and just partition with gparted and install normally? I've tried reading these forums, but it is not really possible to search them with a description of my problem -- same for google. One difference this is the first machine that had a dual core (Centreno) and wubi install amd64 version

---

### Post by chenxiaolong on 2009-12-12
Could you give more details on how it is being connected to the internet? I.e. what's the wireless/wired card model? It could be a driver problem or a hardware problem, based on the information you posted.

---

### Post by ghoracek on 2009-12-12
cable ISP
Linksys router
ethernet to Sis191 ethernet adapter (ASUS motherboard)

The mystery to me is that some sites work (google/gmail) all others don't.  The ethernet feed is working as is the wireless feed from the router -- I have 4 other computers connected and functioning normally.  I'm using one of those connections now.  

booting into XP and everthing works normally.  

I found one thread that said to change about:config in Firefox to block IPV6 (spelling?), but that didn't help.  

This is the only dual core computer I have tried Ubuntu on.  Wubi defaulted to installing AMD64 version of 9.10.

Mystery

---

### Post by ghoracek on 2009-12-12
Additional information.  I tried booting from a live Ubuntu 9.0 CD and got the same results -- connect to gmail and google only (there's a clue there, but I don't know what it means).

Next I booted from a live PuppyLinux CD which is surprisingly powerful.  It uses SeaMonkey as the browser, but the same behavior was seen.  Really quick connections to google and gmail; nothing to yahoo, microsoft, or Motley Fool as examples.  

I think I will try a wireless connection next if I can find a USB wireless fob.  But wireless is silly since the router is two feet away from the computer.  ;-)

glh

---

### Post by chenxiaolong on 2009-12-12
Could you try setting the DNS servers to 208.67.222.222 and 208.67.220.220? Those are OpenDNS's DNS servers at [http://www.opendns.com](http://www.opendns.com).

Right click the Network Manager icon > Edit Connections > Wired tab > Auto eth0 > Edit... > IPv4 Settings > Method: Automatic (DHCP) addresses only > DNS servers: 208.67.222.222;208.67.220.220 > Apply > Close > Restart

---

### Post by ghoracek on 2009-12-12
I made those changes and nothing changed.  Gmail loaded; google loaded; but no other site can be reached.  In network tools I can ping any tested site and get a reply.  For this post, I'm using Pupply linux on an acient laptop and connecting wirelessly to the same router and modem that I'm using with the desktop that only connects to google sites. Also remember I can connect flawlessly in WindowsXP mode. It's a puzzler;  I was really hoping to use this desktop for my wife who only used linux.

glh

---

### Post by chenxiaolong on 2009-12-12
Since you can ping the websites, the computer can reach them. I'm thinking this is a problem with Firefox. Try using epiphany or konqueror. You can download them from [http://packages.ubuntu.com](http://packages.ubuntu.com) on another computer can install them on the desktop.

---

### Post by ghoracek on 2009-12-12
Been chasing dependencies all night, but I finally got epiphany up and going.  Same result.  I can get google and gmail, but no other web site.  If I could figure out why those two sites work, then we'd have a clue.  I'll keep searching.

---

### Post by chenxiaolong on 2009-12-12
Dang, I really have no idea what can make it work then. The only other thing I can think of is to try another disto's live cd, like Puppy or DSL, to see whether it's a Linux or Ubuntu related problem.

---

### Post by ghoracek on 2009-12-12
Nope its a linux thing.  Tried Puppy linux (which has a lot of great tools) and got the same result.  However, it uses SeaMonkey which is in the Mozilla family -- that's why going the epiphany route was a good idea even though chasing down the dependencies was a bear.  I tried deleting the ethernet connection and re-install the drivers and still no go.

ifcongigure shows that I have an assigned IP address, so the router is doing its thing.  The MAC address is the same as in the network configure screen.  I tried two other live distros (Mint and SuSe) and get same result.  Must be a hardware thing?

---

### Post by MeKino on 2009-12-13
It's probably no consolation but I'm having problems too...

Ever since upgrading to karmic my internet connection has become patchier and patchier until now I can't connect to hardly anything!

I have a dual-boot system and under W everything works fine.
I'm still investigating the cause(s) but if anybody has any ideas they'd be welcome!

---

### Post by MeKino on 2009-12-13
Okay, I tried running Hardy Heron from a boot disc and **everything works fine!**

The problem is definitely with the upgrade.

I tried rolling back to version 2.6.31-14 but that still gives problems.

Any ideas?

How do I flag this up for correction??

Thanks

---

### Post by chenxiaolong on 2009-12-13
MeKino, I'm glad you got it working. Maybe you can use a newer version of Ubuntu when the next LTS is out:D. You can report the bug at [http://bugs.launchpad.net](http://bugs.launchpad.net).

ghoracek, could you try turning off the proxy setting in Firefox and also in Ubuntu (System > Preferences > Network Proxy)? Also, could you check the contents of /etc/hosts to see if it's something like this: 
```

127.0.0.1	localhost
127.0.1.1	yourcomputername

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by ghoracek on 2009-12-19
Solution determined, but final action not determined.  I borrowed a USB wireless adapter and I was immediately able to connect to the internet (besides just google and gmail).  The on-board ethernet adapter is to blame for the prior problems.  I have not decided whether to by a PCI ethernet adaptor or just to continue to use wireless -- but I am sure that the problem can be fixed either way.  Thanks for the help.

---

### Post by chenxiaolong on 2009-12-19
You're welcome. I'm glad you found a solution :D.

---

### Post by ghoracek on 2009-12-19
I was a little pre-mature.  While the USB wireless works (I'm using it now), the new PCI ethernet card that I purchased does not.  So I am back to not getting any connection by ethernet which is my preferred option (the new card works fine in WinXP).  Also Ubuntu is showing both adapters so I wonder if there is some confusion there (in Windows I just disabled the on-board adapter and used the new adaptor -- I'm looking for a way to do that in Ubunutu to reduce some of the complication in figuring this out).  This is baffling because Linux usually has no problems with ethernet adaptors.

glh

---

### Post by chenxiaolong on 2009-12-20
Can you disable the onboard ethernet in the BIOS?

---

### Post by ghoracek on 2009-12-20
Did that but still no internet via the PCI card.  The activity light next to the jack is not on and flashing as it should be if the card was active (it is lit in WinXP).  
My Ifconfig shows that the card's MAC address is recongnized (as does the network connections app).  Need some way to tell Ubuntu that the card is available. 

gary@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:25:86:d7:96:20  
          inet6 addr: fe80::225:86ff:fed7:9620/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by chenxiaolong on 2009-12-20
If your new card is eth1, then run

sudo ifconfig eth1 up #makes adapter active
sudo dhclient         #gives network card an ip

---

### Post by ghoracek on 2009-12-21
Thanks, but I think I solved the problem before I saw your post.  I found an obscure post somewhere that indicated that some adapters support Wake on Lan (WOL) under windows.  If this is not activated in Windows, then the card will not wake up for Ubuntu. I activated everything in the adapter properties dialog (WinXP) that said anything about WOL and also disabled the 'shut off to save power' dialog.  It now works in Ubuntu -- and I am posting with it now :-).  Thanks for staying with this; I would probably have given up trying to use Linux on this machine!

---

