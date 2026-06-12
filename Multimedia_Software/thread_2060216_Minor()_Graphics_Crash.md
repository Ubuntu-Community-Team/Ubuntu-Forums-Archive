---
title: "Minor(?) Graphics Crash"
date: 2012-09-19
forum: Multimedia Software
---

### Post by Pengi-FlyGirl26 on 2012-09-19
Without the narrative, my most basic question is this:
Should I be concerned or is my computer just throwing a 'hissy fit'? :roll:

Narrative:
I was recently on a website that uses a TON of graphics and massively increases CPU activity (Pottermore) when my computer screen went black, flickered some bits around, and eventually displayed a 4-way split screen with an error message. I believe it said "Graphics Saving Mode," but I couldn't read all of it. I ended up just restarting. So far, no troubles, but I am conducting a system test at the moment.

Asus F3S
Lucid
Firefox

Suggestions and feedback are highly welcome.
Thanks!

---

### Post by Pengi-FlyGirl26 on 2012-09-25
Update:
Upon startup, screen was split into 8 with this dialogue:
"Ubuntu is running in low-graphics mode"
The following error was encountered. You may need to update your configuration to solve this:
Failed to initialize NVIDIA graphics device (PCI:1:0:0)
Check system kernal log for additional error.
Chapter 8: common problem in the readme
Screen(s) found, but none have a usable configuration"

Went to NVIDIA:
Not using NVIDIA x driver
edit x configuration file (run 'nvidia-xconfig' as root & restart x server)
Went to terminal:
Unable to locate/open x configuration file
Unable to write to directory /ect/x11

Now, my machine will boot normally, but screen resolution is terrible. Don't have time to mess with it right now.

---

### Post by BicyclerBoy on 2012-09-25
None of your apparent fix explains the crash..

The log files in /var/log/Xorg.* could explain...
Xorg.0.log is the current session log..
Look in some of the older files..

In a terminal should have run:
sudo nvidia-xconfig
nvidia-settings


"nvidia-settings" GUI saves settings to hidden file in home (.nvidiarc I think?)
You can save settings (some) back into /etc/X11/xorg.conf but it is not necessary.

If nvidia-settings GUI appears to not "save" its settings you could need to change the permissions on the ~/.nvidiarc file..
nvidia-settings should ask for sudo credentials when attempting to save to xorg.conf.

---

### Post by Pengi-FlyGirl26 on 2012-09-26
It is now to the point where every other startup is low graphics mode. I've been going into the system/administration/hardware drivers and manually activate the accelerated graphics driver (there are 2 choices, so I've been alternating). This really isn't a "fix".

In the terminal, I ran sudo nvidia-xconfig:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

As for nvidia-settings and log files, I can access them, but I don't exactly know what it is I'm looking for or what to change things to.

---

### Post by BicyclerBoy on 2012-09-27
Well if both those cmds ran okay then the driver is prob fine..

I guess an Asus F3S is a laptop with GeForce 8600m GPU..
Possible the thing is full of dust..
Does it get worse when hot?
Is it worse warm rebooted?
Is it better if you shutdown then restart from OFF?

Next time the brick reboots/starts in low res mode..
- login
- copy log file.
cp /var/log/Xorg.0.log ~/Documents/Xorg.log

& post to the thread..

---

### Post by Pengi-FlyGirl26 on 2012-09-27
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux Wubi 2.6.32-43-generic #97-Ubuntu SMP Wed Sep 5 16:43:09 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-43-generic root=UUID=b0ab24a2-e94d-4370-821b-5d606ac51c62 ro quiet splash
Build Date: 25 February 2012  06:59:39AM
xorg-server 2:1.7.6-2ubuntu7.11 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 27 12:59:43 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0425:1043:1514 nVidia Corporation G86 [GeForce 8600M GS] rev 161, Mem @ 0xfc000000/16777216, 0xc0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.22  Sun Nov  8 21:42:44 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  173.14.22  Sun Nov  8 20:43:40 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by Pengi-FlyGirl26 on 2012-09-27
> **BicyclerBoy said:**
> Well if both those cmds ran okay then the driver is prob fine..

I guess an Asus F3S is a laptop with GeForce 8600m GPU..
Possible the thing is full of dust..
Does it get worse when hot?
Is it worse warm rebooted?
Is it better if you shutdown then restart from OFF?
  ..

