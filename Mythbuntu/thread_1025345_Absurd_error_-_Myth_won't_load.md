---
title: "Absurd error - Myth won't load"
date: 2008-12-30
forum: Mythbuntu
---

### Post by shang1 on 2008-12-30
Hey guys,
I'm trying to get mythbuntu up and running and I have a really strange error. When I try to load my install I get a "low graphics mode" error, I select automatically detect, computer restarts back to the exacts same screen.

I tried to edit the xorg server using the terminal but no luck. Any ideas on how to fix it? Nay make it boot..

Thanks.

---

### Post by maxim99 on 2008-12-30
If you can get to a terminal post up the tail of /var/log/Xorg.0.log

tail -20 /var/log/Xorg.0.log

That should help us figure out why Xorg thinks something is wrong.

If 20 lines isn't enough to provide some sort of error message increase it to 30 or so.

Do you know the chipset of the video card in your system? Nvidia, ATI, Intel, Other?

Also info about the monitor would be nice, in addition try a spare Monitor cable as it could be a problem with the cable itself preventing X from retrieving EDID information from the monitor. Also make sure the monitor is turned on before X starts otherwise it can't pull the EDID info.

---

### Post by shang1 on 2008-12-30
Ok, I will post the log in a moment. The weird thing is it works fine on an old CRT monitor. However it doesn't work on my current 24inch benq monitor or the 40inch tv im trying to hook it upto. However, when I load it from the CRT monitor, then change the cables over to the TV it works fine. Odd..?

I even reinstalled the OS using the TV as the monitor, and still get the same error. I will go and retrieve the logs now.

Also the video card is an old nvidia.

EDIT:
shang1@myth:~$ tail -20 /var/log/Xorg.0.log
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"

---

