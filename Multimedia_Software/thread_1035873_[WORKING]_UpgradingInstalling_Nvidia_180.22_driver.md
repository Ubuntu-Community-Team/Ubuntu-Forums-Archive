---
title: "[WORKING] Upgrading/Installing Nvidia 180.22 driver"
date: 2009-01-10
forum: Multimedia Software
---

### Post by ed-koala on 2009-01-10
Hopefully this will help others who can't enable an Nvidia restricted driver without hosing their system.  After many attempts, here is what worked for me ...

Asus M3N72-D motherboard
AMD Phenom 9950 Quad-Core Processor
8 gb RAM
2 Samsung HD501LJ 500gb hard disks
Dual GeForce 9800 GTX+ video cards

First, open Synaptic and make sure the following pkgs are installed:

    make
    gcc
    build-essential
    dkms
    linux-headers-2.6.27-9  (assumes you use the current kernel)
    linux-headers-2.6.27-9-generic
    linux-generic
    linux-headers-generic
    module-assistant

Next, make sure the following are NOT installed, and use the "Mark for complete removal option" if any need to be removed:

    ALL nvidia pkgs (search for nvidia)
    Any old kernel pkgs, ie linux-headers-2.6.27-7 and earlier
       (This might not be necessary, but I did it anyway)


Now, perform the following command in a terminal:

    sudo lspci | grep VGA

The output will look something like this:

    02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)
    03:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)

Write down the number begining each line.

Go to System-Administration-Hardware Drivers and choose 180.22 and active the driver - DO NOT REBOOT yet!!!

Open terminal and type:

    sudo gedit /etc/X11/xorg.conf

Replace the graphics "Device" section with the following:

    Section "Device"
        Identifier     "Configured Video Device"
        BusID          "PCI:1:0:0"
        Driver         "nvidia"
    EndSection

Edit the BusID line to reflect the number you wrote down earlier (for me, that would be "PCI:2:0:0".  Make sure you use all colons as shown, and add the PCI part as shown.

If you have sli, add the following:

    Option "sli" "auto"

Save the file, reboot and you should have 3d graphics working.
Note - for dual graphics PCs, you may boot to a black screen but you'll hear the normal boot sounds.  If that happens, you used the wrong number in BusID.  Change it to the other number OR plug you monitor into the other card.


This got Nvidia's restricted driver working for me after a number of reinstalls.  Hopefully this will solve many people's problems also.  :))

Thanks for all the users posting solutions to the problem.  I used parts of several solutions to make this one work.

---

### Post by shayguitarra on 2009-01-10
This looks great. One question. The 180.22 driver does not show up under hardware drivers as I believe it hasn't been added to the repositories yet. The latest version in Synaptic seems to be 180.11.

I installed it after downloading directly from the Nvidia site. And after installation it still didn't show up under hardware drivers.

So maybe there's a repository I don't have enabled?

---

### Post by ed-koala on 2009-01-10
you'll need the medibuntu repository.  If you haven't installed it yet, google it and you'll get an easy how to if you need it.

---

### Post by shayguitarra on 2009-01-10
I had both medibuntu repositories (free and non free) selected, I've run an update and still not seeing anything. I'll try the 180.11 driver in synaptic and see if that makes any difference.

---

### Post by shayguitarra on 2009-01-10
Whoops! Didn't realise that would getting it through synaptic required knowing how to build a kernel module. I'll wait and see if 180.22 turns up in the repositories.

---

### Post by Tekmoor on 2009-01-10
I'm having the same problems, I can't see any nvidia drivers in the hardware drivers manager anymore and I'm stuck on low graphics mode.

---

### Post by ed-koala on 2009-01-10
Go into Synaptic, and install the nvidia-XXX-modaliases file(s). Those are what make the drivers show up in the restricted list (90% sure).

That will allow you to follow the steps to install the driver.  :)

---

### Post by Tekmoor on 2009-01-10
I installed the modaliase files and the nvidia driver now shows up in hardware drivers. Unfortunately I still can't get my system to detect it. I've followed your instructions and I still get an error saying the nvidia driver could not be found. I've also tried nvidia-xconfig to no avail.
Thanks for your help ed-koala.

---

### Post by ed-koala on 2009-01-10
No problem.  Sorry it hasn't helped.  If I think of something else I'll post it.   :)

---

