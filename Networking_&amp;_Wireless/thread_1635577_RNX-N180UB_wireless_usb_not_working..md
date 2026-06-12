---
title: "RNX-N180UB wireless usb not working."
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by zingorules on 2010-12-02
I am completely new to linux. I am using it for the first time today. I am trying to get my RNX-N180UB wireless usb to work. I downloaded the linux driver from the website and have the tar.gz extracted to my desktop but have no idea where to go from there. It says something about a makefile and a clean and isnmod 8712u.ko can anyone help me?

---

### Post by uncaspi on 2010-12-02
What to do is usually located in the README.txt file in the folder you extracted  the ..tar.gz driver file.

---

### Post by zingorules on 2010-12-02
There is but it assumes that I know how to uncompress the file which is step 1. Step 2 merely says make. Thats the whole command. I have no idea how to do that.

---

### Post by zingorules on 2010-12-02
Oh gosh. I'm stupid. I was referencing it with wrong command. Okay nevermind I got it uncompressed and then used the make command which worked fine. But when I typed ./clean it gave me this:
ERROR: Removing 'r8192s_usb': Operation not permitted
ERROR: Module ieee80211_rsl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep does not exist in /proc/modules
ERROR: Module ieee80211_crypt does not exist in /proc/modules

---

### Post by uncaspi on 2010-12-02
Usually you have to type
sudo make
sudo make install
sudo make clean

Perhaps the README.txt file instruct you to run sudo make clean
first.If so, neglect the errors and proceed withe the other commands.

---

### Post by zingorules on 2010-12-03
o\Okay. So when I type sudo make it gives me back Makefile:ll: /config: No such file or directory make: *** No ruleto make target '/config'. Stop.
So I just used make and it went through and did its stuff. So then I wrote make install and it gave me back
install -p -m 644 8712u.ko /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
install: cannot create regular file '/lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/8712u.ko': Permission denied
make: *** [install] Error 1

So it tried it using
sudo make install
it came back:
Makefile:ll: /config: No such file or directory
make: *** No rule to make target '/config'. Stop.

The driver with install manual is here
[http://www.rosewill.com/products/d_1721/productDetail.htm](http://www.rosewill.com/products/d_1721/productDetail.htm)

---

### Post by uncaspi on 2010-12-03
OK I've downloaded it. You must log in as superuser to perform the steps. Type su and give the root passwd. If you can't remember it, change it. Type sudo passwd

Then issue  the commands

make
make install



After this see if the module is loaded: lsmod  | grep 8712u
If not do
sudo depmod -a
sudo modprobe 8712u

---

### Post by zingorules on 2010-12-03
Ahhh. Thank you so much. Problem fixed and my wonderful wifi is up and running! Difficult but fun.

---

### Post by zingorules on 2010-12-03
Crap wait there is a problem. After I restarted the wireless was no longer there. It worked but the problem was it still gave me the error after the ./clean command.

---

### Post by uncaspi on 2010-12-03
Try to put these commands in the /etc/rc.local file and before the exit 0 line.

depmod -a
modprobe 8712u



You don't have to run make again. After you ran make install the first time the driver module are saved in /lib/modules/$(uname -r)/kernel/drivers/net/wireless  folder.
Verify by typing sudo updatedb  and locate 8712u.ko

---

### Post by zingorules on 2010-12-03
Wait...nevermind after doing make clean and trying to figure out what happened I got it. I just updated so it changed everything and I just had to unplug usb and plug back in.

---

### Post by zingorules on 2010-12-03
Okay. Where is the /etc/rc.local file? and what is the exit 0 line?

---

### Post by uncaspi on 2010-12-03
exit 0 is usually (not always) the last line in the /etc/rc.local file
You can edit it by sudo nano /etc/rc.local

(Ctrl+o) to quit and save the file.

---

### Post by zingorules on 2010-12-03
Actually when I did the updatedb and locate it showed it in both the old generic and and new generic.

---

### Post by uncaspi on 2010-12-03
Ok fine. If it's not loaded on reboot add modprobe 8712u in the /etc/rc.local file before  exit 0 line.

sudo nano /etc/rc.local

(Ctrl+o) to save and quit editor.

---

### Post by zingorules on 2010-12-03
I add the depmod -a and the modprobe 8712u but it still won't work on startup and I actually cant get it to work now.

---

### Post by uncaspi on 2010-12-03
Then you have compile it for your new kernel doing all the steps again.
See if it helps. If not we take it from there;)

