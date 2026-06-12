---
title: "NVIDIA Hell"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by Megatog615 on 2007-04-23
I have an NVIDA Geforce MX 4000 AGP card and I simply cannot get the nvidia drivers to work at all. Right now, the error is this(xorg crash):
```
FATAL: Could not open '/lib/modules/2.6.20-15-generic/volatile/nvidia.ko': No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
```

Using the nvidia-glx package(for 9631).

---

### Post by Syke on 2007-04-23
Yeah, i had the same problems with that version in the repositories. Running the Nvidia installer worked tons better, and it's a newer version.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by psmar on 2007-04-23
> **Megatog615 said:**
> I have an NVIDA Geforce MX 4000 AGP card and I simply cannot get the nvidia drivers to work at all. Right now, the error is this(xorg crash):
```
FATAL: Could not open '/lib/modules/2.6.20-15-generic/volatile/nvidia.ko': No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
```

Using the nvidia-glx package(for 9631).

Just shared your fun last night. I ended up doing a xorg reconfigure setting my vid to vesa and only then could I get the nvivia-glx to connect in the Restricted Drivers Manager, Not sure if it pertains to your problem but I felt I should share what turned out to be my fix  Good Luck

---

### Post by hyperair on 2007-04-23
Do a "dmesg | grep -i nv" and get the error messages. It's excellent for troubleshooting.

---

### Post by Megatog615 on 2007-04-23
Well since the card is a Geforce MX 4000, I have to use the 96xx driver since it's unsupported in the 97xx drivers, so that rules out need for nvidia-glx-new package.

---

### Post by Neecapp on 2007-04-23
You might need the Nvidia-glx-legacy.

As the MX4000 is an older card.. it is now.. as previously stated.. unsupported in the newer versions of the Nvidia Driver series.

Utilizing the Legacy driver should cure your sorrow.

Best of Luck,
-Neecapp

---

### Post by Megatog615 on 2007-04-24
I have considered the legacy driver, however I do not think it will solve my problem because of the error I am getting.
I think the Ubuntu team may have messed up the nvidia-glx package, or just support for that package altogether.

---

### Post by hyperair on 2007-04-24
@Megatog615, please refer to my previous post: Do a "dmesg | grep -i nv" and get the error messages. It's excellent for troubleshooting.

Could you do that and post the output here? 

Also try executing this command in the terminal:
sudo sh -x /sbin/lrm-video nvidia

and post the output here.

EDIT: Also, open the /etc/default/linux-restricted-modules-common and if you see a DISABLED_MODULES="nv", delete that line and restart your system.

---

### Post by electronikjunkie on 2007-04-24
Why don't you try envy.

---

### Post by hyperair on 2007-04-24
While Envy may just work, all it does is get the nVidia installers from the nVidia web site, and downloads and installs it for you automatically. It will not fix your problems, however, if your computer is loading the wrong modules (which it probably is).

I thought Ubuntu had messed up the nvidia-glx package, but in reality, it's not the nvidia-glx package that's messed up, but the nvidia-glx-new and nvidia-glx-legacy packages that are messed up. They introduce files .nvidia_new_installed and .nvidia_legacy_installed in the /etc/linux-restricted-modules folder, causing this problem to occur as well.

---

### Post by Megatog615 on 2007-04-24
It seems every time I reboot it is a different error(in a pool of 3 or so).

Also, I recently downgraded to an NVIDIA Geforce2 GTS(which uses the legacy driver) and get the same thing. Just to let you know from the dmesg log.

The dmesg log is *very* weird. I have no idea why it is trying to load the 9755 driver when I have the legacy driver installed. Something is very wrong with the Legacy and New packages.

---

### Post by hyperair on 2007-04-25
lrm-video is loading the correct module, so that really doesn't explain why it still tries to load the nvidia-new kernel module.

Could you try executing these commands:
sudo modprobe nvidia (try this first)

and sudo modprobe nvidia-legacy

and post the outputs here?

If those two don't work, try this:
sudo dpkg-reconfigure linux-restricted-modules-`uname -r` and then try again, and post the outputs.

---

### Post by kleeman on 2007-04-25
I am having this problem as well. Originally I had the nvidia-glx package installed and it worked fine. Foolishly I decided to try the nvidia-glx-new package instead. It did not work but when I reverted to nvidia-glx X refused to start. I notice that I have the file  

/lib/linux-restricted-modules/.nvidia_new_installed

even though nvidia-glx is installed. What exactly does this do? I checked dmesg as you suggested and it tries to load the new and legacy drivers. Could one change the name of 

/lib/linux-restricted-modules/.nvidia_new_installed

to

/lib/linux-restricted-modules/.nvidia_installed

Edit: There seems to be a bug in nvidia-glx-new causing this which has been confirmed:

