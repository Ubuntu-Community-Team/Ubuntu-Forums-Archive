---
title: "Finally fixed the widescreen: Intel 855GM"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by dsokus on 2006-07-27
Hi All, 

I have posted many times about me being unable to fix my widescreen! 

People suggested 815resolution and 915resolution but they didn't work. I finally realized they did not work because my BIOS was reporting a different resolution that I was trying to get at: my intrinsic resolution reported by the BIOS is 1280x768, instead of 1280x800! I find it quite interesting, as Windows recognizes 1280x800 and that is also the resolution given in the brochure about the specs of my computer. Anyway, then I used 915resolution to set the screen resolution to 1280x768, modified /etc/X11/xorg.conf to have 1280x768 as the resolution at all depths, and it suddenly worked beeeeaaaauuuutifully! 

So to repeat, if you have an Intel 855GM graphics card and 815/915resolution don't seem to fix it, the key is probably: 
[COLOR="Red"][SIZE="4"]
DO NOT TRY TO SET A RESOLUTION THAT YOUR BIOS DOES NOT REPORT![/SIZE][/COLOR]

Thanks to all who have helped, and I really hope this info will help somebody else too!! :)

Z.

---

### Post by daller on 2006-08-08
This is off-topic, but I really need help...

Did you install the proprietary drivers?

My screen acts weird! - It suddenly gets totally blank (white), and i wait some seconds for it to return to normal!

I think I can fix this by installing the proprietary drivers, but I can find a howto on how to do it!

---