---

### Post by zingorules on 2010-12-03
I added it to the kernel but I have a problem with ifconfig wlan0 up and ifconfig wlan0 192.168.1.100 its says SIOCSIFFLAGS: Resource temporarily unavailable.

---

### Post by uncaspi on 2010-12-03
Maybe it is not named wlan0 in your new kernel. It could be eth1,ra0 or wifi0. type sudo ifconfig or sudo iwconfig or even sudo lshw -C network
and look for the logical id: of your card. If it doesn't shows up with these commands, it's a driver problem.

---

### Post by zingorules on 2010-12-03
It showed up on all. Now I have it up and running and am attempting a restart to see if it works after the restart. Okay. I lost it on restart but have it up and running again by going through the make clean and all those steps again, but it still won't go back up on its own.

---

### Post by uncaspi on 2010-12-03
> **zingorules said:**
> but it still won't go back up on its own.

what do you mean?

---

### Post by zingorules on 2010-12-03
When I restart it won't automatically connect. I am looking at the installation instructions and it tells me to disable network manager when using command-line method to connect to AP, because network manager will conflict with the method of command line.

---

### Post by uncaspi on 2010-12-03
This is a common issue here on the forum. And the only solution to it seems to be to remove network-manager completely if you want to use static ip address. There are 4 items that should be removed. Search the threads for which if you decide to remove them.

---

### Post by northd_tech on 2010-12-03
I have no experience with this USB WiFi interface, but it might be informative to post the results of the following terminal commands to see what you have "plugged" into your Linux kernel and the current configuration:

```
lsmod
lsusb
lspci 
sudo lshw -C network
ifconfig
iwconfig

```Edit:  Also, I believe that the commands in post #5 were a little out of order- if re"making," I think that should usually read:

```
sudo make clean
sudo make
sudo make install
```This should clear out the "leftover" object files and modules and start from "scratch" with all the makefiles that I have used in the past (but that will depend upon how each makefile was written).  If it doesn't like that, there will probably be error messages, and it is probably a good idea to post those here too (if you see any).

---

### Post by zingorules on 2010-12-04
lsmod

Module                  Size  Used by

8712u                 301370  0 
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  1 vfat
binfmt_misc             6599  1 
snd_hda_codec_analog    59649  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_analog,snd_hda_intel
nouveau               516971  2 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    56633  1 nouveau
snd                    49006  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         30200  1 nouveau
soundcore                880  1 snd
drm                   168054  4 nouveau,ttm,drm_kms_helper
agpgart                32011  2 ttm,drm
i2c_algo_bit            5168  1 nouveau
i2c_nforce2             5179  0 
lp                      7342  0 
ppdev                   5556  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
parport_pc             26058  1 
psmouse                59033  0 
asus_atk0110           11423  0 
k8temp                  3132  0 
parport                31492  3 lp,ppdev,parport_pc
serio_raw               4022  0 
eeprom_93cx6            1345  0 
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40172  0 
floppy                 54311  0 
firewire_ohci          21106  0 
ahci                   19013  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
pata_jmicron            1855  0 
libahci                21667  1 ahci
pata_amd                8746  0 
sata_nv                19420  2 
forcedeth              49433  0 


sudo lshw -C network

*-network               

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 08:10:74:91:97:2d

       capabilities: ethernet physical wireless

       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=unassociated



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:144 errors:0 dropped:0 overruns:0 frame:0

          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:11384 (11.3 KB)  TX bytes:11384 (11.3 KB)



wlan0     Link encap:Ethernet  HWaddr 08:10:74:91:97:2d  

          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



ifconfig


lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:144 errors:0 dropped:0 overruns:0 frame:0

          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:11384 (11.3 KB)  TX bytes:11384 (11.3 KB)



wlan0     Link encap:Ethernet  HWaddr 08:10:74:91:97:2d  

          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ifwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



eth1      no wireless extensions.



wlan0     unassociated  Nickname:"rtl_wifi"

          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  

          Retry:off   RTS thr:off   Fragment thr:off

          Encryption key:off

          Power Management:off

          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



lsusb

Bus 002 Device 003: ID 05af:0802 Jing-Mold Enterprise Co., Ltd 

Bus 002 Device 002: ID 1267:0214 Logic3 / SpectraVideo plc 

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by northd_tech on 2010-12-04
> **zingorules said:**
> 
**lsmod**
Module                  Size  Used by
[COLOR=Red]**8712u                 301370  0 **[/COLOR]
forcedeth              49433  0 

