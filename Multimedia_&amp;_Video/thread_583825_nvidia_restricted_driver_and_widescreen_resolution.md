---
title: "nvidia restricted driver and widescreen resolutions in Gutsy"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by kolors on 2007-10-20
Just installed Gutsy on a bookshelf PC (ASUS P1-AH2) with an NVIDIA GeForce 6150 integrated graphics chip, and after enabling the restricted driver I lost proper widescreen resolutions.

My monitor is an Acer AL1916W, with native resolution of 1440x900 (60 or 70Hz)

Now under Screens and Graphics, the closest I can select is 1400x1050@50Hz, even when the monitor is selected from the list and the widescreen checkbox is checked.

Using the nv driver, I can select 1440x900 just fine, but the combo of the AL1916W and nvidia restricted driver seems to mess it up (Compiz Fusion effects work fine, as do other features of the restricted driver, but the best looking resolution I can run as is currently 1280x800).

I have modified my xorg.conf multiple times and it just defaults to 1280x800, and the nvidia-settings tool strangely tells me that the Acer AL1916W reports a native resolution of 1400x1050.

Even doing a dpkg-reconfigure -phigh xserver-xorg and generating a new xorg.conf doesn't help... it just doesn't seem to like 1440x900 with this combination.

Any ideas?

-------
Misc information:

Xorg configuration (see attached)
Results of ddcprobe (see attached)

$ lspci -n | grep 0300
00:05.0 0300: 10de:0240 (rev a2)
$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)

---

### Post by cojoco on 2007-10-20
I have a 1680x1050 widescreen, and my resolutions were also getting messed up:
the screen res really *was* 1680x1050, but it was displaying on my monitor in the middle
of the screen at 4:3 aspect ratio.

I gave up and installed Envy, and that sorted everything.

---

### Post by kolors on 2007-10-22
I can select 1400x1050 oddly enough, and it just sort of squashes the resolution a bit... my monitor can't handle beyond 900 vertical px though, so that was a bit surprising.

I would like to run the nvidia restricted driver to enjoy the benefits of Compiz Fusion, but in the meantime the nv driver at least will display the resolutions properly.

I even tried Envy and it didn't seem to do anything -- it just built and installed the restricted driver and again wouldn't allow me to select the widescreen resolution 1440x900

Any ideas?

---

### Post by scottness on 2007-10-22
I've actually had this same problem with my Dell Insprion E1505 laptop.  Resolution just defaults itself to 1280x800.  I don't know why.  I actually had it with the right resolution (1440x900) after the first install, but after (unsuccessfully) trying to hook up an lcd projector for a presentation, my resolution just frizzed out.  I've tried to use envy, and it didn't work.  

Not real sure what to do about this bug.

---

### Post by kolors on 2007-10-23
Oh, and I don't know if this makes any difference, but I'm running the amd64 version of Gutsy.

Does the E1505 use nvidia integrated graphics?

---

### Post by scottness on 2007-10-23
Nvidia Geforce Go 7300 is the card...not sure if that's integrated or not...

---

### Post by dmuir on 2007-10-23
Got a similar problem.... err had.

Fixed it by going into Screen and Graphics under System->Administraion
Selected the 1680x1050 LCD option and ticked the checkbox for widescreen monitor.

---

### Post by smah77 on 2007-10-23
> **kolors said:**
> Just installed Gutsy on a bookshelf PC (ASUS P1-AH2) with an NVIDIA GeForce 6150 integrated graphics chip, and after enabling the restricted driver I lost proper widescreen resolutions.

My monitor is an Acer AL1916W, with native resolution of 1440x900 (60 or 70Hz)

Now under Screens and Graphics, the closest I can select is 1400x1050@50Hz, even when the monitor is selected from the list and the widescreen checkbox is checked.

Using the nv driver, I can select 1440x900 just fine, but the combo of the AL1916W and nvidia restricted driver seems to mess it up (Compiz Fusion effects work fine, as do other features of the restricted driver, but the best looking resolution I can run as is currently 1280x800).

I have modified my xorg.conf multiple times and it just defaults to 1280x800, and the nvidia-settings tool strangely tells me that the Acer AL1916W reports a native resolution of 1400x1050.

Even doing a dpkg-reconfigure -phigh xserver-xorg and generating a new xorg.conf doesn't help... it just doesn't seem to like 1440x900 with this combination.

Any ideas?

-------
Misc information:

Xorg configuration (see attached)
Results of ddcprobe (see attached)

$ lspci -n | grep 0300
00:05.0 0300: 10de:0240 (rev a2)
$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)

Weird, I had the opposite problem - I didn't get proper widescreen resolution at 1440x900 until I installed the nVidia driver.  Before that it was all squished.

---

### Post by mikematsuri on 2007-10-23
I'll voice in to say I have the same problem and have yet to find a solution. Using amd64 Gutsy with the AL1916W monitor and a GF7300GS card. Using the open source drivers I have widescreen 1440x900 but the nvidia proprietary drivers force me on 1400x1050.

I've tried various xorg.conf hacks that fixed a similar problem for me with Feisty, and basically every other fix to a similar problem I've found on these forums. Right now I'm living with a squished screen and Compiz, but I've also been forced to scrolling virtual desktops depending on the xorg I use. This seems to frequently disable the new Screen Resolution tool (claiming something about Xrandr not working), though right now it will open. However, both it and the Screens and Graphics tool tell me my resolution is currently 2424x1050 while nvidia-settings says 1400x1050. Since changing those affects nothing but changing the nvidia-settings does, I tend to think it depends on the proprietary driver right now.

