---
title: "Can connect only to my router. No other wifi possible."
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by somethingcatchy on 2013-04-09
After extensive testing I can connect wirelessly to only my router at  home and I have no idea why. And it does not matter what the  configuration of the other router is. It can be a wide open public  router like at our laundromat, or it can be my friends encrypted home  connection (which BTW, is a different brand but set up to be basically  the same as mine), or it can be the walled garden of the captive portal  down at McD's.

I rolled my own distro. I had to. I've been in to  *nix for ~18 months. I moved from doze vm's to hardware ~12+ months ago. I  have 64Bit + Optimus. A little over a year ago the soultions for that combo required  almost guru skill level to implement. The only way I personally could figure out how to get it to  work was to start from a cli / mimimal install of 12.04. Plus, I really don't like unity. I wanted a  custom DE. I use the XFCE desktop without its program / toolset coupled  with all of the gnome tools and programs without its DE or shell. 

Over  time it has progressed to a hybrid of 12.04.2 + 12.10 + 13.10 + rolled  from source (~90%+ 12.04.2). I had no choice but to do that either. I'm trying to learn.  I need tools. All of the tools I need in the 12.04 repos are old and outdated  versions. The backend stuff in the 12.04 repos (like java and QT4) is  too old to support new versions of the tools I need. The backend stuff  in the 12.04 repos can not be upgraded to the newest versions because of  hundreds (if not thousands) of versioning and pinning error that cause  you to get stuck in a negative feedback loop and makes those modules  un-upgradable.

So now I have this monstrosity and it's light,  fast, powerful, full of hundreds of spiffy tools and will do everything I  want except travel. It's all on a laptop that can never leave home. 

