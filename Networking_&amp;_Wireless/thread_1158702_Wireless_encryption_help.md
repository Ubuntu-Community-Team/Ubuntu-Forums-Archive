---
title: "Wireless encryption help"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by ManyBeers on 2009-05-13
I have managed to get my DLink DWLG630 pcmcia wireless card working on Ubuntu 8.04 using the ndiswrapper package. However it will only
work with my WEP key disabled. I would rather not run like that so can anybody here tell me how to keep the card working and also my routers encryption?

---

### Post by lukenz on 2009-05-13
Hello
 
Install wpasupplicant.
 
If you can connect to the net, open terminal and run the following:
 
sudo apt-get update
 
sudo apt-get install wpasupplicant wpagui
 
 
Hopefully that helps....
 

Luke

---

### Post by ManyBeers on 2009-05-13
> **lukenz said:**
> Hello
 
Install wpasupplicant.
 
If you can connect to the net, open terminal and run the following:
 
sudo apt-get update
 
sudo apt-get install wpasupplicant wpagui
 
 
Hopefully that helps....
 

Luke

I'm on it as i type. Will report back. Mine is a WEP encryption key will that matter?

---

### Post by lukenz on 2009-05-13
Are you using WEP encryption?  I hope not, IMO it is false security...
 
If your router supports it I highly recommend WPA/WPA2 with a strong password.

---

### Post by ManyBeers on 2009-05-14
> **lukenz said:**
> Are you using WEP encryption?  I hope not, IMO it is false security...
 
If your router supports it I highly recommend WPA/WPA2 with a strong password.

 I can't change it because several people use the network and where I live the WEP security is adequate. So the wpasupplicant is for WPA-correct? Whay about WICD network manager?

---

### Post by lukenz on 2009-05-14
> **ManyBeers said:**
> I can't change it because several people use the network and where I live the WEP security is adequate. So the wpasupplicant is for WPA-correct? Whay about WICD network manager?
I can't vouch for WICD as I have never used it but looking at their site they do appear to support wep.  What are you using at the moment to manage the connection?  When you say it only works with wep enabled, what is it doing?  Saying "connection to ...... failed?" or something else?

---

### Post by ManyBeers on 2009-05-14
> **lukenz said:**
> I can't vouch for WICD as I have never used it but looking at their site they do appear to support wep.  What are you using at the moment to manage the connection?  When you say it only works with wep enabled, what is it doing?  Saying "connection to ...... failed?" or something else?
It will only work with WEP disabled. I never get an ip address from the routers dhcp server.

---

### Post by ManyBeers on 2009-05-14
Again would somebody please help me get my network card working with encryption enabled.

---

### Post by lukenz on 2009-05-14
> **ManyBeers said:**
> It will only work with WEP disabled. I never get an ip address from the routers dhcp server.

You are going to have to be a little more forthcoming with information if you want people to help you.

You are saying now that you never get an IP address from the routers DHCP server.  If it is that you can't get an IP address, but your wlan is connected that tells me that it is not because your buntu isn't liking the wep. Or are you saying that when you connect even without encryption you cannot get an IP address?

Could you please open terminal and run iwconfig.  Post it's output.

---

### Post by ManyBeers on 2009-05-14
> **lukenz said:**
> You are going to have to be a little more forthcoming with information if you want people to help you.

You are saying now that you never get an IP address from the routers DHCP server.  If it is that you can't get an IP address, but your wlan is connected that tells me that it is not because your buntu isn't liking the wep. Or are you saying that when you connect even without encryption you cannot get an IP address?

Could you please open terminal and run iwconfig.  Post it's output.

Sorry this took so long bit it was 3:00 a.m. last night whrn I signed off and I was pooped
```
iwconfig(with encryption enabled)
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

---

### Post by ManyBeers on 2009-05-14
I will restate my problem.
I am running Ubuntu 8.04 2.6.24-23 generic and ndiswrapper with 
my WindowsXP drivers to make my DWL G630 pcmcia network card work. 
I can connect wirelessly Only when I disable the routers WEP encryption and run unsecured. 

If anybody out there knows how to go about sorting this out would you maybe give me a hand?

```
output of=~$ dmesg | grep -e ndis -e wlan
[ 1665.975525] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1666.083816] ndiswrapper: driver mrv8k51 (D-Link,12/21/2003,2.2.0.19) loaded
[ 1666.087906] ndiswrapper: using IRQ 10
[ 1190.327421] wlan0: ethernet device 00:0f:3d:04:c4:f5 using NDIS driver: mrv8k51, version: 0x202000b, NDIS version: 0x501, vendor: 'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[ 1190.328618] ndiswrapper (set_iw_encr_mode:710): setting encryption mode to 6 failed (C00000BB)
[ 1190.329222] wlan0: encryption modes supported: WEP; TKIP with WPA
[ 1190.332927] usbcore: registered new interface driver ndiswrapper
[ 1667.842051] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1667.854770] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  840.589537] wlan0: no IPv6 routers present
[ 1906.148164] ndiswrapper (set_essid:53): setting essid failed (C0000001)
[ 1906.190017] ndiswrapper (set_essid:53): setting essid failed (C0000001)
[ 1920.024477] wlan0: no IPv6 routers present

