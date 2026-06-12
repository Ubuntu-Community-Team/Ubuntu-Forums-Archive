---
title: "Wireless connection cannot obtain IP with DHCP"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by dsacchetto on 2010-02-16
I have been sleepless for days with this issue.
I have router and wireless card Linksys. Driver are installed correctly for wireless card.
Using WifiRadar I can see the access point is detected.
DHCP woks perfectly for wired lan.
However when I try to connect to the detected access point the ip addres is never retrieved and the connection never established.
I tried most of he basic instructions posted on ubuntu forums, but the problem doesn't seem to be with basic configuration: driver, essid, wep key, etc..
The problem seems to be with DHCP not able to retrieve an IP address from the DHCP server of the router. Of course the router works file with other laptops (windows based) that have wireless card.
I also tried the Network Connections setup part of ubuntu. That one shows the access point by its essid name in the list of wireless network, but when I try to connect it takes sometime and eventually asks for the wep key, which I provide and then it times out and keep asking it. The same wep key works for other pcs.
Can't figure it out. I am using ubuntu 9.10. Some more details are the following:

1) Here the output from the log file: /var/log/wifi-radar.log

2010-02-15 15:35:52,644: CRITICAL: connect_to_network: DHCP client not found, please set this in the preferences.

Of course it is set ... and dhcp client works for wired lan anyway.

2) diego@mysuperlaptop:/var/run$ sudo iwlist wlan0 scan
[sudo] password for diego: 
wlan0     Scan completed :
          Cell 01 - Address: 00:0E:51:CB:6A:3F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"mysuperrouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d4f49a189
                    Extra: Last beacon: 1172ms ago
                    IE: Unknown: 0007616E74656E6E61
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD050010180102

3) diego@mysuperlaptop:/var/run$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"mysuperrouter"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4) My /etc/network/interfaces:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
wireless_essid mysuperrouter
wireless_mode Managed
wireless_key s:keyinputed

5) ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0b:ce:32:a3:0f  
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe34:a30f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29107984 (29.1 MB)  TX bytes:4480528 (4.4 MB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4802 (4.8 KB)  TX bytes:4802 (4.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:51:CB:6A:3F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00:0E:51:CB:6A:3F-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I tried everything I could think about in the UI windows setting (WifiRadar and Wireless Network Connections) a well in the config files from the shell. I just don't get what the deal is. I am pretty sure it is a DHCP issue but can't figure out what.

Any help very well appreciated.

Thanks,
Diego

---

### Post by chili555 on 2010-02-16
> 4) My /etc/network/interfaces:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
wireless_essid mysuperrouter
wireless_mode Managed
wireless_key s:keyinputedI suggest:```

auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto [COLOR="Red"]wlan0[/COLOR]
iface wlan0 inet dhcp
wireless-essid mysuperrouter
wireless-key s:keyinputed
```Also, the [COLOR="Red"]s:[/COLOR] implies an ASCII WEP key which is pretty rare, but not impossible. Does it have 5 or 13 characters?

If it has 10 or 26 characters, then it's HEX and the s: should be omitted.

The mode is managed by default, so there is no need to declare it again.

Finally, it is unlikely this will work with Network Manager installed. Please completely remove it.

---

### Post by dsacchetto on 2010-02-17
Thank you very much for the response.
I tried the way you proposed, removing th Network Manager. That did seem to cause some system instability (somehow, after awhile I reboot the pc it gets stuck forever on I/O operation and I have to reboot if I want to be able to use the system). Very strange.
Anyway, the interfaces file now is:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

wireless_essid mysuprrouter
wireless_key 1F7214221F

but when I reboot the network the wireless doesn't complete succesfully:

diego@myspuerlaptop:~$ sudo /etc/init.d/networking restart
[sudo] password for diego: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1357
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:cd:34:a3:0f
Sending on   LPF/eth0/00:0b:cd:34:a3:0f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1580
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0c:41:2d:34:4f
Sending on   LPF/wlan0/00:0c:41:2d:34:4f
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:cd:34:a3:0f
Sending on   LPF/eth0/00:0b:cd:34:a3:0f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.118 from 192.168.1.1
DHCPREQUEST of 192.168.1.118 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.118 from 192.168.1.1
bound to 192.168.1.118 -- renewal in 237 seconds.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0c:42:2d:24:4f
Sending on   LPF/wlan0/00:0c:42:2d:24:4f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
diego@mysuperlaptop:~

The last two lines are the poblem. The eth0 however works... (which is why I can write this post).

Thank you.

---

### Post by chili555 on 2010-02-17
I don't think the system normally wants two IP addresses at once, that's why I commented out auto eth0 in interfaces. > #auto eth0
iface eth0 inet dhcpIs the behavior improved with the ethernet cable detached?

---

### Post by grandmaster on 2010-02-17
Just rebooted and im on wireless.
i hope this helps your issues dsacchetto

---

### Post by dsacchetto on 2010-02-18
Tried all the good suggestion, commenting out the eth0, unplug the network cable and rebooting the system. But still no network available. Localhost and hostname can be pinged, but I can't ping the router. However doing ifconfig it seems like the router is found.
The driver of the wireless card seems ok B45...
I wonder if the driver although installed and apparently working is the one causing the issue. I don't know what to look at anymore.. Either I try a different wireless card, or try a different flavor of linux or go back to the slow and virus catcher of windows. Hope I don't have to go to the last one...

Thanks,
Diego

---

### Post by chili555 on 2010-02-18
Please detach the wire and do:```
sudo ifconfig eth0 down
sudo dhclient wlan0
```What is the result?> "[COLOR="Red"]mysuperrouter[/COLOR]" > wireless_essid [COLOR="Blue"]mysuprrouter[/COLOR]Is it spelled correctly in your *interfaces* file?

---

### Post by Julita on 2010-02-18
I have heard that wicd works better with wireless. Try installing it and see if you can connect to wireless.

---

### Post by dsacchetto on 2010-02-18
Thank you for the patient reply. Here the result of your inquiry:

diego@mysuperlaptop:~$ sudo ifconfig eth0 down
[sudo] password for diego: 
diego@mysuperlaptop:~$ 
diego@mysuperlaptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0c:41:2d:34:4f
Sending on   LPF/wlan0/00:0c:41:2d:34:4f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
diego@mysuperlaptop:~$ 

As you see it seems like it cannot configure the network. But I don't know why. It doesn't seem like a driver issue. The lights on the card are up and bright. Maybe the driver just doesn't behave correctly? Or maybe it is just a simpler issue... but I can't figure out what. 

thanks.

---

### Post by dsacchetto on 2010-02-18
By the way.. the EssID is correct. I just happened to misspell it in the forum, but it is correct in the config files (interfaces).

thnaks.

---

### Post by dsacchetto on 2010-02-18
Very nice the wicd tool. I installed and router is found, authentication went though then it moved to the step of obtaining the IP address. it hangs there for awhile and then give the message it can't get one. Look attached screen shots.
I am still convinced something wrong with the dhcp process. But because it works for the wired one, I am afraid it is something with the driver of the card.

Diego

---

### Post by dsacchetto on 2010-02-18
reattached screen shot

---

### Post by Julita on 2010-02-19
Sometimes you have to disable the ethernet for wireless to work properly. Try this: System->Administration->Networking, properties for eth0, uncheck the box and reboot. (You can check this box when this connection is needed; you will just need to check it.)

---

### Post by dsacchetto on 2010-02-24
Finally I resolved the problem... here how I did it. Based on the principle that if I can't make it I'll fake it, I went on ubuntu site to find out which are the wireless cards that work out of the box. At the same time I looked how much I could find them for on ebay.
Turned out that the D-Link WNA-1330 works great out of the box. No driver issue, no headakes, no bad words... nothing. Price $7.95 shipping included. I figured it was well worth my time and peace.
Got one 3/4 days later and here I am typing in this forum through my wireless connection.

Thanks everybody for trying to solve the issue with my Linksys card ... which is going on ebay right after I am done with this.

Diego

---

### Post by Anhedonia on 2010-02-25
Im getting the same issues with my HP 1330ap intel 915 chipset, with an onboard ipw2200.

The absolutely stupid thing is this is with commandline text only server, which i thought was the pro option.

When i install with a GUI it works perfectly.... *slaps forehead* 

I even tried setting it all up statically and it still cant communicate with the network. (other then scanning AP's)

My card has supposedly been working with linux for 5 + years so, the buy a new card option for me seems like a copout.

---

### Post by dsacchetto on 2010-02-27
yeah, you are right about that... It felt like cheating going on ebay to look for a new card. I do like the challenge, but hey my time is more worth then 8 bucks.

---

### Post by nivesh on 2010-02-27
i have the exact same problem with wicd, hangs on obtaining the ip address and the just fails. the curious thing is, i just installed wicd because i wanted to run e17. on gnome, even now !!! network manager running my wireless card works flawlessly ! 

so i dont know how the card could be the problem.

---

### Post by Julita on 2010-02-28
Well, it's great when you can change the card in a laptop, or in a desktop it is even more convenient, but when you can't? If there are drivers available, one should dig deeper to know why something doesn't work. I had problems with wicd that wouldn't acquire IP, I didn't particularly like NetworkManager, so now I connect to my wireless through terminal. For that, you have to remove networkmanager or wicd. So,
sudo ifconfig wifi_interface up (you can find it out launching in terminal: 
lshw -C network)
sudo iwlist wifi_interface scanning (you will see essid of available networks)
sudo iwconfig wifi_interface essid name_from_the_list
sudo dhclient
To avoid typing sudo every time, use once
sudo su

In /etc/network/interfaces you have to uncomment the lines, and replace the existing ones with
auto wifi_interface
iface wifi_interface inet dhcp (if you use dhcp, that is)
As has been stated before, replace wifi_interface with relevant one (wlan0, wifi0 etc, whatever is used in your system; in my case it is ra0 because I have Ralink)

---

