---
title: "Cannot use 720p on Intel 965G"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by karnat10 on 2007-08-27
Hello,

I have a Gigabyte GA-965G-DS3 (rev. 1.0) board with (obviously) onboard Intel 965G chipset and a Panasonic PT-AX100E projector with 720p resolution connected through VGA. I am running Feisty, and reading through all the stuff available online I got the impression that this should work.

I was wrong. After many hours of trying, 720p still refuses to work.

What I tried so far:

- enter 1280x720 resolution and Horiz/Vert info according to projector manual in xorg.conf:

```

Section "Device"
        Identifier      "Intel 965G"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Panasonic PT-AX100E"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-87
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 965G"
        Monitor         "Panasonic PT-AX100E"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x720"
        EndSubSection
EndSection

```

in this configuration, the X server always chooses 1280x768

- told xorg.conf to use i810 driver, installed 915resolution, patched video BIOS
-> patching works, but the X server insists on the wrong resolution

- in dpkg-reconfigure xserver-xorg, 1280x720 never shows up among the resolutions to choose from, no matter which driver I use or whether 915resolution is installed or not

- the resolution is wrong in GDM already, it makes no difference if I use gconf-editor to tell GNOME to use 1280x720, it still uses 1280x768

I cannot find anything else to try. Anyone have an idea?

---

### Post by t52wa_r0x on 2008-06-17
This worked for me:


Generate desired modeline using the "gtf" command:
"gtf 1280 720 60"
Copy and paste the resulting modeline into "Monitor" section of "/etc/X11/xorg.conf". You could give it a reasonable name like "1280x720_60". (You can name it anything you like.)

Under the "Screen" section, under the subsection "Display", there is a line as follows:
**Modes "XXxXX" "XXxXX" "XXxXX"** (and so on)
You should enter the name of your new modeline (e.g. "1280x720_60") in here.
By right, we would like to put it as the first mode, but that's not necessary (since it won't work automatically, anyway).

Now start the xserver with "startx".
Yes -- the modeline is not working yet.
Don't worry, open a term and do:
"xrandr --output VGA --mode 1280x720_60"

If it works, your screen will switch to the new mode.
Congrats!
If you want to apply "1280x720_60" on every X startup,
please insert the following as the 1st line of "~/.xinitrc":
**xrandr --output VGA --mode 1280x720_60**

---

