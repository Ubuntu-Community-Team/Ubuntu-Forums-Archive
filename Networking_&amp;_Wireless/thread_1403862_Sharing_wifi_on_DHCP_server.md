---
title: "Sharing wifi on DHCP server"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by OzzyFreakDude2 on 2010-02-10
Hello
I have spent multiple hours each day for the past few days scowering the internet trying to figure out how to create a local network with a shared internet connection (run through the wifi on a laptop) in Ubuntu.  It was quite simple to do just that in windows, all I had to do was check the "share this connection" box.  I'm new with linux, but so far I like it much better than windows.  this is my only gripe.



Here's what I want to do:
Simply put, I want to create a local network with internet access from my wifi laptop, for the purpose of playing a few particular games and sharing files with a group of people at school.  Some of these games require an internet connection, and some just need a local connection.

I need the internet run through my laptop because it's the school wifi connection, which requires a user to log in with their school credentials.  Because of that, I doubt I'd be able to just get a router, connect it to the internet, and create a wireless network.  I want to do it in linux because it's just better, and also because the main game we're going to play lags horribly in Windows, with no excuse, even after trying all of the well-known workarounds, and on a computer fast enough to run it with all of the settings on high.  But it runs okay in linux.


I was successfully able to set up a DHCP server using dhcp3-server.  using this I'm able to assign clients to my network, assign an IP address, and ping the server to the client.  However, I'm noticing now that after my hours and hours of tinkering with it, my server can no longer ping the client by IP address (I was able to at first).  That's about all I was successful in doing.


Here's what I've already tried, as far as sharing the internet connection:
-Since I'm using Karmic, there's an option in network manager to make the internet connection "shared to other computers".  I tried this, and the other computer on the network couldn't access the internet.  Also, if I leave this option on and reboot, when it comes back up, it continually tries to connect, says its connected and subsequently disconnects right afterward, etc...all the while asking me for the key/password/etc (which is usually saved by network manager, and unlocked by simply typing my password).

-I tried using firestarter, which is supposed to automatically share an internet connection.  Whether it would have or not I don't know.  It won't start unless the network cable is plugged in and I'm connected to the LAN, and when it does start, I can't access the internet at all, whatsoever, not from the client nor the host.  It blocked a lot of Samba connections, all of which I added allow rules for.  Also, when I tried to find a website in firefox, for a minute it would show up in the active applications windows, but still wouldn't load anything.  Basically I added allow incoming rules both for firefox and for the smb connections it was blocking, until it wasn't blocking anything anymore, but even so, I still couldn't even ping google or load anything in firefox.  Then once or twice on reboot, if the network was connected, before I even started firestarter, I still couldn't access the internet.  This persisted until I uninstalled firestarter.


-On quite a few forums and guides, people suggested running specific console commands which modified the iptable and basically set it up as a nat, with masquerading and such.  I tried these, modifying the interface names with the ones I wanted to use, where applicable.  It didn't hurt anything, but it didn't allow my client computer access to the internet, either.

-in my searches, I came across a nice looking gui utility called network-config 0.2.  It manages all of your network configurations for you, and claims to set up a NAT connection.  In it, I set my default gateway device as eth0 (the lan nic), set my custom dns servers to the local dns server I have in dhcp3-server.  Under the eth0 tab, I set it to static ip, specified my static ip and netmask, and checked the NAT checkbox (which clears the gateway window, so I assume I should leave it blank).  Under the wlan0 tab, I didn't activate it, because under wifi settings, it doesn't support the list of encryptions that my school network uses, including wpa2 with username AND password.  I suspect that it might work if it supported the encryptions I need.  I tried it anyway, and needless to say, no internet on the host computer.

-The last thing, I've seen people mention using dnsmasq, and some saying you don't need it.  Whether it works for my situation or not, I don't know, because I couldn't find it, and it wasn't in the karmic repository.

And I've supplied as much information as I can.  Because of that, the post is already quite long, so attaching logs would make it any longer.  If anyone will specify which logs they want to see, I'd be happy to post them. I understand that with linux it will be a bit more manual, but this has just been ridiculous. I would greatly appreciate anybody's feedback, as I'm at my wits end with this issue.
thanks in advance

EDIT:
I've also tried setting up a wifi network (using both a usb wifi stick and my integrated intel wifi chip), to no avail.  The best I was able to do was set up a wifi ad-hoc network, which my dhcp3 server wouldn't assign any ip addresses to.  I also learned that it was probably due to the fact that neither of my wifi adapters support master mode

---

### Post by Iowan on 2010-02-10
Have you seen [this]("http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/") article?
There's a similar (ongoing) thread [here]("http://ubuntuforums.org/showthread.php?t=1397909"). I'm not suggesting you ask there, just see if any of the tips help your problem.

---

### Post by OzzyFreakDude2 on 2010-02-11
apparently the only reason I couldn't ping the clients was the firewall.  it's off and I can now ping them.

I read the post that you linked to, and I agree that he's in a very similar situation as I am, but his problem isn't solved yet, and nothing suggested thus far in the thread has helped me.  Thanks for the reference, though

