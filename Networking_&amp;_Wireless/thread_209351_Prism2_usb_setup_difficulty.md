---
title: "Prism2 usb setup difficulty"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by fredbro on 2006-07-05
Hello,

I am having difficulty getting my Prism based wireless NIC working.

I recently installed Breezy on my notebook after not being able to get Dapper working with dual boot capability.

I have installed Linux-wlan-ng and my NIC appears to associate with the Prism2_usb driver.

I have added the following to my /etc/network/interfaces file:

```
auto wlan0

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid <my essid>
wireless_enc on
wlan_ng_key0 <my wep key>
```

My output for running ifup wlan0, lsusb and lshw is as follows:

```
fred@ubuntuNB:~$ sudo ifup wlan0
Password:
ifup: interface wlan0 already configured
fred@ubuntuNB:~$ lsusb
Bus 003 Device 002: ID 1668:0408 Actiontec Electronics, Inc. [hex] Prism2.5 802.11b Adapter
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:2003 Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
fred@ubuntuNB:~$ lshw
WARNING: you should run this program as super-user.
ubuntunb
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 254MB
     *-cpu
          product: Intel(R) Pentium(R) III Mobile CPU      1133MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.1
          size: 50MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:e8000000-efffffff iomemory:e0000000-e007ffff irq:10
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:f0000000-f7ffffff iomemory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1800-181f irq:10
           *-usbhost
                product: Intel Corporation 82801CA/CAM USB (Hub #1)
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:10
           *-usbhost
                product: Intel Corporation 82801CA/CAM USB (Hub #2)
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: HP f2100a Optical USB Travel Mouse
                   vendor: Hewlett-Packard
                   physical id: 2
                   bus info: usb@2:2
                   version: 2.00
                   capabilities: usb-1.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801CA/CAM USB (Hub #3)
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:5
           *-usbhost
                product: Intel Corporation 82801CA/CAM USB (Hub #3)
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: Prism2.5 802.11b Adapter
                   vendor: Actiontec Electronics, Inc. [hex]
                   physical id: 1
                   bus info: usb@3:1
                   version: 1.32
                   serial: 111111111111
                   capabilities: usb-1.10
                   configuration: driver=prism2_usb maxpower=500mA speed=12.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: ES1988 Allegro-1
                vendor: ESS Technology
                physical id: 3
                bus info: pci@01:03.0
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Maestro3
                resources: ioport:2000-20ff irq:5
           *-communication UNCLAIMED
                description: Communication controller
                product: ES2838/2839 SuperLink Modem
                vendor: ESS Technology
                physical id: 4
                bus info: pci@01:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: ioport:2440-244f irq:10
           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@01:05.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:10000000-10000fff irq:10
           *-network DISABLED
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@01:08.0
                logical name: eth0
                version: 42
                serial: 00:c0:9f:13:57:ec
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 multicast=yes
                resources: iomemory:e0200000-e0200fff ioport:2400-243f irq:10
           *-ide
                description: IDE interface
                product: SiI 0649 Ultra ATA/100 PCI to ATA Host Controller
                vendor: Silicon Image, Inc.
                physical id: c
                bus info: pci@01:0c.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list
                configuration: driver=CMD64x_IDE
                resources: ioport:1228-122f ioport:1220-1223 ioport:1248-124f ioport:1240-1243 ioport:2450-245f irq:15
              *-ide:0
                   description: IDE Channel 0
                   physical id: 1
                   bus info: ide@1
                   logical name: ide1
                   clock: 33MHz
                 *-cdrom
                      product: QSI DVD-ROM SDR-083
                      physical id: 0
                      bus info: ide@1.0
                      logical name: /dev/hdc
                      capabilities: packet
              *-ide:1
                   description: IDE Channel 1
                   physical id: 2
                   bus info: ide@2
                   logical name: ide2
                   clock: 33MHz
                 *-cdrom
                      product: UJDA340
                      physical id: 0
                      bus info: ide@2.0
                      logical name: /dev/hde
                      capabilities: packet
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1860-186f iomemory:e0100000-e01003ff irq:5
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: IC25N030ATCS04-0
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 27GB
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:1880-189f irq:10
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
fred@ubuntuNB:~$
```

