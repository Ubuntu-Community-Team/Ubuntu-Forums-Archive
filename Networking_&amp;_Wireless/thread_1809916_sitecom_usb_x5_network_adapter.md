---
title: "sitecom usb x5 network adapter"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by Hetepeperfan on 2011-07-22
hello,

I'm looking for support on installing a Sitecom usb network adapter on my ubuntu 10.04 LTS x86 32 bits system.

the cdrom of the manufactor provides a rt2870.sys and .inf file. First I tried to load these drivers using ndiswrapper but I had no succes with that. Now Im trying to use the ralink linux driver which i downloaded from their website ( 2010_0709_RT2870_Linux_STA_v2.4.0.1) . 

I was able to build the source and load rt2870sta.ko into the kernel using
```
sudo lsmod ./rt2870sta.ko
```

then the last line from
```
dmesg
``` tells me: [ 254.284916] usbcore: registered new interface driver rt2870

then i hoped that ifconfig or iwconfig provides me with the new ra0 device with wireless extentions however they only show the lo and eth0 device, somehow ra0 is not created for me

so from another thread in this forum i learned I might be necessary to modify /etc/network/interfaces
There I added two lines:
iface ra0 inet dhcp
auro ra0

however even after rebooting no luck and no reported new network device

would anyone please help me?

kind regards, 

hetepeperfan

---

### Post by chili555 on 2011-07-22
That's odd. Let's have a look at:```
lsusb
```Thanks.

---

### Post by Hetepeperfan on 2011-07-22
Hi chili555 thanks for your reply

```
lsusb
```

gives :
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0718:0638 Imation Corp. 
Bus 001 Device 003: ID 0df6:0062 Sitecom Europe B.V. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and for extra info
```
sudo lsusb -v -s 1:3
```gives:

Bus 001 Device 003: ID 0df6:0062 Sitecom Europe B.V. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0df6 Sitecom Europe B.V.
  idProduct          0x0062 
  bcdDevice            1.01
  iManufacturer           1 Ralink
  iProduct                2 802.11 n WLAN
  iSerial                 3 1.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 1.0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

---

### Post by chili555 on 2011-07-22
Well! We have a little adventure ahead of us! I suspect the chipset is relatively new and so a Linux driver hasn't yet been worked out. I suggest that's what you and I are about to do! 

I will assume, based on your forum signature, that the cowards way out, that is, using the Windows XP drivers and ndiswrapper is out of the question.

Here is what I've found so far: [http://www.wikidevi.com/wiki/Sitecom_WLA-5000](http://www.wikidevi.com/wiki/Sitecom_WLA-5000)> Interface: USB

ID: [COLOR="Red"]0df6:0062[/COLOR]

FCC ID: none available

Primary chip: Ralink [COLOR="Red"]RT3572[/COLOR]
I have compiled rt3572sta from Ralink's source code and it's not very hard. At present, it doesn't claim your device by its usb.id, but that can be fixed by modifying rtusb_dev_id.c.

