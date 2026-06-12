---
title: "Installing USB wireless adapter"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by Theophylact on 2010-02-03
Okay, I'm a *super*noob at this, but:

I've got a Rosewill [RNX-EasyN1]("http://www.rosewill.com/products/1280/productDetail.htm") USB adapter, and I want to install it on my laptop (currently running Karmic). I've downloaded Rosewill's Linux driver (the site *says* the adapter isn't supported in Linux, but they do provide a driver).

What's the drill for getting the laptop to recognize the dongle so I can install? How do I use the driver? (I hate to say it, but plug-and-play has its advantages...)

---

### Post by chili555 on 2010-02-03
We may have a driver already! Please insert the device, open a terminal and do:```
lsusb
```Post the result.

PS - I was afraid it was gonna be a Realtek!

PPS - I could get to 4,000 posts just on this!!

---

### Post by Theophylact on 2010-02-04
Looks like you got to 4,000 already.

---

### Post by brawd on 2010-02-04
I did this yesterday. I left clicked on the network symbol at the top right of the desktop. That showed me that it had already found my Orange livebox.
I clicked on that to switch it on.
Then all I had to do was right click and put in my wep number.

It seems so straight forward now, but I was excited that it worked. Lol.

Hope it is as simple for you.

regards,

brawd

---

### Post by chili555 on 2010-02-04
> **Theophylact said:**
> Looks like you got to 4,000 already.Yessir! And all on Realteks! So, is yours recognized in *lsusb*?

---

### Post by Theophylact on 2010-02-05
Yes, it is. Now I'm having a problem connecting to my home wireless network, and I'm not sure why. I name the network, and use the passphrase, but it doesn't connect.

---

### Post by Theophylact on 2010-02-05
When I look at the network in Windows, it says the wireless connection is WPA2-PSK (which I assume is "private shared key") and encryption is AES.

---

### Post by chili555 on 2010-02-05
> **Theophylact said:**
> Yes, it is. Now I'm having a problem connecting to my home wireless network, and I'm not sure why. I name the network, and use the passphrase, but it doesn't connect.Are you clicking the Network Manager icon? Please see attached.

---

### Post by Theophylact on 2010-02-05
Yes.

My Linksys wireless router identifies my network's name/SSID, its security as WPA2 Personal, and encryption as TKIP+AES.

When I give the SSID, and identify Wireless security as WPA & WPA2 Personal, and give it the password, it returns the "Authentication required by wireless network" box.

"Wireless Networks" are greyed out in network manager; I have to try "Connect to Hidden Wireless Network..."

---

### Post by Theophylact on 2010-02-05
If I go into System/Preferences/Network Connections/Wireless and edit the network by name, it still doesn't work, whether I choose "infrastructure" or "ad-hoc". And *now *Network Manager doesn't show wireless networks at all.

---

### Post by chili555 on 2010-02-05
Do you actually have a wireless interface, that is, is a driver installed and operating? Please open a terminal and post:```
iwconfig
lsusb
```Thanks.

---

### Post by Theophylact on 2010-02-06
Apparently not.

lsusb gives

> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root huband iwconfig gives> lo     no wireless extensions.

eth0     no wireless extensions.I have downloaded the Rosewill driver, as I said, but I'm not clear on how to install it.

---

### Post by chili555 on 2010-02-06
If *lsusb* doesn't even detect the device when it's inserted, then the driver will not help. Please remove the device, re-insert it and run:```
lsusb 
```Thanks.

---

### Post by chili555 on 2010-02-06
I downloaded the Linux driver on their site and it's evidently a Ralink RTL3070 chipset. There are several threads going on here about how to get it installed. If we can see the device ID from *lsusb*, we will have a much better idea of how to proceed.

The driver on their site is not the most current version of RTL3070, so it will be of doubtful use to us.

---

### Post by Theophylact on 2010-02-06
Okay; when I reinsert the device and rerun lsusb, I get

> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp.
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubNow what?

---

