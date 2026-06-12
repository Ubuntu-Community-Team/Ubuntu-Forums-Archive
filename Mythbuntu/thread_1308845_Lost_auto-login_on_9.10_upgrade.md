---
title: "Lost auto-login on 9.10 upgrade"
date: 2009-10-31
forum: Mythbuntu
---

### Post by pimlottc on 2009-10-31
After upgrading from 9.04 to 9.10, Mythbuntu no longer auto-logins on boot.

I tried to fix it through gdmsetup (Applications > Settings > Login Screen), but the behavior is not the same as before; now it only auto-logins on initial boot, but not when I logout or restart X.  The old behavior was very handy since I sometimes had to ssh in and restart gdm when something hanged.

EDIT: Solved!  Looks like the gdm conf file was renamed upstream between 9.04 and 9.10.  To fix it, just rename /etc/gdm/gdm-cdd.conf to custom.conf:

```
sudo mv /etc/gdm/gdm-cdd.conf /etc/gdm/custom.conf
```

---

### Post by Boppy3125 on 2009-10-31
The way I re-enabled it is just using Mythbuntu Control Center.  I turned it off, applied the change, then turned it back on and let MCC get me in the right place.  I don't know about any changes to behavior relating to restarting X as I don't think I ever did it before to compare.

---

### Post by Babstar on 2009-11-01
I also had the same problem, solved by modifying /etc/gdm/custom.conf to include the following lines:
```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=*YourUserName*            
TimedLoginDelay=0

```

Change *YourUserName* to the your appropriate MythTV viewing username.
I found the following link useful: [GDM Autologin]("http://www.perturb.org/display/entry/812/").

---

### Post by neutron68 on 2009-11-01
I am having the same auto-login problem.  I had the problem right after the 9.10 upgrade.  I thought I had the problem fixed by changing the Login Screen settings in the Desktop GUI.  The autologin worked for a day and then started making me login again.

The change of the /etc/gdm/custom.conf file as mentioned above does not work for me.  

I get the login box and must log in 2-4 times before Mythtv will start.  Sometimes it only takes 2 logins and sometimes it takes 4!

Eric

---

### Post by ghuber on 2009-11-01
Thanks
The copy in post 1 fixed me!!:D

---

### Post by pimlottc on 2009-11-02
> **Babstar said:**
> I also had the same problem, solved by modifying /etc/gdm/custom.conf to include the following lines:
```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=*YourUserName*            
TimedLoginDelay=0

```


I think you'll find, though, that only logs you the first time after boot, and not after that.  There's additional lines in gdm-cdd.conf that affect that, which is why I found copying it over to be a better solution.

---

### Post by neutron68 on 2009-11-02
> **neutron68 said:**
> I am having the same auto-login problem.  I had the problem right after the 9.10 upgrade.  I thought I had the problem fixed by changing the Login Screen settings in the Desktop GUI.  The autologin worked for a day and then started making me login again.

The change of the /etc/gdm/custom.conf file as mentioned above does not work for me.  

I get the login box and must log in 2-4 times before Mythtv will start.  Sometimes it only takes 2 logins and sometimes it takes 4!

Eric

Also, performing this action did not help either: 
```
sudo mv /etc/gdm/gdm-cdd.conf /etc/gdm/custom.conf
```

Any idea why I would be forced to login 2-4 times?

---

### Post by ilcapo09 on 2009-11-02
I changed it from within the MCC. Forget exactly where, but there is an option there

---

### Post by Babstar on 2009-11-02
pimlottc, can you post a copy of your gdm-cdd.conf file - I don't have one!
I do have a backed file gdm-cdd.conf.mythbuntu-old, however.

---

### Post by Babstar on 2009-11-02
pimlottc, thanks for the hint.  I googled a few thing & found the [Mythtv wiki link]() which pretty much shows how to do it using the Fedora 9 Method 2 & gdm-cdd.conf.mythbuntu-old as a template.

I have attached my file, change MythTvUser to your appropriate login name, rename to custom.conf, copy to /etc/gdm and restart gdm.  It seems to work here.

--
Babstar

---

### Post by sk8er3810 on 2009-11-02
I had the same problem on both of my upgraded boxes.  Fixed the AutoLogin problem with the above solution.  Is this a cause of Mythbuntu not using gdm.conf as default config file and so the upgrade packages not accounting for this?

However my window titles font were huge.  DPI font setting in "Appearance" was set to over 300.  I changed it back down to 96 DPI which looks normal now.  However it is still super huge on the gdm login screen.  Gdm is not using the Mythbuntu theme also.  I installed and reinstall mythbuntu-gdm-themes but no avail.  Any suggestions?

I do see the Mythbuntu splash screen before the login screen pops up

---

