---
title: "Need Lots of Graphic Help Sony Vaio CW"
date: 2010-01-29
forum: Multimedia Software
---

### Post by TCYost on 2010-01-29
I need a super step by step walk-thru of the extreme noob variety to help me solve this issue... The EEID issue that plagues my graphics card... If anyone else has figured this out please help...

---

### Post by TCYost on 2010-01-30
The card is The Nvidia G210 please im drowning

---

### Post by TCYost on 2010-01-30
Just bought a Sony Vaio CW today due to all the specs I wanted... NVIDIA card for compatibility with linux and all...  Its a total wash nothing works... Frustrating!!!

---

### Post by Khakilang on 2010-01-30
Hardware failure than you know what to do, claim warranty. If its Window you can always go to Linux. If its Linux problem you know where to ask and if you still want to throw away your computer, you can always throw at me.

---

### Post by TCYost on 2010-01-30
No its all fixable im just new to linux... And cant make enough sense of alot of stuff to get it fixed... I had Ubuntu on my old laptop and everything worked smooth sailing upon install, I was spoiled...

---

### Post by NightwishFan on 2010-01-30
Welcome to Ubuntu Forums.

It is natural to feel frustrated, but this is a good place to ask for help. What problems are you having may I ask?

---

### Post by TCYost on 2010-01-30
Graphics Card-NVIDIA® GeForce® 310M something about the EDID I have to bring it over from windows but I cant seem to figure it out...

Wireless-Im assuming the card is recognized cause it connects to the network and all... Its a B/G/N variety card win a N-Router that flys on windows but on Linux I get barely 2kb a second download speeds and usually not even that much

---

### Post by TCYost on 2010-01-30
It just took me 28min to install the Adobe Flash Plugin for Firefox... The same download in windows took about 3-5 seconds if that???

---

### Post by TCYost on 2010-01-30
Bump for anyones help

---

### Post by nmaster on 2010-01-30
sudo apt-get install flashplugin-nonfree 


not exactly sure what repositories you have to enable... this isn't a new idea though.  google it.

---

### Post by nmaster on 2010-01-30
btw, i'm not really sure what your question is....

---

### Post by NightwishFan on 2010-01-30
Thread about your graphics card.
[http://ubuntuforums.org/showthread.php?t=1392766](http://ubuntuforums.org/showthread.php?t=1392766)

Please note that Ubuntu is primarily about free software. Adobe Flash is not free software, so support is limited to Adobe's discretion. There is an Ubuntu package to simplify installing the flash plugin as a user stated. Use the Software Center.

---

### Post by TCYost on 2010-01-30
[http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

Step 5 Edit xorg.conf  how do I do that final step?

---

### Post by NightwishFan on 2010-01-30
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by overdrank on 2010-01-30
Please do not create multiple threads on the same issue. Threads merged.

---

### Post by tgui on 2010-01-30
I have a similar sony cw laptop with the 330M GPU. 

You'll need to pull your EDID while in windows. EDID data describes the capability of your LCD screen. Problem with the current NVIDIA drivers is that they can't pull this data for some reason and consequently your LCD doesn't work.


1) Pull EDID in Windows. Most say to use the softmccs program but frankly this doesn't work in Windows 7. Not an option. Use Phoenix EDID Designer 1.3. (attached)

[http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441)


2) Place EDID raw file in /etc/X11 . Name it something like sonyedid.bin 

3) Install nvidia drivers from restricted drivers list.

4) Alter xorg.conf to include edid bin refrence as seen below.

5) Note, this xorg file is now setup to enable your Nvidia drivers to detect external HDMI and CRT monitors.


