---
title: "Ethernet connection not recognised."
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by rojrevo on 2013-05-03
I've just installed 12.04 LTS as a dual boot alongside Windows 7 on my desktop PC which is home networked, but upon start-up it keeps telling me that a network cable is unplugged and therefore I have no internet connection nor a connection to my home network. Yet when I boot W7 there is no problem.
Could someone please suggest the likely cause(s) and how to rectify the problem, as I've exhausted my limited Ubuntu knowledge in attempting to find the solution?
Many thanks in advance to responders.

---

### Post by matt_symes on 2013-05-03
Thread moved to **Networking & wireless**.

---

### Post by matt_symes on 2013-05-03
Hi

I'll get the ball rolling for you. We need more information on your hardware.

Please post the output of

```
sudo lshw -c network
```

Enter your password. It will not be echoed to the screen.

Also post the output of

```
lspci -nn | grep -i net
```

Kind regards

---

### Post by rojrevo on 2013-05-04
Thanks Matt. As I have no network access from my Ubuntu installation, I have uploaded both the outputs to one file in my DropBox from a screen photo, which can be accessed from:
**[https://www.dropbox.com/sh/2ilhn0swsep2u4j/ZdbAnwA9KO](https://www.dropbox.com/sh/2ilhn0swsep2u4j/ZdbAnwA9KO)**I look forward to your comments.
Thanks and regards,
Roger

---

### Post by gordintoronto on 2013-05-04
There might be a useful suggestion or two here:
[http://ubuntuforums.org/archive/index.php/t-1978608.html](http://ubuntuforums.org/archive/index.php/t-1978608.html)

---

### Post by matt_symes on 2013-05-04
Hi

> **gordintoronto said:**
> There might be a useful suggestion or two here:
[http://ubuntuforums.org/archive/index.php/t-1978608.html](http://ubuntuforums.org/archive/index.php/t-1978608.html)

There are some good suggestions in the link above to try.

You have a driver installed for the network card and it looks to be up and running correctly.

I'll give you some other things to check as well.

From the terminal

```
cat /sys/devices/pci0000:00/0000:02:01.0/net/eth0/carrier
```

If it's physically connected to the router you would expect to see a value of 1. If it returns a vlue of 0 then you are not physically connected to the router. Check your cabling etc.

I may have got the path incorrect. If so then check

```
cat /sys/devices/pci0000:00/*/net/eth0/carrier
```

If the path is still incorrect then run this command to find it.

```
find /sys -name carrier
```

On my server... Look for the path with eth0 in it.

```
server1:/home/matthew % find /sys -name carrier                                  
/sys/devices/virtual/net/lo/carrier
/sys/devices/pci0000:00/0000:00:04.0/net/eth0/carrier
find: &#8216;/sys/kernel/debug&#8217;: Permission denied
server1:/home/matthew % 
```


On my server...

```
server1:/home/matthew % cat /sys/devices/pci0000:00/*/net/eth0/carrier
1
server1:/home/matthew % cat /sys/devices/pci0000:00/0000:00:04.0/net/eth0/carrier
1
server1:/home/matthew % 

```

Check network-manager is running correctly

```
service network-manager status
```

Expect to see output like this

```
matthew-S206:/home/matthew/Music % service network-manager status
network-manager start/running, process 1063
matthew-S206:/home/matthew/Music % 

```

Check you have an ip address.

```
ifconfig eth0
```

Expect output such as

```
server1:/home/matthew % ifconfig eth0
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:124491 (124.4 KB)  TX bytes:70162 (70.1 KB)
          Interrupt:22 

server1:/home/matthew % 

```

See if you can ping things.

Try to ping your local router

```
ping -c3 <ip_address_of_router>
```

Then try an external site

```
server1:/home/matthew % ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=33.8 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=26.6 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=29.3 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 26.600/29.933/33.848/2.990 ms
server1:/home/matthew % 

```

Perform a lookup on a name

```
nslookup www.google.com
```

Expect to see output like this...
```

server1:/home/matthew % nslookup www.google.com
Server:        192.168.0.1
Address:    192.168.0.1#53

Non-authoritative answer:
Name:    www.google.com
Address: 173.194.67.147
Name:    www.google.com
Address: 173.194.67.99
Name:    www.google.com
Address: 173.194.67.103
Name:    www.google.com
Address: 173.194.67.105
Name:    www.google.com
Address: 173.194.67.104
Name:    www.google.com
Address: 173.194.67.106

server1:/home/matthew % 
```

Each of these steps will help to isolate the problem area.

Post back if required on how far you got.

Kind regards

---

### Post by rojrevo on 2013-05-05
Thanks Matt (and also thanks to gordintoronto).
Here is the link to the output of your suggested code: ifconfig eth0
**[https://dl-web.dropbox.com/get/public/NetPrint2.pdf?w=AAAjha2UznxltkCcVe-0UB5LP0_j-c3lO4RJ-wDLim83Fg](https://dl-web.dropbox.com/get/public/NetPrint2.pdf?w=AAAjha2UznxltkCcVe-0UB5LP0_j-c3lO4RJ-wDLim83Fg)**
There's no inet addr but only some code unrecognised by me.
Note also its name as being inet6 addr and not just inet
The router is not recognising it as being connected.
The various code you suggested before this produced results as expected and it is connected to the router - which is a Netgear DG-834 v4 and works fine under W7.
Your further thoughts would be greatly appreciated.
I'm now going to work through the link gordintoronto suggested.
Thanks again and regards,
Roger

---

### Post by rojrevo on 2013-05-05
Thanks to gordintoronto (and to Matt). Job done!
The first suggestion in the link posted by gordintoronto solved the issue.
Internet now connected and networked printer also now installed.
Grateful thanks to both of you.
Bestest,
Roger

---

### Post by matt_symes on 2013-05-05
Hi

Don't use 

```
sudo pkill -9 .....
```

unless it absolutely necessary. Try without the -9 (SIGKILL) and let it attempt to shudown normally.

```
sudo pkill ...
```

BTW: When i checked that Dropbox link i had a 403 forbidden error.

I'm glad you fixed it though :D

Kind regards

---

### Post by rojrevo on 2013-05-06
Hi Matt,
Many thanks for the SIGKILL tip. I'm away at present but I'll use it when back in the shack.
However, I did note that I had to use pkill each time I booted up Ubuntu, before I could obtain any connectivity.
Is there no way of permanently resolving the issue, please?
As for you obtaining the 403 forbidden error from DropBox, my apologies. I had omitted to obtain the public link and gave you my own link.
It should have been: [https://www.dropbox.com/s/xg88i5zr2ad72aa/NetPrint2.pdf](https://www.dropbox.com/s/xg88i5zr2ad72aa/NetPrint2.pdf)
Many thanks again, Matt, and kind regards,
Roger

---

### Post by matt_symes on 2013-05-06
Hi

I would post your log files to try to get to the root of the problem.

```
sudo apt-get install pastebinit
```

```
pastebinit /var/log/syslog
```

Post back the URL produced.

KInd regards

---

### Post by matt_symes on 2013-05-07
Hi

From the syslog file you PM'ed to me...

This is when you first boot up.

```
May  7 16:48:05 shack NetworkManager[1906]: nm_netlink_monitor_get_flags_sync: assertion `self != NULL' failed
May  7 16:48:05 shack NetworkManager[1906]: <warn> (eth0): couldn't get carrier state: (-1) unknown 
May  7 16:48:05 shack NetworkManager[1906]: <info> (eth0): carrier now OFF (device state 20, deferring action for 4 seconds) 
May  7 16:48:05 shack NetworkManager[1906]: <info> (eth0): preparing device. May  7 16:48:05 shack NetworkManager[1906]: <info> (eth0): deactivating device (reason 'managed') [2]
```

... and this is after you kill network manager and it gets respawned.

```
May  7 16:48:57 shack NetworkManager[1943]: <warn> failed to allocate link cache: (-10) Operation not supported 
May  7 16:48:57 shack NetworkManager[1943]: <info> (eth0): carrier is ON 
May  7 16:48:57 shack NetworkManager[1943]: <info> (eth0): new Ethernet device (driver: 'sundance' ifindex: 2) 
May  7 16:48:57 shack NetworkManager[1943]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0 
May  7 16:48:57 shack NetworkManager[1943]: <info> (eth0): now managed
```

It looks like network manager cannot get the carrier signal until you respawn. i.e it does not think it's connected to anything via the Ethernet port.

This may be due to the error in the first line: *assertion `self != NULL' failed*.

This may require some research as it's not an error i have come across before.

EDIT:

Can you try something ? Boot into Ubuntu but don't kill network manager. Instead unplug and replug your Ethernet cable.

Does that get you connected ?

Kind regards

---

### Post by rojrevo on 2013-05-08
Thanks Matt.
Disconnecting and then re-connecting the network cable after booting up makes no difference.
I have now re-booted both with and without the network cably plugged in, and then plugged in the cable but again no connectivity.
The only way I can activate the Network manager is by the command: sudo pkill -9 NetworkManager
Once connected, if I then disconnect the cable I get the error message saying I'm now offline.
Then if I re-connect the cable it comes back up immediately.
Hope this helps.
Thanks and regards,
Roger

---

### Post by matt_symes on 2013-05-08
Hi

My research led me here.

[https://bugzilla.redhat.com/show_bug.cgi?id=816719](https://bugzilla.redhat.com/show_bug.cgi?id=816719)

and then consequently here

[http://ubuntuforums.org/showthread.php?t=1981329](http://ubuntuforums.org/showthread.php?t=1981329)

which then linked back into the Redhat bug :)

It seems your driver/card may not support carrier detection and that would explain the syslog messages.

AnnMatt's solution (post #4) was to set up a fixed network connection by ensuring that interface is not managed by Network Manager. It's a tutorial from liberiangeek. I've looked at it and it looks fine for 12.04. You'll also need to set up DNS as also highlighted in that post.

That sound like the kind of workaround i would apply so you may want to give that a go.

If you need help then post back.

I assume this is a desktop PC ?

I'll double check on your driver and i'll also see if there's an updated Network Manager that fixes the issue.

Kind regards

---

### Post by rojrevo on 2013-05-09
Thanks Matt,
The possible fix you example all appears to be very nebulous and perhaps better done by an expert rather than by a ham-fisted enthusiast like me.
I've looked for an update to Network Manager without success and searched other instances of similar problems with NM, and even tried the more simpler suggestions, but none of them appear to work - possibly because they're not quite my problem. Even modifying /etc/network/interfaces to a default ethernet didn't make any difference.
Below is the NM status both immediately post bootup, and then after restarting it. The only difference being the state.
I think its a timing issue in the bootup process - software/hardware.
Any further thoughts please?
Kind regards,
Roger

roj@shack:~$ nmcli -f all -p nm status
===============================================================================================================
                                             NetworkManager status
===============================================================================================================
RUNNING         VERSION    STATE           NET-ENABLED   WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
---------------------------------------------------------------------------------------------------------------
running         0.9.4.0    disconnected    enabled       enabled         enabled    enabled         disabled  
roj@shack:~$ sudo NetworkManager
[sudo] password for roj: 
NetworkManager is already running (pid 750)
roj@shack:~$ sudo pkill -9 NetworkManager
roj@shack:~$ nmcli -f all -p nm status
===============================================================================================================
                                             NetworkManager status
===============================================================================================================
RUNNING         VERSION    STATE           NET-ENABLED   WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
---------------------------------------------------------------------------------------------------------------
running         0.9.4.0    connected       enabled       enabled         enabled    enabled         disabled  
roj@shack:~$ NetworkManager --version
0.9.4.0
roj@shack:~$ sudo apt-get install NetworkManager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package NetworkManager
roj@shack:~$

---

### Post by matt_symes on 2013-05-09
Hi

To see if Linux thinks it has an Ethernet connection at startup, run this command before restarting network manager.

```
find /sys -name carrier -exec cat {} \; -exec echo {} \; 2> /dev/null
```

It could be a timing issue. Maybe network manager is querying the card/driver before it's ready ? That is just supposition though.

We can make network manager start a bit later.

From the terminal...

```
sudo nano /etc/init/network-manager.conf
```

Look for the line that says

```
exec NetworkManager
```

and on the line before it add

```
sleep 60
```

Ctrl + o to save and Ctrl + x to edit.

It'll start up 60 seconds later. If this fixes the issue then it can be adjusted downwards later.

Kind regards

---

### Post by rojrevo on 2013-05-10
Hi Matt,
Adding the sleep 60 line made no difference. It just delayed the message saying no network connection by 60 secs.
So I've removed it.
This is the output of:
roj@shack:~$ find /sys -name carrier -exec cat {} \; -exec echo {} \; 2> /dev/null
1
/sys/devices/virtual/net/lo/carrier
1
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0/carrier
roj@shack:~$ 
Thanks and kind regards,
Roger

---

### Post by rojrevo on 2013-05-10
Hi Again Matt,
It would appear that my version of Network Manager (0.9.4.0-0ubuntu4, 0.9.4.0-0ubuntu4.1) is causing lots of problems and many are apparently reverting to version Oubuntu3.
This link explains more:
[http://ubuntuforums.org/showthread.php?p=12016190#post12016190](http://ubuntuforums.org/showthread.php?p=12016190#post12016190)
Do you think this could be causing my problems and should I attempt to revert and install Oubuntu3?
Unless, of course, you have meanwhile come across an alternative fix?
Kind regards,
Roger

---

### Post by matt_symes on 2013-05-10
Hi

Well judging by that output, you have a carrier signal at the start so that is not the problem.

I would still suggest going down the route of stopping network manager managing the eth0 interface and setting it to get an IP address using DHCP in network interfaces.

I still believe that is your best bet and simpliest fix.

As for downgrading network manager, you look to be getting a different set of error messages than the other posters in that thread. 

However, that being said, you could certainly try it and see how it goes as it may well be a bug in network manager/netlink.

Kind regards

---

### Post by rojrevo on 2013-05-12
Regrettably, Matt, I have tried this workaround by applying the changes for a fixed IP address, etc, as per the links you referred to but without success.
Post changes, the bootup displayed a message 'Waiting for Network Configuration' under the startup Ubuntu logo screen, and would take all of a minute to present the desktop.
Then the network connection symbol would be shown on the top toolbar (Eureka) but alas no internet connection when using the browser or email.
The workaround showed both network and gateway addresses as 192.168.0.1 and I tried different settings for these, but again without success.
As for downgrading Network Manager to the previous version, I've read up further on this and I've reached the same conclusion as yourself, that those are somewhat different - and it looks to be a complicated solution to try.
Surely, if there is a bug in this latest version of Network Manager, then would not Ubuntu have issued a fix by now?
Any further thoughts, please?
And without wishing to appear disrespectful or thankless to you (far from it), how can the [SOLVED] prefix to the title of this thread be removed, in case others may have come across similar, if not the same, problems and are put-off responding, thinking it is solved?
Kind regards,
Roger

---

### Post by matt_symes on 2013-05-12
Hi
> 
Regrettably, Matt, I have tried this workaround by applying the changes  for a fixed IP address, etc, as per the links you referred to but  without success.
Post changes, the bootup displayed a message 'Waiting for Network  Configuration' under the startup Ubuntu logo screen, and would take all  of a minute to present the desktop.
Then the network connection symbol would be shown on the top toolbar  (Eureka) but alas no internet connection when using the browser or  email.

Did you set up a dns server ?

Please post the output of

```
cat /etc/network/interfaces
```

```
ping -c 3 8.8.8.8
```

```
nslookup www.slashdot.com
```

Kind regards

---

### Post by rojrevo on 2013-05-12
Hi Matt,
Done it! I continued researching the problem after my earlier post today and found more evidence of Network Manager causing serious problems since Adam was a lad.
So I removed NM in its entirity and edited /etc/network/interfaces to just recognise eth0 - as per [http://ubuntuguide.org/wiki/Ubuntu_Precise_Network_Management](http://ubuntuguide.org/wiki/Ubuntu_Precise_Network_Management)
-------------------------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
# auto lo
# iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

auto eth0
iface eth0 inet dhcp
-----------------------------------------------------------------
Commented out the loopback two lines and inserting the last two lines.
I then configured eth0 using ifup
Restarted and hey presto - auto Internet access but regretfully with no icon in the system tray telling me that. Can you please suggest a howto for this?
Is there anything any else I should do, please, to make these changes robust?
Do you still want the outputs you requested?
My grateful thanks and kind regards,
Roger

---

### Post by matt_symes on 2013-05-12
Hi

> Restarted and hey presto - auto Internet access but regretfully with no  icon in the system tray telling me that. Can you please suggest a howto  for this?

I don't really know of one i'm afraid.

> Is there anything any else I should do, please, to make these changes robust?

You could look at using wicd instead of network manager.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Been a good while since i have looked at it though and i don't know if it integrates into the panel.

```
sudo apt-get install wicd
```

> Do you still want the outputs you requested?

No :D You have a working solution.

Kind regards

---

### Post by rojrevo on 2013-05-13
Just to say thank you Matt, for your time and effort in guiding me towards the solution.
Much appreciated and kind regards,
Roger

---

