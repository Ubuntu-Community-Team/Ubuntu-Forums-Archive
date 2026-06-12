---
title: "ralink RT5370 help me with compiling drivers"
date: 2012-05-26
forum: Networking &amp; Wireless
---

### Post by GreatDanton on 2012-05-26
Hey.
Few days ago I bought USB Wifi adapter, to connect old pc (Running CNC linux 10.04) to the Wifi. However I wasn't able to connect, because I have no experience in compiling drivers. Now I am trying to connect my desktop computer (take a look at signature) with Precise Pangolin on it, but without success. I was googling around and found this site:

```
http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html
```

which is helpful, but didn't solve my problem at all. I have downloaded drivers from Ralink site, I typed the commands in the terminal (set wpa_Supplicant=y, make, make install). Installation was successful.

When I type lsusb in terminal, terminal recognize my adapter, however I am not able to see the Wifi connections in Network Manager (I think it's called like that).

Does anybody knows how to solve this? Thanks in advance :)

---

### Post by chili555 on 2012-05-26
Let's see:```
lsusb
sudo modprobe rt5370sta
dmesg | grep -e rt5 -e wlan
iwconfig
```Thanks.

---

### Post by GreatDanton on 2012-05-26
lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 004 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 005 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 002 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 005 Device 006: ID 18a5:0302 Verbatim, Ltd 

```

sudo modprobe rt5370sta  = nothing happened


dmesg | grep -e rt5 -e wlan:

```
jan@Jan-Desktop:~$ dmesg | grep -e rt5 -e wlan
[19252.819761] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[19254.234372] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[19254.236019] wlan0: authenticated
[19254.255745] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[19254.258009] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[19254.258013] wlan0: associated
[19372.815289] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[19374.226403] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[19374.227910] wlan0: authenticated
[19374.247400] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[19374.249536] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[19374.249539] wlan0: associated
[19492.803194] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[19494.218184] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[19494.219818] wlan0: authenticated
[19494.239433] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[19494.241570] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[19494.241573] wlan0: associated
[19612.804470] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[19614.218214] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[19614.219846] wlan0: authenticated
[19614.239464] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[19614.241726] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[19614.241729] wlan0: associated
[19732.818376] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[19734.230246] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[19734.231877] wlan0: authenticated
[19734.251497] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[19734.253769] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[19734.253773] wlan0: associated
[19852.813286] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[19854.222153] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[19854.223784] wlan0: authenticated
[19854.243278] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[19854.245414] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[19854.245418] wlan0: associated
[19972.818069] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[19974.234558] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[19974.236070] wlan0: authenticated
[19974.255557] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[19974.257830] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[19974.257835] wlan0: associated
[20092.824978] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[20094.238590] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[20094.240225] wlan0: authenticated
[20094.259714] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[20094.261975] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[20094.261979] wlan0: associated
[20212.818505] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[20214.230248] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[20214.231886] wlan0: authenticated
[20214.251495] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[20214.253755] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[20214.253759] wlan0: associated
[20332.806788] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[20334.226153] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[20334.227783] wlan0: authenticated
[20334.247525] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[20334.249670] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[20334.249674] wlan0: associated
[20452.812072] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[20454.222309] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[20454.223940] wlan0: authenticated
[20454.243434] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[20454.245694] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[20454.245698] wlan0: associated
[20572.803601] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[20574.218338] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[20574.219973] wlan0: authenticated
[20574.239464] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[20574.241600] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[20574.241603] wlan0: associated
[20692.813879] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[20694.246744] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[20694.248388] wlan0: authenticated
[20694.268243] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[20694.270377] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[20694.270380] wlan0: associated
[20812.813787] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[20814.222152] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[20814.223782] wlan0: authenticated
[20814.243275] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[20814.245570] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[20814.245574] wlan0: associated
[21172.820881] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[21174.230871] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[21174.232504] wlan0: authenticated
[21174.251994] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[21174.255126] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[21174.255130] wlan0: associated
[21292.797285] wlan0: deauthenticated from 00:1d:7e:fb:94:33 (Reason: 7)
[21294.206152] wlan0: authenticate with 00:1d:7e:fb:94:33 (try 1)
[21294.207782] wlan0: authenticated
[21294.227404] wlan0: associate with 00:1d:7e:fb:94:33 (try 1)
[21294.229661] wlan0: RX ReassocResp from 00:1d:7e:fb:94:33 (capab=0x411 status=0 aid=2)
[21294.229664] wlan0: associated
[22925.091519] wlan0: deauthenticating from 00:1d:7e:fb:94:33 by local choice (reason=3)

```

iwconfig:

```
lo        no wireless extensions.

eth2      no wireless extensions.

ra0       Ralink STA  ESSID:"RDL-GT"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


That's it-Hope this helps.

P.S My Wifi has Mac address security, but I think that first of all I have to see Wifi connection in Network Manager.

---

### Post by chili555 on 2012-05-26
> I typed the commands in the terminal (set [COLOR="Red"]wpa_Supplicant=y[/COLOR], make, make install). Installation was successful.Please double-check your work and follow the excellent roadmap here: [http://ubuntuforums.org/showpost.php?p=11027794&postcount=4](http://ubuntuforums.org/showpost.php?p=11027794&postcount=4)

Did you make *BOTH* the changes here?> Open the resulting folder and go to os > linux and use any text editor to edit config.mk. [COLOR="Red"]Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.[/COLOR] Proofread carefully, save and close the text editor.If not, please do so and re-compile:```
sudo su
modprobe -r rt5370sta
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt5370sta
exit
```When you are done, check:```
sudo iwlist wlan0 scan
```Do you see networks?

---

### Post by GreatDanton on 2012-05-26
> Did you make BOTH the changes here?
Quote: Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Yes I made both changes, just forgot to type that in my text :)

sudo iwlist wlan0 scan:
```
jan@Jan-Desktop:~$ sudo iwlist wlan0 scan
[sudo] password for jan: 
wlan0     Interface doesn't support scanning.


