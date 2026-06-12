---
title: "Is Ubuntu 10.04 continue support wireless?"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by ario on 2010-09-30
In this topic I successfuly installed and used the driver for my D-link DWA-125 wireless dangle. There are some fundamental tips in doing this. Now I'm able to connect with WEP or None secured modes. But yet can not connect with it trough WAP2 encryption mode. I think the problem is yet with the driver I compiled and installed. If you know a solution I will be glad to now about.
Thanks.
------------------------------------------------------
I have 2 computers both with Windows 7 and Ubuntu 10.04 in dual boot.
I have 2 wireless adapters.
I can not connect my computers wireless and I think this is because of linux as I described below. But the question is:
Is Ubuntu 10.04 continue support wireless? Or I must try another Distro./OS (like fedora, suse, windows, bsd and etc.)?

When boot computers in windows 7
[INDENT]Both can detect and install their wireless adapters automatically, and thus create an Ad-Hoc connection with wpa2 and connect them together without any problem. The only problem is that it is Bill Gates Windows!
[/INDENT]
When Booting both in Linux:
[INDENT]Computer A with DWA-125 wireless can not scan any wireless access point, but the other computer with another wireless adapter can scan two or more wireless points around me! In spite of the fact that Windows on computer A can detect these access points either, **Driver of DWA-125 on Ubuntu 10.04 is buggy and not working.**[/INDENT]

Booting Computer A with DWA-125 adapter in Ubuntu and the other in Windows 7:
[INDENT]Created an ad-hoc connection in windows 7 and the other computer with DWA-125 adapter and Ubuntu 10.04 cannot find any wireless life on the earth![/INDENT]

Booting Computer A with DWA-125 adapter in Windows 7 and the other in Ubuntu:
[INDENT]This time created an ad-hoc connection in windows 7 and tried to scan it trough the other computer via Ubuntu 10.04. It find the connection, but cannot authenticate. Searched about 3 hours trough Internet and were too ANGRY! Completely removed all "network-manager" named packages via synaptic with all their settings. Completely removed WICD 1.7.0 and all its configuration files (Even the one in /var/lib/wicd/configuration !!!). Installed WICD 1.6.2 (Downgraded). It can now authenticate but cannot obtain IP Address! Searched [www.wicd.net](www.wicd.net) forum and yet another unsolved BUG![/INDENT]

So that problems are all on Linux!
[LIST]
[*]They can not without any Windows connect to each other either!
[*]The built-in driver and configuration for DWA-125 in 10.04 is not working, despite iwconfig shows a wlan0 and dmesg shows that device is detected with no errors.
[*] network-manager and WICD set of packages have several errors. from their source codes to their behaviors in software manager system. Their conflict with each other but synaptic don't say it!
[/LIST]

I need wireless guys. And I cant wait. Please tell me if I have to change to another OS.
Any response will be appreciated.

---

### Post by psycho5 on 2010-09-30
Is your ubnuntu updated? Plug in a LAN cable and update it then try the wireless again. Perhaps you've done all this but who knows. I always try updates before doing anything else.

---

### Post by an0dos on 2010-09-30
Here is a forum thread about getting the wireless card working under 9.10:

[http://ubuntuforums.org/showthread.php?t=1289917](http://ubuntuforums.org/showthread.php?t=1289917)

---

### Post by chili555 on 2010-09-30
Does Ubuntu 10.04 support wireless? Yes.

But that wasn't really your question, was it? You may have had better luck had your question been, 'Help me debug my DWA-125.' There are a few things that can be done to help, especially blacklisting conflicting drivers as mentioned in the link. If you can post:```
lsmod | grep rt2
dmesg | grep rt2
```We'll be glad to assist you.> Or I must try another Distro./OS (like fedora, suse, windows, bsd and etc.)?
The drivers in any Linux distribution are largely identical. I wouldn't expect that a switch to Fedora or Suse would significantly improve the DWA-125 driver.

---

### Post by ario on 2010-10-02
> **chili555 said:**
> Does Ubuntu 10.04 support wireless? Yes.

But that wasn't really your question, was it? You may have had better luck had your question been, 'Help me debug my DWA-125.' There are a few things that can be done to help, especially blacklisting conflicting drivers as mentioned in the link. If you can post:```
lsmod | grep rt2
dmesg | grep rt2
```We'll be glad to assist you.The drivers in any Linux distribution are largely identical. I wouldn't expect that a switch to Fedora or Suse would significantly improve the DWA-125 driver.

First of all thanks for your all responses guys.
Second: It's not only with the driver! As I mentioned above, one of my PCs have DWA-125. I brought it up with windows 7 and it detected the wireless and created an Ad-Hoc connection waiting for the other pc.
The other pc with Ubuntu 10.04 detected it's own wireless, but the other problem is with authenticating into an encoded wireless connection. I solved this one and then faced the other problem: Could not obtain IP address! Even by setting static IPs in WICD faced Could not... Could not something else problem!

Third: I black listed 2800 and 2700 modules so that the result of two above commands are nothing!
```
ario@ario-desktop:~$ lsmod | grep rt2
ario@ario-desktop:~$ dmesg | grep rt2
ario@ario-desktop:~$

```
I must add that after black listing those modules, now my wireless has no driver installed and it doesn't work when I connect it to the usb port.
It's not a problem, I can repeat this process as many turns as I want with a virtual Ubuntu server 10.04 installed in virtual box.
Please let me know if you have any solution for these problems:
[LIST]
[*]Driver for DWA-125 really working in 10.04!
[*]Encryption and IP address and other things in default network-manager-gnome package (I don't want to use WICD anymore!)
[/LIST]
Best regards:)

---

### Post by ario on 2010-10-02
> **an0dos said:**
> Here is a forum thread about getting the wireless card working under 9.10:

[http://ubuntuforums.org/showthread.php?t=1289917](http://ubuntuforums.org/showthread.php?t=1289917)

Thanks for your response, but it is all about 9.10 and I'm using 10.04 and in action it different from that you mentioned!

---

### Post by ario on 2010-10-02
> **psycho5 said:**
> Is your ubnuntu updated? Plug in a LAN cable and update it then try the wireless again. Perhaps you've done all this but who knows. I always try updates before doing anything else.

Yes it is updated until um... a month ago! Should I update it more or wait for the 10.10.10?

---

### Post by chili555 on 2010-10-02
I'm not at all clear about what you blacklisted. The link suggests you blacklist:```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```May I see your blacklist.conf file?

---

### Post by ario on 2010-10-02
> **chili555 said:**
> I'm not at all clear about what you blacklisted. The link suggests you blacklist:```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```May I see your blacklist.conf file?

First of all, I have done a sin installing a windows driver using ndiswrapper! Now whenever I connect my wireless to the usb port it will not blink any more, but it used to before ndiswrapper doing nasty things with my system!:D
When I bring up a virtual windows xp machine it will do something magic with the adapter and turn it's led on again but after powering of the virtual machine it will turn of again. removing ndiswrapper driver did not change it.
Now I added those lines you mentioned in a new Ubuntu Server Edition virtual machine's /etc/modeprobe.d/blacklist.conf file.
The result is that there is no wlan0 in report of iwconfig command any more:
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
Before blacklisting those things, it used to be! Now the problem is that system black listed those things but have no other drivers to use either.
Now what?
Thanks again:)

---

### Post by chili555 on 2010-10-02
Let's go back to the beginning. Please plug in the device and post:```
lsusb
```We'll use that information to learn the best driver for your device.

Have you removed ndiswrapper or disabled it in some way? Let's not have two drivers fighting each other.

---

### Post by ario on 2010-10-03
> **chili555 said:**
> Let's go back to the beginning. Please plug in the device and post:```
lsusb
```We'll use that information to learn the best driver for your device.

Have you removed ndiswrapper or disabled it in some way? Let's not have two drivers fighting each other.

Ok. I ran the command you mentioned and that was it:
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3c0d D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
Since it's a long time I have this problem (I decided to get rid of this adapter many times!), I read other forums and did these steps:
Downloaded rt3070sta driver from Ralink site and to compile and after installing it (Although it must be 7th or 8th time I'm doing these steps) just faced the famous error after modprobe command:
```
Unknown symbol in module, or unknown parameter (see dmesg)
```
And I do not know what to do. Changing a bunch of parameters and making a thousand of symbolic link just didn't changed anything.

**>>>Here what I did:**
Created an Ubuntu Server Edition 10.04 Virtual Machine Using Virtual Box 3.1.8r61349
Extracted driver into root home directory in a folder named 'a'
Installed linux-headers-2.6.32-21-generic, gcc, build-essential
in source code folder ran
```
make
```
Poswered off the virtual machine
**>>>Took a snapshot of the whole virtual system<<<**
Powered on the virtual machine
ran:
```
	nano /etc/modprobe.d/blacklist.conf

```added these lines to the file:
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

```Proofread, saved with Ctrl+O and quit with Ctrl+X.
ran:
```
sudo su
cd /root/a
cp RT2870STA.dat RT3070STA.dat
make install
reboot

```make and make install commands had no errors, just a little warnings in make command. After the reboot, inserted device, and activated it in the virtual machine and ran:
```
dmesg
[   32.334724] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   32.583412] usb 1-1: configuration #1 chosen from 1 choice
[   32.611946] rt3070sta: module license 'unspecified' taints kernel.
[   32.614938] Disabling lock debugging due to kernel taint
[   32.617094] rt3070sta: Unknown symbol usb_alloc_urb
[   32.617215] rt3070sta: Unknown symbol usb_free_urb
[   32.617547] rt3070sta: Unknown symbol usb_register_driver
[   32.617805] rt3070sta: Unknown symbol usb_put_dev
[   32.617894] rt3070sta: Unknown symbol usb_get_dev
[   32.618073] rt3070sta: Unknown symbol usb_submit_urb
[   32.618492] rt3070sta: Unknown symbol usb_control_msg
[   32.618976] rt3070sta: Unknown symbol usb_deregister
[   32.619398] rt3070sta: Unknown symbol usb_kill_urb
[   32.619483] rt3070sta: Unknown symbol usb_buffer_free
[   32.619884] rt3070sta: Unknown symbol usb_buffer_alloc

```

ran:
```
modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/rt3070sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
dmesg | grep -e rt2 -ert3
[   32.611946] rt3070sta: module license 'unspecified' taints kernel.
[   32.617094] rt3070sta: Unknown symbol usb_alloc_urb
[   32.617215] rt3070sta: Unknown symbol usb_free_urb
[   32.617547] rt3070sta: Unknown symbol usb_register_driver
[   32.617805] rt3070sta: Unknown symbol usb_put_dev
[   32.617894] rt3070sta: Unknown symbol usb_get_dev
[   32.618073] rt3070sta: Unknown symbol usb_submit_urb
[   32.618492] rt3070sta: Unknown symbol usb_control_msg
[   32.618976] rt3070sta: Unknown symbol usb_deregister
[   32.619398] rt3070sta: Unknown symbol usb_kill_urb
[   32.619483] rt3070sta: Unknown symbol usb_buffer_free
[   32.619884] rt3070sta: Unknown symbol usb_buffer_alloc
[  583.167972] rt3070sta: Unknown symbol usb_alloc_urb
[  583.171927] rt3070sta: Unknown symbol usb_free_urb
[  583.174460] rt3070sta: Unknown symbol usb_register_driver
[  583.174768] rt3070sta: Unknown symbol usb_put_dev
[  583.174889] rt3070sta: Unknown symbol usb_get_dev
[  583.175130] rt3070sta: Unknown symbol usb_submit_urb
[  583.177317] rt3070sta: Unknown symbol usb_control_msg
[  583.177706] rt3070sta: Unknown symbol usb_deregister
[  583.178251] rt3070sta: Unknown symbol usb_kill_urb
[  583.178378] rt3070sta: Unknown symbol usb_buffer_free
[  583.178847] rt3070sta: Unknown symbol usb_buffer_alloc

```

That was all!
Any Idea?

----------------------------
After all, why we the poor users of The Penguin must run a bunch of commands and post in a bunch of forums (Or just in one:D) to sort a paid and bought hardware to work and instead, Those windows freaks just sit on a couch and enjoy playing EA Games? Why?:D

---

### Post by ario on 2010-10-03
Let me guess, I can remember I compiled, installed and used this wireless adapter about 6 month ago on 9.04.
It must be a problem with the driver source code, which can not include a bunch of USB related kernel headers accurately. So after modprobe, system prompts that It can not understand a bunch of functions like:
```
usb_allocate
usb_register_driver
usb_something_here
usb_something_there
usb_etc...
```
Maybe I must change a part of code, to make it adapted with the new kernel?

Now as I seen in this page:
	[http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved.html](http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved.html)
in source code directory ran:
```
nano os/linux/usb_main_dev.c
```
added this line:
```
MODULE_LICENSE("GPL");
```
right after this line:
```
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
```
Didn't need to add my usb Id in the file named common/rtusb_dev_id.c in source code directory, because it was originally there.
ran:
```
[B]make clean
make uninstall
make
make install
modprobe rt3070sta
dmesg[/B]
[ 3477.269245] === pAd = f3066000, size = 508988 ===
[ 3477.269481] 
[ 3477.271150] <-- RTMPAllocAdapterBlock, Status=0
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA
**I love you penguin!**
I: command not found
**ifconfig ra0 up**
SIOCSIFFLAGS: Operation not permitted
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
          

```

No LED Blinking. Now what? Ok, Figured out that one myself! This was because of misconfiguration of this hardware in my Host Ubuntu Desktop 10.04. I again compiled the ralink driver following installation above this time on my Host operating system. after installation modprobe return no message but dmesg returned that it cannot read the file in /etc/Wireless/RT2870STA/RT2870STA.dat
I ran:
```

mkdir /etc/Wireless/RT2870STA
cp /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat

```
reinserted device and now in Host system device is working (I mean just blinking:D).
Now the other purpose of this post, How to get two computers with Ubuntu 10.04 connected trough a safe encrypted wireless connection?
Any helps appreciated guys:)

---

### Post by ario on 2010-10-03
Created an Ad-Hoc connection in computer A (The one with Ralink rt3070sta chip).
Connected to it trough a hidden connection option in default network-manager in gnome.
Other computer is a laptop with Ubuntu 10.04. Scanned wireless networks and found my network with WICD v.1.6.2 (I downgraded it because of encryption issues with 1.7.0 version of WICD). It says that my ad-hoc network is Unsecured! Why?

I tried to connect to my network in dynamic IP mode. Error:
Could not obtain IP address!

I tried to connect to my network in static IP mode. Error:
Connection faild: Could not connect the wireless access point!

Uninstalled WICD completely and reinstalled network-manager and it's gangs:
```
network-manager_0.8-0ubuntu3_i386.deb
network-manager-gnome_0.8-0ubuntu3_i386.deb
network-manager-pptp_0.8-0ubuntu3_i386.deb
network-manager-pptp-gnome_0.8-0ubuntu3_i386.deb

```
It is now connect only when I entered my password, which means connection is secured!
But iwconfig in two computers return two different cell IDs! Which is not good.
Any Idea?
Thanks for your helps:)

---

### Post by chili555 on 2010-10-03
So, it seems that the computer with the rt3070 chipset is working?

When you are connected, please run and post:```
iwconfig
ifconfig
```From the computer with the rt3070 chipset, please.

So is your question really about setting up an ad-hoc connection or about getting wireless to work?

---

### Post by ario on 2010-10-03
> **chili555 said:**
> So, it seems that the computer with the rt3070 chipset is working?

When you are connected, please run and post:```
iwconfig
ifconfig
```From the computer with the rt3070 chipset, please.

So is your question really about setting up an ad-hoc connection or about getting wireless to work?

