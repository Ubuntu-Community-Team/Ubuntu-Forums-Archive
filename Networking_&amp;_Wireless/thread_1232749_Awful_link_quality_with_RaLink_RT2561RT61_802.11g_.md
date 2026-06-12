---
title: "Awful link quality with RaLink RT2561/RT61 802.11g PCI"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by Soldeace on 2009-08-05
Greetings, gentlemen.

Speaking about wired connections I've always had an excellent network performance with Ubuntu. However, I bought a wireless network adapter a few months ago (RaLink RT2561/RT61 802.11g PCI). The link quality is simply horrible and I'm disconnected from minute to minute -- me and the wifi router are in the same room. Sometimes I even have to reboot if I wish to reconnect. This is an example of the best I can get with it:

```
$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"slippersonfire"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:58:14:80:34   
          Bit Rate=11 Mb/s   Tx-Power=3 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          **Link Quality=_30/100_  Signal level:-72 dBm**
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The problem also exists in Debian Lenny. I know it's not a matter of hardware because it doesn't happen in a similar computer with Windows XP installed, which gives me a signal strength of 95/100 and not less (but the link quality is also awful on Ubuntu in that machine).

In face of these circunstances I tried to replace the native RT61PCI driver with a ndiswrapper alternative but in all possible ways I couldn't make it work (wlan0 misteriously isn't listed by iwconfig, although the device is recognized according to lspci and lsmod shows the system is loading the correct drivers).

Well, this forum is my last resort. I've done all I could do. Please, "halp"! Here are the specs:

Network controller: RaLink RT2561/RT61 802.11g PCI
Driver in use: kernel/drivers/net/wireless/rt2x00/rt61pci.ko
System: 2.6.28-15-generic #48-Ubuntu x86_64

---

### Post by Soldeace on 2009-08-06
I disabled DHCP yesterday and it's been working like a charm so far (both Gnome Network Manager and wicd have options to disable it... if you are not using these, try the [old-school solution]("http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html")). With a static IP I don't get disconnected and the link quality floats around 60% now. Weird, very weird.

---

### Post by beltts05 on 2009-12-02
Thanks for following up on your issue.

I  also had this problem and disabling the DHCP worked for me too.  

I did forget to setup the DNS server so I could not connect to the internet but I used step 4.5 of the below post to help figure it out.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)

I did this yesterday and haven't had to reconnect yet.

---

### Post by beltts05 on 2009-12-11
Ok it's been a week now and the disconnect issue is returning.

It's better than it was before but still disconnects on occasion.

I'm only using the wireless because I am out of ports on my switch.  I've ordered a new  switch which should arrive next week so I'll be done with this problem.

---

