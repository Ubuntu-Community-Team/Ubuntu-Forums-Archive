---
title: "Ati Radeon 9250"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by Tulio on 2006-08-10
Hi, sorry if you don't understand me but I don't speak english very well (I'm Pole/Polish man). It's my problem:

I try install drivers to my graphic card (look title) but i have many problems, I try install from this tutorials:


[first link]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=9250")
But I saw this (when I wrote fglrxinfo):
```
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1) 
```

so I search next how-to

[Second link]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")
after I used first method, I have black screen when I restarted computer
after I used second method, I still have Mesa (when I wrote fglrxinfo)

I fixed next how-to (in polish language)

[Third link]("http://forum.ubuntu.pl/viewtopic.php?t=1772")

unfortunately, when I used first method, I got this (when I wrote glxinfo):
"direct rendering: No"
I didn't used second method, because my card graphic is not on the list (Product Support)
when I use third method I got again this problem:
"direct rendering: No"

I wrote on polish ubuntu forum but they didn't knowed what I should do with this problem

ps. I don't know how but I have in Accesories "Ati Control" but still armagetron have only 20FPS and I have "Mesa" (and "direct rendering: No")

Thanks, Tulio

---

### Post by Greycloak on 2006-08-10
Try the howto here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

This worked fine for my Radeon 9200 PCI.

---

### Post by Tulio on 2006-08-10
> Then you can simply install the ubuntu-fglrx-$arch (see above for the meaning of $arch) package.

what is it --> "$arch"?

---

### Post by reubadoob on 2006-08-10
I also have a ATI 9250 PCI card and was considering also considering re-installing it ( I removed it during my prior to instaling Ubuntu). I was justing wondering if anyone had completed the install and what were some recommended steps in doing so. Another reason I ask is because I would LIKE to run XGL/Compiz. I've taken a look at the [list of hardware supported under XGL]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL") and from what I read everything should go smoothly. But please let me know of anythign I should be wary off.

---

### Post by jtbalt on 2006-08-10
I got my Radeon 9800 Pro up and running with ATI drivers and XGL/compiz.  But my other box has a 9250 and while I can install the ATI drivers, XGL just won't go.  It seems to go flawlessly through the install, but upon rebooting and selecting the XGL session, nothing other than the regular interface.  The process I followed was that posted by RacerII, his "second method."  I'm still messing around with it but so far no luck.

---

### Post by Ziox on 2006-08-10
for those who are talking about compiz, which if I remember correctly is effects such as Transparency and such, should considering install the XFCE4 windows manager.  It has better support than the windows manager for gnome

---

### Post by Tulio on 2006-08-11
heh... $arch = my architecture procesor.
But still my card graphics is not work (after using "Install instructions for Ubuntu 6.06 (Dapper Drake)" and "Using the drivers from ati.com" from link [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI))

in fglrxinfo i have "Mesa" and "direct rendering: No" in glxinfo.

---

### Post by Redys on 2006-08-11
I have exactly the same problem (with Radeon 9250)

---

### Post by Greycloak on 2006-08-11
Take a look here:

[http://www.ubuntuforums.org/showthread.php?t=204910&highlight=radeon+fglrx](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=radeon+fglrx)

Download the 8.27.10 drivers from ATI. Just make sure to substitute 8.27.10 for 8.26.18.

---

### Post by reubadoob on 2006-08-12
I have a feeling I will have to make that subsitution so how do I do that?

---

### Post by Greycloak on 2006-08-12
> **reubadoob said:**
> I have a feeling I will have to make that subsitution so how do I do that?

Visit the link I posted above and wherever it references 8.26.18, change it to 8.27.10.

Download the drivers here:

[https://www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run](https://www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run)

Here is fitzman49's original post, edited by me to reflect the 8.27.10 drivers.

> Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

Install necessary tools:

```
sudo apt-get update 
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```



Create .deb packages:

```
chmod +x ati-driver-installer-8.27.10-x86.run
./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/dapper
```


Install .deb packages:

```
sudo dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb 
sudo dpkg -i fglrx-kernel-source_8.27.10-1_i386.deb 
sudo dpkg -i fglrx-control_8.27.10-1_i386.deb
```


Remove any old fglrx deb's from /usr/src/:

```
sudo rm /usr/src/fglrx-kernel*.deb
```


Compile the kernel module:

```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```


Note: You have to recompile the kernel module after each kernel update!

Update the xorg.conf file:

```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```


Reboot.

Confirm that it worked


```
[fitzy@greenmachine49]~ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series Generic
OpenGL version string: 2.0.5879 (8.27.10)
```

---

### Post by Tulio on 2006-08-12
Your link (and your latest post) Greycloak = Second method in my second link (in first post) and it didn't work... (still: Mesa, FPS<20, "direct rendering: No", etc.)

---

### Post by Redys on 2006-08-12
> **Greycloak said:**
> Take a look here:

[http://www.ubuntuforums.org/showthread.php?t=204910&highlight=radeon+fglrx](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=radeon+fglrx)

Download the 8.27.10 drivers from ATI. Just make sure to substitute 8.27.10 for 8.26.18.

it doesn't work

---

### Post by nimrod_abing on 2006-08-13
I have a PowerColor Radeon 9250 card and here's how I got GLX to work properly under Dapper.

The ATI drivers that ship with Dapper have a known bug that prevents GLX from working on rv2xx cards (Radeon 9200 series). But this bug is only in /usr/lib/libGL.so.1.2 and it is possible to replace this with a known good libGL.so.1.2 from an **older** ATI driver package.

If you have been trying (and failing) to install from the ATI packages prior to this, make sure you remove **all** of the gunk introduced into your system when you installed the ATI drivers from the ".run" packages. When you have done that and you have a clean system you **must** install the mesa libraries, the fglrx kernel modules, and fglrx xorg drivers for your specific architecture.

Open an terminal window.

Then download the file attached to this post and from your terminal window uncompress it:

```

bunzip2 libGL.so.1.2.bz2

```

Next do the following:

```

sudo cp libGL.so.1.2 /usr/lib/libGL.so.1.2
sudo ldconfig

```

Next you need to setup the environment variable to allow the libGL.so.1.2 to find the correct location of the xorg modules.

```

sudo gedit /etc/bash.bashrc
[CODE]

Add the following line at the end of the file:

[CODE]
[COLOR="Red"]export LIBGL_DRIVERS_PATH=/usr/lib/dri[/COLOR]

```

Save the file.

Logout of your current session and login again.

Your fglrxinfo should now report the correct strings for GLX.

Report success or failure on this thread. Good luck!

**NOTE 1:** It's probably a good idea to backup your old libGL.so.1.2. I did not do it here since it is possible to restore it by reinstalling the xorg-driver-fglrx package.

**NOTE 2:** I forgot the ATI driver version where I got this libGL.so.1.2 from, which is why I attached what's installed on my system. If you don't trust this file to be "clean", then whatever :roll: Go ahead download each of the ~60MB packages from ATI and extract the packages until you find the right libGL.so.1.2 that works for you. If you do this and you find the right ATI driver package, please post the driver package version that contains the working libGL.so.1.2 here so that others may benefit from your hard work :)

**NOTE 3:** If you want to play around with XGl and compiz, then be forewarned that compiz will probably SEGFAULT the first time you run it. If that's the case do:

```

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz.real --replace gconf

```

until your terminal seemingly locks up. On my system the terminal window will suddenly stop responding to keystrokes. Then press CTRL+Z and enter:

```

bg

```

If you haven't run gnome-window-decorator, then go do:

```

gnome-window-decorator

```

---

### Post by Tulio on 2006-08-14
It still not work nimrod_abing.
I write what have I done:

1. reinstall ubuntu
2. install packages: libgl1-mesa, fglrx-kernel-2.6.15-23-386, xorg-driver-fglrx
3. download file libGL.so.1.2.bz2
4. unzip file
5. paste this to terminal:
```
sudo cp libGL.so.1.2 /usr/lib/libGL.so.1.2
sudo ldconfig
```
6. open file "/etc/bash.bashrc"
7. paste this to file:
```
export LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri
```
8. save file
9. follow by Second Method in my Second link
10. reboot
11. type in terminal: fglrxinfo and I see:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
12. install and play game "supertux" (when I enabled OpenGL then FPS<15)
13. I delete "fglrx" in Disabled_Modules from  /etc/default/linux-restricted-modules-common but it still not work

my xorg.conf:
```

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
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "pl"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 85.0
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x768" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x768" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection

	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by nimrod_abing on 2006-08-14
> **Tulio said:**
> It still not work nimrod_abing.
9. follow by Second Method in my Second link


[-X You should not have done that! Replacing the libGL.so.1.2 that comes with the default xorg-driver-fglrx package for Dapper and setting up the appropriate environment variables is enough. **There is no need to install the LATEST official driver packages from ATI. In fact you should NOT do that if you have an rv2xx card because the new drivers contain a broken libGL.so.1.2**

Also no need to reboot your entire system after you have replaced the libGL.so.1.2 with the one I provided. All you need to do is logout then login again. Or simply ZAP the X server by pressing CTRL+ALT+Backspace, this will restart your X server and bring you back to the login screen. But ZAPPING might cause you to lose data so don't do that unless you are certain you have saved all documents you are working on.

In any case, since you have already messed up your system by installing the driver package from the ATI .run files. You should also be able to just drop in the replacement libGL.so.1.2 and then run ldconfig again.

So go into the folder where you unpacked the libGL.so.1.2, then do:

```

sudo cp libGL.so.1.2 /usr/lib/
sudo ldconfig

```

Then do the logout/login thing (or ZAP your X server) and your fglrxinfo should now report GLX from ATI.

**Troubleshooting Tips**

If you still get Mesa from fglrxinfo, try the following:

Change to the directory where you unpacked libGL.so.1.2, then do:

```

diff libGL.so.1.2 /usr/lib/libGL.so.1.2

```

If you get

```

Binary files libGL.so.1.2 and /usr/lib/libGL.so.1.2 differ

```

Then that means you have **not** replaced the libGL.so.1.2 in /usr/lib and you are still using the packaged version.

If you get no readout from the diff command that means your libGL.so.1.2 is good. Next try:

```

ls -l /usr/lib/libGL.so.1

```

You should get:

```

lrwxrwxrwx 1 root root 12 2006-07-12 12:39 /usr/lib/libGL.so.1 -> libGL.so.1.2

```

That is, the symlink /usr/lib/libGL.so.1 (which is what your GLX programs load into memory) **should** point to libGL.so.1.2. If the symlink points to something else (like say libGL.so.1.2.bak) then remove the file that is pointed to by libGL.so.1 and then run ldconfig again.

It is a very common mistake to place the backup of the old libGL.so.1.2 in the /usr/lib directory. ldconfig will **still** pick the backup over the (older) libGL.so.1.2 that I provided.

If everything is as it should be, enter:

```

env

```

and paste the output here. Then try:

```

LIBGL_DEBUG=verbose LD_PRELOAD=/directory/where/you/unpacked/libGL.so.1.2 fglrxinfo

```

And paste the output here. If the above command hangs (gives you 100% CPU usage and does not finish), you may need to ZAP your X server to clear out the ld cache. Then login and retry the command above.

Here is the sample output from my system using the fglrxinfo (with full debugging and ld preload):

```

[~]
nimrod@iwojima:$ LIBGL_DEBUG=verbose LD_PRELOAD=/usr/lib/libGL.so.1.2 fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/lib/xorg/modules/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)

```

---

### Post by Tulio on 2006-08-14
> **nimrod_abing said:**
> [-X You should not have done that! Replacing the libGL.so.1.2 that comes with the default xorg-driver-fglrx package for Dapper and setting up the appropriate environment variables is enough. **There is no need to install the LATEST official driver packages from ATI. In fact you should NOT do that if you have an rv2xx card because the new drivers contain a broken libGL.so.1.2**

So, I have to follow by first 8 points (1. reinstall ubuntu 2. install [...] 8. save file) next logout and login? enough?

> **nimrod_abing said:**
> [...] And paste the output here [...]

env:
```
tulio@tulio-desktop:~$ env
SSH_AGENT_PID=5571
TERM=xterm
SHELL=/bin/bash
GTK_RC_FILES=/etc/gtk/gtkrc:/home/tulio/.gtkrc-1.2-gnome2
WINDOWID=39846079
USER=tulio
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri
GNOME_KEYRING_SOCKET=/tmp/keyring-qmsw6R/socket
SSH_AUTH_SOCK=/tmp/ssh-UeKKxv5526/agent.5526
SESSION_MANAGER=local/tulio-desktop:/tmp/.ICE-unix/5526
USERNAME=tulio
DCOP_YAKUAKE_SESSION=0
KONSOLE_DCOP=DCOPRef(yakuake,konsole)
DESKTOP_SESSION=default
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
GDM_XSERVER_LOCATION=local
KONSOLE_DCOP_SESSION=DCOPRef(yakuake,session-1)
PWD=/home/tulio
LANG=pl_PL.UTF-8
GDMSESSION=default
HISTCONTROL=ignoredups
HOME=/home/tulio
SHLVL=1
LANGUAGE=pl_PL:pl:en_GB:en
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=tulio
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-lob5cszMmM,guid=d0dde04456b957508ff6c7f6f157d700
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=
XAUTHORITY=/home/tulio/.Xauthority
_=/usr/bin/env
```

LIBGL_DEBUG=verbose LD_PRELOAD=/directory/where/you/unpacked/libGL.so.1.2 fglrxinfo:

```
tulio@tulio-desktop:~$ LIBGL_DEBUG=verbose LD_PRELOAD=/directory/where/you/unpacked/libGL.so.1.2 fglrxinfo
ERROR: ld.so: object '/directory/where/you/unpacked/libGL.so.1.2' from LD_PRELOAD cannot be preloaded: ignored.
libGL error: XF86DRIQueryDirectRenderingCapable returned false
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by nimrod_abing on 2006-08-14
Hello,

> **Tulio said:**
> So, I have to follow by first 8 points (1. reinstall ubuntu 2. install [...] 8. save file) next logout and login? enough?


Yes.

But you **do not** really need to reinstall everything yet. As I have said earlier, since you have already installed the latest ATI drivers on your system, you might as well use them. **However, now you must manually re-install your ATI kernel modules with every ABI-breaking kernel update.**

An "ABI-breaking" kernel upgrade is one of those upgrades that places **another** kernel menu entry in your GRUB boot menu. If you upgraded your kernel and you don't see a new menu entry when you reboot, then you **do not** have to re-install your ATI kernel drivers.

If you want to "play it safe", you should clean up your system of any external or non-APT installed packages. This includes the ATI driver package that comes directly from the ATI website. In this case the best way to ensure that you have a clean system is to re-install Dapper. And this time **install packages via APT/Synaptic only**.

And when you have a clean installed system, I repeat: **do NOT install the ATI drivers from .run files**

But first, let's make do with what you currently have on your system. So basically, you have a clean installed system that has been updated plus ATI drivers installed via apt-get. Then you installed the drivers from ATI .run package.

This is your "env" output, which I trimmed a bit for brevity...

> **Tulio said:**
> 
env:
```
tulio@tulio-desktop:~$ env
...
[COLOR="Red"]LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri[/COLOR]
...
_=/usr/bin/env
```


Now judging from your "env" output, your environment variables are all in order and "LIBGL_DRIVERS_PATH" is set to the correct path on your system.

> **Tulio said:**
> 
LIBGL_DEBUG=verbose LD_PRELOAD=/directory/where/you/unpacked/libGL.so.1.2 fglrxinfo:


I see the problem here. You followed my instructions **too perfectly** ;) So I guess I will have to make them more clear and more copy/paste friendly...

Okay, assuming you **have not reinstalled yet** let's work with what you have right now. So your system already has the ATI drivers installed from .run packages. Note, if you receive any error messages while doing any of the steps below **STOP IMMEDIATELY**. Take a look at what the error message says and then carefully review your steps and make sure you have done everything correctly. If you cannot figure out what the error message means, then post it here so I can see what you are doing wrong.

**Step 1**

Download the libGL.so.1.2.bz2 I provided earlier in this thread. Then on your terminal window, go to the directory where you downloaded libGL.so.1.2.gz. For example, if you saved it in /home/tulio/downloads, then:

```

cd /home/tulio/downloads

```

Unpack libGL.so.1.2.bz2:

```

bunzip2 libGL.so.1.2.bz2

```

If you unpacked it properly, you will no longer have libGL.so.1.2.bz2 in your /home/tulio/downloads directory. It will contain **libGL.so.1.2**

While still in your terminal and with /home/tulio/downloads as your current working directory, proceed to step 2A.

**Step 2A**

Note, this assumes that you are still on the terminal **with /home/tulio/downloads** as your current working directory.

You should now copy the **unpacked** libGL.so.1.2 into /usr/lib. This requires **root** privileges. So assuming you are using the **first** account you created when you installed Ubuntu, enter:

```

sudo cp libGL.so.1.2 /usr/lib

```

This will overwrite the existing libGL.so.1.2 in your /usr/lib. Make sure that **NO** errors occur here and that the copy proceeds OK. When you are sure that you have copied libGL.so.1.2 to the correct location. Go and do:

```

sudo ldconfig

```

This will update the ld.so.cache that is used by the system to resolve dynamic library dependencies. Make sure that **NO** errors occur here either. To check if this is successful you will need to restart the X server. This is needed to make sure that your system is not using the previously cached copy of libGL.so.1.2 in memory.

**STEP 2B**
Logout of your current Gnome or KDE session. Then when you are at the login screen, press CTRL+ALT+BACKSPACE on your keyboard. Your screen should go back to text mode momentarily and then go back to GUI mode again.

**STEP 3A**

Now that you have overwritten libGL.so.1.2 and you have restarted the X server. Login to your account. Then open a new terminal window and enter:

```

cd /home/tulio/downloads

```

This will bring you back to the directory where you downloaded libGL.so.1.2. From here, you can try:

```

fglrxinfo

```

By now, it **should** correctly report that OpenGL vendor string is ATI.

**STEP 3B**

If you still get Mesa then try:

```

LD_PRELOAD=/home/tulio/downloads/libGL.so.1.2 LIBGL_DEBUG=verbose fglrxinfo

```

Post the output here. Note that in case the above command hangs up and gives you 100% CPU usage without finishing, press CTRL+C. Logout of your Gnome or KDE session then repeat STEP 2B and then repeat STEP 3B.

[COLOR="Red"]NOTES IF REINSTALLING UBUNTU[/COLOR]

If you decide you want to start with a clean install, then proceed with installation and package update as usual. Install the xorg-driver-fglrx and the restricted kernel modules for your system.

Then proceed to configure your X server as usual. I assume you know how to do this already since you have done it many times before :-D

At this point: [COLOR="Red"]DO NOT INSTALL ANYTHING FROM ATI .run PACKAGES![/COLOR]

Now follow the steps above **BUT STOP BEFORE STEP 2B** and do:

```

sudo gedit /etc/bash.bashrc

```

Add the following as the last line:

```

export LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri

```

Save the file. And reboot. **SKIP STEP 2B** and proceed to STEP 3A.

Good luck!

---

### Post by Tulio on 2006-08-15
I followed your instruction (without any errors) but in step 3A when I enter fglrxinfo in current dictionary, I got again "MESA"... I don't now, what I doing wrong...
Maybe, I done mistake when I translated your instruction to my language so You write me other instruction:
1. With only commands (minimal text) - without "install xorg-drivers-fglrx and kernel-modules" and "reboot" but "sudo apt-get install xorg-drivers-fglrx fglrx-kernel-2.6.15-23-386" and "sudo reboot"
2. In points (likewise I wrote)
3. with configuration x server (maybe I do something wrong with this)
4. begin since when I reinstall ubuntu and login to system (we started over)

And some questions:
1. "install fglrx kernel modules" is "fglrx-kernel-2.6.15-23-386"?
2. If point 1 is true: I have to install "fglrx-kernel-2.6.15-23-386" or "fglrx-kernel-2.6.15-26-686"? If in boot menu I have "[...]-2.6.15-23-386" but my architecture processor is 686. Maybe I must check it in other way?

---

### Post by nimrod_abing on 2006-08-15
> **Tulio said:**
> I followed your instruction (without any errors) but in step 3A when I enter fglrxinfo in current dictionary, I got again "MESA"... I don't now, what I doing wrong...
Maybe, I done mistake when I translated your instruction to my language so You write me other instruction:


I think you should get someone (a friend maybe) with better command of the English language to read and follow the instructions for you.

I wrote you a complete tutorial on how I got my Radeon 9250 card to work under Dapper and I think I wrote it in very, very simple terms that anyone who has ever installed a Linux system would understand.

I chose to write the steps along with a complete and non-technical explanation of what is going on so that you or anyone else reading this thread will know what exactly is going on.

> **Tulio said:**
> 
1. With only commands (minimal text) - without "install xorg-drivers-fglrx and kernel-modules" and "reboot" but "sudo apt-get install xorg-drivers-fglrx fglrx-kernel-2.6.15-23-386" and "sudo reboot"


I already did that :shock: see my first post in this thread. I figured since you were not able to get it to work with my very short and non-beginner friendly instructions that you needed a bit more guidance.

I suggest that you read through the instructions again and make sure you know what to do and why you should do it. Do this **BEFORE** actually performing the necessary steps.

If you can print out the instructions, that would be good to since you need to "step out" of your browser when you reboot and you have nothing to look at while you are doing that.

> **Tulio said:**
> 
2. In points (likewise I wrote)
3. with configuration x server (maybe I do something wrong with this)


Try:

```
grep ATI /var/log/Xorg.0.log
```

You should get something like:

```
(**) |   |-->Device "ATI Radeon 9250"
(--) PCI:*(1:0:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xd0000000/27, 0xdfef0000/16, I/O @ 0xc800/8, BIOS @ 0xdfec0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) rev 1, Mem @ 0xc8000000/27, 0xdfee0000/16
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) ATI Radeon/FireGL: The following chipsets are supported:
(II) ATI Proprietary Linux Driver Version Identifier:8.25.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.25g1
(II) ATI Proprietary Linux Driver Build Date: May 18 2006 09:54:44
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.25.1-driver-lnx-268237
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9200
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) Loading extension ATITVOUT

```

If your Xorg logs do not mention "FireGL" then you have a misconfigured X server.

> **Tulio said:**
> 
4. begin since when I reinstall ubuntu and login to system (we started over)

And some questions:
1. "install fglrx kernel modules" is "fglrx-kernel-2.6.15-23-386"?


:confused: there is no such package. The fglrx kernel modules are in linux-restricted-modules choose either linux-restricted-modules-386 or linux-restricted-modules-686.

Then install xorg-fglrx-driver and run aticonfig.

> **Tulio said:**
> 
2. If point 1 is true: I have to install "fglrx-kernel-2.6.15-23-386" or "fglrx-kernel-2.6.15-26-686"? If in boot menu I have "[...]-2.6.15-23-386" but my architecture processor is 686. Maybe I must check it in other way?

Instead of providing you with another droll tutorial or a numbered list of things to do, I present you an Bash script instead.

[COLOR="Red"]BIG FAT WARNING!!! This script is based on the steps I provided above. NO GUARANTEES THAT IT WILL NOT KILL YOUR SYSTEM. RUN THIS AT YOUR OWN RISK.[/COLOR]

This assumes that you are on a freshly installed, un-upgraded system. This means the following:

1. You have just finished installing and this is your first boot.
2. The installer has chosen to provide you with the Open Source "ati" driver for your GUI.
3. You are able to connect to the Internet.
4. You have downloaded the libGL.so.1.2.bz2 file found in this forum thread and you have this file in your home directory.
5. VERY IMPORTANT! You have not installed anything else at this point.

Open an terminal window and cd to the directory where your libGL.so.1.2.bz2 can be found. If you downloaded it into /home/tulio/downloads, then:

```

cd /home/tulio/downloads
gedit ati-patch

```

Copy the code below and paste into gedit.

```

function wait_message() {
echo "Press the ENTER key to proceed. CTRL+C to abort."
read
}

# Make sure we are in the directory where libGL.so.1.2.bz2 has been downloaded...
test  -f libGL.so.1.2.bz2 -o -f libGL.so.1.2 || echo "Run this script in the same directory where you downloaded libGL.so.1.2.bz2" && exit 1

sudo echo "This script will upgrade your system and install the ATI kernel and xorg drivers and install an old libGL.so.1.2 that works with rv200 cards."
wait_message

echo "Updating your APT package index files..."
sudo apt-get update

echo "I will now upgrade your default system packages."
wait_message
echo "Performing system upgrade..."
sudo apt-get dist-upgrade -y

echo "I will now install linux-image-686 linux-restricted-modules-686 xorg-driver-fglrx"
wait_message
sudo apt-get install linux-image-686 linux-restricted-modules-686 xorg-driver-fglrx

echo "I will now overwrite the libGL.so.1.2 that came with the latest ATI drivers with an old version that works with rv200 based cards."
wait_message
test -f libGL.so.1.2.bz2 && bunzip2 libGL.so.1.2.bz2
sudo cp libGL.so.1.2
sudo ldconfig

echo "I will now setup the environment variables needed for libGL.so.1.2 to run"
wait_message
sudo echo "# For ATI libGL.so.1.2 from old ATI driver versions" >> /etc/bash.bashrc
[COLOR="Red"]
# Find the correct path for LIBGL_DRIVERS_PATH.
if [ -L /usr/lib/xorg/modules/dri ]; then
  sudo echo "export LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri" >> /etc/bash.bashrc
else
  sudo echo "export LIBGL_DRIVERS_PATH=/usr/lib/dri" >> /etc/bash.bashrc
fi
[/COLOR]

echo "I will now run aticonfig to create a default minimum configuration that"
echo "will be able to load the fglrx module."
wait_message
sudo aticonfig --initial
echo "I have finished creating the xorg.conf. If X fails to start, you may have to"
echo "edit those settings in xorg.conf manually."
wait_message

echo "I will now add the fglrx kernel module to the list of kernel modules to be"
echo "loaded at boot time."
wait_message
echo "fglrx" >> /etc/modules

echo "Your system should now be setup to run hardware-accelerated OpenGL applications."
echo "You need to reboot your computer in order for the changes to take effect."
echo "I can attempt to reboot your computer for you. If this attempt fails, then"
echo "reboot your computer manually"
wait_message
sudo reboot

```

After pasting the above script into gedit, save it.

[COLOR="Red"]BIG FAT WARNING!!! RUN THE ABOVE SCRIPT AT YOUR OWN RISK.[/COLOR]

With that out of the way, cross your fingers and do:

```

bash ati-patch

```

Enter your current password when prompted for it.

[-o< 

Good luck...

---

### Post by Greycloak on 2006-08-17
Nimrod, I tried following your instructions right after a clean install of Ubuntu and it didn't work.  When I did the LIBGL_DEBUG it was complaining about not being able to find  /usr/lib/xorg/modules/dri/atiogl_a_dri.so

After a few minutes of searching I found aitogl_a_dri.so in /usr/lib/dri

So I created the necessaey dirs from the first path (I think I had to add /modules/dri/) and copied the file.  Everything works perfectly after that.  I have no idea why the system was looking for it in a nonexistent dir. Fglrx reports ATI, glxinfo reports direct rendering, and I am actually getting much better performance out of my 9200 with this driver.

---

### Post by nimrod_abing on 2006-08-17
> **Greycloak said:**
> Nimrod, I tried following your instructions right after a clean install of Ubuntu and it didn't work.  When I did the LIBGL_DEBUG it was complaining about not being able to find  /usr/lib/xorg/modules/dri/atiogl_a_dri.so

After a few minutes of searching I found aitogl_a_dri.so in /usr/lib/dri


On my system /usr/lib/xorg/modules/dri is a symbolic link to /usr/lib/dri.

> **Greycloak said:**
> So I created the necessaey dirs from the first path (I think I had to add /modules/dri/) and copied the file.  Everything works perfectly after that.  I have no idea why the system was looking for it in a nonexistent dir. Fglrx reports ATI, glxinfo reports direct rendering, and I am actually getting much better performance out of my 9200 with this driver.

You didn't have to create the directory and copy the atiogl_a_dri.so to it. All that is needed is to do:

```
cd /usr/lib/xorg/modules/ && sudo ln -s /usr/lib/dri

```

In any case, I'm glad that you found a way to make it work for you. I think the fact that /usr/lib/dri is not symlinked into /usr/lib/xorg/modules is probably what has been causing the installation to fail on Tulio's system.

I've edited the script I have wrote earlier to reflect this.

---

### Post by Darth Tux on 2006-08-26
I got my 9250 working with the latest 8.28.8 drivers. In earlier releases I had to used this [guide]("http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26"). 3D acceleration worked right off the bat with the new drivers and I added [ Option "AGPv3Mask" "0x00000002" ] to my xorg.conf under the "Device" section. I added that to stop random freezing and complete lock-ups I was experiencing in games. Hope this helps.

---

### Post by fvgm on 2006-09-09
Hi, take a look this
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

choose your version, and read instructions...
it worked for me...

good luck!

---

### Post by ShinjiLeery on 2006-09-10
The Latest driver can't work with the DVI output... anyone have a clue? 

I have the ati 9250 too

---

