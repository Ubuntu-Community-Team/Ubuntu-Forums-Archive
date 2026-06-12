---
title: "t-mobile 3g modem"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by kpgalligan on 2009-03-27
I picked up the new t-mobile 3g modem (USA modem).  The actual model is Huawei UMG181.  I've got 15 days to see if I can get it working with ubuntu.  I have a dual boot into windows and got it working (after several phone calls.  Turns out I needed to use a different "profile".  They didn't have their tech support really all that ready for the new product).

Anyway, no luck so far.  I tried setup similar to E220...

[https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220)

It gets pretty far.  Even actually looks like it gets an IP address, but can't really connect to anything.  Before I spend many more hours on this, is there anybody out there who's tried this, or has some insight?

Thanks in advance,
-Kevin

---

### Post by GeorgeVita on 2009-03-27
Hi **kpgalligan**, can you post some more info?
What version of Ubuntu you have?
From your link it seems you **wvdial** to connect. Post here your **/etc/wvdial.conf**
Also post the output of **lsusb** (from terminal with the modem attached).

Regards,
George

---

### Post by kpgalligan on 2009-03-27
Turn off wireless
Ubuntu version: **8.10 - Ibex**

**cat /etc/wvdial.conf**

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = Anything
Password = Anything
Baud = 9600

```

**lsub**

```
Bus 008 Device 003: ID 0408:03ba Quanta Computer, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c51b Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 12d1:1414 Huawei Technologies Co., Ltd. 
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

OK.  So, I run...

**wvdial Defaults**

