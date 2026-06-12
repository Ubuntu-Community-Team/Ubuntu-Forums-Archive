---
title: "proprietary nvidia problem with enabling 3d acceleration"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by gdp77 on 2007-04-15
I installed proprietary nvidia drivers + beryl3d. Everything works ok, but i got a minor problem. When I go to system --> administration --> restricted drivers manager I see this :

[[IMG]http://img235.imageshack.us/img235/8361/screenshotuc9.th.jpg[/IMG]](http://img235.imageshack.us/my.php?image=screenshotuc9.jpg)

Then i try to enable 3d and I get :

[[IMG]http://img49.imageshack.us/img49/4369/screenshot1em0.th.jpg[/IMG]](http://img49.imageshack.us/my.php?image=screenshot1em0.jpg)

[[IMG]http://img162.imageshack.us/img162/6479/screenshot2xz3.th.jpg[/IMG]](http://img162.imageshack.us/my.php?image=screenshot2xz3.jpg)

What shall i do to enable 3d acceleration? 

Thank u

---

### Post by tseliot on 2007-04-15
> **gdp77 said:**
> I installed proprietary nvidia drivers + beryl3d. Everything works ok, but i got a minor problem. When I go to system --> administration --> restricted drivers manager I see this :


If you have already installed the nvidia driver then you don't have to use the restricted drivers manager.

---

### Post by gdp77 on 2007-04-15
Then how I enable 3d acceleration?

---

### Post by Compyx on 2007-04-15
Check your /etc/X11/xorg.conf file, in the "Device" section for your video-card, the driver should be "nvidia", like this:
```
Section "Device"
	Identifier	"nVidia Geforce FX-5500"
	**Driver		"nvidia"**
	BusID		"PCI:1:0:0"
EndSection
```

---

### Post by gdp77 on 2007-04-15
I see

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7900 GT/GTO]"
    Driver         "nvidia"
EndSection

My question is why I can't check the "enable" checkbox ?

---

### Post by Compyx on 2007-04-17
You apparently edited your xorg.conf file by hand, so the restricted drivers manager won't touch it. You might still have 3d-acceleration anyway, check the output of:
```
glxinfo | grep 'direct'
```
If you see something like this:
```
compyx@athlonbox:~$ glxinfo | grep 'direct'
direct rendering: Yes
```
You have 3d-acceleration.

I have a hand-edited xorg.cong file, since I needed this line
```
    Option      "AddARGBGLXVisuals" "True"
```
in my "Screen" section to have compiz display window-decorations.

Hope this helps,
Bas

---

### Post by gdp77 on 2007-04-17
Ok thank u. I got "direct rendering : YES" , so I am ok.

---

