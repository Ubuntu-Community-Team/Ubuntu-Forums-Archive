---
title: "Mangled Fonts"
date: 2009-05-20
forum: Multimedia Software
---

### Post by fatboab on 2009-05-20
I managed to get my dual screen setup working buy turning off the on-board ATI Rage XL video and sticking the second monitor onto the DVI output of the Radeon card. A quick modification of the xorg.conf file resulted in dual screen (unless I open RandR when it then decided to go back to being single screen).

Anyway, the result of all of this is that the fonts are now mangled in most applications, see the screen shot.

[IMG]http://bobarnott.com/temp/kubuntu-fonts.png[/IMG]

Does anyone know what I have to do to get the fonts rendering correctly...? My xorg.config is:

```
Section "Device"
        Identifier      "Radeon 7000"
        Driver          "radeon"
        Option          "Monitor-VGA-0" "Monitor A"
        Option          "Monitor-DVI-0" "Monitor B"
EndSection

Section "Monitor"
        Identifier      "Monitor A"
EndSection

Section "Monitor"
        Identifier      "Monitor B"
        Option          "LeftOf" "VGA-0"
EndSection

Section "Screen"
        Identifier      "Dual Screen"
        Monitor         "Monitor A"
        Device          "Radeon 7000"
        Subsection "Display"
                Virtual         2560 1024
        EndSubSection
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
```

Cheers,

-- 
Bob.

---

### Post by psyke83 on 2009-05-20
Disable KDE4's compositing (your chipset is old, so I presume it's doing XRender compositing, which may be causing the corruption issues).

Unfortunately I don't have KDE4 installed at the moment, so you'll need to hunt for the location of that option yourself (it's in the Display/Appearance preferences, or something like that).

---

### Post by fatboab on 2009-05-20
> **psyke83 said:**
> Disable KDE4's compositing (your chipset is old, so I presume it's doing XRender compositing, which may be causing the corruption issues).

Unfortunately I don't have KDE4 installed at the moment, so you'll need to hunt for the location of that option yourself (it's in the Display/Appearance preferences, or something like that).

I found the setting and it was on OpenGL rather than XRender. Changing it to XRender made it worse and now it fails to go back to OpenGL...

Cheers,

-- 
Bob.

---

### Post by fatboab on 2009-05-20
> **fatboab said:**
> I found the setting and it was on OpenGL rather than XRender. Changing it to XRender made it worse and now it fails to go back to OpenGL...


To clarify, this was in the Desktop Effects bit, switching all of them off makes no difference, but at least makes my desktop usable again. Can anyone tell me how to reset it so it goes back to OpenGL, I just get the following when I try:


[IMG]http://www.bobarnott.com/temp/effects-error.png[/IMG]

There is no difference in my xorg.conf for when it was running under OpenGL composting...

Cheers,

-- 
Bob.

---

### Post by psyke83 on 2009-05-20
Your card may be too old to use compositing. You could try to change the acceleration method (AccelMethod) to XAA. See "man radeon" for all the driver options.

---

### Post by fatboab on 2009-05-20
> **psyke83 said:**
> Your card may be too old to use compositing. You could try to change the acceleration method (AccelMethod) to XAA. See "man radeon" for all the driver options.

It's an oldish machine that only has PCI and as it's at work, I'm limited to what's available to put in it. I'll check out the man pages.

Cheers,

---

### Post by fatboab on 2009-05-20
> **psyke83 said:**
> Your card may be too old to use compositing. You could try to change the acceleration method (AccelMethod) to XAA. See "man radeon" for all the driver options.

That appears to have done the trick, thank you!

Cheers,

---

### Post by Irish J on 2009-06-04
Hi, sorry to up the thread, but i'm having the same problem with the same-ish card (radeon 7000 VE).

My xorg.conf looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

I would really appreciate some help with editing this with that XXA thing.

As you can see it doesnt appear to be configured very well, this was the one my default xubuntu install generated.

Would anyone be willing to take me through the steps needed here?

---

