---
title: "WiFi/Network Manager: &quot;No working leases in persistent database - sleeping&quot;"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by Finnius on 2010-12-05
Hello,

When i try to connect to a wireless network with:
 
> sudo iwconfig <interface> essid "essid"
sudo iwconfig dhclient <interface>

I get the reply:

> ...No working leases in persistent database - sleeping.

There is a DHCP server running, all my gear is setup right, and my wireless is in range.

The simple question i ask is: **Can Network Manager interfere** with my manually requesting an ip address to produce this error - as i only get this error sometimes?
If not what else can produce this error?

Cheers ;)

---

### Post by northd_tech on 2010-12-05
Hi Finnius,

Do you know what kind of wireless interface you are running?  It should be indicated if you can copy/paste the results after running the following terminal commands (you might need to do this after a "clean" reboot if you have changed configuration very much):

```
lspci
lsusb
lsmod
sudo lshw -C network
ifconfig
iwconfig

```I think the easiest way would be to run the network-admin executable to set an IP address manually, but are you sure this is even* necessary* for your network?  

I've never had to manually configure IP addresses in order to connect to any wireless network with many versions of Ubuntu on many computers- I just let the dynamic addressing and router(s) do their thing (unless your wireless router has been configured to only recognize/allow certain IP addresses, but that is usually a MAC hardware address "recognition" in the router settings from what I recall).

Now the WPA, WEP, WEP2 wireless encryption keys are another matter, but you would be seeing a different error if that were the problem, I believe.

---

### Post by Finnius on 2010-12-05
Gday,

Thanks for the reply. I was trying to get out of posting more info as i was not on my Ubuntu machine when i originally posted...

-My wireless adapter in iwconfig:
```
ralan0    RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



-My wireless adapter in ifconfig:
```
ralan0    Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

-Your quite right encryption is not a problem
-There is no MAC address filtering on the router
-The reason i am setting it up manually is because i dislike Network Manager - i have found it to be unreliable.

I have a feeling that network manager is interfering, but intermittently...because it also tries to get an IP address through DHCP  -any ideas?

Any help would be appreciated

---

### Post by northd_tech on 2010-12-05
Well, I prefer WICD to Network Manager myself (and WICD requires you to uninstall the [Gnome] Network Manager as they conflict- or they did before Ubuntu 10.xx at least and I seem to have both on this version of 10.04.1 LTS).

[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

[http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu](http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu)

It should be available from System > Administration > Synaptic Package Manger and then search for "wicd" in the search box.  I installed all of the "wicd-..." choices while I was in there (there were about 6-8 of them as I recall, including the development, scripting, and python add-ons).

---

### Post by cmschuster on 2012-04-12
Finnius,
 
did you solve your issue?
 
i think i am having the same problem with my wifi set up.  i have the belkin 7050v3 with the RT2571W chipset (RT73).
 
posted on linuxquestions.org, but havent gotten any takers yet.
 
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/belkin-f5d7050-v3-rt73-usb-wifi-on-debian-cant-connect-to-router-939381/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/belkin-f5d7050-v3-rt73-usb-wifi-on-debian-cant-connect-to-router-939381/)
 
can you shed some light on how you solved your issue?

---