I'm playing with settings and looking for other ideas, but this seems like a good place to keep checking in case someone else figures it out first.

mm

---

### Post by kolors on 2007-10-23
I had been using FreeBSD headless on this machine before Gutsy, so this problem is new to me.

Did anyone have a working 1440x900 resolution using the nvidia proprietary driver with the AL1916w in Feisty or Edgy?

If not, perhaps it's best to start asking around in the nvidia forums

---

### Post by caino on 2007-10-24
i just got my first nvidia card (low end n6200) and have been having a bear of a time getting it to work.  the 7.10 install from the disk ends up crashing when attempting to load drivers.

did 7.04 install -> 7.10 upgrade... still cant get any widescreen resolutions.

frustration.  my main box, using an old radeon 9200 has had no problems since 6.06 and is now running 7.10 + compiz no problems.  i thought nvidia was supposed to be better under *nix?

---

### Post by mikematsuri on 2007-10-24
To clarify, I did get 1440x900 resolution working with my same card/monitor under Feisty with the proprietary nvidia drivers. If I recall correctly, I had a resolution problem with the live CD (which is resolved under Gutsy), as well as after install. Eventually, a xorg.conf hack of adding the right lines resolved the issue, combined with using sudo nvidia-settings to save a bland xorg file where only the resolution was correct. I had to copy all my mouse and other settings from a backup xorg.conf. Unfortunately, nvidia-settings is not giving me the 1440x900 option to do this under Gutsy now.

---

### Post by Hagbard on 2007-10-25
Working on a fresh install of Gutsy Gibbon, Nvidia Geforce 8600 and Acer AL1916W and also having this issue. I've been playing with trying to use the GUI tools that are new in Gutsy, the old standby of dpkg-reconfigure xserver-xorg, and some manual adjustment, and so far have not been able to produce the proper 1440x900 resolution using the nvidia proprietary driver. Any additional suggestions or tweaks to get the correct output? Has someone opened a bug report on this with...someone? Since the issue relates to a closed source driver I'm not sure how much focus the Ubuntu devs will put into it, but it does seem to be related to the interaction of the new GUI configuration tools with the nvidia closed driver.

---

### Post by kolors on 2007-10-25
perhaps it would be best to begin inquiries at [nvnews.net]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")

edit: just found [this thread here]("http://www.nvnews.net/vbulletin/showthread.php?t=86579&highlight=acer+al1916w"), perhaps it'd be of use (I am not at my computer to test this right now)

> i had the same issue (same monitor) and it was fixed with these two lines:

you dont need modelines at all to get this working. remove those and under the screen section, just put in "1400x900" under the 24 bit section and you should be ok.

add them under the device section of the xorg.conf

Option "ExactModeTimingsDVI"
Option "ModeValidation" "NoDFPNativeResolutionCheck"

---

### Post by kolors on 2007-10-25
I seem to have fixed it enough to get 1440x900, although I couldn't exactly tell you how.

The nvidia restricted driver was not loading before with my old xorg.conf, so I purged nvidia-glx-new, and then I blew away the config and did a dpkg-reconfigure -phigh xserver-xorg, selecting 1440x900 and 1280x800

After re-installing the nvidia driver, I changed 'nv' to 'nvidia' in my xorg.conf and I fired up gdm, and it just... started. Although it tells me it's running at 50Hz refresh rate for a custom display.

I'm going to play around with this and see if I can't get a proper refresh rate...


Relevant sections of xorg.conf (note no modelines):

```
Section "Device"
        Identifier      "nVidia Corporation C51PV [GeForce 6150]"
        Driver          "nvidia"
        BusID           "PCI:0:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation C51PV [GeForce 6150]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x900" "1280x800"
        EndSubSection
EndSection
```

---

### Post by cka on 2007-10-26
> **kolors said:**
> perhaps it would be best to begin inquiries at [nvnews.net]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")

edit: just found [this thread here]("http://www.nvnews.net/vbulletin/showthread.php?t=86579&highlight=acer+al1916w"), perhaps it'd be of use (I am not at my computer to test this right now)

That worked for me, thank you (issue with 6150 onboard video & acer AL1916w monitor)

I was going out of my mind with Gutsy defaulting to 1400x1050, everything looking all stretched and mangled.  Now it's all gravy.

---

### Post by Lou Quillio on 2007-11-04
> **Hagbard said:**
> Since the issue relates to a closed source driver I'm not sure how much focus the Ubuntu devs will put into it, but it does seem to be related to the interaction of the new GUI configuration tools with the nvidia closed driver.
I had a lot of problems getting a new 1680x1050 widescreen working properly on both my XFCE desktop and in GDM, with an nVidia 5200 and proprietary drivers.  `displayconfig-gtk` made some bizarre choices, and a pretty big mess.

But when I replaced my `xorg.conf` with the output proposed by `nvidia-settings` -- replaced, not merged -- sanity returned.  So I think maybe the lesson is that if you go with the proprietary driver you should use the proprietary conf tool -- at least for anything related to display.

LQ

---

