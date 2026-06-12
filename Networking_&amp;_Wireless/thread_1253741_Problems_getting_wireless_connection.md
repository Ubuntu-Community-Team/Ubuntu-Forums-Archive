---
title: "Problems getting wireless connection"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by Erik Ramsey on 2009-08-30
I am new to this OS. I have downloaded the latest version of Ubuntu, 9.x on my Dell Latitude D630. I have a Linksys SRX200 wireless router with which I have no problem to access when booted to WinXP.

I attempted to setup Ubuntu with the necessary data including SSID and security information, yet it won't recognize the wireless connection and therefore I cannot access the internet. I have to admit that I don't fully know everything that may have been asked for in setting this up, so I might be lacking some key information.

Forgive me if this basic question has been asked previously, but a search didn't turn up anything specifically. The help feature is pretty vague about how to go about this, which leads me to think this process should go effortlessly.

Help?   Erik:confused:

---

### Post by t0mppa on 2009-08-30
Ok, let's start from the beginning: open up a terminal (Applications / Accessories / Terminal), run **lshw -C network** and post back with the details to find out what kind of a wireless chip you have, what state it is in and if it's getting associated with any drivers.

---

### Post by Erik Ramsey on 2009-08-30
Ok, here goes:
_____________________________________
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

nandan@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:c4:1f:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:38:b7:bf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5755m-v3.29 ip=192.168.15.101 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:6f:63:82:91:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
nandan@ubuntu:~$

---

### Post by t0mppa on 2009-08-30
Ok, personally I have no experience with setting up Intel cards, but it seems to be working and getting associated with a driver.

Try running **sudo iwlist scanning** and see if you can see any networks near you. If you can see your own network, then try clicking the networking icon on the top panel and choosing your network to connect into it. If you have a hidden SSID, try making it public and see if you can then access it through the above steps.

If the above command can detect no networks, then there's some trouble with the drivers and you'll need help from someone who's more experienced with Intel cards or you can always try a Google search with your chip name (Intel 3945ABG).

---

### Post by Erik Ramsey on 2009-08-30
Thanks, I really wouldn't know where to start:
_________________________________________

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

nandan@ubuntu:~$ sudo iwlist scanning
[sudo] password for nandan: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:68:09:81
                    ESSID:"erik"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=98/100  Signal level:-27 dBm  Noise level=-66 dBm
                    Encryption key:on
                    IE: Unknown: 00046572696B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD0C000AF50A0202C00003010305
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000006157c36181
                    Extra: Last beacon: 60ms ago

pan0      Interface doesn't support scanning.

---

### Post by Erik Ramsey on 2009-08-30
According to:
[http://intellinuxwireless.org/](http://intellinuxwireless.org/)
It appears the drivers addressed here:
Note: The iwlwifi driver has been merged into mainline kernel since 2.6.24. If you are using kernels after this release, please use the intree (drivers/net/wireless/iwlwifi) driver directly. After 2.6.26 the intree driver iwlagn also supports the new 5100BG, 5100ABG, 5100AGN, 5300AGN and 5350AGN series hardwares.

later they state:
There used to be a driver specific for the 3945 hardware (ipw3945 hosted on ipw3945.sourceforge.net). This project is deprecated, please use the _iwlwif_i driver instead.

What is iwlwifi? Does it appear I am accessing this driver?

Erik

---

### Post by bkratz on 2009-08-30
> **Erik Ramsey said:**
>  Cell 01 - Address: 00:16:B6:68:09:81
                    ESSID:"erik"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=98/100  Signal level:-27 dBm  Noise [/COLOR]level=-66 dBm
                    Encryption key:on
                    IE: Unknown: 00046572696B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD0C000AF50A0202C00003010305
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000006157c36181
                    Extra: Last beacon: 60ms ago

pan0      Interface doesn't support scanning.

You seem to be seeing a signal named " Eric" , it is encrypted. Have you right clicked on the network icon at the top of the screen and  tried to setup the network?  Remember you do have to disconnect the wired connection when trying the wireless.

---

### Post by oboedad55 on 2009-08-30
> **Erik Ramsey said:**
> According to:
[http://intellinuxwireless.org/](http://intellinuxwireless.org/)
It appears the drivers addressed here:
Note: The iwlwifi driver has been merged into mainline kernel since 2.6.24. If you are using kernels after this release, please use the intree (drivers/net/wireless/iwlwifi) driver directly. After 2.6.26 the intree driver iwlagn also supports the new 5100BG, 5100ABG, 5100AGN, 5300AGN and 5350AGN series hardwares.

later they state:
There used to be a driver specific for the 3945 hardware (ipw3945 hosted on ipw3945.sourceforge.net). This project is deprecated, please use the _iwlwif_i driver instead.

What is iwlwifi? Does it appear I am accessing this driver?

Erik

Erik, I have the same card in my laptop, it is very common. I just had to go and pick a wireless network by left clicking on the icon. Then right click and pick edit connections and choose to edit the wireless connection and check the box that says connect automatically.
If you search the forums for this card you'll find some other answers.

--Jon

---

### Post by Erik Ramsey on 2009-08-30
Jon, Thanks for the encouragement.
Let me review the settings in the wireless setup:

Under Wireless tab:

I have the SSIP filled in.
Mode is infrestructure
Bssid is empty
MAC address is empty
MYU automatic

Under Wire;less security:
Security, I have filled in
WEP index is the default, 1
Authenication is Open System

IPV4 Settings:
Method is Automatic
DHCP client is blank.

Nothing in 'Routes"

Do I have everything set correctly?

Erik

---

### Post by oboedad55 on 2009-08-30
> **Erik Ramsey said:**
> Jon, Thanks for the encouragement.
Let me review the settings in the wireless setup:

Under Wireless tab:

I have the SSIP filled in.
Mode is infrestructure
Bssid is empty
MAC address is empty
MYU automatic

Under Wire;less security:
Security, I have filled in
WEP index is the default, 1
Authenication is Open System

IPV4 Settings:
Method is Automatic
DHCP client is blank.

Nothing in 'Routes"

Do I have everything set correctly?

Erik

Looks like mine. I have DHCP set to automatic. I didn't change any of the default settings. Did you change anything? If so, go back to the original settings and see if that works.

--Jon

---

