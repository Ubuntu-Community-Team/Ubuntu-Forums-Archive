---
title: "lucid. Common thread here with wifi problems"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by myjess on 2010-05-02
Am I wrong here or does there seem to be some common thread with wifi no longer working in lucid for a lot of people including myself (see earlier post which was a fresh lucid install).

Looks like it's going to be a regression to karmic for me to get a good sustainable connection on my medion md 2110 laptop.

My acer one netbook (from which I type, on the other hand seems to have no issues with wifi in a upgraded from karmic install.

---

### Post by brawd on 2010-05-02
I'm beginning to agree with you myjess.

I have a pci card that used to work in 9.10 which is an etec RTL8185l and a D-Link usb job that used to work without a problem. 

Both have gone belly up in 10.04 but at least a lsusb command comes back with the D-Link.

It's just as well the modem/router thingee is right alongside my puter.

brawd

---

### Post by NutmegCT on 2010-05-02
Joining the club.  My wireless worked fine with Karmic, but after moving up (?) to Lucid I lose wireless when the system suspends (sleeps).  Wicd (as well as Network Manager if using that) lose the connection to my linksys router.  

Wake up laptop (Dell Latitude D505), enter password, all is well except Wicd shows "no wireless found".

Only way I can get wireless connection back is to restart.  System is up to date as of this morning.

Puzzling.

Tom in Connecticut

---

### Post by mavk84 on 2010-05-05
same problem. My wifi card is Intel Corporation PRO/Wireless 5100 AGN. It worked perfectly since ubuntu 8.04 but now has become unstable: I have to reconnect to the router every 10 minutes.

---

### Post by mysticdragon on 2010-05-05
Well, I suppose I feel somewhat better after reading some of the letters in this thread.  

I am running Ubuntu 10.04 in a VM (using Virtual Box) on a Dell Latitude e6500 that uses Vista 64 bit as the host OS.  I was previously running Karmic Koala and had no issues with connectivity, even when I did the coding to add my Linux system to the school domain.

With the newest version, however, I've only been able to connect to the internet by wiring in--regardless of what setting I use (NAT, Bridged), I can't get the Ubuntu VM to utilize the wireless.  Has anyone as of yet heard of a fix for this?

---

### Post by ifreecarve on 2010-05-07
I am also running lucid on a Dell Latitude E6500, and experiencing problems.  WHEN I REBOOT, IT SEEMS TO WORK.  However, after the laptop goes to sleep and wakes up a few times, the network manager (nm-applet) is only able to recognize various access points -- not actually associate with them. 

Syslog for that:
```

May  7 14:12:37 crow NetworkManager: <info>  Activation (eth1) starting connection 'Auto MIT'
May  7 14:12:37 crow NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
May  7 14:12:37 crow NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  7 14:12:37 crow NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  7 14:12:37 crow NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  7 14:12:37 crow NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  7 14:12:37 crow NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  7 14:12:37 crow NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May  7 14:12:37 crow NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto MIT' requires no security.  No secrets needed.
May  7 14:12:37 crow NetworkManager: <info>  Config: added 'ssid' value 'MIT'
May  7 14:12:37 crow NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May  7 14:12:37 crow NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
May  7 14:12:37 crow NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  7 14:12:37 crow NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
May  7 14:12:37 crow NetworkManager: <info>  Config: set interface ap_scan to 1
May  7 14:12:37 crow NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
May  7 14:12:42 crow wpa_supplicant[969]: Trying to associate with 00:21:d8:49:bc:41 (SSID='MIT' freq=2462 MHz)
May  7 14:12:42 crow NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
May  7 14:12:42 crow wpa_supplicant[969]: Association request to the driver failed
May  7 14:12:47 crow wpa_supplicant[969]: Authentication with 00:21:d8:49:bc:41 timed out.
May  7 14:12:47 crow NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
May  7 14:12:47 crow NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
May  7 14:12:53 crow NetworkManager: <info>  eth1: link timed out.
May  7 14:12:58 crow wpa_supplicant[969]: Trying to associate with 00:21:d8:49:bc:41 (SSID='MIT' freq=2462 MHz)
May  7 14:12:58 crow wpa_supplicant[969]: Association request to the driver failed
May  7 14:12:58 crow NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
May  7 14:13:03 crow wpa_supplicant[969]: Authentication with 00:21:d8:49:bc:41 timed out.
May  7 14:13:03 crow NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
May  7 14:13:03 crow NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
May  7 14:13:14 crow wpa_supplicant[969]: Trying to associate with 00:21:d8:49:18:f1 (SSID='MIT' freq=2412 MHz)
May  7 14:13:14 crow NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
May  7 14:13:14 crow wpa_supplicant[969]: Association request to the driver failed
May  7 14:13:19 crow wpa_supplicant[969]: Authentication with 00:21:d8:49:18:f1 timed out.
May  7 14:13:19 crow NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
May  7 14:13:19 crow NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
May  7 14:13:30 crow wpa_supplicant[969]: Trying to associate with 00:21:d8:49:8d:c1 (SSID='MIT' freq=2412 MHz)
May  7 14:13:30 crow wpa_supplicant[969]: Association request to the driver failed
May  7 14:13:30 crow NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
May  7 14:13:34 crow NetworkManager: <info>  eth1: link timed out.
May  7 14:13:35 crow wpa_supplicant[969]: Authentication with 00:21:d8:49:8d:c1 timed out.
May  7 14:13:35 crow NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
May  7 14:13:35 crow NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
May  7 14:13:38 crow NetworkManager: <info>  Activation (eth1/wireless): association took too long, failing activation.
May  7 14:13:38 crow NetworkManager: <info>  (eth1): device state change: 5 -> 9 (reason 11)
May  7 14:13:38 crow NetworkManager: <info>  Activation (eth1) failed for access point (MIT)
May  7 14:13:38 crow NetworkManager: <info>  Marking connection 'Auto MIT' invalid.
May  7 14:13:38 crow NetworkManager: <info>  Activation (eth1) failed.
May  7 14:13:38 crow NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
May  7 14:13:38 crow NetworkManager: <info>  (eth1): deactivating device (reason: 0).
May  7 14:13:38 crow NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.

```

LSPCI says:
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

My kernel module for wireless is the "wl" one, which I believe comes from the broadcom-sta-source package.  

It's a very annoying problem.  Where should I report it?

---

### Post by NutmegCT on 2010-05-07
Here's how I fixed exactly the same problem with mine:

[http://ubuntuforums.org/showthread.php?t=1476019](http://ubuntuforums.org/showthread.php?t=1476019)

Tom

---

### Post by ifreecarve on 2010-05-17
That thread worked for me too with the wl kernel module:

did this:```
sudo vi /etc/pm/config.d/config
```

Added one line:```
SUSPEND_MODULES="wl"
```

---

### Post by jamere on 2010-05-17
There seems to be a common thread of networking problems of all types including mobile broadband. Problems connecting Acer Aspire One netbook with Qualcomm HS USB modem. Problem also in Karmic. Has to be affecting many, many folks. GRUB boot problems and connectivity problems are probably running off folks in droves. Hate to see Ubuntu suffer from all these problems, but the problems just don't seem to be getting fixed.:confused:

---

### Post by necromonger on 2010-05-17
wusb54g ver 4 disconnects all the time no fix.To many wireless problems to start with for everyone.

---

