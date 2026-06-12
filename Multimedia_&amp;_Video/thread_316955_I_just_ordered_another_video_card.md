---
title: "I just ordered another video card"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by Olav on 2006-12-11
I just ordered this video card: [http://www.asus.com/products4.aspx?l1=2&l2=7&l3=140&model=484&modelmenu=1](http://www.asus.com/products4.aspx?l1=2&l2=7&l3=140&model=484&modelmenu=1)

If all goes well, it will arrive later this week. Hopefully, it will crash less often than my old Hercules 3d Prophet 8500, wich is an ATI Radeon 8500 LE (R200 QL) based card. It was never adequately supported by the fglrx drivers. I don't need super fast 3D because I'm not a gamer, but I do want to use Beryl (or Compiz) *and* be able to watch TV on my computer. Finally.

So, if someone has anything to say about the **Asus N6200 TD** I want to hear it ;)

---

### Post by adaptr on 2006-12-11
It should do fine.
I'm running Beryl on a Geforce FX 5200 - older and slower than your 6200, on an Athlon XP 1700+ with 512MB, and it is most acceptable.
I have my 1280x1024 screen set to 85Hz refresh, and Beryl is set to the same.
Those animations are smoooov.

---

### Post by Olav on 2006-12-11
Thanks, I'm looking forward for it.

Of course, I did a *bit* of study before ordering this card. But it is still a leap of faith, kind of.

And I said I do not need exceptional 3D performance but now that I think of it, I surely would like decent movement in Google Earth and applications like that. And who knows, if this card does actually work like advertised, what other applications I will find that will make proper use of it :)

---

### Post by rejser on 2006-12-11
Running world of warcraft absolotely fine, 1280*1024 all settings on medium (saw that you wern't a gamer, but if you get into the mood sometime).
It handles blender superbly. 
Google earth will work fine, at least it does on my puter. 
It handles blender better than the rest of my computer.

---

### Post by Olav on 2006-12-11
> **rejser said:**
> Running world of warcraft absolotely fine, 1280*1024 all settings on medium (saw that you wern't a gamer, but if you get into the mood sometime).
It handles blender superbly. 
Google earth will work fine, at least it does on my puter. 
It handles blender better than the rest of my computer.
Glad to see you are so satisfied with it. Makes me feel like I probably made the right choice. Of course, when I picked this card, I was also thinking about how silent it would be and how little power it would consume. I think this card may be a winner, if it can do that and still be a good performer at a very reasonable price.

It is true I am not a gamer but that is only because I have put that more or less behind me... I did like the original Doom and Duke Nukem in the MS-DOS era.

---

### Post by jornahow on 2006-12-11
I'm running Beryl on an Nvidia 7300GS with 512m, using the nvidia 9742 beta driver.  It was not an expensive card, but Beryl works flawlessly - perfectly smooth with no performance degradation that I can see over metacity.  All my apps work fine.

jornahow

---

### Post by zetetic on 2006-12-12
Can you please tell me if the Asus N6200 TD has free open source drivers?

thanks
zetetic

---

### Post by Olav on 2006-12-20
> **zetetic said:**
> Can you please tell me if the Asus N6200 TD has free open source drivers?
Of course there is the "nv" driver, that will probably work. But it does not provide 3D so I did not even bother to try.

---

### Post by Olav on 2006-12-20
In case anyone wondered (guess not... :cool:):

The Asus card works like expected - nothing too fast, probably stinks for serious games, but very silent indeed (no wonder since there are no fans). I am using the nvidia proprietary binary driver that comes with Edgy. It provides me with a very smooth normal desktop with no crashes so far, and the possibility of using 3D applications and games (screensavers, finally!). Or even a 3D accelerated desktop with GLX+Beryl. I may look a bit deeper into the latter next week, but I can confirm that it does work.

I used this to install the driver: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) (method 1, very easy)
and this for GLX+Beryl: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL) (also very easy, but you have to read carefully).

---

### Post by pnix on 2006-12-25
I have one in my box. It work fine with nv driver(default from Dapper installation). I try many way to install nvidia driver but never work, it just give me black screen when gdm start. If you can make nvidia driver work please give me your xorg.conf.

---

### Post by Olav on 2006-12-26
> **pnix said:**
> I have one in my box. It work fine with nv driver(default from Dapper installation). I try many way to install nvidia driver but never work, it just give me black screen when gdm start.
All I actually did (based on the howto mentioned above) was install the nvidia-glx package and run the command "nvidia-xconfig --no-composite" to configure my xorg.conf. Very easy.

> If you can make nvidia driver work please give me your xorg.conf.

Sure, no problem at all. Not sure if this will help you though, because I really did nothing special. I just removed the lines concerning wacom, stylus and such - they are things I will probably never use.

```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
    Option         "XkbVariant" "intl"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

---

