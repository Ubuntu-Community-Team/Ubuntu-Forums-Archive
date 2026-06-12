---
title: "A-LINK WNU wireless usb stick doesnt work"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Saunatonttu on 2009-11-03
[http://paste.ubuntu.com/308682/](http://paste.ubuntu.com/308682/)

What i could do to make it work?

---

### Post by davidaspey on 2009-11-03
just a quick question ive looked at the log your missing the windows realtek windows drivers? for the rtl8* chipset as show 

[ 4851.583715] usb 1-7: firmware: requesting RTL8192SU/rtl8192sfw.bin

[ 4851.585990] rtl819xU:request firmware fail!

david

soz forgot to add look here for more information

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

---

### Post by Saunatonttu on 2009-11-03
Do i have to install some special firmware packages some where or something?

---

### Post by Saunatonttu on 2009-11-03
ndiswrapper says that hardware present: NO

---

### Post by Saunatonttu on 2009-11-04
i have ubuntu 9.10 karmic koala.
this is the name of my USB stick:
Bus 001 Device 005: ID 0bda:8192 Realtek Semiconductor Corp.

i downloaded drivers from this address:
[http://www.a-link.com/uk/WNU.html?id=iWXT933a](http://www.a-link.com/uk/WNU.html?id=iWXT933a)

but after make command this happened:

 CC [M]  /home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.o
/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_probe’:
/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11614: error: ‘struct net_device’ has no member named ‘open’
/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11615: error: ‘struct net_device’ has no member named ‘stop’
/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11616: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11617: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11618: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11619: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11620: error: ‘struct net_device’ has no member named ‘get_stats’
make[2]: *** [/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/mika/Desktop/ajurit/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2

so r8192U_core.c file has to be edit because it doesnt seems to find open, stop, tx_timeout, do_ioctl,  set_multicast_list,  set_mac_address and get_stats... 

hmm

---

### Post by OldSchool_ on 2010-04-23
I have exactly same identical problem as Saunatonttu has. I have tried to find help from ubuntu-fi forum but no luck there. I really would like to know if there is some proven way to get this work. I'm not expert, just installed this great linux so please help with complete commands and explain what & why.

---

### Post by tpheiska on 2010-10-24
Bump.

Same issue here, A-LINK WNU wireless usb dongle does not work. After plugging the device dmesg gives:

```
[ 1252.380063] usb 2-6: new high speed USB device using ehci_hcd and address 7
[ 1252.519439] usb 2-6: configuration #1 chosen from 1 choice
[ 1252.520809] ==>ep_num:11, in_ep_num:2, out_ep_num:9
[ 1252.520814] ==>RtInPipes:3  9  
[ 1252.520820] ==>RtOutPipes:4  5  6  7  8  10  11  12  13  
[ 1252.520833] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[ 1252.520838] 3  2  1  0  4  8  7  6  5  
[ 1252.536593] Dot11d_Init()
[ 1252.536603] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[ 1252.536607] 
[ 1252.577208] rtl819xU: --->FirmwareDownload92S()
[ 1252.577214] 
[ 1252.577225] usb 2-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 1252.583011] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[ 1252.583015] 
[ 1252.583104] rtl819xU:--->FirmwareDownloadCode()
[ 1252.583107] 
[ 1252.583175] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 1252.852300] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 1252.852305] 
[ 1252.852310] rtl819xU:FirmwareDownloadCode() fail ! 
[ 1252.852313] 
[ 1252.852534] rtl819xU:Firmware Download Fail!!4544
[ 1252.852537] 
[ 1252.868670] rtl819xU: --->FirmwareDownload92S()
[ 1252.868673] 
[ 1252.868677] rtl819xU:--->FirmwareDownloadCode()
[ 1252.868679] 
[ 1252.868746] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 1253.119132] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 1253.119134] 
[ 1253.119138] rtl819xU:FirmwareDownloadCode() fail ! 
[ 1253.119140] 
[ 1253.119373] rtl819xU:Firmware Download Fail!!4544
[ 1253.119375] 
[ 1253.119380] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1253.119383] 
[ 1253.140384] rtl819xU: --->FirmwareDownload92S()
[ 1253.140390] 
[ 1253.140397] rtl819xU:--->FirmwareDownloadCode()
[ 1253.140399] 
[ 1253.140458] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 1253.390970] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 1253.390974] 
[ 1253.390978] rtl819xU:FirmwareDownloadCode() fail ! 
[ 1253.390980] 
[ 1253.391212] rtl819xU:Firmware Download Fail!!4544
[ 1253.391215] 
[ 1253.407352] rtl819xU: --->FirmwareDownload92S()
[ 1253.407354] 
[ 1253.407358] rtl819xU:--->FirmwareDownloadCode()
[ 1253.407360] 
[ 1253.407421] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 1253.658447] rtl819xU:FW_STATUS_LOAD_IMEM FAIL CPU, Status=44
[ 1253.658452] 
[ 1253.658457] rtl819xU:FirmwareDownloadCode() fail ! 
[ 1253.658460] 
[ 1253.658683] rtl819xU:Firmware Download Fail!!4544
[ 1253.658686] 
[ 1253.658695] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1253.658698] 

```

After downloading the drivers from the A-link [site]("http://www.a-link.com/WNU.html") and trying to 'make' I get:

```

~/Lataukset/rtl8192su_linux_2.6.0003.0810.2009$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.o
/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c: In function &#8216;rtl8192_usb_probe&#8217;:
/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11614: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11615: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11616: error: &#8216;struct net_device&#8217; has no member named &#8216;tx_timeout&#8217;
/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11617: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11618: error: &#8216;struct net_device&#8217; has no member named &#8216;set_multicast_list&#8217;
/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11619: error: &#8216;struct net_device&#8217; has no member named &#8216;set_mac_address&#8217;
/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.c:11620: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
make[2]: *** [/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/paavo/Lataukset/rtl8192su_linux_2.6.0003.0810.2009/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [all] Error 2

```

I'm running MythBuntu with Ubuntu 10.04.1 and uname -a:

Linux htpc 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

All help would be greatly appreciated!

---

### Post by tpheiska on 2010-10-24
Managed to get the stick to work using NDISWrapper and the Realtek drivers that I found following a [link]("http://www.realtek.com/products/productsView.aspx?Langid=1&PFid=9&Level=6&Conn=5&ProdID=176") from the Ubuntu [documentation]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek"). I used the "WinXP2K" -driver (Noob note: just extracting the .inf-file will not work, you need to extract the whole directory and install the driver from there).

---

### Post by zupidupi on 2010-11-05
Well, this problem arises because the mentioned functions aren't supported in the kernel used by Maverick. A similar problem is discussed at the following site:

[http://forum.parallels.com/showthread.php?t=95272](http://forum.parallels.com/showthread.php?t=95272)

The solution there doesn't make us happy, though, since it's for an entirely different program.

Anyway, the driver should be updated for the new kernel. It would require  knowledge I don't have...the question is, who has?

---

### Post by chili555 on 2010-11-05
> **zupidupi said:**
> Well, this problem arises because the mentioned functions aren't supported in the kernel used by Maverick. A similar problem is discussed at the following site:

[http://forum.parallels.com/showthread.php?t=95272](http://forum.parallels.com/showthread.php?t=95272)

The solution there doesn't make us happy, though, since it's for an entirely different program.

Anyway, the driver should be updated for the new kernel. It would require  knowledge I don't have...the question is, who has?It appears that the posts above are trying to compile 8192U, however, the module r8192u_usb is built in to the most recent kernel. Is it not working for you?

---

### Post by zupidupi on 2010-11-06
Hiya,

lsusb gives me the following output:

Bus 001 Device 002: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

The driver CD provides me with a driver file named RTL8192SU_... Where does that leave me?!

wonders Mike

---

### Post by chili555 on 2010-11-06
The module r8192s_usb supports your device. Here is what *modinfo* says:> modinfo r8192s_usb | grep 8171
alias:          usb:v[COLOR="Red"]0BDA[/COLOR]p[COLOR="Red"]8171[/COLOR]d*dc*dsc*dp*ic*isc*ip*Insert the device and see if the driver loaded:```
lsmod | grep 8192
```If it loaded and your wireless is still not working, let's check for any helpful messages:```
dmesg | grep 8192
```If it is looking for firmware, this post may be helpful:  [http://ubuntuforums.org/showpost.php?p=9931085&postcount=24](http://ubuntuforums.org/showpost.php?p=9931085&postcount=24)

Remove and reinsert the device and see if it comes to life.

Please post back and let us know how it goes.

---

### Post by zupidupi on 2010-11-06
Sir, you are a Genius! An absolute Genius! Thx - rebooted my system and my dongle is there, finding my network. Copying the firmware to the RTL8192SU-directory did the trick.

Now, unfortunately not everything is OK. As I said, the dongle is found by the system and my wireless network is found by the dongle. But, I can't get a working connection. I tried to connect with the Networkmanager from the GUI, the dongle blinks like a Xmas-tree, but no connection - I don't get an IP-number. 

I booted into console/terminal mode (since that's what I'm gonna do anyway), and did "sudo iwconfig essid="WippiesHome" (I'm running an unprotected network) - but still no connection. I attached some output if you're interested.

You might want to know that "dmesg | grep 8192" sends me quite a few of these messages:

[   84.098311] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth


Thx again, you've been tremendously helpful.

   Mike

mike@salem-center:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:4f:bc:b1:cc  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4fff:febc:b1cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126759881 (126.7 MB)  TX bytes:3071717 (3.0 MB)
          Interrupt:21 Memory:fe9e0000-fea00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1a:9f:92:82:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:745 errors:0 dropped:38 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40286 (40.2 KB)  TX bytes:0 (0.0 B)

mike@salem-center:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n ...  ESSID:"WippiesHome"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1D:19:F7:F0:0A   
          Bit Rate=130 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2010-11-06
> I booted into console/terminal mode (since that's what I'm gonna do anyway), and did "sudo iwconfig essid="WippiesHome" (I'm running an unprotected network) - but still no connection.It wants at least one more command. It wants to know how you wish to connect, either DHCP or static. If it's DHCP, then do:```
sudo dhclient wlan0
```If it's static, then:```
sudo ifconfig wlan0 192.168.what.ever up
```Remember, if you prefer static (as I do), then you are responsible to populate /etc/resolv.conf with DNS nameservers; for example:```
sudo su
echo "nameserver 192.168.your.router" > /etc/resolv.conf
exit
```> Sir, you are a Genius! An absolute Genius!Tell my wife!

---

### Post by zupidupi on 2010-11-07
Well, it's never as easy as you'd think, is it :(

After a clean boot into the console, this is what happens:

[http://pastebin.com/W2e8zFBR](http://pastebin.com/W2e8zFBR)

So, I'm up against the wall once again...any suggestions out there?

Thanks again in advance!

   Mike

---

### Post by chili555 on 2010-11-07
Network Manager is designed to prevent a wireless connection if you have a wired ethernet connection, which you do.

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themPlease detach the cable, wait a few moments for NM to notice the change in state and try again.>  mike@salem-center:~$ sudo dhclient wlan0NM will make it very difficult to impossible to manage your network interfaces with manual methods.

---

### Post by zupidupi on 2010-11-08
Naw... :( No success. The computer finds my adapter, but doesn't make a connection...with or without GDM.

Before I bought the USB-adapter  I used a wireless PCI-card. Everything worked fine with this, also a "double" Internet connection. Somehow the USB-adapter just doesn't fit into the grand scheme of things.

Dunno...shouldn't the message "[  254.724418] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth" ring some bells? But what bells, and what tune?

Wonders a gloomy Mike

---

### Post by zupidupi on 2010-11-08
OK, problem solved! Here's the link that put me on the right track:

[http://www.mail-archive.com/debian-kernel@lists.debian.org/msg56637.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg56637.html)

Obviously the driver provided with the distribution wasn't up to date, working, or generally up to it's karma. So, I downloaded a driver from here:

[http://people.debian.org/~benh/rtl-wlan/](http://people.debian.org/~benh/rtl-wlan/)

I used rtl8192su_linux_2.6.0002.0708.2009.tar.gz, extracted the .bin-file, put it into /lib/firmware/RTL8192SU (of course I took a backup of the original one), rebooted my computer, and! voila! I'm so much online now!

A big heartfelt Thank You to Chili555 who stayed interested and provided invaluable help! May his wife some day acknowledge His Geniusness.

I'm out of here for the moment, happily and wirelessly surfing away.

   Mike

---

### Post by OldSchool_ on 2011-01-10
I still have problems with this [a-link wnu wlan usb]("ftp://ftp.a-link.com/wnu/WNU_FI.pdf")<--(link to specifications). I have just installed xubuntu 10.10 32bit to my old laptop and it's running smoothly but i can't get wlan working. I have at home cable modem and wlan router with nat, wpa2 security and hidden network. 

Here's some data below.

[IMG]http://koti.welho.com/lecksa/sekalaiset/wlantext.jpg[/IMG]

I also followed instructions of this thread [http://ubuntuforums.org/showpost.php?p=9931085&postcount=24]("http://ubuntuforums.org/showpost.php?p=9931085&postcount=24") but no help. Could some one help me?

---

### Post by OldSchool_ on 2011-01-10
EDIT: double post, sorry.

---

### Post by OldSchool_ on 2011-01-10
EDIT: double post, sorry.

---

### Post by OldSchool_ on 2011-01-10
EDIT: double post, sorry.

---

### Post by jaacko on 2011-01-10
I have the older version of the wnu stick (not the WNU-L one). I'm running a fresh install of 32-bit 10.10 and I tried the making-RTL8192SU-folder trick. Didn't work for me. I looked at the windows drivers given at [http://www.a-link.com/WNU.html](http://www.a-link.com/WNU.html) and noticed that the file for the newer stick has a file net8192su.inf while the driver for my older stick has a file net8192u.inf.

dmesg|grep 8192 output:
```
[   50.198722] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   50.212732] Linux kernel driver for RTL8192 based WLAN cards
[   50.968466] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   50.968470] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   51.196407] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   51.196410] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

```

Also tried creating a folder /lib/firmware/RTL8192U and copied the rtl8192sfw.inf there but also no luck.

And i'm sorry for resurrecting an old thread but i think i shouldn't start a new one for this.

---

### Post by jaacko on 2011-01-10
I have the older version of the wnu stick (not the WNU-L one). I'm running a fresh install of 32-bit 10.10 and I tried the making-RTL8192SU-folder trick. Didn't work for me. I looked at the windows drivers given at [http://www.a-link.com/WNU.html](http://www.a-link.com/WNU.html) and noticed that the file for the newer stick has a file net8192su.inf while the driver for my older stick has a file net8192u.inf.

dmesg|grep 8192 output:
```
[   50.198722] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   50.212732] Linux kernel driver for RTL8192 based WLAN cards
[   50.968466] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   50.968470] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   51.196407] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   51.196410] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

