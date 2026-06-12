---
title: "Trouble logging into mythbuntu - frozen splash screen"
date: 2011-08-18
forum: Mythbuntu
---

### Post by phyllis_ave on 2011-08-18
Hi All,

This is my first go at using any linux OS and Mythbuntu was recommended to me so I thought I'd give it a try, but I'm having some problems getting it set up on my new HTPC.

I downloaded the 64bit ISO from [http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads) and installed it on the new system.

Once the install finished it told me to remove the cd and press enter to restart. Now every time the machine boots it just freezes on the purple splash screen with the mythbuntu logo and the 5 orange dots.

The only response I can get is from pressing ctrl+alt+del which restarts the system.

Any idea what could be causing this?

System specs:

CPU: AMD A8-3850 - stock cooler
Mobo: Asrock A75M-HVS
RAM: Corsair 1600 2x2GB
HDD: WD 2TB Green
ODD: LiteOn DVD
Case: Antec NSK2480B
PSU: Antec Earthwatts 380W
Tuner: Leadtek DTV2000DS

---

### Post by thatguruguy on 2011-08-18
Are you able to run it as a LiveCD?

---

### Post by nickrout on 2011-08-18
At the splash screen press the <esc> key and a text screen with error messages should come up. Report back the last few messages to us.

---

### Post by phyllis_ave on 2011-08-18
@thatguruguy
Yes I can run the LiveCD fine - that's when you go to the Run Mythbuntu without installing option yes? It brings up the desktop with the message in the middle of the screen saying double click on Install to install Mythbuntu permanently.
 
@nickrout
I'll see what error messages I'm getting tonight and write back.
 
Also when starting up I have noticed an error coming up about USB firmware not being found. The only USB device I have is a mouse and the error still comes up when I try to boot with it disconnected.
 
I have also tried re-installing a few times and have tried without the tuner card in and with a different HDD, which made no difference.

---

### Post by klc5555 on 2011-08-19
> **phyllis_ave said:**
> 
 
I have also tried re-installing a few times and have tried without the tuner card in and with a different HDD, which made no difference.

If you're already into the hardware-pulling stage, check also whether you've got a (NVidia or ATI) video card installed in addition to the Asrock A75M-HVS's embedded graphics (whatever they are). There have been hints that in some failed cases with a secondary video card AND embedded graphics, an installation may succeed if the secondary card is pulled, the install goes onto the embedded graphics with the open-source video drivers, and after this setup is booted, the secondary video card is reintroduced to the system and the proprietary drivers installed.

Lacking any additional information I'd initially suspect that the startup is failing when the Xserver is initializing. This could be confirmed by holding down the escape key at boot, and going into the grub boot menu. In choosing the "recovery" option, you'd eventually be confronted with a menu that would (among other options) allow you to choose booting to a (text-mode) root prompt. If you get to a root prompt at all, you'd know that the OS and hardware driver load were basically all right. If from the root prompt you'd try to start the graphical shell manually by the command "startx" (no quotes) and the Xserver hangs or crashes back to the prompt, you could start debugging from there, whether it's video graphics drivers or something else.

---

### Post by phyllis_ave on 2011-08-21
So I finally got it going.
 
Turns out the AMD video driver that comes with the Mythbuntu install doesn't work with the A8-3850 integrated graphics.
 
I got it working by installing with the default driver and then running the Proprietary Display Driver - [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
 
Just thought I'd post up how I fixed it in case anybody else is having the same problem.
 
Thanks for all the help guys.

---

