---
title: "Howto enable WEP encryption on D-Link DWL-122"
date: 2005-01-18
forum: Networking &amp; Wireless
---

### Post by arno on 2005-01-18
[Sorry this is no HOWTO!!! - I noticed to late that my title might be misleading. Unfortunately the change of the new title didn't propagete yet to the index ..]

after spending several hours and reading several WLAN threads I give up and hope that someone can point me to the point I'm missing ...

Current status: I get the D-Link DWL-122 working when I disable the WEP encryption in my router. But as soon as I enable it it stop working.

When I do
```
ifup wlan0
``` 
I get the following output:
```
 ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:11:95:82:b4:7b
Sending on   LPF/wlan0/00:11:95:82:b4:7b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
``` 

It seems it has trouble getting DHCP Information.
The strange thing is, that in the log of my router there is an entry giving an IP-Address to my connection !?!

The output of iwconfig is:
```
 # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"MyESSID"  Nickname:"MyESSID"
          Mode:Managed  Frequency:2.437GHz  Access Point: 00:04:0E:1A:C4:D9
          Bit Rate:11Mb/s   Tx-Power:2346 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=56/92  Signal level=-59 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``` 

The funny thing is the "Encryption key: off"

When I try to set the key manually via the command line I get the following:
```
# iwconfig wlan0 key ABCDEF1234567890ABCDEF1234
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
``` 

By the way: I set the key via the GUI , in /etc/network/interfaces and in /etc/wlan/wlancfg-MyESSID:

interfaces:
```
#wlan

iface wlan0 inet dhcp
wireless_essid MyESSID
wireless_mode managed
name Drahlose LAN-Karte
wireless_key ABCDEF1234567890ABCDEF1234
channel 6
auto wlan0
``` 

wlancfg-MyESSID:
```
#=======WEP===========================================
# [Dis/En]able WEP.  Settings only matter if PrivacyInvoked is true
lnxreq_hostWEPEncrypt=true     # true|false
lnxreq_hostWEPDecrypt=true     # true|false
dot11PrivacyInvoked=true        # true|false
dot11WEPDefaultKeyID=0          # 0|1|2|3
dot11ExcludeUnencrypted=true    # true|false, in AP this means WEP is required.

# If PRIV_GENSTR is not empty, use PRIV_GENTSTR to generate
#  keys (just a convenience)
PRIV_GENERATOR=/sbin/nwepgen    # nwepgen, Neesus compatible
PRIV_KEY128=true                # keylength to generate
PRIV_GENSTR=""

# or set them explicitly.  Set genstr or keys, not both.
dot11WEPDefaultKey0=AB:CD:EF:12:34:56:78:90:AB:CD:EF:12:34
dot11WEPDefaultKey1=AB:CD:EF:12:34:56:78:90:AB:CD:EF:12:35
dot11WEPDefaultKey2=AB:CD:EF:12:34:56:78:90:AB:CD:EF:12:36
dot11WEPDefaultKey3=AB:CD:EF:12:34:56:78:90:AB:CD:EF:12:37
#=======SELECT STATION MODE===================
IS_ADHOC=n                      # y|n, y - adhoc, n - infrastructure

#======= INFRASTRUCTURE STATION  ===================
# What kind of authentication?
AuthType="opensystem"           # opensystem | sharedkey (requires WEP)

#======= ADHOC STATION ============================
BCNINT=100                      # Beacon interval (in Kus)
CHANNEL=6                       # DS channel for BSS (1-14, depends
                                #   on regulatory domain)
BASICRATES="2 4"                # Rates for mgmt&ctl frames (in 500Kb/s)
OPRATES="2 4 11 22"             # Supported rates in BSS (in 500Kb/s)
``` 

If anybody uses the same device with WEP128 it would be very nice to get the configuration settings.

Thanks for any help !

---

### Post by keyrunner on 2005-02-04
Your experience with the DWL-122 and Utbuntu is not an isolated one.  I have replicated exactly the same experience, suggesting the problem is not an isolated incorrect setting.  If you find the source of the problem or any solution or anyone else knows of one, please post.

---

### Post by Swab on 2005-02-05
This won't help you much.  But just to let you know, I work for D-Link tech support... and half the time people can't even get WEP working in Windows with the DWL-122.  This thing is just a POS.   Infact I think all USB wireless adapters are.

---

### Post by larsdiening on 2005-03-02
After some time I finally got the DWL-122 to work with WEP encryption! Actually, a "ping www.debian.de" works, but higher traffic breaks the system. Let me explain my settings an the problem.

I had the same experience as "arno" that "iwconfig" does not work. But this does not matter.

The solution is the "wlancfg-MyESSID" file. My file differs from arno's in the following lines:

lnxreq_hostWEPEncrypt=false      # true|false
lnxreq_hostWEPDecrypt=false      # true|false
dot11ExcludeUnencrypted=false   # true|false, in AP this means WEP is required.
dot11WEPDefaultKey0=31:32:33:34:39:32:33:38:38:30:31:32:33

With this settings at least the diodes on the DWL-122 show a correct connection. (Note that a constant, periodic blinking shows an error!)

I think the dot11WEPDefaultKey0 line from arno was wrong. It should be 13 digits or 13 hexdigits. The WEPKey above corresponds to the key "1234923880123". Every digit (e.g. "1") is transfered into the hex number of its ASCII code (e.g. "31"). 

Sometimes I had some troubles with my additional device "eth0". So the best thing is to shutdown "eth0" and check with "route" if everything is OK with the gateway.

After that I was able to verify the connection with "ping www.debian.de". Yes, it did work!!!

Then I switched to my browser (firefox) and the system crashed completely. It seems that everytime that if I use more of the connection than just a ping then the system crashes. 

The last lines of /var/log/messages are:

Feb 21 11:01:26 scotty kernel: NETDEV WATCHDOG: wlan0: transmit timed out
Feb 21 11:01:26 scotty kernel: wlan0 rx pipe reset complete.
Feb 21 11:01:26 scotty kernel: wlan0 tx pipe reset complete.
Feb 21 11:01:36 scotty kernel: NETDEV WATCHDOG: wlan0: transmit timed out
Feb 21 11:01:36 scotty kernel: wlan0 rx pipe reset complete.
Feb 21 11:01:36 scotty kernel: wlan0 tx pipe reset complete.
Feb 21 11:01:46 scotty kernel: NETDEV WATCHDOG: wlan0: transmit timed out
Feb 21 11:01:46 scotty kernel: wlan0 rx pipe reset complete.
Feb 21 11:01:46 scotty kernel: wlan0 tx pipe reset complete.
Feb 21 11:01:56 scotty kernel: NETDEV WATCHDOG: wlan0: transmit timed out
Feb 21 11:01:56 scotty kernel: wlan0 rx pipe reset complete.
Feb 21 11:01:56 scotty kernel: wlan0 tx pipe reset complete.
Feb 21 11:02:06 scotty kernel: NETDEV WATCHDOG: wlan0: transmit timed out
Feb 21 11:02:06 scotty kernel: wlan0 rx pipe reset complete.
Feb 21 11:02:06 scotty kernel: wlan0 tx pipe reset complete.
Feb 21 11:02:16 scotty kernel: NETDEV WATCHDOG: wlan0: transmit timed out
Feb 21 11:02:16 scotty kernel: wlan0 rx pipe reset complete.
Feb 21 11:02:16 scotty kernel: wlan0 tx pipe reset complete.
Feb 21 11:02:26 scotty kernel: NETDEV WATCHDOG: wlan0: transmit timed out
Feb 21 11:02:26 scotty kernel: wlan0 rx pipe reset complete.
Feb 21 11:02:26 scotty kernel: wlan0 tx pipe reset complete.

Does anybody has a solution to this problem?

---

### Post by ranf on 2005-03-11
I got it working now.

No changes at all in /etc/network/interfaces. I only created a /etc/wlan/wlancfg-[MyID].

Install "linux-wlan-ng" and "linux-wlan-ng-doc"

```

sudo cp /usr/share/doc/linux-wlan-ng/examples/rc.wlan /etc/init.d/wlan

sudo /etc/init.d/wlan start

sudo ifconfig wlan0 up

sudo dhclient wlan0

```

---

### Post by chimaera on 2005-03-30
[QUOTE=larsdiening]
The last lines of /var/log/messages are:

Feb 21 11:01:26 scotty kernel: NETDEV WATCHDOG: wlan0: transmit timed out
Feb 21 11:01:26 scotty kernel: wlan0 rx pipe reset complete.
Feb 21 11:01:26 scotty kernel: wlan0 tx pipe reset complete.
[/QUOTE]

hi, 
i experience the same problem since i switched from 2.6.7 to 2.6.10 and udev.  anytime i plug-in another USB or IEEE1394 device, my DWL-122 disconnects and i have to un- and replug it to get it working again. did you have any success fixing this?

---

### Post by larsdiening on 2005-04-01
[QUOTE=chimaera]hi, 
i experience the same problem since i switched from 2.6.7 to 2.6.10 and udev.  anytime i plug-in another USB or IEEE1394 device, my DWL-122 disconnects and i have to un- and replug it to get it working again. did you have any success fixing this?[/QUOTE]

Hi,

unfortunately I have not solved the problem yet. The problem is even that everytime the system crashes completely and I have to restart the computer. The problem occurs always if I increase the traffic to something more than just a ping. Bytheway, my DWL-122 is the only USB device connected.

---

### Post by Mr_Welfare on 2006-04-16
Here is a thread that might finally answer my question (if anyone is still going to post here). I have had the exact same problem. My DWL-122 just flashes on and off, indicating an error. I have installed a ndiswrapper windows driver off of the D-Link cd, which installed normally. I have also scoured the forums and Google for anything that might tell me how to fix the problem. No luck. I have a 64 bit enryption code (10 digits) and am getting the same errors as arno. Finally, I have made changes to my

sudo nano /etc/network/interface

could anyone post what this is supposed to look like before editing?

Thanks.

Note: I'm running Breezy as well.

---

### Post by twoey on 2006-12-27
I did find out a way to find your networking using sudo:

ifup wlan0 (my device for some reason was eth2, but it does the job)

and

iwconfig wlan0 key [yourkey]

The trick is ifdown your wireless network device and ifup

while its sending packets, trying to find your DHCP, simoltaniously, in another terminal, use 

iwconfig wlan0 key [yourkey]

This should start connecting you.


I found this out when I sent my key before I used the ifup command, I would receive some packets.  There was some communication between the DCHP and my computer, at least for awhile. So why not do it at the same time? Well, I'm not a newbie to linux, but I'm no genius at it either. I'm learning and trying to get by. I hope this help any of you people with the same problem I've had. Happy New Years!

---

### Post by vbdanl on 2007-02-15
Hi. I am using Ubuntu 6.10, 2wire SBC 1000HW modem that allows 1 ethernet (this computer is using), 1 USB port (a Windows 98 computer is using), and wireless (i think it could have multiple, but all I have is one, the D-Link DWL-122, which I know is now on the end of life list, or basically not supported anymore.  It used to work on XP, but XP went belly up, so now I am trying to get it to work on Ubuntu.  I have read plenty of info on wireless, but after all that, don't really know where to start.  
BTW, now I have to unplug the ethernet cable from one PC and hook it up to the other one to use it - that is the reason I am trying to get the wireless connection to work..)
Did anyone get a DWL-122 D-Link USB wireless adapter to work with Ubuntu, or other linux distro ? Would really appreciate some help getting this to work..

---