If you are ready to proceed, please get a wired ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```Then go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Download the file called RT3572USB to your desktop. I will be working out the details on how to add your usb.id and compile the driver and be back in 30 minutes or so.

---

### Post by Hetepeperfan on 2011-07-22
Hi chili555,

according apt my build-essentials and linux-headers-generic are up to date, although i must confess that I haven't been able to run apt-get update since begin July, is that a problem? I was able to build the rt2780sta.ko driver, which apparently is not the proper one (while the XP seems to it use see my first post in this thread). I downloaded the rt3572 and exstracted it to ~/mysrc/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO.

I love the heat, so i'd love to build the linuxdriver!

I must leave in a few minutes but i will definitely be back on this issue later.

cheers,

hetepeperfan

---

### Post by chili555 on 2011-07-22
On your desktop, right-click the tar.bz2 file and select Extract Here. Another compressed file will appear, without an extension. Right-click it and rename it RT3572. Right-click RT3572 and select Extract Here. Open the extracted file and drill down to os > linux and open config.mk with a text editor. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now go to common and open rtusb_dev_id.c with a text editor. Make an addition as shown here:

```
#ifdef RT35xx
	{USB_DEVICE(0x148F,0x3572)}, /* Ralink 3572 */
	{USB_DEVICE(0x1740,0x9801)}, /* EnGenius 3572 */
	{USB_DEVICE(0x0DF6,0x0041)}, /* Sitecom 3572 */
        [COLOR="Red"]{USB_DEVICE(0x0DF6,0x0062)}, /* Sitecom 3572 */[/COLOR]
	{USB_DEVICE(0x0DF6,0x0042)},
	{USB_DEVICE(0x04BB,0x0944)}, /* I-O DATA 3572 */
	{USB_DEVICE(0x1690,0x0740)}, /* 3572 */
	{USB_DEVICE(0x1690,0x0744)}, /* 3572 */
	{USB_DEVICE(0x5A57,0x0284)}, /* Zinwell 3572 */
	{USB_DEVICE(0x167B,0x4001)}, /* 3572 */
	{USB_DEVICE(0x0930,0x0A07)}, /* TOSHIBA */
#endif /* RT35xx */

```
All before and after this one line is unchanged. Brackets, spaces, etc. *must be exact*. Proofread carefully, twice, save and close the text editor.

Now open a terminal and do:

```
cd Desktop/2011
```

Press Tab and the remainder of the file name will fill in automagically. Press Enter. Now do:

```
sudo su
make
make install
modprobe rt3572sta
exit
```

You may encounter warnings, but no errors. If you get an error or don't understand a step, stop and post back and I'll be glad to help.

---

### Post by Hetepeperfan on 2011-07-24
Hi chili,

Thank you so much for your help sofar if I now type 

```

hetepeperfan@mja-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```However I need to set essid to "the name of my router"
Some how the gnome network manager doesn't help me.
Thus although the device is now listed I'm not able to use it
do you have any suggestions?

best,

hetepeperfan

---

### Post by chili555 on 2011-07-24
If Network Manager is not doing the job for you, I'd double-check this step:> Open the extracted file and drill down to os > linux and open config.mk with a text editor. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.Please check. If it hasn't been done or there is a mistake, you will need to rebuild the driver:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt3572sta
exit
```

---

### Post by Hetepeperfan on 2011-07-24
Hi chili555

I double checked those values in config.mk file and they were set correctly to y before i run make.
I've always had troubles with network manager on my machine. Although in my previous house were i use eth0 i also needed to configure eth0 with ifconfig instead of network manager.
I've got this feeling I have been able to screw up gnome network connections manager on my machine.

have got any ideas how to test this?

best,

hetepeperfan

---

### Post by chili555 on 2011-07-24
Is Network Manager actually running?```
ps aux | grep -i network
```Any interesting messages in system logs?```
sudo cat /var/log/syslog | grep etwork | tail -n20
```You could try manual methods:```
sudo iwconfig ra0 essid <your_router>
sudo dhclient ra0
```Do you have any encryption? WPA, WEP or Klingon?

---

### Post by Hetepeperfan on 2011-07-24
Hi chili,

I believe we have a wpa encryption it's a 10 hexadecimal number code

