---
title: "Nvidia 8600GT and hdmi tv out to Sony LCD Tv resolution problem"
date: 2008-12-05
forum: Multimedia Software
---

### Post by PrimaryMaster on 2008-12-05
Hi everyone,

I have a laptop equipped with an Nvidia 8600GT card. The laptop dual boots to Vista and Ubuntu 8.10. The TV is a 42 inch full hd capable Sony Bravia lcd. 

When i boot to Vista with the hdmi cable connected the TV resolution defaults to 1080i and i can get a proper clone view on the TV. When i boot to Ubuntu and enable the tv out via hardware buttons on the laptop however, the tv resolution defaults to 1366*768. Using Nvidia Xserver settings i change the output for tv to 1920*1080 and set it as a separate X display. TV changes to 1080i but the display has horizontal lines, like the interlaced display is somewhat not working well, hard to read the characters on screen. 

I tried all the settings that i could via Nvidia Xserver but could not get a proper resolution out of my tv. Vista can do that without any adjustment needed. Nvidia Xserver settings info page says the default resolution for my tv is 1366*768 but that should be 1080i. 

How can i set it up correctly? Do i need to edit my Xorg.conf? What information can i provide here so you guys can help me with this? 

Thank you.

---

### Post by tschnittgen on 2009-01-03
It appears that Ubuntu is loading into 720p.  However 1080i and 720p are essentially the same thing.  Therefore I don't think you have anything to worry about.

---

