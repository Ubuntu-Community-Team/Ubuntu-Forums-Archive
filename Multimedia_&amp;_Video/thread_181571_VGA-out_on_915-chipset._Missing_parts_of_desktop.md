---
title: "VGA-out on 915-chipset. Missing parts of desktop"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by brsseb on 2006-05-24
Im using Ubuntu on my Dell Latitude X1 laptop, which for the most part works great. But i want to use it together with my external LCD screen, a Dell 24" (2405) using VGA-out. Ive found the correct modeline for my screen (its taken from the correct monitor specs) and ive set it up in xorg.conf. Ive also used 915resolution patch to change the VBE-modes:

```

# For internal LCD
915resolution 3c 1280 768

# For external LCD
915resolution 32 1920 1200

```

So now the (virtual) BIOS should be ready for business. The internal LCD-screen works perfect with its 1280x768 resolution. 

Problem is when i boot with the external display, i get a 1920x1200 image, but with the rightmost part of the image off-screen. See the pictures below. 

[IMG]http://home.online.no/~bjoseb/x11/1t.JPG[/IMG][IMG]http://home.online.no/~bjoseb/x11/2t.JPG[/IMG]
[IMG]http://home.online.no/~bjoseb/x11/3t.JPG[/IMG][IMG]http://home.online.no/~bjoseb/x11/4t.JPG[/IMG]

The image quality is also somewhat out of focus, indicating that the image is streatched to some degree. Im also including my Xorg.conf and my Xorg.log file:

[http://home.online.no/~bjoseb/x11/xorg.conf  (xorg.conf)]("http://home.online.no/~bjoseb/x11/xorg.conf")
[http://home.online.no/~bjoseb/x11/xorg.0.log (xorg.0.log)]("http://home.online.no/~bjoseb/x11/xorg.0.log")

Please, this is the only thing left to fix before i can finally start using linux on a daily basis. Ive tried for quite some time now to get VGA out working, and im soo close now. Thankz :cool:

Edit: Also, videos are not working on the external screen, only on the internal. I just get a black image with sound.

---

### Post by Sef on 2006-05-25
What graphics card do you have?  Thinking that this is a problem with something with the graphics not right.

---

### Post by brsseb on 2006-05-25
Its using the laptops built-in Intel GMA915GM/GMS-graphic card which uses shared memory with the rest of the system. (Windows calls the graphics chip: Intel 915GM/GMS, 910GML Express Chipset. The VGA-out works perfect in Windows, of course. So its not like the laptop isnt capable of using 1920x1200 resolution).

---

### Post by brsseb on 2006-05-29
Update: Hitting PrintScreen and saving the image, i get a perfect 1920x1200 image. So the VGA is sending out a proper 1920x1200 image, but the monitor wont display it right. Then it MUST be the modeline settings then?

Please help. I really need to get it working!

Edit:

This is the modeline, with its values pulled from other web sites about my monitor. But if the image is too wide, which of the following settings do i need to adjust to scale the image further? 

> Modeline"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235 +HSync -Vsync


EDIT:

Studying the xorg.0.log-file linked above, i found these two lines kinda interessting:

> (II) I810(0): Increasing the scanline pitch to allow tiling mode (1920 -> 2048 ).
(--) I810(0): Virtual size is 1920x1200 (pitch 2048 )

Can this have altered the modeline Ive set up and caused the laptops VGA to send out a wider image signal, 2048 "pixels" instead of 1920?

---

### Post by brsseb on 2006-05-31
Ok, im closing in on the actual problem:

> Modeline"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235 +HSync -Vsync

For the monitor to work in perfect 1920x1200@60hz, the pixel clock MUST be 154 dead on. But using the above modeline, which explicitly say i want 154MHz, results in the monitors clock being 193-194Mhz instead! Thats why i get the distorted picture! 

But i asked for 154MHz. Its not ignoring my modeline, since if i change any setting in it, it results in either a "cannot display this mode"-error, x crash, or just a more distorted image. 

Does anyone know why im not getting my desired pixelclock?

---

### Post by VinylPusher on 2006-06-08
This might be a very very daft suggestion - apologies, but I don't know your level of familiarity with the 2405!

Have you tried pressing the '+' button on your monitor? Only I noticed you were connecting your laptop via D-SUB (due to lack of DVI) and the Dell will sometimes make a wrong guess at the picture dimensions. Pressing + generally fixes the problem.

Again, apologies if this is insultingly simple - perhaps others reading the thread might find it useful ;)

---

### Post by brsseb on 2006-06-08
[QUOTE=VinylPusher]This might be a very very daft suggestion - apologies, but I don't know your level of familiarity with the 2405!

Have you tried pressing the '+' button on your monitor? Only I noticed you were connecting your laptop via D-SUB (due to lack of DVI) and the Dell will sometimes make a wrong guess at the picture dimensions. Pressing + generally fixes the problem.

Again, apologies if this is insultingly simple - perhaps others reading the thread might find it useful ;)[/QUOTE]

