---
title: "Network Manager Applet"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by ldiduck on 2010-09-16
Lucid 64-bit 
My gnome network manager will not detect any wireless connections. 
If I boot from the CD it works fine, and worked from my installed version for an hour or so, now can only detect the wired LAN.

if I do this
ifconfig wlan0 down
dhclient -r
ifconfig wlan0 up
iwconfig wlan0 essid "7A2B"
iwconfig wlan0 key 00xxxxxxxxxx00000000000000
dhclient wlan0

Then I can get connected to internet via wireless,  so this is not a hardware, driver, OS, configuration, whatever issue. In fact connecting this way works but network manager STILL thinks I'm disconnected

Any thoughts? 

Thanks in advance

---

### Post by dmizer on 2010-09-16
Please post the contents of /etc/network/interfaces

---

### Post by ldiduck on 2010-09-17
cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by crokett on 2010-09-17
Here's a snippet of mine.  names changed to protect the innocent. ;)  If you are using WPA the entries after the essid one would be different.

```

auto wlan0
iface wlan0 inet dhcp
wireless-essid xxxxxx
wireless-key xxxxxx

```

Anyway, now when I am at home it autostarts it just fine. Next for me is to try and figure out location switching.

---

### Post by dmizer on 2010-09-18
Does network-manager even show a wireless card? What happens if you right click on the networking applet and select "edit connections"?

---

### Post by ldiduck on 2010-09-19
Adding those lines to /etc/network/interface does work: now I don't need to run that script I created.
However, networkmanager still does not think I'm connected to anything, nor does it show any other wireless (although iwlist xxx scanning shows dozens -- I live in a fairly populated area)

When I click edit connections it takes me to the window where I see the stuff I set up before these problems surfaced, and that it was last used five days ago.

But two more clues: Even though I manually enable the wireless connection (or through /etc/network/interfaces), when I start firefox is believes that I'm working off-line. Furthermore, vpnc connects to my office just fine (by looking at logs), but I cannot resolve any addresses there. vpnc worked fine as well before this trouble started.

And I did try updating the entire system as well, and uninstalling and reinstalling various packages.

Now I'm thinking that whatever process tells the rest of my system there is connectivity does not work, but only when going through a wireless card, since the wired lan works fine. I will have to reread my copy of "Linux Networking Internals" perhaps.

---

### Post by dmizer on 2010-09-19
Remove the stuff you have added to /etc/network/interfaces.

Have you tried disconnecting and reconnecting via network-manager. You can click on the networking icon and select "disconnect". Wait a few minutes and select "connect".

If that's still not working, please post the output of:
```
ifconfig
```

---

### Post by ldiduck on 2010-09-20
The network manager has "disconnect" greyed out. It doesn't think I'm connected in the first place. It will not find any network to reconnect to no matter what I do (other than plugging in the wired LAN cable). It has zero knowledge of any wireless connections, even though this very post is sent via a wireless connection.

ifconfig BEFORE i manually up the wlan0 interface
[FONT=Courier New]eth0      Link encap:Ethernet  HWaddr 00:1d:09:d6:4d:3b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  [/FONT] [FONT=Courier New]
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:655635 (655.6 KB)  TX bytes:655635 (655.6 KB)[/FONT]

When I do ifconfig -a, of course I see the wlan0 interface. Then I run the script I posted before, and then can see 

[FONT=Courier New]wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:66:54:bf  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fe66:54bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:277025 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:280083555 (280.0 MB)  TX bytes:32257838 (32.2 MB)[/FONT]

Naturally, before I up the wlan0 interface and iwconfig it, the bytes are 0, and there is no inet addr

---