Chipset is now working. The first question is now solved (Getting wireless adapter to work or something like this).

The question is really about getting wireless with the hardware configuration I mentioned to work securely.

This is the output of mentioned commands:
```
ario@ario-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

vboxnet0  no wireless extensions.

ra0       Ralink STA  ESSID:"aario-server-3"  Nickname:"RT2870STA"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Cell: CA:C6:DE:16:8D:54   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-13 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

ario@ario-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:92:2f:dd:48  
          inet6 addr: fe80::21d:92ff:fe2f:dd48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6580742 (6.5 MB)  TX bytes:925945 (925.9 KB)
          Interrupt:29 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:22:b0:52:9b:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:125451 (125.4 KB)  TX bytes:125451 (125.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:89.165.81.43  P-t-P:89.165.81.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:952 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1104325 (1.1 MB)  TX bytes:114321 (114.3 KB)

ra0       Link encap:Ethernet  HWaddr 00:26:5a:0c:d3:b0  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5aff:fe0c:d3b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104348 (104.3 KB)  TX bytes:40284 (40.2 KB)


```

When I connect the first computer to a hidden network, and after a while connect the second with correct password and manual IP settings, both computers will connect. But cell numbers are different and I just successfully connected them with same cell numbers once and eventually (Enjoyed wireless Internet just for seconds until I ridiculously disconnected it :D).
Thanks for your helps Chilli:).

---

### Post by chili555 on 2010-10-03
> ra0       Ralink STA  ESSID:"aario-server-3"  Nickname:"RT2870STA"
          [COLOR="Red"]Mode:Ad-Hoc [/COLOR] Frequency=2.412 GHz  Cell: CA:C6:DE:16:8D:54   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-13 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0That's correct. I suggest you increase the bitrate:```
sudo iwconfig ra0 rate 54M
```This looks suspicious:> a0       Link encap:Ethernet  HWaddr 00:26:5a:0c:d3:b0  
          inet addr:[COLOR="Red"]192.168.0.5[/COLOR]  Bcast:192.168.0.255  Mask:255.255.255.0Is the IP address range for the ad-hoc network really set up with a 192.xx address? Usually those addresses are used by routers.> cell numbers are differentThat makes sense, doesn't it? If you have a router or DSL modem with the name, for instance, 'router,' then the first computer will connect to 'router.' The second computer, wanting to make an ad-hoc connection, would connect to the cell, for example, 'computer1.' Therefor, they are connected to different cells. Yes?

---

### Post by ario on 2010-10-03
First, I used the command for increasing the bit-rate, but after probing it by iwconfig, it shows no changes in bit-rate setting. So it didn't work!

Second, I can't understand what is the problem with IP address, Is this affects my connection? My hardware configuration is in this form:
[INDENT]My desktop:
[LIST]
[*]I have a DSL modem without wireless. Connected wired to eth0. eth0 is configured with IP address 192.168.0.1
[*]I have a DWA-125 wireless dangle which I need it to share my dsl internet connection with my laptop
[*]I have Ubuntu 10.04 installed
[*]I have a wireless connection in network-manager in ad-hoc, wpa 2 personal and with IP 192.168.0.5 (Should I change it?)
[/LIST][/INDENT]
[INDENT]My laptop:
[LIST]
[*]I have an Ethernet but not connected
[*]I have a built-in wireless on it which Ubuntu detects and installs right out of the box and accurately.
[*]I have Ubuntu 10.04 installed.
[*]I have a wireless connection in network-manager in ad-hoc, wpa 2 personal, IP 192.168.0.6, and the gateway and DNS are 192.168.0.5 to gain access to the shared Internet connection properly. (Should I change these?)
[/LIST][/INDENT]

Now I figured out the problem with network manager and I think it's time to solve issues in this part of problem:
[LIST=1]
[*]I create an ad-hoc connection in my desktop and connect my desktop to it by the method "Connect to a hidden wireless network" using nm-applet.
[*]I wait until my laptop detects my desktops connection
[*]It will find two connectios with the same name, but one is secured and one is not secured (Has no lock icon near it). This may be a bug! Why to connections while I created just one?
[*]I click on the Icon with a lock on it and it asks me for password, Just password, It will not let me to setup IP address or anything else. I can not enter my password also, because I just allows me to select WEP methods. WAPs are not in the list. This is the other problem!
[*]So as you can guess the connection will not work this way. So after I wait for my laptop to get tired of trying, I will edit the "auto ario-server-3" created connection to set Security to WPA2 and IP address to a suitable one.
[*]I click on connect to use the edited connection in laptop and here is the most important problem: I will not connect to my desktop using the same cell number. It will establish a new ad-hoc connection and waits for other parties! This is not good!
[/LIST]
I must to find a way to tell my laptops nm-applet program to not establish a new ad-hoc connection with a new cell number and just try to connect to my desktops already created network. Do you know how?
Waiting for your helpful response:)
-----------------------------
Update: There is a very critical problem. I set up the ad-hoc connection on my desktop with ubuntu 10.04 in WPA2 security mode, and the other computer (my laptop) even in Ubuntu or in Windows 7 recognizes this connection as an unsecured connection and thus fail to connect to it.
Tried to compile Network-Manager 8.1 (The latest version) but it requires gudev-1.0 to configure, which is not exists anywhere!

---

### Post by chili555 on 2010-10-04
Your questions are related to internet connection sharing. It's a subject I know little or nothing about.

You might study this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

You might also search for or start a new thread referring to connection sharing.

---

### Post by ario on 2010-10-05
> **chili555 said:**
> Your questions are related to internet connection sharing. It's a subject I know little or nothing about.

You might study this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

You might also search for or start a new thread referring to connection sharing.

Ok. Thanks for your helps Chili:)
I'm working on it. For now I decied to forget about network-manager!

---

### Post by johnsuffer on 2010-10-05
**Hi Ario !  **
 After reading and _**searching a lot**_ for the **D-LINK USB DWA 125** PERFECT DRIVER??  Wich NEVER WORK ??  The (**drt2870**) (**original .inf file** (from the dlink CD setup driver files) was installed with diswrapper showing (**Install** **and present**)but not loading at startup)for my new operating system ubuntu 10.04 
 
But after **reading a lot of comments** on the ubuntu community !! 
I found the **rawlink replacement rt3070** to be installed as driver to initiate my usb **wireles adapter** ? BUT I REALLY DONT KNOW *HOW TO INSTALL IT* THE WHOLE RAR ZIP FILE HAS BEEN DOWNLOADED IN MY UBUNTU** download** DESKTOP FILES AND IN MY MACHINE BUT I DONT REALLY KNOW *WHAT COMMANDS TO DO IN TERMINAL TO GET IT INSTALLED** 
 
(I did all the correct steps in network manager to get it going as per ( the ssid name etc Infrastructure wep wpa2a pass word ---mac address--- all are ok ) 
 
I already saved in **black list** the default usb driver (**default driver rt2800usb**)comming with the **cd disk of the ubuntu 10.04** wich was **rt2800usb** But With the command lshw -C network the result still shows **PCI (sysfs)** ??? **Why **?? 
Please help me with all the procedures (Commands) to install the new rawlink replacement driver »»»**rt3070 files** downloaded ? AND ALSO WHY IS THE TERMINAL ALWAYS ASKING ME *YOU SHOULD WRITE AS A *SUPEER-USER* ?? i AM THE ONLY OWNER OF THIS MACHINE 
 
many tks John

---

### Post by ario on 2010-10-12
> **johnsuffer said:**
> **Hi Ario !  **
 After reading and _**searching a lot**_ for the **D-LINK USB DWA 125** PERFECT DRIVER??  Wich NEVER WORK ??  The (**drt2870**) (**original .inf file** (from the dlink CD setup driver files) was installed with diswrapper showing (**Install** **and present**)but not loading at startup)for my new operating system ubuntu 10.04 
 
But after **reading a lot of comments** on the ubuntu community !! 
I found the **rawlink replacement rt3070** to be installed as driver to initiate my usb **wireles adapter** ? BUT I REALLY DONT KNOW *HOW TO INSTALL IT* THE WHOLE RAR ZIP FILE HAS BEEN DOWNLOADED IN MY UBUNTU** download** DESKTOP FILES AND IN MY MACHINE BUT I DONT REALLY KNOW *WHAT COMMANDS TO DO IN TERMINAL TO GET IT INSTALLED** 
 
(I did all the correct steps in network manager to get it going as per ( the ssid name etc Infrastructure wep wpa2a pass word ---mac address--- all are ok ) 
 
I already saved in **black list** the default usb driver (**default driver rt2800usb**)comming with the **cd disk of the ubuntu 10.04** wich was **rt2800usb** But With the command lshw -C network the result still shows **PCI (sysfs)** ??? **Why **?? 
Please help me with all the procedures (Commands) to install the new rawlink replacement driver »»»**rt3070 files** downloaded ? AND ALSO WHY IS THE TERMINAL ALWAYS ASKING ME *YOU SHOULD WRITE AS A *SUPEER-USER* ?? i AM THE ONLY OWNER OF THIS MACHINE 
 
many tks John
I suggest you to read this topic from top to bottom. There I described all commands to modify, compile, install and use the source code.
After you read all posts but not just one or two then try to do them yourself. After you did, I think you will encounter another problem. As I mentioned, this way your adapter will be detected and will start working but will not connect in any of wireless modes!
You blacklisted those drivers and it's alright. Now you have no activated driver on your system so **lshw -C** network will not show any wireless adapter for you.
You must first of all commands run **sudo su** to tell your operating system you know what you are doing and that the responsibility of all abuse is on you (Although it will always be on yourself!).
The lesson I got from this topic and this problem was that:
When you face a network problem in Linux, try to forget about networking until you change your hardware and your method. Because writing thousands of topics and trying thousands of commands will not change the inherent nature of linux for you! **If Linux can connect you with your hardware then It must do it in first attempt. If it didn't, then it will never!**

---

### Post by MeeMaw on 2010-10-12
> **ario said:**
>  **If Linux can connect you with your hardware then It must do it in first attempt. If it didn't, then it will never!**

Well, I don't think that's true.....  if you have mistyped something or have another error, it CAN be corrected. The first time I tried to configure my rt61 wireless, it took me a week. However, it was because of my mistakes, not because of Linux. (Been using it for almost 5 years now.)

I'm sure you can get it all working the way you want.

---

### Post by ario on 2010-10-13
> **MeeMaw said:**
> Well, I don't think that's true.....  if you have mistyped something or have another error, it CAN be corrected. The first time I tried to configure my rt61 wireless, it took me a week. However, it was because of my mistakes, not because of Linux. (Been using it for almost 5 years now.)

I'm sure you can get it all working the way you want.

Thank you man. I'm keep working on it. I will come here and write if I figured out how to make it work. But still no success.
Now I can only connect with my adapter in these modes:
[LIST]
[*]without any encryption or
[*]with WEP
[/LIST]
Which are not secure. The problem is that I can not connect in WPA mode. Whether I start connection in Ad-Hoc mode from my desktop (Which has a DWA-125 on it) or start it first from my laptop (With a different adapter). The second computer which joins to AdHoc network cannot authenticate and will create it's own connection with different cell ID.
Any Idea?

---

### Post by johnsuffer on 2010-10-17
> **ario said:**
> In this topic I successfuly installed and used the driver for my D-link DWA-125 wireless dangle. There are some fundamental tips in doing this. Now I'm able to connect with WEP or None secured modes. But yet can not connect with it trough WAP2 encryption mode. I think the problem is yet with the driver I compiled and installed. If you know a solution I will be glad to now about.
Thanks.
------------------------------------------------------
I have 2 computers both with Windows 7 and Ubuntu 10.04 in dual boot.
I have 2 wireless adapters.
I can not connect my computers wireless and I think this is because of linux as I described below. But the question is:
Is Ubuntu 10.04 continue support wireless? Or I must try another Distro./OS (like fedora, suse, windows, bsd and etc.)?

When boot computers in windows 7[INDENT]Both can detect and install their wireless adapters automatically, and thus create an Ad-Hoc connection with wpa2 and connect them together without any problem. The only problem is that it is Bill Gates Windows!
[/INDENT]When Booting both in Linux:[INDENT]Computer A with DWA-125 wireless can not scan any wireless access point, but the other computer with another wireless adapter can scan two or more wireless points around me! In spite of the fact that Windows on computer A can detect these access points either, **Driver of DWA-125 on Ubuntu 10.04 is buggy and not working.**[/INDENT]Booting Computer A with DWA-125 adapter in Ubuntu and the other in Windows 7:[INDENT]Created an ad-hoc connection in windows 7 and the other computer with DWA-125 adapter and Ubuntu 10.04 cannot find any wireless life on the earth![/INDENT]Booting Computer A with DWA-125 adapter in Windows 7 and the other in Ubuntu:[INDENT]This time created an ad-hoc connection in windows 7 and tried to scan it trough the other computer via Ubuntu 10.04. It find the connection, but cannot authenticate. Searched about 3 hours trough Internet and were too ANGRY! Completely removed all "network-manager" named packages via synaptic with all their settings. Completely removed WICD 1.7.0 and all its configuration files (Even the one in /var/lib/wicd/configuration !!!). Installed WICD 1.6.2 (Downgraded). It can now authenticate but cannot obtain IP Address! Searched [www.wicd.net]("http://www.wicd.net") forum and yet another unsolved BUG![/INDENT]So that problems are all on Linux!
[LIST]
[*]They can not without any Windows connect to each other either!
[*]The built-in driver and configuration for DWA-125 in 10.04 is not working, despite iwconfig shows a wlan0 and dmesg shows that device is detected with no errors.
[*] network-manager and WICD set of packages have several errors. from their source codes to their behaviors in software manager system. Their conflict with each other but synaptic don't say it!
[/LIST]

I need wireless guys. And I cant wait. Please tell me if I have to change to another OS.
Any response will be appreciated.
------------------------------------------------------------------------------------
oct 17-2010
HELLO I'M A LITTLE LATE TO HELP YOU BUT 2 GUYS  HELP ME ON THE UBUNTU 10.04  FORUM  AND TOLD ME HOW TO CONNECT WITH A USB 125 D-LINK NOW I AM CONNECTED. with help from PYTHEAS22  AND  FLASH63 ON NETWORKING SUBJECT 

Step1/ You really have to remove the *Default* in blacklist the  linux driver rt2800usb Even though you use the ndiswrapper and the ndisgtk program those we use to install a windows driver in linux.
First command 

sudo gedit /etc/modprobe.d/blacklist.conf  rt2800usb   blacklist rt2x00usb   blacklist rt200lib

than  SAVED and   reboot

Step 2 /
 
You have  to RENAME the (.inf) file  furnish with your d-link CD ! What to do is you **copy **this file from (Your setup driver files in the dlink CD) iwas saying copy this .inf file on your linux platform (Desktop) the name of this file driver is  **dtr2870.inf**  That file has to be rename  to**  drt2870sta.inf   **So use the normal way to reinstall that new rename driver with  top menu admistration down to windows driver install  (Than install it) a pop up will tell you '' Install and Present . but sometimes it will pop up (Not sure if its present)   Ignore this

Than do this command 

sudo  ls -C Network

Instead of the rt2800usb  driver showing up it will show  *usb*   That`s good  You,r  almost there !

Than follow all the steps suggested by Flash 63 (Review twice all commands ) than suddenly u will be connected on your network (Here are  following **Flash63  link**)
**GOOD LUCK**
John ;-)

