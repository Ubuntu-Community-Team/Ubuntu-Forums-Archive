---
title: "[SOLVED] MythTV Focus"
date: 2007-10-29
forum: Mythbuntu
---

### Post by Tteddo on 2007-10-29
I have an obscure problem. I run a dual head setup (ATI) and have the digital out go to my 1080p TV in native mode, and the VGA out go to a monitor that has a USB wireless keyboard and mouse that I use as a computer. It is set in xorg.conf like this :
Screen 0 LeftOf Screen 1
On my old setup with FC Core 4 in 2004, if I moved the mouse over to the TV and clicked the focus was on MythTV and I could use the keyboard to control it fine. With the new one (the newest Mythbuntu) I have to not only click over on the TV side, but hit ALT TAB to mythfrontend to gain focus. Without Myth running, it works like the old setup (click to focus).
Anyone have any ideas?

---

### Post by superm1 on 2007-10-29
> **Tteddo said:**
> I have an obscure problem. I run a dual head setup (ATI) and have the digital out go to my 1080p TV in native mode, and the VGA out go to a monitor that has a USB wireless keyboard and mouse that I use as a computer. It is set in xorg.conf like this :
Screen 0 LeftOf Screen 1
On my old setup with FC Core 4 in 2004, if I moved the mouse over to the TV and clicked the focus was on MythTV and I could use the keyboard to control it fine. With the new one (the newest Mythbuntu) I have to not only click over on the TV side, but hit ALT TAB to mythfrontend to gain focus. Without Myth running, it works like the old setup (click to focus).
Anyone have any ideas?
Try to play with the Xfce focus settings.  You can change it so the window under the mouse gains focus.

---

### Post by Tteddo on 2007-10-30
Well, that was blindingly simple. That actually works better than having to click. Thanks!

---

