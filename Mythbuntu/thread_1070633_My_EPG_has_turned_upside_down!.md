---
title: "My EPG has turned upside down!"
date: 2009-02-15
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-02-15
Now this isn't the most serious problem ever, but it's bugging me. Until today, my EPG that pops up when I want to watch TV or schedule a recording listed my channels from low to high channel numbers. Today, for no reason that I can think of, it has turned upside down, so it now lists channels from high to low channel numbers.

Any ideas how to turn it back again?

Thanks
NM

---

### Post by NautiusMaximus on 2009-02-21
Bump

---

### Post by crez79 on 2009-02-22
Assuming you have "Allow channel jumping in guide" turned off in Settings->TV Settings->Program Guide (second page of options), you can just press '0' on the remote and it will reverse the sort order. For me if I have "Allow channel jumping in guide" checked, it just jumps to where channel 0 would be if there was one.

If you have mythweb (settings->mythtv->keybindings) or mythcontrols (edit keys->tv frontend->toggleepgorder) installed you can verify what keypress it is and change it if wanted.

You can probably also change it directly from mythweb (settings->mythtv->settings table->EPG sort reverse). If it is 0 change it to 1 or if it is 1 change it to 0. I am not completely sure if that will do it but it sure makes sense. Make sure you are changing it for the correct frontend if you have multiple.

These little things aren't very well documented. Mythtv is so customizable you can change or tweak just about anything but you just have to find it. I knew there was a way because I had this problem a little while ago but it still took me a few minutes of searching all the menus and options to find out what I messed with back then.

---

### Post by NautiusMaximus on 2009-02-22
Thanks for that, you're a star!

I did have "allow channel jumping in guide" ticked, but all I had to do was untick it, go to the guide, press zero, and then go back to settings and tick it again.

Problem solved!

Now I just need to solve the other few dozen problems I have, and my system will be really great...

---

