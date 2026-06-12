---
title: "Have X-Fi, Trying to Use Realtek ALC882"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by Lazy8s on 2008-03-22
I just installed Ubuntu this morning (dual booting with Vista). So far I have WoW up and running like a dream, woohoo!! Anyways I am getting the error 

> "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I did some searching and it seems my X-Fi Platinum is incompatible. No prob I thought, I booted Vista to see what onboard device was used with my HP desktop. Turns out it's the Realtek ALC882. I have done some searching and I cannot figure ut where to get the driver, let alone install it and use the device.

I read your "fix all" sound thread and I got this far:
> bill@bill-desktop:~$ aplay -l
aplay: device_list:204: no soundcards found...
bill@bill-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f8000000-fbffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at fe00 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at fd00 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at fc00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, medium devsel, latency 0, IRQ 17
        Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: e4000000-ebffffff
        Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at fb00 [size=16]

00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at fa00 [size=8]
        I/O ports at f900 [size=4]
        I/O ports at f800 [size=8]
        I/O ports at f700 [size=4]
        I/O ports at f600 [size=16]
        Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: medium devsel, IRQ 11
        I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0420
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at df00 [size=128]
        [virtual] Expansion ROM at fbfe0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at ebfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 150
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

02:05.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs X-Fi Platinum
        Flags: bus master, medium devsel, latency 32, IRQ 7
        I/O ports at ef00 [size=32]
        Memory at ebc00000 (64-bit, non-prefetchable) [size=2M]
        Memory at e4000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 2a5e
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at ebffe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ee00 [size=64]
        Capabilities: <access denied>

bill@bill-desktop:~$ 


Obviously it shows the incompatible X-Fi. Since I dual boot I really do not want to unplug the sound card. How do I disable the X-Fi and use onboard sound? I have googled and most everything is old 2005/2006 and it's all people that can't get it to work. Any help would be GREATLY appreciated. Thanks in advance.


EDIT: I went here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)
And Downloaded what was under the Linux section. When I open the file it has a bunch of ALSA stuff but it doesn't really explain how to make this work even with my card installed and all. I need my device manager. :'( I am having Windows withdrawl.

When I open realtek-linux-audiopack-5.01.tar.bz2 and run the install I get:

> 
bill@bill-desktop:~/Drivers/realtek-linux-audiopack-5.01$ ./install
.....Decompress Driver source v1.0.15-5.01
.....Decompress ALSA Library source v1.0.15
.....Decompress ALSA Utility v1.0.15
Remove old sound driver
Compile Driver........
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/home/bill/Drivers/realtek-linux-audiopack-5.01/alsa-driver-hg20080219'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/bill/Drivers/realtek-linux-audiopack-5.01/alsa-driver-hg20080219'

Please, run the configure script as first...

if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /home/bill/Drivers/realtek-linux-audiopack-5.01/alsa-driver-hg20080219/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot create directory `/include': Permission denied
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
./install: 40: ./snddevices: not found
Remove old alsa library
Compile ALSA Library.....
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
ln: creating symbolic link `/dev/sndstat' to `/proc/asound/oss/sndstat': File exists
cp: cannot create regular file `/usr/share/sounds/alsa/test.wav': Permission denied
Remove Folder.....
./install: 101: alsaconf: not found


Sorry if this info is useless just lead me to a tutorial or tell me what info you need.

---

### Post by xc3RnbFO8P on 2008-03-22
First read this:

> Good news!

There is finally a WORKING beta driver for 32 bit and 64 bit. Its not done by Creative but OSS.

[http://www.opensound.com/]("http://www.opensound.com/")

it works for playback, and I can finally watch movies on my linux box. I dont think recording works yet fine, but its a start!

About C compiler error:
> sudo aptitude update
sudo aptitude install build-essential

---

### Post by Lazy8s on 2008-03-22
I just wanted to say a huge thank you for resolving this for me. Being new here I feel I need to contribute back so I am preparing a step by step guide for people that do not know their way around Linux.

....well it's kind of resolved, I can't use my mic at all and if I'm going to chat with my friends that's kind of half the point of sound. :-/

---

