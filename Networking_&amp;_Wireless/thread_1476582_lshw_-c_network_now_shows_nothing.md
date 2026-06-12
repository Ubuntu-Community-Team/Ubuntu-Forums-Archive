---
title: "lshw -c network now shows nothing"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by polardude1983 on 2010-05-08
OS: Ubuntu 9.10 Karmic Koala
Programs: Network Manager, Ndiswrapper, Device Manager, Terminal
USB Adapter: Linksys WUSB11 v2.8 Driver 4.10
Router: Linksys Wireless-G 2.4ghz

SSID: Doss
Security: Unprotected
Mac Address: Disabled

Whenever i use to type in lshw -c network it used to show details about stuff, but now when i do it it shows nothing. 

Also i did whatever was in this thread
[URL="http://www.techmetica.com/howto/how-to-install-windows-wireless-network-device-drivers-in-ubuntu/"]
how to install windows wireless drivers[/URL]

i restarted my pc and now i cant even see the wireless network! it doesnt even say enable wireless networking in the network manager!

---

### Post by polardude1983 on 2010-05-08
It seems i cant even find wlan0 now

---

### Post by Iowan on 2010-05-08
Try it as **sudo lshw -C network**

---

### Post by polardude1983 on 2010-05-09
> **Iowan said:**
> Try it as **sudo lshw -C network**

yeah done that also doesn't show anything anymore. I know i've always had trouble finding the right driver for it for windows even. Even though I have downloaded the driver for linksys 2.8 maybe its because of the driver?

---

### Post by chili555 on 2010-05-09
> [COLOR="Red"]USB[/COLOR] Adapter: Linksys WUSB11 v2.8 Driver 4.10How about letting us see:```
lsusb
```You can trim away all the lines that don't seem to relate to your wireless device, if you wish.

---

### Post by polardude1983 on 2010-05-09
```

hristoph@christoph-desktop:~$ lsusb
Bus 001 Device 009: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 005: ID 11b0:6566 ATECH FLASH TECHNOLOGY 
Bus 001 Device 004: ID 046d:0809 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 1915:2233 Linksys WUSB11 v2.8 802.11b Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
christoph@christoph-desktop:~$

```

The driver version i tried using was  DriverVer = 03/26/2004,4.10.9.430

here is a sample from the netusb.inf file

```

;    FILE:
;            netusb.inf
;
;    DESCRIPTION:
;            Linksys Wireless-B USB Network Adapter ver.2.8 inf file.
;
;*******************************************************************************************

[Version]
 Signature           = "$Chicago$"
 Compatible          = 1
 Class               = Net
 ClassGUID           = {4d36e972-e325-11ce-bfc1-08002be10318}
 Provider            = %WUSB11_VENDOR%
 CatalogFile.NT      = netrfm2k.cat
 DriverVer = 03/26/2004,4.10.9.430

[ControlFlags]
 ExcludeFromSelect   = USB\VID_066B&PID_2211
 ExcludeFromSelect   = USB\VID_066B&PID_2212
 ExcludeFromSelect   = USB\VID_066B&PID_2219
 ExcludeFromSelect   = USB\VID_077B&PID_2219
 ExcludeFromSelect   = USB\VID_09aa&PID_3642
 ExcludeFromSelect   = USB\VID_1915&PID_2233


[Manufacturer]
 %WUSB11_VENDOR_NAME% = DeviceList, NT.5.1

[DeviceList]
 %WUSB11_20.DeviceDesc%    = USBFVNETA.Ndi,    USB\VID_066B&PID_2211
 %WUSB11_25.DeviceDesc%    = PRISM_USB1,        USB\VID_066B&PID_2212
 %WUSB11_26A.DeviceDesc%   = USBNET.Ndi,        USB\VID_066B&PID_2219
 %WUSB11_26.DeviceDesc%    = USBNET.Ndi,        USB\VID_077B&PID_2219
 %WUSB11_25.DeviceDesc%    = PRISM_USB1,        USB\VID_09aa&PID_3642

 %WUSB11_28.DeviceDesc%    = USBNET28.Ndi,        USB\VID_1915&PID_2233

[DeviceList.NT.5.1] 
 %WUSB11_28.DeviceDesc%    = USBNETXP28.Ndi,       USB\VID_1915&PID_2233
 %WUSB11_26A.DeviceDesc%   = USBNETXP26.Ndi,    USB\VID_066B&PID_2219
 %WUSB11_26.DeviceDesc%    = USBNETXP26.Ndi,    USB\VID_077B&PID_2219
 %WUSB11_25.DeviceDesc%    = PRISM_USB1.NT,        USB\VID_09aa&PID_3642
 %WUSB11_25.DeviceDesc%    = PRISM_USB1.NT,        USB\VID_066B&PID_2212
 %WUSB11_20.DeviceDesc%    = USBFVNETAXP.Ndi,    USB\VID_066B&PID_2211

```

