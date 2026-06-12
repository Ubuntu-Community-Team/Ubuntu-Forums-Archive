---
title: "pernicious problem - wireless stuck at 1mb/s"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by simon@syd on 2009-07-30
Hi there,
I hope i am doing the right thing, I'm actually wanting to publish a solution to a problem which drove me CRAZY, to such an extent I thought I'd have to go back to windows. And, it is a problem that was subtle, it did not involve wireless not working - merely it was going very slowly. I fear that there may be many users out there who are thinking that ubuntu just connects to the internet slowly, and thats the end of the story.
 
The problem:
My internal wireless card in my EEEPC, which is an atheros card, was causing my interent experience to be slow. When right clicking the applet for the connection strength graph, and choosing "connection information" I would get - almost but not quite all the time - that the connection speed is 1mb/s. Sometimes it would be a different, better value, but hardly ever. 
 
I also had an old pc with a g standard USB wireless card - and this connection was much faster than my eee. Then I took to disabling the internal wireless, by enabling the 'madwifi' driver in the 'scan hardware' dialogue. On sticking the USB wireless into my eeepc, the connection would work flawlessly with the USB connection. NOTE - making the USB connection work was a purely plug and play experience: good on you, ubuntu.
 
I eventually found the answer on one forum, and i dont think i have seen it anywhere else on the net: [https://answers.launchpad.net/ubuntu/+source/wireless-tools/+question/30772](https://answers.launchpad.net/ubuntu/+source/wireless-tools/+question/30772) 
 
In case this link disapears, here's what the link says:
[INDENT]1 - go to /etc/rc.local as an administrator
2 - add this before the exit line: iwconfig wlan0 rate 54M
I would like to note that this forces the card into a 54M connection and if that channel is noisy it ignores it. This fixes the problem but can also make it worse depending on the number of 2.4ghz devices surrounding and inside of your home.
[/INDENT]I additionally, had to experiment with different values: this is what worked for me:
iwconfig wlan0 rate 24M
 
From then on, wireless worked fine.
 
Now, it would have been great if it had not taken me ages to find the solution - but it would be far far greater if a more elegent way of treating this issue was built into later iterations of Ubuntu - is this a good place to post this solution? Also, is it an issue with Ubuntu, or an issue with the particular applet that runs the wireless connection? (nm-applet) 
 
I'd just like the linux experience to be smoother... maybe a GUI for this issue?
 
I apologise in advance if this should be in another thread, or if it has been treated already - simon

---

### Post by Crafty Kisses on 2009-07-30
What are the results of the following?
```
lspci
lsusb
ifconfig
iwconfig
```

---

### Post by simon@syd on 2009-07-31
Hey, thanks for your interest - here is what i get in terminal when i put the commands in:

[INDENT][FONT=Courier New]lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
us@us-laptop:~$ lsusb
Bus 001 Device 003: ID 0951:1606 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:0035 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1c4f:0002  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
us@us-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:45:22:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23424 (23.4 KB)  TX bytes:23424 (23.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:b4:26:87  
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:feb4:2687/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3637764 (3.6 MB)  TX bytes:525581 (525.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-B4-26-87-36-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"us2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:70:B9:5E   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=90/100  Signal level:-42 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.





us@us-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"us2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:70:B9:5E   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=90/100  Signal level:-42 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.






us@us-laptop:~$ lsusb
Bus 001 Device 003: ID 0951:1606 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:0035 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1c4f:0002  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
us@us-laptop:~$ 

[/FONT]

[/INDENT]Simon
BTW I am running eeeebuntu - I trust that makes no difference (and i noted the same problem in vanilla ubuntu)

---

### Post by simon@syd on 2009-08-12
(just continuing this discussion with myself)
 
I ended up accidentally installing OpenSuse, with gnome (I found myuself wanting to reinstal, but I had no ubuntu instal disk but i did have an 11.2 OpenSuse disk...)
 
The interesting thing is that it has the same network manager as ubuntu, and when i checked out the connection speed it said 54mb... and then when the connection wasnt so good it said 48mb... and wireless downloads are faster than they were in Ubuntu.
 
Just so it is documented somewhere... I tried ubutnu 9.04, eeebuntu (9.04), Linux Mint (9.04) and i had the problem and workaround as outlined above. When I installed gnome on OpenSuse the problem dissapeared.
 
I hope someone does fix this down the line as I like Ubuntu: I like the way you get a 6 month development cycle - its something to look forward to,  I like the way it is so easy to instal, I like the apps, and I ike the style of it.

---

### Post by a94060 on 2009-08-12
Thank you so much. I had this problem and never knew how to speed it up and basically trashed it. Thanks for giving me hope and a soulution:popcorn:

---

### Post by baditaflorin on 2012-05-03
For it stayed most of the time at 1 mb/s and i changed to 54 mb but then i had a lot of disconnect, and still slow. 
Now i put it on 11 mb and is more acceptable, but still slow. 

I changed the MTU to 2700 and at least for now, 20 minutes, it`s working more better

LATER EDIT : Disable n mode on rooter and you may see the problem solved, at least for my intel wireless card it worked

---

