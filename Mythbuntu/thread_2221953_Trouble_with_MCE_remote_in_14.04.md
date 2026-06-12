---
title: "Trouble with MCE remote in 14.04"
date: 2014-05-04
forum: Mythbuntu
---

### Post by Jukka_Larja on 2014-05-04
Hi all

Few days ago I installed Mythbuntu 14.04 to a new box. Everything went well enough (relatively speaking) and I got important things working. The remote worked out of the box right after the install. Today, I moved the system to my "AV rack" and while doing that, forgot to connect the Windows Media Center USB remote. After some head scratching I noticed my mistake, but for some reason couldn't get remote to work again.

In fact, I can't get any input from the remote. Not with irw, mode2 or ir-keytable. Everything seems to be fine, but there's just no input. Just to make sure, I tested the remote in another computer, where it worked fine. There are no error messages anywhere I can find, lsusb shows the device and when plugged in, there's normal looking message in dmesg. I'm running out of ideas on how to debug this.

One more thing, which may be related or not. It seems that I crashes the box once or twice when unplugging the remote's receiver. Google turned up some old(ish) messages, but they seemed to indicate that the particular problem was fixed several kernel revisions ago. Anyway, it didn't seem to be related, though you never know.

Anyway, if someone has had similar problems, I'd be happy to hear how you fixed them. Any suggestions on how to further debug this are also welcome. I've been running MythTV box since 2008 and Mythbuntu since 2009 (I think), and do Linux sysadmining as part of my job, so I might be able to get something done even with incomplete suggestions. This is a "production" system though, so I rather not do re-install just to see if that would fix it.

-JLarja

---

### Post by squakie on 2014-05-05
This is going to sound strange, but bear with me.........I have an IR receiver (USB) I use with a remote configured as a MCE remote to use with XBMC on the Pi.  The same exact things happens there as well.  The solution:  unplug the device, power off the system, plug the device back in, power on the system.  Don't know why - it does appear that some of IR receivers aren't always hot pluggable.  Not sure if that is any part of your problem or not.

---

### Post by Jukka_Larja on 2014-05-05
Thanks for the suggestion. Unfortunately, it doesn't seem to do anything here. I have rebooted several times before. This time, I did like you said (unplugged, switch the system off, even the PSU, plugged in, switched system on). No change.

-JLarja

---

### Post by khPWXxF on 2014-05-06
I have certainly had an issue with USB devices not working after changes which seem quite unrelated.  My Hauppauge T500 DVB tuner (a PCI device but with onboard USB bus) will consistently stop working after a change of display device (eg VGA to HDMI).  I have not chased this problem because a cold boot fixes it but think that a UDEV rule would also fix it.
 
As for your present issue, I’ll suggest 2 things, though they are rather stabs in the dark as I have yet to try a remote with 14.04.
 
Stab 1 has worked in the past:
 
Find your device and note the event number with:
```
cat /proc/bus/input/devices
``` 
In my case it's on a line ```
H: Handlers= kbd event 4
```
Try to set the ‘event’ number in the infrared section in Mythbuntu control centre.  Note that there used to be (still is?) a bug whereby it did not prompt for the device unless you deleted and re-installed it.
 
Stab 2
 
As far as I can gather, the sequence of getting from a remote key press to action on the screen goes like this:
 
a) The file /etc/lirc/hardware.conf defines for lirc where to look for the device.  Look for the line: 
```
cat /etc/lirc/hardware.conf
[...]
REMOTE_DEVICE= “/dev/lirc0”
[...]
```
I’m not entirely sure how one finds out the device but on my system it matches the output of ```
ls –l /dev ¦ grep lirc
```
 
b) The file /etc/lirc/lircd.conf (and include files) defines the pulse patterns for each remote key.  “If you see 10001110000 pulses then channel up has been pressed on the MCE remote, but if you see 111110000 then it’s red button on a Samsung remote ” These codes are pure fiction of course!
 
c)  ~/.mythtv/lircrc (or the linked file) translates those remote keys  to the keystrokes you would use to control mythtv from a real keyboard (or any other application for that matter).    Keystroke names need to match those in /etc/lirc/lircd.conf exactly.
 
d) Mythtv keybindings say which keyboard key to look for in each frontend menu.
 
Hope this moves you on a bit, but if you can fill in any of the blanks or provide corrections then please do so.   I'll be following you once I fix my nvidia graphics.
 
Phil

---

### Post by Jukka_Larja on 2014-05-07
Thanks for your answer, though unfortunately it didn't help.

> **khPWXxF said:**
> I have certainly had an issue with USB devices not working after changes which seem quite unrelated.  My Hauppauge T500 DVB tuner (a PCI device but with onboard USB bus) will consistently stop working after a change of display device (eg VGA to HDMI).  I have not chased this problem because a cold boot fixes it but think that a UDEV rule would also fix it.
 
As for your present issue, I’ll suggest 2 things, though they are rather stabs in the dark as I have yet to try a remote with 14.04.
 
Stab 1 has worked in the past:
 
Find your device and note the event number with:
```
cat /proc/bus/input/devices
``` 
In my case it's on a line ```
H: Handlers= kbd event 4
```
Try to set the ‘event’ number in the infrared section in Mythbuntu control centre.  Note that there used to be (still is?) a bug whereby it did not prompt for the device unless you deleted and re-installed it.
 

I can see the remote in the listing at /proc/bus/input/devices, along with bluetooth keyboard+mouse combination and other stuff (audio plugs, power button etc.). However, the Mythbuntu Control Centre's infrared section doesn't seem to have anywhere that I could set event number to. I have tried toggling remote on and off in Control Centre, but that didn't seem to have any effect.

> **khPWXxF said:**
> 
Stab 2
 
As far as I can gather, the sequence of getting from a remote key press to action on the screen goes like this:
 
a) The file /etc/lirc/hardware.conf defines for lirc where to look for the device.  Look for the line: 
```
cat /etc/lirc/hardware.conf
[...]
REMOTE_DEVICE= “/dev/lirc0”
[...]
```
I’m not entirely sure how one finds out the device but on my system it matches the output of ```
ls –l /dev ¦ grep lirc
```
 
b) The file /etc/lirc/lircd.conf (and include files) defines the pulse patterns for each remote key.  “If you see 10001110000 pulses then channel up has been pressed on the MCE remote, but if you see 111110000 then it’s red button on a Samsung remote ” These codes are pure fiction of course!
 
c)  ~/.mythtv/lircrc (or the linked file) translates those remote keys  to the keystrokes you would use to control mythtv from a real keyboard (or any other application for that matter).    Keystroke names need to match those in /etc/lirc/lircd.conf exactly.
 
d) Mythtv keybindings say which keyboard key to look for in each frontend menu.
 
Hope this moves you on a bit, but if you can fill in any of the blanks or provide corrections then please do so.   I'll be following you once I fix my nvidia graphics.
 
Phil

Thanks for your tips, but I think the problem is at lower level. Using ir-keytable I get:
```