```

Hmmm, no networks what to do now?

---

### Post by chili555 on 2012-05-26
Let's see:```
dmesg | grep -i rt2
dmesg | grep rt5
```Thanks.

---

### Post by GreatDanton on 2012-05-26
dmesg | grep -i rt2:
```
[23546.818331] <==== rt28xx_init, Status=0
[23547.983951] <==== rt28xx_init, Status=0
[23549.146083] <==== rt28xx_init, Status=0
[24548.059732] <==== rt28xx_init, Status=0
[24549.226113] <==== rt28xx_init, Status=0
[24550.404863] <==== rt28xx_init, Status=0
[25732.416918] <==== rt28xx_init, Status=0
[25733.580299] <==== rt28xx_init, Status=0
[25734.745054] <==== rt28xx_init, Status=0

```

dmesg | grep rt5:

Wow, thank you very much. This works for me. However I don't know if this will work for me after reboot.

---

### Post by chili555 on 2012-05-26
> Wow, thank you very much. This works for me. What works? I don't think we did anything except ask for information.

:confused:  :confused:  :confused:

---

### Post by GreatDanton on 2012-05-26
Well I am not sure what happened, but when I copy and paste your command then suddenly, Wifi adapter starts-but it was losing connection. After a while it stopped and now I can't connect anymore :).

If i copy and paste:dmesg | grep rt5
nothing happen

dmesg | grep -i rt2
```
[23546.818331] <==== rt28xx_init, Status=0
[23547.983951] <==== rt28xx_init, Status=0
[23549.146083] <==== rt28xx_init, Status=0
[24548.059732] <==== rt28xx_init, Status=0
[24549.226113] <==== rt28xx_init, Status=0
[24550.404863] <==== rt28xx_init, Status=0
[25732.416918] <==== rt28xx_init, Status=0
[25733.580299] <==== rt28xx_init, Status=0
[25734.745054] <==== rt28xx_init, Status=0
[25825.970263] <==== rt28xx_init, Status=0
[25827.140263] <==== rt28xx_init, Status=0
[25828.310640] <==== rt28xx_init, Status=0
[25849.558672] <==== rt28xx_init, Status=0
[25850.728669] <==== rt28xx_init, Status=0
[25851.907786] <==== rt28xx_init, Status=0
[25995.414082] <==== rt28xx_init, Status=0
[26041.407380] <==== rt28xx_init, Status=0
[26122.443413] <==== rt28xx_init, Status=0
[26163.420163] <==== rt28xx_init, Status=0
[26183.148438] <==== rt28xx_init, Status=0
[26184.313434] <==== rt28xx_init, Status=0
[26185.478099] <==== rt28xx_init, Status=0
[26206.123819] <==== rt28xx_init, Status=0
[26207.291045] <==== rt28xx_init, Status=0
[26208.459544] <==== rt28xx_init, Status=0
[26252.429512] <==== rt28xx_init, Status=0
[26314.423488] <==== rt28xx_init, Status=0
[26334.538950] !!! rt28xx Initialized fail !!!
[26336.854748] <==== rt28xx_init, Status=0
[26338.021140] <==== rt28xx_init, Status=0
[26339.194373] <==== rt28xx_init, Status=0
[26359.644474] <==== rt28xx_init, Status=0
[26367.164480] <==== rt28xx_init, Status=0
[26370.425715] <==== rt28xx_init, Status=0
[26376.073226] <==== rt28xx_init, Status=0

```

Thanks for your help!

---

### Post by chili555 on 2012-05-26
May I see:```
ls /etc/Wireless/RT2870STA/
```If there is a dat file in there, post:```
head -n5 /etc/Wireless/RT2870STA/RT2870STA.dat
```

---

### Post by GreatDanton on 2012-05-27
ls /etc/Wireless/RT2870STA/ :

```
RT2870STA.dat  RT2870STA.dat~
```


head -n5 /etc/Wireless/RT2870STA/RT2870STA.dat:

```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=US

```

Hope this helps. P.S I am not from Usa. Is that a problem, because there I see Country code=US

It's really strange that sometimes when I plug in this Wifi adapter, I am able to get Internet and signal strength is 5, sometimes signal strength (on the same place) is 2, and sometimes I am not able to connect. But most of the time when I plug in my adapter Linux doesn't recognize it.

---

### Post by sssSami on 2012-05-27
Stupid question, though, but did you reboot after installing/compiling the driver?

---

### Post by GreatDanton on 2012-05-27
> **sssSami said:**
> Stupid question, though, but did you reboot after installing/compiling the driver?

No, but yesterday I shut down the computer and today I started it again.

---

### Post by chili555 on 2012-05-27
> I am not from Usa. Is that a problem, because there I see Country code=USWell, you are very perceptive! You caught me.

You might check the README that came with the package you extracted and edit the .dat file to suit your situation. ```
sudo gedit /etc/Wireless/RT2870STA/RT2870STA.dat
```Once you've made the needed changes, reboot. Generally, the driver and the router will work out the country code and other details with the help of wpa_supplicant and Network Manager. 

Check again:```
dmesg | grep -i rt2
```

---

### Post by GreatDanton on 2012-05-27
> **chili555 said:**
> Well, you are very perceptive! You caught me.

You might check the README that came with the package you extracted and edit the .dat file to suit your situation. ```
sudo gedit /etc/Wireless/RT2870STA/RT2870STA.dat
```Once you've made the needed changes, reboot. Generally, the driver and the router will work out the country code and other details with the help of wpa_supplicant and Network Manager. 

Check again:```
dmesg | grep -i rt2
```

I don't understand what you would like to say. Do I have to fill with data all things (don't know how to explain but take a look at the picture), or not? If so which data is needed?

Edit: Here is the output of dmesg | grep -i rt2:

[   37.695251] rtusb init rt2870 --->
[   37.696964] usbcore: registered new interface driver rt2870
[   38.620564] <==== rt28xx_init, Status=0
[   39.781232] <==== rt28xx_init, Status=0
[   40.947146] <==== rt28xx_init, Status=0
[   60.972388] <==== rt28xx_init, Status=0
[   62.132806] <==== rt28xx_init, Status=0
[   63.288355] <==== rt28xx_init, Status=0
[   91.969271] <==== rt28xx_init, Status=0
[   93.133434] <==== rt28xx_init, Status=0
[   94.300230] <==== rt28xx_init, Status=0
[  112.796979] <==== rt28xx_init, Status=0
[  113.957276] <==== rt28xx_init, Status=0
[  115.120314] <==== rt28xx_init, Status=0
[  124.858570] <==== rt28xx_init, Status=0
[  126.023485] <==== rt28xx_init, Status=0
[  127.200904] <==== rt28xx_init, Status=0
[  195.476897] <==== rt28xx_init, Status=0
[  196.641688] <==== rt28xx_init, Status=0
[  197.807851] <==== rt28xx_init, Status=0

---

### Post by chili555 on 2012-05-27
I would certainly change the first several from CountryRegion down to WirelessMode. The README will tell you what the choices are. Be sure you select the correct country code. If it's not listed in the README, check here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

I would think it would be automatic, but perhaps it's not.

Post back if you get stuck. I'm here.

---

### Post by GreatDanton on 2012-05-27
Well I am stuck here. I don't know where to find these numbers like CountryRegion, CountryABand (i see them in readme but i don't know which option to choose). I am not familiar with these things, so if you could tell me which channel to choose and so on.

Country code is now set to SI     (Slovenia)

Here is my readme.

```
* README
*
* Ralink Tech Inc.
* 
* http://www.ralinktech.com
*