### Post by sofasurfer on 2009-01-11
I followed the steps in post #1 up to the part that says... "Go to System-Administration-Hardware Drivers and choose 180.22 and active the driver". When I went to "System-Administration-Hardware Drivers" I was told that there are NO proprietary drivers.

Until I followed these steps there were Nvidia Graphics Driver 177, 173 and I think 96.

Anyone know what happened?

---

### Post by ed-koala on 2009-01-11
Yeah, you'll need to reinstall the nvidia-modalias files for the options to show up in the list.  An oversight on my part ... an important one too.  But that will solve the problem of no choices.

Good luck!

---

### Post by sofasurfer on 2009-01-11
```

daryl@ubuntu:~$ sudo apt-get install nvidia-modalias
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-modalias

```

Was this what you meant, or did you mean that I should reinstall the individual drivers such as Nvidia GLX 177?

EDIT::
O, never mind. I see that synaptic has a "nvidia-177-modalias". I will install it and let you know.

---

### Post by sofasurfer on 2009-01-11
I installed the "nvidia-177-modalias". Then sys>admin>hardware-drivers shows only "nvidia" as an available driver. It discription says...

```

These binary drivers provide optimized hardwareacceleration of  OpenGL applications via a direct-rendering X Server.AGP, PCIe, SLI, TV-out and flat panel displays are also supported.

Please see the nvidia-177-kernel-source package for building the kernel modulerequired by this package. This will provide nvidia-kernel-<version>

The following GPUs are supported:GeForce 6800 Ultra, GeForce 6800, GeForce 6800 LE, GeForce6800 XE, GeForce 6800 XT, GeForce 6800 GT, GeForce 6800 GT,GeForce 6800 GS, GeForce 6800 XT, GeForce 7800 GTX, GeForce7800 GTX, GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800, GeForce Go 7800 GTX, GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT, GeForce Go 6800, GeForce Go 6800 Ultra, GeForce 6800, GeForce 6600 GT, GeForce 6600, GeForce 6200, GeForce 6600 LE, GeForce 7800 GS, GeForce 6800 GS, GeForce 6800 Ultra, GeForce 6600 GT, GeForce6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600, GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, GeForce Go 6600, GeForce Go 6600 GT, GeForce 6200, GeForce 6500, GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM), GeForce 6200 LE, GeForce Go 6200, GeForce Go 6400, GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,GeForce 8800 GTX, GeForce 8800 GTS, GeForce 8800 Ultra, Tesla C870, GeForce 7350 LE, GeForce 7300 LE, GeForce 7300 SE/7200 GS, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400, GeForce 7500 LE, GeForce 7300 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200, GeForce 6200 A-LE, GeForce 6150, GeForce 6150 LE, GeForce 6100, GeForce Go 6150, GeForce Go 6100, GeForce 7900 GTX, GeForce 7900GT/GTO, GeForce 7900 GS, GeForce 7950 GX2, GeForce 7950 GX2,GeForce 7950 GT, GeForce Go 7950 GTX, GeForce Go 7900 GS, GeForce Go 7900 GTX, GeForce 7600 GT, GeForce 7600 GS, GeForce 7900 GS, GeForce 7950 GT, GeForce 7650 GS, GeForce 7600 GT, GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce7300 GT, GeForce Go 7600, GeForce Go 7600 GT, GeForce 6150SE nForce 430, GeForce 6100 nForce 405, GeForce 6100 nForce 400, GeForce 6100 nForce 420, GeForce 8600 GTS, GeForce 8600GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS, GeForce 8600M GT, GeForce 8700M GT, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT, GeForce 8400M GS, GeForce 8400M G, GeForce 9400 GT, GeForce 7150M / nForce 630M, GeForce 7000M / nForce 610M, GeForce 7050 PV / NVIDIA nForce 630a,GeForce 7050 PV / NVIDIA nForce 630a, GeForce 7025 / NVIDIAnForce 630a, GeForce GTX 280, GeForce GTX 260, GeForce 8800GTS 512, GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS, GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS, GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, GeForce 9600 GT, GeForce 9600 GS, GeForce 9800M GTS, GeForce 9800M GTS, GeForce 9600M GT, GeForce 9600M GS, GeForce 9500M G, GeForce 9300 GS, GeForce 8400 GS, GeForce 9300M GS, GeForce 7150/ NVIDIA nForce 630i, GeForce 7100 / NVIDIA nForce 630i, GeForce 7050 / NVIDIA nForce 610i, GeForce 8300, GeForce 8200,nForce 730a, GeForce 8200, GeForce 8100 / nForce 720a, Quadro FX 4000, Quadro FX 4500, Quadro FX Go1400, Quadro FX 3450/4000 SDI, Quadro FX 1400, Quadro FX 4400/Quadro FX 3400, Quadro NVS 440, Quadro FX 540M, Quadro FX 550, Quadro FX 540, Quadro NVS 285, Quadro FX 5600, Quadro FX 4600, Quadro NVS 110M, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M, QuadroFX 350, Quadro NVS 210S / NVIDIA GeForce 6150LE, Quadro FX2500M, Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500, Quadro FX 4500 X2, Quadro FX 560, Quadro FX 370,Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX570, Quadro FX 1700, Quadro NVS 140M, Quadro NVS 130M, Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290, Quadro FX 3700,Quadro FX 3600M

See /usr/share/doc/nvidia-glx/README.txt.gz for a complete listof supported GPUs and PCIIDs

```

