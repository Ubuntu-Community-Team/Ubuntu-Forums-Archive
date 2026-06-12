---
title: "[SOLVED] what to name new channel icon files?"
date: 2008-08-26
forum: Mythbuntu
---

### Post by boon2 on 2008-08-26
Hello,

I'm wondering if anyone can tell me what the trick is to get new icons (i.e. icons that I've created and want to add because the "download channel icons" function didn't come up with anything, thus leaving a glaring blank in the program guide).

I've managed to come up with where the channel icons are stored, but I'm wondering how to discover either what to name them so that the frontend will pick them up when it starts up or if there's a mySQL record that needs to be altered so that it knows what icon file to use?  

Thanks

---

### Post by newlinux on 2008-08-26
I think you can just enter the fullpath to the icon for each channel in the channel editor in mythtv-setup.

---

### Post by boon2 on 2008-08-27
Thanks,

I actually had tried that but it didn't seem to work.  After reading your reply, I went back and double checked the filename, path, etc. and those seemed to be in order.  Then I looked at another (functional) entry and found something rather strange:

/home/rc/.mythtv//channels/iconfile.jpg

when I inserted an extra slash between .mythtv and channels, the icon popped right into place!  So... yay!  Not sure why that extra slash belongs there, but as long as it all works, I'm happy. :)

Thanks again for all your help.

Rob

---

