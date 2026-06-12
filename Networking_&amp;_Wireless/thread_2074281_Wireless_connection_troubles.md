---
title: "Wireless connection troubles"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by Nagantman on 2012-10-21
Hi, a few days back after some struggling. I managed to install  Ubuntu 11.10 on my 2010 13' Macbook pro 7,1. I'm very new to Linux and entering commands through Terminal. I don't know how to search for wireless networks so, I added it into the wireless connections. But I don't know how to get my BSSID/SSID or MAC device number, I think it's called. So I tried getting onto the internet with an Ethernet cable. When I plugged it in it still wouldn't make a connection. Then I had noticed it said firmware missing by all the connection/wireless information. I have already used a looootttt of google to no avail ](*,) . Any help with this problem will be greatly appreciated thank you in advance

---

### Post by chili555 on 2012-10-21
Let's see what kind of wireless card you have and we'll find some firmware. Please open a terminal and do:```
lspci -nn | grep 0280
```That pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by offgridguy on 2012-10-21
You may need the linux compatible driver for your network device.  You could try a google search
using your device name driver linux

---

### Post by Nagantman on 2012-10-21
Chili555 unfortunately I don't have the laptop right now and I wont for another 4 hours or so. So just please keep this thread in mind, because as soon as I get it later today i'll do what you said and let you know.

---

### Post by chili555 on 2012-10-21
> **Nagantman said:**
> Chili555 unfortunately I don't have the laptop right now and I wont for another 4 hours or so. So just please keep this thread in mind, because as soon as I get it later today i'll do what you said and let you know.I'm subscribed, so I'll get an email when you reply. I'll look forward to your result.

---

### Post by Nagantman on 2012-10-21
Alright chili I just got my laptop back. My wireless card is BCM4322.

---

### Post by chili555 on 2012-10-21
> **Nagantman said:**
> Alright chili I just got my laptop back. My wireless card is BCM4322.That's not what I asked for. Please see post #2.

---

### Post by Nagantman on 2012-10-21
After putting in that command line> lspci -nn | grep 0280 this is what came up in Terminal- 02:00.0 Network controller [0290]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01). Bear with me like I said I am new to this.

---

### Post by chili555 on 2012-10-21
>  Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:432b[/COLOR]] Your device needs:```
sudo apt-get install bcmwl-kernel-source
```Do you have a working ethernet connection? If so and if you can get connected, this will be quick and easy. If not, we have a big job ahead of us. 

If it's not working, let's try to see why:```
lspci -nn | grep 0200
```

---

### Post by Nagantman on 2012-10-21
I tried an Ethernet cable the other night and it didn't work. >  lspci -nn | grep 0200 03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)

---

