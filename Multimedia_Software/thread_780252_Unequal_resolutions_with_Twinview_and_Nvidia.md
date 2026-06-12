---
title: "Unequal resolutions with Twinview and Nvidia"
date: 2008-05-03
forum: Multimedia Software
---

### Post by fizgig on 2008-05-03
I have an Nvidia 8800 card and I get twinview working pretty well with the nvidia driver.  Trouble is, my laptop screen is 900 lines tall and my attached monitor has 1050 lines.

What seems to happen is I can choose to have either the top or bottom 150 lines of my laptop screen not shown.  In other words, I can either see the main menu bar at the top or see the application switching bar at the bottom of the laptop screen but not both at the same time - depending on where I drag the lcd screen in the nvidia control panel.

The 1050 monitor shows both bars.

I've fiddled around with the nvidia control panel for awhile now and don't see a way past this and I didn't have much luck searching the forums for "unequal resolution twinview".  If anyone has an idea, please share!

---

### Post by fizgig on 2008-05-03
Woops, problem went away with a reboot.  All good now.

---

### Post by negustafson on 2008-06-28
Just to clarify since this was the first hit i got when I searched Google for this issue:

1) Remember to run ```
sudo nvidia-settings
``` from the command line. You won't be prompted for a password if you just run it from the menu. If you run as normal, you won't be able to save to your new settings to your xorg.conf file and the system will revert back after a reboot.

2) For whatever reason, rebooting does cause your second monitor to become an extended screen; as opposed to the one large spanning screen you get when you first activate Twinview thus causing the "screen cut-off" problem when using monitors with unequal resolutions.

---

### Post by Pjotr123 on 2008-06-28
> **negustafson said:**
> Just to clarify since this was the first hit i got when I searched Google for this issue:

1) Remember to run ```
sudo nvidia-settings
``` from the command line. 

Right. A small correction, however: since nvidia-settings is a graphical application, gksudo is better than sudo.  :-)

---

