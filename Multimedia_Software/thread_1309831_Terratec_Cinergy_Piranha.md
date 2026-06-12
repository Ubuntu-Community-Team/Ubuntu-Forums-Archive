---
title: "Terratec Cinergy Piranha"
date: 2009-11-01
forum: Multimedia Software
---

### Post by epek on 2009-11-01
Hi,
since I upgraded to karmic with 2.6.31-14-i386, my dvb-t stick does not tune anymore.
Unfortunately the repositories siano-dev and sms1xxxx from linuxtv do not compile out of the box, since some kernel APIs got replaced in the newer kernels(i2c e.g.).

Once again a description of the symptoms:
1. dmesg with debug=3 on smsdvb, smsusb and smsmdtv 
[138183.529080] usb 4-2: new full speed USB device using uhci_hcd and address 15
[138183.684904] usb 4-2: configuration #1 chosen from 1 choice
[138183.717691] smsusb_probe: smsusb_probe 0
[138183.717696] smsusb_probe: endpoint 0 83 02 64
[138183.717699] smsusb_probe: endpoint 1 04 02 64
[138183.717702] smsusb_probe: line: 422: rom interface 0 is not used
[138183.721654] smsusb_probe: smsusb_probe 1
[138183.721673] smsusb_probe: endpoint 0 81 02 64
[138183.721676] smsusb_probe: endpoint 1 02 02 64
[138183.721680] smsusb_probe: stellar device was found.
[138183.721688] usb 4-2: firmware: requesting dvbt_bda_stellar_usb.inp
[138183.765992] smsusb1_load_firmware: sent 38144(38144) bytes, rc 0
[138183.766005] smsusb1_load_firmware: read FW dvbt_bda_stellar_usb.inp, size=38144
[138183.766098] usbcore: registered new interface driver smsusb
[138183.766108] smsusb_module_init: 
[138183.785132] usb 4-2: USB disconnect, address 15
[138186.256071] usb 4-2: new full speed USB device using uhci_hcd and address 16
[138186.418900] usb 4-2: configuration #1 chosen from 1 choice
[138186.432745] smsusb_probe: smsusb_probe 0
[138186.432754] smsusb_probe: endpoint 0 81 02 64
[138186.432761] smsusb_probe: endpoint 1 02 02 64
[138186.432918] smscore_register_device: allocated 50 buffers
[138186.432926] smscore_register_device: device c39b6e00 created
[138186.432934] smsusb_init_device: smsusb_start_streaming(...).
[138186.433158] smscore_set_device_mode: set device mode to 4
[138186.433168] smsusb1_detectmode: 4 "SMS DVBT-BDA Receiver"
[138186.433174] smscore_init_ir: IR port has not been detected 
[138186.433181] smscore_start_device: device c39b6e00 started, rc 0
[138186.433187] smsusb_init_device: device efd54000 created
[138186.433193] smsusb_probe: rc 0

Ad rom interface: does anyone know, what this error message exactly means?
Ad firmware: i´ve linked dvbt_bda_stellar_usb.inp to sms1xxx-stellar-dvbt-01.fw or even terratec´s actual driver´s SMS100x_Dvbt.inp.

I let kaffeine tune for me. Even on my High gain dvb-t antenna, which works perfectly for two TV sets, kaffeine´s indicator does not even show a channel. It stays always green.

I remember, that the older krufky-repository siano-dev, worked well on jaunty.

Now to my questions:
Does anyone else have the same problem?
Is ubuntus dvb driver from kernel.org or is it modified?
Which version is used in karmic?
Who is the maintainer - and should I cross-post to the linuxtv ML?

Thanks und regards
Erich

---

### Post by epek on 2009-11-02
Am I the only one?

---

### Post by realzippy on 2009-11-04
linux-firmware-nonfree,dvb-apps,libdvbpsi5, w-scan installed?
Talking about old or new kaffeine?

---

### Post by epek on 2009-11-05
Hi 
dvb-apps 1.1.1
w-scan: no, will try
libdvbpsi5 0.1.6-1
linux-firmware-nonfree 1.1

I even tried the manufacturer´s firmware binaries - linked against the stellar-filename according to dmesg.

The original firmware seems to fail, linux-firmware start´s up all modules - the stick seems to be available - see my dmesg from my first post. Then, tuning seems to begin, but no channels, not even a change in the signal strength appears.

In my opinion an old, unpatched driver version from linuxtv.org found it´s way back in the kernel. I remember to have tried a patched version from Mkrufky from 2.6.18 to 2.6.26(?), where scanning and tuning worked perfectly.
Unfortunately, the linuxtv-repos are quite old for the siano-based hardwares.

Does anyone know, wheter the ubuntu kernel uses it´s own patches for this or is it probably just  an old issue with linuxtv.org?

---

### Post by pa-pa-panic on 2009-12-27
Sorry for my bad english!

I have the same problem with terratec piranha.

I tried ubuntu, suse an debian, but without success.

The first time the problem appears was kernel 2.6.30-5 of debian sid.
Since this kernel-version I was not able to use dvb-t with the terratec piranha.
Since 2.6.30-5 other Kernel drivers were loaded. Up to 2.6.30-5 it was sms1xxx. Now smsusb and smsmdtv are loaded. smsdvb is not loaded, but loading with modprobe takes so success.

Firmware is original from terratec. I changed the name into the requested name "dvbt_bda_stellar_usb.inp" and dmesg showed, that it is all correct, if I load smsdvb with modprobe.
But tuning failed with kaffeine, me-tv and scan (dvb-utils).

To Build a kernel modul from v4l failed. 

I don't know weather it is a problem of the kernel driver or of the firmware.

Any help is welcome.

---

