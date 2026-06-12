---
title: "Terrible problem with Intel driver"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by BilliShere on 2007-10-08
ok i have intel 82945G graphic card. the computer model is hp pavilion a1740n. im running (or attempting to properly run) ubuntu. the monitor im using is a lg 204wt widescreen monitor with 1680x1050 resolution. this resolution works fine under vista @60 hz refresh rate. however i boot up into ubuntu and i get 1280x1024 as default resolution and i cant go any higher than that. i installed the 915resolution fix it worked and i could select the 1680x1050 resolution but this just wont fit on my lcd monitor's screen

It stretches beyond the borders of my monitor. It is interesting to note that my lcd monitor doesnt have a function button to stretch or shrink screen sizes. just one button that auto does it for you (optimal display). there is a button on my monitor to move/shift the screen left and right though. 

what do i do? i uninstalled the 915resolution fix and got the new intel drivers (the modesetting ones? sorry i am new to ubuntu and linux). yet now i boot up and get a black screen with one blue box on my lcd saying "out of range 89hz or summin like...i gues the refresh rate?)

---

### Post by BilliShere on 2007-10-08
anyone help?

---

### Post by RomeReactor on 2007-10-08
Hi. Since I don't have an Intel video card, my only suggestion would be for you to reconfigure your display: press CTRL+ALT+F1; that will leave you in a terminal. Then enter:
```
sudo /etc/init.d/gdm stop
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
When it asks you which video driver to use, select **intel**; otherwise, accept all the defaults. Once that's finished, if the display doesn't start automatically:
```
sudo /etc/init.d/gdm start
```

However, you should probably wait for someone who actually has an Intel video card to comment on your problem before doing this.

---

### Post by BilliShere on 2007-10-08
ok one little improvement after doing what romereactor said...ive got lots of resolutions now. 1680X1050 is listed. i click it and apply it. but it seems the resolution is much bigger than my monitor? the height is fine but the width is bigger than my monitor. the desktop extends beyond the edges of my screen. i keep pressing the auto adjust button on my monitor but it is not resizing it to the so that it fits the screen? anyone know what should i do?

---

### Post by BilliShere on 2007-10-09
ok i went to this website and someone has a lg 204wt flatron monitor as well. i copied the section for monitor (modesetting and what not) into my xorg.conf file...and unlike stampeder on that website i dont use dvi--> i use vga and an intel graphic card. 
[http://www.linuxforums.org/forum/linux-desktop-x-windows/66753-how-run-lg-l204wt-flatron-lcd-monitor-x-windows.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/66753-how-run-lg-l204wt-flatron-lcd-monitor-x-windows.html)

it turns out i still can't get the 1680x1050 resolution to fit my monitors screen! is ubuntu simply not made for widescreen monitors+intel graphic cards combo?  what am i doing wrong. i've tried everything! nothing works.:(

someone please help this is really ruining my ubuntu experience

---

### Post by BilliShere on 2007-10-20
no solutions yet... so now im trying ubuntu 7.10 in virtualbox in windows vista and its running beautifully. and guess what? the widescreen problem doesnt exist anymore (i guess cuz its virtual now?) ive dumped feisty fawn for gutsy gibbon and will be attempting a proper installation on a separate partition soon. If there are any improvements where as this problem will be resolved i shall post about it.

---

### Post by BilliShere on 2007-10-25
WOHOOOO!!! I corrected the problem... everything is soo awesome now!!! I installed ubuntu gutsy gibbon.. then i did this in my xorg.conf file:::

Section "Monitor"
	Identifier	"L204WT"
	Option		"DPMS"
#    HorizSync 28.0-83.0
#    VertRefresh 60
# Only working modelines below
Modeline "1680x1050@55" 140.00 1680 1712 2240 2272 1050 1071 1081 1103
Modeline  "1680x1050@61"   146.25   1680 1772 1948 2204   1050 1053 1059 1089 +hsync -vsync
EndSection

then i also did this: i went to  sudo gedit /etc/modules
opened it in terminal and typed it then 
i added this line to it
"i2c" without the quotations..
this is necessary for edid to work on monitors...which is like extened data id or summin like that.. 

NOW EVERYTHING IS AWESOME WOHOOO!! and im running compiz fusion too with absolutely no problems! took long to solve this problem but i finally did it!
:guitar: :)

---

