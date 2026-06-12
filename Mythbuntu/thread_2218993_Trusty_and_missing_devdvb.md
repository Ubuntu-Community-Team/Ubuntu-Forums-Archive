---
title: "Trusty and missing /dev/dvb"
date: 2014-04-22
forum: Mythbuntu
---

### Post by jensk on 2014-04-22
I am testing upgrade to Trusty before upgrading the famiuly setup.
I have installed Trusty on a desktop for this. When i connect my Anysee E30 Combo Plus i can se drivers loading with lsmod but i get no creation  af /dev/dvb dir. Sp w-scan doesn't se any dvb devices to scan for mux'es on.

My lsmod shows:
```
Module                  Size  Used by
dvb_usb_anysee         23982  0 
dvb_usb_v2             36018  1 dvb_usb_anysee
dvb_core              121659  2 dvb_usb_v2,dvb_usb_anysee
rc_core                28124  2 dvb_usb_v2,dvb_usb_anysee
ctr                    13049  1 
ccm                    17773  1 
rfcomm                 69160  8 
bnep                   19624  2 
binfmt_misc            17468  1 
snd_hda_codec_conexant    57441  1 
cdc_ether              14351  0 
usbnet                 43918  1 cdc_ether
mii                    13934  1 usbnet
cdc_wdm                19053  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
cdc_acm                28803  0 
videodev              134688  2 uvcvideo,videobuf2_core
arc4                   12608  2 
iwldvm                232285  0 
coretemp               13435  0 
kvm_intel             143060  0 
mac80211              626584  1 iwldvm
kvm                   451519  1 kvm_intel
thinkpad_acpi          80817  0 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
psmouse               101945  0 
serio_raw              13462  0 
iwlwifi               169932  1 iwldvm
snd_hda_intel          52355  3 
btusb                  32412  0 
bluetooth             395423  22 bnep,btusb,rfcomm
snd_hda_codec         192906  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
i915                  783354  3 
lpc_ich                21080  0 
mei_me                 18499  0 
drm_kms_helper         52758  1 i915
cfg80211              490477  3 iwlwifi,mac80211,iwldvm
drm                   302631  4 i915,drm_kms_helper
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mei                    82274  1 mei_me
wmi                    19177  0 
i2c_algo_bit           13413  1 i915
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  17 snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
parport_pc             32701  0 
mac_hid                13205  0 
video                  19421  1 i915
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ahci                   25819  2 
libahci                32168  1 ahci
e1000e                254433  0 
ptp                    18933  1 e1000e
pps_core               19382  1 ptp

```
I have tried to blacklist all Anysee related modules i /etc/modprobe.d/blacklist.conf like:
```
blacklist tda10023
blacklist zl10353
blacklist dvb_usb_anysee
```
and the load:
```
modprobe zl10353 
```
and 
```
modprobe dvb_usb_anysee adapter_nr=0 delsys=1
```
With no luck - still no dvb adapters i /dev.

How do i get the /dev/dvb adapters to be created?

---

### Post by blm-ubunet on 2014-04-22
output of dmesg ?
linux firmware packages ?

Why the blacklisting ? was this so you could control the module loading time/order ?

---

### Post by jensk on 2014-04-23
The blacklisting was because i couldn't get it to work first. Then I read about Anysee driver defaulting to the tda10023 and DVB-C and not letting the zl10353 and DVB-T part work. This was for the original 12.04 lucid kernels and i don't know if this issue accessing the DVB-T part still exists in the 14.04 kernels.

I have installed linux-firmware and linux-firmware-nonfree

I will post dmesg when i get homefrom work today

---

### Post by jensk on 2014-04-23
This is the Trusty dmesg:
> [ 1924.148315] usb 2-2: new high-speed USB device number 3 using ehci-pci
[ 1925.264163] usb 2-2: device not accepting address 3, error -71
[ 1925.336794] Monitor-Mwait will be used to enter C-3 state
[ 1925.584116] usb 6-2: new full-speed USB device number 2 using uhci_hcd
[ 1926.811163] usb 6-2: not running at top speed; connect to a high speed hub
[ 1926.829162] usb 6-2: New USB device found, idVendor=1c73, idProduct=861f
[ 1926.829170] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1926.829177] usb 6-2: Product: anysee-FA(LP)
[ 1926.829183] usb 6-2: Manufacturer: AMT.CO.KR
[ 1926.870500] usb 6-2: dvb_usb_v2: found a 'Anysee' in warm state
[ 1926.877156] usb 6-2: dvb_usb_anysee: firmware version 1.2 hardware id 15
[ 1926.877243] usb 6-2: dvb_usb_v2: this USB2.0 device cannot be run on a USB1.1 port (it lacks a hardware PID filter)
[ 1926.877312] usbcore: registered new interface driver dvb_usb_anysee

and Trusty lsusb
> $ lsusb
Bus 002 Device 002: ID 0bdb:1900 Ericsson Business Mobile Networks BV F3507g Mobile Broadband Module
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 17ef:4807 Lenovo UVC Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2145 Broadcom Corp. BCM2045B (BDC-2.1) [Bluetooth Controller]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 003 Device 003: ID 1c73:861f AMT Anysee E30 USB 2.0 DVB-T Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


