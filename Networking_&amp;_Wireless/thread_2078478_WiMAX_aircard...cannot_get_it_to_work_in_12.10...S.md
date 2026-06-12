---
title: "WiMAX aircard...cannot get it to work in 12.10...SO FAR!!!"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by pandacookie on 2012-10-31
Hi. I posted over in the Absolute Beginners section, and no one could help. I had no idea of this section of the forums! I would have come here sooner. I hope to get help, and I hope this thread doesn't get closed because I posted in the other forum. Please don't! I am desperate for help.

Okay, so for weeks I have been trying to get my Franklin Wireless u600 USB Sprint aircard to work in 4G. I have done everything to get it to work, and nothing has helped so far. But then I was messing around with the aircard in my Windows setup in VirtualBox. I saw all the USB devices I could use there, when something caught my eye. A device called
[COLOR=Red][COLOR=Black]Beceem Communications Inc. BCSM250 WiMAX Adapter. I did an lsusb later in Ubuntu, and sure enough, this came up:

panda@panda-VPCEH34FX:~$ lsusb[/COLOR] [COLOR=Black]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5986:0510 Acer, Inc 
Bus 002 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 004: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 006: ID 198f:0220 Beceem Communications Inc. BCSM250 WiMAX Adapter
Bus 002 Device 005: ID 1fac:0151  
panda@panda-VPCEH34FX:~$ 

Nothing at all about a Franklin Wireless Modem! [/COLOR] [COLOR=Black]

The trouble now is how to get this little baby to work in Ubuntu! The system recognizes it, yet it only works as a 3G CDMA modem thus far. I want to use the WiMax portion of this modem. [/COLOR] [COLOR=Black]