```

Also tried creating a folder /lib/firmware/RTL8192U and copied the rtl8192sfw.inf there but also no luck.

And i'm sorry for resurrecting an old thread but i think i shouldn't start a new one for this.

---

### Post by jaacko on 2011-01-10
I have the older version of the wnu stick (not the WNU-L one). I'm running a fresh install of 32-bit 10.10 and I tried the making-RTL8192SU-folder trick. Didn't work for me. I looked at the windows drivers given at [http://www.a-link.com/WNU.html](http://www.a-link.com/WNU.html) and noticed that the file for the newer stick has a file net8192su.inf while the driver for my older stick has a file net8192u.inf.

dmesg|grep 8192 output:
```
[   50.198722] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   50.212732] Linux kernel driver for RTL8192 based WLAN cards
[   50.968466] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   50.968470] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   51.196407] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   51.196410] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

```

Also tried creating a folder /lib/firmware/RTL8192U and copied the rtl8192sfw.inf there but also no luck.

And i'm sorry for resurrecting an old thread but i think i shouldn't start a new one for this.

---

### Post by jaacko on 2011-01-10
I have the older version of the wnu stick (not the WNU-L one). I'm running a fresh install of 32-bit 10.10 and I tried the making-RTL8192SU-folder trick. Didn't work for me. I looked at the windows drivers given at [http://www.a-link.com/WNU.html](http://www.a-link.com/WNU.html) and noticed that the file for the newer stick has a file net8192su.inf while the driver for my older stick has a file net8192u.inf.

dmesg|grep 8192 output:
```
[   50.198722] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   50.212732] Linux kernel driver for RTL8192 based WLAN cards
[   50.968466] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   50.968470] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   51.196407] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   51.196410] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