[FONT=&quot][http://ubuntuforums.org/showthread.php?t=1593480](http://ubuntuforums.org/showthread.php?t=1593480)[/FONT]

---

### Post by aneganov on 2010-10-25
Oh my god. Damn the day, when I decided to buy this **** - D-Link DWA-125 Wireless 150 USB Adapter. Now I wasted 6 hours trying to get it working on Ubuntu 10.04. 

I suppose my problem doesn't concern the driver-module itself - its ok. I had compiled it from sources, it's called rt3370sta.ko now and smoothly insmodded into my kernel. 

Now. What the hell is wrong with Network Manager, so that it doesn't work with my DWA-125? Adapter blinks, iwlist'ing shows all the surrounding networks, but NM does not show ANYTHING available in its menu.

When I plug the DWA-125 in, NM puts into syslog:

```
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/net/ra0, iface: ra0)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/net/ra0, iface: ra0): no ifupdown configuration found.
NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/3
NetworkManager: <info>  (ra0): now managed
NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (ra0): bringing up device.
NetworkManager: <info>  (ra0): preparing device.
NetworkManager: <info>  (ra0): deactivating device (reason: 2).
NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 42)
```

Any ideas, how to make NM to work with my adapter?

UPD. Sorry, Ario, nothing personal, but the topic's name is just stupid.

---

### Post by chili555 on 2010-10-25
> Any ideas, how to make NM to work with my adapter?May I please see:```
cat /etc/network/interfaces
```Also, is the wired ethernet attached and connected?

Thanks.

---

### Post by aneganov on 2010-10-26
Hello, chili555.

> **chili555 said:**
> May I please see:```
cat /etc/network/interfaces
```Also, is the wired ethernet attached and connected?

Here it is:

```
$ cat /etc/network/interfaces  | grep -v ^#
auto lo
iface lo inet loopback
```

and

```
$ cat /etc/NetworkManager/nm-system-settings.conf | grep -v ^#
[main]
plugins=ifupdown,keyfile

no-auto-default=00:1d:72:cc:58:42,

[ifupdown]
managed=true

```


> Also, is the wired ethernet attached and connected?

Yes, it is. 

**Some details about my setup.**

It is Acer 5930G laptop, with built-in WiFi:

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

To test the new DWA WiFi device, I disabled IWL 5100 by blacklisting both of its modules: iwlcore.ko and iwlagn.ko.

---

### Post by chili555 on 2010-10-26
> $ cat /etc/NetworkManager/nm-system-settings.conf | grep -v ^#
[main]
plugins=ifupdown,keyfile

no-auto-default=00:1d:72:cc:58:42,

[ifupdown]
managed=trueTry changing to managed = false.

---

### Post by aneganov on 2010-10-26
> **chili555 said:**
> Try changing to managed = false.

Already tried. No difference.

---

### Post by chili555 on 2010-10-26
After you set it to false, did you reboot? Are networks still not showing when you click the Network Manager icon?

---

### Post by aneganov on 2010-10-26
> **chili555 said:**
> After you set it to false, did you reboot? Are networks still not showing when you click the Network Manager icon?

I tried both rebooting and restarting servics:
$ /etc/init.d/networking restart
$ restart network-manager

Neither works.

But NM does see the DWA-125: when the adapter is not plugged, only wired networks available in menu, but when it is plugged in, then Wirelsee category appearing in the menu. The problem - the list of networks is empty, while performing simple scan shows the are available:

```

$ iwlist ra0 scan

ra0       Scan completed :
          Cell 01 - Address: 00:22:15:7B:26:C3
                    Protocol:802.11b/g
                    ESSID:"WL520GC_rzsL"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:68/100  Signal level:-63 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:19:E1:00:0A:50
                    Protocol:802.11b/g
                    ESSID:""
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:7/100  Signal level:-87 dBm  Noise level:-82 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 03 - Address: 00:19:E1:00:0A:51
                    Protocol:802.11b/g
                    ESSID:"Beeline_WiFi"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-91 dBm  Noise level:-86 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 04 - Address: 00:14:D1:59:EF:CF
                    Protocol:802.11b/g
                    ESSID:"XNet"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:83/100  Signal level:-57 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 05 - Address: 00:19:E1:01:92:B0
                    Protocol:802.11b/g
                    ESSID:""
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-76 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 06 - Address: 00:19:E1:01:92:B1
                    Protocol:802.11b/g
                    ESSID:"Beeline_WiFi"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:31/100  Signal level:-77 dBm  Noise level:-72 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 07 - Address: 00:19:E1:01:92:B2
                    Protocol:802.11b/g
                    ESSID:"Beeline_WiFi_WPA"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-74 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
etc

```

---

### Post by chili555 on 2010-10-26
May I see:```
dmesg | grep -i rt2
```Thanks.

---

### Post by aneganov on 2010-10-26
> **chili555 said:**
> May I see:```
dmesg | grep -i rt2
```Thanks.

There are only latest records, dmesg doesn't show what happened before. I have no clean bootlog since was restarted yesterday last time.

Instead I can provide output of kernel driver when I plug the DWA-125 in (its huge, so I snip it to the first seconds):

```


16:03:16 kernel: [23622.136083] usb 2-3: new high speed USB device using ehci_hcd and address 14
16:03:16 kernel: [23622.285187] usb 2-3: configuration #1 chosen from 1 choice
16:03:16 kernel: [23622.285896] ===>rt2870_probe()!
16:03:16 kernel: [23622.285901] --> RTMPAllocAdapterBlock
16:03:16 kernel: [23622.286171] 
16:03:16 kernel: [23622.286172] 
16:03:16 kernel: [23622.286174] === pAd = f8804000, size = 511944 ===
16:03:16 kernel: [23622.286176] 
16:03:16 kernel: [23622.286310] <-- RTMPAllocAdapterBlock, Status=0
16:03:16 kernel: [23622.286315] NumEndpoints=7
16:03:16 kernel: [23622.286319] BULK IN MaxPacketSize = 512
16:03:16 kernel: [23622.286323] EP address = 0x81
16:03:16 kernel: [23622.286327] BULK OUT MaxPacketSize = 512
16:03:16 kernel: [23622.286331] EP address = 0x 1  
16:03:16 kernel: [23622.286335] BULK OUT MaxPacketSize = 512
16:03:16 kernel: [23622.286339] EP address = 0x 2  
16:03:16 kernel: [23622.286343] BULK OUT MaxPacketSize = 512
16:03:16 kernel: [23622.286347] EP address = 0x 3  
16:03:16 kernel: [23622.286350] BULK OUT MaxPacketSize = 512
16:03:16 kernel: [23622.286354] EP address = 0x 4  
16:03:16 kernel: [23622.286358] BULK OUT MaxPacketSize = 512
16:03:16 kernel: [23622.286362] EP address = 0x 5  
16:03:16 kernel: [23622.286366] BULK OUT MaxPacketSize = 512
16:03:16 kernel: [23622.286370] EP address = 0x 6  
16:03:16 kernel: [23622.286375] STA Driver version-2.4.0.1
16:03:16 kernel: [23622.286676] NVM is EFUSE
16:03:16 kernel: [23622.286683] Allocate a net device with private data size=0!
16:03:16 kernel: [23622.286700] Allocate net device ops success!
16:03:16 kernel: [23622.286708] The name of the new ra interface is ra0...
16:03:16 kernel: [23622.286713] RtmpOSNetDevAttach()--->
16:03:16 kernel: [23622.292613] <---RtmpOSNetDevAttach(), ret=0
16:03:16 kernel: [23622.299931] <===rt2870_probe()!
16:03:16 kernel: [23622.307846] ===>rt_ioctl_giwrange
16:03:16 kernel: [23622.307856] INFO::Network is down!
16:03:16 kernel: [23622.307873] ===>rt_ioctl_giwrange
16:03:16 kernel: [23622.308254] Allocate 8192 memory for BA reordering
16:03:16 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/net/ra0, iface: ra0)
16:03:16 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/net/ra0, iface: ra0): no ifupdown configuration found.
16:03:16 NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
16:03:16 NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
16:03:16 NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/6
16:03:16 NetworkManager: <info>  (ra0): now managed
16:03:16 NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
16:03:16 NetworkManager: <info>  (ra0): bringing up device.
16:03:16 kernel: [23622.309756] MAC_CSR0  [ Ver:Rev=0x30700201]
16:03:17 kernel: [23622.581937] <=== RtmpAsicLoadFirmware (status=0)
16:03:17 kernel: [23622.581946] --> RTMPAllocTxRxRingMemory
16:03:17 kernel: [23622.581951] --> NICInitTransmit
16:03:17 kernel: [23622.582391] MGMT Ring: total 32 entry allocated
16:03:17 kernel: [23622.582400] <-- NICInitTransmit(Status=0)
16:03:17 kernel: [23622.582404] --> NICInitRecv
16:03:17 kernel: [23622.582555] <-- NICInitRecv(Status=0)
16:03:17 kernel: [23622.582562] <-- RTMPAllocTxRxRingMemory, Status=0
16:03:17 kernel: [23622.582733] --> MLME Initialize
16:03:17 kernel: [23622.582820] <-- MLME Initialize
16:03:17 kernel: [23622.582824] --> UserCfgInit
16:03:17 kernel: [23622.582829] --> UserCfgInit. BACapability = 0x3024040
16:03:17 kernel: [23622.582876] <-- UserCfgInit
16:03:17 kernel: [23622.582882] --> NICInitializeAdapter
16:03:17 kernel: [23622.583057] <== DMA offset 0x208 = 0x0
16:03:17 kernel: [23622.583303] --> NICInitializeAsic
16:03:17 kernel: [23622.583429] MAC_CSR0  [ Ver:Rev=0x30700201]
16:03:17 kernel: [23622.584306] -->RTUSBVenderReset
16:03:17 kernel: [23622.584430] <--RTUSBVenderReset
16:03:17 kernel: [23622.594558] BBP version = 60
16:03:17 kernel: [23622.864061] --->Disable TSF synchronization
16:03:17 kernel: [23622.865803] <-- NICInitializeAsic
16:03:17 kernel: [23622.865808] <-- NICInitializeAdapter
16:03:17 kernel: [23622.865972] CountryRegion=5
16:03:17 kernel: [23622.866004] CountryRegionABand=7
16:03:17 kernel: [23622.866036] CountryCode=
16:03:17 kernel: [23622.866072] RTMPSetProfileParameters::(SSID=11n-AP)
16:03:17 kernel: [23622.866109] RTMPSetProfileParameters::(NetworkType=1)
16:03:17 kernel: [23622.866146] Channel=0
16:03:17 kernel: [23622.866183] PhyMode=5
16:03:17 kernel: [23622.866320] BeaconPeriod=100
16:03:17 kernel: [23622.866359] TxPower=100
16:03:17 kernel: [23622.866399] BGProtection=0
16:03:17 kernel: [23622.866440] TxPreamble=0
16:03:17 kernel: [23622.866483] RTSThreshold=2347
16:03:17 kernel: [23622.866527] FragThreshold=2346
16:03:17 kernel: [23622.866571] TxBurst=1
16:03:17 kernel: [23622.866617] PktAggregate=0
16:03:17 kernel: [23622.866663] WmmCapable=1
16:03:17 kernel: [23622.866711] AckPolicy[0]=0
16:03:17 kernel: [23622.866715] AckPolicy[1]=0
16:03:17 kernel: [23622.866719] AckPolicy[2]=0
16:03:17 kernel: [23622.866723] AckPolicy[3]=0
16:03:17 kernel: [23622.866785] APSDCapable=0
16:03:17 kernel: [23622.866945] APSDAC0  0
16:03:17 kernel: [23622.866949] APSDAC1  0
16:03:17 kernel: [23622.866952] APSDAC2  0
16:03:17 kernel: [23622.866956] APSDAC3  0
16:03:17 kernel: [23622.867132] IEEE80211H=0
16:03:17 kernel: [23622.867409] WirelessEvent=0
16:03:17 kernel: [23622.867459] RTMPSetProfileParameters::(AuthMode=0)
16:03:17 kernel: [23622.867510] RTMPSetProfileParameters::(EncrypType=1)
16:03:17 kernel: [23622.867608] DefaultKeyID(0~3)=0
16:03:17 kernel: [23622.867712] Key1Str is Invalid key length(0) or Type(0)
16:03:17 kernel: [23622.867818] Key2Str is Invalid key length(0) or Type(0)
16:03:17 kernel: [23622.867927] Key3Str is Invalid key length(0) or Type(0)
16:03:17 kernel: [23622.868070] Key4Str is Invalid key length(0) or Type(0)
16:03:17 kernel: [23622.868243] HT: MIMOPS Mode  = 3
16:03:17 kernel: [23622.868312] HT: BA Decline  = Disable
16:03:17 kernel: [23622.868380] HT: Auto BA  = Enable
16:03:17 kernel: [23622.868542] HT: RDG = Enable(+HTC)
16:03:17 kernel: [23622.868611] HT: Tx A-MSDU = Disable
16:03:17 kernel: [23622.868678] HT: MPDU Density = 4
16:03:17 kernel: [23622.868749] HT: BA Windw Size = 64
16:03:17 kernel: [23622.868820] HT: Guard Interval = 400
16:03:17 kernel: [23622.868884] HT: Operate Mode = Mixed Mode
16:03:17 kernel: [23622.869049] HT: Channel Width = 40 MHz
16:03:17 kernel: [23622.869113] HT: Ext Channel = BELOW
16:03:17 kernel: [23622.869184] HT: MCS = AUTO
16:03:17 kernel: [23622.869259] HT: STBC = 0
16:03:17 kernel: [23622.869628] HT: Disallow TKIP mode = ON
16:03:17 kernel: [23622.869986] PSMode=0
16:03:17 kernel: [23622.870045] AutoRoaming=0
16:03:17 kernel: [23622.870106] RoamThreshold=-70  dBm
16:03:17 kernel: [23622.870185] TGnWifiTest=0
16:03:17 kernel: [23622.870276] BeaconLostTime=1000 
16:03:17 kernel: [23622.870493] MlmeSetPsmBit = 0
16:03:17 kernel: [23622.870505] 1. Phy Mode = 5
16:03:17 kernel: [23622.870509] 2. Phy Mode = 5
16:03:17 kernel: [23622.870512] --> NICReadEEPROMParameters
16:03:17 kernel: [23622.870518] NVM is Efuse and its size =2d[2d0-2fc] 
16:03:17 kernel: [23622.882057] eFuseGetFreeBlockCount is 0xa
16:03:17 kernel: [23622.882062] NVM is Efuse and force to use EEPROM Buffer Mode=0
16:03:17 kernel: [23622.882179] --> E2PROM_CSR = 0x20408
16:03:17 kernel: [23622.882183] --> EEPROMAddressNum = 6
16:03:17 kernel: [23622.882187] Initialize MAC Address from E2PROM 
16:03:17 kernel: [23622.885764] E2PROM MAC: =1c:af:f7:6d:06:7e
16:03:17 kernel: [23622.885770] Use the MAC address what is assigned from EEPROM. 
16:03:17 kernel: [23622.886681] Current MAC: =1c:af:f7:6d:06:7e
16:03:17 kernel: [23622.916684] E2PROM: Version = 1, FAE release #0
16:03:17 kernel: [23622.922559] NICReadEEPROMParameters: RxPath = 1, TxPath = 1
16:03:17 kernel: [23622.922564] phy mode> Error! The chip does not support 5G band 5!
16:03:17 kernel: [23622.922721] RTMPSetPhyMode : PhyMode=9, channel=0 
16:03:17 kernel: [23622.922729] country code=5/7, RFIC=5, PHY mode=9, support 14 channels
16:03:17 kernel: [23622.922735] BuildChannel # 1 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922737]  BuildChannel # 2 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922743]  BuildChannel # 3 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922748]  BuildChannel # 4 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922754]  BuildChannel # 5 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922759]  BuildChannel # 6 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922764]  BuildChannel # 7 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922769]  BuildChannel # 8 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922774]  BuildChannel # 9 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922780]  BuildChannel # 10 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922785]  BuildChannel # 11 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922790]  BuildChannel # 12 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922795]  BuildChannel # 13 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922800]  BuildChannel # 14 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.922806]  RTMPSetPhyMode: channel is out of range, use first channel=1 
16:03:17 kernel: [23622.922816] RTMPSetHT : HT_mode(0), ExtOffset(3), MCS(33), BW(1), STBC(0), SHORTGI(1)
16:03:17 kernel: [23622.922822] RTMPSetHT : RxBAWinLimit = 64
16:03:17 kernel: [23622.922828] RTMPSetHT : AMsduSize = 0, MimoPs = 3, MpduDensity = 4, MaxRAmpduFactor = 3
16:03:17 kernel: [23622.926428] EDCA [#0]: AIFSN CWmin CWmax  TXOP(us)  ACM
16:03:17 kernel: [23622.926434]      AC_BE       3      4      6         0     0
16:03:17 kernel: [23622.926441]      AC_BK       7      4     10         0     0
16:03:17 kernel: [23622.926447]      AC_VI       1      3      4      3008     0
16:03:17 kernel: [23622.926452]      AC_VO       1      2      3      1504     0
16:03:17 kernel: [23622.926458] RTMPSetIndividualHT : Desired MCS = 33
16:03:17 kernel: [23622.926463] MlmeUpdateHtTxRates===> 
16:03:17 kernel: [23622.926468]  MlmeUpdateHtTxRates<---.AMsduSize = 0  
16:03:17 kernel: [23622.926474] TX: MCS[0] = ff (choose 7), BW = 1, ShortGI = 1, MODE = 2,  
16:03:17 kernel: [23622.926479] MlmeUpdateHtTxRates<=== 
16:03:17 kernel: [23622.926484] Chip specific bbpRegTbSize=0!
16:03:17 kernel: [23622.929433] E2PROM: G Tssi[-4 .. +4] = 255 255 255 255 - 255 -255 255 255 255, step=255, tuning=0
16:03:17 kernel: [23622.932560] E2PROM: A Tssi[-4 .. +4] = 255 255 255 255 - 255 -255 255 255 255, step=255, tuning=0
16:03:17 kernel: [23622.933178] E2PROM: RF FreqOffset=0x29 
16:03:17 kernel: [23622.933184] RTMPSetPhyMode : PhyMode=9, channel=1 
16:03:17 kernel: [23622.933191] country code=129/129, RFIC=5, PHY mode=9, support 13 channels
16:03:17 kernel: [23622.933197] BuildChannel # 1 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933199]  BuildChannel # 2 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933205]  BuildChannel # 3 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933211]  BuildChannel # 4 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933216]  BuildChannel # 5 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933221]  BuildChannel # 6 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933226]  BuildChannel # 7 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933232]  BuildChannel # 8 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933237]  BuildChannel # 9 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933242]  BuildChannel # 10 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933247]  BuildChannel # 11 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933252]  BuildChannel # 12 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933257]  BuildChannel # 13 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23622.933263]  RTMPSetHT : HT_mode(0), ExtOffset(3), MCS(33), BW(1), STBC(0), SHORTGI(1)
16:03:17 kernel: [23622.933273] RTMPSetHT : RxBAWinLimit = 64
16:03:17 kernel: [23622.933279] RTMPSetHT : AMsduSize = 0, MimoPs = 3, MpduDensity = 4, MaxRAmpduFactor = 3
16:03:17 kernel: [23622.937803] EDCA [#0]: AIFSN CWmin CWmax  TXOP(us)  ACM
16:03:17 kernel: [23622.937810]      AC_BE       3      4      6         0     0
16:03:17 kernel: [23622.937816]      AC_BK       7      4     10         0     0
16:03:17 kernel: [23622.937822]      AC_VI       1      3      4      3008     0
16:03:17 kernel: [23622.937828]      AC_VO       1      2      3      1504     0
16:03:17 kernel: [23622.937833] RTMPSetIndividualHT : Desired MCS = 33
16:03:17 kernel: [23622.937837] MlmeUpdateHtTxRates===> 
16:03:17 kernel: [23622.937842]  MlmeUpdateHtTxRates<---.AMsduSize = 0  
16:03:17 kernel: [23622.937848] TX: MCS[0] = ff (choose 7), BW = 1, ShortGI = 1, MODE = 2,  
16:03:17 kernel: [23622.937853] MlmeUpdateHtTxRates<=== 
16:03:17 kernel: [23622.944304] Txpower per Rate
16:03:17 kernel: [23622.944929] Gpwrdelta = 1, Apwrdelta = 0 .
16:03:17 kernel: [23622.949552] 20MHz BW, 2.4G band-88886666,  Adata = 88886666,  Gdata = 77775555 
16:03:17 kernel: [23622.951051] 20MHz BW, 2.4G band-77776677,  Adata = 77776677,  Gdata = 66665566 
16:03:17 kernel: [23622.952551] 20MHz BW, 2.4G band-aaaa5566,  Adata = aaaa5566,  Gdata = 99994455 
16:03:17 kernel: [23622.957053] 20MHz BW, 2.4G band-aaaa6688,  Adata = aaaa6688,  Gdata = 99995577 
16:03:17 kernel: [23622.958426] 20MHz BW, 2.4G band-ffff6688,  Adata = ffff6688,  Gdata = eeee5577 
16:03:17 kernel: [23622.959051] <-- NICReadEEPROMParameters
16:03:17 kernel: [23622.959058] 3. Phy Mode = 9
16:03:17 kernel: [23622.959062] --> NICInitAsicFromEEPROM
16:03:17 kernel: [23622.993674] RTMPFilterCalibration - CaliBW20RfR24=0x8, CaliBW40RfR24=0x27
16:03:17 kernel: [23622.996431] RTMPSetLED::Mode=10,HighByte=0x20,LowByte=0x0a
16:03:17 kernel: [23622.999930] NICInitAsicFromEEPROM: pAd->TxPowerCtrl.bInternalTxALC = 0
16:03:17 kernel: [23623.001930] Use Hw Radio Control Pin=0; if used Pin=0;
16:03:17 kernel: [23623.003706] TxPath = 1, RxPath = 1, RFIC=5, Polar+LED mode=a
16:03:17 kernel: [23623.003711] <-- NICInitAsicFromEEPROM
16:03:17 kernel: [23623.003717] RTMPSetPhyMode : PhyMode=9, channel=1 
16:03:17 kernel: [23623.003725] country code=129/129, RFIC=5, PHY mode=9, support 13 channels
16:03:17 kernel: [23623.003731] BuildChannel # 1 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003733]  BuildChannel # 2 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003739]  BuildChannel # 3 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003744]  BuildChannel # 4 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003750]  BuildChannel # 5 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003755]  BuildChannel # 6 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003761]  BuildChannel # 7 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003766]  BuildChannel # 8 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003771]  BuildChannel # 9 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003776]  BuildChannel # 10 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003781]  BuildChannel # 11 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003786]  BuildChannel # 12 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003792]  BuildChannel # 13 :: Pwr0 = 12, Pwr1 =0, 
16:03:17 kernel: [23623.003797]  RTMPSetHT : HT_mode(0), ExtOffset(3), MCS(33), BW(1), STBC(0), SHORTGI(1)
16:03:17 kernel: [23623.003808] RTMPSetHT : RxBAWinLimit = 64
16:03:17 kernel: [23623.003813] RTMPSetHT : AMsduSize = 0, MimoPs = 3, MpduDensity = 4, MaxRAmpduFactor = 3
16:03:17 kernel: [23623.007068] EDCA [#0]: AIFSN CWmin CWmax  TXOP(us)  ACM
16:03:17 kernel: [23623.007075]      AC_BE       3      4      6         0     0
16:03:17 kernel: [23623.007081]      AC_BK       7      4     10         0     0
16:03:17 kernel: [23623.007087]      AC_VI       1      3      4      3008     0
16:03:17 kernel: [23623.007093]      AC_VO       1      2      3      1504     0
16:03:17 kernel: [23623.007098] RTMPSetIndividualHT : Desired MCS = 33
16:03:17 kernel: [23623.007103] MlmeUpdateHtTxRates===> 
16:03:17 kernel: [23623.007108]  MlmeUpdateHtTxRates<---.AMsduSize = 0  
16:03:17 kernel: [23623.007115] TX: MCS[0] = ff (choose 7), BW = 1, ShortGI = 1, MODE = 2,  
16:03:17 kernel: [23623.007119] MlmeUpdateHtTxRates<=== 
16:03:17 kernel: [23623.007125] MCS Set = ff 00 00 00 01
16:03:17 kernel: [23623.017782] NDIS_STATUS_MEDIA_DISCONNECT Event B!
16:03:17 kernel: [23623.017796] RTUSBBulkReceive!
16:03:17 kernel: [23623.017802] <==== rt28xx_init, Status=0
16:03:17 kernel: [23623.017806] ==> RTMPEnableRxTx
16:03:17 kernel: [23623.018230] <== WRITE DMA offset 0x208 = 0x45
16:03:17 kernel: [23623.019177] <== RTMPEnableRxTx
16:03:17 kernel: [23623.019305] 0x1300 = 00064300
16:03:17 kernel: [23623.019310] Driver auto reconnect to last OID_802_11_SSID setting - 11n-AP, len - 6
16:03:17 kernel: [23623.019396] CntlOidSsidProc():CNTL - 0 BSS of 0 BSS match the desire (6)SSID - 11n-AP
16:03:17 kernel: [23623.019405] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
16:03:17 kernel: [23623.019563] SCANNING, suspend MSDU transmission ...
16:03:17 NetworkManager: <info>  (ra0): preparing device.
16:03:17 NetworkManager: <info>  (ra0): deactivating device (reason: 2).
16:03:17 kernel: [23623.021302] SYNC - BBP R4 to 20MHz.l
16:03:17 kernel: [23623.025922] ==>rt_ioctl_giwmode(mode=0)
16:03:17 kernel: [23623.025949] ===>Set_NetworkType_Proc::(INFRA)
16:03:17 kernel: [23623.025954] Set_NetworkType_Proc::(NetworkType=1)
16:03:17 kernel: [23623.026063] ===>rt_ioctl_giwrange
16:03:17 kernel: [23623.030585] ===> rt_ioctl_siwpmksa
16:03:17 kernel: [23623.030592] rt_ioctl_siwpmksa - IW_PMKSA_FLUSH
16:03:17 kernel: [23623.030600] ===>Set_NetworkType_Proc::(INFRA)
16:03:17 kernel: [23623.030604] Set_NetworkType_Proc::(NetworkType=1)
16:03:17 kernel: [23623.030625] ===>rt_ioctl_giwrange
16:03:17 kernel: [23623.038677] SwitchChannel#1(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
16:03:17 kernel: [23623.040092] rt_ioctl_siwauth::IW_AUTH_WPA_ENABLED - Driver supports WPA!(param->value = 1)
16:03:17 kernel: [23623.040550] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
16:03:17 kernel: [23623.040553] 		WCIDAttri = 0x1 
16:03:17 kernel: [23623.040555] AsicRemovePairwiseKeyEntry : Wcid #1 
16:03:17 kernel: [23623.040556] AsicRemoveSharedKeyEntry: #0 
16:03:17 kernel: [23623.040797] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
16:03:17 kernel: [23623.041299] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8401)
16:03:17 kernel: [23623.041797] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
16:03:17 kernel: [23623.041800] 		WCIDAttri = 0x1 
16:03:17 kernel: [23623.041802] AsicRemovePairwiseKeyEntry : Wcid #1 
16:03:17 kernel: [23623.041804] AsicRemoveSharedKeyEntry: #1 
16:03:17 kernel: [23623.042050] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
16:03:17 kernel: [23623.042546] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8402)
16:03:17 kernel: [23623.043047] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
16:03:17 kernel: [23623.043049] 		WCIDAttri = 0x1 
16:03:17 kernel: [23623.043051] AsicRemovePairwiseKeyEntry : Wcid #1 
16:03:17 kernel: [23623.043054] AsicRemoveSharedKeyEntry: #2 
16:03:17 kernel: [23623.043297] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
16:03:17 kernel: [23623.043796] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8403)
16:03:17 kernel: [23623.045296] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
16:03:17 kernel: [23623.045299] 		WCIDAttri = 0x1 
16:03:17 kernel: [23623.045302] AsicRemovePairwiseKeyEntry : Wcid #1 
16:03:17 kernel: [23623.045304] AsicRemoveSharedKeyEntry: #3 
16:03:17 kernel: [23623.045419] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
16:03:17 NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
16:03:17 NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 42)
16:03:17 kernel: [23623.045668] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8404)
16:03:17 kernel: [23623.045677] rt_ioctl_siwauth::IW_AUTH_DROP_UNENCRYPTED - param->value = 1!
16:03:17 kernel: [23623.045682] ===> rt_ioctl_siwpmksa
16:03:17 kernel: [23623.045684] rt_ioctl_siwpmksa - IW_PMKSA_FLUSH
16:03:17 kernel: [23623.050741] rt_ioctl_giwscan:: Still scanning
16:03:17 kernel: [23623.050816] !!! MLME busy, reset MLME state machine !!!
16:03:17 kernel: [23623.051130] !!! reset MLME state machine !!!
16:03:17 kernel: [23623.051133] MlmeRestartStateMachine 
16:03:17 kernel: [23623.060303] SwitchChannel#1(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
16:03:17 kernel: [23623.064539] SCAN done, resume MSDU transmission ...
16:03:17 kernel: [23623.065014] SCANNING, suspend MSDU transmission ...
16:03:17 kernel: [23623.066795] SYNC - BBP R4 to 20MHz.l
16:03:17 kernel: [23623.075047] SwitchChannel#1(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
16:03:17 kernel: [23623.226065] SwitchChannel#2(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x07, R=0x02
16:03:17 kernel: [23623.377936] SwitchChannel#3(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF2, K=0x02, R=0x02
16:03:18 kernel: [23623.528313] SwitchChannel#4(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF2, K=0x07, R=0x02
16:03:18 kernel: [23623.680575] SwitchChannel#5(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF3, K=0x02, R=0x02
16:03:18 kernel: [23623.832313] SwitchChannel#6(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF3, K=0x07, R=0x02
16:03:18 kernel: [23623.984431] SwitchChannel#7(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF4, K=0x02, R=0x02
16:03:18 avahi-daemon[961]: Registering new address record for fe80::1eaf:f7ff:fe6d:67e on ra0.*.
16:03:18 kernel: [23624.134315] SwitchChannel#8(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF4, K=0x07, R=0x02
16:03:18 kernel: [23624.284563] SwitchChannel#9(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF5, K=0x02, R=0x02
16:03:19 kernel: [23624.436309] SwitchChannel#10(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF5, K=0x07, R=0x02
16:03:19 kernel: [23624.589439] SwitchChannel#11(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF6, K=0x02, R=0x02
16:03:19 kernel: [23624.740313] SwitchChannel#12(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF6, K=0x07, R=0x02
16:03:19 kernel: [23624.892313] SwitchChannel#13(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF7, K=0x02, R=0x02
16:03:19 kernel: [23625.044317] SwitchChannel#1(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
16:03:19 kernel: [23625.048575] SYNC - End of SCAN, restore to channel 1, Total BSS[09]
16:03:19 kernel: [23625.048595] SCAN done, resume MSDU transmission ...
16:03:19 kernel: [23625.048689] rt_ioctl_giwscan:: Still scanning

```

---

### Post by chili555 on 2010-10-26
All of this stuff is from /etc/Wireless/RT2870STA/RT2870STA.dat:> 16:03:17 kernel: [23622.866072] RTMPSetProfileParameters::(SSID=11n-AP)
16:03:17 kernel: [23622.866109] RTMPSetProfileParameters::(NetworkType=1)
16:03:17 kernel: [23622.866146] Channel=0
16:03:17 kernel: [23622.866183] PhyMode=5
16:03:17 kernel: [23622.866320] BeaconPeriod=100
16:03:17 kernel: [23622.866359] TxPower=100
16:03:17 kernel: [23622.866399] BGProtection=0
16:03:17 kernel: [23622.866440] TxPreamble=0
16:03:17 kernel: [23622.866483] RTSThreshold=2347
16:03:17 kernel: [23622.866527] FragThreshold=2346
16:03:17 kernel: [23622.866571] TxBurst=1
16:03:17 kernel: [23622.866617] PktAggregate=0
16:03:17 kernel: [23622.866663] WmmCapable=1
etc., etc.You might try amending it to suit your network and see if you can connect.

As a wild, crazy experiment, you might try to amend it to ***not*** load all those incorrect parameters and see if Network Manager will do its job. I am not sure this will work; I don't have the device. 

Remove the device.

First, back up the file so we can restore it if this doesn't work:```
sudo mv /etc/Wireless/RT2870STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat.bak
```Now, let's write a new one with just one word:```
sudo echo Default > /etc/Wireless/RT2870STA/RT2870STA.dat
```Now, reinsert the device and see what the kernel says:```
sudo tail -n 20 /var/log/syslog
```

---

### Post by aneganov on 2010-10-26
Done:

```
21:54:01 kernel: [20413.208102] usb 2-3: new high speed USB device using ehci_hcd and address 10
21:54:02 kernel: [20413.357844] usb 2-3: configuration #1 chosen from 1 choice
21:54:02 kernel: [20413.361681] ===>rt2870_probe()!
21:54:02 kernel: [20413.361688] --> RTMPAllocAdapterBlock
21:54:02 kernel: [20413.362045] 
21:54:02 kernel: [20413.362047] 
21:54:02 kernel: [20413.362048] === pAd = fc3e0000, size = 511944 ===
21:54:02 kernel: [20413.362051] 
21:54:02 kernel: [20413.362172] <-- RTMPAllocAdapterBlock, Status=0
21:54:02 kernel: [20413.362178] NumEndpoints=7
21:54:02 kernel: [20413.362182] BULK IN MaxPacketSize = 512
21:54:02 kernel: [20413.362186] EP address = 0x81
21:54:02 kernel: [20413.362190] BULK OUT MaxPacketSize = 512
21:54:02 kernel: [20413.362194] EP address = 0x 1  
21:54:02 kernel: [20413.362198] BULK OUT MaxPacketSize = 512
21:54:02 kernel: [20413.362201] EP address = 0x 2  
21:54:02 kernel: [20413.362205] BULK OUT MaxPacketSize = 512
21:54:02 kernel: [20413.362209] EP address = 0x 3  
21:54:02 kernel: [20413.362213] BULK OUT MaxPacketSize = 512
21:54:02 kernel: [20413.362217] EP address = 0x 4  
21:54:02 kernel: [20413.362220] BULK OUT MaxPacketSize = 512
21:54:02 kernel: [20413.362224] EP address = 0x 5  
21:54:02 kernel: [20413.362228] BULK OUT MaxPacketSize = 512
21:54:02 kernel: [20413.362232] EP address = 0x 6  
21:54:02 kernel: [20413.362237] STA Driver version-2.4.0.1
21:54:02 kernel: [20413.362459] NVM is EFUSE
21:54:02 kernel: [20413.362465] Allocate a net device with private data size=0!
21:54:02 kernel: [20413.362490] Allocate net device ops success!
21:54:02 kernel: [20413.362498] The name of the new ra interface is ra0...
21:54:02 kernel: [20413.362502] RtmpOSNetDevAttach()--->
21:54:02 kernel: [20413.364728] <---RtmpOSNetDevAttach(), ret=0
21:54:02 kernel: [20413.370442] <===rt2870_probe()!
21:54:02 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/net/ra0, iface: ra0)
21:54:02 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/net/ra0, iface: ra0): no ifupdown configuration found.
21:54:02 NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
21:54:02 NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
21:54:02 NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/7
21:54:02 NetworkManager: <info>  (ra0): now managed
21:54:02 NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
21:54:02 NetworkManager: <info>  (ra0): bringing up device.
21:54:02 kernel: [20413.385816] ===>rt_ioctl_giwrange
21:54:02 kernel: [20413.385828] INFO::Network is down!
21:54:02 kernel: [20413.385845] ===>rt_ioctl_giwrange
21:54:02 kernel: [20413.386191] Allocate 8192 memory for BA reordering
21:54:02 kernel: [20413.386758] MAC_CSR0  [ Ver:Rev=0x30700201]
21:54:02 kernel: [20413.651462] <=== RtmpAsicLoadFirmware (status=0)
21:54:02 kernel: [20413.651470] --> RTMPAllocTxRxRingMemory
21:54:02 kernel: [20413.651475] --> NICInitTransmit
21:54:02 kernel: [20413.651942] MGMT Ring: total 32 entry allocated
21:54:02 kernel: [20413.651953] <-- NICInitTransmit(Status=0)
21:54:02 kernel: [20413.651957] --> NICInitRecv
21:54:02 kernel: [20413.652125] <-- NICInitRecv(Status=0)
21:54:02 kernel: [20413.652132] <-- RTMPAllocTxRxRingMemory, Status=0
21:54:02 kernel: [20413.657162] --> MLME Initialize
21:54:02 kernel: [20413.657272] <-- MLME Initialize
21:54:02 kernel: [20413.657276] --> UserCfgInit
21:54:02 kernel: [20413.657282] --> UserCfgInit. BACapability = 0x3024040
21:54:02 kernel: [20413.657341] <-- UserCfgInit
21:54:02 kernel: [20413.657347] --> NICInitializeAdapter
21:54:02 kernel: [20413.657475] <== DMA offset 0x208 = 0x0
21:54:02 kernel: [20413.657715] --> NICInitializeAsic
21:54:02 kernel: [20413.657841] MAC_CSR0  [ Ver:Rev=0x30700201]
21:54:02 kernel: [20413.658705] -->RTUSBVenderReset
21:54:02 kernel: [20413.658827] <--RTUSBVenderReset
21:54:02 kernel: [20413.669218] BBP version = 60
21:54:02 kernel: [20413.946707] --->Disable TSF synchronization
21:54:02 kernel: [20413.948581] <-- NICInitializeAsic
21:54:02 kernel: [20413.948585] <-- NICInitializeAdapter
21:54:02 kernel: [20413.948969] 1. Phy Mode = 0
21:54:02 kernel: [20413.948974] 2. Phy Mode = 0
21:54:02 kernel: [20413.948977] --> NICReadEEPROMParameters
21:54:02 kernel: [20413.948983] NVM is Efuse and its size =2d[2d0-2fc] 
21:54:02 kernel: [20413.961085] eFuseGetFreeBlockCount is 0xa
21:54:02 kernel: [20413.961091] NVM is Efuse and force to use EEPROM Buffer Mode=0
21:54:02 kernel: [20413.961205] --> E2PROM_CSR = 0x20408
21:54:02 kernel: [20413.961209] --> EEPROMAddressNum = 6
21:54:02 kernel: [20413.961213] Initialize MAC Address from E2PROM 
21:54:02 kernel: [20413.963082] E2PROM MAC: =1c:af:f7:6d:06:7e
21:54:02 kernel: [20413.963087] Use the MAC address what is assigned from EEPROM. 
21:54:02 kernel: [20413.963579] Current MAC: =1c:af:f7:6d:06:7e
21:54:02 kernel: [20413.995332] E2PROM: Version = 1, FAE release #0
21:54:02 kernel: [20414.001332] NICReadEEPROMParameters: RxPath = 1, TxPath = 1
21:54:02 kernel: [20414.001338] Chip specific bbpRegTbSize=0!
21:54:02 kernel: [20414.003959] E2PROM: G Tssi[-4 .. +4] = 255 255 255 255 - 255 -255 255 255 255, step=255, tuning=0
21:54:02 kernel: [20414.008584] E2PROM: A Tssi[-4 .. +4] = 255 255 255 255 - 255 -255 255 255 255, step=255, tuning=0
21:54:02 kernel: [20414.009210] E2PROM: RF FreqOffset=0x29 
21:54:02 kernel: [20414.009218] RTMPSetPhyMode : PhyMode=0, channel=0 
21:54:02 kernel: [20414.009226] country code=129/129, RFIC=5, PHY mode=0, support 13 channels
21:54:02 kernel: [20414.009233] BuildChannel # 1 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009235]  BuildChannel # 2 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009241]  BuildChannel # 3 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009246]  BuildChannel # 4 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009251]  BuildChannel # 5 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009256]  BuildChannel # 6 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009261]  BuildChannel # 7 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009266]  BuildChannel # 8 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009271]  BuildChannel # 9 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009277]  BuildChannel # 10 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009282]  BuildChannel # 11 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009287]  BuildChannel # 12 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009292]  BuildChannel # 13 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.009297]  RTMPSetPhyMode: channel is out of range, use first channel=1 
21:54:02 kernel: [20414.016081] Txpower per Rate
21:54:02 kernel: [20414.016831] Gpwrdelta = 1, Apwrdelta = 0 .
21:54:02 kernel: [20414.018579] 20MHz BW, 2.4G band-88886666,  Adata = 88886666,  Gdata = 77775555 
21:54:02 kernel: [20414.020229] 20MHz BW, 2.4G band-77776677,  Adata = 77776677,  Gdata = 66665566 
21:54:02 kernel: [20414.021705] 20MHz BW, 2.4G band-aaaa5566,  Adata = aaaa5566,  Gdata = 99994455 
21:54:02 kernel: [20414.023330] 20MHz BW, 2.4G band-aaaa6688,  Adata = aaaa6688,  Gdata = 99995577 
21:54:02 kernel: [20414.024954] 20MHz BW, 2.4G band-ffff6688,  Adata = ffff6688,  Gdata = eeee5577 
21:54:02 kernel: [20414.025579] <-- NICReadEEPROMParameters
21:54:02 kernel: [20414.025584] 3. Phy Mode = 0
21:54:02 kernel: [20414.025588] --> NICInitAsicFromEEPROM
21:54:02 kernel: [20414.060963] RTMPFilterCalibration - CaliBW20RfR24=0x8, CaliBW40RfR24=0x27
21:54:02 kernel: [20414.063836] RTMPSetLED::Mode=10,HighByte=0x20,LowByte=0x0a
21:54:02 kernel: [20414.067323] NICInitAsicFromEEPROM: pAd->TxPowerCtrl.bInternalTxALC = 0
21:54:02 kernel: [20414.069079] Use Hw Radio Control Pin=0; if used Pin=0;
21:54:02 kernel: [20414.070576] TxPath = 1, RxPath = 1, RFIC=5, Polar+LED mode=a
21:54:02 kernel: [20414.070578] <-- NICInitAsicFromEEPROM
21:54:02 kernel: [20414.070581] RTMPSetPhyMode : PhyMode=0, channel=1 
21:54:02 kernel: [20414.070584] country code=129/129, RFIC=5, PHY mode=0, support 13 channels
21:54:02 kernel: [20414.070586] BuildChannel # 1 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070587]  BuildChannel # 2 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070590]  BuildChannel # 3 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070592]  BuildChannel # 4 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070594]  BuildChannel # 5 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070596]  BuildChannel # 6 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070598]  BuildChannel # 7 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070600]  BuildChannel # 8 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070602]  BuildChannel # 9 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070604]  BuildChannel # 10 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070606]  BuildChannel # 11 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070608]  BuildChannel # 12 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070610]  BuildChannel # 13 :: Pwr0 = 12, Pwr1 =0, 
21:54:02 kernel: [20414.070612]  MCS Set = 00 00 00 00 00
21:54:02 NetworkManager: <info>  (ra0): preparing device.
21:54:02 NetworkManager: <info>  (ra0): deactivating device (reason: 2).
21:54:02 kernel: [20414.081138] NDIS_STATUS_MEDIA_DISCONNECT Event B!
21:54:02 kernel: [20414.081153] RTUSBBulkReceive!
21:54:02 kernel: [20414.081158] <==== rt28xx_init, Status=0
21:54:02 kernel: [20414.081163] ==> RTMPEnableRxTx
21:54:02 kernel: [20414.081753] <== WRITE DMA offset 0x208 = 0x45
21:54:02 kernel: [20414.082696] <== RTMPEnableRxTx
21:54:02 kernel: [20414.082822] 0x1300 = 00073200
21:54:02 kernel: [20414.082825] Driver auto reconnect to last OID_802_11_SSID setting - , len - 0
21:54:02 kernel: [20414.082890] CntlOidSsidProc():CNTL - 0 BSS of 0 BSS match the desire (0)SSID - 
21:54:02 kernel: [20414.082895] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
21:54:02 kernel: [20414.082982] SCANNING, suspend MSDU transmission ...
21:54:02 kernel: [20414.085430] ==>rt_ioctl_giwmode(mode=0)
21:54:02 kernel: [20414.085442] ===>Set_NetworkType_Proc::(INFRA)
21:54:02 kernel: [20414.085444] Set_NetworkType_Proc::(NetworkType=1)
21:54:02 kernel: [20414.085514] ===>rt_ioctl_giwrange
21:54:02 kernel: [20414.086691] SYNC - BBP R4 to 20MHz.l
21:54:02 kernel: [20414.088059] ===> rt_ioctl_siwpmksa
21:54:02 kernel: [20414.088062] rt_ioctl_siwpmksa - IW_PMKSA_FLUSH
21:54:02 kernel: [20414.088066] ===>Set_NetworkType_Proc::(INFRA)
21:54:02 kernel: [20414.088068] Set_NetworkType_Proc::(NetworkType=1)
21:54:02 kernel: [20414.088077] ===>rt_ioctl_giwrange
21:54:02 kernel: [20414.097047] rt_ioctl_siwauth::IW_AUTH_WPA_ENABLED - Driver supports WPA!(param->value = 1)
21:54:02 kernel: [20414.097826] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
21:54:02 kernel: [20414.097829] 		WCIDAttri = 0x1 
21:54:02 kernel: [20414.097831] AsicRemovePairwiseKeyEntry : Wcid #1 
21:54:02 kernel: [20414.097832] AsicRemoveSharedKeyEntry: #0 
21:54:02 kernel: [20414.098070] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
21:54:02 kernel: [20414.098572] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8401)
21:54:02 kernel: [20414.099068] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
21:54:02 kernel: [20414.099071] 		WCIDAttri = 0x1 
21:54:02 kernel: [20414.099073] AsicRemovePairwiseKeyEntry : Wcid #1 
21:54:02 kernel: [20414.099074] AsicRemoveSharedKeyEntry: #1 
21:54:02 kernel: [20414.099320] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
21:54:02 kernel: [20414.099828] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8402)
21:54:02 kernel: [20414.100320] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
21:54:02 kernel: [20414.100322] 		WCIDAttri = 0x1 
21:54:02 kernel: [20414.100324] AsicRemovePairwiseKeyEntry : Wcid #1 
21:54:02 kernel: [20414.100326] AsicRemoveSharedKeyEntry: #2 
21:54:02 kernel: [20414.100570] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
21:54:02 kernel: [20414.101320] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8403)
21:54:02 kernel: [20414.101821] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
21:54:02 kernel: [20414.101823] 		WCIDAttri = 0x1 
21:54:02 kernel: [20414.101825] AsicRemovePairwiseKeyEntry : Wcid #1 
21:54:02 kernel: [20414.101827] AsicRemoveSharedKeyEntry: #3 
21:54:02 kernel: [20414.102074] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
21:54:02 kernel: [20414.102577] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8404)
21:54:02 kernel: [20414.102584] rt_ioctl_siwauth::IW_AUTH_DROP_UNENCRYPTED - param->value = 1!
21:54:02 kernel: [20414.102588] ===> rt_ioctl_siwpmksa
21:54:02 kernel: [20414.102590] rt_ioctl_siwpmksa - IW_PMKSA_FLUSH
21:54:02 NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
21:54:02 NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 42)
21:54:02 kernel: [20414.105579] SwitchChannel#1(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
21:54:02 kernel: [20414.106162] rt_ioctl_giwscan:: Still scanning
21:54:02 kernel: [20414.106229] !!! MLME busy, reset MLME state machine !!!
21:54:02 kernel: [20414.110333] !!! reset MLME state machine !!!
21:54:02 kernel: [20414.110337] MlmeRestartStateMachine 
21:54:02 kernel: [20414.119325] SwitchChannel#1(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
21:54:02 kernel: [20414.123565] SCAN done, resume MSDU transmission ...
21:54:02 kernel: [20414.124052] SCANNING, suspend MSDU transmission ...
21:54:02 kernel: [20414.125829] SYNC - BBP R4 to 20MHz.l
21:54:02 kernel: [20414.134209] SwitchChannel#1(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
21:54:03 kernel: [20414.286827] SwitchChannel#2(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x07, R=0x02
21:54:03 kernel: [20414.436713] SwitchChannel#3(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF2, K=0x02, R=0x02
21:54:03 kernel: [20414.589462] SwitchChannel#4(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF2, K=0x07, R=0x02
21:54:03 kernel: [20414.740330] SwitchChannel#5(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF3, K=0x02, R=0x02
21:54:03 kernel: [20414.888713] SwitchChannel#6(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF3, K=0x07, R=0x02
21:54:03 kernel: [20415.040712] SwitchChannel#7(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF4, K=0x02, R=0x02
21:54:03 kernel: [20415.192837] SwitchChannel#8(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF4, K=0x07, R=0x02
21:54:04 kernel: [20415.346092] SwitchChannel#9(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF5, K=0x02, R=0x02
21:54:04 avahi-daemon[899]: Registering new address record for fe80::1eaf:f7ff:fe6d:67e on ra0.*.
21:54:04 kernel: [20415.498212] SwitchChannel#10(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF5, K=0x07, R=0x02
21:54:04 kernel: [20415.652342] SwitchChannel#11(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF6, K=0x02, R=0x02
21:54:04 kernel: [20415.805838] SwitchChannel#12(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF6, K=0x07, R=0x02
21:54:04 kernel: [20415.958337] SwitchChannel#13(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF7, K=0x02, R=0x02
21:54:04 kernel: [20416.113087] SwitchChannel#1(RF=5, Pwr0=12, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
21:54:04 kernel: [20416.117333] SYNC - End of SCAN, restore to channel 1, Total BSS[08]
21:54:04 kernel: [20416.117354] SCAN done, resume MSDU transmission ...
21:54:04 kernel: [20416.117448] rt_ioctl_giwscan:: Still scanning
```

Still no networks in the list.

---

### Post by chili555 on 2010-10-26
Well, that did no good. Let's restore the original, but keep an unedited copy in case we need one:```
sudo cp /etc/Wireless/RT2870STA/RT2870STA.dat.bak /etc/Wireless/RT2870STA/RT2870STA.dat
```Using the cp command, meaning copy, leaves a copy called .bak intact.

Next, I'd suggest you amend it to add the details of your own network, especially these:```
SSID=[COLOR="Red"]11n-AP[/COLOR]
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=[COLOR="Red"]OPEN[/COLOR]
EncrypType=[COLOR="Red"]NONE[/COLOR]
WPAPSK=[COLOR="Red"]???[/COLOR]

