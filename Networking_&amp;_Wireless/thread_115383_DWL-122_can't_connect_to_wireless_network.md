---
title: "DWL-122 can't connect to wireless network"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by Viro on 2006-01-10
Hi there. I've been following the instructions in the HOWTO on these forums [http://ubuntuforums.org/showthread.php?t=25676](http://ubuntuforums.org/showthread.php?t=25676) and I've followed the instructions provided by aussieoddsocks and I have even typed in my wireless key correctly.

When I run the script, it says everything is fine and I get no error messages. However, it doesn't seem to find any network. I get the following message:
```

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0d:88:fa:d8:7c
Sending on LPF/wlan0/00:0d:88:fa:d8:7c
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

What is going on? My router is at 192.168.2.1 if that helps, but it seems to be sending a dhcp request to 255.255.255.255? I would be very grateful to anyone who would help me get this to work.

---

### Post by carlosqueso on 2006-01-10
I have the same router.....try restarting the router (unplug and plug back in.)  That seemed to work for me.  I really hate that router.....:rolleyes:

---

### Post by Viro on 2006-01-10
errr... same router? You mean you have a Belkin?

---

### Post by Viro on 2006-01-10
Just restarted my router by switching it off at the mains, unplugging it, waiting 5 minutes and plugging it in again.

Still the same results. This is really vexing.

---

### Post by carlosqueso on 2006-01-10
Nope D-link....thought that's what the post referred to (can't read the numbers on mine so thought it may have been)

---

### Post by carlosqueso on 2006-01-10
Will it work if you don't use encryption?

---

### Post by az on 2006-01-10
I used his script in this post:
[http://ubuntuforums.org/showthread.php?t=25676#top](http://ubuntuforums.org/showthread.php?t=25676#top)


I find this script to be the most relable way of using this device. 

What is the full output of running the script?

---

### Post by Viro on 2006-01-11
Here is the entire output after running the script /etc/hotplug/usb/prism2_usb. The keys and SSID have been changed, but they are in the same format as the original, so if I made a mistake there, it would be in the original too.

```

message=lnxreq_ifstate
  ifstate=enable
  resultcode=success
message=lnxreq_autojoin
  ssid='Zentradae'
  authtype=sharedkey
  resultcode=success
message=lnxreq_hostwep
  resultcode=no_value
  decrypt=true
  encrypt=true
message=dot11req_mibset
  mibattribute=dot11PrivacyInvoked=true
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKeyID=0
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11ExcludeUnencrypted=true
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKey0=5c:82:ad:d6:03
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKey1=20:32:40:79:15
  resultcode=success
There is already a pid file /var/run/dhclient.pid with pid 6615
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0d:88:fa:d8:7c
Sending on   LPF/wlan0/00:0d:88:fa:d8:7c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Here is the content of my /etc/hotplug/usb/prism2_usb:
```

sudo modprobe prism2_usb prism2_doreset=1

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="Zentradae" authtype="sharedkey"

sudo wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11ExcludeUnencrypted=true
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="5C:82:aD:D6:03"
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey1="20:32:40:79:15"

sudo sleep 2

sudo dhclient wlan0

```

I can't see anything wrong, but perhaps some kind soul will be able to spot where I've gone wrong?

---

### Post by az on 2006-01-11
I made a mistake, I posted the wrong link:

