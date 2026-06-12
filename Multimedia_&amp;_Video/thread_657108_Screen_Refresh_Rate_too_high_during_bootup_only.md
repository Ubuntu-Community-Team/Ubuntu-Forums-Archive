---
title: "Screen Refresh Rate too high during bootup only"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by dmrlook on 2008-01-03
Hello - I was hoping someone could help me on this strange issue.  I have a 17 inch LCD monitor that displays an error message when the frequency being fed into it is too high.  I see that message each time Ubuntu loads, and thus can not see the loading status bar.  Once I get to the login-screen, everything is fine from that point forward.  I am using ubuntu 7.10.

I have a dual boot machine (XP on the primary HDD and ubuntu on the secondary HDD).  I can see the grub menu no problems, as soon as I hit enter with Ubuntu selected, the screen goes black and I see the "Out of Range" message.  Everything returns back to normal once the login screen is loaded.  

I am guessing there is a parameter somewhere that configures trhe refresh rate during the initial load.  How can I change this?

Thanks!

---

### Post by PPAAUULL on 2008-01-03
I had the same problem, you might want to check what resolution you have the bootup set for in the grub file. Here is a handy post that I found, it helped me fix my problem. [http://ubuntuforums.org/archive/index.php/t-119696.html](http://ubuntuforums.org/archive/index.php/t-119696.html)

---

### Post by dmrlook on 2008-01-03
Thanks for the fast reply.  I tried what the thread suggested with no luck.  I did the following:

cd /boot/grub
sudo pico menu.lst

Update the menu option for ubuntu to set vga=769 and a few other options.  Also set defoptions=vga=769

After each update, I ran "sudo update-grub"

Then rebooted, and still the same issue.

I noticed that after typing "sudo update-grub", when the command completed, my updated were deleted from menu.lst.  So this might explain why my updates were not making a difference.  Am I doing something wrong that would prevent the updates from taking hold?

Thanks everyone!

---