Attempting to enable extra desktop effects still 
shows "desktop effects could not be enabled".

Now I will install "nvidia-177-kernel-source", since it is mentioned above. 

I see that "nvidia-kernel-<version>" is also mentioned above. Should this be installed? Synaptic only shows "nvidia-kernel-common".

I'll let you know.

---

### Post by sofasurfer on 2009-01-11
I have now installed "nvidia-177-kernel-source" and still can not enable desktop effects.

---

### Post by smokyboy0 on 2009-01-12
Hi,

I am having huge problems since upgrading to nvidia 180.xx drivers on my Intrepid box with 9800gtx+. During the boot and after the progress bar goes away, the screen shortly flashes and then it remains black. I can only hard-restart the system.
The problem appears with all sorts of nvidia 180.x drivers - I used 180.22 from nvidia website and also ubuntu 180.11 drivers. I removed all nvidia stuff when trying the 180.22 drivers, so there was no conflict with existing restricted drivers. Anyway, the problem persists even with ubuntu drivers - after I activate them in restricted driver manager, I run nvidia-xconfig and restart the system, but the black screen comes up again.
I saved the syslog of the unsuccessful boot. It says that nvidia module was loaded and ends with the following lines about bluetooth when the boot freezes (or at least appears to freeze):

Jan 12 18:54:00 tectonic kernel: [   10.613070] nvidia: module license 'NVIDIA' taints kernel.
Jan 12 18:54:00 tectonic kernel: [   10.776789] nvidia 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 12 18:54:00 tectonic kernel: [   10.776799] nvidia 0000:05:00.0: setting latency timer to 64
Jan 12 18:54:00 tectonic kernel: [   10.777434] input: PC Speaker as /devices/platform/pcspkr/input/input6
Jan 12 18:54:00 tectonic kernel: [   10.777984] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.11  Wed Nov 26 10:53:43 PST 2008
......
Jan 12 18:54:02 tectonic bluetoothd[5774]: Bluetooth daemon
Jan 12 18:54:02 tectonic kernel: [   17.751221] Bluetooth: Core ver 2.13
Jan 12 18:54:02 tectonic kernel: [   17.751764] NET: Registered protocol family 31

Upon successful boot (e.g. after using fallback xorg.conf) the syslog continues with the following lines:

Jan 12 19:00:34 tectonic kernel: [   38.276937] Bluetooth: HCI device and connection manager initialized
Jan 12 19:00:34 tectonic kernel: [   38.276940] Bluetooth: HCI socket layer initialized
Jan 12 19:00:34 tectonic bluetoothd[5967]: Starting SDP server
Jan 12 19:00:34 tectonic kernel: [   38.293816] Bluetooth: L2CAP ver 2.11
Jan 12 19:00:34 tectonic kernel: [   38.293821] Bluetooth: L2CAP socket layer initialized

I don't know if this is relevant at all.
The Xorg log file is not even created during failed boots.

I tried virtually everything I found on the forums, including the BusId trick, even upgraded BIOS, etc. Nvidia 177.82 drivers work fine, even after reinstalling them. I would like to use original nvidia drivers, because they include support for CUDA, which I don't know if ubuntu drivers do.
Does anyone have a slightest idea about what else I could try? I don't know how to supply more info on failed boot because when the black screen appears I can only reboot.

