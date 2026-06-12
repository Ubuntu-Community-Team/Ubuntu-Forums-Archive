---
title: "Network setup"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by OldManRiver on 2011-07-14
All,

Hve internet connection on this box, U ver 9.10, updating to 10.04 while entering this.  Inet connects thru DLink wireless card.  Want to serve DHCP on the eth0 port and connect local network through this computer.

What HOWTOs address this setup?

Addressed this on irc.freenode.net/#ubuntu and got no response.

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-15
All,

OK found a bunch of HOWTOs, but none of them work, at least not right.

I do not think the writers of these HOWTOs ever thought of SERVING IPs to their network from their server.

I see a few that talk about multiple NICs, but even their instuctions do not get DHCP serving IPs to the network.  One main diff I noticed is all of them are working with DHCPD and my box does not have that, instead it has DHCP3-SERVER.

Do not understand the what this means but looking.

Thanks!

OMR

---

### Post by atomicben on 2011-07-15
Are you talking about ICS (internet connection sharing)?  Are you saying you have one device connected to the internet and you want other devices to be able to connect to the internet through your main device?  Sounds like it.  Try this:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by OldManRiver on 2011-07-21
> **atomicben said:**
> Are you talking about ICS (internet connection sharing)?  Are you saying you have one device connected to the internet and you want other devices to be able to connect to the internet through your main device?  Sounds like it.  Try this:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

atomicben,

Looks like your HOWTO is supposed to work, problem is the HOWTO says "select Auto eth0" but I get no "Auto eth0" on my machine.  It used to be there, but disappeared when I upgraded from 9.10 to 10.04.

could use a little help on this.

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-22
All,

Dang screwed the pooch on this.  I went on IRC.freenode.net to the #ubuntu channel and got so advice.  I was told to use dnsmasq instead of dhcpd and tried it an the network totally blew, with errors, when I restarted, so had to come up with 9.10 liveCD to get back here as say "That is not the way"

Still looking for the right way to do this.

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-22
All,

Found this HOWTO at:

