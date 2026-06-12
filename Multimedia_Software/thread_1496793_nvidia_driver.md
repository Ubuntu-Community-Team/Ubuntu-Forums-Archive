---
title: "nvidia driver"
date: 2010-05-29
forum: Multimedia Software
---

### Post by rickdavis on 2010-05-29
I'm in the process of installing a video driver. So far I've done the whole hardware driver bit where it downloaded and installed the recommended driver. However, upon restart I get an error screen telling me it's entering into low graphics mode. I'm a a loss here. I'm only mildly tech savy so it's getting a little frustrating. Does anyone have a suggestion?

---

### Post by lrgmmc on 2010-05-29
well just need to know a few things. video card and which ubuntu you running ? and is it 32 bit or 64 bit?

---

### Post by rickdavis on 2010-05-29
ive got the nvidia geforce 7900 gt and I think ive just got standard ubuntu

---

### Post by lrgmmc on 2010-05-29
did you use the built in driver installer from ubuntu or go to nvidia website and download them that way?

---

### Post by rickdavis on 2010-05-29
i did the built in driver installation.

---

### Post by lrgmmc on 2010-05-29
are you on the machine that u need drivers for or on a diffrent machine. the processe is goin to be done through shell.i had the same problem.

---

### Post by rickdavis on 2010-05-29
im on the machine that i need the driver for. it seemed like it installed fine but when i restart is when the problems arise.

---

### Post by lrgmmc on 2010-05-29
ya same here. it has to do with kernel module. i will start typing it up or mabe find the source of the info i have and post for you. i hope you have a printer.

---

### Post by rickdavis on 2010-05-29
haha I do but no ink. Regardless I really appreciate the help.

---

### Post by lrgmmc on 2010-05-29
the driver you want is here[HTML] http://us.download.nvidia.com/XFree86/Linux-x86/195.36.24/NVIDIA-Linux-x86-195.36.24-pkg1.run
[/HTML]
download that and make it executable.
[]("http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/195.36.24/NVIDIA-Linux-x86-195.36.24-pkg1.run&lang=us&type=GeForce")

---

### Post by rickdavis on 2010-05-29
okay its got about 20 min. for the download. Now how do i go about making that executable? This is my first time with ubuntu or any linux for that matter.

---

### Post by lrgmmc on 2010-05-29
is it downloading to your downloads folder? if so when it is done open up a terminal shell. applications ---> accessories ---> Terminal. then type this into there. ```
cd Downloads
chmod +x ./NVIDIA-Linux-x86-195.36.24-pkg1.run
```

---

### Post by rickdavis on 2010-05-29
I entered that into the terminal and got this message: chmod: cannot access `/NVIDIA-Linux-x86-195.36.24-pkg1.run': No such file or directory

I dont understand this I'm looking at the file in the downloads folder right now

---

### Post by rickdavis on 2010-05-29
i just retried it and this time after pressing enter it just went to the next line...

---

### Post by lrgmmc on 2010-05-29
now the next parts are a little much but i'll help you through it. it will be a good learning experience.

blacklist the following by adding them to the end of this file.
in terminal 
```
gsudo gedit /etc/modprobe.dblacklist.conf
```and add this to that file
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

---

### Post by lrgmmc on 2010-05-29
its ```
./NVIDIA-Linux-x86-195.36.24-pkg1.run
``` the dot before the slash is important.

---

### Post by rickdavis on 2010-05-29
this is what my terminal looks like. I'm at a loss 
alex@alex-desktop:~$ cd Downloads
alex@alex-desktop:~/Downloads$ chmod +x ./NVIDIA-Linux-x86-195.36.24-pkg1.run
alex@alex-desktop:~/Downloads$ gsudo gedit /etc/modprobe.dblacklist.conf
No command 'gsudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'gksudo' from package 'gksu' (main)
gsudo: command not found
alex@alex-desktop:~/Downloads$ blacklist vga16fb
blacklist: command not found
alex@alex-desktop:~/Downloads$

---

### Post by lrgmmc on 2010-05-29
sorry my typo ```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

