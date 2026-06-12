---
title: "How to make DVB-T tuner work under Linux"
date: 2015-01-12
forum: Multimedia Software
---

### Post by fkervin on 2015-01-12
Hi all,

In the past I've use some DVB-T USB dongle with kubuntu but now I'm trying to make it work with a new installation of Xubuntu 14.04 and I'm unable to.

I have those two USB devices:

1f4d:c803 G-Tek Electronics Group (not working on kubuntu 14.04)
1d19:1101 Dexatek Technology Ltd. DK DVB-T Dongle (Worked on kubuntu 14.04)

Both of them are recognized by kaffeine as RTL2832.

I remember that in Kubuntu I used [V4L-DVB]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers") procedure to install drivers, but I also installed something else I don't remember.

The question is that with Xubuntu 14.04 both devices appears in kaffeine but when I try to scan I get the message "there is no device detected", strangely once I tried it scanned but found no channels.

Mu question is obvious... How can I install drivers for those tuner in order they (or at least one of them) work correctly?

Many thanks in advance

---

### Post by fkervin on 2015-01-14
Hi all again,

anyone can give some advice?

Regards :)

---

### Post by oldos2er on 2015-01-14
Moved to Multimedia.

---

### Post by Bucky Ball on 2015-01-14
Do you mean the RTL2832U? I have one of those and it 'just works' (using a minimal install with the xfce4 desktop environment, so basically a pared down Xubuntu). So let's try and figure out why yours doesn't.

Anyways, pull the TV dongle out, plug it in and immediately open a terminal and type:

```
dmesg
```

Please post the last part of the output concerning the TV dongle which should show that you've plugged the device in and the system's response to it. Thanks.

Mine looks like this:

```
[94625.342295] usb 2-1.1: Product: RTL2838UHIDIR
[94625.342298] usb 2-1.1: Manufacturer: Realtek
[94625.348056] usb 2-1.1: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[94625.411072] usb 2-1.1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[94625.411101] DVB: registering new adapter (Realtek RTL2832U reference design)
[94625.414604] usb 2-1.1: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[94625.423970] i2c i2c-0: e4000: Elonics E4000 successfully identified
[94625.435564] Registered IR keymap rc-empty
[94625.435739] input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rc/rc3/input20
[94625.435878] rc3: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rc/rc3
[94625.436261] input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input21
[94625.436559] rc rc3: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[94625.436571] usb 2-1.1: dvb_usb_v2: schedule remote query interval to 400 msecs
[94625.448640] usb 2-1.1: dvb_usb_v2: **'Realtek RTL2832U reference design' successfully initialized and connected**
```

The bold bit is the important part.

PS: Just wondering why you're using Kaffeine in Xubuntu? That is a Kubuntu app and drags in a heap of Kubuntu stuff. That could be part of your problem. Try MeTV and see if you get the same response. It's in the repositories.

---

### Post by fkervin on 2015-01-17
> **Bucky Ball said:**
> Do you mean the RTL2832U? I have one of those and it 'just works' (using a minimal install with the xfce4 desktop environment, so basically a pared down Xubuntu). So let's try and figure out why yours doesn't.

Anyways, pull the TV dongle out, plug it in and immediately open a terminal and type:

```
dmesg
```

Please post the last part of the output concerning the TV dongle which should show that you've plugged the device in and the system's response to it. Thanks.

Mine looks like this:

```
[94625.342295] usb 2-1.1: Product: RTL2838UHIDIR
[94625.342298] usb 2-1.1: Manufacturer: Realtek
[94625.348056] usb 2-1.1: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[94625.411072] usb 2-1.1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[94625.411101] DVB: registering new adapter (Realtek RTL2832U reference design)
[94625.414604] usb 2-1.1: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[94625.423970] i2c i2c-0: e4000: Elonics E4000 successfully identified
[94625.435564] Registered IR keymap rc-empty
[94625.435739] input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rc/rc3/input20
[94625.435878] rc3: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rc/rc3
[94625.436261] input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input21
[94625.436559] rc rc3: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[94625.436571] usb 2-1.1: dvb_usb_v2: schedule remote query interval to 400 msecs
[94625.448640] usb 2-1.1: dvb_usb_v2: **'Realtek RTL2832U reference design' successfully initialized and connected**
```

