---
title: "Wireless Access Point"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by lvleph on 2010-05-20
I am trying to create a wireless access point, since my router keeps losing its settings. Eventually, the plan is to replace the router with my Linux Box. Anyway, I was trying to following the how to located [here](http://blog.bokhorst.biz/3395/computers-en-internet). But, now I can't even create the access point, whereas before I could create one, but just couldn't get WPA to work. During the setup I did hit one hickup while trying to start hostapd it failed.
**sudo /etc/init.d/hostapd restart**
```

 * Stopping advanced IEEE 802.11 management                              [ OK ] 
 * Starting advanced IEEE 802.11 management                              [fail]

```

**lspci | grep Network**
```

04:06.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)

```

**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:1f:e2:04:f3:a1  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fe04:f3a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:231436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:249093561 (249.0 MB)  TX bytes:45935995 (45.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10713 (10.7 KB)  TX bytes:10713 (10.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:01:60:c9:0b  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``` 

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Clearly, something is all screwy, but I don't know how to fix it. I am starting to think that I am just clueless, so I need some help setting this crap up.

EDIT: Had some errors in my hostapd.conf file. I fixed them but still get the following
**sudo hostapd -B /etc/hostapd/hostapd.conf**
```
 
Configuration file: /etc/hostapd/hostapd.conf
wlan0: IEEE 802.11 Configured channel (60) not found from the channel list of current mode (1) IEEE 802.11g
wlan0: IEEE 802.11 Hardware does not support configured channel
Could not select hw_mode and channel. (-1)
rmdir[ctrl_interface]: No such file or directory
```

**sudo /etc/init.d/hostapd restart**
```

 * Stopping advanced IEEE 802.11 management                              [ OK ] 
 * Starting advanced IEEE 802.11 management                                     rmdir[ctrl_interface]: No such file or directory
                                                                         [fail]
```

---

### Post by lvleph on 2010-05-20
I got rid of the errors and hostapd loads, but I can't seem to find the connection. Here is my hostapd.conf
```

interface=wlan0
driver=nl80211
ssid=Testnet
channel=1
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=1234567890
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP

```

EDIT: Now I can see the wireless connection, but I can't seem to connect to it.

EDIT2: Scratch that I can't see it anymore. Not sure what happened.

EDIT3: Looks like I am back to this error
```
Configuration file: /etc/hostapd/hostapd.conf
Failed to create interface mon.wlan0.
nl80211 driver initialization failed.
wlan0: Unable to setup interface.
```

---

### Post by lvleph on 2010-05-20
I restarted the computer and now I can get hostap to start. However, I would like it to autostart, and I am not able to use the internet. Can someone help me out there?

---

### Post by lvleph on 2010-05-21
Okay, now I have the internet through the wireless using
```
sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
```
But, how do I make all this persistent?

EDIT: I would also like to make the wireless available before log in. Although this is not a big deal since it only takes about 15 secs from grub to login.

---

### Post by purelinuxuser on 2010-05-21
You know what, I actually have a shell script that does just what you are trying to achieve- turn a target wireless card into an access point with a shared Internet connection!  A .tar.gz file is attached to this post- extract it and you'll get a file called "ap_ctl."  Move it to /usr/bin (or somewhere else).  You will need to have hostapd and dhcp3-server installed.

Anyway, to use the script, you'll have to open it up in a text editor and make some changes to suit your situation.

[LIST=1]
[*]Near the top of the script, you'll see the following lines:
```
# broadcasting interface
BROADCAST="wlan1"

# receiving interface broadcast is connected to
RECEIVE="wlan0"
```Replace "wlan1" with your "broadcasting" wireless interface and "wlan0" with your "receiving" network interface (probably eth0 since you are going through Ethernet).
.
[*]Next you'll have to set the IP address of your Linux box/router.  Find the following two sections:
```
 # set IP address
 ifconfig $BROADCAST 192.168.111.151
 sleep 2
``````
 # create iptables rules
 iptables -A FORWARD -i $RECEIVE -o $BROADCAST -s 192.168.111.151/24 -m conntrack --ctstate NEW -j ACCEPT
 iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```...and replace "192.168.111.151" with whatever you want that IP to be.
.
[*]Configure /etc/hostapd/hostapd.conf and /etc/dhcp3/dhcpd.conf to your liking.
.
[*]To start the access point, run:
```
ap_ctl --start
ap_ctl --ics
```
.
[*]You can add those two lines in /etc/rc.local to have them run at boot, usually just before login.
[/LIST]
And that's pretty much it!  Everything else should pretty much take care of itself. :) Post back with any problems you may have.

---

### Post by lvleph on 2010-05-21
Thank you very much. I will get this up and make sure I don't have any questions soon.

---

### Post by lvleph on 2010-05-21
Okay, here the result of running
**sudo ./ap_ctl --start**
```
Starting hostapd
	You can view the log at /var/log/hostapd.log
Starting dhcpd3
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Wrote 0 leases to leases file.

No subnet declaration for wlan0 (0.0.0.0).
** Ignoring requests on wlan0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface wlan0 is attached. **


Not configured to listen on any interfaces!

```

Here is my edited **ap_ctl**
```
#!/bin/bash

# broadcasting interface
BROADCAST="wlan0"

# receiving interface broadcast is connected to
RECEIVE="eth0"

if [[ $1 == "-0" || $1 == "--start" ]]
 then
 ## start hostapd
 echo "Starting hostapd"
 echo "	You can view the log at /var/log/hostapd.log"

 # launch hostapd daemon
 hostapd -d /etc/hostapd/hostapd.conf > /var/log/hostapd.log &

 ## start dhcp server
 echo "Starting dhcpd3"

 # set IP address
 ifconfig $BROADCAST 192.168.0.2
 sleep 2

 # launch dhcpd3 daemon
 echo "INTERFACES=$BROADCAST" > /etc/default/dhcp
 dhcpd3 $BROADCAST &

elif [[ $1 == "-1" || $1 == "--stop" ]]
 then
 # send signal 2 to hostapd and dhcpd3
 killall -2 hostapd dhcpd3

elif [[ $1 == "-2" || $1 == "--ics" ]]
 then
 # create iptables rules
 iptables -A FORWARD -i $RECEIVE -o $BROADCAST -s 192.168.0.2/24 -m conntrack --ctstate NEW -j ACCEPT
 iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
 iptables -A POSTROUTING -t nat -j MASQUERADE

 # set kernel variable(s)
 echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

 # edit kernel configuration
 cp /etc/sysctl.conf /etc/sysctl.conf.ap_ctl
 echo "net.ipv4.conf.default.forwarding=1" >> /etc/sysctl.conf
 echo "net.ipv4.conf.all.forwarding=1" >> /etc/sysctl.conf

 # restart networking
 /etc/init.d/networking restart

elif [[ $1 == "-3" || $1 == "--noics" ]]
 then
 # remove iptables rules
 iptables -D FORWARD 1
 iptables -D FORWARD 1

 # set kernel variable(s)
 echo 0 > /proc/sys/net/ipv4/conf/all/forwarding

 # revert kernel configuration
 mv -i /etc/sysctl.conf.ap_ctl /etc/sysctl.conf

 # restart networking
 /etc/init.d/networking restart

else
 echo $0
 echo "A tool to manage hostapd and dhcpd3"
 echo "Usage:"
 echo "	-0 --start	Start hostapd and dhcpd3"
 echo "	-1 --stop	Stop hostapd and dhcpd3 with signal 2"
 echo "	-2 --ics	Activate internet connection sharing"
 echo "			between specified interfaces"
 echo "	-3 --noics	Undo internet connection sharing settings"
fi

exit 0

```

Here is my **dhcpd.conf**
```
ddns-update-style interim;
ignore client-updates;
 
 subnet 192.168.0.0 netmask 255.255.255.0 {
  
   # The range of IP addresses the server
   # will issue to DHCP enabled PC clients
   # booting up on the network
  
   range 192.168.0.3 192.168.0.220;
  
   # Set the amount of time in seconds that
   # a client may keep the IP address

  default-lease-time 86400;
  max-lease-time 86400;
 
   # Set the default gateway to be used by
   # the PC clients
  
   option routers 192.168.0.2;
   # Don't forward DHCP requests from this
   # NIC interface to any other NIC
   # interfaces
 
    option ip-forwarding off;
 
    # Set the broadcast
		# address and subnet mask
    # to be used by the
 		# DHCP clients
  
  option broadcast-address 192.168.0.255;
  option subnet-mask 255.255.255.0;
  
   # Set the NTP server to be used by the
   # DHCP clients

  option ntp-servers 192.168.0.100;

   # Set the DNS server to be used by the
   # DHCP clients

  option domain-name-servers 192.168.0.100;
 
   # If you specify a WINS server for your Windows clients,
   # you need to include the following option in the dhcpd.conf file:

   option netbios-name-servers 192.168.0.100;
  
   # You can also assign specific IP addresses based on the clients'
   # ethernet MAC address as follows (Host's name is "laser-printer":

 # host laser-printer {
 #     hardware ethernet 08:00:2b:4c:59:23;
 #    fixed-address 192.168.0.222;
 #   }
}
#
# List an unused interface here
#
subnet 192.168.2.0 netmask 255.255.255.0
{
}
```

---

### Post by purelinuxuser on 2010-05-21
It looks like there is a problem with your dhcpd.conf.  I have had to fiddle around with that thing to get everything working correctly- darn, I should have backed it up when I upgraded to 10.04.

I'll try and see if I can get a sample config working.  I'll post back when it works.

---

### Post by purelinuxuser on 2010-05-21
Ok, I've created a valid and working dhcpd.conf file and a client has been able to successfully associate and have an IP assigned.  Here's my working config:
```
default-lease-time            600;
max-lease-time                7200;

option subnet-mask            255.255.255.0;
option broadcast-address      192.168.111.255;
option routers                192.168.111.151;
option domain-name-servers    208.67.222.222, 208.67.220.220;
[B]
subnet 192.168.111.0 netmask 255.255.255.0 {
    range 192.168.111.100 192.168.111.150;
    }[/B]
```*Source: *[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

Just adapt it to your preference.  I suspect the problem with your file is the section in bold- you didn't specify an IP address range.  That's just my guess though, don't think it's actually correct! :P

---

### Post by lvleph on 2010-05-21
Got the same error.

---

### Post by purelinuxuser on 2010-05-22
> **lvleph said:**
> Got the same error.

May I see your dhcpd.conf?  Also, did you adapt mine or change your existing one?

EDIT: Specify your desired setup too (range, router IP, subnet, etc.) and I will try to configure it on my computer.  Man, why does dhcp3-server have to be so nitpicky?

---

### Post by lvleph on 2010-05-22
I used your dhcpd.conf but changed the router to be 192.168.0.2, the broadcast address was set to 192.168.0.255, and the range to 192.168.0.3 to 192.168.0.220. The subnet was left the same.

---

### Post by purelinuxuser on 2010-05-22
> **lvleph said:**
> I used your dhcpd.conf but changed the router to be 192.168.0.2, the broadcast address was set to 192.168.0.255, and the range to 192.168.0.3 to 192.168.0.220. The subnet was left the same.

Okay, give me a few minutes- I will try to use your settings and see if I can get things working.

---

### Post by purelinuxuser on 2010-05-22
Try this as your /etc/dhcp3/dhcpd.conf:
```
default-lease-time              600;
max-lease-time                  7200;

option subnet-mask              255.255.255.0;
option broadcast-address        192.168.0.255;
option routers                  192.168.0.2;
option domain-name-servers      208.67.222.222, 208.67.220.220;

subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.3 192.168.0.220;
        }
```Router IP set to 192.168.0.2
Broadcast IP set to 192.168.0.255
Subnet set to 192.168.0.0
Netmask set to 255.255.255.0
Range set from 192.168.0.3 to 192.168.0.220

HOPEFULLY this will work... :mad: I tried these settings on my computer and they worked perfectly.

---

### Post by lvleph on 2010-05-22
Nope, that didn't work. It must be a problem somewhere else.

---

### Post by lvleph on 2010-05-22
It seems like it would be easier for me to run 
```
hostapd
``` and then run
```
sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
```
at startup. So if I place this in rc.local it should be good, yes?

---

### Post by lvleph on 2010-05-22
Okay, so I am confused. hostapd is already in /etc/init.d so shouldn't this already start on boot? This means I should see the connection without running this crap manually, but this is not the case.

---

### Post by lvleph on 2010-05-22
Restarted the computer and now nothing works and am back to the error
```
Configuration file: /etc/hostapd/hostapd.conf
Failed to create interface mon.wlan0.
nl80211 driver initialization failed.
```
If my router didn't suck so much I wouldn't even bother at this point.

EDIT: Restarted again and it is fine.

---

### Post by lvleph on 2010-05-22
Okay, I figured out all the problems. I had hostapd running and that is why your script wasn't working.

Thank you for your help!

---

### Post by purelinuxuser on 2010-05-22
> **lvleph said:**
> Okay, I figured out all the problems. I had hostapd running and that is why your script wasn't working.

Thank you for your help!

Oh, so my script worked? :) That's a relief!

Don't forget to mark this thread solved ;)

EDIT: If you run into a similar situation in the future (multiple hostapd's running), you can run "ap_ctl -1" or "ap_ctl --stop."

---

### Post by lvleph on 2010-05-22
When I run **sudo ./ap_ctl --stop** I get
```
dhcpd3: no process found
```
But, then I run **sudo /etc/init.d/hostapd stop** 
and it will stop.
The only issue I am having now is that I would like my ap to have the ip address 19.168.1.2, this way I can pretend nothing ever changed. I have many things that rely on that computer have that ip address. I thought the settings I gave you would ensure this ip address, but I get 192.168.1.1 instead. How can I fix that?

---

### Post by purelinuxuser on 2010-05-22
> **lvleph said:**
> When I run **sudo ./ap_ctl --stop** I get
```
dhcpd3: no process found
```But, then I run **sudo /etc/init.d/hostapd stop** 
and it will stop.
The only issue I am having now is that I would like my ap to have the ip address 19.168.1.2, this way I can pretend nothing ever changed. I have many things that rely on that computer have that ip address. I thought the settings I gave you would ensure this ip address, but I get 192.168.1.1 instead. How can I fix that?

Stopping hostapd: hmm, the script just runs "killall -2 hostapd"... guess that is not always reliable! :P

For the IP thing: your computer is not getting the IP you want, right?  Start the AP and post the output of```
ifconfig
```

---

### Post by lvleph on 2010-05-22
Apperantly, when running ./ap_ctl --ics things break. The ip address was correct, but things go wrong when that command is run. 

Right now I have everything running on startup without your script. The only thing that I need to get working is masquerade. Is there a way to add the following command to iptables permanently?
```
iptables -t nat _A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
```
The only thing left after this is to make static ips for my other comps. Any idea how to do this?

Thank you for all your help.

---

### Post by lvleph on 2010-05-22
Okay, I made a script **/etc/init.d/startup** that contains
```

#!/bin/bash
sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE

```
Then I made it executable **sudo chmod +x /etc/init.d/startup** and finally updated the startup scripts with **sudo update-rc.d startup defaults**.

So the only thing left is to figure out how to assign static IP addresses.

---

### Post by purelinuxuser on 2010-05-22
> **lvleph said:**
> So the only thing left is to figure out how to assign static IP addresses.

Man, bummer that ap_ctl --ics breaks things for you. :( Always worked fine for me, Internet being available on both the host and client computers (and those clients can be Windows XP, Nintendo DS, iPhone, whatever...).

As for assigning static IPs- uhm, couldn't you set that up on client computers?  On Ubuntu/Linux, you can right-click on nm-applet, click "Edit Connections," select the wireless network, click edit, then set your IPv4 settings to "Manual."  I have no idea how to do that on Windows, and I'm too lazy to look it up. :P

If you plan to do things on the server-side, then I can't help you there- my script is set for a DHCP-enabled access point.

---

### Post by lvleph on 2010-05-22
Yep going into nm and then editing the connection allows me to change ip settings to manual. I set the ip address to the desired address, then set netmask to 255.255.255.0, gateway to 192.168.1.2 (router address), and dns server to 192.168.1.2 (router address. Now everything works.

Thank you for all your help. Your script helped me understand what was going on much better.

---

### Post by purelinuxuser on 2010-05-22
> **lvleph said:**
> Yep going into nm and then editing the connection allows me to change ip settings to manual. I set the ip address to the desired address, then set netmask to 255.255.255.0, gateway to 192.168.1.2 (router address), and dns server to 192.168.1.2 (router address. Now everything works.

Thank you for all your help. Your script helped me understand what was going on much better.

You're welcome!  Glad my script helped even though you didn't actually use it lol :)

---

### Post by adejoe on 2010-06-14
Sorry to open this issue again. I have followed the steps described in this thread and even used the same variables such as the I.P addresses etc but I still get an error message when I run the script...

sudo ./ap_ctl -0

My error message: 

Starting hostapd
    You can view the log at /var/log/hostapd.log
Starting dhcpd3
Internet Systems Consortium DHCP Server V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Wrote 2 leases to leases file.
ubuntu@Visteon:~/Desktop$ Multiple interfaces match the same subnet: eth0 eth1
Multiple interfaces match the same shared network: eth0 eth1
Listening on LPF/eth1/00:04:23:a3:b9:15/192.168.0/24
Sending on   LPF/eth1/00:04:23:a3:b9:15/192.168.0/24
Sending on   Socket/fallback/fallback-net
Can't create PID file /var/run/dhcpd.pid: Permission denied.



Please please please help!!

---

### Post by purelinuxuser on 2010-06-15
Got your private message ;) Please post the contents of the following files:

[LIST]
[*]/etc/hostapd/hostapd.conf
[*]/etc/dhcp3/dhcpd.conf
[/LIST]

Also, what is your problem?  Can wireless clients not connect?  If everything works properly you can probably just ignore the error message.

---

### Post by adejoe on 2010-06-16
> **purelinuxuser said:**
> Got your private message ;) Please post the contents of the following files:

[LIST]
[*]/etc/hostapd/hostapd.conf
[*]/etc/dhcp3/dhcpd.conf
[/LIST]

Also, what is your problem?  Can wireless clients not connect?  If everything works properly you can probably just ignore the error message.
Thanks for your reply...  Here's the content of my hostapd.conf

interface=eth1
driver=hostad
ssid=Testnet
channel=1
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=1234567890
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP


and dhcp.conf

option subnet-mask              255.255.255.0;
option broadcast-address        192.168.0.255;
option routers                  192.168.0.2;
option domain-name-servers      208.67.222.222, 208.67.220.220;

subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.3 192.168.0.220;
        }


The error message now is 
Starting hostapd
    You can view the log at /var/log/hostapd.log
Starting dhcpd3
ubuntu@##:~/Desktop$ Internet Systems Consortium DHCP Server V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Wrote 7 leases to leases file.
Listening on LPF/eth1/00:04:23:a3:b9:15/192.168.0/24
Sending on   LPF/eth1/00:04:23:a3:b9:15/192.168.0/24
Sending on   Socket/fallback/fallback-net
Can't create PID file /var/run/dhcpd.pid: Permission denied.


The main issue is I can't even see it as a router talk less of connecting to it as a client.
My wireless card is not supposed to detect other networks when I'm using it as the router right?
I probably even have to configure other files. I have gone through other guides and now I'm even more confused. I'm sticking with your script now though.
Looking forward to hearing from you soon

---

### Post by purelinuxuser on 2010-06-16
> **adejoe said:**
> Thanks for your reply...  Here's the content of my hostapd.conf

interface=eth1
**driver=hostad**

That should be "driver=*hostapd*", not hostad.

> **adejoe said:**
> The main issue is I can't even see it as a router talk less of connecting to it as a client.
Probably caused by the typo above.  If you are still having problems post
```
iwconfig
```

> **adejoe said:**
> My wireless card is not supposed to detect other networks when I'm using it as the router right?
Correct.

> **adejoe said:**
> I probably even have to configure other files. I have gone through other guides and now I'm even more confused. I'm sticking with your script now though.
Looking forward to hearing from you soon

Thanks, glad to see my script is useful for *someone*.:lolflag:
P.S. Use the [CODE] tag (the # sign) to identify codes.

---

### Post by adejoe on 2010-06-17
Hi, thank you once again here's my iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Visteon"  Nickname:"ipw2100"
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 02:04:23:71:F5:6E 
          Bit Rate=0 kb/s   Tx-Power:16 dBm 
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/100  Signal level=-86 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:44   Missed beacon:0

pan0      no wireless extensions.

```My network card driver is showing as the interface nickname, I have tried it as my driver in the hostapd.conf still doesn't work. I had a few dodgy configurations I found from other tutorials in the /etc/network/interface file but now I have removed them and left

```

auto lo
iface lo inet loopback

```

 Here is my ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:0d:56:df:61:2b 
          inet addr:192.168.1.43  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fedf:612b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1711977 (1.7 MB)  TX bytes:339571 (339.5 KB)

eth1      Link encap:Ethernet  HWaddr 00:04:23:a3:b9:15 
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fea3:b915/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:325 errors:39 dropped:0 overruns:0 frame:0
          TX packets:293 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36614 (36.6 KB)  TX bytes:41707 (41.7 KB)
          Interrupt:5 Base address:0x6000 Memory:fcffe000-fcffefff

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23892 (23.8 KB)  TX bytes:23892 (23.8 KB)

```No br0 in as I have removed the configurations from /etc/network/interface... Don't know what else to add at this point.
MORE SUGGESTIONS PLEASE

---

### Post by purelinuxuser on 2010-06-17
> **adejoe said:**
> My network card driver is showing as the interface nickname, I have tried it as my driver in the hostapd.conf still doesn't work.

Actually, change that driver line to
```
driver=nl80211
```
Trust me, it won't work with anything else.

Also, you *did* change these few lines at the top of ap_ctl to match your settings, right? ;)
```
#!/bin/bash

# broadcasting interface
BROADCAST="**YOURROUTERINTERFACEHERE**"

# receiving interface broadcast is connected to
RECEIVE="**YOURINTERNETINTERFACEHERE**"

if [[ $1 == "-0" || $1 == "--start" ]]
```

---

### Post by adejoe on 2010-06-17
Hi, once again I would like to thank you for your constant help but unfortunately I have tried using the driver suggestion and still does not work. I had already changed the sections in the script that you refered to. I'm still curious I seriously believe there has to be a configuration done in the /etc/network/interface file. The content I have in mine as posted in my previous post. I don't know where you are helping me from but will really appreciate getting a reply tonight but anytime will be fine LOL...

After restart and ```
 ./ap_ctl -0 
``` command entered I still get the initial error message on dhcp PID file in my first post. 

Here is my new ifconfig and iwconfig file not much change though.


```

eth0      Link encap:Ethernet  HWaddr 00:0d:56:df:61:2b  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fedf:612b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1306248 (1.3 MB)  TX bytes:351788 (351.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:04:23:a3:b9:15  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fea3:b915/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:696 errors:1 dropped:1 overruns:0 frame:0
          TX packets:63 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:224268 (224.2 KB)  TX bytes:9914 (9.9 KB)
          Interrupt:5 Base address:0x8000 Memory:fcffe000-fcffefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6380 (6.3 KB)  TX bytes:6380 (6.3 KB)

```

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"SKY35607"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:69:6C:8B:18   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

pan0      no wireless extensions.

```

HELP!!!

---

### Post by purelinuxuser on 2010-06-17
> **adejoe said:**
> 'm still curious I seriously believe there has to be a configuration done in the /etc/network/interface file. The content I have in mine as posted in my previous post.
Doubt it.  Neither me nor the OP have had to mess with that file to get the AP working.

Please post the output of
```
sudo iwconfig eth1 mode Master
```

---

### Post by adejoe on 2010-06-18
Nope doesn't work the command does not even change my iwconfig mode when I check after the command is entered. I'm getting close to giving up now.

---

### Post by purelinuxuser on 2010-06-18
> **adejoe said:**
> Nope doesn't work the command does not even change my iwconfig mode when I check after the command is entered. I'm getting close to giving up now.

So I assume there were no error messages?  If so, you may be better off configuring the AP using the "Master mode" feature of the ipw2100 driver (the mac80211 drivers that come with other wireless cards use hostapd like my script does).  Sorry, I have no expertise with the Master mode feature. :( You can probably find a tutorial online.

---

### Post by adejoe on 2010-06-19
Nope no errors but doesn't change I'll give master mode configuration a go... Thanks for you help. I'll let you know how I get on.

---

### Post by tspoon765 on 2010-12-05
Hi, I have been following the advice on this thread so far, and have been partially successful. My laptop running XP is able to see and connect to the wireless access point on my motherboard (running an Atheros card). But no internet access is available. I have disabled the firewall in XP and am not running one in 10.04 on my desk machine. I also cannot ping from laptop to desktop, or in the reverse direction.

** ipconfig** on XP gives :

Ethernet adaptor Wireless Network Connection:

                 Connection-specific DNS Suffix   . :
                 IP Address .    .    .    .    .    .    . : 192.168.1.50
                 Subnet Mask   .    .    .    .    .    . : 255.255.255.0
                 Default Gateway   .    .    .    .    . : 192.168.1.99

**ifconfig** on Ubuntu gives : 
dad@mainbox:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:01:2e:27:89:7c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe27:897c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2330970 (2.3 MB)  TX bytes:745952 (745.9 KB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34018 (34.0 KB)  TX bytes:34018 (34.0 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr 00-24-23-09-22-D3-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1151 (1.1 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:23:09:22:d3  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:23ff:fe09:22d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:531 errors:0 dropped:0 overruns:0 frame:0
          TX packets:577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66308 (66.3 KB)  TX bytes:88858 (88.8 KB)

 

my **dhcpd.conf**:

default-lease-time              600;
max-lease-time                  7200;

option subnet-mask              255.255.255.0;
option broadcast-address        192.168.1.255;
option routers                  192.168.1.99;
option domain-name-servers      208.67.222.222, 208.67.220.220;

subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.50 192.168.1.90;
        }

my **hostapd.conf**

interface=wlan0
driver=nl80211
ssid=DadsWAP
channel=1
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=1234567890
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP


 /**etc/default/hostapd**  :

RUN_DAEMON="yes"
DAEMON_CONF="/etc/hostapd/hostapd.conf"



So I get the feeling I'm close, but not quite. Any suggestions or easy fixes you can see? Any help appreciated, thanks in advance.

---

### Post by nok_bvdc on 2010-12-30
hi,

i am totally a noob to this. i am trying to set it up myself. so far i have everything you guys have posted but haven't tried it as yet. I just have a simple question would appreciate your answer

what should i place on the option domain-name-server on the dhcpd.conf file?

i mean it has 208.67.222.222 and 208.67.220.220. should i leave it as is? i wonder if it's a standardized address or if i have to insert my own dns address.

please specify.

by the way i encounter an error when running:

    ap_ctl --start

i get:

> nok@ubu-h4x0r:~$ sudo ap_ctl --start
Starting hostapd
	You can view the log at /var/log/hostapd.log
Starting dhcpd3
nok@ubu-h4x0r:~$ Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Wrote 0 leases to leases file.
Listening on LPF/eth1/00:24:2c:ac:be:6a/192.168.3/24
Sending on   LPF/eth1/00:24:2c:ac:be:6a/192.168.3/24
Sending on   Socket/fallback/fallback-net
Can't create PID file /var/run/dhcpd.pid: Permission denied.

nok@ubu-h4x0r:~$ sudo gedit /usr/bin/ap_ctl

(gedit:2413): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:2413): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:2413): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

can someone please help me. i don't know what i did wrong

---

### Post by wildmanne39 on 2012-07-31
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

