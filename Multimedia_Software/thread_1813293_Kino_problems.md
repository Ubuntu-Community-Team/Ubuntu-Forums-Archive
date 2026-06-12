---
title: "Kino problems"
date: 2011-07-27
forum: Multimedia Software
---

### Post by abooks on 2011-07-27
Got a new firewire card for my desktop and have downloaded every conceivable 1394-related thing from synaptics, but my KINO still says raw1394 module not loaded, and won't recognize my handycam. Computer seems to recognize card, but something is missing. Any ideas?

---

### Post by Johnny Buffalkill on 2011-07-27
This seems to be a security thing with firewire.  If you run kino as root it should work.

In terminal:
> sudo kinoThen you should be able to capture.  The only problem is that the files will be owned by root instead of you, so you might have to change ownership.  If you capture to an separate drive or partition, you might be able to avoid the ownership problem.  

There are other solutions too, but they aren't as simple.
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

---

### Post by abooks on 2011-07-27
I swear I tread that, too, and it just got stuck. This time it says "no AV/C compliant cam or not switched on." I turned it on after I was in Kino, but I wonder if I need to mess with the camera play settings?

---

### Post by Johnny Buffalkill on 2011-07-28
Drag.  That's the limit to my knowledge on the subject.  Maybe somebody better informed than me will know something.

If you do happen to figure it out, let us know what it is.

---

### Post by abooks on 2011-07-28
OK, here's the latest: someone had suggested turning on the camera BEFORE starting the computer. . .and when I did sudo kino, I got raw 1394 not loaded again. I switched it off. sudo kino'd again, and it said it wasn't on, but didn't detect that I HAD turned it on. Here's the terminal play by play:

> help language code en
> Kino Common being built
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating ExportMJPEG Page
/usr/share/kino/scripts/dvdauthor/dvdauthor-brasero.sh
/usr/share/kino/scripts/dvdauthor/none.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor-k3b.sh
/usr/share/kino/scripts/dvdauthor/growisofs.sh
/usr/share/kino/scripts/dvdauthor/qdvdauthor.sh
> Initializing MJPEG Export Page settings from Preferences
> Creating ExportPipe Page
/usr/share/kino/scripts/exports/ffmpeg_mp3.sh
/usr/share/kino/scripts/exports/ffmpeg_vcd.sh
/usr/share/kino/scripts/exports/ffmpeg_divx_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
/usr/share/kino/scripts/exports/mencoder.sh
/usr/share/kino/scripts/exports/ffmpeg_mov.sh
/usr/share/kino/scripts/exports/extract_chapters
/usr/share/kino/scripts/exports/ffmpeg_utils.sh
/usr/share/kino/scripts/exports/ffmpeg2dirac.sh
/usr/share/kino/scripts/exports/gstreamer_theora.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid_dual.sh
/usr/share/kino/scripts/exports/rawplay.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd.sh
/usr/share/kino/scripts/exports/ffmpeg_huffyuv.sh
/usr/share/kino/scripts/exports/ffmpeg2theora.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4.sh
/usr/share/kino/scripts/exports/ffmpeg_divx.sh
/usr/share/kino/scripts/exports/ffmpeg_3gp.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_ps3.sh
/usr/share/kino/scripts/exports/gstreamer_utils.sh
/usr/share/kino/scripts/exports/ffmpeg_flv.sh
> Creating page trim
>>> Image Create: Colour Range
>>> Image Create: Fixed Colour
>>> Image Create: From File
>>> Image Create: Gradient
>>> Image Create: Random noise
>>> Image Filter: No Change
>>> Image Filter: Black & White
>>> Image Filter: Kaleidoscope
>>> Image Filter: Fade In
>>> Image Filter: Fade Out
>>> Image Filter: Flip
>>> Image Filter: Mirror
>>> Image Filter: Reverse Video
>>> Image Filter: Sepia
>>> Image Transition: Dissolve
>>> Image Transition: Barn Door Wipe
>>> Image Transition: Differences
>>> Image Transition: No Change
>>> Image Transition: Push Wipe
>>> Image Transition: Switch
>>> Audio Filter: No Change
>>> Audio Filter: Dub
>>> Audio Filter: Fade In
>>> Audio Filter: Fade Out
>>> Audio Filter: Gain
>>> Audio Filter: Mix
>>> Audio Filter: Silence
>>> Audio Transition: Cross Fade
>>> Audio Transition: No Change
> Creating Magick Page
>> Searching /usr/lib/kino-gtk2 for plugins
>>> Registering plugin /usr/lib/kino-gtk2/libtimfx.so
>>> Registering plugin /usr/lib/kino-gtk2/libkinoplus.so
>>> Registering plugin /usr/lib/kino-gtk2/libdvtitler.so
>>> Image Filter: Blur
>>> Image Filter: Colour Hold
>>> Image Filter: Soft Focus
>>> Image Transition: Luma Wipe
>>> Image Filter: Colour Average
>>> Image Filter: Charcoal
>>> Image Filter: Jerky
>>> Image Filter: Levels
>>> Image Filter: Pan and Zoom
>>> Image Filter: Pixelate
>>> Image Transition: Composite
>>> Image Transition: Blue Chroma Key
>>> Image Transition: Green Chroma Key
>>> Image Filter: Superimpose
>>> Image Filter: Titler
>> Creating undo/redo buffer
>> Starting Editor
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
>> Leaving Editor
>> Left Editor
>> Starting Capture
>> AV/C Enabled
>>> Using iec61883 capture
>>> iec61883Reader::StartThread on port 0
>> Constructing File Capture tracker
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
rom1394_0 warning: read failed: 0x0000fffff0000414
>> Kino Common newFile
>> Leaving Capture
>> Starting Editor
>>> Received playlist to store at position 0
>>>> Adding to end
Exiting Kino
Any suggestions? Is it 11.4? The firewire card? The camera? Kino?

