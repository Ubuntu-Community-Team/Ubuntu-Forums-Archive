---
title: "ATI HD 3200 limits res to 1024x768"
date: 2009-05-30
forum: Multimedia Software
---

### Post by MushZA on 2009-05-30
Hi,

I am a noob Linux user & this is my first post. Please move to correct section if this is incorrect.

I have installed Jaunty on my HP 6735s and have been having some problems with the graphics.

It only allows resolutions from 320x200 to 1024x768.

The laptop screen's default is 1280x800.

I downloaded and installed ATI Catalyst™ 9.5 Proprietary Linux x86 Display Driver from
AMD's website, followed the instructions but the display properties still only allow a max of 1024x768.

I have googled and searched this forum for answers, the closest topic being [http://ubuntuforums.org/showthread.php?t=1133950&page=2](http://ubuntuforums.org/showthread.php?t=1133950&page=2) and while they do not appear to have the same problem, i followed their instructions anyways, still no 1280x800. 

I can confirm that the fglrx drivers are loading by running  aticonfig --initial=check
Here are the contents of my /etc/X11/xorg.conf:
```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
        SubSection "Display"
                Virtual   1152 1632
        EndSubSection
EndSection

```i did try sudo aticonfig --resolution=Screen0,1280x800 but get the following error:
Error: Section # expected
aticonfig: parsing the command-line failed.

I attributed this to noobness at first, but after reading and re-reading the usage just got frustrated at it because thats the exact syntax it specifies.

I am unsure as to what other information is required for this type of problem.

Any help/input/suggestions is/are much appreciated!

Kind Regards
Hamish

---

### Post by MushZA on 2009-06-05
Hi.

If anyone else has same prob this is what I did to fix it:

1) uninstall ATI proprietry drivers in System->Administration->Hardware Drivers

2) sudo gedit /etc/X11/xorg.conf . I edited my "Screen Section" to look like this:

```

Section "Screen"
              Identifier "Default Screen"
              Device     "Configured Video Device"
              Monitor    "Configured Monitor"
              DefaultDepth     24
              SubSection "Display"
#                                Virtual   1152 1632
                                  Depth 24
                                  Modes "1280x800"
                EndSubSection
EndSection

```3) Restart Linux

4) Goto Display Properties in System->Preferences

Now resolutions above 1024x768 are available (up to 1280x800)! :D

Cheers
Hamish

---

### Post by stylius on 2009-06-15
Yes, that's what I did, but this way we have not 3D Acceleration at all! I want to try some games and they all fail, because the lack of drivers.

---

