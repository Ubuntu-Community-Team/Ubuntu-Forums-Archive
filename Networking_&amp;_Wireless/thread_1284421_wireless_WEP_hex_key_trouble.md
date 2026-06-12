---
title: "wireless WEP hex key trouble"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by yasmar on 2009-10-06
Hi,

In my hotel I have been given a 'key' for wireless access, but I am unable to connect in Ubuntu. Some details:

* I connect fine in Vista, typing in the key as given
* Vista reports that it is WEP
* The proprietor told me that if I have a mac, I need to specify that the key is a 64-bit hex
* The given key is 10 digits (no letters a-f, as I would expect in a hex key)
* I am using the wireless right now via a free connection in another hotel
* I have successfully connected elsewhere using a WEP "passphrase"

I normally connect via the nm-applet 0.6.6, but since it wasn't working, I tried following the instructions here:

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [interface] essid <93>ESSID_IN_QUOTES<94>
sudo iwconfig [interface] key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed -- sudo iwconfig [interface] key open <<<----See note below
sudo iwconfig [interface] mode Managed
sudo dhclient [interface]

I tried with and without the s: prefix. There are no obvious errors output, but I do not get an ip address in the last step.

My driver is iwl3945   (I'm using an HP Pavillion dv6000 series)
[interface] is wlan0 for me

I suspect that I need to manipulate the key to get it to work -- all indications are that the wireless driver is functoning okay. If anybody has any suggestions, for resolving the problem or gaining insight into it (more debug output), I'd really appreciate it.

Thanks.

---

### Post by chili555 on 2009-10-06
If your key is 10-characters, it *is* HEX. Is Network Manager running, and therefor attempting to control your interface, at this time? Please try:```
sudo /etc/init.d/NetworkManager stop
sudo iwconfig wlan0 essid <your_essid>
```Quotes are only needed if there is a space in the name of the ESSID; like 'my router', if it's 'myrouter' no quotes are strictly needed, but won't hurt. To continue:```
sudo iwconfig wlan0 key 0123456789 open
sudo dhclient wlan0
```Do you connect or time-out? If you time-out, please let us see:```
sudo cat /var/log/messages | grep wlan0
```Thanks.

---

### Post by yasmar on 2009-10-06
Thanks for your help chili555. I really appreciate it. Unfortunately, I'm writing my thanks from Vista :(.

I am running 8.04 (Hardy Heron), and NetWorkManager is not in /etc/init.d/, so I had to kill it manually. I also killed NetworkManagerDispatcher. However, that apparently wasn't the problem.

I first tried again without killing NetWorkManager, and then I attempted to follow your directions. 
I am including below a copy of what I did, as well as info from /var/log/messages/ after both tries, and a iwlist scan. I have only changed the name of the hotel and the key. Any further insights you can give me would be great. Thanks again for your help.

```

 ps aux | grep NetworkManager
root      5123  0.0  0.0  56636  2348 ?        Ssl  19:33   0:00
/usr/sbin/NetworkManager --pid-file
/var/run/NetworkManager/NetworkManager.pid
root      5137  0.0  0.0  24156  1392 ?        Ss   19:33   0:00
/usr/sbin/NetworkManagerDispatcher --pid-file
/var/run/NetworkManager/NetworkManagerDispatcher.pid
yasmar    6764  0.0  0.0   5168   836 pts/3    R+   19:42   0:00 grep NetworkManager

-------------
try without killing NetworkManager:

# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:15:32:f5
Sending on   LPF/wlan0/00:1f:3c:15:32:f5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

-----------------------------------------------

# tail /var/log/messages
Oct  6 19:33:30 osprey kernel: [   44.175518] Bluetooth: RFCOMM socket
layer initialized
Oct  6 19:33:30 osprey kernel: [   44.175544] Bluetooth: RFCOMM TTY
layer initialized
Oct  6 19:33:30 osprey kernel: [   44.175547] Bluetooth: RFCOMM ver
1.8
Oct  6 19:34:27 osprey kernel: [   54.325416] NET: Registered protocol
family 10
Oct  6 19:34:27 osprey kernel: [   54.325935] lo: Disabled Privacy
Extensions
Oct  6 19:34:27 osprey kernel: [   54.326545] ADDRCONF(NETDEV_UP):
eth0: link is not ready
Oct  6 19:34:27 osprey kernel: [   54.327235] ADDRCONF(NETDEV_UP):
wlan0: link is not ready
Oct  6 19:53:27 osprey -- MARK --
Oct  6 19:57:03 osprey kernel: [  245.696437] NET: Registered protocol
family 17
Oct  6 19:57:11 osprey kernel: [  246.550203] ADDRCONF(NETDEV_UP):
wlan0: link is not ready

-------------------------------------------------------------
-------------------------------------------------------------

Now kill it:

# kill 5137
# kill 5123
# ps aux |grep NetworkManager
root      8124  0.0  0.0   5168   848 pts/1    R+   20:03   0:00 grep
NetworkManager

# ifconfig wlan0 down
# dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 7936
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:15:32:f5
Sending on   LPF/wlan0/00:1f:3c:15:32:f5
Sending on   Socket/fallback

# ifconfig wlan0 up
# iwconfig wlan0 essid "Fauxname Hotel"
# iwconfig wlan0 key 0123456789
# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:15:32:f5
Sending on   LPF/wlan0/00:1f:3c:15:32:f5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

# tail /var/log/messages
Oct  6 19:33:30 osprey kernel: [   44.175547] Bluetooth: RFCOMM ver
1.8
Oct  6 19:34:27 osprey kernel: [   54.325416] NET: Registered protocol
family 10
Oct  6 19:34:27 osprey kernel: [   54.325935] lo: Disabled Privacy
Extensions
Oct  6 19:34:27 osprey kernel: [   54.326545] ADDRCONF(NETDEV_UP):
eth0: link is not ready
Oct  6 19:34:27 osprey kernel: [   54.327235] ADDRCONF(NETDEV_UP):
wlan0: link is not ready
Oct  6 19:53:27 osprey -- MARK --
Oct  6 19:57:03 osprey kernel: [  245.696437] NET: Registered protocol
family 17
Oct  6 19:57:11 osprey kernel: [  246.550203] ADDRCONF(NETDEV_UP):
wlan0: link is not ready
Oct  6 20:05:03 osprey kernel: [  312.226726] ADDRCONF(NETDEV_UP):
wlan0: link is not ready
Oct  6 20:05:33 osprey kernel: [  315.639033] ADDRCONF(NETDEV_UP):
wlan0: link is not ready


# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :

[...]
          Cell 03 - Address: 00:18:D2:00:54:57
                    ESSID:"Fauxname Hotel"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/100  Signal level=-71 dBm  Noise
                    level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6
                    Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36
                    Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001358e8f916
[...]


```

---

### Post by yasmar on 2009-10-07
Just to follow up, I am now connected, but I still don't know what the problem was. Last night I kept losing the connection from Vista, and eventually it seemed to stop working altogether. Vista would claim that I was connected, but I wasn't, or at least there was no DNS or something. Anyway, it was evidence that the problem may not be entirely on my end.

I then tried again in Ubuntu, using the nm-applet, and it actually accepted the key! But I couldn't get out -- just as in Vista. This morning I boot into Ubuntu and the wireless comes on automatically and everything just works.

Btw. I had noticed that I'd forgot to specify 'open' after the key in my attempt to follow chilli555's directions above. I did try that after, but with the same negative result.

Thanks again for the advice chilli555.

---