### Post by neutron68 on 2009-11-02
I copied the file that Babstar posted into the /etc/gdm directory and altered the username to be mine.  I STILL am forced to login 2-4 times before Mythtv will finally start up.  

There MUST be more to the autologin than the /etc/dgm/custom.conf file.
What other files are coming into play here?

This multi-login is really annoying.  ](*,)

Eric

---

### Post by neutron68 on 2009-11-02
I just found relief.  :biggrin:

This login problem is an official bug:
[http://bugs.launchpad.net/mythbuntu/+bug/463314](http://bugs.launchpad.net/mythbuntu/+bug/463314)

I just copied the contents of the gdm-cdd.conf from 9.04 (posted in the comments for this bug) into my /etc/dgm/custom.conf file.  I edited the username to be mine, and restarted the computer.  That fixed it!

I wonder why the other posted versions of this file didn't work on my system???

Eric

---

### Post by sk8er3810 on 2009-11-03
It looks like in the new GDM many of the settings that were in the old gdm-cdd.conf were deprecated in this new version.  Maybe some of the pre-existing settings confused the new version.

---

### Post by kdavies on 2009-11-03
I found a solution that simply copies files.
the option for the user was greyed out so I looked at the authentication mechanisms in pam. 
In /etc/pam
there is a file gdm and gdm-autologin
As root, I moved gdm to gdm-plogin
         I copied gdm-autologin gdm

Result works fine with no passwords.

My crib would be to get the developers to reexamin why the option is there but greyed out.

Otherwise well done. excellent distro Ubuntu 9.10

---

### Post by one4yourlife on 2009-11-04
> **neutron68 said:**
> I just found relief.  :biggrin:

This login problem is an official bug:
[http://bugs.launchpad.net/mythbuntu/+bug/463314](http://bugs.launchpad.net/mythbuntu/+bug/463314)

I just copied the contents of the gdm-cdd.conf from 9.04 (posted in the comments for this bug) into my /etc/dgm/custom.conf file.  I edited the username to be mine, and restarted the computer.  That fixed it!

I wonder why the other posted versions of this file didn't work on my system???

Eric

Thanks for the post. This fixed it!

---

### Post by neutron68 on 2009-11-04
> **neutron68 said:**
> I STILL am forced to login 2-4 times before Mythtv will finally start up.  

There MUST be more to the autologin than the /etc/dgm/custom.conf file.
What other files are coming into play here?

This multi-login is really annoying.  ](*,)

Eric
The multi login behavior is back.  CRAP! :mad:

At one point tonight, the system made me login with the password 10 times before it FINALLY booted into Ubuntu, and then into Mythtv!

At each login, I see the black Mythbuntu splash screen with the animated white line under the word, then the screen goes black, then I get the Ubuntu login window.  If I enter the password for my username, the screen goes back to the black Mythbuntu splash screen with the animated white line under the word, then the screen goes black and then I get the Ubuntu login window agian.  (repeat until user is angry)

How is this possible?  How can the login work sometimes and not others?  A race condition?  
What else would be fighting the system for a login?
Perhaps some part of gdm is crashing and causing a reboot, and thus the multi-logins??

I just went into the Mytyhbuntu Control Center and disabled the autostart of Mythtv - thinking it might help narrow down the search for the cause.

Do we have any people on the forum knowledgable about gdm login mechanics?
Are there any logs I can check to see what is going on?

Help!

I just read out this gdm bug in Ubuntu 9.10:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/447226](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/447226)

Is this what is happening to me?  gdm and upstart are fighting each other and respawing gdm?

My system won't let me look at the gdm logs in /var/log/gdm.  I can't even "sudo cd /var/log/gdm".  I get the response "sudo: cd: command not found".

11-6-09
I'll start a new thread, since this is slightly different than the auto-login problem...

---

### Post by chipppy on 2009-11-11
Good Evening

A trick I found that sometimes works is to do a ```
sudo thunar
```.

Then use Thunar to open the file that I want to look at.  Not always a solution but worth a try.

Out of interest I have the same problem on a clean install of 9.10 so it is not just an upgrade issue

Cheers 
chipppy

---

### Post by neutron68 on 2009-11-11
> **chipppy said:**
> Good Evening
<snip>
Out of interest I have the same problem on a clean install of 9.10 so it is not just an upgrade issue

Cheers 
chipppy
Curious...Are you getting the multiple logins or just a single login?

Eric

---

### Post by neutron68 on 2009-11-11
I have tried reinstalling gdm and 4 other gdm packages using the Synaptic Package Manager.  It didn't work on my system.  

I've also downloaded updates with the Update Manager and that has not helped either.

I used "sudo thunar" to activate the Thunar File Manager, and was able to view the gdm log files.  
I'm not sure if there are any smoking guns here.  I do see that gdm splash is choosing a 2560x1600 background, and my monitor is only a 1920x1080 LCD.

