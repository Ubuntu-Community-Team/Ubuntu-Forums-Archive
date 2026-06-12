---
title: "HDMI to TV"
date: 2012-11-30
forum: Multimedia Software
---

### Post by MissThrasher on 2012-11-30
I have an HP Mini 311 and I'm trying to hook up to my Panasonic Viera tv.  I run Ubuntu 12.04 LTS.

Upon intitial connection of HDMI from TV to Laptop, my tv stays black and it has stayed black throughout everything I list below.

I have tried:
Plugging in HDMI cord from TV to laptop then rebooting.

Switching HDMI1 to HDMI2 on my tv

Then when I go to:

System setting - Display sees nothing but my laptop.
And when I go to Sound and change my audio over to HDMI, I get no sound either.

NVidia X Server Settings - I see that my Panasonic is listed near the bottom it says: DFP-1-(PANASONIC-TV).  I look under X Server Display Information and there is an error that reads: Unable to Load X Server Configuration page: Failed to query NoScanout for screen 0
(I don't know if that means anything)

Additional Drives - I click this and it searches, but nothing happens.

I've been googling for an answer for almost 2 hours and no dice.  Please help me.  I just want to watch a movie.

---

### Post by SeijiSensei on 2012-11-30
Sometimes there is a function key combination that needs to be pressed to switch between displays.  Take a look at your computer's manual.

---

### Post by MadMadness on 2012-11-30
Thrasher, I had somewhat similiar issues with the additional drivers not opening.

What you need to do is run:

```
sudo apt-get update
```

And once that is done run:

```
sudo apt-get dist-upgrade
```

Then reboot (not sure if its necessary) and run the additional drivers utility again.

Hope this helps.

---

