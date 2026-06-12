---
title: "Network connection really slow"
date: 2006-01-24
forum: Networking &amp; Wireless
---

### Post by dazednconfused on 2006-01-24
I've just installed Breezy on an old 300Mhz Celeron with 196MB RAM.

Everything is working except the network connection is really slow - web pages can take several minutes to load!

I've disabled IPV6

Follwing the 'Wired Ethernet Troubleshooting Process' gives the following:

mii-tool - SIOCGMIIPHY on 'eth0' failed: Operation not supported

ifconfig eth0

Link encap:Ethernet HWAddr 00:E0:7D:72:26:F6
inet address:192.168.123.145 Bcast:192.168.123.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:342 errors:0 dropped:0 overruns:0 frame:0
TX packets:329 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:175737 (171.6 KiB)  TX bytes:34341 (33.5 KiB)
Interrupt:9 Base adddress:0xdd80

lspci

0000:00:oa.o Ethernet controller: Realtek Semiconductor Co., Ltd RTL-8029(AS)

lsmod returns nothing!

I can ping my router:

6 packets transmitted, 6 received, 0% packet loss, time 9075ms
rtt min/avg/max/mdev = 0.724/0.737/0.754/0.036 ms

And I can reach the internet by number and name:

4 packets transmitted, 4 received, 0% packet loss, time 10829ms
rtt min/avg/max/mdev = 291.037/291.727/292.586/0.771 ms

Can anyone suggest what I should check next?

---

### Post by stream303 on 2006-01-24
[QUOTE=dazednconfused]I've just installed Breezy on an old 300Mhz Celeron with 196MB RAM.

Everything is working except the network connection is really slow - web pages can take several minutes to load!
[/QUOTE]

I'd check your **/etc/resolv.conf** file, and see what your nameserver is.

It's possible that the slow dns queries might be due to your system not specifying the actual nameservers of your isp.

We can change that, but lets see what /etc/resolv.conf shows first....

---

### Post by dazednconfused on 2006-01-25
One of the dns in resolv.conf was wrong.

I've changed it to match my windows boxes, i.e 80.225.249.178 and 192.168.123.254 and made sure its set as read only.

Unfortunately this hasn't cured the problem which I didn't explain very well :-)

While pages are loading - which takes several minutes, the computer becomes unresponsive, the mouse won't move etc. System monitor reports 100% CPU, 57% user memory, and 3.7% swap usage. 

Once a page has loaded CPU usage drops to 16%. The smallest amount of network traffic causes 100% CPU usage.

The CPU is an old 300Mhz Celeron, but even so it should have enough proceesing power, shouldn't it?

---

### Post by stream303 on 2006-01-25
> One of the dns in resolv.conf was wrong.

I've changed it to match my windows boxes, i.e 80.225.249.178 and 192.168.123.254 and made sure its set as read only.

Unfortunately this hasn't cured the problem which I didn't explain very well :-)


Oops.  Setting /etc/resolv.conf to read-only won't work as it will be **rewritten** upon every new lease or reboot.

Since you know your isp's nameservers, try this:

edit **/etc/dhcp3/dhclient.conf**
(sudo gedit /etc/dhcp3/dhclient.conf)

Just before the "request" line, add this  (using your isp's real dns addresses):
**prepend domain-name-servers 123.45.678.90, 123.45.678.91;**

If you have multiple addresses, just separate with a comma and don't forget the semicolon at the end.

Now to make the changes work, you can bring your ethernet interface down and up again from the terminal:

sudo ifdown eth0
sudo ifup eth0

Should be good to go!

---

### Post by dazednconfused on 2006-01-27
OK, done that - no difference!

From the 'transferring data from www.***.***' message coming up in Firefox it takes upto 3 minutes to display the page.

Watching the lights on my router, the computer appears to grab some data wait 10/15 seconds then grab somemore until the page has loaded. My windows machine grab the same page in seconds so its not a router or connection problem!

---

