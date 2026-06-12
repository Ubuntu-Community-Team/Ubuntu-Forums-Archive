---
title: "Help! Problem with wireless connection"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by Cohech on 2010-04-07
New to this so please excuse any obvious errors I've made here.  I've spent the majority of my day doing this and am pulling my hair out...

Fresh install of Desktop v9.10 (32 bit) on old Dell Latitude D505 laptop.  All works fine apart from wireless connection.

lspci shows the card as:
[I]01:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
[/I]

lspci -n shows the chip set as:
*01:03.0 0280: 14e4:4320 (rev 03)*

I've followed the instructions in the page below and blacklisted b43 and ssb:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

I've followed the instructions in the page below and tried to get it working with Ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

I downloaded the Windows drivers from here:
[http://www.fjall.org/d505/](http://www.fjall.org/d505/)

Problem is it still doesn't work!

Running "tail /var/log/messages" shows the following, which all looks good (I think) apart from the final line:
> Apr  7 17:11:41 d505-laptop kernel: [ 4885.154633] usbcore: deregistering interface driver ndiswrapper
Apr  7 17:11:41 d505-laptop kernel: [ 4885.154776] ndiswrapper (ntoskernel_exit:2677): object deb5fd20(2) was not freed, freeing it now
Apr  7 17:11:41 d505-laptop kernel: [ 4885.179009] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Apr  7 17:11:41 d505-laptop kernel: [ 4885.198678] ndiswrapper: driver bcmwl5 (Broadcom,11/02/2005, 4.10.40.0) loaded
Apr  7 17:11:41 d505-laptop kernel: [ 4885.199084] ndiswrapper 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Apr  7 17:11:41 d505-laptop kernel: [ 4885.203503] ndiswrapper: using IRQ 5
Apr  7 17:11:41 d505-laptop kernel: [ 4885.417343] wlan0: ethernet device 00:90:96:f0:01:85 using NDIS driver: bcmwl5, version: 0x40a2800, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
Apr  7 17:11:41 d505-laptop kernel: [ 4885.417458] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr  7 17:11:41 d505-laptop kernel: [ 4885.417558] usbcore: registered new interface driver ndiswrapper
Apr  7 17:11:42 d505-laptop kernel: [ 4885.518360] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Running "lshw -C Network" shows the following:
> *-network:0            
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:f0:01:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,11/02/2005, 4.10.4 latency=32 multicast=yes wireless=IEEE 802.11g

But still no wireless networks are available.  Clicking on the network icon in the system bar (top right) there's just a "disconnected" message under "Wireless Networks".

Any advice would be greatly appreciated!

---

### Post by Gunman1982 on 2010-04-07
If I may suggest:
Uninstall ndiswrapper and try this page:
[http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")
They say your card is supported:
14e4:4320 | supported | BCM4306/2 | b/g | G | b43legacy 
But keep in mind that you need firmware for the driver to work, the page tells you where/how to get it and where to put it.

Imho ndiswrapper should only be used if there is absolutely no other solution.

---

### Post by kmsalex on 2010-04-07
are you shour the card isn't a dud, did it work in windows, or is this the first time your using it?

---

### Post by NurMohammod on 2010-04-07
> **Gunman1982 said:**
> If I may suggest:
Uninstall ndiswrapper and try this page:
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
They say your card is supported:
14e4:4320 | supported | BCM4306/2 | b/g | G | b43legacy 
But keep in mind that you need firmware for the driver to work, the page tells you where/how to get it and where to put it.

Imho ndiswrapper should only be used if there is absolutely no other solution.
I have no usb dial-up modriver for ubuntu 9.10. Now I'm using xp sp2 that supports .exe driver. how can i get a ubuntu supported usb dial-up modem driver?

---

### Post by Gunman1982 on 2010-04-07
> **NurMohammod said:**
> I have no usb dial-up modriver for ubuntu 9.10. Now I'm using xp sp2 that supports .exe driver. how can i get a ubuntu supported usb dial-up modem driver?
.... What? ... 
You want to use a usb dial-up modem? I would suggest creating a new thread with some more information: Whch Ubuntu version are you using, type of modem, ...

---

### Post by Cohech on 2010-04-07
> **kmsalex said:**
> are you shour the card isn't a dud, did it work in windows, or is this the first time your using it?

Sorry, should have said in original post - Ubuntu has replaced WinXP on this laptop.  Wireless was working fine under WinXP.

---

### Post by Cohech on 2010-04-07
> **Gunman1982 said:**
> If I may suggest:
Uninstall ndiswrapper and try this page:
[http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")
They say your card is supported:
14e4:4320 | supported | BCM4306/2 | b/g | G | b43legacy 
But keep in mind that you need firmware for the driver to work, the page tells you where/how to get it and where to put it.

Imho ndiswrapper should only be used if there is absolutely no other solution.

Tried running b43-fwcutter earlier (it was automatically installed after first logging in) but no joy.  I believe I read it doesn't support my card but your link contradicts this.

I'll try re-installing Ubuntu (rather than revert all the changes I've made) and following the instructions provided.  Thanks for the suggestion.

---

### Post by wfarr_09 on 2010-04-07
> **Cohech said:**
> Tried running b43-fwcutter earlier (it was automatically installed after first logging in) but no joy.  I believe I read it doesn't support my card but your link contradicts this.

I'll try re-installing Ubuntu (rather than revert all the changes I've made) and following the instructions provided.  Thanks for the suggestion.


I think it's a universal problem across all of the older laptops, because I'm having the same sort of issue.

---