If i install it on my Debian Squeeze server running 3.2 backports kernel i get this dmesg:
> [156580.856250] usb 2-3: device not accepting address 3, error -71
[156580.972284] usb 2-3: new high-speed USB device number 4 using ehci_hcd
[156582.414177] usb 2-3: config 1 interface 0 altsetting 0 bulk endpoint 0x1 has invalid maxpacket 64
[156582.414193] usb 2-3: config 1 interface 0 altsetting 0 bulk endpoint 0x81 has invalid maxpacket 64
[156582.414206] usb 2-3: config 1 interface 0 altsetting 1 bulk endpoint 0x1 has invalid maxpacket 64
[156582.414217] usb 2-3: config 1 interface 0 altsetting 1 bulk endpoint 0x81 has invalid maxpacket 64
[156582.414937] usb 2-3: New USB device found, idVendor=1c73, idProduct=861f
[156582.414952] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[156582.414961] usb 2-3: Product: anysee-FA(LP)
[156582.414968] usb 2-3: Manufacturer: AMT.CO.KR
[156582.448214] IR NEC protocol handler initialized
[156582.458710] dvb-usb: found a 'Anysee DVB USB2.0' in warm state.
[156582.458860] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[156582.458869] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[156582.458919] IR RC5(x) protocol handler initialized
[156582.459756] DVB: registering new adapter (Anysee DVB USB2.0)
[156582.462924] anysee: firmware version:1.2 hardware id:15
[156582.467097] IR RC6 protocol handler initialized
[156582.472207] IR JVC protocol handler initialized
[156582.477142] IR Sony protocol handler initialized
[156582.485010] IR MCE Keyboard/mouse protocol handler initialized
[156582.490390] DVB: registering adapter 0 frontend 0 (Philips TDA10023 DVB-C)...
[156582.495650] lirc_dev: IR Remote Control driver registered, major 250 
[156582.497513] IR LIRC bridge handler initialized
[156582.545765] DVB: registering adapter 0 frontend 1 (Zarlink ZL10353 DVB-T)...
[156582.592247] Registered IR keymap rc-anysee
[156582.592649] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.2/usb2/2-3/rc/rc0/input6
[156582.592974] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.2/usb2/2-3/rc/rc0
[156582.592985] dvb-usb: schedule remote query interval to 250 msecs.
[156582.592998] dvb-usb: Anysee DVB USB2.0 successfully initialized and connected.
[156582.596150] usbcore: registered new interface driver dvb_usb_anysee

and /dev/dvb/adapter0/..... [frontendx, dvrx, demuxx etc] gets created. So aparently it is an error introduced somewhere between kernel 3.2 and kernel 3.5
I shall mention that my testmachines are lenovo x301 and en media pc running on a intel D2700DC mobo

---

### Post by jensk on 2014-04-23
I can see that the Trusty kernel only sees my usb device as USB 1.1 and the zl10353 aparently demands usb 2.0 but why arent my usb 2.0 ports only available as usb 1.1? I have tried to run additional hardware drivers but nothing is detected

---

### Post by blm-ubunet on 2014-04-23
You see all the error messages with your tuner device & 3.2 kernel..
Surprising it works at all..

The later kernel (3.5) could be falling back to USB1.0 because of those similar type of errors.

I would remove & re-attach all USB devices one at a time..
Could have some other slow device plugged into same controller.
Prove that USB controller works as USB2 (or better) with ext HDD or similar.
Faulty cables
Faulty front panel USB wiring.
Bad hub
Try plugging tuner device into 1 foot USB cable.

 Or could just be the USB speed fallback error threshold has been lowered with later kernel.

---

### Post by jensk on 2014-04-24
Well my testmachines are all Lenovo laptops X301, X200s and X61s They all show the same behavior with Trusty (or rather kernels newer than 3.2) The device is registrered as a USB 1.1 device and doesn't function - like zl10353 cannot load.

If I take the same device (Anysee tuner) incl cable to a similar machine with Debian Squeeze and 3.2 backports kernel it is detected as a USB 2.0 device and works ok - like zl10353 loading and /dev/dvb/adapterx/.... is created

So why does kernels newer than 3.2 only detect the device as a USB 1.1 device while kernel 3.2 and older correctly detects the device as a USB 2.0 device?

I have tried this with similar results for three different tuner devices Anysee E30 Combo, Anysee E30 Combo Plus and a Anysee E30 - all with each their own USB cable

---

### Post by jensk on 2014-04-24
I have now tried the same cables on a USB disc and it comes on as a USB 2.0 device so i assume that cables and USB host is ok. The error is only present when i try to connect the Anysee tuners. As i se it it is the zl10353  that is the problem.