The bold bit is the important part.

PS: Just wondering why you're using Kaffeine in Xubuntu? That is a Kubuntu app and drags in a heap of Kubuntu stuff. That could be part of your problem. Try MeTV and see if you get the same response. It's in the repositories.

Many thanks for your help, Bucky Ball

I tryed Kaffeine since it's the program I used on Kubuntu, haha, but really I'm also trying TVHeadend, that is what I'm really interested in, and here also doesn't work.

This is the output of dmesg

```
[ 1456.312188] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 1456.312191] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 1456.368057] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1456.368069] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1456.368071] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1456.413847] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1456.413878] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1456.413917] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1456.413957] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1456.413997] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1456.414037] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1456.414078] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 1698.803562] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1698.803579] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1698.803581] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1698.803599] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[ 1698.803602] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 1698.803604] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1698.803605] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 1698.803606] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[ 1698.803607] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[ 1698.803608] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[ 1698.803610] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[ 1698.839232] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1698.839256] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1698.839265] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1698.839281] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 1698.839287] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 1698.843424] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 1698.843455] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 1698.843462] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 1698.843476] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 1698.843482] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[ 1698.878247] ieee80211 phy0: rt2800usb_txdone: Warning - Data pending for entry 7 in queue 2
[ 1698.878325] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878365] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878395] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878440] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878521] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878560] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878602] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878643] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878682] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878734] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878781] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.878861] ieee80211 phy0: rt2800usb_txdone: Warning - Data pending for entry 8 in queue 2
[ 1698.884731] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1698.884752] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.161825] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[ 1737.161844] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[ 1737.161847] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[ 1737.161860] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 1737.161876] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1737.166008] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 1737.166026] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 1737.166029] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 1737.166044] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[ 1737.166049] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[ 1737.166054] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[ 1737.166058] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[ 1737.166063] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1737.166067] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 1737.170192] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 1737.170203] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 1737.170206] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 1737.170232] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 1737.170247] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 1737.170255] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[ 1737.170263] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[ 1737.174408] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1737.174419] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1737.174422] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1737.241604] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 1737.252209] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252250] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252297] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252350] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252402] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252441] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252481] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252531] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252612] ieee80211 phy0: rt2800usb_txdone: Warning - Data pending for entry 2 in queue 2
[ 1737.252691] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252730] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252781] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252862] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.252901] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1737.255263] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 3984.259868] usb 3-6: new high-speed USB device number 7 using xhci_hcd
[ 3984.289138] usb 3-6: New USB device found, idVendor=1d19, idProduct=1101
[ 3984.289146] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3984.289151] usb 3-6: Product: DVB-T Dongle
[ 3984.289155] usb 3-6: Manufacturer: Realtek
[ 3984.289159] usb 3-6: SerialNumber: 00000991
[ 3984.310407] rc_core: module verification failed: signature and/or  required key missing - tainting kernel
[ 3984.311341] WARNING: You are using an experimental version of the media stack.
[ 3984.311341]     As the driver is backported to an older kernel, it doesn't offer
[ 3984.311341]     enough quality for its usage in production.
[ 3984.311341]     Use it with care.
[ 3984.311341] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[ 3984.311341]     654a731be1a0b6f606f3f3d12b50db08f2ae3c34 [media] media: s5p-mfc: use vb2_ops_wait_prepare/finish helper
[ 3984.311341]     c747404dbf2dcc0d8cb5d2e8aee5810b6ebba496 [media] media: s5p-tv: use vb2_ops_wait_prepare/finish helper
[ 3984.311341]     8776ff659d8f9e86850fbe432610461ab09a94a0 [media] media: sh_veu: use vb2_ops_wait_prepare/finish helper
[ 3984.313001] WARNING: You are using an experimental version of the media stack.
[ 3984.313001]     As the driver is backported to an older kernel, it doesn't offer
[ 3984.313001]     enough quality for its usage in production.
[ 3984.313001]     Use it with care.
[ 3984.313001] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[ 3984.313001]     654a731be1a0b6f606f3f3d12b50db08f2ae3c34 [media] media: s5p-mfc: use vb2_ops_wait_prepare/finish helper
[ 3984.313001]     c747404dbf2dcc0d8cb5d2e8aee5810b6ebba496 [media] media: s5p-tv: use vb2_ops_wait_prepare/finish helper
[ 3984.313001]     8776ff659d8f9e86850fbe432610461ab09a94a0 [media] media: sh_veu: use vb2_ops_wait_prepare/finish helper
[ 3984.314036] usb 3-6: dvb_usb_v2: found a 'Dexatek DK DVB-T Dongle' in warm state
[ 3984.344956] usb 3-6: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[ 3984.344964] DVB: registering new adapter (Dexatek DK DVB-T Dongle)
[ 3984.345367] i2c i2c-6: Added multiplexed i2c bus 7
[ 3984.347967] i2c i2c-6: Added multiplexed i2c bus 8
[ 3984.347972] usb 3-6: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[ 3984.349111] fc0013: Fitipower FC0013 successfully attached.
[ 3984.350424] media: Linux media interface: v0.10
[ 3984.351820] Linux video capture interface: v2.00
[ 3984.351822] WARNING: You are using an experimental version of the media stack.
[ 3984.351822]     As the driver is backported to an older kernel, it doesn't offer
[ 3984.351822]     enough quality for its usage in production.
[ 3984.351822]     Use it with care.
[ 3984.351822] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[ 3984.351822]     654a731be1a0b6f606f3f3d12b50db08f2ae3c34 [media] media: s5p-mfc: use vb2_ops_wait_prepare/finish helper
[ 3984.351822]     c747404dbf2dcc0d8cb5d2e8aee5810b6ebba496 [media] media: s5p-tv: use vb2_ops_wait_prepare/finish helper
[ 3984.351822]     8776ff659d8f9e86850fbe432610461ab09a94a0 [media] media: sh_veu: use vb2_ops_wait_prepare/finish helper
[ 3984.353250] usb 3-6: Registered as swradio0
[ 3984.353253] i2c i2c-6: rtl2832_sdr: Realtek RTL2832 SDR attached
[ 3984.353255] usb 3-6: rtl2832_sdr: SDR API is still slightly experimental and functionality changes may follow
[ 3984.359660] Registered IR keymap rc-empty
[ 3984.359726] input: Dexatek DK DVB-T Dongle as /devices/pci0000:00/0000:00:14.0/usb3/3-6/rc/rc0/input14
[ 3984.360076] rc0: Dexatek DK DVB-T Dongle as /devices/pci0000:00/0000:00:14.0/usb3/3-6/rc/rc0
[ 3984.361130] IR NEC protocol handler initialized
[ 3984.361203] IR RC5(x/sz) protocol handler initialized
[ 3984.364553] IR RC6 protocol handler initialized
[ 3984.368954] IR JVC protocol handler initialized
[ 3984.369200] IR Sony protocol handler initialized
[ 3984.370157] IR SANYO protocol handler initialized
[ 3984.370757] IR Sharp protocol handler initialized
[ 3984.371098] usb 3-6: dvb_usb_v2: schedule remote query interval to 400 msecs
[ 3984.371172] input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input15
[ 3984.371594] lirc_dev: IR Remote Control driver registered, major 247 
[ 3984.372003] IR MCE Keyboard/mouse protocol handler initialized
[ 3984.372277] rc rc0: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[ 3984.372279] IR LIRC bridge handler initialized
[ 3984.372325] IR XMP protocol handler initialized
[ 3984.379050] usb 3-6: dvb_usb_v2: 'Dexatek DK DVB-T Dongle' successfully initialized and connected
[ 3984.379074] usbcore: registered new interface driver dvb_usb_rtl28xxu
[ 3984.870814] usb 3-6: DVB: adapter 0 frontend 0 frequency 0 out of range (174000000..862000000)

```

I'm going to try MeTV, althought I want TVHEadend to work and it doesn't

Regards

---

### Post by Bucky Ball on 2015-01-17
Looks like the dongle is recognised and a driver is loaded for it. If you try MeTV and it picks up the dongle, that has an autoscan for channels. This is the only bit I can see in the dmesg output that is problematic:

```
[ 3984.870814] usb 3-6: DVB: adapter 0 frontend 0 [B]frequency 0 out of range (174000000..862000000)
[/B]
```

The bit in bold. Unsure how to fix that. :-k

---