```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 47.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.bin"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


Ive attached my EDID bin for a sony vaio CW with 1600x900 graphics.

-E-

---

### Post by warfacegod on 2010-01-30
```
sudo apt-get install envyng-core
```

That will search for and install the most appropriate video driver for you. After installing envy, It will be found in Applications> System Tools

---

### Post by tgui on 2010-01-30
> **warfacegod said:**
> ```
sudo apt-get install envyng-core
```

That will search for and install the most appropriate video driver for you. After installing envy, It will be found in Applications> System Tools

There is no driver in any repository in any package that will solve the OPs problem. The issue exists with the Nvidia driver itself. Until release 196.x is out, the custom EDID route is the only way to go.

Its a crappy situation.

---

### Post by warfacegod on 2010-01-30
> **tgui said:**
> There is no driver in any repository in any package that will solve the OPs problem. The issue exists with the Nvidia driver itself. Until release 196.x is out, the custom EDID route is the only way to go.

Its a crappy situation.

My mistake. Sorry.

---

### Post by tnunamak on 2010-02-05
> **tgui said:**
> I have a similar sony cw laptop with the 330M GPU. 
...
Ive attached my EDID bin for a sony vaio CW with 1600x900 graphics.

-E-

Thanks a ton, that was really helpful. I also have a CW with the 330M, but I had to get my own EDID binary to get it to work.

Does xserver have to be restarted in order to enable/disable HDMI output? Right now, I have to save changes to xorg config to enable/disable the second screen (through nvidia-settings)... I can't just plug in an HDMI cable and switch it on the fly. I thought maybe KRandR could do it but that only detects displays that are enabled.

Thanks again for the help.

---

### Post by tgui on 2010-02-06
> **tnunamak said:**
> Thanks a ton, that was really helpful. I also have a CW with the 330M, but I had to get my own EDID binary to get it to work.

Does xserver have to be restarted in order to enable/disable HDMI output? Right now, I have to save changes to xorg config to enable/disable the second screen (through nvidia-settings)... I can't just plug in an HDMI cable and switch it on the fly. I thought maybe KRandR could do it but that only detects displays that are enabled.

Thanks again for the help.

No prob! 

Could you post your edid bin just in case others need it?

As far as HDMI and auto detection, I personally setup my xorg.conf to only load the laptop LCD on boot. From there I use nvidia-settings to temporarily enable whatever CRT or HDMI monitor I might be using at the moment. (almost on the fly, all monitors are detected real time)

No other solution works as NVIDIA for some damn reason won't support the latest RandR specification.

Now if only my ath9k internal wireless worked well without dropping packets... you have any luck with that? This laptop has been work.

---

### Post by tnunamak on 2010-02-07
> **tgui said:**
> No prob! 

Could you post your edid bin just in case others need it?

As far as HDMI and auto detection, I personally setup my xorg.conf to only load the laptop LCD on boot. From there I use nvidia-settings to temporarily enable whatever CRT or HDMI monitor I might be using at the moment. (almost on the fly, all monitors are detected real time)

No other solution works as NVIDIA for some damn reason won't support the latest RandR specification.

Now if only my ath9k internal wireless worked well without dropping packets... you have any luck with that? This laptop has been work.

Sure thing, it's attached (renamed to .txt)

I was hoping to get HDMI working the way you have it working. Right now, nvidia-settings detects both displays but I can't enable/disable one or the other. I'm just switching between two different xorg.conf files and restarting xserver... a pain, but better than nothing. It might have something to do with using KDE and not GNOME.

I haven't been able to get audio over HDMI either, after struggling with it for a while. I even recompiled the newest alsa drivers to no avail.

Another audio issue is that I can't audio input from the built-in microphone (not the port).

I have also noticed wireless seems to have issues that don't occur in windows... I didn't realize that maybe it was because of dropped packets.

Below are the two xorg.conf files I'm using, lspci, aplay -l. The model I'm using is the VPCCW26FX. I'm just hoping that support for this hardware is not here yet, but coming soon.

xorg.conf (built-in display)
```

Section "Monitor"
        Identifier     "Vaio_Display"
        VendorName     "Sony"
        ModelName      "VPCCW26FX"
        HorizSync       28.0 - 33.0
        VertRefresh     43.0 - 72.0
        Option         "DPMS"
EndSection
Section "Monitor"
        Identifier     "Big_Display"
        VendorName     "Westinghouse"
        ModelName      "LVM-42w2"
        HorizSync       31.5 - 80.0
        VertRefresh     59.0 - 60.0
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Nvidia330M"
        Monitor        "Vaio_Display"
        Option         "ConnectedMonitor"       "DFP-0,DFP-1"
        Option         "CustomEDID" "DFP-0:/etc/X11/edid_raw.bin"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "InputDevice"        
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "kbd"
EndSection

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
        Identifier      "Nvidia330M"
        VendorName      "NVIDIA Corporation"
        Driver          "nvidia"
        Option          "NoLogo" "True"
        BoardName       "GeForce GT 330M"
EndSection

```

xorg.conf (external display, used via HDMI)
```

Section "Monitor"
        Identifier     "Vaio_Display"
        VendorName     "Sony"
        ModelName      "VPCCW26FX"
        HorizSync       28.0 - 33.0
        VertRefresh     43.0 - 72.0
        Option         "DPMS"
EndSection

Section "Monitor"
        Identifier     "Big_Display"
        VendorName     "Westinghouse"
        ModelName      "LVM-42w2"
        HorizSync       31.5 - 80.0
        VertRefresh     59.0 - 60.0
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Nvidia330M"
        Monitor        "Big_Display"
        Option         "ConnectedMonitor"       "DFP-1"
        Option          "DPI" "144x144"
        Option          "UseEdidDpi" "false"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "kbd"
EndSection

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
        Identifier      "Nvidia330M"
        VendorName      "NVIDIA Corporation"
        BoardName       "GeForce GT 330M"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