### Post by chili555 on 2010-02-06
This device is grabbed by two competing drivers and they don't work and play well together, so we must do some tinkering under the hood. Please go to Applications -> Accessories -> Terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist rt2800usb
```Proofread, save and close gedit.

Now, in the terminal, do:```
sudo rmmod -f rt2800usb
sudo modprobe rt2870sta
```Does the light on your Rosewill start blinking? Now check again for networks in Network Manager. Can you click and connect?

---

### Post by Theophylact on 2010-02-07
Not blinking. But when I remove it and reinsert, Network Manager lets me get in via Hidden Wireless Network, so I guess it works.

(Why is there now a folder for sudo on my desktop, and how do/should I get rid of it?)

---

### Post by chili555 on 2010-02-07
> Why is there now a folder for sudo on my desktop, and how do/should I get rid of it?What's in it? If you are very sure you don't want or need it, simply right-click it and select Move to Trash.

---

### Post by Theophylact on 2010-02-07
It was empty, so I trashed it.

When I reboot, I go back to the previous situation: I get the greyed-out "Wireless Networks", the "Connect to Hidden Wireless Network", the "Authentication required by wireless network" and so on; no connection. 

Running lsusb gives me> Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp so I *should* be okay, no?

Running iwconfig gives> lo     no wireless extensions.

wmaster0      no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID: " "
     mode: Managed Frequency: 2.412 GHz Access Point: Not -Associated
Tx-Power=16 dBm
Retry  long limit:7    RTS thr: off   Fragment thr: off
Power Management: on
Link quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0 Missed beacon:0


---

### Post by chili555 on 2010-02-07
> wlan0 IEEE 802.11bgn ESSID: " "
mode: Managed Frequency: 2.412 GHz Access Point: Not -Associated
--- snip ---This says you have a working wireless interface that's simply not connected to anything. > when I remove it and reinsert, Network Manager lets me get inDoes it work better if you remove and re-insert it? I wonder why it takes that to wake up NM.

---

### Post by Theophylact on 2010-02-07
Network Manager is aware, but it still won't let me connect. I name the network, specify wireless security correctly, and give it the password, but it keeps returning the "Authentication required..." box.

---

### Post by Theophylact on 2010-02-07
If I *create* a new network connection with the right name, it *does* connect.

It then gives me a "connection established" for the named network. Network Manager shows the terminal icon, the antenna icon with a lock, and three signal bars, but I can't get online.

---

### Post by chili555 on 2010-02-07
If you right-click the NM icon and edit connections, is 'connect automatically' selected?

i wonder if NM is correctly writing *resolv.conf*. May we please see:```
cat /etc/resolv.conf
```When you create a new network connection, are you asked for DNS nameservers?

---

### Post by Theophylact on 2010-02-07
NM connection information for Active Network Connections:>  [my wireless network name]
Interface: 802.11 WiFi (wlan0)
Hardware Address: 00:02:6F:6C:FA
Driver: rt2800usb
Speed: unknown
Security: WPA/WPA2

IP Address: 10.42.43.1
Broadcast Address: 10.42.43.255
Subnet mask: 255.255.255.0

---

### Post by chili555 on 2010-02-07
> IP Address: 10.42.43.1Did you assign this address or did your router assign it by DHCP? A x.x.x.1 address would typically be that used by the gateway, not by a client.

---

### Post by Theophylact on 2010-02-07
cat /etc/resolv.conf gives
> # Generated by NetworkManagerAnd yes, "connect automatically" is selected, and I'm not asked for DNS servers (presumably because that's handled by my router). My router assigns by DHCP.

---

### Post by chili555 on 2010-02-07
Your router and NM should be properly completing *resolv.conf*. We'll have to figure out why or why not. In the meantime, please run:```
route -n
```Determine the IP address of the gateway. I am guessing it might be 10.42.43.254. Please verify. Please do:```
sudo gedit /etc/resolv.conf
```Change it to be:```
# Changed by Theophylact 
nameserver 10.42.43.254 
```Substitute your gateway address here, if it's not x.254. Proofread, save and close gedit. Now do:```
ping -c3 www.google.com
```Are you now able to go on line?

---

### Post by Theophylact on 2010-02-07
route -n returns *two* values:

Destination[COLOR="White"]...[/COLOR]Gateway[COLOR="White"]...[/COLOR]Genmask
10.42.43.0[COLOR="White"]....[/COLOR]0.0.0.0[COLOR="White"]...[/COLOR]255.255.255.0
169.254.0.0[COLOR="White"]...[/COLOR]0.0.0.0[COLOR="White"]...[/COLOR]255.255.0.0

---

### Post by chili555 on 2010-02-07
But under gateway, it simply shows 0.0.0.0. This just gets curiouser! Please do:```
sudo route add default gw 10.42.43.254
```Substitute whatever the IP address of your router is. Can you determine that on another computer?

I am puzzled why NM is not doing all this for you. If your card was unable to get an IP address at all, then I'd understand.

---

### Post by Theophylact on 2010-02-07
Did gedit.

Pinging Google gives unknown host.

NM *still* thinks I have an active connection to my named network. But I can't get onto the net.

---

### Post by Theophylact on 2010-02-07
My *router*'s address is 192.168.1.1, but I'm not sure that's what's wanted here.

---

### Post by chili555 on 2010-02-07
If you get your IP address by DHCP, I wonder how it is that your router, 192.168.1.1, gave you this:> IP Address: 10.42.43.1
Broadcast Address: 10.42.43.255
Subnet mask: 255.255.255.0 Am I just having a bad dream? Maybe you are really my old computing 101 instructor from college playing a trick. Remember punchcards?

---

### Post by Theophylact on 2010-02-07
Damfino. I may have set Windows to specify a DNS server. (checks) Nope; IP and DNS are obtained automatically.

(I *do *remember punchcards; I worked at IBM the summer of 1961.)

---

### Post by Theophylact on 2010-02-07
I just can't understand why mouseover says "Wireless network connection '[network name]' active" but I'm not getting through.

---

### Post by chili555 on 2010-02-07
Damfino! Please let me see:```
ifconfig
iwconfig
```Now I have to go back to UMKC and start learning all over again.

---

### Post by Theophylact on 2010-02-07
> **chili555 said:**
> If you get your IP address by DHCP, I wonder how it is that your router, 192.168.1.1, gave you this:> IP Address: 10.42.43.1
Broadcast Address: 10.42.43.255
Subnet mask: 255.255.255.0 Am I just having a bad dream? Maybe you are really my old computing 101 instructor from college playing a trick. Remember punchcards?I'm sure my router specifies my ISP's address. It has my username (which includes the ISP, earthlink.net) and my password, and the DNS server probably resolves the ISP name automagically.

---

### Post by chili555 on 2010-02-07
So that the router can do effective network address translation (NAT), it should take the ISP's external IP address and hand out 192.168.x addresses to all the computers that associate inside the LAN.> I may have set Windows to specifyIs the IP address of the Windows machine 10.x or 192.x? Are these two separate computers or dual booting or, horrors, a Windows host and an Ubuntu virtual machine with a bridge network?

---

### Post by Theophylact on 2010-02-07
Here's ifconfig:

UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:02:6f:6f:6c:fa  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::202:6fff:fe6f:6cfa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:62956 (62.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-02-6F-6F-6C-FA-36-66-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Here's iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Chaotics Airnet"  
          Mode:Ad-Hoc  Frequency: 2.412 GHz  Cell: 72:92:1B:79: D9:11   
          Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2010-02-07
> wlan0 IEEE 802.11bgn ESSID:"Chaotics Airnet"
Mode:[COLOR="Red"]Ad-Hoc[/COLOR]Do you, intentionally or accidentally, have an internet connection sharing arrangement with the Windows computer? I suggest you go to the NM icon, disconnect, then do:```
sudo iwconfig wlan0 mode managed
```Then try to connect again, this time, hopefully to the router. Run:```
ifconfig
``` after you connect to verify a 192.x address and see if you can get to the internet.

---

### Post by Theophylact on 2010-02-07
I keep trying to disconnect, and it keeps showing a whole bunch of gibberish networks. Trying to set mode gives me > 
Error for wireless request "Set Mode" (8806):
SET failed on device wlan0 ; Device or resource busy.

---

### Post by Theophylact on 2010-02-07
Okay; I *disabled* wireless, ran set mode, and reenabled wireless.

Running ifconfig gives the same 10.42.43.1 inet addr as before, and I have no internet connection. iwconfig recognizes the mode as "managed".

---

### Post by Theophylact on 2010-02-07
I'm going to give this a rest for a while; real life has other imperatives. Back in a couple of days.

---

### Post by error420 on 2010-03-20
> **chili555 said:**
> This device is grabbed by two competing drivers and they don't work and play well together, so we must do some tinkering under the hood. Please go to Applications -> Accessories -> Terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist rt2800usb
```Proofread, save and close gedit.

Now, in the terminal, do:```
sudo rmmod -f rt2800usb
sudo modprobe rt2870sta
```Does the light on your Rosewill start blinking? Now check again for networks in Network Manager. Can you click and connect?

Tried this but failed. Also blacklisting does not work. Neither does trying to remove the mod. 

~$ sudo rmmod -f rt2800usb
ERROR: Removing 'rt2800usb': No such file or directory

After doing -l is still get...

laptop:~$ sudo ndiswrapper -l

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2870 : driver installed
	device (148F:2770) present (alternate driver: rt2800usb)

Wireless always shows up however you still can't connect. This light also blinks several times.

---

### Post by chili555 on 2010-03-20
Do you have the same device and the same situation as Theophylact?

---