```

---

### Post by ManyBeers on 2009-05-14
bump

---

### Post by lukenz on 2009-05-14
Have you tried to manually set up the interface?
 
```
 
iwconfig wlan0 mode managed key [WEP key here]
iwconfig wlan0 essid "[ESSID]"
dhclient wlan0

```
 
In regards to your question earlier about WICD.  I tried it last night because I was having slight issues as well and it is great.

---

### Post by ManyBeers on 2009-05-14
> **lukenz said:**
> Have you tried to manually set up the interface?
 
```
 
iwconfig wlan0 mode managed key [WEP key here]
iwconfig wlan0 essid "[ESSID]"
dhclient wlan0

```
 
In regards to your question earlier about WICD.  I tried it last night because I was having slight issues as well and it is great.

I installed it and tried it twice and it did not work. It didn't connect my laptop to the Internet via my usb port, which Network Manager does. For wired networking my Actiontec modem/router
has both USB and standard Ethernet ports on the back. So my 
desktop is connected via Ethernet and my laptop connects via USB or wirelessly-- if I can ever get it to work using WEP. So I went back to Network Manager.I can still connect wirelessly if I disable WEP in the router and run unencrypted(which I won't do). Any ideas?

---

### Post by lukenz on 2009-05-14
Did you try the iwconfig commands as I suggested?

---

### Post by ManyBeers on 2009-05-14
> **lukenz said:**
> Did you try the iwconfig commands as I suggested?

I set it up manually through the  Network manager GUI app.
How do I do the iwconfig commands?

---

### Post by lukenz on 2009-05-14
1. Open terminal and type sudo su
2. Type iwconfig wlan0 mode managed key [WEP key here]
3. Type iwconfig wlan0 essid "[add the essid of the network]"
4. Type dhclient wlan0

---

### Post by ManyBeers on 2009-05-14
> **lukenz said:**
> 1. Open terminal and type sudo su
2. Type iwconfig wlan0 mode managed key [WEP key here]
3. Type iwconfig wlan0 essid "[add the essid of the network]"
4. Type dhclient wlan0

Here is what I get:
```
sudo su
[sudo] password for mark: 
root@ubuntu:/home/mark# iwconfig wlano mode managed key f1e2d3c4b5a6987f6e5d4ceb2a
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlano ; No such device.
root@ubuntu:/home/mark# iwconfig wlano essid "SurfsUp"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlano ; No such device.
root@ubuntu:/home/mark# dhclient wlano
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlano: ERROR while getting interface flags: No such device
wlano: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
root@ubuntu:/home/mark# 



```
This all is happening while encryption is Enabled in my router and the card is in the slot and it's green link l;ight is on. If I was to turn off encryption on my router and reboot the card would work.

---

### Post by lukenz on 2009-05-14
> **ManyBeers said:**
> Here is what I get:
```
sudo su
[sudo] password for mark: 
root@ubuntu:/home/mark# iwconfig wlano mode managed key f1e2d3c4b5a6987f6e5d4ceb2a
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlano ; No such device.
root@ubuntu:/home/mark# iwconfig wlano essid "SurfsUp"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlano ; No such device.
root@ubuntu:/home/mark# dhclient wlano
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
 
SIOCSIFADDR: No such device
wlano: ERROR while getting interface flags: No such device
wlano: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
root@ubuntu:/home/mark# 
 
 

```
This all is happening while encryption is Enabled in my router and the card is in the slot and it's green link l;ight is on. If I was to turn off encryption on my router and reboot the card would work.
 
 
It is because you used an o (as in the letter o) instead of number 0 on wlan0.

---

### Post by ManyBeers on 2009-05-14
> **lukenz said:**
> It is because you used an o (as in the letter o) instead of number 0 on wlan0.

Ok I'll try again. Incidentally Im am posting this reply using my wireless card right now. I rebooted my computer after disabling Wep and after reaching my desktop I put the card in the slot opened Network manager removed the Wep key and my wireless cards activity light immediately started flashing.

When i configure mt network using Network Manager after entering my 26 character WEP key am I supposed to click the "Set" key? I don't.

---

### Post by ManyBeers on 2009-05-15
bump

---

### Post by ManyBeers on 2009-05-15
I dumped Network manager for the 3rd time and reinstalled WICD and now all is working correctly.
End Of Thread.

---

