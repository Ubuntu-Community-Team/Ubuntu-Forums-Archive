---
title: "'Failed to parse existing file etc/X11/xorg.conf !"
date: 2009-11-03
forum: Multimedia Software
---

### Post by Steam. on 2009-11-03
I have a problem, whenever i restart my pc the resolution reverts to 1024x768, but when i change it to 1600x1200 and try to save to X Configuration File, it says the thing i said in the title of this topic.Some say Nvidia X Server Settings doesn't have permissions to do this, how can i give it permissions to replace and save the old xorg.conf?

---

### Post by jtreg on 2009-11-03
same here. I installed Karmic Koala 64 bit and one monitor is disabled, wont parse the xorg.conf file (running x server settings as gksudo.... worked in 32 bit version

---

### Post by realzippy on 2009-11-03
there is no xorg.conf file in Karmic,or an empty one.
Have a look in /etc/X11/

If there is one,delete it.Then make a new one:

**sudo nvidia-xconfig**

Restart X

then:

**gksudo nvidia-settings**

Make changes,apply,save to X configuration file....

---

### Post by undoIT on 2009-11-18
> **realzippy said:**
> there is no xorg.conf file in Karmic,or an empty one.
Have a look in /etc/X11/

If there is one,delete it.Then make a new one:

**sudo nvidia-xconfig**

Restart X

then:

**gksudo nvidia-settings**

Make changes,apply,save to X configuration file....

Thanks! Exactly what I was looking for.

```
sudo nvidia-xconfig
```

then

```
sudo nvidia-settings
```

and now my settings are saved without any error messages :)

---

### Post by realzippy on 2009-12-12
One detail...:

[COLOR="Lime"]gk[/COLOR]sudo nvidia-settings

...always use *gk*sudo when running a GUI...

in this case (nvidiasettings) it does no harm,but if you run
sudo nautilus instead of gksudo you can smash your system easily...
so mind that gk for everything not running on the shell..

---

### Post by undoIT on 2009-12-13
> **realzippy said:**
> One detail...:

[COLOR="Lime"]gk[/COLOR]sudo nvidia-settings

...always use *gk*sudo when running a GUI...

in this case (nvidiasettings) it does no harm,but if you run
sudo nautilus instead of gksudo you can smash your system easily...
so mind that gk for everything not running on the shell..

Thanks for that clarification, it's something I learned a long time ago and it should probably be a disclaimer for anything like this.

However, I tried kdesudo nvidia-settings in Kubuntu 9.04 and it didn't work. I had to use sudo. Has this changed with *buntu 9.10 and the latest version of the Nvidia binaries?

---

### Post by realzippy on 2009-12-13
Can't you use gksudo instead of kdesu also in KDE?
I am pretty sure I ran e.g. "gksudo dolphin" successfully when I used to play around with Kubuntu....

---

### Post by undoIT on 2009-12-15
Konsole says:
> The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
gksudo: command not found


---

### Post by murthy on 2009-12-16
After deleting the old file and creating a new xorg.conf file, nvidia-settings has saved the file, but the resolution that I set 1280*1024 is not saved and the old 800*600 resolution is used when I login again.  My card is nvidia 6100 and worked well in 9.04 it is troubling me in 9.10.

---

### Post by murthy on 2009-12-17
My problem is solved unexpectedly after installing xfce over my ubuntu by sudo aptitude update&&sudo aptitude install x*ubuntu-desktop.  I do not know the reason, but in xubuntu the resolution of is saved.  I am yet t check in ubuntu.

---

### Post by Aiolos on 2010-01-03
I share the problem; am bewildered. Here is the error message that results from "sudo nvidia-settings". Sorry for its length.

ERROR: Cannot open display 'ubuntu:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 20 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 21 of configuration file '/home/administrator/.nvidia-settings-rc' (no   Display connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 22 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 23 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 24 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 25 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 26 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 27 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAniso specified on line 28 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAA specified on line 29 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 30 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute gammaCorrectedAALines specified on line 31 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display
connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display
connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display
connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display
connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 46 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display
connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
47 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
48 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 49 of configuration file '/home/administrator/.nvidia-settings-rc' (no Display
connection).


VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf. Undefined Device "(null)" referenced by Screen "Configured Screen Device".

Segmentation fault

---

### Post by angeliki on 2010-01-14
> **realzippy said:**
> there is no xorg.conf file in Karmic,or an empty one.
Have a look in /etc/X11/

If there is one,delete it.Then make a new one:

**sudo nvidia-xconfig**

Restart X

then:

**gksudo nvidia-settings**

Make changes,apply,save to X configuration file....

I had the same problem in Ubuntu 9.10 (nvidia x server settings not being able to save to xorg.conf), this worked :) thank you!

---

### Post by lupin492 on 2010-01-14
I followed the procedure, saved the xorg.conf file, but every time I log-in I get 800x600 and I have to reconfigure it through system>admin>nVidia X server settings.
The xorg.conf file has got the right parameters:

   VendorName     "Unknown"
[COLOR="Blue"]    ModelName      "BenQ FP92Wa"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0[/COLOR]
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
[COLOR="Blue"]    BoardName      "GeForce 7050 PV / nForce 630a"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "[COLOR="Blue"]1440x900[/COLOR] +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"

But even so, I loose resolution settings every time I quit, and the only suspect I see is in ~/.xsession-errors:

(gnome-settings-daemon:1746): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
GNOME_KEYRING_SOCKET=/tmp/keyring-uIFSFQ/socket
SSH_AUTH_SOCK=/tmp/keyring-uIFSFQ/socket.ssh
Unable to find a synaptics device.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
Comparing resolution (800x600) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).

(polkit-gnome-authentication-agent-1:1848): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1848): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(nautilus:1837): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3
Starting gtk-window-decorator
** (gnome-panel:1836): DEBUG: Adding applet 0.
** (gnome-panel:1836): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1836): DEBUG: Adding applet 1.
** (gnome-panel:1836): DEBUG: Adding applet 2.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
** (gnome-panel:1836): DEBUG: Adding applet 3.
** (gnome-panel:1836): DEBUG: Adding applet 4.

(gnome-panel:1836): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -4 and height 24
** (gnome-panel:1836): DEBUG: Adding applet 5.

** (nautilus:1837): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1837): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1837): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
** (gnome-panel:1836): DEBUG: Adding applet 6.
I/O warning : failed to load external entity "/home/claudio/.compiz/session/106b3df8ee9de3ab7012635134581084300000016670023"
** (gnome-panel:1836): DEBUG: Adding applet 7.
** (gnome-panel:1836): DEBUG: Adding applet 8.
** (gnome-panel:1836): DEBUG: Adding applet 9.
** (gnome-panel:1836): DEBUG: Adding applet 10.
** (gnome-panel:1836): DEBUG: Adding applet 11.
** (gnome-panel:1836): DEBUG: Adding applet 12.
** (gnome-panel:1836): DEBUG: Adding applet 13.
** (gnome-panel:1836): DEBUG: Adding applet 14.

ERROR: Cannot open display 'fenix:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 20 of
       configuration file '/home/claudio/.nvidia-settings-rc' (no Display
       connection).

...several paragraphs follow ending with the same "no display connection".