Yeah, ive tried the auto-adjust-feature. What happens is kinda odd, the image shakes and streacthes the image even further, and the result is a 1600x1200@60-resolution image (ive checked in the monitor control panel). 

The problem seems to be that the monitor ALMOST get 1920x1200 running ok, but anything, even hittig autoadjust, changing inputs or turning the monitor on and off during the prosess results in the same thing -> back to 1600x1200@60 again, with useless image size and quality.

You wont belive how frustrating this is.. :(. Seems that the remedy is a laptop with a DVI-port). 

Ive even read every last bit of documentation there is for the 2405, and hard-coded the proper values needed to run 1920x1200.

---

### Post by VinylPusher on 2006-06-08
Erm, I can't find a definitive description of the 'Modeline' keyword, but I have a sneaking suspicion that you don't enter the pixel clock as the first argument, I think you should be entering a figure of 74, relating to the horizontal frequency.

**EDIT**

According to one online modeline calculator (and contrary to my thoughts above!) your modeline should read:

Modeline "1920x1200" 204.95  1920 2024 2272 2744  1200 1200 1203 1244

**EDIT2**

I think the Dell documentation may be incorrect. It lists 1600x1200 @ 60Hz as requiring a dot clock of 162.0MHz. How can 1920x1200 @ 60Hz require a lower clock? Doesn't make any sense.

---

### Post by brsseb on 2006-06-08
Thanks for the reply VinylPusher, but it didnt work. With 74 i got "cannot display this mode", with 204.95 X does something funny: It sets the desktop resolution to 1920x1200, but runs it inside a scrollable 1280x1024-window (the monitor reports 1280x1024@75). 

All the Xorg logs as well as the Dell docs reports that the pixelclock should be 154. But if its correct...who knows. Anyhow, when I start X with the modeline im using, it says 154 but the monitor tells me im looking at 194MHz (its shown in red font in the monitor control panel, inicating thats its out of the monitors limit, which is a pixelclock of around 170-ish MHz).

So, all the data ive set up are correct according to the monitors spec, but somehow X, Dell or both messes up and uses 194 as the pixelclock!

Edit: Here are the manual with most of the specs:

[http://support.euro.dell.com/support/edocs/monitors/2405fpw/no/about.htm#Specifioications]("http://support.euro.dell.com/support/edocs/monitors/2405fpw/no/about.htm#Specifioications")

---

### Post by mjukr on 2006-06-09
brsseb,

I'm having the EXACT same problem with a different setup (i945gm chipset with a Sharp LC-37D7U LCD Display). My modeline, etc. look fine but there's just a bit of the screen that runs off the edges.

I understand your frustration!!! I've been banging my head against my desk for a couple of days trying to get it to work. Not much good information out there and these problems.

Good luck, and please post back if you get it working, and I'll do the same.

---

### Post by brsseb on 2006-06-10
Nice to know Im not the only one. Im starting to wonder if this is all X`s fault, that there is some sinister bug that makes it put out the wrong signals on the VGA-port different than the stuff given in the modeline. Maybe the combination with "troublesome" displays with odd screen resolutions confuses X. 

I have now installed Ubuntu on my desktop PC too, using DVI only and a GeForce 7800GTX. It found the 1920x1200 resolution on hte first boot, didnt have to do anything, and the picture is as sharp as in Windows. I looked though its Xorg.0.logfile and found it pretty much deteced the same values for pixelclock, v/hsync, etc (and all the values that makes up my current modeline). 

Would be a shame to have to give up on my lovely X1-laptop just to get one with a DVI-out (where i *belive*, but aint certain, it will work)..

---

### Post by mjukr on 2006-06-12
Unfortunately, mine *does* use a DVI connection, and still I have the problem :(

---

### Post by brsseb on 2006-06-12
Then if it works fine under Windows, as it does for me, it must be some sort of weird bug in the X system. Perhaps we should file a bug report somewhere..but im not sure how to properly describe the bug.

---

### Post by mjukr on 2006-06-14
I'm wondering if it might be the i810 driver in X.org that's the problem. I need to check and see if Intel offers a proprietary driver for linux for the 945GM onboard video controller. Maybe that will work?

---

### Post by brsseb on 2006-06-14
[QUOTE=mjukr]I'm wondering if it might be the i810 driver in X.org that's the problem. I need to check and see if Intel offers a proprietary driver for linux for the 945GM onboard video controller. Maybe that will work?[/QUOTE]

Do that, and tell me if it did something good. 

Btw, have you tried using the "vesa" driver instead of i810. Its not as good in performance, but might be good to test it and see if it does anything too aliviate the resolution problem.

---

