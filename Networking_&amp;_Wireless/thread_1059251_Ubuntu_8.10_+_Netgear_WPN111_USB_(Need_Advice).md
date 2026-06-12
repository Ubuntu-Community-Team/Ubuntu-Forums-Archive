---
title: "Ubuntu 8.10 + Netgear WPN111 USB (Need Advice)"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by ozbuntu01 on 2009-02-03
Hi all ,

I am a begginer with linux/ubuntu , so I will try to keep this short, sweet & to the point.

OK

My aim is to solve my Wireless Netgear WPN111 adapter, internet connection drop out problem.

_OS:_ Ubuntu 8.10
_Wireless Dongle:_ Netgear WPN111
_Router:_ Netgear DG834G

This is the link/guide I started with: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

...............................................................................................................................................................

_Step 1 [Successful]_: I Install the ndisgtk package from the Ubuntu repositories: 

```
sudo apt-get install ndisgtk 
```


_Step 2 [Successful]_: I blacklist all the Free Drivers to avoid interference: 

```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```


_Step 3 [Successful]_: I identify the Wireless USB Adapter:

```
lsusb
```

_**The following was the output:**_

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 1385:5f01 Netgear, Inc WPN111 (no firmware) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 



_Step 4 [Successful]_: I installed the Driver on my Windows PC & I find the INF / SYS / BIN files. Which are:

-ar5523.bin
-netwpn11.inf
-WPN111.cat
-WPN111.sys

All these files were in the same folder.



_Step 5 [Successful]_: I transfer the Driver files onto my Ubuntu PC using my usb stick. I copy the folder onto the desktop.

_Step 6 [Successful]_: I open ndisgtk and "Add" driver , directing it to the INF file. The Driver installs fine and is present in ndisgtk. (NOTE: All this done WITHOUT WPN111 adapter connected)

_Step 7 {Successful]_: I make sure the Driver installed correctly:

```
ndiswrapper -l
```

_**The following was the output:**_

netwpn11 : driver installed 
	device (1385:5F01) present 



_Step 8 [Successful]_: I load the driver into memory, and try to establish a network connection:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

**Both commands slightly delay after enter. Then returns to default.** (I presume it worked correctly)


_Step 9 [Successful]_: I check for error messages:

```
tail /var/log/messages
```

_**The following was the output:**_

Feb  4 07:23:46 xxxx-desktop kernel: [  825.014100] usbcore: registered new interface driver usb-storage 
Feb  4 07:23:46 xxxx-desktop kernel: [  825.014112] USB Mass Storage support registered. 
Feb  4 07:23:51 xxxx-desktop kernel: [  830.014166] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2 
Feb  4 07:23:51 xxxx-desktop kernel: [  830.017763] sd 4:0:0:0: [sdb] 31506432 512-byte hardware sectors (16131 MB) 
Feb  4 07:23:51 xxxx-desktop kernel: [  830.018527] sd 4:0:0:0: [sdb] Write Protect is off 
Feb  4 07:23:51 xxxx-desktop kernel: [  830.021388] sd 4:0:0:0: [sdb] 31506432 512-byte hardware sectors (16131 MB) 
Feb  4 07:23:51 xxxx-desktop kernel: [  830.022138] sd 4:0:0:0: [sdb] Write Protect is off 
Feb  4 07:23:51 xxxx-desktop kernel: [  830.022184]  sdb: sdb1 
Feb  4 07:23:51 xxxx-desktop kernel: [  830.268970] sd 4:0:0:0: [sdb] Attached SCSI removable disk 
Feb  4 07:23:51 xxxx-desktop kernel: [  830.269227] sd 4:0:0:0: Attached scsi generic sg1 type 0 



_Step 10 [Successful]_: I also check the following:

```
ifconfig
iwconfig
```

_**The following is the output:**_


