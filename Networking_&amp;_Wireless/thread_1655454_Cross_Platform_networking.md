---
title: "Cross Platform networking?"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2010-12-29
Hey all, i would like to network my to computers together, using an ethernet switch. The main machine is running Ubuntu 10.4 LTS, and the secondary machine is running Microsoft Windows XP. 

Can anyone point me in the right direction or direct me to a useful guide?

Thanks, 

SlashWannabe94

---

### Post by PatchesTheCaveman on 2010-12-29
Hi slashwannabe94!

What exactly do you want to do?  Share the Internet connection from one computer to the other?  Share files between them?  Something else?

---

### Post by slashwannabe94 on 2010-12-29
Hi man, i want to be able to share the internet connection from my usb hsdpa T-mobile dongle, between my ubuntu 10.4 system and my windows xp system. while having these machines networked with access to each others files and folders. 

But the only networking i have ever done is ssh in terminal, that is it. 

Can you help?

---

### Post by PatchesTheCaveman on 2010-12-29
Okay, first you'll want to connect your T-Mobile mobile broadband connection on your Ubuntu laptop.  If you haven't done that yet, there are instructions here:  [https://help.ubuntu.com/10.10/internet/C/connecting-mobile.html](https://help.ubuntu.com/10.10/internet/C/connecting-mobile.html)

I've used a Verizon mobile broadband USB dongle with Ubuntu before and it was pretty much just plug and play.

Once you're all connected, you can install the software you need. Go to Applications > Accessories > Terminal on your top panel.  Then, in the black box that pops up, type this in and press Enter:
```
sudo apt-get install system-config-samba firestarter
```
Enter your password and say yes to install those programs and all the other programs they'll need to function.

Now you can set up Internet sharing.  Plug your Ubuntu machine into the switch.  Then go to Applications > Internet > Firestarter.  I believe the Welcome to Firestarter screen will pop up when you first run it but if not go to Firewall > Run Wizard.

Click Forward.  Under *Please select your Internet connected network device* choose the one labeled *ppp0*.  Make sure both *Start the firewall on dial-out* and *IP Address is assigned by DHCP* are checked.  Click Forward.

Check *Enable Internet connection sharing*.  Choose *eth0* as the *Local area nework device*.  Check *Enable DHCP for local network*.  Click Forward.

Make sure *Start firewall now* is checked and click Save.  Your Ubuntu machine is now configured to share the Internet with your Windows XP machine and any others you see fit to plug into the switch.  At this point you should be able to plug in your Windows XP machine into the switch and it will automatically recieve an IP address from the Ubuntu machine and hook up to its Internet connection.

You can now go to System > Administration > Samba to set up all the folders you want to share from the Ubuntu machine.  Your Ubuntu machine should then show up when you go to Start > My Network Places on the Windows XP machine and give you access to all the folders you have shared.

To share files from your Windows XP machine, right-click on the folder you want to share in Windows Explorer, click Properties, and go to the Sharing tab and turn on sharing of that folder.  To access those folders on your Ubuntu machine, go to Places > Network on the top panel.

---

### Post by slashwannabe94 on 2010-12-30
Thank you so much man :) I will do this right away :P

---

### Post by slashwannabe94 on 2010-12-30
I have done what you said man, but it won't let me enable DHCP man. It is just greyed out.

---

### Post by PatchesTheCaveman on 2010-12-30
Finish the wizard like I said without enabling DHCP.

After that, go to Edit > Preferences.  Click *Network Settings* under *Firewall* on the left.  Check *Enable DHCP for the local network*.  Click on the arrow next to *DHCP server details* to reveal the additional DHCP options.  Click the *Create new DHCP configuration* radio button.  Leave the rest of the settings at their default.

While you're in there, verify that *Enable internet connection sharing* is checked and that your *Internet connected network device* has **(ppp0)** at the end and that your *Local network connected device* has **(eth1)** at the end.

After you've done all that, click *Accept*.  Then go to Firewall > Start Firewall.

Now you can plug in your Windows computer to the switch and it should automatically get its network configuration and be able to access the Internet.

---

### Post by slashwannabe94 on 2010-12-31
Tried that dude, and all it says is "Failed to start the firewall, An unknown error occurred, Please check your network device settings and make sure your internet connection is active"

Could this have something to do with my network settings on eth0?

I have it set to shared to other computers. 

I have tried changing it to "Automatic DHCP", but it then stops me from browsing the net when the eth0 is connected. 

I am hitting brick walls here man. Please help me thus further?

---

### Post by PatchesTheCaveman on 2010-12-31
Go to Applications > Accessories > Terminal.  Type in these commands, pressing Enter after each line:
```
ifconfig -a
cat /etc/dhcp3/dhcpd.conf
sudo ufw show raw
sudo grep -i dhcp /var/log/syslog
```

Copy all the information that spits out and paste it in a reply to this thread.  That will give us all your configuration information so we can see where things might be going wrong.

---