[http://ubuntuforums.org/showthread.php?t=1470618](http://ubuntuforums.org/showthread.php?t=1470618)

but when I tried to get the chroot to work kept getting the error:

> you must specify the filesystem type

That with with the command:

```
sudo mount -t auto /dev/sda2 /media/version
```

What is the default filesystem type for 10.04?

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-22
All,

OK recovered from my "no internet" around 2:30 am last night, using my 9.10 liveCD to recover with.

Had run a complete uninstall of dhcp including all it components, but found the directory still existed, when I booted under the liveCD and issued the chroot cmd sequence (mine was sda1 not sda2).

When I deleted the directory, rebooted to HDD and ran apt-get purge dhcp, I came back clean, then installed dhcp3 client and now I'm back.

Not sure what the difference between dhcp and dhcp3 is but some of the tools I use require the second and assume it is a later and more enhance version, so guess I'm stuck with that "for better or worse"  Ha Ha LOL :) :)

Anyway I'm up but still have to fix this dhcp server issue so the rest of my machine can us the inet also.

I did learn not to use dnsmasq as that is what took me down.

Anyway got to run so will finish this later.

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-22
All,

Found this HOWTO at:

[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

and pretty much looks like what I need accept they are using eth0 as inet source and broadcasting on wlan0, where mine is just the reverse of that with wlan0 as inet resource and eth0 broadcasting DHCP/IP address.

Will see if this works with mods, of course.

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-22
All,

Before I restart my network, here is my /etc/network/interfaces file settings:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0
auto ath0
auto br0

# The internet network interface
#iface eth0 inet dhcp
iface wlan0 inet dhcp

# The local network bridge
#iface br0 inet static
iface ath0 inet dhcpd
  bridge_ports ath0 eth0
  address 192.168.3.2
  netmask 255.255.255.0

# The wireless side of the bridge
#iface ath0 inet manual
iface br0 inet manual
  wireless-essid MY_ESSID
  wireless-key **********
  wireless-mode master

```
Not sure about the last line of "wireless-mode master".  Need to know if my wireless needs to be in another mode for the cofig I'm using?

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-23
All,

Working with the guys on irc.freenode.net I entered, on the cmd line:
```
ip addr del 192.168.1.2/24 dev wlan0; brctl addbr br0; brctl addif br0 wlan0; brctl addif br0 eth0; ip addr add 192.168.1.2/24 dev br0
```
But that also disconnected my wlan0 inet connection, and networking restart did not restore, so rebooted.

Still working on this.  Haven't seen any of the normal gurus adding anything here yet.

Can I get some help please?

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-25
All,

Well Auto eth0 is now working but totally bogus address being assigned.  Notice the 10.42.43.1 IP setting in the ifconfig but the setting called for is 192.168.3.x.  Happy that the Auto eth0 is always coming up now, but it is still not serving IPs to the network and totally confused by where is is getting the 10.42.43.1 address and have not found this searching my system.

Put all this in a pastebin at:

[http://pastebin.com/ZaahMihm](http://pastebin.com/ZaahMihm)

Hope this helps someone help me debug this.

Thanks!

OMR

Oh hey if I fogot to list the HOWTOs I have been consulting they are:

[https://help.ubuntu.com/community/Internet/ConnectionSharing#DHCP/DNS%20server](https://help.ubuntu.com/community/Internet/ConnectionSharing#DHCP/DNS%20server)
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)
[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)
[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)
[http://ubuntuforums.org/showthread.php?t=402581](http://ubuntuforums.org/showthread.php?t=402581)
[http://www.linuxquestions.org/questions/linux-hardware-18/how-to-bridge-two-network-connections-on-ubuntu-746926/](http://www.linuxquestions.org/questions/linux-hardware-18/how-to-bridge-two-network-connections-on-ubuntu-746926/)
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)
[http://techspalace.blogspot.com/2008/05/how-to-setup-network-bridge.html](http://techspalace.blogspot.com/2008/05/how-to-setup-network-bridge.html)

OMR

---

### Post by OldManRiver on 2011-07-25
Can I get some help please?

---

### Post by jmoorse on 2011-07-25
In regards to your 10.x.x.x address, you have the static portion for eth0 commented out in your config with #s:

```

#iface eth0 inet static
#address 192.168.3.2
#gateway 192.168.3.1
#netmask 255.255.255.0
#network 192.168.3.0
#broadcast 192.168.3.255

```

I would guess your router is handing this address out via dhcp...

This is likely why you cannot route out via eth0 if you have an invalid subnet assigned to eth0...

Forgive the terse nature of this reply, I am eating lunch :)

---

### Post by drdos2006 on 2011-07-25
It would appear that your router is handing out the IP address.
```

#
Snap shot of the network settings from ifconfig
#
 
#
eth0      Link encap:Ethernet  HWaddr 00:07:e9:3d:c3:e8  
#
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
#
          inet6 addr: fe80::207:e9ff:fe3d:c3e8/64 Scope:Link
#
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
#
          RX packets:9455 errors:0 dropped:0 overruns:0 frame:0
#
          TX packets:6813 errors:0 dropped:0 overruns:0 carrier:0
#
          collisions:0 txqueuelen:1000
#
          RX bytes:1564285 (1.5 MB)  TX bytes:1141629 (1.1 MB)

```
Do you have two NICs ?
One would be external from your router on the 10.0.....address and the second NIC would be your internal 192.168.. addresses so your server would act as the DHCP router/server.

Check out Untangle, [http://www.untangle.com/](http://www.untangle.com/) 

regards

---

### Post by DawieS on 2011-07-25
The IP Address on the LAN side of the router (acting as a DHCP server) is normally fully adjustable on the router, and is totally different to the actual IP address of the router as supplied by your ISP, which is visible to the Internet (WAN side of the router).

The attached screenshot shows that I have set the starting address at 192.168.1.100. The router will start handing out addresses from 100 upwards, whenever a machine on the LAN is switched on (with the connection set to obtain DHCP automatically).

I also have a few machines with fixed addresses (below 100) on the LAN. Doing it this way avoids the possibility of any conflicts.


The IP address block 10-11 is not officially assigned to anyone, and may be used by any private network without registering with IANA. It is possible that this is the default address range used by your router. Doing a **whois** on any 10-11 address returns:
```

NetRange:       10.0.0.0 - 10.255.255.255
CIDR:           10.0.0.0/8
OriginAS:       
NetName:        PRIVATE-ADDRESS-ABLK-RFC1918-IANA-RESERVED
NetHandle:      NET-10-0-0-0-1
Parent:         
NetType:        IANA Special Use
Comment:        This block is used as private address space.
Comment:        Traffic from these addresses does not come from IANA.
Comment:        IANA has simply reserved these numbers in its database 
Comment:        and does not use or operate them. We are not the source 
Comment:        of activity you may see on logs or in e-mail records.
Comment:        Please refer to  http://www.iana.org/abuse/
Comment:             
Comment:        Addresses from this block can be used by 
Comment:        anyone without any need to coordinate with 
Comment:        IANA or an Internet registry. Addresses from
Comment:        this block are used in multiple, separately 
Comment:        operated networks.
Comment:        
Comment:        This block was assigned by the IETF in the
Comment:        Best Current Practice document, RFC 1918
Comment:        which can be found at:
Comment:        
Comment:        http://www.rfc-editor.org/rfc/rfc1918.txt
RegDate:        
Updated:        2011-04-12
Ref:            http://whois.arin.net/rest/net/NET-10-0-0-0-1
```It is good practice to have the LAN side address range completely different from the Internet (WAN side) to avoid possible conflicts and confusion.:smile:

---

### Post by jmoorse on 2011-07-25
Yes, 10.0.0.0/8 is private.  Just as 192.168.0.0/16 and 172.16.0.0/18.

---

### Post by OldManRiver on 2011-07-25
All,

Sorry been on irc.freenode.net/#ubuntu, #linux, and #debian working on this.  What I noticed that was screwing me was two things:

1. I had LinkSys router on LAN, being config'd so can use, where visitors to this remote warehouse can use internet.  Removed that so I no longer get confusing signals/IPs from it,

2. In my /etc/network/interfaces file I had the "auto eth0" before a lot of commands, then later on had the eth0 static info.  When I moved the "auto eth0" down so it was grouped with the other eth0 commands I started seeing all the right settings in ifconfig for eth0.

However if you look at my latest PB posts at:

[http://pastebin.com/YJKNRXVk](http://pastebin.com/YJKNRXVk) - configs
[http://pastebin.com/M5zUxbnf](http://pastebin.com/M5zUxbnf) - syslog last 20

You see the eth0 is right, but it still is not serving IPs to the network.

I'm glad I'm this far, but hope to finish soon.  This one is wearing me out.

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-25
> **DawieS said:**
> The IP Address on the LAN side of the router
D,

Sorry no router, only router that will be used will get it's ip from this server and allow visitor to use inet through it.

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-26
All,

Eureka almost there.  I now get IPs from the dhcp3-server so the win laptop is getting 192.168.3.10 and the Linksys WRTU54G is getting 192.168.3.11.

My config PB is:

[http://pastebin.com/0RceWbY6](http://pastebin.com/0RceWbY6)

and my log PB is:

[http://pastebin.com/9qJ9Wufi](http://pastebin.com/9qJ9Wufi)

As you can see the log is clean, from errors, but I can not ping through using "ping www.google.com" from the Laptop, therefore I assume what I am missing is the correct nameserver setting that I need from the wlan0 interface, which I assume needs to be entered in my dhcpd.conf file, where you see it in line # 29 in my config PB.

Anyway any help to find the nameserver will be appreciated.  In the mean time I am going back to look at the GUI config in the HOWTOS, as so many things I set before, keep getting reset by the different processes I was undertaking.

Cheers and Thanks!

OMR

---

### Post by OldManRiver on 2011-07-26
All,

Since the description of my problem is spread out a little, thought I would recap:

**Problem Description**
[LIST=1]
[*]Have network in remote warehouse 2 miles from main warehouse, due to cost connect via high gain antennas on wifi, interface wlan0,
[*]Currently daily burning CDs to transfer DB data to main data center,
[*]Trying to get Inet and Networking on from existing U-Box 10.04 so the data transfers via LAN/Inet avoiding daily trips,
[*]Have installed dhcp3-server, edited config file, and have/had eth0 serving IPs to network,
[*]Could Ping hard address for [www.google.com](www.google.com) of 74.125.67.99 but not by name, so know the problem is with nameservers/DNS,
[*]Network Mgr was rewriting the /etc/resolv.conf file so removed/purged it,
[/LIST]

**Status**
**Last Action:** Remove Network Mgr
**Results:**
[LIST]
[*]After restart of network the removal of NM took out the defs for wlan0, therefore not able to access inet, so rebooted from liveCD,
[*]Captured network restart errors and reboot errors, in file and posted on PB at: [http://pastebin.com/yqWk3ucd](http://pastebin.com/yqWk3ucd)
[*]Posted configs on PB at: [http://pastebin.com/yC9fcguh](http://pastebin.com/yC9fcguh)
[*]Ran CHROOT with mount of HDD and attempted re-install of NM,
[*]Rebooted but still no wlan0, so attempted to open synaptic to check the status of the NM install, synaptic will not open,
[*]Rebooted from liveCD to post this status,
[*]Waiting on help, this is over my head.
[/LIST]
Anyway this is where I am at here and now 17:26 Tues July 26 2011!

Hope I get help soon, considering complete re-install of 10.04 to get back to ground zero.

All help appreciated!

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-27
All,

Found out the reason synaptic is not working on the HDD boot is that the chroot setup I did had not properly bound all the resources, since you need about 10 command to get this right and all must go right.

Anyway that is what splattered the aynaptic, so been working on recovering that, but no success yet.

Have some ideas on skinning this cat, but will put them in later.  Never met a box I can not conquer so will continue on this until I prevail.

Thanks!

OMR

---

### Post by newbie-user on 2011-07-27
Okay, I'm just going to go all the way back to address your original post because it seems that the simple problem got all jumbled up.

So you have a fresh Ubuntu 10.04 with a wireless card that connects you to the Internet and you want to use your wired connection to serve your LAN with DHCP.

1) Install dhcp3-server.
2) Edit the file /etc/default/dhcp3-server, uncommenting the line #INTERFACES="" and changing it to INTERFACES="eth0".  This tells the dhcp server to hand out IP addresses through eth0 only (the dhcp server won't start without making that change).
3) Now you can edit /etc/dhcp3/dhcpd.conf to your liking.  Make sure that within dhcpd.conf, you specify the IP address of eth0 as the gateway for the network.
4) Edit the file /etc/sysctl.conf, uncomment the line #net.ipv4.ip_forward=1, so it reads net.ipv4.ip_forward=1
5) Reboot the server (not ideal, but loads all new configurations)  
6) Done!

---

### Post by OldManRiver on 2011-07-27
All,

Well this one ticked me off, so downloaded and burnt liveCD and server copy for 10.04 and did install of both.  Now back to having IPs served on eth) LAN side, but have no ping of either mames or hard addresses there, but ping working fine, here via wlan0 on U-Box.

Will be chating with irc.freenode.net to see what fixes this.

Thanks!

OMR

---

### Post by newbie-user on 2011-07-27
Do you have an internal DNS server to resolve the hostnames?  Also, you'll have to set up static routing so that boxes on the wlan0 side of the ubuntu box know how to find the boxes on the eth0 side.

---

### Post by OldManRiver on 2011-07-28
All,

Maybe a picture helps:
```

 _____________                                    ______________
|             |                                  |              |
|             |__/|                          |\__|              |
|    MAIN     |  \|    WIFI W/HGain Ants     |/  |    REMOTE    |
|   WHOUSE    |                                  |    WHOUSE    |
|             |                                  |              |
|_____________|                                  |______________|
                                                         |
                                                         |  wlan0
       _______     _______     _______    ______     ____|___
      |       |   |       |   |       |  |      |   |        |
      | W-Box |   | Svr1  |   | Svr2  |  | Svr3 |   |  UBox  |
      |_______|   |_______|   |_______|  |______|   |________|
          |           |           |         |            |
          |___________|___________|_________|____________|  eth0
                         Local Remote Network R-LAN

```
**DEFS:**
Main Warehouse is source of internet and PDS
Bridging and routing takes place in the Ubutu Gatewau (U-Box)
W-Box is new LinkSys WiFi for visiting laptop users
Ubox is the router/DHCP server providing the Remote LAN (R-LAN) with IPs, internet and networking to main warehouse.

If I have to, I can declare the UBox as secondary PDS, once all this is up and working.  Remember none of the Servers 1-3 are using network logins at this time; they are all stand-alone boxes now, not even talking to each other.

**Status:**
Well here again via liveCD, but got a few things done.  Right now the DHCP3-Server is working giving IPs to the R-LAN, nothing else.  WLAN0 is down, outside of the liveCD so need to tweak the settings somewhere to get it up when booting from HDD.

I performed some backup from the HDD boot to my external HD, but since I've done multiple installs, etc. due to ongoing problems will have to use "Parted Magic" or some other partitioning and recover tool to get the disk back to a clean state.

Will be running my config script shortly and posting all the config files to pastebin.com; but have to reboot to HDD, capture, then reboot to liveCD to post.

Also, in desperation, gutted the old U-Box, and added to another old Dell in our scrap pile, that had more memory a CD burner, so I could quit going crazy on some of these things and get up faster on the reboots.

Anyway got to reboot to HDD now to get the configs for you.  If you know what log files I need to be adding to my config script for catching all the errors; please comment with that so I can provide that info also.

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-28
All,

Configs in PB at: [http://pastebin.com/WWcjkFwX](http://pastebin.com/WWcjkFwX)

Errors in PB at:  [http://pastebin.com/XhyN0nZi](http://pastebin.com/XhyN0nZi)

Thanks!

---

### Post by OldManRiver on 2011-07-28
All,

Latest config at: [http://pastebin.com/85YpS1RF](http://pastebin.com/85YpS1RF)
Latest errors at: None

Get IPs on win laptop, but can not ping anything, only self ping on:

192.168.3.10

OMR

---

### Post by OldManRiver on 2011-07-29
All,

Well had to go out to the Gentoo guys to get this fixed.  Since they have to really hammer their code from the command line, they seem to have a slightly better understanding of things and how they work.  Anyway my friend "kerframil" out there sent me this PB write up at:

[http://dpaste.com/581177/](http://dpaste.com/581177/)

I ran the cmds and restarted with these errors.

[http://dpaste.com/581223/](http://dpaste.com/581223/)

After a couple more tweak and network restarts we started testing from the XP laptop I had connected to the R-LAN,  DHCP was serving IPs fine, so I got bold and tried the ping on google.  I hestitated at first, then BAM it connected and ping responded.  Excited I opened the browser and BOOM it all came up.

Post note he has me cleaning up a few thing, so will repost all the configs when I finish.  Also I need help getting the last command:

```
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

```
Into the Ubuntu IPTables so it will be there for reboot, but 

**Hallaluejah it works!!!!!!!!**

You all have no idea how happy I am that this is working!!!

Thanks all!!!!!!

I don't know if I can write this up so other understand it, but will try!

OMR

---

### Post by OldManRiver on 2011-07-29
All,

Thought as addendum I'd put out some scripts I wrote in this process:

**Config File Edit Script:**
```
#!/bin/bash

# define the file vars
fil1="/etc/network/interfaces";
fil2="/etc/dhcp3/dhcpd.conf";
fil3="/etc/sysctl.conf";
fil4="/etc/resolv.conf";

fil5="/etc/network/interfaces_bup";
fil6="/etc/dhcp3/dhcpd.conf_bup";
fil7="/etc/sysctl.conf_bup";
fil8="/etc/resolv.conf_bup";


cp "$fil1 $fil5 -f";
cp "$fil2 $fil6 -f";
cp "$fil3 $fil7 -f";
cp "$fil4 $fil8 -f";

gedit "$fil1 $fil2 $fil3 $fil4";
```

**Config File Capture Script:**
```
#!/bin/bash

clear;
filename="settings-wifi.txt";
pathname="/home/ndavis/myfiles/";
rm "$pathname$filename";
touch "$pathname$filename";
chown root:users "$pathname$filename";
chmod 775 "$pathname$filename";

# copy the config files into a holding file
{
echo "Gen'd by Script";
echo ' '; 
echo "Contents of the NetWork config file /etc/network/interfaces"; 
echo ' ';
cat "/etc/network/interfaces";
echo ' ';
echo "Contents of the DHCP config file /etc/dhcp3/dhcpd.conf"; 
echo ' ';
cat "/etc/dhcp3/dhcpd.conf";
echo ' '; 
echo "Contents of the sysctl.conf file /etc/sysctls.conf"; 
echo ' ';
cat "/etc/sysctl.conf";
echo ' '; 
echo "Contents of the hostname file /etc/hostname"; 
echo ' ';
cat "/etc/hostname";

# capture the ip settings
echo ' '; 
echo "Snap shot of the network settings from ifconfig"; 
echo ' ';
ifconfig;
echo ' ';
} > "$pathname$filename";
chown ndavis:users "$pathname$filename";
chmod 775 "$pathname$filename";
```

**Errors Capture Script**
```
#! /bin/bash

filename="errors-wifi.txt";
pathname="/home/ndavis/myfiles/";
rm "$pathname$filename";
touch "$pathname$filename";
chown root:users "$pathname$filename";
chmod 775 "$pathname$filename";
{
# Capture run errors
/etc/init.d/networking restart;
#restart bridge-network-interface;
/etc/init.d/dhcp3-server start;

# Capture log errors
tail -n 30 /var/log/syslog;
} > "$pathname$filename";

```

**WiFi Start Script**
```
#! /bin/bash

# Run the commands to start network passthru
/etc/init.d/dhcp3-server restart;
/etc/init.d/networking restart;

sysctl -w net.ipv4.ip_forward=1
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE;
```
You sometimes have to rerun the DHCP server start/restart, if errors occur

Thought this might help anyone else facing this same problem.

Cheers!

OMR

---

### Post by OldManRiver on 2011-08-23
All,

This is working sorta!  Have 2 issues:
[LIST=1]
[*]DHCP Server drops out routinely every 5 minutes, at the new local wireless router, so WiFi quests having lots of issues,
[*]Lease on the wlan0 WiFi (inet source) side keeps dropping, during certain time of the day,
[/LIST]
Not sure if these two are interelated or if the local WiFi router has a lease renewal setting that is causing it to drop.

Open to suggestions.  Need a way to monitor and log the signal strength on the wlan0 side.  AirCrack NG has some of these features, but not sure how to use it just to monitor and log wlan0 signal strength, so I can isolate my problem.

Thanks!

OMR

---

### Post by OldManRiver on 2011-08-27
All,

I've been sniffing around trying to find a good GUI program that will work like WiFi Radar on Windows, which let's you see signal strength and find best azimuth to remote antenna.

Reason, is I found my signal that used to consistantly stay around 59% in now deteriorating to less than 15% during the hottest part of the day, and y'all know how hot it gets here is TX.

Anyway from 3-7 pm I pretty much loose the signal so have to fine tune this bad boy to get it back up to an acceptable level all day long.

Been looking at dd-wrt to see if they have at least a beta for my D-Link DWL G520 WiFi card with the Atheros AR5001X+ driver set.  Posted on their forum, but have no direction from them yet.  The main warehouse AP is not on their compatible list, nor is the D_Link card, but they do support the Atheros chip set, so hoping they can get me code or something to let me boost the signal some, to get enough punch to get through during these HOT times.

If I get this problem resolved, then I still need to monitor drop-out on this node and find an automation of my WiFi start script to keep it up.

Guess that means I need a way to get it to report to system health, but do not know what parms I need to be watching, that are available to system health and/or if I need to create a process that will send a notification to system health, when this drops out.

Open to ideas and suggestions on this!

Thanks!

OMR

---

### Post by OldManRiver on 2011-09-12
All,

Can I get some help here?

OMR

---

### Post by OldManRiver on 2011-09-28
All,

Resolved this with manual downloads of all the code for NM, DHCP, etc and did manual offline install.

Been super solid for 2 weeks now!

Marking this SOLVED

---