```Consult the README for further details.

Remove and reinsert the module:```
sudo rmmod -f rt2870sta && sudo modprobe rt2870sta
```

Did you try the native built-in rt2870sta?

---

### Post by aneganov on 2010-10-27
Still no success.

I stopped NM at all and tried to bring up the wireless interfaces manually. 
This is my setup from /etc/network/interfaces:

```
iface ra0 inet static # DWA-125
    address 192.168.1.10
    netmask 255.255.255.0
    wireless-essid XNet
    wireless-key s:passwordddddd

iface wlan0 inet static # Builtin Intel wireless
    address 192.168.1.2
    netmask 255.255.255.0
    wireless-essid XNet
    wireless-key s:passwordddddd

```
Then, I tried ifup'ing them:
```

ifup wlan0
ifup ra0

```
both interfaces gain static IPs, but only one (wlan0) actually working and connecting to AP.
Here is the output of iwconfig:

```

$ifconfig wlan0

wlan0     IEEE 802.11abg  ESSID:"XNet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:D1:59:EF:CF   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ifconfig ra0

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

As you can see, ESSID isn't changed properly and no any connection is establed. Same happens if I try to change essid using classic iwconfig:
```

iwconfig ra0 essid "XNet"

```
-- after this command, ESSID is still 11n-AP. 

