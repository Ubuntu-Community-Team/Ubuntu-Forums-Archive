---
title: "Internet Stopped Working"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by dabestharpis on 2009-05-28
Can someone please help me? I can no longer access the internet in Ubuntu 9.04. It worked fine previously in Ubuntu 9.04. I am connecting wirelessly with a PCMCIA card. I have tried more than one card but still have had no luck. I am duel booting with Windows XP and they work fine in that. If I run sudo lshw -C network in the terminal it tells me that me card is disabled. Any help would be greatly appreciated.

---

### Post by dabestharpis on 2009-05-28
Update: Ubuntu lets me connect to my wireless network but when I open firefox I got "server not found"

---

### Post by dabestharpis on 2009-05-30
*bump*

---

### Post by superprash2003 on 2009-05-31
post output of the following
1)iwconfig
2)ifconfig

---

### Post by dabestharpis on 2009-06-02
root@eric-laptop:~# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:0f:9d:24  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe0f:9d24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2044 (2.0 KB)  TX bytes:684 (684.0 B)

eth0      Link encap:Ethernet  HWaddr 00:02:8a:a5:00:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23184 (23.1 KB)  TX bytes:23184 (23.1 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-0F-9D-24-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1196 errors:0 dropped:0 overruns:0 frame:12918
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:91748 (91.7 KB)  TX bytes:6290 (6.2 KB)
          Interrupt:11 



root@eric-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Eric1"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:3F:7E:D6:4C   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:ff   Fragment thr:off
          Encryption key:3042-9161-95   Security mode:restricted
          Power Management:off
          Link Quality=54/70  Signal level=-40 dBm  Noise level=-94 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by dabestharpis on 2009-06-02
Sorry, no clue why the smiley faces were added. To see the output of the commands without the smiley faces you can download a TXT file of them here:

[http://www.mediafire.com/?sharekey=739a91f3634cb85224a64199ac7f73e5e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=739a91f3634cb85224a64199ac7f73e5e04e75f6e8ebb871)

---

### Post by Iowan on 2009-06-02
The forum "conveniently" interprets colon-O and colon-D (among others) as smilies.  You can avoid that by enclosing the text in "code" tags (the # icon). There's also an option at the bottom to turn off smilies.

"Disabled" suggests a driver problem... outta my league.

---

### Post by superprash2003 on 2009-06-03
post output of
1)route -n
2)ping 208.67.222.222

---

### Post by dabestharpis on 2009-06-03
root@eric-laptop:~# ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ect...



root@eric-laptop:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 ath0

---

### Post by superprash2003 on 2009-06-04
in your terminal type
1)sudo ifdown eth0
2)sudo ifdown wifi0

now try to ping again..

---

### Post by dabestharpis on 2009-06-04
root@eric-laptop:~# sudo ifdown eth0
ifdown: interface eth0 not configured

root@eric-laptop:~# sudo ifdown wifi0
ifdown: interface wifi0 not configure

root@eric-laptop:~# ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 208.67.222.222 ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8063ms

---

### Post by tumescentliposuction on 2009-06-05
Hello...
          There are lots of reason behind that so try to contact your ISP because you can't get exact answer from forums...

---

### Post by dabestharpis on 2009-06-05
I contacted my ISP (Comcast) and told that I was running Linux and what my problem was, but they were no help. They just told to follow the instructions here:

[http://www.pocketpcfaq.com/wce/linux-serial.htm](http://www.pocketpcfaq.com/wce/linux-serial.htm)

---

### Post by dabestharpis on 2009-06-08
Does nobody have any other ideas? Please help. I really do not want to do a clean install, but I'm afraid that's my only option.

---

### Post by Iowan on 2009-06-08
Wireless is NOT my forte, but...
Edit **/etc/udev/rules.d/70-persistent-net.rules** Comment out (#) the lines for **wifi0** definition. Reboot. [Here]("http://ubuntuforums.org/showthread.php?p=7421639#post7421639") is a slightly more aggressive version (post #5).

---

### Post by dabestharpis on 2009-06-09
I tried your advice but that did not work. Then I tried the more aggressive approach but that did not work either. Any other ideas?

---

### Post by Iowan on 2009-06-09
What is in */etc/udev/rules.d/70-persistent-net.rules*? 
What is current result of **ifconfig -a**?
Your router is at 10.0.0.1?
What's in */etc/resolv.conf*?
Is there a firewall running that might be blocking?

---

### Post by dabestharpis on 2009-06-10
In */etc/udev/rules.d/70-persistent-net.rules* before I tried your advice or the more aggressive approach:

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1031 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:8a:a5:00:a9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0013 (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:46:0f:9d:24", ATTR{type}=="1", KERNEL=="ath*", NAME="ath0"

# PCI device 0x168c:0x0013 (ath5k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:46:0f:9d:24", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x10ec:0x8180 (rtl8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:66:b9:94:25", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

When I tried your advice I removed the entry for "wlan0".  When I tried the more aggressive approach I removed the the wlan1, wlan0, eth0, ath0. Now after trying the more aggressive approach and rebooting my PC more than once I only see the entry's for eth0 and ath0.

In */etc/resolv.conf*:

# Generated by NetworkManager
domain WORKGROUP
search WORKGROUP
nameserver 208.67.222.222
nameserver 208.67.220.220

The result of ifconfig -a is:

root@eric-laptop:~# ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:13:46:0f:9d:24  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe0f:9d24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8063 (8.0 KB)  TX bytes:684 (684.0 B)

eth0      Link encap:Ethernet  HWaddr 00:02:8a:a5:00:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25760 (25.7 KB)  TX bytes:25760 (25.7 KB)

pan0      Link encap:Ethernet  HWaddr 26:f0:48:72:e3:d1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-0F-9D-24-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20849 errors:0 dropped:0 overruns:0 frame:8280
          TX packets:671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1569591 (1.5 MB)  TX bytes:32146 (32.1 KB)
          Interrupt:11 


As I mentioned earlier in this thread I recently installed firestarter and then my internet stopped working. So I removed firestarter but my internet still does not work. Other than firestarter I never installed any firewalls. If I look in Synaptic for firewalls the only things that come up as installed are: 
iptables
ufw
wget
Also, I do not know if this is any help but before I installed firestarter I installed Guarddog. When I installed Guarddog my internet stopped working too. So I simply removed it and my internet was working. Later, I then installed firestarter. And again my internet stopped working. So I simply removed it thinking that would fix my internet. However, that did not happen when I removed firestarter. As I am without internet right now in ubuntu.

---

### Post by Iowan on 2009-06-10
IPTABLES is another area I know little (next to nothing) about... but another [thread]("http://ubuntuforums.org/showthread.php?t=1150372") suggested **iptables -F** to flush the rules.  Although temporary, it *might* show if there's light at the end of the tunnel.

---

### Post by dabestharpis on 2009-06-10
I tried iptables -F . But nothing seemed to happen and I still got "server not found."

root@eric-laptop:~# iptables -F
root@eric-laptop:~#

---

### Post by Iowan on 2009-06-11
Curious - my machine complained when I tried it without **sudo**. What are results of **sudo iptables -L**?

---

### Post by dabestharpis on 2009-06-17
Thanks for the help but none of the solutions seemed to work. So I just did a clean install. Thanks though.

---