xsplash-gdm.log
```
[16:24:34:467828962 - MSG] xsplash started
[16:24:34:467829083 - MSG] get_logo_filename(): looking for the best logo for screen width...
[16:24:34:467829098 - MSG]  ** Chose `large'
[16:24:34:467829108 - MSG]  ** logo filename is: /usr/share/images/xsplash/logo_large.png
[16:24:34:467829119 - MSG] get_throbber_filename(): looking for the best throbber for screen width...
[16:24:34:467829131 - MSG]  ** Chose `large'
[16:24:34:467829141 - MSG]  ** throbber filename is: /usr/share/images/xsplash/throbber_large.png
[16:24:34:467829151 - MSG] background_image = /usr/share/images/xsplash/bg_2560x1600.jpg
[16:24:34:467829162 - MSG] logo_image = /usr/share/images/xsplash/logo_large.png
[16:24:34:467829172 - MSG] throbber_image = /usr/share/images/xsplash/throbber_large.png
[16:24:35:466233389 - MSG] get_logo_filename(): user provided a logo on the command line; using that
[16:24:35:466235520 - MSG] get_throbber_filename(): user provided a throbber on the command line; using that
[16:24:35:466250613 - MSG] throbber started (50 frames)
[16:24:35:467008969 - MSG] received signal: gdm
[16:24:35:467009029 - MSG] gdm mode: fading out
[16:24:36:465836962 - MSG] fade finished
[16:24:36:465837129 - MSG] exiting...
```

xsplash-user.log
```
[16:24:42:459696935 - MSG] xsplash started
[16:24:42:459697065 - MSG] get_logo_filename(): looking for the best logo for screen width...
[16:24:42:459697079 - MSG]  ** Chose `large'
[16:24:42:459697090 - MSG]  ** logo filename is: /usr/share/images/xsplash/logo_large.png
[16:24:42:459697101 - MSG] get_throbber_filename(): looking for the best throbber for screen width...
[16:24:42:459697113 - MSG]  ** Chose `large'
[16:24:42:459697123 - MSG]  ** throbber filename is: /usr/share/images/xsplash/throbber_large.png
[16:24:42:459697133 - MSG] background_image = /usr/share/images/xsplash/bg_2560x1600.jpg
[16:24:42:459697143 - MSG] logo_image = /usr/share/images/xsplash/logo_large.png
[16:24:42:459697154 - MSG] throbber_image = /usr/share/images/xsplash/throbber_large.png
[16:24:43:458170119 - MSG] get_logo_filename(): user provided a logo on the command line; using that
[16:24:43:458172271 - MSG] get_throbber_filename(): user provided a throbber on the command line; using that
[16:24:43:458187838 - MSG] throbber started (50 frames)
[16:24:43:458488975 - MSG] received a new signal to wait for: xfdesktop
[16:24:43:458489037 - MSG] adding signal `xfdesktop'
[16:24:43:458968977 - MSG] received signal: xfdesktop
[16:24:43:458969031 - MSG] received signal xfdesktop
[16:24:44:457786963 - MSG] fade finished
[16:24:44:457787212 - MSG] exiting...
```

0.log file
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Mythbuntu8 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: root=UUID=cd96068d-ce8c-4263-acd3-30fe2815dc76 ro quiet splash 
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 11 16:24:33 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(--) using VT number 7

(--) PCI:*(0:0:5:0) 10de:0240:1043:81cd nVidia Corporation C51PV [GeForce 6150] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     ACER X233H (CRT-0)
(--) NVIDIA(0): ACER X233H (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x720"; removing.
(WW) NVIDIA(0): No valid modes for "720x480"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0):     "1920x1080"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(**) NVIDIA(0): DPI set to (100, 100); computed from "DPI" X config option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing extension GLX
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) NVIDIA(0): Setting mode "1920x1080_60_0"
```

0-greeter.log file
```
gnome-session[2446]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
** (process:2459): DEBUG: Greeter session pid=2459 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-4LKmyj/database
```

0-slave.log file
```
gdm-session-worker[2460]: pam_unix(gdm:session): session opened for user eric by (uid=0)
gdm-session-worker[2460]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
```

I wonder if there are any gdm experts that see any smoking guns here?

Eric

---

### Post by chipppy on 2009-11-14
Good Evening

Multi login requests

Cheers
chipppy

---

### Post by neutron68 on 2009-11-15
Something has changed on my system and the forced multi-logins have stopped!

I posted a description of what I tried yesterday on a thread in the Ubuntu Installation and Upgrade section:

[http://ubuntuforums.org/showthread.php?p=8322246](http://ubuntuforums.org/showthread.php?p=8322246)

---