### Post by slashwannabe94 on 2011-01-01
Output of the commands listed:

ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:1c:25:53:c6:6e  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe53:c66e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:12813 (12.8 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16128 (16.1 KB)  TX bytes:16128 (16.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:178.105.101.254  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:118928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:165012861 (165.0 MB)  TX bytes:2852830 (2.8 MB)



cat: /etc/dhcp3/dhcpd.conf

cat: /etc/dhcp3/dhcpd.conf: No such file or directory

sudo ufw show raw

IPV4 (raw):
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       149.254.230.7        0.0.0.0/0           tcp flags:!0x17/0x02 
     204    26590 ACCEPT     udp  --  *      *       149.254.230.7        0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       149.254.192.126      0.0.0.0/0           tcp flags:!0x17/0x02 
      13     1465 ACCEPT     udp  --  *      *       149.254.192.126      0.0.0.0/0           
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
       0        0 DROP       all  --  ppp0   *       0.0.0.0/0            255.255.255.255     
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
       0        0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
  118756 165002144 INBOUND    all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
       0        0 INBOUND    all  --  eth0   *       0.0.0.0/0            10.42.43.1          
       0        0 INBOUND    all  --  eth0   *       0.0.0.0/0            178.105.101.254     
       4     1018 INBOUND    all  --  eth0   *       0.0.0.0/0            10.42.43.255        
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
       0        0 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
       0        0 OUTBOUND   all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            10.42.43.0/24       state RELATED,ESTABLISHED 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            10.42.43.0/24       state RELATED,ESTABLISHED 
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       178.105.101.254      149.254.230.7       tcp dpt:53 
     208    13175 ACCEPT     udp  --  *      *       178.105.101.254      149.254.230.7       udp dpt:53 
       0        0 ACCEPT     tcp  --  *      *       178.105.101.254      149.254.192.126     tcp dpt:53 
      13      826 ACCEPT     udp  --  *      *       178.105.101.254      149.254.192.126     udp dpt:53 
       0        0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
      11      959 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
   60807  2856951 OUTBOUND   all  --  *      ppp0    0.0.0.0/0            0.0.0.0/0           
       4     1018 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (4 references)
    pkts      bytes target     prot opt in     out     source               destination         
  118752 165001840 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       4      304 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:138 
       4     1018 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
       0        0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
    pkts      bytes target     prot opt in     out     source               destination         
       1      154 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
   60656  2850069 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       3      228 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
     151     7518 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 2 packets, 532 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     367    20457 MASQUERADE  all  --  *      ppp0    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 380 packets, 21948 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 118977 packets, 165031217 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 118977 packets, 165031217 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 61043 packets, 2872929 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 61036 packets, 2872988 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


IPV6:
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


And the last command. 


Jan  1 04:01:53 static-desktop NetworkManager: <debug> [1293854513.221679] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  1 04:01:53 static-desktop dnsmasq[2713]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  1 04:01:53 static-desktop dnsmasq-dhcp[2713]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  1 04:04:55 static-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  1 04:04:55 static-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  1 04:04:55 static-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 04:04:55 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan  1 04:04:57 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 04:04:57 static-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  1 04:04:57 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Jan  1 04:04:57 static-desktop NetworkManager: <info>    hostname 'dhcppc0'
Jan  1 04:20:57 static-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 3480
Jan  1 04:21:05 static-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  1 04:21:05 static-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  1 04:21:05 static-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 04:21:05 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan  1 04:21:05 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 04:21:09 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 04:21:17 static-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan  1 04:21:22 static-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan  1 04:21:22 static-desktop dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
Jan  1 04:21:22 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 04:21:22 static-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  1 04:21:22 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan  1 04:21:22 static-desktop NetworkManager: <info>    hostname 'dhcppc0'
Jan  1 04:22:37 static-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 5509
Jan  1 04:22:45 static-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  1 04:22:45 static-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  1 04:22:45 static-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 04:22:45 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan  1 04:22:45 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 04:22:50 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 04:22:56 static-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  1 04:22:59 static-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan  1 04:23:04 static-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  1 04:23:04 static-desktop dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
Jan  1 04:23:04 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 04:23:04 static-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  1 04:23:04 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan  1 04:23:04 static-desktop NetworkManager: <info>    hostname 'dhcppc0'
Jan  1 04:32:31 static-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 5823
Jan  1 04:33:43 static-desktop NetworkManager: <debug> [1293856423.351890] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  1 04:33:43 static-desktop dnsmasq[7700]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  1 04:33:43 static-desktop dnsmasq-dhcp[7700]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  1 04:33:47 static-desktop NetworkManager: <debug> [1293856427.555830] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  1 04:33:47 static-desktop dnsmasq[8182]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  1 04:33:47 static-desktop dnsmasq-dhcp[8182]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  1 14:57:15 static-desktop kernel: [    6.091099] type=1505 audit(1293893832.637:3):  operation="profile_load" pid=562 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  1 14:57:18 static-desktop kernel: [   12.196893] type=1505 audit(1293893838.743:7):  operation="profile_replace" pid=1119 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  1 14:57:21 static-desktop NetworkManager: <debug> [1293893841.568806] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  1 14:57:21 static-desktop dnsmasq[1336]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  1 14:57:21 static-desktop dnsmasq-dhcp[1336]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h

---

### Post by slashwannabe94 on 2011-01-01
I did find this file /etc/dhcp3/dhclient.conf

I think that is /etc/dhcp3/dhcpd.conf

I'm probably wrong haha.

---

### Post by PatchesTheCaveman on 2011-01-01
I don't think you have the DHCP server package installed, which is odd because it should have installed with Firestarter.  Open a terminal and run this command:
```
sudo apt-get install dhcp3-server
```

Then go back into Firestarter and make sure the DHCP settings are still present and then stop and start the firewall.

---

### Post by astrob0t on 2011-01-01
hello PatchesTheCaveman

i too am facing the same issue here..but the main prob is that
1. i am in a home network of 50 PCs connected through switches(no routers and other complex thingys)
2. most of the pcs run windows. while i run ubuntu 10.10.
3. all the windows pc have been assigned static ips 169.254.x.x in order to enable simple file sharing and playing lan games.
4. i want to share my internet connection with a windows user as well as be able to access the shared folders on the other pcs..

so would the above discussed procedure help me out..

i am really freaked out as i dont know if a system restore option exists in ubuntu or not..and everytime something goes wrong i end up installing ubuntu all over again..

plz suggest..

---

### Post by slashwannabe94 on 2011-01-01
I have done what you said dude and still receive the "please check your network device settings and make sure your internet connection is active" error man. 

I have done some research and came up with this. 

[https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3](https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3)

It says stuff about iptables etc. 

Would this help? 

or am i still doing something wrong... 

Thanks, 

SlashWannabe94

---

### Post by astrob0t on 2011-01-01
> **slashwannabe94 said:**
> I have done what you said dude and still receive the "please check your network device settings and make sure your internet connection is active" error man. 

I have done some research and came up with this. 

[https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3](https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3)

It says stuff about iptables etc. 

Would this help? 

or am i still doing something wrong... 

Thanks, 

SlashWannabe94


hello SlashWannabe94

i think the tutorial u discoverd is grt..but i dont think that would work out in your case(as well as mine)..because it says that the server setup requires 2 NIC cards ..but in ur case there's one ethernet card and one dial up modem (if i am not mistaken)..i dont think dial up modems like the t-mobile usb dongle can be configured thru dhcp
so lets hope thers's another suitable solution out there..

---

### Post by PatchesTheCaveman on 2011-01-01
I used a Verizon USB dongle with the setup I described and it worked fine.

Open a terminal, and start Firestarter from it:
```
gksudo firestarter
```

Try and stop and start your firewall.  Error messages should appear in the terminal window.  Copy and paste them into a reply to this thread.

---

### Post by slashwannabe94 on 2011-01-01
Here are the error reports you requested man. 

Firewall started
Failed to start DHCP server

---

### Post by slashwannabe94 on 2011-01-01
I am still having trouble man. When i have my eth0 connected aswell as my t-mobile ppp0 device connected, i cannot browse the web. but when i disconnect the eth0 i can browse the net again.... 

Why is all of this happening? All i ever do is run into errors.

---

### Post by PatchesTheCaveman on 2011-01-01
Run these commands (again) and copy/paste the output:
```
cat /etc/dhcp3/dhcpd.conf
sudo cat /var/log/syslog | grep -i dhcp
ifconfig -a
```

---

### Post by slashwannabe94 on 2011-01-01
Output of "cat /etc/dhcp3/dhcpd.conf"

# DHCP configuration generated by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 16.128.142.9 netmask 16.128.142.9 {
    option routers 16.128.142.9;
    option subnet-mask 16.128.142.9;
    option domain-name-servers 8.8.8.8, 149.254.230.7, 149.254.192.126;
    option ip-forwarding off;
    range dynamic-bootp 192.168.0.100 192.168.0.254;
    default-lease-time 21600;
    max-lease-time 43200;
}

------------------------------------------------------------------------------------------------

Output of "sudo cat /var/log/syslog | grep -i dhcp"

Jan  1 20:22:46 static-desktop kernel: [    4.663478] type=1505 audit(1293913363.205:3):  operation="profile_load" pid=520 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  1 20:22:49 static-desktop kernel: [   10.805714] type=1505 audit(1293913369.350:7):  operation="profile_replace" pid=1082 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  1 20:22:53 static-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  1 20:22:53 static-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  1 20:22:53 static-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 20:22:53 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan  1 20:22:55 static-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan  1 20:22:55 static-desktop dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
Jan  1 20:22:55 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 20:22:55 static-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  1 20:22:55 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan  1 20:22:55 static-desktop NetworkManager: <info>    hostname 'dhcppc0'
Jan  1 20:24:30 static-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1286
Jan  1 20:24:30 static-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  1 20:24:30 static-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  1 20:24:30 static-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 20:24:30 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan  1 20:24:33 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 20:24:33 static-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  1 20:24:33 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Jan  1 20:24:33 static-desktop NetworkManager: <info>    hostname 'dhcppc0'
Jan  1 20:24:34 static-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1816
Jan  1 20:28:44 static-desktop kernel: [    9.225273] type=1505 audit(1293913723.771:3):  operation="profile_load" pid=512 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  1 20:28:44 static-desktop kernel: [    9.631755] type=1505 audit(1293913724.179:7):  operation="profile_replace" pid=859 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  1 22:02:56 static-desktop kernel: [ 5661.668038] type=1505 audit(1293919376.218:25):  operation="profile_replace" pid=30933 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  1 22:09:16 static-desktop kernel: [    7.543347] type=1505 audit(1293919754.086:3):  operation="profile_load" pid=570 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  1 22:09:18 static-desktop kernel: [   11.659614] type=1505 audit(1293919758.202:6):  operation="profile_replace" pid=943 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  1 22:13:50 static-desktop kernel: [  284.018307] type=1505 audit(1293920030.563:15):  operation="profile_load" pid=2078 name="/usr/sbin/dhcpd3"
Jan  1 22:13:50 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  1 22:13:50 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  1 22:13:50 static-desktop dhcpd: All rights reserved.
Jan  1 22:13:50 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 22:13:50 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  1 22:13:50 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  1 22:13:50 static-desktop dhcpd: All rights reserved.
Jan  1 22:13:50 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 22:13:50 static-desktop dhcpd: Wrote 0 leases to leases file.
Jan  1 22:13:50 static-desktop dhcpd: 
Jan  1 22:13:50 static-desktop dhcpd: Not configured to listen on any interfaces!
Jan  1 22:15:06 static-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  1 22:15:07 static-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  1 22:15:07 static-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 22:15:07 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan  1 22:15:09 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 22:15:09 static-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  1 22:15:09 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Jan  1 22:15:09 static-desktop NetworkManager: <info>    hostname 'dhcppc0'
Jan  1 22:15:10 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:15:10 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  1 22:15:10 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  1 22:15:10 static-desktop dhcpd: All rights reserved.
Jan  1 22:15:10 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 22:15:10 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:15:12 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:15:12 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  1 22:15:12 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  1 22:15:12 static-desktop dhcpd: All rights reserved.
Jan  1 22:15:12 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 22:15:12 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:15:26 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:15:26 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  1 22:15:26 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  1 22:15:26 static-desktop dhcpd: All rights reserved.
Jan  1 22:15:26 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 22:15:26 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:16:21 static-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2432
Jan  1 22:18:39 static-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  1 22:18:39 static-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  1 22:18:39 static-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 22:18:39 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan  1 22:18:42 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  1 22:18:42 static-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  1 22:18:42 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Jan  1 22:18:42 static-desktop NetworkManager: <info>    hostname 'dhcppc0'
Jan  1 22:18:43 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:18:43 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  1 22:18:43 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  1 22:18:43 static-desktop dhcpd: All rights reserved.
Jan  1 22:18:43 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 22:18:43 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:18:49 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:18:49 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  1 22:18:49 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  1 22:18:49 static-desktop dhcpd: All rights reserved.
Jan  1 22:18:49 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  1 22:18:49 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  1 22:19:43 static-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 3262
Jan  2 01:58:06 static-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  2 01:58:06 static-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  2 01:58:06 static-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  2 01:58:07 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan  2 01:58:07 static-desktop dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Jan  2 01:58:07 static-desktop dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  2 01:58:07 static-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Jan  2 01:58:07 static-desktop NetworkManager: <info>    hostname 'dhcppc0'
Jan  2 01:58:09 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  2 01:58:09 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 01:58:09 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 01:58:09 static-desktop dhcpd: All rights reserved.
Jan  2 01:58:09 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  2 01:58:09 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  2 01:58:16 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  2 01:58:16 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 01:58:16 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 01:58:16 static-desktop dhcpd: All rights reserved.
Jan  2 01:58:16 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  2 01:58:16 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  2 01:58:22 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  2 01:58:22 static-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 01:58:22 static-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 01:58:22 static-desktop dhcpd: All rights reserved.
Jan  2 01:58:22 static-desktop dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  2 01:58:22 static-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 16.128.142.9 netmask 16.128.142.9
Jan  2 01:59:14 static-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 8066

------------------------------------------------------------------------------------------------------------------------------

Output of "ifconfig -a" 

eth0      Link encap:Ethernet  HWaddr 00:1c:25:53:c6:6e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe53:c66e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9220 (9.2 KB)  TX bytes:29807 (29.8 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24620 (24.6 KB)  TX bytes:24620 (24.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:178.99.136.233  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:90 (90.0 B)  TX bytes:157 (157.0 B)
--------------------------------------------------------------------------------------------------------

That's it all man, still cannot browse the net when both interfaces are connected though.

---

### Post by slashwannabe94 on 2011-01-01
Hey __aviasit, it can be done with a t-mobile dongle because a late friend of mine set it up for me, all using terminal, iptables, and firestarter. but unfortunately, i am no where near as good as he was. but thank you for the reply dude, input is much appreciated.

---

### Post by astrob0t on 2011-01-02
> **slashwannabe94 said:**
> Hey __aviasit, it can be done with a t-mobile dongle because a late friend of mine set it up for me, all using terminal, iptables, and firestarter. but unfortunately, i am no where near as good as he was. but thank you for the reply dude, input is much appreciated.


hi slashwannabe94
if u mean ur problem is solved, then would u please elaborate the procedure thru a step by step process..
initially i hesitated to try the process discussed at post #4..but somehow i decided to try it but got the same errors as of urs..

plz help/

---

### Post by slashwannabe94 on 2011-01-02
I can't help you man, i am hoping PatchesTheCaveman can help me out.

---

### Post by slashwannabe94 on 2011-01-02
Can someone please help :(

---

### Post by PatchesTheCaveman on 2011-01-02
Sorry, this slipped by me somehow.  Your dhcpd.conf file is so wrong its ridiculous.  I don't know why firestarter did it that way.

Change /etc/dhcp3/dhcpd.conf to say this:
```

ddns-update-style interim;
ignore client-updates;

subnet 192.168.1.0 netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option domain-name-servers 8.8.8.8, 149.254.230.7, 149.254.192.126;
option ip-forwarding off;
range dynamic-bootp 192.168.1.100 192.168.1.254;
default-lease-time 21600;
max-lease-time 43200;
}
```

Then, right-click on your network icon, click *Edit Connections*, click on *eth0*, click *Edit*, switch to the *IPv4 Settings* tab, change *Method* to **Manual**, click *Add* next to the white box under *Addresses*, type in **192.168.1.1**, leave everything else alone and click *Apply* then *Close*.

Then, go back into Firestarter and stop and start the firewall.  Everything should work now, hopefully.

---

### Post by astrob0t on 2011-01-03
> **PatchesTheCaveman said:**
> Sorry, this slipped by me somehow.  Your dhcpd.conf file is so wrong its ridiculous.  I don't know why firestarter did it that way.

Change /etc/dhcp3/dhcpd.conf to say this:
```

ddns-update-style interim;
ignore client-updates;

subnet 192.168.1.0 netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option domain-name-servers 8.8.8.8, 149.254.230.7, 149.254.192.126;
option ip-forwarding off;
range dynamic-bootp 192.168.1.100 192.168.1.254;
default-lease-time 21600;
max-lease-time 43200;
}
```

Then, right-click on your network icon, click *Edit Connections*, click on *eth0*, click *Edit*, switch to the *IPv4 Settings* tab, change *Method* to **Manual**, click *Add* next to the white box under *Addresses*, type in **192.168.1.1**, leave everything else alone and click *Apply* then *Close*.

Then, go back into Firestarter and stop and start the firewall.  Everything should work now, hopefully.


the above step was fine..no errors so far..the firewall started and stopped without any errors..
so now what to do on the windows pc to enable them to access internet??

---

### Post by PatchesTheCaveman on 2011-01-03
They should Just Work.  But if they were already booted and plugged into the network when you fixed the configuration you will need to force them to get a new IP address.

Open the Command Prompt from the Start Menu or by pressing Windows+R and typing *cmd* and pressing Enter, and run these commands:
```
ipconfig /release
ipconfig /renew
```

---

### Post by astrob0t on 2011-01-03
my  /etc/dhcp3/dhcpd.conf looks like this

```

# DHCP configuration generated by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 169.254.0.0 netmask 255.255.0.0 {
	option routers 169.254.169.254;
	option subnet-mask 255.255.0.0;
	option domain-name-servers 4.2.2.1, 4.2.2.2;
	option ip-forwarding off;
	range dynamic-bootp 169.254.170.250 169.254.170.255;
	default-lease-time 21600;
	max-lease-time 43200;
}
```

so what should i do in the windows system ..
plz illustrate an example static ip  such that the windows system is able to access the shared folders on other pcs with static ip 169.254.x.x as well as access internet from the ubuntu system.

---

### Post by PatchesTheCaveman on 2011-01-03
The 169.254.0.0/16 subnet is reserved by RFC3927 for link-local addresses used for stateless IPv4 address autoconfiguration.  A lot of programs automatically assign addresses in this block, including Windows Vista and 7 and the avahi daemon in many Linux distributions.  So you really shouldn't use those IP addresses unless you want a buttload of headaches.

Follow my instructions in post #25 to configure NetworkManager and DHCP to use an address in one of the private IPv4 address spaces reserved in RFC1918.

---

### Post by spiky001 on 2011-01-03
I would like to try this set up, Is there a reason to use firestarter? can it be done without it, I use gufw.

---

### Post by slashwannabe94 on 2011-01-03
Hey PatchesTheCaveman, i'm still having trouble man. I have edited the file as you said. But when i try to manually edit the eth0 with network manager, the apply button is just greyed out. i have even tried running it as root and no luck... 

Please don't give up on me dude. 

Thanks, 

SlashWannabe94

---

### Post by PatchesTheCaveman on 2011-01-03
spiky001:  I'm not familiar with that software, so I couldn't tell you how to do it, but it certainly should be possible.  Both programs are just frontends for *ufw*.

slashwannabe94:  If you made any change to *eth0*, the *Apply* button should not be greyed out.  Make sure your screen looks like the atached screenshot.

---

### Post by slashwannabe94 on 2011-01-03
Hello man, i have done as you said again and still cannot do as you said. i have attached a screenshot of my network manager.

---

### Post by PatchesTheCaveman on 2011-01-03
You accidentally added a couple blank lines to the bottom.  Delete them so only the top line exists and it should work.

---

### Post by slashwannabe94 on 2011-01-03
Hey man, it works :D :D :D :D The firewall starts with no errors man :D 

I have restarted my Windows XP machine, and it is connected to the local network, with an IP address of 192.168.1.3, while the Linux machine has an IP address of 192.168.1.2. 

Yet Windows XP automatically tries to dial the T-mobile device. It is definitely picking it up, but does not connect. the error i receive is this.

Error Connecting to T-Mobile UK

Error 797: A connection to the remote computer could not be established because the modem was not found or was busy. For further assistance, click more info or search help and support center for this error number. 

Why did that pop up dude? 

Thanks for all the help you have gave me so far man :) 

SlashWannabe94

---

### Post by PatchesTheCaveman on 2011-01-03
Go to Control Panel > Internet Options and go the the Connections tab and hit the Never dial a connection radio button.

You could also delete the old T-Mobile connection out of Control Panel > Network Connections since you probably don't need it anymore.

Glad to hear everything's working okay now!  :-D

---

### Post by slashwannabe94 on 2011-01-03
It's all operational now man. Thank you so much for all your help. Wish i had real friends in person like you man.

---

### Post by slashwannabe94 on 2011-01-03
WHOAAAA
 
Just had a major mess up man. I restarted both computers and now my ubuntu machine, has forgoten all connections including my "auto eth0" and t-mobile device. I cannot even access them as the network manager applet 0.8 that resides on my top panel has dissapeared. when i try to add it back it just leaves a little black barley visable icon. 
 
What the hell has happened man?
 
It was all working before i restarted my machines?

---

### Post by PatchesTheCaveman on 2011-01-03
That's *no bueno*.  

Try giving her another reboot to see if it goes back to normal.  You might have to recreate and reconfigure your *eth0* and T-Mobile connections.

Ordinarily I'd tell you to switch to *wicd*, but that doesn't support mobile broadband connections yet.

---

### Post by slashwannabe94 on 2011-01-03
damn haha. i have rebooted several times and still no luck. it won't even let me create connections, with network manager. :'(

---

### Post by PatchesTheCaveman on 2011-01-03
Let's try completely erasing and reinstalling NetworkManager.  First, do this to make sure you have all the neccessary packages downloaded:
```
sudo apt-get --reinstall network-manager network-manager-gnome
```

(See if that fixes it first by some miracle.  If not, go on.)

Now, completely remove NetworkManager:
```
sudo apt-get purge network-manager
```

Then, reinstall it:
```
sudo apt-get install network-manager-gnome
```

---

### Post by slashwannabe94 on 2011-01-03
I cannot use the repository man, as the connection has been wiped and will not let me make any new ones. is their a way to download the network manager gnome package, so i can then put it on a usb stick and then install it to the ubuntu machine? 
 
A site with this package availbile etc?

---

### Post by spiky001 on 2011-01-03
Just a thought can you get it off the cd?

---

### Post by slashwannabe94 on 2011-01-03
I don't know, but good idea, i will take a look haha.

---

### Post by spiky001 on 2011-01-03
Yo would have to enale cd in software sources

---

### Post by PatchesTheCaveman on 2011-01-03
Here are the links to the necessary packages:
[http://us.archive.ubuntu.com/ubuntu/pool/main/m/mobile-broadband-provider-info/mobile-broadband-provider-info_20100910-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mobile-broadband-provider-info/mobile-broadband-provider-info_20100910-1_all.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.1+git.20100810t184654.ab580f4-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.1+git.20100810t184654.ab580f4-0ubuntu2_i386.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.1+git.20100809t190028.290dc70-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.1+git.20100809t190028.290dc70-0ubuntu3_i386.deb)

To install them, run ```
sudo dpkg -i
``` on them in that order, or just double-click them in Nautilus.  If you install them in the order listed, you shouldn't get any dependency errors.

If you get one for a package I didn't provide, let me know what it is and I can link you to it.

---

### Post by slashwannabe94 on 2011-01-03
Thanks for that man, but i got a dependency error, "Error: Dependency is not satisfiable: libdbus-glib-1-2 (>=0.88)"
 
That was the error man. 
 
I assume i just need to install that package in order for the others to work.

---

### Post by newcityboy on 2011-01-03
Hello I am trying to do something similar. I am using an old Dell 1405 with 10.10/Vista and its wireless. And a venerable compaq desktop running xp/10.10 I have no hardline net here but I do have wireless. I am trying to hook the desktop to the net using the laptops wireless. I have gone over the post here and have had little luck. Firestarter returns me an error message just like the others but it also tells me that eth0 is not responding. I will post as much of the outputs that you requested of the other posters. I tried to sift through the lines to find something wrong but I just do not have the knowledge to make any sense of it. I know a good deal of it should be different numbers and such but I don't know enough to find what is wrong.

I ran.
```
sudo apt-get install dhcp3-server
```gksudo firestarter

```
Internal network device eth0 is not ready. Aborting..
```My  /etc/dhcp3/dhcpd.conf is this. Which is read only and I don't know how to overwrite it. If need be please give me an idea how to.

```
# DHCP configuration generated by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 24.76.183.8 netmask 24.76.183.8 {
    option routers 24.76.183.8;
    option subnet-mask 24.76.183.8;
    option domain-name-servers <dynamic>;
    option ip-forwarding off;
    range dynamic-bootp 192.168.0.100 192.168.0.254;
    default-lease-time 21600;
    max-lease-time 43200;
}
```ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr 00:14:22:a9:d3:19  
          inet6 addr: fe80::214:22ff:fea9:d319/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8250 (8.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:6c:70:f1  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe6c:70f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1378620 (1.3 MB)  TX bytes:202596 (202.5 KB)
```cat /etc/dhcp3/dhcpd.conf

```
cat: /etc/dhcp3/dhcpd.conf: No such file or directory
```sudo ufw show raw

```
IPV4 (raw):
Chain INPUT (policy ACCEPT 1188 packets, 1201807 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1013 packets, 163167 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 410 packets, 79168 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 154 packets, 10383 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 154 packets, 10383 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 1589 packets, 1279471 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 1187 packets, 1201641 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1012 packets, 163001 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1066 packets, 171271 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


IPV6:
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

```sudo grep -i dhcp /var/log/syslog

```

Jan  3 14:43:48 ubuntu NetworkManager[956]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 14:43:49 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 14:43:49 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 14:43:49 ubuntu NetworkManager[956]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 14:43:49 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 14:43:52 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan  3 14:44:00 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan  3 14:44:10 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan  3 14:44:20 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Jan  3 14:44:34 ubuntu NetworkManager[956]: <warn> (eth0): DHCPv4 request timed out.
Jan  3 14:44:34 ubuntu NetworkManager[956]: <info> (eth0): canceled DHCP transaction, DHCP client pid 7361
Jan  3 14:47:04 ubuntu NetworkManager[956]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 14:47:04 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 14:47:04 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 14:47:04 ubuntu NetworkManager[956]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 14:47:04 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 14:47:07 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan  3 14:47:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Jan  3 14:47:25 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Jan  3 14:47:32 ubuntu NetworkManager[956]: <info> (eth0): canceled DHCP transaction, DHCP client pid 8143
Jan  3 14:47:32 ubuntu NetworkManager[956]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 14:47:32 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 14:47:32 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 14:47:32 ubuntu NetworkManager[956]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 14:47:32 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 14:47:35 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan  3 14:47:42 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jan  3 14:47:51 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  3 14:48:05 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  3 14:48:06 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 192.168.0.1 port 67
Jan  3 14:48:07 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1
Jan  3 14:48:07 ubuntu NetworkManager[956]: <info> (wlan0): DHCPv4 state changed bound -> renew
Jan  3 14:48:18 ubuntu NetworkManager[956]: <warn> (eth0): DHCPv4 request timed out.
Jan  3 14:48:18 ubuntu NetworkManager[956]: <info> (eth0): canceled DHCP transaction, DHCP client pid 8264
Jan  3 15:04:00 ubuntu kernel: [   15.512611] type=1400 audit(1294092228.908:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=512 comm="apparmor_parser"
Jan  3 15:04:00 ubuntu kernel: [   27.350339] type=1400 audit(1294092240.748:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=986 comm="apparmor_parser"
Jan  3 15:04:09 ubuntu NetworkManager[1186]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 15:04:09 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 15:04:09 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 15:04:09 ubuntu NetworkManager[1186]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 15:04:09 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 15:04:12 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan  3 15:04:16 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan  3 15:04:24 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Jan  3 15:04:32 ubuntu NetworkManager[1186]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 15:04:32 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 15:04:32 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 15:04:32 ubuntu NetworkManager[1186]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan  3 15:04:32 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 255.255.255.255 port 67
Jan  3 15:04:33 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1
Jan  3 15:04:33 ubuntu NetworkManager[1186]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan  3 15:04:42 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jan  3 15:04:51 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  3 15:04:55 ubuntu NetworkManager[1186]: <warn> (eth0): DHCPv4 request timed out.
Jan  3 15:04:55 ubuntu NetworkManager[1186]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1679
Jan  3 15:11:04 ubuntu NetworkManager[1186]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 15:11:04 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 15:11:04 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 15:11:04 ubuntu NetworkManager[1186]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 15:11:04 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 15:11:07 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan  3 15:11:15 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jan  3 15:11:24 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jan  3 15:11:36 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  3 15:11:50 ubuntu NetworkManager[1186]: <warn> (eth0): DHCPv4 request timed out.
Jan  3 15:11:50 ubuntu NetworkManager[1186]: <info> (eth0): canceled DHCP transaction, DHCP client pid 4493

```

---

### Post by PatchesTheCaveman on 2011-01-03
[http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.88-2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.88-2_i386.deb)

---

### Post by PatchesTheCaveman on 2011-01-03
newcityboy:  Follow my instructions in post 25 to reconfigure your eth0 connection with the appropriate IP address.

Also, edit your dhcpd.conf in the manner described.  To do so, run:
```
gksudo gedit /etc/dhcp3/dhcpd.conf
```

---

### Post by slashwannabe94 on 2011-01-03
Done that dude and it wants another package. network-manager requsts "libnm-glib2". i have a feeling that it's going to ask me for tons of packages. We can get the internet connection sharing done, but once done, my network manager messes up... 
 
and network-manager-gnome requests "libgconf2-4"
What do you reccomend ? 
 
re-installation of ubuntu, switch distro? 
 
Or keep going and see how many packages this thing requests?

---

### Post by newcityboy on 2011-01-03
No change on my end. Same error as before.

My wireless is not getting interupted when I plug in the CAT5 in.

---

### Post by PatchesTheCaveman on 2011-01-03
It's up to you.  If you think a reinstall would be easier go for it.

If you want to keep going I'll tell you how to figure out the package download yourself instead of having to ask me every time.  ;-)

For instance, since it asked for "libgconf2-4", you would run this command:
```
apt-cache show libgconf2-4
```

It will output a bunch of info, but the bolded line is the one you want:
```
Package: libgconf2-4
Priority: optional
Section: libs
Installed-Size: 484
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Josselin Mouette <joss@debian.org>
Architecture: i386
Source: gconf
Version: 2.31.91-0ubuntu3.1
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libglib2.0-0 (>= 2.25.16), libldap-2.4-2 (>= 2.4.7), liborbit2 (>= 1:2.14.10), libxml2 (>= 2.7.4), gconf2-common (>= 2.31), gconf2-common (<< 2.32)
Conflicts: libbonobo2-0 (<< 2.24)
**Filename: pool/main/g/gconf/libgconf2-4_2.31.91-0ubuntu3.1_i386.deb**
Size: 153030
MD5sum: 48af324e829fe468036cf68373aac832
SHA1: 70b4d14c5f5130601cdf9998324c3c84876e882f
SHA256: 9babce18d392cb73e27817aa94842023f90b926255651da640b1a0f0f4aabcf4
Description: GNOME configuration database system (shared libraries)
 GConf is a configuration database system for storing application
 preferences. It supports default or mandatory settings set by the
 administrator, and changes to the database are instantly applied to all
 running applications. It is written for the GNOME desktop but doesn't
 require it.
 .
 This package contains the shared libraries and the GConf daemon.
Homepage: [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, ubuntu-uec-live, kubuntu-dvd-live, edubuntu-desktop, edubuntu-desktop-kde, edubuntu-uec-live, xubuntu-desktop, mythbuntu-backend-master, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend, mythbuntu-frontend, ubuntu-netbook
```

That's the filename line.  Append the Ubuntu download archive URL to the front of it:
```
http://gb.archive.ubuntu.com/ubuntu/
```

And you get ```
[http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gconf/libgconf2-4_2.31.91-0ubuntu3.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gconf/libgconf2-4_2.31.91-0ubuntu3.1_i386.deb)
```
the full download link.

Good luck!

If it gets to be too much, and you have a working Ubuntu CD, using spiky001's CD method would work fine too.

---

### Post by slashwannabe94 on 2011-01-03
thanks man, i will do this. you have been such a great help man. 
 
Many thanks, 
 
SlashWannabe94

---

### Post by PatchesTheCaveman on 2011-01-03
newcityboy:  I'm not showing any rules in your ufw output.  Try going into Firestarter, go to the Firewall menu and hit Run Wizard, and reconfiguring everything from scratch.  If it still doesn't work, go to Edit > Preferences, hit Network Settings on the left, and expand "DHCP server details"  Then take a screenshot (just press PrintScreen on your keyboard) of that screen and attach it to a post here.

If you can use Shotwell or another image program to crop it down to just that window.  I'm away for the holidays and am stuck on a dialup connection at present so that'll help me help you faster.  :-)

---

### Post by newcityboy on 2011-01-03
I just tired running *apt-cache show* and got 

```

E: No packages found

```might this be a source of the problem?

standby.

---

### Post by PatchesTheCaveman on 2011-01-03
newcityboy:  That was just for slashwannabe94.  He has a different problem than you.

---

### Post by newcityboy on 2011-01-03
Just trying anything I can in the lag time. Here is the photo. The DHCP was greyed out. I followed a link explaining it and it said something about me not having the underlying system needed. Funny thing though is it is greyed out in the wizard but not in the preferences. I included a little of what it said as well.

**[SIZE=1]Enabling the DHCP Service[/SIZE]**

    [SIZE=1]*Note*: Firestarter does not itself include a DHCP server, it depends on the underlying system to provide this feature. **The system does not need to have the DHCP server configured, or running.** It is sufficient that the *dhcpd* program is located on the system, after that Firestarter will manage the DHCP server completely on the user's behalf. [/SIZE]
   [SIZE=1]**If a DHCP binary is not detected on the system, the DHCP controls will remain inactive**[/SIZE]
   [SIZE=1]Packages that need to be installed for the Firestarter DHCP service to function[/SIZE]  [SIZE=1]Distribution[/SIZE][SIZE=1]Package name[/SIZE][SIZE=1]Installed with[/SIZE]  [SIZE=1]Red Hat 9, Fedora Core[/SIZE][SIZE=1]dhcp[/SIZE][SIZE=1]"yum install dhcp"[/SIZE]  [SIZE=1]Debian[/SIZE][SIZE=1]dhcp[/SIZE][SIZE=1]"apt-get install dhcp"[/SIZE]  [SIZE=1]Mandrake[/SIZE][SIZE=1]dhcp-server[/SIZE][SIZE=1]"urpmi dhcp-server"[/SIZE]  [SIZE=1]Gentoo[/SIZE][SIZE=1]dhcp[/SIZE][SIZE=1]"emerge dhcp"[/SIZE]  [SIZE=1]SuSE[/SIZE][SIZE=1]dhcp-server[/SIZE][SIZE=1]Manually during system install or from RPM[/SIZE]

[ATTACH]180040[/ATTACH]

---

### Post by PatchesTheCaveman on 2011-01-03
newcityboy:  Change your network settings as described in post #25 to make them look like the attached screenshot.  (Basically set your wired IPv4 address to 192.168.0.1.

Then stop and start the firestarter firewall and see if you get an error.

If you do, rerun all those diagnostic terminal commands and paste them here again.

If not, test it out from the desktop.

ETA:  You do have the DHCP server installed.  (I can tell from your previous diagnostic output.)  The wizard always seems to report that error.  I'll report a bug to the Firestarter team.

---

### Post by newcityboy on 2011-01-03
gksudo firestarter
```

Internal network device eth0 is not ready. Aborting..

```ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:14:22:a9:d3:19  
          inet6 addr: fe80::214:22ff:fea9:d319/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8250 (8.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:6c:70:f1  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe6c:70f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12494674 (12.4 MB)  TX bytes:2183089 (2.1 MB)

```cat /etc/dhcp3/dhcpd.conf
```

ddns-update-style interim;
ignore client-updates;

subnet 192.168.1.0 netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option domain-name-servers 8.8.8.8, 149.254.230.7, 149.254.192.126;
option ip-forwarding off;
range dynamic-bootp 192.168.1.100 192.168.1.254;
default-lease-time 21600;
max-lease-time 43200;
}

```
sudo ufw show raw
```
 
IPV4 (raw):
Chain INPUT (policy ACCEPT 6071 packets, 6515658 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 5447 packets, 1103943 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 303 packets, 78133 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 732 packets, 46662 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 732 packets, 46662 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 6359 packets, 6590493 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 6071 packets, 6515658 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 5447 packets, 1103943 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 5457 packets, 1106408 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 11099 packets, 10595613 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 8626 packets, 1702973 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


IPV6:
Chain INPUT (policy ACCEPT 75 packets, 10135 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 1570 packets, 328096 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 75 packets, 10135 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 1570 packets, 328096 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

```sudo grep -i dhcp /var/log/syslog
```

Jan  3 14:43:48 ubuntu NetworkManager[956]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 14:43:49 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 14:43:49 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 14:43:49 ubuntu NetworkManager[956]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 14:43:49 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 14:43:52 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan  3 14:44:00 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan  3 14:44:10 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan  3 14:44:20 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Jan  3 14:44:34 ubuntu NetworkManager[956]: <warn> (eth0): DHCPv4 request timed out.
Jan  3 14:44:34 ubuntu NetworkManager[956]: <info> (eth0): canceled DHCP transaction, DHCP client pid 7361
Jan  3 14:47:04 ubuntu NetworkManager[956]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 14:47:04 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 14:47:04 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 14:47:04 ubuntu NetworkManager[956]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 14:47:04 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 14:47:07 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan  3 14:47:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Jan  3 14:47:25 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Jan  3 14:47:32 ubuntu NetworkManager[956]: <info> (eth0): canceled DHCP transaction, DHCP client pid 8143
Jan  3 14:47:32 ubuntu NetworkManager[956]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 14:47:32 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 14:47:32 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 14:47:32 ubuntu NetworkManager[956]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 14:47:32 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 14:47:35 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan  3 14:47:42 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jan  3 14:47:51 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  3 14:48:05 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  3 14:48:06 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 192.168.0.1 port 67
Jan  3 14:48:07 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1
Jan  3 14:48:07 ubuntu NetworkManager[956]: <info> (wlan0): DHCPv4 state changed bound -> renew
Jan  3 14:48:18 ubuntu NetworkManager[956]: <warn> (eth0): DHCPv4 request timed out.
Jan  3 14:48:18 ubuntu NetworkManager[956]: <info> (eth0): canceled DHCP transaction, DHCP client pid 8264
Jan  3 15:04:00 ubuntu kernel: [   15.512611] type=1400 audit(1294092228.908:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=512 comm="apparmor_parser"
Jan  3 15:04:00 ubuntu kernel: [   27.350339] type=1400 audit(1294092240.748:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=986 comm="apparmor_parser"
Jan  3 15:04:09 ubuntu NetworkManager[1186]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 15:04:09 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 15:04:09 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 15:04:09 ubuntu NetworkManager[1186]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 15:04:09 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 15:04:12 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan  3 15:04:16 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan  3 15:04:24 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Jan  3 15:04:32 ubuntu NetworkManager[1186]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 15:04:32 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 15:04:32 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 15:04:32 ubuntu NetworkManager[1186]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan  3 15:04:32 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 255.255.255.255 port 67
Jan  3 15:04:33 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1
Jan  3 15:04:33 ubuntu NetworkManager[1186]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan  3 15:04:42 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jan  3 15:04:51 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  3 15:04:55 ubuntu NetworkManager[1186]: <warn> (eth0): DHCPv4 request timed out.
Jan  3 15:04:55 ubuntu NetworkManager[1186]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1679
Jan  3 15:11:04 ubuntu NetworkManager[1186]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 15:11:04 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 15:11:04 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 15:11:04 ubuntu NetworkManager[1186]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 15:11:04 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 15:11:07 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan  3 15:11:15 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jan  3 15:11:24 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jan  3 15:11:36 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan  3 15:11:50 ubuntu NetworkManager[1186]: <warn> (eth0): DHCPv4 request timed out.
Jan  3 15:11:50 ubuntu NetworkManager[1186]: <info> (eth0): canceled DHCP transaction, DHCP client pid 4493
Jan  3 15:28:52 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 192.168.0.1 port 67
Jan  3 15:28:53 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1
Jan  3 15:28:53 ubuntu NetworkManager[1186]: <info> (wlan0): DHCPv4 state changed reboot -> renew
Jan  3 15:29:09 ubuntu kernel: [ 1537.015438] type=1400 audit(1294093749.455:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/dhcpd3" pid=9955 comm="apparmor_parser"
Jan  3 15:29:10 ubuntu kernel: [ 1538.416905] type=1400 audit(1294093750.859:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/dhcpd3" pid=9990 comm="apparmor_parser"
Jan  3 15:29:11 ubuntu dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  3 15:29:11 ubuntu dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  3 15:29:11 ubuntu dhcpd: All rights reserved.
Jan  3 15:29:11 ubuntu dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 15:29:11 ubuntu dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  3 15:29:11 ubuntu dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  3 15:29:11 ubuntu dhcpd: All rights reserved.
Jan  3 15:29:11 ubuntu dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 15:29:11 ubuntu dhcpd: Wrote 0 leases to leases file.
Jan  3 15:29:11 ubuntu dhcpd: 
Jan  3 15:29:11 ubuntu dhcpd: No subnet declaration for wlan0 (192.168.0.17).
Jan  3 15:29:11 ubuntu dhcpd: ** Ignoring requests on wlan0.  If this is not what
Jan  3 15:29:11 ubuntu dhcpd:    you want, please write a subnet declaration
Jan  3 15:29:11 ubuntu dhcpd:    in your dhcpd.conf file for the network segment
Jan  3 15:29:11 ubuntu dhcpd:    to which interface wlan0 is attached. **
Jan  3 15:29:11 ubuntu dhcpd: 
Jan  3 15:29:11 ubuntu dhcpd: 
Jan  3 15:29:11 ubuntu dhcpd: Not configured to listen on any interfaces!
Jan  3 15:56:13 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 192.168.0.1 port 67
Jan  3 15:56:14 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1
Jan  3 16:21:10 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 192.168.0.1 port 67
Jan  3 16:21:11 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1
Jan  3 16:46:11 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 192.168.0.1 port 67
Jan  3 16:46:12 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1
Jan  3 17:12:56 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 192.168.0.1 port 67
Jan  3 17:12:57 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1
Jan  3 17:39:45 ubuntu dhclient: DHCPREQUEST of 192.168.0.17 on wlan0 to 192.168.0.1 port 67
Jan  3 17:39:46 ubuntu dhclient: DHCPACK of 192.168.0.17 from 192.168.0.1

```

---

### Post by PatchesTheCaveman on 2011-01-03
I'm not quite sure why your Ethernet network configuration isn't sticking.

Please run ```
nm-tool
``` and copy/paste the output to a reply to this thread.

---

### Post by newcityboy on 2011-01-03
```

NetworkManager Tool

State: connected

- Device: wlan0  [Auto Motorola] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        00:16:CE:6C:70:F1

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    WAYNE-PC_Network:Infra, 40:4A:03:85:E4:25, Freq 2412 MHz, Rate 54 Mb/s, Strength 38 WPA
    Bronze Star:     Infra, 00:1E:E5:74:85:58, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA
    jim:             Infra, 00:1C:DF:F4:9E:D9, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    Chipilon:        Infra, 68:7F:74:21:8A:A0, Freq 2412 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    *Motorola:       Infra, 00:14:A5:C5:5F:B5, Freq 2412 MHz, Rate 54 Mb/s, Strength 64
    myqwest7329:     Infra, 00:24:7B:6D:36:52, Freq 2412 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2
    myqwest5375:     Infra, 00:24:7B:2A:59:50, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    CASTRO:          Infra, 40:4A:03:BE:46:15, Freq 2462 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             24.116.2.50
    DNS:             24.116.2.34


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:14:22:A9:D3:19

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```

---

### Post by PatchesTheCaveman on 2011-01-03
newcityboy:  For some reason your wired Ethernet connection settings weren't saved.

Right-click back on the network icon, click on *eth0*, click Edit, switch to the *IPv4 Settings* tabs, change *Method* to **Manual**, and click the *Add* button to the right of the big white box, then type **192.168.1.1**, which will appear under the *Address* field.  Press Enter.  The field under *Netmask* will automatically fill with the number *24*.  Your settings window should now appear like the attached screenshot.

Now make sure you hit the *Apply* button to save your settings, not the X in the corner or anything else, as that won't save the settings.

At this point, connect the laptop directly to the desktop via Ethernet, or plug both into a switch if you have one.  Then go into Firestarter and stop and start the Firewall.  All of your other settings look good so you shouldn't get an error this time.

---

### Post by newcityboy on 2011-01-03
well that got rid of my error. :) however I still cannot access the internet from the desktop. I have some communiction between the two. the firewall has recieved a few hits from the desktop. The desktops IP address is identical to the eth0 on the laptop.... not sure what to do next. I wanted to say thank you for the help so far. you have been great.

can't get them to ping each other either.

---

### Post by PatchesTheCaveman on 2011-01-03
newcityboy:  Did you manually configure an IP address on the Windows machine?  You'll need to switch it back to automatic.  The Linux computer would not have automatically assigned it the same address it has.

If it doesn't work after you do that, open a Command Prompt on the Windows machine and run these commands:
```
ipconfig /release
ipconfig /renew
```

If it still doesn't work after that, run this command and copy/paste the output:
```
ipconfig /all
```

---

### Post by newcityboy on 2011-01-03
I am running 10.10 on the desktop right now. it does not like those commands. what is the linux equivilent?
I rebooted into xp and the net works. now for the linux side of things

---

### Post by PatchesTheCaveman on 2011-01-03
Of course not.  They're Windows commands!  ;-)

Make sure the eth0 configuration on Linux is set to Automatic (DHCP).

The equivalent to the first set of commands, which requests a new IP address from the laptop:
```
sudo dhclient eth0
```

The equivalent to the second, which outputs the IP configuration, is:
```
ifconfig -a
```

---

### Post by newcityboy on 2011-01-03
for some odd reason when I tried to reboot back into 10.10 it suddenly did not exist,,, I went to reinstall and it said that it had to uninstall the original version before a reinstall. it was a brand new install so no loss except for some time. It will take a little time before I can check to see if that will fix my problem.

---

### Post by newcityboy on 2011-01-04
well I thought that might happen.... when I finished up the install the system got a whole new IP address. e have connection and internet. you have been great. I thank you for your time.

---

### Post by joebrady on 2011-01-12
:guitar:

---

### Post by Efaustus9 on 2011-11-20
After much google searching and much frustration it seems this thread may be able to generate a solution to my current predicament. I have converted an old dell pc with both an internal Ethernet card and wireless card into a ubuntu 11.10 multimedia box for the living room. I am also intending to use it as a bridge for my direct tv receiver so that I can get on demand content for the device. I have installed firestarter, system-config-samba, and dhcp3-server. Initially I was getting a eth0 is not ready when trying to start the firewall. After going into network tools and manually giving the eth0 the static address IP address of 192.168.2.3 and a network mask of 255.255.255.0 (per [http://tinyurl.com/86t5tkv](http://tinyurl.com/86t5tkv)) did that error go away. Now however when I try to start the firewall I get the error "Failed to start DHCP server". dhcp3 is installed and I have the directory /etc/dhcp3/ but there is no .conf file with in it, it just has a dhclient-enter-hooks.d folder. However there is a /etc/dhcp folder and it does have a dhcpd.conf file with in it. So any ideas as to how I could resolve this? Thanks in advance.:)

---