---

### Post by chili555 on 2010-05-09
I think this works with the module *at76c50x-usb*. Let's try it:```
sudo modprobe at76c50x-usb
```Was a wireless interface created?```
iwconfig
```If not, let's see what the kernel has to report:```
dmesg | grep at76
```Thanks.

---

### Post by chili555 on 2010-05-09
> The driver version i tried using was DriverVer = 03/26/2004,4.10.9.430ndiswrapper? We may have to unravel dueling drivers! Let's also see:```
ndiswrapper -l
```

---

### Post by polardude1983 on 2010-05-09
Here is all the commands you suggested for me to try. I can now see the wireless network again but it will not connect again. Do i need to blacklist the alternate driver?
```

   christoph@christoph-desktop:~$ sudo modprobe at76c50x-usb
[sudo] password for christoph: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
christoph@christoph-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

christoph@christoph-desktop:~$ dmesg | grep at76
[162435.107429] Atmel at76x USB Wireless LAN Driver 0.17 loading
[162435.107457] usb 2-1: firmware: requesting atmel_at76c505-rfmd2958.bin
[162435.154800] usb 2-1: using firmware atmel_at76c505-rfmd2958.bin (version 1.101.0-86)
[162435.218267] usbcore: registered new interface driver at76c50x-usb
christoph@christoph-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netusb : driver installed
      device (1915:2233) present (alternate driver: at76c50x_usb)
christoph@christoph-desktop:~$ 

 
  

```

---

### Post by chili555 on 2010-05-10
Let's try to work out whether ndiswrapper or at76c50x_usb is going to drive the card correctly. Reboot. Now let's see which driver is loaded or both.```
lsmod | grep -e ndis -e at76
```Are both loaded or neither or what? If none are loaded, please do:```
sudo modprobe ndiswrapper
```Now can you connect? If so we will tweak a couple of files to make sure ndiswrapper loads and at76c50x_usb does not.

If ndiswrapper does not allow you to connect, let's unload it and try the native driver:```
sudo rmmod -f ndiswrapper
sudo modprobe at76c50x_usb
```Now does it connect and surf? If so, we will tweak the same two files and make the better of the two drivers permanent.

---

### Post by polardude1983 on 2010-05-10
I got this from the first code. Which of the following 2 codes you gave me should i try now?

```

christoph@christoph-desktop:~$ lsmod | grep -e ndis -e at76
at76c50x_usb           37640  0 
mac80211              181140  1 at76c50x_usb
ndiswrapper           185532  0 
christoph@christoph-desktop:~$ 

