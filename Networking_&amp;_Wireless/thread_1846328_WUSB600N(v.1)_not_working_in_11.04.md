---
title: "WUSB600N(v.1) not working in 11.04"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by Prorator on 2011-09-18
I'm running an Ubuntu/Win7 dual boot.

The adapter works fine in Windows, but Ubuntu won't even detect the adapter (WUSB600N) as connected anymore.

When I first installed Ubuntu, it detected the adapter, and would hold a connection. However it was slow (~5-50kb/s), and would occasionally drop connection. In trying to troubleshoot it, I managed to make it so that Ubuntu now won't even detect the adapter, much less connect to any network.

I've tried looking around the forums for a similar problem, but from what I can tell the WUSB600N is supposed to have support out of the box in 11.04.

Any help would be much appreciated.

---

### Post by chili555 on 2011-09-18
Please open a terminal and run and post:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Prorator on 2011-09-18
Nothing is output after running the command.

I did double check that I had it input correctly.

---

### Post by chili555 on 2011-09-19
> **Prorator said:**
> Nothing is output after running the command.

I did double check that I had it input correctly.Hey, I took my best shot to guess what was the driver in use and I missed; sorry. Now we'll have to do it the right way. Please post:```
lsusb
lsmod
```Thanks.

---

### Post by Prorator on 2011-09-19
lsusb

```
  [FONT=&quot]
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1737:0071 Linksys WUSB600N Dual-Band Wireless-N USB Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/FONT]
  
```lsmod

```
  
[FONT=&quot]Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
binfmt_misc            17565  1 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
nvidia              10709116  40 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           249811  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                13119  0 
edac_core              53845  0 
edac_mce_amd           23464  0 
sp5100_tco             13744  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13303  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
ahci                   25951  2 
firewire_core          62646  1 firewire_ohci
floppy                 74120  0 
crc_itu_t              12707  1 firewire_core
libahci                26642  1 ahci
r8169                  48022  0 
pata_jmicron           12747  0 
xhci_hcd               77643  0 
[/FONT]
  
```

---

### Post by chili555 on 2011-09-19
> ID [COLOR="Red"]1737:0071[/COLOR] Linksys WUSB600N Dual-Band Wireless-N USB Network AdapterThis device is claimed by both rt2870sta and rt2800usb and they conflict. That leads to poor or no performance. That's probably what lead you to try ndiswrapper. As you have seen, it's performance is not much better. Let's try a temporary experiment. We'll unload ndiswrapper and load rt2870sta. Tell us if it works better; if so, we'll make it permanent.```
sudo ifconfig wlan0 down
sudo rmmod -f ndiswrapper
sudo modprobe rt2870sta
sudo ifconfig wlan0 up
```

---

### Post by Prorator on 2011-09-19
That did the trick.

Probably not of any consequence but when bringing wlan0 down I was given this response:

```

wlan0: ERROR while getting interface flags: No such device

```

Everything else worked. The adapter is now detected in the network menu, and is holding a connection at regular speed.

Now to make it permanent?

---

### Post by praseodym on 2011-09-19
Additionally you may want to remove ndiswrapper and its config completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Reload the driver:

```
sudo modprobe -rf rt2870sta
sudo modprobe -v rt2870sta
```
Replug the stick and check:

```
lsmod | grep rt2
```
If two drivers, namely rt2870sta and rt2800usb are shown, blacklist the wrong one:

```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot or reload the driver rt2870sta again.

---

### Post by Prorator on 2011-09-19
I did all the above steps. 

There were more than just 2 rt2 drivers (rt2800usb, rt2800lib, rt2x00usb, rt2x00lib) I blacklisted those as well.

Now after a restart rt2870 is the only driver showing up when running the 'lsmod | grep' line which I assume was the intent.

Is this now the permanent solution?

---

### Post by praseodym on 2011-09-19
**rt2800usb** normally is enough, you can delete the others from the list by hand via

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

---

### Post by Prorator on 2011-09-19
Okay.

Having just un-blacklisted the rest of the drivers (with the exception of rt2800usb) it is once again only showing:

```

rt2870sta             450556  1 
crc_ccitt              12667  1 rt2870sta

```

Which I assume is the whole idea. Is that all that is necessary?

---

### Post by praseodym on 2011-09-19
Yes, that should be the trick. Check:

```
iwconfig
ifconfig -a
sudo iwlist scan
ping -c 4 213.95.41.11
route -n #without cable
```

---

### Post by Prorator on 2011-09-19
Everything seems to be in good order.

Thanks for the help praseodym and chili555. It was much appreciated.

---

