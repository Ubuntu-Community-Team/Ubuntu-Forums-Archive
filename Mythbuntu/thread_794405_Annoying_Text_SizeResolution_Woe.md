---
title: "Annoying Text Size/Resolution Woe"
date: 2008-05-14
forum: Mythbuntu
---

### Post by singedwings on 2008-05-14
I have been having some weird text size/resolution problems with Mythbuntu 8.04, although I think I have partially solved them now.

Mythbuntu was incorrectly detecting my monitor, and when I chose the correct monitor and desired resolution all the text sizes and screen sizing was going absolutely bonkers. Some text would be tiny, some normal size. Some screens such as mythtv frontend would try to fill a monitor 4x the size.

I traced part of the problem to the **font DPI** setting in the user interface preferences in the settings manager. Once I had changed this to **96 instead of default** everything goes back to normal.

For some reason though the resolution keeps changing when I restart the computer instead of the desired **1280x1024x85** it reverts to **1920x1440x50**:confused: This only seems to happen after I have made some changes to the display/graphics driver. So it is not the end of the world.

Also even though the monitor has been correctly identified when using the open source driver. Once I install the nvidia driver, nvidia settings identifies the monitor incorrectly again, even though the system still identifies the right monitor.:confused:

Thx for your help.

---

