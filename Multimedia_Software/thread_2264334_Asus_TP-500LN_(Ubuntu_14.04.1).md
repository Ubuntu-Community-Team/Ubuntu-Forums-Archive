---
title: "Asus TP-500LN (Ubuntu 14.04.1)"
date: 2015-02-06
forum: Multimedia Software
---

### Post by halidrauf on 2015-02-06
Hello,
My laptop contains one combo Headset(L+R+MIC+GND) Jack, but Ubuntu fails to recognize the headset's microphone, it only detects it as an output(headphone) jack. I tried to HdaJackRetask but it fails as well because it doesn't detects the input pin. The hardware works flawlessly on Windows, so it's not a hardware fault.

Note: When I go to my sound settings applet, it shows to inputs who both take signal from the laptop's built in microphone.
I have searched all over the internet and none of the solutions actually worked.

---

### Post by halidrauf on 2015-02-09
I actually found a solution that worked for me and enabled the usual TRRS functionality for my model. 
1. Download HDAJackRetask (available in alsa-tools I think)
2. Select the proper card (for me it was Realtek ALC233)
3. Check Show Unconnected pins.
4. scroll until you see Pin 0x19
5. check override and choose "Microphone". 
6. click on apply, and see if it's working.
7. if it worked, click on "Install boot override".
Thanks in advance, bye!

---

