---
title: "Limited resolution with external monitor/projector (10.10, Thinkpad)"
date: 2010-11-20
forum: Multimedia Software
---

### Post by phlibi on 2010-11-20
Hi folks,

I have some trouble configuring an external monitor or projector on my Notebook.
A few details about my Setup:

- Thinkpad W510, 15.6" with 1920x1080
- AOC 17" flat panel, 1280x1024 native resolution
- Ubuntu Maverick (10.10), x64
- nvidia proprietary driver

Most of the graphics stuff works like a charm, I have 3D acceleration, smooth desktop effects and native resolution on the integrated panel.
The problem I have is when I want to connect an external monitor (or a projector) using the VGA-Port. When plugged in, nothing happens. This is quite ok. I have a special key (Fn+F7) to switch display modes. This works without any further intervention in Windows, but in Ubuntu a Gnome-Message pops up saying "Could not switch the monitor configuration". In the "Nvidia X Server Settings" I can detect the monitor and enable it. But the maximum selectable resolution is 1152x864 (or 1360x768 ), the monitor's native resolution does not show up. When I select 1152x864, the screen can be enabled without any problems and extends my desktop just as it should.

In short, the functionality I would like to have is the following:
- Working key combo to switch between "single monitor" and "extended desktop"
- Native resolution on attached display, or at least a way to select the right resolution manually

I've tried with "gnome-randr-applet", which gives me an exhaustive list of resolutions, but simply does nothing at all (not even activating the selected option button) if click some different resolution. read-edid seems to have trouble getting the EDID of the external monitor, it says "Function supported, call failed" for the second block.

The issues are not crucial for me, but it would be very nice if it just worked as in the OS which must not be named ;)
I have basic knowledge of messing around with the CLI and Linux in general, but not with the x-server and all of it's settings.

Any help will be greatly appreciated.

Regards,
Philipp

---

### Post by phlibi on 2010-12-05
Hi folks,

I've just managed to get the whole stuff running almost as I want it :)

Maybe it helps anyone, so here's a quick overview of the steps I needed to perform.
Important: I've installed the nvidia-proprietary-driver, so this may or may not work with other drivers/graphics cards.

At first, I had to figure out how this metamode-stuff works with nvidia-xserver-settings. It is not quite obvious, since it is not possible to edit the lines in text-mode, but you have to create a new one ("Add") and then make the appropriate changes to the monitor setup. So here is how I did it:
1. Start nvidia-xserver-settings from System>Administration>"NVIDIA X Server Settings".
2. Select "X Server Display Configuration".
3. Connect your external monitor/projector if not done already.
4. Hit "Detect Displays" to get the external monitor showing up.
5. Select the "X Screen" tab and click "Advanced..." to gain access to the metamode settings.
6. Hit "Delete" until only one MetaMode is present any more.
7. Configure the screen setup for the first MetaMode. This will most likely be a single-screen setup. However, it won't work if you Configure>Disable the external monitor. Just set it to TwinView and choose "Off" as resolution.
8. Go to the "X Screen" tab again and create a new MetaMode. It will copy the previous options.
9. Create the screen layout for this mode. Don't worry if you can't select the correct resolution for your external monitor, we will address this problem afterwards.
10. Do steps 8 and 9 until you have created all the necessary MetaModes.
11. Select "Save to X Configuration File" and ignore inconsistencies if it complains. Let it save the file as "/etc/X11/xorg.conf" (which is the default) and remove the "Merge with existing file" if you have not changed anything manually that needs to be persistent.
12. You should now have a good xorg.conf for further improvements, so close the Settings-Window.

After having done this, I thought I could just modify the xorg.conf and everything would be fine. This was true until I restarted X (by logging out or rebooting) without having the external monitor connected. After doing so, the xorg.conf was still the same, but all the metamodes were lost. This seemed to happen because X could no longer detect the external monitor and therefore regarding the MetaModes with "CRT:..." in them as invalid. After searching for the cause of this problem I stumbled over the "ConnectedMonitor" option in [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9742/README/appendix-d.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9742/README/appendix-d.html)
This looked as if it could quite nicely address this problem and, well, it did :)
So let's mess around with xorg.conf a bit:
13. Fire up a terminal (Applications>Accessories>Terminal) and create a backup of xorg.conf, then open xorg.conf as root with your favourite editor, e.g. gedit:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```14. Scroll down until you find "Section "Screen"" with "Option "metamodes" "..."".
15. Update the metamodes-line to fit your needs. Check below for an example.
16. Scroll to "Section "Device"" and add the line
```
Option "ConnectedMonitor" "DFP,CRT"
```to it. This will cause X to detect an external monitor even if none is present.
17. Test the configuration: Save the file, close all open applications, disconnect the external monitor and log out.
18. If X refuses to start, you have made a mistake while editing xorg.conf. Let it recreate the config file if it offers this option. Otherwise, switch to another virtual Terminal (Ctrl+Alt+F1 for example), log in and run
```
sudo dpkg-reconfigure xserver-xorg
```This will create a completely new xorg.conf with default values which should allow X to start again. It will also overwrite all your changes, so you have to start again at point 1 if you have not backed up your xorg.conf before...
19. If everything went fine, start again the Nvidia-X-Settings.
20. Check the "X Screen" tab for your configured MetaModes. They should all show up in the list and be selectable even without an external monitor being present. Try them by selecting and hitting "Apply". You should now also be able to connect and disconnect your monitor without any problem, it should display a picture if you select the appropriate MetaMode and go blank if you select the "Internal-Only" MetaMode.
21. If all this works, it's now a good time to relax and feel a bit lucky :)

At this point, the "hard work" is done. What would be a good idea now could be to install grandr, a little applet (named "Display Geometry Switcher") to be able to easily switch between the different display modes without having to start the nvidia-settings.

Maybe it is helpful to have an example xorg.conf, so here is the one I currently use:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010

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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LEN"
    HorizSync       56.5 - 67.8
    VertRefresh     40.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 880M"
    Option         "NoLogo" "1"
    Option         "ConnectedMonitor" "DFP,CRT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0; DFP: nvidia-auto-select +0+0, CRT: 1280x1024 +1920+0; DFP: 1280x1024 +0+0, CRT: 1280x1024 +0+0; DFP: nvidia-auto-select +0+0, CRT: 1024x768 +1920+0; DFP: 1024x768 +0+0, CRT: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```As you can see, I have the following metamodes configured:
```

DFP: nvidia-auto-select +0+0;  (Internal only)
DFP: nvidia-auto-select +0+0, CRT:  1280x1024 +1920+0;  (Extended desktop on 1280x1024-monitor)
DFP: 1280x1024 +0+0, CRT: 1280x1024 +0+0;  (Cloned output with 1280x1024)
DFP: nvidia-auto-select +0+0, CRT: 1024x768 +1920+0;  (Extended desktop on 1024x768-monitor)
DFP: 1024x768 +0+0, CRT:  1024x768 +0+0  (Cloned output with 1024x768)

```**Known issues:**
- The login screen looks a bit weird, since it seems to use 1280x1024 (on my setup)
- The output-switcher-shortcut (Fn+F7) only works partly, it can't select some of the modes
- There seem to be problems with some external devices. The computer once or twice got terribly slow after having changed to some different MetaMode, but mostly it works fine.
- Maybe things I haven't noticed yet...

Hopefully this was of any help to someone.

Best regards,
Philipp

---