eth0      Link encap:Ethernet  HWaddr 00:1c:c0:b4:e5:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:632 (632.0 B)  TX bytes:632 (632.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:18:4d:d6:60:ad  
          inet addr:192.XXX.X.X  Bcast:192.XXX.X.XXX  Mask:255.255.255.0 
          inet6 addr: fe80::218:4dff:fed6:60ad/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:21434 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:23020 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:8619601 (8.6 MB)  TX bytes:3204126 (3.2 MB) 


...............................................................................................................................................................


lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:33:85:D1:EE   
          Bit Rate=54 Mb/s   
          Power Management:off 
          Link Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 


...............................................................................................................................................................


_Step 11 [Successful]_: I configure for "Automatic Loading at Startup" using the following:

```
sudo ndiswrapper -m 
```   (this adds an Alias to associate wlan0 to ndiswrapper in modprobe.d )


_Step 12 [Successful]_: I restart PC & connect the NETGEAR WPN111 USB Adapter.
Network Manager reveals "Wireless Networks available"

_Step 13 [Succesful]_: I configure my IPv4 Settings manually , configuring the Address / Netmask / Gateway / DNS Severs.

_Step 14 [Successful]_: I enable "WPA personal" wireless security & enter my password , I also enter the keyring phrase lock afterwards.

SSID: NETGEAR
Mode: Infrastructure
BSSID: N/A
MAC Address: N/A
MTU: automatic



_Step 15 [Successful]_: I enter my Netgear Router settings & I Add the new device MAC address into the "Access Point Control List". Corresponding with the WPA Security.

_Step 16 [Successful]_: I open Network Manager and Connect the Wireless Network. It connects fine.

_**Step 17 [NEED HELP]**_: After succesful connection. After a few minutes , the UPLOAD & DOWNLOAD just STOP in their tracks as if there is no more connection. (Cannot browse web pages , DL/UL speeds hang on 0 , sometimes DL sits on = 0.5kbps or similar)


.................................................................................................................................................................


**NOTE: Here is some Additional Info:**

```
lshw -C Network
```

WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1c:c0:b4:e5:0d 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes 
  *-network:0 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:18:4d:d6:60:ad 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.53+NETGEAR,09/26/2005,1.5.0.21 ip=192.168.0.2 multicast=yes wireless=IEEE 802.11g 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 22:c5:00:6e:56:55 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

..................................................................................................................................................................


NOTE: The exact same outcome happend for **"Automatic DHCP"** & **"WEP Security"** settings also.

It Connects fine for a few minutes , then completely drops out, But the NETGEAR Wireless Driver is still acting as if it is "Connected" as the Network & Signal Strength are still available.

Maybe I have:
-missed something
-done something incorrect
-is a potential bug ?


_Does anyone have some more suggestions/ideas about this ??? Would be muchly appreciated._

_If you need anymore information on any aspect please ask._

Cheers :D

---

### Post by ozbuntu01 on 2009-02-03
Bump :popcorn:

---

### Post by ozbuntu01 on 2009-02-03
:guitar: Bumpidy

I really hope Ubuntu will support the Netgear WPN111 USB Wireless Adapter out of the box shortly :D

---

### Post by ozbuntu01 on 2009-02-03
UPDATE: 

- Even after the Wireless Adapter Connection drops out , the WPN111 Adapter still says it is "Connected" in Network Manager also with Full Signal strength (As suggested by the network icons).
I tried entering my router settings and checking the "Attatched Devices" Setting , My router is _**NOT**_ picking up the WPN111 Wireless Adapter Device in the Attatched Devices list.

Bring any ideas to mind ?

---

### Post by ozbuntu01 on 2009-02-04
Burp :D

---

### Post by kamlesh30rao on 2009-02-04
Looks like you are doing lots of setting manually. In my case a fresh installation of Ubuntu 8.10 detected everything and was able to show all the Wireless Connections.  It is also able to connect to Wireless Router without any problems, and get an IP address.

But, the Internet doesn't work. Even I am unable to ping to router (192.168.1.1)

My Router is : Cisco LinkSys WRT54G
My USB : Netgear WG111v3
My OS - Uubutu version 8.10 (32bit running on AMD desktop PC)

Regards,
Kamlesh

---

### Post by ozbuntu01 on 2009-02-04
Hi Kamlesh ,

Seems like we are experiencing very similar issues. (If not identical)


One important thing to NOTE here is that:

1) My Wireless Adapter is: Netgear WPN111 -  _**NOT Supported Out of the Box**_

2) Your Wireless Adapter is: Netgear WG111v3 -   _**SUPPORTED Out of the Box**_ (Supposively)


Also NOTE:

1) My router is: Netgear DG834G

2) Your Router is: Cisco LinkSys WRT54G

(Which is worth mentioning)


Yet we are using different routers , but experiencing very similar issues with these Netgear USB Wireless Adapters.


NOTE: You can also follow along with Kamlesh30rao Thread for the "Netgear WG111v3 USB Dongle" here: [http://ubuntuforums.org/showthread.php?t=1059999](http://ubuntuforums.org/showthread.php?t=1059999)


As we are experiencing very similar problems (If not identical) , I think our threads should be kept close together. :D

---

### Post by ozbuntu01 on 2009-02-05
](*,) Bump

---

### Post by ozbuntu01 on 2009-02-06
\\:D/ Bump

---

### Post by ozbuntu01 on 2009-02-09
#-o Bump

---

### Post by natrixnatrix89 on 2009-03-14
Hi. I have a Netgear WPN111 too.. I see you dig deep. In my case I just ordered a linksys adapter that is supported out of the box.. which gives much less sweating.. :D
If I were you I would donate the Netgear WPN111 to the poor.. ;)

---

### Post by booyoo on 2009-03-20
@ozbuntu01 Does your netgear equipment work flawlessly with windows? I've been having similar 'crawl to a halt' tranfers using this atheros 108 technology and never got it to work right in their turbo (channel binding) mode. I suggest you try to set your router to not use turbo but only SuperG and see if its stable.

@natrixnatrix89 Better not donate to the poor...they already suffer...

---

### Post by Scubdup on 2009-03-20
Can't offer any decent help I'm afraid.
Just wanted to say I experienced a lot of problems with my Netgear WG111v3 (documented in various requests for help on here!) before eventually giving up and buying a £12 replacement made by Edimax. IMO this was the best solution. The replacement really did work straightaway and since then I have had no problems whatsoever with my internet connection.

Good luck however you choose to proceed.

---

### Post by darrenleeweber on 2010-05-02
I switched from the default network manager to

wicd - wired and wireless network manager

Try that and see if you get more stable network connectivity.

PS, Thanks for your detailed post on how to install the driver.

---

### Post by darrenleeweber on 2010-05-02
Trying

[http://wireless.kernel.org/en/users/Drivers/ath9k_htc](http://wireless.kernel.org/en/users/Drivers/ath9k_htc)

Got the 'raw' firmware file "ar9271.fw" from

[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD)

Placed this file into /lib/firmware/ and then 

'sudo chown root:root /lib/firmware/ar9271.fw' 

Then reboot and see what happens.  (Will update post if it works.)

---

