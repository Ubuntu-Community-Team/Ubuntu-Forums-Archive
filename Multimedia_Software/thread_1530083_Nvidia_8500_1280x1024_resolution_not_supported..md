---
title: "Nvidia 8500 1280x1024 resolution not supported."
date: 2010-07-13
forum: Multimedia Software
---

### Post by EzeKB on 2010-07-13
Hi!
I'm a first timer on Ubuntu and I have a little problem with my Nvidia graphic card. After lots of attempts I can't get the 1280x1024 resolution that both of my monitors have. Instead I'm running on 1024x768.
Is this a way to fix it?
Thanks :)

---

### Post by paradiggum on 2010-08-02
I have a 7900 GS and am having the exact same problem. The screen looks like garbage in the 1024x768 resolution... in specific the text is almost unreadable.

---

### Post by JustinR on 2010-08-02
Not sure what you guys have done so far but, go to:

**System > Administration > Hardware Drivers**

And install the NVIDIA proprietary driver.

---

### Post by paradiggum on 2010-08-03
> **JustinR said:**
> Not sure what you guys have done so far but, go to:

**System > Administration > Hardware Drivers**

And install the NVIDIA proprietary driver.

Unfortunately the "current" driver did not work. It did not seem to give a decent number of resolutions of modern monitors, mine in particular.

What I tried to to is download the latest Linux-compatible drivers in hopes that would work. Even though I have the 7900GS it was the same file used for a very large amount of Nvidia products. I then tried to run the file. It gave a (1) "character encoding" error ("gedit has not been able to detect the character encoding"). Its a stupid error message because in fact .run files are not meant to be opened by gedit any way. I then right-clicked the file and checked the box allowing execution of the file as a program. I then tried to run the program and (2) absolutely nothing happened. I then tried again, and selected the run in terminal option. I then got an error message as follows:

(3) ERROR: nvidia-installer must be run as root

I then found out that one of the ways to "run as root" is to open up a console session using Ctrl+Alt+F2, entering my username and then password, then typing the commands (after copying the installation file to my Ubuntu desktop): (case sensitive!):
```
cd ~/Desktop 
sudo sh NVIDIA-Linux-x86_64-256.44.run
```The installer program ran and immediately gave an error message. The error message was something like:
(4) X server must be closed.

I then looked up ways to close X server and found a large number of different methods. The first method was to type the command (in the console screen you can get to with Ctrl+Alt+F2):
```
sudo /etc/init.d/gdm stop
```What that did was bring up a blank screen with a cursor. It also (3)froze my computer and so I had to restart. I then tried another methods suggested for closing X server. The recommended method was to type in the following command line:
```
sudo telinit 3
```That line seemed to do something. However, whatever it did, did not apparently stop X server because the error message about (5) x server must be closed remained. I then typed:

sudo telinit 5 because that was supposed to undo whatever the line sudo telinit 3 was supposed to do.

I then tried another suggestion to close x server as follows:
```
sudo invoke-rc.d gdm stop
```If I remember correctly (6)that command wasn't even recognized.

I then tried another suggestion for re-starting in console mode only without x server, which was the line:
```
sudo rcconf
```That line (7) was not recognized as a valid command if I remember correctly. It was supposed to work to start up Ubuntu in console mode so that x server never starts, but that is not what happened.

So I tried the three methods over again thinking I got one of them  wrong. Now, instead of them simply not working I also got an additional  error message when trying to type the "invoke" and "init.d" command  lines which read something like this:
(8) error: job was converted to an upstart So, apparently the telinit  line or something I did converted something else to "an upstart" job,  which of course I probably did not want to do.

I also saw a suggestion consisting of a whole bunch of lines including the phrase "linux-headers- `[uName -r` build" and a bunch of other mysterious stuff, but it didn't seem like a good idea so I never tried. Any way, I then tried another suggestion to use the following command line (again, using the ctrl-alt-f2 shortcut to get to):
```
sudo service gdm stop
```Shockingly, it worked! It actually stopped the x server. So, I typed:
```
sudo service gdm stop
cd ~/Desktop   [Note: The driver file was placed on the desktop]
sudo sh NVIDIA-Linux-x86_64-256.44.run
```This group of commands is what finally actually worked to stop x server and start installing the drivers.