### Post by chili555 on 2012-10-21
Your ethernet card is supposed to work with the driver *tg3*. I am not sure *tg3* is present in 11.10. Let's check:```
modinfo tg3 | grep 1684
```If it is present an drives your device, you'll see:```
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]1684[/COLOR]sv*sd*bc*sc*i*
```If so, load the driver and see if you can get a wired ethernet connection:```
sudo modprobe tg3
```If you can, install the wireless driver:```
sudo apt-get install bcmwl-kernel-source
```After we find out what happens, we'll set the driver *tg3* to load on boot automatically.

---

### Post by Nagantman on 2012-10-21
I did get this> alias:          pci:v000014E4d00001684sv*sd*bc*sc*i* but when I plugged in my Ethernet cable and typed- sudo modprobe tg3 after that I put in my password. But nothing happened and I still couldn't connect.

---

### Post by chili555 on 2012-10-21
Let's see what's going on under the hood:```
dmesg | grep -e tg3 -e eth0
```I realize you can't copy and paste with no connection; just try to pick out any error or warning messages or anything that smells funny and post it here.

---

### Post by Nagantman on 2012-10-21
Unfortunately I have no idea what to look for.  
Link is down 
Link is up at 100Mbps, full duplex 
Flow control is on for TX and on for Rx 
Link is down
No IPv6 routers present. 
     All of that is mainly at the bottom of the Terminal window. Ethernet cable was not plugged in when I executed that command by the way

---

### Post by Nagantman on 2012-10-21
I gotta go again, I will have the computer, pretty much all week so, i'll be on when I get out of school tomorrow. Then we can resume this sound good?

---

### Post by chili555 on 2012-10-21
Sounds good. 

However, this doesn't:>  Ethernet cable was not plugged in when I executed that command by the wayIn order to troubleshoot, we need to see your readings when it *IS* plugged in and trying to connect.

---

### Post by Nagantman on 2012-10-21
Okay at 3 p.m. tomorrow i'll update you on that.

---

### Post by Nagantman on 2012-10-22
With the Ethernet plugged in and typing the command you gave me this is what I got. [1.106373] tg3.c:v3.119 (May 18, 2011)
[ 1.106391] tg3 0000:03:00.0: PCI INT A -> Link [Z00N]  -> GSI 21 (level, low) -> IRQ 21 
[ 1.106400] tg3 0000:03:00.0: setting latency timer to 64 
[ 1.216179] tg3 0000:03:00.0: eth0: Tigon3 [partno(BCM95764m) rev 5784100] (PCI Express) MAC address 10:9a:dd:48:2f:74 
[ 1.216184] tg3 0000:03:00.0: eth0: attached PHY is 5784 (10/100/1000Base- T Ethernet) (Wirespeed[1], EEE[0]) 
[ 1.216187] tg3 0000:03:00.0: eth0: RXcsums [1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1] 
[ 1.216189] tg3 0000:03:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[16.730059] tg3 0000:03:00.0: irq 44 for MSI/MSI-x
[17.497326] ADDRCONF(NETDEV_UP): eth0: Link is not ready
[562.792899] tg3 0000:03:00.0: eth0: Link is up at 100 Mbps, full duplex 
[562.792899] tg3 0000:03:00.0: eth0: Flow control is on TX and on for RX 
[562.794036] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[573.088149] eth0: no IPv6 routers present 
{596.824046] eth0: no IPv6 routers present 
        That is it. Whew.

---

### Post by chili555 on 2012-10-22
> [562.794036] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[573.088149] eth0: no IPv6 routers present
{596.824046] eth0: no IPv6 routers present That's pretty typical of an interface that's connected! Let's see:```
ifconfig
sudo cat /var/log/syslog | grep eth0 | tail -n10
```If you are having trouble getting the text posted (by pencil??), I have a suggestion.

---

### Post by Nagantman on 2012-10-22
What would that suggestion should be, I will still type it all out, but it is rather tedious.

---

### Post by chili555 on 2012-10-22
> **Nagantman said:**
> What would that suggestion should be, I will still type it all out, but it is rather tedious.You can copy and paste from the terminal to a text document, such as gedit or kate and save it as anything, such as info.txt. Drag and drop the file info.txt to a USB key and open it in Windows or however you are answering these posts and copy and paste it to your forum reply. Please see attached.

---

### Post by Nagantman on 2012-10-22
Won't detect flash drive, can we talk over AIM instead?

---

### Post by chili555 on 2012-10-22
Nope, sorry. A big part of the forum's usefulness is for searchers to see what worked and didn't months and years later. They can't read my IM logs.

---

### Post by Nagantman on 2012-10-22
Okay, I understand. So like I said the computer didn't detect the flash drive, so i'm not really sure what I should do. Are there specific things you want me to look for to tell you. Or shall I just type in all the results again?

---

### Post by chili555 on 2012-10-22
I'm afraid you'll have to type them in. You can abbreviate MAC addresses and other trivial details: mac:xx:yy

---

### Post by Nagantman on 2012-10-22
Registering new address record for fe80 : :129a:ddff:fe48:2f74 on eth0.*.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6. 
      does that tell you anything or do you need more

---

### Post by chili555 on 2012-10-22
That tells me the ethernet device is asking for an IP address, just as we hope and expect.

What happens next? Does it get one or time out? Something like this??> Registering new address record for **192.168.1.6** on eth0.IPv4.

---

### Post by Nagantman on 2012-10-22
I get up to stage 5 but the IP Configure fails because of no IP Configuration found. ip config failed reason ip-config-unavailable. If this is noteworthy, during installation I never set up anything relating to DHCP since I don't really know what it is.

---

### Post by Nagantman on 2012-10-23
It said online this version of ubuntu on this mac, wired and wireless should work out of the box. So many issues : |

---

### Post by chili555 on 2012-10-23
Have you put any possibly confusing or conflicting settings in Network Manager? What does this tell us?```
cat /etc/network/interfaces
```DHCP is the most common method for a router or access point to hand out an IP address. If Network Manager is set to use DHCP, and it is by default, it says to the router, 'may I have any old IP address; I don't care what it is.' Assuming everything is working correctly, the router assigns one.

---

### Post by Nagantman on 2012-10-23
> **chili555 said:**
>  'may I have any old IP address; I don't care what it is.' 
I don't know how to get one :| or check for one. 
# this file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5) 
 
# The loopback network interface 
auto lo
iface lo inet loopback

---

### Post by chili555 on 2012-10-23
> # this file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5)

# The loopback network interface
auto lo
iface lo inet loopbackPerfect!

You get one with Network Manager. Check:```
ifconfig
```Here is an example from my machine:> wlan0     Link encap:Ethernet  HWaddr xx:94:6b:99:55:xx  
          [COLOR="Red"]inet addr:192.168.1.6[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5a94:6bff:fe99:55a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:561576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:706863904 (706.8 MB)  TX bytes:56614549 (56.6 MB)If you have one, you should be able to reach Google:```