```

Also tried creating a folder /lib/firmware/RTL8192U and copied the rtl8192sfw.inf there but also no luck.

And i'm sorry for resurrecting an old thread but i think i shouldn't start a new one for this.

---

### Post by OldSchool_ on 2011-01-10
EDIT: double post, sorry.

---

### Post by OldSchool_ on 2011-01-10
EDIT: double post, sorry.

---

### Post by chili555 on 2011-01-10
Open a terminal and do:```
sudo mkdir /lib/firmware/RTL8192U
```Download the attached file to your desktop. Right-click it and select 'Extract Here.' Back to the terminal and do:```
cd Desktop/RTL8192U
sudo cp * /lib/firmware/RTL8192U/
```Now, let's unload and reload the driver:```
sudo rmmod -f r8192u_usb
sudo modprobe r8192u_usb
```Any improvement?

---

### Post by OldSchool_ on 2011-01-11
> **chili555 said:**
> Open a terminal and do:```
sudo mkdir /lib/firmware/RTL8192U
```Download the attached file to your desktop. Right-click it and select 'Extract Here.' Back to the terminal and do:```
cd Desktop/RTL8192U
sudo cp * /lib/firmware/RTL8192U/
```Now, let's unload and reload the driver:```
sudo rmmod -f r8192u_usb
sudo modprobe r8192u_usb
```Any improvement?

That helped little. After i did those the network manager disappeared from top so i reboot system. Now i can get wlan connection to my router and when i check from router it looks like to be connected. In xubuntu if i go to mozilla it says "*can't connect to server *website* please check your network connection*", also update manager says no internet connection even network manager says i'm connected to wireless network.

Here's below some data again but this it looks different. What could be wrong? From windows xp i can connect to internet with same wireless settings so i don't know what now. Please help. 

[IMG]http://koti.welho.com/lecksa/sekalaiset/wlantext2.jpg[/IMG]

---

### Post by chili555 on 2011-01-11
> That helped little. Why would you think that?? You have no more firmware error and you can connect to the router! Please connect and post:```
ifconfig
route -n
cat /etc/resolv.conf
```Thanks.

---

### Post by OldSchool_ on 2011-01-11
> **chili555 said:**
> Why would you think that?? You have no more firmware error and you can connect to the router! Please connect and post:```
ifconfig
route -n
cat /etc/resolv.conf
```Thanks.

So does this help? With these setting it's not work properly.

[IMG]http://koti.welho.com/lecksa/sekalaiset/wlantext3.jpg[/IMG]

---

### Post by chili555 on 2011-01-11
I believe you have an ad-hoc connection; in other words computer to computer. When you run:```
iwconfig
```Does it show Mode:Adhoc? Unless computer to computer is the way you intend to connect, I think you want Managed:```
sudo iwconfig wlan0 mode managed
```Now does Network Manager connect to the router instead?

---

### Post by Olppari on 2011-01-11
Good day everybody!

I've been trying to establish WLAN connection with my A-link WNU adapter for 2 days now. I've managed this far:
I can see available networks and connect to my own wlan network. It says that I'm connected.

Problem:
Cant connect to Internet. When I unplug my ethernet cable or just disconnect it from NM I still am connected to my wlan, but it doesnt take me to Internet.
I tested the wlan with my phone, and it works well.

Here's screen cap of some basic info: 
[IMG]http://users.metropolia.fi/%7Em0602505/Screenshot.png[/IMG]

I'm quite desperate now that I've gotten this adapter to actually show networks and connect them. I had problems first with the firmware which solved by reading this thread. I hope someone can help me with this?

PS. I'm quite new to ubuntu!

---

### Post by chili555 on 2011-01-11
> When I unplug my ethernet cable or just disconnect it from NM I still am connected to my wlan, Please detach the ethernet cable and reboot. Then run and post:```
ping -c3 192.168.100.1
ping -c3 72.14.204.103
ping -c3 www.google.com
```Thanks.

---

### Post by Olppari on 2011-01-11
```

