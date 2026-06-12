---
title: "Issues With WUSB600N Adapter in 11.10"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by Prorator on 2011-10-15
After updating from 11.04 to 11.10 my wireless adapter (WUSB600N) doesn't work. 

The issues are similar to the problems I had with it in 11.04 (found [here]("http://ubuntuforums.org/showthread.php?t=1846328")), and were solved by blacklisting rt2800usb. In 11.10, however, the wireless manager isn't even displaying the adapter as connected, and rt2800usb and rt2870sta cannot be found.

If it helps:
lsmod

```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
vesafb                 13809  1 
snd_hda_codec_realtek   330769  1 
nvidia              11713772  40 
snd_usb_audio         118064  2 
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96755  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  19 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 47198  0 
hid                    95463  1 usbhid
wmi                    19256  0 
sp5100_tco             13791  0 
k10temp                13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  0 
i2c_piix4              13301  0 
edac_mce_amd           23709  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
floppy                 70365  0 
pata_jmicron           12747  0 
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 
xhci_hcd               78641  0 


```lsusb

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 1737:0071 Linksys WUSB600N v1 Dual-Band Wireless-N Network Adapter [Ralink RT2870]
Bus 004 Device 002: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 007 Device 002: ID 046d:0a0b Logitech, Inc. ClearChat Pro USB


```Any help would be much appreciated. Thanks.

---

### Post by wildmanne39 on 2011-10-15
Hi, please try:
```
sudo modprobe rt2800usb
```
Thank you

---

### Post by ales on 2011-10-15
> **wildmanne39 said:**
> Hi, please try:
```
sudo modprobe rt2800usb
```
Thank you


Well I had same problem and still have. Only when using this command my wifi goes on. But I have to type it alsways after restart / switch on ....
ANy idea how to make it default?

---

### Post by wildmanne39 on 2011-10-15
Hi, so you can connect right?

You can make it permanent like this.
```
sudo su 
echo rt2800usb >> /etc/modules 
exit
```
if your problem is solved would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by ales on 2011-10-15
> **wildmanne39 said:**
> Hi, so you can connect right?

You can make it permanent like this.
```
sudo su 
echo rt2800usb >> /etc/modules 
exit
```
if your problem is solved would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.


I am going to test it now. But I have another wirelles USB device. Mine is Intelinet 150N (lspci shows RT3070). But work command for me. Should I still mark it solved, when my USB WiFi is another brand?

---

### Post by wildmanne39 on 2011-10-15
Hi, not until it is solved.

So the usb that is working is not the WUSB600N Adapter then?
Thank you

---

### Post by ales on 2011-10-15
> **wildmanne39 said:**
> Hi, not until it is solved.

So the usb that is working is not the WUSB600N Adapter then?
Thank you


No it is not. BUt I used the commands you typed for me and it made my problem solved. Now after start the wifi (USB INtellinet 150N) goes on alone. I am going to past this to my request I wrote to another Thread, so that, other will find it. Many thanks. for the help.

---

### Post by wildmanne39 on 2011-10-15
Hi, shut down your computer then unplug the usb adapter you are using then plugin the WUSB600N Adapter and it should work also I would appreciate if you let me know.
Thank you

---

### Post by Prorator on 2011-10-15
That did the trick for me.

Thank-you very much for the help.

---

### Post by wildmanne39 on 2011-10-15
Hi, that is great we got 2 usb adapters working for the work of one.
Enjoy

---