root@Willow:~# ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event5) with:
        Driver mceusb, table rc-rc6-mce
        Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other
        Enabled protocols: LIRC
        Name: Media Center Ed. eHome Infrared
        bus: 3, vendor/product: 0471:0815, version: 0x0000
        Repeat delay = 500 ms, repeat period = 125 ms

```

But in test mode (ir-keytable -t) I get nothing. No error or anything like that, just no input.

I'm having bit of a hard time trying to trouble-shoot right now. Too much TV shows need to be recorded, so it's a bit hard to find a time when I can boot the box. Realistically speaking I probably won't be doing much before Saturday, but if you (or anyone else) has any suggestions, I'll be sure to remember them.

-JLarja

---

### Post by Dave_Alverson on 2014-05-07
> **Jukka_Larja said:**
> 


Thanks for your tips, but I think the problem is at lower level. Using ir-keytable I get:
```

root@Willow:~# ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event5) with:
        Driver mceusb, table rc-rc6-mce
        Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other
        Enabled protocols: LIRC
        Name: Media Center Ed. eHome Infrared
        bus: 3, vendor/product: 0471:0815, version: 0x0000
        Repeat delay = 500 ms, repeat period = 125 ms

```

But in test mode (ir-keytable -t) I get nothing. No error or anything like that, just no input.

-JLarja

I think the **Enabled protocols: LIRC** is the problem.  You should have RC-6 enabled.  

Try stopping lirc, then run ir-keytable and if RC-6 is now enabled, then try "ir-keytable -t".  If those work, then I think you need to have:

DISABLE_KERNEL_SUPPORT=false

in your /etc/lirc/hardware.conf file.

---

### Post by Jukka_Larja on 2014-05-08
(Hah, I did manage to get home in time for an hour of troubleshooting :) )

> **Dave_Alverson said:**
> I think the **Enabled protocols: LIRC** is the problem.  You should have RC-6 enabled.  

Try stopping lirc, then run ir-keytable and if RC-6 is now enabled, then try "ir-keytable -t".  If those work, then I think you need to have:

DISABLE_KERNEL_SUPPORT=false

in your /etc/lirc/hardware.conf file.

Doesn't seem to help. Stopping lirc doesn't affect the Enabled protocols line, neither does adding DISABLE_KERNEL_SUPPORT="false" to hardware.conf and rebooting. ir-keytable -t stays silent.

-JLarja

---

### Post by Dave_Alverson on 2014-05-08
I'm still on 12.04 and in that version, the lirc init script will set enabled protocols to just LIRC when started if LOAD_MODULES is true.  In a later version of the lirc package (0.9.0-0ubuntu3), it would also only do the disable if DISABLE_KERNEL_SUPPORT is true.  I cant think of anything else that would be tweaking the enabled protocols for your remote.  I believe at startup, all the protocols are enabled.

You can try manually setting the protocol with this:

```
sudo  echo "rc-6" > /sys/class/rc/rc0/protocols
```

Then see what ir-keytable shows for enabled protocols, and try "ir-keytable -t".

NOTE: if there is no DISABLE_KERNEL_SUPPORT set in hardware.conf, it will default to "true" to emulate the way the older script ran.

---

### Post by Jukka_Larja on 2014-05-09
There's DISABLE_KERNEL_SUPPORT="false" by default in hardware.conf. I did try setting it to true for a while. I haven't done any manual tweaking before the troubleshooting. After the initial install, remote just worked (TM). Then it just stopped working. I'm about 98 % certain that I have reverted all the changes I've been doing during the troubleshooting, though I may have forgotten something at some point.

Doing the echo "rc-6" > /sys/class/rc/rc0/protocols did change the ir-keytable output:

```