olppari@olppari-ubuntu:~$ ping -c3 192.168.100.1
PING 192.168.100.1 (192.168.100.1) 56(84) bytes of data.

--- 192.168.100.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms

olppari@olppari-ubuntu:~$ ping -c3 72.14.204.103
PING 72.14.204.103 (72.14.204.103) 56(84) bytes of data.

--- 72.14.204.103 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms

olppari@olppari-ubuntu:~$ ping -c3 www.google.com
ping: unknown host www.google.com
olppari@olppari-ubuntu:~$ 


```

Thanks for taking interest! I Hope those are any help. Cheers!

---

### Post by chili555 on 2011-01-11
I don't believe you are actually connected. With the ethernet cable detached, run and post:```
dmesg | grep -e wlan -e 819
```Thanks.

---

### Post by Olppari on 2011-01-11
After detaching cable and reboot:

```

olppari@olppari-ubuntu:~$ dmesg | grep -e wlan -e 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    3.168193] type=1505 audit(1294783459.247:7):  operation="profile_replace" pid=664 name="/usr/lib/connman/scripts/dhclient-script"
[    3.174616] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[    3.177468] Linux kernel driver for RTL8192 based WLAN cards
[    3.642923] usbcore: registered new interface driver rtl819xU
[    3.674495] rtl819xU: --->FirmwareDownload92S()
[    3.674500] usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[    3.679412] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[    3.679434] rtl819xU:--->FirmwareDownloadCode()
[    3.679459] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[    3.680494] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[    3.680496] rtl819xU:--->FirmwareDownloadCode()
[    3.680520] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[    3.682191] rtl819xU:-->FirmwareEnableCPU()
[    3.684745] rtl819xU:IMEM Ready after CPU has refilled.
[    3.684747] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[    3.684749] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[    3.684752] rtl819xU:--->FirmwareDownloadCode()
[    3.684756] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[    3.684869] rtl819xU:DMEM code download success, CPUStatus(0x3f)
[    3.686118] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[    3.687117] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[    3.687243] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(3), rtStatus(0)
[    3.687245] rtl819xU:Firmware Download Success!!
[    6.473075] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.675927] =====>rtl8192SU_link_change 1
[   24.677053] <=====rtl8192SU_link_change 2
[   24.715296] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[   24.729049] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[   24.736187] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[   24.736195] rtl819xU:qos active process with associate response received
[   24.773919] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 40MHz bandwidth
[   24.789921] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[   24.789926] =====>rtl8192SU_link_change 1
[   24.799295] <=====rtl8192SU_link_change 2
[   24.799698] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.951010] rtl819xU:EnableHWSecurityConfig8192:, hwsec:1, pairwise_key:2, SECR_value:c
[   24.951289] rtl819xU:====>to setKey(), dev:ffff880128c90000, EntryNo:4, KeyIndex:0, KeyType:2, MacAddr00:0c:c3:79:5f:98
[   27.971306] rtl819xU:====>to setKey(), dev:ffff880128c90000, EntryNo:1, KeyIndex:1, KeyType:2, MacAddrff:ff:ff:ff:ff:ff
[   35.000005] wlan0: no IPv6 routers present
olppari@olppari-ubuntu:~$ 


