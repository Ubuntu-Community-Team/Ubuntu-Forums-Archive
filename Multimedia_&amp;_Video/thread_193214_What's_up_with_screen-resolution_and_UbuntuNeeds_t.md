---
title: "What's up with screen-resolution and Ubuntu?Needs to be fixed before ubuntu rules all"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by Osamabingandhi on 2006-06-09
I've tried some more distros than ubuntu and what they have in common is screen-resolution trouble. The first thing an linux user need to fix is the screen resolution. That's where the trouble begins. I really believe a lot of people throw linux in the trashcan because of this! To write comands in the terminal will scare anyone especially when you are not sure what to write and what to do when you finally figure out how to do it. You have search the forums like a maniac and then trial and error.:confused:  I broke my ubuntu by doing this! To make a new installation was not very funny.:cry: 

How do you know what to write in safe mode to fix the xorg.conf? Ahhh i feel this frustration hanging over me and how easy it would have been for me to give up. When a total beginner is thrown into system modification on this level it's bad.

What i have understood is that linux systems only support up to 1024x768 resolutions. In this day of age most people have 1280x1024 on their monitors. And almost everyone needs to change the system settings! I can't believe that this isn't fixed yet. It seems like i should not be a impossible thing to correct.

After that what is really missing in ubuntu is an official cd with the codecs nvidia drivers, flash, java, more games, newer alsa sound drivers etc...and other things that for most people is a must have. I know work is being done here and automatix and easyubuntu is striving for this. When i go home to my father's computer with just a modem i will forget about ubuntu. To sit a couple of hours downloading is too much trouble. This gives me one good alternativ, vector linux. But ubuntu is better in other ways, but the fact is that a lot of people don't have broadbands yet and then you gives them big trouble. An mix of easy ubuntu and automatix in a 700meg super-cd would be perfect!!! 

Don't get me wrong here i really like ubuntu a lot! Linux will rule the world, and ubuntu has come such a long way. Things i talk about is minor things but extremly important. For med almost everything else worked out of the box for exept these monitor issues and some sound problems. It will be very little windows for me after this...Linux is da shit!:D

---

### Post by Ivhassel on 2006-06-09
[QUOTE=Osamabingandhi]I've tried some more distros than ubuntu and what they have in common is screen-resolution trouble. The first thing an linux user need to fix is the screen resolution. That's where the trouble begins. I really believe a lot of people throw linux in the trashcan because of this! To write comands in the terminal will scare anyone especially when you are not sure what to write and what to do when you finally figure out how to do it. You have search the forums like a maniac and then trial and error.:confused:  I broke my ubuntu by doing this! To make a new installation was not very funny.:cry: 

How do you know what to write in safe mode to fix the xorg.conf? Ahhh i feel this frustration hanging over me and how easy it would have been for me to give up. When a total beginner is thrown into system modification on this level it's bad.

What i have understood is that linux systems only support up to 1024x768 resolutions. In this day of age most people have 1280x1024 on their monitors. And almost everyone needs to change the system settings! I can't believe that this isn't fixed yet. It seems like i should not be a impossible thing to correct.

After that what is really missing in ubuntu is an official cd with the codecs nvidia drivers, flash, java, more games, newer alsa sound drivers etc...and other things that for most people is a must have. I know work is being done here and automatix and easyubuntu is striving for this. When i go home to my father's computer with just a modem i will forget about ubuntu. To sit a couple of hours downloading is too much trouble. This gives me one good alternativ, vector linux. But ubuntu is better in other ways, but the fact is that a lot of people don't have broadbands yet and then you gives them big trouble. An mix of easy ubuntu and automatix in a 700meg super-cd would be perfect!!! 

Don't get me wrong here i really like ubuntu a lot! Linux will rule the world, and ubuntu has come such a long way. Things i talk about is minor things but extremly important. For med almost everything else worked out of the box for exept these monitor issues and some sound problems. It will be very little windows for me after this...Linux is da shit!:D[/QUOTE]

Run this from command line:
```

sudo dpkg-reconfigure xserver-xorg

```

There you can select your screen resolution, if it isn't set automatically.

---