[https://bugs.beta.launchpad.net/ubuntu/+bug/106217](https://bugs.beta.launchpad.net/ubuntu/+bug/106217)

The fix is to remove the file 

/lib/linux-restricted-modules/.nvidia_new_installed

I'll try that and report back

---

### Post by hyperair on 2007-04-25
> **kleeman said:**
> I am having this problem as well. Originally I had the nvidia-glx package installed and it worked fine. Foolishly I decided to try the nvidia-glx-new package instead. It did not work but when I reverted to nvidia-glx X refused to start. I notice that I have the file  

/lib/linux-restricted-modules/.nvidia_new_installed

even though nvidia-glx is installed. What exactly does this do? I checked dmesg as you suggested and it tries to load the new and legacy drivers. Could one change the name of 

/lib/linux-restricted-modules/.nvidia_new_installed

to

/lib/linux-restricted-modules/.nvidia_installed

Heheh, here we go, someone who foolishly did what I did :lolflag: 

Ok.. firstly: delete .nvidia_new_installed
.nvidia_new_installed is actually a file created by nvidia-glx-new package to tell /sbin/lrm-video to load the nvidia-new module instead of the regular nvidia module. For some reason they didn't make the nvidia-glx-new package remove it when you uninstall the package. Stupid move, if you ask me.
There's also .nvidia_legacy_installed which is a file created by nvidia-glx-legacy, and yes, you got it.. not removed by nvidia-glx-legacy when removed. 

Try restarting your X server now with nvidia enabled and if it doesn't work, hunt down..
/etc/default/linux-restricted-modules-common
If you see a line there DISABLED_MODULES = "nv" or DISABLED_MODULES = "bla bla bla nv bla bla bla"

Remove nv from the list. That was added by the nvidia installer (if you used it before). Then restart your system. Hopefully it'll work. If it doesn't come back here with a "dmesg | grep nv" output and an output of sudo modprobe nvidia (try this first) as well as sudo modprobe nvidia_legacy

---

### Post by kleeman on 2007-04-26
OK I appear to be fine now. 

There was one final weird wrinkle that others may find interesting: I got a PCI bus error in my Xorg.log file just before the end and then an (EE) message saying no devices. The PCI bus the driver was looking for was 1:0:0 but in my /etc/X11/xorg.conf I had 0:5:0 (in the nvidia device section of the file). I switched to 1:0:0 as per the log message and now things work.

The developers really need to sort this mess out imo. The whole point of the restricted-manager was to allow noobs to use proprietary drivers. I am not a noob and had trouble with nvidia.  Ergo there is a big problem.....

---

### Post by hyperair on 2007-04-26
PCI Bus error eh, that usually is fixed by a "sudo dpkg-reconfigure xserver-xorg"

---

### Post by Megatog615 on 2007-04-26
```
sudo dpkg-reconfigure linux-restricted-modules-`uname -r`
```Seems to have worked after I deleted .nvidia_new_installed. Now I will try installing nvidia-glx for my other card.

---

### Post by hyperair on 2007-04-26
You should try restarting your system first. If you have used the nVidia binary installers before this, you may face YET another bug. That bug causes the nvidia.ko and nvidia_legacy.ko to not be copied over to /lib/modules/`uname -r`/volatile. And again you'll face an error. Here's the fix: look into your /etc/default/linux-restricted-modules-common and remove "nv" from the list of DISABLED_MODULES.

---

### Post by RAKninja on 2007-04-26
I'm having similar problems, but i have the added problems of an integrated intel gfx chip.  after much tinkering i can get signal though my PCI GeForce6200 (though BIOS is set to integrated gfx, if i change gfx settings in BIOS, i crash during boot with page faults)  but there is no GLX while doing it that way.  I'm new to Ubuntu but have a passing education in GNU/Linux.

---

### Post by alainhenry on 2007-04-27
Great!.  i had a similar problem.  After installing Feisty with a Geforce4 MX 4000 AGP 8x, I tried nvidia-glx and nvidia-glx-new.  After what the nvidia driver could not be recognised anymore.  Thus
-  I removed the /lib/linux-restricted-modules/.nvidia_new_installed, 
- re-installed the nvidia-glx package (using the restricted drivers manager)
- restarted the computer
And it went OK.  But
My screen resolution is limited to 1024x... , while with the same computer and Edgy, I could use 1280x....  
I remember seeing a discussion on this in another thread.  I'll investigate again.

Thanks

Alain
Edit: I did a "sudo dpkg-reconfigure xserver-xorg" and manually added the 1280x1024 resolution I know my monitor supports and it went fine.

---

### Post by hyperair on 2007-04-27
Next time you could try using the Nvidia Settings tool.

---

### Post by RAKninja on 2007-04-27
as a listed fix, i tried it with no success.

---

### Post by Megatog615 on 2007-04-29
Yes, it's the dreaded "Cannot find any NVIDIA GPU's on display #", which I have too.

---

### Post by johngrinham on 2007-04-30
So those of us who own a geforce mx4000 can only run beryl by downgrading from feisty to edgy ??? How do we do that ???

---

### Post by hyperair on 2007-04-30
It is not about downgrading Feisty to Edgy. There is no way. It's about using the nvidia-glx package instead of the nvidia-glx-new

---

### Post by johngrinham on 2007-05-01
Great.! Which tutorial tells me how to do that. I've tried probably more than ten times to install aiglx and beryl. So far each and every attempt has ended with the same text only page saying that it has failed, and I have to replace 'nvidia' with 'nv' in xorg.conf to regain a desktop.
It took me probably two attempt to get it working under edgy, but it appears I haven't even come close with feisty. I've tried numerous sets of instructions from different web sites, I've used envy both automated and manually. I've tried to turn it on through the beryl interface. I'm running out of things to try. Are there any geforce mx4000 users out there who have succeeded in getting aiglx working under feisty? If so please tell me how.

---

### Post by hyperair on 2007-05-01
I'm running a Geforce 4 MX 440, and installed from the repository, and all works fine for me. Could you provide a more comprehensive explanation about your problem? Your description seems at best very general. 

If you get any error messages of any sort, please describe or copy paste the error message here. From your description I can't even tell if your driver is working fine.

If possible please post the output of the following codes:
1. ```
dmesg | grep nv
```
2. ```
cat /etc/X11/xorg.conf
```
3. ```
sudo modprobe nvidia
```
4. ```
sudo modprobe nvidia-legacy
```
5. [code]sudo modprobe nvidia-new[/code

Also, please provide the full name of your card. For example: "nVidia Geforce 4 MX 440 AGP 8x"

---

### Post by johngrinham on 2007-05-02
This is the message I get every time. (it's in a text out lined box)


Failed to start the X server (your graphical
interface). It is likely that it is not set
up correctly. Would you like to view the X
server output to diagnose the problem?

    <YES>               <NO>

dmesg | grep nv - produces

[   48.956295] nvidia: module license 'NVIDIA' taints kernel.
[   48.963251] NVRM: visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[   49.109731] NVRM: visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[   61.956099] NVRM: visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[   66.193762] NVRM: visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[   70.392683] NVRM: visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more


cat /etc/X11/xorg.conf produces

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        Fontpath        "/usr/share/X11/fonts/misc"
        Fontpath        "/usr/share/X11/fonts/cyrillic"
        Fontpath        "/usr/share/X11/fonts/100dpi/:unscaled"
        Fontpath        "/usr/share/X11/fonts/75dpi/:unscaled"
        Fontpath        "/usr/share/X11/fonts/Type1"
        Fontpath        "/usr/share/X11/fonts/100dpi"
        Fontpath        "/usr/share/X11/fonts/75dpi"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "type1"
        Load            "vbe"
        Load            "dbe"
        Load            "dri"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"

        # /dev/input/event
        # for USB
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/wacom"# Change to
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

        # /dev/input/event
        # for USB
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/wacom"# Change to
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

        # /dev/input/event
        # for USB
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/wacom"# Change to
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "AOC Spectrum"
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Driver          "nvidia"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
        Option          "XAANoOffScreenPixmaps"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Monitor         "AOC Spectrum"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"
        Option          "XAANoOffscreenPixmaps"
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

Section "DRI"
        Mode 0666
EndSection


sudo modprobe nvidia produces

FATAL: Error running install command for nvidia

sudo modprobe nvidia-legacy produces

FATAL: Error running install command for nvidia-legacy

sudo modprobe nvidia-new produces
FATAL: Error running install command for nvidia-new

Card description, nVIDIA
Geforce MX4000 GPU
64MB/128MB Fast Video DDR Memory
Low-Profile support
nVIEW  3.0 - Best Multi-Display Solution

I hope this makes sense to you. :)

---

### Post by hyperair on 2007-05-02
Holy shi-*!!
I've never seen such weird error messages before (regarding dmesg | grep nv)

Anyway, it seems that it isn't even trying to load the kernel module, are you sure your xorg.conf is fine? Try doing this:
```

sudo apt-get install nvidia-glx-new

```

and repost the same logs again, with this as well:
```

cat /var/log/Xorg.0.log

```

Also, this time, please pack each of them in separate text files and include them as attachments. Scrolling to and fro was a nightmare >.<

---

### Post by johngrinham on 2007-05-04
Ok, here tis
two attachments,

But this was too big apparently

john@john-studio-ubuntu:~$ cat /var/log/Xorg.0.log

---

### Post by hyperair on 2007-05-04
Do this:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```

and restart your X server, and post the logs again. This time, instead of posting the entire Xorg.0.log, use
```

cat /var/log/Xorg.0.log | grep nv

```

---