lscpi
```
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a2b (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
3f:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
3f:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by tnunamak on 2010-02-07
tgui: I don't see any dropped packets, do you have the same card I do (AR9285)?

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:24:be:b2:b5:d4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53887 (53.8 KB)  TX bytes:53887 (53.8 KB)

wlan0     Link encap:Ethernet  HWaddr 2c:81:58:ed:3d:2d
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e81:58ff:feed:3d2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33457644 (33.4 MB)  TX bytes:5682388 (5.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 2C-81-58-ED-3D-2D-65-64-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by kewvention on 2010-02-07
i managed to have success with using a custom edid by dumping it in from windows. however the issue is that i cannot set the brightness of the screen using the FN keys at all. i could start the nvidia control panel and adjust the brightness of the colours, but its not the same thing at all.  anyone else have that issue aswell?

---

### Post by tgui on 2010-02-08
> **tnunamak said:**
> tgui: I don't see any dropped packets, do you have the same card I do (AR9285)?

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:24:be:b2:b5:d4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53887 (53.8 KB)  TX bytes:53887 (53.8 KB)

wlan0     Link encap:Ethernet  HWaddr 2c:81:58:ed:3d:2d
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e81:58ff:feed:3d2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33457644 (33.4 MB)  TX bytes:5682388 (5.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 2C-81-58-ED-3D-2D-65-64-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I do. Uses the ATH9k driver. No matter the version of driver I try, pulling a large file and running ping reveals dropped packets.  I've got a USB 802.11N network card until the driver stabilizes.

---

### Post by tgui on 2010-02-08
> **tnunamak said:**
> Sure thing, it's attached (renamed to .txt)

I was hoping to get HDMI working the way you have it working. Right now, nvidia-settings detects both displays but I can't enable/disable one or the other. I'm just switching between two different xorg.conf files and restarting xserver... a pain, but better than nothing. It might have something to do with using KDE and not GNOME.

I haven't been able to get audio over HDMI either, after struggling with it for a while. I even recompiled the newest alsa drivers to no avail.

Another audio issue is that I can't audio input from the built-in microphone (not the port).

I have also noticed wireless seems to have issues that don't occur in windows... I didn't realize that maybe it was because of dropped packets.

Below are the two xorg.conf files I'm using, lspci, aplay -l. The model I'm using is the VPCCW26FX. I'm just hoping that support for this hardware is not here yet, but coming soon.

xorg.conf (built-in display)
```

Section "Monitor"
        Identifier     "Vaio_Display"
        VendorName     "Sony"
        ModelName      "VPCCW26FX"
        HorizSync       28.0 - 33.0
        VertRefresh     43.0 - 72.0
        Option         "DPMS"
EndSection
Section "Monitor"
        Identifier     "Big_Display"
        VendorName     "Westinghouse"
        ModelName      "LVM-42w2"
        HorizSync       31.5 - 80.0
        VertRefresh     59.0 - 60.0
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Nvidia330M"
        Monitor        "Vaio_Display"
        Option         "ConnectedMonitor"       "DFP-0,DFP-1"
        Option         "CustomEDID" "DFP-0:/etc/X11/edid_raw.bin"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "InputDevice"        
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "kbd"
EndSection

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
        Identifier      "Nvidia330M"
        VendorName      "NVIDIA Corporation"
        Driver          "nvidia"
        Option          "NoLogo" "True"
        BoardName       "GeForce GT 330M"
EndSection

```

xorg.conf (external display, used via HDMI)
```

Section "Monitor"
        Identifier     "Vaio_Display"
        VendorName     "Sony"
        ModelName      "VPCCW26FX"
        HorizSync       28.0 - 33.0
        VertRefresh     43.0 - 72.0
        Option         "DPMS"
EndSection

Section "Monitor"
        Identifier     "Big_Display"
        VendorName     "Westinghouse"
        ModelName      "LVM-42w2"
        HorizSync       31.5 - 80.0
        VertRefresh     59.0 - 60.0
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Nvidia330M"
        Monitor        "Big_Display"
        Option         "ConnectedMonitor"       "DFP-1"
        Option          "DPI" "144x144"
        Option          "UseEdidDpi" "false"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "kbd"
EndSection

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
        Identifier      "Nvidia330M"
        VendorName      "NVIDIA Corporation"
        BoardName       "GeForce GT 330M"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

