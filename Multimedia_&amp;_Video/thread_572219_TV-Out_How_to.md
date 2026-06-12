---
title: "TV-Out How to"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by maj81 on 2007-10-10
I have Tried Ubuntu LiveCD, every thing seems to be fine til I have tired to press Fn + F5 on my my labtop to switch to the TV. 

The picture was a disaster at all resolutions, but when I switched to the safe graphic mode, I found out that I can use the TV-Out on 640*480, but 800*600 and 1024*768 still have major qualtiy problems but still butter than the situation with out the safe graphic mode.

I have installed ubuntu on the hard disk and every thing was fine except the TV-Out thing. (BTW there was no option for safe graphic mode after installing ubuntu!?!?!?

After many research in the web (BTW I'm completely linux n00b) I have figured out that I must make some changes to the etc/X11/xorg.conf file, I have update the file after reading many toturials but so far I run to the same results.

My question: I can switch to tv while in booting and every thing is fine, but when log into x window the picture will currapte, but the thing that I'm using the shortcut keys on the labtop.....will these keys going use the settings I have made for my TV on the xorg.conf file? or it will just make it on the hardware level? is there any special keys to switch between the screen I have identity at the server layout section on the xorg.conf file?

I have thought about a solution, I want to use the same settings that been used in the safe graphic mode. I don't know from where to get the xorg.conf file  but I assumed that it will be the file on the system disk when booting with the LiveCD on the safe graphic mode. so I have replace the original xorg.conf file with the file in the LiveCD. but unfortunatly I get black screen even on the labtop sceen it self. I have tried to boot from the liveCD in the normal and the graphic save mode which was working just the other day, but I still have black screen when ever the x windows going to start !?!?!?!?!? does installing ubuntu on the hard disk make the LiveCD behave like this way?!?!

I just want to use the safe graphic mode as the default settings for video then starting from there I can start modifying the file till I get the final version.

BTW My video card is Triend Blade.

---