```

---

### Post by polardude1983 on 2010-05-10
When i would try the at76 driver it would show the network but not connect.

When i do the ndiswrapper i can't even see any wireless network

---

### Post by chili555 on 2010-05-10
In your PM, it looks like *both* modules are loading. I am sure they are conflicting. Let's temporarily remove ndiswrapper and see why you can't connect. Please do:```
sudo rmmod -f ndiswrapper
iwconfig
```Is your wireless interface wlan0 or eth1 or otherwise? Next do:```
sudo iwlist wlan0 scan
```Substitute your interface if it is not wlan0. What kind of encryption does *scan* say your router has? What is your card capable of?```
sudo iwlist wlan0 auth
```

---

### Post by polardude1983 on 2010-05-12
OK so weird, but In my first post i said i had the driver my v2.8 usb adapter and the version of the driver was 4.10.9.430

Well i looked on my tv pc that originally had this usb adapter and of course its driver version is 4.10.9.430. Anyways So when I took the driver from my tv pc and installed it in the linux pc im trying to get working. Well it works somewhat.

Its weird its the same version but yet somehow grabbing the driver from my tv pc worked.

Anyways I did sudormmod -f at76c50x or what ever it is
and did sudo modprobe ndiswrapper

Well whenever i did that I would never get any wireless networks to show. Until i grabbed the driver from my tv pc.

YAY so i can see it now but still can't connect. Anyways before this new driver i would only get a 38% connectivity to the doss network. Now after this new driver i get 100% connectivity!

Anways i dont get it but it works.

Ok so i was trying with network manager and well it still won't connect. So i uninstalled network-manager and installed wicd 1.6.1 to see if it could give me any info.

Well it says cannot obtain Ip address. im guessing the same is happening with network-manager

In wicd if i try to put a certain ip address. Then it says cannot contact wireless access point.

---

### Post by polardude1983 on 2010-05-12
So basically i Believe i have a working network driver.

When i only have ndiswrapper loaded I CAN NOW see wireless networks unlike before.

But it won't connect. no internet

---

### Post by chili555 on 2010-05-12
What does this tell us?```
iwconfig
lsmod | grep -e ndis -e at76
dmesg | grep ndis
sudo iwlist wlan0 scan
```Thanks.

---

### Post by polardude1983 on 2010-05-12
Here is what i get

```

   christoph@christoph-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

christoph@christoph-desktop:~$ lsmod | grep -e ndis -e at76
ndiswrapper           185532  0 
christoph@christoph-desktop:~$ dmesg | grep ndis
[   14.014389] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.944384] ndiswrapper: driver netusb (Linksys,03/26/2004,4.10.9.430) loaded
[   15.205688] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[   15.205730] usbcore: registered new interface driver ndiswrapper
[   16.372364] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[  107.828137] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  112.829270] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  117.845285] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  122.850575] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  127.855866] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  132.861163] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  137.864249] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  142.869534] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  147.874820] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  152.876417] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  157.881710] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  162.882405] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  167.883094] ndiswrapper (iw_set_auth:1602): invalid cmd 12
christoph@christoph-desktop:~$ sudo iwlist wlan1 scan
[sudo] password for christoph: 
wlan1     No scan results

christoph@christoph-desktop:~$   


```

[IMG]http://i40.tinypic.com/10ojn6b.jpg[/IMG]

---

### Post by chili555 on 2010-05-13
> ndiswrapper (iw_set_auth:1602): invalid cmd 12I have been searching on this and, so far, have found no solution. I will keep looking and suggest you do so, as well. 

When you tried the native driver, what was your experience?

---

### Post by polardude1983 on 2010-05-13
When it was using the at76 driver it would see the unsecured wireless network called Doss, but it said only 38% (uh whats the word lol) It would try to connect but never actually do it

When I found a working diver for my usb adapter it now shows the doss network at 100% So its definitely the right driver. but though still won't connect just like the at76

---

### Post by chili555 on 2010-05-13
I understand this problem may be fixed with a later kernel version. What version are you running?```
uname -r
```If you are running 2.6.31-xx, it may be resolved by running a newer 2.6.32-x kernel. Can you try the live CD for Lucid? 

What version of ndiswrapper do you run?```
ndiswrapper -v
```

---

### Post by bkratz on 2010-05-13
@Chili--a bit of useless history

I was one of the ones that was "infected" but this back in 9.10. My final solution was to upgrade the kernel, to at that time, version 2.6.32/9 (February time frame) and built my own ndiswrapper (version 1.56) from
[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)    
The version I had problems with was 1.55. After release of 10.04 I notice that when I downloaded ndisgtk (the gui) the version of ndiswrapper offered was 1.54 again. Everything worked with the new kernel and version.

---

### Post by chili555 on 2010-05-13
> **bkratz said:**
> @Chili--a bit of useless history

I was one of the ones that was "infected" but this back in 9.10. My final solution was to upgrade the kernel, to at that time, version 2.6.32/9 (February time frame) and built my own ndiswrapper (version 1.56) from
[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)    
The version I had problems with was 1.55. After release of 10.04 I notice that when I downloaded ndisgtk (the gui) the version of ndiswrapper offered was 1.54 again. Everything worked with the new kernel and version.I think that is useful information; it will help polardude1983 realize that there is a solution close at hand.

Do you suppose 1983 is the year he was born? Gosh, I feel old!

---

### Post by bkratz on 2010-05-13
> **chili555 said:**
> I think that is useful information; it will help polardude1983 realize that there is a solution close at hand.

Do you suppose 1983 is the year he was born? Gosh, I feel old!

If that is true--I was old then!

---

### Post by polardude1983 on 2010-05-13
> **bkratz said:**
> If that is true--I was old then!

Yes it was when i was born lolz :P

---

### Post by polardude1983 on 2010-05-14
I updated my kernel from 2.6.31-20 to 2.6.32-10

```

   christoph@christoph-desktop:~$ uname -r
