---
title: "Fglrx problems"
date: 2006-01-30
forum: Multimedia &amp; Video
---

### Post by mushroom on 2006-01-30
I have an ATI Radeon 9000 card, and if I use the fglrx driver, problems arise. When I'm using the composite extension, nothing's coherent, everything's garbled and impossible to make out. Without the composite extension, only GDM is garbled, but everything else is crystal clear. However, TV Time and Totem do not work. When I use the ati driver, all of these problems are alleviated, but I still want 3D to work.

Help would be much appreciated.

---

### Post by mushroom on 2006-01-30
bump

---

### Post by Horndog on 2006-01-30
Try this: [http://ubuntuforums.org/showthread.php?p=423589]("http://ubuntuforums.org/showthread.php?p=423589")

---

### Post by mushroom on 2006-01-31
When installing the driver as described, I got an error message that started with this:

extension "XFree86-DRI" missing on display ":0.0".

When I installed the driver with dpkg-reconfigure, it worked, but with the same problems as before.

---

### Post by newuser111 on 2006-01-31
forget about composite support on fglrx drivers, it will disable 3d acceleration if enabled, and it just caused lockups when i tried it

i guess we can only hope in the future ati attempts to make some decent drivers

just run sudo dpkg-reconfigure xserver-xorg and select fglrx

and after that edit /etc/X11/xorg.conf and add these lines under the device section to enable XV support if you want it

	Option 		"VideoOverlay" 		"on"
	Option 		"OpenGLOverlay" 	"off"

---

### Post by mushroom on 2006-01-31
That fixed video, but composite and a coherent GDM are going to be hard to let go.

---

