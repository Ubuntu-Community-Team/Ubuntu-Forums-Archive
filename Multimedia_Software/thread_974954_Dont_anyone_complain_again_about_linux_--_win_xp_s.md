---
title: "Dont anyone complain again about linux -- win xp sucks!"
date: 2008-11-08
forum: Multimedia Software
---

### Post by tropdoug on 2008-11-08
Hi guys

Strange title I guess. OK this is the issue. I have both my laptop and Desktop happily converted to Ubuntu, and working well. My laptop required an NVidia driver for its GeForce 7300 Go video card, no problems, downloaded and installed a breaze, used the config tool supplied and a perfect result. Yahoo! 

However as yet I have been totally unable to get my external projector to work on the laptop. I need both screens working as clones for public presentations I do. (I asked this question a while ago, but never got to a solution)

Why then do I mention windows above! my only solution up to now has been to use the Win XP partition I still have on the laptop and use office powerpoint. BUT I recently added a disk label to the partition stupidly forgetting that I would wipe out the partition and sure enough I could no longer boot into it. 

So no worries I used my WinXP disc and reinstalled. PROBLEM -- no Nvidia driver installed, and after three days of downloading and trying various Nvidia drivers, supposedly for XP but actually requiring Vista to work (this was originally a vista oem machine, until I reformatted it - to put a good system on)I am giving up. 

So once again Windows proves to me what a bucket of horse manure it really is. 

**So I return to my main issue, can anyone help me get an external projector working with linux, so that I can use ooORG Presentation and the best OS on the planet --- pleeeeeese!**

---

### Post by Ng Oon-Ee on 2008-11-08
Well, using Nvidia's own control panel (the binary, not Ubuntu's version) should work, shouldn't it? Worked default for mine. Just click 'detect displays' and it should show the displays. You can select 'clone' mode, but make sure both displays are the same resolution.

---

### Post by tropdoug on 2008-11-08
Tried that, and in th3e control panel it shows both displays, correct resolutions etc. However only 1 actually shows the display. I could switch between them, but not get both showing at the same time. 

How do I know if I am using the binary and not ubuntu's one, maybe that was the issue?

---

### Post by Ng Oon-Ee on 2008-11-09
> **tropdoug said:**
> Tried that, and in th3e control panel it shows both displays, correct resolutions etc. However only 1 actually shows the display. I could switch between them, but not get both showing at the same time. 

How do I know if I am using the binary and not ubuntu's one, maybe that was the issue?

Okay, try this, select any of your screens. Below the picture that allows you to select screens, you have a bunch of lines. The first line says 'Model' and you can use that to select which screen you want to mess around with (useful when you've set them to overlap, and can't select them from the picture).

The next line says "Configuration" and probably has the value Separate X Screen or Disabled, depending on which screen you have selected. Click the 'Configure' button next to it, and select the 'Twinview' option.

Click Apply at the bottom and see if both displays have picture. If they do, then the next thing you need to do is select Clone (the option to do so will appear after you have selected 'Twinview', in a lower line) and apply again.

---

