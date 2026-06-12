---
title: "nVidia Resolution Resets"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by brickheadbs on 2007-03-22
[FONT="Verdana"]My problem: display resolution and bit depth will not save.

I've attempted two completely different ways to fix this. First I had used "Envy" to install the nVidia drivers for me. My resolution kept reverting to 800x600. This has been my first installation attempt of Ubuntu so I tinkered around with the xorg.conf and found some other suggestions in the forums about editing the bit depth, etc. Nothing worked.

Now I reinstalled since, aside from this problem, I'm planning on giving Ubuntu my whole system. I reformatted my HDDs and went to work.

This time I installed the driver from nVidia's website. Now my resolution is stuck too HIGH! Less annoying I guess. The biggest problem is I can't change my bit depth. I want to run Beryl but can't change to 24 bit depth. My only options are 16 & 32 in the nVidia X server utility. I press save to X file and it says it's saving but reboot and...

I also had trouble with no video to start until I changed xorg.conf to the vesa driver. Then I could see to setup my system. I'm not letting this stop me. But Ubuntu REALLY doesn't like my graphics card!

System basics:
AMD64 3000+ (20% overclock)
ECS nForce-3A Motherboard
nVIdia GeForce 6600 256MB
1GB Corsair
3 160GB HDD's (anyone know if fakeRAID really works?)

And the important part of my xorg.conf:
[PHP]
Section "Monitor"
    Identifier     "E90f-2"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "E90f-2"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
[/PHP]
Help![/FONT]

---

### Post by tseliot on 2007-03-22
> **brickheadbs said:**
> [FONT="Verdana"]My problem: display resolution and bit depth will not save.

I've attempted two completely different ways to fix this. First I had used "Envy" to install the nVidia drivers for me. My resolution kept reverting to 800x600. This has been my first installation attempt of Ubuntu so I tinkered around with the xorg.conf and found some other suggestions in the forums about editing the bit depth, etc. Nothing worked.

Now I reinstalled since, aside from this problem, I'm planning on giving Ubuntu my whole system. I reformatted my HDDs and went to work.

This time I installed the driver from nVidia's website. Now my resolution is stuck too HIGH! Less annoying I guess. The biggest problem is I can't change my bit depth. I want to run Beryl but can't change to 24 bit depth. My only options are 16 & 32 in the nVidia X server utility. I press save to X file and it says it's saving but reboot and...
[/FONT]
There's no need to reinstall Ubuntu for such a thing.

nvidia-settings didn't save your settings because you should have launched it with "sudo":
```
sudo nvidia-settings
```

The next time you press "save to X file" your resolution will be saved

---

### Post by brickheadbs on 2007-03-22
The first time around I found that listed as one of the fixes. This time, DOCH! It worked??

I'm having trouble learning how things like this work...Thanks for the trouble of helping me. ENVY is a great program. I hope the Ubuntu developers continue to simplify things. Well done.

You don't know how I can get 24 bit color do you? I've got it to save to 16 now...hopefully Beryl will work...

It's really hard getting used to linux. I can't stop the urge to reinstall every 5 minutes...That's how you fix WINDOWS problems!

---

### Post by tseliot on 2007-03-22
> **brickheadbs said:**
> You don't know how I can get 24 bit color do you? I've got it to save to 16 now...hopefully Beryl will work...
Weird... I saw "DefaultDepth    24" in your xorg.conf

> **brickheadbs said:**
> It's really hard getting used to linux. I can't stop the urge to reinstall every 5 minutes...That's how you fix WINDOWS problems!
I know what you mean. There are many things I just can't solve in Windows. GNU/Linux distros are much more open and transparent.

---

### Post by brickheadbs on 2007-03-22
Again thanks for getting the save issue fixed. Do you know why it won't save if I launch from the applications menu?

And the lack of the 24 bit depth, should I start a new thread on that? I guess I can't run Beryl on 16 or 32 bit???

I've always been good at breaking computers, even when I don't touch anything. That's how I've leaned so much. Maybe I should do some Beta testing. Any ideas?

[COLOR="Sienna"]Edited Addition: I just changed the advanced setting rendering path to 'copy' and it seems to have gotton me title bars back in Beryl. Maybe I don't really need 24 bit color??? 32 is better.

I think that will cap this thread. I hope. Give me 5 minutes to break something else... :-)[/COLOR]

---

### Post by mynis on 2007-06-10
im having the same problem, i tried booting the settings pannel with sudo like you suggested but it didnt fix the problem. However on my pc, it starts up ubuntu in 1280 x 1024, but then when i log in with my username/pass it resets it back to 1024 x 768 when loading the actual desktop.

this is my xorg.conf

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Gateway"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

i noticed it lists the available resolutions, but i dont see an arena that suggests a default resolution

---

### Post by mynis on 2007-06-10
i fixed it myself, didnt even have to edit  xorg.conf.
turns out in the end, all i had to do was check the box in system>screen resolution that says "make default for this computer only" seems the system setting was overwriting the nvidia pannel upon startup. Afterwards after restarting i opened the terminal and did sudo nvidia-settings and applied the default refresh rate i wanted to the xorg.conf file, which now overwrites the system preference pannel. Strange but, it works.

---

### Post by Footer on 2007-06-13
> **mynis said:**
> i fixed it myself, didnt even have to edit  xorg.conf.
turns out in the end, all i had to do was check the box in system>screen resolution that says "make default for this computer only" seems the system setting was overwriting the nvidia pannel upon startup. Afterwards after restarting i opened the terminal and did sudo nvidia-settings and applied the default refresh rate i wanted to the xorg.conf file, which now overwrites the system preference pannel. Strange but, it works.

I think I'm suffering from the exact same thing ... But I presume your fix above is for Gnome window manager?  I'm trying to find this same thing in KDE but so far, am striking out.  The Monitor & Display settings under System Settings is as close as I can come but there's no "make default for this computer only" button!

Anyone know the solution in KDE/Kubuntu???  This is driving me nuts!

:(

EDIT:  I found the solution in KDE:  There is a file at ~/.kde/share/config/displayconfigrc that stores special display settings for each user's KDE session.  It's normally adjusted using the utility at K Menu->System Settings->Monitor & Display.  But for some reason, saving the settings there was not working on my system.  So, I just edited ~/.kde/share/config/displayconfigrc and deleted everything under the section beginning with [Screen0] which resolved my problem on subsequent logins (nvidia-settings retained).

---

