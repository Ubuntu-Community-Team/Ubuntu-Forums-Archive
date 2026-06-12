---
title: "Cannot connect to wireless - network SSID visible"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by inosek on 2011-04-20
I'm having a hell of a time here.  I've been searching the forums, but haven't found anything that has worked yet.

I'm running 10.04 LTS on a Dell Latitude.  Wired networking is fine and the wireless can see the network, but cannot connect.  This is a public network at a library (there isn't security on the network, but you do need to accept TOS before continuing.

I cannot join the open network, it's bombing out when it attempts to assign an IP.  I tried using wicd, but it didn't make any difference.

Here's the lspci results for the machine.
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)


And the iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"opplair"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any help would be greatly appreciated.

---

### Post by inosek on 2011-04-21
Anyone?

---

### Post by dandnsmith on 2011-04-21
> but you do need to accept TOS before continuing.

I've not idea what TOS might be!

Usually with no security, there isn't a problem - but then, all the networks I currently use have some sort of protection which requires a password, so what do I know?

---

### Post by Hippytaff on 2011-04-21
TOS - Terms of Service? :?
 
Anyway, it might be worth downloading, running and posting the script from the link below (wireless Script) it will return lots of wireless diagnostic info which you can post here (code tags should already be on the results.txt) and people will have a better idea of issues and how to troubleshoot. Them :-)

---

### Post by Blasphemist on 2011-04-21
TOS, Terms of Service, only comes up when you've already connected to the network, but haven't yet been given rights. What browser are you using? I'm no expert on how these pages work but I wonder if your browser or it's security settings are preventing you communicating the acceptance of the TOS. Try another browser. I use chromium, sea monkey is also easily available through the software center. If you are using Firefox, which version? Do you have extensions installed that might be interfering with this?

---

### Post by inosek on 2011-04-21
Basically, the network is open, it will allow machines to connect and issue an IP address.  However, it will not allow web access until the terms of service are accepted.

I've added the machine's MAC address to our wireless controller to bypass the TOS requirement, so it's essentially operating as a wide open network, but it will not connect to it.

---

### Post by dandnsmith on 2011-04-21
Even adding the MAC to the 'wireless controller', you won't have satisfied the TOS.

I suggest you follow jim's suggestions - I know I would (and have done in the past to sort out problems of that nature)

---

### Post by Hippytaff on 2011-04-21
> **dandnsmith said:**
> 

I suggest you follow jim's suggestions out problems of that nature)
+1

I am not familiar with TOS and open networks either, though it looks like this is the problem

---

### Post by inosek on 2011-04-21
Adding the MAC address does actually bypass the TOS.  We have several other devices set up this way.

Also, I'm using Firefox 3.6.13

---

### Post by Hippytaff on 2011-04-21
if they usually work the way you've got this one set up tou might benefit from the findings of the wireless info script which you can download from the link below.

:-)

do you have ubuntu or any other debian based operating systems on your other setups?

---

