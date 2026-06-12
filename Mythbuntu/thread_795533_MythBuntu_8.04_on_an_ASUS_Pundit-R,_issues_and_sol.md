---
title: "MythBuntu 8.04 on an ASUS Pundit-R, issues and solutions"
date: 2008-05-15
forum: Mythbuntu
---

### Post by difosfor on 2008-05-15
This is a record of the issues I encountered while installing MythBuntu 8.04 on an ASUS Pundit-R computer with the following specifications:

**CPU:** Intel Celeron 2.4 GHz
**RAM:** 512 MB
**Video Card:** ATI 9100 IGP (builtin) with 64 MB shared video memory
**Remote:** Hauppage
**Hard Disk:** 250GB PATA
**Tuner:** Hauppauge PVR-350


**_Issue #1: Live CD doesn't boot_**

Trying to boot the Live CD, Installation proces or the Alternate CD all resulted in a busybox screen after a little while of loading. I noticed some errors relating to 'ata2' in the dmesg.

**Solution:** Add this boot option: generic.all_generic_ide=1
**Update:** This boot option also seems to solve segfaults after installation (also see [thread 772485]("http://ubuntuforums.org/showthread.php?t=772485&page=4"))


**_Issue #2: S-video out doesn't work_**

Apparantly the ATI 9100 AGP is no longer supported by ATI's proprietary driver (fglrx) which is needed to run Xorg. So we're left with the opensource ati/radeon driver which works fine on the VGA and DVI outputs, but can't seem to be convinced to enable it's S-video output. The closest thing I got to working with S-video was by setting the BIOS to 'TV-only' and using the vesa Xorg driver. Worked like a charm, except for the video playback performance staggering along at about 1 frame per second.
Trying to enable S-video with xrandr (based on: [http://www.ibeentoubuntu.com/2007/06/singing-ati-9100-igp-blues.html](http://www.ibeentoubuntu.com/2007/06/singing-ati-9100-igp-blues.html)) only results in bright/high contrast colors on the VGA output (higher gamma?).

Finally I decided to give the PVR 350's TV out another try. I had experimented with it in the past, but ivtv-fb at the time performed poorly and was unsuitable for playing AVI's and DVD's. Luckily things are now running smoothly with the ivtvfb kernel module.
Installation was pretty straight forward with ivtv already running:
[LIST]
[*]sudo echo ivtvfb >> /etc/modules
[*]Reboot and verify your console is showing on the 350's TV out
[*]sudo apt-get install xserver-xorg-video-ivtv
[*]Modify /etc/X11/xorg.conf (attached below)
[LIST]
[*]Determine /dev/fb number with 'cat /proc/fb'
[*]Determine busid with 'lspci | grep Internext' (convert to decimal)
[/LIST]
[*]sudo /etc/init.d/gdm restart
[*]Verify X is showing on the 350's TV out
[*]Configure MythTV to use the 350 (TV Settings->Playback)
[LIST]
[*]The video device is usually /dev/video16
[/LIST]
[/LIST]
**Solution summary:** Use PVR 350 S-video out with ivtvfb


**_Issue #3: Mythfrontend segfaults_**

Whenever I tried to watch Live TV or a recorded program mythfrontend segfaulted on me. It seems the ati/radeon Xorg driver doesn't support MythTV's OpenGL painting.

**Solution:** Leave MythTV 'Paint Engine' (Setup->Appearance) on Qt instead of OpenGL
**Update:** For some reason it started segfaulting again; I must have inadvertedly enabled another troublemaking option. After changing to the ivtv Xorg driver things worked like a charm though.


**_Issue #4: Tuning Dutch channels and getting XMLTV data_**

During configuration I could not find a Dutch XMLTV source, so I downloaded my favorite grabber from: [http://code.google.com/p/tvgrabnlpy/](http://code.google.com/p/tvgrabnlpy/) into /usr/bin after which I could select it. Make sure to configure the grabber on the command line as well as documented. 
Channel frequencies in the Netherlands are non-standard so I set the frequencies to 'try all' instead of 'western european', looked up the frequencies at my provider's website and mapped them to the frequency id's (mapping formula: try-all freq. id = freq. (in MHz?) - 43).

**Solution summary:** Download tv_grab_nl_py and work with 'try-all' frequencies


**_Issue #5: Overscan and menubar_**

My PVR-350+TV combo was suffering from significant overscan (elements falling off the edges of the screen).

**Solution:** Use Screen Setup Wizards and set menubar to hide automatically


**_Issue #6: TV Guide becomes hidden_**

This seems to be a known bug: [http://svn.mythtv.org/trac/ticket/4964](http://svn.mythtv.org/trac/ticket/4964)

**No solution yet**


**_Attachments_**

**/etc/X11/xorg.conf**
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Hauppauge PVR 350 Framebuffer"
        Driver          "ivtv"
        BusID           "PCI:2:14:0"
        Option          "fbdev"         "/dev/fb0"
        Option          "TVStandard"    "PAL"
        Option          "VideoOverlay"  "on"
        Option          "XVideo"        "1"
        Screen 0
EndSection

Section "Monitor"
        Identifier  "PAL Monitor"
        HorizSync  30-68
        VertRefresh 50-120
        Mode "720x576"
                # D: 41.475 MHz, H: 44.693 kHz, V: 74.488 Hz
                DotClock 41.476
                HTimings 720 752 840 928
                VTimings 576 580 584 600
                Flags    "-HSync" "-VSync"
        EndMode
EndSection

Section "Screen"
        Identifier      "TV Screen"
        Monitor         "PAL Monitor"
        Device          "Hauppauge PVR 350 Framebuffer"
        Defaultdepth    24
        DefaultFbbpp    32
        SubSection "Display"
                Depth   24
                FbBpp   32
                Modes   "720x576"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "TV Screen" 0 0
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "dri"
        Load            "v4l"
EndSection

Section "DRI"
        Group           "video"
        Mode            0666
EndSection

```

**~/.xmltv/tv_grab_nl_py.conf**
```

1 Nederland 1
2 Nederland 2
3 Nederland 3
4 RTL 4
5 E&eacute;n
6 KETNET/Canvas
7 BBC 1
8 BBC 2
9 ARD
10 ZDF
17 TV 5
18 National Geographic
19 Eurosport
25 MTV
26 CNN
29 Discovery Channel
31 RTL 5
34 Veronica
35 TMF
36 SBS 6
37 NET 5
40 AT 5
46 RTL 7
86 BBC World
89 Nickelodeon
91 Comedy Central
92 RTL 8

```

**update-channels-nl-upc-amsterdam.sql**
```

UPDATE channel SET freqid='173', finetune='0' WHERE callsign='NED1';
UPDATE channel SET freqid='141', finetune='0' WHERE callsign='NED2';
UPDATE channel SET freqid='149', finetune='0' WHERE callsign='NED3';
UPDATE channel SET freqid='181', finetune='0' WHERE callsign='RTL4';
UPDATE channel SET freqid='189', finetune='0' WHERE callsign='RTL5';
UPDATE channel SET freqid='237', finetune='0' WHERE callsign='SBS6';
UPDATE channel SET freqid='197', finetune='0' WHERE callsign='RTL7';
UPDATE channel SET freqid='493', finetune='0' WHERE callsign='RTL8';
UPDATE channel SET freqid='629', finetune='0' WHERE callsign='VER';
UPDATE channel SET freqid='229', finetune='0' WHERE callsign='NET5';
UPDATE channel SET freqid='517', finetune='0' WHERE callsign='NICK';
UPDATE channel SET freqid='517', finetune='0' WHERE callsign='COMC';
UPDATE channel SET freqid='245', finetune='0' WHERE callsign='TMF';
UPDATE channel SET freqid='725', finetune='0' WHERE callsign='MTV';
UPDATE channel SET freqid='469', finetune='0' WHERE callsign='AT5';
UPDATE channel SET freqid='157', finetune='0' WHERE callsign='VRT1';
UPDATE channel SET freqid='165', finetune='0' WHERE callsign='KET';
UPDATE channel SET freqid='741', finetune='0' WHERE callsign='BBC1';
UPDATE channel SET freqid='749', finetune='0' WHERE callsign='BBC2';
UPDATE channel SET freqid='709', finetune='0' WHERE callsign='BBCW';
UPDATE channel SET freqid='205', finetune='0' WHERE callsign='CNN';
UPDATE channel SET freqid='613', finetune='0' WHERE callsign='EURO';
UPDATE channel SET freqid='501', finetune='0' WHERE callsign='NGEO';
UPDATE channel SET freqid='757', finetune='0' WHERE callsign='DISC';
UPDATE channel SET freqid='677', finetune='0' WHERE callsign='ARD';
UPDATE channel SET freqid='685', finetune='0' WHERE callsign='ZDF';
UPDATE channel SET freqid='525', finetune='0' WHERE callsign='TV5';

```

---

### Post by lenn-art on 2008-05-27
@ Issue 2: did you use the TV out for liveTV only or also for the X?

---

### Post by difosfor on 2008-05-27
> **lenn-art said:**
> @ Issue 2: did you use the TV out for liveTV only or also for the X?

I use it both for console/Xorg (with ivtvfb module) and MythTV (live/recorded) out.

---

