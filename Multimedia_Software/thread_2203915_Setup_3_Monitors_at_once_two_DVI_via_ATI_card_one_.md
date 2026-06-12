---
title: "Setup 3 Monitors at once two DVI via ATI card one via VGA onboard"
date: 2014-02-05
forum: Multimedia Software
---

### Post by bob46 on 2014-02-05
I am trying to get three display support going and it may  just be a matter of setting up a xorg.conf file properly.  After all the  research I've done, it should work with the hardware I'm using just  fine.

  [B]
Ubuntu[/B]:

  ```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:   precise

```  **Processor**:
  ```
Intel® Core™ i5-3450 CPU @ 3.10GHz × 4 

```  That 3rd gen processor supports 3 monitors:
  ```
# of Displays Supported ‡   3

```  Source: [http://ark.intel.com/products/65511/Intel-Core-i5-3450-Processor-6M-Cache-up-to-3_50-GHz](http://ark.intel.com/products/65511/Intel-Core-i5-3450-Processor-6M-Cache-up-to-3_50-GHz)
  [B]
Graphics[/B]:

  ```
sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: RV620 LE [Radeon HD 3450]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:e0000000-efffffff memory:f7c20000-f7c2ffff ioport:e000(size=256) memory:f7c00000-f7c1ffff
  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)

```  The Radeon HD 3450 has ATI CrossFireX™ multi-GPU support which I  understand will enable it to work fine with another video card: the  onboard VGA compatible controller.
  Source: [http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-3000/hd-3400/Pages/ati-radeon-hd-3400-overview.aspx](http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-3000/hd-3400/Pages/ati-radeon-hd-3400-overview.aspx)
  [B]
Contents of X11[/B] (I haven't touched anything):

  ```
ls /etc/X11/
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config

```

 So with the ATI card I have a dual head splitter which I connect to  two DVI cords on dual monitors - and when the VGA screen isn't plugged  in - they work as expected as a dual set-up.  When trying to attach the  VGA card it doesn't get any juice or show up under the ubuntu display  settings and just continues as a dual set-up.  I figured I'd have to  boot with the VGA onboard enabled then activated the ATI attached  displays somehow.  So what I'm trying now is to boot with the VGA  plugged in (which is working fine) but I can't get either of the other  two screens up and they are not listed under the display settings.

When I boot up the Ubuntu logo is on the two DVI connected monitors - but when the login screen comes it is on the VGA onboard monitor and the other two go black (no source video).

  

  
I also have an onboard HDMI port I could utilize (one dvi  through ati, one vga via onboard, one hdmi via onboard), but I thought  HDMI had to be dedicated, but not sure about that..


  This is a Dell Optiplex 3010, and I just flashed to the latest BIOS version.

Note: I have not tried anything out of the box yet - no drivers, no xorg.conf configurations, etc.

Any suggestions are welcome, thanks.  (I did post this on ask ubuntu, but this seemed like a more fitting place, sorry if this is against any rules)

---

### Post by bob46 on 2014-02-06
I'm thinking if I can create an xorg.conf which includes all three screen then maybe I can force the system to see all three?

Any ideas??

---

### Post by gordintoronto on 2014-02-06
The first thing I would do is install the Additional Driver for the ATI card. Then I would see what I could do with (I think) Catalyst Control Center. If there is an onboard DVI port, I would connect to it and the DVI on the video card. Then I would try adding the onboard VGA port.

I think your understanding of "That 3rd gen processor supports 3 monitors" and Crossfire are incomplete; you might do further reading on those topics.

---

### Post by bob46 on 2014-02-08
@gordintoronto - thats for the reply.

I have successfully installed the Catalyst Control Center from AMD.  Now I have many more options for configuration than before with the standard Ubuntu settings.

I do not have an onboard DVI port.  I have an onboard VGA port and an onboard HDMI port.

Currently I'm sucessfully running dual monitors via the Radeon card.  Do you have any pointers as how to try to enable my onboard VGA or HDMI port to work together with the Radeon now that I have the custom drivers and software loaded?

Thanks!

---

### Post by bob46 on 2014-02-08
My current xorg.conf file:

```
cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3840 1920
        Depth     24
    EndSubSection
EndSection
```


I need to figure out how to get my onboard VGA or HDMI ports to run with the two DVI displays which are connected to the ATI card.

Anyone have any pointers?  Thanks!

---

### Post by bob46 on 2014-02-08
In my BIOS under graphics there is the option to "enable multi display support" or whatever - with a note this feature is only for windows 7 and doesn't not apply to other operating systems.

Not sure if this will help anyone help me...

Halp!

---

### Post by frank18 on 2014-02-08
Hi guys;i also have an ATI AMD HD6450 card and have Hdmi DVI and VGA  i have HDMI Mirrored with DVI runing great but also would like to have the VGA also at same time but it's not possible only can run 2 outputs mirrored and there is no option to run a third monitor at same time,there's where Linux socks on these details,why have a card with 3 outputs if you only can have 2 running,if you guys find a solution for this it would be appreciated.

---

### Post by QIII on 2014-02-08
Hello!

Linux itself has nothing to do with this issue.  OEMs write drivers for their hardware.  OS developers do not.  Microsoft does not write ATI drivers for Windows.  ATI does.

If either of you is using a desktop, most OEMs allow you to select EITHER onboard or dedicated graphics, but not both.  Sometimes you can select both, but that is a BIOS/EFI setting.  If you are using an ATI APU, this may work, but the graphics series of both GPUs must be supported by an ATI driver.  Many APUs have older series drivers that ATI no longer supports Linux drivers for.

Provided the BIOS allows concurrent use and both GPUs are still supported,  both GPUs must be initialized after installing the driver by doing ```
 sudo amdconfig --adapter=all --initial
``` and Xinerama is usually required across separate GPUs.

I have several machines I can run triple monitors on in Eyefinity mode.  My primary machine is doing that now.  But the card has to be designed to support three monitors and it must work with a current ATI driver.

Unfortunately I'm on my cell phone right now and can't offer much more help.  But I'll try to look back in on this later this evening.

---

### Post by QIII on 2014-02-08
@bob46 --

Now that I am on a computer (not at home -- on the road, so I am not at a Linux machine) and have had a chance to look more carefully at this, I can say that you are not likely to find a setting in the BIOS/EFI for that machine that will allow the use of both GPUs.   Even if you could, your HD 3000 series ATI GPU is no longer supported on Linux by ATI.  Beyond 12.04.1, the HD 4000 series graphics will not work because the legacy driver ATI has assigned to them will not work with the current X Server.  Although there are hacks out there, I would not recommend using them because they effectively break your installation and I don't think any of them would work successfully with 12.04.4 in any case.

Add to that the complication that your other GPU is an Intel unit and you would have quite a mess.  The long and the short of it is that you are very unlikely to find any way to get both the Intel and ATI GPUs working concurrently on a desktop board.  With laptops using hybrid graphics, this was problematic.  Support from the OEMs has improved and with 14.04 there is much better support for Intel/ATI hybrids on the way.   But that is not true with 12.04 unless you want to back-port the hardware support stack from Trusty, which would be risky even if you were running a hybrid laptop.  With a desktop there would be no chance at all of that helping.

Your Intel unit may be capable of driving 3 monitors under Windows, but I am not sure that the Linux Intel driver (which you do not have to activate since it is already included in the Linux kernel) will support it.  I don't know enough about Intel's driver to say for sure.

I wish I had better news for you.  I'm sorry.

@frank18 --

Would you please begin a new thread.  Please include in that new thread the details of your GPU arrangement.  Your problem is a different one than the issue bob46 has and will take a different approach.

Best wishes.

---

### Post by bob46 on 2014-02-09
@QIII - thanks for the info, I really appreciate you taking the time to help me out!

Guess I'll have to rethink my approach, good to know.

Again, thanks.

---