I found this link: [/COLOR] [COLOR=Black][http://minhazulhaque.blogspot.com/2012/01/run-beceem-wimax-devices-on-linux-mint.html](http://minhazulhaque.blogspot.com/2012/01/run-beceem-wimax-devices-on-linux-mint.html), but the question is, how do I get this to work for me, in plain English? 

Can anyone help? I realise this may be a tall order, and no one could help so far, but I am determined to get this to work! It says in the above link it is possible. So tell me...how can we make this work in Ubuntu 12.10? 

EDIT: I have 64 bit Ubuntu, if it helps.
[/COLOR] [/COLOR]

---

### Post by pandacookie on 2012-10-31
Here's one thing I don't get. It says in the directions[ here]("http://minhazulhaque.blogspot.com/2012/01/run-beceem-wimax-devices-on-linux-mint.html") that I have to create a wimaxd.conf file, then it shows a blueprint. Do I just copy/paste what's in the blueprint? Or do I need to edit it somehow?

---

### Post by pandacookie on 2012-10-31
Trying the instructions on [http://minhazulhaque.blogspot.com/2012/01/run-beceem-wimax-devices-on-linux-mint.htm](http://minhazulhaque.blogspot.com/2012/01/run-beceem-wimax-devices-on-linux-mint.htm), stuck here;

panda@panda-VPCEH34FX:/usr/src$ tar xvfj linux-source-3.5.0-17-generic.tar.bz2
tar (child): linux-source-3.5.0-17-generic.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
panda@panda-VPCEH34FX:

I did download Linux Source, Header, OpenSSL library, and Patch. It says the directories don't exist. Man, this sucks. I guess it really doesn't work in 64 bit.

I don't know what to do. :(

---

### Post by pandacookie on 2012-11-01
Okay. Made some progress. Now I'm stuck here;

panda@panda-VPCEH34FX:~$ insmod drxvi314.ko
insmod: can't read 'drxvi314.ko': No such file or directory
panda@panda-VPCEH34FX:~$ 

Also, the computer is no longer "seeing" the modem;

panda@panda-VPCEH34FX:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5986:0510 Acer, Inc 
Bus 002 Device 008: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 009: ID 1fac:0151  
panda@panda-VPCEH34FX:~$ 

It lists "Bus 002 Device 009: ID 1fac:0151 " instead of the Beceem modem.

Is there ANYONE out there that can help??????

---

### Post by pandacookie on 2012-11-01
So far I'm going this alone...

The driver drxvi314.ko continues to be elusive. I found some documentation on the very Sprint Beceem aircard I am working on. It comes straight from Sprint themselves. I'd upload it if I weren't on a 3G connection...but anyway...it came with instructions on how to install drxvi314.ko:

[B]3.4 Instructions for Build/Execution
1. Copy the following source provided by Beceem into a directory (For example, /home/xyz).
Relx.x.x-USB/Source/Driver/Linux/usb
It has the following folder structure:
Relx.x.x 1 -USB/Source/Driver/Network/OSAL/Linux/usb
/Common
/Include
/Interface
/Makefile
2. Run make clean followed by make from the same directory.
3. For Linux 2.6 it generates driver binary drxvixxx.ko.
4. Copy the firmware binary and CFG file to /lib/firmware folder.
5. Install the driver by running insmod drxvi314.ko.
6. Run dmesg –c on the console to dump the driver debug prints.
7. After Successful download of the firmware wait for DSA ACK to appear on the console, use following
command:
$ dmesg –c
8. After loading the driver, you can see the Ethernet device in the ifconfig.[/B]

I only get as far as "make":

```
panda@panda-VPCEH34FX:~/Documents/USB_350/Source/Driver/Network/OSAL/Linux/usb$ make clean
find . -name \*.o -exec rm -rf '{}' ';'
find . -name .\*.o.cmd -exec rm -rf '{}' ';'
find . -name \*.*~ -exec rm -rf '{}' ';'
find . -name \*.*.bak -exec rm -rf '{}' ';'
rm -f *.ko *.o *.mod.* .*.cmd
rm -fr .tmp_versions
rm -rf Module.symvers
panda@panda-VPCEH34FX:~/Documents/USB_350/Source/Driver/Network/OSAL/Linux/usb$ make
make -Wall O=/lib/modules/3.5.0-17-generic/build -C /lib/modules/3.5.0-17-generic/source SUBDIRS=/home/panda/Documents/USB_350/Source/Driver/Network/OSAL/Linux/usb modules
make: *** /lib/modules/3.5.0-17-generic/source: No such file or directory.  Stop.
make: *** [default] Error 2
panda@panda-VPCEH34FX:~/Documents/USB_350/Source/Driver/Network/OSAL/Linux/usb$
```

I went to check on /lib/modules/3.5.0-17-generic/source. When I click on "source" I get this:

"The link "source" is broken. Move it to trash? 
This link cannot be used, because it's target /usr/src/linux/ doesn't exist"

I checked on that. The path DOES exist. Except that too leads to a "the link is broken" message.

The mystery deepens. If anyone has anything to chime in, feel free, please. I'm not about to give up now...

---

### Post by paperplate9 on 2013-06-06
I'm trying to get this working too.

I have a Virgin Mobile Franklin U600 3G/4G USB modem that I'm trying to get working on Ubuntu 12.10.

I have been able to get 3G net connectivity fine with a usb_modeswitch, ppp, and wvdial.

The  interesting thing about this USB stick is that it appears to have an  internal hub with 4 ports, with 1 port going to the 3G chipset (qualcomm  chipset), and another port going to the 4G chipset (Beceem). But it's  as if the 2nd port (powering the 4G chipset) is not powered by default.

Here is an lsusb showing new devices upon plugging in the USB modem:

```
Bus 002 Device 008: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 009: ID 1fac:0150
```

1fac:0150 is the mass  storage device, green LED blinks. usb_modeswitch that to a product ID of  0151 and the 3G chipset is loaded (with cdc_acm and qcaux  drivers)....green LED is now solid.

lsusb after usb_modeswitch: 
```
Bus 002 Device 008: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 009: ID 1fac:0151
```

I built the drxvi314  driver from the Sprint4GDev pack and loaded the module. However, the  problem is that the 4G chipset doesn't show up in lsusb. What I  *expect* to see if the 4G Beceem chipset has power:

```
[COLOR=Red][COLOR=Black]Bus 002 Device 008: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device XXX: ID 198f:0220 Beceem Communications Inc. BCSM250 WiMAX Adapter
Bus 002 Device 009: ID 1fac:0151
```[/COLOR][/COLOR]

So I am  guessing that the 4G chipset needs to be enabled before it will pop up  in lsusb, which drxvi314 will then be able to detect & bind to. My  guess is that the internal hub port is not powered when the USB card is  first plugged in. What I need to find out is how to enable that internal  hub port. Any ideas?

To comapre with what I see on Windows:  Plugging the card in gives me the solid green LED meaning the 3G modem  is on. But until I run the Virgin Mobile app (Broadband2Go), the Wimax  4g Beceem adapter does not show anywhere in dev mgr. I run the app, and  it's like it turns on the 4G hub port and dev mgr then shows a device of  198f:0220. I've run USBlyzer to try to reverse-engineer how it's  enabling this 2nd intenral hub port of the Terminus Technology, but I  would assume it's standard...since the dev class is a hub. I know when  the 4G chipset is enabled once the red LED lights solid. Turns blue once  it has a 4g connection.

Will try to document my progress here. But any new help & opinions are appreciated.

---

### Post by paperplate9 on 2013-06-06
Found out how to enable 4G/Wimax

1. Plug in the Franklin Wireless U600 (3G/4G USB modem)
2. usb_modeswitch 1fac:0150 to 1fac:0151 (module cdc_acm will drive this device)
3. connect to the serial port for the modem (/dev/ttyACM0)
4. run this AT command: AT+4GMODE=2
 If  you don't get your standard "OK" response back, either wrong port or  something else is wrong. Reference: AT+4GMODE=0 means 3G only,  AT+4GMODE=1 means 4G only, AT+4GMODE=2 means auto (both). It appears the  default when plugged in is 3G only.
5. After running this, both the  3G and 4G LEDs illuminated, and there was an additional dmesg for the  Beceem chipset (198f:0220).
6. In ubuntu, by default bcm_wimax  autmoaticaly got loaded once the 4G modem is enabled. This module  doesn't work with the U600, so blacklist it & insmod the drxvi314  module that you build from the Sprint4gDev pack. This module built fine  for me (Ubuntu 12.10, kernel 3.5.0-31-generic, x86_64). I pulled  macxvi350.bin and macxvi.cfg (that belongs in /lib/firmware) from the  Virgin Mobile install directory from my windows 7 box. The Sprint4gDev  pack contains these files too, but I avoided them since Virgin Mobile  had them. 

After that, my usb devs:
```
Bus 001 Device 014: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 019: ID 198f:0220 Beceem Communications Inc. BCSM250 WiMAX Adapter
Bus 001 Device 016: ID 1fac:0151

lsusb -t:

/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/5p, 12M
        |__ Port 4: Dev 14, If 0, Class=hub, Driver=hub/4p, 12M
               |__ Port 1: Dev 19, If 0, Class=vend., Driver=usbbcm, 12M
               |__ Port 2: Dev 16, If 0, Class=comm., Driver=cdc_acm, 12M
               |__ Port 2: Dev 16, If 1, Class=data, Driver=cdc_acm, 12M
               |__ Port 2: Dev 16, If 2, Class=vend., Driver=qcaux, 12M
               |__ Port 2: Dev 16, If 3, Class=vend., Driver=qcaux, 12M
               |__ Port 2: Dev 16, If 4, Class=vend., Driver=qcaux, 12M
               |__ Port 2: Dev 16, If 5, Class=vend., Driver=qcaux, 12M

```

Kernel output after insmod drxvi314:
```
[ 8993.080433] usbbcm_device_probe:subtype[1] = 0x000000ff
[ 8993.080447] 
[ 8993.080453] usbbcm_device_probe:subtype[2] = 0x00000000
[ 8993.080458] 
[ 8993.080463] usbbcm_device_probe:subtype[4] = 0x00000000
[ 8993.080468] 
[ 8993.080473] usbbcm_device_probe:subtype[8] = 0x00000000
[ 8993.080477] 
[ 8993.080483] InitAdapter:Initialising Adapter = 0xffff8800550a0000
[ 8993.080556] InitAdapter:Adapter initialised
[ 8993.080569] usbbcm_device_probe:psIntfAdapter 0xffff8800cd348000
[ 8993.080577] InterfaceAdapterInit:MODEM IS CONFIGURED TO FULL_SPEED 
[ 8993.082298] InterfaceAdapterInit:First RDM Chip ID 0xbece3301
[ 8993.082303] 
[ 8993.082309] InterfaceAdapterInit:Current number of endpoints :6 
[ 8993.082313] 
[ 8993.083607] InterfaceAdapterInit:usb dev registered
[ 8993.083804] create_worker_threads:Init Threads...
[ 8993.092682] open_firmware_file:Got file descriptor pointer of /lib/firmware/macxvi.cfg!
[ 8993.092702] bcm_parse_target_params:Config file /lib/firmware/macxvi.cfg size = 144 bytes
[ 8993.092729] beceem_parse_target_struct:AutoSyncup is Disabled
[ 8993.092737] 
[ 8993.092742] beceem_parse_target_struct:Disabling autolink up
[ 8993.092749] beceem_parse_target_struct:DDR Setting: 3
[ 8993.092753] 
[ 8993.092758] beceem_parse_target_struct:Enabling Auto Firmware Download
[ 8993.092762] 
[ 8993.092768] beceem_parse_target_struct:HarqCat5Enable   : 0x101
[ 8993.092771] 
[ 8993.092776] beceem_parse_target_struct:HarqCat5Enable   : 0x0
[ 8993.092780] 
[ 8993.092785] beceem_parse_target_struct:MIPSConfig   : 0x0
[ 8993.092788] 
[ 8993.092793] beceem_parse_target_struct:PMU MODE: 0
[ 8993.092798] beceem_parse_target_struct:bDisableFastFlashWrite:0
[ 8993.092804] beceem_parse_target_struct:uiEEPROMFlag  : 0x2
[ 8993.092808] 
[ 8993.092813] beceem_parse_target_struct:Power Save Mode: 0
[ 8993.092816] 
[ 8993.092821] doPowerAutoCorrection:PMU selected ....
[ 8993.092827] beceem_parse_target_struct:LinkUp Config   : 0x3
[ 8993.092831] 
[ 8993.097435] updateWriteProtectedRegister:Value read from Reg: 0xf000c00 is 0x1f4022
[ 8993.097435]  
[ 8993.097454] updateWriteProtectedRegister:Register 0xf000c00 restored successfully, with value 0x1f4022 !!
[ 8993.097462] 
[ 8993.097468] updateWriteProtectedRegister:Tried to restore Reg: 0xf000c00, 0 times
[ 8993.097468]  
[ 8993.097477] Bcm_kill_all_URBs:Cancelling All Submitted TX Urbs 
[ 8993.097482] 
[ 8993.097501] Bcm_kill_all_URBs:Cancelling All submitted Rx Urbs 
[ 8993.097505] 
[ 8993.097523] 
[ 8993.097523] <<<<No of tries in the tx side:0>>>
[ 8993.097529] 
[ 8993.097529] <<<<No of tries in the Rx side:0>>>
[ 8993.097536] Bcm_kill_all_URBs:TCB: used- 0 cur-0
[ 8993.097541] 
[ 8993.097545] Bcm_kill_all_URBs:RCB: used- 0 cur-0
[ 8993.097549] 
[ 8993.097554] reset_card_proc:Reseting UMA-B 
[ 8993.097558] 
[ 8993.097566] ====================>
[ 8993.174361] usb 1-4.1: reset full-speed USB device number 19 using ohci_hcd
[ 8993.276224] Do Post chip reset setting here if it is requiredddr_init:Register Count is =48
[ 8993.599870] 
[ 8993.723761] InitCardAndDownloadFirmware:CFG file downloaded
[ 8993.811692] 
[  8993.811692]  /usr/src/USB_350/Source/Driver/Network/OSAL/Linux/usb/Common/nvm.c:ReadMacAddressFromNVM:441:Buffer  dump of size 0x6 in the HEX:
[ 8993.811710] 12 34 56 78 9A BC 
[ 8993.811727] register_networkdev:Registering netdevice notifier
[ 8993.811732] 
[ 8993.811745] register_networkdev:BCM Notifier got Registered
[ 8993.812253] bcm_notify_event:Register RefCount: 7
[ 8993.812259] 
[ 8993.812412] register_networkdev:Beceem Network device name is eth2!
[ 8994.560057] ReadLEDInformationFromEEPROM:GPIO's bit map correspond to LED :0xA000
[ 8994.779868] ReadLEDInformationFromEEPROM:SPIO's bit map correspond to LED :0x0
[ 8994.783907] open_firmware_file:Got file descriptor pointer of /lib/firmware/macxvi350.bin!
[ 8994.783917] BcmFileDownload:Opened file is = /lib/firmware/macxvi350.bin and length =0x2039a8 to be downloaded at =0xbfc00000
[ 8994.783925] BcmFileDownload:download start 13f1be7e2e3
[ 8999.139253] InterfaceFileDownload:Got end of file!
[ 9003.261792] InterfaceFileReadbackFromChip:Got end of file!
[ 9003.261826] BcmFileDownload:file download done at 13f1be80408
[ 9003.261833] InitCardAndDownloadFirmware:BIN file downloaded
[ 9003.275867] device_run:Sending first interrupt URB down......
[ 9003.277961] device_run:Got the mailbox interrupt ...Registering control interface...
[ 9003.277961]  
[ 9003.278232] register_control_device_interface:Got Major No: 251
[ 9003.281846] usbbcm_device_probe:Enabling USB Auto-Suspend
[ 9003.281859] 
[ 9003.281990] usbcore: registered new interface driver usbbcm
```

Notice it downloads macxvi350.bin (firmware) at 8994 thru 9003. But...I got a new eth2 device.

The  hard part is now connecting to Sprint's wimax network. I don't get a 4g  signal with the Windows box I have so can't really try much. The good  thing is that after running wimaxd (with wimaxd.conf containing the  proper Wimax frequencies...in KHz), running wimaxc -i  and 'search' does  indicate scanning is taking place. With the bcm_wimax driver, errors  left & right. Will keep this updated for the other folks who have a  U600 on Sprint/Virgin Mobile.

---

### Post by paperplate9 on 2013-06-07
Making progress...it turns out the Virgin Mobile software (provided by Franklin Wireless) actually uses the wimaxd daemon and wimaxc client internally for connection management. By accident I happened to run the app  (BroadbandToGo.exe) as Administrator on my Windows box & saw some interesting files in the install directory (program files/virginmobile/broadbandtogo). 

- BroadbandToGo.ini
- CM_Server_Debug.log <--- the exact same file name wimaxd on linux logs to 

An image dump of broadbandtogo.exe confirmed that it's got wimaxd and wimaxc packaged in that binary since strings revealed pretty much the same wimaxd.conf config keys.

When BroadbandToGo.exe was closed, broadbandtogo.ini was updated. Had some useful config keys in there as well related to wimax:

```
_wimax_bandwidths_=5000,10000[U]
wimax_centerfreqs[/U]=2508500,2518500,2528500,2541500,2551500,2561500,2630500,2640500,2650500,2663500,2673500,2683500,2525000,2535000,2545000,2647000,2657000,2667000,2499000,2505250,2510250,2515250,2521750,2526750,2531750,2538250,2543250,2548250,2554750,2559750,2564750,2621000,2627250,2632250,2637250,2643750,2648750,2653750,2660250,2665250,2670250,2676750,2681750,2686750,2578000,2584000,2590000,2596000,2602000,2608000,2575000,2581000,2587000,2593000,2599000,2605000,2611000wimax_dration=0
wimax_report_type=2
[U]wimax_eap_method=4
wimax_ca_cert_path[/U]=C:\Program Files (x86)\VirginMobile\Broadband2Go\cert\wimaxrootcert_integration.pem[U]
wimax_client_cert_path[/U]=DeviceMemSlot1[U]
wimax_client_sub_ca1_cert_path[/U]=DeviceMemSlot3[U]
wimax_client_private_key_path[/U]=DeviceMemSlot2[U]
wimax_client_private_key_passwd=[/U]
wimax_polling_interval=50
wimax_is_radius=0
wimax_radius_ip=
wimax_radius_port=0
wimax_radius_secret=
wimax_is_always_tlslen=0
_wimax_realm_=**@vmu.mbb.sprintpcs.com**[U]
wimax_passwd_uppercase=1
wimax_devcert_used=1[/U]
wimax_userinfo_used=0
wimax_handoff_mode=2
wimax_use_engine=1
wimax_use_mru=1
```

I'm pretty sure most of these get mapped into wimaxd.conf keys. This will be very useful when trying to figure out the right wimaxd.conf values when I'm on linux again. The main things of note are underlined...these tell me the frequencies, EAP method, where I can find the CA certificate, and most likely what my username should be (I'm guessing *MACID*@vmu.mbb.sprintpcs.com).

Once I'm in an area of good coverage, this will get me closer by analyzing the CM_Server_Debug.log file (generated by Virgin Mobile's BroadbandToGo.exe). 

Stay tuned....

---

### Post by paperplate9 on 2013-06-09
I'm able to connect to a base station, not yet able to be authenticated though. Looks like wimaxd doesn't like the private keys (getting openssl errors). Error I'm getting is when auth is attempted, the EAP supplicant isn't able to load my private key ("no start line" in openssl tls code) and then spits out a lot of ASN1 error messages. Will probably build openssl myself so I can add some debug printf's to it to see what it doesn't like.

---

### Post by paperplate9 on 2013-06-10
Quick tidbit - the (Windows) Virgin Mobile connection manager app for the U600 also logs to c:\Users\[username]\BroadbandToGo.log.

---

### Post by paperplate9 on 2013-06-18
I am successfully posting this message with my U600 on Virgin Mobile/Sprint with a 4G Wimax connection!!!

The last message I posted was the "key" (no pun intended....). BroadbandToGo.log at c:\users\[username] had a line that was pretty blatant called "TLSDevicePrivateKeyPassword", which is the same key that wimaxd.conf uses. But I'll save you all the time & effort in searching through that file to find out what your PrivateKeyPassword is...in my case, the TLSDevicePrivateKeyPassword was just the U600's MAC address in caps!

So, the important stuff:
- Make sure you have the frequencies correct (CenterFrequencyMHz)..I am in the USA.
- Make sure your UserIdentity is [EMAIL="MACADDRESS@vmu.mbb.sprintpcs.com"]MACADDRESS@vmu.mbb.sprintpcs.com[/EMAIL]
- Make sure you have the CA Certificates (grab it from the Virgin Mobile BroadbandToGo install directory)
- TLSDeviceCertFileName should be DeviceMemSlot1
- TLSDeviceSubCA!CertFileName should be DeviceMemSlot3
- TLSDevicePrivateKeyPassword should be MACADDRESS
- PrivateKeyPasswordFormat should be Ascii
- FirmwareRSAPrivateKeyEncrypt should be Yes, my FirmwareRSAPrivateKeyBits was 2048
- Make sure you grab the firmware bin & cfg files (from the Virgin Mobile BroadbandToGo install directory)'

I only have one U600 device so I am assuming the above applies to all Virgin Mobile U600's in the US, but I could be wrong since I have no other data to base my conclusions on. All I know is that it works....(stability, on the other hand.....is another thing to worry about).

So this is my wimaxd.conf file (I modified this file almost a thousand times...):

```

BandwidthMHz                     5 10
CenterFrequencyMHz               2508.500 2518.500 2528.500 2541.500 2551.500 2561.500 2630.500 2640.500 2650.500 2663.500 2673.500 2683.500 2525.000 2535.000 2545.000 2647.000 2657.000 2667.000 2499.000 2505.250 2510.250 2515.250 2521.750 2526.750 2531.750 2538.250 2543.250 2548.250 2554.750 2559.750 2564.750 2621.000 2627.250 2632.250 2637.250 2643.750 2648.750 2653.750 2660.250 2665.250 2670.250 2676.750 2681.750 2686.750 2578.000 2584.000 2590.000 2596.000 2602.000 2608.000 2575.000 2581.000 2587.000 2593.000 2599.000 2605.000 2611.000
NetworkSearchTimeoutSec          60
LPSearchInShutDownEnabled        No
NetworkEntryTimeoutSec           10
NEToHighestCINRBaseStation       No
AuthEnabled                      Yes
EAPMethod                        4
ValidateServerCert               Yes
UserIdentity                     'MAC_ADDRESS_HERE_IN_CAPS_6CHARS@vmu.mbb.sprintpcs.com'
UserPassword                     ''
CACertPath                       ''
CACertFileName                   '/wimaxrootcert_integration.pem'
TLSDeviceCertFileName            'DeviceMemSlot1'
#TLSDevicePrivateKeyFileName       'DeviceMemSlot2'
TLSDeviceSubCA1CertFileName       'DeviceMemSlot3'
TLSDevicePrivateKeyPassword      'MAC_ADDRESS_HERE_IN_CAPS_6CHARS'
PrivateKeyPasswordFormat         'Ascii'
AuthenticationTimeoutSec         10
InvertMSKByteOrder               No
AlwaysIncludeTLSLength           No
EAPFragmentMaxLength             1398
EAPPollingLoopIntervalMs         50
FirmwareRSAPrivateKeyEncrypt     Yes
FirmwarePrivateKeyBits           2048
InnerNAIChange                   No
BeceemEngineFileName             '/lib/libengine_beceem.so'
AuthEthernetToRADIUS             No
RADIUSIPAddress                  '192.168.100.1'
RADIUSPort                       1812
RADIUSSecret                     ''
AutoReConnectEnabled             No
AutoReDisconnectEnabled          No
SkipNetSearch                    No
AutoReConnectIntervalSec         20
AutoReDisconnectIntervalSec      20
LinkStatusRequestPeriodSec       4
IPRefreshCommand                 'udhcpc --now --quit -i veth0 &'
NetEntryIPRefreshEnabled         No
TerminateDHCPClient              No
FirmwareFileName                 '/lib/firmware/macxvi200.bin'
ConfigFileName                   '/lib/firmware/macxvi.cfg'
CSCMDebugLogLevel                3
CSCMDebugLogFileName             '/tmp/CM_Server_Debug.log'
CSCMDebugLogFileMaxSizeMB        5
AuthLogLevel                     3
AuthLogFileName                  '/tmp/CM_Auth.log'
EnableAuthSysLogPrints           No
AuthLogFileMaxSizeMB             5
EngineLoggingEnabled             Yes
EngineLogFileName                '/tmp/CM_Engine.log'
EngineLogFileMaxSizeMB           1
RADIUSClientLogLevel             3

```

---

### Post by mredding on 2013-06-25
Thanks for updating me on the other thread ([http://ubuntuforums.org/showthread.php?t=1807782](http://ubuntuforums.org/showthread.php?t=1807782)), paperplate9. I was able to connect to 4G from my present location on Windows with a good signal strength. However, when following the directions at [http://minhazulhaque.blogspot.com/2012/01/run-beceem-wimax-devices-on-linux-mint.html](http://minhazulhaque.blogspot.com/2012/01/run-beceem-wimax-devices-on-linux-mint.html) with the information that you kindly provided, the "search" command yielded "Network search returned 0 base stations." Ideas? Thanks!

---

### Post by paperplate9 on 2013-06-26
> **mredding said:**
> Thanks for updating me on the other thread ([http://ubuntuforums.org/showthread.php?t=1807782](http://ubuntuforums.org/showthread.php?t=1807782)), paperplate9. I was able to connect to 4G from my present location on Windows with a good signal strength. However, when following the directions at [http://minhazulhaque.blogspot.com/2012/01/run-beceem-wimax-devices-on-linux-mint.html](http://minhazulhaque.blogspot.com/2012/01/run-beceem-wimax-devices-on-linux-mint.html) with the information that you kindly provided, the "search" command yielded "Network search returned 0 base stations." Ideas? Thanks!

Glad to see someone else trying this out!

How quickly did the 'search' command return? For me a 'search' takes about 5-10 seconds before it returns.

And you are using the drxvi314 driver & not bcm_wimax, correct?

Also did you obtain the firmware .bin and .cfg file from the Windows Broadband2Go install directory so that all files wimaxd.conf point to exist?

---

### Post by mredding on 2013-07-08
Ok, I've gotten a little further. This is from a different location then when I tried before, but the signal strength on Windows 7 is comparable, so I'm not sure what the difference is.
BTW, I have to insmod the full path to the kernel module; insmod drxvi314.ko doesn't seem to work. Also, although I get "OK" after AT+4GMODE=2 in minicom, the 4G light doesn't turn on (red) until I insmod. Oh, and yes, I have obtained the firmware files and placed them in appropriate locations and blacklisted the other modules. I tried it with network-manager stopped too in case that fouled things up with similar results. Anyway, here we go:

```

:~$ sudo insmod /lib/modules/3.8.0-26-generic/drxvi314.ko 
:~$ sudo wimaxd -c /etc/wimaxd.conf
********** CSCM Server Started ********** 07/08/13 19:04:00
matthew@matthew-laptop:~$ wimaxc -i
Beceem CM Server Version 1.1.7.0

> search
Network search returned 1 base station.
Idx BSID                    Pre      Freq      BW  RSSI  CINR
 0  01:01:00:00:02:19:18:75 0x3D 2535.000  10.000   -87     9

> connect 0
Connect request submitted for:
     Center frequency    2535.000 MHz
     Bandwidth           10.000 MHz
     Preamble index      0x3D
> status
Link status	 HOST INITIATED SYNC DOWN
Server up time	 0:0:46

> status
Link status	 LINKUP ACHIEVED
Connection time	 0:0:1
Server up time	 0:0:52


Base Station ID	 00:00:02:19:18:75
Preamble Index	 61
UL Cell ID	 29
RSSI Mean	 -84 dBm
CINR Mean	 10 dB
UL Center Freq	 2535000 kHz
DL Center Freq	 2535000 kHz


```

So, I should be good, right? But it's not. Appropriate part of ifconfig show no IP address:
```
:~$ ifconfig -a eth1
eth1      Link encap:Ethernet  HWaddr f4:63:49:06:XX:XX  
          BROADCAST MULTICAST  MTU:1400  Metric:1
          RX packets:625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

After a "sudo ifconfig eth1 up" it showed:

```
:~$ ifconfig -a eth1
eth1      Link encap:Ethernet  HWaddr f4:63:49:06:XX:XX  
          inet6 addr: fe80::f663:49ff:fe06:XXXX/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1400  Metric:1
          RX packets:8649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

So, some wacky IPV6 address based on my MAC address with no internet connection. Back at wimaxc I tried getting a DHCP lease:
```
> dhcp
IP refresh started
> status
Link status	 WAIT FOR NETWORK ENTRY CMD (Waiting for EAP re-authentication)
Server up time	 0:7:49
```

... and that's as far as I get. Ugh. So close!

---

### Post by paperplate9 on 2013-07-09
> **mredding said:**
> BTW, I have to insmod the full path to the kernel module; insmod drxvi314.ko doesn't seem to work. Also, although I get "OK" after AT+4GMODE=2 in minicom, the 4G light doesn't turn on (red) until I insmod.

I installed my drxvi314 module into the /lib/modules/.... tree so that all I had to do was a modprobe. But yes, an insmod does require the full path. Not sure why your LED feedback differs, but as long as you get the red LED after the insmod/modprobe, it should be ok..

> **mredding said:**
> 
```

...

> status
Link status     LINKUP ACHIEVED
Connection time     0:0:1
Server up time     0:0:52


Base Station ID     00:00:02:19:18:75
Preamble Index     61
UL Cell ID     29
RSSI Mean     -84 dBm
CINR Mean     10 dB
UL Center Freq     2535000 kHz
DL Center Freq     2535000 kHz


```

Yes! You have authenticated against the base station! At this point, I think I left out what I actually did next. I usually do an "ifconfig eth# up" right after the modprobe of the module. This will give you a generic ipv6 IP but no ipv4 IP. The next step I do is just a 'dhclient eth#' to get an ipv4 IP. I don't use the dhcp command from within wimaxc. Should probably just update wimaxd.conf to run the correct command instead of that other stuff that's in there that I have no clue what it does.

Once you are connected to a base station, the eth# device should act just like a wired ethernet device. So if you are connecting to the base station, just try 'ifconfig eth# up' and then a 'dhclient eth#' in a shell...if you get an IP, you are there! You should then see the blue LED blink when there's 4G data transfer. 

I'm not so good with automating things in a smooth process (more of a hacker) but if you connect to the base station, you *should* be able to get an inet connection. It's funny how I could get this thing to work on Ubuntu but not Windows 8 (no drivers)!

---