---

### Post by Tekmoor on 2009-01-12
I've been able to get the 180.08 beta driver working but anything newer just won't work.
You can get it from the nvidia ftp: [ftp://download.nvidia.com/XFree86/Linux-x86/180.08/](ftp://download.nvidia.com/XFree86/Linux-x86/180.08/)
I simply uninstalled all old drivers and followed the installation instructions.

---

### Post by smokyboy0 on 2009-01-14
Just a warning for all owners of Gigabyte 9800gtx+ graphics card - no nvidia 180.x drivers will work unless you flash the vga bios to version F11 or newer.

---

### Post by bobdobbs on 2009-01-14
I've been trying to get various versions of nvidia drivers working.
I've had very little success.

If I want to start from scratch, how do uninstall everything that a driver install puts on my system?

---

### Post by flameproof on 2009-01-14
I went through with it, but only got 180.11 installed, which does not work for me.

After that I could not get back to 173 and only get crash reports. I am now using the noname Ubuntu driver.

---

### Post by thornberry on 2009-01-17
Thanks very much - wonderful post!

I'm running a Biostar GF8200 M2+ and for the last 6 months have had a GeForce 7200 installed - all attempts to load the latest Nvidia drivers were horrendous.

Today did pretty much everything you said and had it running in about 20 minutes.

Just a couple of points:
running 8.10 32 bit with standard repos so no 180.22 in my hardware drivers - downloaded NVIDIA-Linux-x86-180.22-pkg1.run from the Nvidia site.

cleaned out all the old Nvidia files and made sure I had all of the components you specified.

Logged out, Ctl F1 to terminal, stopped X server and executed the .run file. This produced three file errors such as -
Unable to create /usr/lib/nvidia/libglx.so.xserver-xorg-core.
Continued after each error and the driver loaded beautifully.

Seems to run a little quicker and crisper than before but that's a bit subjective.
Big upside - was able to pull a video card and two fans and the system still runs cooler than before (about 23c, was about 26c).

Found that Brasero now thinks that my DVDs have zero space and K3B just locks the entire system up, no matter what.
Those two are gone - GnomeBaker works the very best.

Once again, thanks, great job.

---

### Post by mikewhatever on 2009-01-18
> **ed-koala said:**
> 
Go to System-Administration-Hardware Drivers and choose 180.22 and active the driver - DO NOT REBOOT yet!!!


I've looked at the list of packages in medibuntu, and 180.22 wasn't there, as well as any other graphics driver. This instruction seems to be simply wrong.
[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

---

### Post by Nov8tr on 2009-01-18
He is absolutely correct. In checking the medibuntu index for 8.04 and 8.10 there are NO graphics drivers of any kind for any card. So it adds squat. I have been 3 weeks now trying to get my SLI 8800GT's to work in Unbuntu. I have tried 8.04 and 8.10. I have tried Unbuntu, Kubuntu, Xbuntu and even Mephis. I have tried it with hardware drivers, direct downloads from nvidia where it even built a kernel, and EnvyNG. ALL of them dont' work as soon as I reboot. I get a black screen everytime. I have spent hours and hours and hours following forum advice and tried at least 30 different "solutions" None have worked so far. I am going to try the OP's solution after I try to get it back to just low rez drivers. I had it working with Envy drivers 169 with it showing one card. I have many many days of work in this setup and DO NOT want to rebuild it again. I'm tired of rebuilding it. I am more than open to any suggestions. thanks!!

---

### Post by dk75 on 2009-01-24
nVidia 180.22 drivers are in 9.04 repository thus it is for Jaunty instruction.

---

### Post by mikewhatever on 2009-01-24
> **dk75 said:**
> nVidia 180.22 drivers are in 9.04 repository thus it is for Jaunty instruction.

Obviously not. The OP speaks of 2.6.27-9 kernel, which is still the current version for Intrepid. Furthermore, nvidia-glx-180.22 wasn't in Jaunty repositories at the time post#1 was written.
Hope I won't offend anyone, at least that is not my intension, but I'd advise to stay away from this particular, very poorly written guide.

---

### Post by allCuExpMa on 2009-01-31
.

---

### Post by MrCharles on 2009-02-05
After using Ubuntu for the better part of 3 years.

I'm done.

---