After the installation proceeded, I got an error (9)"pre-install script failed". It seemed like something not too important so I clicked the continue button rather than cancel. But another error showed up saying:
(8)"Nouveau kernel incompatible with NVIDIA driver, and must be disabled"
It seemed like a bad idea to disable the driver, but also said I could later re-enable the kernel by deleting a certain file, and it also said that it could try disabling the kernel itself automatically, so I continued the installation. However, another error popped up saying:
(11)"Error: Installation has failed" and then referred to a log file.

Rather than seeing what the log file has to say I think I'd rather try out other suggestions to manually install the resolution wanted using a configuration file. And that is where I'm at right now. I'm very frustrated that I've up to this point I've so far run into 11 distinct and annoying obstacles getting into the way of me doing the very simple task of setting my display resolution to 1280x1024... which is not that uncommon of a resolution. It may seem like i'm not that frustrated because of the smilies but those are just numbers in parentheses that were supposed to be read as numbers instead of smileys. And I seem a very long ways off from actually doing this. So, any advice at this point is greatly appreciated.

---

### Post by mike4ubuntu on 2010-08-05
yes, you're on the right track.  Unfortunately, commands change frequently in Linux especially dealing services like the GNOME desktop manager (X Server desktop mgr, gdm) service.  You've found now that starting/stopping services is done by the service command.  You can look in the /etc/init directory to see all of the services you can control with the service command.  What most people do is type a ALT-CTRL-F1 to get a console window.  You can log into the shell as root if you know the password and if you've enabled root logins.  Otherwise you log in as normal user and type sudo bash to get to root priv.  Then you stop the gdm with service command.  However, in your case, since you were already running the nvidia-nouveau open source display drivers, instead of the nvidia proprietary drivers, you need to remove nouveau.

```

sudo apt-get --purge remove xserver-xorg-video-nouveau 

```
see the forum link
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by paradiggum on 2010-08-08
> **mike4ubuntu said:**
> yes, you're on the right track. Unfortunately, commands change frequently in Linux especially dealing services like the GNOME desktop manager (X Server desktop mgr, gdm) service. You've found now that starting/stopping services is done by the service command. You can look in the /etc/init directory to see all of the services you can control with the service command. What most people do is type a ALT-CTRL-F1 to get a console window. You can log into the shell as root if you know the password and if you've enabled root logins. Otherwise you log in as normal user and type sudo bash to get to root priv. Then you stop the gdm with service command. However, in your case, since you were already running the nvidia-nouveau open source display drivers, instead of the nvidia proprietary drivers, you need to remove nouveau.

```

sudo apt-get --purge remove xserver-xorg-video-nouveau

```see the forum link
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Thanks Mike, using the suggested command in the console (using ctrl-alt-F1) I was able to remove the Nouveau kernel. The latest Nvidia driver as of 08/05/10 is installed successfully.

Sadly, the maximum resolution available went down rather than up. I went to a tiny 640x480 screen after installing the latest Nvidia drivers. I should mention I have an NEC Multisync LCD 2010 XtraView monitor which is about 10 years old at this point.

The next step to try involved "manually" installing the resolution using Ubuntu configuration commands. It was recommended that I update the xorg.conf file using the following modification of the xorg.conf file:
```
Section "Screen"
    SubSection "Display"
        Modes      "1280x1024_60.00"
    EndSubSection
EndSection
```I found my xorg.conf file at the /etc/X11/xorg.conf filepath. After editing it, I hit save and recieved an error message something like:
(12) unable to modify file

Unfortunatley the permissions are not set to write to the file, only read it. To open it to a mode to write the file it was suggested I type in:
```
sudo gedit /etc/x11/xorg.conf
```In the terminal window (which is accessible at the very top-left screen corner using the menu). That did not work because (13) I was not paying attention to case. The filepath is case-sensitive. So I tried:
```
sudo gedit /etc/X11/xorg.conf
``` and I was able to edit and save the xorg.conf file.

