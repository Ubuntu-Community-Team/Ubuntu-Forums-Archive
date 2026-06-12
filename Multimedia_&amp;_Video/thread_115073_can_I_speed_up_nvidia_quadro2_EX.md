---
title: "can I speed up nvidia quadro2 EX?"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by Nancy on 2006-01-09
Hi, 

I could use some advice about the graphics on my system. glxgears -printfps => 1000 to 1600 fps on my system. That's slow compared to what others report, I wonder if my configurations are wrong or if that's just what to expect with this card. I just upgraded to Ubuntu from an old version of Redhat. Didn't pay much attention to graphics previously. In between old RH and new Ubuntu, I briefly had the newest version of RH on the machine, and the fps was higher (perhaps 5000) even though that flavor of RH didn't support direct rendering. So it seems better performance than what I have now should be possible. 

This is a Dell Precision 530 Workstation, dual-processor XEON, circa 2002 with nvidia Quadro2 EX, 32MB (that's what the shipping sheet claimed). 

After installing Ubuntu, I followed directions in the forum to install the drivers for nvidia, followed by "sudo nvidia-glx-config enable" and "CTRL-ALT-Backspace" to restart the X Server. Here are the installed packages that seem relevant
    linux-restricted-modules-2.6.12-10-686-smp
    linux-restricted-modules-2.6.12-10-686-smp-nvidia-legacy   
    nvidia-glx-legacy
    nvidia-kernel-common
    nvidia-settings
    xserver-xorg-driver-nv 

Are the legacy drivers the right ones for this? Does anything seem to be configured wrong (more details below)? How to get better performance?

Below is all the related info I know to provide.

$ uname -a
Linux LinuxMay02 2.6.12-10-686-smp #1 SMP Thu Dec 22 12:13:35 UTC 2005 i686 GNU/Linux

$ Per the device manager GUI, pci.product = NV11GL (Quadro2 MXR/EX), pci.product_id = 275(0x113). But under the PCI tab, OEM Product = Unknown (0x0070). 

$ Relevant portions of /etc/X11/xorg.conf:
Section "Module"
        # Load  "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        # Load  "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV11GL [Quadro2 MXR/EX]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL P992"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11GL [Quadro2 MXR/EX]"
        Monitor         "DELL P992"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection


%%%%%%%%%%%%%%%%%%%%%%
$ more /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled


%%%%%%%%%%%%%%%%%%%%%%%%%
This snippet is from /usr/share/doc/nvidia-glx-legacy/README.gz , I've added comments to indicate which files my system doesn't have

If you think there may be something awry
in your installation, check that the following files are in place
(these are all the files of the NVIDIA Accelerated Linux Driver Set,
plus their symlinks):

        /usr/X11R6/lib/modules/drivers/nvidia_drv.o    <= OK, dated  2005-11-22

        /usr/X11R6/lib/modules/extensions/libglx.so.x.y.z   <= OK
        /usr/X11R6/lib/modules/extensions/libglx.so -> libglx.so.x.y.z   <= OK

        /usr/lib/libGL.so.x.y.z     <=  OK, file /usr/lib/libGL.so.1.0.7174  dated 2005-11-22
        /usr/lib/libGL.so.x -> libGL.so.x.y.z  <= OK  
        /usr/lib/libGL.so -> libGL.so.x         <= This link is missing

        /usr/lib/libGLcore.so.x.y.z  <= OK
        /usr/lib/libGLcore.so.x -> libGLcore.so.x.y.z   <= OK

        /lib/modules/`uname -r`/video/nvidia.o, or      <= Don't have, no such video directory
        /lib/modules/`uname -r`/kernel/drivers/video/nvidia.o     <= Don't have, the directory is there but not the file

Installation will also create the /dev files:

        crw-rw-rw-    1 root     root     195,   0 Feb 15 17:21 nvidia0
        crw-rw-rw-    1 root     root     195,   1 Feb 15 17:21 nvidia1   <= Don't have
        crw-rw-rw-    1 root     root     195,   2 Feb 15 17:21 nvidia2   <= Don't have
        crw-rw-rw-    1 root     root     195,   3 Feb 15 17:21 nvidia3   <= Don't have
        crw-rw-rw-    1 root     root     195, 255 Feb 15 17:21 nvidiactl


%%%%%%%%%%%%%%%%%%%%%%%%
$ ldd /usr/bin/glxgears
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7eb1000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e3b000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e11000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7def000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cc1000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c01000)
        libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0xb74b0000)
        libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0xb74ae000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb74a0000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb749d000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb73b7000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb73ac000)
        /lib/ld-linux.so.2 (0xb7f35000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb73a9000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb73a4000)



Thanks for any insight,
Nancy

---

### Post by bannerboy on 2006-01-09
this sounds like what happens to my card when I don't plug in the external power connector. If this is a seperate card, and not built into the motherboard, you should check to see if it has external power plugged in, and if it is built into the motherboard, it may be a problem there. otherwise I would try the latest nVidia drivers, and see if that helps.

---

### Post by Nancy on 2006-01-10
Thanks for the suggestion.  My card doesn't have an external power connector.  As for drivers, I thought this was a legacy card, but now looking more carefully at nvidia's README files, maybe not.  So I'll try the new drivers, thanks.

---

### Post by Nancy on 2006-01-10
Tried the newer drivers, Xserver would not work.  nvidia has conflicting info as to whether my graphics chip is new or old.  Their Readme on page [http://www.nvidia.com/object/linux_display_ia32_1.0-8178.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8178.html) gives Quadro2 MXR/EX/Go as supported, but the link "Supported Products List" on the same page puts the Quadro2 EX into the older devices.  Probably one list was not updated when the Quadro2 EX was made a legacy product.  So I think I must use the legacy drivers, and the fps is still low.  :-(

---

