---
title: "Using 2 networks simultaneously"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by gpgp on 2009-11-04
I want to connect to 2 physical networks. I am using my wired to go to lan used for machine control. And using my wireless to connect to the lan attached to the internet.

It seems i cannot use both at the same time in Karmic. If i open a web page via wireless then plug in to the machine control lan with my wired connection, i can no longer get web pages via wireless. The settings for wired are over riding the wireless and it doesn't try the wireless connection.
Can anyone help with this ?
Thanks
gpgp

I found it.  there is a box to check : use this connection only for resources on this network. System> Prefernces> Network Connections> Select conection, edit> ip4 tab> routes button> check box.
Thanks, hope this helps someone else.

gpgp

---

### Post by Iowan on 2009-11-04
Glad you found the solution. There's an option to mark the thread [SOLVED] under Thread Tools.

---

### Post by ajMac on 2011-03-22
> **gpgp said:**
> I want to connect to 2 physical networks. I am using my wired to go to lan used for machine control. And using my wireless to connect to the lan attached to the internet.

It seems i cannot use both at the same time in Karmic. If i open a web page via wireless then plug in to the machine control lan with my wired connection, i can no longer get web pages via wireless. The settings for wired are over riding the wireless and it doesn't try the wireless connection.
Can anyone help with this ?
Thanks
gpgp

I found it.  there is a box to check : use this connection only for resources on this network. System> Prefernces> Network Connections> Select conection, edit> ip4 tab> routes button> check box.
Thanks, hope this helps someone else.

gpgp

> **houstonbofh said:**
> If I am reading this right, you want to browse the Internet on wlan, while also connecting to a single network on lan.  This is easy.

1) Right click on your network manager icon, and select 'Edit Connections.'

2) Under 'Wired' click '+ Add'

3) Name it something, uncheck 'connect automatically' select the 'IPV4' tab, and give yourself static IP, but do not fill in the gateway.

By not putting a gateway in, your lan interfaces has no default gateway, so the wlan one can be used.  Otherwise the lan gateway takes precedence.

Amazing, finally its all working!! 

Setup: Ubuntu 10.10 connects to the internet using wireless (wlan0) and it also connects to my iMac running Snow Leopard 10.6.6 over the lan (eth0). I have also configured netatalk and avahi so my Linux machine shows up in iMac thru zero conf/Bonjour (No manual connection required. Excellent writeup [here]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/"))

I'm only summarizing & adding a few tweaks to the info that has been discussed in the quotes above, since I needed both these valuable comments to get my networking adventure on the road!
Steps: 
1. I am using Network Manager. I removed Wicd Network Manager since I was looking for this option "Use this connection only for resources on this network"
2. As per quote 2, add a wired connection manually (iMac LAN). Setup is: 
[ATTACH]186869[/ATTACH]
Then configure a static IP as shown in LAN.
[ATTACH]186865[/ATTACH]
3. For this LAN connection, using NM add the route and check "Use this connection only for resources on this network". 
[ATTACH]186997[/ATTACH]
4. I left wireless as is, but here it is: 
[ATTACH]186868[/ATTACH]
The config is now 
[ATTACH]186866[/ATTACH]

5. Additionally, I configured the Network settings on the iMac. Go to System Preferences>Networking>Select 'Ethernet' on the left and for 'Configure IPv4' as Using DHCP with manual address. I used 169.254.26.55/255.255.0.0. This works with the LAN settings!

And now I am streaming movies from my RAID 5 on my Linux to the iMac over this LAN and using the internet on the Linux machine as well. Note: Somehow iMac chose this LAN interface over the wireless one! My avahi configuration does not have any interface info. BTW I need to be able to use the Linux RAID for my laptop over the wireless. Talk about a simple setup ;).

I am sure a nifty /etc/network/interfaces file config can do the same. But for now this is the Eureka moment :P!

---