I am normally very careful about dust & dirt, but I'll try cleaning it again anyway. I shut the computer off completely after each session (the actual shut-down, not just the power button). Last night I tried to just put it in suspend, but on the restart of the session, it's back in low graphics. I'm hoping this is more of a software issue than a hardware problem.

---

### Post by Pengi-FlyGirl26 on 2012-09-27
[/QUOTE]
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
[QUOTE
Ok, so that's the actual problem (now that I can actually read it). How/why is this happening and how do I go about a permanent fix?

---

### Post by BicyclerBoy on 2012-09-27
Not sure this is normal:
```
I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072

```
The fact the problem only occurs 50% of reboots is bad. But could be software race condition..
If it is not related/effected by heat is a good thing. Most h/w faults are affected by heat.

When it reboots into low res...can you run
dmesg > ~/Documents/dmesg.txt

Have a read thru that file for clues..(ACPI, IRQ, interrupt).

---

### Post by Pengi-FlyGirl26 on 2012-09-29
Half a can of air and a dozen restarts later, it's doing well. I guess it was just a viral, mutant bit of dust. I hope this isn't just the tip of the iceberg or something.
Thanks for your time and insight. These past few days have been really disconcerting. I appreciate the support.

---

### Post by BicyclerBoy on 2012-09-29
You're welcome.

Be happy it's not a apple laptop just out of warranty..

Often you can break into the laptop by prising up the keyboard, this seems to be a entry point for air/dust/fluff.
Use a paint-brush with your air (natural bristle is less static risk).

Go easy on the air as it is dry & generates static.
Blowing damp/moist air from your lungs is safer (for the PC).

---

### Post by Pengi-FlyGirl26 on 2012-09-30
As soon as I marked this as solved, it starts acting up again...
What could be some other methodologies/troubleshooting/reasoning things I should be on the lookout for?

---

### Post by BicyclerBoy on 2012-10-01
You could try some stress testing..

[http://vmtce.sourceforge.net/](http://vmtce.sourceforge.net/)
(this looks to require compilation)

First run "nvidia-settings" & watch the GPU temperature...should idle about 40 - 60 degreesC

Open a terminal & run "glxgears"
Stop the test if you hit 105 degC.

---

### Post by Pengi-FlyGirl26 on 2012-10-02
While trying to "mend" drivers, I think I disabled them. (I felt stupid as soon as I did that) I can't really get a usable boot with that machine at the moment. I took out the hard drive, hooked it up to an external SATA/USB adapter cord and booted my school's machine up into my hard drive. I can access all the files and records, but it's obviously picking up my school's hardware instead of my laptop's (I also don't want to do this often or know how stable of a setup this is). At the moment, I'm looking for a totally clean reload of NVIDIA drivers. I've seen other commands of something like "sudo apt-get purge..." and "sudo install-latest..." but I don't really know where to go with this. If it's just a matter of downloading files/drivers (I know it won't be that easy), what directory, if any is involved?
Can someone give me a step-by-step or command-by-command rundown? I still have the option of formatting another hard drive.
This is, again, hoping it's a software issue. Hardware is a more involved issue I don't have the resources to fix at the moment.

---

### Post by BicyclerBoy on 2012-10-03
Without evidence from system logs & testing progs etc I doubt purging & reinstalling will do anything..
The install can be messed up by attempting the driver install direct from nVidia website..

Best ubuntu advice:
Do not download files/drivers.
Do not go outside package management

If you really what to clear out/reinstall  driver:
apt-get purge nvidia*
apt-get install nvidia-current nvidia-settings vdpauinfo

Run the tests in post #13 & these

glxinfo | grep OpenGL
vdpauinfo
glxgears & nvidia-settings same time; monitor GPU temperature.

---

### Post by Pengi-FlyGirl26 on 2012-10-22
Ok, this still isn't solved, but I'm not really able to mess with his as much as I'd like. Another computer booted into the hard drive will work and another monitor hooked up to the laptop (harddrive in or out) is also fine. I'm guessing this mans the card's fried or something. It'll be a while. I'm breaking in another laptop in the meantime.

---

### Post by BicyclerBoy on 2012-10-23
When you plug 2 or more monitors into nVidia video card, the card runs at max performance level.
If there was a h/w fault I would have thought this setup would have been more unstable due to heat etc.

Maybe the problem is s/w (drivers)..

---