=======================================================================
ModelName:
===========
RT2870 Wireless Lan Linux Driver


=======================================================================
Driver lName:
===========
rt2870.o/rt2870.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Ralink Hardware:
===================
Ralink 802.11n Wireless LAN Card.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile	        : Makefile
*.c					: c files
*.h					: header files


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta
	
=======================================================================
CONFIGURATION:  
====================
RT2870 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)modify configuration file "RT2870STA.dat" in /etc/Wireless/RT2870STA/RT2870STA.dat.
           
Configuration File : RT2870STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT2870STA/RT2870STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi RT2870STA.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.
# 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0

-----------------------------------------------
*NOTE:
	WMM parameters
			WmmCapable			Set it as 1 to turn on WMM Qos support				
			AckPolicy1~4		Ack policy which support normal Ack or no Ack
								(AC_BK, AC_BE, AC_VI, AC_VO)		
	
	All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡&#352;¡&#352;, 
	please store all parameter to RT2870STA.dat, and restart driver. 	

-----------------------------------------------
syntax is 'Param'='Value' and describes below. 

@> CountryRegion=value                                 
	value
		0: use 1 ~ 11 Channel
		1: use 1 ~ 13 Channel
		2: use 10 ~ 11 Channel
		3: use 10 ~ 13 Channel
		4: use 14 Channel
		5: use 1 ~ 14 Channel
		6: use 3 ~ 9 Channel
		7: use 5 ~ 13 Channel
	   31: use 1 ~ 14 Channel (ch1-11:active scan, ch12-14 passive scan)
   	 	                                      
@> CountryRegionABand=value      							
	value	
		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
		4: use 149, 153, 157, 161, 165 Channel
		5: use 149, 153, 157, 161 Channel
		6: use 36, 40, 44, 48 Channel
		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
		8: use 52, 56, 60, 64 Channel
		9: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 132, 136, 140, 149, 153, 157, 161, 165 Channel
	   10: use 36, 40, 44, 48, 149, 153, 157, 161, 165 Channel
	   11: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 149, 153, 157, 161 Channel

@> CountryCode=value
	value
		AG, AR, AW, AU, AT, BS, BB, BM, BR, BE, BG, CA, KY, CL, CN, CO, CR, CY, CZ, DK, DO, EC, SV, FI, FR, DE, 
		GR, GU, GT, HT, HN, HK, HU, IS, IN, ID, IE, IL, IT, JP, JO, LV, LI, LT, LU, MY, MT, MA, MX, NL, NZ, NO,
		PE, PT, PL, RO, RU, SA, CS, SG, SK, SI, ZA, KR, ES, SE, CH, TW, TR, GB, UA, AE, US, VE
		"" => using default setting: 2.4 G - ch 1~11; 5G - ch 52~64, 100~140, 149~165
                                                           
@> SSID=value                	
	value
		0~z, 1~32 ascii characters.
                    	
@> WirelessMode=value
	value	
		0: legacy 11b/g mixed 
		1: legacy 11B only 
		2: legacy 11A only         //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
		3: legacy 11a/b/g mixed     //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
		4: legacy 11G only
		5: 11ABGN mixed
		6: 11N only
		7: 11GN mixed
		8: 11AN mixed
		9: 11BGN mixed
	   10: 11AGN mixed	
                     
@> Channel=value
	value
		depends on CountryRegion or CountryRegionABand
                    	
@> BGProtection=value
	value
		0: Auto 
		1: Always on 
		2: Always off
                    	
@> TxPreamble=value
  	value
		0:Preamble Long
		1:Preamble Short 
		2:Auto
                    	
@> RTSThreshold=value
	value
		1~2347                                                       
                    	                                       
@> FragThreshold=value
	value       	
		256~2346
                    	
@> TxBurst=value
	value
		0: Disable
		1: Enable

@> NetworkType=value	    		
	value 
		Infra: infrastructure mode
       	Adhoc: adhoc mode
                                                                                                                                                        	                                                          
@> AuthMode=value
	value
		OPEN	 	For open system	
		SHARED	  	For shared key system	
		WEPAUTO     Auto switch between OPEN and SHARED
		WPAPSK      For WPA pre-shared key  (Infra)
		WPA2PSK     For WPA2 pre-shared key (Infra)
		WPANONE		For WPA pre-shared key  (Adhoc)
		WPA         Use WPA-Supplicant
		WPA2        Use WPA-Supplicant

@> EncrypType=value
	value
		NONE		For AuthMode=OPEN                    
		WEP			For AuthMode=OPEN or AuthMode=SHARED 
		TKIP		For AuthMode=WPAPSK or WPA2PSK                    
		AES			For AuthMode=WPAPSK or WPA2PSK                     
		
@> DefaultKeyID=value
	value
		1~4

@> Key1=value
    Key2=value
    Key3=value
    Key4=value
	value
		10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
    (usage : "iwpriv" only)     

@> Key1Type=vaule
    Key2Type=value
    Key3Type=vaule
    Key4Type=vaule
    value
		0   hexadecimal type
		1   assic type
    (usage : reading profile only)