### Post by Osamabingandhi on 2006-06-10
That doesn't work for me...Thanks anyways. I got it fixed but what i want to say is that ubuntu need a better way to modify settings for monitors and graphic cards. The way it is now is truly bad.

---

### Post by jokeypiu2 on 2006-06-11
excuse me HOW did u do that? i have the same problem with my screen resolution and im very interested in ubuntu but i cant do nothing with 1024x768, i have a 915gm ideo cars, is a laptop, maybe u have the same video card
! please if u know how to fix the problem post it, there are a lot of people with the same problem!


;) :rolleyes:

---

### Post by Torquemada28 on 2006-06-11
> **Ivhassel]Run this from command line:
```

sudo dpkg-reconfigure xserver-xorg

```

There you can select your screen resolution, if it isn't set automatically.[/QUOTE]
I tried that said:**
> That doesn't work for me...Thanks anyways. I got it fixed but what i want to say is that ubuntu need a better way to modify settings for monitors and graphic cards. The way it is now is truly bad.
I beg of you, tell us how you fixed the problem.
As I mentioned earlier, I'm a linux noob, so explain it like you're conversing with an idiot. ;)

---

### Post by Patrick-Ruff on 2006-06-11
you need to manually edit your xorg file.

---

### Post by Torquemada28 on 2006-06-11
[QUOTE=Patrick-Ruff]you need to manually edit your xorg file.[/QUOTE]
Did I mention I'm a linux noob?
*checks previous post* 
Hmm, twice.

For a start, maybe you could tell me how to edit xorg.conf when it tells me I haven't got permission to do so?
That would be rather helpful at this point.
Thanks in advance.:)

---

### Post by Patsoe on 2006-06-11
A lot of problems with GNU/Linux user-friendliness _have_ been solved over the last few years. What I think is holding back these developments in the graphics area is the fact that the graphics chip companies are all very sparse in giving implementation details to the open source world. If nobody knows about the internals of the "fglrx" or "nvidia" driver, then nobody can help that there are issues with those all the time...

So, I would say, let's all email our graphics chip vendors to complain... 

In my opinion, they should at least help to develop a reliable, open source 2D driver. One that autodetects all the little switches that we are now setting by hand. If they want to protect their 3D "knowledge", then they could perhaps make a modular design, where the 2D bit is open source, and the 3D bit is an add-on driver. Still less than ideal, but at least we would all be able to install and boot to a working desktop environment straight away...

(with all due respect to the xorg people, there are indeed too many problems with the "ati" and "nv" drivers to make me think of those as the reliable drivers I'm talking about. The xorg people can't help this much I guess, being starved for information. The chip vendors should help there)

---

### Post by HankB on 2006-06-12
In all fairness to the Xorg and Ubuntu developers, a *lot* of progress has been made. One of the reasons I'm sticking with Ubuntu at the moment is that I can do a laptop install and at least for me, the video resolution comes out right. (*) I suppose this doesn't always happen, but when it doesn't, the best thing is to provide as much information as you can to help the developers identify and resolve the problem.

(*) I've gotten the right resolution on:

   ATI Radeon XPRESS 200M (AMD64 - HP L2000 laptop)
   1280x768 - an odd size

   Neomagic Corporation NM2200 [MagicGraph 256AV]
   Thinkpad 600e
   1024x768 (IIRC)

   ATI Radeon Mobility M7 (Thinkpad T30)
  1400x1040 - also a bit odd

I know this doesn't help directly, but it does point out the problem may not be as wide spread as you seem to think.

And I can tell you that you should be awfully happy that we've moved on from the day when we had to manually construct modelines!

---

### Post by takingheights on 2006-06-19
Hey guys,

    This isnt the first time i install Ubuntu, but this is the first time i install 6.06, i have one great problem that i need fixed ASAP. My screen resolution is stuck at 1024x768. I am using Microsoft Virtual PC to run this btw. I am currently helping out a company by taking screenshots of their homepage. They asked me to take a few screenshots using 3 different resolutions (800x600, 640x480 and 1024x768 ). When i try to change my resolutions i get a blurr of the desktop (like the bad starts on an NES) and i am sent back to the login page. I'm in great need of assistance and if you could please guide me through to find my resolution i would greatly appreciate it.

     Thanks a bunch,
             TakingHeights

