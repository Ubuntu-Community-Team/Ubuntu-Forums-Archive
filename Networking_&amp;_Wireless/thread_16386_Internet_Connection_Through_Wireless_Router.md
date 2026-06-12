---
title: "Internet Connection Through Wireless Router"
date: 2005-02-21
forum: Networking &amp; Wireless
---

### Post by transkinetic on 2005-02-21
I Just installed Ubuntu onto my laptop. It auto detected my wireless card and I found connecting to my WEP encrypted network fairly straight forward; just punched the numbers into the network setup GUI. It now shows me as connected and gives a neat little display of the %signal strength. All is well but when I open up firefox it behaves as though I am without an internet connection. Is there some step I need to go through to get the connection being broadcast over my network or is it something to do with firefox?

Appreciate the help,

-Francois

---

### Post by alastair on 2005-02-21
Check your routing perhaps and network setup e.g. output of :

ifconfig -a
route -n
cat /etc/resolv.conf

Try using "ping" - ping the router, ping google by IP (66.102.11.99) and then by name ([www.google.com](www.google.com)) etc.

---

### Post by transkinetic on 2005-02-21
I am very new to linux and am not at all sure what you're suggesting.

I'm assuming that those are all bash commands.

When I typed ping <router ip> into bash I got an error reading "Network is unreachable."
Same thing when I typed ping <google's ip>.

I'll continue trying to learn bash semantics and commands but in the meantime, can anyone offer a more detail set of steps I should try?

---

### Post by alastair on 2005-02-22
OK - sorry if I assumed too much knowledge. I don't tend to use the GUI tools very much. It is useful to know the shell commands though - good to know and standard unix stuff.

I assume you know what your network IP addresses are roughly. Below, I will assume your wireless access point (or whatever) is IP address 192.168.0.100. 

In a bash shell :

1) To see your current network device configuration (i.e. IP address, status etc.), type :

ifconfig -a

2) To see your wireless network device connection status, type :

iwconfig

3) The network "route" for your machine is a table of "directions" to send network data i.e. if I want to conect to network A (e.g. 192.168.0.0), what device (route) should I send to? If there is no explicit "route", then send via the default route (device). To see your routes, type :

route -n

4) To see if a network or device is accessible, we can "ping" it i.e. send network packets and see if they get through. Try pinging something you should be connected to e.g. your wireless access point i.e. type :

ping 192.168.1.100

(assuming your access point is "192.168.1.100").

The output of these commands will help diagnose your problem.

---

### Post by transkinetic on 2005-02-24
Here's the terminal output:

IFCONFIG -A

ath0      Link encap:Ethernet  HWaddr 00:90:96:8B:06:37
          inet6 addr: fe80::290:96ff:fe8b:637/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:606 dropped:0 overruns:0 frame:606
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Memory:dfb11000-dfb21000

eth0      Link encap:Ethernet  HWaddr 00:08:0D:8D:76:F3
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1253557 (1.1 MiB)  TX bytes:1253557 (1.1 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


IWCONFIG

lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"actiontech"
          Mode:Managed  Frequency:2.462GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:1Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=11/94  Signal level=-84 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


ROUTE -N

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by alastair on 2005-02-24
Firstly, is "actiontech" the correct ESSID name for your wireless?

Do you know how your access point (ap) is setup? i.e.

 - broadcast ESSID?
 - WEP, key?
 - MAC address?

Do you have a DHCP server to give out IP addresses? 

I assume, at some point, you configured the ap?

---

### Post by transkinetic on 2005-02-24
I'm running windows on the same computer as we speak. Acording to it I'm connected to ACTIONTEC using the Atheros AR5001X+ Wireless Network Adapter.

I can't remember what I've done with the AP it was a while ago when I first set it up.

Going into it's setting I see:

DHCP server = on

WEP = 3333333333


ESSID = ACTIONTEC

I'm gonna try ubuntu with actiontec instead of actiontech, hopefully that's it.

Any suggestions?

thanks

---

### Post by transkinetic on 2005-02-24
I've got it working somewhat. The sticky seems to address my new problems. I am however, POSTING THIS FROM LINUX!

Thanks for all your help!

---

### Post by alastair on 2005-02-24
Great news!

What do you think it was then? "Sticky"?

---