@> Key1Str=value
    Key2Str=value
    Key3Str=vaule
    Key4Str=vaule
    value
		10 or 26 characters (key type=0)
		5 or 13 characters  (key type=1)
    (usage : reading profile only)	

@> WPAPSK=value              	
	value
		8~63 ASCII  		or 
		64 HEX characters
																                    																		
@> WmmCapable=value
	value
		0: Disable WMM
		1: Enable WMM
        
@> PSMode=value
    value
    	CAM			    Constantly Awake Mode
		Max_PSP		    Max Power Savings
		Fast_PSP		Power Save Mode

@> FastRoaming=value
	value
		0				Disabled
		1				Enabled

@> RoamThreshold=value
	value
		Positive Interger(dBm)

@> HT_RDG=value
	value
		0				Disabled
		1				Enabled

@> HT_EXTCHA=value (Extended Channel Switch Announcement)
	value
		0				Below
		1 				Above

@> HT_OpMode=value
	value
		0				HT mixed format
		1				HT greenfield format

@> HT_MpduDensity=value
	value (based on 802.11n D2.0)
		0: no restriction
		1: 1/4 £gs
		2: 1/2 £gs
		3: 1 £gs
		4: 2 £gs
		5: 4 £gs
		6: 8 £gs
		7: 16 £gs

@> HT_BW=value
	value
		0				20MHz
		1				40MHz

@> HT_AutoBA=value
	value
		0				Disabled
		1				Enabled

@> HT_BADecline
	value
		0				Disabled
		1			    Enabled <Reject BA request from AP>

@> HT_AMSDU=value
	value
		0				Disabled
		1				Enabled

@> HT_BAWinSize=value
	value
		1 ~ 64

@> HT_GI=value
	value
		0				long GI
		1				short GI

@> HT_MCS=value
	value
		0 ~ 15
		33: auto

@> HT_MIMOPSMode=value
	value (based on 802.11n D2.0)
		0				Static SM Power Save Mode
		1				Dynamic SM Power Save Mode
		2				Reserved
		3				SM enabled
	(not fully support yet)

@> EthConvertMode=value
	value
		dongle
		clone
		hybrid

@> EthCloneMac=value
	value
		xx:xx:xx:xx:xx:xx

@> IEEE80211H=value
	value
		0				Disabled
		1				Enabled

@> TGnWifiTest=value
	value
		0				Disabled
		1				Enabled

@> WirelessEvent=value
	value
		0				Disabled
		1				Enabled <send custom wireless event>
	    
@> MeshId=value
	value
		Length 1~32 ascii characters

@> MeshAutoLink=value
	value
		0				Disabled
		1				Enabled

@> MeshAuthMode=value
	value
		OPEN	 	For open system	
		WPANONE		For WPA pre-shared key  (Adhoc)

@> MeshEncrypType=value
	value
		NONE		For MeshAuthMode=OPEN                    
		WEP			For MeshAuthMode=OPEN
		TKIP		For MeshAuthMode=WPANONE
		AES			For MeshAuthMode=WPANONE

@> MeshWPAKEY=value
	value
		8~63 ASCII  		or 
		64 HEX characters

@> MeshDefaultkey=value
	value
		1~4

@> MeshWEPKEY=value
	value
		10 or 26 characters
		5 or 13 characters

@> CarrierDetect=value
	value
		0				Disabled
		1				Enabled

MORE INFORMATION
=================================================================================
If you want for rt2870 driver to auto-load at boot time:
A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2870sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'     


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
    add the line
    GATEWAY=x.x.x.x   
    in /etc/sysconfig/network
   
=======================================================================
Dongle/Clone Features:
======================
A) Dongle mode: 
   	Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
   	can transparently connect to the AP.

B) Clone mode:
	Provides a 1-to-1 MAC address mapping mechanism. 
	STA can use own MAC as SA MAC or 
			use user desired MAC as SA MAC or
		    use source MAC of first packet coming from wired device as SA MAC.
	NOTE: In this mode, only the PC who own the specified MAC can connect to the AP.

 
C) Hybrid mode(Dongle+Clone):
	Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
   	can transparently connect to the AP.
	STA can use own MAC as SA MAC or 
			use user desired MAC as SA MAC or
		    use source MAC of first packet coming from wired device as SA MAC.