```
hetepeperfan@mja-desktop:~$ ps aux | grep -i network
root       719  0.0  0.9   9640  4776 ?        Ss   16:58   0:00 NetworkManager
maarten   2716  0.0  0.1   3328   856 pts/0    S+   18:19   0:00 grep -i network
hetepeperfan@mja-desktop:~$ sudo cat /var/log/syslog | grep network | tail -n20
[sudo] password for maarten: 
hetepeperfan@mja-desktop:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  (ra0): now managed
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  (ra0): preparing device.
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  (ra0): deactivating device (reason: 2).
Jul 24 16:58:05 mja-desktop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  (eth0): carrier is OFF
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000')
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 24 16:58:05 mja-desktop NetworkManager: <info>  modem-manager is now available
Jul 24 16:58:05 mja-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 24 16:58:06 mja-desktop NetworkManager: <info>  Trying to start the supplicant...
Jul 24 16:58:06 mja-desktop NetworkManager: <info>  (ra0): supplicant manager state:  down -> idle
Jul 24 16:58:06 mja-desktop NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 0)
Jul 24 16:58:06 mja-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 24 16:58:06 mja-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 24 16:58:06 mja-desktop NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
Jul 24 17:00:24 mja-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 24 18:00:15 mja-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

hetepeperfan@mja-desktop:~$ sudo iwconfig  ra0 essid Thomson055537

hetepeperfan@mja-desktop:~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ra0/00:0c:f6:b3:38:15
Sending on   LPF/ra0/00:0c:f6:b3:38:15
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
hetepeperfan@mja-desktop:~$ e output.txt

```As far as i can see the network manager is running.
the sudo iwconfig ra0 essid "router" is not changing anything if I now enter ra0 it shows the essid unchanged.

---

### Post by chili555 on 2011-07-24
> he sudo iwconfig ra0 essid "router" is not changing anything if I now enter ra0 it shows the essid unchanged.I believe, with Network Manager in control, that the ESSID won't appear until you are actually connected. 

Network Manager looks pretty solid to me. It looks like you have a wired ethernet connection. NM is designed to disallow a wireless connection if you have wired. Please detach the cable and try to connect. Do you see your network in NM? Does it try?

---

### Post by Hetepeperfan on 2011-07-24
> **chili555 said:**
> I believe, with Network Manager in control, that the ESSID won't appear until you are actually connected. 

Network Manager looks pretty solid to me. It looks like you have a wired ethernet connection. NM is designed to disallow a wireless connection if you have wired. Please detach the cable and try to connect. Do you see your network in NM? Does it try?
Hi chili555

I don't have a cable attached.

somewhere during boot I run ```
ifconfig eth0 inet 192.168.1.123
``` (in a start up script), can this cause the trouble? However, since I moved out of my old home i don't have access to a cable anymore, therefore i bougth this sitecom adapter.

best,

Hetepeperfan

---

### Post by chili555 on 2011-07-24
> somewhere during boot I run
Code:

ifconfig eth0 inet 192.168.1.123

(in a start up script), can this cause the trouble?It's very hard to say for sure, but I'd remove it just to be sure. Is it in /etc/rc.local?

---

### Post by Hetepeperfan on 2011-07-24
Hi chili555,

It is a script in /etc/init.d/ . and it was registered by ```
sudo update-rc connectme defaults
```.

It is now removed by ```
$sudo update-rc -f connectme defaults
```.

Additionally I have been able to cable wire me to the router. Finally Internet runs, but not via the gnome network connections editor. (I think this was also the reason why I invented this startup script in the first place) .  In the gnome network manager i added a line for a dhcp connection to the router. that leads to no results. However, if i run #```
sudo ifconfig eth0 inet
#dhclient eth0
```the wired connection will run. Therefore, i really think there is something wrong with my network connection manager provided by gnome, I probably screwed it up myself but don't know how to get it running again.

But things do run when using the command line interface to them.

any ideas left?

best hetepeperfan

---

### Post by chili555 on 2011-07-24
You could certainly go into Synaptic and remove it and mark for complete removal including configuration files. Then reinstall it, or install Wicd. Make sure you have a wired connection first. If it stops, you can probably restart the connection with:```
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

### Post by Hetepeperfan on 2011-07-25
Heey chili555,

Thanks for all your help!! I can now use this device to connect to the world. On top of that i also learned how to use quite a bit of commandline utilities on my machine to connect a network card to the web. Wicd seems to work better for me; even reinstalling the gnome equivalent didn't help. 

cheers,

Maarten

---

### Post by chili555 on 2011-07-25
That's awesome. Great work! Would you please use thread tools at the top to Mark Solved.

---

