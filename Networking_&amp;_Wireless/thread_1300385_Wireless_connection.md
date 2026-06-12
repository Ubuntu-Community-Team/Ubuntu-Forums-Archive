---
title: "Wireless connection"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by Nitewalker on 2009-10-24
how do you get your wireless to connect on ubuntu 9.10, I can not find any connection to hook to my wirless system?

---

### Post by shihabs on 2009-10-24
Click on the network icon and it will list all your networks click the one you need.
If that doesn't work, go to System>Preferences>Network Connections>Wireless and then add or edit a network. Try changing the settings for connection.

---

### Post by Eagle Nest on 2009-10-24
> **shihabs said:**
> Click on the network icon and it will list all your networks click the one you need.
If that doesn't work, go to System>Preferences>Network Connections>Wireless and then add or edit a network. Try changing the settings for connection.

I'm having similar problems. Could you outline a little more about adding or editing a network ... or point me to some documentation in this regard? 

Thanks.

---

### Post by dreamingdarkness on 2009-10-25
Not much to it to describe.
In the top right corner of the screen you should also see a network icon. If you are connected via ethernet you will see a computer monitor icon.
If you are wireless you will see an icon icon with some bars and a red 'x' in the top of it. 

Click on it (left mouse click) to get a list of wireless networks.
Click on the name of the wireless network to connect to.
If the wireless is secured, enter your password.
Internet!

---

### Post by Nitewalker on 2009-10-25
there is nothing displayed, I had it working till I upgraded to 9.10, now it doesent even show I have a wireless network

---

### Post by dreamingdarkness on 2009-10-25
You might check if NetworkManager is not running
Try going to Applications->Accessories->Terminal
type in:
```
ps aux | grep NetworkManager
```
If you get a few results, it's running and something else is awry.
If you only see one result, something like:
```
1000      4954  0.0  0.0   7528   912 pts/0    S+   13:37   0:00 grep NetworkManager
```
Your NetworkManager isn't running.
Try in terminal:
```
sudo killall NetworkManager
```
Wait a few seconds, then:
```
sudo NetworkManager
```
See if that helps out and brings the NetworkManager applet up in the top right corner.

If it doesn't come up, we're missing something!
You may need to go to System->Administration->Log File Viewer and select 'Syslog' on the left side, then scroll all the way down to see what happened when you tried to start NetworkManager.

---

### Post by Nitewalker on 2009-10-25
I uninstalled the update that I had done to get the 9.10 update, and reloaded new clean install, now it shows connection but will not go online or will not ping server.  When I ran "ifcofig" this is what I got:
To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 

