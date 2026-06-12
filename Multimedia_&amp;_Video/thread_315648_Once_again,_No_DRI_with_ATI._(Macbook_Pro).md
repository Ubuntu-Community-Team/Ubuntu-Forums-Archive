---
title: "Once again, No DRI with ATI. (Macbook Pro)"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by emil.s on 2006-12-09
Hello!
I'm sitting here with my new Macbook Pro and try to get DRI work. (for XGL/Beryl). :)

I think i have tried with everything. apt-get install... "./atidriver --buildpkg / --extract".
Copy files manualy, use scripts, etc...

I have tried with the "Mobility radeon driver" (8.29.6), and the "Radeon driver" (8.31.5).

I have tried with everything from this guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But i have still mesa! :(

```
emil@Macbooken: ~ $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

My xorg.conf:
```
emil@Macbooken: ~ $ cat /etc/X11/xorg.conf
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "se"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "Device"                "/dev/input/mice"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. ATI Default Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Color LCD"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. ATI Default Card"
        Monitor         "Color LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "0"
EndSection
```


P.S:
Sorry for my bad english. :cool:

---

### Post by emil.s on 2006-12-12
Please!
No one who know!?

---

### Post by emil.s on 2006-12-14
Now i have more info. :)

I tried with the new 8.32-5. But i get still no DRI. Now i get more errors. :p
```
emil@Macbooken: ~/Desktop $ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

But here i found some (maybe) important information:
```
emil@Macbooken: ~/Desktop $ cat /usr/share/ati/fglrx-install.log
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.19-mactel/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/root/linux-2.6.19'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:89:26: error: linux/config.h: Filen eller katalogen finns inte
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:456: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘firegl_stub_open’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:579: warning: assignment discards qualifiers from pointer target type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_request_irq’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2568: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Fel 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Fel 2
make[1]: Leaving directory `/root/linux-2.6.19'
make: *** [kmod_build] Fel 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.

```
Anyone who know what this is about?

---

### Post by RudolfMDLT on 2006-12-14
Hi there,

Go here, [http://ubuntuforums.org/showthread.php?t=195845](http://ubuntuforums.org/showthread.php?t=195845)

and I'll see if I can help you any further.

Thanks,

Rudolf

---

### Post by emil.s on 2006-12-20
> **RudolfMDLT said:**
> Hi there,

Go here, [http://ubuntuforums.org/showthread.php?t=195845](http://ubuntuforums.org/showthread.php?t=195845)

and I'll see if I can help you any further.

Thanks,

Rudolf
Hello again!
Now i have tried with you guide. But it's no difference:
```
root@Macbooken: /home/emil/Desktop # ln -sf /bin/bash /bin/sh
root@Macbooken: /home/emil/Desktop # bash ./ati-driver-installer-8.32.5-x86.x86_64_Mobility.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/edgy
Package /home/emil/Desktop/xorg-driver-fglrx_8.32.5-1_i386.deb has been successfully generated
Package /home/emil/Desktop/xorg-driver-fglrx-dev_8.32.5-1_i386.deb has been successfully generated
Package /home/emil/Desktop/fglrx-kernel-source_8.32.5-1_i386.deb has been successfully generated
Package /home/emil/Desktop/fglrx-control_8.32.5-1_i386.deb has been successfully generated
Package /home/emil/Desktop/fglrx-sources_8.32.5-1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install
root@Macbooken: /home/emil/Desktop # dpkg -i *.deb
(Läser databasen ... 63557 filer och kataloger installerade.)
Förbereder att ersätta fglrx-control 8.29.6-1 (med fglrx-control_8.32.5-1_i386.deb) ...
Packar upp ersättande fglrx-control ...
Förbereder att ersätta fglrx-kernel-source 8.29.6-1 (med fglrx-kernel-source_8.32.5-1_i386.deb) ...
Packar upp ersättande fglrx-kernel-source ...
Förbereder att ersätta fglrx-sources 8.29.6-1 (med fglrx-sources_8.32.5-1_i386.deb) ...
Packar upp ersättande fglrx-sources ...
Förbereder att ersätta xorg-driver-fglrx 8.29.6-1 (med xorg-driver-fglrx_8.32.5-1_i386.deb) ...
Stopping atieventsd: done.
Packar upp ersättande xorg-driver-fglrx ...
Förbereder att ersätta xorg-driver-fglrx-dev 8.29.6-1 (med xorg-driver-fglrx-dev_8.32.5-1_i386.deb) ...
Packar upp ersättande xorg-driver-fglrx-dev ...
Ställer in fglrx-kernel-source (8.32.5-1) ...
Ställer in fglrx-sources (8.32.5-1) ...
Ställer in xorg-driver-fglrx (8.32.5-1) ...
Starting atieventsd: done.

Ställer in xorg-driver-fglrx-dev (8.32.5-1) ...
Ställer in fglrx-control (8.32.5-1) ...
```

But i get this when i do "module-assistant build,install fglrx":

```
root@Macbooken: /home/emil # module-assistant build,install fglrx
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...

```
And then:
```

       &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; module-assistant, interactive mode &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
       &#9474; Build of the package fglrx-kernel-source failed! How do you   &#9474;
       &#9474; wish to proceed?                                              &#9474;
       &#9474;                                                               &#9474;
       &#9474;       VIEW     Examine the build log file                     &#9474;
       &#9474;       CONTINUE Skip and continue with the next operation      &#9474;
       &#9474;       STOP     Stop processing the build commands             &#9474;
       &#9474;                                                               &#9474;
       &#9474;                                                               &#9474;
       &#9474;                                                               &#9474;
       &#9474;                                                               &#9474;
       &#9474;                <Ok>                    <Avbryt>               &#9474;
       &#9474;                                                               &#9474;
       &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

And the log:
```
      &#9474; dh_testroot                                                                &#8593;
      &#9474; rm -f configure-stamp                                                      &#9646;
      &#9474; rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a                               &#9618;
      &#9474; rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd                        &#9618;
      &#9474; rm -rf .tmp_versions                                                       &#9618;
      &#9474; rm -rf patch                                                               &#9618;
      &#9474; dh_clean                                                                   &#9618;
      &#9474; rm /usr/src/modules/fglrx/debian/control
      &#9474; rm /usr/src/modules/fglrx/debian/dirs                                      &#8593;
      &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           &#9618;
      &#9474;         cat /usr/src/modules/fglrx/debian/control.template >               &#9618;
      &#9474; /usr/src/modules/fglrx/debian/control; \                                   &#9618;
      &#9474;         fi                                                                 &#9618;
      &#9474; if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \                   &#9646;
      &#9474;         mv /usr/src/modules/fglrx/debian/postinst                          &#9618;
      &#9474; /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.19-mactel.postinst; \       &#9618;
      &#9474;         fi                                                                 &#9618;
      &#9474; dh_testdir                                                                 &#9618;
      &#9474; touch configure-stamp                                                      &#9618;
      &#9474; dh_testdir                                                                 &#9618;
      &#9474; /usr/bin/make -C /lib/modules/2.6.19-mactel/source                         &#9618;
      &#9474; SUBDIRS=/usr/src/modules/fglrx modules                                     &#9618;
      &#9474; make[1]: Entering directory `/root/linux-2.6.19'
      &#9474;   CC [M]  /usr/src/modules/fglrx/firegl_public.o                           &#8593;
      &#9474; /usr/src/modules/fglrx/firegl_public.c:89:26: error: linux/config.h:       &#9618;
      &#9474; Filen eller katalogen finns inte                                           &#9618;
      &#9474; /usr/src/modules/fglrx/firegl_public.c:456: warning: initialization from   &#9618;
      &#9474; incompatible pointer type                                                  &#9618;
      &#9474; /usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_stub_open’:    &#9618;
      &#9474; /usr/src/modules/fglrx/firegl_public.c:579: warning: assignment discards   &#9618;
      &#9474; qualifiers from pointer target type                                        &#9618;
      &#9474; /usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_request_irq’:    &#9618;
      &#9474; /usr/src/modules/fglrx/firegl_public.c:2568: warning: passing argument 2   &#9618;
      &#9474; of ‘request_irq’ from incompatible pointer type                            &#9618;
      &#9474; make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Fel 1                &#9618;
      &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Fel 2                        &#9618;
      &#9474; make[1]: Leaving directory `/root/linux-2.6.19'                            &#9646;
      &#9474; make: *** [build] Fel 2

Fel 2 = Error 2
```

---

