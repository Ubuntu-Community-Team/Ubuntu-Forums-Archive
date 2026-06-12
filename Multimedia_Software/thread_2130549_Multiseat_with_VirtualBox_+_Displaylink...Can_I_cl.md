---
title: "Multiseat with VirtualBox + Displaylink...Can I clone displays? Also added tutorial."
date: 2013-03-29
forum: Multimedia Software
---

### Post by statikregimen on 2013-03-29
**Scroll down a few replies for the tutorial**

HI all... I am setting up an interesting pseudo-multiseat environment on my computer, using a 64bit Windows 7 Pro host OS, with VirtualBox 4.2.10 running 64bit Ubuntu Server 12.04 guest OS, installed with the "minimal virtual machine" option and the minimum additional packages to get VBox Guest Additions and LXDE up and running. Attached to my computer is a [Kensington universal USB docking station]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834991988&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-") with DVI output via DisplayLink, LAN, Audio and attached USB keyboard/mouse. All of those devices have been filtered to the guest OS successfully. I've managed to get the displaylink working with the guest and Xorg/LXDE looks nice and runs fairly smooth; the keyboard, mouse and LAN work fine - was even able to install the system with Vbox networking disabled. I have not messed with sound yet.

There are just two problems I need help with, that I anticipate will be very simple:

1) [SOLVED - SEE POSTS BELOW] My biggest issue for now is that almost ALL menus are opening off the screen - any menu in any application, including all LXDE menus *except* the middle click desktop switcher, opens to where I can just see a 1-2 pixel tall horizontal line (about the width I would expect the menu to be), in the upper left corner of the screen. The mouse is confined to the space just fine and windows maximize/resize properly. It seems like something has bum coordinates set somewhere...EDIT: I just noticed that menus like File/Edit/Etc do not open in the upper left corner, but are 1px tall horizontal bars that open along the left edge...it's very odd. I will try to provide a screenshot, if I can...

