---
title: "Fresh minimal install, no sound"
date: 2009-10-25
forum: Multimedia Software
---

### Post by djmoore85 on 2009-10-25
Hey yall. I just finished a barebones/minimal install with xfce, and I am having sound issues now. I am getting no sound, even after going through alsamixer in the terminal and adjusting volume. I also can't get the built-in vol buttons on my laptop to respond to anything. This is what I have reading in the terminal for my sound card. I installed kterm and have xterm but can't seem to pull up menu options for copying and pasting, so unfortunately I don't have any code to post up here. I have browsed through the sound problem guide sticky but haven't as of yet found a solution. Video works fine, but no sound. Thansk to all who can help out with a solution

---

### Post by onespeedbiker on 2009-10-25
> **djmoore85 said:**
> Hey yall. I just finished a barebones/minimal install with xfce, and I am having sound issues now. I am getting no sound, even after going through alsamixer in the terminal and adjusting volume. I also can't get the built-in vol buttons on my laptop to respond to anything. This is what I have reading in the terminal for my sound card. I installed kterm and have xterm but can't seem to pull up menu options for copying and pasting, so unfortunately I don't have any code to post up here. I have browsed through the sound problem guide sticky but haven't as of yet found a solution. Video works fine, but no sound. Thansk to all who can help out with a solution
Try clicking on the little speaker icon and make sure the mute box is not checked. I don't know why this happens, but it does.

Hey we have the same amount of beans!

---

### Post by djmoore85 on 2009-10-26
Thanx onespeed. Unfortunately I don't have the clickable speaker icon on the desktop. It's not in panel options either. So far the only mixer I have been able to pull up is alsamixer in the terminal. Anyone got ideas as to why lspci -v shows a card and driver, aplay -l finds the card and says it's working, yet I still have no sound?

*EDIT* I got sound comin out of the speakers. Downfall is I have no volume control by push-button, only through alsamixer in terminal. Any ideas or am I missing a package to have full use of the hardware?

---

### Post by RichardLinx on 2009-10-26
I haven't used Xfce too much, but maybe you can assign a shortcut key for volume up/down.

---

### Post by ran_talbott on 2009-10-27
KDE and (I think) Gnome come with mixer controllers as part of the "basic" package,  so most people don't have to think about it much.

But a lot of people (like,  e.g., me) use xfce on "minimal" systems,  so it doesn't include as many goodies by default.

You need to add a GUI mixer.  Probably something like [this]("http://www.xfce.org/projects/xfce4-mixer") (although there might be better one: I can't recall using xfce on a PC where I used sound,  so I never actually researched what's available until a few minutes ago).

Ran

---

### Post by djmoore85 on 2009-10-28
Thank yall very much. I got the xfce-mixer frontend and the alsa backend that goes with it installed. Worked beatifully. Ran, might I ask what you used your minimal xfce install on/for?

---

### Post by mrmhead on 2009-10-28
> **djmoore85 said:**
> Thanx onespeed. Unfortunately I don't have the clickable speaker icon on the desktop. It's not in panel options either. So far the only mixer I have been able to pull up is alsamixer in the terminal. Anyone got ideas as to why lspci -v shows a card and driver, aplay -l finds the card and says it's working, yet I still have no sound?

*EDIT* I got sound comin out of the speakers. Downfall is I have no volume control by push-button, only through alsamixer in terminal. Any ideas or am I missing a package to have full use of the hardware?

So what'd ya do?
I'm hunting same symptoms on a desktop machine ... does the "x" in xfce imply Xubuntu? - that's what I got....

Thanks
m

---

