---
title: "Network is unreachable ... urrggghhh"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by grw on 2006-02-20
Another update ... with solution!!!

My network is unreachable problem was due to a DHCP bug (at least in Ubuntu 5.10 and 6.06) relating to networks with a netmask of 255.255.255.255. This seems to be an uncommon address but it is a valid one (in contrast to what some people have suggested)

You can fix the problem by making a small change in /etc/dhcp3/dhclient-script

In teh terminal type: sudo gedit /etc/dhcp3/dhclient-script
Scroll down until you find the line: for router in $new_routers; do
Then replace:
for router in $new_routers; do
route add default dev $interface gw $router $metric_arg
done
with
for router in $new_routers; do
route add -host dev $interface gw $router
route add default dev $interface gw $router $metric_arg
done

See this bug report for details:[https://launchpad.net/distros/ubuntu...cp3/+bug/33382](https://launchpad.net/distros/ubuntu...cp3/+bug/33382)

Don't know why Ubuntu haven't fixed this problem

.....

This is an UPDATED post (I have finally managed to get my floppy working and can post output from the terminal)

I am running Ubuntu 5.10. I can connect to the internet via broadband at home, but NOT via my university network. 
My problem seems similar to that of qqqqqqqqqqqqqqqqq - [http://ubuntuforums.org/showthread.php?t=134970](http://ubuntuforums.org/showthread.php?t=134970) . We both have 255.255.255.255 as broadcast address. And also Erakepio [http://ubuntuforums.org/showthread.php?t=135415](http://ubuntuforums.org/showthread.php?t=135415)

The university network is a 'roaming network' for wireless and non uni machine access. I am plugged in via ethernet cable - green LED is on and orange flashes ocasionally.  It's DHCP. Pinging gives me 'Network is unreachable'. (Windows works fine though. As did Suse when i had that on my machine)

I have a Dell inspiron 2500 laptop, with Intel 8255x-based PCI Ethernet. Here is some terminal output:

gwyn@grw23:~$ sudo mii-tool eth0
Password:
eth0: negotiated 10baseT-FD, link ok

gwyn@grw23:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:20:E0:6E:A0:66
          inet addr:10.0.9.173  Bcast:10.0.9.173  Mask:255.255.255.255
          inet6 addr: fe80::220:e0ff:fe6e:a066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:56828 (55.4 KiB)  TX bytes:1062 (1.0 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:54730 (53.4 KiB)  TX bytes:54730 (53.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

gwyn@grw23:~$ sudo ifconfig eth0 up

gwyn@grw23:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

gwyn@grw23:~$ ping 10.0.8.1
connect: Network is unreachable

gwyn@grw23:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:20:e0:6e:a0:66
Sending on   LPF/eth0/00:20:e0:6e:a0:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.0.8.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.8.1
SIOCADDRT: Network is unreachable
bound to 10.0.8.243 -- renewal in 4212 seconds.

gwyn@grw23:~$ cat /etc/resolv.conf
search sussex.ac.uk
nameserver 139.184.32.27
nameserver 139.184.32.25
nameserver 139.184.32.26

gwyn@grw23:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

gwyn@grw23:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
0000:00:02.0 VGA compatible controller: Intel Corp. 82815 CGC [Chipset Graphics Controller] (rev 11)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 03)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 03)
0000:01:03.0 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
0000:01:03.1 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
0000:01:0b.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
0000:02:04.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 08)
0000:02:08.0 Communication controller: Lucent Microelectronics WinModem 56k (rev 01)

gwyn@grw23:~$ lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_powersave       1920  0
cpufreq_stats           5124  0
cpufreq_userspace       4444  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
freq_table              4484  1 cpufreq_stats
pcmcia                 24584  4
ipv6                  217408  6
ipt_limit               2432  0
iptable_mangle          2816  0
ipt_LOG                 6400  0
ipt_MASQUERADE          3328  0
iptable_nat            21076  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5248  0
ip_conntrack_irc       71824  0
ip_conntrack_ftp       72336  0
ipt_state               2048  0
ip_conntrack           39864  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2944  0
ip_tables              18176  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
tc1100_wmi              6916  0
video                  16004  0
battery                 9604  0
container               4608  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
pcc_acpi               11392  0
sony_acpi               5516  0
ac                      4996  0
dev_acpi               11396  0
hotkey                  9508  0
af_packet              20232  4
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
yenta_socket           22540  2
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
hw_random               5268  0
intel_agp              21276  1
agpgart                32328  2 intel_agp
nls_cp437               5888  1
ntfs                   92016  1
dm_mod                 50364  1
tsdev                   7616  0
joydev                  9280  0
evdev                   9088  1
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
reiserfs              217200  1
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
e100                   32768  0
mii                     5248  1 e100
uhci_hcd               28048  0
usbcore               104316  3 usbhid,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  4
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  722
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

gwyn@grw23:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0


gwyn@grw23:~$ tail -f /var/log/syslog
Feb 27 17:11:03 localhost dhclient: sit0: unknown hardware address type 776
Feb 27 17:11:03 localhost dhclient: sit0: unknown hardware address type 776
Feb 27 17:11:03 localhost dhclient: Listening on LPF/eth0/00:20:e0:6e:a0:66
Feb 27 17:11:03 localhost dhclient: Sending on   LPF/eth0/00:20:e0:6e:a0:66
Feb 27 17:11:03 localhost dhclient: Sending on   Socket/fallback
Feb 27 17:11:03 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Feb 27 17:11:03 localhost dhclient: DHCPOFFER from 10.0.8.1
Feb 27 17:11:03 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Feb 27 17:11:03 localhost dhclient: DHCPACK from 10.0.8.1
Feb 27 17:11:03 localhost dhclient: bound to 10.0.8.243 -- renewal in 4212 seconds.

In another terminal I then typed:  sudo /etc/init.d/networking restart
tail -f /var/log/syslog output was as follows:

Feb 27 17:16:14 localhost dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6096
Feb 27 17:16:14 localhost dhclient: killed old client process, removed PID file
Feb 27 17:16:14 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Feb 27 17:16:14 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Feb 27 17:16:14 localhost dhclient: All rights reserved.
Feb 27 17:16:14 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Feb 27 17:16:14 localhost dhclient:
Feb 27 17:16:14 localhost dhclient: sit0: unknown hardware address type 776
Feb 27 17:16:14 localhost dhclient: sit0: unknown hardware address type 776
Feb 27 17:16:14 localhost dhclient: Listening on LPF/eth0/00:20:e0:6e:a0:66
Feb 27 17:16:14 localhost dhclient: Sending on   LPF/eth0/00:20:e0:6e:a0:66
Feb 27 17:16:14 localhost dhclient: Sending on   Socket/fallback
Feb 27 17:16:14 localhost dhclient: DHCPRELEASE on eth0 to 10.0.8.1 port 67
Feb 27 17:16:14 localhost dhclient: send_packet: Network is unreachable
Feb 27 17:16:14 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Feb 27 17:16:14 localhost dhclient: receive_packet failed on eth0: Network is down
Feb 27 17:16:14 localhost dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Feb 27 17:16:14 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Feb 27 17:16:14 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Feb 27 17:16:14 localhost dhclient: All rights reserved.
Feb 27 17:16:14 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Feb 27 17:16:14 localhost dhclient:
Feb 27 17:16:14 localhost dhclient: sit0: unknown hardware address type 776
Feb 27 17:16:14 localhost kernel: [4295349.497000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
Feb 27 17:16:14 localhost dhclient: sit0: unknown hardware address type 776
Feb 27 17:16:14 localhost dhclient: Listening on LPF/eth0/00:20:e0:6e:a0:66
Feb 27 17:16:14 localhost dhclient: Sending on   LPF/eth0/00:20:e0:6e:a0:66
Feb 27 17:16:14 localhost dhclient: Sending on   Socket/fallback
Feb 27 17:16:18 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Feb 27 17:16:18 localhost dhclient: DHCPOFFER from 10.0.8.1
Feb 27 17:16:18 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Feb 27 17:16:18 localhost dhclient: DHCPACK from 10.0.8.1
Feb 27 17:16:18 localhost dhclient: bound to 10.0.9.173 -- renewal in 5209 seconds.
Feb 27 17:16:24 localhost kernel: [4295359.994000] eth0: no IPv6 routers presentFeb 27 17:17:01 localhost /USR/SBIN/CRON[8055]: (root) CMD (   run-parts --report /etc/cron.hourly)


And according to Windows where everything works fine:

 Connection-specific DNS Suffix . : sussex.ac.uk
IP Address. . . . . . . . . . . . : 10.0.9.96
Subnet Mask . . . . . . . . . . . : 255.255.255.255
Default Gateway . . . . . . . . . : 10.0.8.1

Active Routes:
Network Destination Netmask Gateway Interface Metric
0.0.0.0 0.0.0.0 10.0.8.1 10.0.9.96 30
10.0.9.96 255.255.255.255 127.0.0.1 127.0.0.1 30
10.255.255.255 255.255.255.255 10.0.9.96 10.0.9.96 30
127.0.0.0 255.0.0.0 127.0.0.1 127.0.0.1 1
224.0.0.0 240.0.0.0 10.0.9.96 10.0.9.96 30
255.255.255.255 255.255.255.255 10.0.9.96 10.0.9.96 1
Default Gateway: 10.0.8.1 Adapter (10/100)...


Any ideas?
Thanks

---

### Post by drakeoutlaw on 2006-02-20
[QUOTE=grw]> dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware adress type 776
can&#8217;t create /var/lib/dhcp3/dhclient.leases: Permission denied
can&#8217;t create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
[/QUOTE]

The "Permission denied" messages are because you should use sudo before "dhclient eth0". Type: sudo dhclient eth0

---

### Post by grw on 2006-02-21
ok

> sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:20:e0:6e:a0:66
Sending on LPF/eth0/00:20:e0:6e:a0:66
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 10.0.8.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.8.1
SIOCADDRT: Network is unreachable
bound to 10.0.10.243 - - renewal in 4911 seconds

---

### Post by drakeoutlaw on 2006-02-21
Open a new terminal window run: tail -f /var/log/syslog

This will give you a running output of the syslog.

Now in your old terminal restart networking with: sudo /etc/init.d/networking restart

Watch what happens in the terminal running the tail command. You should get more info on exactly what is failing.

---

### Post by grw on 2006-02-22
In teh terminal running tail -f /var/log/syslog it says (after I did sudo /etc/init.d/networking restart):

localhost dhclient: There is already a PID file /var/run/dhclient.eth0.pid with pid 6134
localhost dhclient: killed old client process, removed PID file
.... For info visit [www.isc.org/products/DHCP](www.isc.org/products/DHCP) ....
...
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:20:e0:6e:a0:66
Sending on LPF/eth0/00:20:e0:6e:a0:66
DHCPRELEASE on eth0 to 10.0.8.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address

Before I typed sudo /etc/init.d/networking restart it there was this:

localhost kernel: [4294762.222000] Bluetooth: RFCOMM ver 1.5
localhost kernel: [4294762.222000] Bluetooth: RFCOMM socket layer initialized
localhost kernel: [4294762.222000] Bluetooth: RFCOMM TTY layer intitialized
localhost anacron[7339]: Anacron 2.3 started on 2006-02-22
localhost /usr/sbin/cron[7364]: (CRON) INFO (pidfile fd = 3)
localhost /usr/sbin/cron[7365]: (CRON) STARTUP (fork ok)
localhost anacron[7339]: Normal exit (0 jobs run)
localhost /usr/sbin/cron[7365]: (CRON) INFO (Running @reboot jobs)
localhost kernel: [4294771.767000] eth0: no IPv6 routers present
localhost gconfd (gwyn-7168): Resolved address "xml:readwrite:/home/gwyn/.gconf" to a writable configuration source at potition 0


I found the stuff below in the README file at the web address above. Is this the problem? Should I follow these instructions? I am running a recent version of linux (5.10).

LINUX: BROADCAST

If you are running a recent version of Linux, this won't be a problem, but on older versions of Linux (kernel versions prior to 2.2), there is a potential problem with the broadcast address being sent incorrectly.

In order for dhcpd to work correctly with picky DHCP clients (e.g., Windows 95), it must be able to send packets with an IP destination address of 255.255.255.255. Unfortunately, Linux changes an IP destination of 255.255.255.255 into the local subnet broadcast address (here, that's 192.5.5.223).

This isn't generally a problem on Linux 2.2 and later kernels, since we completely bypass the Linux IP stack, but on old versions of Linux 2.1 and all versions of Linux prior to 2.1, it is a problem - pickier DHCP clients connected to the same network as the ISC DHCP server or ISC relay agent will not see messages from the DHCP server. It *is* possible to run into trouble with this on Linux 2.2 and later if you are running a version of the DHCP server that was compiled on a Linux 2.0 system, though.

It is possible to work around this problem on some versions of Linux by creating a host route from your network interface address to 255.255.255.255. The command you need to use to do this on Linux varies from version to version. The easiest version is:

    route add -host 255.255.255.255 dev eth0 

On some older Linux systems, you will get an error if you try to do this. On those systems, try adding the following entry to your /etc/hosts file:

255.255.255.255 all-ones

Then, try:

    route add -host all-ones dev eth0 

Another route that has worked for some users is:

    route add -net 255.255.255.0 dev eth0 

If you are not using eth0 as your network interface, you should specify the network interface you *are* using in your route command.

---

### Post by grw on 2006-02-24
Well, I follwed the instructions above:
sudo route add -host 255.255.255.255 dev eth0
But still the network is unreachable.

I really have no idea about this. Can anyone help?

---

### Post by erakepio on 2006-02-24
grw...im having the same issues (i think) from my university (collage).  i think the drivers for my card are the problem however i cannot confirm this.

Could you not email the Sussex help desk and explain your problem? I'd imagine they would have some sort of basic knowledge of linux

---

### Post by jamesr on 2006-02-24
What version of Ubuntu are you running, because I do not believe that the broadcast problem  should be a problem.

What is the the address of the DHCP server? the help desk should be able to help .

> > ifconfig eth0
Link encap: Ethernet HW addr 00:20:e0:6e:a0:66
inet addr:10.0.10.234 Bcast:10.0.10.234 Mask: 255.255.255.255
inet6 addr: fe80::220:e0ff:fe6e:a066/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
RX packets: 1077 errors: 0 dropped: 0 overuns: 0 frame: 0
TX packets: 7 errors: 0 ... 0... 0... 0
Collisions: 0 txqueuelen: 1000
RX bytes: 156349 (152.6 KiB) TX bytes: 1062 (1.0 KiB)

lo RX packets: 5489 errors: 0 ....0....0.....0
TX packets: 5489 ....0.....0....0.....0.


I wonder where to found the address 10.0.10.234 with a broadcast 10.0.10.234

When it works at home how are You connecting.?

> > Ping 139.184.32.27
Network is unreachable
what is this address.

---

### Post by grw on 2006-02-24
I am running a newly installed Ubuntu 5.10
I have explained the problem to the helpdesk here. They are very insistent that they do not support linux. One of them did say he was personnaly interested and would investigate things for me, but that was ages ago and he hasn't got back to me. He suggested that the problem might be something to do with the 'roaming network' I am on - but he couldn't tell me more than that.

These are teh settings I get from windows: 

Connection-specific DNS Suffix . : sussex.ac.uk
IP Address. . . . . . . . . . . . : 10.0.9.96
Subnet Mask . . . . . . . . . . . : 255.255.255.255
Default Gateway . . . . . . . . . : 10.0.8.1

139.184.32.27 is the DHCP server - at least it is the DNS server at sussex (there's also 139.184.32.25 and 139.184.32.26)
Or do I misunderstand? Am I wrong to think this is the DHCP server?
Ah! here I have written that the DHCP server is 10.0.8.1 - same as teh default gateway. (When I first installed 5.10 at university, teh installation was unable to set a default route. I later reinstalled at home, and did not have the same problem)

10.0.10.234 with a broadcast 10.0.10.234 - don't know...

At home I connect with broadband - direct connection I think it is called

---

### Post by grw on 2006-02-27
Thanks to everyone who has tried to help. The problem persists. 

I have updated my first post with more information...
Hoping for enlightenment....

---

### Post by claes on 2006-02-27
Looks very strange.

When you get a mask of 255.255.255.255 means that all other ip addresses are on a different subnet. Even your default gateway is on another subnet. So you can't connect to that. The only address you can connect to i your own ip everything else have to go through your default gatewat which you can't connect to with that mask. Very strange. Not sure why it works in windows or suse. That ip configuration should not work. 

What do /var/lib/dhcp3/dhclient.leases look like?

Claes

---

### Post by hajk on 2006-02-27
Could be a nameserver problem...
Why not use the Gnome System-->Administration-->Networking menu to handle the connection details (it takes care of /etc/networking/interfaces as well).
Open Properties for eth0, enable the interface and specify DHCP; and under DNS add your router. Then OK and activate the interface should bring it up with eth0 as gateway -- if not you may have a hardware problem (cable or something).

---

### Post by grw on 2006-02-28
Thanks. 
I have already configured eth0. DHCP is specified and DNS servers are listed. But it doesn't work. Maybe there is something else I need to do? Hosts?

Here is the content of /var/lib/dhcp3/dhclient.leases

lease {
  interface "eth0";
  fixed-address 10.0.8.243;
  option subnet-mask 255.255.255.255;
  option dhcp-lease-time 10800;
  option routers 10.0.8.1;
  option dhcp-message-type 5;
  option dhcp-server-identifier 10.0.8.1;
  option domain-name-servers 139.184.32.27,139.184.32.25,139.184.32.26;
  option domain-name "sussex.ac.uk";
  renew 1 2006/2/27 11:35:36;
  rebind 1 2006/2/27 12:47:50;
  expire 1 2006/2/27 13:10:20;
}
lease {
  interface "eth0";
  fixed-address 10.0.8.243;
  option subnet-mask 255.255.255.255;
  option routers 10.0.8.1;
  option dhcp-lease-time 10800;
  option dhcp-message-type 5;
  option domain-name-servers 139.184.32.27,139.184.32.25,139.184.32.26;
  option dhcp-server-identifier 10.0.8.1;
  option domain-name "sussex.ac.uk";
  renew 1 2006/2/27 18:21:15;
  rebind 1 2006/2/27 19:48:33;
  expire 1 2006/2/27 20:11:03;
}

---

### Post by hajk on 2006-02-28
Yes, I know that you have already configured eth0, and I must admit that you've done an enormous amount of work doing that (more than I would be prepared to do, at any rate).

Still, why don't you humour me and try to do it the Gnome/Ubuntu way, and use the router as nameserver, as I've suggested -- it will only take a minute to carry out. What have you got to lose?

---

### Post by grw on 2006-02-28
I did actually try doing exactly what you suggested via Gnome - admin - networking etc. I put in 10.0.8.1 (which is what I should have entered isn't it - i.e the router?)
Sorry no luck.

---

### Post by hajk on 2006-02-28
I agree that the problem has to do with the roaming network. Just looked through the on-line documentation on roaming access at your university... You have registered your Ethernet card's MAC address with the university, I take it. There is some info available ("resnet") for wired roaming connections from Mac OS 10.3, some of it (proxies) may be applicable to your case.

---

### Post by grw on 2006-02-28
Yes, my MAC address is registered. I shall see what I can find out about roaming networks and proxies. Thanks.

---

### Post by copperwave on 2006-02-28
Dude - this is killing me - if it works under XP or Suse what addresses do you get? Try ipconfig /all in an XP dos box. 

FWIW 255.255.255.255 'aint ever going to work - all you will see is yourself.  This needs to be at a minimum x.y.z.0

Hope this helps
//copperwave

---

### Post by grw on 2006-03-01
It's killing me too!!!

Here's the windows info:

>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : gwyn
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Mixed
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : sussex.ac.uk

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : sussex.ac.uk
        Description . . . . . . . . . . . : Intel 8255x-based PCI Ethernet Adapt
er (10/100)
        Physical Address. . . . . . . . . : 00-20-E0-6E-A0-66
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.0.9.96
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 10.0.8.1
        DHCP Server . . . . . . . . . . . : 10.0.8.1
        DNS Servers . . . . . . . . . . . : 139.184.32.27
                                            139.184.32.25
                                            139.184.32.26
        Lease Obtained. . . . . . . . . . : 01 March 2006 13:17:34
        Lease Expires . . . . . . . . . . : 01 March 2006 16:17:34

Numerous people have said that a subnet mask of 255.255.255.255 will not work. But that is precisely what windows gives me. I really don't understand...

On the subject of proxies ... I have tried to configure the automatic proxy url through the Gnome configuration manager (previously I had just done it through firefox). But this doesn't work either. I shall try manual config later. If anyone knows more about this I would much appreciate it. 

Thanks everyone.

---

### Post by claes on 2006-03-01
Could you please ask your network admin why they use a subnet mask of 255.255.255.255 in the dhcp server. To my knowledge this is wrong. Not sure if microsoft have changed the ip stack in windows to work with that subnet mask. Very curious to why they have configured it like that. 

Claes

---

### Post by grw on 2006-03-01
I'll look into it.

---

### Post by grw on 2006-03-09
Sorry to take so long to get back about this. The computer people here are not so easy to get in touch with. 

What I have been told about the 255.255.255.255 netmask is that "it's so that each connection looks as if it's alone on it's own network, so that it can't interfere with others". 

The person who told me this has sent my query on to someone else for more information but has not yet had a response. Patience is a virtue, so they say! Will post more when I can...

---

### Post by grw on 2006-06-12
I have a solution I think (after all these months). Thre seems to be a bug in Ubuntu (at least in 5.10 and 6.06). You can fix the problem by making a small change in /etc/dhcp3/dhclient-script

Scroll down until you find the line: for router in $new_routers; do
Then replace:
            for router in $new_routers; do
                route add default dev $interface gw $router $metric_arg
            done
with
            for router in $new_routers; do
                route add -host dev $interface gw $router
                route add default dev $interface gw $router $metric_arg
            done

See this bug report for details:[https://launchpad.net/distros/ubuntu/+source/dhcp3/+bug/33382](https://launchpad.net/distros/ubuntu/+source/dhcp3/+bug/33382) 

Don't know why Ubuntu haven't fixed this problem

---

### Post by wombat20 on 2006-06-25
Many thanks for sharing this information.  I'm very happy to have this fixed.  :)

**_Worth noting however, that:_**
```
 for router in $new_routers; do
```
...appears twice in the **dhclient-script** file, and you have to get both occurrences!

---

### Post by grw on 2006-06-26
I didn't realise it appeared twice. Thanks.

I can now access teh network but not with teh solution that I give above. This is what works for me (fix I got from my network admin people):

for router in $new_routers; do

# !!! hack

if [ "$new_subnet_arg" == 'netmask 255.255.255.255' ]; then

	route add -host $router dev $interface

fi

# !!! end of hack

                route add default dev $interface gw $router $metric_arg

            done

One problem that remains is that I can't update repository indexes - apt-get won't work. Don't know if this is related to the dhcp bug or the fact that I am behind a proxy server or what. I have just tried adding the fix to the second 'for router in $new_routers; do' line (actually there are three) bu no luck.

---

### Post by robertmcox on 2006-06-30
Officially, your IT staff is *wrong* -- their DHCP server should be using a different subnet mask; the one they gave you is a host-only netmask (just like they said) and puts your default gateway on a different network so you can't route to it!

Now, how to fix it.....

(One solution is to use a static IP and put the correct netmask of 255.255.255.0)

---