lscpi
```
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a2b (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
3f:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
3f:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Same here, no sound over HDMI yet. Ohh well, my HTPC runs an Intel GPU which supports sounds over HDMI in linux.

I like and hate Nvidia at the same time. :D

---

### Post by dakochan on 2010-02-26
@tgui:

Thank you so much for the files. It fixed my problem.

---

### Post by azizmulhim on 2010-03-09
Hi
[SIZE=2]
I have a similar problem with My sony Vaio laptop [/SIZE][B][SIZE=2]VPCS117GAwith  NVIDIA® GeForce® 310M GPU with CUDA™ Technology.

[/SIZE][/B][SIZE=2]Which Nvidia driver I should use 185 , 190 or 195. I have downloaded & installed them from nvidia site but none is working.
  I have even added into my xorg.conf  edid extracted from window 7 proffessional using [/SIZE]softMCCS "running using  windows 98 compability".

My problem is once I install driver   from the command line & login to Gnome to activate the driver using  sudo nvidia-xconfig  the xorg.conf is replaced by the driver. 

How do I force my own version  xorg.conf to be loaded instead. 
I have tried replacing the xorg.conf generated by the driver by the modified one "containing reference to my edid file"  and the result I got either "low graphic or gray screen"

I have followed  many instructions in ubuntu forums & other but no success, I am back to the default xorg.conf.

---

### Post by fungiscience on 2010-04-21
Got the same problem here with **Sony VAIO VPC-CW13FD** containing a **nVidia GeForce 210M** running on Ubuntu Karmic 9.10 64 bits.

-Without nVidia driver, HDMI output isn't working
-With nVidia driver (from repositories version 185 or from nVidia website version 195.36.15) HDMI output is activated but main laptop display is black
-With EDID workaround the laptop screens comes up but the HDMI output screen isn't detected anymore

For the last point, I tested with the solution proposed earlier with the forced connection :

```

    Option         "ConnectedMonitor" "DFP-0, DFP-1, CRT"

```

But the HDMI connected screen doesn't come up. Here is another attempt I made with the HDMI screen EDID :

```

    Option         "CustomEDID" "DFP-0:/etc/X11/VAIOLCD_edid.bin"
    Option         "CustomEDID" "DFP-1:/etc/X11/Philips220SW_edid.bin"

```

Still no success.
I'm trying to extend my desktop with the HDMI screen. I would use VGA (cause it is working fine without nVidia driver with VGA), but I'm trying to connect 2 computers to the same display and the other computer has only VGA output.

Any hints?

---

### Post by fungiscience on 2010-04-30
Installed the latest nVidia driver yesterday and thought you should know it fixed all my problems with the HDMI output.

Version 195.36.24

Here is my xorg.conf for the record :

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:36:15 PDT 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony Nvidia Default Flat Panel"
    HorizSync       29.0 - 47.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Philips 220SW"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G210M"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G210M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ConnectedMonitor" "DFP-0, DFP-1, CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/VAIOLCD_edid.bin"
    Option         "ModeValidation" "NoTotalSizeCheck"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+282, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by kvmanohar on 2010-05-01
> **tgui said:**
> I have a similar sony cw laptop with the 330M GPU. 

You'll need to pull your EDID while in windows. EDID data describes the capability of your LCD screen. Problem with the current NVIDIA drivers is that they can't pull this data for some reason and consequently your LCD doesn't work.


1) Pull EDID in Windows. Most say to use the softmccs program but frankly this doesn't work in Windows 7. Not an option. Use Phoenix EDID Designer 1.3. (attached)

[http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441)


2) Place EDID raw file in /etc/X11 . Name it something like sonyedid.bin 

3) Install nvidia drivers from restricted drivers list.

4) Alter xorg.conf to include edid bin refrence as seen below.

5) Note, this xorg file is now setup to enable your Nvidia drivers to detect external HDMI and CRT monitors.


```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 47.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.bin"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


Ive attached my EDID bin for a sony vaio CW with 1600x900 graphics.

-E-



Last month I bought new Sony CW series same as with the configuration show in your thread above... yesterday i have downloaded the Ubuntu10.04 x64bit edit and created a CD from the ISO file... as instructed I have placed the CD in the drive and restarted the laptop to install Ubuntu.. but, after first screen (which has two icons at the bottom) the screen turned blank and nothing was displayed.. I don't know who to continue further.. Please could you help me.. 

Thank you
Manohar

---

### Post by gochichi on 2010-05-02
I have the same problem, Ubuntu 10.04 just goes to black screen.  Live CD or Install Ubuntu now both don't work at all.

I should say also that the last Beta worked Live CD wise, and it even worked fine and dandy until I activated the proprietary NVIDIA drivers.  

I also have the the 1600 x 900 screen.  I haven't tried all of the other video outputs, I know VGA out with the laptop open didn't work at all either.  I was thinking about trying to close the laptop and try the HDMI out also.

Any and all help would be tremendous.  I was really looking forward to geeking out on some Linux and enjoying my very nice hardware.  The model number if it matters:  VPCCW27FX

---

### Post by thepolishkid on 2010-05-02
I have the same problem, managed to install it using the alternate install cd, but the screen still goes black on boot. Right after nouveau puts up some messages that I can't read that fast. I think disabling nouveau might at least return it to the way that 9.10 used to work with the custom edid.

---

### Post by thepolishkid on 2010-05-03
I finally got 10.04 working on my cw. To install it I hooked up my laptop to an external monitor using the vga port and everything showed up on the external monitor during the install. after the reboot everything still showed up on the external monitor (sony screen was still blank). I installed the nvidia drivers (this blacklists the nouveau stuff). Then I had to edit my xorg.conf file the same way that you do in 9.10 and after reboot the sony screen started working again.