I also tried to clean up RT2870STA.dat, leaving ony the "Default" there, but this didn't help. The only way to change ESSID is to set it in RT2870STA.dat or (I guess) is using iwpriv (but not tested).


Yesterday I'd tested the device on a Windows machine - works perfectly. 

So the device just doesn't work on Linux. Is this problem with driver or with how I compiled it - don't know. 
This is my config.mk:

```

# Support ATE function
HAS_ATE=n

# Support ATE NEW TXCONT solution
# NOTE : RT2xxx does not support this feature !
HAS_NEW_TXCONT=n

# Support QA ATE function
HAS_QA_SUPPORT=y

HAS_RSSI_FEEDBACK=n

# Support XLINK mode
HAS_XLINK=n


HAS_NINTENDO=n

# Support LLTD function
HAS_LLTD=n

# Support WDS function
HAS_WDS=n

# Support AP-Client function
HAS_APCLI=n

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

#Support Net interface block while Tx-Sw queue full
HAS_BLOCK_NET_IF=n

#Support IGMP-Snooping function.
HAS_IGMP_SNOOP_SUPPORT=n

#Support DFS function
HAS_DFS_SUPPORT=n

#Support Carrier-Sense function
HAS_CS_SUPPORT=n


# Support user specific transmit rate of Multicast packet.
HAS_MCAST_RATE_SPECIFIC_SUPPORT=n

# Support for Multiple Cards
HAS_MC_SUPPORT=n

#Support for PCI-MSI
HAS_MSI_SUPPORT=n


#Support for IEEE802.11e DLS
HAS_QOS_DLS_SUPPORT=n

#Support for EXT_CHANNEL
HAS_EXT_BUILD_CHANNEL_LIST=n

#Support for IDS 
HAS_IDS_SUPPORT=n


#Support for Net-SNMP
HAS_SNMP_SUPPORT=n

#Support features of 802.11n Draft3
HAS_DOT11N_DRAFT3_SUPPORT=y

#Support features of Single SKU. 
HAS_SINGLE_SKU_SUPPORT=n

#Support features of 802.11n
HAS_DOT11_N_SUPPORT=y



#Support for 2860/2880 co-exist 
HAS_RT2880_RT2860_COEXIST=n

HAS_KTHREAD_SUPPORT=n




#Support for Auto channel select enhance
HAS_AUTO_CH_SELECT_ENHANCE=n

#Support statistics count
HAS_STATS_COUNT=n


#Support Antenna Diversity
HAS_ANTENNA_DIVERSITY_SUPPORT=n

#Client support WDS function
HAS_CLIENT_WDS_SUPPORT=n

#Support for Bridge Fast Path & Bridge Fast Path function open to other module
HAS_BGFP_SUPPORT=n
HAS_BGFP_OPEN_SUPPORT=n

# Support HOSTAPD function
HAS_HOSTAPD_SUPPORT=n

#Support GreenAP function
HAS_GREENAP_SUPPORT=n

#Support MAC80211 LINUX-only function
HAS_CFG80211_SUPPORT=n

#Support RFKILL hardware block/unblock LINUX-only function
HAS_RFKILL_HW_SUPPORT=n



HAS_RTMP_FLASH_SUPPORT=n

HAS_RESOURCE_PRE_ALLOC=n

```