I  would rate my skill level as intermediate at best. I'm no guru. And I'm  a brand spankin new, wet behind the ears, totally green noob at  networking (one of the things I'm trying to learn).

I'm assuming  that this is something stupid that I have done and don't even realize  it; I.E. something I didn't install correctly or at all or something I didn't configure properly or a conflict between the mismash of parts. However, I don't think the last one is likely. I originally built this monster on strictly 12.04 on another machine and used remastersys to move over to this machine. The original machine belongs to my wife. Even though it is strictly 12.04 it has the exact same problem.

I  had assumesd that the issue was due to not being able to resolve DNS; which we  couldn't until just recently. After reading about some security concerns  I had taken dnsmasq out of the system. I installed bind9. I could not get it  to resolve DNS for my connections; even though every diagnostic I ran  that I found on the web said it was working. So I took bind out,  reinstalled dnsmaq and ran in to the exact same problem.

So, I  finally dropped a ton of addresses in to my network interfaces: OpenDNS,  my router and the defualt IP addresses of the two dozen most popular  routers.

I can resolve DNS now, no problem. When I dig google it  shows the name server as OpendDNS and not my router. And even though I  told the network interfaces to run through the list of IPs for all of  the most popular routers to resolve DNS I still can't connect to any  router other than my own.

Another thing I've noticed: When I want  any VM (doze or *nix) to connect to another router I have to completely  separate it from the internal virtual network by "disconnecting"  (unchecking) its LAN card and plugging in a USB wifi card. Even with the  UB wifi card, if the LAN card is not "unplugged" the VM cannot connect  to the outside router.

I have chased this for weeks on end. I  have run every diagnostic I can find on the web and in my books.  Everything appears to be working, except for the fact that it's not!

Any help greatly appreciated.

---

### Post by somethingcatchy on 2013-04-09
Sitting here experimenting and I still think that this has something to wth me having some how fouled DNS resolution.

Since I can connect to wireless out in the world with a VM if I disable the VLAN card and since I can connect to my router from the host via wifi I tried to connect to my router from a doze VM via USB wifi card with the VLAN enabled.

I was able to connect to my router with the USB wifi card with the VLAN enabled. However, I cannot identify the routers network or connect to the internet through the router. But, my VLAN card is connected to the internet through my host wifi card. 

The ASUS control panel for the USB wifi card shows the DNS server on the Vnet at 10.0.2.3 with no DHCP server listed. 

But, the doze wireless control panel shows no info at all for a an IPv4 DNS server. It does however have three DNS servers listed for IPv6. But, I have IPv6 turned off in the host.

Putting OpenDNS addresses in the doze control panel for the USB wifi card made no difference.

The ASUS control panel for the card does not have a way to change DNS. So I deleted the config file and restarted the connection. It then kept the local Vnet address for DNS resolution and did not pick up the OpenDNS address for DNS resolution from doze. But, it also now has the local Vnet address listed as DCHP server where it had nothing listed before. Just as before, it will connect to my router with the VLAN enabled; however, it cannot identify the network nor connect to the internet.

So then I tried "splitting" DNS resolution by putting the Vnet address in the doze control panel (10.0.2.3) as the primary DNS and then an OpenDNS address as the secondary and got the exact same results.

Then I tried it with just the Vnet address as the primary DNS server with no secondary address in the doze control panel. And to my complete shock it actually worked. The ASUS doze control panel is now completely populated with the local Vnet address acting as both DNS and DHCP server and my router acting as the primary gateway.

Frankly I'm working on trial and error and do not understand why it worked.

Just for giggles I set my router to intentionally use a malformed local  network IP addresses to resolve DNS. I'm still able to resolve DNS just  fine in both the host and the doze VM because I can ping [www.google.com]("http://www.google.com")  from both with no issue. Of course dig tells me it's using OpenDNS to resolve addresses and doze is using the Vnet to do it. In the doze VM IPconfig shows the wireless gateway as the router's IP and the  LAN gateway as a Vnet address.

So, since the VLAN can resolve IP adresses  from 10.0.2.2 and the host LAN is resolving from OpenDNS from both eth0 and wlan0 then why will a VM guest wlan not resolve DNS until I specifically tell it to use the Vnet and why won't my host wlan resolv DNS with any router other than mine; even though I have it set to use external DNS resolution and everything still works just fine even though I've made it impossible for my router to resolve DNS?

There's obviously some kind of issue with wlan0 DNS resolution on the host / guests? But I'll be danged if I know what it is. Do I have a misconfigured IPTables FW that is preventing local, remote and Vnet DNS resolution on on wlan0 on the host and guests? Is this because I'm resolving remotely and never could get it to resolve locally? Is it a combo of the two?

---

### Post by somethingcatchy on 2013-04-09
Note: I just realized that all of the above experiments were done with a LAN connection established on the host. So I turned it off. With the host LAN disconnected the doze guest cannot resolve the name of the routers network from the USB wifi via the Vnet address ***_even if a wlan0 host wifi connection is established!_*****

I have DNS resolution disabled in my router. So how is it I can connect to my router via wifi in my host without the router resolving DNS when the host wlan0 can't resolve DNS for the VNET, but I can't connect to any other router at all?

---

### Post by papibe on 2013-04-09
Hi somethingcatchy.

How do you set up your network?
Do you have network-manager installed, or do you set it using /etc/network/interfaces?

Regards.

---

### Post by somethingcatchy on 2013-04-09
Both actually. I have network manager installed and I could connect to my router with no issue because I have it set up to resolve DNS. But, when I started trying to travel with my laptop I couldn't connect to any other router. After lot's of reading and experimentation I became convinced that it was due to the fact that I was not resolving DNS at all on the lasptop itself. I had removed dnsmasq after reading about some security concerns. I installed bind 9, but never got it working properly. Convinced that the problem was DNS related I took bind out and put DNSmasq back. I don't think it's working properly either? So, in order to enable my system to be able to resolve DNS in at least some way, shape or form I added OpenDNS addresses to network interfaces. Now it appears I can resolve DNS on eth0, but not wlan0? :confused:

---

### Post by somethingcatchy on 2013-04-09
OK? I might have found part of the issue? Just for giggles I tired reinstalling network-manager, network-manager-gome, dnsmasq-base and installing dnsmasq and then running dpkg-reconfigure on all of them. I got this error on dnsmasq: "resolvconf: Error: /etc/resolv.conf isn't a symlink, not doing anything."

---

### Post by papibe on 2013-04-09
Try this then:
```
sudo mv /etc/resolv.conf /etc/resolv.conf.old

sudo ln -s /etc/resolv.conf /run/resolvconf/resolv.conf

sudo service network-manager restart
```
Let us know how it goes.
Regards.

---

### Post by somethingcatchy on 2013-04-09
Well, I wish I had caught you before I went digging. I tried reinstalling resolvconf and then ran dpkg-reconfigure on it. I followed the prompts and told the system to create the new dynamic link and to append the old network interfaces file to the new dynamic file and that fouled things up a lot.

     Now my system runs like a snail and all connections time out to the outside world. (I'm on my wife's computer now.) Sudo takes forever to respond, so does anything that tries to connect to the localhost. I can ping, dig and host the localhost but they all run slow. I can't resolve anything outside my own local host. My DNS name server is now local host in /etc/resolv.conf (I restored it.) I've tried re-running sudo dpkg-reconfigure resolvconf and rebooting / restarting services to no avail.

   I think I have mulitple issues here.  

I have webmin installed. When I was trying to fix things before I tried adding addresses directly to the interfaces file and my system would become super slow. When I used webmin to add the addresses to interfaces my system was fast, but the addresses were not recorded in interfaces; at least not that I could see. Also, none of the appended addresses from the old interfaces file were carried over to /etc/resolvconf/resolv.conf.d/tail as the dpkg prompts said they would be.  This plus the fact that when I used webmin on my wife's computer to add  the interfaces those addresses were actually recorded in the interfaces  file leads me to believe that the /etc/network/interfaces file on my  system has some kind of corruption in it.

   So now I need to figure out a way to repair that with no direct net access.  Once I fix that corruption then I think I need to fix resolvconf.  But, since I doofed around before I saw your message your second  command just returned an error saying the link already existed. 

   Any ideas on how to fix a possible corruption in the interfaces file without a direct net connection?

I'm thinking I'll pull a copy of the folder and file off of my wife's machine and delete mine / copy her's over.

---

### Post by somethingcatchy on 2013-04-10
Well pulling the folder and files from etc/network off of her system didn't fix anything. And I realized that since I had just run everything it would still be in my apt cache, so I reinstalled everything with aptitude and ran dpkg-reconfigure on everything. Of course when I reconfigure resolvconf now I get asked no questions because the network interfaces file is not populated any more. But, even though everything appears to go right all of my connections to the outside world still time out and my system is very slow.

---

### Post by papibe on 2013-04-10
Could you post the result of these commands?
```
cat /etc/network/interfaces

cat /etc/resolv.conf

grep dnsmasq /etc/NetworkManager/NetworkManager.conf

cat /var/run/nm-dns-dnsmasq.conf
```
Regards.

---

### Post by somethingcatchy on 2013-04-10
Everything came back as OOB / default except the last one. I don't have a nm-dns-dnsmasq.conf file in /var/run, neither does my wife's machine. So this is probably something I've missed when building.

 BTW, the file did not get created on my machine just now when I installed / reinstalled / dpkg-reconfigured dnsmasq. Is this a sign of a deeper issue / corruption? Or is this file generated by a plugin like network-manager-openvpn or network-manager-openvpn-gnome? If so can you give me the exact package name so I can DL it?

And, digging in my machine I've blown up DNS as it stands with what I did above. But, only DNS and not the whole network stack. I can connect to a resolved external host.

---

### Post by somethingcatchy on 2013-04-10
```
adam@adam-L502X:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


adam@adam-L502X:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
adam@adam-L502X:~$ grep dnsmasq /etc/NetworkManager/NetworkManager.conf
dns=dnsmasq
adam@adam-L502X:~$ cat /var/run/nm-dns-dnsmasq.conf
cat: /var/run/nm-dns-dnsmasq.conf: No such file or directory
```

Like I said: It all came back default execpt for the last one. That file does not exist on my machine. How does it get created and what creates it?

---

### Post by papibe on 2013-04-10
Try creating the file by yourself to see what happens.

You may try OpenDNS:
```
sudo bash -c 'echo "server=208.67.222.222" > /var/run/nm-dns-dnsmasq.conf'
```
Or Google DNS:
```
sudo bash -c 'echo "server=8.8.8.8" > /var/run/nm-dns-dnsmasq.conf'
```
Regards.

---

### Post by somethingcatchy on 2013-04-10
Thank you very, very much. 

On first test that seems to have fixed the problems. I can resolve DNS now through my localhost. Dig, host and ping [www.google.com]("http://www.google.com") all work now with dig showing my host as the name server. And the issue with sudo being slow to respond was also solved. (I didn't realize that it made a local server call.) And, an issue with Thunar has been resolved as well. It is now *quickly* resolving my local samba location in the side bar; rather than taking several minutes to "figure it out". 

 I need to do some testing with my virtual network and with wifi connections out in the world to see if this has fixed all of my DNS resolution issues. If so I'll be back in a few hours to mark the thread as solved and apply the repairs to my wife's machine as well.  

If not I'll be asking more questions.  

Thank's for the help!

---

### Post by somethingcatchy on 2013-04-10
OK, I didn't have to get very far in testing to hit the first snag: I still can't resolve DNS on wlan0. 

If I have the cat5 from my router plugged in to eth0 I can resolve DNS / navigate the web. 

If eth0 is attached to the router I can make a wlan0 / wifi connection from my host to my router. 

If eth0 is not attached to the router via hard line I cannot connect my host via wlan0 to the router to establish a wifi connection. 

This tells me that I am resolving DNS on eth0 but not resolving DNS on wlan0. (Yes, no, different issue?)

So, what configuration file am I missing for this one?

And, BTW, yes the router is set up to resolve DNS for its clients. And I have verified that it is working. We have a droid tablet that cannot resolve DNS locally and is set up by the manufacturer to rely on the gateway for DNS resolution. It is navigating the web and connecting to the router with no issue.

---

### Post by somethingcatchy on 2013-04-10
Strike that last post. I've touched tons of stuff trying to fix this problem. I just realized that I had changed some of the connection parameters in the config file of my wifi home connection. When I fixed them I was able to connect on wlan0 without eth0 plugged in with no issue.

So now I'm off to do more testing.

---

### Post by papibe on 2013-04-10
Check if there's a custom setting on your wireless connection. You could go to
```
'Network Connections' -> 'Wireless' tab -> wlan0 or the name of your wireless network.
```
Alternatively, you co go to this directory:
```
/etc/NetworkManager/system-connections
```
And check the content of the file there. It should be name something like "Wireless-Network-name connection 1" or similar. For instance:
```
sudo more /etc/NetworkManager/system-connections/Wireless-Network-name\ connection\ 1
```
Regards.

---

### Post by somethingcatchy on 2013-04-10
Two steps forward and one step back:

I can only connect to my router on eth0 or wlan0 if I mark them as "connect automatically" in the Network Connections GUI control panel and then reboot my machine?

---

### Post by papibe on 2013-04-10
When an interface is set not to connect automatically (field uncheck), an entry is set on /etc/NetworkManager/NetworkManager.conf.

It has this format:
```
no-auto-default=63:D3:DA:15:A5:BC,
```
Where the string is the MAC address of the interface.

May be the 'Network Connections' tool is not properly writing those changes to the file?  Or settings are not being read at boot? Permissions? (here it has 644 permissions).

Just some thoughts.
Regards.

---

### Post by somethingcatchy on 2013-04-10
644 = rw owner /r users in group owner /r everyone? (root:root) If so then it's correct.

My eth0 / LAN MAC was set to no-auto-default, even though it is currently checked for auto connect. So I removed it.

And my wife's LAN or wlan MAC got copied over to no-auto-default when I extracted this build from her system with remastersys. So I removed it.

And my wlan0 was not set for no-auto-default even though I unchecked the GUI box, so I added it.

Rebooted and no difference.

(It appears those values are not being written and even setting them manually is not making a difference?)

So I took no-auto-default out completely and deleted both the wired and wireless confg profiles in Network Connections GUI.

Then I rebooted and pluged in eth0 after logging in. The system auto configured a new auto-connect profile. But could not actually connect to it until I had rebooted again. I also couldn't connect to wlan0 either until after reboot.

Even

 ```
sudo service network-manager stop
sudo service resolvconf stop
sudo service dnsmasq stop
sudo service dnsmasq start
sudo service resolvconf start
sudo service network-manager start
```

made no difference, only a reboot will establish the connections.

I think both connections are timing out. They request an IP address for ~60 seconds and then disconnect.

Is there a command (or is one needed) to tell the dnsmasq network manager plugin to run in the background as an always on daemon? I ask because pstree shows dnsmasq running, but it is forking from init; not network-manager.

And / or should I pin hole my firewall to / from localhost on port 53 to let dnsmasq resolve a connection after boot? I ask because even though webmin runs as a local server I had to pinhole the service to be able to log in to the localhost.

BTW, I'm not sure if this means anything or not but I still don't have a nm-dns-dnsmasq.conf in var/run even though

```
sudo bash -c 'echo "server=208.67.222.222" /var/run/nm-dns-dnsmasq.conf
``` 

caused DNS resolution to start working (at least at boot). And, if I try to physically create the file in the root GUI it will disappear. As a matter of fact I just ran a comprehensive search that said that there is no file by that name anywhere on my system?

---

### Post by somethingcatchy on 2013-04-11
I'm starting to think this is no longer a DNS issue and is something else; maybe a permissions issue?

I just tried manually setting my routers IP as the name server in the network connections GUI and I still could not connect to it on wlan0 until I rebooted with the connection set to auto.

---

### Post by somethingcatchy on 2013-04-11
OK, so I guess it's not a permission issue?

```
adam@adam-L502X:~$ nmcli con up id Home-PC_Network
Active connection state: activating
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/0
state: unknown
Error: Connection activation failed.
adam@adam-L502X:~$ sudo nmcli con up id Home-PC_Network
[sudo] password for adam: 
Active connection state: activating
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/1
state: unknown
Error: Connection activation failed.
adam@adam-L502X:~$ sudo -i
root@adam-L502X:~# nmcli con up id Home-PC_Network
Active connection state: activating
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/2
state: unknown
Error: Connection activation failed.
```

Are there any tools for connecting from cli that are more verbose than nmcli? Or a set of logs I should be checking for error messages?

---

### Post by somethingcatchy on 2013-04-11
In answer to my own question:

```
grep -i networkmanager /var/log/syslog > ~/test.txt
```

So now to try and figure out what it all means. Any help greatly appreciated.

Seems like the first place I should start looking is:

```
Apr 11 00:28:38 adam-L502X NetworkManager[1838]: <warn> dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
```

```
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> Activation (wlan0/wireless): connection 'Home-PC_Network' has security, and secrets exist.  No new secrets needed.
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> Config: added 'ssid' value 'Home-PC_Network'
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> Config: added 'scan_ssid' value '1'
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> Config: added 'psk' value '<omitted>'
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> Config: set interface ap_scan to 1
Apr 10 22:01:15 adam-L502X NetworkManager[1844]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): supplicant interface state: associating -> associated
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Home-PC_Network'.
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> dhclient started with pid 12654
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): DHCPv4 client pid 12654 exited with status 1
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <warn> Activation (wlan0) failed for access point (Home-PC_Network)
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <warn> Activation (wlan0) failed.
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 10 22:01:16 adam-L502X NetworkManager[1844]: <info> (wlan0): supplicant interface state: completed -> disconnected
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> (eth0): carrier now ON (device state 20)
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Auto-activating connection 'Wired connection 1'.
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) starting connection 'Wired connection 1'
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> dhclient started with pid 14195
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> (eth0): DHCPv4 client pid 14195 exited with status 1
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Apr 10 22:02:05 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Apr 10 22:02:25 adam-L502X NetworkManager[1844]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 10 22:02:25 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 10 22:02:25 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 10 22:02:25 adam-L502X NetworkManager[1844]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 10 22:02:25 adam-L502X NetworkManager[1844]: <warn> Activation (eth0) failed.
Apr 10 22:02:25 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 10 22:02:25 adam-L502X NetworkManager[1844]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 10 22:02:25 adam-L502X NetworkManager[1844]: <info> (eth0): deactivating device (reason 'none') [0]
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Auto-activating connection 'Wired connection 1'.
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) starting connection 'Wired connection 1'
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> dhclient started with pid 14961
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 10 22:02:28 adam-L502X NetworkManager[1844]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 10 22:02:29 adam-L502X NetworkManager[1844]: <info> (eth0): DHCPv4 client pid 14961 exited with status 1
Apr 10 22:02:29 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Apr 10 22:02:29 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Apr 10 22:02:29 adam-L502X NetworkManager[1844]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Apr 10 23:31:10 adam-L502X kernel: [   23.388329] type=1400 audit(1365658268.071:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=897 comm="apparmor_parser"
Apr 10 23:31:10 adam-L502X kernel: [   23.388410] type=1400 audit(1365658268.071:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1399 comm="apparmor_parser"
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: init!
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: update_system_hostname
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPluginIfupdown: management mode: unmanaged
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/net/eth0, iface: eth0)
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: end _init.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    Ifupdown: get unmanaged devices count: 0
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: (36120368) ... get_connections.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    SCPlugin-Ifupdown: (36120368) ... get_connections (managed=false): return empty list.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile: parsing AirVPN_US-Vega_UDP-443 ... 
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile:     read connection 'AirVPN_US-Vega_UDP-443'
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile: parsing AirVPN_US-Librae_UDP-443 ... 
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile:     read connection 'AirVPN_US-Librae_UDP-443'
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile: parsing Home-PC_Network ... 
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile:     read connection 'Home-PC_Network'
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile: parsing AirVPN_US-Octantis_UDP-443 ... 
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile:     read connection 'AirVPN_US-Octantis_UDP-443'
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile: parsing AirVPN_GB-Bootis_UDP-443 ... 
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    keyfile:     read connection 'AirVPN_GB-Bootis_UDP-443'
Apr 10 23:31:10 adam-L502X NetworkManager[1838]:    Ifupdown: get unmanaged devices count: 0
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> trying to start the modem manager...
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> Networking is enabled by state file
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): using nl80211 for WiFi device control
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): now managed
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): bringing up device.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): preparing device.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <warn> failed to allocate link cache: (-10) Operation not supported
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (eth0): carrier is OFF
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (eth0): now managed
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (eth0): bringing up device.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (eth0): preparing device.
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/net/eth0
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> wpa_supplicant started
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <info> (wlan0): supplicant interface state: ready -> inactive
Apr 10 23:31:10 adam-L502X NetworkManager[1838]: <warn> Trying to remove a non-existant call id.
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> (eth0): carrier now ON (device state 20)
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Auto-activating connection 'Wired connection 1'.
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) starting connection 'Wired connection 1'
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> dhclient started with pid 2151
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 10 23:31:12 adam-L502X NetworkManager[1838]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 10 23:31:13 adam-L502X NetworkManager[1838]: <info> (eth0): DHCPv4 state changed preinit -> bound
Apr 10 23:31:13 adam-L502X NetworkManager[1838]: <info>   address 192.168.1.4
Apr 10 23:31:13 adam-L502X NetworkManager[1838]: <info>   prefix 24 (255.255.255.0)
Apr 10 23:31:13 adam-L502X NetworkManager[1838]: <info>   gateway 192.168.1.1
Apr 10 23:31:13 adam-L502X NetworkManager[1838]: <info>   nameserver '192.168.1.1'
Apr 10 23:31:13 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 10 23:31:13 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Apr 10 23:31:14 adam-L502X NetworkManager[1838]: <info> DNS: starting dnsmasq...
Apr 10 23:31:14 adam-L502X NetworkManager[1838]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Apr 10 23:31:14 adam-L502X NetworkManager[1838]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 10 23:31:14 adam-L502X NetworkManager[1838]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Apr 10 23:31:14 adam-L502X NetworkManager[1838]: <info> Activation (eth0) successful, device activated.
Apr 10 23:31:14 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 10 23:31:14 adam-L502X NetworkManager[1838]: <warn> dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
Apr 10 23:31:14 adam-L502X NetworkManager[1838]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Apr 10 23:31:19 adam-L502X NetworkManager[1838]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 10 23:31:20 adam-L502X NetworkManager[1838]: <info> (eth0): carrier now ON (device state 100)
Apr 10 23:31:32 adam-L502X NetworkManager[1838]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 10 23:31:32 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 10 23:31:32 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 10 23:31:32 adam-L502X NetworkManager[1838]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) starting connection 'Home-PC_Network'
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Activation (wlan0/wireless): connection 'Home-PC_Network' has security, and secrets exist.  No new secrets needed.
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Config: added 'ssid' value 'Home-PC_Network'
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Config: added 'scan_ssid' value '1'
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Config: added 'psk' value '<omitted>'
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> Config: set interface ap_scan to 1
Apr 11 00:28:26 adam-L502X NetworkManager[1838]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> (wlan0): supplicant interface state: associating -> associated
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Home-PC_Network'.
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> dhclient started with pid 2314
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 11 00:28:27 adam-L502X NetworkManager[1838]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 11 00:28:36 adam-L502X NetworkManager[1838]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 11 00:28:36 adam-L502X NetworkManager[1838]: <info>   address 192.168.1.8
Apr 11 00:28:36 adam-L502X NetworkManager[1838]: <info>   prefix 24 (255.255.255.0)
Apr 11 00:28:36 adam-L502X NetworkManager[1838]: <info>   gateway 192.168.1.1
Apr 11 00:28:36 adam-L502X NetworkManager[1838]: <info>   nameserver '192.168.1.1'
Apr 11 00:28:36 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 11 00:28:36 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 11 00:28:37 adam-L502X NetworkManager[1838]: <info> DNS: starting dnsmasq...
Apr 11 00:28:37 adam-L502X NetworkManager[1838]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Apr 11 00:28:38 adam-L502X NetworkManager[1838]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Apr 11 00:28:38 adam-L502X NetworkManager[1838]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 11 00:28:38 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) successful, device activated.
Apr 11 00:28:38 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 11 00:28:38 adam-L502X NetworkManager[1838]: <warn> dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
Apr 11 00:28:38 adam-L502X NetworkManager[1838]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Apr 11 00:28:47 adam-L502X NetworkManager[1838]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 11 00:28:47 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 11 00:28:47 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 11 00:28:47 adam-L502X NetworkManager[1838]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 11 00:30:59 adam-L502X NetworkManager[1838]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 11 00:31:03 adam-L502X NetworkManager[1838]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Apr 11 00:31:03 adam-L502X NetworkManager[1838]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Apr 11 00:31:04 adam-L502X NetworkManager[1838]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2151
Apr 11 00:31:04 adam-L502X NetworkManager[1838]: <info> DNS: starting dnsmasq...
Apr 11 00:31:04 adam-L502X NetworkManager[1838]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Apr 11 00:31:04 adam-L502X NetworkManager[1838]: <info> Policy set 'Home-PC_Network' (wlan0) as default for IPv4 routing and DNS.
Apr 11 00:31:04 adam-L502X NetworkManager[1838]: <info> Policy set 'Home-PC_Network' (wlan0) as default for IPv4 routing and DNS.
Apr 11 00:31:04 adam-L502X NetworkManager[1838]: <warn> dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
Apr 11 00:31:04 adam-L502X NetworkManager[1838]: <info> (eth0): writing resolv.conf to /sbin/resolvconf

```

Not the whole log, but hopefully enough. I don't think I have permissions for attachments yet?

---

### Post by papibe on 2013-04-11
What Ubuntu version are you actually using?

In 12.04 there is (or used to be) a bug that does not allow running dnsmasq (package by itself), because how was the network-manager dnsmasq plugin originally set up.

To my knowledge, that was fixed on 12.10, but if you are running 12.04 I would uninstall dnsmasq and try to resolve the basic network problems first.

Regards.

---

### Post by somethingcatchy on 2013-04-11
OK, I think I'm making some progress here. I uninstalled "dnsmasq" and left "dnsmasq-base" installed and configured. I am still resolving DNS only at boot. But I am no longer getting the same error message as above and pstree now shows dnsmaq as forking from network manager and not init.

This is the connection log for today after I corrected the issue with dnsmasq. I'm still not connecting, now to figure out why?


```
Apr 11 13:56:27 adam-L502X kernel: [    8.004721] type=1400 audit(1365710184.672:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1290 comm="apparmor_parser"
Apr 11 13:56:27 adam-L502X kernel: [    8.004731] type=1400 audit(1365710184.672:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1092 comm="apparmor_parser"
Apr 11 13:56:27 adam-L502X kernel: [    8.004738] type=1400 audit(1365710184.672:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1093 comm="apparmor_parser"
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> NetworkManager (version 0.9.4.0) is starting...
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> VPN: loaded org.freedesktop.NetworkManager.openvpn
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> DNS: loaded plugin dnsmasq
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: init!
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: update_system_hostname
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPluginIfupdown: management mode: unmanaged
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/net/eth0, iface: eth0)
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: end _init.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    Ifupdown: get unmanaged devices count: 0
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: (14006064) ... get_connections.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    SCPlugin-Ifupdown: (14006064) ... get_connections (managed=false): return empty list.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile: parsing AirVPN_US-Vega_UDP-443 ... 
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile:     read connection 'AirVPN_US-Vega_UDP-443'
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile: parsing AirVPN_US-Librae_UDP-443 ... 
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile:     read connection 'AirVPN_US-Librae_UDP-443'
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile: parsing Home-PC_Network ... 
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile:     read connection 'Home-PC_Network'
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile: parsing AirVPN_US-Octantis_UDP-443 ... 
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile:     read connection 'AirVPN_US-Octantis_UDP-443'
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile: parsing AirVPN_GB-Bootis_UDP-443 ... 
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    keyfile:     read connection 'AirVPN_GB-Bootis_UDP-443'
Apr 11 13:56:30 adam-L502X NetworkManager[2117]:    Ifupdown: get unmanaged devices count: 0
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> trying to start the modem manager...
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> Networking is enabled by state file
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (wlan0): using nl80211 for WiFi device control
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (wlan0): now managed
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (wlan0): bringing up device.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (wlan0): preparing device.
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <warn> failed to allocate link cache: (-10) Operation not supported
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (eth0): carrier is OFF
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (eth0): now managed
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 11 13:56:30 adam-L502X NetworkManager[2117]: <info> (eth0): bringing up device.
Apr 11 13:56:31 adam-L502X NetworkManager[2117]: <info> (eth0): preparing device.
Apr 11 13:56:31 adam-L502X NetworkManager[2117]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 11 13:56:31 adam-L502X NetworkManager[2117]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/net/eth0
Apr 11 13:56:31 adam-L502X NetworkManager[2117]: <info> wpa_supplicant started
Apr 11 13:56:31 adam-L502X NetworkManager[2117]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 11 13:56:31 adam-L502X NetworkManager[2117]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 11 13:56:31 adam-L502X NetworkManager[2117]: <info> (wlan0): supplicant interface state: ready -> inactive
Apr 11 13:56:31 adam-L502X NetworkManager[2117]: <warn> Trying to remove a non-existant call id.
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) starting connection 'Home-PC_Network'
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Activation (wlan0/wireless): connection 'Home-PC_Network' has security, and secrets exist.  No new secrets needed.
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Config: added 'ssid' value 'Home-PC_Network'
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Config: added 'scan_ssid' value '1'
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Config: added 'psk' value '<omitted>'
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> Config: set interface ap_scan to 1
Apr 11 13:58:27 adam-L502X NetworkManager[2117]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 11 13:58:28 adam-L502X NetworkManager[2117]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 11 13:58:28 adam-L502X NetworkManager[2117]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 11 13:58:28 adam-L502X NetworkManager[2117]: <info> (wlan0): supplicant interface state: associating -> associated
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Home-PC_Network'.
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> dhclient started with pid 8156
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> (wlan0): DHCPv4 client pid 8156 exited with status 1
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Apr 11 13:58:30 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <warn> Activation (wlan0) failed for access point (Home-PC_Network)
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <warn> Activation (wlan0) failed.
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 11 13:58:50 adam-L502X NetworkManager[2117]: <info> (wlan0): supplicant interface state: completed -> disconnected
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> (eth0): carrier now ON (device state 20)
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Auto-activating connection 'Wired connection 1'.
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) starting connection 'Wired connection 1'
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> dhclient started with pid 8950
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> (eth0): DHCPv4 client pid 8950 exited with status 1
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Apr 11 13:58:57 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Apr 11 13:59:17 adam-L502X NetworkManager[2117]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 11 13:59:17 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 11 13:59:17 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 11 13:59:17 adam-L502X NetworkManager[2117]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 11 13:59:17 adam-L502X NetworkManager[2117]: <warn> Activation (eth0) failed.
Apr 11 13:59:17 adam-L502X NetworkManager[2117]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 11 13:59:17 adam-L502X NetworkManager[2117]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 11 13:59:17 adam-L502X NetworkManager[2117]: <info> (eth0): deactivating device (reason 'none') [0]
```

EDIT___________________

I'm thinking this is probably the current issue:


```
device state change: unmanaged -> unavailable (reason 'managed')
```

---

### Post by somethingcatchy on 2013-04-11
> **papibe said:**
> What Ubuntu version are you actually using?

In 12.04 there is (or used to be) a bug that does not allow running dnsmasq (package by itself), because how was the network-manager dnsmasq plugin originally set up.

To my knowledge, that was fixed on 12.10, but if you are running 12.04 I would uninstall dnsmasq and try to resolve the basic network problems first.

Regards.


We cross-posted, I came to the same conclusion. And have made some progress: see post above.

Now I'm working on:


```
(wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5] 
```

and

```
device state change: unmanaged -> unavailable (reason 'managed')
```

Ubuntu version = Hybrid. (Originally built on 12.04 cli / minimal / core install +3.5 kernel. Now contains sources from 12.10+ 13.04 +compiled from source. But sources are are 90% 12.04)

DE = X-Gome (XFCE DE minus all XFCE bundled programs "grafted" on to the gnome tool set without the gnome shell or DE.)

I am finding similar issues, but no solutions yet.

Maybe you can give me some insight to something I'm missing?

[URL="http://> **papibe said:**
> What Ubuntu version are you actually using?In 12.04 there is (or used to be) a bug that does not allow running dnsmasq (package by itself), because how was the network-manager dnsmasq plugin originally set up.To my knowledge, that was fixed on 12.10, but if you are running 12.04 I would uninstall dnsmasq and try to resolve the basic network problems first.Regards. We cross-posted, I came to the same conclusion. And have made some progress: see post above.Now I'm working on:```
(wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5] 
```and```
device state change: unmanaged -> unavailable (reason 'managed')
```Ubuntu version = Hybrid. (Originally built on 12.04 cli / minimal / core install +3.5 kernel. Now contains sources from 12.10+ 13.04 +compiled from source. But sources are are 90% 12.04)DE = X-Gome (XFCE DE minus all XFCE bundled programs &quot;grafted&quot; on to the gnome tool set without the gnome shell or DE.)I am finding similar issues, but no solutions yet.Maybe you can give me some insight to something I'm missing?"]This one[/URL]is the most similar so far.


After digging though these I have tried to reboot without a LAN connection and then restart network manager and then bringing up all interfaces to no avail.

Currently investigating ip-config unavailable.

_________
Edit 

I had several links inserted, but the system must have thought I was trying to spam or I can't do links yet b/c all the links were empty after I posted. Below is a copy of the most similar from the gnome mailing list (it never went anywhere):
> 
**Re: network interfaces not coming up**

 [HR][/HR]   
[LIST]
[*]*From*: Dan Williams <dcbw redhat com> 
[*]*To*: fuzzy_4711 gmx de 
[*]*Cc*: networkmanager-list gnome org 
[*]*Subject*: Re: network interfaces not coming up 
[*]*Date*: Fri, 28 Sep 2012 13:20:01 -0500 
[/LIST]
   [HR][/HR]   
On Thu, 2012-09-27 at 11:52 +0200, fuzzy_4711 gmx de wrote: 
> Hi list. 
>  > I am using xubuntu 12.04 32bit on a dell vostro 1720 laptop. I would like to use network-manager but it is not bringing up my interfaces (eth0 and wlan0). 
>  > /var/log/syslog says, when enabling networking: 
> eth0 now managed > eth0 device state change: unmanaged -
> unavailable (reason 'managed') [ 10 20 2 ] 
> eth0 bringing up device 
> eth0 preparing device 
> eth0 deactivating device (reason managed) 

 This could be a few things...  
1) the kernel driver doesn't think there is a carrier, and thus there's no way to use the interface until it does  
2) there is no connection set up for the device yet (ie, IP configuration)

  If you can provide more logs from NM, that would be great.  Dan  

> ip li sh shows both links, udev-rule is loading them with correct mac addresses, but state is down. 
>  > Drivers are loaded, at least I would expect running eth0... 
>  > Could you please advice? 
>  > Thanks > fuz > _______________________________________________ 
> networkmanager-list mailing list > networkmanager-list gnome org

---

### Post by somethingcatchy on 2013-04-11
Ok, maybe some progress? There seems to be lots of possible causes for the two errors above and the device state change may or may not be an issue.

But, the problem with ip-config seems to be most likely dhcp related from what I've found digging on the web.

I went digging manually in my var logs instead of grepping (some times there's something to be said for doing things the long way) and found this in my syslog:

```
Apr 11 20:41:28 adam-L502X NetworkManager[1869]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 11 20:41:28 adam-L502X dhclient: Listening on LPF/eth0/14:fe:b5:a1:74:81
Apr 11 20:41:28 adam-L502X dhclient: Sending on   LPF/eth0/14:fe:b5:a1:74:81
Apr 11 20:41:28 adam-L502X dhclient: Can't bind to dhcp address: Address already in use
Apr 11 20:41:28 adam-L502X dhclient: Please make sure there is no other dhcp server
Apr 11 20:41:28 adam-L502X dhclient: running and that there's no entry for dhcp or
Apr 11 20:41:28 adam-L502X dhclient: bootp in /etc/inetd.conf.   Also make sure you
Apr 11 20:41:28 adam-L502X dhclient: are not running HP JetAdmin software, which
Apr 11 20:41:28 adam-L502X dhclient: includes a bootp server.
```

To my knowedge I haven't intentionally installed a DHCP server on my system. I don't have an /etc/inetd.conf. (Should I?) The only obvious DHCP server listed in pstree is the dhclient forking from network-manager. Synaptic shows that I have the ISC DHCP client. Should I remove it? Is it interfering with the nm-dhclient?

_______________
Edit

Possible indentfication of problem, unsure of solution?

Synaptic description of dnsmasq-base states it resolves DHCP.

Synaptic description of ISC DHCP client states it resolves DHCP.

I can't remove the ISC DHCP client without also removing network-manager, network-manager-gnome and ubuntu-minimal.

Is this conflict (or is it even a conflict at all?) due to the fact that I started with a minimal install and can ubuntu-minimal be removed from my system without harming it?

If not, then can I mark network-manager, network-manager-gnome and ubuntu-minimal for re-installation in synaptic without pulling  ISC DHCP client back in? 

Or do I need to start using aptitude to break dep-chains again so I can pull only the exact packages I want thereby allowing me to dump only the ISC DHCP client; like I did with XFCE and Gnome to create my DE?

Or am I off on a completely wrong tangent?

-------
Edit 2

Just read up on ubuntu-minimal; removing is a no-go. So is ISC and dnsmasq a conflict?

---

### Post by somethingcatchy on 2013-04-12
So, did I wear out my welcome or is everybody just out of ideas?

---

### Post by somethingcatchy on 2013-04-12
Well, since it seems I'm out here on my own I plunged ahead. And now I'm really stuck. I can't break the deps on  isc-dhcp-client. The following:

```
sudo aptitude unmarkauto 'depends(ubuntu-minimal) | ?recommends(ubuntu-minimal)'

sudo aptitude unmarkauto '?reverse-depends(ubuntu-minimal) | ?reverse-recommends(ubuntu-minimal)'

sudo aptitude unmarkauto 'depends(isc-dhcp-client) | ?recommends(isc-dhcp-client)'

sudo aptitude unmarkauto '?reverse-depends(isc-dhcp-client) | ?reverse-recommends(isc-dhcp-client)'
```

is not working. IDK if this is because ubuntu-minimal is something "special" that does not follow the normal rules of package dependency or if some recent update has changed (or broken) aptitudes syntax.

Either way I'm out of ideas.

1) IDK if isc-dhcp-client (which I assume was installed along with my cli installation of ubuntu-minimal) conflicts with dnsmasq-base. If so then there is apparently no way to remove it. Maybe there's a way to stop it from running?

2) IDK if the device state change is a cause for concern or not. If it is it could be caused by a myriad of issues; including having the wrong driver for *both* of my cards (since it happens on both devices).

3) IDK if the ip-config unavailable issue is related to #1 or  something else.

Any input greatly appreciated; you never know which piece of information will be key to untying a knot like this.

---

### Post by steeldriver on 2013-04-12
Sorry if this has been covered - I haven't read the whole thread

Is it possible that rather than having another DHCP server on your  network, you have a static IP defined somewhere without reserving it on  your DHCP server / router?

> ```
**Apr 11 20:41:28 adam-L502X dhclient: Can't bind to dhcp address: Address already in use**
Apr 11 20:41:28 adam-L502X dhclient: Please make sure there is no other dhcp server
Apr 11 20:41:28 adam-L502X dhclient: running and that there's no entry for dhcp or
Apr 11 20:41:28 adam-L502X dhclient: bootp in /etc/inetd.conf.   Also make sure you
Apr 11 20:41:28 adam-L502X dhclient: are not running HP JetAdmin software, which
Apr 11 20:41:28 adam-L502X dhclient: includes a bootp server.
```

I don't think isc-dhcp-client and dnsmasq-base conflict - afaik they are a standard part of the current Desktop config (at least they appear together on my 12.04 box), isc-dhcp-config provides the actual DHCP client and dnsmasq-base provides the dnsmasq binary

```
$ apt-file search $(which dhclient)
isc-dhcp-client: /sbin/dhclient
isc-dhcp-client: /sbin/dhclient-script
isc-dhcp-client: /sbin/dhclient3
isc-dhcp-client-dbg: /usr/lib/debug/sbin/dhclient
$
$ apt-file search $(which dnsmasq)
dnsmasq-base: /usr/sbin/dnsmasq
```

---

### Post by somethingcatchy on 2013-04-12
> **steeldriver said:**
> Sorry if this has been covered - I haven't read the whole thread

Is it possible that rather than having another DHCP server on your  network, you have a static IP defined somewhere without reserving it on  your DHCP server / router?

No, it hasn't. Thanks for jumping in. I've been chasing this for weeks and I have tried so many solutions and touched so many config files it is very well possible that I borked DHCP somewhere. I'll start checking the config files for any obvious mistakes.

Any suggestions on particular files or mistakes to check for or diagnostic command inqueries to run?



> I don't think isc-dhcp-client and dnsmasq-base conflict - afaik they are a standard part of the current Desktop config (at least they appear together on my 12.04 box), isc-dhcp-config provides the actual DHCP client and dnsmasq-base provides the dnsmasq binary

```
$ apt-file search $(which dhclient)
isc-dhcp-client: /sbin/dhclient
isc-dhcp-client: /sbin/dhclient-script
isc-dhcp-client: /sbin/dhclient3
isc-dhcp-client-dbg: /usr/lib/debug/sbin/dhclient
$
$ apt-file search $(which dnsmasq)
dnsmasq-base: /usr/sbin/dnsmasq
```

Cool, thanks for the info. I'm trouble shooting bind at the moment and picking at any and everything that may possibly be a problem. Thanks for eliminating one.

---

### Post by somethingcatchy on 2013-04-12
I'm starting to wonder if there's not still some kind of deeper DNS issue as well despite whatever else may or may not be going on?

I just tried an experiment:

I booted with the LAN plugged in and made the connection. I then unplugged the LAN and established a wireless connection. And it worked without the LAN plugged in; although name resolution was extremely slow while navigating the web. 

But, when I reboot without the LAN plugged in I cannot establish as wired or wireless connection.

So, if I'm understanding correctly, when I boot with a LAN cable plugged in the name of the connection is resolved at boot and then I can unplug the cable and make a wireless connection because the name of the connection has already been resolved.

But, if I boot without a LAN cable plugged in then the name is not resolved and I can't establish either a wired or wireless connection.

All of this is also true for connecting to the wireless connection automatically at boot / reboot.

Therefore, is not the issue that I'm only resolving DNS at boot and not afterwards?

And wouldn't resolving DNS after boot be a function of DNS not DHCP?

--------------
Edit

And can someone please suggest some better connection debugging tools than what I'm currently using? Unless I'm completely off base the syslog only shows connection issues that occur at boot and nmcli is about as verbose as a dead chipmunk.

I need to see everything thats going on at a system level in real time for every connection attempt.

Thanks.

---

### Post by somethingcatchy on 2013-04-12
Progress?

Going on *steeldriver*'s recommendation I started taking a closer look at DHCP configuration. I didn't find anything. So I set up a VM with OOB 12.04.2 to start comparing to and to have a source of default files and configuration.

I compared both /etc/dhcp/dhclient.conf for about 20 minutes and saw no difference. But there had to be one there somewhere because the file size was different by .1KB. I had made a lot of changes to it. But when they didn't work I removed them. Maybe the file got corrupted? I copied the one from the VM to my hardware. Now my connection log looks like this:

```
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: init!
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: update_system_hostname
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPluginIfupdown: management mode: unmanaged
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/net/eth0, iface: eth0)
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: end _init.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    Ifupdown: get unmanaged devices count: 0
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: (36869936) ... get_connections.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    SCPlugin-Ifupdown: (36869936) ... get_connections (managed=false): return empty list.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile: parsing AirVPN_US-Vega_UDP-443 ... 
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile:     read connection 'AirVPN_US-Vega_UDP-443'
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile: parsing AirVPN_US-Librae_UDP-443 ... 
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile:     read connection 'AirVPN_US-Librae_UDP-443'
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile: parsing Home-PC_Network ... 
Apr 12 17:44:36 adam-L502X kernel: [   23.608392] type=1400 audit(1365810274.290:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1239 comm="apparmor_parser"
Apr 12 17:44:36 adam-L502X kernel: [   23.608400] type=1400 audit(1365810274.290:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=979 comm="apparmor_parser"
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile:     read connection 'Home-PC_Network'
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile: parsing AirVPN_US-Octantis_UDP-443 ... 
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile:     read connection 'AirVPN_US-Octantis_UDP-443'
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile: parsing AirVPN_GB-Bootis_UDP-443 ... 
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    keyfile:     read connection 'AirVPN_GB-Bootis_UDP-443'
Apr 12 17:44:36 adam-L502X NetworkManager[1978]:    Ifupdown: get unmanaged devices count: 0
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> trying to start the modem manager...
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> Networking is enabled by state file
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): using nl80211 for WiFi device control
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): now managed
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): bringing up device.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): preparing device.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <warn> failed to allocate link cache: (-10) Operation not supported
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (eth0): carrier is OFF
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (eth0): now managed
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (eth0): bringing up device.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (eth0): preparing device.
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:06:00.0/net/eth0
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> wpa_supplicant started
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <info> (wlan0): supplicant interface state: ready -> inactive
Apr 12 17:44:36 adam-L502X NetworkManager[1978]: <warn> Trying to remove a non-existant call id.
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> (eth0): carrier now ON (device state 20)
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Auto-activating connection 'Wired connection 1'.
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) starting connection 'Wired connection 1'
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> dhclient started with pid 2243
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 12 17:44:39 adam-L502X NetworkManager[1978]: <info> (eth0): DHCPv4 state changed preinit -> bound
Apr 12 17:44:39 adam-L502X NetworkManager[1978]: <info>   address 192.168.1.5
Apr 12 17:44:39 adam-L502X NetworkManager[1978]: <info>   prefix 24 (255.255.255.0)
Apr 12 17:44:39 adam-L502X NetworkManager[1978]: <info>   gateway 192.168.1.1
Apr 12 17:44:39 adam-L502X NetworkManager[1978]: <info>   nameserver '192.168.1.1'
Apr 12 17:44:39 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 12 17:44:39 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Apr 12 17:44:40 adam-L502X NetworkManager[1978]: <info> DNS: starting dnsmasq...
Apr 12 17:44:40 adam-L502X NetworkManager[1978]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Apr 12 17:44:40 adam-L502X NetworkManager[1978]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 12 17:44:40 adam-L502X NetworkManager[1978]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Apr 12 17:44:40 adam-L502X NetworkManager[1978]: <info> Activation (eth0) successful, device activated.
Apr 12 17:44:40 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 12 17:44:47 adam-L502X NetworkManager[1978]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 12 17:44:49 adam-L502X NetworkManager[1978]: <info> (eth0): carrier now ON (device state 100)
Apr 12 17:44:58 adam-L502X NetworkManager[1978]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 12 17:44:58 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 12 17:44:58 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 12 17:44:58 adam-L502X NetworkManager[1978]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 12 19:42:50 adam-L502X NetworkManager[1978]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 12 19:42:54 adam-L502X NetworkManager[1978]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Apr 12 19:42:54 adam-L502X NetworkManager[1978]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Apr 12 19:42:55 adam-L502X NetworkManager[1978]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2243
Apr 12 19:42:55 adam-L502X NetworkManager[1978]: <info> DNS: starting dnsmasq...
Apr 12 19:42:55 adam-L502X NetworkManager[1978]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
```

and my dhclient now:
```

