---
title: "Some 14.04 setup hiccups"
date: 2014-05-20
forum: Mythbuntu
---

### Post by gga96 on 2014-05-20
**My Configuration**
  Mythbuntu 14.04 64 bit
  Linux backend1 3.13.0-24-generic #46-Ubuntu
  Primary BE: HP DC7900
  Remote FE: AsRock Ion 3d 

**Remote Frontend shut down**
  Remote FE exit popup "Yes, Exit and Shutdown" not responding.
  I checked the Primary BE Setup>General>Shutdown/Wakeup>Server halt command = sudo /sbin/halt -p
  Worked fine with same hardware and mythbuntu 12.04 32 bit.

  What can I do to fix this, any polite suggestions?

**FE and BU both with no Volume or Mute control**
  The BE worked out of the box with 12.04 32 bit so what will enable this now?
  The FE uses hdmi to connect to TV. I followed this link:
       [http://www.serkey.com/ubuntu-no-sound-over-hdmi-bd446v.html](http://www.serkey.com/ubuntu-no-sound-over-hdmi-bd446v.html)
  and had total success on 12.04 32 bit but an 14.04 64 bit I get sound but no Volume or Mute control from myth.

  Can anyone help here?

**Software Updater Hangs**
  The Software Updater stops working without a hint of what is wrong. Each time I 
  have tried running it the screen saver after 30 minutes blanks the screen and the dialog is not 
  refreshed on wake up.

  Is this a 14.04 teething pain currently be experienced by others and currently being fixed?

**Mythuntu Control Centre MySQL bug**
  This is a known problem discussed in thread "MythBuntu Control Centre error with MySQL plugin 
  after 14.04 upgrade".

**sudo gedit waring**
  >   
  glen@backend1:~$ sudo gedit /etc/network/interfaces
  [sudo] password for glen: xxx
  (gedit:3202): Gtk-WARNING **: Calling Inhibit failed:
  GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was 
  not provided by any .service files
  
  A guru is needed to fix this one.

---

### Post by blm-ubunet on 2014-05-20
**shutdown:**
- privileged operation
- requires the current mythtv user to be in sudoer's list/file for shutdown cmd.
- current user might not be "mythtv"
- default mythbuntu installs FE user="mythtv"
- BE always runs as user="mythtv"
 
What's the BE server halt commands got to do with remote FE shutdown ?
Are you trying to shutdown BE when idle ?

**Audio volume/mute:**
For volume/mute to work, mythtv must decode all audio (HDA/AC3/DTS/AAC) to discrete PCM.
Then it **can** re-encode to AC3 or just output discrete multi-channel PCM (inc stereo).

If you have a TV but no receiver/HTA then AAC & multi-channel PCM (>2 ch) probably **not** supported.

If you have a HTA/receiver you might have problem with ELD reporting/management.

**Software updater:**
I uninstall software centre & only use synaptic/aptitude/apt-get..
Synaptic has log files & works.
```
sudo apt-get install synaptic
```
use it to indicate broken packages & then re-install them to reconfigure.
Might have to figure out the ONE package causing problem & fix it first..the logs & stdout is helpful.
Might have to wash & rinse multiple times..

**MCC mysql bug:**
you can just edit the offending python file...
```
gksudo gedit <some-file>
```

**Sudo gedit warning:**
Does the command still work?
Does "gksudo gedit" work
Did the synaptic "mark broken packages" & re-installing them help?

After manually upgrading from 12.04LTS to 14.04 had lots of problems with networkmanager/sessionmanager.
I still get one gdbus/freedesktop error:-
> Error: GDBus.Error:org.freedesktop.DBus.Error...
but it is not the same as yours & it seems harmless.
I don't have a solution.
I'm not moving mythtv box until 14.04-LTS upgrade path released.

There are truckloads of updates pouring into 14.04.
You can use:-
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by gga96 on 2014-05-25
**Shutdown:**
As far as I can determine user &#8220;glen&#8221; is the current user and &#8220;glen&#8221; group  includes user &#8220;mythtv&#8221;. But still no shutdown.
 The operation of Applications>System>Users and Groups does not allow  users to be added to a group in this release.
 The only reference to shutdown was found in BE setup. No I am not trying to  shutdown an idle BE, it runs all the time.
  
**Audio volume/mute:**
Thanks for your brief blm-ubunet but my research did not come up with a  fix. It is still not working.  The main reference  was
 [http://www.alsa-project.org/main/index.php/Asoundrc#The_naming_of_PCM_devices](http://www.alsa-project.org/main/index.php/Asoundrc#The_naming_of_PCM_devices) and  some others. At the moment I am only trying to get the BE working. With 12.04  The BE worked as installed and this reference provided a positive fix for  12.04  remote FE hdmi connection, some 12 months ago, but neither  work now.    
  
 **MCC bug:**
Edited [FONT=Times New Roman]/etc/mysql/my.cnf file setting  bind-address to my  static IP.  FE connects to MySQL.[/FONT]
  
 **[FONT=Times New Roman][SIZE=3]Sudo gedit warning:[/SIZE][/FONT]**
[FONT=Times New Roman][SIZE=3]Command worked, edit was saved, the  warning came post exit. [/SIZE][/FONT]
  

 [FONT=Times New Roman][SIZE=3]I am now reluctant to grope about  in the online BE  and remote FE, this release has almost brought on a myth  revolt. It is working with some clunks and bumps.  [/SIZE][/FONT]
  
 [FONT=Times New Roman][SIZE=3]I am now setting up another machine  that I can play and learn on, it should be up by Friday next.  I am not sure  what version of [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]Ubuntu I should  install, this release appears full of unwanted side effects.   [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]How do I know when 14.04-LTS upgrade  path is released?[/SIZE][/FONT]
  
 [FONT=Times New Roman][SIZE=3]Glen[/SIZE][/FONT]

---

### Post by blm-ubunet on 2014-05-25
user glen should be member of mythtv group but not sure it matters for a FE only machine.

I think you need to add user glen into sudoer's file for shutdown without password prompt.
```
man sudoers
```
possibly something like:
```
%glen ALL = NOPASSWD: /sbin/shutdown
```

Are you using nVidia driver ?

```
dmesg | grep -i hda
```
Did you rescan the audio devices in FE setup?
Do you have some old snd_hda_intel driver modprobe hack in /etc/modprobe.d/*.conf file?

0.27+fixes is available for 12.04LTS..just use that.

---

### Post by gga96 on 2014-05-27
**Shutdown:**
Pursuing sudoers led to file ***/etc/sudoers.d/README*** so that and [http://askubuntu.com/questions/192050/how-to-run-sudo-command-with-no-password/443071#443071](http://askubuntu.com/questions/192050/how-to-run-sudo-command-with-no-password/443071#443071) gave  the solution:
  ```

cd /etc/sudoers.d
sudo gedit
```
   Add line to gedit.
   ```

glen ALL = (All) NOPASSWD:ALL
```
Save to any file name of your choice.
  
 **Audio volume/mute:**
No progress.

Using nVidia hdmi on the FE and HDA Intel on the BE. Both boxes have no audio  volume and mute control, video is fine.

BE hda response.
```

glen@backend1:~$ dmesg | grep -i hda
 [   10.900586] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
 [   11.278489] input: HDA Intel Front Headphone as  /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
 [   11.278626] input: HDA Intel Line Out as  /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
 [   11.278720] input: HDA Intel Line as  /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
 [   11.278831] input: HDA Intel Mic as  /devices/pci0000:00/0000:00:1b.0/sound/card0/input14

```

I used rescan in the FE, it did not give any responses.

The list of *.conf files.
```

glen@backend1:~$ ls  /etc/modprobe.d/*.conf
 /etc/modprobe.d/alsa-base.conf                /etc/modprobe.d/blacklist-modem.conf         /etc/modprobe.d/iwlwifi.conf
 /etc/modprobe.d/blacklist-ath_pci.conf       /etc/modprobe.d/blacklist-oss.conf           /etc/modprobe.d/mlx4.conf
 /etc/modprobe.d/blacklist.conf                  /etc/modprobe.d/blacklist-rare-network.conf   /etc/modprobe.d/vmwgfx-fbdev.conf
 /etc/modprobe.d/blacklist-firewire.conf       /etc/modprobe.d/blacklist-watchdog.conf
 /etc/modprobe.d/blacklist-framebuffer.conf   /etc/modprobe.d/fbdev-blacklist.conf

```
 
There common point with this behavior is the 14.04 software release.

 [FONT=Times New Roman][SIZE=3]Glen
[/SIZE][/FONT]

---

### Post by blm-ubunet on 2014-05-27
HDMI HDA
I don't think nouveau driver supports HDMI audio on ION (NVAC). ION is an oddball.
[http://nouveau.freedesktop.org/wiki/FeatureMatrix/](http://nouveau.freedesktop.org/wiki/FeatureMatrix/)
You need to use the nVidia proprietary driver (legacy).

```
cat /var/log/Xorg.0.log
```

Any content of all /etc/modules.d/*.conf file is parsed..
What is in alsa-base.conf ?

Sudoers:
I think your edit of the sudoers file is unsafe; should **not **be recommended.

---

### Post by gga96 on 2014-05-29
**Shutdown:**
Tried “glen ALL = NOPASSWD: /sbin/shutdown” and it did not work.
 Changed it to “glen ALL = NOPASSWD: /sbin/halt”, it worked is this  ok?

 **FE HDMI:**
I do not comprehend the possible involvement of nouveau. I thought the  nVidia driver was being used.
 Synaptic>Additional Drivers output:
> 
NVIDIA Corporation: GT218[ION]
   This device is using the recommended diver.
     NVDIA binary driver – version 331.38 from nvidia-331

The output of  “[FONT=Arial]cat /var/log/Xorg.0.log” is:[/FONT]
> 
glen@frontend1:~$ cat /var/log/Xorg.0.log
[    31.153] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    31.154] X Protocol Version 11, Revision 0
[    31.154] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    31.154] Current Operating System: Linux frontend1 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64
[    31.154] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=6f325286-41d1-4cce-8035-6e61c2dd20dc ro quiet splash
[    31.154] Build Date: 16 April 2014  01:36:29PM
[    31.154] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    31.154] Current version of pixman: 0.30.2
[    31.154]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    31.154] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.155] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 29 10:45:07 2014
[    31.213] (==) Using config file: "/etc/X11/xorg.conf"
[    31.213] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.271] (==) ServerLayout "Layout0"
[    31.271] (**) |-->Screen "Screen0" (0)
[    31.271] (**) |   |-->Monitor "Monitor0"
[    31.272] (**) |   |-->Device "Device0"
[    31.272] (**) |-->Input Device "Keyboard0"
[    31.272] (**) |-->Input Device "Mouse0"
[    31.272] (**) Option "Xinerama" "0"
[    31.272] (==) Automatically adding devices
[    31.272] (==) Automatically enabling devices
[    31.272] (==) Automatically adding GPU devices
[    31.322] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.322]     Entry deleted from font path.
[    31.322] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    31.322]     Entry deleted from font path.
[    31.322] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    31.322]     Entry deleted from font path.
[    31.322] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    31.322]     Entry deleted from font path.
[    31.322] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    31.323]     Entry deleted from font path.
[    31.323] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    31.323] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.323] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    31.323] (WW) Disabling Keyboard0
[    31.323] (WW) Disabling Mouse0
[    31.323] (II) Loader magic: 0x7fc6fe8bfd60
[    31.323] (II) Module ABI versions:
[    31.323]     X.Org ANSI C Emulation: 0.4
[    31.323]     X.Org Video Driver: 15.0
[    31.323]     X.Org XInput driver : 20.0
[    31.323]     X.Org Server Extension : 8.0
[    31.324] (II) xfree86: Adding drm device (/dev/dri/card0)
[    31.327] (--) PCI:*(0:2:0:0) 10de:0a64:1849:0a64 rev 162, Mem @ 0xf7000000/16777216, 0xe0000000/268435456, 0xde000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    31.328] Initializing built-in extension Generic Event Extension
[    31.328] Initializing built-in extension SHAPE
[    31.328] Initializing built-in extension MIT-SHM
[    31.328] Initializing built-in extension XInputExtension
[    31.328] Initializing built-in extension XTEST
[    31.328] Initializing built-in extension BIG-REQUESTS
[    31.328] Initializing built-in extension SYNC
[    31.328] Initializing built-in extension XKEYBOARD
[    31.329] Initializing built-in extension XC-MISC
[    31.329] Initializing built-in extension SECURITY
[    31.329] Initializing built-in extension XINERAMA
[    31.329] Initializing built-in extension XFIXES
[    31.329] Initializing built-in extension RENDER
[    31.329] Initializing built-in extension RANDR
[    31.329] Initializing built-in extension COMPOSITE
[    31.329] Initializing built-in extension DAMAGE
[    31.329] Initializing built-in extension MIT-SCREEN-SAVER
[    31.329] Initializing built-in extension DOUBLE-BUFFER
[    31.329] Initializing built-in extension RECORD
[    31.329] Initializing built-in extension DPMS
[    31.329] Initializing built-in extension Present
[    31.329] Initializing built-in extension DRI3
[    31.329] Initializing built-in extension X-Resource
[    31.329] Initializing built-in extension XVideo
[    31.329] Initializing built-in extension XVideo-MotionCompensation
[    31.329] Initializing built-in extension SELinux
[    31.329] Initializing built-in extension XFree86-VidModeExtension
[    31.330] Initializing built-in extension XFree86-DGA
[    31.330] Initializing built-in extension XFree86-DRI
[    31.330] Initializing built-in extension DRI2
[    31.330] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    31.330] (II) "glx" will be loaded by default.
[    31.330] (WW) "xmir" is not to be loaded by default. Skipping.
[    31.330] (II) LoadModule: "glx"
[    31.351] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    32.032] (II) Module glx: vendor="NVIDIA Corporation"
[    32.032]     compiled for 4.0.2, module version = 1.0.0
[    32.032]     Module class: X.Org Server Extension
[    32.032] (II) NVIDIA GLX Module  331.38  Wed Jan  8 19:10:17 PST 2014
[    32.037] Loading extension GLX
[    32.037] (II) LoadModule: "nvidia"
[    32.037] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    32.135] (II) Module nvidia: vendor="NVIDIA Corporation"
[    32.135]     compiled for 4.0.2, module version = 1.0.0
[    32.135]     Module class: X.Org Video Driver
[    32.147] (II) NVIDIA dlloader X Driver  331.38  Wed Jan  8 18:51:00 PST 2014
[    32.147] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    32.148] (++) using VT number 7

[    32.198] (II) Loading sub module "fb"
[    32.198] (II) LoadModule: "fb"
[    32.267] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.280] (II) Module fb: vendor="X.Org Foundation"
[    32.280]     compiled for 1.15.1, module version = 1.0.0
[    32.281]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.281] (WW) Unresolved symbol: fbGetGCPrivateKey
[    32.281] (II) Loading sub module "wfb"
[    32.281] (II) LoadModule: "wfb"
[    32.282] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    32.287] (II) Module wfb: vendor="X.Org Foundation"
[    32.287]     compiled for 1.15.1, module version = 1.0.0
[    32.287]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.287] (II) Loading sub module "ramdac"
[    32.288] (II) LoadModule: "ramdac"
[    32.288] (II) Module "ramdac" already built-in
[    32.309] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    32.309] (==) NVIDIA(0): RGB weight 888
[    32.309] (==) NVIDIA(0): Default visual is TrueColor
[    32.309] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.309] (**) NVIDIA(0): Option "Stereo" "0"
[    32.310] (**) NVIDIA(0): Option "SLI" "Off"
[    32.310] (**) NVIDIA(0): Option "MultiGPU" "Off"
[    32.310] (**) NVIDIA(0): Option "BaseMosaic" "off"
[    32.310] (**) NVIDIA(0): Stereo disabled by request
[    32.310] (**) NVIDIA(0): NVIDIA SLI disabled.
[    32.310] (**) NVIDIA(0): NVIDIA Multi-GPU disabled.
[    32.310] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    32.310] (**) NVIDIA(0): Enabling 2D acceleration
[    33.288] (II) NVIDIA(0): Display (AOC 2450W (DFP-1)) does not support NVIDIA 3D Vision
[    33.288] (II) NVIDIA(0):     stereo.
[    33.289] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[    33.291] (II) NVIDIA(0): NVIDIA GPU ION (GT218) at PCI:2:0:0 (GPU-0)
[    33.291] (--) NVIDIA(0): Memory: 524288 kBytes
[    33.291] (--) NVIDIA(0): VideoBIOS: 70.18.5a.00.19
[    33.291] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    33.293] (--) NVIDIA(0): Valid display device(s) on ION at PCI:2:0:0
[    33.294] (--) NVIDIA(0):     CRT-0
[    33.294] (--) NVIDIA(0):     DFP-0
[    33.294] (--) NVIDIA(0):     AOC 2450W (DFP-1) (boot, connected)
[    33.294] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    33.294] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    33.294] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    33.294] (--) NVIDIA(0): AOC 2450W (DFP-1): Internal Single Link TMDS
[    33.294] (--) NVIDIA(0): AOC 2450W (DFP-1): 165.0 MHz maximum pixel clock
[    33.294] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    33.294] (**) NVIDIA(0):     device AOC 2450W (DFP-1) (Using EDID frequencies has been
[    33.294] (**) NVIDIA(0):     enabled on all display devices.)
[    33.297] (WW) NVIDIA(GPU-0): The EDID for AOC 2450W (DFP-1) contradicts itself: mode
[    33.297] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    33.297] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-83.000 kHz) would exclude
[    33.297] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    33.297] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    33.310] (II) NVIDIA(0): Validated MetaModes:
[    33.310] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    33.310] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    33.370] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    33.370] (--) NVIDIA(0):     option
[    33.370] (--) Depth 24 pixmap format is 32 bpp
[    33.370] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    33.380] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    33.511] Loading extension NV-GLX
[    33.556] (==) NVIDIA(0): Disabling shared memory pixmaps
[    33.556] (==) NVIDIA(0): Backing store enabled
[    33.556] (==) NVIDIA(0): Silken mouse enabled
[    33.558] (**) NVIDIA(0): DPMS enabled
[    33.558] Loading extension NV-CONTROL
[    33.559] Loading extension XINERAMA
[    33.559] (II) Loading sub module "dri2"
[    33.560] (II) LoadModule: "dri2"
[    33.560] (II) Module "dri2" already built-in
[    33.560] (II) NVIDIA(0): [DRI2] Setup complete
[    33.560] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    33.560] (--) RandR disabled
[    33.577] (II) SELinux: Disabled on system
[    33.580] (II) Initializing extension GLX
[    33.838] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.861] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.861] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.861] (II) LoadModule: "evdev"
[    33.862] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.902] (II) Module evdev: vendor="X.Org Foundation"
[    33.902]     compiled for 1.15.0, module version = 2.8.2
[    33.902]     Module class: X.Org XInput Driver
[    33.902]     ABI class: X.Org XInput driver, version 20.0
[    33.902] (II) Using input driver 'evdev' for 'Power Button'
[    33.902] (**) Power Button: always reports core events
[    33.902] (**) evdev: Power Button: Device: "/dev/input/event1"
[    33.903] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.903] (--) evdev: Power Button: Found keys
[    33.903] (II) evdev: Power Button: Configuring as keyboard
[    33.903] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    33.903] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.903] (**) Option "xkb_rules" "evdev"
[    33.903] (**) Option "xkb_model" "pc105"
[    33.903] (**) Option "xkb_layout" "us"
[    33.905] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    33.905] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.905] (II) Using input driver 'evdev' for 'Power Button'
[    33.905] (**) Power Button: always reports core events
[    33.905] (**) evdev: Power Button: Device: "/dev/input/event0"
[    33.905] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.905] (--) evdev: Power Button: Found keys
[    33.905] (II) evdev: Power Button: Configuring as keyboard
[    33.906] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    33.906] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    33.906] (**) Option "xkb_rules" "evdev"
[    33.906] (**) Option "xkb_model" "pc105"
[    33.906] (**) Option "xkb_layout" "us"
[    33.908] (II) config/udev: Adding input device         USB Receiver (/dev/input/event2)
[    33.908] (**)         USB Receiver: Applying InputClass "evdev keyboard catchall"
[    33.908] (II) Using input driver 'evdev' for '        USB Receiver'
[    33.908] (**)         USB Receiver: always reports core events
[    33.908] (**) evdev:         USB Receiver: Device: "/dev/input/event2"
[    33.908] (--) evdev:         USB Receiver: Vendor 0x5af Product 0x3062
[    33.908] (--) evdev:         USB Receiver: Found keys
[    33.908] (II) evdev:         USB Receiver: Configuring as keyboard
[    33.908] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input5/event2"
[    33.908] (II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD, id 8)
[    33.909] (**) Option "xkb_rules" "evdev"
[    33.909] (**) Option "xkb_model" "pc105"
[    33.909] (**) Option "xkb_layout" "us"
[    33.911] (II) config/udev: Adding input device         USB Receiver (/dev/input/event3)
[    33.911] (**)         USB Receiver: Applying InputClass "evdev pointer catchall"
[    33.911] (**)         USB Receiver: Applying InputClass "evdev keyboard catchall"
[    33.911] (II) Using input driver 'evdev' for '        USB Receiver'
[    33.911] (**)         USB Receiver: always reports core events
[    33.911] (**) evdev:         USB Receiver: Device: "/dev/input/event3"
[    33.911] (--) evdev:         USB Receiver: Vendor 0x5af Product 0x3062
[    33.911] (--) evdev:         USB Receiver: Found 9 mouse buttons
[    33.911] (--) evdev:         USB Receiver: Found scroll wheel(s)
[    33.911] (--) evdev:         USB Receiver: Found relative axes
[    33.911] (--) evdev:         USB Receiver: Found x and y relative axes
[    33.911] (--) evdev:         USB Receiver: Found keys
[    33.911] (II) evdev:         USB Receiver: Configuring as mouse
[    33.911] (II) evdev:         USB Receiver: Configuring as keyboard
[    33.911] (II) evdev:         USB Receiver: Adding scrollwheel support
[    33.911] (**) evdev:         USB Receiver: YAxisMapping: buttons 4 and 5
[    33.911] (**) evdev:         USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.912] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input6/event3"
[    33.912] (II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD, id 9)
[    33.912] (**) Option "xkb_rules" "evdev"
[    33.912] (**) Option "xkb_model" "pc105"
[    33.912] (**) Option "xkb_layout" "us"
[    33.913] (II) evdev:         USB Receiver: initialized for relative axes.
[    33.914] (**)         USB Receiver: (accel) keeping acceleration scheme 1
[    33.914] (**)         USB Receiver: (accel) acceleration profile 0
[    33.914] (**)         USB Receiver: (accel) acceleration factor: 2.000
[    33.914] (**)         USB Receiver: (accel) acceleration threshold: 4
[    33.915] (II) config/udev: Adding input device         USB Receiver (/dev/input/mouse0)
[    33.915] (II) No input driver specified, ignoring this device.
[    33.915] (II) This device may have been added with another device file.
[    33.916] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event14)
[    33.916] (II) No input driver specified, ignoring this device.
[    33.916] (II) This device may have been added with another device file.
[    33.917] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event13)
[    33.917] (II) No input driver specified, ignoring this device.
[    33.917] (II) This device may have been added with another device file.
[    33.918] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event12)
[    33.918] (II) No input driver specified, ignoring this device.
[    33.918] (II) This device may have been added with another device file.
[    33.919] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event11)
[    33.919] (II) No input driver specified, ignoring this device.
[    33.919] (II) This device may have been added with another device file.
[    33.920] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event10)
[    33.921] (II) No input driver specified, ignoring this device.
[    33.921] (II) This device may have been added with another device file.
[    33.921] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event9)
[    33.922] (II) No input driver specified, ignoring this device.
[    33.922] (II) This device may have been added with another device file.
[    33.923] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event8)
[    33.923] (II) No input driver specified, ignoring this device.
[    33.923] (II) This device may have been added with another device file.
[    33.923] (II) config/udev: Adding drm device (/dev/dri/card0)
[    33.923] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    33.924] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event18)
[    33.925] (II) No input driver specified, ignoring this device.
[    33.925] (II) This device may have been added with another device file.
[    33.926] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event17)
[    33.926] (II) No input driver specified, ignoring this device.
[    33.926] (II) This device may have been added with another device file.
[    33.927] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event16)
[    33.927] (II) No input driver specified, ignoring this device.
[    33.928] (II) This device may have been added with another device file.
[    33.929] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event15)
[    33.929] (II) No input driver specified, ignoring this device.
[    33.929] (II) This device may have been added with another device file.
[    33.930] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event4)
[    33.930] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[    33.930] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[    33.930] (**) USB USB Keykoard: always reports core events
[    33.930] (**) evdev: USB USB Keykoard: Device: "/dev/input/event4"
[    33.930] (--) evdev: USB USB Keykoard: Vendor 0x1c4f Product 0x2
[    33.930] (--) evdev: USB USB Keykoard: Found keys
[    33.930] (II) evdev: USB USB Keykoard: Configuring as keyboard
[    33.931] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/input/input7/event4"
[    33.931] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 10)
[    33.931] (**) Option "xkb_rules" "evdev"
[    33.931] (**) Option "xkb_model" "pc105"
[    33.931] (**) Option "xkb_layout" "us"
[    33.933] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event5)
[    33.933] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[    33.933] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[    33.933] (**) USB USB Keykoard: always reports core events
[    33.933] (**) evdev: USB USB Keykoard: Device: "/dev/input/event5"
[    33.933] (--) evdev: USB USB Keykoard: Vendor 0x1c4f Product 0x2
[    33.933] (--) evdev: USB USB Keykoard: Found 1 mouse buttons
[    33.933] (--) evdev: USB USB Keykoard: Found scroll wheel(s)
[    33.933] (--) evdev: USB USB Keykoard: Found relative axes
[    33.933] (II) evdev: USB USB Keykoard: Forcing relative x/y axes to exist.
[    33.933] (--) evdev: USB USB Keykoard: Found absolute axes
[    33.934] (II) evdev: USB USB Keykoard: Forcing absolute x/y axes to exist.
[    33.934] (--) evdev: USB USB Keykoard: Found keys
[    33.934] (II) evdev: USB USB Keykoard: Configuring as mouse
[    33.934] (II) evdev: USB USB Keykoard: Configuring as keyboard
[    33.934] (II) evdev: USB USB Keykoard: Adding scrollwheel support
[    33.934] (**) evdev: USB USB Keykoard: YAxisMapping: buttons 4 and 5
[    33.934] (**) evdev: USB USB Keykoard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.934] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.1/input/input8/event5"
[    33.934] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 11)
[    33.934] (**) Option "xkb_rules" "evdev"
[    33.934] (**) Option "xkb_model" "pc105"
[    33.934] (**) Option "xkb_layout" "us"
[    33.935] (II) evdev: USB USB Keykoard: initialized for relative axes.
[    33.935] (WW) evdev: USB USB Keykoard: ignoring absolute axes.
[    33.935] (**) USB USB Keykoard: (accel) keeping acceleration scheme 1
[    33.935] (**) USB USB Keykoard: (accel) acceleration profile 0
[    33.935] (**) USB USB Keykoard: (accel) acceleration factor: 2.000
[    33.936] (**) USB USB Keykoard: (accel) acceleration threshold: 4
[    33.943] (II) config/udev: Adding input device Nuvoton w836x7hg Infrared Remote Transceiver (/dev/input/event6)
[    33.944] (**) Nuvoton w836x7hg Infrared Remote Transceiver: Applying InputClass "evdev keyboard catchall"
[    33.944] (II) Using input driver 'evdev' for 'Nuvoton w836x7hg Infrared Remote Transceiver'
[    33.944] (**) Nuvoton w836x7hg Infrared Remote Transceiver: always reports core events
[    33.944] (**) evdev: Nuvoton w836x7hg Infrared Remote Transceiver: Device: "/dev/input/event6"
[    33.944] (--) evdev: Nuvoton w836x7hg Infrared Remote Transceiver: Vendor 0x1050 Product 0xb4
[    33.944] (--) evdev: Nuvoton w836x7hg Infrared Remote Transceiver: Found keys
[    33.944] (II) evdev: Nuvoton w836x7hg Infrared Remote Transceiver: Configuring as keyboard
[    33.944] (**) Option "config_info" "udev:/sys/devices/pnp0/00:05/rc/rc0/input9/event6"
[    33.944] (II) XINPUT: Adding extended input device "Nuvoton w836x7hg Infrared Remote Transceiver" (type: KEYBOARD, id 12)
[    33.944] (**) Option "xkb_rules" "evdev"
[    33.944] (**) Option "xkb_model" "pc105"
[    33.944] (**) Option "xkb_layout" "us"
[    33.946] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (nuvoton-cir) (/dev/input/event7)
[    33.946] (**) MCE IR Keyboard/Mouse (nuvoton-cir): Applying InputClass "evdev pointer catchall"
[    33.946] (**) MCE IR Keyboard/Mouse (nuvoton-cir): Applying InputClass "evdev keyboard catchall"
[    33.946] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (nuvoton-cir)'
[    33.946] (**) MCE IR Keyboard/Mouse (nuvoton-cir): always reports core events
[    33.946] (**) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Device: "/dev/input/event7"
[    33.946] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Vendor 0 Product 0
[    33.946] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Found 3 mouse buttons
[    33.946] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Found relative axes
[    33.947] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Found x and y relative axes
[    33.947] (--) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Found keys
[    33.947] (II) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Configuring as mouse
[    33.947] (II) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): Configuring as keyboard
[    33.947] (**) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): YAxisMapping: buttons 4 and 5
[    33.947] (**) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.947] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event7"
[    33.947] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (nuvoton-cir)" (type: KEYBOARD, id 13)
[    33.947] (**) Option "xkb_rules" "evdev"
[    33.947] (**) Option "xkb_model" "pc105"
[    33.947] (**) Option "xkb_layout" "us"
[    33.948] (II) evdev: MCE IR Keyboard/Mouse (nuvoton-cir): initialized for relative axes.
[    33.948] (**) MCE IR Keyboard/Mouse (nuvoton-cir): (accel) keeping acceleration scheme 1
[    33.948] (**) MCE IR Keyboard/Mouse (nuvoton-cir): (accel) acceleration profile 0
[    33.948] (**) MCE IR Keyboard/Mouse (nuvoton-cir): (accel) acceleration factor: 2.000
[    33.949] (**) MCE IR Keyboard/Mouse (nuvoton-cir): (accel) acceleration threshold: 4
[    33.949] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (nuvoton-cir) (/dev/input/mouse1)
[    33.950] (II) No input driver specified, ignoring this device.
[    33.950] (II) This device may have been added with another device file.
[    40.309] (II) NVIDIA(GPU-0): Display (AOC 2450W (DFP-1)) does not support NVIDIA 3D Vision
[    40.341] (II) NVIDIA(GPU-0):     stereo.
[    44.809] (II) NVIDIA(GPU-0): Display (AOC 2450W (DFP-1)) does not support NVIDIA 3D Vision
[    44.809] (II) NVIDIA(GPU-0):     stereo.
[    44.841] (II) NVIDIA(GPU-0): Display (AOC 2450W (DFP-1)) does not support NVIDIA 3D Vision
[    44.841] (II) NVIDIA(GPU-0):     stereo.
[    62.693] (II) NVIDIA(GPU-0): Display (AOC 2450W (DFP-1)) does not support NVIDIA 3D Vision
[    62.693] (II) NVIDIA(GPU-0):     stereo.
[    62.725] (II) NVIDIA(GPU-0): Display (AOC 2450W (DFP-1)) does not support NVIDIA 3D Vision
[    62.725] (II) NVIDIA(GPU-0):     stereo.

The content o  alsa-base.conf:
> 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2


---

### Post by blm-ubunet on 2014-05-29
With ION2 you should have on-board chipset audio codec & GPU HDA codec.
You might be right about the 14.04 problems.

aplay -l
I believe the later alsa code enumerates differently but try:
speaker-test -l 1 -c 2 -D hw:1,3 -r 44100
speaker-test -l 1 -c 2 -D hw:1,7 -r 44100
speaker-test -l 1 -c 2 -D hw:1,8 -r 44100
speaker-test -l 1 -c 2 -D hw:1,9 -r 44100

Then try:
speaker-test -l 1 -c 2 -D hw:1,0 -r 48000
speaker-test -l 1 -c 2 -D hw:1,1 -r 48000
speaker-test -l 1 -c 2 -D hw:1,2 -r 48000

If this cmd complains about missing card 1 then just stop.

Possibly, there are alsa backport modules that could try next..

---

### Post by gga96 on 2014-05-29
Tested all 4 but only **speaker-test -l 1 -c 2 -D hw:1,7 -r 44100** produced sound.
**speaker-test -l 1 -c 2 -D hw:1,0 -r 48000** complained.
It also worked with **speaker-test -l 1 -c 2 -D hw:1,7 -r 48000.**

---

### Post by blm-ubunet on 2014-05-29
I'm leading you wrong here (previous)...

Your HDMI audio works fine ?
Just volume & mute do not work ?

There is 3 methods to control volume over HDMI
1. MythTV decode to PCM & then scale then output discrete PCM (if supported) or re-encode
2. let alsa or pulseaudio do the same as above
3. CEC adaptor control - volume & mute is done on the target TV or HT Amp.

You probably just need to enable the (MythTV) volume control & possibly set the audio output type/capabilites.

---

### Post by gga96 on 2014-05-29
[SIZE=2][FONT=arial]To clarify, I  have 2 hardware setups that suffer a common problem following a vanilla 14.04   mythbuntu installation.
 Hardware 1:> HP DC7900 with HDA Intel,  used as BE and with local FE.
 Hardware 2:> AsRock Ion 3D with HDA  Nvidia, used as remote FE and attacked to TV by a HDMI cable.
 Common Problem:>  There is no FE Volume  control or FE Mute control on either system.
 Note:> Both  systems Video and Audio work fine.
  
 BE local FE Audio Setup:
> 
Audio output device: ALSA:default
Use internal volume control: Checked
 Mixer device: ALSA:default
 Mixer controls: PCM[SIZE=2][FONT=arial]
 [/FONT][/SIZE]Remote FE Audio Setup:
 > 
Audio output device: ALSA:hdmi_complete
 Use internal volume control: Checked
 Mixer device: ALSA:default
 Mixer controls: hdmi_volume[/FONT][/SIZE][SIZE=2][FONT=arial]

[/FONT][/SIZE]

---

### Post by SMANN on 2014-05-30
For what it's worth, I'm having largely the same issues with a clean install.  Asus M2NPV-VM board w/ Nvidia 6150 integrated running as a dedicated frontend.  Everything was working great w/ 12.04.
-Mute/Volume controls have no effect.
-Shutdown/Reboot from on-screen menu have no effect.

There also a variety of other issues but just wanted to let gga96 know this isn't some isolated thing.

---

### Post by blm-ubunet on 2014-05-30
For what it is worth.. volume & mute works fine with master 0.28 on ubuntu 10.04-LTS.
Audio setup is similar to your BE (after changing from IEC958 to default audio device)

Is there any info in frontend logs when you change audio setup &/or attempt volume change?
Restart FE with more logging:
```
mythfrontend.real -v audio --loglevel=debug

```

Is your FE user a member of the audio group?
```
groups
```
alsa permissions have caused problems with mythtv's audio buffer size requests for years..

---

### Post by gga96 on 2014-05-30
? The same code setup on BE, FE worked for 12 months with 12.04  and same HW! ?

FE log follows:  
See "ALSA: no playback control hdmi_volume found on mixer device default".
```

glen@frontend1:~$ mythfrontend.real -v audio --loglevel=debug
2014-05-31 08:17:11.168523 I  Setup Interrupt handler
2014-05-31 08:17:11.168613 I  Setup Terminated handler
2014-05-31 08:17:11.168651 I  Setup Segmentation fault handler
2014-05-31 08:17:11.168689 I  Setup Aborted handler
2014-05-31 08:17:11.168726 I  Setup Bus error handler
2014-05-31 08:17:11.168765 I  Setup Floating point exception handler
2014-05-31 08:17:11.168803 I  Setup Illegal instruction handler
2014-05-31 08:17:11.168844 I  Setup Real-time signal 0 handler
2014-05-31 08:17:11.168886 I  Setup User defined signal 1 handler
2014-05-31 08:17:11.168924 I  Setup User defined signal 2 handler
2014-05-31 08:17:11.169351 C  mythfrontend version: fixes/0.27 [v0.27.1-4-g81c77ba] www.mythtv.org
2014-05-31 08:17:11.169381 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2014-05-31 08:17:11.169410 N  Enabled verbose msgs:  general audio
2014-05-31 08:17:11.169457 N  Setting Log Level to LOG_DEBUG
2014-05-31 08:17:11.181309 N  Using runtime prefix = /usr
2014-05-31 08:17:11.181485 I  Added logging to the console
2014-05-31 08:17:11.181361 N  Using configuration directory = /home/glen/.mythtv
2014-05-31 08:17:11.181771 I  Assumed character encoding: en_AU.UTF-8
2014-05-31 08:17:11.183088 N  Empty LocalHostName.
2014-05-31 08:17:11.183126 I  Using localhost value of frontend1
2014-05-31 08:17:11.183242 I  Testing network connectivity to '192.168.1.3'
2014-05-31 08:17:11.185281 I  Starting process manager
2014-05-31 08:17:11.185677 I  Starting process signal handler
2014-05-31 08:17:11.185830 I  Starting IO manager (read)
2014-05-31 08:17:11.190148 I  Starting IO manager (write)
2014-05-31 08:17:11.289125 I  New Client:  (#1)
2014-05-31 08:17:11.346104 D  FindDatabase() - Success!
2014-05-31 08:17:11.357005 N  Setting QT default locale to en_AU
2014-05-31 08:17:11.357187 I  Current locale en_AU
2014-05-31 08:17:11.357350 E  No locale defaults file for en_AU, skipping
2014-05-31 08:17:11.486702 I  ScreenSaverX11Private: XScreenSaver support enabled
2014-05-31 08:17:11.488911 I  ScreenSaverX11Private: DPMS is disabled.
2014-05-31 08:17:11.532230 N  Desktop video mode: 1920x1080 60.000 Hz
2014-05-31 08:17:11.688091 D  Adding IPv4 loopback to address list.
2014-05-31 08:17:11.688146 D  Adding IPv6 loopback to address list.
2014-05-31 08:17:11.688276 D  Adding '192.168.1.4' to address list.
2014-05-31 08:17:11.688367 D  Adding link-local 'FE80::BE5F:F4FF:FE8E:7558%eth0' to address list.
2014-05-31 08:17:11.688875 I  Listening on TCP 127.0.0.1:6547
2014-05-31 08:17:11.689175 I  Listening on TCP 192.168.1.4:6547
2014-05-31 08:17:11.689591 I  Listening on TCP [::1]:6547
2014-05-31 08:17:11.689890 I  Listening on TCP [fe80::be5f:f4ff:fe8e:7558%eth0]:6547
2014-05-31 08:17:12.604841 D  MMulticastSocketDevice(:25): setsockopt - IP_MULTICAST_IF 
            eno: Cannot assign requested address (99)
2014-05-31 08:17:12.654622 D  MMulticastSocketDevice(:25): setsockopt - IP_MULTICAST_IF 
            eno: Cannot assign requested address (99)
2014-05-31 08:17:12.690725 I  Loading en_us translation for module mythfrontend
2014-05-31 08:17:12.718207 E  LIRC: Failed to connect to Unix socket '/etc/lirc/lircd'
            eno: No such file or directory (2)
2014-05-31 08:17:12.718360 E  JoystickMenuThread: Joystick disabled - Failed to read /home/glen/.mythtv/joystickmenurc
2014-05-31 08:17:12.718376 I  UDPListener: Enabling
2014-05-31 08:17:12.720570 I  Binding to UDP 127.0.0.1:6948
2014-05-31 08:17:12.720738 I  Binding to UDP 192.168.1.4:6948
2014-05-31 08:17:12.720962 I  Binding to UDP [::1]:6948
2014-05-31 08:17:12.721195 I  Binding to UDP [fe80::be5f:f4ff:fe8e:7558%eth0]:6948
2014-05-31 08:17:12.721474 I  Binding to UDP 192.168.1.255:6948
2014-05-31 08:17:12.850332 I  Using Frameless Window
2014-05-31 08:17:12.850366 I  Using Full Screen Window
2014-05-31 08:17:13.256950 I  Trying the OpenGL painter
2014-05-31 08:17:13.303618 I  OpenGL: Sync to VBlank is enabled (good!)
2014-05-31 08:17:13.463100 D  OpenGL: Extension not found: glGenFencesAPPLE
2014-05-31 08:17:13.463155 D  OpenGL: Extension not found: glDeleteFencesAPPLE
2014-05-31 08:17:13.463200 D  OpenGL: Extension not found: glSetFenceAPPLE
2014-05-31 08:17:13.463246 D  OpenGL: Extension not found: glFinishFenceAPPLE
2014-05-31 08:17:13.463750 I  OpenGL1: Fragment program support available
2014-05-31 08:17:13.463903 I  OpenGL: OpenGL vendor  : NVIDIA Corporation
2014-05-31 08:17:13.463920 I  OpenGL: OpenGL renderer: ION/PCIe/SSE2
2014-05-31 08:17:13.463934 I  OpenGL: OpenGL version : 3.3.0 NVIDIA 331.38
2014-05-31 08:17:13.463955 I  OpenGL: Max texture size: 8192 x 8192
2014-05-31 08:17:13.463970 I  OpenGL: Max texture units: 4
2014-05-31 08:17:13.463985 I  OpenGL: Direct rendering: Yes
2014-05-31 08:17:13.463998 I  OpenGL: PixelBufferObject support available
2014-05-31 08:17:13.464010 I  OpenGL: Initialised MythRenderOpenGL
2014-05-31 08:17:13.890775 D  Copying DLManager's Cookie Jar
2014-05-31 08:17:13.951499 D  MythCookieJar: loading cookies from: /home/glen/.mythtv/MythBrowser/cookiejar.txt
2014-05-31 08:17:13.959493 I  MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
2014-05-31 08:17:13.960651 E  MythUIWebBrowser: failed to find our parent screen
2014-05-31 08:17:13.964462 I  MythUIWebBrowser: enabling plugins
2014-05-31 08:17:14.021917 I  MythCoreContext: Connecting to backend server: 192.168.1.3:6543 (try 1 of 1)
2014-05-31 08:17:14.034664 I  Using protocol version 77
2014-05-31 08:17:14.177118 E  RAOP Device: Aborting startup - no key found.
2014-05-31 08:17:14.179491 I  AirPlay: Created airplay objects.
2014-05-31 08:17:14.180224 I  Listening on TCP 127.0.0.1:5100
2014-05-31 08:17:14.180497 I  Listening on TCP 192.168.1.4:5100
2014-05-31 08:17:14.180811 I  Listening on TCP [::1]:5100
2014-05-31 08:17:14.181148 I  Listening on TCP [fe80::be5f:f4ff:fe8e:7558%eth0]:5100
2014-05-31 08:17:14.192746 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-05-31 08:17:14.356095 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2014-05-31 08:17:14.356127 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2014-05-31 08:17:14.357875 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2014-05-31 08:17:14.357910 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2014-05-31 08:17:14.999753 N  Registering Internal as a media playback plugin.
2014-05-31 08:17:15.009059 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:15.104725 I  Bonjour: Service registration complete: name 'MythTV on frontend1' type '_airplay._tcp.' domain: 'local.'
2014-05-31 08:17:15.511226 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:16.013284 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:16.515265 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:17.017286 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:17.519280 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:18.021317 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:18.523355 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:19.025439 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:19.527396 A  MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
2014-05-31 08:17:20.029291 W  No plugins directory /usr/lib/mythtv/plugins
2014-05-31 08:17:20.248594 N  Found mainmenu.xml for theme 'MythCenter-wide'
2014-05-31 08:17:20.276403 I  Registering HouseKeeperTask 'HardwareProfiler'.
2014-05-31 08:17:20.282201 I  Starting HouseKeeper.
2014-05-31 08:17:20.747229 I  Bonjour: Service registration complete: name 'Mythfrontend on frontend1' type '_mythfrontend._tcp.' domain: 'local.'
2014-05-31 08:17:22.728564 D  SendReceiveStringList(QUERY_HOSTNAME) called from UI thread
2014-05-31 08:17:27.231386 I  TV: Creating TV object
2014-05-31 08:17:27.286702 N  Suspending idle timer
2014-05-31 08:17:27.299777 I  TV: Created TvPlayWindow.
2014-05-31 08:17:27.318111 I  TV: Attempting to change from None to WatchingPreRecorded
2014-05-31 08:17:27.328015 D  SendReceiveStringList(QUERY_CHECKFILE,0...) called from UI thread
2014-05-31 08:17:27.329537 D  SendReceiveStringList(QUERY_FILE_EXISTS,1062_20140530103000.mpg) called from UI thread
2014-05-31 08:17:27.587140 I  Pulse: Created PulseHandler object
2014-05-31 08:17:27.590140 I  Pulse: Callback: State changed Unconnected->Connecting
2014-05-31 08:17:27.590658 I  Pulse: Callback: State changed Connecting->Authorizing
2014-05-31 08:17:27.642096 I  Pulse: Callback: State changed Authorizing->Setting Name
2014-05-31 08:17:27.682668 I  Pulse: Callback: State changed Setting Name->Ready!
2014-05-31 08:17:27.692774 I  Pulse: Initialised handler
2014-05-31 08:17:27.713466 I  Pulse: Operation: success 1 remaining 1
2014-05-31 08:17:27.733809 I  Pulse: Operation: success 1 remaining 0
2014-05-31 08:17:27.743914 I  Pulse: PulseAudio suspend OK
2014-05-31 08:17:27.756491 I  ALSA: OpenDevice hdmi_complete
2014-05-31 08:17:27.757777 I  AOS: Sample rate 48000 is supported
2014-05-31 08:17:27.757838 I  AOS: Format signed 16 bit is supported
2014-05-31 08:17:27.757946 I  AOS: 2 channel(s) are supported
2014-05-31 08:17:27.758624 I  ALSA: Successfully retrieved ELD data
2014-05-31 08:17:27.758740 I  ELDUTILS: Detected monitor 2450W at connection type HDMI
2014-05-31 08:17:27.758765 I  ELDUTILS: available speakers: FL/FR
2014-05-31 08:17:27.758788 I  ELDUTILS: max LPCM channels = 2
2014-05-31 08:17:27.758808 I  ELDUTILS: max channels = 2
2014-05-31 08:17:27.758827 I  ELDUTILS: supported codecs = LPCM
2014-05-31 08:17:27.758878 I  ELDUTILS: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16
2014-05-31 08:17:27.878278 I  AOS: may be AC3 or DTS capable
2014-05-31 08:17:27.878333 I  AOS: 6 channel(s) are supported
2014-05-31 08:17:27.883390 N  AudioPlayer: Enabling Audio
2014-05-31 08:17:28.404896 I  AFD: codec MP2 has 2 channels
2014-05-31 08:17:28.405134 I  AFD: Opened codec 0x5510f60, id(MP2) type(Audio)
2014-05-31 08:17:28.405802 I  AFD: Audio Track #1, of type (Normal) is A/V stream #1 (id=0xe8a) and has 2 channels in the English language(6647399).
2014-05-31 08:17:28.462952 I  VDPAU: Version 1
2014-05-31 08:17:28.462985 I  VDPAU: Information NVIDIA VDPAU Driver Shared Library  331.38  Wed Jan  8 19:13:15 PST 2014
2014-05-31 08:17:28.480238 I  AFD: Opened codec 0x5679360, id(MPEG2VIDEO) type(Video)
2014-05-31 08:17:28.496246 I  AFD: Selected track 1: English MP2 2ch (A/V Stream #1)
2014-05-31 08:17:28.496325 I  AFD: Audio data is planar
2014-05-31 08:17:28.496382 I  AFD: Initializing audio parms from audio track #1
2014-05-31 08:17:28.496441 I  AFD: Audio format changed 
            from id(NONE)     -1Hz -1ch -1bps     (profile 0) to id( MP2)  48000Hz  2ch 16bps     (profile 0)
2014-05-31 08:17:28.496504 I  AOBase: Killing AudioOutputDSP
2014-05-31 08:17:28.496552 I  AOBase: Original codec was MP2, signed 16 bit, 48 kHz, 2 channels
2014-05-31 08:17:28.496593 I  AOBase: enc(0), passthru(0), features () configured_channels(2), 2 channels supported(1) max_channels(2)
2014-05-31 08:17:28.496639 I  AOBase: Opening audio device 'hdmi_complete' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2014-05-31 08:17:28.496657 I  ALSA: OpenDevice hdmi_complete
2014-05-31 08:17:28.505097 I  ALSA: SetParameters(format=2, channels=2, rate=48000, buffer_time=500000, period_time=4)
2014-05-31 08:17:28.505903 I  ALSA: Buffer size range from 64 to 16384
2014-05-31 08:17:28.505928 I  ALSA: Period size range from 32 to 8192
2014-05-31 08:17:28.506092 E  ALSA: Requested 500000us got 341333 buffer time
2014-05-31 08:17:28.506365 I  ALSA: Hardware audio buffer cur: 64 need: 128 max allowed: 32768
2014-05-31 08:17:28.506474 E  ALSA: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card1/pcm7p/sub0/prealloc
2014-05-31 08:17:28.506515 I  ALSA: Buffer time = 341333 us
2014-05-31 08:17:28.506800 I  ALSA: Period time = 4 periods
2014-05-31 08:17:28.609327 I  ALSA: Buffer size = 16384 | Period size = 4096
2014-05-31 08:17:28.748536 E  ALSA: no playback control hdmi_volume found on mixer device default
2014-05-31 08:17:28.748563 E  ALSA: Unable to open audio mixer. Volume control disabled
2014-05-31 08:17:28.748604 I  AOBase: Audio fragment size: 8192
2014-05-31 08:17:28.748649 I  AOBase: Audio Stretch Factor: 1
2014-05-31 08:17:28.748753 I  AOBase: Ending Reconfigure()
2014-05-31 08:17:28.749145 I  AOBase: kickoffOutputAudioLoop: pid = 1815
2014-05-31 08:17:28.749255 I  AOBase: OutputAudioLoop: Play Event
2014-05-31 08:17:29.539345 I  Clearing OpenGL painter cache.
2014-05-31 08:17:29.728943 I  VDPAU: Created 2 output surfaces.
2014-05-31 08:17:29.729044 I  VDPAU: Created VDPAU render device 1920x1080
2014-05-31 08:17:29.804144 N  Player(0): Forcing decode extra audio option on (Video method requires it).
2014-05-31 08:17:30.027783 I  AOBase: OutputAudioLoop: Play Event
2014-05-31 08:17:30.028861 I  Player(0): Video timing method: USleep with busy wait
2014-05-31 08:17:30.029269 I  TV: Created player.
2014-05-31 08:17:30.029488 I  TV: Changing from None to WatchingPreRecorded
2014-05-31 08:17:30.087000 I  TV: Main UI disabled.
2014-05-31 08:17:30.087163 I  TV: Entering main playback loop.
2014-05-31 08:17:30.166555 I  VDPAU: Added 2 output surfaces (total 4, max 4)
2014-05-31 08:17:32.951961 I  muting sound 1
2014-05-31 08:17:37.031858 I  unmuting sound 0
2014-05-31 08:17:39.351887 I  muting sound 1
2014-05-31 08:17:41.832704 I  TV: Attempting to change from WatchingPreRecorded to None
2014-05-31 08:17:41.845496 W  MythPainter: 16 images not yet de-allocated.
2014-05-31 08:17:41.845623 I  VDPAU Painter: Clearing VDPAU painter cache.
2014-05-31 08:17:41.922756 I  AOBase: Killing AudioOutputDSP
2014-05-31 08:17:41.941362 I  AOBase: OutputAudioLoop: Stop Event
2014-05-31 08:17:41.941388 I  AOBase: kickoffOutputAudioLoop exiting
2014-05-31 08:17:42.131061 I  Pulse: Operation: success 1 remaining 1
2014-05-31 08:17:42.151377 I  Pulse: Operation: success 1 remaining 0
2014-05-31 08:17:42.161497 I  Pulse: PulseAudio resume OK
2014-05-31 08:17:42.161761 I  TV: Changing from WatchingPreRecorded to None
2014-05-31 08:17:42.161832 I  TV: Exiting main playback loop.
2014-05-31 08:17:42.184577 N  Resuming idle timer
2014-05-31 08:17:44.015151 D  SendReceiveStringList(QUERY_IS_ACTIVE_BACKEND,frontend1) called from UI thread
2014-05-31 08:17:50.031489 I  Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on frontend1'
2014-05-31 08:17:50.032383 I  RAOP Device: Cleaning up.
2014-05-31 08:17:50.032441 I  AirPlay: Cleaning up.
2014-05-31 08:17:50.032904 I  Bonjour: De-registering service '_airplay._tcp.' on 'MythTV on frontend1'
2014-05-31 08:17:50.036144 I  Pulse: Cleaning up PulseHandler
2014-05-31 08:17:50.036175 I  Pulse: Destroying PulseAudio handler
2014-05-31 08:17:50.036746 I  Shutting down UPnP client...
2014-05-31 08:17:50.783272 I  OpenGL1: Deleting OpenGL Resources
2014-05-31 08:17:50.800589 I  OpenGL: Deleting OpenGL Resources
2014-05-31 08:17:50.810511 D  Refreshing DLManager's Cookie Jar
2014-05-31 08:17:50.810742 D  MythCookieJar: saving cookies to: /home/glen/.mythtv/MythBrowser/cookiejar.txt
2014-05-31 08:17:50.810758 D  Updating DLManager's Cookie Jar
2014-05-31 08:17:50.812947 I  Waiting for threads to exit.

```

The FE /etc/asound.conf:
Log refers to "hdmi_volume".
```

# Works in Ubuntu 9.04  5/9/2009
# Instructions for use
# 1) Find your hmdi hardware Card Number and Device Number.  Open a terminal and do:  
#    aplay -L
#    That will list all of the hardware audio devices.  Look for the one labeled HDMI.
#    Note what Card Number and Device Number it lists (they seem to be card 0,
#    device 3 but your system may be different).
# 2) Edit the pcm.hdmi_hw device defined here to set your Card Number and Device Number.
# 3) Put this file in either /etc/asound.conf or in your home directory as .asoundrc.
#    sudo cp deweys_asound.conf /etc/asound.conf
#      or 
#    sudo cp deweys_asound.conf $HOME/.asound.conf
# 4) Exit mythfrontend.  Then restart the sound system:
#    sudo /etc/init.d/alsa-utils restart
# 5) Start mythfrontend and go to the audio setup screen
#    "Utilities / Setup"  then "Setup" then "General" then "Next" until you
#    get to the Audio tab.
# 6) Fill in the info - it's case sensitive:
#    Audio output device: ALSA:hdmi_complete     <--- note you have to type in this field
#    Passthrough output devide: Default
#     ... Stereo... ... Passive...
#    Mixer Device: ALSA:default
#    Mixer controls: hdmi_volume                 <--- type in this field
# 7) Work your way back to Watch TV and give it a try.

pcm.hdmi_hw {
  type hw
  card 1    #  <-----  Put your card number here
  device 7  #  <-----  Put your device number here
}

pcm.hdmi_formatted {
  type plug
  slave {
    pcm hdmi_hw
    rate 48000
    channels 2
  }
}

pcm.hdmi_complete {
  type softvol
  slave.pcm hdmi_formatted
  control.name hdmi_volume
  control.card 0
}

#pcm.hdmi_complete {
#  type copy
#  slave.pcm hdmi_volume
#  slave {
#    pcm front
#  }
#}

pcm.!default hdmi_complete

```

The groups responce:
```

glen@frontend1:~$ groups
glen root adm cdrom sudo dip video plugdev sambashare mythtv lpadmin

```

---

### Post by blm-ubunet on 2014-05-30
> pcm.!default hdmi_complete
That line redefines the default audio device..

I would guess that if you comment out all the changes in that file then volume control may just work.
I believe the volume/mute mixer is (for most audio codecs) a h/w mixer device.

I'm fairly sure forcing 48Kbps is a thing of the past..& mythtv has a option to do this as well.

---

### Post by gga96 on 2014-05-30
I do not know what changes are to be commented out

---

### Post by blm-ubunet on 2014-05-31
just the one line that I quoted.

You need to add your frontend user to the audio group.
```
usermod -a -G audio glen
```
might be the reason audio volume does not work, but I do believe all of asound.conf is old unnecessary cruft.

Need to restart alsa .. just reboot.
Need to rescan with mythtv FE setup/audio.
the alsa default will not point to hdmi device..you need to select an hdmi device in list.
I think it will be enumerated as ALSA:hdmi:CARD=NVidia,DEV=1 (which is hw:1,7)

---

### Post by gga96 on 2014-05-31
Good morning.
Followed your instruction ... and set audio to ALSA:hdmi:CARD=NVidia,DEV=1.
Still no Mute or Volume control.

---

### Post by blm-ubunet on 2014-05-31
Good morning back..

Did you add your FE user to the audio group?

---

### Post by gga96 on 2014-05-31
Yes. Followed all of your instructions.

---

### Post by blm-ubunet on 2014-05-31
I can't check or expt with 14.04 & mythtv just yet..

Check your user is on audio group with:
```
groups
```
I guess:
- alsa permissions gone further backwards.
- alsa in 14.04 kernel does not work right. SMANN has same problem.
- HDMI codec on nVidia GPU does not have mixer (v. unlikely)
- you're outputting a bitstream requiring/forcing pass-thru' (AC3 encoding or AC3/DTS etc)..but you aren't.

does 
```
ls -al /proc/asound/card1/
```
show root user & audio group?

---

### Post by gga96 on 2014-05-31
Some data:
```

glen@frontend1:~$ groups
glen root adm cdrom sudo audio dip video plugdev sambashare mythtv lpadmin

glen@frontend1:~$ groups root
root : root

glen@frontend1:~$ groups audio
groups: audio: no such user

glen@frontend1:~$ ls -al /proc/asound/card1/
total 0
dr-xr-xr-x 6 root root 0 Jun  1 10:54 .
dr-xr-xr-x 5 root root 0 Jun  1 10:54 ..
-r--r--r-- 1 root root 0 Jun  1 10:54 codec#0
-r--r--r-- 1 root root 0 Jun  1 10:54 codec#1
-r--r--r-- 1 root root 0 Jun  1 10:54 codec#2
-r--r--r-- 1 root root 0 Jun  1 10:54 codec#3
-rw-r--r-- 1 root root 0 Jun  1 10:54 eld#0.0
-rw-r--r-- 1 root root 0 Jun  1 10:54 eld#1.0
-rw-r--r-- 1 root root 0 Jun  1 10:54 eld#2.0
-rw-r--r-- 1 root root 0 Jun  1 10:54 eld#3.0
-r--r--r-- 1 root root 0 Jun  1 10:54 id
dr-xr-xr-x 3 root root 0 Jun  1 10:54 pcm3p
dr-xr-xr-x 3 root root 0 Jun  1 10:54 pcm7p
dr-xr-xr-x 3 root root 0 Jun  1 10:54 pcm8p
dr-xr-xr-x 3 root root 0 Jun  1 10:54 pcm9p
```

---

### Post by gga96 on 2014-05-31
Does this provide you with some clues:
[http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)

---

### Post by blm-ubunet on 2014-05-31
No, not really..
One of the most useful desktop GUI sound config tools for pulseaudio is
pavucontrol
No help here tho..

try:
```
sudo chgrp -R audio /proc/asound/card1
```
Can you now see the group change in /proc/asound/card1/* ?

This change will not survive a reboot.

This makes the permissions match my (working) 14.04 *install & match my (working) 10.04 MythTV box.

 *install == hacked from 12.04 to 14.04 without using upgrade scripts.

---

### Post by gga96 on 2014-05-31
[SIZE=2][FONT=arial]Ran **sudo chgrp -R audio /proc/asound/card1**.
[/FONT][/SIZE][FONT=arial][/FONT][SIZE=3][/SIZE][SIZE=1][/SIZE][SIZE=2][/SIZE][SIZE=3][FONT=arial]Could not see a change in /proc/asound/card1/*.
Tried FE play video, result is no sound, volume or mute.[/FONT][/SIZE]

---

### Post by blm-ubunet on 2014-06-01
Not with the fullstop tho?
> [SIZE=2][FONT=arial]**sudo chgrp -R audio /proc/asound/card1**.[/FONT][/SIZE]

That cmd must cause ls -al /proc/asound/card1 to show a different group (was root:root)  & needs to be (root:audio).
Is there some other error reported that suggests the cmd failed ?


On my mythtv box all files/folders in /proc/asound/ are "audio" group (excepting 2 symlinks Intel & NVidia)..

---

### Post by gga96 on 2014-06-01
No dot following cmd and without errors.
  
Ran the following again, can now see the require change.
Ran FE video and result is the same as before, video is fime but no sound, mute or volume control, 
```

glen@frontend1:~$ sudo chgrp -R audio /proc/asound/card1
[sudo] password for glen: 
glen@frontend1:~$ ls -al /proc/asound/card1
total 0
dr-xr-xr-x 6 root audio 0 Jun  1 14:41 .
dr-xr-xr-x 5 root root  0 Jun  1 14:41 ..
-r--r--r-- 1 root audio 0 Jun  1 14:41 codec#0
-r--r--r-- 1 root audio 0 Jun  1 14:41 codec#1
-r--r--r-- 1 root audio 0 Jun  1 14:41 codec#2
-r--r--r-- 1 root audio 0 Jun  1 14:41 codec#3
-rw-r--r-- 1 root audio 0 Jun  1 14:41 eld#0.0
-rw-r--r-- 1 root audio 0 Jun  1 14:41 eld#1.0
-rw-r--r-- 1 root audio 0 Jun  1 14:41 eld#2.0
-rw-r--r-- 1 root audio 0 Jun  1 14:41 eld#3.0
-r--r--r-- 1 root audio 0 Jun  1 14:41 id
dr-xr-xr-x 3 root audio 0 Jun  1 14:41 pcm3p
dr-xr-xr-x 3 root audio 0 Jun  1 14:41 pcm7p
dr-xr-xr-x 3 root audio 0 Jun  1 14:41 pcm8p
dr-xr-xr-x 3 root audio 0 Jun  1 14:41 pcm9p
```

---

### Post by blm-ubunet on 2014-06-01
Grasping at straws..
Maybe the folder one level up needs group change.
sudo chgrp audio /proc/asound

This folder is root:audio on my 14.04 machine..

---

### Post by gga96 on 2014-06-01
```

glen@frontend1:~$ sudo chgrp audio /proc/asound
[sudo] password for glen: 

```
No different to before!!!
I think I should try and recover the sound by redoing the /etc/asound.conf with the DeweyOxberger file uless you have more things to try.

---

### Post by gga96 on 2014-06-01
The lack of sound is my mistake, sorry. I brought the FE from the lounge and plugged it into a monitor in the study that bloke Murphy had put the sound volume right down. All ok with the sound now.

---

### Post by blm-ubunet on 2014-06-01
Question is will it survive the relocation back to lounge & a reboot !

I have some cmds in /etc/rc.local to force alsa permissions etc on reboot.

---

### Post by gga96 on 2014-06-01
FE survived!
I am surprised the changes with permissions and commenting out **pcm.!default hdmi_complete** has not changed things a bit.
I thought I was root (when typing sudo and password).
Sorry, but this audio nuts and bolts business does not compute for me.
You think the problem remains with permissions?

---

### Post by gga96 on 2014-06-01
The simpler more convenient problem is to attack the HP BE local FE. 
It worked out of the box with 12.04 and is still connected with VGA cable. 
After installing 14.04 it lost Mute and Volume control.

---

### Post by blm-ubunet on 2014-06-01
When you say the FE survived..
I assume that means HDMI audio works.. but does volume & mute work ?

Do they work after re-setting the /proc/asound to "audio" group?

I think the group/permissions of /proc/asound is lost because it is recreated at boot.
I think the real problem is with the alsa source code.

MythTV suspends pulse-audio sound server (unless you pick a pulse device).
It could be easier to debug with pulseaudio (pavucontrol) & some simple music player.
See if pavucontrol can control volume & mute..

BE box:
Check the /etc/asound.conf is empty..(backup/rename)
Users mythtv & FE user (if diff) should be members of audio group.

---

### Post by gga96 on 2014-06-01
[SIZE=3][FONT=arial]FE actions:
Yes FE sound OK, but volume and mute do not work.  (if i ever get a possetive result YOU WILL HEAR ABOUT IT).
Without rebooting I reset[/FONT] sudo chgrp audio /proc/asound and then tested but mute and volume control still not working. 
[B]
[FONT=arial][/FONT][/B][FONT=arial]BE actions:
File /etc/asound.conf  is blank.
Installed pavucontrol but did not know how to make the assignment to have it work with myth.  
Tested with myth video but no mute and volume control.[/FONT][/SIZE]

---

### Post by ridgeland on 2014-10-19
For Sound controls:
Exit the MythTV frontend
From the Ubuntu Software Center search for and install
xfce4-mixer
This will add an item in the main menu - Applications -> Multi-media -> Audio Mixer
Launch the Audio Mixer (I had to enlarge the window)
On my Mythbuntu 14.04.1 the volume is down to about 40% - now slide it up to 100% and it's much more sane when I switch my TV from "PC" back to "DVR"
To also have the Audio Mixer on the panel as an icon:
Right click on the panel - Panel -> Add new item -> select "Audio Mixer" from the list

So why is this not included in Mythbuntu?
So why is system volume set so low by default?

---

### Post by ridgeland on 2014-10-19
Couple more observations:
[F9] should be mute on/off - doesn't work
[F10] should be volume down - doesn't work
[F11] should be volume up - doesn't work
I have a Logitech wireless keyboard - with multimedia buttons - on the keyboard the mute, up and down work.

---

### Post by gga96 on 2014-10-21
Thanks ridgeland,

I am on the road at the moment until about December so cant get to myth.
Look forward to trying your ideas then.

Glen

---