I tried adding my username to the root group (because one of the messages say: ... nvidiactl permission denied... but it's useless.
Any helping hand, thanks in advance!  :-D

(May be late to say this, but I want to comment that I couldn't make a fresh install of Karmic. I had to install Jaunty and then upgrade. Otherwise installing Karmic from live-CD the screen was blank right after the first white Ubuntu logo appearance.  Trying with text installer, it installs ok, but when finally restarts to allow you to log-in, it blanks screen again (I could even hear the login screen sound), and like now, I couldn't fix the video.
This PC's video hardware is in the text above.  On my workplace PC, I also tried Karmic ( it is a Pentium4 with 768MB RAM and an integrated Intel i815 chip) but I couldn't even pass from the white logo. It stays reading the CD and reading-it and reading-it and...).

---

### Post by lupin492 on 2010-01-16
I already found the solution.
Just want to post it for others with similar problem.

Reading the wiki at:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I found the necessary clue just at the top of the document: "resetting an out-of-range resolution".
I got curious about the contents of the file ~/.config/monitors.xml, and oh surprise! it stated:
          <width>800</width>
          <height>600</height>
          <rate>75</rate>
while defaults for my monitor are: 1440x900@60Hz.
Well, I just deleted the file and log-out and log-in-again, and the screen is normal again (1440x900).  Surprisingly, the file was not re-generated, so I can't figure out where it came from.

What I don't get now is the reason for having /etc/X11/xorg.conf and ~/.config/monitors.xml.  May be for having a general config and a per-user config.  ???  It would be "aligned" with the symptoms I was experiencing: high resolution in the login screen and low resolution once logged-in.   :popcorn:

---

### Post by munchkinmunchkin on 2010-01-16
I had the same problem a few days ago and managed to get it working.

I had to use 'sudo nvidia-xconfig' to create a new xorg.conf file that the nvidia-settings application could parse. I didn't delete the old file first but I did save a copy just in case. I got an error the first time I used 'sudo nvidia-config', on the second try it worked.

The 'Nvidia X server settings' had to be run as root, 'gksu nvidia-settings'.

And lastly once the screen resolution and other settings were changed, I had to click on "Save to X Configuration File" else the settings would be lost on a system reboot. 

Not sure if I did it 100% right, but it works.

---

### Post by JohannesE on 2010-02-08
Just wanted to say that I had the same problem until 5 minutes ago; in other words: above description works!

---

### Post by wbee on 2010-02-13
Hello,

I had the identical problem,save this one thing:

I installed the nvidia proprietary driver(Which took forever by the way,if that is relevant.).

Prompted to reboot,I did so,and a screen came on the monitor telling me the signal was out of range.

So,I reinstalled it and am using it now without the driver,so,of course,I'm getting " command not found" or whatever whenever I try to access nvidia stuff that is not installed.

I have on board nvidia geoforce 6100,which the shell recognizes.

So,how do I repair this without the nvidia stuff installed?

((Following is a copy/paste from another entry,and since it's been a day,I figure it does not violate the spirit of one bump a day.:-)))

----------------

>  How Do I Set Proper Screen Resolution?
Hello,

System>Preferences>Display tells me my screen is "unknown".

When I click "detect monitors" it does nothing.

The screen resolution is set incorrectly at 800X600, which makes pages' sides beyond the edges of the screen. 800X600 is the top setting on the drop down menu provided. Those,of course,are 4 to 3 ratios.

I looked up my monitor. It's LCD, WXGA+,17",with a maximum resolution of 1440X900,which is a 16 to 10 ratio.

How do I reset my screen resolution to the correct value and keep it there?

Can I experiment plugging different resolution values into the proper shell code once I have it?


----------------

Thanks.

---

### Post by Steam. on 2010-02-13
First, make sure that you have the nvidia-settings package installed.Look it up in Synaptic Package manager, not with the quick search, the button next to it, put description and name as search criteria, and type nvidia.Find it, mark for installation, apply.Try the stuff in the 3rd post of this topic and post back.

---

### Post by wbee on 2010-02-13
Steam,

I downloaded the file in question.

(As an aside,when I checked to make sure the check box was green for nvidia-settings(it was),none of the kernels,general or specific were installed.)

Following the steps in the third post,here is the output:

```
wbee@wbee-desktop:~$ /etc/X11/
bash: /etc/X11/: is a directory
wbee@wbee-desktop:~$ sudo nvidia-xconfig
[sudo] password for wbee: 
sudo: nvidia-xconfig: command not found
wbee@wbee-desktop:~$ gksudo nvidia-settings
wbee@wbee-desktop:~$ 


```

Running the third step returned me to the System>Administration>Nvidia X Server Settings,telling me to do step two.

In step one,is there distinction between a file and a directory?

Even if I knew how to delete a directory(or a file),I'd hesitate ,fearful I'd do more harm than good.

---

### Post by HappyFeet on 2010-02-13
This isn't the only way to do it, but it works.

Do:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
gksudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button labeled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

### Post by wbee on 2010-02-13
Happy Feet,

Thank you.

Doing your first step resulted in this output:

```
wbee@wbee-desktop:~$ sudo rm /etc/X11/xorg.conf
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
wbee@wbee-desktop:~$ 

```

-----------

I checked the specs for my monitor to get the correct resolution but it said nothing about speed. When I do get in to reset,what speed should I set?

LCD,WXGA+,17",1440x900

---

### Post by wbee on 2010-02-13
Here is something new I found playing around:

>  How to Get to the Shell Booting Up...
Hello,

In the process of getting a screen resolution issue settled,I have tried accessing.

Code:

sudu nvidia-xconfig

to no avail.

Finally,I tried,

Code:

`sudo nvidia-xconfig`

and got this:

Code:

wbee@wbee-desktop:~$ sudo `nvidia-xconfig`
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-glx-173
 * nvidia-glx-185
 * nvidia-glx-96
Try: sudo apt-get install <selected package>
nvidia-xconfig: command not found
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
wbee@wbee-desktop:~$

The problem is the last time I tried to load nvidia drivers,it just made things worse. So bad,in fact,that when I rebooted,my monitor told me it could not process it because it was "outside of range".

----------

So,is there a way I can access the terminal at boot,from the grub,and if so,how?

And if so,is there any reason the instructions in this thread would not work there?

------

Thank you.

---

### Post by wbee on 2010-02-13
Steam and Happy Feet:

Thank you.

:-)Issue Resolved!:-)

---

### Post by unsui on 2010-02-14
All praise HappyFeet! That worked.:D

---

### Post by Steam. on 2010-02-14
To make this easier, do not download drivers from the nvidia page.Go to Administration>Hardware Drivers.It will show you the graphic card drivers to download.Much easier, and to set a resolution forever(once you put those drivers), follow the 3rd post.

---

### Post by Mr Gates on 2010-03-21
this blog here worked for me

[]("http://pascalg.wordpress.com/2010/01/10/twinview-on-ubuntu-9-10linux-mint-helena/")[Click here]("http://pascalg.wordpress.com/2010/01/10/twinview-on-ubuntu-9-10linux-mint-helena/")

I couldnt get my dual screens to save the settings, this trick did it

---

### Post by rm_rf_star on 2010-03-23
> **realzippy said:**
> there is no xorg.conf file in Karmic,or an empty one.
Have a look in /etc/X11/

If there is one,delete it.Then make a new one:

**sudo nvidia-xconfig**

Restart X

then:

**gksudo nvidia-settings**

Make changes,apply,save to X configuration file....

Using ubuntu 9,10. Above instructions worked, but only after going to system --> administration --> hardware drivers and enabling/activating the driver that was labelled "recommended". In my case, it was "nvidia accelerated graphics driver (version 185) [recommended]".

---

### Post by ginjaninja405 on 2010-03-23
> **realzippy said:**
> there is no xorg.conf file in Karmic,or an empty one.
Have a look in /etc/X11/

If there is one,delete it.Then make a new one:

**sudo nvidia-xconfig**

Restart X

then:

**gksudo nvidia-settings**

Make changes,apply,save to X configuration file....

How do you restart X? I'm having the same problem, and after doing this the login is fine but then it reverts back to the 60Hz refresh rate making it all stretched. Only once I've signed in though.

---

### Post by theodisious on 2010-05-10
hi guys, i tryed several other suggestions from this sight and was getting frusterated... what does parse MEAN? theres already a file there... cant i just merge it? GAH.. 
so ... i found the solution to my personal demon, i added a 1 to the name and saved it as 
  xorg1.conf  for some reason, this worked for me :) i dont know why... but im very happy it did, i was having to re-set my graphics adapter every time i logged in... time consuming. hope this helps :)

---

