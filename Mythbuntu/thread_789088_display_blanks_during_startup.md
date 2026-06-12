---
title: "display blanks during startup"
date: 2008-05-10
forum: Mythbuntu
---

### Post by ctucker10 on 2008-05-10
I've installed Mythbuntu (8.04). It is set up and working. I have my Mythbuntu box connected to a 32-inch LCD TV via its VGA connector. However, when I boot the machine, I see the startup messages as the bootloader does its thing then the display goes blank (the TV displays, "VGA No Signal"). During this time I would normally expect to see linux startup messages quickly scroll by.

After about a minute. the display springs back to life, the XFCE desktop shows up, and the MythTV frontend starts.

I don't think this is a Mythbuntu issue. I noticed this issue when I did a test install of Ubuntu 7.xx several months ago. I have an older NVIDIA graphics card (GeForce 4 MX 440, AGP). I am using the proprietary NVIDIA driver. The screen resolution is set to 1366x768.

I'm pretty sure my graphics card/graphics driver/LCD monitor combination is not "incompatible"...it worked fine (without this startup blank screen issue) with a previous MythTV installation using a different distribution (Mythdora).

Has anyone else seen this problem? Any ideas on how to resolve it?

---

### Post by mrand on 2008-05-10
Does it happen every time?
Could it be fsck running at bootup?

You could try removing "quiet" from the kernel line of /boot/grub/menu.lst.  Maybe also remove the word "splash" from the kernel line as well.

[INDENT]Marc[/INDENT]

---

### Post by ctucker10 on 2008-05-10
@marc

Yes. It blanked out every time until I tried your suggestions. Removing "quiet" from the kernel line in /boot/grub/menu.lst didn't change the symptom. So, I put it back and tried removing "splash".

That did the trick! Evidently there is something about the splash graphic/animation that my setup does not like. Anyway, with that small modification, I get the usual startup messages on screen rather than it going blank.

Fantastic. Thanks.

---