[http://ubuntuforums.org/showpost.php?p=465719&postcount=7](http://ubuntuforums.org/showpost.php?p=465719&postcount=7)

This is the script I use:

:~$ cat Desktop/prism2_usb
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="1a:1a:1a:1a:1a"
wlanctl-ng wlan0 lnxreq_autojoin ssid="PutNameHere" authtype="sharedkey"
sleep 2
dhclient wlan0


~$ sudo Desktop/prism2_usb
message=lnxreq_ifstate
  ifstate=enable
  resultcode=success
message=lnxreq_ifstate
  ifstate=enable
  resultcode=success
message=lnxreq_hostwep
  resultcode=no_value
  decrypt=true
  encrypt=true
message=dot11req_mibset
  mibattribute=dot11PrivacyInvoked=true
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKeyID=0
  resultcode=success
message=dot11req_mibset
  mibattribute=dot11WEPDefaultKey0=1a:1a:1a:1a:1a
  resultcode=success
message=lnxreq_autojoin
  ssid='PutNameHere'
  authtype=sharedkey
  resultcode=success
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0d:88:66:00:59
Sending on   LPF/wlan0/00:0d:88:66:00:59
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.104 -- renewal in 264876 seconds.

---

### Post by Viro on 2006-01-11
I tried your script, and I get the same results. I don't seem to get any DHCP offers.

---

### Post by Viro on 2006-01-11
I just realized that this is posted in the wrong forum! Doh!

Can some mods move this to the networking forum?

---

### Post by az on 2006-01-11
Can you connect through dhcp with another network device?

Are you using two keys or just one?

---

### Post by Viro on 2006-01-12
I can connect through DHCP using my wired network card, through the same router. Also, wirelessly I can connect via DHCP on my Mac laptop so I don't know what could be wrong. :(

I used 2 keys before, and 4 keys before that, but I'm using just the one now.

---

### Post by az on 2006-01-12
*Bows head in shame*

Perhaps you can try using ndiswrapper?

Card: [D-Link] DWL-122 
Chipset: Prism USB 
usbid: 2001:3700 
Driver: Get latest driver from [ftp://ftp.dlink.com/Wireless/dwl122/Driver](ftp://ftp.dlink.com/Wireless/dwl122/Driver). Tested with driver version 102. 
Other: Works with WEP and WPA-PSK+TKIP. With this driver, other Prism USB (not Prism54) devices also may work. Change all occurences of above Vendor and Device IDs in Drivers/WinXP/NETPRISM.inf into the Vendor and Device ID of your device. 

Use the most recent driver for it (see above link - version 1.02).  Even if that is not the version of the driver that came with your card, that is the driver that will work.  You also need to blacklist the prism2_usb module from being loaded when you plug the device in (/etc/hotplug/blacklist).  Reboot once you have blacklisted it so that the module is not loaded.

Install ndiswrapper-utils (it is on the install cd - just use synaptic) and set up the windows driver with it

(unzip the driver and find the .inf file as well as any other file and put them in the same directory)

sudo ndiswrapper -i NETPRISM.inf
sudo modprobe ndiswrapper
ndiswrapper -l

Then go to the networking GUI and see if your wireless card apprears.

If you find that the device works, please add to the bug report in the link I posted above.

---

### Post by Viro on 2006-01-12
Oh noes, I gotta use the evil Windows drivers. I guess I'll just leave this alone for now, and just use my wired connection. Once Drake is released, I'll give it a try again. This thing is really vexing me.

---

### Post by Mr_Grieves on 2006-01-12
[QUOTE=Viro]
What is going on? My router is at 192.168.2.1 if that helps, but it seems to be sending a dhcp request to 255.255.255.255?[/QUOTE]
Yes, DHCP Discover packets is send to a broadcast adress that adresses all hosts in your network.

Do you have a firewall in the network or on you're computer that might be blocking the traffic? Tried sniffing to figure out if somethings wrong?

---

### Post by Viro on 2006-01-12
The network has a standard firewall that prevents access from outside the network, but allows pretty much anything to go out of the network. Therefore, it shouldn't be preventing this DHCP broadcast from reaching the router. The computer I'm on is just with a standard Ubuntu install, so no firewall there.

---

### Post by Viro on 2006-01-12
The network has a standard firewall that prevents access from outside the network, but allows pretty much anything to go out of the network. Therefore, it shouldn't be preventing this DHCP broadcast from reaching the router. The computer I'm on is just with a standard Ubuntu install, so no firewall there.

---