Any assistance will be very much appreciated, fredbro

---

### Post by Dr. Nick on 2006-07-05
Been awhile since Ive messed with my prism2 card, but what are you having trouble with? just connecting?

The gui's to configure this are useless, I belive most has to be done via command line and editing text files.

If you havent seen thses commands before they may help you connect
First enables the card, 2nd tries to connect to ap, 3rd tries to get a ip

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="myssid" authtype=sharedkey

sudo dhclient wlan0

I had a fun time getting mine going at first, just look here
[http://ubuntuforums.org/showthread.php?t=72362](http://ubuntuforums.org/showthread.php?t=72362)

If I recall you must also set the wep in  /etc/wlan/wlancfg-DEFAULT(or your ssid)

One of my last post covers how I set mine up, Its different now though since thats quite old.


If that doesnt help then post a but more specific problem/circumstance and Ill see what I can do.

---

### Post by fredbro on 2006-07-05
Thanks for the help Dr. Nick,

I really appreciate forum responders like yourself!

My problem is that my computer does not seem to see or connect to my wireless network.

Below is the output after following your previous instructions.

When I do: sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable, I get:

fred@ubuntuNB:~$ sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
Password:
message=lnxreq_ifstate
  ifstate=enable
  resultcode=implementation_failure

When I do: "sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=newnomo authtype=sharedkey", I get:

fred@ubuntuNB:~$ sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=newnomo authtype=shared key
authtype="argument_item_data_is_invalid"
message=lnxreq_autojoin
  ssid='newnomo'
  authtype=argument_item_data_is_invalid
  resultcode=no_value

When I do: "sudo dhclient wlan0", I get:

red@ubuntuNB:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I looked at my wlancfg-DEFAULT file but did not understand how to insert my WEP.  
Are there some other commands for me to use to check my wlan0 setup and function?

I wasn't sure how to put these outputs in boxes like most of the threads, so I could use a tip for this also.

Thank you, fredbro

---

### Post by Dr. Nick on 2006-07-05
To get the boxes around the output use code tags. On the reply hit "go advanced" then select the text and hit the # button on the toolbar, Or just put the text inbetween code tags ```
[CODE]
```[/codE]

```
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
``` 
should not give that output. It needs to say sucess instead of implementation_failure. Try to run it 2 times and see if it says sucess.

Ill post on the wep instructions in a sec


EDIT with wep instructions

I am going to post part of my wlancfg-Default file and explain it. I think this is correct, I havent used my wireless card in a long time, but i think this worked last i tried. Just put the wep key into the 2nd line in red and make sure the 1st red line number matches (0,1,2,3). I found it easier to disable wep until I got it connected. If you want to disable wep in your router you need to edit the file below aswell and set exclude unencrypted to false like I have done. If you dont I dont think it will let you connect. If you have no wep then replace sharedkey with **opensystem** in the config file, and in the line to connect to ssid that you run from a terminal
```

# [Dis/En]able WEP.  Settings only matter if PrivacyInvoked is true
lnxreq_hostWEPEncrypt=false     # true|false
lnxreq_hostWEPDecrypt=false     # true|false
dot11PrivacyInvoked=false    # true|false
[COLOR=Red]dot11WEPDefaultKeyID=0  [/COLOR]      # 0|1|2|3
dot11ExcludeUnencrypted=false    # true|false, in AP this means WEP is required.

# If PRIV_GENSTR is not empty, use PRIV_GENTSTR to generate 
#  keys (just a convenience)
# add-ons/ in the tarball contains other key generators.
PRIV_GENERATOR=/sbin/nwepgen    # nwepgen, Neesus compatible
PRIV_KEY128=false        # keylength to generate
PRIV_GENSTR=""

# or set them explicitly.  Set genstr or keys, not both.
[COLOR=Red]dot11WEPDefaultKey0=Dx:Fx:2x:BC:Bx:CB:x9:0x:E6:Dx:14:x5:x1[/COLOR]        # format: xx:xx:xx:xx:xx   or
dot11WEPDefaultKey1=        #         xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
dot11WEPDefaultKey2=        #  e.g.   01:20:03:40:05   or
dot11WEPDefaultKey3=        #         01:02:03:04:05:06:07:08:09:0a:0b:0c:0d
```

---

### Post by fredbro on 2006-07-08
Dr. Nick,

I don't seem to be able to edit my wlancfg-DEFAULT files using either sudo or the GUI.  I don't understand why because I have been able to edit other files.  

When I use the GUI I get a window with options to: run in terminal, display, or run.

When I try sudo gedit, it opens a new file in my home folder with the name wlancfg-DEFAULT.

Would you be able to help me with this?

Also, I have been trying some tips from other posts but have not been able to get my wireless working yet.

Thanks for the time and assistance, fredbro

---

### Post by Dr. Nick on 2006-07-08
this should do 

[B]sudo gedit /etc/wlan/wlancfg-DEFAULT

[/B]when you launch gedit from a terminal you need to specify the full path to the file.

I have gotten ndiswrapper to work on my primsm2 card also, so if you cant get the native driver to work that is a option

---

### Post by fredbro on 2006-07-08
Dr. Nick,

I will try to edit again with the full file path.

Will I need a driver inf and sys files to use Ndiswrapper.  I've searched all over for these files but can only find a Windows package that does not show these files separately.

Thanks for the quick reply, fredbro

---

### Post by Dr. Nick on 2006-07-08
yes you need a .inf and .sys file. 

Most drivers are packaged in a .exe file and must be extrated. I happen to have my cd so I could avoid this step, What make/model is your card. It may work with the drivers I have

---

### Post by fredbro on 2006-07-08
Dr. Nick,

I have an Actiontec Prism wireless lan USB card.  It came with my HP Omnibook 510 notebook computer.  Windows identifies the driver as, Actiontec, 10/22/01, version 1.7.29.0.  

My network card info from lshw is shown below:  

*-usb
                   description: Generic USB device
                   product: Prism2.5 802.11b Adapter
                   vendor: Actiontec Electronics, Inc. [hex]
                   physical id: 1
                   bus info: usb@3:1
                   version: 1.32
                   serial: 111111111111
                   capabilities: usb-1.10
                   configuration: driver=prism2_usb maxpower=500mA speed=12.0MB/s

If I try to use Ndiswrapper, will I have to take some steps to remove Linux-wlan-ng things?

Thanks again, fredbro

---

### Post by az on 2006-07-08
> **fredbro said:**
> 


wlan_ng_key0 <my wep key>


is that 1a2b3c4e or 1a:2b:3c:4e:5f

Because that format is required.


> **fredbro said:**
> 
If I try to use Ndiswrapper, will I have to take some steps to remove Linux-wlan-ng things?

Thanks again, fredbro

You would have to blacklist prism2_usb.  You add the line

blacklist prism2_usb
to  /etc/modprobe.d/blacklist

and reboot.

---

### Post by fredbro on 2006-07-08
Hello Azz,

Thank you for your reply to my post.  I feel like I know you somewhat from all of your other posts that I have read.

My wep is of the form 389yyyyy62 where the y's are lower case letters.  I presently have been formatting this as: 38:9y:yy:yy:62 but was previously using other incorrect formats, so I think I am doing this right.

Some recent output when I run iwconfig and iwconfig wlan0 is as follows:

```

```fred@ubuntuNB:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:13:57:EC
          inet6 addr: fe80::2c0:9fff:fe13:57ec/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:507549 (495.6 KiB)  TX bytes:507549 (495.6 KiB)

fred@ubuntuNB:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:192.168.15.102  Bcast:192.168.15.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)```

```

From the ifconfig wlan0 output it appears that my system does not have a hardware address for my NIC. 

Please let me know if there are other tests or commands that I can use to provide insight to my connection problem. 

Thanks alot for the help, fredbro

---