D) Please refer to "Config STA to link as dongle mode..." in iwpriv_usage.txt for releated commands.
```

---

### Post by chili555 on 2012-05-27
I suggest:

CountryRegion=1

CountryRegionABand=0

SSID=yournetwork [COLOR="Red"]<--whatever the name is for your router
[/COLOR]
WirelessMode=9

I'm a bit concerned about all this:> [ 112.796979] <==== rt28xx_init, Status=0
[ 113.957276] <==== rt28xx_init, Status=0
[ 115.120314] <==== rt28xx_init, Status=0The fact that it repeats continuously is troubling.

---

### Post by GreatDanton on 2012-05-27
i fill in like you suggested.

It seems to be working now, but I concerned, because it took 3 minutes to connect to the wireless,so I am quite sure it will stop once.

At this moment I am connected with this adapter, signal strength is 3 sometimes 4, but we will see if it's working or not. Wifi connection with this adapter is not stable like with my Lynksys WUSB54GC.

Edit:The problem is not solved yet, because sometimes the adapter works and sometimes doesn't.

One funny thing I noticed. When adapter loses connection, if I turn antenna for 360 degres I am connected again (sometimes it work sometimes not)--very strange behaviour :)
 
Here is the output:
dmesg | grep -i rt2
[   10.833507] rtusb init rt2870 --->
[   10.844165] usbcore: registered new interface driver rt2870
[   12.391232] <==== rt28xx_init, Status=0
[   13.636800] <==== rt28xx_init, Status=0
[   39.805595] <==== rt28xx_init, Status=0
[   40.967714] <==== rt28xx_init, Status=0
[   56.060607] <==== rt28xx_init, Status=0
[   57.218970] <==== rt28xx_init, Status=0
[   89.480739] <==== rt28xx_init, Status=0


Thanks for your help! ;)

---

### Post by chili555 on 2012-05-27
When it's connected and you run:```
iwconfig
```What does it say the signal strength is? Can you orient the router differently? Mine produces the best signal strength standing on its nose.

Have you tried different channels? I have better luck with channel 1 or channel 11.

---

### Post by GreatDanton on 2012-05-27
iwconfig:

lo        no wireless extensions.

eth2      no wireless extensions.

ra0       Ralink STA  ESSID:"RDL-GT"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1D:7E:FB:94:33   
          Bit Rate=36 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=92/100  Signal level:-74 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It's very good signal strenght-much better than with my Linksys.

How can I try different channels?

---

### Post by chili555 on 2012-05-27
> How can I try different channels?You'll need to go into the administration pages of the router and change it there. Also,some routers and DSL modems allow you to manipulate the transmission strength. You might check that as well. Please see attached.

---

### Post by GreatDanton on 2012-05-27
Changed the channels, but the problem still remains, so I changed back to the previous configuration. I am still loosing connections with router/signal is wonderful as you can see in the image I had attached in previous post). What can I try now?

I still think that there is problem with drivers not the router.

---

### Post by chili555 on 2012-05-27
> I still think that there is problem with drivers not the router.Please post:```
lsb_release -a
modinfo rt5370sta | grep version
```If you have a newer driver version and an older kernel version, and you got lots of warnings during your compile, we may have better luck with an older version of the driver.

Of course, Ubuntu 12.04 supports your device out of the box.

---

### Post by GreatDanton on 2012-05-27
lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

modinfo rt5370sta | grep version
version:        2.5.0.3
srcversion:     B5F68EDB8F10C7E19E04080
vermagic:       3.2.0-24-generic-pae SMP mod_unload modversions 686 


That is the output. Drivers are from 2011.

---

### Post by chili555 on 2012-05-27
> Of course, Ubuntu 12.04 supports your device out of the box. Please pardon me. I am mistaken. However, the Ubuntu version of compat-wireless does. If you'd care to try:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
sudo modprobe -r rt5370sta
sudo modprobe rt2800usb
```If it works, we'll need to uninstall rt5370sta.

---

### Post by GreatDanton on 2012-05-27
I have installed:
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae

This commands doesn't work for me (sometimes just freezes the system):
sudo modprobe -r rt5370sta
sudo modprobe rt2800usb

One more question. What is this command (modprobe) good for?

---

### Post by chili555 on 2012-05-27
So did it work? Can you connect reliably?> One more question. What is this command (modprobe) good for?modprobe loads a module and all its dependencies. As you might expect, modprobe -r removes a module and all its dependencies. Check here:```
$ modinfo rt2800usb | grep depends
[COLOR="Red"]depends:        rt2x00lib,rt2800lib,rt2x00usb[/COLOR]
```

---

### Post by GreatDanton on 2012-05-27
No, sorry it's not working. Any suggestions?

---

### Post by chili555 on 2012-05-27
Let's see:```
iwconfig
dmesg | grep rt2
```Please skip past all these:> [25732.416918] <==== rt28xx_init, Status=0
[25733.580299] <==== rt28xx_init, Status=0
[25734.745054] <==== rt28xx_init, Status=0Try to see where the new module was modprobed and post everything after that.

---

### Post by GreatDanton on 2012-05-27
iwconfig:lo        no wireless extensions.

eth2      no wireless extensions.


dmesg | grep rt2:
I delete some lines (like this [  918.311974] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.) to shorten the post:

```
[  221.882158] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -71.
[  221.982209] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -71.
0x06 failed for offset 0x0500 with error -19.
[  862.837620] Registered led device: rt2800usb-phy4::radio
[  862.837645] Registered led device: rt2800usb-phy4::assoc
[  862.837678] Registered led device: rt2800usb-phy4::quality
[  863.016663] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3840 with error -71.
[  863.116664] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 
[  866.184663] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  866.194496] phy4 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf15d19f8
[  866.217953] phy4 -> rt2800_wait_bbp_ready: Error - BBP register access failed, aborting.
[  866.217958] phy4 -> rt2800usb_set_device_state: Error - Device failed to enter state 4 (-5).
[  867.762607] Registered led device: rt2800usb-phy5::radio
[  867.762633] Registered led device: rt2800usb-phy5::assoc
[  867.762667] Registered led device: rt2800usb-phy5::quality
[  868.296693] phy5 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x6190 with error -71.
[  868.396663] phy5 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1998 with error -71.
[  868.416662] phy5 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x68cc with error -19.
[  868.433951] phy5 -> rt2800_wait_bbp_ready: Error - BBP register access failed, aborting.
[  868.433957] phy5 -> rt2800usb_set_device_state: Error - Device failed to enter state 4 (-5).
[  870.682654] Registered led device: rt2800usb-phy6::radio
[  870.682679] Registered led device: rt2800usb-phy6::assoc
[  870.682704] Registered led device: rt2800usb-phy6::quality
[  871.352213] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1130 with error -71.
[  871.764586] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 
[  918.311974] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
[  918.312078] phy6 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf15d1960
[  918.724347] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0438 with error -71.
[  919.136846] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0408 with error -71.
[  919.549347] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0408 with error -71.
[  919.964848] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0438 with error -71.
[  920.377350] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -71.
[  920.789723] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -71.
[  921.202223] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -71.
[  921.614723] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -71.
[  922.027223] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -71.
[  922.192597] phy6 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -19.
[  922.202030] phy6 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x0000101c, value=0xf39e5ecc