```There you go.

---

### Post by chili555 on 2011-01-11
I don't see anything obviously wrong and it actually looks pretty healthy. Please detach the ethernet cable and wait a few moments for Network Manager to notice the change of state. You should see a notification that you are disconnected.

Now click the NM icon and tell us if you see your network. When you click it to connect, are you asked for the encryption key? Does it try to connect? Rerun the ping tests above if it connects.

---

### Post by OldSchool_ on 2011-01-12
> **chili555 said:**
> I believe you have an ad-hoc connection; in other words computer to computer. When you run:```
iwconfig
```Does it show Mode:Adhoc? Unless computer to computer is the way you intend to connect, I think you want Managed:```
sudo iwconfig wlan0 mode managed
```Now does Network Manager connect to the router instead?
Thanks it was adhoc so i changed to infrastructure and automatic dhcp from router and now it's properly connected to router and i can to internet. :)

---

### Post by Olppari on 2011-01-12
> **chili555 said:**
> 
Now click the NM icon and tell us if you see your network. When you click it to connect, are you asked for the encryption key? Does it try to connect? Rerun the ping tests above if it connects.

It does connect. It's already connected as I unplug the cable. I can always disconnect from my network and delete the profile of my network so it asks for the key again. I Insert the key and it gets connected but no Internet. All this with the A-link WNU adapter. Funny thing is...

I still had my old D-Link DWL-G122 wlan usb adapter. When I plug that, I can access Internet! :) So I'm guessing this whole thing with the A-link WNU adapter is a driver-issue.

Maybe it's just impossible to get this WNU adapter work perfectly with 64bit 10.4?
Oh btw I got my WNU adapter to show and connect networks this way:

> **tpheiska said:**
> Managed to get the stick to work using NDISWrapper and the Realtek drivers that I found following a [link]("http://www.realtek.com/products/productsView.aspx?Langid=1&PFid=9&Level=6&Conn=5&ProdID=176") from the Ubuntu [documentation]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek").  I used the "WinXP2K" -driver (Noob note: just extracting the .inf-file  will not work, you need to extract the whole directory and install the  driver from there).

---

### Post by Spyderkid on 2011-01-16
Here are some instructions it worked for me (theres quite alot)

Step 1 :
run this to download the package (don't use the link just run in terminal)

[FONT="Courier New"]wget  [http://samiux.volospin.com/rtl8192SU_usb_linux_v2.6.0006.20100226.zip](http://samiux.volospin.com/rtl8192SU_usb_linux_v2.6.0006.20100226.zip)[/FONT]

then...
Step 2 :

[FONT="Courier New"]sudo apt-get install unzip

unzip rtl8192SU_usb_linux_v2.6.0006.20100226.zip

cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/driver

tar -xvzf rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226.tar.gz

cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226[/FONT]

Step 3 :

[FONT="Courier New"]cd include

nano osdep_service.h[/FONT]

add "[FONT="Courier New"]#include <linux/sched.h>[/FONT]" to the file "[FONT="Courier New"]osdep_service.h[/FONT]"

the result looks like this :

[FONT="Courier New"]#ifndef __OSDEP_SERVICE_H_
#define __OSDEP_SERVICE_H_

#include <drv_conf.h>
#include <basic_types.h>
#include <linux/sched.h>
//#include <rtl871x_byteorder.h>
......[/FONT]


Step 4 :

[FONT="Courier New"]cd ..

nano Makefile[/FONT]

add "[FONT="Courier New"]nullstring :=[/FONT]" under "[FONT="Courier New"]export TOPDIR := $(PWD)[/FONT]"

locate "[FONT="Courier New"]ifeq ($(CONFIG_BUILT_IN), y)[/FONT]" and make changes to this ifeq block. The result looks like this :

[FONT="Courier New"]ifeq ($(CONFIG_BUILT_IN), y)
include $(src)/config
else
ifeq ($(TOPDIR), $(nullstring))
include config
else
include $(TOPDIR)/config
endif
endif[/FONT]

The result of the first 19 lines is as the following :

[FONT="Courier New"]EXTRA_CFLAGS += -O1 -Wno-unused-variable -Wno-unused-value -Wno-unused-label -W$
EXTRA_CFLAGS += -I$(src)/include -Wno-unused -Wno-unused-function

CONFIG_BUILT_IN = n

export TOPDIR := $(PWD)
nullstring :=

ifeq ($(CONFIG_BUILT_IN), y)
include $(src)/config
else
ifeq ($(TOPDIR), $(nullstring))
include config
else
include $(TOPDIR)/config
endif
endif

ifeq ($(CONFIG_RTL8711), y)[/FONT]

Step 5 :

[FONT="Courier New"]make clean
make
sudo make install[/FONT]

Step 6 :
[FONT="Courier New"]sudo modprobe 8712u
echo "8712u" | sudo tee -a /etc/modules[/FONT]

Every now and again when you do certain updates your dongle will stop working. to solve this run this...

[FONT="Courier New"]
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/
cd driver
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/[/FONT]
make clean
make
sudo make install
sudo modprobe 8712u
echo "8712u" | sudo tee -a /etc/modules
[/FONT]

then restart



If you want to make a script copy and paste this into a file then when it stops working you can just run this (you'll have to type [FONT="Courier New"]y[/FONT] to make it restart

[FONT="Courier New"]#!/bin/bash
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/
cd driver
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/
make clean && make 
sudo make install && sudo modprobe 8712u && echo "8712u" | sudo tee -a /etc/modules &&
echo "reboot?"

read answ
if [ "$answ" = "y" ]
then
        sudo reboot
else
        echo "ok"
fi[/FONT]

---