**sudo lshw -C network**
*-network               
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 08:10:74:91:97:2d
capabilities: ethernet physical wireless
configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=unassociated

wlan0     Link encap:Ethernet  HWaddr 08:10:74:91:97:2d  
inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**ifconfig**
wlan0     Link encap:Ethernet  HWaddr 08:10:74:91:97:2d  
inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


**ifwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      no wireless extensions.
wlan0     unassociated  Nickname:"rtl_wifi"

          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
Retry: off   RTS thr: off   Fragment thr: off
Encryption key: off
Power Management: off
Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lsusb**
Bus 001 Device 004: ID 0bda:8172[COLOR=Red]** Realtek Semiconductor Corp. RTL8191S**[/COLOR] WLAN Adapter

OK-according to the red part above, that USB WiFi looks to use a Realtek 8191S chipset- and I only found 2 threads searching here for that (and neither one looked too helpful).  I formatted the output to make it a little more readable (for me at least).

[http://ubuntuforums.org/showthread.php?t=1579483&highlight=realtek+8191S](http://ubuntuforums.org/showthread.php?t=1579483&highlight=realtek+8191S)

Let's compare the "verbose" version of the **lsusb** command from post #1 of another thread to what your terminal output for this command gives:

```
lsusb -v
```[http://ubuntuforums.org/showpost.php?p=9408472&postcount=1](http://ubuntuforums.org/showpost.php?p=9408472&postcount=1)

It looks to me like you have an "8712u" module loaded, and I'm guessing that is a Realtek module.  I do NOT see any of the 802.11 authentication/encryption modules that usually accompany a wireless module though- so you might be missing some modules or have the wrong ones for that USB network adapter.

From my experience working on a 64-bit Realtek 8192E wireless on a different computer, I had to email Realtek to get updated Linux drivers (several times, and I'm still working on that one...)

You probably want to look at these threads:
Realtek 8192U USB wireless
[http://www.wireless-driver.com/download/realtek/realtek-rtl8192u-wireless-linux-macos-drivers.htm](http://www.wireless-driver.com/download/realtek/realtek-rtl8192u-wireless-linux-macos-drivers.htm)

[http://driverlaptop.net/realtek-802-11abgn-wireless-lan-card-windowslinuxmac-os-drivers/](http://driverlaptop.net/realtek-802-11abgn-wireless-lan-card-windowslinuxmac-os-drivers/)

[http://www.linuxquestions.org/hcl/showproduct.php/product/4387](http://www.linuxquestions.org/hcl/showproduct.php/product/4387)

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

From my experience an Realtek 8192**E** is very different from the Realtek 8192**SE** (different driver needed, 8192E much more difficult, etc.).  You **might** want to try the 819**2U** driver here (but I did NOT see one listed for an 819**1S **specifically):

[http://download.wireless-driver.com/driver/Realtek/RTL8192U/RTL8192U_Linux_26.0003.0902.2008.zip](http://download.wireless-driver.com/driver/Realtek/RTL8192U/RTL8192U_Linux_26.0003.0902.2008.zip)

I would say that it would probably be best just to email Kidman at the Realtek website WiFi tech support:

[EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL]

Hope that helps.

Edit:  that "forcedeth" module looks like the same NVIDIA Nforce ethernet module that my laptop uses, and it looks OK.

---

### Post by zingorules on 2010-12-04
here is the lsusb -v

> Bus 002 Device 003: ID 05af:0802 Jing-Mold Enterprise Co., Ltd 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               1.10 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8 
  idVendor           0x05af Jing-Mold Enterprise Co., Ltd 
  idProduct          0x0802 
  bcdDevice            1.30 
  iManufacturer           1  
  iProduct                2 USB Keyboard 
  iSerial                 0 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           59 
    bNumInterfaces          2 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0xa0 
      (Bus Powered) 
      Remote Wakeup 
    MaxPower              100mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           1 
      bInterfaceClass         3 Human Interface Device 
      bInterfaceSubClass      1 Boot Interface Subclass 
      bInterfaceProtocol      1 Keyboard 
      iInterface              0 
        HID Device Descriptor: 
          bLength                 9 
          bDescriptorType        33 
          bcdHID               1.10 
          bCountryCode            0 Not supported 
          bNumDescriptors         1 
          bDescriptorType        34 Report 
          wDescriptorLength      62 
         Report Descriptors: 
           ** UNAVAILABLE ** 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0008  1x 8 bytes 
        bInterval              10 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        1 
      bAlternateSetting       0 
      bNumEndpoints           1 
      bInterfaceClass         3 Human Interface Device 
      bInterfaceSubClass      0 No Subclass 
      bInterfaceProtocol      0 None 
      iInterface              0 
        HID Device Descriptor: 
          bLength                 9 
          bDescriptorType        33 
          bcdHID               1.10 
          bCountryCode            0 Not supported 
          bNumDescriptors         1 
          bDescriptorType        34 Report 
          wDescriptorLength      99 
         Report Descriptors: 
           ** UNAVAILABLE ** 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x82  EP 2 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0008  1x 8 bytes 
        bInterval              10 
Device Status:     0x0000 
  (Bus Powered) 

Bus 002 Device 002: ID 1267:0214 Logic3 / SpectraVideo plc 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               1.10 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8 
  idVendor           0x1267 Logic3 / SpectraVideo plc 
  idProduct          0x0214 
  bcdDevice           51.15 
  iManufacturer           0 
  iProduct                2 PS/2+USB Mouse 
  iSerial                 0 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           34 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0xa0 
      (Bus Powered) 
      Remote Wakeup 
    MaxPower              100mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           1 
      bInterfaceClass         3 Human Interface Device 
      bInterfaceSubClass      1 Boot Interface Subclass 
      bInterfaceProtocol      2 Mouse 
      iInterface              0 
        HID Device Descriptor: 
          bLength                 9 
          bDescriptorType        33 
          bcdHID               1.11 
          bCountryCode            0 Not supported 
          bNumDescriptors         1 
          bDescriptorType        34 Report 
          wDescriptorLength      52 
         Report Descriptors: 
           ** UNAVAILABLE ** 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0008  1x 8 bytes 
        bInterval              10 
Device Status:     0x0000 
  (Bus Powered) 

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               1.10 
  bDeviceClass            9 Hub 
  bDeviceSubClass         0 Unused 
  bDeviceProtocol         0 Full speed (or root) hub 
  bMaxPacketSize0        64 
  idVendor           0x1d6b Linux Foundation 
  idProduct          0x0001 1.1 root hub 
  bcdDevice            2.06 
  iManufacturer           3 Linux 2.6.35-22-generic ohci_hcd 
  iProduct                2 OHCI Host Controller 
  iSerial                 1 0000:00:02.0 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           25 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0xe0 
      Self Powered 
      Remote Wakeup 
    MaxPower                0mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           1 
      bInterfaceClass         9 Hub 
      bInterfaceSubClass      0 Unused 
      bInterfaceProtocol      0 Full speed (or root) hub 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0002  1x 2 bytes 
        bInterval             255 
Hub Descriptor: 
  bLength              11 
  bDescriptorType      41 
  nNbrPorts            10 
  wHubCharacteristic 0x0012 
    No power switching (usb 1.0) 
    No overcurrent protection 
  bPwrOn2PwrGood        1 * 2 milli seconds 
  bHubContrCurrent      0 milli Ampere 
  DeviceRemovable    0x00 0x00 
  PortPwrCtrlMask    0xff 0xff 
 Hub Port Status: 
   Port 1: 0000.0303 lowspeed power enable connect 
   Port 2: 0000.0303 lowspeed power enable connect 
   Port 3: 0000.0100 power 
   Port 4: 0000.0101 power connect 
   Port 5: 0000.0100 power 
   Port 6: 0000.0100 power 
   Port 7: 0000.0100 power 
   Port 8: 0000.0100 power 
   Port 9: 0000.0100 power 
   Port 10: 0000.0100 power 
Device Status:     0x0003 
  Self Powered 
  Remote Wakeup Enabled 

Bus 001 Device 009: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  idVendor           0x0bda Realtek Semiconductor Corp. 
  idProduct          0x8172 RTL8191S WLAN Adapter 
  bcdDevice            2.00 
  iManufacturer           1 Manufacturer Realtek 
  iProduct                2 RTL8191S WLAN Adapter 
  iSerial                 3 00e04c000001 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           46 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0x80 
      (Bus Powered) 
    MaxPower              500mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           4 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x83  EP 3 IN 
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
        bEndpointAddress     0x06  EP 6 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x0d  EP 13 OUT 
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

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            9 Hub 
  bDeviceSubClass         0 Unused 
  bDeviceProtocol         0 Full speed (or root) hub 
  bMaxPacketSize0        64 
  idVendor           0x1d6b Linux Foundation 
  idProduct          0x0002 2.0 root hub 
  bcdDevice            2.06 
  iManufacturer           3 Linux 2.6.35-22-generic ehci_hcd 
  iProduct                2 EHCI Host Controller 
  iSerial                 1 0000:00:02.1 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           25 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0xe0 
      Self Powered 
      Remote Wakeup 
    MaxPower                0mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           1 
      bInterfaceClass         9 Hub 
      bInterfaceSubClass      0 Unused 
      bInterfaceProtocol      0 Full speed (or root) hub 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0004  1x 4 bytes 
        bInterval              12 
Hub Descriptor: 
  bLength              11 
  bDescriptorType      41 
  nNbrPorts            10 
  wHubCharacteristic 0x000a 
    No power switching (usb 1.0) 
    Per-port overcurrent protection 
  bPwrOn2PwrGood       10 * 2 milli seconds 
  bHubContrCurrent      0 milli Ampere 
  DeviceRemovable    0x00 0x00 
  PortPwrCtrlMask    0xff 0xff 
 Hub Port Status: 
   Port 1: 0000.0100 power 
   Port 2: 0000.0100 power 
   Port 3: 0000.0503 highspeed power enable connect 
   Port 4: 0000.0100 power 
   Port 5: 0000.0100 power 
   Port 6: 0000.0100 power 
   Port 7: 0000.0100 power 
   Port 8: 0000.0100 power 
   Port 9: 0000.0100 power 
   Port 10: 0000.0100 power 
Device Status:     0x0003 
  Self Powered 
  Remote Wakeup Enabled 


Also I actually found a new version of driver so I'm gonna try that. It was on one of the links you put up.

---

### Post by northd_tech on 2010-12-04
> Bus 001 Device 009: ID 0bda:**8172 Realtek** Semiconductor Corp. **RTL8191S** WLAN Adapter 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  idVendor           0x0bda Realtek Semiconductor Corp. 
  idProduct          0x8172** RTL8191S WLAN Adapter **
  bcdDevice            2.00 
  iManufacturer           1 Manufacturer **Realtek** 
  iProduct                2 **RTL8191S WLAN Adapte**r 
  iSerial                 3 00e04c000001 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           46 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0x80 
      (Bus Powered) 
    MaxPower              500mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           4 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x83  EP 3 IN 
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
        bEndpointAddress     0x06  EP 6 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x0d  EP 13 OUT 
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
  (Bus Powered) I quoted the USB WiFi portion and bolded some relevant stuff that I noticed.  It is possible that one of the Realtek** 8172** drivers might work for your **8191**S USB adapter, but unfortunately I've never worked with one of those.

Edit:  I'm not sure that "[COLOR=Red]87[/COLOR]12u" module is correct in red in post #26 above, but I'm just guessing that it looks suspicious, with me never having worked with one of those Realtek USB WiFi adapters yet- you might want to look at another **lsmod** terminal command and make sure it still reads that way.

---

### Post by zingorules on 2010-12-04
It still says 8712 u and I tried the Samiux's way but I ran into a problem with the terminal saying only on 'else' per conditional.

---

### Post by northd_tech on 2010-12-04
If you're still interested zingo, there is a 6 page thread about Realtek USB **81**72 and **87**12**u** and 81**92**_ _  over here:

[http://ubuntuforums.org/showthread.php?t=1620923](http://ubuntuforums.org/showthread.php?t=1620923)

It looks like chili555 got everyone fixed up over there across several pages.

---

### Post by zingorules on 2010-12-04
Thank you. checking it out now.

---

### Post by hotdoog on 2012-05-16
I'm running Lucid and trying to get a Patriot Wireless 11n USB going. It shows up as realtek 8191. Anyway none of the makefile worked for me and in fact it froze up my computer.

I stumbled upon [http://blog.christophersmart.com/2010/10/22/realtek-usb-wireless-on-linux-fedora/](http://blog.christophersmart.com/2010/10/22/realtek-usb-wireless-on-linux-fedora/) which is something that actually worked for me. It is instructions for Fedora but it is actually easier for ubuntu. Just skip the first two steps and start with the wget command. Hope that helps someone.

Cheers,
rusl

---

### Post by Iowan on 2012-05-16
From Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread is already marked [SOLVED].

---

