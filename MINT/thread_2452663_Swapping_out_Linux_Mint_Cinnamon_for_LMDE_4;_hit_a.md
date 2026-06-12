---
title: "Swapping out Linux Mint Cinnamon for LMDE 4; hit a snag *boot help*"
date: 2020-10-26
forum: MINT
---

### Post by mixonesix on 2020-10-26
Before I begin, I have been told Linux Mint and Ubuntu are completely unrelated. However, after having boot issues today, I noticed "ubuntu" (followed by Windows Boot Manager) in my Dell XPS series boot sequence.

I'll try to keep this short. I thought I successfully removed Windows 10 and replaced it with Cinnamon (I've been using a full featured Linux desktop for the last month). However, today I was unable to access any programs (aside from via Terminal) and could not see any taskbars. I also couldn't resize any windows nor close them. When I do boot up the system, I see my background applied and am able to log in with my password. However, upon completion of this, my background also disappears.

I downloaded the iso for LMDE 4, to try something else for a refresh, and wrote it to a USB stick (this is shown as a folder with 7 subfolders, one of which is a boot folder). I'm now in the boot manager and at a complete loss of what to do next. I don't see the USB stick as an option. What do I do to boot from the USB stick or did I write it to my USB stick incorrectly?

If this isn't the right forum, please direct me to the correct one. I have work to complete and cannot do anything right now. &#129396;

---

### Post by deadflowr on 2020-10-26
*Thread moved to **MINT***

---

### Post by mixonesix on 2020-10-26
Update: So I tried Ctrl + Alt + Esc which returned everything back to how it was initially. However, I reset the system to test it and I found I had to hit the same key combo AGAIN. Perhaps someone can explain what's going on? My taskbar also reset to its original setup instead of the custom organization I had.

---

### Post by yancek on 2020-10-28
>   I have been told Linux Mint and Ubuntu are completely unrelated.  However, after having boot issues today, I noticed "ubuntu" (followed by  Windows Boot Manager) in my Dell XPS series boot sequence.

Not completely unrelated.  Mint was and is based on Ubuntu.  Mint uses the Ubuntu repositories from which software is downloaded.  In your boot options from the BIOS on an EFI machine, the entry for Mint is labelled ubuntu.  This is/was a decision made by the Mint developers.  They could have changed it and a user can change it also.

If you have a UEFI install of windows (8 or 10) then you will have a windows entry on the efi partition/BIOS firmware even after overwriting windows on the installed partition.  This can also be changed to remove that entry if you wish, efibootmgr is probaby the best option with Mint.

You indicate you were no longer able to access any programs and several other problems which don't normally happen without user interaction.  Did you make some changes just prior to noticing these problems?

What software or method did you use to write the Mint LMDE iso to the usb stick and on which operating system.  Is this an EFI machine?  Can you no access the BIOS now as you were able to when you installed Mint Cinnamon?

---

