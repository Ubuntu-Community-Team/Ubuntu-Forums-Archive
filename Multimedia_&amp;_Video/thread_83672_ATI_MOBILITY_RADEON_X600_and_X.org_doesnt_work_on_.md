---
title: "ATI MOBILITY RADEON X600 and X.org doesnt work on Breezy"
date: 2005-10-29
forum: Multimedia &amp; Video
---

### Post by infinito on 2005-10-29
Hello,

I was using Hoary without any problem, when 2 days ago i upgraded to Breezy. The upgrade was perfect, but after reboot, X couldn't be started. So i tried booting with the LiveBreezy CD, but the problem is still there. No X.Org.

I'm using a HP nx8220 laptop with a ATI Mobility Radeon X600 inside.

Could anyone tell me whats going on?
Here's my Xorg.0.log (couldn't paste here): [http://infinito.f2o.org/downloads/Xorg.0.log](http://infinito.f2o.org/downloads/Xorg.0.log)

Hope someone can give some light on this issue....
Thanks!

---

### Post by lawi on 2005-10-31
I had to update my xorg driver with  xorg-driver-fglrx

---

### Post by snow-man on 2005-11-08
"Xorg-debug" worked for me :)

---

### Post by lik3n on 2005-11-08
I had that problem on my laptop while I was trying to do an install.

I put up my way of getting it to work on my blog. I didn't think me doing that would actually come in handy.


[http://worldclock.blogspot.com](http://worldclock.blogspot.com)

---

### Post by Daiver on 2006-01-27
Can you link to the specific post? I can't seem to find it.

---

### Post by deusdeceptor on 2006-02-14
I had the same problem and solved it like this.

Downloaded the ATI Linux driver installer from here.
You will need the ATI Driver Installer, not the seperate XFree86/X.org rpm packages.
[https://support.ati.com/ics/support/KBList.asp?folderID=356](https://support.ati.com/ics/support/KBList.asp?folderID=356)

Then change directory in a console to where the downloaded installer is and do following commands (<version> must be replaced with the correct one):

sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper
chmod +x ati-driver-installer-<version>.run
fakeroot ./ati-driver-installer-<version>.run

Choose "Generate distribution specific packages" and "Ubuntu" and the Ubuntu version you use. 5.10 or Breezy that is.
Continue with:

sudo dpkg -i *.deb
sudo module-assistant build,install fglrx-kernel

I did the aticonfig and after that corrected the resolution in /etc/X11/xorg.conf to only "1680x1050" under "Section". Answer the default value to the things you don't understand during aticonfig

Also I had to change the font path in xorg.conf to:

	FontPath     "/usr/share/X11/fonts/local/"
	FontPath     "/usr/share/X11/fonts/misc/"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1/"
	FontPath     "/usr/share/X11/fonts/Speedo/"
	FontPath     "/usr/share/X11/fonts/75dpi/"
	FontPath     "/usr/share/X11/fonts/100dpi/"

Not to sure if you have to do this but my xemacs demanded it.

Reboot and enjoy accelerated 1680x1050! :D

---

### Post by Daiver on 2006-02-14
Did you ever have a problem with a "screen not found" error message?

---

### Post by deusdeceptor on 2006-02-15
Nope. Have you tried aticonfig? That should generate a xorg.conf that works.

---

