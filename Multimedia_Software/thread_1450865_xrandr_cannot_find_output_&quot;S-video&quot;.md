---
title: "xrandr: cannot find output &quot;S-video&quot;"
date: 2010-04-09
forum: Multimedia Software
---

### Post by n-alexander on 2010-04-09
Kubuntu Karmic, ATI card. 

Trying to get s-video work. Ubuntu forums suggest using xrandr, but it does not seem to see it at all:

```
~: sudo xrandr --addmode S-video 800x600
xrandr: cannot find output "S-video"

```

It isn't just --addmode, any command for S-video fails in the same way.

xorg.conf:
```
Section "Device"
    Option "TVDACLoadDetect" "TRUE"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Help appriciated!
Alex

---

### Post by doas777 on 2010-04-09
you may be able to find a hint here:
[http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42](http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42)

---

### Post by n-alexander on 2010-04-10
> **doas777 said:**
> you may be able to find a hint here:
[http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42](http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42)

yes, I have been there. As I said, any xrandr command for S-video fails in the same way. It doesn't seem to know I have S-video at all. 

```
~: xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1280
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1024x768       85.0*+   85.0*    75.0
   1280x1024      85.0     75.0
   800x600        85.1     75.0
   640x480        85.0     75.0     59.9
   720x400        70.1
DVI-0 disconnected (normal left inverted right x axis y axis)


```

---

