---
title: "Wired ethernet not connecting [9.04]"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by iain_m on 2009-07-16
I would appreciate any help and advice with getting the wired internet connection working under Linux on a new laptop, the Novatech **"[Xplora E16]("http://www.novatech.co.uk/novatech/range.html?t=nb&c=home&r=E16")"**, AKA Clevo W76K.

**The problem is that under Ubuntu 9.04 (both live and installed, straight out of the box), when I plug in an ethernet cable to the laptop, the network icon in the taskbar rotates briefly, then promptly notifies me that the network connection is disconnected ("wired network: disconnected, you are now offline"). This happens repeatedly. It never successfully connects.**

Incidentally the exact same behaviour happens under Linux Mint 7 Live and Eeebuntu 3. With the Ubuntu 8.04.1 live CD, nothing happens at all when the ethernet cable is connected (i.e. the network icon doesn't move). **However, under Windows XP, once the supplied LAN drivers have been installed, the same network connection DOES work as expected.** This leads me to think it is a software problem.

To be clear: the ethernet cable connects to my BT Home Hub (router) which in turn plugs into the telephone socket. (It is not a cable internet connection so I can't plug the laptop directly into the wall socket.) The same cable, attached in the same way, works when plugged into my desktop Windows XP PC. **Significantly, the ethernet connection also worked when used with an Asus EeePC 1000 with Ubuntu 9.04 NBR installed - straight out of the box.** 

According to lspci, the ethernet adaptor of the laptop is a **Jmicron "JMC260 Pci Express Fast Ethernet (rev 02)".**

In the laptop BIOS there are no settings related to networking to adjust. There is an option to change the "installed O/S" (choices are Win XP, Vista IDE, Vista AHCI, Other) but changing this makes no difference.

I have also tried the following, with no effect on the issue:

Pressing the restart button on the router; pressing the 'reset to defaults' button on the router; unplugging the router from the mains power for 1min; using a different ethernet cable; connecting only the laptop (not the desktop) to the router; changing the Network connections > auto eth0 > edit > IPv4 settings > method from 'automatic (DHCP)' to 'automatic (addresses only); creating a new wired connection in Network connections and copying and pasting the MAC address from eth0 into this connection.

I am not familiar with what kinds of terminal commands would be helpful here but some googling led me to try the following:

"sudo ifconfig -a", which returns this:

```
eth0
	Link encap:Ethernet  HWaddr 00:90:f5:87:4a:e3  
	inet6 addr: fe80::290:f5ff:fe87:4ae3/64 Scope:Link
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:15 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000 
	RX bytes:900 (900.0 B)  TX bytes:0 (0.0 B)
	Interrupt:250 

lo
	Link encap:Local Loopback  
	inet addr:127.0.0.1  Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Host
	UP LOOPBACK RUNNING  MTU:16436  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0 
	RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0
	Link encap:Ethernet  HWaddr 6a:5e:5d:9e:dc:92  
	BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0 
	RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
	
"cat /etc/network/interfaces", which returns this:
```
auto lo
iface lo inet loopback
```

"sudo ifup eth0", which returns this:
```
Ignoring unknown interface eth0=eth0
```

"sudo ifodwn eth0", which returns this:
```
Interface eth0 not configured
```

Having googled these ifup and ifdown results, I found some other discussions of them but no clear fix. For example, this page [http://blog.sillar.net.au/?tag=interface-eth0-not-configured](http://blog.sillar.net.au/?tag=interface-eth0-not-configured) talks about manually setting "the IP address, subnet, gateway and DNS servers" - but how is one to know what values would be correct for these?

I also tried this fix for the Davicom ethernet adaptor, on the off-chance that it would help:
[http://ubuntuforums.org/showthread.php?t=186430](http://ubuntuforums.org/showthread.php?t=186430) (result: it didn't help…).

Lastly, I should say that I talked to Novatech support. Of course they didn't have much to say about how to configure Ubuntu (as expected) but they did say there weren't any known issues with running Ubuntu on the laptop. 

So, I am absolutely stumped! Any ideas please? **Thank you** in advance! :KS

---

### Post by agwblack on 2009-07-16
Just to say that I am having the same problem on 9.04 as well. The output of all the commands you have given are the same for me, but my ethernet card is given as "nVidia Corporation MCP73 Ethernet (rev a2)".

Any help would be much appreciated.

---

### Post by iain_m on 2009-07-16
Interesting -- what make and model of computer are you using?

Thanks for replying.

---

### Post by agwblack on 2009-07-16
The computer is an HP Pavillion Slimline.
Intel Core 2 Duo, 2.40Ghz

Really want to get this sorted. Its intensely frustrating having to do everything on my (rather old) laptop!

---

### Post by iain_m on 2009-07-18
Update - for reasons unrelated to this issue, I've actually ended up exchanging the laptop for another (of the same model) which I'm giving to someone else. 

At any rate, I did try the wired connection on the new laptop with the Ubuntu Live 9.04 CD but the problem was identical. 

So if it is a hardware issue it must be to do with the chipset rather than a flaw with the individual laptop.

---

### Post by ZhuaSD on 2009-07-20
Did you run pppoeconf?

What does plog give you?

---

### Post by iain_m on 2009-07-20
Unfortunately I no longer have the laptop but thank you for replying. 

agwblack, perhaps these suggestions might help you?

---

### Post by petegale on 2009-07-29
I am experiencing this exact same issue. Any advice would be most welcome.

Thanks

Pete

---

### Post by Iowan on 2009-07-29
Address via DHCP? Check [here]("http://ubuntuforums.org/showthread.php?t=1156441"). Might not fix it - but worth a try.

---

### Post by prak97 on 2009-08-07
Hi ...I had the exact same problem .... abit of reading and a guess fixed it :-)
Try typing in a terminal ....dhclient
Fixed it for me :-)

---

