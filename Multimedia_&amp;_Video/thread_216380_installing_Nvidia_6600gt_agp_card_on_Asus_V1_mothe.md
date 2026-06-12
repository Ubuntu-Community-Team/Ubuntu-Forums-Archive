---
title: "installing Nvidia 6600gt agp card on Asus V1 motherboard"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by sophtpaw on 2006-07-15
Please help

I am about to cry...


just bought Nvidia 6600gt agp card and trying to install it on my Asus Vintage motherboard system. 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Followed this link. Installed nvidia glx did sudo enable but still not working

Problem is  that the motherboard had integrated graphics card. I hoped the nvidia would just get recognised and ovewrite the integrated graphics card.

But when i reboot, i get a blank screen. So, i have to take the card out to get a screen again.

If the card has to be in while the drivers are installed then i have a catch 22 situation. 

I have tried installing the drivers first and then adding the card but it hasn't worked

I was told i may need to disable the onboard graphics card on the motherboard through the BIOS, but i odn't see where that is

Any ideas?

help much appreciated

thank you in advance

--
sophtpaw

---

### Post by tseliot on 2006-07-15
Plug in you card, boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

And let's see what happens.

If that doesn't work, please post:

1) the output of:
lspci

2) your /etc/X11/xorg.conf

---

### Post by Rashid584 on 2006-07-15
Awesome, I was just about to make a new thread asking a very similar question.

I don't wanna hijack your thread, but I'm interested in the answer too. I just got given an FX5500 PCI card as a gift (from my work experience employer) and I dunno how to install it. I'm waiting to see if that solution worked for you, cos I have a real problem with starting up to a scary screen :p

-Rashid

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> Plug in you card, boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

And let's see what happens.

If that doesn't work, please post:

1) the output of:
lspci

2) your /etc/X11/xorg.conf



when i put the card in teh agp slot, upon bootup my monitor does not switch on. The light stays orange whereas it usually kicks in, and turns yellow/green as the script comes up.

So, how would i boot into recovery mode?

i shall give you the /etc/X11 out put shortyly

---

### Post by tseliot on 2006-07-15
> **sophtpaw said:**
> when i put the card in teh agp slot, upon bootup my monitor does not switch on. The light stays orange whereas it usually kicks in, and turns yellow/green as the script comes up.

So, how would i boot into recovery mode?

i shall give you the /etc/X11 out put shortyly

Which card has the monitor's cable plugged in?

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> 

And let's see what happens.

If that doesn't work, please post:

1) the output of:
lspci

2) your /etc/X11/xorg.conf

