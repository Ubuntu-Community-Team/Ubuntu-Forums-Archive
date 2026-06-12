---
title: "Video card &amp; sound card issues"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by xnn-ro on 2007-09-19
Hey ppl. I'm having some problems here :D My Ubuntu is set to start gnome automatically (the default way). However, before the login screen is drawn, I only see the "loading" mouse cursor and everything is black. I have to:

```
CTRL + SHIFT + ALT + F1
// Login in text mode
sudo rm -rf /tmp/.X0-lock
startx
```

And everything runs ok. But I suppose there's a problem with the display drivers, since it should work ok, and it does (with vesa driver).

My stuff: Ubuntu 7.04 (Feisty) + NVidia GeForce 7600GT (256/256) + nvidia-glx driver.

```
uname -r
2.6.20-16-generic
```

Also, I have a Creative Audigy SE sound cart, but it sounds a little crappy (I'm using Amarok, with the full bass & treble eq). I also visited alsa-mixer, but no improvements. It should sound very smooth (so it does on win - without the EAX stuff, too). Thanks in advance for your help.

---

### Post by HellBoyz77 on 2007-09-20
Maybe Gnome try to start some service and something go wrong.

Have you checked with dmesg?

---

### Post by xnn-ro on 2007-09-21
Only found this...

```
nvidia: module license 'NVIDIA' taints kernel.
NET: Registered protocol family 17
ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) ->
PCI: Setting latency timer of device 0000:01:00.0 to 64
NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
```

Don't know what to do next :confused: Any more ideas?

---

### Post by HellBoyz77 on 2007-09-22
I'm not a Linux veteran, but i try to reason with you about this problem ...

I've checked my dmesg and is similar to your's, the main difference is that i use a recompiled vanilla kernel with the latest nvidia drivers downloaded directly from their site.

Maybe you can check the login window option in the system -> administration. I use the italian version so is better that you post here the option that you use in the various tab, so i can compare it with the mine.

Also you can check the .xsession-errors with less .xsession-errors in your home folder. Maybe some interesting info lay there.

---

### Post by xnn-ro on 2007-09-23
Didn't know about .xsession-errors, but the last session info is below:

```
** (gnome-session:5452): WARNING **: Failed to authenticate with GDM
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
kded: Fatal IO error: client killed
kdeinit: Fatal IO error: client killed
klauncher: Exiting on signal 15
klauncher: Fatal IO error: client killed
Xsession: X session started for xenon at Sun Sep 23 14:43:24 EEST 2007
SESSION_MANAGER=local/xenon:/tmp/.ICE-unix/5614

(gnome-panel:5670): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -12 and height 24
inotify_add_watch: No such file or directory
Initializing gnome-mount extension
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80993c8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80993c8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(gnome-terminal:6216): Vte-WARNING **: No handler for control sequence `device-control-string' defined.
```

As you can see, there's some info about bad devices, but it doesn't say which devices (I can only assume it's the video card). Thanks alot for your involvement.

PS: the video card is on PCI Express, if that helps.

LE: just discovered this weird problem. When clicking System -> Administration -> Login window, gnome crashes (or tries to restart itself, I suppose), and it remains in the initial state (black screen with the loading cursor). That happened 3 times in a row. Every time I want to go to Administration -> Login window, the window itself appears, but Gnome crashes (??). If I then press CTRL + ALT + F1, I only see an error message (3 times) that says something about not being able to load /dev/input/wacom. This is so weird. Then I press CTRL+C and I'm given the command line, in which I type startx and everything starts as it should.

---

### Post by HellBoyz77 on 2007-09-23
Have you tried to reinstall GDM? 
sudo apt-get install --reinstall gdm

In alternative:
sudo apt-get remove --purge gdm
sudo apt-get install gdm

Maybe this should work

---

### Post by xnn-ro on 2007-09-24
Nope, that didn't do it, either. Last night I tried to fix all this mess, and purged nvidia-glx + linux-restricted-modules + everything that was related to it, and install the proprietary NVidia driver. However, that didn't start, because of a missing /sbin/lrm-video app/file. Then I decided to remove that and stick with nvidia-glx for now, because I've got a lot of work to do and I really don't need 3D acceleration atm, since I only work with Eclipse PDT and listen music using Amarok :D

Thanks alot for all your help. I'll reinstall the whole system one day and I'll try to be more careful about it :)

---

