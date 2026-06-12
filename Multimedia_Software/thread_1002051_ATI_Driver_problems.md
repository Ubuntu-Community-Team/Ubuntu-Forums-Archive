---
title: "ATI Driver problems"
date: 2008-12-04
forum: Multimedia Software
---

### Post by sandyd on 2008-12-04
When i installed the ati driver using envyng, i noticed that the compiz effects had black spots in it that would flicker. I tried installing the driver from the ati website. After i installed it, it still didn't work. Instead, because i hadn't remembered to remove the envy driver, it crashed X and it can't start up anymore. How can i remove one of the drivers?

---

### Post by avianbc on 2008-12-04
If you can control-alt-backspace and get to a login screen, you can choose options -> Gnome failsafe to get back to a GUI to fix it. If not, you better be ready for some ugly command line work.

> C) What happens if you are no longer able to access your Desktop Environment (because of a blank screen at boot)?

Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line). Then you will need to type:
envy --uninstall-all

then simply type:
reboot

and boot as usual. On next reboot the Xserver should work fine (but you will use the open source driver) 

^From [http://www.albertomilone.com/envyfaq.html#C](http://www.albertomilone.com/envyfaq.html#C)

EDIT: I also had the black flickering problem with the envy driver. I fixed it by adding a few lines to my xorg.conf under the device section:

	Option		"XAANoOffscreenPixmaps"
	Option		"OpenGLOverlay"	"off"
	Option "TexturedVideo" "on"

---

### Post by IQRules on 2008-12-04
Go to rescue mode, chroot /target and apt-get remove driver

---

### Post by sandyd on 2008-12-04
Thanks sooo much!:D That fixed the problem!

---

