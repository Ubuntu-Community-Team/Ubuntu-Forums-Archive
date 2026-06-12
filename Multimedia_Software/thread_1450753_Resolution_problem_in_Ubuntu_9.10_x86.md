---
title: "Resolution problem in Ubuntu 9.10 x86"
date: 2010-04-09
forum: Multimedia Software
---

### Post by Ronen444 on 2010-04-09
[SIZE=3]Hello, this is my first thread in the Ubuntu Forums!

Anyways, installed **Ubuntu 9.10 x86** on a dual-boot with Windows XP from a USB-Key I created using the utility that pendrivelinux.com provides.

So, Ubuntu detects that the optimal resolution for my screen in **1440x900**, which is correct, but I can't stand that resolution (too small for me, go figure). **My monitor is a Hyundai X93W**A and my **graphics adapter is a built-in (to the motherboard) NVIDIA GeForce 6150SE.**

Now, I want 1280x800, which works in Windows quite well. So, I add the mode "1280x800" to xrandr (--newmode), however when I try to set it using this command:

xrandr --addmode default --mode 1280x800_60.00

xrandr throws an error that contains "crtc 0 failed". "Default" is how Ubuntu detects my monitor, I guess, because this name appears when I type "xrandr".

How do I solve this "crtc 0" error? I updated to the latest kernel (2.6.20, I think) and I have the latest NVIDIA drivers... I searched a lot through google, but I haven't found anything useful... :(

Help, please...? :confused:
[/SIZE]

---

### Post by WinterRain on 2010-04-09
Undo what you did in xorg.conf, and do
```
gksudo nvidia-settings
```
You will be able to change resolutions there.

---

### Post by Ronen444 on 2010-04-09
> **WinterRain said:**
> Undo what you did in xorg.conf, and do
```
gksudo nvidia-settings
```You will be able to change resolutions there.

[SIZE=3]That's the problem - I don't have 1280x800 in the NVIDIA X Server Settings window....

Any way to do a custom resolution from the NVIDIA utility..?
[/SIZE]

---

### Post by WinterRain on 2010-04-09
> **Ronen444 said:**
> [SIZE=3]That's the problem - I don't have 1280x800 in the NVIDIA X Server Settings window....

Any way to do a custom resolution from the NVIDIA utility..?
[/SIZE]

I don't think so. Have you tried 1280x960 in the utility?

---

### Post by Ronen444 on 2010-04-10
> **WinterRain said:**
> I don't think so. Have you tried 1280x960 in the utility?

[SIZE=3]Yes - but unfortunately, it is 4:3, and I need a resolution that is 16:10. The instruction manual says that the monitor also supports 5:4, however 1280x1024 looks weird (I don't know how to explain it - but it's kind of "stretched")...

So, any other ideas...?
[/SIZE]

---

### Post by WinterRain on 2010-04-10
Have you tried editing your xorg.conf file?

---

### Post by Ronen444 on 2010-04-11
> **WinterRain said:**
> Have you tried editing your xorg.conf file?

[SIZE=3]Ummm...
Well, I tried something using a guide I found on google, but it didn't work...

Can you tell me (or direct me to) some way to edit the xorg.conf file..? I'm not sure how to do this. I seem to have a non-standard NVIDIA xorg.conf...
[/SIZE]

---

### Post by WinterRain on 2010-04-11
> **Ronen444 said:**
> 
Can you tell me (or direct me to) some way to edit the xorg.conf file..? I'm not sure how to do this. I seem to have a non-standard NVIDIA xorg.conf...

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Ronen444 on 2010-04-12
> **WinterRain said:**
> ```
gksudo gedit /etc/X11/xorg.conf
```

[SIZE=3]Looks like I didn't express myself correctly - **I know how to edit the xorg.conf file! **I'm asking of a way to edit a **non-standard NVIDIA-based xorg.conf file**, because it is different from a normal xorg.conf...
Besides, why are you the only one who is trying to help me..? I have seen many people in this forum... is my problem that weird...?
[/SIZE]

---

### Post by thundre on 2010-04-12
Non-availability of supported resolutions is a problem I haven't seen before, or at least I haven't noticed.  My only suggestion for that is to try different (newer) versions of the Nvidia driver, just in case the chipset is new.  Unlikely.

