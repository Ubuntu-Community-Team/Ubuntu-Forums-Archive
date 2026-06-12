---
title: "Really strange wlan0 error... please help!"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by tomaspineda on 2005-12-14
I can't get my wireless LAN to work after a fresh installation of Ubuntu Breezy. The connection is deactivated on startup (according to GNOME's network applet), and when I activate it, it shows signal (good signal BTW, and it's moving so it's "alive")... but wlan0 still says "Disconnected" and nothing works (not even a simple ping to my gateway).


- my WLAN device is a USB ZD1211, and its driver seems to be pre-installed and working correctly (it appears on lsmod).
- GNOME's Network Settings (network-admin) had some trouble detecting it as wlan0 on first boot, but I used ifconfig to activate it once, and then went back to network-adming to configure its parameters via GUI.
- no I didn't make mistakes with the WEP key or any other data I had to input in network-admin; I checked everything several times.
- I did a iwlist scan and it seems like wlan0 sees my Access Point correctly (with its ESSID) and everything.
- I already deactivated eth0 both in network-admin and /etc/network/interfaces.
- sometimes iwlist channel says my device is working on channel 11 (while the Access Point uses 6), but I can't change it with iwconfig (it says "Invalid argument" no matter what I do)... but eventually it auto-detects channel 6, so I guess that's not the problem.
- pretty much the same happens when I activate the device in the commandline (with ifconfig ) instead of graphically (via network-admin).

Well that's it. I really hope someone can help me, because it's the strangest error I've ever seen (everything seems to work, but it doesn't!), and I haven't read anything like this, anywhere (and believe me, I've searched more than enough).

Thanks in advance!

Tomas Pineda
[email]tomas.pineda@gmail.com[/email]

---

### Post by Lambert on 2005-12-14
Post the output of these two commands here after trying to activate the connection.

iwconfig
ifconfig

What I'm looking for in iwconfig is that you are associated with the access point.
What I'm looking for in ifconfig is that you have an ip address assigned to the interface.

---

### Post by tomaspineda on 2005-12-14
root@breezy:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"foo"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:10:CE:55:82
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:****-****-**   Security mode:open
          Power Management:off
          Link Quality=76/92  Signal level=38/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.





root@breezy:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3541986 (3.3 MiB)  TX bytes:3541986 (3.3 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:02:72:4E:2F:4C
          inet addr:192.168.1.53  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:72ff:fe4e:2f4c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27568 (26.9 KiB)  TX bytes:0 (0.0 b)



Hope this helps, and thank you.

---

### Post by harisund on 2005-12-14
Ok here is what I do on my machine. 

iwconfig wlan0 essid <Insert your access point ESSID here> 
iwconfig wlan0 mode Managed
iwconfig wlan0 key restricted <Your WEP key if you have one>
dhclient wlan0

ofcourse you would follow it with sudo if it is required. 

this is how I connect using the device, and since your device is indeed recognized, I would think this works for you too. 

Regards, hari

---

### Post by Lambert on 2005-12-14
Ok, everything looks good here, but you can't ping router....
So let's look at one more command

route

you should get something like this

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

If it's blank then a route needs to be set up

---