```

Since it's worse behaviour than before, maybe it's time to recompile?

---

### Post by chili555 on 2012-05-27
> Since it's worse behaviour than before, maybe it's time to recompile?Let's do it in two steps:```
cd Desktop/RT5370 [COLOR="Red"]<--or wherever you extracted the files[/COLOR]
sudo su
make clean
make uninstall
exit
```Now shut down completely. Boot back up. Now check:```
dmesg | grep rt2
```Is it still dire?> phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failedIf not, does it work?

If so, let's blacklist rt2800usb and recompile:```
sudo su
modprobe -r rt2800usb
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
cd Desktop/RT5370 [COLOR="Red"]<--or wherever you extracted the files[/COLOR]
make
make install
modprobe rt5370sta
exit
```If there are warnings, please copy and paste them to a text document so we can examine and possibly fix them.

---

### Post by GreatDanton on 2012-05-27
dmesg | grep rt2:
-nothing happened
-it doesn't work


```
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffset&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c:939:10: warning: unused variable &#8216;bTempSuccess&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c:938:6: warning: unused variable &#8216;LookupTableIndex&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c:937:6: warning: unused variable &#8216;CurrentTemp&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c:936:8: warning: unused variable &#8216;BbpValue&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c:935:32: warning: unused variable &#8216;pTxPowerTuningEntry2&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c:932:8: warning: unused variable &#8216;RFValue&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c:931:32: warning: unused variable &#8216;pTxPowerTuningEntry&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c: In function &#8216;AsicAdjustTxPower&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c:1585:20: warning: unused variable &#8216;pFinalTxPwr&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_asic.c:1583:11: warning: unused variable &#8216;bAutoTxAgc&#8217; [-Wunused-variable]

```

```
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:235:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:242:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:280:11: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:509:12: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:568:13: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:598:12: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:612:12: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:630:13: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;

```

```
/home/jan/Desktop/RT5370/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicLoadFirmware&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rtmp_mcu.c:383:11: warning: unused variable &#8216;MacReg1&#8217; [-Wunused-variable]
```

```
Calibration&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/frq_cal.c:202:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/frq_cal.c:215:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/frq_cal.c:230:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/frq_cal.c:252:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/frq_cal.c:265:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/frq_cal.c:280:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/frq_cal.c:136:10: warning: unused variable &#8216;bUpdateRFR&#8217; [-Wunused-variable]
  CC [M]  /home/jan/Desktop/RT5370/os/linux/../../chips/rt3070.o
  CC [M]  /home/jan/Desktop/RT5370/os/linux/../../chips/rt30xx.o
/home/jan/Desktop/RT5370/os/linux/../../chips/rt30xx.c: In function &#8216;RT30xx_ChipSwitchChannel&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt30xx.c:619:17: warning: unused variable &#8216;BbpR109&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt30xx.c:618:30: warning: unused variable &#8216;Tx1FinePowerCtrl&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt30xx.c:618:8: warning: unused variable &#8216;Tx0FinePowerCtrl&#8217; [-Wunused-variable]
  CC [M]  /home/jan/Desktop/RT5370/os/linux/../../chips/rt33xx.o
/home/jan/Desktop/RT5370/os/linux/../../chips/rt33xx.c: In function &#8216;RT33xxSetRxAnt&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt33xx.c:164:9: warning: unused variable &#8216;x&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt33xx.c: In function &#8216;RT33xx_ChipSwitchChannel&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt33xx.c:409:17: warning: unused variable &#8216;BbpR109&#8217; [-Wunused-variable]
  CC [M]  /home/jan/Desktop/RT5370/os/linux/../../chips/rt3370.o
/home/jan/Desktop/RT5370/os/linux/../../chips/rt3370.c: In function &#8216;NICInitRT3370RFRegisters&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt3370.c:51:7: warning: unused variable &#8216;bbpreg&#8217; [-Wunused-variable]
  CC [M]  /home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.o
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_Init&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:490:25: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c: In function &#8216;RT5390SetRxAnt&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:756:9: warning: unused variable &#8216;Value&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c: In function &#8216;RT5390LoadRFSleepModeSetup&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:915:8: warning: unused variable &#8216;RFValue&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c: In function &#8216;RT5390ReverseRFSleepModeSetup&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:991:8: warning: unused variable &#8216;RFValue&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ChipSwitchChannel&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:1609:17: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:1620:17: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:1634:16: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:1498:17: warning: unused variable &#8216;BbpR110&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:1497:23: warning: unused variable &#8216;BbpR109&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c: In function &#8216;GetDesiredTssiAndCurrentTssi&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:3085:2: warning: missing braces around initializer [-Wmissing-braces]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:3085:2: warning: (near initialization for &#8216;htTssiInfo.PartA.field&#8217;) [-Wmissing-braces]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ATETssiCalibration&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:3364:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:3453:4: warning: passing argument 3 of &#8216;eFuseWrite&#8217; from incompatible pointer type [enabled by default]
/home/jan/Desktop/RT5370/include/rtmp.h:5774:10: note: expected &#8216;PUSHORT&#8217; but argument is of type &#8216;UCHAR *&#8217;
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:3365:42: warning: unused variable &#8216;ChannelPower&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c: In function &#8216;GetPowerDeltaFromTssiRatio&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:3595:2: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;LONG&#8217; [-Wformat]
/home/jan/Desktop/RT5370/os/linux/../../chips/rt5390.c:3624:2: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;LONG&#8217; [-Wformat]
  CC [M]  /home/jan/Desktop/RT5370/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/jan/Desktop/RT5370/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/jan/Desktop/RT5370/os/linux/../../os/linux/usb_main_dev.o
  CC [M]  /home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.o
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;DefaultATEAsicSwitchChannel&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:1276:16: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:1044:21: warning: unused variable &#8216;RFValue2&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;ATETxPwrHandler&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:5358:45: warning: unused variable &#8216;CfgOfTxPwrCtrlOverMAC&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TX_FREQOFFSET_Proc&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:7770:13: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_EX_Proc&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9496:9: warning: unused variable &#8216;CurrentChannel&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9495:9: warning: unused variable &#8216;BSSID_ADDR&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9494:10: warning: unused variable &#8216;ChannelPower&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9493:10: warning: unused variable &#8216;EEPData&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9492:31: warning: unused variable &#8216;TssiDeltaPerChannel&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9492:8: warning: unused variable &#8216;TssiRefPerChannel&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9491:53: warning: unused variable &#8216;BBP49Value&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9491:42: warning: unused variable &#8216;RF28Value&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9491:31: warning: unused variable &#8216;RF27Value&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9491:22: warning: unused variable &#8216;RFValue&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9491:9: warning: unused variable &#8216;BbpData&#8217; [-Wunused-variable]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9499:1: warning: control reaches end of non-void function [-Wreturn-type]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_Proc&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:9483:1: warning: control reaches end of non-void function [-Wreturn-type]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_ATE_E2PROM_READ_BULK&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:4037:1: warning: the frame size of 1036 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_E2PROM_READ_ALL&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:3044:1: warning: the frame size of 1032 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_ATE_E2PROM_WRITE_BULK&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:4070:1: warning: the frame size of 1048 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_E2PROM_WRITE_ALL&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:3061:1: warning: the frame size of 1032 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;Set_EERead_Proc&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:4673:1: warning: the frame size of 1028 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_Load_E2P_Proc&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:8563:1: warning: the frame size of 1044 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_Read_E2P_Proc&#8217;:
/home/jan/Desktop/RT5370/os/linux/../../common/rt_ate.c:8584:1: warning: the frame size of 1028 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  LD [M]  /home/jan/Desktop/RT5370/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jan/Desktop/RT5370/os/linux/rt5370sta.mod.o
  LD [M]  /home/jan/Desktop/RT5370/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic-pae'
