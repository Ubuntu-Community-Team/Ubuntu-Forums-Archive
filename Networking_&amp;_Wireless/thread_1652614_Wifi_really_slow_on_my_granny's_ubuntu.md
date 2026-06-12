---
title: "Wifi really slow on my granny's ubuntu"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by JeyPeyy on 2010-12-25
I've installed Ubuntu 10.04 on my french grandmother's computer and tried to make a very simple configuration for her. The only problem is that the wifi connection is really slow. If I boot Windows (vista) it gets much faster.

I don't want to upgrade to 10.10 because I live in Sweden and I only get to see her here once every two years. I don't have any firewall running, so I don't see where the problem is.

---

### Post by JeyPeyy on 2010-12-25
iwconfig shows this:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Livebox-8d8c"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:70:58:8F:C0   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by JeyPeyy on 2010-12-25
I found out I might need to install windows drivers. I have a cd with drivers for the router mounted on /media/Livebox/, but I don't know which driver I should choose. Here is the output from 'tree /media/Livebox/Drivers/':

> /media/Livebox/Drivers/
&#9500;&#9472;&#9472; Sagem
&#9474;   &#9500;&#9472;&#9472; XG-703A
&#9474;   &#9474;   &#9492;&#9472;&#9472; Win98_Me_2K_XP
&#9474;   &#9474;       &#9500;&#9472;&#9472; WlanUI9X.sys
&#9474;   &#9474;       &#9500;&#9472;&#9472; WlanUIG.cat
&#9474;   &#9474;       &#9500;&#9472;&#9472; WlanUIG.inf
&#9474;   &#9474;       &#9492;&#9472;&#9472; WlanUIG.sys
&#9474;   &#9500;&#9472;&#9472; XG-760A
&#9474;   &#9474;   &#9500;&#9472;&#9472; 98_Me_2K_XP
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanUZ2K.sys
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanUZ98.sys
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanUZG.cat
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanUZG.inf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanUZME.sys
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; WlanUZXP.sys
&#9474;   &#9474;   &#9500;&#9472;&#9472; Vista_7
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; athru6ext.cat
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; athru6.sys
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; netathru6.inf
&#9474;   &#9474;   &#9492;&#9472;&#9472; Vista_7 64bit
&#9474;   &#9474;       &#9500;&#9472;&#9472; athrxu6ext.cat
&#9474;   &#9474;       &#9500;&#9472;&#9472; athrxu6.sys
&#9474;   &#9474;       &#9492;&#9472;&#9472; netathrxu6.inf
&#9474;   &#9500;&#9472;&#9472; XG-760N et XG-762N
&#9474;   &#9474;   &#9500;&#9472;&#9472; 98_Me_2K_XP
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanBZ2K.sys
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanBZ64.SYS
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanBZ98.sys
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanBZG.cat
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanBZG.inf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; WlanBZME.sys
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; WlanBZXP.sys
&#9474;   &#9474;   &#9500;&#9472;&#9472; Vista_7
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; athrusbext.cat
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; athrusb.sys
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; netathrusb.inf
&#9474;   &#9474;   &#9492;&#9472;&#9472; Vista_7 64bit
&#9474;   &#9474;       &#9500;&#9472;&#9472; athrxusbext.cat
&#9474;   &#9474;       &#9500;&#9472;&#9472; athrxusb.sys
&#9474;   &#9474;       &#9492;&#9472;&#9472; netathrxusb.inf
&#9474;   &#9500;&#9472;&#9472; XN-720
&#9474;   &#9474;   &#9500;&#9472;&#9472; Vista_7
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; arusb_lh.cat
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; arusb_lh.inf
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; arusb_lh.sys
&#9474;   &#9474;   &#9500;&#9472;&#9472; Vista_7 64bit
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; arusb_lhx.cat
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; arusb_lhx.inf
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; arusb_lhx.sys
&#9474;   &#9474;   &#9492;&#9472;&#9472; XP
&#9474;   &#9474;       &#9500;&#9472;&#9472; arusb_2k.pdb
&#9474;   &#9474;       &#9500;&#9472;&#9472; arusb_2k.sys
&#9474;   &#9474;       &#9500;&#9472;&#9472; arusb_xp.cat
&#9474;   &#9474;       &#9500;&#9472;&#9472; arusb_xp.inf
&#9474;   &#9474;       &#9500;&#9472;&#9472; arusb_xp.pdb
&#9474;   &#9474;       &#9500;&#9472;&#9472; arusb_xp.sys
&#9474;   &#9474;       &#9500;&#9472;&#9472; arusb_xpx.pdb
&#9474;   &#9474;       &#9492;&#9472;&#9472; arusb_xpx.sys
&#9474;   &#9492;&#9472;&#9472; XN-720s
&#9474;       &#9500;&#9472;&#9472; Vista_7
&#9474;       &#9474;   &#9500;&#9472;&#9472; WlanuhnV32.cat
&#9474;       &#9474;   &#9500;&#9472;&#9472; WLANUHNV32.inf
&#9474;       &#9474;   &#9492;&#9472;&#9472; WlanuhnV32.sys
&#9474;       &#9500;&#9472;&#9472; Vista_7 64bit
&#9474;       &#9474;   &#9500;&#9472;&#9472; WlanuhnV64.cat
&#9474;       &#9474;   &#9500;&#9472;&#9472; WLANUHNV64.inf
&#9474;       &#9474;   &#9492;&#9472;&#9472; WlanuhnV64.sys
&#9474;       &#9492;&#9472;&#9472; XP
&#9474;           &#9500;&#9472;&#9472; WLANUH2k.sys
&#9474;           &#9500;&#9472;&#9472; WLANUH64.sys
&#9474;           &#9500;&#9472;&#9472; WLANUHN.cat
&#9474;           &#9500;&#9472;&#9472; WLANUHN.inf
&#9474;           &#9492;&#9472;&#9472; WLANUHN.sys
&#9492;&#9472;&#9472; Thomson
    &#9500;&#9472;&#9472; Cameo_WLG-1500A
    &#9474;   &#9500;&#9472;&#9472; 2000
    &#9474;   &#9474;   &#9500;&#9472;&#9472; setparam.ini
    &#9474;   &#9474;   &#9500;&#9472;&#9472; sis163u.cat
    &#9474;   &#9474;   &#9500;&#9472;&#9472; sis163u.inf
    &#9474;   &#9474;   &#9500;&#9472;&#9472; SiS163u.sys
    &#9474;   &#9474;   &#9492;&#9472;&#9472; Unwlsdrv.exe
    &#9474;   &#9500;&#9472;&#9472; 98
    &#9474;   &#9474;   &#9500;&#9472;&#9472; SIS163u.CAT
    &#9474;   &#9474;   &#9500;&#9472;&#9472; SiS163u.INF
    &#9474;   &#9474;   &#9500;&#9472;&#9472; SiS163u.sys
    &#9474;   &#9474;   &#9492;&#9472;&#9472; UNWLSDRV.EXE
    &#9474;   &#9500;&#9472;&#9472; ME
    &#9474;   &#9474;   &#9500;&#9472;&#9472; SIS163u.CAT
    &#9474;   &#9474;   &#9500;&#9472;&#9472; SiS163u.INF
    &#9474;   &#9474;   &#9500;&#9472;&#9472; SiS163u.sys
    &#9474;   &#9474;   &#9492;&#9472;&#9472; UNWLSDRV.EXE
    &#9474;   &#9500;&#9472;&#9472; Vista_7
    &#9474;   &#9474;   &#9500;&#9472;&#9472; DPInst.exe
    &#9474;   &#9474;   &#9500;&#9472;&#9472; sis163u.cat
    &#9474;   &#9474;   &#9500;&#9472;&#9472; sis163u.inf
    &#9474;   &#9474;   &#9500;&#9472;&#9472; SiS163u.sys
    &#9474;   &#9474;   &#9492;&#9472;&#9472; Uninstall.bat
    &#9474;   &#9500;&#9472;&#9472; Vista_7 64bit
    &#9474;   &#9474;   &#9500;&#9472;&#9472; dmapi.dll
    &#9474;   &#9474;   &#9500;&#9472;&#9472; DPInst.exe
    &#9474;   &#9474;   &#9500;&#9472;&#9472; installInf.exe
    &#9474;   &#9474;   &#9500;&#9472;&#9472; sis163u.cat
    &#9474;   &#9474;   &#9500;&#9472;&#9472; sis163u.inf
    &#9474;   &#9474;   &#9500;&#9472;&#9472; SiS163u.sys
    &#9474;   &#9474;   &#9492;&#9472;&#9472; Uninstall.bat
    &#9474;   &#9492;&#9472;&#9472; XP
    &#9474;       &#9500;&#9472;&#9472; setparam.ini
    &#9474;       &#9500;&#9472;&#9472; sis163u.cat
    &#9474;       &#9500;&#9472;&#9472; SiS163u.INF
    &#9474;       &#9500;&#9472;&#9472; SiS163u.sys
    &#9474;       &#9492;&#9472;&#9472; Unwlsdrv.exe
    &#9492;&#9472;&#9472; TG123g
        &#9500;&#9472;&#9472; 2000
        &#9474;   &#9500;&#9472;&#9472; net8187b.cat
        &#9474;   &#9500;&#9472;&#9472; net8187b.inf
        &#9474;   &#9492;&#9472;&#9472; rtl8187B.sys
        &#9500;&#9472;&#9472; 98
        &#9474;   &#9500;&#9472;&#9472; net8187b.inf
        &#9474;   &#9492;&#9472;&#9472; rtl8187B.sys
        &#9500;&#9472;&#9472; ME
        &#9474;   &#9500;&#9472;&#9472; net8187b.inf
        &#9474;   &#9492;&#9472;&#9472; rtl8187B.sys
        &#9500;&#9472;&#9472; Vista_7
        &#9474;   &#9500;&#9472;&#9472; net8187b.cat
        &#9474;   &#9500;&#9472;&#9472; net8187b.inf
        &#9474;   &#9492;&#9472;&#9472; rtl8187B.sys
        &#9500;&#9472;&#9472; Vista_7 64bit
        &#9474;   &#9500;&#9472;&#9472; dmapi.dll
        &#9474;   &#9500;&#9472;&#9472; installInf.exe
        &#9474;   &#9500;&#9472;&#9472; net8187b.cat
        &#9474;   &#9500;&#9472;&#9472; net8187b.inf
        &#9474;   &#9492;&#9472;&#9472; rtl8187B.sys
        &#9500;&#9472;&#9472; XP
        &#9474;   &#9500;&#9472;&#9472; net8187b.cat
        &#9474;   &#9500;&#9472;&#9472; net8187b.inf
        &#9474;   &#9492;&#9472;&#9472; rtl8187B.sys
        &#9492;&#9472;&#9472; XP 64bit
            &#9500;&#9472;&#9472; dmapi.dll
            &#9500;&#9472;&#9472; installInf.exe
            &#9500;&#9472;&#9472; net8187b.cat
            &#9500;&#9472;&#9472; net8187b.inf
            &#9492;&#9472;&#9472; rtl8187B.sys

