---
title: "need to manually change the active connection to Wired Connection 1 after reboot."
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by Cherag Mistry on 2012-07-14
Hi,

Every time I reboot the pc I need to change the active connection from Ifupdown (eth0) to Wired Connection 1 in the dropdown network connection menu in Edubuntu 12.04 LTS. This is because the IP address from my ISP is only received when selected the Wired Connection 1 option. Also it does not get the ip address  ( via the ISP 's dhcp server )the first time but only on the second attempt. 

is there any way in which I can set the Wired Connection 1 option as default when rebooting. Or if the Ifupdown (eth0) itself could get the Ip Address when enabled.

Please see the below output of the ifconfig -a command

eth0      Link encap:Ethernet  HWaddr 00:25:22:ec:07:58  
          inet addr:10.26.55.24  Bcast:10.26.63.255  Mask:255.255.192.0
          inet6 addr: fe80::225:22ff:feec:758/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63799415 (63.7 MB)  TX bytes:3588889 (3.5 MB)
          Interrupt:60 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1914 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:181326 (181.3 KB)  TX bytes:181326 (181.3 KB)

lxcbr0    Link encap:Ethernet  HWaddr 7a:cf:c5:64:be:29  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::78cf:c5ff:fe64:be29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:10491 (10.4 KB)

---

### Post by Kirk Schnable on 2012-07-15
Right click your network manager icon and click "Edit Connections". If you delete the other profile and set Wired Connection 1 to auto connect, it should behave the way you expect. 

If you have trouble doing this, let us know and someone will give you a hand. 

Kirk

---

### Post by Cherag Mistry on 2013-03-02
> **Kirk Schnable said:**
> Right click your network manager icon and click "Edit Connections". If you delete the other profile and set Wired Connection 1 to auto connect, it should behave the way you expect. 

If you have trouble doing this, let us know and someone will give you a hand. 

Kirk

I cannot delete the profile Ifupdown (eth0) as the option are disabled for this profile. However I can do the same for Wired Connection 1. Attached screenshots of both.

---

### Post by Cherag Mistry on 2013-03-02
Hi, It seems that I have found the solution.

Opened the network interfaces file ( in this case using text editor 'vi' ) by typing: 

[COLOR=#0000ff]vi /etc/network/interfaces[/COLOR]

(Note instead of vi you can use th editor of your choice such as 'nano' or 'emacs' etc.)

 and then commented out all lines ( by put # in the begining of the lines ) except for those that had 'lo' in them and saved it. (See below how the file looked after the action)

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet static
#  address 192.168.0.254
#  netmask 255.255.255.0


Then I restarted the network manager service by the command:

 [COLOR=#0000ff]/etc/init.d/network-manager restart[/COLOR] ( Please note that I have already typed '[COLOR=#0000ff]sudo bash[/COLOR]' in the terminal when I started working on it). In case you have not already done sudo bash, then add sudo before command [COLOR=#0000ff]/etc/init.d/network-manager restart[/COLOR]  (ie. type the command as [COLOR=#0000ff]sudo /etc/init.d/network-manager restart[/COLOR]).

This resolved my issue and now I get only 1 profile in network manager which automatically receives the ip address from my ISP ( even on restarting the pc ).

Thanks for the help.

---