Found /sys/class/rc/rc0/ (/dev/input/event4) with:
        Driver mceusb, table rc-rc6-mce
        Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other
        Enabled protocols: RC-6
        Name: Media Center Ed. eHome Infrared
        bus: 3, vendor/product: 0471:0815, version: 0x0000
        Repeat delay = 500 ms, repeat period = 125 ms

```

... but unfortunately ir-keytable -t still shows now input.

I guess there isn't any more low-level way of monitoring input in Linux for mere mortals. There's always the possibility that the receiver really is broken, just in some weird way that still allows it to work in Windows.

Edit: I did some testing with evtest. It lists 
```

/dev/input/event4:      Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)
/dev/input/event5:      MCE IR Keyboard/Mouse (mceusb)

```

but doesn't show any input for either. I don't whether that's surprising or not considering the silence of ir-keytable.

Edit:

Since I still have the old 12.04 box sans TV-tuners and big disks, I fired it up and tested the remote with it. It did work with irw and once I shut down lirc, also in ir-keytable. So apparently not a hardware problem at least on remote's side. Ir-keytable shows (with lirc disabled):
```

Found /sys/class/rc/rc0/ (/dev/input/event2) with:
        Driver mceusb, table rc-rc6-mce
        Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other
        Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC other
        Repeat delay = 500 ms, repeat period = 125 ms

```

Apart from SANYO, seems to be the same list as on 13.04.

Just another data point. Unfortunately I don't see how this would help.

-JLarja

---

### Post by khPWXxF on 2014-05-11
Not sure it adds anything new to the equation but I'll mention it anyway.  This article has a pointer to a comprehensive XBMC article on LIRC.
[https://forum.mythtv.org/viewtopic.php?f=36&t=123](https://forum.mythtv.org/viewtopic.php?f=36&t=123)
Phil

---

### Post by Dave_Alverson on 2014-05-13
Just to be sure, you are running ir-keytable -t under root/sudo?  Also, here are the rc and ir modules I have loaded on my 12.04 system:
```
davea@dvr:~$ lsmod | grep "rc\|ir"
libcrc32c              12644  1 btrfs
ir_lirc_codec          12859  0 
lirc_dev               19204  1 ir_lirc_codec
ir_mce_kbd_decoder     12777  0 
ir_sony_decoder        12510  0 
ir_jvc_decoder         12507  0 
ir_rc6_decoder         12507  0 
ir_rc5_decoder         12507  0 
rc_rc6_mce             12502  0 
ir_nec_decoder         12507  0 
rc_core                26412  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,mceusb
```

---

### Post by Jukka_Larja on 2014-05-14
Yes, running under root (I get permission denied as a regular user, so hard to do that by accident). 

Here's what I get from lsmod | grep "rc\|ir" :

```

crct10dif_pclmul       14289  0
crc32_pclmul           13113  0
ir_lirc_codec          13021  3
lirc_dev               19980  1 ir_lirc_codec
ir_mce_kbd_decoder     13214  0
ir_sanyo_decoder       12839  0
ir_sony_decoder        12713  0
ir_jvc_decoder         12751  0
ir_rc6_decoder         12874  0
ir_rc5_decoder         12710  0
ir_nec_decoder         12915  0
rc_rc6_mce             12502  0
rc_core                28124  12 lirc_dev,ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,mceusb,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
libcrc32c              12644  1 btrfs

```

Compared to your output, there seems to be and extra lirc_dev and ir_sanyo_decoder.

I haven't had any new ideas about this, so I've resigned and used the box with Logitech small diNovo keyboard / touchpad combination. The most annoying thing is actually that I have to use SSH to restart lightdm every time I power off the TV (some trouble with HDMI apparently). I had a nice script bound to remote's red button for that.

-JLarja

---

### Post by dannyboy79 on 2014-05-14
not sure about your remote issue but the issue about having to restart lightdm everytime the tv is shut off is related to your xserver not receiving any signal from your tv over hdmi so it stops working. Is the tv providing accurate EDID information? Try to add this to your xorg.conf file
```

Option "ConnectedMonitor" "DFP"
Option "UseDisplayDevice" "DFP-0
```
but i'd have to see your Xorg.0.log file for sure

---

### Post by Jukka_Larja on 2014-05-17
> **dannyboy79 said:**
> not sure about your remote issue but the issue about having to restart lightdm everytime the tv is shut off is related to your xserver not receiving any signal from your tv over hdmi so it stops working. Is the tv providing accurate EDID information? Try to add this to your xorg.conf file
```