I tried the tutorial you linked to, about setting the lan connection (I commented out my eth0 connection in networking\interfaces and set up the connection in networkmanager, had to stop my dhcp3 server).
It keeps popping up saying "wired network connection established".....but the popup keeps flashing up over and over like it keeps connecting and disconnecting.  when I try to ipconfig /renew from the windows 7 box I'm using as the client, the DHCP request times out.  It also says "An error occurred while releasing interface loopback pseudo-interface 1 : The system cannot find the file specified"
Maybe you can make sense of my log?  (if you want to see any other logs or returns from terminal commands, I'd be glad to do so, just let me know in particular what to post)
here is an excerpt from the syslog:

Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table nat --delete POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --out-interface eth0 --jump REJECT
Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --jump REJECT
Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 10:09:57 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 10:09:58 patrick-laptop ntpdate[20044]: adjust time server 91.189.94.4 offset 0.014062 sec
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) starting connection 'Wired connection 2'
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Feb 11 10:10:00 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Feb 11 10:10:00 patrick-laptop avahi-daemon[870]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.42.43.1.
Feb 11 10:10:00 patrick-laptop dnsmasq[1186]: reading /etc/resolv.conf
Feb 11 10:10:00 patrick-laptop dnsmasq[1186]: using nameserver 72.28.160.36#53
Feb 11 10:10:00 patrick-laptop dnsmasq[1186]: using nameserver 12.127.16.68#53
Feb 11 10:10:00 patrick-laptop dnsmasq[1186]: using nameserver 72.28.160.35#53
Feb 11 10:10:00 patrick-laptop avahi-daemon[870]: New relevant interface eth0.IPv4 for mDNS.
Feb 11 10:10:00 patrick-laptop avahi-daemon[870]: Registering new address record for 10.42.43.1 on eth0.IPv4.
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Policy set 'Auto MyInternet' (wlan0) as default for routing and DNS.
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --jump REJECT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --out-interface eth0 --jump REJECT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Starting dnsmasq...
Feb 11 10:10:01 patrick-laptop NetworkManager: <debug> [1265901001.081672] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --no-poll --except-interface=lo --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Feb 11 10:10:01 patrick-laptop NetworkManager: <debug> [1265901001.082414] nm_dnsmasq_manager_start(): dnsmasq started with pid 20098
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Activation (eth0) successful, device activated.
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Feb 11 10:10:01 patrick-laptop dnsmasq[20098]: failed to bind listening socket for 10.42.43.1: Address already in use
Feb 11 10:10:01 patrick-laptop dnsmasq[20098]: FAILED to start up
Feb 11 10:10:01 patrick-laptop NetworkManager: dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  (eth0): device state change: 8 -> 9 (reason 18)
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Activation (eth0) failed.
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Feb 11 10:10:01 patrick-laptop avahi-daemon[870]: Withdrawing address record for 10.42.43.1 on eth0.
Feb 11 10:10:01 patrick-laptop avahi-daemon[870]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.42.43.1.
Feb 11 10:10:01 patrick-laptop avahi-daemon[870]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Policy set 'Auto MyInternet' (wlan0) as default for routing and DNS.
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table nat --delete POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --out-interface eth0 --jump REJECT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --jump REJECT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 10:10:01 patrick-laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 10:10:02 patrick-laptop ntpdate[20160]: adjust time server 91.189.94.4 offset 0.003787 sec

---

### Post by mhgsys on 2010-02-11
I guess the easiest way is very clickable'

Meaning; You can share your internet connection with firestarter (firewall)

```
sudo apt-get install firestarter
```

when installed it's located at Applications> Internet, 

Not sure if it comes up in the first menu you'll have to configure,

But it will be a option anyway ;
 In firestarter: go to Edit>Preferences>Firewall>>Network Settings

edit: (You might want to get rid of/disable the previous dhcp3 settings etc you've made to make this way work,)

---

### Post by doas777 on 2010-02-11
many folks now suggest using gufw instead of firestarter, because it is an older project and no longer being maintained. I do prefer firestarter, but some problems have been cropping up with it in recent years.

you should be able to do what you need to in either gufw or firestarter.

---

### Post by OzzyFreakDude2 on 2010-02-11
like I said in my first post, I already tried firestarter, and with it running (and sometimes not even running, but simply by being installed), it completely breaks my internet connection.  Apparently it's a rare issue, as a google search for the issue turned up little to nothing.  But if you know how to get my internet working in firestarter, I'd be happy to install it again.

---

### Post by doas777 on 2010-02-11
> **OzzyFreakDude2 said:**
> like I said in my first post, I already tried firestarter, and with it running (and sometimes not even running, but simply by being installed), it completely breaks my internet connection.  Apparently it's a rare issue, as a google search for the issue turned up little to nothing.  But if you know how to get my internet working in firestarter, I'd be happy to install it again.

try gufw instead. I think it may run more like you expect. I always had to have firestarter loaded to apply the exception rules i gave it.

---

### Post by OzzyFreakDude2 on 2010-02-11
I installed gufw, and it doesn't appear to have any options for internet connection sharing.  

I'm allowed on the internet, but then again I'm currently on my laptop waiting for class to start, and therefore don't have another computer to test it with.  It very well might break the internet as soon as I connect to the LAN just like firestarter did.

---

### Post by doas777 on 2010-02-11
> **OzzyFreakDude2 said:**
> I installed gufw, and it doesn't appear to have any options for internet connection sharing.  

I'm allowed on the internet, but then again I'm currently on my laptop waiting for class to start, and therefore don't have another computer to test it with.  It very well might break the internet as soon as I connect to the LAN just like firestarter did.
you have to create IP range exceptions for the lans in question. once that is done, a simple route shoudl be all you need.

---

### Post by OzzyFreakDude2 on 2010-02-25
For those with the same issue, it had something to do with my Ubuntu installation.  I reinstalled on a clean format and it worked.

---

