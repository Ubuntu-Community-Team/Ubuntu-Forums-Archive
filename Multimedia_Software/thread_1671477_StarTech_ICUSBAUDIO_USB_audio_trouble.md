---
title: "StarTech ICUSBAUDIO USB audio trouble"
date: 2011-01-20
forum: Multimedia Software
---

### Post by Vortalex on 2011-01-20
Hello,

I'm having trouble getting sound to work in Ubuntu 10.10. The system belongs to a friend of mine and has been dual booted with Vista, but the plan was to make Ubuntu the primary OS. The systems onboard audio is dead and has no standard PCI slots so we purchased a usb soundcard off newegg because of the review about it's success in Linux.

newegg item page : [http://www.newegg.com/Product/Product.aspx?Item=N82E16829128002](http://www.newegg.com/Product/Product.aspx?Item=N82E16829128002)

When the system is booted with the device plugged in sometimes you can hear the startup sound at the login menu. But after you login, nothing. The audio icon is crossed out and no slider but, if I run alsamixer I see Speaker, Mic and Auto Gain Control. Trying to adjust them makes alsamixer lag and the result of change are slow. Thats goes for any program that tries to access audio, it lags or freezes up.

I noticed our user wasn't part of the audio group so I made the change, reboot... no change.

Under the Output tab of the Sound Preferences the device usually isn't listed, just Dummy Output. The only time I've been able to get it show up is if I plug the device in after logging into the system. Still no audio, but you can select it as an output and you get the taskbar audio slider, but it doesn't really work. I watched alsamixer while moving it, nothing.


The onboard sound is disabled in the bios, but
I tried commenting out the line: options snd-usb-audio index=-2
in /etc/modprobe.d/alsa-base.conf
no change


So after messing around with it for some hours I'm out of ideas, the devices works just fine in Windows. So if anyone could help, it would be much appreciated.

cat /proc/asound/cards
```
 0 [default        ]: USB-Audio - USB PnP Sound Device
                      C-Media Electronics Inc.       USB PnP Sound Device           at usb-0000:00:02
```uname --all
```
Linux Voltron 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux
```

---

### Post by BicyclerBoy on 2011-01-20
Plug it in after booting into desktop.

post last 20 lines from 
dmesg

post output of
lsusb
lsmod


Where do you read around the linux success with this device ?

---

### Post by Vortalex on 2011-01-20
dmesg | tail -20
```
[    9.722091] type=1400 audit(1295574912.116:8): apparmor="STATUS" operation="p                                                                                        rofile_load" name="/usr/lib/cups/backend/cups-pdf" pid=958 comm="apparmor_parser                                                                                        "
[    9.722448] type=1400 audit(1295574912.116:9): apparmor="STATUS" operation="p                                                                                        rofile_load" name="/usr/sbin/cupsd" pid=958 comm="apparmor_parser"
[   10.173225] type=1400 audit(1295574912.566:10): apparmor="STATUS" operation="                                                                                        profile_replace" name="/sbin/dhclient3" pid=984 comm="apparmor_parser"
[   10.173501] type=1400 audit(1295574912.566:11): apparmor="STATUS" operation="                                                                                        profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=984 co                                                                                        mm="apparmor_parser"
[   10.242053] ppdev: user-space parallel port driver
[   10.982273]   alloc irq_desc for 45 on node 0
[   10.982276]   alloc kstat_irqs on node 0
[   10.982286] forcedeth 0000:00:0a.0: irq 45 for MSI/MSI-X
[   14.319483] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   21.220298] eth0: no IPv6 routers present
[   24.883309] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   86.530310] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   86.861114] usbcore: registered new interface driver hiddev
[   86.869254] input: C-Media Electronics Inc.       USB PnP Sound Device                                                                                                   as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.3/input/input5
[   86.869405] generic-usb 0003:0D8C:013C.0001: input,hidraw0: USB HID v1.00 Dev                                                                                        ice [C-Media Electronics Inc.       USB PnP Sound Device          ] on usb-0000:                                                                                        00:02.0-2/input3
[   86.869442] usbcore: registered new interface driver usbhid
[   86.869445] usbhid: USB HID core driver
[   87.238611] usbcore: registered new interface driver snd-usb-audio
[   93.741423] timeout: still 3 active urbs..
[   99.741268] timeout: still 8 active urbs..
```lsusb
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0d8c:013c C-Media Electronics, Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```lsmod```

Module                  Size  Used by
snd_usb_audio         105567  2
snd_pcm                89104  1 snd_usb_audio
snd_page_alloc          8588  1 snd_pcm
snd_hwdep               6660  1 snd_usb_audio
snd_usbmidi_lib        21313  1 snd_usb_audio
snd_seq_midi            5932  0
snd_rawmidi            22207  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64181  12 snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 42062  0
soundcore               1240  1 snd
hid                    84710  1 usbhid
binfmt_misc             7984  1
parport_pc             30086  0
ppdev                   6804  0
nvidia              10221046  56
edac_core              46822  0
edac_mce_amd            9387  0
k10temp                 3535  0
i2c_nforce2             6155  0
shpchp                 34910  0
psmouse                62080  0
serio_raw               4910  0
video                  22176  0
output                  2527  1 video
lp                     10201  0
parport                37032  3 parport_pc,ppdev,lp
usb_storage            50372  0
firewire_ohci          24615  0
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
ahci                   22210  2
forcedeth              55649  0
libahci                26052  1 ahci
```Thanks for the reply.

> **BicyclerBoy said:**
> Where do you read around the linux success with this device ?

I meant the reviews/feedback on Newegg.com for that product.  There were some people that claimed they had no problem getting it to work in Linux.  The installation guide paper that came with it even list Linux as a compatible operating system.

---

### Post by Vortalex on 2011-01-22
So any ideas of what it could be?

---

### Post by Vortalex on 2011-01-29
Another try.

---

### Post by Vortalex on 2011-02-04
bump

---

### Post by Vortalex on 2011-02-17
bump

---

### Post by chessnerd on 2011-02-20
I'm also having trouble with this exact USB sound adapter. The adapter shows up under Sound Preferences, and I can choose it as output, but it doesn't work.

It worked the very first time I used it, but it hasn't worked since. The microphone input works great (much better than the on-board one) but the headphone output doesn't seem to function.

If I plug it in when sound is playing, I'll get about 1 second of audio played into my headphones before it goes dead.

---

