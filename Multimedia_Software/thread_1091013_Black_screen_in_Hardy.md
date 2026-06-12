---
title: "Black screen in Hardy"
date: 2009-03-08
forum: Multimedia Software
---

### Post by snakep on 2009-03-08
Hello,

I am having some difficulties with my display.  It periodically goes black, and then flashes as if it is in power saver mode and unsuccessfully trying to return to normal display.  It alternates between completely black and just dark every second or so.  A box shows up that says "no signal", as it does during a reboot.  The only way I can stop this behavior is to force the computer to power down.  I cannot notice any pattern of actions that might cause this behavior.  Sometimes it happens when I am using firefox, sometimes when I click something on the desktop.

My video card is a Radeon 9800XT.  I am using the proprietary driver (I believe).  The package is installed, and is listed in my xorg.conf, but when I click on System->Administration->Hardware Drivers, the box next to the ATI driver is not checked.  When I try to click it, I get a message that a restart is needed, but restarting doesn't change anything.

Does anybody have an idea what the problem is?

Thanks,

Jeremiah

---

### Post by snakep on 2009-03-10
Bump.

---

### Post by snakep on 2009-03-11
Well, I figured out the problem, and it has nothing to do with software.  It turns out the fan on my video card is broken, and the card has been overheating.  Part of the problem is that, due to the way the motherboard is installed in the case, the video card seems to be upside down.  By this I mean that the fan and heat sink are on the bottom side of the card.  The fan blade seems to have fallen off.  I think that if it were oriented differently, the heat sink would be enough to cool the card, but on the underside it is ineffective.  

Anyway, I've cleaned the case fans and intakes, and the whole machine seems to be running a little cooler.  This might work for the time being.  I have also installed the lm-sensors package to try to keep an eye on it.  Does anybody know if the Radeon 9800 Pro has a temperature sensor?  I see a temperature reported for the motherboard and the CPU, and there is a Temp3 as well, but I don't know if that is the video card or something else (power supply?).

---

