---
title: "Nvidia has different configs for different users?????"
date: 2008-09-26
forum: Multimedia Software
---

### Post by cforput on 2008-09-26
I recently upgraded to Hardy (what a mistake but that is a different story) and had to redo a lot of my configuration. Some of it I have working but I am stuck on my graphics. Here is what is driving me crazy. I have an acer laptop (aspire 5520-5334) and have different users set up. I have installed the latest nvidia drivers and I use the nvidia x server settings to configure my card. Here is the problem:

When I log in as user "A", the graphics work as I have them configured which is 1280 x 800. When I log in as user B, even though I have the configuration set at 1280 x 800 the graphics drop down to 1024 x 768. I can manually set it back to 1280 x 800 and it works fine but why would a user ID control the graphics settings. I'm a newbie and lost!

---

### Post by markbuntu on 2008-09-26
Graphics configurations are considered to be user preferences. In a multiuser system this makes sense.

---

### Post by cforput on 2008-09-26
OK. So that makes sense. Can you tell me where I might find the files that have the different preferences so that I can compare the 2 and try and find out how to fix it.

Thanks!

---

### Post by ad_267 on 2008-09-26
How did you set the resolution? What happens if you use "gksu nvidia-settings" and do a "Save to X configuration file"

---

### Post by cforput on 2008-09-26
That's the frustrating part. I did use gksu nvidia-settings. I did it 3 times just to make sure I did it right. It saved fine (not like doing it in system/administration/NVIDIA xserver settings where NVIDIA doesn't have the rights to save the file). I set it to 1280 x 800 using gksu. My screen changes. When I reboot, it reverts back to 1024 x 768. What is even more weird is that my other users on the system come up at 1280 x 800. So I have obviously goofed up something in the user preferences for the user that doesn't work. If I could find out where the files are that govern these preferences, I could compare the 2 users and see what is different. My only other alternative is to save all my info on the original user. Delete the original user. Recreate the original user and copy my data back. I am worried though that I might cope back a bad config file and be right back to where I started.

Anyone know where the config files are stored, especially ones dealing with graphics?

---

### Post by ad_267 on 2008-09-26
Maybe try deleting/renaming the .nvidia-settings-rc file from each users home directory if there is one.

---

