---
title: "Microphone not working, and sound problem"
date: 2010-08-01
forum: Multimedia Software
---

### Post by Eremis on 2010-08-01
Hi everybody,

I have had this problem since I installed ubuntu on my Sony Vaio EB... In Win sound and microphone both work perfectly, but in ubuntu at first nether worked...

So in order to get my sound working I followed a tutorial in which I installed the most current alsa drivers... (1.0.23 I think...)

This solved my sound issue (sort of) I can play music, but from one application at a time. For example if I play a mp3 from file, and turn on another program that plays music, the sound stops working, and in order to get them to start working again I need to exit and play one at a time... 

The second problem (even more annoying) is that my microphone does not work at all, so using skype is impossible... 

2 issues I need to fix:

1. Microphone
2. Sound (not as important, but I would like to be able to have 2 sound application play sound at once...)

Can anyone help me?

Thanks!

Some things that you might need to know:

Output of "aplay -l" command:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Output from "lspci -v" command:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: e0000000-f00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f5e0a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f5e08000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 36
	Memory at f5e00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f4a00000-f5dfffff
	Prefetchable memory behind bridge: 00000000f5f00000-00000000f60fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f3600000-f49fffff
	Prefetchable memory behind bridge: 00000000f6100000-00000000f62fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f2200000-f35fffff
	Prefetchable memory behind bridge: 00000000f6300000-00000000f64fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f0200000-f21fffff
	Prefetchable memory behind bridge: 00000000f6500000-00000000f66fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f5e07000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 35
	I/O ports at e070 [size=8]
	I/O ports at e060 [size=4]
	I/O ports at e050 [size=8]
	I/O ports at e040 [size=4]
	I/O ports at e020 [size=32]
	Memory at f5e06000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: medium devsel, IRQ 4
	Memory at f5e05000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f5e04000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 38
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0020000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at d000 [size=256]
	Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 37
	Memory at f0040000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e017
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4a00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 SD Host controller: Ricoh Co Ltd Device e822
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f3602000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:00.1 System peripheral: Ricoh Co Ltd Device e230
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f3601000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.4 SD Host controller: Ricoh Co Ltd Device e822
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f3600000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at f2220000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	Expansion ROM at f2200000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0


```

If you need more info, just post...

---

### Post by lidex on 2010-08-01
Did you uninstall pulseaudio?
What do you have selected in:
```
gstreamer-properties
```
Can you provide this output please:
```
dpkg -l | grep "pulse"
```

---

### Post by Eremis on 2010-08-01
I fixed both the microphone problem, and the sound problem...
After an update, I got kernel version 24, so I had to reinstall alsa drivers again... Insted of doing so, I searched diffrent forums, and found this fix on fedora forums... (This does not require to install new alsa, but to just change some settings around...)

> 
 Originally Posted by kvinayaks  View Post
Try the following solution (found at [https://bugs.launchpad.net/ubuntu/+s...er/+bug/537448](https://bugs.launchpad.net/ubuntu/+s...er/+bug/537448)) which worked for me:

"There is this tool that lets you flip settings around but the changes aren't persistant: [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

To get my speakers working, I ran the hda_analyzer above and under "Node[0x19]" at the bottom in a pane called "Widget Control", I flipped the VREF to "HIZ" and that did the trick." [Source: Arwind Tugade on [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/445889](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/445889))


Before I did this, I changed some settings in "sound preferences" under "hardware tab" I choose "Analog Sterio Duplex" which made my mic work...

The only problem now, is then restart, I have to run that python script again, and change the setting to "HIZ", is there a permanent way of changing this setting?

Thanks!

---

### Post by Eremis on 2010-08-01
Here is the output from that command:
```

ii  gstreamer0.10-pulseaudio             0.10.21-1ubuntu3                                GStreamer plugin for PulseAudio
ii  libcanberra-pulse                    0.22-1ubuntu2                                   PulseAudio backend for libcanberra
ii  libpulse-browse0                     1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client libraries (zeroconf suppor
ii  libpulse-dev                         1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client development headers and li
ii  libpulse-mainloop-glib0              1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client libraries (glib support)
ii  libpulse0                            1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client libraries
ii  libsdl1.2debian-pulseaudio           1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and Pulse
ii  pulseaudio                           1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio sound server
ii  pulseaudio-esound-compat             1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio ESD compatibility layer
ii  pulseaudio-module-bluetooth          1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-gconf              1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 GConf module for PulseAudio sound server
ii  pulseaudio-module-x11                1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 X11 module for PulseAudio sound server
ii  pulseaudio-utils                     1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 Command line tools for the PulseAudio sound 
ii  vlc-plugin-pulse                     1.0.6-1ubuntu1.1                                PulseAudio plugin for VLC

```

It would be nice if you could tell me, how to permanently change those (the ones I talk about above...) setting...

---

### Post by lidex on 2010-08-01
You'll need to run a script at startup to make that happen. Here is an example:
[http://ubuntuforums.org/showpost.php?p=9599525&postcount=152](http://ubuntuforums.org/showpost.php?p=9599525&postcount=152)

The links you provided do not work, if you could post them in the proper format maybe I could figure something out.

---

### Post by Eremis on 2010-08-01
This is the link for the program: [http://www.alsa-project.org/main/index.php/HDA_Analyzer]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")

Can you write the script for me? Or show me how? that link did not really help me... 

All I need to do is in Node[0x19] under "Widget Control" switch the "VREF" to "HIZ"

Thanks

---

### Post by Eremis on 2010-08-01
This is the python script that you get from the link above (save as run.py, and run as root)  This script will open up that program that I was talking about where you can change the settings. 

```

#!/usr/bin/env python

URL="http://git.alsa-project.org/?p=alsa.git;a=blob_plain;f=hda-analyzer/"
FILES=["hda_analyzer.py", "hda_guilib.py", "hda_codec.py", "hda_proc.py",
       "hda_graph.py", "hda_mixer.py"]

try:
  import gobject
  import gtk
  import pango
except:
  print "Please, install pygtk2 or python-gtk package"

import os
import sys
from urllib import splithost
from httplib import HTTP

if os.path.exists("/dev/shm"):
  TMPDIR="/dev/shm"
else:
  TMPDIR="/tmp"
TMPDIR += "/hda-analyzer"
print "Using temporary directory: %s" % TMPDIR
print "You may remove this directory when finished or if you like to"
print "download the most recent copy of hda-analyzer tool."
if not os.path.exists(TMPDIR):
  os.mkdir(TMPDIR)
for f in FILES:
  dest = TMPDIR + '/' + f
  if os.path.exists(dest):
    print "File cached " + dest
    continue
  print "Downloading file %s" % f
  host, selector = splithost(URL[5:])
  h = HTTP(host)
  h.putrequest('GET', URL + f)
  h.endheaders()
  h.getreply()
  contents = h.getfile().read(2*1024*1024)
  h.close()
  open(dest, "w+").write(contents)
print "Downloaded all files, executing %s" % FILES[0]
os.system("python %s" % TMPDIR + '/' + FILES[0] + ' ' + ' '.join(sys.argv[1:]))

```

---

### Post by bhavya juneja on 2010-08-04
[SIZE=2]hi..
i am a new user and i have installed fedora on my vaio eb16 and i am facing the same problem..can u please give me the link to the tutorial you followed to make your sound working...
Thanks[/SIZE]

---

