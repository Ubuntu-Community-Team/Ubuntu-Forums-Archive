---
title: "No video on TV after initial boot"
date: 2008-10-20
forum: Mythbuntu
---

### Post by Figtoria on 2008-10-20
Hi, I've read through the FAQs and I haven't seen this issue anywhere.   My machine works fine on the computer monitor, but when I use the S-video cable and hook it up to my Sony Wega, the picture goes to black after the initial "Mythbuntu" loading screen.

The only other difference between the two setups, is that I have no internet connection when it is hooked up to the TV.

I wondered if it was maybe hanging there looking for one?


Thanks very much for any ideas you might have.

---

### Post by Figtoria on 2008-10-23
bump

No one has any ideas about this?

---

### Post by SiHa on 2008-10-24
When yor PC boots, it will look for any connected video devices and send the video signal there. If it can't see anything, it will generally default to VGA as the most likely candidate. From my experience I got exactly what you describe - the picture is sent to **all** ports until the X-server starts.

then if your PC just can't see anything connected to the S-Video connector, or doesn't know what to do with it, it squirts the signal out the VGA.

You'll need to edit to Xorg conf to:

Tell it to use TV-out regardless of what it thinks is connected
Tell it that you're using S-Video (as opposed to composite / component)
Tell it what video standard to use (PAL / NTSC etc)

**NB** always make a backup before tinkering:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```

Note the upper case '**X**11'

Before all of that of course you need to be able to see the screen. I guess from the fact that the PC has no internet connection, that means there is no ethernet so you can't remote logon via SSH / VNC?

So you're going to need to connect a monitor to the box at the same time as the TV.

So, assuming you've now got a picture on your monitor:

Are you using Nvidia graphics? If so, this should be quite easy. First, ensure you are using the restricted drivers, you should have had the chance to enable these during setup. To check, look in 'Hardware drivers' under the 'System' (I think) menu on the Xfce desktop.
Then, install nvidia-settings:```
sudo apt-get install nvidia-settings
```

The run it from the menu 'NVidia X-Server utility' or a terminal window ```
sudo nvidia-settings
```
I use 'sudo', as sometimes it complains it can't write the xorg.conf file.

Hopefully when this opens, it will have detected the TV, and you can play with the settings and save them to xorg. If you're lucky, a reboot will now see a picture on the TV.

Otherwise you're going to need to manually edit your xorg.conf.

There's a very good guide [ [COLOR="Blue"]here[/COLOR] ](http://en.wikibooks.org/wiki/NVidia/TV-OUT). 

Essentially, you need these three lines in the 'device' section:
```
 Option      "TVOutFormat" "SVIDEO"
 Option      "TVStandard" "PAL-B" *Or whatever is correct for your country*
 Option      "ConnectedMonitor" "TV"

```

Bob should now be your uncle and fanny your aunt.

If you still have problems, have a look at ** /var/log/xorg.0.log** and check for any error messages.

Finally, if you manage to screw up your X configuration so badly the system will only boot into low - graphics mode (This is actually quite easy to do).

Reboot, and look for the 'press Esc to enter boot menu' prompt, press it, and you'll get the Grub boot menu. Select the second entry - boot to recovery console. You will eventually get a menu screen with several options, including 'drop to root prompt' and 'continue normal boot'.

Select the root prompt, and when you get the terminal window, simply renew your backed-up xorg.conf
```
cp /etc/X11/xorg.bak /etc/X11/xorg.conf
```
Note you don't need 'sudo' as you are root.
```
exit
```
should get you back to the above menu. Select 'continue normal boot' and you should hopefully be back to where you were before tinkering.

---

### Post by penbrock on 2008-11-26
I am having the same issue, I see everything on the monitor and the TV until the desktop starts then the TV drops out. I am using an ASUS ATI A9200SE video card and can not seem to find any help on the WIKI.

I manualy added the 3 lines to my [DEVICE]so the file now looks like this
> Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
        Option      "TVOutFormat" "SVIDEO"
        Option      "TVStandard" "NTSC"
        Option      "ConnectedMonitor" "TV"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Save, reboot and no change. I looked in the log files but I am not sure what I am looking for. Here is a section where I THINK it is showing the error

> (II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL
(EE) RADEON(0): Invalid TV Standard: NTSC
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0

Any idea what I can try now?

---

### Post by fatmonk on 2008-11-26
> **penbrock said:**
> I am having the same issue, I see everything on the monitor and the TV until the desktop starts then the TV drops out. I am using an ASUS ATI A9200SE video card and can not seem to find any help on the WIKI.

I manualy added the 3 lines to my [DEVICE]so the file now looks like this


Save, reboot and no change. I looked in the log files but I am not sure what I am looking for. Here is a section where I THINK it is showing the error



Any idea what I can try now?

The OutFormat and Standard Options should be in the Screen section of the config file.

There is a How To ([http://ubuntuforums.org/showthread.php?t=665704]("http://ubuntuforums.org/showthread.php?t=665704"))on doing this for nVidia but the xorg options should be pretty much the same I'd guess - they still have to be in the right section.

I haven'ttried this with an ATI card and they are supposed to be problematic, but its worth a go.

-FM

---