```

well I copied warnings when during make

Now make install:
```
 make install
make -C /home/jan/Desktop/RT5370/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/jan/Desktop/RT5370/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/jan/Desktop/RT5370/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-24-generic-pae
make[1]: Leaving directory `/home/jan/Desktop/RT5370/os/linux'
root@Jan-Desktop:/home/jan/Desktop/RT5370# 

```

modprobe rt5370sta-nothing happened.

another question-when i copy and paste this:modprobe rt5370sta
Is something wrong if nothing happened? Does it have to be some pop-up window or something?

I hope you will be able to examine this warnings, because I am really stuck here ;)

Edit: Now if I type lsusb in terminal, it doesn't recognize it anymore. I am not sure if I broke something or not (because I change a lot in USB ports), but the adapter doesn't flash blue light anymore. Tommorow I will try it in Windows, and we will see if the adapter is still ok or not.

---

### Post by chili555 on 2012-05-27
> another question-when i copy and paste this:modprobe rt5370sta
Is something wrong if nothing happened? Does it have to be some pop-up window or something?Nope; that's a good thing. That means, roughly, 'command executed as requested and there are no warnings or errors to report.' That's what you want to happen.> I hope you will be able to examine this warnings, because I am really stuck hereStudying...

---

### Post by chili555 on 2012-05-28
I have played with this driver for hours. I have found and applied patches. I have made manual changes to .h files. I have cursed and prayed. I have downloaded and compiled different versions of the driver. Nothing in my power can get this thing to work with less than a zillion warnings, perhaps a bit fewer than you have. As you have seen, the warnings and unused variables don't allow the driver to actually work!

I suggest we concentrate our efforts on rt2800usb. Please do:```
cd Desktop/RT5370 [COLOR="Red"]<--or wherever you extracted the files[/COLOR]
sudo su
make clean
make uninstall
echo rt2800usb >> /etc/modules
exit
```Now reboot and let us see:```
lsmod | grep rt2
iwconfig
dmesg | grep -i rt2
```Thanks.

---

### Post by GreatDanton on 2012-05-28
```
lsmod | grep rt2
rt2800usb              22150  0 
rt2800lib              52596  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              19941  2 rt2800usb,rt73usb
rt2x00lib              48261  4 rt2800usb,rt2800lib,rt73usb,rt2x00usb
mac80211              440734  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178818  2 rt2x00lib,mac80211

```

```
iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"RDL-GT"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:FB:94:33   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:63   Missed beacon:0

```

I have to inform you that I also have Linksys Usb adapter (I am using it for internet), which is described here at wlan0. Because it is Usb adapter and antenna is inside of the key, the signal is not so strong.

```
dmesg | grep -i rt2
[   10.413801] usbcore: registered new interface driver rt2800usb

```


Anyway, thanks for your effort.

---

### Post by GreatDanton on 2012-05-28
I have downloaded the drivers from Ralink site (this drivers on which we are working on), because I though the newer would be compatible with newer operating system.

There is one last thing to try out. With this Wifi adapter I got also CD with drivers on it. Look at the screenshot I attached. Unfortunately the drivers are from 2008. Which package should I extract and use?

---

### Post by chili555 on 2012-05-28
> I have to inform you that I also have Linksys Usb adapter (I am using it for internet), which is described here at wlan0. We're not going to get meaningful data trying to troubleshoot the internal wireless with a working USB wireless in the way. Please unplug the USB, reboot and run the tests again. You can copy and paste the terminal output to a text document so you can save it to post after you connect with the USB. Your readings, for troubleshooting purposes, need to be *without* the USB. Please add:```
modinfo rt2800usb | grep -e module -e 5370
```> Unfortunately the drivers are from 2008. Which package should I extract and use? None. You aren't going to get a 2008 driver to compile against a 2012 kernel. No way, no how.

---

### Post by GreatDanton on 2012-05-28
```
 lsmod | grep rt2 
rt2800usb              22150  0 
rt2800lib              52596  1 rt2800usb 
crc_ccitt              12595  1 rt2800lib 
rt2x00usb              19941  1 rt2800usb 
rt2x00lib              48261  3 rt2800usb,rt2800lib,rt2x00usb 
mac80211              440734  3 rt2800lib,rt2x00usb,rt2x00lib 
cfg80211              178818  2 rt2x00lib,mac80211 
```

```
iwconfig 
lo        no wireless extensions. 

eth2      no wireless extensions. 
```

```
 dmesg | grep -i rt2 
[   10.481529] usbcore: registered new interface driver rt2800usb

```

```
modinfo rt2800usb | grep -e module -e 5370
filename:       /lib/modules/3.2.0-24-generic-pae/updates/cw-3.3/rt2800usb.ko
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*

