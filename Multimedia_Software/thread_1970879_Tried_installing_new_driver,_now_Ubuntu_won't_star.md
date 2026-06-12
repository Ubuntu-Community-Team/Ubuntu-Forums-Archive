---
title: "Tried installing new driver, now Ubuntu won't start"
date: 2012-05-01
forum: Multimedia Software
---

### Post by EricDallal on 2012-05-01
I've been having a problem where I can't do presentations on my computer because the screen won't transfer to a projector. My Ph. D. thesis proposal presentation is three days away and I've been desperately trying to get this to work so I thought I would update the driver with a proprietary one. I installed the driver for the ATI Mobility Radeon 5730 video card and upon restating the computer Ubuntu doesn't start. The screen goes black, the fan goes crazy, and I have to restart the computer. I only have access to safe mode. Please help me.

---

### Post by The Rnegade on 2012-05-01
> **EricDallal said:**
> I've been having a problem where I can't do presentations on my computer because the screen won't transfer to a projector. My Ph. D. thesis proposal presentation is three days away and I've been desperately trying to get this to work so I thought I would update the driver with a proprietary one. I installed the driver for the ATI Mobility Radeon 5730 video card and upon restating the computer Ubuntu doesn't start. The screen goes black, the fan goes crazy, and I have to restart the computer. I only have access to safe mode. Please help me.

buddy if you install the ati driver from anything other than the ubuntu repos, you have to type 

sudo aticonfig --initial

into the terminal before restarting or you get that problem.hold on let me think over a solution, i've solved this problem for myself in the past

---

### Post by The Rnegade on 2012-05-01
> **The Rnegade said:**
> buddy if you install the ati driver from anything other than the ubuntu repos, you have to type 

sudo aticonfig --initial

into the terminal before restarting or you get that problem.hold on let me think over a solution, i've solved this problem for myself in the past

ok the only chance to solve this problem without a fresh install is to try to manualy create an ati xorg configuration problem. ok so you need to boot into an ubuntu live cd and click try ubuntu. from there you need to open a terminal and type

gksu nautilus

you may get some kind of message or error crap, ignore that and close it, then you'll notice a window that should have an icon that says desktop or someithng else or nothing, doesnt matter, on the left side of that window there will be a list of things, file systems, disk drives. click on the filesystem that contains your ubuntu partition. now open the etc folder and then the x11 folder. if there is a xorg.conf file in there already rename it xorg.conf1, there might not be one, it doesnt matter. now create a new text file in that directory and name it xorg.conf   

ok now you need to put some info in that text file. here's the content of my xorg.conf, you might have to make a few changes to it to make it more relevant to your graphics card and screen
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


like i said you may have to amend it slightly, but that essentially what you want in your xorg.conf.

now when thats stuffs in there, save it and reboot, make sure to take out the disc. now your computer should start up. if not post another message here and i'll give you some alternative solutions

---

### Post by alphacrucis2 on 2012-05-02
> **EricDallal said:**
> I've been having a problem where I can't do presentations on my computer because the screen won't transfer to a projector. My Ph. D. thesis proposal presentation is three days away and I've been desperately trying to get this to work so I thought I would update the driver with a proprietary one. I installed the driver for the ATI Mobility Radeon 5730 video card and upon restating the computer Ubuntu doesn't start. The screen goes black, the fan goes crazy, and I have to restart the computer. I only have access to safe mode. Please help me.

Did you try 

```
sudo aticonfig --initial -f
```

---

### Post by The Rnegade on 2012-05-02
> **alphacrucis2 said:**
> Did you try 

```
sudo aticonfig --initial -f
```

Yeah that would probably work too

---

### Post by EricDallal on 2012-05-03
Thanks for the help guys. I actually found an article on-line [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide") which explained how to remove the driver entirely and then re-install it. I went to campus today and after getting some help managed to get it to work with the projector. I had to go into the ATI configuration settings (i.e., Ubuntu's built in "Monitors" settings in the preferences was not enough).

If anyone sees this post and has the same problem, I highly recommend following that guide and then using the ATI configuration settings to get things to work.

---

