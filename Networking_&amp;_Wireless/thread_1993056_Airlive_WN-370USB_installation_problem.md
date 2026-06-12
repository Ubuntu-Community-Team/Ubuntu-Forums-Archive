---
title: "Airlive WN-370USB installation problem"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by hoolgirl69 on 2012-06-01
Hy everyone!

I won't say that I'm sorry because opening new thread :D :D :D


So, what's the problem? - the title says. I bought Airlive WN-370USB dongle and I'm having problems with installing it on my Linux OS (Ubuntu and Backtrack).

I am able to install network card with ndiswrapper but in that case "Monitor mode" can't be achived (need monitor mode for wireless data sniffing).

I think that only way to achive wireless data sniffing is to install driver through "terminal installation" (commands: make, make install, ...). 

In my case, if these commands are written nothing happens - iwconfig command does not see my network card.

Has anybody had the same problem or does anybody know how to start up my network card?

Would be grateful for any answer :)

---

### Post by chili555 on 2012-06-01
> I won't say that I'm sorry because opening new threadThere is no need to be sorry. If you or anyone needs help and a search of the forum has not yielded a solution, then I encourage you to start a new thread.> I bought Airlive WN-370USB dongleLet's see more details about it. Please open a terminal and run and post:```
lsusb
lsb_release -a
```> I am able to install network card with ndiswrapper but in that case "Monitor mode" can't be achivedLet's make sure ndiswrapper is not interfering. Please run and post:```
ndiswrapper -l
```That's a lower-case L for list, not a one.> install driver through "terminal installation" (commands: make, make install, ...). What exactly did you install? What file did you download and extract? Were there any errors?

I have no knowledge, nor do I care to gain any knowledge about data sniffing. I will be happy to help you get the wireless device to connect.

---

### Post by hoolgirl69 on 2012-06-01
```
lsusb
lsb_release -a
```
[SPOILER]user@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty[/SPOILER]


(one more command: maybe it will be useful)
```
user@ubuntu:~$ sudo lsusb -v -s 002:005
```[SPOILER]Bus 002 Device 005: ID 1b75:8171 Ovislink Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1b75 Ovislink Corp.
  idProduct          0x8171 
  bcdDevice            2.00
  iManufacturer           1 Manufacturer Realtek 
  iProduct                2 AirLive WN-370USB Adapter
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
[/SPOILER]


```
ndiswrapper -l
```
There are no loaded drivers - I unloaded them all!


> 
What exactly did you install? What file did you download and extract? Were there any errors?
[U]

[/U] Downloaded driver from:  [these page](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) 						 						Example Usage
I have successfully unpacked it, then with these commands: 
```
sudo make uninstall
sudo make
sudo make install
```
successfuly installed it with no errors.

---

### Post by chili555 on 2012-06-01
Let's see if the driver claims your device:> ID 1b75:8171 Ovislink Corp. Please run:```
modinfo rtl8192su | grep 1B75
```Is v0000[COLOR="Red"]1B75[/COLOR]d0000[COLOR="Red"]8171[/COLOR] listed? If not, then the driver you built is not written for your device. Of course, we could hack it and try to trick it to do so, but there are no guarantees.


--------------

Note to chili: HAL/rtl8192u/r8192U_core.c

---

### Post by hoolgirl69 on 2012-06-02
Unfortunately there is nothing listed except the error message :(

[code]user@Ubuntu:~$ modinfo rtl8192su | grep 1B75
ERROR: modinfo: could not find module rtl8192su[\code]

Probably it's because rtl8192su the driver wasn't installed - something else is in that installation file :S

If I enter [code]user@Ubuntu:~$ modinfo r8712u | grep 1B75[\code]
then nothing is listed

---

### Post by chili555 on 2012-06-02
> ERROR: modinfo: could not find module rtl8192suWhat did you compile, then? What did it install when you got to 'make install?'

---

### Post by hoolgirl69 on 2012-06-02
> user@Ubuntu:~/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405$ sudo make

```
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.38-8-generic/build M=/home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic' 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl8712_cmd.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/crypto/rtl871x_security.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/debug/rtl871x_debug.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/eeprom/rtl871x_eeprom.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/efuse/rtl8712_efuse.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/hal_init.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops_linux.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_halinit.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl871x_io.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl8712_io.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_query.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_set.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_linux.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_rtl.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/led/rtl8712_led.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/ieee80211.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/rtl871x_mlme.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp_ioctl.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/io_linux.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/xmit_linux.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/cmd_linux.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/mlme_linux.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/recv_linux.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/osdep_service.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/os_intfs.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/usb_intf.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/rtw_android.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/pwrctrl/rtl871x_pwrctrl.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/rtl871x_recv.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/rtl8712_recv.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/rtl871x_rf.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/rtl8712_rf.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/sta_mgt/rtl871x_sta_mgt.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/rtl871x_xmit.o 
  CC [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/rtl8712_xmit.o 
  LD [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/8712u.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/8712u.mod.o 
  LD [M]  /home/user/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/8712u.ko 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic' 
```

> user@Ubuntu:~/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405$ sudo make install

```

install -p -m 644 8712u.ko  /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-8-generic
```

---

### Post by chili555 on 2012-06-02
> install -p -m 644 [COLOR="Red"]8712u[/COLOR].ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/Please run:
```
modinfo [COLOR="Red"]8712u[/COLOR] | grep 1B75
```

Is v00001B75d00008171 listed? If not, then the driver you built is not written for your device.

---

### Post by hoolgirl69 on 2012-06-02
> **chili555 said:**
> Please run:
```
modinfo [COLOR=Red]8712u[/COLOR] | grep 1B75
```

Nothing is listed :(
](*,)

> **chili555 said:**
> If not, then the driver you built is not written for your device.

I have forgotten to say that there is no listed WN-370USB Linux driver at the: [official Airlive web page](http://www.airlive.com/support/support_3a.jsp?pdid=PD1303495445027), what possibly means that this dongle was not designed for Linux OS :S

---

### Post by chili555 on 2012-06-02
> Nothing is listedDo you want to try to hack the driver you compiled? Hey, what do we have to lose???

---

### Post by hoolgirl69 on 2012-06-03
> **chili555 said:**
> Hey, what do we have to lose???
Nothing :)


Let's do it :guitar:

---

### Post by chili555 on 2012-06-03
I understand we believe this is an 8192**SU** device from reading the Windows .inf file. Using that information, please go into the file you extracted rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.201204 05, and find os_intf > linux > usb_intf.c. Open the file with any text editor, such as gedit, kate, nano, leafpad, etc. Find the 8192SU section and add your device as shown here. CAUTION: We are *adding* to the file only; all parts before and after are untouched.```
/* RTL8192SU */
	[COLOR="Red"]/* Ovislink */
	{USB_DEVICE(0x1B75, 0x8171)},[/COLOR]
	/* Realtek */
	{USB_DEVICE(0x0BDA, 0x8174)},
	{USB_DEVICE(0x0BDA, 0x8174)},
	/* Belkin */
	{USB_DEVICE(0x050D, 0x845A)},
```Proofread carefully; spacing, brackets, etc., are crucial. Proofread again! Save and close the text editor.

Now we recompile:```
cd Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.201204\ 05
sudo su
make clean
make
make intall
modprobe -r 8712u
modprobe 8712u
exit
```Is it working?

---

### Post by hoolgirl69 on 2012-06-03
> **chili555 said:**
> Is it working?

what to say ..., what kind of message should I send ... :D :D :D

One thing is certain - You are genius!!! :D
God bless: You and Your intellect!!! :D
thank You so so much!!! :D
live at least 100 more years!!!!!! :)

):P

---

### Post by chili555 on 2012-06-03
Awesome! Glad it's working.

Whenever you compile a driver from source code, you compile it against the specific kernel you are running at the time. Whenever a newer kernel version is installed, you'll need to re-compile exactly as above. Please make a note of this and the instructions so you'll be ready.

Finally, we've explored new ground here. If you Googled your device as we were trying to get it going, you found that there was only ndiswrapper, maybe, to get this device going. Now we know the way to trick the native Linux driver to work. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

Thank you for your kind comments.

---

### Post by hoolgirl69 on 2012-06-03
Unfortunately I have to say bad news.](*,)

This method has several issues:
- you can only connect to the unsecured wireless access point (if there is no WEP or WPA). 
- in the terms of secured network, Ubuntu is trying to establish connection and it goes to the infinity (Ubuntu does not output what is going on). In the Backtrack 5 (after about 30 seconds)  it says "bad password", although the password is 100% correct.
- as well as in the case of the ndiswrapper, monitor mode can't be established. Generaly speaking there are two ways to achive Monitor mode: *iwconfig wlanX mode Monitor* which is always accompanied with this report 
```
root@bt:~# iwconfig wlan0 mode Monitor
Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Invalid argument.

```  
and *airmon-ng start wlanX*. Airmon-ng will show network adapter only if connected to a network (we can only connect to the unsecured network). Output is shown in the attached picture. If there is no established connection airmon-ng doesn't show anything - nothing is listed. Wierd ... :?


-it all comes down that ndiswrapper installaton is unhappily better choice (you can  connect to secured network) but of corse the monitor mode can't be achived :(

---

### Post by chili555 on 2012-06-03
Hmmm. Isn't wlan0 the internal device you don't wish to use? And isn't wlan2 the Airlive?> wlan0 IEEE 802.11abg ESSID:"DLZSMS"
Mode:Managed Frequency:2.437 GHz Access Point: 00:24:174:2A:A6
Bit Rate=36 Mb/s Tx-Power=15 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=38/70 Signal level=-72 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:14 Missed beacon:0

[COLOR="Red"]wlan2[/COLOR] unassociated Nickname:"[COLOR="Red"]rtl_wifi[/COLOR]"
Mode:Managed Access Point: Not-Associated Sensitivity:0/0
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by hoolgirl69 on 2012-06-04
> **chili555 said:**
> Hmmm. Isn't wlan0 the internal device you don't wish to use? And isn't wlan2 the Airlive?

Print screen which I last attached was captured in Backtrack. In Backtrack, Airlive dongle represents wlan0 interface because integrated module isn't connected. 
I used Backtrack to see how antenna behaves in that environment. In Ubuntu: wlan0 is the integrated module :)

No matter in which OS (Linux or Backtrack) command iwconfig is  executed, it is written "unassociated  Nickname:"rtl_wifi" "
In the case of integrated card there is no Nickname and there is well-marked group of network protocol standards: IEEE 802.11abg

---

### Post by chili555 on 2012-06-04
I strongly feel that the only way you're going to get NM to concentrate on the Airlive only is to blacklist the driver for the internal or at least temporarily unload it:```
sudo modprobe -r some_driver
```> used Backtrack to see how antenna behaves in that environment. In Ubuntu: wlan0 is the integrated moduleIt would be very helpful to stick to one subject at a time. I'm old and low on RAM!

---

### Post by hoolgirl69 on 2012-06-04
Ok, I'm only oriented to Ubuntu :)

```
user@Ubuntu:~$ sudo airmon-ng
[sudo] password for queen: 


Interface    Chipset        Driver

wlan0        Intel 3945ABG    iwl3945 - [phy0]

USER@Ubuntu:~$ modprobe -r iwl3945
FATAL: Error removing iwl3945 (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko): Operation not permitted
user@Ubuntu:~$ sudo modprobe -r iwl3945
user@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Sadly the same story :(
I can scan (after scanning - available networks are shown), I can try to connect to secured wireless network but without success :(

---

### Post by chili555 on 2012-06-04
What do the message logs report?```
sudo cat /var/log/syslog | grep -e etwork -e 8712 | tail -n20
```What are the symptoms? Does it ask for the password?

---

### Post by hoolgirl69 on 2012-06-04
> **chili555 said:**
> What do the message logs report?```
sudo cat /var/log/syslog | grep -e etwork -e 8712 | tail -n20
```
```
user@Ubuntu:~$ sudo cat /var/log/syslog | grep -e etwork -e 8712 | tail -n20
[sudo] password for user: 
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f8981c40>] ? free_assoc_resources+0x58/0xa0 [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f8982dd7>] ? stadel_event_callback+0x39/0x150 [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f89734c6>] ? event_handle+0xf8/0x10c [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f898d99e>] ? rxcmd_event_hdl+0x26/0x36 [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f8977bc9>] ? usb_read_port_complete+0x89/0x187 [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536] Modules linked in: hp_wmi sparse_keymap 8712u snd_hda_codec_analog tpm_infineon snd_hda_intel arc4 snd_hda_codec snd_hwdep snd_pcm snd_seq_midi rfcomm snd_rawmidi i915 joydev sco bnep binfmt_misc snd_seq_midi_event l2cap snd_seq ppdev hid_logitech ff_memless pcmcia snd_timer usbhid snd_seq_device btusb tpm_tis parport_pc hp_accel hid yenta_socket bluetooth lis3lv02d tpm pcmcia_rsrc snd tpm_bios pcmcia_core input_polldev cfg80211 drm_kms_helper psmouse drm soundcore snd_page_alloc serio_raw i2c_algo_bit video lp parport firewire_ohci firewire_core crc_itu_t tg3 [last unloaded: mac80211]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f898ff0e>] ? free_stainfo+0x149/0x180 [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f8981c40>] ? free_assoc_resources+0x58/0xa0 [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f8982dd7>] ? stadel_event_callback+0x39/0x150 [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f89734c6>] ? event_handle+0xf8/0x10c [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f898d99e>] ? rxcmd_event_hdl+0x26/0x36 [8712u]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f8977bc9>] ? usb_read_port_complete+0x89/0x187 [8712u]
Jun  4 15:56:28 Ubuntu NetworkManager[677]: <info> (wlan2): supplicant connection state:  disconnected -> scanning
Jun  4 15:56:30 Ubuntu kernel: [ 3833.955309] fwdbg:8712 not supported 5G ch: 36
Jun  4 15:56:30 Ubuntu NetworkManager[677]: <info> (wlan2): supplicant connection state:  scanning -> associating
Jun  4 15:56:30 Ubuntu kernel: [ 3833.964577] Modules linked in: hp_wmi sparse_keymap 8712u snd_hda_codec_analog tpm_infineon snd_hda_intel arc4 snd_hda_codec snd_hwdep snd_pcm snd_seq_midi rfcomm snd_rawmidi i915 joydev sco bnep binfmt_misc snd_seq_midi_event l2cap snd_seq ppdev hid_logitech ff_memless pcmcia snd_timer usbhid snd_seq_device btusb tpm_tis parport_pc hp_accel hid yenta_socket bluetooth lis3lv02d tpm pcmcia_rsrc snd tpm_bios pcmcia_core input_polldev cfg80211 drm_kms_helper psmouse drm soundcore snd_page_alloc serio_raw i2c_algo_bit video lp parport firewire_ohci firewire_core crc_itu_t tg3 [last unloaded: mac80211]
Jun  4 15:56:30 Ubuntu kernel: [ 3833.964806]  [<f8982f21>] ? surveydone_event_callback+0x33/0x135 [8712u]
Jun  4 15:56:30 Ubuntu kernel: [ 3833.964836]  [<f89734c6>] ? event_handle+0xf8/0x10c [8712u]
Jun  4 15:56:30 Ubuntu kernel: [ 3833.964866]  [<f898d99e>] ? rxcmd_event_hdl+0x26/0x36 [8712u]
Jun  4 15:56:30 Ubuntu kernel: [ 3833.964896]  [<f8977bc9>] ? usb_read_port_complete+0x89/0x187 [8712u]
user@Ubuntu:~$ 

```> **chili555 said:**
> What are the symptoms? Does it ask for the password?
Yeah, pop up window was shown several times; I had to choose type of security (WPA/WPA2) and password, but there was no established connection

---

### Post by chili555 on 2012-06-04
> [ 3832.426536]  [<f8981c40>] ? free_assoc_resources+0x58/0xa0 [[COLOR="Red"]8712u[/COLOR]]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f8982dd7>] ? stadel_event_callback+0x39/0x150 [[COLOR="Red"]8712u[/COLOR]]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f89734c6>] ? event_handle+0xf8/0x10c [[COLOR="Red"]8712u[/COLOR]]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f898d99e>] ? rxcmd_event_hdl+0x26/0x36 [[COLOR="Red"]8712u[/COLOR]]
Jun  4 15:56:28 Ubuntu kernel: [ 3832.426536]  [<f8977bc9>] ? usb_read_port_complete+0x89/0x187 [[COLOR="Red"]8712u[/COLOR]]You have a very unhappy driver right there! I'm not too sure we'll ever get it to work properly. Remember:> Of course, we could hack it and try to trick it to do so, ***but there are no guarantees.***Will it connect if you temporarily turn off encryption in the router? Is your router set for mixed mode WPA and WPA2? You'll probably have more luck with WPA2 only.

---

### Post by hoolgirl69 on 2012-06-04
Yesterday I tryed several scenarios: 
1. no secure on the AP
2. WEP secured
3. WPA secured 
4. WPA2 secured 

Dongle works only in the environment of the unsecured network :???:

Something is wrong in the implemented security methods (of course in the Linux driver). [-( --> I suppose

---

### Post by chili555 on 2012-06-04
> Something is wrong in the implemented security methods (of course in the Linux driver). --> I supposeI suppose you are exactly correct. I think we've pretty well explored how far we can go trying to trick an unsupported, experimental driver to drive this device.

Although I hate to solve a problem by throwing money at it, is there a chance you might invest $10-15 in a fully supported wireless dongle?

[http://www.linuxcompatible.org/compatdb/category/network_hardware_linux.html](http://www.linuxcompatible.org/compatdb/category/network_hardware_linux.html)

[http://ubuntuforums.org/showpost.php?p=11962969&postcount=3](http://ubuntuforums.org/showpost.php?p=11962969&postcount=3)

---

### Post by hoolgirl69 on 2012-06-04
Money does not play any role. I don't care for 20 bucks - which were "thrown in the wind". 

I'll take a huge hammer and I'll break this dongle into the 8712 pieces.

Actually, in this case I have learned a lot of things - many were learned thanks to you Chili555 :)


From the my side, this is the last thing that was bought from Airlive - third-rate company which produces third-rate products.

Bye to all!

---