But maybe I can help with another suggestion.

Your real problem is that the **text** is too small, right?  You can change it under System->Preferences->Appearance->Fonts.  Some applications (like Firefox) have their own font size preference, accessible from the Preferences dialog inside the app.

---

### Post by Ronen444 on 2010-04-12
> **thundre said:**
> Non-availability of supported resolutions is a problem I haven't seen before, or at least I haven't noticed.  My only suggestion for that is to try different (newer) versions of the Nvidia driver, just in case the chipset is new.  Unlikely.

But maybe I can help with another suggestion.

Your real problem is that the **text** is too small, right?  You can change it under System->Preferences->Appearance->Fonts.  Some applications (like Firefox) have their own font size preference, accessible from the Preferences dialog inside the app.

[SIZE=3]First of all, I must say that I tried the 190 version and the 185 (available from the update manager). Both still don't show 1280x800... Weird...

I'll try what you said about the text size - I'll also try to install an older version of the driver (93, or something, I don't remember), I'll edit this message if it helped!
[/SIZE]

---

### Post by Ronen444 on 2010-04-13
> **Ronen444 said:**
> [SIZE=3]First of all, I must say that I tried the 190 version and the 185 (available from the update manager). Both still don't show 1280x800... Weird...

I'll try what you said about the text size - I'll also try to install an older version of the driver (93, or something, I don't remember), I'll edit this message if it helped!
[/SIZE]

[SIZE=3]Well, I could resize the text, but... I don't really know how to explain this, but all of the text is too... "Sharp", I guess...

BTW, Installed the oldest version of the driver, and still no 1280x800!!! Grrr, what's so special about that resolution?!

[/SIZE]

---

### Post by Ronen444 on 2010-04-15
[SIZE=3]Bump.[/SIZE]

---

### Post by Ronen444 on 2010-04-16
[SIZE=3]Bump :(.[/SIZE]

---

### Post by Ronen444 on 2010-04-17
[SIZE=3]Bump... :confused:[/SIZE]

---

### Post by Ronen444 on 2010-04-18
[SIZE=3]Still bumping...

I can't believe I'm actually saying this, but I really consider rolling back to Windows...
[/SIZE]

---

### Post by Mach1723 on 2010-04-18
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       20.0 - 70.0
    VertRefresh     20.0 - 70.0
    Option         "DPMS"
EndSection
```In your xorg.conf have you tried changing the HorizSync and VertRefresh to what your monitor supports(according to google 75hz) that makes all the resolutions my monitor supports available(as long as you dont set 70.0 - 70.0).

EDIT: You also have to restart your xserver with "sudo service gdm restart" , after making edits.

---

### Post by Ronen444 on 2010-04-18
> **Mach1723 said:**
> ```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       20.0 - 70.0
    VertRefresh     20.0 - 70.0
    Option         "DPMS"
EndSection
```In your xorg.conf have you tried changing the HorizSync and VertRefresh to what your monitor supports(according to google 75hz) that makes all the resolutions my monitor supports available(as long as you dont set 70.0 - 70.0).

EDIT: You also have to restart your xserver with "sudo service gdm restart" , after making edits.

[SIZE=3]Thanks, but seems like it's not enough:

1. I edited the xorg.conf file exactly as you told me to (changed HorizSync and VertRefresh to 20.0 - 75.0), and still no 1280x800.

2. So, I went to xrandr, tried to add the mode manually, and still the same problem:

[/SIZE]> xrandr: crtc 0 failed

[SIZE=3]I used "cvt 1280 800 75" to get the modeline...

Back to the start... Thanks for trying, though...
Anything else? Anyone?
[/SIZE]

---

### Post by Ronen444 on 2010-04-19
[SIZE=3]Why do I always have to bump?! :confused:[/SIZE]

---

### Post by Ronen444 on 2010-04-20
[SIZE=3]Bump.... :([/SIZE]

---

### Post by Ronen444 on 2010-04-21
[SIZE=3]Thanks to anyone who tried to help me. Guess I'll have to run Linux under a Virtual Machine, because I don't think, and I'll never think of, buying a new monitor, and I don't really want to bump all the time.

There is absolutely no reason to keep this thread open, only so I can bump it more. Bottom line - _**please lock**_.
[/SIZE]

---