---

### Post by Yap Siauw Soen Gie on 2010-05-11
in my VCCW26FG the phoenix extracted different type of file with .dat extension
with some warning that this is not an up to date version of edid file
look like below:

EDID BYTES: 
0x   00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    ------------------------------------------------ 
00 | 00 FF FF FF FF FF FF 00 4D D9 FA 06 00 00 00 00 
10 | 2D 0C 01 03 90 1F 11 00 EA A8 E0 99 57 4B 92 25 
20 | 1C 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01 
30 | 01 01 01 01 01 01 40 38 40 F6 63 84 13 30 52 52 
40 | 66 50 36 AE 10 00 00 18 00 00 00 FC 00 4E 76 69 
50 | 64 69 61 20 44 65 66 61 75 6C 00 00 00 FC 00 74 
60 | 20 46 6C 61 74 20 50 61 6E 65 6C 00 00 00 00 FD 
70 | 00 00 3D 1D 38 0B 00 00 20 20 20 20 20 00 00 48

I try to rename it with .bin extension and put it under /etc/x11/ and reconfigure the xorg.conf after activate nvidia recommended driver

After restarting the machine the screen blinking... look terrible and divided into 4 horizontal identical section

Do you have solution for this kind of problem tgui?

btw. The ubuntu installed on my system is lucid lynx amd64

---

### Post by thepolishkid on 2010-05-11
> **Yap Siauw Soen Gie said:**
> in my VCCW26FG the phoenix extracted different type of file with .dat extension
with some warning that this is not an up to date version of edid file
look like below:

EDID BYTES: 
0x   00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    ------------------------------------------------ 
00 | 00 FF FF FF FF FF FF 00 4D D9 FA 06 00 00 00 00 
10 | 2D 0C 01 03 90 1F 11 00 EA A8 E0 99 57 4B 92 25 
20 | 1C 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01 
30 | 01 01 01 01 01 01 40 38 40 F6 63 84 13 30 52 52 
40 | 66 50 36 AE 10 00 00 18 00 00 00 FC 00 4E 76 69 
50 | 64 69 61 20 44 65 66 61 75 6C 00 00 00 FC 00 74 
60 | 20 46 6C 61 74 20 50 61 6E 65 6C 00 00 00 00 FD 
70 | 00 00 3D 1D 38 0B 00 00 20 20 20 20 20 00 00 48

I try to rename it with .bin extension and put it under /etc/x11/ and reconfigure the xorg.conf after activate nvidia recommended driver

After restarting the machine the screen blinking... look terrible and divided into 4 horizontal identical section

Do you have solution for this kind of problem tgui?

btw. The ubuntu installed on my system is lucid lynx amd64

I had that graphical problem when I did not have my edid file installed in xorg. I attached my edid.bin file. Let me know if it works for you. I extracted it from my windows partition using softmccs or something like that, so if you don't trust my upload maybe try using that program. I don't have my xorg.conf file on hand but if this doesn't help maybe you can post urs,

---

### Post by Yap Siauw Soen Gie on 2010-05-12
thanks polishkid... unfortunately softmccs won't work on 64 bit system, that is why i use phoenix instead
not yet try some edid created by other that i already downloaded included yours...
just worry because of my ubuntu system also have 64 bit configuration either.

but again thanks for your kindness

---

### Post by thepolishkid on 2010-05-12
> **Yap Siauw Soen Gie said:**
> thanks polishkid... unfortunately softmccs won't work on 64 bit system, that is why i use phoenix instead
not yet try some edid created by other that i already downloaded included yours...
just worry because of my ubuntu system also have 64 bit configuration either.

but again thanks for your kindness

I used softmccs on a windows 7 professional x64 system. I'm not sure why people are saying that it doesnt work on x64 system but it worked for mine. I am running ubuntu 10.04 x64 as well with that edid file.

---

### Post by Yap Siauw Soen Gie on 2010-05-12
yeeehawwwwwww :D

Finally I did it :)

I open your EDID file with a hex editor (ghex), coincidentally I saw that your EDID exactly have the same sum number in hex as what phoenix already shown above 16x8 or 128 hex number.
... and then I edited them one by one to match what the phoenix program already extracted for me and save it as SNY06FA.bin

- logout then login as root and put the copy of SNY06FA.bin to /etc/x11/
- Go online to the internet....
- get the nvidia driver from System -> Administration ->  Hardware Drivers
- remove the nomodeset word from /etc/default/grub which has been suggested for me [here]("http://ubuntuforums.org/showthread.php?p=9267547#post9267547")
- open /etc/x11/xorg.conf with gedit and replace the content as tgui's code above:

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 47.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/SNY06FA.bin"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection- reboot... and voila... here i am with 1600 x 900 ; 59.94 hz resolution :)

