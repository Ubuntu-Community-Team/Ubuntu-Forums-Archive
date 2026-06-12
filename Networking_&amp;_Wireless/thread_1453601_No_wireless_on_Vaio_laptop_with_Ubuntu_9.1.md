---
title: "No wireless on Vaio laptop with Ubuntu 9.1"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by archkidd on 2010-04-13
I am running Ubuntu 9.10 from the install CD on a Vaio VGN TX650P laptop to try it (my first time with Linux so please bear with me) and it all works EXCEPT it is not recognizing my wireless connection.
I went to Ubuntu Help and in Section 5 - Wireless Troubleshooting, Check for Device Recognition, it recommended:
   
1.Open a Terminal (Applications &#8594; Accessories &#8594; Terminal) and type the command: sudo lshw -C network
You should see an output, along with the words "CLAIMED, UNCLAIMED, ENABLED or DISABLED"
What I get is below.  (It also lists the ethernet connections as network 0) but I don't see any CLAIMED etc.
"*-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: b
       bus info: pci@0000:06:0b.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:98:5d:37
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:22 memory:b0108000-b0108fff"

So, I went to the section on 'Using Windows Drivers' where it says that you have to use the ndisgtk package to allow Windows wireless drivers under ubuntu. But the first instructions says "Obtain the Windows Driver for your system and locate the file that ends with .inf."  What does that mean?  'Obtain"?  Above it lists the driver as ipw2200 which I cannot find anywhere on my computer, but there is a whole folder of .inf files.
Am I even on the right track? Help please.

---

### Post by archkidd on 2010-04-13
Update!  I found the Community Support Wireless Troubleshooting Guide, which I should have done earlier.  Through this I found that ipw2200 is the ubuntu driver and by using sudo iwlist scan I can show that my wireless card is recognized 
"eth1      Scan completed :
          Cell 01 - Address: 00:22:A4:1D:4A:49
                    ESSID:"2WIRE192"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-45 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 164ms ago
But I still cannot connect to the router. Running sudo iwconfig I get
"eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This would seem to indicate that I am not associated with a router.
Still trying!

---

### Post by archkidd on 2010-04-14
Problem solved!  I decided to do  an install, dual boot, instead of running off the CD.  When I did that the wireless connected seamlessly!  So the CD does not seem to operate the same way as an install?  I did at least learn a lot about ubuntu.

---

### Post by coffeecat on 2010-04-14
> **archkidd said:**
> So the CD does not seem to operate the same way as an install?

I think you'll find it will with the Intel 2200BG chipset. I have that on my old Sony laptop and it works just fine - live CD or HD install.

If you have the time and/or curiosity, boot up from the live Karmic CD. When the desktop has loaded resist any temptation to open a terminal! :wink: Instead, have a look for the Network manager applet icon. When unconnected it's pretty-well insignificant looking and easy to miss. It should be next to the audio volume icon near the right on the upper panel. Click on it and you should see all available wireless networks. Click on your network, type in your passkey where prompted, and voila! Easier than Windows! :p

---

### Post by archkidd on 2010-04-15
Thanks, but that is what I was doing.  The Network Manager showed my network but would not connect.  I even tried turning off my security to no avail.  Now I don't have to use the Manager, the box for my passkey just comes up automatically and I am in.

---

