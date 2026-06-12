---
title: "Sudden problems with resolution"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by starfireview on 2006-06-03
When i booted the colour and resolution was off. I went to reset it under system, but it will not allow me to make a change. It says the only resolution is 640X480 (which is driving me nuts). There is also a lot of flashing going on...i only usually see that in the first three seconds when the desktop opens. The hertz rate is the same as usual which is giving me a headache rapidly. The system won't allow me to change the hertz rate either, even though i usually can. I have tried rebooting but it hasn't helped.

I looked through the help section. There was a line about resetting the desktop to the default. I could not cut and past it, but i copied it very carefully and typed it into the terminal. Nothing happened. I made sure I'd typed it write and it didn't help. Part of the example was in italics. I don't know what this means. I remember a tool that appeared when i first installed Ubuntu that could give you information to post here...but i can't find it now (tell me where it is and i'll post what i can).

Looked through gnome terminal trying to find a place where I could do something. Moved around extensively...but couldn't find out where i needed to go or what command to give.

I'm a newbie...so i could be missing something obvious. But I've been using Ubuntu for a month. I've reinstalled twice over some problems, but i've never come across this type of thing before...I'd really prefer not to reinstall. It takes over 2 hours on my computer.



Recent changes: 
-plugged in my speakers (my sound card isn't working at the moment...but it's not my top priority). Unplugged it. No change and i can't see how this would be related.

-installed a script blocker on Firefox. I have unistalled it. No change.

-I have recently created some simple folders on my desktop to clean up my desktop and moved files into the folders. I have never had problems doing this before.

-started using a USB stick a few days ago. Have encountered no problems with it.

-My printer would not print yesterday no matter what i tried, i don't know if this would be related. It was working earlier. I checked the connection. It seems fine.

What my screen looks like:
-purple for some reason.

-I can't see all of my desktop because of the resolution. I can see the edge of my folders.

-colour scheme for my wallpaper is really wierd

-there is a constant flickering on the edge that I can't get rid of.

I'm sorry if this is considered too long. I figured I would try to give as much information as I could think of so people could know everything I've noticed as different or done lately.

I can barely use the computer at the moment, can use gnome and firefox, however it is so poor i can't use it for anything other than using support forums.

My computer is a P2 450mh 20gb harddrive 192mb of memory. My modem speed is the lowest high speed in the area...twice the rate of dial up.

I would greatly appreciate any help i can get with this. I'm am totally stumped.
Starfireview

---

### Post by usernamed on 2006-06-03
[QUOTE=starfireview]When i booted the colour and resolution was off. I went to reset it under system, but it will not allow me to make a change. It says the only resolution is 640X480 (which is driving me nuts). There is also a lot of flashing going on...i only usually see that in the first three seconds when the desktop opens. The hertz rate is the same as usual which is giving me a headache rapidly. The system won't allow me to change the hertz rate either, even though i usually can. I have tried rebooting but it hasn't helped.

My computer is a P2 450mh 20gb harddrive 192mb of memory. My modem speed is the lowest high speed in the area...twice the rate of dial up.

I would greatly appreciate any help i can get with this. I'm am totally stumped.
Starfireview[/QUOTE]


Have you recompiled or altered your kernel recently?  That usually causes gfx drivers to break.  It would also be useful to know the gfx card make + model, and which gfx driver you're currently using.  Type 

```
cat /etc/X11/xorg.conf|grep "Driver"
```

and paste the output here.

---

### Post by starfireview on 2006-06-03
The only update I have done lately was the Ubdate that Ubuntu said was needed a day or two ago.

I haven't knowingly done anything with the kernel...in fact I haven't been using the terminal much the last few days (although I'll keep this in mind in the future...could help sometime to figure out a problem).

I put the command you suggested into my terminal. This is what came back:

   Driver          "kbd"
        Driver          "mouse"
        Driver          "s3virge"

Looking forward to hearing more....
Starfireview

---

### Post by usernamed on 2006-06-03
[QUOTE=starfireview]The only update I have done lately was the Ubdate that Ubuntu said was needed a day or two ago.

I haven't knowingly done anything with the kernel...in fact I haven't been using the terminal much the last few days (although I'll keep this in mind in the future...could help sometime to figure out a problem).

I put the command you suggested into my terminal. This is what came back:

   Driver          "kbd"
        Driver          "mouse"
        Driver          "s3virge"

Looking forward to hearing more....
Starfireview[/QUOTE]

OK, now we know that in x.org you're using the s3virge driver.  Do you know if your computer has an s3 graphics card?  (that sounds feasible based on the specs that you posted, but it would be nice to confirm it)

could you make a backup of your xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then open up xorg.conf in whichever text editor you feel most at home with (eg. gedit or nano or vi or emacs) by typing (gedit used in this example):
```
sudo gedit /etc/X11/xorg.conf
```

scroll down to the section headed "Device" and copy and paste that section of your xorg.conf into this post, then scroll down a bit further to the section headed "Screen" and paste that section into this post.  If you were to accidentally edit something and save the change, you'd be able to revert to your old xorg.conf by typing:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Can you give me a bit more detail on exactly when this problem began?  Have you had Ubuntu running ok, and then it broke, or has it always been this way.

Also, just out of interest, have you had the screen running at resolutions other than 640x480 in ubuntu before?

---

### Post by starfireview on 2006-06-04
[QUOTE=usernamed]OK, now we know that in x.org you're using the s3virge driver.  Do you know if your computer has an s3 graphics card?  (that sounds feasible based on the specs that you posted, but it would be nice to confirm it)[/QUOTE]

I don't know for sure. I bought the computer used (but i've been using it since January). It is an IBM Personal Computer 300PL. It can be propreitary (it wouldn't use the first stick of memory i bought because it didn't like it, tested fine at the store...they picked out the second piece when i brought the computer in and it was ok).

When you open up the computer there are no obvious "cards". I bought a used network card because Ubuntu couldn't recognize my ethernet card (called it a firewire...used network card was $5 and seemed the easiest solution).

[QUOTE=usernamed]could you make a backup of your xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```[/QUOTE]
Yes, i should be able to...i'm going to leave the suggestions a bit until i wake up though...

[QUOTE=usernamed]then open up xorg.conf in whichever text editor you feel most at home with (eg. gedit or nano or vi or emacs) by typing (gedit used in this example):
```
sudo gedit /etc/X11/xorg.conf
```

scroll down to the section headed "Device" and copy and paste that section of your xorg.conf into this post, then scroll down a bit further to the section headed "Screen" and paste that section into this post.  If you were to accidentally edit something and save the change, you'd be able to revert to your old xorg.conf by typing:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```[/QUOTE]

I haven't used any of those editors yet (i think). I used UNIX one term in unversity for a stats course and we used Piko (which sucked) couldn't be any worse...but it will take some playing.

[QUOTE=usernamed]Can you give me a bit more detail on exactly when this problem began?  Have you had Ubuntu running ok, and then it broke, or has it always been this way.

Also, just out of interest, have you had the screen running at resolutions other than 640x480 in ubuntu before?[/QUOTE]

Actually the *boot screen* is still running at a better resolution (it looks normal). UIbuntu then slows down, shows the circle that represents the mouse and THEN the resolution goes off and i get the sign in screen).

I never ran the resolution at this. I was using 1024X8* (can't remember exactly) with Ubuntu. I've also used it on Windows and for quite a while used 800X600 until web sites started using the higher resolution more. Ubuntu automatically chose a resolution slightly higher than what i used so i lowered it to the 1024 one.

In fact i loved the fact i could increase the general font size more concretely on Ubuntu (to 12 or 14 can't remember)...i didn't like the size in windows 98 at the higher resolution much, and found it a bit hard to read...the only reason i hadn't changed resoltions a long time ago (instead i put increase text buttons in many programs).

I've been running Ubuntu for a month. I have had to reinstall twice. Once a program didn't fully install (although i didn't realize that was a problem at first) and the force to fix the synaptic manager wasn't working. I hadn't found this spot yet, so i couldn't think of what else to do. It is a real pain because of the old computer and the internet connection. About two hours to install and the updates that are immediately needed take another 2-3 hours to download and install. Which is the big reason i'm trying to avoid it (there isn't much on it yet that i can't move my memory stick and reinstall although it would be a hassle).

The first time i reinstalled  my Office Program writer was having problems. However that seemed to be from my disk, so i reinstalled with another Ubuntu disk...since it was on the disk it Ubuntu was giving me problems with dowloading it (it wanted it from the CD-ROM) and because it was default software i didn't know how to uninstall and reinstall.

I do usually look around more and use the terminal more. This week though i was writing a paper that was important to me. I lost a small part of it last week when i had problems with dependencies...so i decided not to do anything until the paper was done.

The only other thing I've done was i did add a user with all powers (and now i'm having problem with the passwork...aren't i smart). I wanted to see if i could get my sound card working without messing up my current environment. I was then going to use what worked on my main account. Never did anything about it though...had problems soon after (could that be related...the problems with the printer driver started about two days BEFORE that).

Hope that helps, and thanks for the suggestions...when i'm more awake i'll start putting them in and see what happens (I'd like to write on my blog...but it'll wait...email will need to be checked tonight for one thing...uch). I use my computer a lot but i'm not being paid for my work now (as i was earlier in the year---when i had problems with the computer when i was working it was a much larger issue---the windows vulnerability got me before there was a patch. That was when i got serious about working a change to Linux.

Starfireview

---

### Post by starfireview on 2006-06-05
My system is up and running normally again. I think it will stay this way (for now anyway).

Thanks for all the help usernamed. I didn't need to get into the editor afterall but it was you identifying the driver (after telling me what to type in) that fixed the problem.

In the end i look at my Device Manager. I then looked it up on the synaptic manager---and the first response i got was the one installed --with a note saying it WOULDN'T work for my video card. It gave the information on where to find the right driver.

The driver was installed, but I REINSTALLED it which solved the problem. I don't know if the driver got corrupted or if somehow the driver settings got changed to the other one...but i'm up and running again.

Starfireview

---