---

### Post by chili555 on 2010-10-27
I guess I don't understand why you want two wireless cards connected with IP addresses at the same time. I could certainly understand one IP address from the router and an ad-hoc connection to another computer in internet connection sharing. 

Did you try the Ralink only?

Did you try the native built-in rt2870sta?

---

### Post by aneganov on 2010-10-27
> **chili555 said:**
> I guess I don't understand why you want two wireless cards connected with IP addresses at the same time. I could certainly understand one IP address from the router and an ad-hoc connection to another computer in internet connection sharing. 

I don't want DWA-125, just getting it working to then move to another Ubuntu 10.04 (my mother's computer)

> Did you try the Ralink only?

Yes

> Did you try the native built-in rt2870sta?

There is no such a native built-ins since DWA-125 is not using 2870, it has 3070 in it.

---

### Post by chili555 on 2010-10-27
> DWA-125 is not using 2870, it has 3070 in it.```
$ modinfo rt2870sta
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/[COLOR="Red"]RT3070[/COLOR] Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       [COLOR="Red"]rt3070.bin[/COLOR]
firmware:       rt2870.bin
```If you are ready to try, I am ready to help. Please post lsusb so we can see if the usb.id is 07d1:3c0d.

---

### Post by aneganov on 2010-10-27
> **chili555 said:**
> If you are ready to try, I am ready to help. Please post lsusb so we can see if the usb.id is 07d1:3c0d.

Of course I'm ready. Will try later - in 10-20 minutes.
Now I want to mention, that I started to playing with Ralink because my Ubuntu haven't recognized DWA-125. Which means usually, driver doesn't support the chip.

UPD.
The output:

```

$ lsusb | grep -v hub
Bus 008 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 008 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 003 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
**Bus 002 Device 019: ID 07d1:3c16 D-Link System **
Bus 002 Device 012: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 003: ID 064e:a117 Suyin Corp. 

```

So it is **07d1:3c16**, not **07d1:3c0d**

P.S. Chili, thank you for the help. I appreciate it very much actually!

---

### Post by chili555 on 2010-10-27
Here are the steps. First, remove the device from the USB port. Next, open a terminal and navigate to the directory where you compiled the driver, for example:```
cd Desktop/RalinkDriverFile
sudo make uninstall
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba rt2870sta"

```Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread twice, save and close gedit.

Now, I suggest you temporarily disable the built-in wireless:```
sudo ifconfig wlan0 down
```Re-insert the D-link. Is it working? Do you see networks in Network Manager?

---

### Post by aneganov on 2010-10-27
> **chili555 said:**
> Re-insert the D-link. Is it working? Do you see networks in Network Manager?

You are magician, Chili! It works!
How did you know they (2870 and 3370) are just same so that same driver is able to operate them?

---

### Post by chili555 on 2010-10-27
> How did you know they (2870 and 3370) are just same so that same driver is able to operate them?Oh, I guess just about ten years of experience in Linux and thousands of solved threads. 

I suggest you print off my instructions and head on over to mom's computer and make her a happy Ubuntu user. My wife loves it!

Have fun. I'm very glad it's working.

---

### Post by ario on 2010-10-28
Looks like I missed a lot! After all did you guys figured out how to enable WPA encryption mode or just used WEP modes? If you used WPA successfully was it on an Ad-Hoc network or an Infrastructure one?
Thanks.

---

### Post by chili555 on 2010-10-28
Is your router or ad-hoc network set for WPA ***and*** WPA2? Lots of drivers have trouble with mixed mode. Try setting up for WPA or WPA2; not both.

---

### Post by ario on 2010-10-30
> **chili555 said:**
> Try setting up for WPA or WPA2; not both.

I just used network-manager applet to setup an Ad-Hoc network.
Settings were:
[INDENT]connection name: something
SSID: something
Mode: Ad-hoc
IPv4: some manual numbers
IPv6: Ignore
Wireless Security: The only WPA options there were WPA **&** WPA2 Personal and Enterprise. Which won't work at all. Guess that must be the problem.[/INDENT]
There was no option for WPA or WPA2 only.
How can I try setting up that?
Thanks in advance.

---

### Post by ario on 2010-11-01
Bump!

---

### Post by ario on 2010-11-09
Bump!

---

### Post by ario on 2010-11-16
Bumpity Bump!

---

### Post by moonkitten on 2010-11-24
I'm completely new to ubuntu.:KS I have no idea how to do anything. I was able to make this work for my dlink dwa-125 on ubuntu 10.10. These instructions are so easy for me to use. THANKS a million. I now have wireless access. 

:P

***Next stop I'm trying to get perfect world installed on my machine. Searching the forums now!***

---

### Post by druminus on 2010-11-27
Hello.

I've tried a lot of instructions to make dwa 125 work.
I've got 07d1:3c0d version and kubuntu maverick.
I want to make this adapter work on maverick and then move it to another computer with kubuntu lucid.

Well, kubuntu finds device and using rt2870sta (there is no rt3070sta in maverick, looks like they were merged), but network manager says that "driver does not support SSID scans". 
It's strange, because I can scan networks with: 
```

ifconfig wlan0 up
iwlist wlan0 scan

```

That's my syslog after I connect adapater:
```


Nov 27 18:19:13 afbook kernel: [21056.572646] usb 2-3: new high speed USB device using ehci_hcd and address 17
Nov 27 18:19:13 afbook kernel: [21056.741684] === pAd = ffffc900058d2000, size = 504952 ===
Nov 27 18:19:13 afbook kernel: [21056.741692] <-- RTMPAllocAdapterBlock, Status=0
Nov 27 18:19:13 afbook NetworkManager[1234]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/net/wlan0, iface: wlan0)
Nov 27 18:19:13 afbook NetworkManager[1234]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 27 18:19:13 afbook NetworkManager[1234]: <error> [1290871153.598638] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
Nov 27 18:19:13 afbook NetworkManager[1234]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Nov 27 18:19:13 afbook NetworkManager[1234]: <info> (wlan0): new 802.11 WiFi device (driver: 'usb' ifindex: 19)
Nov 27 18:19:13 afbook NetworkManager[1234]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/14
Nov 27 18:19:13 afbook NetworkManager[1234]: <info> (wlan0): now managed
Nov 27 18:19:13 afbook NetworkManager[1234]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Nov 27 18:19:13 afbook NetworkManager[1234]: <info> (wlan0): bringing up device.
Nov 27 18:19:13 afbook NetworkManager[1234]: <info> (wlan0): deactivating device (reason: 2).
Nov 27 18:19:13 afbook NetworkManager[1234]: <error> [1290871153.599365] [nm-device-wifi.c:1542] nm_device_wifi_set_mode(): (wlan0): error setting mode 2

```

I think that line 
```

<error> [1290871153.598638] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)

```
 is strange too, because ifconfig says:
```

wlan0     Link encap:Ethernet  HWaddr 1c:af:f7:06:3d:2c
...

```

So, how can I make this adapter work?

---

### Post by chili555 on 2010-11-27
You might start at post #126 here: [http://ubuntuforums.org/showthread.php?t=1625657&page=13](http://ubuntuforums.org/showthread.php?t=1625657&page=13)

You must have *build-essential* and *linux-headers-generic *installed.

Post back if you get stuck.

---

