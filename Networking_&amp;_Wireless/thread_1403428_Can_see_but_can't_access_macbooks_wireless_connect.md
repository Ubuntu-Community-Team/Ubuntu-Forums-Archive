---
title: "Can see but can't access macbooks wireless connection"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by coupedeluxe on 2010-02-10
Hello 

I have installed 9.10 on my 701sd eeepc. I am trying to share my internet connection (ethernet cable) through my Macbooks wireless signel.

My 701 can see the signal in Network Connections but I can't seem to connect.

I have a Realtek RTL8187SE Wireless Lan. Through searching the net and this forum this card is supported and I checked  the 701 and it comes up with driver r8180 installed and that it was broadcasting.

A screen comes up with SSID, Mode, BSSID, Mac Address and MTU.

I'm not sure how to fill these boxes out, can someone please help me. 

I was having problems with the original linux OS it shipped with and thought this OS would work "out of the bag" like I kept reading.

It also won't play avi files which was one of the main reasons I switched...but that's another thread!

Thanks for your help.
Brendon

---

### Post by superprash2003 on 2010-02-10
are you trying to share it wirelessly to just one machine or multiple machines?

---

### Post by coupedeluxe on 2010-02-10
I am just trying to share the macbook connection with one computer (701sd). I have the macbook internet sharing set up correctly as I have done it the same way with other macs.

I have also tried to connect the ethernet cable straight into the 701. It comes up showing all the address's ie IP, Netmask,Gateway, DNS filled out etc but still won't let me get online.

I plug my cable straight back into the macbook and the internet is there.

Thanks
Brendon

---

### Post by coupedeluxe on 2010-02-10
When I run iwconfig I get

lo   no wireless ext...
eth0 no wireless......

wlan0  802.11b/g ESSID:"Brendon Fraser's MacBook"
Mode:Managed   Frequency=2.472 GHz   Access Point: Not-Associated
Bit Rate:54 Mb/s
Retry:on  RTS thr:off   Fragment thr:off
Power Management:off
Link Quality=0/100 Signal level=0 dBm Noise level-0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by coupedeluxe on 2010-02-10
I have checked in BIOS and the wlan controller was disabled.

I turned it on and tried to connect again.

I set up a new Network and my wireless icon in the task bar is showing some bars and when I activate the drop down box it shows a small computer with a wireless signal coming out of it. It also has the wireless bars near it.

I tried the internet through firefox but it still tells me I am not connected...

Please help!! ;)

---

### Post by coupedeluxe on 2010-02-12
I just tried Easypeasy on a usb stick and I still have the same problem.

I still can't connect through an ethernet cable either even though all the relevant info appears to be there.

What puzzles me is it seems like a connection is there but its not.

Can anyone please help me before I load WinXP on my little 701Sd eeepc....

---

### Post by superprash2003 on 2010-02-17
there are 2 things that are required for this
1) Enable internet connection sharing - [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
2) Setup ad hoc network - [http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html](http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html)

---