Thank you to all of you here  \\:D/

btw. below I attach my edid file as your request polishkid

---

### Post by darinho on 2010-05-25
Valew cara, funcionou perfeitamente.



Obrigado.:smile::smile::smile:

---

### Post by expfunc on 2010-06-19
Hi, I have vaio cw, and having the same problem.
I want to try as the way you have explained but I don't know where is /etc/X11. Also, don't know where I supposed to put the CODE into. Could you help this out? 
Many thanks..   


> **tgui said:**
> I have a similar sony cw laptop with the 330M GPU. 

You'll need to pull your EDID while in windows. EDID data describes the capability of your LCD screen. Problem with the current NVIDIA drivers is that they can't pull this data for some reason and consequently your LCD doesn't work.


1) Pull EDID in Windows. Most say to use the softmccs program but frankly this doesn't work in Windows 7. Not an option. Use Phoenix EDID Designer 1.3. (attached)

[http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441)


2) Place EDID raw file in /etc/X11 . Name it something like sonyedid.bin 

3) Install nvidia drivers from restricted drivers list.

4) Alter xorg.conf to include edid bin refrence as seen below.

5) Note, this xorg file is now setup to enable your Nvidia drivers to detect external HDMI and CRT monitors.


```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 47.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.bin"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


Ive attached my EDID bin for a sony vaio CW with 1600x900 graphics.

-E-

---

### Post by zorocke on 2010-07-01
> **tgui said:**
> I have a similar sony cw laptop with the 330M GPU. 


2) Place EDID raw file in /etc/X11 . Name it something like sonyedid.bin 


Can someone help explain how to do this. I cannot even boot ubuntu from the cd in order to get to a filesystem.

---

### Post by Shompol on 2010-07-07
> **zorocke said:**
> Can someone help explain how to do this. I cannot even boot ubuntu from the cd in order to get to a filesystem.
Connect your laptop with external monitor. There is a VGA port on the left of your VIAO -- use it.  With external monitor everything works: you can install Ubuntu at your leisure, and then follow the instructions by tgui (page 2) to patch Nvidia driver.

---

### Post by sython on 2010-07-23
> **Shompol said:**
> Connect your laptop with external monitor. There is a VGA port on the left of your VIAO -- use it.  With external monitor everything works: you can install Ubuntu at your leisure, and then follow the instructions by tgui (page 2) to patch Nvidia driver.

Hi. Like the previous person had said, I'm very new to linux so i don't even know where to start. I've downloaded the program and everything else that has been attached from page 2. Is the EDID file only located in linux? Because I can't find it in windows...

---

### Post by Shompol on 2010-07-26
> **sython said:**
> Hi. Like the previous person had said, I'm very new to linux so i don't even know where to start. I've downloaded the program and everything else that has been attached from page 2. Is the EDID file only located in linux? Because I can't find it in windows...

It is located in Windows:
Use Phoenix EDID Designer 1.3.

[http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441)

Tools --> Extract Registry EDID...

Press button "Extract EDID", 

File --> Export ->> Save as type: Raw EDID format *.raw

Now, the resulting file should be accessed from Linux. You can mount the windows partition, given you installed dual boot, by using the mount command, but the easiest way is to save the file to a flash drive and just read it back in Linux.

---

### Post by alessandro_ufms on 2010-08-03
Hello,

nvidia 256.44 solved the EDID problem for me (330m). I needn't specify EDID manually on xorg.conf anymore. :-)

---

### Post by teo_rossi on 2010-09-04
alessandro_ufms is right, with drivers above 256.44 no custom EDID is required. Now dual monitor works flawlessly!!!!

---

### Post by speedygeo on 2010-09-10
Great news for the next install! Thanks!):P

---

### Post by verdecito on 2010-09-11
hi this info is good but i couldnot fix my lap this is what happened  
i just updated my 10.04 and i shutdow but went i turn it on just a black screen the  recovery mode do not work nothing just black i try with live cd y paste all the files like you said guys but i so new in ubuntu so here im  lol im paste edid file and the xorg.conf nothing just black screen i got a vaio  intel core i3 m330@2.13ghz 2.13 4.00 gm ram nvidia getforce with cuda 310M and ubuntu 10.04 /windows7

---

### Post by tnunamak on 2010-11-03
Does anyone have any information or solutions for getting the 260 drivers working with Ubuntu 10.10?

---

### Post by speedygeo on 2010-11-04
[http://www.nvnews.net/vbulletin/showpost.php?p=2118873](http://www.nvnews.net/vbulletin/showpost.php?p=2118873)

---

### Post by oskar321 on 2011-01-07
Thank you very much... you helped me to fix my problem with my vaio mac osx 10.6.6. I'm going to test, if i can get the full resolution of 1600x900 instead of 1280x800.

---

### Post by lyokos on 2011-02-06
what's this all about I could not understand any of these solution !!!

I mean I had the black screen when I wanted to install the ubuntu 10.4 also 10.10 black screen 
 
the steps ???!!!! where on windows 7 anyone can explain ?? 


2) Place EDID raw file in /etc/X11 . Name it something like sonyedid.bin 

3) Install nvidia drivers from restricted drivers list.

4) Alter xorg.conf to include edid bin refrence as seen below.

5) Note, this xorg file is now setup to enable your Nvidia drivers to detect external HDMI and CRT monitors.

---

### Post by drdineshml on 2011-02-16
> **tgui said:**
> I have a similar sony cw laptop with the 330M GPU. 

You'll need to pull your EDID while in windows. EDID data describes the capability of your LCD screen. Problem with the current NVIDIA drivers is that they can't pull this data for some reason and consequently your LCD doesn't work.


1) Pull EDID in Windows. Most say to use the softmccs program but frankly this doesn't work in Windows 7. Not an option. Use Phoenix EDID Designer 1.3. (attached)

[http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441)


2) Place EDID raw file in /etc/X11 . Name it something like sonyedid.bin 

3) Install nvidia drivers from restricted drivers list.

4) Alter xorg.conf to include edid bin refrence as seen below.

5) Note, this xorg file is now setup to enable your Nvidia drivers to detect external HDMI and CRT monitors.


```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 47.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.bin"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
Ive attached my EDID bin for a sony vaio CW with 1600x900 graphics.

