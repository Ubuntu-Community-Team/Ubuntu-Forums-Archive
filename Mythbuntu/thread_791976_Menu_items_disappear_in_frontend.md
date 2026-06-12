---
title: "Menu items disappear in frontend"
date: 2008-05-12
forum: Mythbuntu
---

### Post by verhage on 2008-05-12
I'm having a problem concerning the menu's in my MythTV frontend. It only displays my theme's background, all menu items are gone. I'm using the default Mythbuntu theme, so all I'm seeing is the blue background. When I go through the menu's using up and down the menu items appear for a short time and I'm facing only the background again.

I'm running the Gutsy version of Mythbuntu. I updated a couple of days ago and hauled in an update that was related to frontend themes (I think, didn't really pay attention). Tonight, when I gave the frontend a restart, the problem started to show. One thing I noticed is that now the date and time is displayed at the bottom right of the screen, those weren't there before and now they're the only thing that is displayed on screen.

Anyone familiar with this problem and aware of a fix? I ran apt-get update, but it seems my system is up-to-date...

---

### Post by migres on 2008-05-13
I have exactly the same issue, Mythbuntu 7.10 - I tried to correct it before (and was successful) by: exiting the front end, opening a terminal window, erasing the .mythtv directory in the default user's home directory and then restarting the front end. However, last night this solution didn't help, it started to happen after the front end has crashed while watching recorded shows. If you search the web, it seems to be an issue while using the OpenGL option instead of Qt in the "Appearance" setup of the frontend. I'll try that later today.
Anyone else having this issue?

---

### Post by CornMaster on 2008-05-13
I had that problem with my old Mythtv install.

I think I tried changing all the settings under appearance to use both OpenGL and Software, or whatever was available at the time.  It didn't make a difference.

I'd just exit mythfrontend and restart it and it was fine.

Forgot to mention this hasn't happened with the Mythbuntu 8.04 yet (only had it working since Saturday evening).

---

### Post by verhage on 2008-05-13
> **migres said:**
> I have exactly the same issue, Mythbuntu 7.10 - I tried to correct it before (and was successful) by: exiting the front end, opening a terminal window, erasing the .mythtv directory in the default user's home directory and then restarting the front end. However, last night this solution didn't help, it started to happen after the front end has crashed while watching recorded shows. If you search the web, it seems to be an issue while using the OpenGL option instead of Qt in the "Appearance" setup of the frontend. I'll try that later today.
Anyone else having this issue?

That's exactly when the problem first occurred, when my frontend crashed watching a recorded show! Switching from OpenGL to Qt was one of the first things I tried, but that didn't work unfortunately...

---

### Post by migres on 2008-05-13
Hm, interesting. I think I'll go ahead and upgrade to Hardy in a few days. Looks like the solution is not as easy then, I'll still try the Qt option, with a reboot. I use the closed nVidia video drivers, the box is a Shuttle bare-bones with an AMD64 x2 processor, 2 GB of RAM, 250 SATA2 disk with an on-board video that has a built-in HDMI port. I wonder if it'd be best to install a good video PCI-x card instead... the video RAM is shared for this on-board video chipset and I have had issues before with shared video RAM configurations before.

---

### Post by migres on 2008-05-14
> **verhage said:**
> That's exactly when the problem first occurred, when my frontend crashed watching a recorded show! Switching from OpenGL to Qt was one of the first things I tried, but that didn't work unfortunately...

Last night I changed OpenGL to Qt and did a reboot. It corrected the problem (for now, anyway). I'll keep an eye on what goes on and see if the issue shows up again.

---

### Post by verhage on 2008-05-14
> **migres said:**
> Last night I changed OpenGL to Qt and did a reboot. It corrected the problem (for now, anyway). I'll keep an eye on what goes on and see if the issue shows up again.

You had to reboot your machine for this 'fix' to work?

---

### Post by migres on 2008-05-14
> **verhage said:**
> You had to reboot your machine for this 'fix' to work?

Yes, I changed to "Qt" from "OpenGL", rebooted and it works now. In fact the menu navigation and selection seems faster now, no crashes so far.

---

### Post by verhage on 2008-05-15
> **migres said:**
> Yes, I changed to "Qt" from "OpenGL", rebooted and it works now. In fact the menu navigation and selection seems faster now, no crashes so far.

Yesterday I changed from OpenGL to Qt and tried a reboot. Magic! It works perfectly :)

No wonder the menu seems to be responding faster, no nice fade in/out effects anymore.

---

### Post by migres on 2008-05-15
> **verhage said:**
> Yesterday I changed from OpenGL to Qt and tried a reboot. Magic! It works perfectly :)

No wonder the menu seems to be responding faster, no nice fade in/out effects anymore.

Glad to know it worked for you. Yes, there is always a trade-off but I guess until the issues with OpenGL and MythTV are resolved this solution solves the problem for now. I suspect it has to do with the nVidia chipset and the restricted driver that I am using. Probably avoiding the on-board video and installing a decent video card will solve the problems once and for all!

---