---

### Post by abooks on 2011-07-28
One more thing and I'll leave y'all alone: if the firewire card is perceived, but not initialized, did I get one that won't work with ubuntu? I should throw it away and try another?

alt@walt-Dell-DM061:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)

THEN


walt@walt-Dell-DM061:~$ grep 1394 /var/log/kern.log
Jul 25 17:41:49 walt-Dell-DM061 kernel: [    1.913943] pnp 00:06: [mem 0x01000000-0x1f651bff]
Jul 25 17:41:49 walt-Dell-DM061 kernel: [    1.913947] pnp 00:06: [mem 0x000f0000-0x000fffff]
Jul 26 21:01:59 walt-Dell-DM061 kernel: [    9.139447] usbcore: registered new interface driver usblp
Jul 27 10:25:08 walt-Dell-DM061 kernel: [    1.851394] PCI: Using ACPI for IRQ routing

---

### Post by scubasean on 2011-09-27
Hi,

Did you ever sort this problem? I am pretty new to Linux but seem to have had a similar problem to you. Kino gave:

"WARNING: raw1394 kernal module not loaded or failure to read/write/dev/raw1394!"

Then when I made Kino root I got:

"No AV/C compliant cam or not switched on"

Somebody then said this is all because the raw1394 stack has been replaced on 11.04.

I also get similar responses to lspci:

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

And grep 1394 /var/log/kern.log:

Sep 25 15:31:25 sean-desktop kernel: [    0.513947] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

That is no mention of firewire.

Could you, or someone else, help me?

Sean

---

### Post by tiberiustibz on 2012-03-28
> Did you ever sort this problem? I am pretty new to Linux but seem to have had a similar problem to you. Kino gave:

"WARNING: raw1394 kernal module not loaded or failure to read/write/dev/raw1394!"

Then when I made Kino root I got:

"No AV/C compliant cam or not switched on"

Somebody then said this is all because the raw1394 stack has been replaced on 11.04.


I have the same problem. The pci card is recognized, but the kernel does not initialize the driver. Any luck?

---

### Post by Lobstercat on 2012-03-29
I too am having issues with this....  I have been casually trying to figure out what was going on but nothing urgent until Google somehow erased the Microsoft DV driver from the registry & after searching the web  I found only that other people have the same problem but nobody has a solution.  Microsoft says to call Toshiba & Toshiba says to call Microsoft & Google just doesn't respond at all.  DV had been working on my Linux partition about a year ago, but since then I did a massive upgrade - I had been using Ubuntu 8 or 9 something.  Firewire hasn't worked since but I had just been using Windows.  Now that that doesn't work either I am really screwed.  I have been trying all sorts of things, nothing worked yet but if I find something I WILL post it.  Likewise, I'll be looking here for answers as well.....!

---

### Post by Corvair on 2012-06-07
I have the same problem with Kino and my Sony camcorder. Seems nobody knows the solution or is interested in solving the problem

---

### Post by Paul91 on 2012-07-15
Hi everyone. There is an open bug on Ubuntu re Firewire devices not being initialised. This seems to effect from v 10 onwards.

Search on "Ubuntu bug 890539"

It would be a great help if everyone experiencing this bug went to that page and registered that they have the problem. Canonical will react and fix it if enough people want it fixed. Yesterday there were only two of us which is never going to be enough to gain attention.

Please pass this on in whichever forums you see the problem raised.

---

### Post by Paul91 on 2012-07-15
Doing a bit more research also see bug 548513. There are some suggested work arounds there

---