1) lspci - [http://paste.ubuntu-nl.org/18097](http://paste.ubuntu-nl.org/18097)

2) /etc/X11/xorg.conf - [http://paste.ubuntu-nl.org/18098](http://paste.ubuntu-nl.org/18098)

thank you

---

### Post by Rashid584 on 2006-07-15
Wait...to install a new card, should you remove the drivers for the old one first?? (i have an integrated intel chip)

Or should I just open my pc up, insert the card, boot up and do the "dpkg-reconfigure xserver-xorg" command?

-Rashid

---

### Post by tseliot on 2006-07-15
> **sophtpaw said:**
> 1) lspci - [http://paste.ubuntu-nl.org/18097](http://paste.ubuntu-nl.org/18097)

2) /etc/X11/xorg.conf - [http://paste.ubuntu-nl.org/18098](http://paste.ubuntu-nl.org/18098)

thank you

```
sudo nano -w /etc/X11/xorg.conf
```

and comment out the busid and the option:

```
Section "Device"
        Identifier        "Generic Video Card"
        Driver                "vesa"
        [COLOR="Red"]#[/COLOR]BusID                "PCI:1:0:0"
        [COLOR="Red"]#[/COLOR]Option                "UseFBDev"                "true"
EndSection
```

CTRL+X to exit (save the file).

Then shutdown Ubuntu.

Plug in your Nvidia card and plug your monitor cable in it.

Turn on your computer.

The video card should be detected (it won't look for that specific busid) and display images on your moitor

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> Which card has the monitor's cable plugged in?

The Asus V1 motherboard had onboard integrated graphics card. I don't know how to disable it.

So, there was no card to remove. I just slotted the nvidia card into the agp slot and hoped it would override, you know?...

---

### Post by tseliot on 2006-07-15
> **sophtpaw said:**
> I just slotted the nvidia card into the agp slot and hoped it would override, you know?...
It will. Please, try what I have suggested above.

---

### Post by Rashid584 on 2006-07-15
tseliot, I'm gonna try what you've said (turn my computer off now, plug in the card, plug my monitor into it, boot up, go into recovery mode, and try "sudo dpkg-reconfigure xserver-xorg" )

Do I need to do the xorg changes too?? Is there anything else other than what I've said above that I need to do?

Thanks man :D

-Rashid

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> It will. Please, try what I have suggested above.

I SEE!

i never tried putting the monitor cable into the graphics card. I had just left it where it was (in the network card aguess?) Doh...

Ok. i go and try that now

thank you

--
sophtpaw

---

### Post by tseliot on 2006-07-15
> **Rashid584 said:**
> tseliot, I'm gonna try what you've said (turn my computer off now, plug in the card, plug my monitor into it, boot up, go into recovery mode, and try "sudo dpkg-reconfigure xserver-xorg" )

Do I need to do the xorg changes too?? Is there anything else other than what I've said above that I need to do?

Thanks man :D

-Rashid

Please, post your xorg.conf first

---

### Post by Rashid584 on 2006-07-15
OK.

BTW, just wanna congratulate you on being so patient and polite ;) :D

```
rashid@rashid-desktop:~$ cat /etc/X11/xorg.conf
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

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "NEC LCD1525X"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "NEC LCD1525X"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

-Rashid

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> It will. Please, try what I have suggested above.

Bellissimo!

100% improvement. I now have graphics on my monitor. Maybe the only difference was attaching the monitor vga cable to the graphics card, which i didn't even realise i had to do. So, i don't know whether editing the xserver-xorg files made a difference. 

Well, as i said at the top of the thread; i followed the nvidia how to. installed nvidia glx and so on. It did say that on reboot i would get a screensplash saying Nvidia proving that it was detected. 
I did NOT get that, so i don't know whether the drivers have been installed or whether the card has in fact been recognised

what are your thoughts, comments, suggestions?


thank you

--
sophtpaw

---

### Post by Rashid584 on 2006-07-15
Wait...you have to do a sudo apt-get install nvidia-glx first??

I was just gonna plug it in and do the "dpkg-reconfigure xserver-xorg" :S

But I wanna play wolfenstein too...so should I do "sudo apt-get install nvidia-glx" after that?

Thanks for all your help tseliot!

-Rashid

---

### Post by tseliot on 2006-07-15
> **Rashid584 said:**
> OK.

BTW, just wanna congratulate you on being so patient and polite ;) :D
Thanks.

See the corrections in red, apply them and shutdown Ubuntu. Plug the new card in, plug your monitor cable in the Nvidia card and turn on your computer

```
Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "[COLOR="Red"]vesa[/COLOR]"
        [COLOR="Red"]#[/COLOR]BusID           "PCI:0:2:0"
EndSection

```

---

### Post by tseliot on 2006-07-15
> **sophtpaw said:**
> Bellissimo!

100% improvement. I now have graphics on my monitor. Maybe the only difference was attaching the monitor vga cable to the graphics card, which i didn't even realise i had to do. So, i don't know whether editing the xserver-xorg files made a difference. 

Well, as i said at the top of the thread; i followed the nvidia how to. installed nvidia glx and so on. It did say that on reboot i would get a screensplash saying Nvidia proving that it was detected. 
I did NOT get that, so i don't know whether the drivers have been installed or whether the card has in fact been recognised

what are your thoughts, comments, suggestions?


thank you

--
sophtpaw

1) Post the output of:

```
dmesg | grep NVIDIA
```


2) Type:
```
glxgears
```

---

### Post by tseliot on 2006-07-15
I'm going to have dinner now (I'm not abandoning you ;)  )

see you later

---

### Post by Rashid584 on 2006-07-15
Cheers man :D And you're welcome :)

I'm gonna try this, and get back. Hope to see you back here later.

Enjoy your dinner :D

-Rashid

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> 1) Post the output of:

```
dmesg | grep NVIDIA
```


2) Type:
```
glxgears
```

i followed the nivida how to > [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

and when i got to: sudo nvidia-glx-config enable i got:

> livingdaylight@baraka:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


but that was just a 'by the way' and before i deal with that, let me give you the output you request: 1)
> livingdaylight@baraka:~$ dmesg | grep NVIDIA
[17179589.088000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.092000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006


2)
> livingdaylight@baraka:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Thanks for sticking with us!
bon appetito!

--
sophtpaw

ps. the /etc/X11/xserver-xorg file again - [http://paste.ubuntu-nl.org/18100](http://paste.ubuntu-nl.org/18100)

---

### Post by sophtpaw on 2006-07-15
i don't know what i've done.

While waiting i was advised to go and sudo dpkg -reconfigure xserver-xorg and put nvidia as the driver

Upon rebooting i got no graphics again like before. 

So i had to take the monitor off the graphics card and put it back on the network card and use the onboard graphics aguess.

However, error pages came up and i appeared to haev lost X altogether

Anyway, here i am back in X having reconfigured the xserver-xorg files once more

But im back to square A

I know, i should have just waited

which is what i'll do now

sorry

--
sophtpaw

---

### Post by tseliot on 2006-07-15
> **Rashid584 said:**
> Wait...you have to do a sudo apt-get install nvidia-glx first??

I was just gonna plug it in and do the "dpkg-reconfigure xserver-xorg" :S

But I wanna play wolfenstein too...so should I do "sudo apt-get install nvidia-glx" after that?

Thanks for all your help tseliot!

-Rashid

Let's do 1 thing per time.

Please, follow what I suggested before.

---

### Post by Rashid584 on 2006-07-15
OK, I applied your changes to the xorg.conf so the device section looks like this

```
Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "vesa"
        #BusID          "PCI:0:2:0"

```

I turned off. Opened it up, inserted my FX5500 PCI card, it clicked into place but I couldn't find a screw in the box or anywhere so I just left it like that.

I definitely plugged the blue VGA thing (or whatever its called) into the correct, new card. When I booted up, I got the orange monitor LED thing. I restarted a few times but still, nothing comes up on the screen except a message from my monitor saying no signal. The only way to get back is to plug it back into my integrated graphics card.

Any ideas? Help, please :)

-Rashid

P.S. Is it safe for me to not use a screw? Will it rattle around or anything when in use...I dunno, but I can't find a little screw anywhere :S

---

### Post by tseliot on 2006-07-15
> **sophtpaw said:**
> i don't know what i've done.

While waiting i was advised to go and sudo dpkg -reconfigure xserver-xorg and put nvidia as the driver

Upon rebooting i got no graphics again like before. 

So i had to take the monitor off the graphics card and put it back on the network card and use the onboard graphics aguess.

However, error pages came up and i appeared to haev lost X altogether

Anyway, here i am back in X having reconfigured the xserver-xorg files once more

But im back to square A

I know, i should have just waited

which is what i'll do now

sorry

--
sophtpaw
Don't use the guide in the official wiki. You should use mine (or my script) instead (once we solve your new problem):
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

Plug in your Nvidia card and connect your monitor to it.

Then turn on your computer and boot in Recovery Mode.

Then edit your xorg.conf:
```
nano /etc/X11/xorg.conf
```

comment out the busid and the option (if it's still there) and set the driver to "vesa"

CTRL+X

and reboot:
```
reboot
```

---

### Post by Rashid584 on 2006-07-15
I'm trying what you just said to sophtpaw, but I can't see ANYTHING let alone boot into recovery mode to type anything :(

-Rashid

---

### Post by tseliot on 2006-07-15
> **Rashid584 said:**
> OK, I applied your changes to the xorg.conf so the device section looks like this

```
Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "vesa"
        #BusID          "PCI:0:2:0"

```

I turned off. Opened it up, inserted my FX5500 PCI card, it clicked into place but I couldn't find a screw in the box or anywhere so I just left it like that.

I definitely plugged the blue VGA thing (or whatever its called) into the correct, new card. When I booted up, I got the orange monitor LED thing. I restarted a few times but still, nothing comes up on the screen except a message from my monitor saying no signal. The only way to get back is to plug it back into my integrated graphics card.
Plug in the Nvidia card and enter the BIOS so as to see if you can disable your integrated card.

> **Rashid584 said:**
> P.S. Is it safe for me to not use a screw? Will it rattle around or anything when in use...I dunno, but I can't find a little screw anywhere :S
It is fine for now but I suggest you to find some screws to fix it

---

### Post by Rashid584 on 2006-07-15
[quote=tseliot]Plug in the Nvidia card and enter the BIOS so as to see if you can disable your integrated card.[/quote]

Well, the nvidia card is plugged in already, but the monitor is just plugged into the integrated card. 

I'm afraid if I go into the BIOS now, and disable my integrated card, and reboot, I may end up without an integrated chip, and the new card won't work either. Then I'll be COMPLETELY stuck and without access to these forums or the internet at all. (i only have this computer with the net)

And I'll try to find a screw, but have no idea where to get them. Thanks for the advice though.

-Rashid

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> Don't use the guide in the official wiki. You should use mine (or my script) instead (once we solve your new problem):
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

Plug in your Nvidia card and connect your monitor to it.

Then turn on your computer and boot in Recovery Mode.

Then edit your xorg.conf:
```
nano /etc/X11/xorg.conf
```

comment out the busid and the option (if it's still there) and set the driver to "vesa"

CTRL+X

and reboot:
```
reboot
```

i had already thought it might be that the setting went back, so i did that, well, my way; sudo nautilus and uncommented as before and saved but still the same problem. 

Get this error come up on reboot. 

don't know what to do....

---

### Post by tseliot on 2006-07-15
> **Rashid584 said:**
> Well, the nvidia card is plugged in already, but the monitor is just plugged into the integrated card. 

I'm afraid if I go into the BIOS now, and disable my integrated card, and reboot, I may end up without an integrated chip, and the new card won't work either. Then I'll be COMPLETELY stuck and without access to these forums or the internet at all. (i only have this computer with the net)

That won't happen. The BIOS will allow you to disable the onboard card only if another one is plugged in.

Connect your monitor to your Nvidia card and try what I suggested

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> Don't use the guide in the official wiki. You should use mine (or my script) instead (once we solve your new problem):
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

Plug in your Nvidia card and connect your monitor to it.

Then turn on your computer and boot in Recovery Mode.

Then edit your xorg.conf:
```
nano /etc/X11/xorg.conf
```

comment out the busid and the option (if it's still there) and set the driver to "vesa"

CTRL+X

and reboot:
```
reboot
```

i need to start from scratch - right from the beginning

this is the current output: [http://paste.ubuntu-nl.org/18106](http://paste.ubuntu-nl.org/18106) I don't see option anymore.

Also, i don't know what recovery mode is?

---

### Post by Rashid584 on 2006-07-15
Yeah, but if I connect my monitor to the nvidia card, when I boot up i can't see ANYTHING. I can't go into the BIOS at all. I only get a no signal thing from my monitor. The monitor LED is orange (its supposed to be green...usually by then it goes green)

I'm gonna try anyway, with the monitor plugged into my integrated chip.

-Rashid

---

### Post by tseliot on 2006-07-15
> **sophtpaw said:**
> i had already thought it might be that the setting went back, so i did that, well, my way; sudo nautilus and uncommented as before and saved but still the same problem. 

Get this error come up on reboot. 

don't know what to do....

1) I need to see your xorg.conf again then.

2) And do this other thing ONLY IF you DON't connect to the internet via wireless:
```
sudo apt-get remove --purge nvidia-glx nvidia-kernel-common
```

OTHERWISE just type:
```
sudo apt-get remove --purge nvidia-glx
```

---

### Post by tseliot on 2006-07-15
> **sophtpaw said:**
> i need to start from scratch - right from the beginning

this is the current output: [http://paste.ubuntu-nl.org/18106](http://paste.ubuntu-nl.org/18106) I don't see option anymore.

Also, i don't know what recovery mode is?

I'm sure you don't need to reinstall anything.

Put a # before "BusID                "PCI:1:0:0"" and follow the method I have suggested in my previous post

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> 1) I need to see your xorg.conf again then.

2) And do this other thing ONLY IF you DON't connect to the internet via wireless:
```
sudo apt-get remove --purge nvidia-glx nvidia-kernel-common
```

OTHERWISE just type:
```
sudo apt-get remove --purge nvidia-glx
```

i anticipated that 'guess, and have already given you the xorg.conf again

I do use wireless, so i have sudo apt-get remove --purge nvidia-glx

---

### Post by Rashid584 on 2006-07-15
OK, I rebooted while plugged into my integrated chip and couldn't find anywhere to disable my on board graphics.

Just for good measure, I plugged into the new card and tried to boot, but still, nothing :(

Any ideas, at all? Should I try "dpkg-reconfigure xserver-xorg" while logged in now? (the monitor is plugged into my integrated chip)

-Rashid

---

### Post by tseliot on 2006-07-15
> **sophtpaw said:**
> i anticipated that 'guess, and have already given you the xorg.conf again

I do use wireless, so i have sudo apt-get remove --purge nvidia-glx

As far as I've understood your motherboard disables the onboard card whenever you plug in a new graphic card. This means that you can't boot with your Nvidia card plugged in and the monitor connected to the onboard card (which would be disabled).

Plug in the Nvidia card and connect the monitor to it.

I need to know what happens if you boot in Recovery Mode (please follow this exact steps), type this:
```
dpkg-reconfigure xserver-xorg
```

Select the "vesa" driver.

Then:
```
nano /etc/X11/xorg.conf
```

and comment out (i.e. put a "#" before ) the busid.

CTRL+X to exit

then type:
```
reboot
```

---

### Post by tseliot on 2006-07-15
> **Rashid584 said:**
> OK, I rebooted while plugged into my integrated chip and couldn't find anywhere to disable my on board graphics.

Just for good measure, I plugged into the new card and tried to boot, but still, nothing :(

Any ideas, at all? Should I try "dpkg-reconfigure xserver-xorg" while logged in now? (the monitor is plugged into my integrated chip)

-Rashid

If plugging in the Nvidia card (with the monitor connected to it) doesn't allow you to see the BIOS then the problem is not Ubuntu.

The BIOS has nothing to do with Ubuntu.

1) Check that your Nvidia card is not damaged (try it on another PC if you can

2) Try your card in another PCI port (in case the port you're using is damaged)

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> As far as I've understood your motherboard disables the onboard card whenever you plug in a new graphic card. This means that you can't boot with your Nvidia card plugged in and the monitor connected to the onboard card (which would be disabled).

Plug in the Nvidia card and connect the monitor to it.

I need to know what happens if you boot in Recovery Mode (please follow this exact steps), type this:
```
dpkg-reconfigure xserver-xorg
```

Select the "vesa" driver.

Then:
```
nano /etc/X11/xorg.conf
```

and comment out (i.e. put a "#" before ) the busid.

CTRL+X to exit

then type:
```
reboot
```


can you tell me how to boot in recovery mode?

---

### Post by Rashid584 on 2006-07-15
> **tseliot said:**
> If plugging in the Nvidia card (with the monitor connected to it) doesn't allow you to see the BIOS then the problem is not Ubuntu.

The BIOS has nothing to do with Ubuntu.

1) Check that your Nvidia card is not damaged (try it on another PC if you can

2) Try your card in another PCI port (in case the port you're using is damaged)

Yeah, I guess it isn't a problem with Ubuntu. I'll open it up and check if the card is damaged. I'll probably feel like crying if it is :p :( My sister has a windows computer (but no internet) so I may try it on that (its under a LOT of rubbish atm so itll be effort :p)

Thanks for all your help tseliot. I'll get back when I can.

-Rashid

---

### Post by tseliot on 2006-07-15
> **sophtpaw said:**
> can you tell me how to boot in recovery mode?

You can boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer.

NOTE: the GRUB menu contains a few lines with your kernel versions

---

### Post by tseliot on 2006-07-15
> **Rashid584 said:**
> Yeah, I guess it isn't a problem with Ubuntu. I'll open it up and check if the card is damaged. I'll probably feel like crying if it is :p :( My sister has a windows computer (but no internet) so I may try it on that (its under a LOT of rubbish atm so itll be effort :p)

Thanks for all your help tseliot. I'll get back when I can.

-Rashid

Good luck with your card. And BTW there are worse things to cry for ;)

---

### Post by tseliot on 2006-07-15
I have to go to bed now (I'm extremely tired).

Good night!

---

### Post by sophtpaw on 2006-07-15
> **tseliot said:**
> I have to go to bed now (I'm extremely tired).

Good night!

Alrite, good nite

Well, i seem to be where i was. 

I have the graphics card slotted in, and the monitor is attached to the graphics card. I rebooted without the error pages coming up and bootup went smooth into login.

I don't know about recovery mode and just logged in as per usual.

Maybe tomorrow you'll tell me exactly where to go from here. I can follow your 'how to' instead of the ubuntu one, maybe?

thanks again

--
sophtpaw

---

### Post by jjf on 2006-07-15
I've had similar experience with AGP cards and overriding onboard graphics, so I'll chime in what I know.  

First, there is the possibility that your graphics card is not compatible with your motherboard.  The GeForce 6600GT is an AGP 4x/8x card.  If your motherboard only supports AGP 2x, you will not get it to run.  I think this is only a small possibility, but it still exists.  If you know the model number of your motherboard, post it here.

From what you describe, it sounds like your BIOS is still trying to use onboard graphics even though a graphics card is present.  I seem to remember working on a computer that did not automatically switch the onboard graphics off when a card was present.  

Here is what I would try:

[LIST]
[*]Turn the computer off.
[*]Plug the graphics card into its slot.
[*]Hook the monitor's VGA cable into the onboard graphics connector (that is, ***not*** your graphics card connector -- the other one).
[*]Turn the computer on.
[*]If the monitor displays an image, then hit whatever key is necessary to take you into your BIOS setup (often F1, F2, or delete -- hopefully the screen tells you "Press <this> to enter setup.")
[*]In order to proceed, you **must** find the option to "Disable Onboard Graphics."  It might also read "Enable AGP."  If you can't find it, locate your BIOS manufacturer and revision number (Award and Pheonix are two common brands) somewhere on the screen.  Post it here to get help, but also google it to see if you can find instructions to switch from onboard graphics to AGP graphics.
[*]Once you've switched from onboard to AGP graphics, save changes and exit.
[*]Turn the computer off.
[*]Plug the monitor's VGA cable into your graphics card connector.
[*]Turn the computer on.  Hopefully you now have a picture on the screen with the monitor plugged into the graphics card.
[/LIST]

That's only step 1.  Once you have display from your graphics card, you need to configure Ubuntu to use the nvidia driver.  I've found this to be the shortest method:

***NOTE: THESE INSTRUCTIONS ARE ONLY FOR A RECENT NVIDIA CARD LIKE THE 6600 or 6600 GT***

[LIST]
[*]As the computer is booting, be on the lookout for the GRUB menu, or the message "Press <ESC> to enter the GRUB menu."  You have to be quick, because the "Press <ESC>" only gives you 3 seconds.
[*]Once you see the GRUB boot menu, choose the topmost entry that ends in "(Recovery Mode)".  
[*]Linux will boot you into a command prompt.
[*]If you haven't already, install the nvidia drivers:
```
apt-get install nvidia-glx
```
[*]Once those are installed, open the configuration file that tell Ubuntu which of various drivers to use:
```
nano /etc/X11/xorg.conf
```
[*]Find the section that looks *something* like this (the particulars may be a little different):
```
Section "Device"
     Identifier   "Generic Graphics"
     Driver       "vesa"
     PCI:ID       0:0:0:1
EndSection
```
[*]You can leave that section as it is.  Underneath it, add these lines:
```
Section "Device"
     Identifier    "GeForce"
     Driver        "nvidia"
EndSection
```
[*]What you just did was leave the old driver listed in there as a device (in case you ever need to come back to it for some reason), but told Ubuntu that you have a *new* device that you're calling "GeForce" and that uses the "nvidia" driver.  But now you need to tell Ubunut to use this new device ("GeForce") instead of the old one.
[*]A few lines down find this section:
```
Section "Screen"
     Identifier    "Default Screen"
     Device        "Generic Graphics"
```
[*]Change the Device from "Generic Graphics" to "GeForce".  Be careful -- capitalization matters.
[*]Press CTRL and O (that's the letter "O", not the number 0) to "Write Out" (save changes).
[*]Press CTRL and X to exit.
[*]Reboot:
```
reboot
```
[/LIST]

That should fix you up.  At least, I know it's worked for me on the dozen or so computers I've had to do this to.  But if you'd feel better waiting for TS Eliot's approval or revision of these steps, that can't hurt (since he seems to know a lot about this).  Good luck.

---

### Post by Rashid584 on 2006-07-15
[quote=tseliot]Good luck with your card. And BTW there are worse things to cry for ;)[/quote]

Thanks. And lol, thats very, VERY true. There are brothers and sisters in Lebananon DYING :( And I'm sitting here frustrated because my new graphics card won't work. *sigh*

OK, I've plugged in an old S3 Virge card I also picked up from work, and the same thing happened. I tried it in another PCI slot, and it still didn't do anything. So unless both cards, and both PCI slots are damaged (which I HOPE isn't true :p) its gotta be something else.

jjf, I'll take a look at the BIOS again in a minute, I gotta have dinner now :D Thanks for your suggestions. 

-Rashid

---

### Post by jjf on 2006-07-15
Some BIOS's I've seen have a section called "PCI Devices."  Onboard graphics might be under that.

---

### Post by sophtpaw on 2006-07-15
> **jjf said:**
> I've had similar experience with AGP cards and overriding onboard graphics, so I'll chime in what I know.  

First, there is the possibility that your graphics card is not compatible with your motherboard.  The GeForce 6600GT is an AGP 4x/8x card.  If your motherboard only supports AGP 2x, you will not get it to run.  I think this is only a small possibility, but it still exists.  If you know the model number of your motherboard, post it here.

From what you describe, it sounds like your BIOS is still trying to use onboard graphics even though a graphics card is present.  I seem to remember working on a computer that did not automatically switch the onboard graphics off when a card was present.  

Here is what I would try:

[LIST]
[*]Turn the computer off.
[*]Plug the graphics card into its slot.
[*]Hook the monitor's VGA cable into the onboard graphics connector (that is, ***not*** your graphics card connector -- the other one).
[*]Turn the computer on.
[*]If the monitor displays an image, then hit whatever key is necessary to take you into your BIOS setup (often F1, F2, or delete -- hopefully the screen tells you "Press <this> to enter setup.")
[*]In order to proceed, you **must** find the option to "Disable Onboard Graphics."  It might also read "Enable AGP."  If you can't find it, locate your BIOS manufacturer and revision number (Award and Pheonix are two common brands) somewhere on the screen.  Post it here to get help, but also google it to see if you can find instructions to switch from onboard graphics to AGP graphics.
[*]Once you've switched from onboard to AGP graphics, save changes and exit.
[*]Turn the computer off.
[*]Plug the monitor's VGA cable into your graphics card connector.
[*]Turn the computer on.  Hopefully you now have a picture on the screen with the monitor plugged into the graphics card.
[/LIST]

That's only step 1.  Once you have display from your graphics card, you need to configure Ubuntu to use the nvidia driver.  I've found this to be the shortest method:

***NOTE: THESE INSTRUCTIONS ARE ONLY FOR A RECENT NVIDIA CARD LIKE THE 6600 or 6600 GT***

[LIST]
[*]As the computer is booting, be on the lookout for the GRUB menu, or the message "Press <ESC> to enter the GRUB menu."  You have to be quick, because the "Press <ESC>" only gives you 3 seconds.
[*]Once you see the GRUB boot menu, choose the topmost entry that ends in "(Recovery Mode)".  
[*]Linux will boot you into a command prompt.
[*]If you haven't already, install the nvidia drivers:
```
apt-get install nvidia-glx
```
[*]Once those are installed, open the configuration file that tell Ubuntu which of various drivers to use:
```
nano /etc/X11/xorg.conf
```
[*]Find the section that looks *something* like this (the particulars may be a little different):
```
Section "Device"
     Identifier   "Generic Graphics"
     Driver       "vesa"
     PCI:ID       0:0:0:1
EndSection
```
[*]You can leave that section as it is.  Underneath it, add these lines:
```
Section "Device"
     Identifier    "GeForce"
     Driver        "nvidia"
EndSection
```
[*]What you just did was leave the old driver listed in there as a device (in case you ever need to come back to it for some reason), but told Ubuntu that you have a *new* device that you're calling "GeForce" and that uses the "nvidia" driver.  But now you need to tell Ubunut to use this new device ("GeForce") instead of the old one.
[*]A few lines down find this section:
```
Section "Screen"
     Identifier    "Default Screen"
     Device        "Generic Graphics"
```
[*]Change the Device from "Generic Graphics" to "GeForce".  Be careful -- capitalization matters.
[*]Press CTRL and O (that's the letter "O", not the number 0) to "Write Out" (save changes).
[*]Press CTRL and X to exit.
[*]Reboot:
```
reboot
```
[/LIST]

That should fix you up.  At least, I know it's worked for me on the dozen or so computers I've had to do this to.  But if you'd feel better waiting for TS Eliot's approval or revision of these steps, that can't hurt (since he seems to know a lot about this).  Good luck.

Thank you for chiming in and your generous input indeed.

For a start my mother board is the P5800-VM Vintage in the Asus Vintage - PE!
there are many links:
[http://www.fitwears.co.uk/barebone-systems/ASUS_VINTAGE-PE1_SOCKET_775_BLACK_BAREBONE.html](http://www.fitwears.co.uk/barebone-systems/ASUS_VINTAGE-PE1_SOCKET_775_BLACK_BAREBONE.html)

Now i don't know if it supports AGPx2 only or what as you suggest might be the case. 

As far as having the graphics card in place BUT the monitors vga cable in the network slot (not in the graphics  card) this does NOT give me a picture at all. 

If i want to get a picture this way i have to take the nvidia card out. Whatever can be concluded from that...

Right now i have the nvidia agp slotted in and the monitor connected to it.

so, far as you've gathered i've had difficulty getting the nvidia drivers installed and the card configured and recognised.

I'm tempted to try your solution

I've been at this for a while now. I don't know how many times i've shutdown taken the card out or put it back in messed with teh xserver-xorg files, so if it doesn't work i'll have to go back to basics.

I might just sleep on it and try again in the morning when i am reinvigorated for what is unfortunately ALOT of work. 

Maybe tseliot can also see what you say and we can go from there

thank you for your input again, I appreciate it

--
sophtpaw

---

### Post by sophtpaw on 2006-07-15
> **jjf said:**
> I've had similar experience with AGP cards and overriding onboard graphics, so I'll chime in what I know.  


[*]Linux will boot you into a command prompt.
[*]If you haven't already, install the nvidia drivers:
```
apt-get install nvidia-glx
```
[*]Once those are installed, open the configuration file that tell Ubuntu which of various drivers to use:
```
nano /etc/X11/xorg.conf
```
[*]Find the section that looks *something* like this (the particulars may be a little different):
```
Section "Device"
     Identifier   "Generic Graphics"
     Driver       "vesa"
     PCI:ID       0:0:0:1
EndSection
```
[*]You can leave that section as it is.  Underneath it, add these lines:
```
Section "Device"
     Identifier    "GeForce"
     Driver        "nvidia"
EndSection
```
[*]What you just did was leave the old driver listed in there as a device (in case you ever need to come back to it for some reason), but told Ubuntu that you have a *new* device that you're calling "GeForce" and that uses the "nvidia" driver.  But now you need to tell Ubunut to use this new device ("GeForce") instead of the old one.
[*]A few lines down find this section:
```
Section "Screen"
     Identifier    "Default Screen"
     Device        "Generic Graphics"
```
[*]Change the Device from "Generic Graphics" to "GeForce".  Be careful -- capitalization matters.
[*]Press CTRL and O (that's the letter "O", not the number 0) to "Write Out" (save changes).
[*]Press CTRL and X to exit.
[*]Reboot:
```
reboot
```
[/LIST]

That should fix you up.  At least, I know it's worked for me on the dozen or so computers I've had to do this to.  But if you'd feel better waiting for TS Eliot's approval or revision of these steps, that can't hurt (since he seems to know a lot about this).  Good luck.



Ok, i couldn't help it. I've gone ahead and made the changes you sugges. apt-get install nvidia-glx

swapped identifier and Driver as you suggest

Just before i reboot i wondered if you would agree with tseliots advice to put# next to busid ?

--
sophtpaw

---

### Post by jjf on 2006-07-15
> **sophtpaw said:**
> 
For a start my mother board is the P5800-VM Vintage in the Asus Vintage - PE!
there are many links:
[http://www.fitwears.co.uk/barebone-systems/ASUS_VINTAGE-PE1_SOCKET_775_BLACK_BAREBONE.html](http://www.fitwears.co.uk/barebone-systems/ASUS_VINTAGE-PE1_SOCKET_775_BLACK_BAREBONE.html)

Now i don't know if it supports AGPx2 only or what as you suggest might be the case. 

I checked the link.  Your AGP slot does support AGP 8x, so the card should work fine for you.  (After configuring, of course).

> As far as having the graphics card in place BUT the monitors vga cable in the network slot (not in the graphics  card) this does NOT give me a picture at all. 

If i want to get a picture this way i have to take the nvidia card out. Whatever can be concluded from that...

Right now i have the nvidia agp slotted in and the monitor connected to it.

Good!  You're halfway there, then.  

You've got the AGP card in its slot, and the monitor connected to the back of the AGP card, and you're getting a display.  You should have no reason to pull the card out again.  Now that you're at this point, it's just a matter of getting the drivers recognized by Ubuntu.

With that in mind, I highly recommed you try my solution, starting from "*NOTE: THESE INSTRUCTIONS ARE ONLY FOR..."  

If you're at all hesitant, just back up your current xorg.conf file first.  Of course, you've already changed it a great deal, so I don't know how much that will help you after all.  Still, it never hurts.

TO BACKUP YOUR XORG.CONF FILE:

Once you're booted into Recovery Mode and see the command prompt, type:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

That makes a copy of your current xorg.conf file and calls it xorg.conf.bak

Then, if you ever decide that using my steps you've mangled that xorg.conf file beyond fixing, all you need to do is get back to the Recovery Mode command prompt and type:

```
cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

In other words, copy the backup file (xorg.conf.bak) back over the original (xorg.conf).

---

### Post by Rashid584 on 2006-07-15
BTW sophtpaw, I'm really sorry for butting into your thread and stealing half the help :p

jjf, I rebooted and went into the BIOS setup and wrote down as much relevant info as I could find.

I'm using PhoenixBIOS Setup Utility. 
Release: v 5.00 R1.04.1740
Date: 06/11/04

Under the PCI-something section, all it had was "PCI IRQ Line" 1 through to 8. All of them were set on "Auto" but they could have been disabled, or set to IRQ3-15.

Under Advanced there was an option called "PCI Bus Parity Check". I enabled that and tried booting plugged into a graphics card...didn't work.

And there was also an option for "Graphics Aperture" which was set to 64M, could have been 128/256.

Hmm.

I'm gonna give up for now, and try again tomorrow. Waiting eagerly for some advice and suggestions :D

Thanks guys (and sorry again to sophtpaw :$)

-Rashid

---

### Post by jjf on 2006-07-15
> **sophtpaw said:**
> Ok, i couldn't help it. I've gone ahead and made the changes you sugges. apt-get install nvidia-glx

swapped identifier and Driver as you suggest

Just before i reboot i wondered if you would agree with tseliots advice to put# next to busid ?

--
sophtpaw

My first recommendation would be not to swap them at all, but just add a new "Device" section below the current one.  It doesn't hurt to define two devices and only use one of them, and that way if you ever need to go back to the first device it's still there in your xorg.conf file.

But if you've already *changed* those lines, it should still be OK.  Yes, put the # in front of busid.  # just means "ignore this line."  It will do no permanent damage to your computer, and you could always go back and remove that character so that Ubuntu would no longer ignore that line (if it were necessary).

---

### Post by jjf on 2006-07-15
Headed out for dinner.  Good luck, sophtpaw.  And I'll research your BIOS tonight or tomorrow, rashid.  You could get a heardstart on me by googling 

"PhoenixBIOS 5.00 R1.04.1740"

with different variations (like adding "AGP" or "disable onboard graphics" or something)

---

### Post by sophtpaw on 2006-07-15
> **jjf said:**
> I checked the link.  Your AGP slot does support AGP 8x, so the card should work fine for you.  (After configuring, of course).



Good!  You're halfway there, then.  

You've got the AGP card in its slot, and the monitor connected to the back of the AGP card, and you're getting a display.  You should have no reason to pull the card out again.  Now that you're at this point, it's just a matter of getting the drivers recognized by Ubuntu.

With that in mind, I highly recommed you try my solution, starting from "*NOTE: THESE INSTRUCTIONS ARE ONLY FOR..."  

If you're at all hesitant, just back up your current xorg.conf file first.  Of course, you've already changed it a great deal, so I don't know how much that will help you after all.  Still, it never hurts.

TO BACKUP YOUR XORG.CONF FILE:

Once you're booted into Recovery Mode and see the command prompt, type:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

That makes a copy of your current xorg.conf file and calls it xorg.conf.bak

Then, if you ever decide that using my steps you've mangled that xorg.conf file beyond fixing, all you need to do is get back to the Recovery Mode command prompt and type:

```
cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

In other words, copy the backup file (xorg.conf.bak) back over the original (xorg.conf).

ok, i missed this post because i was already started on installing nvidia drivers AGAIN. Like i said i couldn't helpo myself. I intuited that things were alrite in terms of compatibility etc...


Anyways, unfortunately it didn't work out,yet again. It boots up but the monitor after switching on for 1/2 sec, it switched off. I don't know what the pc was doing. Humming away but nothing was happening.

So, i had to go back to the beginning. i.e. take out the card put the monitor back on the integrated motherboard, login without x, reconfigure xserver.xorg file to its original default setting and i'm back in X again.

I must be close, but i don't know what i'm doing wrong or what is missing

---

### Post by Rashid584 on 2006-07-15
[quote=jjf]Headed out for dinner. Good luck, sophtpaw. And I'll research your BIOS tonight or tomorrow, rashid. You could get a heardstart on me by googling

"PhoenixBIOS 5.00 R1.04.1740"

with different variations (like adding "AGP" or "disable onboard graphics" or something)[/quote]

Enjoy your dinner! :D

OK, I'll try. It doesn't look like its coming up with much useful stuff...

Good night! (i guess its not night for you but meh)

-Rashid

---

### Post by noelferg on 2006-07-15
I also have a Nvidia 6600GT graphics card.

One simple question to Rashid584 or sophtpaw (whoever has been pulling the plug on your graphics card lots):

Have you also plugged the internal power connector from your PSU into the graphics card?

---

### Post by sophtpaw on 2006-07-16
> **noelferg said:**
> I also have a Nvidia 6600GT graphics card.

One simple question to Rashid584 or sophtpaw (whoever has been pulling the plug on your graphics card lots):

Have you also plugged the internal power connector from your PSU into the graphics card?

that is a good question!  I don't know what PSU means but if you mean teh motherboard to the graphics card then the answer is NO

When i opened the box i did notice the power lead. that is to say a red, 2black and 1yellow combination lead, yes? The same as in the box attached and powering the dvd roms and hard-drives.

I also wondered whether i was supposed to connect it to one of the spare power cables in the box.

What i found is that the fan switched on either way. So, i presumed that it got power just from being slotted in the AGP slot. 

But you are saying that the power needs to be connected as well?

thank you for notincing and bringing this up. Could you please confirm how this card is correctly installed then

--
sophtpaw

---

### Post by sophtpaw on 2006-07-16
By the way Tseliot, i have nvidia-kernel-common 20051028+1 ticked and installed i see in synaptic

> NVIDIA binary kernel module common files
This package contains files shared between nvidia module
packages. 

and the next one too: nvidia-kernel-source

it says that nvidia-glx requires it.

> NVIDIA binary kernel module source
This package builds the NVIDIA XFree86 4.x/X.Org binary kernel module needed
by nvidia-glx.  This package is not needed on an Ubuntu system because
a pre-compiled kernel module is supplied by the linux-restricted-modules
packages. 

i noticed that it says ubuntu systems don't require it, i've therefore removed it

--
sophtpaw

---

### Post by tseliot on 2006-07-16
> **sophtpaw said:**
> By the way Tseliot, i have nvidia-kernel-common 20051028+1 ticked and installed i see in synaptic
It's required by Method 1
 

> **sophtpaw said:**
> and the next one too: nvidia-kernel-source

it says that nvidia-glx requires it.

 

i noticed that it says ubuntu systems don't require it, i've therefore removed it

--
sophtpaw
That package is useless in this case.

did you try Method 1 of my guide?

If so, what happened?

---

### Post by sophtpaw on 2006-07-16
> **tseliot said:**
> It's required by Method 1
 


That package is useless in this case.

did you try Method 1 of my guide?

If so, what happened?

Good Day Tseliot,

ok, Round 2

No, i haven't tried your method 1 yet. I thought i'd wait for today. For you to reasess and prescribe exactly what i need to do next.

I did look at the method, it seems that its everything we did yesterday already.

Can you comment on the need to plug the card to power. Previously, i had just slotted it in, and the fan came on so i thought that was enough. Should i add the power lead too however?

thank you

--
sophtpaw

---

### Post by Rashid584 on 2006-07-16
[quote=noelferg]One simple question to Rashid584 or sophtpaw (whoever has been pulling the plug on your graphics card lots):

Have you also plugged the internal power connector from your PSU into the graphics card?[/quote]

No, I haven't. But I don't see any wires or anything. There is just one black+red wire coming out of the fan that goes straight into a white thing in the card. I've stuck an old S3 Virge in now and I get the same problem...and I don't think that one needs the PSU...

Thanks for the suggestion though.

I have a 3DFuzion FX5500 BTW

-Rashid

---

### Post by sophtpaw on 2006-07-16
> **tseliot said:**
> It's required by Method 1
 


That package is useless in this case.

did you try Method 1 of my guide?

If so, what happened?

Ok, 

I've followed Method1. 

It seems that it has worked!

I went through the steps and did Cntl+alt+backspace which relogged me back in.
Also i can see Nvidia settings in Applications/SystemTools

So, that appears to be sorted

How can i prove it or test it?

Edit:

just did a complete reboot, and just before the login page coming up there was the Nvidia bootsplash so i am indeed confident that it is now successfully installed.

Thank you Tseliot for the Method! [-o< 

Now i can finally go and install XGL which this was all about. I hope it is quicker than this was. :) 

final observation. The system is MUCH louder now :(  Which is a shame. I loved how quite it was. The price of having two fans aguess

--
sophtpaw

---

### Post by Rashid584 on 2006-07-16
[quote=sophtpaw]
Ok,

I've followed Method1.

It seems that it has worked!

I went through the steps and did Cntl+alt+backspace which relogged me back in.
Also i can see Nvidia settings in Applications/SystemTools

So, that appears to be sorted

How can i prove it or test it?

Edit:

just did a complete reboot, and just before the login page coming up there was the Nvidia bootsplash so i am indeed confident that it is now successfully installed.

Thank you Tseliot for the Method!

Now i can finally go and install XGL which this was all about. I hope it is quicker than this was.

final observation. The system is MUCH louder now Which is a shame. I loved how quite it was. The price of having two fans aguess

--
sophtpaw[/quote]

Awesome! I'm glad you got it sorted man! :D Good luck with XGL ;)

-Rashid

---

### Post by Rashid584 on 2006-07-16
OK, the good news: I can get signal from the nVidia card :D :D After a bit of research (thanks jjf ;)) I found that I had to enable PCI Parity Checking, and in Main>>Boot Options>>Primary Display I had to change it from "VGA AGP" to "VGA PCI".

I did that, plugged in and I got a display.

The bad news: It goes through the boot process all the way through, and at the end, the blue loading bar goes straight back to 0 and theres no text or anything, and it just freezes there :(

I rebooted and went into recovery mode and did the dpkg-reconfigure xserver-xorg (answered the ridiculously long set of questions :p) and rebooted. Still, it did the same thing.

I've reenabled the onboard chip and rebooted using it now, to make this post.

Now I'm pretty sure its a problem with Kubuntu, not my BIOS :p

Any help appreciated.

UPDATE: OK, I tried booting from my Kubuntu Dapper Drake LiveCD, and got the same problem as with my actual install (boots but then freezes before loading X).

I then tried inserting the XGL Kororaa LiveCD, it looked like it booted fine, but at the end (when I assume it loaded X) i got not display and my monitor had a message saying "Out of Range". I hit CTRL+ALT+F2 and looked at my old xorg.conf_backup and used CTRL+ALT+F1 to edit the /etc/X11/xorg.conf to insert the ones I use normally. Removed /tmp/X0-lock and started X but still got the same "Out of Range" error even though the correct values were there in my xorg.conf

OK, so now I'm willing to admit it may be more than a problem with ubuntu alone :p

Any ideas?

-Rashid

---

### Post by tseliot on 2006-07-16
> **sophtpaw said:**
> Now i can finally go and install XGL which this was all about. I hope it is quicker than this was. :)
Be careful not to screw up your system with XGL :p 

And it's normal that the Nvidia driver generates more heat.

---

### Post by tseliot on 2006-07-16
> **Rashid584 said:**
> OK, the good news: I can get signal from the nVidia card :D :D After a bit of research (thanks jjf ;)) I found that I had to enable PCI Parity Checking, and in Main>>Boot Options>>Primary Display I had to change it from "VGA AGP" to "VGA PCI".

I did that, plugged in and I got a display.
Great news!

Please follow these steps **exactly** as I write them:

1) Do as jjf suggested, plug the card in and connect your monitor to it.

2) Boot in Recovery Mode

3) type:
```
lspci | grep VGA
```

and write down the output on a piece of paper (there's no need to post it right now).

OR (if you don't want to use a piece of paper)
```
lspci | grep VGA > /home/your_username/videolist.txt
```

OF COURSE replace "your_username" with your username.

You will find the output of that command in /home/your_username/videolist.txt

You might need that output later

4) Type: 
```
sudo nano -w /etc/X11/xorg.conf
```

Put a # before the BUSID in the section Device
Set the driver to "vesa"

CTRL+X to exit

5) reboot:
```
sudo reboot
```

and boot as usual.

If that doesn't work (explain me what happens) please post the output you got in step 4

---

### Post by sophtpaw on 2006-07-16
> **tseliot said:**
> Be careful not to screw up your system with XGL :p 

And it's normal that the Nvidia driver generates more heat.

I hope not to screw my system up with XGL :D 

I hear alot of people who are using XGL happily, so it should be possible.

It was the sole reason pretty much for getting the nvidia card. I don't see it serving any other function.

I'm not worried about the extra heat generated, but the noise! argh...:rolleyes:

---

### Post by Rashid584 on 2006-07-16
Alhamdulillah! It works! :D

tseliot, you're a genius! I really wasn't expecting that to make any difference but it works.

So now I get video output from my nVidia card...next step, I want to enable 3d acceleration. Could you guide me through that also please? I would appreciate it a LOT.

Thanks to tseliot, jjf and noelferg :D

[quote=sophtpaw]It was the sole reason pretty much for getting the nvidia card. I don't see it serving any other function.[/quote]

Dude, XGL works FINE on my intel on board graphics chip (with Kororaa) so you didn't need the new card :p I've heard people having major problems with their high end graphics card...lol. Sorry if I ruined your day :p :)

-Rashid

---

### Post by sophtpaw on 2006-07-16
> **Rashid584 said:**
> Alhamdulillah! It works! :D





Dude, XGL works FINE on my intel on board graphics chip (with Kororaa) so you didn't need the new card :p I've heard people having major problems with their high end graphics card...lol. Sorry if I ruined your day :p :)

-Rashid

HUH?! are you telling me i just spent 80pounds on a graphics card for nothing?  ](*,) 

I was told i would not be able to run XGL with teh system running with onboard graphics card

It would be great if that was true. Because, my system is rather noisy compared to the inaudible hum i enjoyed previously.

But i doubut you're right, Rashid, but i hope you are.:mrgreen:

---

### Post by Rashid584 on 2006-07-16
> **sophtpaw said:**
> HUH?! are you telling me i just spent 80pounds on a graphics card for nothing?  ](*,) 

I was told i would not be able to run XGL with teh system running with onboard graphics card

It would be great if that was true. Because, my system is rather noisy compared to the inaudible hum i enjoyed previously.

But i doubut you're right, Rashid, but i hope you are.:mrgreen:

lol, i did says sorry if I ruined your day :p

I was "told" similar things and really didn't expect it to work but when I booted it worked PERFECTLY, at smooth speed too and everything. I was like "up yours" to Bill Gates and Windows Vista, I can have all those effects with on board graphics :D :D

You can check out if your on board chip can handle XGL. Download the [Kororaa XGL LiveCD](http://kororaa.org/static.php?page=static060318-181203), burn it to ISO and boot from it. See what happens ;)

-Rashid

---

### Post by tseliot on 2006-07-16
> **Rashid584 said:**
> Alhamdulillah! It works! :D

tseliot, you're a genius! I really wasn't expecting that to make any difference but it works.

So now I get video output from my nVidia card...next step, I want to enable 3d acceleration. Could you guide me through that also please? I would appreciate it a LOT.
I'm happy for you ;) 

Try this guide of mine:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by sophtpaw on 2006-07-16
> **Rashid584 said:**
> lol, i did says sorry if I ruined your day :p

I was "told" similar things and really didn't expect it to work but when I booted it worked PERFECTLY, at smooth speed too and everything. I was like "up yours" to Bill Gates and Windows Vista, I can have all those effects with on board graphics :D :D

You can check out if your on board chip can handle XGL. Download the [Kororaa XGL LiveCD](http://kororaa.org/static.php?page=static060318-181203), burn it to ISO and boot from it. See what happens ;)

-Rashid

I'd be amazed if you're right. I was told onboard graphics was good for 2D only.

I will burn the iso you suggest. That is very useful to know. Thanks

So, why are you trying to configure a graphics card, if onboard is satisfactory? games aguess?

---

### Post by jjf on 2006-07-16
Glad you got it working, sophtpaw.  Good luck with XGL.  And I have a GeForce 6600 also in my small form factor PC.   It sounds like an airplane taking off.  :(  

My next box will be a small form factor that uses a laptop graphics card.  (If they don't make them already, I'm sure somebody will think of it soon.)  I want a little muscle for games, but want it much quieter than what I've currently got.

---

### Post by sophtpaw on 2006-07-16
> **jjf said:**
> Glad you got it working, sophtpaw.  Good luck with XGL.  And I have a GeForce 6600 also in my small form factor PC.   It sounds like an airplane taking off.  :(  

My next box will be a small form factor that uses a laptop graphics card.  (If they don't make them already, I'm sure somebody will think of it soon.)  I want a little muscle for games, but want it much quieter than what I've currently got.

Thanks JJF

airplane is right...
will see if xgl doesn't work without the card afterall as Rashid was suggesting. 
Or else i'm gonna try to find a box i can put the pc in

---

### Post by Rashid584 on 2006-07-16
[quote=sophtpaw]
I'd be amazed if you're right. I was told onboard graphics was good for 2D only.

I will burn the iso you suggest. That is very useful to know. Thanks

So, why are you trying to configure a graphics card, if onboard is satisfactory? games aguess?
Reply With Quote[/quote]

Yup. I'm not normally a games person, but I started playing Wolfenstein (was v v bored and had a completely free week with nothing to do) and enjoyed it a lot, except I got pathetic FPS. I got given this card as a gift from my work experience employer so I'm happy :D Now I'm gonna try and enable 3d accel so I can play wolfenstein enemy territory and actually get some kills, as opposed to just arty-n00bing :p

-Rashid

---

### Post by Rashid584 on 2006-07-16
OK, tseliot, I've hit a brick wall within seconds of starting :p

First I done "sudo apt-get update" then "sudo apt-get install linux-386". It told me it was up to date and fine

> rashid@rashid-desktop:~$ sudo apt-get install linux-386
Reading package lists... Done
Building dependency tree... Done
linux-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

So thats fine. I went on to do "sudo apt-get install nvidia-glx" and it gave me this error:

> rashid@rashid-desktop:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Package nvidia-glx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx has no installation candidate

So, what happened?? Do I need to add a repository? Is the package broken??

This is my sources.list

```
rashid@rashid-desktop:~$ cat /etc/apt/sources.list

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#XGL and Compiz  repositories from the Ubuntu wiki:
# deb http://xgl.compiz.info/ dapper main
rashid@rashid-desktop:~$
```

-Rashid

---

### Post by tseliot on 2006-07-16
> **Rashid584 said:**
> OK, tseliot, I've hit a brick wall within seconds of starting :p

First I done "sudo apt-get update" then "sudo apt-get install linux-386". It told me it was up to date and fine



So thats fine. I went on to do "sudo apt-get install nvidia-glx" and it gave me this error:



So, what happened?? Do I need to add a repository? Is the package broken??

This is my sources.list

```
rashid@rashid-desktop:~$ cat /etc/apt/sources.list

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#XGL and Compiz  repositories from the Ubuntu wiki:
# deb http://xgl.compiz.info/ dapper main
rashid@rashid-desktop:~$
```

-Rashid

Try adding these lines:
```
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

then type:
```
sudo apt-get update
```

and try again

---

### Post by Rashid584 on 2006-07-16
I love ya man!! :D :p

I now have a 3d enabled FX5500, thanks to everyone in this thread. The Ubuntu community ROCKS! :D

I'm gonna try out my new "muscle" on Wolfenstein enemy territory now. Ta!

-Rashid

---

### Post by sophtpaw on 2006-07-17
> **Rashid584 said:**
> lol, i did says sorry if I ruined your day :p

I was "told" similar things and really didn't expect it to work but when I booted it worked PERFECTLY, at smooth speed too and everything. I was like "up yours" to Bill Gates and Windows Vista, I can have all those effects with on board graphics :D :D

You can check out if your on board chip can handle XGL. Download the [Kororaa XGL LiveCD](http://kororaa.org/static.php?page=static060318-181203), burn it to ISO and boot from it. See what happens ;)

-Rashid

Hi, 
thought i'd just update you on this issue. As you suggested i might be able to run XGL with my onboard graphics card, i gave it a whirl.

Unfortunately, Kororaa did not work with my default system. My onboard graphics card was not supported and did not support 3-D or something.

So, i would need the nevidia graphics card after all to enable XGL. Now, i'm just wondering whether it is worth it! Sure, the cube was fun but i have to weigh that against the silence of a barely inaudible hum i have now again after taking the graphics card out.

What system do you have exactly that allowed XGL with only your onboard graphics card?

Seems the ideal-to have a system with only one fan in it (cpu) but with onboard graphics capable of supporting 3-D. Or XGL anyways...


--
sophtpaw

---

### Post by Rashid584 on 2006-07-17
Fujitsu Siemens scaleo p it has an Intel on board i82845G (whatever that means)

Its two years old, with on board graphics, which is why I was so impressed it worked perfectly with XGL/Compiz! :D Shame about yours though, I guess its a different on board chip?

Yeah, I've started to hear my computer get quite a bit louder now when I play wolfenstein. The fan is "attached" to the CPU and GPU temperature so when its working harder, the fan turns on and makes more noise :rolleyes:

and lol, can you still return it?? Otherwise, thats 80 quid down the drain :P

-Rashid

---

