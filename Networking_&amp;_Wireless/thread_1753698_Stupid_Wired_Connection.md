---
title: "Stupid Wired Connection"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by Irony on 2011-05-09
For reasons best known to itself my wired internet connection (Lucid) has decided that it will not connect on booting up or resuming from suspend. I have not done anything to cause this (no updating). It was fine a week ago, yet if I boot into a snapshot taken a week ago it it still does it! Windows is of course fine. The only way I can connect is by repeatedly using the network manager and unticking a re-ticking Enable Network Connection...

```
~$ lspci | grep Ethernet
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```

```
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr xxxxxxxxxxxxx 
          inet addr:192.168.1.08  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe02:4187/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36288145 (36.2 MB)  TX bytes:2338477 (2.3 MB)
          Interrupt:34 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58250 (58.2 KB)  TX bytes:58250 (58.2 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I note that I get the following message when doing;

```
~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
```

Yet clearly eth0 is there, I tried adding to /etc/network/interfaces;

```
auto lo
iface lo inet loopback

#I added this
auto eth0
iface eth0 inet dhcp
```

but get;

```
~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/xxxxxxxxxxxxx
Sending on   LPF/eth0/xxxxxxxxxxxxx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.64 from 192.168.1.254
DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.254
DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.254
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.64 from 192.168.1.254
DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.254

```
In short I don't know why I should now be unable to connect when previously it was working fine for many months and how is it that it affects a snapshot taken a week ago. I have not changed anything in the BIOS.

---

### Post by Irony on 2011-05-09
Note; I had this problem before in a previous version of Ubuntu but it, for reasons best known to itself, resolved itself spontaneously.

When the problem occurs I cannot even browse the router (bthomehub 2).

---

### Post by dargaud on 2011-05-09
Does it help if you set your network as static ?
Edit /etc/network/interfaces in a way similar to this:
```
auto lo eth0
iface lo inet loopback
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
```

---

### Post by dineshs on 2011-05-09
If you are using network manager your /etc/network/interfaces should only contain ```
auto lo
iface lo inet loopback

```
To restart network manager run ```
sudo service network-manager restart
```
If you have done manual configuration for eth0 the configuration file will be in /etc/NetworkManager/system-connections

---

### Post by chili555 on 2011-05-09
I think your system is confused about whether you want to use manual methods (/etc/network/interfaces and dhclient) or automatic methods (Network Manager). If you want to use NM, I suggest you amend intefaces to read:```
auto lo
iface lo inet loopback

#I added this
#chili says remove it
#auto eth0
#iface eth0 inet dhcp
```Then right click the NM icon and Edit Connections. Select Wired and select Edit on auto eth0. Be sure Connect Automatically is checked.

Reboot and see if the behavior is improved.

If you would rather use manual methods, remove NM and populate interfaces and resolv.

---

### Post by Irony on 2011-05-09
> **dargaud said:**
> Does it help if you set your network as static ?
Edit /etc/network/interfaces in a way similar to this:
Thanks for the suggestion, it didn't seem to work first time and I spent ages unticking and ticking Enable networking.

I then changed it back to the default and tried;

```
~$ sudo ifdown eth0
ifdown: interface eth0 not configured
~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
```

but that didn't work so I changed it back to your suggestion and did;

```
~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
~$ sudo ifdown eth0
~$ sudo ifup eth0
```

I then unticked and ticked 'Enable networking' and it connected... but I tried it again, to double check, and it didn't work.

... But then I did the whole process again and it worked, so it seems to semi-work - it seems to get rid of the "Ignoring unknown interface eth0=eth0" message... but I am not entirely sure

I will have to try a few re-boots and suspends to see what happens.

---

### Post by Irony on 2011-05-09
> **chili555 said:**
> I think your system is confused about whether you want to use manual methods (/etc/network/interfaces and dhclient) or automatic methods (Network Manager).
I was on automatic, I've only added stuff to the /etc/network/interfaces to try to resolve the problem which started yesterday (for no discernible reason).

---

### Post by chili555 on 2011-05-09
> I've only added stuff to the /etc/network/interfaces to try to resolve the problemThen you are no longer on automatic; you are on confused. If this is a stay at home computer that doesn't go down to the coffee shop and select from among many networks, I suggest purging NM altogether and properly set up interfaces and resolv. You should connect on boot automatically from then on.

---

### Post by Irony on 2011-05-09
> **chili555 said:**
> Then you are no longer on automatic; you are on confused. If this is a stay at home computer that doesn't go down to the coffee shop and select from among many networks, I suggest purging NM altogether and properly set up interfaces and resolv. You should connect on boot automatically from then on.
No I am not confused, it was on automatic but was not connecting automatically hence I tried some changes.

However, whether those changes are the correct way is debatable, it seems to have worked on reboot though my applet has disappeared - probably I would need to set up any changes in a different manner.

---

### Post by Irony on 2011-05-09
> **dargaud said:**
> Does it help if you set your network as static ?
Using dargaud's manual suggestion I entered my figures for the address, netmask and gateway figures into the Network Connections dialogue (by setting it to manual) on my network applet (rather than into the /etc/network/interfaces file) and this seems to have worked.

I'll test it over a few days to see if it is stable, if it is I'll mark it as solved... though I am still puzzled as to why it can't find the router automatically.

---

### Post by Irony on 2011-05-12
Tried to auto connect using a xubuntu usb stick and the same problem occurred but was solved by manually editing the network manager.

So in short windows auto-connects but ubuntu doesn't - as I haven't touched the settings of the router or BIOS I am a bit puzzled.

Just noticed the following in the router;
	
```
Hub Firmware Information
Current firmware	4.7.5.1.83.3.18 (Type B)
Last updated	07/05/11
```

So the last hub update (which is automated) has made the BThomehub incompatible with ubuntu and probably linux...

---

### Post by Irony on 2011-05-12
Here is the answer (same as what I did);

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9)

---

### Post by CPKS on 2011-05-18
Those of you having trouble with connexions on machines that dual boot with some variety of Windows may perhaps cure the problem as follows:

1) Click on the network widget in the top panel and select "Edit connexions..."

2) Select the connexion you're using and click the "Edit" button.

3) Select the IPv4 tab. You should see "Automatic (DHCP)" as the choice at the top.

4) Fill in the empty field "DHCP client ID:" with the machine name as used by Windows, and apply the change.

I don't have a dual-boot machine and so cannot test this directly, but I did find that it instantly fixed the problem on a machine that stopped connecting after the firmware upgrade.

I'd be interested to know if this works for you, if you are unlucky enough to suffer from this problem.

---