2.6.32-10-generic
christoph@christoph-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-10-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.32-10-generic SMP mod_unload modversions 586 
christoph@christoph-desktop:~$
 
  

```

---

### Post by polardude1983 on 2010-05-14
here is latest of lots of commands done in terminal

```

   christoph@christoph-desktop:~$ uname -r
2.6.32-10-generic
christoph@christoph-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-10-generic/misc/ndiswrapper.ko
version:        1.56
vermagic:       2.6.32-10-generic SMP mod_unload modversions 586 
christoph@christoph-desktop:~$ lsusb
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 1915:2233 Linksys WUSB11 v2.8 802.11b Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 005: ID 11b0:6566 ATECH FLASH TECHNOLOGY 
Bus 001 Device 004: ID 046d:0809 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
christoph@christoph-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

christoph@christoph-desktop:~$ lsmod | grep -e ndis -e at76
ndiswrapper           183533  0 
christoph@christoph-desktop:~$ dmesg | grep ndis
[   27.055161] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   27.986066] ndiswrapper: driver netusb (Linksys,03/26/2004,4.10.9.430) loaded
[   28.496784] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[   28.496836] usbcore: registered new interface driver ndiswrapper
[   28.510817] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   42.749244] ndiswrapper (iw_set_auth:1602): invalid cmd 12
christoph@christoph-desktop:~$ sudo iwlist wlan1 scan
[sudo] password for christoph: 
wlan1     No scan results

christoph@christoph-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netusb : driver installed
      device (1915:2233) present (alternate driver: at76c50x_usb)
christoph@christoph-desktop:~$ modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
christoph@christoph-desktop:~$ 

 
  

```

---

### Post by chili555 on 2010-05-14
I recommend we revisit the native driver. Please see: [http://ubuntuforums.org/showthread.php?t=1483506](http://ubuntuforums.org/showthread.php?t=1483506)

I think all you need is firmware.

---

### Post by polardude1983 on 2010-05-14
When i did do sudo modprobe at76c50x and I
did the sudo rmmod -f ndiswrapper

I could no longer see the wireless networks like before. I think thats because my wlan0 is now wlan1?

So now with ndiswrapper i can see the wireless networks but with the native driver i cant anymore.

---

### Post by chili555 on 2010-05-15
After you remove ndiswrapper and load at76c50x-usb, does dmesg report missing firmware?```
dmesg | grep at76
```If you need it, here it is. Please refer to the thread I linked for instructions.

---

### Post by polardude1983 on 2010-05-15
Here is what i get

```

   christoph@christoph-desktop:~$ dmesg | grep at76
[  489.031476] Atmel at76x USB Wireless LAN Driver 0.17 loading
[  489.031518] usbcore: registered new interface driver at76c50x-usb
[  607.737997] Atmel at76x USB Wireless LAN Driver 0.17 unloading
[  607.738002] usbcore: deregistering interface driver at76c50x-usb
christoph@christoph-desktop:~$
  

```

Doesn't seem to me its reporting missing firmware or is it? :p

---

### Post by chili555 on 2010-05-15
Does it create an interface, wlan0, perhaps?```
iwconfig
sudo iwlist wlan0 scan
dmesg | grep wlan
```

---

### Post by polardude1983 on 2010-05-15
here is what i get

```

   christoph@christoph-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

christoph@christoph-desktop:~$ sudo iwlist wlan0 scan
[sudo] password for christoph: 
wlan0     Interface doesn't support scanning.

