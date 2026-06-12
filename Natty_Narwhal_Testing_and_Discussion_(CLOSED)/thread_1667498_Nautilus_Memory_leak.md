---
title: "Nautilus Memory leak"
date: 2011-01-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by LewRockwellFAN on 2011-01-14
I posted on this in GH but ibuclaw believes it is more appropriate here. Makes sense if, as I'm told, the problem is solved in Meercat. But Nautilus is still gradually nibbling away at my memory until it gets to a crises point and either I catch on and kill it or I crash. So I was thinking about a work around:

Make a script that runs every minute or so (there is a gui ap in  synaptic that makes it easier to schedule scripts. I think it is called  gnome-schedule) and tests free memory and, if it drops below some  threshold you set, pops up a window on top of everything that reports the  problem and offers to run "killall nautilus". This works fine if done manually. The desktop and any open directories disappear, Nautilus restarts and re-establishes the desktop using a more normal amount of memory. I'd like to try this  approach but I haven't figured out how to write the conditional if  statement or how to make it pop up a dialogue box or anything like that.  If anyone can point me in the right direction on this that would be  really cool. Thanks if you can.

LOL, I just found this part of the forum after ibuclaw sent me looking for it. NOW, I see the sticky that says "There's basically no point in upgrading to Natty at this point". I'm not complaining. Y'all DID label it a beta. And it seems to have worked fine for me so far except for this occasional memory leak problem.

---

### Post by dino99 on 2011-01-15
when things goes wrong you can try, either:

- remove/purge then reinstalling the package(s), (cant really do that with nautilus)

- cleaning the system as much as possible: gconf-cleaner and bleachbit (used as root, check what you want/need) often help

- make a reconfiguration:
sudo dpkg-reconfigure -phigh -a (could be long, dont stop it)

- force a fsck on next reboot: sudo shutdown now -R

- fight misconfiguration with fwts and/or valgrind

- into a terminal: run the app with --debug

At last: make a fresh installation (reformat the partitions: / & swap)

---

### Post by ronacc on 2011-01-15
Natty isn't even beta yet that isn't scheduled to happen until march 31 .
[https://wiki.ubuntu.com/NattyReleaseSchedule](https://wiki.ubuntu.com/NattyReleaseSchedule) 
we aren't even to alpha 2 yet . 

I just checked my test box and I'm not seeing any memory leak with nautilus . how are you checking the amount of memory that nautilus is using ?
With top I show nautilus as 0% memory use unless I move the mouse or do something else that gets its attention so you need to check what nautilus is doing that is eating your memory , if you are using unity try rebooting and selecting "classic desktop" at login .

---

### Post by kyleabaker on 2011-01-15
I've seen a memory leak in Nautilus for some time now, but I don't think its at all related to Natty or Unity. Maybe I'll get around to creating a usable bug report soon.

For now, all I know is that it grows heavily in mem usage from ~20-30mb to ~180-250mb after organizing files for about an hour or so. Seems to be related to generating thumbnails or something for me.

---

### Post by LewRockwellFAN on 2011-01-17
@ [dino99]("http://ubuntuforums.org/member.php?u=129712"), Thanks. All nice things to study. Half of them I'd never heard of.

@ [ronacc]("http://ubuntuforums.org/member.php?u=80744"), Thanks. I'm checking memory when things start slowing down or not working with System, Administration, System_Monitor (2.28.1), Resources_tab. Right now, after having booted a few minutes ago, it is around 404 miB out of 2 giB. and in the Processes tab it shows one Nautilus, sleeping, using about 113 miB, which is more than twice what FireFox is using, with everything else under 10 miB. When things go sour, the total usage will be over 1600 miB with Nautilus accounting for all the extra usage. I don't know Unity. I'll look it up. It's not anything I knowingly added so it it isn't in the default Nautilus install, probably not. I didn't realize Nautilus had more than one type of desktop. I'll look that up also.

@ [kyleabaker]("http://ubuntuforums.org/member.php?u=391929"), Thanks. Interesting point about thumbnails. I used the detailed view by default, but it still makes tiny thumbnails. I'll try to see if I can turn that off if and when I get Nautilus to working as a file browser again. Darn. I just tried to launch it from the places menu and it tris to launch Document Viewer instead of Nautilus on any directory. Nautilus stll works though. I have made a "open this folder in Nautilus" context menu item I made in Thunar OK, I found it. I turned off thumbnails. /me crosses fingers.

Thanks a lot, y'all. I was dumb to install Narwhal without noticing it's alpha status. If this gets too annoying I'll just reinstall Meercat.

---

### Post by ronacc on 2011-01-17
unity is the default desktop of Ubuntu now if you have a 3d capable graphics card and driver . a 2d version is available but I don't know if it defaults to that now if you don't have 3d capability, if not that then the classic gnome desktop . For comparison I'm showing nautilus using 26.7mb and not increasing on my AMD64 sys running the classic desktop . nvidia 7600gs and nvidia-current driver .

---

### Post by dino99 on 2011-01-18
on natty i386 (generic-pae), without compiz/unity, nautilus use 6.1 Mio :)

---

### Post by LewRockwellFAN on 2011-01-23
Haven't had a chance to investigate all these things or make much progress on this yet. As you can see from the sig line, I've reinstalled 10.04, lucid. Still getting the same problem. For what it is worth I had and have all the "visual effects" turned off in System,prefs, appearances, which I presume would be extra gew-gaws on the desktop that would be nautilus managed. The only unity I see in Synaptic is just a theme so I don't know how to check if Nautilus is using it to manage the desktop.  If Thunar had tabs, I'd ditch Nautilus.  Anyway, I thought I should follow up since I started it here even though it is clearly not a Natty issue per se. If I figure out an answer or how to make the script work I'll post it. Thanks again.

---

