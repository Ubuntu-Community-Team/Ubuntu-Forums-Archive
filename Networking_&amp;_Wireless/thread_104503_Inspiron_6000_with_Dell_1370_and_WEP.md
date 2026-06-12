---
title: "Inspiron 6000 with Dell 1370 and WEP"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by dbindner on 2005-12-16
I want to report a success using ndiswrapper with my wife's Dell Inspiron 6000.  There was one gotcha (that I didn't find for hours naturally) and I wish it had been posted somewhere on the forums.  Here's what I have:

Dell Inspiron 6000
Dell 1370 Wireless 802.11b/g -- Broadcom 4318
I'm connecting to an 802.11b network with WEP.

My stumbling block?  When the laptop boots, the wireless transmitter is turned off.  Maybe those of you who do wireless a lot are familiar with this, but I had no idea.  In the BIOS, the setting was for the wireless transmitter to be enabled by key only (Fn-F2).

There's a good chance I could have had success hours earlier if I had only known to press Fn-F2!  In any event, I changed the BIOS setting to boot with the transmitter running.  I am now running successfully.

The relevant line from **lspci -n** is:

```
0000:03:03.0 0280: 14e4:4318 (rev 02)
```

For the interested, I am using the bcmwl5.inf that came with the laptop.  I found it on the WinXP partition:

# **mount | grep ntfs**
```
/dev/sda2 on /media/sda2 type ntfs (rw)
```

# **cd /media/sda2/drivers/network/addon/**

# **ls *.inf**
```
bcmwl5a.inf  bcmwl5.inf
```

# **ndiswrapper -i bcmwl5.inf**

# **ndiswrapper -l**
```
bcmwl5          driver present, hardware present
```


If you didn't keep your initial Win32 installation, I'm pretty sure you'll be successful with the drivers you can download from Dell.  I got a similar result using the AR/bcmwl5.inf from R102320.EXE I believe.

# **modprobe ndiswrapper**


Since I'm using WEP, it will be impossible to make further progress until I set the WEP key:

# **iwconfig wlan0 key ************
#** iwconfig wlan0**
```
wlan0     IEEE 802.11b  ESSID:"********"
          Mode:Managed  Frequency:2.412 GHz  Access Point: **:**:**:**:**:**
          Bit Rate:11 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:****-****-**   Security mode:restricted
          Power Management min timeout:0us  mode:All packets received
          Link Quality:100/100  Signal level:-56 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

It correctly shows my ESSID and Access point (both of which I've removed from this post).  Since I'm running a DHCP server on this network, I can simply run dhclient on this and bring up the interface:

# **dhclient wlan0**


Missing details:

Ok, to be perfectly honest, this isn't quite the setup I'm running.  Before I discovered the transmitter problem, I had tried everything.  When I was trying everything, I upgraded ndiswrapper to version 1.5 from the Debian package in Debian unstable.  I don't want to take the trouble to downgrade again.

I really think my problem was the transmitter, so I won't post the drawn-out process of upgrading the ndiswrapper package unless others really need it.

The kernel I used was 2.6.12-10-686.

---

