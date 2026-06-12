---
title: "Broadcom 4238 a/b/g/n Ver 3"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by MonthOLDpickle on 2010-05-08
Now I have search, read many different forums, tried many things, and yet I am still having an issue. Using UNE 10.04.

Now this is what my wireless icon looks like (Even though I am connected to my home netowork):

It shows the WiFi icon with a red ! and just says Disconnect when you click on it under wireless. 

Here is iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"Fallout"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:26:5A:B5:D6:E9   
          Bit Rate=2 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr=2346 B   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-27 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:6  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```And here is ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:21:70:dc:87:74  
          inet6 addr: fe80::221:70ff:fedc:8774/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3628702 (3.6 MB)  TX bytes:500264 (500.2 KB)
          Interrupt:27 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:97:7c:de  
          inet addr:192.168.0.195  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe97:7cde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:840 errors:0 dropped:0 overruns:0 frame:9307
          TX packets:94 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45550 (45.5 KB)  TX bytes:16147 (16.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```

This is an N card and I do have an N network. I have it on WEP with AKES and TKIP (Memory for the terms).

---

### Post by pdc on 2010-05-08
so if you type

> lspci in a terminal you get this

> Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

bkratz suggests here in post #5

[http://ubuntuforums.org/showthread.php?p=9263484#post9263484](http://ubuntuforums.org/showthread.php?p=9263484#post9263484)

that you need the broadcom sta driver

...... described here ......


[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by MonthOLDpickle on 2010-05-09
Even with the STA driver (which I do have activated) I get 2mb/s rate? Faster when I connect to a G? Which the WiFi icon works correctly?



Also when I read that guid I don't see the 4328 mentioned, I see the 4322 - highest it goes.


But I guess hits just a problem with all of linux...was told draft n is broken.

---

### Post by bkratz on 2010-05-09
> **MonthOLDpickle said:**
> Even with the STA driver (which I do have activated) I get 2mb/s rate? Faster when I connect to a G? Which the WiFi icon works correctly?



Also when I read that guid I don't see the 4328 mentioned, I see the 4322 - highest it goes.


But I guess hits just a problem with all of linux...was told draft n is broken.

You are looking in the wrong column..  Look at the section
"
SUPPORTED DEVICES
-----------------
The cards with the following PCI Device IDs are supported with this driver.
Both Broadcom and and Dell product names are described.  Cards not listed here
may also work.

	   BRCM		    PCI		  PCI		  Dell
	  Product Name	  Vendor ID	Device ID	Product 


at the pci vendor and pci device ID columns, not the BRCM code! your's is there.

 4321 Dualband	       0x14e4	    0x4328  	   Dell 1505
 4321 Dualband	       0x14e4	    0x4328     	   Dell 1500
"

---

### Post by MonthOLDpickle on 2010-05-09
Going trough both links, each page searching for the word supported..FF doesn't even find that word.

Not to mention I do have the STA driver -enabled- but like the other person in the second link some posts down saying it really doesn't work for their 

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03).

And this has been what I been finding over the internet trying to fix the N part. I tether on my phone and I get a rate of 7mb/s than connect to my draft n and get a rate of 2 Oo

Tethering results in the WiFi icon actually looking connected and I can see what network I am connected to.

Connecting to an N network results in the WiFi Icon not showing a connect (has a red !) and not telling me what network its connected to, even though it is.

I am not trying to say your wrong but I have already tried the second link on my frist few attempts since its really just restating what the computer/OS should say when you click on Hardware drivers. I never seen the link but thats the typical solution everybody tries at first.

---

### Post by MonthOLDpickle on 2010-05-10
Okay, I downgraded back to 9.10. Thing shows actual WiFi connection and what network connection, and I went from rate of 2mb to 24mb...

Now thats a bit better for being on a N connection even though it should be faster, it may be - not that savy.

---

### Post by wkdown on 2010-05-10
I am also having a problem with my wireless. The wifi is enabled, and it finds the AP I am trying to connect to. The "wifi waves" in the status bar flash as it tries to connect. After about 60 seconds, I am prompted for the AP password. The password is correct, and I can connect from outside the Ubuntu machine; so the problem isn't the router.  I am working off a Dell Latitude D630. I have enabled the STA driver under **System > Administration > Hardware Drivers**

I have also changed my /etc/modules and blacklist, per [[COLOR="Blue"]this post[/COLOR]]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues"). The output from *lsmod | egrep 'Module|iwl|ipw'* is:
```
Module                  Size  Used by
iwl3945                79404  0 
iwlcore               124955  1 iwl3945
mac80211              238128  2 iwl3945,iwlcore
led_class               3732  2 iwl3945,iwlcore
cfg80211              148386  3 iwl3945,iwlcore,mac80211
```

lspci:
```
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

iwconfig:
```
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:171
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

ifconfig:
```
eth1      Link encap:Ethernet  HWaddr [redacted]  
          inet6 addr: [redacted]/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:62219
          TX packets:2 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:226 (226.0 B)  TX bytes:290 (290.0 B)
          Interrupt:17 Base address:0xc000 

```

Any further guidance would be awesome.

**EDIT:** Sorry, forgot this tidbit. It has worked in the past; namely after the STA driver being enabled. Now it is failing to connect. Someone mentioned toggling the "wifi switch" on the side of my machine, but this made no change.

---

### Post by wkdown on 2010-05-10
On a whim, I decided to remove the STA driver, restart my system, connect via hardline, re-install the driver, and try my wifi again.

...

It worked.

So try this solution to get a connection, but this not practical at all. There should be a permanent solution for this issue. Hopefully someone can post one!

**I spoke too soon. Although it said a connection was established, no sooner did I remove the hardline that the connection dropped. *sigh***

---

### Post by MonthOLDpickle on 2010-05-13
Best bet would to go back to 9.10. Its seems 10.04 breaks the 4328 even more.

---

### Post by johnrobert on 2010-05-13
I have one observation to add about the same problem. The only sure-fire method I've found for getting my wireless connection is to plug in my ethernet cable first. After I've connected to my home network via the ethernet cable, I can then unplug the cable, manually tell network manager to connect to my wireless router, and get a wireless connection with no fuss. But if I try to just let network-manager do the job itself, it's completely hit-or-miss, with an emphasis on lots of misses. I hate randomness.:(

---

### Post by tekrytor on 2010-07-24
I'm having similar issues on my HP tx2510 running KXstudio 10.4, the 64-bit version, also with the Broadcom 4328 wifi adapter and using the STA proprietary driver. 

The first time I enable the STA driver with Ethernet connection, the wifi then works. Reboot, it does not work. I found that if I then disable the STA driver, then enable it again, wifi works again. This is very consistent, every time behavior.

I have tried dozens of things to fix this, but nothing successfully reloads the STA driver on boot. I always have to reset it manually in the Hardware Drivers gui, disable and then enable it. I now assume I will spend the first 3 or 4 minutes after boot doing this, every time. 

Does anyone have a suggestion?

---