Option "ConnectedMonitor" "DFP"
Option "UseDisplayDevice" "DFP-0
```
but i'd have to see your Xorg.0.log file for sure

I can't seem to find the xorg.conf. It's not in the usual /etc/X11/xorg.conf and locate can't find it either. X seems to use "system config directory", but I probably shouldn't directly edit the files there.

Mythbuntu box is actually attached to Yamaha AV receiver, but the same problem was present when attached directly to TV (though I wasn't looking at logs then). I didn't actually think there's anything particularly wrong. I just though it was being stupid and defaulting VGA or DVI, HDMI was turned off. That's what it seems to do on every Intel GPU driven Linux computer I try to run via HDMI. I don't actually need to restart lightdm to move the picture back to HDMI, but it's a lot easier than changing TV's input to VGA and navigating the menus. In kern.log there are following lines:

```

May 17 06:43:56 Willow kernel: [397068.851404] HDMI: ELD buf size is 0, force 128
May 17 06:43:56 Willow kernel: [397068.851445] HDMI: invalid ELD data byte 0

```

I attached the Xorg.0.log file below. Output on turning on the receiver and TV starts from the line

```
[396605.412] (II) intel(0): EDID vendor "MEI", prod id 41126
```

I don't see anything obviously wrong there, but frankly, X has always been a mystery to me :) .

```

[360409.080] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[360409.080] X Protocol Version 11, Revision 0
[360409.080] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[360409.080] Current Operating System: Linux Willow 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64
[360409.080] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=1f76c59f-c7bd-400c-9497-2a4b9d5cccac ro quiet splash vt.handoff=7
[360409.080] Build Date: 16 April 2014  01:36:29PM
[360409.080] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[360409.080] Current version of pixman: 0.30.2
[360409.080]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[360409.080] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[360409.080] (==) Log file: "/var/log/Xorg.0.log", Time: Fri May 16 20:40:40 2014
[360409.081] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[360409.082] (==) No Layout section.  Using the first Screen section.
[360409.082] (==) No screen section available. Using defaults.
[360409.082] (**) |-->Screen "Default Screen Section" (0)
[360409.082] (**) |   |-->Monitor "<default monitor>"
[360409.082] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[360409.082] (==) Automatically adding devices
[360409.082] (==) Automatically enabling devices
[360409.082] (==) Automatically adding GPU devices
[360409.083] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[360409.083]     Entry deleted from font path.
[360409.083] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[360409.083]     Entry deleted from font path.
[360409.083] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[360409.083]     Entry deleted from font path.
[360409.086] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[360409.086]     Entry deleted from font path.
[360409.086] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[360409.086]     Entry deleted from font path.
[360409.086] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[360409.086] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[360409.086] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[360409.086] (II) Loader magic: 0x7ff874dfad60
[360409.086] (II) Module ABI versions:
[360409.087]     X.Org ANSI C Emulation: 0.4
[360409.087]     X.Org Video Driver: 15.0
[360409.087]     X.Org XInput driver : 20.0
[360409.087]     X.Org Server Extension : 8.0
[360409.087] (II) xfree86: Adding drm device (/dev/dri/card0)
[360409.088] (--) PCI:*(0:0:2:0) 8086:0412:1849:0412 rev 6, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[360409.088] Initializing built-in extension Generic Event Extension
[360409.088] Initializing built-in extension SHAPE
[360409.088] Initializing built-in extension MIT-SHM
[360409.088] Initializing built-in extension XInputExtension
[360409.088] Initializing built-in extension XTEST
[360409.088] Initializing built-in extension BIG-REQUESTS
[360409.088] Initializing built-in extension SYNC
[360409.088] Initializing built-in extension XKEYBOARD
[360409.088] Initializing built-in extension XC-MISC
[360409.088] Initializing built-in extension SECURITY
[360409.088] Initializing built-in extension XINERAMA
[360409.088] Initializing built-in extension XFIXES
[360409.088] Initializing built-in extension RENDER
[360409.088] Initializing built-in extension RANDR
[360409.088] Initializing built-in extension COMPOSITE
[360409.088] Initializing built-in extension DAMAGE
[360409.088] Initializing built-in extension MIT-SCREEN-SAVER
[360409.088] Initializing built-in extension DOUBLE-BUFFER
[360409.088] Initializing built-in extension RECORD
[360409.088] Initializing built-in extension DPMS
[360409.088] Initializing built-in extension Present
[360409.088] Initializing built-in extension DRI3
[360409.088] Initializing built-in extension X-Resource
[360409.088] Initializing built-in extension XVideo
[360409.088] Initializing built-in extension XVideo-MotionCompensation
[360409.088] Initializing built-in extension SELinux
[360409.088] Initializing built-in extension XFree86-VidModeExtension
[360409.088] Initializing built-in extension XFree86-DGA
[360409.088] Initializing built-in extension XFree86-DRI
[360409.088] Initializing built-in extension DRI2
[360409.088] (II) LoadModule: "glx"
[360409.090] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[360409.092] (II) Module glx: vendor="X.Org Foundation"
[360409.092]     compiled for 1.15.1, module version = 1.0.0
[360409.092]     ABI class: X.Org Server Extension, version 8.0
[360409.092] (==) AIGLX enabled
[360409.092] Loading extension GLX
[360409.092] (==) Matched intel as autoconfigured driver 0
[360409.092] (==) Matched intel as autoconfigured driver 1
[360409.092] (==) Matched modesetting as autoconfigured driver 2
[360409.092] (==) Matched fbdev as autoconfigured driver 3
[360409.092] (==) Matched vesa as autoconfigured driver 4
[360409.092] (==) Assigned the driver to the xf86ConfigLayout
[360409.092] (II) LoadModule: "intel"
[360409.092] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[360409.094] (II) Module intel: vendor="X.Org Foundation"
[360409.094]     compiled for 1.15.0, module version = 2.99.910
[360409.094]     Module class: X.Org Video Driver
[360409.094]     ABI class: X.Org Video Driver, version 15.0
[360409.094] (II) LoadModule: "modesetting"
[360409.094] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[360409.095] (II) Module modesetting: vendor="X.Org Foundation"
[360409.095]     compiled for 1.15.0, module version = 0.8.1
[360409.095]     Module class: X.Org Video Driver
[360409.095]     ABI class: X.Org Video Driver, version 15.0
[360409.095] (II) LoadModule: "fbdev"
[360409.095] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[360409.096] (II) Module fbdev: vendor="X.Org Foundation"
[360409.096]     compiled for 1.15.0, module version = 0.4.4
[360409.096]     Module class: X.Org Video Driver
[360409.096]     ABI class: X.Org Video Driver, version 15.0
[360409.096] (II) LoadModule: "vesa"
[360409.096] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[360409.097] (II) Module vesa: vendor="X.Org Foundation"
[360409.097]     compiled for 1.15.0, module version = 2.3.3
[360409.097]     Module class: X.Org Video Driver
[360409.097]     ABI class: X.Org Video Driver, version 15.0
[360409.097] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[360409.099] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[360409.099] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[360409.099] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[360409.099] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[360409.099] (II) FBDEV: driver for framebuffer: fbdev
[360409.099] (II) VESA: driver for VESA chipsets: vesa
[360409.099] (++) using VT number 7


