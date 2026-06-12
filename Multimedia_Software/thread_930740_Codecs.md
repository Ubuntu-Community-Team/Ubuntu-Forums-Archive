---
title: "Codecs"
date: 2008-09-26
forum: Multimedia Software
---

### Post by papabill on 2008-09-26
I'm trying to use the built-in video player, but all I get is a grainy, unable to view picture.

Do I need to download any codecs? And if so, what and where.

Thanks

---

### Post by jualin on 2008-09-26
You can always install the ubuntu-restricted-extras package which includes many codecs. You can do it via terminal > sudo apt-get install ubuntu-restricted-extras You can also install VLC player which is a very good video player, and it doesn't require extra codecs. > sudo apt-get install vlcHope this helps!

---

### Post by papabill on 2008-09-27
Thanks, but they still don't solve my problems. So long as I leave the view screen about the size of a postage stamp, everything is clear as a bell. But when I try to enlarge it to a reasonable size, it becomes all fuzzy. I know it's not my monitor (capable of 1280 x 1024).

Ideas?

Thanks

---

### Post by jualin on 2008-09-27
Do you have the Desktop Effects enabled (Compiz)? Have you installed the video card drivers?

---

### Post by papabill on 2008-09-27
Fortunately, these two new motherboards came with setup and driver discs. Unfortunately, they are for WinDoze, and not Linux. So, I have no drivers for my audio, video, etc.

The motherboards are equipped with SiS UniVGA3 VGA, AD1888 Audio, and SiS RAID. I cannot find any of the drivers I need for Linux (one of the major problems with being a NOOB).

---

### Post by jualin on 2008-09-27
Can you type the output of > lshw on the terminal?

---

### Post by papabill on 2008-09-27
That is a **_*HUGE*_** amount of information. What part of it do you need to see?

---

### Post by Yellow Pasque on 2008-09-28
Try
```
sudo lshw -C video
```
Also, the SiS video driver comes pre-installed by default on Ubuntu.

---

### Post by papabill on 2008-09-28
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0

---

### Post by jualin on 2008-09-28
Try enabling the Desktop effects and see if they work.

---

### Post by papabill on 2008-09-28
I loaded them with the Synaptic Package Manager, but it still says they cannot be enabled.

Is there anywhere else I need to look to activate them?

---

### Post by jualin on 2008-09-28
You should go to System, Preferences, Appearance, and Visual Effects, to enable the Visual Effects. If you can enable them then the driver is probably installed.

---

### Post by papabill on 2008-09-28
That's where I've been going and it tells me that it cannot be enabled.

---

### Post by Yellow Pasque on 2008-09-30
> **papabill said:**
> That's where I've been going and it tells me that it cannot be enabled.
I don't think the SiS driver is capable of visual effects. It's not on the whitelist.

---

### Post by papabill on 2008-09-30
So basically this entire box is worthless, huh? So far as Linux is concerned.

---

### Post by jualin on 2008-09-30
> **papabill said:**
> So basically this entire box is worthless, huh? So far as Linux is concerned.

No, the entire box is not worthless, it's just that the "Visual Effects" (3D Acceleration) cannot be enabled since SiS doesn't provide the Linux drivers. 
I am trying to look for a solution for your problem but I haven't found anything yet, maybe someone else has a different approach to tackle this problem.

---

### Post by jualin on 2008-09-30
I found [this thread]("http://ubuntuforums.org/showthread.php?t=347451") regarding your video card drivers. Maybe you should give it a try. Feel free to ask if you don't understand something on the thread. Good luck!

---

### Post by papabill on 2009-06-24
Well, I have downloaded and installed 4 different sets of codecs, 3 movie players, and still cannot view movies.

lshw -C video gives me this:
*-display
             description: VGA compatible controller
             product: 82810 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810

*-cdrom
                description: DVD-RAM writer
                product: iHAP322   8
                vendor: ATAPI
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: UL14
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready

lspci gave me this:
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:0a.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]

Please help....

thanks

---