### Post by druminus on 2010-11-27
I've tried to build v2.1.2.0 (from dlink ftp) and v2.4.0.1 (from Ralink) and make fails:

```

$ LANG=C make
make -C tools
make[1]: Entering directory `/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools'
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.35-23-generic/build SUBDIRS=/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c: In function 'NICInitRecv':
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function 'usb_buffer_alloc'
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function 'usb_buffer_free'
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c: In function 'NICInitTransmit':
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:219: warning: cast to pointer from integer of different size
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:306: warning: cast to pointer from integer of different size
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:324: warning: cast to pointer from integer of different size
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:341: warning: cast to pointer from integer of different size
/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:357: warning: cast to pointer from integer of different size
make[2]: *** [/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/afunix/opt/src/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [LINUX] Error 2

```

---

### Post by chili555 on 2010-11-27
> 2009_1204_RT3070_Linux_STA_v2.1.2.0Please toss that old antique away. I'd love to see your result from 2.4.0.1 built as sudo su.

---

### Post by druminus on 2010-11-27
ok. so there is 2 drivers at Ralink:
2010_0709_RT2870_Linux_STA_v2.4.0.1 and  2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO.

I've tried to build 2.4.0.1 with no luck, but 2.4.0.1_DPO was built, but networkmanager still fails to manage device:
```

Nov 28 00:53:57 afbook kernel: [44740.242565] usb 2-1: new high speed USB device using ehci_hcd and address 26
Nov 28 00:53:57 afbook kernel: [44740.411219] ===>rt2870_probe()!
Nov 28 00:53:57 afbook kernel: [44740.411223] --> RTMPAllocAdapterBlock
Nov 28 00:53:57 afbook kernel: [44740.411433] 
Nov 28 00:53:57 afbook kernel: [44740.411434] 
Nov 28 00:53:57 afbook kernel: [44740.411435] === pAd = ffffc90005d16000, size = 545880 ===
Nov 28 00:53:57 afbook kernel: [44740.411436] 
Nov 28 00:53:57 afbook kernel: [44740.411500] <-- RTMPAllocAdapterBlock, Status=0
Nov 28 00:53:57 afbook kernel: [44740.411503] NumEndpoints=7
Nov 28 00:53:57 afbook kernel: [44740.411505] BULK IN MaxPacketSize = 512
Nov 28 00:53:57 afbook kernel: [44740.411507] EP address = 0x81
Nov 28 00:53:57 afbook kernel: [44740.411508] BULK OUT MaxPacketSize = 512
Nov 28 00:53:57 afbook kernel: [44740.411510] EP address = 0x 1  
Nov 28 00:53:57 afbook kernel: [44740.411512] BULK OUT MaxPacketSize = 512
Nov 28 00:53:57 afbook kernel: [44740.411514] EP address = 0x 2  
Nov 28 00:53:57 afbook kernel: [44740.411515] BULK OUT MaxPacketSize = 512
Nov 28 00:53:57 afbook kernel: [44740.411517] EP address = 0x 3  
Nov 28 00:53:57 afbook kernel: [44740.411519] BULK OUT MaxPacketSize = 512
Nov 28 00:53:57 afbook kernel: [44740.411521] EP address = 0x 4  
Nov 28 00:53:57 afbook kernel: [44740.411523] BULK OUT MaxPacketSize = 512
Nov 28 00:53:57 afbook kernel: [44740.411524] EP address = 0x 5  
Nov 28 00:53:57 afbook kernel: [44740.411526] BULK OUT MaxPacketSize = 512
Nov 28 00:53:57 afbook kernel: [44740.411528] EP address = 0x 6  
Nov 28 00:53:57 afbook kernel: [44740.411530] STA Driver version-2.4.0.1
Nov 28 00:53:57 afbook kernel: [44740.411798] NVM is EFUSE
Nov 28 00:53:57 afbook kernel: [44740.411802] Allocate a net device with private data size=0!
Nov 28 00:53:57 afbook kernel: [44740.411815] Allocate net device ops success!
Nov 28 00:53:57 afbook kernel: [44740.411819] The name of the new ra interface is ra0...
Nov 28 00:53:57 afbook kernel: [44740.411821] RtmpOSNetDevAttach()--->
Nov 28 00:53:57 afbook kernel: [44740.412553] <---RtmpOSNetDevAttach(), ret=0
Nov 28 00:53:57 afbook kernel: [44740.414674] <===rt2870_probe()!
Nov 28 00:53:57 afbook kernel: [44740.428653] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Nov 28 00:53:57 afbook kernel: [44740.435896] rtusb init --->
Nov 28 00:53:57 afbook kernel: [44740.435904] Error: Driver 'rt2870' is already registered, aborting...
Nov 28 00:53:57 afbook NetworkManager[1234]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/net/ra0, iface: ra0)
Nov 28 00:53:57 afbook NetworkManager[1234]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/net/ra0, iface: ra0): no ifupdown configuration found.
Nov 28 00:53:57 afbook NetworkManager[1234]: <error> [1290894837.289455] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Nov 28 00:53:57 afbook NetworkManager[1234]: <info> (ra0): driver does not support SSID scans (scan_capa 0x00).
Nov 28 00:53:57 afbook NetworkManager[1234]: <info> (ra0): new 802.11 WiFi device (driver: 'usb' ifindex: 31)
Nov 28 00:53:57 afbook NetworkManager[1234]: <info> (ra0): exported as /org/freedesktop/NetworkManager/Devices/21
Nov 28 00:53:57 afbook NetworkManager[1234]: <info> (ra0): now managed
Nov 28 00:53:57 afbook NetworkManager[1234]: <info> (ra0): device state change: 1 -> 2 (reason 2)
Nov 28 00:53:57 afbook NetworkManager[1234]: <info> (ra0): bringing up device.
Nov 28 00:53:57 afbook NetworkManager[1234]: <info> (ra0): deactivating device (reason: 2).
Nov 28 00:53:57 afbook NetworkManager[1234]: <warn> (ra0): error -55281948 getting card mode
Nov 28 00:53:57 afbook NetworkManager[1234]: <error> [1290894837.290134] [nm-device-wifi.c:1542] nm_device_wifi_set_mode(): (ra0): error setting mode 2
Nov 28 00:53:57 afbook kernel: [44740.480737] ===>rt_ioctl_giwrange
Nov 28 00:53:57 afbook kernel: [44740.480749] INFO::Network is down!
Nov 28 00:53:57 afbook kernel: [44740.480857] ===>rt_ioctl_giwrange
Nov 28 00:53:57 afbook kernel: [44740.481414] INFO::Network is down!
Nov 28 00:53:57 afbook kernel: [44740.481444] INFO::Network is down!
Nov 28 00:53:57 afbook NetworkManager[1234]: <warn> (ra0): error -55281948 getting card mode
Nov 28 00:53:57 afbook kernel: [44740.522953] INFO::Network is down!
Nov 28 00:53:57 afbook NetworkManager[1234]: <warn> (ra0): error -55281948 getting card mode
Nov 28 00:53:57 afbook kernel: [44740.537620] INFO::Network is down!

```

NM still says:
```

NetworkManager[1234]: <error> [1290894837.289455] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)

```
and
```

NetworkManager[1234]: <info> (ra0): driver does not support SSID scans (scan_capa 0x00).

```

But I can still scan networks with iwlist.

---

### Post by chili555 on 2010-11-27
> Error: Driver 'rt2870' is already registered, aborting...
This bothers me. Did you have ndiswrapper installed or do you believe the old driver was still loaded? What does this tell us?```
cat /etc/Wireless/RT2870STA/RT2870STA.dat
```I'm not interested in seeing the whole file; just that it exists with a lot of lines. Can you confirm that you made the changes to os/linux/config.mk to have NM manage your device? Are there conflicting drivers loaded?```
lsmod | grep rt2
```Is */etc/network/interfaces* empty except the loopback stanza?

---

### Post by druminus on 2010-11-27
> **chili555 said:**
> This bothers me. Did you have ndiswrapper installed or do you believe the old driver was still loaded? 
Ooops. I've forgot about /etc/udev.d/network_drivers.rules from another instructions. So I have commented out lines in /etc/udev.d/network_drivers.rules and /etc/modprobe.d/network_drivers.conf. I've restarted udev.

> What does this tell us?```
cat /etc/Wireless/RT2870STA/RT2870STA.dat
```I'm not interested in seeing the whole file; just that it exists with a lot of lines. 


I've tried with that strange config file and without it.
I've tried default one and tried to fill config with my AP settings. Nothing changed.

> 
Can you confirm that you made the changes to os/linux/config.mk to have NM manage your device? 


```

$ grep WPA_SUPPLICANT os/linux/config.mk
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
...

```

Is there any other options I have to change?

> 
Are there conflicting drivers loaded?```
lsmod | grep rt2
```

Now drivers are:
```

# lsmod | grep rt2
# lsmod | grep rt3
rt3370sta             660062  0 

```


> 
Is */etc/network/interfaces* empty except the loopback stanza?

```

$ grep -v -r '^#' /etc/network/interfaces 

auto lo
iface lo inet loopback



iface bnep0 inet dhcp
        hostname        afbook
        pre-up          /usr/bin/pand -c 00:15:B7:48:F7:C1 -n; sleep 1
        post-down       /usr/bin/pand -k 00:15:B7:48:F7:C1 -n

```

After deleting udev rule syslog still says:
```

Nov 28 01:26:31 afbook kernel: [46694.592679] usb 2-1: new high speed USB device using ehci_hcd and address 32
Nov 28 01:26:31 afbook kernel: [46694.758877] ===>rt2870_probe()!
Nov 28 01:26:31 afbook kernel: [46694.758885] --> RTMPAllocAdapterBlock
Nov 28 01:26:31 afbook kernel: [46694.759259] 
Nov 28 01:26:31 afbook kernel: [46694.759261] 
Nov 28 01:26:31 afbook kernel: [46694.759263] === pAd = ffffc90005d16000, size = 545880 ===
Nov 28 01:26:31 afbook kernel: [46694.759265] 
Nov 28 01:26:31 afbook kernel: [46694.759403] <-- RTMPAllocAdapterBlock, Status=0
Nov 28 01:26:31 afbook kernel: [46694.759408] NumEndpoints=7
Nov 28 01:26:31 afbook kernel: [46694.759412] BULK IN MaxPacketSize = 512
Nov 28 01:26:31 afbook kernel: [46694.759417] EP address = 0x81
Nov 28 01:26:31 afbook kernel: [46694.759420] BULK OUT MaxPacketSize = 512
Nov 28 01:26:31 afbook kernel: [46694.759425] EP address = 0x 1  
Nov 28 01:26:31 afbook kernel: [46694.759428] BULK OUT MaxPacketSize = 512
Nov 28 01:26:31 afbook kernel: [46694.759433] EP address = 0x 2  
Nov 28 01:26:31 afbook kernel: [46694.759436] BULK OUT MaxPacketSize = 512
Nov 28 01:26:31 afbook kernel: [46694.759440] EP address = 0x 3  
Nov 28 01:26:31 afbook kernel: [46694.759444] BULK OUT MaxPacketSize = 512
Nov 28 01:26:31 afbook kernel: [46694.759448] EP address = 0x 4  
Nov 28 01:26:31 afbook kernel: [46694.759452] BULK OUT MaxPacketSize = 512
Nov 28 01:26:31 afbook kernel: [46694.759456] EP address = 0x 5  
Nov 28 01:26:31 afbook kernel: [46694.759460] BULK OUT MaxPacketSize = 512
Nov 28 01:26:31 afbook kernel: [46694.759463] EP address = 0x 6  
Nov 28 01:26:31 afbook kernel: [46694.759468] STA Driver version-2.4.0.1
Nov 28 01:26:31 afbook kernel: [46694.759709] NVM is EFUSE
Nov 28 01:26:31 afbook kernel: [46694.759717] Allocate a net device with private data size=0!
Nov 28 01:26:31 afbook kernel: [46694.759743] Allocate net device ops success!
Nov 28 01:26:31 afbook kernel: [46694.759750] The name of the new ra interface is ra0...
Nov 28 01:26:31 afbook kernel: [46694.759756] RtmpOSNetDevAttach()--->
Nov 28 01:26:31 afbook kernel: [46694.761509] <---RtmpOSNetDevAttach(), ret=0
Nov 28 01:26:31 afbook kernel: [46694.763820] <===rt2870_probe()!
Nov 28 01:26:31 afbook NetworkManager[1234]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/net/ra0, iface: ra0)
Nov 28 01:26:31 afbook NetworkManager[1234]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/net/ra0, iface: ra0): no ifupdown configuration found.
Nov 28 01:26:31 afbook NetworkManager[1234]: <error> [1290896791.595869] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Nov 28 01:26:31 afbook NetworkManager[1234]: <info> (ra0): driver does not support SSID scans (scan_capa 0x00).
Nov 28 01:26:31 afbook NetworkManager[1234]: <info> (ra0): new 802.11 WiFi device (driver: 'usb' ifindex: 37)
Nov 28 01:26:31 afbook NetworkManager[1234]: <info> (ra0): exported as /org/freedesktop/NetworkManager/Devices/27
Nov 28 01:26:31 afbook NetworkManager[1234]: <info> (ra0): now managed
Nov 28 01:26:31 afbook NetworkManager[1234]: <info> (ra0): device state change: 1 -> 2 (reason 2)
Nov 28 01:26:31 afbook NetworkManager[1234]: <info> (ra0): bringing up device.
Nov 28 01:26:31 afbook NetworkManager[1234]: <info> (ra0): deactivating device (reason: 2).
Nov 28 01:26:31 afbook NetworkManager[1234]: <warn> (ra0): error -55281948 getting card mode
Nov 28 01:26:31 afbook kernel: [46694.787148] ===>rt_ioctl_giwrange
Nov 28 01:26:31 afbook kernel: [46694.787160] INFO::Network is down!
Nov 28 01:26:31 afbook kernel: [46694.787274] ===>rt_ioctl_giwrange
Nov 28 01:26:31 afbook kernel: [46694.787841] INFO::Network is down!
Nov 28 01:26:31 afbook kernel: [46694.787869] INFO::Network is down!
Nov 28 01:26:31 afbook NetworkManager[1234]: <error> [1290896791.596562] [nm-device-wifi.c:1542] nm_device_wifi_set_mode(): (ra0): error setting mode 2
Nov 28 01:26:31 afbook NetworkManager[1234]: <warn> (ra0): error -55281948 getting card mode
Nov 28 01:26:31 afbook kernel: [46694.845245] INFO::Network is down!
Nov 28 01:26:31 afbook NetworkManager[1234]: <warn> (ra0): error -55281948 getting card mode
Nov 28 01:26:31 afbook kernel: [46694.854737] INFO::Network is down!


```

---

### Post by chili555 on 2010-11-27
Is Network Manager refusing to use your wireless in deference to wired? Can you please detach the ethernet cable, tell us if you see your network in the NM icon and let us see the relevant syslog post-01:26:31? Thanks.

PS-Dinner date soon; my replies will be later.

---

### Post by druminus on 2010-11-27
> **chili555 said:**
> Is Network Manager refusing to use your wireless in deference to wired? Can you please detach the ethernet cable, tell us if you see your network in the NM icon

Tried with wired network and without it -- no luck.

NetworkManager plasmoid says that "Wireless network" is "unavailable". It also has 2 checkbox to enable/disable wired and wireless networks. Checkbox for wired network is enabled and checked. Checkbox for wireless network is disabled (in gray colors) and unchecked.
It's seems normal, as NetworkManager says in syslog "deactivating device (reason: 2)"

> 
and let us see the relevant syslog post-01:26:31? Thanks.


after 01:26:31 I've unplugged device, so syslog says:
```