---

### Post by Marvin@UKS on 2006-06-21
similar problem but mine's at the very beginning of the installation of xubuntu and kubuntu 6.06 (i tried did xubuntu 1st and when i had problems, decided to try kubuntu)

when i try to install, both disro's show me a 320 x something screen "i'm going to ask a few questions" etc, the bottom part of which is off the display and i can't 'slide' to it.  i assume that there's a continue box but as i can't see it, i can't click the thing.
i previously used an nv mx400 video card but when an earlier release wouldn't install it was suggested linux preferred older ones so went back to my emergency card, an ati 3d charger - pci too!

words of one syllable plez - total no brainer noob!

p.s.
preferred tipple, Hot Lava Java
(which is a 6 on the 1 to 5 coffee scale)
... or is that advertising?

---

### Post by Aldoliel on 2006-06-22
I have to say that i envy you guys being stuck in 1024x768, how i would love to reach such heights of resolution. Whilst I sit here typing this out in 640x480 where even some of the configuration dialogs are larger than the screen.
It's not that i mind, it's just that it was fine before i upgraded last week, i think the i810 driver got broken somewhere. Anyway, i'm off for food before i try some more solutions that i think could work.

---

### Post by Punio4 on 2006-06-24
The way I enabled the resolutions was to type *some* command which asked me for my resolution, vertical, and horrizontal refresh rate. After that, it printed out a code, which i manually pasted in the bottom of the [device] section of xorg.conf.
It's just a text file, but to edit it you'll have to login as root or type:
sudo gedit /etc/X11/xorg.conf.
To lower my login screen resolution, I had to delete all unnecesarry resolutions listed at the bottom...

---

### Post by Timokl on 2006-06-24
I am also a Linux Newbie, and I had that same problem with the resolution at first, but with the help of the beautiful ppl in this forum, I managed to get it right. At the moment, my notebooks runs in 1280x800 without problems.

These are some hints I have learned: Please correct me if I am wrong.

[LIST]Make sure that you have the correct driver for your graphics adapter. Don't use the *standard* drivers, as they only give you access to the canonical resolutions (no pun intended!), like 640x400, 800x600, and 1024x768.
[/LIST]
[LIST]Learn to use this forum (and search engines) effectively, like look for information that matches with **your hardware**. When it comes to proprietary drivers (like for ATI cards), you need to stick with the specific information for this piece of hardware.
[/LIST]
[LIST]Also search the Ubuntu Wiki at [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/), as you can find a lot of (mostly) understandable and doable step by step instructions.
[/LIST]
[LIST]Provide information about your machine in the forum, e.g. the output of *lspci*, or post your conf files. Mostly, ppl can tell you where there is the mistake. :D 
[/LIST]
[LIST]Back up your conf files before you change them!!!
[/LIST]
[LIST]Something went wrong with your conf file, and the system does not start up correctly? Learn to use the command line to get back to a back uped files. There is just a few commands you need:
[LIST]*mv*[/LIST]
[LIST]*cp*[/LIST]
[LIST]*cd*[/LIST]
[LIST]*ls*[/LIST]
[LIST]*gedit*, or *nano* (when there is no gui available)[/LIST]
[LIST]and of course: *sudo*[/LIST]
[/LIST]

It cannot be argued of course, that Linux has a steep learning curve at the beginning, because things work differently than under Windows. But in my experience, in many cases somebody will tell you why something does not work and how to solve the problem. With Windows, it was mostly: It works, or not. Nobody knows, and quite often nobody has a solution to a problem.

At least my experience. :rolleyes: 

Bye,
Timo

---

### Post by tlg on 2006-06-24
[QUOTE=Ivhassel]Run this from command line:
```

sudo dpkg-reconfigure xserver-xorg

```

There you can select your screen resolution, if it isn't set automatically.[/QUOTE]

Thanks, that was just what I was looking for.

---

### Post by Aldoliel on 2006-06-28
Well, i got mine fixed, thanks to a lot of searching and an update to a driver that didn't break when i used it :D

Just had to make sure everything was configuerd correctly.

---