Apr 12 17:44:36 adam-L502X kernel: [   23.608109] type=1400 audit(1365810274.290:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=1239 comm="apparmor_parser"
Apr 12 17:44:36 adam-L502X kernel: [   23.608117] type=1400 audit(1365810274.290:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=979 comm="apparmor_parser"
Apr 12 17:44:36 adam-L502X kernel: [   23.608552] type=1400 audit(1365810274.290:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=1239 comm="apparmor_parser"
Apr 12 17:44:36 adam-L502X kernel: [   23.608561] type=1400 audit(1365810274.290:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=979 comm="apparmor_parser"
Apr 12 17:44:38 adam-L502X NetworkManager[1978]: <info> dhclient started with pid 2243
Apr 12 17:44:38 adam-L502X dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Apr 12 17:44:38 adam-L502X dhclient: Copyright 2004-2011 Internet Systems Consortium.
Apr 12 17:44:38 adam-L502X dhclient: All rights reserved.
Apr 12 17:44:38 adam-L502X dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 12 17:44:38 adam-L502X dhclient: 
Apr 12 17:44:38 adam-L502X dhclient: Listening on LPF/eth0/14:fe:b5:a1:74:81
Apr 12 17:44:38 adam-L502X dhclient: Sending on   LPF/eth0/14:fe:b5:a1:74:81
Apr 12 17:44:38 adam-L502X dhclient: Sending on   Socket/fallback
Apr 12 17:44:38 adam-L502X dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 12 17:44:39 adam-L502X dhclient: DHCPREQUEST of 192.168.1.5 on eth0 to 255.255.255.255 port 67
Apr 12 17:44:39 adam-L502X dhclient: DHCPOFFER of 192.168.1.5 from 192.168.1.1
Apr 12 17:44:39 adam-L502X dhclient: DHCPACK of 192.168.1.5 from 192.168.1.1
Apr 12 17:44:39 adam-L502X dhclient: bound to 192.168.1.5 -- renewal in 39827 seconds.
Apr 12 17:46:32 adam-L502X dhclient: can't create /var/lib/dhcp/dhclient.leases: Permission denied
Apr 12 17:46:32 adam-L502X dhclient: Open a socket for LPF: Operation not permitted
Apr 12 17:54:11 adam-L502X dhclient: DHCPREQUEST of 192.168.1.5 on eth0 to 255.255.255.255 port 67
Apr 12 17:54:11 adam-L502X dhclient: DHCPACK of 192.168.1.5 from 192.168.1.1
Apr 12 17:54:11 adam-L502X dhclient: bound to 192.168.1.5 -- renewal in 38061 seconds.
Apr 12 17:54:36 adam-L502X dhclient: DHCPREQUEST of 192.168.1.9 on wlan0 to 255.255.255.255 port 67
Apr 12 17:54:39 adam-L502X dhclient: DHCPREQUEST of 192.168.1.9 on wlan0 to 255.255.255.255 port 67
Apr 12 17:54:47 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 17:54:50 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Apr 12 17:54:56 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 17:55:07 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 17:55:21 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 17:55:41 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 17:55:58 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 17:56:17 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 17:56:30 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 17:56:37 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 17:56:45 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 17:56:59 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 17:57:09 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 17:57:29 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 17:57:45 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 17:58:05 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 17:58:24 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 17:58:45 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 17:59:04 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 17:59:14 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 17:59:24 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 17:59:43 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Apr 12 17:59:48 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 17:59:48 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 17:59:51 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 18:03:22 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 18:03:31  dhclient: last message repeated 2 times
Apr 12 18:03:31 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Apr 12 18:03:36 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:03:45 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:04:01 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:04:11 adam-L502X dhclient: can't create /var/lib/dhcp/dhclient.leases: Permission denied
Apr 12 18:04:11 adam-L502X dhclient: Open a socket for LPF: Operation not permitted
Apr 12 18:04:16 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 18:04:35 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:04:51 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:05:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:05:14 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 18:05:21 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:05:29 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:05:37 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 18:05:44 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:06:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:06:14 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 18:06:31 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 18:06:50 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 18:07:07 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:07:18 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:07:26 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:07:37 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:07:52 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 18:07:56 adam-L502X dhclient: DHCPREQUEST of 192.168.1.5 on eth0 to 255.255.255.255 port 67
Apr 12 18:07:56 adam-L502X dhclient: DHCPACK of 192.168.1.5 from 192.168.1.1
Apr 12 18:07:56 adam-L502X dhclient: bound to 192.168.1.5 -- renewal in 38749 seconds.
Apr 12 18:08:05 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:08:14 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:08:23 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 18:08:23 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 18:08:26 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 18:12:27 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 18:12:30 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Apr 12 18:12:34 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:12:42 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:12:57 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 18:13:10 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:13:25 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 18:13:42 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:13:52 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:14:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 12 18:14:18 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:14:29 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 18:14:41 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 18:15:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 18:15:19 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:15:29 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 12 18:15:47 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 18:16:07 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:16:22 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:16:32 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:16:53 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 18:17:12 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:17:22 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Apr 12 18:17:28 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 18:17:28 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 18:17:31 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 18:24:25 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 18:24:28 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:24:36 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:24:47 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:25:01 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:25:10 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:25:25 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 18:25:32 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 18:25:45 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:25:56 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 18:26:09 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 12 18:26:27 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 18:26:39 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:27:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:27:21 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:27:35 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:27:43 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:27:57 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 18:28:15 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:28:25 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:28:46 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:29:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 12 18:29:18 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:29:26 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 18:29:26 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 18:29:29 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 18:35:46 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 18:35:49 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Apr 12 18:35:55 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 18:36:08 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:36:17 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:36:28 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:36:43 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:36:57 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:37:12 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:37:28 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:37:49 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:37:58 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:38:08 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:38:18 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 18:38:39 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 18:38:51 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:39:12 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:39:22 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:39:31 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 18:39:38 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 18:39:50 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:40:11 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:40:27 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 18:40:47 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 18:40:47 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 18:40:50 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 18:45:01 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 18:45:04 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:45:12 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:45:26 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 18:45:39 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:45:47 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:45:57 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:46:07 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:46:18 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:46:27 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 18:46:37 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:46:48 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:46:57 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 18:47:16 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 12 18:47:34 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:47:43 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 18:48:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 18:48:20 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:48:36 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:48:45 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 18:48:54 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:49:05 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:49:26 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 18:49:43 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:49:59 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 18:50:02 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 18:50:02 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 18:50:05 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 18:53:17 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 18:53:20 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 18:53:27 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:53:42 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 18:54:01 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:54:22 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:54:38 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:54:54 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:55:15 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 18:55:32 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 18:55:44 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 18:55:52 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 18:56:03 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:56:17 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 18:56:32 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 18:56:45 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 18:56:59 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:57:15 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 18:57:34 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 18:57:50 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 18:58:11 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 18:58:18 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 18:58:18 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 18:58:21 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 19:04:35 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 19:04:38 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Apr 12 19:04:43 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:04:56 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 19:05:08 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:05:21 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:05:34 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 19:05:49 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:06:02 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 19:06:10 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 19:06:25 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 19:06:44 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 19:07:05 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 12 19:07:23 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 19:07:31 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 12 19:07:49 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 19:07:59 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 19:08:06 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 19:08:25 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 19:08:46 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 19:09:22  dhclient: last message repeated 3 times
Apr 12 19:09:22 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 19:09:30 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Apr 12 19:09:36 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 19:09:36 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 19:09:39 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 19:13:13 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 19:13:16 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Apr 12 19:13:22 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 19:13:34 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 19:13:46 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 19:14:07 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 19:14:21 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 19:14:40 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 19:14:48 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 19:15:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:15:13 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 19:15:24 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:15:37 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 19:15:46 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 19:16:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 19:16:08 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 19:16:18 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 19:16:27 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 19:16:44 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 19:17:03 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 19:17:20 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 19:17:28 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 19:17:43 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 19:18:03 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 19:18:14 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 19:18:14 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 19:18:17 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 19:25:33 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 19:25:36 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 19:25:44 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 19:26:04 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 19:26:16 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 19:26:26 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 19:26:40 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 19:26:48 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 19:27:04 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 19:27:18 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 19:27:29 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:27:42 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 19:28:01 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 12 19:28:17 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 19:28:38 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 19:28:49 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 19:28:56 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 19:29:05 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 19:29:20 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:29:33 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 19:29:53 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 19:30:08 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 19:30:17 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:30:30 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Apr 12 19:30:34 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 19:30:34 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 19:30:37 adam-L502X dhclient: No working leases in persistent database - sleeping.
Apr 12 19:36:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 12 19:36:03 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 12 19:36:11 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 12 19:36:29 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 19:36:49 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 12 19:37:06 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr 12 19:37:17 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Apr 12 19:37:26 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 19:37:41 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 19:38:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:38:13 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 12 19:38:25 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Apr 12 19:38:46 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 12 19:39:00 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:39:13 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 12 19:39:31 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 12 19:39:38 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Apr 12 19:39:57 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 12 19:40:07 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Apr 12 19:40:27 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 12 19:40:40 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Apr 12 19:40:55 adam-L502X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Apr 12 19:41:01 adam-L502X dhclient: No DHCPOFFERS received.
Apr 12 19:41:01 adam-L502X dhclient: Trying recorded lease 192.168.1.9
Apr 12 19:41:04 adam-L502X dhclient: No working leases in persistent database - sleeping.
```

So, at least I'm not getting told that my DHCP server can't start or bind to an address any more.

But, I still can't connect after boot.

One thing I have noticed digging through the syslogs on both my hardware and on my VM: On the VM every connection attempt is written to syslog. On hardware that is not the case. It is only some and I haven't been able to determine yet when / why. Maybe a permission or group error?

When you move hardware with remastersys you have to manually add yourself back to a lot of groups on the new hardware. Maybe I missed one? Or maybe a group never got created because I started from cli / minimal install?

Or maybe I fouled a permission? I've done some d-bus editing. I took away all of power managers run authorizations because I got tired of fighting with it; no matter what I told it to do it would shut my machine off after 4 hours.

 And I also changed that really annoying "feature" where you have to put in your admin password to connect wirelessly.

I noticed in my 12.04.02 OOB VM that I didn't have to put in a password to connect to a wireless. Is this due to d-bus policy being auto installed differently in a VM vs hardware or did they fix that so called "feature"? If they fixed it maybe I need to copy over to hardware the appropriate d-bus policies?

Any other ideas on what could cause me to write only some connection attempts to the syslog with no apparent rhyme or reason for when / why I'm writing and when / why I'm not?

---

### Post by steeldriver on 2013-04-12
What are the permissions on your /var/lib/dhcp/xxx?

```
ls -l /var/lib/dhcp/dhclient.leases
ls -ld /var/lib/dhcp/
```

What happens if you do

```
sudo dhclient -r wlan0
sudo dhclient -v wlan0
```

---

### Post by somethingcatchy on 2013-04-12
ls -l /var/lib/dhcp/dhclient.leases
```
-rw-r--r-- 1 root root 1108 Apr 12 18:07 /var/lib/dhcp/dhclient.leases
```

ls -ld /var/lib/dhcp/
```
drwxr-xr-x 2 root root 16384 Apr 12 20:31 /var/lib/dhcp/
```

sudo dhclient -r wlan0
```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
```

sudo dhclient -v wlan0
```
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/8c:a9:82:57:34:e2
Sending on   LPF/wlan0/8c:a9:82:57:34:e2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
```


I'm not currently connected on wlan0, but on eth0. So I threw this in, just in case since I'm having the same issues with both:

sudo dhclient -r eth0
```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
```

sudo dhclient -v eth0
```
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/14:fe:b5:a1:74:81
Sending on   LPF/eth0/14:fe:b5:a1:74:81
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST of 192.168.1.5 on eth0 to 255.255.255.255 port 67
DHCPOFFER of 192.168.1.5 from 192.168.1.1
DHCPACK of 192.168.1.5 from 192.168.1.1
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
bound to 192.168.1.5 -- renewal in 36088 seconds.
```

Do you want me to run a boot cycle without an auto-connection at boot and re-run the same diagnostics since the overall issue is being able to auto-connect at boot but not being able to connect after boot?

--------
Edit

Killing time with nothing better to do. I ran the reboot with no connection and ran the diags. It didn't reveal anything useful; just that I couldn't bind to any addresses. And that makes since since I wasn't plugged in to any thing or set for any auto-connects. And since syslog hasn't written anyting in about 3 hours there's no info there. I guess that's the next thing to work on?

---

### Post by somethingcatchy on 2013-04-13
OK, now network manager is writing every connection to syslog. It was my own fault that it wasn't. I had been doing some work on some cron jobs a while back and the logging was flooding my syslog and making it too big to be managable. The rotate log function was creating 3 crompressed zips per day. And it was a pain to dig through three different logs for 1/3 of a day each. So I made some changes in rsyslog.d to cut down on how verbose cron was so it would only throw me the "important" stuff. Evidently I over did it.

Back to digging.

---

### Post by somethingcatchy on 2013-04-13
A couple of days ago *papibe *suggested simplifying the problem by removing dnsmasq. I did, as I had installed it mistakenly while attempting repairs because I thought it was necessary.

Well, in an effort to simplify things even more I have done some cleaning on my system. I included samba and a zero configuration mDNS tool while building for later use. But, since I'm not actually using them at the moment I purged them in an effort to get to the core of the problem.

I also pulled portsentry off of my firewall because it is depreciated and Nmap has had hardcoded ways around it for a while now.

At this point my networking core *should* be OOB 12.04.

I use IP KungFU, fwsnort, psad and denyhost as deamons on my firewall to manage IPTables. But they shouldn't (?) be blocking a system initiated network connection.

And my connection logs look perfectly normal now when I boot with an auto wired/wireless connection.

So, let's see what happens without one.

---

### Post by somethingcatchy on 2013-04-13
It works. But wireless is really, super slow.

I'll need to spend a few hours on the wife's machine getting her back to an OOB network stack and then test both on public wifi's. I'll comeback later tonight or tomorrow and mark it solved or ask more questions.

If I can't get it to speed up I'll start a new thread on that.

Thanks to *papibe* and *steeldriver* for their input.

---

### Post by somethingcatchy on 2013-04-14
Just finished cleaning, repairing and backing up the wife's machine. From working on both it looks like for whatever reason that /var/run/nm-dns-dnsmasq.conf was not created in the process of my building out from cli / minimal install and in the process of learning and trying to repair my core networking functions I broke a bunch of other stuff.

Also, FYI: Do not install portsentry on 12.04. Not only is it old, depreciated and Nmap has hard coded ways around it; but, I learned while fixing my wife's machine that it is breaks core networking on 12.04 and makes it impossible for the nm dhclient and dnsmasq plugins to resolve addresses after boot.

And her machine has good internet speed; which is reassuring. It should mean that I haven't made any more mistakes and my slow wireless internet is due to hardware issues. That shouldn't be too hard to fix before I start testing on public networks.

---

### Post by somethingcatchy on 2013-04-15
Solved. I went testing today and I connected to several different types of public wifi with both machines with no issues. And I fixed my slow wireless speed. It was the "n" problem with an intel card.

---