---

### Post by rickdavis on 2010-05-29
okay i got the blacklist.conf open and now i just throw this in there wherever and press save?
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

---

### Post by lrgmmc on 2010-05-29
yes and make sure that at the end of the file you have a blank line.

---

### Post by rickdavis on 2010-05-29
done and done. wha'ts next?

---

### Post by lrgmmc on 2010-05-29
then in terminal ```
sudo apt-get --purge remove nvidia-*
```

---

### Post by rickdavis on 2010-05-29
okay it looks like everything was removed just fine.

---

### Post by rickdavis on 2010-05-29
here's what it gave me after that last command:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-180-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-185-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-173-dev for regex 'nvidia-*'
Note, selecting nvidia-current for regex 'nvidia-*'
Note, selecting nvidia-libvdpau-ia32 for regex 'nvidia-*'
Note, selecting nvidia-libvdpau1 for regex 'nvidia-*'
Note, selecting nvidia-glx-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-185-dev for regex 'nvidia-*'
Note, selecting nvidia-173 for regex 'nvidia-*'
Note, selecting nvidia-settings for regex 'nvidia-*'
Note, selecting nvidia-185-libvdpau for regex 'nvidia-*'
Note, selecting nvidia-185-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-vdpau-driver for regex 'nvidia-*'
Note, selecting nvidia-96-dev for regex 'nvidia-*'
Note, selecting nvidia-cg-toolkit for regex 'nvidia-*'
Note, selecting nvidia-96 for regex 'nvidia-*'
Note, selecting nvidia-glx-96-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-173 for regex 'nvidia-*'
Note, selecting nvidia-glx-180 for regex 'nvidia-*'
Note, selecting nvidia-glx-185 for regex 'nvidia-*'
Note, selecting nvidia-180-modaliases for regex 'nvidia-*'
Note, selecting nvidia-kernel-common for regex 'nvidia-*'
Note, selecting nvidia-libvdpau for regex 'nvidia-*'
Note, selecting nvidia-current-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-96 for regex 'nvidia-*'
Note, selecting nvidia-glx-180-dev for regex 'nvidia-*'
Note, selecting nvidia-current-modaliases for regex 'nvidia-*'
Note, selecting nvidia-173-modaliases for regex 'nvidia-*'
Note, selecting nvidia-185-modaliases for regex 'nvidia-*'
Note, selecting nvidia-common for regex 'nvidia-*'
Note, selecting nvidia-96-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-173-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-180-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-96-modaliases for regex 'nvidia-*'
Note, selecting nvidia-glx for regex 'nvidia-*'
Note, selecting nvidia-173-dev for regex 'nvidia-*'
Note, selecting nvidia-180-libvdpau for regex 'nvidia-*'
The following packages will be REMOVED:
  nvidia-173* nvidia-173-modaliases* nvidia-185-modaliases*
  nvidia-96-modaliases* nvidia-common* nvidia-current*
  nvidia-current-modaliases* nvidia-settings*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 108MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 145482 files and directories currently installed.)
Removing nvidia-173 ...
Removing all DKMS Modules
Done.
Purging configuration files for nvidia-173 ...
dpkg: warning: while removing nvidia-173, directory '/usr/lib/nvidia-173/tls' not empty so not removed.
dpkg: warning: while removing nvidia-173, directory '/usr/lib/nvidia-173' not empty so not removed.
Removing nvidia-common ...
Purging configuration files for nvidia-common ...
Removing nvidia-173-modaliases ...
Removing nvidia-185-modaliases ...
Removing nvidia-96-modaliases ...
Removing nvidia-current ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching gl_conf to auto mode
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
Purging configuration files for nvidia-current ...
dpkg: warning: while removing nvidia-current, directory '/usr/lib/nvidia-current/tls' not empty so not removed.
dpkg: warning: while removing nvidia-current, directory '/usr/lib/nvidia-current' not empty so not removed.
Removing nvidia-current-modaliases ...
Removing nvidia-settings ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...
alex@alex-desktop:~/Downloads$