-E-

Hi,
I am also using vpccw26fg and I tried the method you given but while booting it enter to the blank violet ubuntu screen and stuck there, cannot boot.
Installed Ubuntu10.10 32 bit
Thanks

---

### Post by drdineshml on 2011-02-16
Hi,
I am also using vpccw26fg and I tried the method you given but while  booting it enter to the blank violet ubuntu screen and stuck there,  cannot boot.
Installed Ubuntu10.10 32 bit
Thanks

---

### Post by ahmad598 on 2011-03-11
> **tgui said:**
> I have a similar sony cw laptop with the 330M GPU. 

You'll need to pull your EDID while in windows. EDID data describes the capability of your LCD screen. Problem with the current NVIDIA drivers is that they can't pull this data for some reason and consequently your LCD doesn't work.


1) Pull EDID in Windows. Most say to use the softmccs program but frankly this doesn't work in Windows 7. Not an option. Use Phoenix EDID Designer 1.3. (attached)

[http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441)


2) Place EDID raw file in /etc/X11 . Name it something like sonyedid.bin 

3) Install nvidia drivers from restricted drivers list.

4) Alter xorg.conf to include edid bin refrence as seen below.

5) Note, this xorg file is now setup to enable your Nvidia drivers to detect external HDMI and CRT monitors.