35 directories, 107 files

btw, is there a way to use a filter with tree, so that only files with the name "*.inf" are shown?

---

### Post by JeyPeyy on 2010-12-26
Anyone? I can't find the model name, I only see that it's a sagem. I've installed all drivers under /media/Livebox/Drivers/Sagem/*/(XP and older). How can I find out which model I have, and why is it still not much faster?

I'm not staying here very long, and I REALLY need to fix this for her before I leave. So PLEASE someone help me.

---

### Post by Boondoklife on 2010-12-26
I would start with lspci, it should help you figure out just what card you are dealing with.

---

### Post by wilee-nilee on 2010-12-26
Are you sure it is defaulting to her wifi not somebody else's?

---

### Post by JeyPeyy on 2010-12-27
> **Boondoklife said:**
> I would start with lspci, it should help you figure out just what card you are dealing with.


[QUOTE=lspci]00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)[/QUOTE]



[QUOTE=wilee-nilee]Are you sure it is defaulting to her wifi not somebody else's?[/QUOTE]

Positive. I can see from the NetworkManager applet that I'm connected to that one (the name is written on the backside of the router).

---

### Post by Boondoklife on 2010-12-27
post the output of ```
iwlist wlan0 scan
```

You can test if you are connecting to the wrong network by just changing the password for wifi access. This should force you to put the new password in to connect to it again.

