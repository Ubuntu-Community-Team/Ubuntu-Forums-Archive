---
title: "DHCP Fails Following Reboot from Windows 7 to Ubuntu 11.10"
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by flight878 on 2011-12-01
This is a strange problem that's been an annoyance to solve.  Every instance, following a reboot from Windows 7 to Ubuntu 11.10, the system fails to obtain an IP address from the Linksys E1500 router to which it's connected.  The only way to solve this is by powercycling the router.  Why?  This did not occur with the 11.04 installation.  By the way, this is a **wired connection**.

Here is some added info and failed attempts to solve this issue:

[LIST]
[*]Tried disabling IPv6 on both the router and through NetworkManager
[*]Firmware was already up to date on the router long before upgrade to 11.10
[*]Not a NetworkManager issue: removed it temporarily and same thing still happened
[*]Tried fully shutting down from Windows and waiting 1 min before booting into Ubuntu; problem persisted
[*]This problem is only related between this PC and the router.  While it struggled to obtain an IP address, a separate laptop running Ubuntu 11.10 was wired to the router -- no problem obtaining an IP address via DHCP; it also worked via wireless.
[*]Tried a direct connection to the cable modem.  No problem.  Ubuntu system successfully obtains an IP address following reboot from Windows.
[*]This PC is setup on a Samba network; I had a different computer name for Windows and for Ubuntu, and then setup an identical name for both installations (Winston), and it didn't make a difference.
[*]The [FONT=Courier New][SIZE=2]resolv.conf[/SIZE][/FONT] file is empty when the system struggles to obtain an IP address.
[*]The router is configured to provision a static-leased IP address for every device connected to the network.  The host devices obtain these addresses via DHCP.
[/LIST]
I also tried modifying the [FONT=Courier New][SIZE=2]/etc/network/interfaces[/SIZE][/FONT] configuration file to add the following: 
```
auto eth0
iface eth0 inet dhcp
```In addition, the [FONT=Courier New][SIZE=2]/etc/NetworkManager/NetworkManager.conf[/SIZE][/FONT] file was modified to set:
```
[ifupdown]
managed=true
#default value was false
```Following a reboot, all that happened was that the boot screen stalled with a "Waiting for network configuration..." message, eventually followed by a "Waiting 60 more seconds for network configuration...".  This whole process was undone and reversed.

Here are the results of [FONT=Courier New][SIZE=2]ifconfig[/SIZE][/FONT]:
```
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:a0:90:4d  
          inet6 addr: fe80::20c:f1ff:fea0:904d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1086 (1.0 KB)  TX bytes:9841 (9.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3072 (3.0 KB)  TX bytes:3072 (3.0 KB)
```And, if anyone is curious, here are the (partial) results of [FONT=Courier New][SIZE=2]less /var/log/syslog | grep -i network[/SIZE][/FONT]:
```
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Auto-activating connection 'Wired to E1500'.
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) starting connection 'Wired to E1500'
Dec  1 00:17:31 Winston NetworkManager[723]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec  1 00:17:31 Winston NetworkManager[723]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec  1 00:17:31 Winston NetworkManager[723]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec  1 00:17:31 Winston NetworkManager[723]: <info> dhclient started with pid 2992
Dec  1 00:17:31 Winston NetworkManager[723]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec  1 00:17:31 Winston NetworkManager[723]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec  1 00:17:31 Winston NetworkManager[723]: <info> (eth0): DHCPv4 state changed preinit -> expire
Dec  1 00:17:31 Winston NetworkManager[723]: <info> (eth0): DHCPv4 state changed expire -> preinit
Dec  1 00:18:16 Winston NetworkManager[723]: <warn> (eth0): DHCPv4 request timed out.
Dec  1 00:18:16 Winston NetworkManager[723]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2992
Dec  1 00:18:16 Winston NetworkManager[723]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Dec  1 00:18:16 Winston NetworkManager[723]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Dec  1 00:18:16 Winston NetworkManager[723]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Dec  1 00:18:16 Winston NetworkManager[723]: <warn> Activation (eth0) failed.
Dec  1 00:18:16 Winston NetworkManager[723]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Dec  1 00:18:16 Winston NetworkManager[723]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec  1 00:18:16 Winston NetworkManager[723]: <info> (eth0): deactivating device (reason 'none') [0]
```This was one iteration of the cyclic reponse (as NetworkManager attempts multiple times to obtain the IP address from the router), with only the pid varying.  Any solutions for this issue?  I reboot from Windows to Linux quite often, and having to powercycle the router every time isn't really a proper solution.

---

### Post by praseodym on 2011-12-01
Hi,

what hardware is in use? Please show
```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by flight878 on 2011-12-01
> **praseodym said:**
> Hi,

what hardware is in use? Please show
```
lspci -nnk | grep -iA2 net
lsmod
```

The results of [FONT=Courier New][SIZE=2]lspci -nnk | grep -iA2 net[/SIZE][/FONT], showing the relevant hardware in use, are:
```
02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 01)
    Subsystem: Intel Corporation Desktop Board D865GBF [8086:302f]
    Kernel driver in use: e100
```The results of [FONT=Courier New][SIZE=2]lsmod[/SIZE][/FONT] are:
```
Module                  Size  Used by
vesafb                 13489  1 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
nvidia              10782577  40 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  24 
soundcore              12600  1 snd
psmouse                73673  0 
xt_addrtype            12596  4 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
binfmt_misc            17292  1 
parport_pc             32114  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  0 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
e100                   36289  0 

```

---

### Post by praseodym on 2011-12-01
Do you need the firewall (iptables there)? If not, remove it:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by flight878 on 2011-12-01
> **praseodym said:**
> Do you need the firewall (iptables there)? If not, remove it:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

I do need the firewall actually.  This gave me the idea to try disabling the firewall, and rebooting the computer to Ubuntu.  The problem still persists.  If this is the case, how would removing the firewall or clearing the iptables rules help?

---

### Post by flight878 on 2011-12-01
Well, a workaround was found, not quite a solution.  Since I already configured the router so that the IP addresses it provisions be static leases, I disabled DHCP in NetworkManager.  I chose a Manual configuration instead, setting the static IP for this PC in particular, the proper netmask and gateway, and setting the DNS servers to the ones obtained from the router.

Now I can boot from Windows to Ubuntu without problems.  Still, this was not a problem in Natty.  It seems like this ocelot is not oneiric enough.

---