Nov 28 01:31:11 afbook kernel: [46974.486329] usb 2-1: USB disconnect, address 32
Nov 28 01:31:11 afbook kernel: [46974.486544] rtusb_disconnect: unregister usbnet usb-0000:00:1d.7-1
Nov 28 01:31:11 afbook kernel: [46974.486553] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
Nov 28 01:31:11 afbook NetworkManager[1234]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/net/ra0, iface: ra0)
Nov 28 01:31:11 afbook NetworkManager[1234]: <info> (ra0): now unmanaged
Nov 28 01:31:11 afbook NetworkManager[1234]: <info> (ra0): device state change: 2 -> 1 (reason 36)
Nov 28 01:31:11 afbook kernel: [46974.531233]  RTUSB disconnect successfully

```

There is no other lines between 01:26:31 and 01:31:11.

---

### Post by druminus on 2010-11-27
Wow!
I'm experimenting with DWA-125 on my laptop with wifi module and I've disabled it with rfkill switch.

But I've just tried to turn it on and then plug DWA-125 in.
DWA-125 starts blinking. Logs are full of messages -- it looks like DWA tries to scan channels.
But it does not find anything. Status of device in NetworkManager plasmoid is "Not connected" and there is no networks found in ra0's network list (my built-in wifi module finds 3 networks).

Now syslog says:
```

Nov 28 02:09:49 afbook kernel: [49292.626070] rt_ioctl_giwscan:: Still scanning
Nov 28 02:09:50 afbook kernel: [49293.984144] rt28xx_get_wireless_stats --->
Nov 28 02:09:50 afbook kernel: [49293.984148] <--- rt28xx_get_wireless_stats
Nov 28 02:09:52 afbook kernel: [49295.970280] rt28xx_get_wireless_stats --->
Nov 28 02:09:52 afbook kernel: [49295.970287] <--- rt28xx_get_wireless_stats
Nov 28 02:09:54 afbook kernel: [49297.969627] rt28xx_get_wireless_stats --->
Nov 28 02:09:54 afbook kernel: [49297.969634] <--- rt28xx_get_wireless_stats
Nov 28 02:09:56 afbook kernel: [49299.969692] rt28xx_get_wireless_stats --->
Nov 28 02:09:56 afbook kernel: [49299.969699] <--- rt28xx_get_wireless_stats
Nov 28 02:09:58 afbook kernel: [49301.970201] rt28xx_get_wireless_stats --->
Nov 28 02:09:58 afbook kernel: [49301.970208] <--- rt28xx_get_wireless_stats
Nov 28 02:10:00 afbook kernel: [49303.969959] rt28xx_get_wireless_stats --->
Nov 28 02:10:00 afbook kernel: [49303.969967] <--- rt28xx_get_wireless_stats
Nov 28 02:10:02 afbook kernel: [49305.969862] rt28xx_get_wireless_stats --->
Nov 28 02:10:02 afbook kernel: [49305.969870] <--- rt28xx_get_wireless_stats
Nov 28 02:10:04 afbook kernel: [49307.969666] rt28xx_get_wireless_stats --->
Nov 28 02:10:04 afbook kernel: [49307.969670] <--- rt28xx_get_wireless_stats
Nov 28 02:10:06 afbook kernel: [49309.969542] rt28xx_get_wireless_stats --->
Nov 28 02:10:06 afbook kernel: [49309.969546] <--- rt28xx_get_wireless_stats
Nov 28 02:10:08 afbook kernel: [49311.969896] rt28xx_get_wireless_stats --->
Nov 28 02:10:08 afbook kernel: [49311.969903] <--- rt28xx_get_wireless_stats
Nov 28 02:10:10 afbook kernel: [49313.970405] rt28xx_get_wireless_stats --->
Nov 28 02:10:10 afbook kernel: [49313.970413] <--- rt28xx_get_wireless_stats
Nov 28 02:10:12 afbook kernel: [49315.970156] rt28xx_get_wireless_stats --->
Nov 28 02:10:12 afbook kernel: [49315.970163] <--- rt28xx_get_wireless_stats
Nov 28 02:10:14 afbook kernel: [49317.970262] rt28xx_get_wireless_stats --->
Nov 28 02:10:14 afbook kernel: [49317.970269] <--- rt28xx_get_wireless_stats
Nov 28 02:10:16 afbook kernel: [49319.969862] rt28xx_get_wireless_stats --->
Nov 28 02:10:16 afbook kernel: [49319.969869] <--- rt28xx_get_wireless_stats
Nov 28 02:10:17 afbook kernel: [49320.193780] !!! WpaSupplicantScanCount > 3
Nov 28 02:10:17 afbook kernel: [49320.666915] Driver auto reconnect to last OID_802_11_SSID setting - 11n-AP, len - 6
Nov 28 02:10:17 afbook kernel: [49320.667041] CntlOidSsidProc():CNTL - 0 BSS of 2 BSS match the desire (6)SSID - 11n-AP
Nov 28 02:10:17 afbook kernel: [49320.667052] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
Nov 28 02:10:17 afbook kernel: [49320.667211] SCANNING, suspend MSDU transmission ...
Nov 28 02:10:17 afbook kernel: [49320.669008] SYNC - BBP R4 to 20MHz.l
Nov 28 02:10:17 afbook kernel: [49320.678014] SwitchChannel#1(RF=5, Pwr0=11, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
Nov 28 02:10:17 afbook kernel: [49320.822913] SwitchChannel#2(RF=5, Pwr0=11, Pwr1=0, 1T), N=0xF1, K=0x07, R=0x02
Nov 28 02:10:17 afbook kernel: [49320.970156] SwitchChannel#3(RF=5, Pwr0=10, Pwr1=0, 1T), N=0xF2, K=0x02, R=0x02
Nov 28 02:10:17 afbook kernel: [49321.120533] SwitchChannel#4(RF=5, Pwr0=10, Pwr1=0, 1T), N=0xF2, K=0x07, R=0x02
Nov 28 02:10:18 afbook kernel: [49321.269911] SwitchChannel#5(RF=5, Pwr0=10, Pwr1=0, 1T), N=0xF3, K=0x02, R=0x02
Nov 28 02:10:18 afbook kernel: [49321.422316] SwitchChannel#6(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF3, K=0x07, R=0x02
Nov 28 02:10:18 afbook kernel: [49321.568684] SwitchChannel#7(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF4, K=0x02, R=0x02
Nov 28 02:10:18 afbook kernel: [49321.723800] SwitchChannel#8(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF4, K=0x07, R=0x02
Nov 28 02:10:18 afbook kernel: [49321.870432] SwitchChannel#9(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF5, K=0x02, R=0x02
Nov 28 02:10:18 afbook kernel: [49321.970264] rt28xx_get_wireless_stats --->
Nov 28 02:10:18 afbook kernel: [49321.970272] <--- rt28xx_get_wireless_stats
Nov 28 02:10:18 afbook kernel: [49322.020310] SwitchChannel#10(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF5, K=0x07, R=0x02
Nov 28 02:10:18 afbook kernel: [49322.172816] SwitchChannel#11(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF6, K=0x02, R=0x02
Nov 28 02:10:19 afbook kernel: [49322.318699] SwitchChannel#12(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF6, K=0x07, R=0x02
Nov 28 02:10:19 afbook kernel: [49322.468703] SwitchChannel#13(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF7, K=0x02, R=0x02
Nov 28 02:10:19 afbook kernel: [49322.619202] SwitchChannel#1(RF=5, Pwr0=11, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
Nov 28 02:10:19 afbook kernel: [49322.623456] SYNC - End of SCAN, restore to channel 1, Total BSS[02]
Nov 28 02:10:19 afbook kernel: [49322.623480] SCAN done, resume MSDU transmission ...
Nov 28 02:10:19 afbook kernel: [49322.623661] rt_ioctl_giwscan:: Still scanning
Nov 28 02:10:20 afbook kernel: [49323.969376] rt28xx_get_wireless_stats --->
Nov 28 02:10:20 afbook kernel: [49323.969379] <--- rt28xx_get_wireless_stats
Nov 28 02:10:22 afbook kernel: [49325.970293] rt28xx_get_wireless_stats --->
Nov 28 02:10:22 afbook kernel: [49325.970300] <--- rt28xx_get_wireless_stats
Nov 28 02:10:24 afbook kernel: [49327.970250] rt28xx_get_wireless_stats --->
Nov 28 02:10:24 afbook kernel: [49327.970257] <--- rt28xx_get_wireless_stats
Nov 28 02:10:26 afbook kernel: [49329.970294] rt28xx_get_wireless_stats --->
Nov 28 02:10:26 afbook kernel: [49329.970301] <--- rt28xx_get_wireless_stats
Nov 28 02:10:28 afbook kernel: [49331.970229] rt28xx_get_wireless_stats --->
Nov 28 02:10:28 afbook kernel: [49331.970236] <--- rt28xx_get_wireless_stats
Nov 28 02:10:30 afbook kernel: [49333.970749] rt28xx_get_wireless_stats --->
Nov 28 02:10:30 afbook kernel: [49333.970756] <--- rt28xx_get_wireless_stats
Nov 28 02:10:47 afbook kernel: [49350.690452] Driver auto reconnect to last OID_802_11_SSID setting - 11n-AP, len - 6
Nov 28 02:10:47 afbook kernel: [49350.690533] CntlOidSsidProc():CNTL - 0 BSS of 2 BSS match the desire (6)SSID - 11n-AP
Nov 28 02:10:47 afbook kernel: [49350.690563] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
Nov 28 02:10:47 afbook kernel: [49350.690753] SCANNING, suspend MSDU transmission ...
Nov 28 02:10:47 afbook kernel: [49350.692722] SYNC - BBP R4 to 20MHz.l
Nov 28 02:10:47 afbook kernel: [49350.701195] SwitchChannel#1(RF=5, Pwr0=11, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
Nov 28 02:10:47 afbook kernel: [49350.848448] SwitchChannel#2(RF=5, Pwr0=11, Pwr1=0, 1T), N=0xF1, K=0x07, R=0x02
Nov 28 02:10:47 afbook kernel: [49351.004962] SwitchChannel#3(RF=5, Pwr0=10, Pwr1=0, 1T), N=0xF2, K=0x02, R=0x02
Nov 28 02:10:47 afbook kernel: [49351.152218] SwitchChannel#4(RF=5, Pwr0=10, Pwr1=0, 1T), N=0xF2, K=0x07, R=0x02
Nov 28 02:10:48 afbook kernel: [49351.304218] SwitchChannel#5(RF=5, Pwr0=10, Pwr1=0, 1T), N=0xF3, K=0x02, R=0x02
Nov 28 02:10:48 afbook kernel: [49351.451471] SwitchChannel#6(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF3, K=0x07, R=0x02
Nov 28 02:10:48 afbook kernel: [49351.608461] SwitchChannel#7(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF4, K=0x02, R=0x02
Nov 28 02:10:48 afbook kernel: [49351.758598] SwitchChannel#8(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF4, K=0x07, R=0x02
Nov 28 02:10:48 afbook kernel: [49351.918347] SwitchChannel#9(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF5, K=0x02, R=0x02
Nov 28 02:10:48 afbook kernel: [49352.071495] SwitchChannel#10(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF5, K=0x07, R=0x02
Nov 28 02:10:49 afbook kernel: [49352.224616] SwitchChannel#11(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF6, K=0x02, R=0x02
Nov 28 02:10:49 afbook kernel: [49352.371601] SwitchChannel#12(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF6, K=0x07, R=0x02
Nov 28 02:10:49 afbook kernel: [49352.519628] SwitchChannel#13(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF7, K=0x02, R=0x02
Nov 28 02:10:49 afbook kernel: [49352.672011] SwitchChannel#1(RF=5, Pwr0=11, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
Nov 28 02:10:49 afbook kernel: [49352.676380] SYNC - End of SCAN, restore to channel 1, Total BSS[02]
Nov 28 02:10:49 afbook kernel: [49352.676405] SCAN done, resume MSDU transmission ...
Nov 28 02:10:49 afbook kernel: [49352.676512] rt_ioctl_giwscan:: Still scanning

Nov 28 02:11:47 afbook kernel: [49410.715048] Driver auto reconnect to last OID_802_11_SSID setting - 11n-AP, len - 6
Nov 28 02:11:47 afbook kernel: [49410.715119] CntlOidSsidProc():CNTL - 0 BSS of 3 BSS match the desire (6)SSID - 11n-AP
Nov 28 02:11:47 afbook kernel: [49410.715124] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
Nov 28 02:11:47 afbook kernel: [49410.715219] SCANNING, suspend MSDU transmission ...
Nov 28 02:11:47 afbook kernel: [49410.716929] SYNC - BBP R4 to 20MHz.l
Nov 28 02:11:47 afbook kernel: [49410.725310] SwitchChannel#1(RF=5, Pwr0=11, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
Nov 28 02:11:47 afbook kernel: [49410.868695] SwitchChannel#2(RF=5, Pwr0=11, Pwr1=0, 1T), N=0xF1, K=0x07, R=0x02
Nov 28 02:11:47 afbook kernel: [49411.031570] SwitchChannel#3(RF=5, Pwr0=10, Pwr1=0, 1T), N=0xF2, K=0x02, R=0x02
Nov 28 02:11:47 afbook kernel: [49411.179079] SwitchChannel#4(RF=5, Pwr0=10, Pwr1=0, 1T), N=0xF2, K=0x07, R=0x02
Nov 28 02:11:48 afbook kernel: [49411.333332] SwitchChannel#5(RF=5, Pwr0=10, Pwr1=0, 1T), N=0xF3, K=0x02, R=0x02
Nov 28 02:11:48 afbook kernel: [49411.479339] SwitchChannel#6(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF3, K=0x07, R=0x02
Nov 28 02:11:48 afbook kernel: [49411.630857] SwitchChannel#7(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF4, K=0x02, R=0x02
Nov 28 02:11:48 afbook kernel: [49411.784213] SwitchChannel#8(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF4, K=0x07, R=0x02
Nov 28 02:11:48 afbook kernel: [49411.930600] SwitchChannel#9(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF5, K=0x02, R=0x02
Nov 28 02:11:48 afbook kernel: [49412.083242] SwitchChannel#10(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF5, K=0x07, R=0x02
Nov 28 02:11:49 afbook kernel: [49412.229856] SwitchChannel#11(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF6, K=0x02, R=0x02
Nov 28 02:11:49 afbook kernel: [49412.383010] SwitchChannel#12(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF6, K=0x07, R=0x02
Nov 28 02:11:49 afbook kernel: [49412.532493] SwitchChannel#13(RF=5, Pwr0=9, Pwr1=0, 1T), N=0xF7, K=0x02, R=0x02
Nov 28 02:11:49 afbook kernel: [49412.684240] SwitchChannel#1(RF=5, Pwr0=11, Pwr1=0, 1T), N=0xF1, K=0x02, R=0x02
Nov 28 02:11:49 afbook kernel: [49412.688485] SYNC - End of SCAN, restore to channel 1, Total BSS[02]
Nov 28 02:11:49 afbook kernel: [49412.688503] SCAN done, resume MSDU transmission ...
Nov 28 02:11:49 afbook kernel: [49412.688578] rt_ioctl_giwscan:: Still scanning

```

---

### Post by druminus on 2010-11-27
After few minutes of scanning NetworkManager shows networks, it even connects. It took about 3 minutes... 
But when I've disabled rfkill switch to turn off my built-in wifi module -- both connections became dead.

---

### Post by druminus on 2010-11-27
Looks like it connects only when I configure correct SSID in RT2870STA.dat. It's very strange for wireless and roaming adapter.

---