ping -c3 www.google.com
```> chili@LAPTOP410:~$ ping -c3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (173.194.75.103) 56(84) bytes of data.
64 bytes from ve-in-f103.1e100.net (173.194.75.103): icmp_req=1 ttl=42 time=37.2 ms
64 bytes from ve-in-f103.1e100.net (173.194.75.103): icmp_req=2 ttl=42 time=37.5 ms
64 bytes from ve-in-f103.1e100.net (173.194.75.103): icmp_req=3 ttl=42 time=37.2 ms

--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 37.204/37.313/37.507/0.209 ms


---

### Post by Nagantman on 2012-10-23
eth0       Link encap:Ethernet   HWaddr 10:8a:dd:48:2f:74 
UP BROADCAST MULTICAST MTU:1500 Metric:1      
After putting in ping -c3 [www.google.com](www.google.com) 
Terminal said "unknown host [www.google.com](www.google.com)" 
Also on my terminal after typing in ifconfig for RX packets and TX packets everything was 0 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:host 
UP LOOPBACK RUNNING MTU:16436 Metric:1

---

### Post by Nagantman on 2012-10-26
chris12393@Chris:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 10:9a:dd:48:2f:74  
          inet6 addr: fe80::129a:ddff:fe48:2f74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:371 (371.0 B)  TX bytes:2355 (2.3 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9472 (9.4 KB)  TX bytes:9472 (9.4 KB)

chris12393@Chris:~$

---

### Post by chili555 on 2012-10-26
Awesome! Now how about:```
sudo cat /var/log/syslog | grep -e tg3 -e eth0 -e etwork | tail -n20
```Thanks.

---

### Post by Nagantman on 2012-10-26
chris12393@Chris:~$ sudo cat /var/log/syslog | grep -e tg3 -e eth0 -e etwork | tail -n20
[sudo] password for chris12393: 
Oct 27 00:13:21 Chris NetworkManager[847]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Oct 27 00:13:21 Chris NetworkManager[847]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 27 00:13:21 Chris NetworkManager[847]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Oct 27 00:13:21 Chris NetworkManager[847]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 27 00:13:21 Chris NetworkManager[847]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Oct 27 00:13:21 Chris NetworkManager[847]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Oct 27 00:13:21 Chris NetworkManager[847]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 27 00:13:21 Chris NetworkManager[847]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 27 00:13:21 Chris kernel: [  113.848537] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 27 00:13:21 Chris NetworkManager[847]: <info> dhclient started with pid 1989
Oct 27 00:13:21 Chris NetworkManager[847]: <info> Activation (eth0) Beginning IP6 addrconf.
Oct 27 00:13:21 Chris NetworkManager[847]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Oct 27 00:13:21 Chris NetworkManager[847]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct 27 00:13:21 Chris dhclient: Listening on LPF/eth0/10:9a:dd:48:2f:74
Oct 27 00:13:21 Chris dhclient: Sending on   LPF/eth0/10:9a:dd:48:2f:74
Oct 27 00:13:21 Chris dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 27 00:13:23 Chris avahi-daemon[768]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::129a:ddff:fe48:2f74.
Oct 27 00:13:23 Chris avahi-daemon[768]: New relevant interface eth0.IPv6 for mDNS.
Oct 27 00:13:23 Chris avahi-daemon[768]: Registering new address record for fe80::129a:ddff:fe48:2f74 on eth0.*.
Oct 27 00:13:23 Chris dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
chris12393@Chris:~$

---

### Post by chili555 on 2012-10-26
That looks soooooo close! Please make sure, when you right-click the Network Manager icon and select Edit Connections, that there are no extra settings entered. If there are, please remove them. Please see attached.

Also, we see no entries related to tg3, the ethernet driver. Let's dig deeper:```
sudo cat /var/log/syslog | grep tg3
nm-tool
```

---

### Post by Nagantman on 2012-10-26
chris12393@Chris:~$ sudo cat /var/log/syslog | grep tg3
[sudo] password for chris12393: 
Oct 24 01:34:42 Chris kernel: [    1.070393] tg3.c:v3.119 (May 18, 2011)
Oct 24 01:34:42 Chris kernel: [    1.070523] tg3 0000:03:00.0: PCI INT A -> Link[Z00N] -> GSI 21 (level, low) -> IRQ 21
Oct 24 01:34:42 Chris kernel: [    1.070531] tg3 0000:03:00.0: setting latency timer to 64
Oct 24 01:34:42 Chris kernel: [    1.329022] tg3 0000:03:00.0: eth0: Tigon3 [partno(BCM95764m) rev 5784100] (PCI Express) MAC address 10:9a:dd:48:2f:74
Oct 24 01:34:42 Chris kernel: [    1.329027] tg3 0000:03:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Oct 24 01:34:42 Chris kernel: [    1.329030] tg3 0000:03:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Oct 24 01:34:42 Chris kernel: [    1.329032] tg3 0000:03:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Oct 24 01:34:42 Chris NetworkManager[762]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Oct 24 01:34:42 Chris kernel: [   16.797396] tg3 0000:03:00.0: irq 44 for MSI/MSI-X
Oct 26 22:45:39 Chris kernel: [    1.086433] tg3.c:v3.119 (May 18, 2011)
Oct 26 22:45:39 Chris kernel: [    1.086452] tg3 0000:03:00.0: PCI INT A -> Link[Z00N] -> GSI 21 (level, low) -> IRQ 21
Oct 26 22:45:39 Chris kernel: [    1.086461] tg3 0000:03:00.0: setting latency timer to 64
Oct 26 22:45:39 Chris kernel: [    1.196480] tg3 0000:03:00.0: eth0: Tigon3 [partno(BCM95764m) rev 5784100] (PCI Express) MAC address 10:9a:dd:48:2f:74
Oct 26 22:45:39 Chris kernel: [    1.196485] tg3 0000:03:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Oct 26 22:45:39 Chris kernel: [    1.196488] tg3 0000:03:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Oct 26 22:45:39 Chris kernel: [    1.196490] tg3 0000:03:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Oct 26 22:45:39 Chris NetworkManager[788]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Oct 26 22:45:39 Chris kernel: [   16.820332] tg3 0000:03:00.0: irq 44 for MSI/MSI-X
Oct 26 22:57:07 Chris kernel: [  705.017548] tg3 0000:03:00.0: eth0: Link is up at 100 Mbps, full duplex
Oct 26 22:57:07 Chris kernel: [  705.017558] tg3 0000:03:00.0: eth0: Flow control is on for TX and on for RX
Oct 26 22:57:15 Chris kernel: [  712.622791] tg3 0000:03:00.0: eth0: Link is down
Oct 27 00:11:44 Chris kernel: [    1.096874] tg3.c:v3.119 (May 18, 2011)
Oct 27 00:11:44 Chris kernel: [    1.096890] tg3 0000:03:00.0: PCI INT A -> Link[Z00N] -> GSI 21 (level, low) -> IRQ 21
Oct 27 00:11:44 Chris kernel: [    1.096899] tg3 0000:03:00.0: setting latency timer to 64
Oct 27 00:11:44 Chris kernel: [    1.205452] tg3 0000:03:00.0: eth0: Tigon3 [partno(BCM95764m) rev 5784100] (PCI Express) MAC address 10:9a:dd:48:2f:74
Oct 27 00:11:44 Chris kernel: [    1.205456] tg3 0000:03:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Oct 27 00:11:44 Chris kernel: [    1.205459] tg3 0000:03:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Oct 27 00:11:44 Chris kernel: [    1.205462] tg3 0000:03:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Oct 27 00:11:44 Chris NetworkManager[847]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Oct 27 00:11:45 Chris kernel: [   17.308128] tg3 0000:03:00.0: irq 44 for MSI/MSI-X
Oct 27 00:13:21 Chris kernel: [  113.847323] tg3 0000:03:00.0: eth0: Link is up at 100 Mbps, full duplex
Oct 27 00:13:21 Chris kernel: [  113.847334] tg3 0000:03:00.0: eth0: Flow control is on for TX and on for RX
Oct 27 00:17:04 Chris kernel: [  337.044097] tg3 0000:03:00.0: eth0: Link is down
Oct 27 00:48:39 Chris kernel: [ 2231.436633] tg3 0000:03:00.0: eth0: Link is up at 100 Mbps, full duplex
Oct 27 00:48:39 Chris kernel: [ 2231.436643] tg3 0000:03:00.0: eth0: Flow control is on for TX and on for RX
Oct 27 00:50:57 Chris kernel: [ 2369.751573] tg3 0000:03:00.0: eth0: Link is down
Oct 27 00:50:59 Chris kernel: [ 2371.408727] tg3 0000:03:00.0: eth0: Link is up at 100 Mbps, full duplex
Oct 27 00:50:59 Chris kernel: [ 2371.408738] tg3 0000:03:00.0: eth0: Flow control is on for TX and on for RX
Oct 27 00:51:00 Chris kernel: [ 2372.425329] tg3 0000:03:00.0: eth0: Link is down
chris12393@Chris:~$ 

For Wired connection 1 IPv4 settings, everything was as the picture you attached. Aside from the "Require IPv3 addressing for this connection to complete" check box, after I unchecked it I still couldn't connect.

---

### Post by chili555 on 2012-10-26
Studying...

I'll check in tomorrow.

---

### Post by Nagantman on 2012-10-26
Okay, thanks by the way for all the help. I know it has been a mess but I really appreciate it.

---

### Post by chili555 on 2012-10-27
I keep hoping, fruitlessly, it seems, that a miracle will occur and the ethernet will have connected. Oh, well.

Let's install bcmwl-kernel-source without any internet. :cry: :cry:

Please download the package here: [http://packages.ubuntu.com/oneiric/bcmwl-kernel-source](http://packages.ubuntu.com/oneiric/bcmwl-kernel-source)

Be sure to get either the 32-bit or 64-bit package, known respectively as i386 and amd64. Find which you have :```
arch
```32-bit will return i686 and 64-bit will return x86_64.

You will also need all the dependencies: dkms, libc6-dev, linux-headers-generic and linux-libc-dev. linux-headers-generic also needs linux-headers matching your running kernel version:```
uname -r
```For instance, on my system:> chili@LAPTOP410:~$ uname -r
3.5.0-17-genericSo, if I were installing bcmwl-kernel-source, I'd also need linux-headers-*3.5.0-17-generic*. 

I suggest you download all these packages and drag and drop them to a USB key and then to your desktop. Then open a terminal and do:```
cd Desktop
sudo dpkg -i *.deb
```The wildcard * means install _everything_ that's a .deb. If there are any complaints about other packages that are required, download them and install them, too.

I wish there was an easier way. Post back any questions or errors.

---

### Post by Nagantman on 2012-10-28
Sorry it took me so long to get back to you. Been preparing for the hurricane. After doing what you said. I had some issues, here is the Terminal output. 
chris12393@Chris:~$ cd Desktop sudo dpkg -i *.deb
chris12393@Chris:~/Desktop$ 
chris12393@Chris:~/Desktop$ sudo dpkg -i *.deb
[sudo] password for chris12393: 
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 124664 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu4_amd64.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from dkms_2.2.0.2-1ubuntu4_all.deb) ...
Preparing to replace libc6-dev 2.13-20ubuntu5 (using libc6-dev_2.13-20ubuntu5.2_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace linux-headers-3.0.0-12-generic 3.0.0-12.20 (using linux-headers-3.0.0-12-generic_3.0.0-12.20_amd64.deb) ...
Unpacking replacement linux-headers-3.0.0-12-generic ...
Preparing to replace linux-libc-dev 3.0.0-12.20 (using linux-libc-dev_3.0.0-26.43_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
dpkg: dependency problems prevent configuration of dkms:
 dkms depends on patch; however:
  Package patch is not installed.
dpkg: error processing dkms (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.13-20ubuntu5.2); however:
  Version of libc6 on system is 2.13-20ubuntu5.
 libc6-dev depends on libc-dev-bin (= 2.13-20ubuntu5.2); however:
  Version of libc-dev-bin on system is 2.13-20ubuntu5.
dpkg: error processing libc6-dev (--install):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.0.0-12-generic (3.0.0-12.20) ...
Examining /etc/kernel/header_postinst.d.
Setting up linux-libc-dev (3.0.0-26.43) ...
dpkg: dependency problems prevent configuration of bcmwl-kernel-source:
 bcmwl-kernel-source depends on dkms; however:
  Package dkms is not configured yet.
 bcmwl-kernel-source depends on libc6-dev; however:
  Package libc6-dev is not configured yet.
dpkg: error processing bcmwl-kernel-source (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 dkms
 libc6-dev
 bcmwl-kernel-source
chris12393@Chris:~/Desktop$

---

### Post by chili555 on 2012-10-28
> dpkg: dependency problems prevent configuration of dkms:
dkms depends on patch; however:
Package patch is not installed.You will need to download and include *patch* in the files you want to install.> libc6-dev depends on libc6 (= 2.13-20ubuntu5.2); however:
Version of libc6 on system is 2.13-20ubuntu5.
libc6-dev depends on libc-dev-bin (= 2.13-20ubuntu5.2); however:
Version of libc-dev-bin on system is 2.13-20ubuntu5.You will need to get the later versions of these packages; namely, libc6-*2.13-20ubuntu5.2* and libc-dev-bin-*2.13-20ubuntu5.2*.

Get these three packages, add them to your desktop and try again.

Really not too bad, actually!

I hope the hurricane's damage misses you. Fingers crossed.

---

### Post by Nagantman on 2012-10-28
I'm confused the files you said I have to download. I entered them in google, and downloaded. But those are the ones I already got from Ubuntu packages. Also when I do get the correct ones I assume I remove the old ones from my desktop and then run the command.

---

### Post by chili555 on 2012-10-28
You want to get them here: [http://packages.ubuntu.com/oneiric/patch](http://packages.ubuntu.com/oneiric/patch)

These two just need newer versions than you have: [http://packages.ubuntu.com/oneiric/libc6](http://packages.ubuntu.com/oneiric/libc6) 

Note it says:> libc6 ([COLOR="Red"]2.13-20ubuntu5.2[/COLOR])And this: [http://packages.ubuntu.com/oneiric/libc-dev-bin](http://packages.ubuntu.com/oneiric/libc-dev-bin)> libc-dev-bin ([COLOR="Red"]2.13-20ubuntu5.2[/COLOR]) I'd probably install libc6 alone:```
sudo dpkg -i libc6*.deb
```Then create a folder on your desktop named anything, like 'done.' Drag and drop libc6 into it. If you have any older versions on your desktop, delete them. Then try the remaining files as before:```
cd Desktop
sudo dpkg -i *.deb
```Note and post any errors. I will only be here another four hours!

---

### Post by Nagantman on 2012-10-28
[http://s1291.beta.photobucket.com/user/nagantman/media/Issues.png.html?sort=3&o=0](http://s1291.beta.photobucket.com/user/nagantman/media/Issues.png.html?sort=3&o=0) 
I don't get it :( and when I tried doing libc6 alone I got the same issue.

---

### Post by Nagantman on 2012-10-28
Never mind that last post. Here: 
chris12393@Chris:~$ cd Desktop
chris12393@Chris:~/Desktop$ sudo dpkg -i libc6*.deb
[sudo] password for chris12393: 
(Reading database ... 124769 files and directories currently installed.)
Preparing to replace libc6 2.13-20ubuntu5.2 (using libc6_2.13-20ubuntu5.2_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on libc-bin (= 2.13-20ubuntu5.2); however:
  Version of libc-bin on system is 2.13-20ubuntu5.
dpkg: error processing libc6 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6
chris12393@Chris:~/Desktop$

---

### Post by chili555 on 2012-10-28
Here you go! [http://packages.ubuntu.com/oneiric/libc-bin](http://packages.ubuntu.com/oneiric/libc-bin)

---

### Post by Nagantman on 2012-10-28
Okay, Kernel depends upon libc6. When I go to install libc6 everything runs smooth and this is what it says at the end of the Terminal. ldconfig deferred processing now taking place. Then after I try to install all packages and I get the Kernel error. Saying it is because libc6 isn't configured.

---

### Post by chili555 on 2012-10-28
Please try, one at a time, libc-bin and then libc-dev-bin and then linux-libc-dev. Then move those .debs into your folder *done*. Now try the remaining on your desktop.

---

### Post by Nagantman on 2012-10-28
Did exactly what you said. Still getting the libc6 not configured, but when I go to install it there are no issues?????

---

### Post by chili555 on 2012-10-28
Please try:```
sudo dpkg-reconfigure libc6_2*.deb
```Then try the other *lib* packages.

---

### Post by Nagantman on 2012-10-28
chris12393@Chris:~/Desktop$ sudo dpkg-reconifgure libc6_2*.deb
sudo: dpkg-reconifgure: command not found
chris12393@Chris:~/Desktop$ sudo dpkg-reconfigure libc6_2*.deb
Package `libc6_2.13-20ubuntu5.2_amd64.deb' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: libc6_2.13-20ubuntu5.2_amd64.deb is not installed
chris12393@Chris:~/Desktop$ sudo dpkg -i libc6*.deb
(Reading database ... 124769 files and directories currently installed.)
Preparing to replace libc6 2.13-20ubuntu5.2 (using libc6_2.13-20ubuntu5.2_amd64.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.13-20ubuntu5.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
chris12393@Chris:~/Desktop$ 
What can you tell me?

---

### Post by chili555 on 2012-10-28
> $ sudo dpkg -i libc6*.deb
(Reading database ... 124769 files and directories currently installed.)
Preparing to replace libc6 2.13-20ubuntu5.2 (using libc6_2.13-20ubuntu5.2_amd64.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.13-20ubuntu5.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking placeThat looks perfect. Now drop it in to 'done' and try the other lib-whatever packages.

---

### Post by Nagantman on 2012-10-28
Did all the other lib ones. Then did "sudo dpkg -i *.deb" and I got the following back.
chris12393@Chris:~/Desktop$ sudo dpkg -i *.deb
(Reading database ... 124769 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu4 (using bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu4_amd64.deb) ...
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace dkms 2.2.0.2-1ubuntu4 (using dkms_2.2.0.2-1ubuntu4_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-3.0.0-12-generic 3.0.0-12.20 (using linux-headers-3.0.0-12-generic_3.0.0-12.20_amd64.deb) ...
Unpacking replacement linux-headers-3.0.0-12-generic ...
Preparing to replace patch 2.6.1-2 (using patch_2.6.1-2_amd64.deb) ...
Unpacking replacement patch ...
dpkg: dependency problems prevent configuration of bcmwl-kernel-source:
 bcmwl-kernel-source depends on libc6-dev; however:
  Package libc6-dev is not configured yet.
dpkg: error processing bcmwl-kernel-source (--install):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.0.0-12-generic (3.0.0-12.20) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.0.0-12-generic /boot/vmlinuz-3.0.0-12-generic
Setting up patch (2.6.1-2) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Errors were encountered while processing:
 bcmwl-kernel-source
chris12393@Chris:~/Desktop$

---

### Post by chili555 on 2012-10-28
> bcmwl-kernel-source depends on libc6-dev; however:
Package libc6-dev is not configured yet.Please try to install it again:```
sudo dpkg -i libc6-dev*.deb
```Then try again.

I think we're really close!

---

### Post by Nagantman on 2012-10-28
I ran "sudo dpkg -i libc6*.deb" (not libc6-dev, I tried that and it didn't work) 3 or 4 times and got the same results I posted before. Then after "sudo dpkg -i *.deb" I got > bcmwl-kernel-source depends on libc6-dev; however:
Package libc6-dev is not configured yet. Then I ran > Code:
sudo dpkg-reconfigure libc6_2*.deb and Terminal said, that libc6_2.13-20ubuntu5.2_amd64.deb' is not installed and no info is available. So, it seems more than apparent that for some reason libc6 won't properly install.

---

### Post by chili555 on 2012-10-28
Please confirm that you have and have tried to install this: [http://packages.ubuntu.com/oneiric/libc6-dev](http://packages.ubuntu.com/oneiric/libc6-dev)

And this: [http://packages.ubuntu.com/oneiric/libc-dev-bin](http://packages.ubuntu.com/oneiric/libc-dev-bin)

And this: [http://packages.ubuntu.com/oneiric/linux-libc-dev](http://packages.ubuntu.com/oneiric/linux-libc-dev)

You might drag and drop these into a new folder 'libs' and do:```
cd Desktop/libs
sudo dpkg -i *.deb
```Then try the packages left on the desktop:```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by Nagantman on 2012-10-28
It worked here is the Terminal output.
chris12393@Chris:~$ cd Desktop
chris12393@Chris:~/Desktop$ sudo dpkg -i *.deb
[sudo] password for chris12393: 
(Reading database ... 124769 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu4 (using bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu4_amd64.deb) ...
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace dkms 2.2.0.2-1ubuntu4 (using dkms_2.2.0.2-1ubuntu4_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace libc-bin 2.13-20ubuntu5.2 (using libc-bin_2.13-20ubuntu5.2_amd64.deb) ...
Unpacking replacement libc-bin ...
Preparing to replace linux-headers-3.0.0-12-generic 3.0.0-12.20 (using linux-headers-3.0.0-12-generic_3.0.0-12.20_amd64.deb) ...
Unpacking replacement linux-headers-3.0.0-12-generic ...
Preparing to replace patch 2.6.1-2 (using patch_2.6.1-2_amd64.deb) ...
Unpacking replacement patch ...
Setting up libc-bin (2.13-20ubuntu5.2) ...
Setting up linux-headers-3.0.0-12-generic (3.0.0-12.20) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.0.0-12-generic /boot/vmlinuz-3.0.0-12-generic
Setting up patch (2.6.1-2) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu4) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-12-generic
Building for architecture x86_64
Building initial module for 3.0.0-12-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
W: Possible missing firmware /lib/firmware/nouveau/fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409c for module nouveau
chris12393@Chris:~/Desktop$

---

### Post by chili555 on 2012-10-28
> It worked Awesome. Now do:```
sudo modprobe wl
iwconfig
```Is your wireless working?

---

### Post by Nagantman on 2012-10-28
I got "FATAL: Module w1 not found." in the top right when I click on the internet symbol it still says "device not ready (firmware missing)" should I reboot and try > Code:
sudo modprobe wl
iwconfig again?

---

### Post by chili555 on 2012-10-28
>  "FATAL: Module w1 not found."Did you type double-you one or double-you ell? It is ell.```
sudo modprobe wl
dmesg | grep wl
```

---

### Post by Nagantman on 2012-10-28
woops, sorry the font looks rather odd on this old computer i'm using to get back to you. 
chris12393@Chris:~$ sudo modprobe wl
[sudo] password for chris12393: 
chris12393@Chris:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
chris12393@Chris:~$ sudo modprobe wl iwconfig
chris12393@Chris:~$ 
(there shouldn't be emoticons?? those are :0's)

---

### Post by chili555 on 2012-10-29
> chris12393@Chris:~$ sudo modprobe wl
[sudo] password for chris12393:
chris12393@Chris:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

[COLOR="Red"]wlan0[/COLOR] IEEE 802.11bg ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementn
I'm not sure I like that at all. Usually, the Broadcom wl driver creates an interface eth1, not wlan0. Perhaps you have conflicting drivers loaded.```
lsmod | grep -e wl -e b43 -e brcm
```> (there shouldn't be emoticons?? those are :0's) Right below the reply box, you can disable smilies in text.

---

### Post by Nagantman on 2012-10-29
chris12393@Chris:~$ lsmod | grep -e wl -e b43 -e brcm
wl                   2568210  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
chris12393@Chris:~$ 
Sorry it took me so long to get back to you.

---

### Post by Nagantman on 2012-10-29
You know i'm sorry and thanks for helping me. But I think i'm all set with the whole linux thing. I will be able to less on Linux than OS X and I don't have any experience with Terminal. Or how to program etc.

---

### Post by chili555 on 2012-10-29
> **Nagantman said:**
> You know i'm sorry and thanks for helping me. But I think i'm all set with the whole linux thing. I will be able to less on Linux than OS X and I don't have any experience with Terminal. Or how to program etc.Sorry I couldn't be of more assistance.

---