```

---

### Post by chili555 on 2012-05-28
Can you please run:```
rfkill list all > danton.txt
dmesg >> danton.txt
lsmod >> danton.txt
```Find the file danton.txt in your user directory and post it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Give us the link so we can hopefully see what's wrong here. Thanks.

---

### Post by GreatDanton on 2012-05-28
Here it is:
[http://paste.ubuntu.com/1011693/](http://paste.ubuntu.com/1011693/)

---

### Post by chili555 on 2012-05-28
I see no sign of your Ralink 5370 device at all in the pastebin. Are you sure it was plugged in when you rebooted? Can you try again and perhaps try a different USB slot? I do see this:> [   22.088048] usb 6-2: new full-speed USB device number 8 using uhci_hcd
[   22.504083] usb 6-2: device not accepting address 8, error -71
[   22.616021] usb 6-2: new full-speed USB device number 9 using uhci_hcd
[   23.032027] usb 6-2: device not accepting address 9, error -71According to your lsusb in post #3, the Ralink was in 2-2, so I wonder if the error is relevant.> [COLOR="Red"]Bus 002 Device 002[/COLOR]: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

---

### Post by GreatDanton on 2012-05-28
Ok here it is:
[http://paste.ubuntu.com/1011855/](http://paste.ubuntu.com/1011855/)

Yes I am sure that adapter is connected to the USB.
I switched the adapter to the other Usb port, so that's the reason why you don't see it in the paste.ubuntu.com. (Now I have switched it back to the previous port-so it's in the port 2-2)

Also I would like to mention that since I have installed -something like backports (Edit: This is the command: sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae), I am not able to see Wifi adapter with lsusb command(I am sure it's connected to the Usb).

Why is so? Do I have to remove that application or not?

---

### Post by chili555 on 2012-05-28
While I study the pastebin, let's have a look:```
lsusb
```

---

### Post by GreatDanton on 2012-05-28
Well, here it is:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 004 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard

---

### Post by chili555 on 2012-05-28
> Do I have to remove that application or not?I doubt it has any connection, but you can try:```
sudo apt-get remove linux-backports-modules-cw-3.3-precise-generic-pae
```Remember, however, that the 5370 device is recognized in backports but not the default in-kernel rt2800usb. I would be more suspicious that your kernel parameter acpi=force is a factor.> Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=0c942e6d-965f-4532-bf2a-eb51a57f9028 ro [COLOR="Red"]acpi=force[/COLOR] quiet splash vt.handoff=7

There is no sign of your device in pastebin or lsusb. I wonder if either the device or the USB bus is faulty.

---

### Post by GreatDanton on 2012-05-28
I remove backports-like you said nothing has changed.

I add acpi=force because I had to unplug the cables of the computer to shut it down.

---

### Post by GreatDanton on 2012-05-28
I delete acpi=off line/ nothing changed so far. I am unable to shut down, and the Wifi adapter is not recognized.

---

### Post by chili555 on 2012-05-28
> **GreatDanton said:**
> I delete acpi=off line/ nothing changed so far. I am unable to shut down, and the Wifi adapter is not recognized.I wonder if either the device or the USB bus is faulty. Can you test the device in another computer?

---

### Post by GreatDanton on 2012-05-28
I will try tommorow. Today I tryed on Windows XP (still got it somewhere), and windows recognized that something is plugged in, but I wasn't able to get the internet because of drivers. I also have Live Fedora 16 on Usb, and I try device in Fedora, unfortunately no luck for me-it doesn't recognize it (lsusb).

Tommorow I will try it on Windows 7 and we will see if it's still working or not (before I was trying to get it work in Ubuntu I tryed Usb in Windows 7 and it was working/ however I don't know if it still working ;)

---

### Post by jrushslo on 2012-05-31
Hi ! I also trying to setup RT5370 WiFi card.
And i not satisfyed with speed(signal quality?) of rt5370sta ralink compiled driver.
Now i activate rt2800usb module, but new Wireless interface not appeared.
My data is here: [http://paste.ubuntu.com/1016338/](http://paste.ubuntu.com/1016338/)
P.S. When rt2800usb driver is loaded, lsusb not works and hangs.
rmmod rt2800usb also not possible (helps only removing configs and reboot).

---

### Post by chili555 on 2012-05-31
> **jrushslo said:**
> Hi ! I also trying to setup RT5370 WiFi card.
And i not satisfyed with speed(signal quality?) of rt5370sta ralink compiled driver.
Now i activate rt2800usb module, but new Wireless interface not appeared.
My data is here: [http://paste.ubuntu.com/1016338/](http://paste.ubuntu.com/1016338/)
P.S. When rt2800usb driver is loaded, lsusb not works and hangs.
rmmod rt2800usb also not possible (helps only removing configs and reboot).I'm sorry, I have only one suggestion. Not all driver hacks work for all devices all the time. You might download the live CD for Ubuntu 12.04 and see if it works better.

---

### Post by gnusci on 2012-05-31
Try Wicd, but you need to stop the NetworkManager.

---

### Post by jrushslo on 2012-05-31
> **chili555 said:**
> I'm sorry, I have only one suggestion. Not all driver hacks work for all devices all the time. You might download the live CD for Ubuntu 12.04 and see if it works better.

with LiveCD i successfully install rt2800usb and appears wlan0 interface, but pings to my AP have same problem:
64 bytes from 192.168.1.1: icmp_req=581 ttl=64 time=940 ms
64 bytes from 192.168.1.1: icmp_req=582 ttl=64 time=254 ms
64 bytes from 192.168.1.1: icmp_req=583 ttl=64 time=1103 ms
64 bytes from 192.168.1.1: icmp_req=585 ttl=64 time=1239 ms
Maybe it's cheap WiFi hardware issue...
Later i will repeat my tests under Windows.

---

### Post by chili555 on 2012-05-31
Would you please try:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb nohwcrypt=1
ping -c3 192.168.1.1
```Any improvement? If so we can write a quick file to make it permanent.

---

### Post by GreatDanton on 2012-06-11
Hi again.

I've been away for a while so I was not able to test it on the Windows machine. Today I have tested it and it's not working anymore (before messing with Ubuntu drivers it was working). In Windows it says something like Usb device malfunction-please reconnect and try again. Even if I install drivers from scratch it's not working. I don't know what we have done, because I am not the expert, but I hope you know what we are doing.

So what did we wrong? Any solutions to solve this?

---

### Post by chili555 on 2012-06-11
I'm not aware of anything that can be done to damage a wireless device from Ubuntu or Windows. Either the driver, firmware and hardware combination work or they don't. I am also not aware of anything that can be done to fix a damaged a wireless device.

In this case, it's evidently the hardware that doesn't work.

---

### Post by GreatDanton on 2012-06-12
Yeah it's strange behaviour and I accepted that the hardware don't work, but I still can't accept the fact that Wifi adapter was working on Windows, but now it doesn't anymore. Well thanks for your help anyway.

---

