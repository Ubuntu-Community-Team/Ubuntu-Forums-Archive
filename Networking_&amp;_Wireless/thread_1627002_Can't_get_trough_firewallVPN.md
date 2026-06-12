---
title: "Can't get trough firewall/VPN"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by tzicatl on 2010-11-20
I also posted this problem to Ubuntu Questions on Launchpad here: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/134713](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/134713)

--------------
On the office we have a Firewall/VPN infrastructure. Everybody connects to internet trough an Access Point (Lynksys RWT120N), which, in turn, connects to a WatchWard/Firebox red box. I suppose this is the equipment that does the VPN stuff. Finally, the red box connects to a DSL modem from our ISP.

The problem is: Everybody on the office can connect to the AP and surf the internet without any issues, excepting me when I connect with ubuntu 10.10. I have windows on the same machine and I can access the internet without problems.

What I have seen so far is that Network Manager associates with the AP, gets what I would consider all the expected information from DHCP, but internet connectivity is none.

For "expected information from DHCP" i mean: IP address, gateway, and DNS.
I can ping my assigned IP address, the gateway and even other machines in the same network. I cannot ping the DNS or other external IP addresses.

So, as I said, If I reboot on Windows, I can connect. So what else would be going wrong?

I can provide more information if requested.

---

### Post by tzicatl on 2010-11-24
Well I did some tests:

Test 1:
Ubuntu 10.10 connects to Acces Point, receives correct IP address, netmask, DNS and Gateway information. Can ping to all other computers in the network and the gateway, but pinging to any other host outside the network results in "Network Unreachable".

Test 2:
Restart machine and boot into Windows 7. Connection to AP is successful and can surf the internet and ping whatever DNS I want.

Test 3:
Restart machine an boot into Ubuntu 10.10 again, configured connection using Network Manager and tell it to ignore the DNS provided by the DHCP server (i.e. the AP) and use another well known DNS. I tried several DNS's including google's and OpenDNS's. Still can't ping to any other host except the ones on the local network.

Test 4:
Restart and Boot into ubuntu 10.10 and connect another wireless network. Everything works OK.

Test 5:
Restart and Boot into Ubuntu 10.10, configure network manager to use a known good static IP which was previously used by another host. Shut down that host and thest with ubuntu. Still the same results: no connectivity.

Test 6:
This was a coincidence. 
The other host was alive. Then I started ubuntu with the previous settings from Test 5 (Static IP). An IP address conflict emerged, but Ubuntu had connectivity (WTF!?)

---

### Post by tzicatl on 2010-12-09
Some more tests...

Step 1: connect to the Access Point
Step 2: Ping to 8.8.8.8 and get "Network Unreachable"
Step 3: Display arp cache:
[INDENT]The gateway is 192.168.1.254, my IP addr is 192.168.1.111 netmask 255.255.255.0
  arp cache is: 192.168.1.254  = 00:25:9a:9b:7c:56
  But in other computers the arp cache for 192.168.1.254 is 00:90:7f:2e:8d:3c
  Why don't ubuntu gets it right in the first time, I still don't know.[/INDENT]

Step 4: Modify mac addr of the gateway on the arp cache:
[INDENT]  arp -s 192.168.1.254 00:90:7f:2e:8d:3c

  And bingo! internet is working.
[/INDENT]
This weird problem is partially solved.

---