2) [UNSOLVED] I would like the VBox virtual display to mirror/duplicate/clone the DisplayLink output, so I can work on the guest from the host seat (the guest will be used as a family computer, as I do not like people using my machine, especially when I'm on it)... SO, I'm hoping there's a way to have Xorg output the same thing to two devices?

The first problem, I'd guess, lies in my Xorg configuration, and presume that's what i'll need to adjust to get the displays mirrored as well. 

To set up the displaylink, I followed [this guide]("http://how-to.cc/get-a-displaylink-video-adapter-working-with-ubuntu-12-04"), creating the file /usr/share/X11/xorg.conf.d/52-displaylink.conf as directed, then copied/pasted/adjusted the provided config. Here is what I have so far:

```

[COLOR=black][FONT=Consolas]Section "Device"[/FONT][/COLOR][COLOR=#444444][FONT=Consolas]  
 Identifier "vbox1"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  driver "vboxvideo"
[COLOR=black]EndSection[/COLOR][/FONT][/COLOR]

[COLOR=#444444][FONT=Consolas]Section "Device"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Identifier "dl1"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  driver "displaylink"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Option "fbdev" "/dev/fb1"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]EndSection[/FONT][/COLOR]

[COLOR=#444444][FONT=Consolas]Section "Monitor"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Identifier "monitor0"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]EndSection[/FONT][/COLOR]

[COLOR=#444444][FONT=Consolas]Section "Monitor"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Identifier "monitor1"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]EndSection[/FONT][/COLOR]

[COLOR=#444444][FONT=Consolas]Section "Screen"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Identifier "screen0"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Device "dl1"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Monitor "monitor0"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  DefaultDepth 16[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]EndSection[/FONT][/COLOR]

[COLOR=#444444][FONT=Consolas]Section "Screen"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Identifier "screen1"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Device "vbox1"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Monitor "monitor1"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  DefaultDepth 16[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]EndSection[/FONT][/COLOR]

[COLOR=#444444][FONT=Consolas]Section "ServerLayout"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Identifier "multihead"[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]  Screen 0 "screen0"[/FONT][/COLOR]
[COLOR=black][FONT=Consolas]EndSection
[/FONT][/COLOR]
```

The DisplayLink is being properly set to 1280x1024, the attached monitor's native resolution, and like I said, LXDM and LXDE come up and I am able to log in and (mostly, except the menus issue) use it.

Thank you in advance for any assistance and I will be writing up a comprehensive guide on how to get this all working, as soon as I do! Once I do get it all sorted out, I plan to do a similar setup with an ELO touchscreen in my kitchen + a seat for my big screen :D

---

### Post by statikregimen on 2013-03-30
So I tried Xfce and get the same result with the menus (see above or below for description of the problem). Also tried Windows 7 as a guest and displaylink and sound were both a total no-go, so it's up to linux to save the day!

If you have any ideas what might cause this issue, please let me know!
 
To reitterate: ALL menus, including right-click context, main menus, panel menus, etc. appear as a 1-2 pixel thick horizontal lines about the width you'd expect the menu to be, along the left edge of the screen. It's really weird and it doesn't make any sense...I mean, I'm not a Linux noob (maybe intermediate) and have sussed out some pretty strange problems, but this one is far beyond me =/

---

### Post by statikregimen on 2013-03-30
Victory is mine!

I upgraded Xorg from [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa"), which puts me at 1.12.3. Then I updated my xorg.conf as follows:
[COLOR=#000000][FONT=monospace]
[/FONT][/COLOR]```

[COLOR=#000000][FONT=monospace]Section "Device"
  Identifier "Card1"
  driver "fbdev"  
  Option "fbdev" "/dev/fb0"  
  Option "ShadowFB" "on"
EndSection
[/FONT][/COLOR]
```[COLOR=#000000][FONT=monospace]

[/FONT][/COLOR]Using displaylink with newer versions of Xorg (that come after whichever version ships with Ubuntu 12.04) doesn't seem to be well documented (or I'm just bad at google)... The steps have changed a little, and all of the search hits come up with outdated/non-working instructions (e.g. the package xserver-xorg-video-displaylink no longer exists, which current tutorails/how-tos call for).[COLOR=#000000][FONT=monospace]
[/FONT][/COLOR]
So the menu issue is resolved now, with the updates, and it seems that my little multiseat experiment is going to be a success!

Also, if anybody can please tell me how/if I can make the virtualbox display mirror/duplicate the displaylink - again, I feel like this can be done and I've googled my fingers raw with no answers. It seems like it happens by default/accident to most people and they DONT want it, but I DO want it...

---

### Post by statikregimen on 2013-03-31
[COLOR=#474B4E][FONT=Helvetica]Tip: since the udlfb may jump between /dev/fb*, I found this little gem, [here]("http://charlesoram.blogspot.com/2012/09/lilliput-um-80ct-usb-display-with.html"):

[/FONT][/COLOR]Configure udev to create a symbolic link to the DisplayLink framebuffer device by creating the following file:

/etc/udev/rules.d/80-displaylink.rules

And in it, put:
```
# Match DisplayLink USB display
KERNEL=="fb[0-9]*", SUBSYSTEMS=="graphics", ATTR{name}=="udlfb", SYMLINK+="fbdl"
```


Finally, update xorg.conf:
```
Option "fbdev" "/dev/fbdl"
```

---

### Post by statikregimen on 2013-03-31
Consolidated how-to to get as far as I have:

I'm using VirtualBox 4.2.10, running Ubuntu Server 12.04 on a Windows 7 Pro 64-bit host machine. The purpose of this little project was to provide a "family/guest computer" running on just one physical machine - not much unlike a multiseat setup. So, you'll just need a spare keyboard, mouse, monitor and displaylink adapter + whatever USB cables you'll need to run (hint: I use a universal USB docking station by Kensington, so I just need 1 cable or you could use a wireless keyboard and mouse or hub to reduce cables). For my setup, the guest seat is in a room just on the other side of a wall from my computer, so I have run an 8ft USB cable through the hole my ethernet was already going through.

My host machine is an Intel i7-2600k with 2 GTX 570s in SLI, EVGA P67 FTW motherboard, 8gb DDR3 1600mhz RAM, 120gb SATA3 SSD with 3 monitors attached to/used by the host.

At the end of this tutorial, you should have a working VirtualBox guest with it's own keyboard, mouse and dedicated displaylink-attached monitor. You can go ahead and attach everything now, and I would strongly suggest disabling, in the host's device manager, the USB devices you'll be filtering to the guest, to avoid device busy issues.

1. Create a new virtual machine with desired USB filters [http://www.virtualbox.org/manual/ch03.html](http://www.virtualbox.org/manual/ch03.html) - I configured mine with 2 CPUs, 1024mb RAM, 8gb HDD, 64mb video memory and it runs fairly well (tho you could do this with a lot less). I also enabled VRDP on port 3391, which allows me to at least grab a console to work on the VM. However, until somebody tells me how to clone 2 displays, console is all you're gonna get and you have to obviously ctrl+alt+f* and log in (well, I suppose you /could/ set up a multiseat within a multiseat). Also, it seems for some reason /dev/fb* is not available and X will not start on a fresh boot (tho it seems to do ok on a soft reboot), forcing me to connect on VRDP and relaunch X... 
2. Download Ubuntu Server 12.04 (so far 12.10 has been a complete no-go for me)
3. Boot the VM with the iso - a screen should come up asking you to select a language - chose and hit enter, then hit F4 and chose "minimal virutal machine"; hit enter twice
4. Follow the steps to installing Ubuntu
5. Once you've booted into your new OS, run 
```
sudo su
apt-get update && apt-get dist-upgrade && apt-get install nano acpid
``` 
- I would reboot at this point

6. Add the xorg-edgers PPA and install X (NOTE: You can probably use their more stable repository: ppa:ubuntu-x-swat/x-updates, but for this tutorial, I used the bleeding edge stuffs): 
```
sudo su
apt-get install python-software-properties && add-apt-repository ppa:xorg-edgers/ppa && apt-get update && apt-get install lxde build-essential
```
- might want to reboot again to make sure everything is working, or at least run startx

7. Install virtualbox guest additions...Click inside the guest VM window, press host-key+D (host-key is usually right ctrl) to load the guest additions iso, then:
```
sudo su
mount /dev/cdrom /media/cdrom && /media/cdrom/VBoxLinuxAdditions.run
```
Note: My VBoxGuestAdditions.iso wouldn't mount - was corrupted some how - to remedy this, simply re-download it from [here]("http://download.virtualbox.org/virtualbox/4.2.10/VBoxGuestAdditions_4.2.10.iso")... just copy/move it into your C:\Program Files\Oracle\VirtualBox\, delete or rename the old, and rename the new VBoxGuestAdditions.iso and repeat this step.

8. Create a udev rule to give us a symlink (/dev/fbdl) that always points to the displaylink framebuffer for xorg.conf: 
```
sudo echo 'KERNEL=="fb*", ATTR{name}=="udlfb", SYMLINK+="fbdl"' > /etc/udev/rules.d/80-displaylink.rules
```
9. Generate and edit your xorg.conf file: drop out to a terminal (ctrl+alt+f1) and run 
```
sudo su
service lxdm stop && X -configure && cp /root/xorg.conf.new /etc/X11/xorg.conf && nano /etc/X11/xorg.conf
```
- Assuming you configured just one virtual display through virtalbox, a working xorg.conf file, at this point, should look a lot like this (you can probably just copy and paste, skipping the step above):

```

Section "ServerLayout"
        Identifier       "X.org Configured"
        Screen      0  "Screen1" 0 0
        InputDevice   "Mouse0" "CorePointer"
        InputDevice   "Keyboard0" "CoreKeyboard"
EndSection


Section "Files"
        ModulePath  "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection


Section "Module"
        Load  "record"
        Load  "dri2"
        Load  "glx"
        Load  "extmod"
        Load  "dbe"
        Load  "dri"
EndSection


Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection


Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option     "Protocol" "auto"
        Option     "Device" "/dev/input/mice"
        Option     "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
        Identifier       "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection


Section "Monitor"
        Identifier       "Monitor1"
        VendorName  "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection


Section "Device"
        Identifier  "Card0"
        Driver      "vboxvideo"
        BusID       "PCI:0:2:0"
EndSection


Section "Device"
        Identifier  "Card1"
        Driver      "fbdev"
        Option     "fbdev" "/dev/fbdl"
        Option   "ShadowFB" "off"         # Set this to whatever gives better performance - I've not tested much, but seems not much difference either way...
EndSection


Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
EndSection


Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
EndSection

```
Now, it would seem that 9 times out of 10, /dev/fb* doesn't exist in time for X to use on boot/reboot, requiring me to log in and run "sudo service lxdm start"...Then it starts fine.

To fix this, I edited /etc/init/lxdm.conf and around line 55-57, tell it to sleep for a bit before running (this probably could be 1-2s, but I'm not sure):
```
export XORGCONFIG
sleep 10s
exec lxdm-binary $* $CONFIG_FILE
```

Further thoughts: 

1. I would like to be able to put the host to sleep at night, however it never succeeds while the VM is running (guessing because of the USB filters), requiring a manual shut down of the VM beforehand. One way to automate this, is to download and configure VBoxVMService (very easy and so far I've only tested with ShutdownMethod=acpipowerbutton), then create a new task in Windows Task Scheduler (click start, type "task" and it should be the first result). Add new trigger to the Triggers tab, configured as follows:

Begin the task: On an event
Settings: Basic
Log: System
Source: Kernel-Power
 Event ID: 42 

Then add an Action in the Actions tab, configured like:

Action: Start a program
Program/script: net
Add arguments (optional): stop VBoxVMService

Of course, if you use VBoxVMService, it's a good idea to enable VRDP on the guest, so you grab a tty without having to get up :)

Additionally, to have the machine wake back up at a set time in the morning, you could create a new daily task to run the program "net" and arguments "start VBoxVMService" and under the Conditions tab, check "Wake the computer to run this task".

2. Try a USB audio adapter for dedicated guest audio. My docking station has one built in, but it seems to hard lock the VM or the VM wont shut down; either way causing a stuck process on the host that forever uses 13% cpu until it is rebooted). I have yet to get any further.

Hope this helps somebody! Cheers.

---

### Post by statikregimen on 2013-04-19
Updated VirtualBox to 4.2.12 with minimal fuss :)

---