I read this posting:
[http://ubuntuforums.org/showthread.php?t=1376057]("http://ubuntuforums.org/showthread.php?t=1376057")
So I have tried to blacklist uhci_hcd (the usb 1.1 driver) to get it to get it to load the ehci_hcd (the sub 2.0 driver). aparently the uhci_hcd is compiled into the kernel so i can't blacklist it.

---

### Post by jensk on 2014-04-25
I have tried the tuner under a old mythbuntu precise12.04.1 boot. The dmesg is like:
```
[   47.048085] usb 2-1: new high-speed USB device number 4 using ehci_hcd
[   48.164075] usb 2-1: device not accepting address 4, error -71
[   48.276078] usb 2-1: new high-speed USB device number 5 using ehci_hcd
[   49.728451] usb 2-1: config 1 interface 0 altsetting 0 bulk endpoint 0x1 has invalid maxpacket 64
[   49.728456] usb 2-1: config 1 interface 0 altsetting 0 bulk endpoint 0x81 has invalid maxpacket 64
[   49.728460] usb 2-1: config 1 interface 0 altsetting 1 bulk endpoint 0x1 has invalid maxpacket 64
[   49.728464] usb 2-1: config 1 interface 0 altsetting 1 bulk endpoint 0x81 has invalid maxpacket 64
[   49.774298] IR NEC protocol handler initialized
[   49.787376] dvb-usb: found a 'Anysee DVB USB2.0' in warm state.
[   49.788667] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   49.788672] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   49.790407] IR RC5(x) protocol handler initialized
[   49.791174] DVB: registering new adapter (Anysee DVB USB2.0)
[   49.792863] IR RC6 protocol handler initialized
[   49.794947] IR JVC protocol handler initialized
[   49.795425] anysee: firmware version:1.2 hardware id:15
[   49.802778] IR Sony protocol handler initialized
[   49.807298] IR MCE Keyboard/mouse protocol handler initialized
[   49.814926] lirc_dev: IR Remote Control driver registered, major 250 
[   49.815237] IR LIRC bridge handler initialized
[   49.826196] DVB: registering adapter 0 frontend 0 (Philips TDA10023 DVB-C)...
[   49.835302] tda18212: NXP TDA18212HN successfully identified
[   49.849851] DVB: registering adapter 0 frontend 1 (Zarlink ZL10353 DVB-T)...
[   49.852819] tda18212: NXP TDA18212HN successfully identified
[   49.880044] Registered IR keymap rc-anysee
[   49.880191] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/rc/rc0/input12
[   49.880271] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/rc/rc0
[   49.880275] dvb-usb: schedule remote query interval to 250 msecs.
[   49.880280] dvb-usb: Anysee DVB USB2.0 successfully initialized and connected.
[   49.881971] usbcore: registered new interface driver dvb_usb_anysee
```

The differences from the original 12.04.1 kernel to the 14.04 kernel is the reaction on the initial:
```
[   48.164075] usb 2-1: device not accepting address 4, error -71
```
Under 12.04.1 the load proces continues by using the **ehci_hcd** which is the USB 2.0 driver
Under 14.04 the load proces continues by using the **uchi_hcd** which is the USB 1.1 driver

When the USB 1.1 (uhci_hcd) driver is loaded the zl10353 won't load and then the dir's /dev/dvb/adapter...... isn't created

Is it possible to force the load of echi_hcd?

---

### Post by blm-ubunet on 2014-04-25
That's what I meant about the error threshold seems to have changed.
I could see the different usb hcd driver in your logs..
The errors in your 3.2 kernel probably should have caused fall-back from high speed to full speed.

AFAIU The ehci & uhci modules are built-in so the blacklist does not work (same/at all).

The only info I can find about this suggested the fix was to compile kernel without uhci_hcd. Seems very drastic.
I couldn't find any obvious grub boot kernel options..

I would just use 12.04-LTS & mythtv 0.27+fixes.
I actually use 10.04 & mythtv master 0.28.

---

### Post by jensk on 2014-04-26
Thanks Blm-ubunet.
I don't know what the initial "error" is about. But I find it a bit strange that the policy in case of initial errors lets USB faal back to uhci_hcd when the faster ehic_hcd seems to work.  I read somwhere about USB 2.0 and USB 1.1 companion setting under /sys/bus/usb/devices and that it should be possible to turn of this falling back to uhci_hcd on errors. I can't find any docomentation though. Could you point me in the right direction?

---

### Post by blm-ubunet on 2014-04-26
I have only come across using /sys/bus/usb/devices to control USB power to external tuners etc..

This returns a good summary.
```
usb-devices
```

Sorry.

---

### Post by jensk on 2014-04-28
Thank you for your reply.
Yes the usb-devices command gives a lot of information.

I have read about companion usb 1.1 devices at [https://bbs.archlinux.org/viewtopic.php?id=172005]("https://bbs.archlinux.org/viewtopic.php?id=172005")
I will try to turn off the companion function by issuing:
```
echo -x > /sys/bus/usb/devices/usb1/../companion
``` where x is the usb 1.1 fall back port

I still wonder where to find documentation on how to revert to the behavior of the old versions of the kernel (3.2.x) where usb didn't fall back to uhci-hcd on ehci_hcd errors

---

