---
title: "Wireless works with wlassistant, but not manually?"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by krazyshane on 2006-06-22
Okay, this is very frustrating because I like to konw why things are happening the way they are. ](*,) 

Right now, I'm on my wireless, but I'm only able to accomplish this with wlassistant.  

Here's how I got where I'm at:
uninstalled all the pre-discovered wireless that ubuntu had, by blacklisting my wireless card and running rmmod bcm43xx (i think that was it)

At any rate, I installed ndiswrapper and have the wireless working w/ wlassistant, which is a nice program.

What makes me mad is the innability for me to manually change these settings.

If I run iwconfig, I can see my wireless adapter.
If I run iwlist scan, I can see my wireless network.  GREAT.

[B]If I try to run
iwconfig eth1 essid Home

nothing will change.  If I run iwconfig again, I still see ESSID: off/any.[/B]

Any idea why it will not take the change?  When I run and connect through wlassistant, and then run iwconfig, I see ESSID: Home

Which it should be... little help?

Shane

---

### Post by krazyshane on 2006-06-22
Here is a list of commands that I run and their outputs.

 sudo ifdown eth1
> 
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:90:96:a3:7d:6d
Sending on   LPF/eth1/00:90:96:a3:7d:6d
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67


iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-50 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


iwlist eth1 scan
> 
eth1      Scan completed :
          Cell 01 - Address: 00:11:95:6B:BB:9C
                    ESSID:"Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-49 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


sudo iwconfig eth1 essid Home
  --It takes the command
sudo iwconfig eth1 key [MY KEY]
  --It takes the command

iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


^^ Notice that neither the ESSID or the KEY have changed despite my commands.

sudo ifup eth1
> 
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:90:96:a3:7d:6d
Sending on   LPF/eth1/00:90:96:a3:7d:6d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database &#8211; sleeping.



Oh and just for shits and grins, I connected with wlassistant and ran

iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Home"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:6B:BB:9C
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-55 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Well look!  The settings I couldnt get it to take ](*,)

---

### Post by krazyshane on 2006-06-22
Upon further inspection, once wlassistant gets it working, I can manipulate it manually such as changed the essid and the key and such.

However, if I bring the card down by doing  "sudo ifdown eth1"

and then bring it back up "sudo ifup eth1", I'm in the same boat i was originally in.  it will not take any of my settings. 

Someone please any ideas here?

Shane

---

### Post by oohblue on 2006-09-15
My notebook wlan adapter is wli-cb-g54hp and I used ndiswrapper to make it work for starters.
Same problem here. I can't connect to my wlan with Administration/Networking, but wlassistant works fine...  But, to my Buffalo whr-hp-g54 AP both ways work ok. So this must be somehow dependant on access point.

Anything new on this?

---

### Post by oohblue on 2006-09-15
More info from my part.

I can connect from command line to both with the following line:
sudo iwconfig wlan0 mode managed channel 11 key open xxxxxxxxxx essid XXXXX

But if I omit the "open" from the command line:
sudo iwconfig wlan0 mode managed channel 11 key xxxxxxxxxx essid XXXXX
then I can only connect to my Buffalo AP which also works from ubuntu Networking.

So is this where System/Administration/Networking fails?

---

### Post by oohblue on 2006-09-16
To get it working I had to edit /etc/network/interfaces 
Line before:
wireless-key 1e2e3e4e5e
after:
wireless-key open 1e2e3e4e5e

---

