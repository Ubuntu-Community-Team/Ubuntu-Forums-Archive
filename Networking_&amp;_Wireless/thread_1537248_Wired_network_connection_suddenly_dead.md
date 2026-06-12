---
title: "Wired network connection suddenly dead"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by ubunterooster on 2010-07-23
[COLOR=Red]{edit] Okay the problem reoccurred but I fixed it by taking down the entire network for 10 minutes. See post #11 for more details[/edit]
[/COLOR]

It was working a little bit ago. I locked the screen and walked away and when I came back I could not get internet ```
ubunterooser@ubunterooser-server ~ $ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 6c:f0:49:79:8d:e4   
           inet6 addr: fe80::6ef0:49ff:fe79:8de4/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:37 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:4070 (4.0 KB)  TX bytes:2736 (2.7 KB)  
           Interrupt:26 Base address:0x6000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:14 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:14 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:820 (820.0 B)  TX bytes:820 (820.0 B) 
```Okay, so it sees the card I think. Time to look at the hosts file
 ```
ubunterooser@ubunterooser-server ~ $ gksu gedit /etc/hosts  
 

 127.0.0.1    localhost  
 127.0.1.1    ubunterooser-server  
 

 # The following lines are desirable for IPv6 capable hosts  
 ::1     localhost ip6-localhost ip6-loopback  
 fe00::0 ip6-localnet  
 ff00::0 ip6-mcastprefix  
 ff02::1 ip6-allnodes  
 ff02::2 ip6-allrouters  
 ff02::3 ip6-allhosts
``````
ubunterooser@ubunterooser-server ~ $ ping -c 3 localhost  
 PING localhost (127.0.0.1) 56(84) bytes of data.  
 64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.061 ms  
 64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.056 ms  
 64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.057 ms  
 

 --- localhost ping statistics ---  
 3 packets transmitted, 3 received, 0% packet loss, time 1998ms  
 rtt min/avg/max/mdev = 0.056/0.058/0.061/0.002 ms  
 ubunterooser@ubunterooser-server ~ $ 
``` What now?
 

 I tried rebooting which did not work and then booting to another partition (10.10 )which also now has no internet. So I tried a different CAT6 cable (known to be good) and plugged it into a different port in the router (also known to be good)
 

 {written via USB shuttled files and pasted to UF through another PC}

---

### Post by pricetech on 2010-07-23
I know it's a "duh" but other computers on the network connect ??

---

### Post by ubunterooster on 2010-07-23
> **pricetech said:**
> I know it's a "duh" but other computers on the network connect ??Yes


Oh, and the xsession file for the PC with the problem

v
v```
xsessionerrors

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-iXec8M
SSH_AUTH_SOCK=/tmp/keyring-iXec8M/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-iXec8M
SSH_AUTH_SOCK=/tmp/keyring-iXec8M/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-iXec8M
SSH_AUTH_SOCK=/tmp/keyring-iXec8M/ssh
gnome-session[2113]: WARNING: Could not launch application 'uptrack-manager.desktop': Unable to start application: Failed to execute child process "uptrack-manager" (No such file or directory){I removed Uptrack a while ago-it should not start so ignore that part}

(gnome-power-manager:2189): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x1f6e5e0'
[COLOR=Red]
(polkit-gnome-authentication-agent-1:2193): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2193): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed[/COLOR] [COLOR=Red]
** (nm-applet:2194): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-open-terminal extension[/COLOR]
```

---

### Post by pricetech on 2010-07-23
Sadly the logs don't mean as much to me as they should. (sorry)

I notice that you're using IPv6.  Have you tried pinging ::1  ??

It doesn't sound like a software issue though, since the OS on the other partition doesn't connect either, even though the NIC appears to be seen and configured.

Got another NIC you can try ??

---

### Post by ubunterooster on 2010-07-23
No other cards to try, hang on while I reinstall to see if that helps

---

### Post by ubunterooster on 2010-07-23
Tada! all better! Maybe I should not use 10.10 to see if things are working right

---

### Post by pricetech on 2010-07-23
I didn't notice if you said, same version on both partitions ??  That would help explain the same issue manifesting on both.

Glad you got it back to working either way.

---

### Post by ubunterooster on 2010-07-23
Actually it was Mint9 on main; 10.10 on backup.

Reason both went at once, I have no idea

---

### Post by Iowan on 2010-07-24
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") ? ;)

---

### Post by ubunterooster on 2010-07-24
> **iowan said:**
> [[solved]]("https://wiki.ubuntu.com/unansweredpoststeam/solvedthreads") ? ;)
lol

---

### Post by ubunterooster on 2010-07-24
Okay, the problem is not the OS, it is between VOIP device and router I think. The desktop's network went down again but the one laptop (wireless) was fine. I turned on another laptop which was unable to connect wireslessly. I turned off modem, router, VOIP device and all PCs for 10 minutes and on starting back up, all seemed fine. But this seems to be happening to frequently, being the fourth time.[COLOR=Blue] Any ideas to figure out what is the intermittent culprit?[/COLOR]

---

### Post by ubunterooster on 2010-07-28
It is the router.
 *marks as "solved"* 
Seems like we just bought this router, so I hope we can find the receipt.

---

### Post by naveen9885 on 2010-07-28
CAn some one pls help me with the issue in this thread. [http://ubuntuforums.org/showthread.php?t=1537782](http://ubuntuforums.org/showthread.php?t=1537782)

---

