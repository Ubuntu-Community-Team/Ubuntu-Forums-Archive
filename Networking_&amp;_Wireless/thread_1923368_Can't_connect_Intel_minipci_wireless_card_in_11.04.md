---
title: "Can't connect Intel minipci wireless card in 11.04"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by grey1beard on 2012-02-10
I've just done a clean install of 11.04 Natty on my Toshiba Satellite A30 2.6GHz, 1.2G RAM, and the wireless card was detected and is switched on.

However, though Enable Wireless and Networking are both ticked, the Wireless Network is greyed out.

I used a LAN connection to update the system, and am using it to post this.

Reading numbers of threads on this general topic, I've produced the following edited info:-

> john@Frizzy:~$ lspci

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

> sudo iwconfig

lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11b  ESSID:"Dragon1805"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:75:29:3B:31   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=100/100  Signal level=-36 dBm  
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc:48   Missed beacon: 0

> dmesg | grep -i ipw2100

[   20.298430] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   20.298437] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   20.308292] ipw2100 0000:02:02.0: PCI INT A -> Link[LNKG] -> GSI 11 (level, low) -> IRQ 11
[   20.309400] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection

sudo iwlist eth1 scan

eth1      Scan completed :
          Cell 01 - Address: 00:22:75:29:3B:31
                    ESSID:"Dragon1805"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:93  Signal level: 0  Noise level: 0
                    Extra: Last beacon: 100ms ago


Grateful for advice on my next move.

John

---

### Post by praseodym on 2012-02-10
Try WPA2-AES encryption instead of "none"

---

### Post by grey1beard on 2012-02-10
> **praseodym said:**
> Try WPA2-AES encryption instead of "none"

That's not a setting in my Network Connections menu that  I can find in 11.04, there's only "WAP & WAP2 Personal" and "WAP & WAP2 Enterprise"

It would also mean setting up passwords for the rest of the network, which I prefer not to at the moment.
Regards
John

---

### Post by praseodym on 2012-02-10
Connect via cable to the router and type the router IP address into your browser. The encryption mode can be changed there. "WPA&WPA2 Personal" is then the right setting in the NM applet

---

### Post by grey1beard on 2012-02-10
I've carried that out, set up a WAP personal, with my desktop and this laptop having the same password.
I then disconnected the LAN line, rebooted, but still no wireless link shows up.:(

Next ?

John

---

### Post by praseodym on 2012-02-11
Well, this card obviously only supports WEP or WPA encryption, respectively. The driver development was cancelled. Did you try an earlier Ubuntu version like 10.04?

---

### Post by grey1beard on 2012-02-11
Yes, I've had it working on 8.04, 9.04, and 10.04.
I've just tried to login to my router, and it no longer accepts any password, either left blank, as originally set, nor the password that was set when I changed it to wap personal, so I'll have to try and sort that out first.
This is where I didn't want to be.

---

### Post by grey1beard on 2012-02-11
Correction to my earlier reference to wap personal.
That should read WPA/WPA-Personal(PSK).
Sorry about that.

I've now got into my router via another system, so I feel a little more secure now.
I await your thoughts,
Regards
John

---

### Post by praseodym on 2012-02-11
Try Wicd with the Add-On:
```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
```
Deactivate/uninstall the NM for that. Choose "wlan0" as interface name and "wext" as driver.

---

### Post by grey1beard on 2012-02-11
I'm fine with the code, but can you spell out where and how I > Choose "wlan0" as interface name and "wext" as driver.

I'm afraid your dealing with a 73 year old newbie :)
John

---

### Post by grey1beard on 2012-02-11
I started the code in terminal, but got a 404 for the url.
> john@Frizzy:~$ wget [http://www.elektronenblitz63.de/down...don0144.tar.gz](http://www.elektronenblitz63.de/down...don0144.tar.gz)
--2012-02-11 10:31:39--  [http://www.elektronenblitz63.de/down...don0144.tar.gz](http://www.elektronenblitz63.de/down...don0144.tar.gz)
Resolving [www.elektronenblitz63.de](www.elektronenblitz63.de)... 82.165.83.231
Connecting to [www.elektronenblitz63.de|82.165.83.231|:80](www.elektronenblitz63.de|82.165.83.231|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-11 10:31:40 ERROR 404: Not Found.


If I click on your link it gives me a file to download, so shall I get it that way ?
EDIT I've downloaded the tar folder, but don't know what to do with it !

---

### Post by grey1beard on 2012-02-11
Well,this is a bit embarrassing, but as I wasn't sure where to place the wicd folder I searched for the existing one.
The search gave its location as the desktop, which puzzled me until I looked at the Applications menu, and lo and behold, at the bottom of the Internet menu, there it was.
Opened it, and ticked connect to wireless automatically, and hey presto, I now am online wirelessly.

The only thing left is that at the moment is that the applet(?) on the top bar doesn't show a connection, and the various menus from it don't display the present state of affairs.
For example, Connection Information says "No valid active connection found", and the top half of the drop down menu is greyed out. The Network Information is also greyed out in the Edit connections menu.

John

---

### Post by praseodym on 2012-02-11
If you start Wicd you need to type in the wireless interface name (e.g. wlan0 or eth1) in the wicd-applet. In the drop-down-menu choose "wext" as driver there. Obviously the Link changed?! Here this link worked:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
```

---

### Post by grey1beard on 2012-02-11
All is now working. :D
Many thanks praseodym.
Regards
John

---