---

### Post by lrgmmc on 2010-05-29
ok now the next stuff you will need to do your gonna want to write down. your gonna need to reboot and then from the grub menu choose recovery mode. then in the selection menu chose "drop to root shell" then in the terminal ```
init 3
``` then install the driver with ```
cd /home/yourusername/Downloads/
sudo sh ./NVIDIA-Linux-x86-195.36.24-pkg1.run
``` replace yourusername with yours then when that is done reboot.
```
sudo shutdown -r 00
```

---

### Post by rickdavis on 2010-05-29
okay now what is the grub menu and how do i access it?

---

### Post by lrgmmc on 2010-05-29
when you reboot it shows a list of avalible operating systems. if you dont see it hold shift after your pc reboots and the you should see it. somthing like [I]Ubuntu, Linux 2.6.32-15-generic recovery. just chose the highest number. 2.6.xx-x
[/I]

---

### Post by rickdavis on 2010-05-29
after I typed sudo sh ./NVIDIA-Linux-x86-195.36.24-pkg1.run i got a screen that said ERROR: nvidia-installer must be run as root

---

### Post by lrgmmc on 2010-05-29
and that was done in recovery mode?

---

### Post by rickdavis on 2010-05-29
yeah everything seemed to be gong smoothly as far as following your instructions went

---

### Post by lrgmmc on 2010-05-29
try it with out the sh ```
sudo ./NVIDIA-Linux-x86-195.36.24-pkg1.run
```
oh and you logged in after typing init 3 right?

---

### Post by rickdavis on 2010-05-29
yeah. ill give that a try

---

### Post by rickdavis on 2010-05-29
okay it installed, however upon reboot i got the same error message, it reads:
Your GeForce 7900 GT/GTO graphics card does not have the necessary external power cables attached. X will not start unless this is rectified. Please shut down your computer, open its case and attach the appropriate power connectors. Your video card may have multiple power connectors. If so, each must be attached to a separate power cable. Please see the documentation provided with your video card for more details. If you think you received this message as an error, you may specify the "NoPowerConnectorCheck" X configuration option in the Screen section of your X config file.

I could be mistaken but everything looks plugged in in there. A friend built my pc and its his old video card so i dont have the documentation for it. What do you suggest I do?

---

### Post by lrgmmc on 2010-05-29
in the terminal do ```
gksudo gedit /etc/X11/xorg.conf
``` and past that here

---

### Post by rickdavis on 2010-05-29
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
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

---

### Post by lrgmmc on 2010-05-29
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

to 

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
Option "NoPowerConnectorCheck" "true"
EndSection

just add Option "NoPowerConnectorCheck" "true"

---

### Post by rickdavis on 2010-05-29
done, now save and restart?

---

### Post by lrgmmc on 2010-05-29
yes. and dont forget ... cross your fingers lol

---

### Post by rickdavis on 2010-05-29
I think were good. I got no error messages or anything like that. Now is there any way to double check that everything's working now?

---

### Post by lrgmmc on 2010-05-29
run ```
glxinfo | grep "direct rendering"
``` from terminal and past the output

---

### Post by rickdavis on 2010-05-29
alex@alex-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
alex@alex-desktop:~$

---

### Post by lrgmmc on 2010-05-29
congrats my friend you have now installed nvidia drivers. you can adjust the setting with ```
*nvidia*-*settings*
``` in terminal.

---

### Post by rickdavis on 2010-05-29
Thank you, thank you, thank you! I cant tell you how much I appreciate the help, finally videos without the heavy lag haha

---

### Post by lrgmmc on 2010-05-29
if you still get video tearing while watching videos run the *nvidia*-[I]settings and go through and make sure sync on black is checked. i think the are to places where it needs to be checked.
good luck and enjoy the many benefits of linux!!!
[/I]

---

