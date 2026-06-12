---
title: "Odd mythwelcome behaviour on 12.04"
date: 2012-12-14
forum: Mythbuntu
---

### Post by JasonEde on 2012-12-14
I've recently upgraded from 11.10 to 12.04. I'm setting up automatic startup and shutdown... This bit seems to work fine.

However, I've got a problem with mythwelcome... Despite the line being uncommented in session-settings then when I start mythwelcome it immediately starts the frontend. If I exit the frontend then the display hangs... However, the system does shut itself down in 5 minutes so the shutdown is working...

There is something wrong, but I don't seem to have much luck looking through the logs... Other than errors about can't find this font, so using that font I can't seem to find any other errors. :(

Any ideas?

---

### Post by PhilWig on 2012-12-14
Hi Jason,
    you are not alone.  I have 12.04 and use Mythwelcome and ACPI wakeup too.  When I exit frontend I get partial painting of the screen.  A dark band across top of screen and a block at bottom middle, with the rest unchanged.  You can get the welcome screen by tapping control-F1 /ctrl F2 a few times.
This is behaviour I did not get in 9.04.
I don't know Ubuntu well enough to decide which component it is. 
If you get a fix please post it here! 
Phil

---

### Post by JasonEde on 2012-12-16
I think I've solved it...

When I exited from mythfrontend then at the top I can see a tab saying mythwelcome... I took the chance that it was active, but I just couldn't see anything... I pressed i and got the configuration screen up... There I unticked the option to automatically start the frontend and clicked on finish and it started working... That options screen was in my old theme, but when I clicked on finish it went back to the current theme... (I used metallurgy theme before I upgraded)

---

### Post by PhilWig on 2012-12-20
Great!  that works here too.
Thanks Jason.
Phil

---