[360409.099] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[360409.099] (WW) Falling back to old probe method for modesetting
[360409.099] (WW) Falling back to old probe method for fbdev
[360409.099] (II) Loading sub module "fbdevhw"
[360409.099] (II) LoadModule: "fbdevhw"
[360409.099] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[360409.099] (II) Module fbdevhw: vendor="X.Org Foundation"
[360409.099]     compiled for 1.15.1, module version = 0.0.2
[360409.099]     ABI class: X.Org Video Driver, version 15.0
[360409.099] (WW) Falling back to old probe method for vesa
[360409.100] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[360409.100] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[360409.100] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[360409.100] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[360409.100] (==) intel(0): RGB weight 888
[360409.100] (==) intel(0): Default visual is TrueColor
[360409.100] (**) intel(0): Framebuffer tiled
[360409.100] (**) intel(0): Pixmaps tiled
[360409.100] (**) intel(0): "Tear free" disabled
[360409.100] (**) intel(0): Forcing per-crtc-pixmaps? no
[360409.100] (II) intel(0): Output VGA1 has no monitor section
[360409.100] (II) intel(0): Output HDMI1 has no monitor section
[360409.100] (II) intel(0): Output HDMI2 has no monitor section
[360409.100] (II) intel(0): Output VIRTUAL1 has no monitor section
[360409.100] (--) intel(0): Output HDMI2 using initial mode 1920x1080 on pipe 0
[360409.100] (==) intel(0): DPI set to (96, 96)
[360409.100] (II) Loading sub module "dri2"
[360409.100] (II) LoadModule: "dri2"
[360409.100] (II) Module "dri2" already built-in
[360409.100] (II) UnloadModule: "modesetting"
[360409.100] (II) Unloading modesetting
[360409.100] (II) UnloadModule: "fbdev"
[360409.100] (II) Unloading fbdev
[360409.100] (II) UnloadSubModule: "fbdevhw"
[360409.100] (II) Unloading fbdevhw
[360409.100] (II) UnloadModule: "vesa"
[360409.100] (II) Unloading vesa
[360409.100] (==) Depth 24 pixmap format is 32 bpp
[360409.101] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[360409.101] (==) intel(0): Backing store enabled
[360409.101] (==) intel(0): Silken mouse enabled
[360409.101] (II) intel(0): HW Cursor enabled
[360409.101] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[360409.101] (==) intel(0): DPMS enabled
[360409.101] (II) intel(0): [DRI2] Setup complete
[360409.101] (II) intel(0): [DRI2]   DRI driver: i965
[360409.101] (II) intel(0): [DRI2]   VDPAU driver: i965
[360409.101] (II) intel(0): direct rendering: DRI2 Enabled
[360409.101] (==) intel(0): hotplug detection: "enabled"
[360409.102] (--) RandR disabled
[360409.106] (II) SELinux: Disabled on system
[360409.126] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[360409.126] (II) AIGLX: enabled GLX_ARB_create_context
[360409.126] (II) AIGLX: enabled GLX_ARB_create_context_profile
[360409.126] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[360409.126] (II) AIGLX: enabled GLX_INTEL_swap_event
[360409.126] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[360409.126] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[360409.126] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[360409.126] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[360409.126] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[360409.126] (II) AIGLX: Loaded and initialized i965
[360409.126] (II) GLX: Initialized DRI2 GL provider for screen 0
[360409.128] (II) intel(0): switch to mode 1920x1080@50.0 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[360409.152] (II) intel(0): Setting screen physical size to 508 x 285
[360409.161] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[360409.163] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[360409.163] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[360409.163] (II) LoadModule: "evdev"
[360409.163] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[360409.164] (II) Module evdev: vendor="X.Org Foundation"
[360409.164]     compiled for 1.15.0, module version = 2.8.2
[360409.164]     Module class: X.Org XInput Driver
[360409.164]     ABI class: X.Org XInput driver, version 20.0
[360409.164] (II) Using input driver 'evdev' for 'Power Button'
[360409.164] (**) Power Button: always reports core events
[360409.164] (**) evdev: Power Button: Device: "/dev/input/event1"
[360409.164] (--) evdev: Power Button: Vendor 0 Product 0x1
[360409.164] (--) evdev: Power Button: Found keys
[360409.164] (II) evdev: Power Button: Configuring as keyboard
[360409.164] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[360409.164] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[360409.164] (**) Option "xkb_rules" "evdev"
[360409.164] (**) Option "xkb_model" "pc105"
[360409.164] (**) Option "xkb_layout" "fi"
[360409.165] (II) XKB: reuse xkmfile /var/lib/xkb/server-F30D752BAEAAD4B8C79BE2C421539A0D3700902C.xkm
[360409.167] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[360409.167] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[360409.167] (II) Using input driver 'evdev' for 'Video Bus'
[360409.167] (**) Video Bus: always reports core events
[360409.167] (**) evdev: Video Bus: Device: "/dev/input/event6"
[360409.167] (--) evdev: Video Bus: Vendor 0 Product 0x6
[360409.167] (--) evdev: Video Bus: Found keys
[360409.167] (II) evdev: Video Bus: Configuring as keyboard
[360409.167] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9/event6"
[360409.167] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[360409.167] (**) Option "xkb_rules" "evdev"
[360409.167] (**) Option "xkb_model" "pc105"
[360409.167] (**) Option "xkb_layout" "fi"
[360409.167] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[360409.167] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[360409.167] (II) Using input driver 'evdev' for 'Power Button'
[360409.167] (**) Power Button: always reports core events
[360409.167] (**) evdev: Power Button: Device: "/dev/input/event0"
[360409.167] (--) evdev: Power Button: Vendor 0 Product 0x1
[360409.167] (--) evdev: Power Button: Found keys
[360409.167] (II) evdev: Power Button: Configuring as keyboard
[360409.167] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[360409.167] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[360409.167] (**) Option "xkb_rules" "evdev"
[360409.167] (**) Option "xkb_model" "pc105"
[360409.167] (**) Option "xkb_layout" "fi"
[360409.168] (II) config/udev: Adding drm device (/dev/dri/card0)
[360409.168] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[360409.168] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event9)
[360409.168] (II) No input driver specified, ignoring this device.
[360409.168] (II) This device may have been added with another device file.
[360409.168] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event8)
[360409.168] (II) No input driver specified, ignoring this device.
[360409.168] (II) This device may have been added with another device file.
[360409.168] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event7)
[360409.168] (II) No input driver specified, ignoring this device.
[360409.168] (II) This device may have been added with another device file.
[360409.169] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) (/dev/input/event2)
[360409.169] (**) Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Applying InputClass "evdev keyboard catchall"
[360409.169] (II) Using input driver 'evdev' for 'Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)'
[360409.169] (**) Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): always reports core events
[360409.169] (**) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Device: "/dev/input/event2"
[360409.169] (--) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Vendor 0x471 Product 0x815
[360409.169] (WW) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Don't know how to use device
[360409.176] (EE) PreInit returned 8 for "Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)"
[360409.176] (II) UnloadModule: "evdev"
[360409.176] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event4)
[360409.176] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[360409.176] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[360409.176] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[360409.176] (**) evdev: Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event4"
[360409.176] (--) evdev: Logitech Logitech BT Mini-Receiver: Vendor 0x46d Product 0xc71e
[360409.176] (--) evdev: Logitech Logitech BT Mini-Receiver: Found keys
[360409.176] (II) evdev: Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[360409.176] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14.2/3-14.2:1.0/input/input7/event4"
[360409.176] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD, id 9)
[360409.176] (**) Option "xkb_rules" "evdev"
[360409.176] (**) Option "xkb_model" "pc105"
[360409.176] (**) Option "xkb_layout" "fi"
[360409.176] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event5)
[360409.176] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
[360409.176] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[360409.176] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[360409.176] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[360409.176] (**) evdev: Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event5"
[360409.176] (--) evdev: Logitech Logitech BT Mini-Receiver: Vendor 0x46d Product 0xc71f
[360409.176] (--) evdev: Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
[360409.176] (--) evdev: Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
[360409.176] (--) evdev: Logitech Logitech BT Mini-Receiver: Found relative axes
[360409.176] (--) evdev: Logitech Logitech BT Mini-Receiver: Found x and y relative axes
[360409.176] (--) evdev: Logitech Logitech BT Mini-Receiver: Found absolute axes
[360409.176] (II) evdev: Logitech Logitech BT Mini-Receiver: Forcing absolute x/y axes to exist.
[360409.176] (--) evdev: Logitech Logitech BT Mini-Receiver: Found keys
[360409.176] (II) evdev: Logitech Logitech BT Mini-Receiver: Configuring as mouse
[360409.176] (II) evdev: Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[360409.176] (II) evdev: Logitech Logitech BT Mini-Receiver: Adding scrollwheel support
[360409.176] (**) evdev: Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
[360409.176] (**) evdev: Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[360409.176] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14.3/3-14.3:1.0/input/input8/event5"
[360409.176] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD, id 10)
[360409.176] (**) Option "xkb_rules" "evdev"
[360409.177] (**) Option "xkb_model" "pc105"
[360409.177] (**) Option "xkb_layout" "fi"
[360409.177] (II) evdev: Logitech Logitech BT Mini-Receiver: initialized for relative axes.
[360409.177] (WW) evdev: Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
[360409.177] (**) Logitech Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
[360409.177] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration profile 0
[360409.177] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration factor: 2.000
[360409.177] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration threshold: 4
[360409.177] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse1)
[360409.177] (II) No input driver specified, ignoring this device.
[360409.177] (II) This device may have been added with another device file.
[360409.177] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event16)
[360409.177] (II) No input driver specified, ignoring this device.
[360409.177] (II) This device may have been added with another device file.
[360409.178] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event15)
[360409.178] (II) No input driver specified, ignoring this device.
[360409.178] (II) This device may have been added with another device file.
[360409.178] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event14)
[360409.178] (II) No input driver specified, ignoring this device.
[360409.178] (II) This device may have been added with another device file.
[360409.178] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event13)
[360409.178] (II) No input driver specified, ignoring this device.
[360409.178] (II) This device may have been added with another device file.
[360409.178] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event12)
[360409.178] (II) No input driver specified, ignoring this device.
[360409.178] (II) This device may have been added with another device file.
[360409.178] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event11)
[360409.178] (II) No input driver specified, ignoring this device.
[360409.178] (II) This device may have been added with another device file.
[360409.179] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event10)
[360409.179] (II) No input driver specified, ignoring this device.
[360409.179] (II) This device may have been added with another device file.
[360409.181] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (mceusb) (/dev/input/event3)
[360409.181] (**) MCE IR Keyboard/Mouse (mceusb): Applying InputClass "evdev pointer catchall"
[360409.181] (**) MCE IR Keyboard/Mouse (mceusb): Applying InputClass "evdev keyboard catchall"
[360409.181] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (mceusb)'
[360409.181] (**) MCE IR Keyboard/Mouse (mceusb): always reports core events
[360409.181] (**) evdev: MCE IR Keyboard/Mouse (mceusb): Device: "/dev/input/event3"
[360409.181] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Vendor 0 Product 0
[360409.181] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found 3 mouse buttons
[360409.181] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found relative axes
[360409.181] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found x and y relative axes
[360409.181] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found keys
[360409.181] (II) evdev: MCE IR Keyboard/Mouse (mceusb): Configuring as mouse
[360409.181] (II) evdev: MCE IR Keyboard/Mouse (mceusb): Configuring as keyboard
[360409.181] (**) evdev: MCE IR Keyboard/Mouse (mceusb): YAxisMapping: buttons 4 and 5
[360409.181] (**) evdev: MCE IR Keyboard/Mouse (mceusb): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[360409.181] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event3"
[360409.181] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (mceusb)" (type: KEYBOARD, id 11)
[360409.181] (**) Option "xkb_rules" "evdev"
[360409.181] (**) Option "xkb_model" "pc105"
[360409.181] (**) Option "xkb_layout" "fi"
[360409.181] (II) evdev: MCE IR Keyboard/Mouse (mceusb): initialized for relative axes.
[360409.181] (**) MCE IR Keyboard/Mouse (mceusb): (accel) keeping acceleration scheme 1
[360409.181] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration profile 0
[360409.181] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration factor: 2.000
[360409.181] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration threshold: 4
[360409.181] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (mceusb) (/dev/input/mouse0)
[360409.181] (II) No input driver specified, ignoring this device.
[360409.181] (II) This device may have been added with another device file.
[360409.591] (II) intel(0): EDID vendor "MEI", prod id 41126
[360409.591] (II) intel(0): Using EDID range info for horizontal sync
[360409.591] (II) intel(0): Using EDID range info for vertical refresh
[360409.591] (II) intel(0): Printing DDC gathered Modelines:
[360409.591] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz eP)
[360409.591] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[360409.591] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[360409.591] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[360409.591] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[360409.591] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[360409.591] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[360409.591] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[360409.591] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[360409.591] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[360409.591] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[360409.591] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[360409.591] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[360409.591] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[360409.591] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[360409.591] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[360409.591] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[360409.591] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[360409.591] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[360409.591] (II) intel(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[360409.591] (II) intel(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[360409.591] (II) intel(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[360409.591] (II) intel(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)
[360409.819] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[396605.412] (II) intel(0): EDID vendor "MEI", prod id 41126
[396605.412] (II) intel(0): Using hsync ranges from config file
[396605.412] (II) intel(0): Using vrefresh ranges from config file
[396605.412] (II) intel(0): Printing DDC gathered Modelines:
[396605.413] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz eP)
[396605.413] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[396605.413] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[396605.413] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[396605.413] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[396605.413] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[396605.413] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[396605.413] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[396605.413] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[396605.413] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[396605.413] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[396605.413] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[396605.413] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[396605.413] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[396605.413] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[396605.413] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[396605.413] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[396605.413] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[396605.413] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[396605.413] (II) intel(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[396605.413] (II) intel(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[396605.413] (II) intel(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[396605.413] (II) intel(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)

```

---

### Post by Ottoko on 2014-07-28
I think I have exactly the same remote and exactly the same issue
> otto@server:~$ sudo ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event8) with:
    Driver mceusb, table rc-rc6-mce
    Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other 
    Enabled protocols: LIRC 
    Name: Media Center Ed. eHome Infrared 
    bus: 3, vendor/product: 0471:0815, version: 0x0000
    Repeat delay = 500 ms, repeat period = 125 ms



I've tried all the things mentoined in this thread and it just doesn't work. I'm posting this just because it's happening me too with te same device so I would rule out hardware issue. My remote used to work on Linux Mint 13 but it stopped working after switching to Ubuntu 13.10 and 14.04.

---

### Post by kirk2 on 2014-07-28
I had the same problem with my NUC and MCE remote.  I had to restart the IR service on the NUC after boot up.  Maybe you have to do the same for yours.  Here's how you do it on the NUC:

[COLOR=#000000][FONT=Verdana]**# modprobe the IR controller**[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**modprobe -r nuvoton-cir**[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**echo "auto" > "/sys/bus/acpi/devices/NTN0530:00/physical_node/resources"**[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**modprobe nuvoton-cir**[/FONT][/COLOR]

---

### Post by zafayar on 2014-08-02
Did anyone actually managed to get LIRC working?

I have tried everything on this thread and few other threads, but still my eHOME receiver and MCE remote refuse to work.

---

### Post by jmail5242 on 2014-08-11
Any new ideas as I am also having this problem?

With a fresh install of Mythbuntu 14.04, my MSI MCEUSB (RC6) remote doesn't work.

Thanks.
-Brian

---

### Post by JamesBe on 2014-08-12
I'm also looking for help here.

Just setup a new pc, MCE remote not working, never had issues with ubuntu 12.  14.04 I've tried everything listed here and much more.

---

### Post by JamesBe on 2014-08-12
I hooked my remote back up to my computer with ubuntu 12.04 here is the ir-keytable for reference, so not the issue as listed above it seems.

Found /sys/class/rc/rc0/ (/dev/input/event5) with:
	Driver mceusb, table rc-rc6-mce
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
	Enabled protocols: LIRC 
	Repeat delay = 500 ms, repeat period = 125 ms

I'm in the process of grabbing as much info from the Ubuntu 12 machine as I can then compare it to 14.  I may just install 12 again...

---

### Post by JamesBe on 2014-08-13
I installed LIRC on 12.04 on my new machine and it does not work either.  So it's not an ubuntu 12.04 vs 14.04 issue.

What it looks like is it may be a hardware issue where ubuntu is not properly recognizing the 1.1 usb device on the 2.0 controller on newer machines / chipsets.

I'm going to try windows to eliminate total hardware failure.

---

### Post by JamesBe on 2014-08-13
It works with windows 7 so this seems to be a USB chipset driver issue on the new motherboards.

I may do some more debugging with usbmon but if I like windows as my frontend I may just call it a day with that.  Too bad because mythbuntu is usually very stable.  I was going to try fedora but I can't even that that to boot....

---

### Post by jmail5242 on 2014-08-15
I managed to get my MSI MCE remote working.  (FYI, it actually shows up as a Philips eHome Infrared Receiver with 'lsusb'.)  I had to disable the USB port's "xHCI" feature in the BIOS.  The remote immediately started working after that.  I don't understand why I had to change that setting all of a sudden, but at least it's working.

Thanks.
-Brian

---

### Post by JamesBe on 2014-08-15
That makes sense.  As the device has issues with USB 3.0 and disabling xHCI means you no longer have USB 3.0 only 2.0.  Unfortunately it did not work for me :(

It seems linux has an issue with the USB 3.0 drivers since it works in windows.

Doing some USB debugging with usbmon I can clearly see the device is working pulling all the keys from the remote etc, but certainly not sending them to the proper kernel driver I guess.

---

### Post by JamesBe on 2014-08-16
I got it working!

to the OP if you haven't got this working yet.  Try this:
sudo apt-get install inputlirc

point inputlirc to the proper event number for your device.

Reboot.  

Stop and start lircd on every reboot (you can do this in an rc.local script)

---

### Post by jerry79 on 2014-12-13
I recently upgraded my hardware and in the process the remote stopped working.  I have an ASUS Z97M motherboard which states: 

> Due to the design of the Intel ® 9 series chipset, all USB devices connected to the
USB 2.0 and USB 3.0 ports are controlled by the xHCI controller. Some legacy USB
devices must update their firmware for better compatibility.

I happened to have an extra USB 2.0 card, plugged it in and after inputlirc mods and lircd restart everything started working.

Thanks for the tip for using inputlirc and stop/start lircd.

---

