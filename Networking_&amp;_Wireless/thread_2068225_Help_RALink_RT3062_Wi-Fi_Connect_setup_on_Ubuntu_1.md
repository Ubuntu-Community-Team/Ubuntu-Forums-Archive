---
title: "Help RALink RT3062 Wi-Fi Connect setup on Ubuntu 12.04 Server"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by ddomain1 on 2012-10-08
Running Ubuntu 12.04 Server (3.2.0-29-generic-pae) on i686 desktop
Trying to get RAlink RT3062 PCI card connected to wireless router - no luck. Other devices (phone, laptop) see wireless network and work Ok. Ethernet works perfectly - network cable is now disconnected from this desktop.
Successfully installed driver from RAlink site using previous post - so wireless card is now '***ra0***', and module loaded is '***rt3562sta***'

I have attached .zip file has output of various commands: *uname, lshw, lspci, lsmod, syslog, ifconfig, iwconfig, iwlist*, as well as *interfaces* and *wpa_supplicant* config files.

Followed other posts but cant' seem to get this working.
Any help here is appreciated.

---

### Post by ddomain1 on 2012-10-09
**UPDATE:**
I seem to have gotten the card working. It successfully gets an IP via DHCP from the router. Querying the router from laptop shows the IP assigned to the ubuntu-box. Good!
Bad thing is I can only ping that IP only..not even the GW, much less for beyond that.
On the final hurdle - Did I miss something?

```
eth0      Link encap:Ethernet  HWaddr 8c:89:a5:e4:97:85  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ra0       Link encap:Ethernet  HWaddr c8:3a:35:cc:6a:ce  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43761 (43.7 KB)  TX bytes:6923 (6.9 KB)
          Interrupt:21
```

```
netstat -anr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG        0 0          0 ra0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 ra0
```

As shown below, the result of *iwconfig* shows 'Not Associated' with router, yet I got an IP addr.

```
ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by varunendra on 2012-10-11
Are you sure it gets the IP address without cable connection? Is it a repeated behaviour? I'm asking because access point 'Not Associated' clearly means no connection at all! Or maybe it got connected for a few seconds, but got disconnected 'after' getting IP from the dhcp.

Please run the following command (just copy-paste in terminal) to automatically download and run 'wireless_script' (courtesy wild man, dave and other who contributed):
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
This will create a "netinfo.txt" file in your home directory. Post back the contents of that file here. Hopefully, it will give us some useful clues.

---

### Post by ddomain1 on 2012-10-15
Thanks for your reply.
I walked back through all my steps in detail, and I got the card to work. Can't say what I was doing wrong.

However, the card only stays connected for 1-2mins to a max of ~5mins, then it disconnects everytime, and only a shutdown/restart will make it re-connect.

I will mark this thread as solved though, and go through some troubleshooting before I raise a new thread.

Thanks again.

---

### Post by varunendra on 2012-10-15
If it's getting disconnected every 5 min or less, then I won't call it as 'Solved'.

I think you can remove the 'Solved' prefix if you wish to continue troubleshooting in this thread. If you decide to start a new one, I'd suggest to post its link here so that anyone watching this one (including me of course) could follow it.

In any case, if you need help with wireless, you should post the output of the script I suggested above to provide a detailed status report of the wireless & networking. Also, try anything AFTER trying an update if possible. [COLOR="DarkRed"]Who[/COLOR] knows if a newer package already contains a fix. :)

Good luck!

---

### Post by ddomain1 on 2012-10-16
Ok I altered thread to UNSOLVED.
I have attached the results: one when I'm connected, and the other when I'm not.
Also @varunendra - could you clarify ```
"*Also, try anything AFTER trying an update if possible. How knows if a newer package already contains a fix.*"
```

---

### Post by chili555 on 2012-10-16
Would you please amend your /etc/network/interfaces file as follows:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet static
	# address 192.168.1.16
	# netmask 255.255.255.0
	# network 192.168.1.0
	# broadcast 192.168.1.255
	# gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	# dns-nameservers
	# dns-search mark.local

auto ra0
iface ra0 inet dhcp
         wpa-ssid linksys
	 wpa-psk <WPA key removed>
#        wpa-ap-scan 1
#        wpa-proto WPA
#        wpa-pairwise TKIP
#        wpa-group TKIP
#        wpa-key-mgmt WPA-PSK
```Then reload the details:```
sudo ifdown ra0 && sudo ifup ra0
```Does it stay connected any better?

---

### Post by varunendra on 2012-10-17
> **ddomain1 said:**
> Also @varunendra - could you clarify > Also, try anything AFTER trying an update if possible. [COLOR="DarkRed"]How[/COLOR] knows if a newer package already contains a fix.

Oops! it was a typo. I think that's what made it unclear.. I meant to do an update (while you are connected via ethernet), BEFORE trying anything else. Because sometimes, when there is a driver or firmware problem, it is likely that an updated version may contain bug-fixes and thus be more stable.

As for now, please do what *chili555* suggested.

---

### Post by ddomain1 on 2012-10-17
Yes! I think that recommendation did the trick.
Thanks for the heads up here...managed to complete an entire *apt-get update*, which wasn't possible before.
I will now install GUI and browser and continue see for next couple days.

Thanks, [COLOR="Navy"]@chili555[/COLOR] && [COLOR="navy"]@varunendra[/COLOR]

Also, [COLOR="navy"]@chili555[/COLOR] I would like to understand thinking behind that troubleshooting tidbit thanks.

---

### Post by chili555 on 2012-10-17
> Also, @chili555 I would like to understand thinking behind that troubleshooting tidbit thanks.It's very sophisticated and I'm sure you will be impressed: When I set up my */etc/network/interfaces* file for WPA2-PSK, being a bit lazy, I tried as few lines as possible. This combination works perfectly for me:```
auto wlan0
iface wlan0 inet dhcp
         wpa-ssid <my_ssid>
	 wpa-psk <WPA key removed>
```Simple, eh? I am happy to see it is working for you as well.

As Thoreau says, "Simplify, simplify!"

---

