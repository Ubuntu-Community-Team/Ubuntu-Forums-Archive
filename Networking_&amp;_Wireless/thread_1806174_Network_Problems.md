---
title: "Network Problems"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by Phil Binner on 2011-07-17
Hi

I have a complex network. ADSL broadband comes into the house and connects to an Orange Livebox. An Ethernet cable then connects the Livebox to a more powerful router, a DrayTek Vigor 2710Vn. The reason for this is that the Livebox has a second line capability using Voip, but it is not powerful enough to get around my stone house. The DrayTek router has Voip capability, but as yet Orange will not connect the Voip line to it. 

I connect to this system with Ubuntu. Android, Windows and I-phone. I can connect to either of the routers, though I usually use the DrayTek.

Voip on the Livebox does not require a computer to run it, you just plug a normal phone into it and use it to get free calls. I actually take this line into a Panasonic telephone switch to give me a 2 line system around the house.

The problem with this set-up is that after a short time something happens to the network which prevents Ubuntu computers connecting to it. Windows machines, I-phones and Android phones connect, but Ubuntu does not.  If I re-boot the Livebox, or in an extreme case take it back to it's factory settings, the Ubuntu machines can connect again, but it's only temporary.

The fact that fixing Livebox sorts the problem definitely points to Ubuntu being innocent, but at the moment I can't do without the Livebox. That means, for the moment, having to stay with Windows.

If I post the output log after a failed connection attempt, all it would show is the connection timing out. Why is Ubuntu so sensitive to network problems that are not of it's making. Is there anything I can do about it other than changing my ISP. I am considering that, but other factors make that difficult.

Help please.

Phil

---

### Post by jmoorse on 2011-07-17
Phil, definitely sounds like an issue with the Livebox that Ubuntu is exasperating.  Let's try and figure out what that is!  It almost sounds like some odd DHCP lease loss of vendor IPv6 implementation issue.

