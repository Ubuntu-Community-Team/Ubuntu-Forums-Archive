---
title: "5x1 5400x1920 how is it possible in the most concise way. or impossible?"
date: 2015-04-20
forum: Multimedia Software
---

### Post by divine_fisher_smit on 2015-04-20
"Linux sucks, you need to tweak a lot before you get stuff working" a friend told me. his a windows patriot. but I love linux so his not my friend anymore :guitar:
Haha anyways I am not a ubuntu pro user yet! Ive been searching the internet finding a good instruction on how to setup multiple screen on ubuntu and make it work as one like eyefinity. Ive seen few which is not really that helpful and concise. almost all of them are for 3 monitor setup only. 

I just want to put this straight. in a brief and concise way. How is this setup possible on ubuntu? Ive seen eyefinity setup on ubuntu on youtube (these, [https://www.youtube.com/watch?v=N6Vf8R_gOec](https://www.youtube.com/watch?v=N6Vf8R_gOec) [https://www.youtube.com/watch?v=ha1j0iLpAjU](https://www.youtube.com/watch?v=ha1j0iLpAjU)) but they dont have instructions on how to do it. plus the monitors are upright and not flip sideways like on this picture.
[IMG]http://i1122.photobucket.com/albums/l534/twinklelonelystar/SANY00062_zpsxbqxrkrd.jpg[/IMG]

1. to flip the screen sideways permanent in a way that it is already configured and you dont need to teak it everytime you open your computer.
2. how to setup this up as one monitor with a single resolution "**&#8203;**5400x1920" and not just a standard multi screen setup. like eyefinity mainly for games.

Ive heard a lot that this is impossible in linux, but the video Ive seen strengthen my belief that it is possible. But is there any good instructions out there? I mean for those people (fine you may call me idiot) who dont know a lot on tweaking in order to set this up. In way that beginners can understand ;) I really hope there is.

---

### Post by Bucky Ball on 2015-04-20
*Thread moved to **Multimedia**.*

Hmm, interesting proposition. If there is a way, you'll have a better chance of finding it here. Good luck. ;)

---

### Post by Bucky Ball on 2015-04-20
*Thread moved to **Multimedia**.*

Hmm, interesting proposition. If there is a way, you'll have a better chance of finding it here. Good luck. ;)

PS: Please attach large images using the paper clip icon in 'Go Advanced' or 'Adv Reply'. Thanks.

---

### Post by jdami534 on 2015-04-29
Sounds like you wanna use arandr, the monitor configuration tool which is a wrapper for xrandr (which is a command line monitor configuration tool)
Assuming you have a computer with enough video ports (or video splitters, or pretty much anything that works), you could use arandr which has a nice GUI that is much easier to use then the xrandr it wraps to. also it handles orientation, in case you wanted sideways monitors.

My first post Woot woot!

Edit: to answer number one, arandr spits out a execuable script that will set the monitors to a specific position, orientation an resolution ( and refresh rate is also possible, but i imagine you would need to edit the scrips to include that). and then just figure out where to put that script so its run on startup/login (its a bit specific for each os). for my os (lubuntu) i would suggest startmenu>preferences>Default applications for LXSession. then pick the autostart tab and add the custom script(might have to put it in the /usr/bin folder for it to work). but thats specific to lubuntu, ubuntu could be entirely diffrent.

as for number 2, technically, arandr cannot actually set 2 monitors to anything else then a single screen so tick.

---

