---
title: "Nvidia Settings can't save conf file"
date: 2009-07-25
forum: Multimedia Software
---

### Post by babujbf on 2009-07-25
ok so I got setup my computer with my tv just how I want it. With both displays twin view but when I got to save the conf file it gives me this error window.

[[IMG]http://img151.imageshack.us/img151/8638/screenshotnvidiasetting.th.png[/IMG]](http://img151.imageshack.us/i/screenshotnvidiasetting.png/)

Thanks guys

---

### Post by 67GTA on 2009-07-25
The nvidia-settings app needs administrator rights to write to xorg.conf, which is a system file. Try starting it as administrator (root) in a terminal. ```
sudo nvidia-settings
``` If that is not the problem, you may need to set up xorg.conf first. Open a terminal and run ```
sudo nvidia-xconfig
```

---

### Post by babujbf on 2009-07-25
I got one question. I had my displays as Twin and I just put one over the other with the same resolution. Now my tv has way more definition than my computer monitor plus my monitor is square my tv is not. So I set them up as separate screens to adjust the resolutions differently on each displays.

I see the desktop on my tv but what I do on my computer displays does not happen on my tv display. Is there a way I can switch momenteraly to the tv screen and play a movie there and then comeback to the normal computer display?

Thanks

---

### Post by HappyFeet on 2009-07-25
Did you set the monitor you want as the main screen to be the primary display?

---

### Post by babujbf on 2009-07-25
well... I guess because the one I am using right now is the one I want. SO I guess its primary. But the thing is I want to play movies on the other one and when I play them on here the other one just stays on desktop.

Is there a way I can switch and control the mouse on the other display or make the things that I do on my primary display happen on my secondary?

Thanks

---

### Post by babujbf on 2009-07-25
help please lol wanna get this set up

---

### Post by andy16666 on 2009-07-25
[babujbf]("http://ubuntuforums.org/member.php?u=162040"): I don't understand what you are asking. Do you want the first display to be mirrored or copied exactly on the second one? Or do you want your desktop to simply extend onto it?

---

### Post by babujbf on 2009-07-27
Andy right now I have my tv working as an extension of my desktop. My monitor(primary) is set at 1280x1024 resolution because thats as high as my pc monitor can go. On the other hand my tv is set to 1920x1080 and its perfect to run movies.

Its setup right now as an extension which I am not happy with because for some reason when I press full screen on movie player it stays on that screen like I want it too but then I try it with other apps such as frozen bubble and it comes back to my primary (tv monitor) when I want it to be on my tv.

Clones would be Ideal the thing with the clones is that since my tv is bigger than my monitor once you place one over the other the tv has alot of blank space and only using a small portion of the display. If there could be a way to show what happens on my primary on to my tv with different resolutions that would be ideal.

Thanks

---

### Post by tyeo098 on 2009-07-27
Clone settings will clone the resolution. If you have a square monitor and a rectangular TV it will make the TV picture a square.

You cannot clone at different resolutions (4:3 and 16:9 anyway)

---

### Post by babujbf on 2009-07-28
whats the other option then? I want one full desktop on both displays be it one mirroring the other or two completely separate desktops. Not an extension...

How can I do that?

---

### Post by xc3RnbFO8P on 2009-07-28
How do you connect your monitor and TV?
The best way is to connect monitor DVI<>DVI and TV HDMI<>HDMI
Use separate screens.
Resolution: don't use Auto 
Check if the TV is 1080i or 1080p.
1080i , you choose 1920x1080_60i 
1080p ,  1920x1080_60

---

### Post by babujbf on 2009-07-28
thanks ringi I go it running now. My tv is connected dvi to hmi.

However I still have a problem that the apps I open in the tv screen actually open in my regular monitor. I heard this is a bug on Jaunty... any updates on that bug?

---

