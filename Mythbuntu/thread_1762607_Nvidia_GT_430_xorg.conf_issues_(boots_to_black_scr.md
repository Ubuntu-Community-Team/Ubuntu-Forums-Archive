---
title: "Nvidia GT 430 xorg.conf issues (boots to black screen)"
date: 2011-05-19
forum: Mythbuntu
---

### Post by davidstoll on 2011-05-19
I can't seem to get a good xorg.conf file for my Nvidia GT 430.

I have run nvidia-xconfig and rebooted and have even deleted the xorg.conf and THEN run nvidia-xconfig so to make sure it created a new file...no luck.

I've run:
sudo dpkg-reconfigure -phigh xserver-xorg
but that didn't help either.

I've uninstalled (sudo apt-get remove nvidia-current) and also tried purging.

I've downloaded the Nvidia drivers directly from their homepage, killed gdm and restarted.

I've tried installing driver version 173 (as some posts have suggested).

I've enabled the nvidia driver through the hardware driver gui.

The only way I can get a gui is to use the failsafe xorg so it uses the vesa.

One wierd thing that happened was that one time I used someone elses xorg.conf, restarted gdm and got full 1080, but after a reboot, I got the same black screen.

I can ssh in.

I'm using Mythbuntu 10.04 32bit.

I'm sure the problem is related to my linux experience and missing something obvious, but I'm just really stumped.

Can someone please help me?

Attached is my xorg.0.log file and xorg.conf* .  But remember that I won't be able to match up what xorg.conf file matches which error, but maybe there is something else that can be deciphered from it with a better trained eye.

I want to be able to get 1080 with the latest vdpau support.

Thank you for any help you can give me.

---

### Post by realzippy on 2011-05-19
Well,the Xorg.0.log you posted was created when you tried to install the 173.xx driver,which does **not** work with your card:

(EE) NVIDIA(0): The NVIDIA GPU at PCI:1:0:0 is not supported by the 173.14.22
(EE) NVIDIA(0):     NVIDIA driver.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!

Suggest to add [xswatppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") to your software sources,then install nvidia-current again (driver will come from xswat then).
If again no GUI,post the Xorg.0.log again.
Btw,the minimal xorg.conf (xorg.conf.original) normally should work.

---

### Post by davidstoll on 2011-05-19
I'm not sure what you mean by adding xswatppa.

Is it a specific software source from nvidia or something?  I assume I add it to the software list, but I'm not sure of exactly what I need to add.

I did a apt-get install nvidia-current and rebooted.  Anything else?

Thanks you!

---

### Post by erod20 on 2011-05-19
You need to download the latest driver from Nvidia. Install that the same way you installed the 173 driver. Here is a link [http://www.nvnews.net/vbulletin/showthread.php?p=2421151]("http://www.nvnews.net/vbulletin/showthread.php?p=2421151")

---

### Post by realzippy on 2011-05-19
> **davidstoll said:**
> I'm not sure what you mean by adding xswatppa.

Is it a specific software source from nvidia or something?  I assume I add it to the software list, but I'm not sure of exactly what I need to add.

I did a apt-get install nvidia-current and rebooted.  Anything else?

Thanks you!


Added a link to my post for xswatppa...


edit:

Just run (old nvidia-driver must be uninstalled):

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
sudo apt-get upgrade
```

Then install nvidia-current with additional drivers tool......

---

### Post by davidstoll on 2011-05-19
Ok, cool...

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

Is this correct?  Then what?  apt-get update..apt-get upgrade...reboot...?

Thanks, I just don't want to skip anything.

---

### Post by realzippy on 2011-05-19
Correct.Edited post #5

BTW,
running
```
sudo nvidia-bug-report.sh
```
creates a bug file in your home directory which includes
Xorg.0.log,xorg.conf aso
(if again no GUI)

---

### Post by davidstoll on 2011-05-19
One thing I noticed, not sure if it matters, although, I would like to fix it...

apt-get upgrade
The following packages have been kept back:
  xserver-xorg-video-intel


Anyway, no gui, so I ran sudo nvidia-bug-report.sh

file attached

I think I did everything correctly, please forgive me if I didn't correctly remove/add something.

---

### Post by realzippy on 2011-05-19
Ok,there is a problem (see xorg.0.log):
the driver cannot read the monitor's specifications. (EDID)

II) May 19 11:24:14 NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) May 19 11:24:14 NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) May 19 11:24:14 NVIDIA(0):     from CRT-0's EDID.


Which samsung model is it exactly?

---

### Post by davidstoll on 2011-05-19
It's actually a TV.  Samsung ln42b750

In my previous posting with all the xorg.conf files in the zip...the xorg.conf.oldcard is the file I used with my old video card using the same TV.

I normally use the VGA port as my default, but also use the HDMI out.  I think the reason I got used to using the VGA port is because, I get my bios and post screen info through the VGA when I reboot.

---

### Post by realzippy on 2011-05-19
Ok,open your xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```

 ..and add a monitor section,so it looks like:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Reboot or restart X server.

---

### Post by davidstoll on 2011-05-19
> **realzippy said:**
> Ok,open your xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```

 ..and add a monitor section,so it looks like:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Reboot or restart X server.


Ok, we're getting somewhere.  I now have a gui, but got an error.  jpg attached.

It looks like it's running at 640x480, but I don't see my launcher bar and I can't right click on the desktop and also the windows that I have always open don't have menu bars.

---

### Post by davidstoll on 2011-05-19
I used: sudo /etc/init.d/gdm restart  to get the gui (above).

However, I rebooted after that and no gui again.

:(

---

### Post by realzippy on 2011-05-19
Admit I am not experienced with mythbuntu.

You run it with gnome?
Suggest a shot in the dark,like reinstalling ubuntu-desktop  .. :P
..or begin with
gnome-settings-daemon, dbus, dbus-core,policykit.

Also you could add a new (test-) user,which starts with a vanilla account..

---

### Post by davidstoll on 2011-05-19
Well, it runs xfce, so, I'm not sure about all that.

One interesting thing...

```
sudo nvidia-settings 

ERROR: Cannot open display 'Mythbuntu:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 22 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 23 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 24 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 25 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 26 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 27 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 28 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 29 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAniso specified on line 30 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAA specified on line 31 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 32 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 33 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 34 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 35 of configuration
       file '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 36 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 37 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedBrightness specified on line 38 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 39 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 40 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedContrast specified on line 41 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenContrast specified on line 42 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueContrast specified on line 43 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedGamma specified on line 44 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenGamma specified on line 45 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueGamma specified on line 46 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 47 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 48 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 49 of configuration
       file '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 50 of configuration
       file '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 51 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 52 of configuration
       file '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line 53 of
       configuration file '/home/david/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 54 of configuration file
       '/home/david/.nvidia-settings-rc' (no Display connection).
```

---

### Post by realzippy on 2011-05-19
Indeed interesting.

Suggest to delete

/home/david/.nvidia-settings-rc

then recreate it by running

```
nvidia-settings 
```  (no "sudo")

---

### Post by davidstoll on 2011-05-19
I deleted the .nvidia-settings-rc and re-ran nvidia-settings and it came up correctly.  I re-detected displays, made them absolute clones, etc...and saved the xorg.conf file.

Rebooted.

No automatic gdm, but I ran: sudo /etc/init.d/gdm restart
and the gui started, but it's still strange, I get that same error (see jpg above) and I get no buttons, menus, etc.  Just the command window and the thunar window that I have always open.

latest xorg and log attached

---

### Post by realzippy on 2011-05-19
*I deleted the .nvidia-settings-rc and re-ran nvidia-settings and it came up correctly*
what does "came up correctly" mean?


*Just the command window and the thunar window that I have always open.*

Does this mean you have an option like
"remember current session" or something?
If so,turn that off temporarily...and try again.

What is the error output when you run
```
startx
```
instead of
sudo /etc/init.d/gdm restart ?

Will check your log later (watching soccer right now),but I am quite sure that this is not related to the nvidia-driver.
Do you have a file 
*monitors.xml* ?
If so,delete it.

---

### Post by davidstoll on 2011-05-19
Normally I do have an option to save the settings, but since I don't have any buttons, menus etc now, I can only: sudo /etc/init.d/gdm stop

I do not have a monitors.xml file.

I can't do the startx command because I can only ssh in.  If I am in the strange gui and stop the gdm, I just have a black screen, so I can't run it.  :(



> **realzippy said:**
> *I deleted the .nvidia-settings-rc and re-ran nvidia-settings and it came up correctly*
what does "came up correctly" mean?


*Just the command window and the thunar window that I have always open.*

Does this mean you have an option like
"remember current session" or something?
If so,turn that off temporarily...and try again.

What is the error output when you run
```
startx
```
instead of
sudo /etc/init.d/gdm restart ?

Will check your log later (watching soccer right now),but I am quite sure that this is not related to the nvidia-driver.
Do you have a file 
*monitors.xml* ?
If so,delete it.

---

### Post by realzippy on 2011-05-19
*I deleted the .nvidia-settings-rc and re-ran nvidia-settings and it came up correctly*

...what does "came up correctly" mean?

---

### Post by davidstoll on 2011-05-19
Sorry, the nvidia settings window in the gui.  I did all this within the X gui.  I got those errors when I ran nvidia-settings from the command prompt in X.  I deleted the problem file (.nvidia-settings-rc) and ran nvidia-settings again and the settings window came up without all those errors from post #15.

---

### Post by realzippy on 2011-05-19
Just checked your xorg.conf made by nvidia-settings.
The Hsync/Vrefresh values are wrong/vanilla (compared to your xorg.conf.oldcard),which also can be seen in Xorg.0.log where
the EDID for CRT-0 cannot be read,so the nvidia-driver uses standart values.
Btw,wondering why there is only 1 monitor/screen section since you
have 2 displays connected.
Anyway,try this modified version:

```


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
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0   #values from your old file
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 430"
    Option         "IgnoreEDID"    "1"  #to workaround EDID problem
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

You might know (I do not):

Where is xfce's autostart?
Check if the command
nvidia-settings -l
exists.
Since it is getting late and I have to work tomorrow,I will be out soon.
Sorry I cannot help,will have a closer look tomorrow.

---

### Post by davidstoll on 2011-05-19
nvidia-settings -l
ERROR: The control display is undefined; please run `nvidia-settings --help` for usage information.

The xfce autostart is located at:
~/.config/autostart/

I'm tempted to reinstall the os...but I'm not sure if it's worth the hassle because this is a new install as of about 2 days ago.

Unfortunately, your xorg suggestion did not help.

By the way, I'm only getting a mouse cursor (it's just an X) with no windows or anything else in the gui, but that happened before your test xorg.


> **realzippy said:**
> 
You might know (I do not):

Where is xfce's autostart?
Check if the command
nvidia-settings -l
exists.
Since it is getting late and I have to work tomorrow,I will be out soon.
Sorry I cannot help,will have a closer look tomorrow.

---

### Post by davidstoll on 2011-05-19
Ok, wow, try this on for size...

I have a SilverStone HTPC case with an LCD display.

When it boots to the black screen, I ssh in and run this command..
sudo /etc/init.d/LCDd restart

Then X finishes booting up.

soooo...any ideas how I can fix this?
Maybe I should start a new thread?

---

### Post by davidstoll on 2011-05-19
Ok, so I decided to just do a reinstall...granted my home dir is intact...but the OS partition got totally reformmated.

Same issue.  At this point, only the failsafe (or have no xorg.conf) is working.  I tried the example/sample from post #22.

Also, I didn't install lcdproc this time, so I can't use my little restart of the LCDd deamon trick.

I might as well give you my latest log...

---

### Post by davidstoll on 2011-05-19
actually, the startx was able to start the gui in a low graphics mode when  sudo /etc/init.d/gdm start  wouldn't.

> **realzippy said:**
> 
What is the error output when you run
```
startx
```
instead of
sudo /etc/init.d/gdm restart ?


---

### Post by realzippy on 2011-05-20
was about merging your
*xorg.conf.oldcard*  (guess it used to work?)
with the new one's device section (since card has changed,also, there are the 2 Monitor/Screen sections I have missed in the new one..
and stumbled about:

Option         "TVOutFormat" "SVIDEO"

Did you formerly use Svideo output and now HDMI ?
BTW,for some reason I cannot open your attached Xorg.0.log :confused:

---

### Post by davidstoll on 2011-05-20
Updated the attachment in post 25.

At one point I did use it with a slingbox, but the new card doesn't have that.  The old card had DVI, HDMI and svideo.  I used an adapter for the DVI to go into the VGA port on my TV.

The new card has VGA, DVI and HDMI.  I just plugged the same VGA cable with the adapter into the DVI...but I could go directly into the VGA without converting...but I guess it doesn't really matter.

I tried this, but got a gui based error (popup window) that says...

------------------------------------------------------
Ubuntu is running in low-graphics mode.

The following error was encountered.  You may need to update your configuration to solve this.

(EE) Nvidia(0): Failed to initialize the NVIDIA kernel module.  Please see the
(EE) NVIDIA(0):    system's kernel log for additional error messages and
(EE) NVIDIA(0):    consult the NVIDIA README for details.
(EE) NVIDIA(0): *** Aporting ***
(EE) Screen(s) found, but none have a usable configuration.
------------------------------------------------------

I know some of the above error seems cutoff or has extra spaces or whatever, that that's what the little gray popup says.

Then I can click OK and it gives me the options...
Run in log graphics mode for 1 session
Reconfigure graphics
Troubleshoot
Exit to console
Restart X

But nothing seems to do any good.

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 430"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
	# Removed Option "metamodes" "CRT: 1920x1080 +0+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TVOutFormat" "SVIDEO"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1920x1080_60 +0+0, DFP: 1920x1080_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enabled"
	#    Option         "Composite" "Disabled"
EndSection
```

---

### Post by ian dobson on 2011-05-21
Hi,

Could you attach a copy of your dmesg output. It looks as if the nvidia kernel module can't load.

Regards
Ian Dobson

---

### Post by realzippy on 2011-05-21
..maybe old kernel modules?
try:

```
sudo /etc/init.d/gdm stop 
sudo rmmod nvidia
sudo modprobe nvidia
sudo /etc/init.d/gdm start
```

same error popup?

---

### Post by davidstoll on 2011-05-21
dmesg output attached


> **ian dobson said:**
> Hi,

Could you attach a copy of your dmesg output. It looks as if the nvidia kernel module can't load.

Regards
Ian Dobson

---

### Post by davidstoll on 2011-05-21
sudo /etc/init.d/gdm start
wouldn't work this time.

However,
startx
did, but I'm in a different looking (different skin'ed) gui and I can't vnc in (that's not a big deal for now, but I'm just trying to be descriptive).

The highest res that I can choose is 640x480 for the VGA connection.  The HDMI connection will allow me to choose 1920x1080, but as soon as I choose that, all the buttons for the nvidia settings window drip below my 640x480 screen and I can't edit anything.  So, I added panning to increase the viewable area and be able to attempt a save to X Configuration file.  When I hit that button, I get a "segmentation fault" (I ran it as sudo from a terminal window).




> **realzippy said:**
> ..maybe old kernel modules?
try:

```
sudo /etc/init.d/gdm stop 
sudo rmmod nvidia
sudo modprobe nvidia
sudo /etc/init.d/gdm start
```

same error popup?

---

### Post by davidstoll on 2011-05-21
All of this is very similar to my issue a couple of years ago with my old video card.  Eventually, I found settings in my xorg.conf file that made it work correctly.  There may be something else going on here, but it just feels like the same issue.

My old video card was a 8500 GT.

I've also tried 11.04 and 10.10 and can't seem to get anything different....but then again, I guess that's not a surprise if it's a driver or xorg.conf file issue.

I have a nettop with an ION card and it just works...no configuration needed.  In my testing with that, I've reinstalled several times (for various reasons...i'm learning) and the video works like magic.

I'm not sure what else to do?  Offer a bounty?

---

### Post by davidstoll on 2011-05-21
I think there is something wrong with the "updates" (i.e. apt-get) somewhere....or...?

I decided to try a fresh install (picked 10.10 randomly) and did not check the "download updates" checkbox.  However, I did check the box to have it download 3rd party updates (mp3, etc).  I also had it use the open source drivers when it asked.

When it finished, I let it reboot twice...why?...because it seems like thumb drives don't actually mount until after the 2nd reboot and there is another setting (record X minutes past a certian event) that I can never set after the first boot after the install.  Maybe it doesn't mean anything.

Then, I added the Nvidia hardware drivers via the "additional drivers" program.  Rebooted again.

It comes up and only allows me to use up to 1360x768 (half HD) on the VGA.  It allows me to set 1920x1080 on the HDMI, but it doesn't actually output any video.

Copied my xorg.conf.oldcard (from one of my early posts) into /etc/X11/xorg.conf and rebooted again.

blamo...I get full 1080 on both outputs.

NOW, I do apt-get update/upgrade

WTF?


One other side note.  10.10 seems to be the best for scanning OTA.  10.04 scans and tells me there are conflicts and makes me choose names.  11.04 gives me a kernel panic on 4/5 boot attempts from the live cd.  Also, 11.04 doesn't restart when you ask it to restart...restart=logout on 11.04...I don't like that.  I'm sure it could be changed/configured, but if I want to logout, I can choose that.  dumb

---

### Post by davidstoll on 2011-05-21
BTW, after I got everything working and rebooted.

Then I did the apt-get update/upgrade (like I said above).

Now I get a black screen when I boot.

Can someone help me figure out which update is causing me issues and maybe blacklist it?

I would really appreciate it.

---

### Post by davidstoll on 2011-05-21
I think it is related to irexec.

---

### Post by BicyclerBoy on 2011-05-21
Your dmesg shows (3) different versions of nvidia driver modules trying to be loaded..
IMO That does seem normal.

Are you using the 32 bit pae kernel ? Is that reliable ?

I would install the nvidia driver from a 3rd party package ppa that installs properly.
AFAIK The only blacklist needed is to nouveau but the nvidia package install script is meant to do this.

Module vga16fb is blacklisted in *buntu 10.04 but you can see it loaded in your dmesg std out..

Have you tried the nvidia driver from nvidia x-swat team ppa or JYAs ppa
Both these install properly.

The cmd to stop start gdm X server
sudo service gdm stop  (& start)

What is in your /var/log/Xorg.0.log file..

---

### Post by davidstoll on 2011-05-22
Unfortunately I don't know how (or how not) to use/install pae.  But, yes, I am using 32bit.

Yes, I have tried the ppa you mentioned.

My Xorg.0.log is posted a few posts back...but I've posted it a few times.

Again, I think it's related to irexec.  I'm thinking it has to do with it loading as a deamon (or not as a deamon...i.e. with the -d switch).  The loading seems to be in this file:  /usr/share/mythbuntu/session.sh

There is a line (approx line 31) where the only thing on the line is irexec.  It may or may not have a -d after it depending on what you're running.

Removing or adding the -d might be what I am looking for to help me fix the boot to black screen issue.  There is still a problem with the xorg.conf file, but I think my custom build along with checking this irexec call in the session.sh file seems to be fixing my issue.

Why?  I have no idea, but I hope if anyone knows why, maybe they can explain and it might help other people.



> **BicyclerBoy said:**
> Your dmesg shows (3) different versions of nvidia driver modules trying to be loaded..
IMO That does seem normal.

Are you using the 32 bit pae kernel ? Is that reliable ?

I would install the nvidia driver from a 3rd party package ppa that installs properly.
AFAIK The only blacklist needed is to nouveau but the nvidia package install script is meant to do this.

Module vga16fb is blacklisted in *buntu 10.04 but you can see it loaded in your dmesg std out..

Have you tried the nvidia driver from nvidia x-swat team ppa or JYAs ppa
Both these install properly.

The cmd to stop start gdm X server
sudo service gdm stop  (& start)

What is in your /var/log/Xorg.0.log file..

---

### Post by BicyclerBoy on 2011-05-22
So you did post Xorg.0.log...lazy me.

I meant to say:
Your dmesg shows (3) different versions of nvidia driver modules trying to be loaded..
IMO That does _**NOT**_ seem normal.

I guess you have incompletely installed/uninstalled packages..

As your VGA-0 wired port display does not report a valid EDID you need to use the following in the appropriate monitor section of your xorg.conf. Then the mode validation will be done using the h & v freq data you provide.

    Option         "UseEDID" "FALSE"

If you have to make the driver use a wired port that does not auto detect then add this:
    Option         "UseDisplayDevice" "CRT-0"

BTW All the lirc stuff has completely changed with newer kernels 2.6.36...(I still using 10.04 *buntu & MythTV)
 So lirc-module-sources package is now only needed for the really old original imon devices..


Don't know your usage but ..
If you run irexec without the -d option it will run in foreground & your script will not terminate until irexec exits..

---

