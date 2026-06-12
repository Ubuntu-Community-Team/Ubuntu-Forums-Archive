---
title: "&quot;Belkin N wireless USB adapter&quot; worked... and stopped to work (after reboot)!"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by lilso on 2011-04-23
Hello,

As it is my first post, allow me a small introduction! :) I've been using Windows all my life (and still have to use it at work) but I made the big leap yesterday and installed Ubuntu on my personal machine (at last). With my "Windows-centric" mind, there are a million things that I still don't get, but I must say the community and forums look quite impressive and easy to access (kudos! ;)). I am testing this today!

My current problem is with the wireless adapter. I have a Belkin N Wireless USB adapter (FSD8053v3) and Belkin, of course, doesn't make linux drivers. When I installed Ubuntu, it recognized it automatically and I could connect to my network, but navigation was very slow so I tried to install Belkin windows drivers using ndiswrapper. It worked immediately, and navigation was very fast. However after a reboot, I lost the connection, I can't even see any of the neighbouring networks.

ndiswrapper -l gives me:

```
rt2870 : driver installed
	device (050D:815C) present (alternate driver: rt2800usb)
```

ifconfig doesn't give me a wlan0:
```
lilso@lilso:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:19:6f:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
```

Thanks a lot for your help and any advice you may have for this problem!

Lilso

---

### Post by chili555 on 2011-04-23
May I please see:```
lsmod | grep -e rt2 -e ndis
```Thanks.

---

### Post by lilso on 2011-04-23
I only get one line:
```
ndiswrapper          249811 0
```
I guess this means the wireless drivers are not loaded?

Thanks!

---

### Post by chili555 on 2011-04-23
It means that ndiswrapper is loaded and that no other conflicting drivers are loaded. So far, so good. What does this say?```
dmesg | grep ndis
iwconfig
```Where did you get the Windows .inf and .sys files? Windows XP, I hope (but suspect not.) Thanks.

By the way, after we struggle a while, I am quite confident we can fix up the native driver.

---

### Post by lilso on 2011-04-23
Hi

Thanks for your help.

```
sudo modprobe rt2800usb
``` reactivated the connection, probably by reactivating the native driver (even if I have to type it in the console at each restart, I don't know why as it's not in blacklist). However, I still can't get the Belkin drivers to work. I got the Belkin .inf file from an install on a 32-bit WinXP machine, and tranferred it to my 64-bit Ubuntu machine, which may be the cause of the problem (?). But Belkin only provides the drivers in .exe format, and installs only the appropriate version on a given machine (that's why I got only the 32-bit version on the 32-bit WinXP machine). I was maybe thinking of trying Wine or something similar, but I don't know if that's not starting to be too much.

The first line of command you suggested gave:

```
lilso@lilso:~$ dmesg | grep ndis
[    7.708135] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[    8.807414] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[    8.807421] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[    8.807996] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[    8.808127] usbcore: registered new interface driver ndiswrapper
```

The second one gave:
```
lilso@lilso:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"homewifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:5A:29:EB:78   
          Bit Rate=108 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0
```

Thanks again.

---

### Post by chili555 on 2011-04-23
> kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B> from an install on a 32-bit WinXP machine, and tranferred it to my 64-bit Ubuntu machine, which may be the cause of the problem (?)Yes, indeed.

I think we can ditch ndiswrapper and enable not rt2800usb but rt2870sta. Please try:```
sudo rmmod -f ndiswrapper
sudo rmmod -f rt2800usb
sudo modprobe rt2870sta
```Any improvement? If so, we'll need to amend a file or two to make it permanent.

---

### Post by lilso on 2011-04-24
It seems to work very well and the connection is much faster. How can I load this at each startup?

Thank you for your time and help

---

### Post by chili555 on 2011-04-24
It's a bit tedious, but do this:```
sudo gedit /etc/modules
```Add the following:```
rt2870sta
```If ndiswrapper is in there, remove it. Proofread carefully, save and close gedit.

Some ndiswrapper tutorials ask you to add a file /etc/modprobe.d/blacklist. It is, on newer systems, incorrect. Please do:```
sudo rm /etc/modprobe.d/blacklist
```If there is no such file, you will be notified and that's fine. Now do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add the following:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```If rt2870sta is in there, remove it. Proofread carefully, save and close gedit. Now do:```
sudo ndiswrapper -e rt2870
```Reboot and let us have your report.

---

### Post by lilso on 2011-04-24
Solved! Everything works perfectly fine now (and it seems somehow faster than my previous configuration on Windows). Also, I learnt good basic things while solving this problem thanks to you.

Thanks.

---

### Post by lilso on 2011-04-24
Just a small thing though. At each startup, it asks me for the password for the keyring. Even if I ask to automatically do it, it keeps asking it to me at startup and the connection does not establish if I don't do it. Is there a way to remove this?

Thanks again.

---

### Post by chili555 on 2011-04-24
> At each startup, it asks me for the password for the keyring. Even if I ask to automatically do it, it keeps asking it to me at startup and the connection does not establish if I don't do it. Is there a way to remove this?I clicked 'Cancel' once and never saw it again. My machines connect on boot with no further intervention.

---

### Post by lilso on 2011-04-25
Hmm.
Pressing "cancel" it tells me that the password is incorrect and I have to type it to get in...

---

### Post by chili555 on 2011-04-25
Pressing Cancel on the request for the WPA password? I am asking you to press Cancel on the request for the keyring password.> At each startup, it asks me for the password for the keyring.

---

### Post by lilso on 2011-04-25
I think this is what I am doing. This is not a windows for the WPA password that appears but one that says:
```
Enter password for keyring 'Default' to unlock
An application wants access to the keyring 'Default', but it is locked
```
And each time I am typing my password and choosing:
```
Automatically unlock this keyring whenever I'm logged in
```
But at each startup, this windows appear.
I don't see anything wrong in the settings for "Passwords and Encryption keys"

Thanks for your help

---

### Post by chili555 on 2011-04-25
I am out of ideas. I suggest you search and/or ask in General Help.

---