```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 47.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sonyedid.bin"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


Ive attached my EDID bin for a sony vaio CW with 1600x900 graphics.

-E-

Hi
I've tried this solution and still no success. Here's my info:
[LIST]
[*]my vaio is VPC S136 FG with a GeForce 310M.
[*]I've extractes EDID file using Phoenix in Win7. the EDID file is attached.
[*]my xorg log file doesnt say any error about the edid file. you can find it in the following.
[*]when ubuntu boots up, the screen is divided to 6-7 gray bars. sound just works.
[*]i can boot up ubuntu in failsafe mode with 1280*... resolution, but it doesnt use nvidia driver.
[*]I've installed Nvidia driver, version 260.19.06-0ubuntu1.
[/LIST]

also this is my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
	Option	"ConnectedMonitor"	"DFP-0"
	Option	"CustomEDID"	"DFP-0:/etc/X11/edid.raw"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
and the xorg log file:
```
[    12.345] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    12.353] X Protocol Version 11, Revision 0
[    12.353] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    12.353] Current Operating System: Linux vaio 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    12.353] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=af281b98-981a-4eb6-9ebf-36357393bed5 ro quiet splash
[    12.353] Build Date: 16 September 2010  05:39:22PM
[    12.353] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    12.353] Current version of pixman: 0.18.4
[    12.353] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.353] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.353] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 11 20:20:10 2011
[    12.399] (==) Using config file: "/etc/X11/xorg.conf"
[    12.399] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.435] (==) ServerLayout "Layout0"
[    12.435] (**) |-->Screen "Screen0" (0)
[    12.435] (**) |   |-->Monitor "Monitor0"
[    12.435] (**) |   |-->Device "Device0"
[    12.435] (**) |-->Input Device "Keyboard0"
[    12.435] (**) |-->Input Device "Mouse0"
[    12.435] (==) Automatically adding devices
[    12.435] (==) Automatically enabling devices
[    12.534] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.534] 	Entry deleted from font path.
[    12.566] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    12.566] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.566] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    12.566] (WW) Disabling Keyboard0
[    12.566] (WW) Disabling Mouse0
[    12.566] (II) Loader magic: 0x81f8e00
[    12.566] (II) Module ABI versions:
[    12.566] 	X.Org ANSI C Emulation: 0.4
[    12.566] 	X.Org Video Driver: 8.0
[    12.566] 	X.Org XInput driver : 11.0
[    12.566] 	X.Org Server Extension : 4.0
[    12.567] (--) PCI:*(0:1:0:0) 10de:0a75:104d:9069 rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00007000/128, BIOS @ 0x????????/524288
[    12.567] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.567] (II) LoadModule: "extmod"
[    12.640] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.653] (II) Module extmod: vendor="X.Org Foundation"
[    12.653] 	compiled for 1.9.0, module version = 1.0.0
[    12.653] 	Module class: X.Org Server Extension
[    12.653] 	ABI class: X.Org Server Extension, version 4.0
[    12.653] (II) Loading extension MIT-SCREEN-SAVER
[    12.653] (II) Loading extension XFree86-VidModeExtension
[    12.653] (II) Loading extension XFree86-DGA
[    12.653] (II) Loading extension DPMS
[    12.653] (II) Loading extension XVideo
[    12.653] (II) Loading extension XVideo-MotionCompensation
[    12.653] (II) Loading extension X-Resource
[    12.653] (II) LoadModule: "dbe"
[    12.654] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.654] (II) Module dbe: vendor="X.Org Foundation"
[    12.654] 	compiled for 1.9.0, module version = 1.0.0
[    12.654] 	Module class: X.Org Server Extension
[    12.654] 	ABI class: X.Org Server Extension, version 4.0
[    12.654] (II) Loading extension DOUBLE-BUFFER
[    12.654] (II) LoadModule: "glx"
[    12.654] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    13.395] (II) Module glx: vendor="NVIDIA Corporation"
[    13.395] 	compiled for 4.0.2, module version = 1.0.0
[    13.395] 	Module class: X.Org Server Extension
[    13.395] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    13.395] (II) Loading extension GLX
[    13.395] (II) LoadModule: "record"
[    13.395] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.403] (II) Module record: vendor="X.Org Foundation"
[    13.403] 	compiled for 1.9.0, module version = 1.13.0
[    13.403] 	Module class: X.Org Server Extension
[    13.403] 	ABI class: X.Org Server Extension, version 4.0
[    13.403] (II) Loading extension RECORD
[    13.403] (II) LoadModule: "dri"
[    13.404] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.407] (II) Module dri: vendor="X.Org Foundation"
[    13.407] 	compiled for 1.9.0, module version = 1.0.0
[    13.407] 	ABI class: X.Org Server Extension, version 4.0
[    13.407] (II) Loading extension XFree86-DRI
[    13.407] (II) LoadModule: "dri2"
[    13.407] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.408] (II) Module dri2: vendor="X.Org Foundation"
[    13.408] 	compiled for 1.9.0, module version = 1.2.0
[    13.408] 	ABI class: X.Org Server Extension, version 4.0
[    13.408] (II) Loading extension DRI2
[    13.408] (II) LoadModule: "nvidia"
[    13.408] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    13.560] (II) Module nvidia: vendor="NVIDIA Corporation"
[    13.560] 	compiled for 4.0.2, module version = 1.0.0
[    13.560] 	Module class: X.Org Video Driver
[    13.616] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    13.644] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    13.644] (++) using VT number 7

[    13.647] (II) Loading sub module "fb"
[    13.647] (II) LoadModule: "fb"
[    13.647] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.660] (II) Module fb: vendor="X.Org Foundation"
[    13.660] 	compiled for 1.9.0, module version = 1.0.0
[    13.660] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.660] (II) Loading sub module "wfb"
[    13.660] (II) LoadModule: "wfb"
[    13.661] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    13.685] (II) Module wfb: vendor="X.Org Foundation"
[    13.685] 	compiled for 1.9.0, module version = 1.0.0
[    13.685] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.685] (II) Loading sub module "ramdac"
[    13.685] (II) LoadModule: "ramdac"
[    13.685] (II) Module "ramdac" already built-in
[    13.717] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    13.717] (==) NVIDIA(0): RGB weight 888
[    13.717] (==) NVIDIA(0): Default visual is TrueColor
[    13.718] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    13.718] (**) NVIDIA(0): Option "ConnectedMonitor" "DFP-0"
[    13.718] (**) NVIDIA(0): Option "CustomEDID" "DFP-0:/etc/X11/edid.raw"
[    13.720] (**) NVIDIA(0): Enabling RENDER acceleration
[    13.721] (**) NVIDIA(0): ConnectedMonitor string: "DFP-0"
[    13.721] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    13.721] (II) NVIDIA(0):     enabled.
```

any solution or idea is appreciated.
Thanx ;-)

---

