---
title: "Laptop + Dual Head, Nvidia Advice needed"
date: 2010-02-23
forum: Multimedia Software
---

### Post by windfix on 2010-02-23
I have a Dell E6500 laptop (1280x800 screen), which I frequently dock.  The dock as two Dell 1908FP 20" monitors connected by DVI. I can move between the laptop display and the twins by manually changing display configuration in NVIDIA X Server settings, but this is a pain requiring about 15 clicks each time.

I have tried using the "Save to X Configuration File" option in the Nvidia server settings, but this seems to screw everything up.  I need to dynamically change between the setups... anyone have advice on getting that done?  Can the xorg.conf file be configured to do it?

My xorg.conf looks like this:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by RichardG891 on 2010-03-10
Been a while since at the forums; sorry. Now, the problem with ubuntu is the supplied nvidia driver is not configured to utilise the X configuration file so you get errors even when loading "nvidia-settings" as root. It does have it's own save settings, but they're a pain as well. The best way is to reinstall the nvidia driver manually and set it up properly. Don't panic, It's dead easy. You might as well update the driver at the same time. Go here first:

"http://www.nvidia.com/Download/index5.aspx?lang=en-us"

Just accept the default selection if you have any kind of modern GeForce/nForce card (linux driver is unified) and you'll download the file "NVIDIA-Linux-x86-190.53-pkg1.run".

Now launch Administration>Hardware Drivers, and deactivate your existing nvidia driver (which will uninstall it as well). Make sure your start up sequence requires you to login. Put the new Nxxx.run file on your Desktop so you can find it again, and reboot (but read the rest of this first).

Once back at the login screen, press <CTRL><ALT><F1>
This takes you out of X to terminal level. Then do this:

$: cd Desktop
$: sudo /etc/init.d/gdm stop
$: sudo sh ./NVIDIA-Linux-x86-190.53-pkg1.run

and follow the nvidia install instructions, particularly when it asks you if you want to integrate X configuration. Finally,

$: sudo reboot

Now when you login in again and run nvidia-settings as root, Save to X Configuration should work, and you'll have a more up-to-date driver as well. The X.conf should now automatically use a single screen when the laptop isn't connected to the dock, and your saved multi-screen settings when you are (if you hot-plug it you may need to logout and login again to restart X - re-enable <CTRL><ALT><BACKSPACE> if you plug and unplug frequently, it's quicker).

If all goes horribly wrong, go back to the login screen and press <CTRL><ALT><F1> again and type:

$: sudo sh ./NVIDIA-Linux-x86-190.53-pkg1 --uninstall

---

### Post by windfix on 2010-03-11
Thanks, RichardG891 -

Quick question though, I have an NVIDIA NVS 160M graphics card (identified via "LSPCI" from the terminal).  The website says "no certified drivers available" for this card.

I am currently using the nvidia-glx-185 (package installed in Synaptic).

Should I use the NVIDIA-Linux-x86-190.53-pkg1.run file you referenced anyway?

---

### Post by RichardG891 on 2010-03-11
It's not a problem if the .185 driver was OK (It's the one I replaced on mine). The .190 is just a minor update. As I understand it, there are only two nvidia drivers for linux - this up-to-date series, and a legacy build for much older cards (TnT2 etc.) I think that because most laptops use heavily customised motherboards, nVidia doesn't provide support directly for them. I also found (with My HP laptop with nvidia graphics) that the nvidia site just tells me to go to HP for any updates, but I've never had an issue running the proper nvidia linux driver on it. Mine has an nForce 610M chipset with a G7000M integrated graphics chip.

Hope that helps!

PS: I just reinstalled it again, just make sure I hadn't missed any steps, and after the "sudo /etc/init.d/gdm stop" it tells me not to do it from init.d but by using a service instead (and gave me a couple of commands to try). They didn't seem to do anything and it didn't make a difference anyway - I guess if you start a "real" terminal session prior to logging in, the display manager isn't running to start with.

---

### Post by windfix on 2010-03-12
Thanks for the help.  Results: it works, mostly.  I did run into some glitches to warn other of:

After removing the hardware driver via Administration | Hardware drivers, my laptop did not boot back to the login screen.  It went to GRUB, but blanked out black past that.  this freaked me out, but it ends well.  I needed to use GRUB to select recovery mode, then continue your instructions from that command line. It installed fine.

As promised, I used the NVIDIA X Server Settings tool (System | Administration) to configure to my external monitors and it saved to X configuration file without a problem.  Now, when booted while docked, video goes to the externals.  When booted undocked, it goes to the laptop display.  Nice!  Thanks for the help

---

### Post by windfix on 2010-03-15
Just in case it helps someone else, I am pasting my new xorg.conf file below.  This miraculously works with both my twin 20" monitors at work and my combined 24"+20" monitors at home.  Both sets of monitors are via DVI into the dock for my Dell E6500.

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
    ModelName      "ACI VK246"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 160M"
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-1: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