1. Are the connections to the draytek wired or wireless?
2. Does the draytek do DHCP/NAT or is it just a switch / wap?
3. What version of Windows? 
4. Can you try disabling IPv6 on one ubuntu box to see if anything changes? ([http://ubuntuforums.org/showthread.php?t=1778105](http://ubuntuforums.org/showthread.php?t=1778105))
5. Would it be possible for you to run a few commands when Ubuntu loses connectivity?  

eg: ifconfig, traceroute 8.8.8.8, dig [www.google.com](www.google.com), dig [www.google.com](www.google.com) @8.8.8.8 and maybe even firing up wireshark to watch the traffic and see if anything sticks out.

---

### Post by Phil Binner on 2011-07-17
1. Connections can be wired or wireless. I've tried both, it makes no difference.
2. I'm sorry, I don't understand this. I'll try to do some research tomorrow, or if you could simplify the question it may help.
3. All versions of windows are now windows 7. It didn't have any problem with XP before I converted that machine.
4. I'll try disabling IPv6. I don't know how to do that, but it sounds like the kind of thing I could find out. I did have an IPv6 problem with Windows 7 about a year ago (not a similar problem - an issue with zone alarm) and I'm very suspicious of this. Too big and too new at the moment. The experiment I carried out today, however, was to reload Ubuntu 8.10 on an old machine to see how that got on. The symptoms were identical.
5. It's too late to run those commands at the moment. Currently I'm on a windows machine, but tomorrow I'll try to re-connect on the Ubuntu machine and do that.

Thanks. Be talking to you.

---

### Post by Phil Binner on 2011-07-19
First, sorry about the delay. I re-booted the livebox to use this machine to view the forum, then I had to wait for it to fail again to run the commands. I then found that I didn't have Traceroute or Wireshark installed, so I had to reboot again to get them. What I have is here. I'll run Traceroot again when the connection next fails. I had a look at Wireshark, however, and I don't know what you want me to do there. More specific instructions, aimed at someone with little technical nouse, would be helpfull.

Second, I don't know how to put the output from commands into boxes, as others seem to do. That may make it more difficult to read.

OK.

DrayTek is a sophisticated router. Under NAT it has pages for for "Port Redirection", "DMZ Host", and "Open Ports". It's DHCP server IP address is 192.168.1.1, which is the address of Livebox on the network.

Livebox is also capable of having DHCP and NAT. I would not call it a sophisticated router (usually I call it a p*** of s****) but it is more than a switch.

I just discovered that I was wrong about my android phone and my son's I-phone. Neither of them will connect now when the Livebox is misbehaving. That must have been an earlier problem. Windows does connect fine, however.

Under networking, under “Connection Information” , it says that Ipv6 is ignored. This is for the Ubuntu laptop and the Ubuntu Desktop. The Ipv6 tab for each connection shows the method as “Ignore”.  Is this the same as disabling it.

The following output, as requested, was produced while the connection was down.

bigbin@Middlebin-Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:6a:4a:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1144 (1.1 KB)  TX bytes:1144 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:37:4d:1b  
          inet6 addr: fe80::21e:4cff:fe37:4d1b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1567 (1.5 KB)  TX bytes:7444 (7.4 KB)

bigbin@Middlebin-Ubuntu:~$ dig [www.google.com](www.google.com)

; <<>> DiG 9.7.3 <<>> [www.google.com](www.google.com)
;; global options: +cmd
;; connection timed out; no servers could be reached

bigbin@Middlebin-Ubuntu:~$ dig [www.google.com](www.google.com) @8.8.8.8

; <<>> DiG 9.7.3 <<>> [www.google.com](www.google.com) @8.8.8.8
;; global options: +cmd
;; connection timed out; no servers could be reached[/HTML]

I had to reset livebox to install Traceroute and Wireshark, so the following output occurred when the connection was working.

traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  WANConnectionDevice.home (192.168.1.1)  0.935 ms  0.925 ms  1.006 ms
 2  217.47.130.186 (217.47.130.186)  28.957 ms  30.554 ms  34.966 ms
 3  217.47.130.193 (217.47.130.193)  34.703 ms  36.342 ms  38.240 ms
 4  213.1.67.26 (213.1.67.26)  44.476 ms  46.111 ms  47.968 ms
 5  213.1.79.30 (213.1.79.30)  50.174 ms  51.799 ms  54.077 ms
 6  87.237.20.244 (87.237.20.244)  55.717 ms  32.586 ms  33.141 ms
 7  bundle-ether1.lontr1.London.opentransit.net (193.251.255.101)  38.459 ms  38.622 ms  86.091 ms
 8  google-16.GW.opentransit.net (193.251.254.182)  40.314 ms  41.908 ms  44.156 ms
 9  66.249.94.76 (66.249.94.76)  46.557 ms  48.170 ms 66.249.94.78 (66.249.94.78)  52.964 ms
10  209.85.253.92 (209.85.253.92)  53.117 ms 209.85.253.94 (209.85.253.94)  53.886 ms 209.85.253.88 (209.85.253.88)  55.485 ms
11  66.249.95.173 (66.249.95.173)  67.054 ms  68.837 ms  70.225 ms
12  209.85.251.231 (209.85.251.231)  43.601 ms  42.146 ms  64.789 ms
13  209.85.243.73 (209.85.243.73)  51.402 ms 209.85.243.85 (209.85.243.85)  47.264 ms 209.85.243.73 (209.85.243.73)  51.524 ms
14  google-public-dns-a.google.com (8.8.8.8)  50.919 ms  52.358 ms  53.783 ms

Regards
Phil B

---

### Post by jmoorse on 2011-07-19
In the output above your machine does not have a DHCP lease (IP address), this leads me to suspect the Draytek. 

Though that doesn't explain why rebooting the livebox would give you a DHCP address.  Do you reboot both the livebox and the draytek when you do this?

Can you try assigning a static IP to one of your boxes?  Something like this:
```

IP: 192.168.1.234
Subnet mask: 255.255.255.0
Gateway: 192.168.1.1
DNS: 192.168.1.1

```
Like this (but with your own IPs): [http://www.liberiangeek.net/2011/03/configure-permanent-static-ip-addresses-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/03/configure-permanent-static-ip-addresses-ubuntu-11-04-natty-narwhal/)

Then see if the machine with the static IP stops working at the same time as the other devices?

---

### Post by Phil Binner on 2011-07-20
Hi Jeff

Contact was lost again this morning, so I ran the code. This is the output.


bigbin@Middlebin-Ubuntu:~$ traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
connect: Network is unreachable

Not too usefull I guess.

I'll follow the instructions and set up the desktop with a static IP address, they wait for the laptop to loose connection again and see.

One more thing, when I can't get Draytek I can't get wireless to Livebox either. If things go seriously wrong I use a windows 7 netbook to get a wireless connection to livebox, then take it back to factory settings.

Regards
Phil B

---

### Post by Phil Binner on 2011-07-20
Unfortunately not so simple.

When I put in all the information the save button is not highlighted. 

The connection I was editing was Auto eth0. In the IPv4 page it seems to want a search domain and a route, as well as the information you provided. I entered 192.168.1.1 as teh search domain, and when I clicked "routes" it provided a box very similar to the address box I just completed, except that it includes a field for "Metric". Metric is not an IP address (it can't contain dots), and I can't save without it.

One more thing, when I try to enter teh netmask in the IPv4 address line it offers a prefix of 24. If I type over this it goes in normally. If i type after it it brings up a separate box for teh entry, and after I save that it disappears, leaving only 24 as the subnet mask. Which ever way i complete this the save button remains greyed out.

On my network 192.168.1.1 is Livebox, and 192.168.1.101 is draytek. The wired connection I was editing is to DrayTek.

Regards
Phil B

---

### Post by jmoorse on 2011-07-20
Phil, you can follow this video almost exactly.  Except instead of setting the IP on wireless you are going to set it on 'Auto eth0'

[http://www.youtube.com/watch?v=2_ifSRJhtQU](http://www.youtube.com/watch?v=2_ifSRJhtQU)

---

### Post by jmoorse on 2011-07-21
Wow, didn't expect to see a Windows user trolling the Ubuntu forums.  Way to go champ!

[http://tomayko.com/writings/that-dilbert-cartoon](http://tomayko.com/writings/that-dilbert-cartoon)

---

### Post by Phil Binner on 2011-07-21
Hi again,

Thanks for that, both, but the same response in both cases.

Windows 7 may be a great operating system, but it imposes certain strictures, in the same way that being mugged every time you leave your front door would impose strictures. That's why I'm trying to leave it. So thanks Josef, but no thanks.

As to the video, unfortunately the first part demonstrates exactly what I did. In my case it can't be done because NM is not allowing me to update the connection when I select manual in the method for IPv4. As soon as I do this the Save button get's greyed out. In the case of the wireless connection on the laptop the whole IPv4 screen was greyed out.

I've been thinking about this overnight, and I suspect this can only be because either DrayTek or Livebox are not set to allow static IP addresses. What should I look for in the homepage of each to rectify this.

Thanks again, Phil B

---

### Post by jmoorse on 2011-07-21
> **Phil Binner said:**
> 
I've been thinking about this overnight, and I suspect this can only be because either DrayTek or Livebox are not set to allow static IP addresses.

No, your network devices have no bearing on IP assignment on your machine.  

To be frank, I think you are mistyping one of the fields which is not allowing you to save it.  That's absolutely fine please don't take it personally.  I will post an exact series of steps.

1. Click on the network Icon up near the clock
2. Click "Edit Connections"
3. Highlight your wired connection, likely "Auto eth0"
4. Click "Edit"
5. Select the IPv4 Settings Tab
6. From the Method dropdown Select "Manual"
7. Click the "Add" button
8. In address type 192.168.1.234
9. LEAVE the netmask at "24", no quotes
10. Put 192.168.1.1 in "Gateway"
11. In DNS servers put "192.168.1.1", no spaces or quotes <-- If this is wrong it will grey out Save
12. Click "Save".  You may have to provide your user password here.  Provide it if needed 
13. Click close.

Open up a terminal window.  Run:

```

ifconfig -a
ping 8.8.8.8
traceroute www.google.com

```

Please post the results here.

---

### Post by Phil Binner on 2011-07-22
Nailed the b****r.

As soon as I saved the connection connection was established. ifconfig looked OK, but ping 8.8.8.8 started sending packets and is still going, at least 10 minutes later. What should iI do to stop it, or if I don't how long is it likely to go on.

Now I have a static IP address on the network, do they all have to be static. i.e. while I still have Windows machines (I'll wash my mouth with soap and water later) will they need static addresses to avoid conflict. If so I may need Josef to instruct me.

As an asside, as long as you're helping I won't take offense easily, but I didn't actually mistype anything. It was the 24 in netmask. From your first instructions I assumed netmask and subnet mask were the same, so I tried to enter 255.255.255.0. The video actualy shows that being done.

While editing the connection the save button gets greyed out when manual is connected, and comes back when a correct line is entered. Since I was trying to enter 255.255.255.0 it never came back.

Ping is still pinging. I think I'll have to close the terminal.

Thanks

Phil B

---

### Post by Phil Binner on 2011-07-22
OK I closed the terminal and tried a more pragmatic test. Firefox can see google so all seems to be well. I also intalled updates, so it's downloading OK.

One more question. Does a static IP address go with the machine or the connection. I.e. when I'm setting up both wired and wireless connections on the same machine do they have the same static IP address.

Thanks

Phil B

---

### Post by jmoorse on 2011-07-23
It binds to the adapter in the OS you are running.  If you setup both adapters they should have different IPs and can be a mix of DHCP/static.  Does that make sense? In fact if wifi works fine, don't change it :)

---

### Post by Phil Binner on 2011-07-23
Your fix about static IPs worked fine, on both wired and wireless. Neither worked before, both work now. I'll change them all now I know to make them relevant to the connection rather than the machine.

The only thing I still need to know is whether I need to do anything to the windows machines now I have static IPs on the network. I'm fairly sure the answer to that is no, however, so I'll mark this as solved now. 

Thanks for all your help. I'm getting to feel that this time my Ubuntu experiment will be successful.

---

