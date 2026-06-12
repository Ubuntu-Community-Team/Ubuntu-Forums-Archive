---
title: "Screen Resolution"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by ryuninja on 2007-08-19
I am having problems making the computer keep my resolution settings that I set in the nvidia-settings area.  I have tried numerous guides and none seem to work.  I would greatly appreciate any help, thanks.

---

### Post by kyphi on 2007-08-20
How about providing some background information, ryuninja.

1. Which version of Ubuntu are you using?
2. Is your monitor widescreen or normal screen?
3. Is your computer a  laptop or a desktop?
4. Which video card are you using?
5. Have you loaded the drivers for your video card?
6. If you have, where did you get them from?
7. What have you tried to resolve this problem?

etc, etc, etc

Some information would sure take the guesswork out of trying to think of a solution to your problem.

I also like to know which part of the world this request comes from but that is just a personal preference.

---

### Post by Harlequin on 2007-08-20
Bring up a terminal and type:

sudo nano /etc/X11/xorf.conf

in the file that opens find the section that looks like this

> Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G70 [GeForce 7600 GT]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1600x1200" "1024x768"  "800x600"       "640x480"
        EndSubSection
EndSection

Remove all the resolution options that you don't want.  Typically you will only need to do this to the Depth 24 section (unless you are running 8 or 16 bit in which case edit the corresponding section).  By default X will use the first resolution setting in the line - this is also the place for you to enter unusual resolutions if you have a wide screen monitor.

Save and exit the file by pressing ctrl-X and then restart the X server - either by restarting the machine or pressing ctrl-alt-backspace

---

### Post by ryuninja on 2007-08-20
I'm running the newest version of the Desktop version of Ubuntu.  My monitor is a regular one.  My computer is a desktop and I'm running a Nvidia 8800 gts.  I used the ENVY script to install and configure my drivers.  I'm afraid I don't have the links to the tutorials Ive tried nor the memory of which commands I used.  When I typed In the sudo nano /ect/X11/xorf.conf I get the following output in the terminal: >   GNU nano 2.0.2           File: /etc/X11/xorf.conf                             




















                                  [ New File ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell
  And to answer your last question Kyphi, I hale from the United Sates of America.

---

### Post by hailtothethief on 2007-08-20
To throw in my two bits:

The actual file path is

/etc/X11/xor**g**.conf

notice, g, not f. It must have been  a typo.

---

### Post by acavella on 2007-08-20
I am also experiencing this same problem.  I am running Ubuntu 7.04 w/ a nVidia GeForce 6600.  I have installed the "default" nVidia drivers that Ubuntu provided.  When I did this, Ubuntu went out to the internet and download a nVidia package update.  

The follow is the output from: /etc/X11/xorg.conf
> 
Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600]"
        Driver          "nvidia"
        Busid           "PCI:5:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV43 [GeForce 6600]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
                SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1024x768"      "800x600"
        EndSubSection
EndSection


As you can see I have gone in and edited the 24 bit subsection, adding 1280x1024 to the list of resolutions.  Now, when I turn the computer on, the "log-in/welcome" screen seems to display at 1280x1024.  However, once I log in it defaults back to 1024x768.  When I go to change the screen resolution, the screen goes haywire (becomes distorted/blocks) and a few seconds later goes completely black.  Any thoughts?  I'm somewhat at a loss now.

---

### Post by gotvols on 2007-08-20
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics $
        Monitor         "HP w1907"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection

I'm using Ubuntu 7.04 and I edited my config file so that only one screen resolution is available, but it still won't go to it. When i go to the perferences screen resolution it still has the default resolutions.  Any help would be appreciated.  It has the right monitor.

---

### Post by acavella on 2007-08-20
gotvols,

I'll try not to sound like I know anything, however, I think I have noticed a problem w/ your configuration.  

You have deleted all but "1 bit" screen resolutions.  However, your configuration still is telling your system to use 24 bit as it's default res...

---

### Post by ryuninja on 2007-08-20
I finally got it (thanks to others ideas and advice)! :)  I went into the /etc/X11/xorg.conf file in the terminal and edited every line with my resolution to what I wanted: > Section "Screen"
        Identifier      "Default Screen"
        Device          "Nvidia 8800 GTS"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
 then pressed the keys:   ctrl x, y, enter in that sequence.  Then I pressed ctrl backspace.  When I first loged in it game me a lower setting than 1600x1200 so I went into system->preferences->Screen Resolution and chose 1600x1200 from the list and pressed ctrl backspace.  It saved and Im enjoying good times.  Thanks for everyones help, all the steps I followed above were not thought of by me.  Thanks everyone who contributed to the solution.

---

### Post by acavella on 2007-08-21
ryuninja,

Well, wasn't that an easy fix...

Thanks for tracking down and sharing the final solution.  Changing all of the different settings to reflect the same options/screen resolutions fixed my problem as well.  

> 
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV43 [GeForce 6600]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"  "1024x768" "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x1024"  "1024x768" "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x1024"  "1024x768" "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x1024"  "1024x768" "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x1024"  "1024x768" "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"  "1024x768" "800x600"  "640x480"
        EndSubSection
EndSection


gotvols,

I would suggest you try a setup like either mine or ryuninja.  Not sure the resolution you are seeking, but I'm sure you get the idea...  Good luck!

---

### Post by gotvols on 2007-08-21
> **ryuninja said:**
> I finally got it (thanks to others ideas and advice)! :)  I went into the /etc/X11/xorg.conf file in the terminal and edited every line with my resolution to what I wanted:  then pressed the keys:   ctrl x, y, enter in that sequence.  Then I pressed ctrl backspace.  When I first loged in it game me a lower setting than 1600x1200 so I went into system->preferences->Screen Resolution and chose 1600x1200 from the list and pressed ctrl backspace.  It saved and Im enjoying good times.  Thanks for everyones help, all the steps I followed above were not thought of by me.  Thanks everyone who contributed to the solution.

I did what you said you did, but nothing changed for me.  I still have the default resolutions. Here is what my file looks like now.

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics $
        Monitor         "HP w1907"
        Defaultdepth 24
SubSection "Display"
Depth 1
Modes "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by kyphi on 2007-08-22
Hello gotvols,

From your specifications it seems that you have a wide-screen monitor as well as an intel graphics chip so you will need an intel graphics driver.

You may be able to find a solution at the following URL

[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b4edf9f796d7f1ff720372aa5e7f4759618cf6d3](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b4edf9f796d7f1ff720372aa5e7f4759618cf6d3)

I hope that you have not changed your xorg config file too much or that you had a backup copy.  That file is much easier to change by using

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and selecting your desired resolution with your spacebar.

But it is always a good idea to backup any file you want to change in case things go wrong.

---