I get a bunch of text right away, then it stops at 'Carrier detected.  Waiting for prompt.'

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
```

It will stay here for a while.  Then, it will do more stuff.  If I run it without 'sudo', I get permission errors...

```
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
```

Then I kill it.  With sudo, after waiting at the "Carrier detected" line ...

```
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Fri Mar 27 09:11:05 2009
--> Pid of pppd: 7094
--> Using interface ppp0
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> local  IP address 25.64.157.60
--> pppd: &#65533;[7f]
--> remote IP address 10.64.64.64
--> pppd: &#65533;[7f]
--> primary   DNS address 10.177.0.34
--> pppd: &#65533;[7f]
--> secondary DNS address 10.165.17.242
--> pppd: &#65533;[7f]
```

Now that seems promising.  After that, though, I don't know what to do.  Trying to browse on the web doesn't work.  The little network guy at the top right still says disconnected.  ifconfig does show the ppp entry, but basically, I don't know what to do with it.  In windows, there was a big difference depending on which profile I picked.  "T-Mobile Broadband" didn't work, but "T-Mobile" standard did.  I took screenshots of both configs, and I think the only major differences were 'APN used' and the DNS servers (the APN that worked was 'internet2.voicestream.com').  I don't think we've involved APN anywhere in this process so far, which makes me think there's some step that's missing.

The only other clue.  When i go to 'System > Preferences > Network Configuration', the Mobile Broadband tab has what seems like something familiar.  The 'T-Mobile (Internet)' provider has the 'internet2.voicestream.com' APN.  It seems like I need to connect to something with that, but again, no idea.

Thanks again for any help.  Output of ifconfig attached:

**sudo ifconfig**

```
eth0      Link encap:Ethernet  HWaddr 00:23:8b:54:0d:17  
          inet6 addr: fe80::223:8bff:fe54:d17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1275068340 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:96:a5:f9  
          inet6 addr: fe80::221:ff:fe96:a5f9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2419 errors:0 dropped:0 overruns:0 frame:12772
          TX packets:1616 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2116208 (2.1 MB)  TX bytes:356518 (356.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:25.64.157.60  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1147 (1.1 KB)  TX bytes:1224 (1.2 KB)
```

---

### Post by kpgalligan on 2009-03-27
Sorry.  Before the "Turn off wireless" part I was going to put something like "OK, here's the steps I followed.  Step 1, turn off wireless ..."

---

### Post by kpgalligan on 2009-03-27
I looked around a bit more.  I found another modem thread, which you actually posted to George...

[http://ubuntuforums.org/showthread.php?t=1065934&highlight=mobile+broadband+apn](http://ubuntuforums.org/showthread.php?t=1065934&highlight=mobile+broadband+apn)

You mentioned something about the system recognizing the modem as a drive instead of a modem (if I may paraphrase).  I looked up the output of lsusb (12d1:1414), and found the following on a debian page...

**[http://wiki.debian.org/DeviceDatabase/USB](http://wiki.debian.org/DeviceDatabase/USB)**

12d1:1414
dz0000dc*dsc*dp*ic*isc*ip*
**usb-storage**
none
Huawei Technologies Co., Ltd.

So maybe the same type of thing?

---

### Post by kpgalligan on 2009-03-27
Kept reading.  Boiled it down to switching the usb mode.  Tried usb_modeswitch.  Sort of works, but doesn't seem to make a difference.  Will keep going down that path a little later.

---

### Post by GeorgeVita on 2009-03-27
Sorry, I was out for some hours...

OK, you are trying to use wvdial as the connection program.
Edit your /etc/wvdial.conf as below:

[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 =AT+CGDCONT=1,"IP","internet2.voicestream.com"

If you can ask your provider about **internet2.voicestream.com**

To connect use (from terminal): **sudo wvdial**
To disconnect press ctrl-c at the same terminal window.

Post here any error message. Till then I will try to find something to make Network Manager work.

Regards,
George

EDIT: after "connection" just click on Firefox icon, remove "work offline" with ALT-F W and try browsing.
You were connected after Primary DNS xxx & Secondary DNS xxx !

---

### Post by kpgalligan on 2009-03-27
Cool!  It sort of works...

**sudo wvdial**
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet2.voicestream.com"
AT+CGDCONT=1,"IP","internet2.voicestream.com"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Mar 27 14:38:20 2009
--> Pid of pppd: 15000
--> Using interface ppp0
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> local  IP address 10.190.81.90
--> pppd: &#65533;[7f]
--> remote IP address 10.64.64.64
--> pppd: &#65533;[7f]
--> primary   DNS address 66.94.25.120
--> pppd: &#65533;[7f]
--> secondary DNS address 66.94.9.120
--> pppd: &#65533;[7f]

```

The pause with the carrier detected line is gone.  It goes right through.  After that, I was even able to ping the DNS server.  However, trying to browse says I'm in offline mode, and I can't do much else.  The gnome panel networking icon still says I'm disconnected.  Is there another thing I need to do?

By the way, I really appreciate the help.

-Kevin

---

### Post by GeorgeVita on 2009-03-27
... and an idea for Network Manager:

From a terminal window:
**sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi**

Search (**ctrl-F**) for the string **12d1**
Two lines below edit the line:
**...int_outof="0x1001;0x1406">** to **int_outof="0x1001;0x1406;0x1414">**

Save, Exit, Reboot without modem, wait for the system to stabilize, plug the modem to the USB port, wait for a while and if a message does not appear (to help you with the setup) try to set the Mobile Broadband manually (right click on the 2PC screens, Edit connections,...).

Hope for the best!

EDIT: just to add that wvdial is the best (my opinion) program to connect BUT the system DOESN'T co-operates with it so Firefox and Network Manager remain "offline".

---

### Post by kpgalligan on 2009-03-27
Oh man!!!  You're a genius!!!

Rebooted.  Disabled my wireless.  Plugged in the modem.  Waited for a bit, as nothing happened, but then I saw the "T-Mobile (Internet)" entry in the networking dropdown.  Connected to it.  Done.

The speed itself is so-so.  Download is .78Mb/s.

Still, really glad this is working.  Thanks again!

---

### Post by GeorgeVita on 2009-03-27
Well done!

A final note: You edit HAL info which possibly will return to original after a "big" system update. If it stops working with the Network Manager check the 10-modem.fdi file.

For further info Take a look at:
**man wvdial** and **man wvdial.conf** (from terminal)
[http://forum.huawei.com/jive4/thread.jspa?threadID=322982](http://forum.huawei.com/jive4/thread.jspa?threadID=322982)

If you feel it is "solved", mark this thread as "solved" via Thread Tools.

G

---

### Post by kpgalligan on 2009-03-27
Not sure how to mark it solved.  No option remotely like that in my thread tools.  Changing the tags, though.

---

### Post by jdb91 on 2009-09-08
Mine worked once, for about 10 seconds. Now i get

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Any help?

---

### Post by GeorgeVita on 2009-09-09
Hi **jdb91**, under the commercial name of 'T-mobile XYZ' could be a different type of modem. Can you do some basic tests providing more info?

Boot without the modem, **wait** for the system to load, delete any existing Mobile Broadband connection (right click Network Manager icon, Edit connections, Mobile Broadband, click on any existing, delete).

Open a terminal window: ```
sudo dmesg -c
```
Attach your modem, **wait** 15 seconds, check from terminal: ```
dmesg
``` ```
lsusb
``` If any wizard appear follow instruction to setup new connection. If not try setup manually (via network manager icon).

Post here terminal output from 2nd dmesg command, lsusb and data about country/provider/Ubuntu version.

Regards,
George

---

### Post by jdb91 on 2009-09-09
> **GeorgeVita said:**
> Hi **jdb91**, under the commercial name of 'T-mobile XYZ' could be a different type of modem. Can you do some basic tests providing more info?

Hi, currently at work, so can't do all the diag, but it's a MFZTE 636

Cheers

---

### Post by GeorgeVita on 2009-09-09
Hi **jdb91**, for ZTE MF636 and Ubuntu 9.04 it is better to send an AT command from windows so it will turn always in 'real modem' mode (19d2:0031) and then adjust a file.

More info: [http://ubuntuforums.org/showthread.php?p=6894586#post6894586](http://ubuntuforums.org/showthread.php?p=6894586#post6894586)
post#8, points **2 & 4** as /dev/ttyUSBx ports are created at 9.04

Regards,
George

---