By the way, you can also get into the xorg.conf file with write permissions, in the CD bootable version of Ubuntu 10.04, Amd64, (but not regular install), without using the terminal, by right-clicking on the xorg.conf file icon, then clicking "open with application", then clicking the "open using command" box at the bottom and typing "sudo gedit".

After editing the file, I had accomplished (13) absolutely nothing since it had no effect on my system. I then tried editing my xorg.conf file with:
```
Section "Monitor"
    Modes            "1280x1024_60.00"
EndSection
```Which (14) damaged my boot functionality and neither Ubuntu nor Windows would boot. I used the Ubuntu CD I made to get back online and found a recommended solution which I don't remember what it was but remember it (15) didn't work. So, I re-installed Ubuntu from the CD, which got my boot menu back. I blame it partly on my ASUS motherboard as it kept freezing up during the boot screen. I turned whatever I wasn't using off (like IDE) and it has not acted up again. I also now only put one device on the boot priority list.

At that point I wanted to give up but pressed on because I knew there was a lot of xrandr commands to try. First I typed this into a Ubuntu command terminal:
```
$cvt 1280 1024
```Which yielded this output:
```
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```I then typed this command:
```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```and then
```
xrandr
```which did list the new resolution I just typed in, added to the end of the list.

The next step was:
```
xrandr --addmode VGA1
```Which produced an error message (16) "VGA1 not found; Ignoring"
I also tried: VGA0, VGA1, VGA-0, and VGA-1 which also produced the same error message. In comparing my "xrandr" [by itself, without arguments, default] message with others I realized the problem which is that my connection was not a "VGA1" connection but rather it read "default" in place of where other people's connections read VGA1. In specific, the xrandr command (without arguments) reads as follows:
```

Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
  1280x1024_60.00 (0x1c5)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

```I then tried the command:
```
xrandr --addmode default 1280x1024
```This seemed to work as it did not produce any error message. I then typed:
```
xrandr --output default --mode 1280x1024_60.00
```
which produce the following error message (17): "Screen cannot be larger than 640x480."  Apprently if, when you type in the command:
```
xrandr
``` and it lists your maximum resolution as 640x480, the xrandr commands will do absolutely nothing for you.

I searched the error message and found another person who had the same problem. He also had no VGA1 connection and only had "default". And like him, he was unable to increase his resolution. For people with VGA1 connections the commands seem to work. However, for people without VGA1 like myself with only a "default" connection, the xrandr commands do not seem to work at all and I'm not so sure there is any solution.

I think I should give up and go back to Windows at this point. :(

---

### Post by kelvin spratt on 2010-08-08
if you are using the nvidia graphic card drivers you use the terminal and type "gksudo nvidia-settings". to set your resulotion not xrand. sudo does not save the settings on reboot hence the elevated settings.

---

### Post by mike4ubuntu on 2010-08-09
I just noticed that sometime last week, nvidia 256.44 was added to the standard repository, so now you should be able to use the System -> Drivers menu option to install them.  This will also install the nvidia settings applet also under the System menu.  You can also execute the settings config aplet like Kevin suggested from the command line 

> gksudo nvidia-settings

The xrandr command only sets the config temporarily, and I have had problems with that as well.  With the proprietary nvidia 256.44 drivers, you shouldn't even really need the xorg.conf file, if the drivers are working properly for your graphics chipset.  You can delete it or back it up like this

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.save
```

remember, to modify any system files, like this one, you need to escalate to system privilegs first, and that's what the sudo command is for.

I'll warn you though, I have problems with the nvidia 256.44 drivers on my Thinkpad T61 with the nvidia NVS 140m chipset.  It looks like some support for older chipsets got removed in this nvidia release.  My other nvidia based systems seem to be ok

---

### Post by paradiggum on 2010-08-13
> **kelvin spratt said:**
> if you are using the nvidia graphic card drivers you use the terminal and type "gksudo nvidia-settings". to set your resulotion not xrand. sudo does not save the settings on reboot hence the elevated settings.

Thanks for the advise, but the monitor settings automatically divert to Nvidia's control panel when clicking the monitor settings icon. Therefore, the gksudo nvidia-settings command really is not necessary. The whole problem I've been having is that Nvidia's control panel is missing resolutions greater than 640x480.

---

