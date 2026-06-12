---
title: "Wireless Authentication failure?"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by vsrao on 2009-06-13
I am facing a situation I don't know how to debug. Can anyone pls help? Here are my details:

HP/Compaq nx9010 Laptop (P4 2.4GHz, 512MB RAM, 40GB HDD)
Latest Ubuntu (9.0.4) downloaded and installed just a couple of days ago. 
Earlier this was loaded with winxp pro sp2. 

I have a Dlink 2460 ADSL2 + Broadband router, configured with WPA security & mac address based acl. Works fine with my other laptops and mobile device. Obviously I have allowed this laptop's MAC address in the ADSL router. 

I already did:

**sudo apt-get install b43-fwcutter**

$ uname -a
$ Linux cmcgb-user-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

$ lspci -vnn | grep 14e4
$ 00:09.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)

All packages are uptodate & latest. 

$ dmesg | grep b43
[    3.828231] b43-pci-bridge 0000:00:09.0: enabling device (0000 -> 0002)
[    3.828249] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNK3] -> GSI 10 (level, low) -> IRQ 10
[   14.793274] b43legacy-phy0: Broadcom 4301 WLAN found
[   14.816073] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   14.816097] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   14.840097] b43legacy-phy0 debug: Radio initialized
[   29.518539] input: b43legacy-phy0 as /devices/virtual/input/input9
[   29.552118] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   29.649703] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   29.722144] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   29.912098] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   30.012323] b43legacy-phy0 debug: Chip initialized
[   30.012633] b43legacy-phy0 debug: 30-bit DMA initialized
[   30.017947] Registered led device: b43legacy-phy0:tx
[   30.017977] Registered led device: b43legacy-phy0:rx
[   30.018015] Registered led device: b43legacy-phy0:radio
[   30.018056] b43legacy-phy0 debug: Wireless interface started
[   30.026009] b43legacy-phy0 debug: Adding Interface type 2
[   30.520044] b43legacy-phy0: Radio hardware status changed to DISABLED
[   30.531741] b43legacy-phy0 debug: Radio initialized
[   30.616054] b43legacy-phy0: Radio turned on by software
[   30.616062] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

$ tail /var/log/wpa_supplicant.log
Trying to associate with 00:1c:f0:3d:7e:ec (SSID='Suri-Home' freq=2462 MHz)
Authentication with 00:1c:f0:3d:7e:ec timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1c:f0:3d:7e:ec (SSID='Suri-Home' freq=2462 MHz)
Authentication with 00:1c:f0:3d:7e:ec timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1c:f0:3d:7e:ec (SSID='Suri-Home' freq=2462 MHz)
CTRL-EVENT-SCAN-RESULTS 
Authentication with 00:1c:f0:3d:7e:ec timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1c:f0:3d:7e:ec (SSID='Suri-Home' freq=2462 MHz)
Authentication with 00:1c:f0:3d:7e:ec timed out.

Obviously the authentication is failing. But why & how do I debug? This is my first try at Ubuntu.

Thanks and Regards
V S Rao

---

### Post by vsrao on 2009-06-13
[INDENT]Sorry to post reply to my own question, but thought I would post the following also:

$ iwconfig
wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:3D:7E:EC
                    ESSID:"Suri-Home"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/100  Signal level:-53 dBm  Noise level=-43 dBm
                    Encryption key:on
                    IE: Unknown: 0009537572692D486F6D65
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000c2d13e1b6
                    Extra: Last beacon: 132ms ago

Thanks 
V S Rao

[/INDENT]

---

### Post by Bucky Ball on 2009-06-13
Go to Synaptic Package Manager (System->Administration), search for and install

ubuntu-restricted-extras

You should be offered an update when done; accept. Give it a minute and does it now tell you there is a hardware driver available?

Open System->Admin->Hardware Drivers. What do you have in there?

---

### Post by vsrao on 2009-06-13
Thanks for the response. Installed ubuntu-restricted-extras. Did not prompt me for anything. Rebooted laptop. No result.

Hardware drivers says:

Broadcom b43legacy wireless driver.

Thanks 
V S Rao

---

### Post by Bucky Ball on 2009-06-13
System->Admin->Update Manager

Anything?

And the broadcom legacy driver in Hardware Drivers is obviously enabled? (box to the right should tell ya).

---

### Post by vsrao on 2009-06-13
Update Manager updated a few updates like firefox etc. No change. Yes the driver is enabled. 

iwlist scan shows that the system can detect my wireless router and trying to connect. It is failing to authenticate. So obviously there must be an issue with WPA PSK. But where and how do I debug that?

Thanks
V S Rao

---

### Post by Bucky Ball on 2009-06-14
In

System->Admin->Network

You must have the correct details to match those in your router. You router (or AP - Access Point) will, or should, have a name for your network and be set with a WPA key. Get into the router config and get these details or set them if they aren't there. 

Open the 'Network' gui and:

Make sure 'enable roaming' is disabled
Set 'Configuration' to 'Automatic Configuration (DHCP)'. Everything below this should be left blank as you are getting served an IP by your router, and to do that ... make sure above and to the right in that window, the details for network name and WPA match those of your router.

---

