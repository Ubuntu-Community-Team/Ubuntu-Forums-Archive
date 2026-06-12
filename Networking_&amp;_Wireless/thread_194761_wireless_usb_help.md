---
title: "wireless usb help"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by Mechanical on 2006-06-11
I was really excited to see my wireless netgear usb adapters lights come on when installing the new ubuntu, but now I can't connect.  It says the thing is there, in the system properties it shows up and even displays the name of it, but I can't seem to connect.  I was reading on here about some ways to get it working, but I am very new to linux and could use some assistance.  I would switch over from windows if I can only connect to my router and get online in ubuntu.  If anyone could help, thanks!

---

### Post by Mechanical on 2006-06-12
Ok, I have tried installing ndiswrapper and using it to get the driver for my card installed and running.  I cd to the directory and follow the instructions but I keep getting an error saying 'make' isn't working.  I was doing this in the terminal, isn't that where one would execute these commands or am I completely lost?  Everything on my computer is running smoothly except the netgear card, which I can't get to work correctly.  My wireless network is not picking up and I can't seem to connect to the router.

update...........


Ah.. ndiswrapper is on the cd, and I had to install the tools for compiling programs as well.  I managed to get ndiswrapper installed and the driver for my netgear usb adapter.  The thing still doesn't seem to be able to detect any network.

---

### Post by Tobbz on 2006-06-12
Which netgear usb model is it?

Try to type the following in terminal, and paste the outcome here.

ifconfig

iwconfig

---

### Post by Mechanical on 2006-06-12
Thanks for the reply!  My netgear usb reciever is the wg121, and below is the outcome of ifconfig and iwconfig.  I am almost completely clueless as to what I am doing wrong.  Also, does the ndiswrapper load the driver at startup?  I haven't done anything to make it.  It did say the driver installed fine.  I have a feeling I am overlooking something that might be obvious, but not sure what..

I am guessing eth2 is what I am after.



ifconfig


eth0      Link encap:Ethernet  HWaddr 00:13:D4:D2:26:9D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth2      Link encap:Ethernet  HWaddr 00:09:5B:A1:77:63
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6340 (6.1 KiB)  TX bytes:6340 (6.1 KiB)



iwconfig



lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any
          Mode:Auto  Channel=14  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by Tobbz on 2006-06-12
OK, so eth2 is your wireless.

Is your wireless network broadcasting it's ID/Name (ssid)?
Try this, and paste the outcome:
iwlist eth2 scan

can you ping your router?
ping 192.168.1.1 , (guess that is the IP, but im not sure)

try dhcpclient eth2 , what is the outcome?

Is your wireless using any kind of encryption?

typing ndiswrapper -l should show if the driver and hardware is present.

---

### Post by Mechanical on 2006-06-12
Ok, trying other things with no luck.  

iwlist eth2 scan came back saying there were no scan results.

ndiswrapper states that it has the driver and recognizes the hardware.

dhcpclient eth2 came back saying the command couldn't run.

I do have my router broadcasting the wireless network name, and I am using wep encryption.  I attempted to ping my router, no luck.  Nothing comes back.  

My router is not the best, but could it be the problem?  It is a microsoft router and I have read they aren't the best.  I haven't had any trouble with it so far though under windows.

---

### Post by Mechanical on 2006-06-12
A small update, I read through more stuff.  I read the wiki on usb adapters in ubuntu and found others have got the wg121 working fine.  I messed with it again, unplugged my reciever, reset everything, still no connection.  :confused: 

I am starting to think my ubuntu days may be over.  :-( 

I will keep the partitions in place and try other things for a while.  Still looking for any advice anyone can give.  Thanks.

---

### Post by Mechanical on 2006-06-13
I found a solution that works!!!

I moved around some things, put the network adapter on the computer running windows still (hopefully can change that soon too) and got the router on this computer.  Everything works fine now!!  Ok, not really a software solution, but oh well... Im using ubuntu!

---

### Post by gbw69 on 2006-06-14
I'm new to Ubuntu/Linux myself.
Try this link to troubleshoot your wireless network
[https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide)
See how far you get, if it doesn't sort out your problem then atleast you'll have a good idea what to look for next.
Good luck.

---

### Post by geetarista on 2006-06-14
I was having a problem similar to this and I fixed it by blacklisting the driver that ubuntu uses by default.  See if this thread helps:

[http://www.ubuntuforums.org/showthread.php?t=189146](http://www.ubuntuforums.org/showthread.php?t=189146)

---