christoph@christoph-desktop:~$ dmesg | grep wlan
[   28.994352] wlan0: ethernet device 00:04:ac:6c:32:70 using NDIS driver: netusb, version: 0xa0004, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1915:2233.F.conf
[   28.994370] wlan0: encryption modes supported: WEP; TKIP with WPA
[   29.005861] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   29.005895] udev: renamed network interface wlan0 to wlan1
[   29.007343] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  181.188064] ndiswrapper: device wlan1 removed
christoph@christoph-desktop:~$ 
  

```

---

### Post by chili555 on 2010-05-17
> $ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netusb : driver installed
      device (1915:2233) present ([COLOR="Red"]alternate driver: at76c50x_usb[/COLOR])I wonder if both modules are loaded at once. Let's do:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
sudo su
echo at76c50x_usb >> /etc/modprobe.d/blacklist.conf
exit
reboot
```Now is this message still present in *dmesg*?> ndiswrapper: device wlan1 removed

---

### Post by polardude1983 on 2010-05-17
here is what i get. but now when i restart my pc ndiswrapper is only listed at lsmod | grep -e ndis -e at76

Also now when i restart my pc i can no longer see any wireless network from the native driver or ndiswrapper

```

   christoph@christoph-desktop:~$ lsmod | grep -e ndis -e at76
ndiswrapper           183533  0 
christoph@christoph-desktop:~$ sudo modprobe at76c50x_usb
[sudo] password for christoph: 
WARNING: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'at76c50x_usb'
christoph@christoph-desktop:~$ sudo rmmod -f ndiswrapper
christoph@christoph-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

christoph@christoph-desktop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

christoph@christoph-desktop:~$ sudo iwlist wlan auth
wlan      no authentication information.

christoph@christoph-desktop:~$ lsmod | grep -e ndis -e at76
at76c50x_usb           33566  0 
mac80211              204859  1 at76c50x_usb
christoph@christoph-desktop:~$ dmesg | grep wlan
[   28.890806] wlan0: ethernet device 00:04:ac:6c:32:70 using NDIS driver: netusb, version: 0xa0004, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1915:2233.F.conf
[   28.890826] wlan0: encryption modes supported: WEP; TKIP with WPA
[   28.908080] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   28.908118] udev: renamed network interface wlan0 to wlan1
[   28.909736] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  715.700053] ndiswrapper: device wlan1 removed
christoph@christoph-desktop:~$ sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
mv: cannot stat `/etc/modprobe.d/ndiswrapper': No such file or directory
christoph@christoph-desktop:~$ sudo su
root@christoph-desktop:/home/christoph# echo at76c50x_usb >> /etc/modprobe.d/blacklist.conf
root@christoph-desktop:/home/christoph# exit
exit
christoph@christoph-desktop:~$ ^C
christoph@christoph-desktop:~$ lsmod | grep -e ndis -e at76
at76c50x_usb           33566  0 
mac80211              204859  1 at76c50x_usb
christoph@christoph-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

christoph@christoph-desktop:~$ sudo iwlist wlan scan
wlan      Interface doesn't support scanning.

christoph@christoph-desktop:~$ sudo iwlist wlan1 scan
wlan1     Interface doesn't support scanning.

christoph@christoph-desktop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

christoph@christoph-desktop:~$ 

 
  

```

---

### Post by chili555 on 2010-05-17
> echo at76c50x_usb >> /etc/modprobe.d/blacklist.conf
root@christoph-desktop:/home/christoph# exitI made a mistake, I am sorry. Please do:```
sudo gedit  /etc/modprobe.d/blacklist.conf

```There is a line in there: at76c50x_usb. Please change it to:```
blacklist at76c50x_usb
```Reboot and let me see:```
iwconfig
dmesg | grep -e wlan -e ndis
ndiswrapper -l
```Thanks.

I am starting to think ndiswrapper is not going to drive this device correctly. Hopefully, *dmesg* will tell us what's going wrong.

---

### Post by polardude1983 on 2010-05-19
here it is
```

christoph@christoph-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

christoph@christoph-desktop:~$ dmesg | grep -e wlan -e ndis
christoph@christoph-desktop:~$ ndiswrapper -l
netusb : driver installed
christoph@christoph-desktop:~$ 


```

---

### Post by polardude1983 on 2010-05-22
bump

---