nitewalker@smj:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:d4:14:9f:fd  
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:131383 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:131383 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6584075 (6.5 MB)  TX bytes:6584075 (6.5 MB) 

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:0b:01:d2  
          inet addr:192.168.1.46  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:cfff:fe0b:1d2/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:6536 (6.5 KB)  TX bytes:18468 (18.4 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CF-0B-01-D2-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

nitewalker@smj:~$ 
If I go to System,Admin,Network tools, and try and ping the 192.168.1.1, I get no returns, only time can get returns is if I ping 192.168.1.146.  When I Go to System,Admin, System test, and select test for network, it says I have no Internet connection?

I am sending this from the same machine using 9.04 version off of a USB hard drive so I know computer has right stuff and works.....:confused:

---

### Post by Nitewalker on 2009-10-25
ran "ps aux | grep NetworkManager, below is result:

nitewalker@smj:~$ ps aux | grep NetworkManager 
root       798  0.0  0.1  92476  4984 ?        Ssl  22:46   0:00 NetworkManager 
root      1881  0.0  0.0   6464  1076 ?        S    22:47   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp3/dhclient-f778d5fe-5cd0-4850-ab3f-90e92cd7620b-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0 
1000      2013  0.0  0.0   7340   976 pts/0    R+   22:47   0:00 grep --color=auto NetworkManager 
nitewalker@smj:~$

---

### Post by dreamingdarkness on 2009-10-25
Ok, 

It looks like you are actually connecting to the wireless but instead of passing packets you're getting errors back.
You're seeing it on wlan0, though it looks like ethernet's working, and you have different IPs so it is connecting ethernet.
I take it works fine from ethernet I assume?

```
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:99 errors:0 dropped:0 overruns:0 carrier:0 
```

So the packets aren't getting anywhere - what happens when you ping 192.168.1.1? Is it a Destination Host Unreachable, or another message?

Try this also:
```
sudo route -v
```
and post the results, I'm wondering if your gateway is wrong. The other option of course is that for some reason you aren't actually connecting fully to the wifi. 
Are you using DHCP from the wireless modem? Also, what wireless security is it using and are you certain there is no MAC filtering list set up?

---

### Post by Nitewalker on 2009-10-25
if using wireless only can not ping gateway 192.168.1.1 but can ping 192.168.1.24 & 46.  When ethernet cable attached can ping everything and goes online to net without problems.

results of route -v with ethernet cable attached:
nitewalker@smj:~$ sudo route -v 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
localnet        *               255.255.255.0   U     0      0        0 eth0 
localnet        *               255.255.255.0   U     2      0        0 wlan0 
link-local      *               255.255.0.0     U     1000   0        0 eth0 
default         dslrouter       0.0.0.0         UG    0      0        0 wlan0 
default         dslrouter       0.0.0.0         UG    100    0        0 eth0 
nitewalker@smj:~$ 

results of route -v when ONLY wireless, no ethernet attached:
nitewalker@smj:~$ sudo route -v 
[sudo] password for nitewalker: 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
localnet        *               255.255.255.0   U     0      0        0 eth0 
localnet        *               255.255.255.0   U     2      0        0 wlan0 
link-local      *               255.255.0.0     U     1000   0        0 eth0 
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0 
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0 
nitewalker@smj:~$ 

results of runing "iwconfig":
nitewalker@smj:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"08FX10081863"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:A6:61:C8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dreamingdarkness on 2009-10-25
Is this a DSL modem/router combo or is there a separate wireless router connected to a DSL modem? If it's a separate router connected to the modem, we have a problem with the gateway you're using. 

Also check you wireless network settings for this connection:
System-Preferences-Network Connections, click on Wireless
Should be listed as "Auto"08FX10081863", or whatever the SSID of the wireless is. 

Click on it and choose "Edit"
Make sure the "Mode" is set up as "infrastructure"
Click on ipv4 settings tab
Let me know if the Method is set to "Automatic (DHCP) " or something else. It should be set to "Automatic (DHCP)".

---

### Post by Nitewalker on 2009-10-25
It is a DSL/routher combo, settings in Sys,Preferences, Network connections, shows the correct SSID, auto DHCP, and Infrastructure.

I checked what is shown when I run ifconfig on the 9.04 system that is on a USB HD [which the wirless works correctly] and it shows;
atho=192.168.1.47
etho= no ip address shown
lo=127.0.0.1
wifio= no ip address shown

on this system which is the 9.10 it shows;
etho=192.168.1.24
lo=127.0.0.1
wlano=192.168.1.46
wmaster0= no ip address

why is there a difference between the 9.04 and 9.10 ifconfig files?

Not sure if this is of any help, but this is what is shown in my etc/network/interfaces:# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.24
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
	dns-search net

---

### Post by dreamingdarkness on 2009-10-26
Couple more things, of course!
1. What is the SSID of your DSL router/gateway? Is it the "08FX10081863" from the earlier post or should it be something else that your wireless reports as?

What kind of wireless card do you have? Built in or external? Interesting that the USB HD 9.04 pulls up an ath0 (indicating Atheros), but 9.10 is pulling up a wlan0, which is either a DIFFERENT Atheros driver, or is a different driver altogether.

If it IS an Atheros, you might have to go for a native Linux driver for Atheros chipsets - hopefully someone who has set this up already has posted a how-to for it. There is one called madwifi out there, not certain if there are other newer ones.

The /etc/network/interfaces looks like it's set up to use a static IP for ethernet, but not for wireless.

You can always try, if it's built-in and you don't know the manufacturer:
```
sudo lspci
```
Or a 
```
sudo lshw
```
I can't remember which one will do the really detailed print out, I'm @ work with only Win XP :(

Trying to think of other stuff to try but unfortunately I'm starting to run dry. Hopefully someone else out there has some thoughts, who has more specific experience with your wireless device. You probably want to make sure to post the exact wireless device that is in use, and maybe google Ubuntu (nameofdevice) and see if there are some specific threads.

---

### Post by Nitewalker on 2009-10-27
got tired of fighting the battle, reloaded 9.10 and ensured that I did not set up network by accident and get 2 IP addresses.  All works correctly and only 1 IP address, wireless right up.  I must have made a error when installing and clicked something wrong.  Thanks to all of you who assisted me in trying to fix it, much appreciated.

---

### Post by dreamingdarkness on 2009-10-27
Well, we tried! Reinstall is something I hate recommending, but it sure seems to fix the problem more effectively sometimes!

Anyhow, best of luck :)

---