---

### Post by JeyPeyy on 2010-12-27
> **Boondoklife said:**
> post the output of ```
iwlist wlan0 scan
```

> **iwlist wlan0 scan]wlan0     Scan completed :
          Cell 01 - Address: 00:19:70:58:8F:C0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"Livebox-8d8c"
                    Bit Rates:1 Mb/s said:**
> 


[QUOTE=Boondoklife;10284045]You can test if you are connecting to the wrong network by just changing the password for wifi access. This should force you to put the new password in to connect to it again.
Ok, I'm sure I'm on the right network anyways, but thanks for the tip.

---

### Post by bkratz on 2010-12-27
May not help but I notice in your second post

wlan0 IEEE 802.11bg ESSID:"Livebox-8d8c" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:19:70:58:8F:C0 
[COLOR="Red"]Bit Rate=1 Mb/s[/COLOR] Tx-Power=20 dBm 
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=59/70 Signal level=-51 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Could be worth a try to do the following 

sudo iwconfig wlan0 rate 54M

to set the bit rate higher

---

### Post by JeyPeyy on 2010-12-27
> **bkratz said:**
> May not help but I notice in your second post

wlan0 IEEE 802.11bg ESSID:"Livebox-8d8c" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:19:70:58:8F:C0 
[COLOR="Red"]Bit Rate=1 Mb/s[/COLOR] Tx-Power=20 dBm 
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=59/70 Signal level=-51 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Could be worth a try to do the following 

sudo iwconfig wlan0 rate 54M

to set the bit rate higher

That didn't help :/

---

### Post by grahammechanical on 2010-12-27
Here is a link to the wireless trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I wonder if you are confused. You do not need drivers for the router. You may need a driver for the wireless adapter in the computer but you are getting a connection to the router only it is a slow connection.

From lspci your wireless adapter is

> 09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)If you think that a different driver would give you a better performance then read the trouble shooting guide on ndiswrapper.

It is my guess that the files on the Windows driver disc that you should be interested in are those files that begin with > ath. I think that they reference Atheros

regards.

---

