---
title: "Dual Monitos, Cloning - I'm about to drop linux"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by costello302 on 2007-12-06
I have a Dell D620 that I have loaded WinXp and Ubuntu 7.1 dual boot, using the linux boot manager.  Install went well, all hardware devices appear to be active and running properly.  Here is where my issue comes in...

I use this pc to connect to my primary LCD TV in my living room to watch Video stored on the HD and to browse the web.  When I go under screens and graphics to initiate the external display nothing happens.  There is a option for a second monitor which does not do anything no matter what option I select.  So at this point I searched for drivers for the 945gm chipset/950 graphics adapter.  From what I read on intellinuxdrivers or something like that it states the 945 and below are standard in the linux OS.  So one would assume I don't need an additional driver?  Regardless I had rebooted the laptop and when it comes back up it's stuck in 1024/768 and the fonts are now huge.  In the login the letters are bigger than the field, ect...  As well the OS or X? is now not fitting to the 1280/800 full screen res or whatever.  I really could care less what the laptop displays as long as it outputs to the LCD TV.

I have read post on editing some xconf file to no avail.  I as well notice that after making changes in S/Graphics I now have a xconf.x11, x12, and x13 files?

Can anyone assit, if not I will be dumping this [SIZE="4"]primative os[/SIZE] for the over bloated windows that supports my Dual Monitor needs...

---

### Post by wolfen69 on 2007-12-06
see this thread: [http://ubuntuforums.org/showthread.php?t=573484&highlight=dual+monitors+intel+945](http://ubuntuforums.org/showthread.php?t=573484&highlight=dual+monitors+intel+945)

in the future, you might want to refrain from using such words as "primitive os" if you want help. attitude wont get you anywhere. i just happened to be in a good mood. good luck.

---

### Post by rsambuca on 2007-12-06
> **costello302 said:**
> I have a Dell D620 that I have loaded WinXp and Ubuntu 7.1 dual boot, using the linux boot manager.  Install went well, all hardware devices appear to be active and running properly.  Here is where my issue comes in...

I use this pc to connect to my primary LCD TV in my living room to watch Video stored on the HD and to browse the web.  When I go under screens and graphics to initiate the external display nothing happens.  There is a option for a second monitor which does not do anything no matter what option I select.  So at this point I searched for drivers for the 945gm chipset/950 graphics adapter.  From what I read on intellinuxdrivers or something like that it states the 945 and below are standard in the linux OS.  So one would assume I don't need an additional driver?  Regardless I had rebooted the laptop and when it comes back up it's stuck in 1024/768 and the fonts are now huge.  In the login the letters are bigger than the field, ect...  As well the OS or X? is now not fitting to the 1280/800 full screen res or whatever.  I really could care less what the laptop displays as long as it outputs to the LCD TV.

I have read post on editing some xconf file to no avail.  I as well notice that after making changes in S/Graphics I now have a xconf.x11, x12, and x13 files?

Can anyone assit, if not I will be dumping this [SIZE="4"]primative os[/SIZE] for the over bloated windows that supports my Dual Monitor needs...

Hmmm...[IMG]http://itre.cis.upenn.edu/~myl/languagelog/archives/chimp.jpg[/IMG]

---

### Post by costello302 on 2007-12-06
[QUOTE=rsambuca;3903507]Hmmm

Thats about how I'm feeling right now...

I have to reinstall 3 times today just to get the display on the laptop back in order.

Gedit from the command line wouldn't let me open the xconf file and I still don't understand while multiple xconf files are being created automatically any time I adjust the display settings?

---

### Post by wolfen69 on 2007-12-06
are you doing "gksudo gedit"? try that.

---

### Post by roaldz on 2007-12-06
> **rsambuca said:**
> Hmmm

Thats about how I'm feeling right now...

I have to reinstall 3 times today just to get the display on the laptop back in order.

Gedit from the command line wouldn't let me open the xconf file and I still don't understand while multiple xconf files are being created automatically any time I adjust the display settings?

There´s only ONE real x.org config file: /etc/X11/xorg.conf
The rest is backups, in case you screw it op, you can do this: 
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
cp /etc/X11/xorg.conf.<whatever_it_appends> /etc/X11/xorg.conf
```

to open the /etc/X11/xorg.conf file in gedit in superuser mode, do this: 
```
gksu gedit /etc/X11/xorg.conf
```

Just be very careful if you edit this, make a backup like I told you.
I´m assume you´re using Ubuntu 7.10 ¨Gutsy¨.

---

### Post by costello302 on 2007-12-06
Yes, I'm using Gutsy.

I can understand and I see a backup xorg.conf, but why EVERYTIME I make a change it makes another file?

xconf.x11, x12, x13, x14, ect...

Is that the way it's supposed to work and why?  I can understand one backup or even two, but geez I have about 20 of them now, doesn't seem so streamlined to me?

Anyway, I'm at work and will have to wait until later to walk through the above posted link.

Still why is the option there when it doesn't work?  

Not to get 'tude again but I feel like I'm restoring a car and trying to drive it at the same time getting this OS to work...

BTW, I don't have these probs on my PS3.

---

### Post by costello302 on 2007-12-06
N/M, thanks for the assistance, formatted and reinstalled Vista.  I'm putting my OSX box back in the living room for my current needs.

---

### Post by rsambuca on 2007-12-06
Ohhh...  the primitive monkeys will be so disappointed.

---

### Post by costello302 on 2007-12-06
When the Intelligent life decides to make functional dual monitors a working matter for the primitive like myself I'll be back.  I don't have time between my wife/school/sports/work/side job/studying for CCNE to sit and type endless commands HOPING one might work.  I'm not knocking you guys, as this is my first dip in linux but I can sit and code all day in widows/osx and get what I need done without the hokey pokey-ness of this mess call x.

---

### Post by rsambuca on 2007-12-06
No shame in going with what works.  The computer is supposed to be our tool, not the other way around!  If you ever decide to try it again, you might get better assistance with less hostile posts.

Good luck.

---

### Post by costello302 on 2007-12-06
Hostile, haha, I didn't realize you were so sensitive.  Anyway...

w1n40w3 & 03x FTW..... for now anyway..

---

### Post by rsambuca on 2007-12-06
> **costello302 said:**
> Hostile, haha, I didn't realize you were so sensitive.  Anyway...

w1n40w3 & 03x FTW..... for now anyway..

Extra large font, in bold, calling it a primitive OS?  I just think it is a rather questionable way to go about asking for help from others.

---

### Post by ahm911 on 2007-12-06
lol i know its frustrative but i like to think of it as a learning experience ! 
on a very similar topic i would like some help i have used fiesty for 8 months now and loved it learnt alot of new code and alot of friends installed it as double boot with their windows and macs. anyway my question is im trying to dual monitor with my samsung plasma using svideo. i followed a tutorial which scripted  a "switchmon " command with various .xorg files. one of the options worked but the plasma had perfect resolution my laptop had a very a symmetrical display. 

Then i found the graphics and screens option in the adminstrator .. whne i tried changing that to fit my needs thinking it would automatically reset my .xorg files.. it actually disabled my monitor. my display works while booting till i get up to login then i get a blank screen. 

im on my windows xp now on the same laptop which is a toshiba sattelie A100-Ta6 centrino duo 1.73 1 gig ram intel video card.. but i cant access gutsy. 

in dire need of help

EDIT : i am running gutsy right now

---

### Post by costello302 on 2007-12-06
> **rsambuca said:**
> Extra large font, in bold, calling it a primitive OS?  I just think it is a rather questionable way to go about asking for help from others.

Just larger font, no bold.

If I gave a PC with this OS on it to my mother or father they would have no clue where to begin.  And I'm talking about install, making changes ect... 

In my mind it seems if this is what your community is pushing for, becoming more mainstream and moving into the real world desktop realm (not the one where geeks live and have the time and know how to figure things out on there own) then why such the difficulty in performing basic funtions, on top of adding a feature that did not even work?

---

### Post by rsambuca on 2007-12-06
> **costello302 said:**
> Just larger font, no bold.

If I gave a PC with this OS on it to my mother or father they would have no clue where to begin.  And I'm talking about install, making changes ect... 

In my mind it seems if this is what your community is pushing for, becoming more mainstream and moving into the real world desktop realm (not the one where geeks live and have the time and know how to figure things out on there own) then why such the difficulty in performing basic funtions, on top of adding a feature that did not even work?

Installation can be tough, depending on your hardware.  But that is the same for Windows too.  Once Ubuntu is installed, though, it is just as easy as Windows or OSX to use.  My 67 year old mother is completely happy with it.

Anyways, like I say, some people come to the forums and are polite and ask for help.  Others come with a sense of entitlement and demand it.  Since this is strictly a volunteer environment, I have a choice as to who I can help...

---

### Post by dottedquad on 2007-12-06
> **rsambuca said:**
> Installation can be tough, depending on your hardware.  But that is the same for Windows too.  Once Ubuntu is installed, though, it is just as easy as Windows or OSX to use.  My 67 year old mother is completely happy with it.

Anyways, like I say, some people come to the forums and are polite and ask for help.  Others come with a sense of entitlement and demand it.  Since this is strictly a volunteer environment, I have a choice as to who I can help...

Don't feed the troll! :mad:

---

### Post by costello302 on 2008-01-11
I have since uninstalled linux due to not being able to get my external LCD to function - properly...  I was quite disappointed in the fact they have everything in the display options there that look like what I need yet don't offer any functionality whatsoever.

Does the new version of Ubuntu, being tested and released in April from what I hear, going to natively support dual monitors and external displays?

---

### Post by crumja on 2008-01-11
Linux has supported dual monitors for several years now. Recent changes to X.org and especially xrandr have made it easy. On all of my machines, including D620, I just plug in to another monitor and it's usually autodetected. If not, try using the command line tool xrandr to output.

Keep in mind that LCD TVs are special in that they only take special resolutions - 1368x768 or some arcane numbers, so specify that when outputting using xrandr.

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by billybobshibal on 2008-01-11
I'm an AV tech and generally find that intel chipset to be a pain in the a**, even on windows getting that thing to sync to projectors can be a royal pain. Cloning it can sometimes be impossible where as extended desktop usually works. The s-video output on my desktop works great in ubuntu (nvidia 7800gs card) but on my laptop (ati xtremely200mediocre card) is a lesson in futility. Anyways enjoy the DRM on vista! Where as us Cro-Magnan men will continue using our media freely:)

---

### Post by costello302 on 2008-01-11
Oh I ditched Vista as well. Bet though that I have plently of DRM free media.  Bittorent and VLC are my friends.  Anyway, I'll try the link above this weekend and see what I get.  If you are using a D620 I would be very interested in seeing your config...if you could copy and paste that section I would greatly appreciate it.  The option for the dual monitor/extended monitor was completely greyed out no matter if I booted with or without the LCD connected and no matter what config I had edited in xconf.  And something even more strange is that after attempting to boot twice with the monitor setup linux would lock on boot.

:confused:

---

### Post by Shibby73 on 2008-01-12
Ubuntu - "I am what I am because of who we all are"

I think before criticizing anything one "consumes" for free related to the computer one ought to study a little history or some anthropology or whatever surrounding the internet.  Why?  Because common sense is apparently not very common per Samuel Clemens and technology seems to breed frustration in many of us... but some have banded together to overcome these PRIMITIVE DRIVES.

If anyone suggests your a "troll" or doing something "bad" then check yourself... resist the temptation to become defensive.

Here's a tip -  when people politely ask you to refrain from insulting them and what they are interested in and then THEY CONTINUE to offer you help RESPOND IN KINDNESS! --> adjust your tone in your next post accordingly, apologize for venting your frustrations... your ingraciousness is NOT appreciated. (I imagine this is true even of people being paid to "serve you" and others in the society where you come from and live in outside of the internet and virtual world... its a fairly common human cultural universal).  Flame off... NOT on.

If you can't... then I would suggest you reboot to whatever television your used to experiencing as a CONSUMER... and spend all of your money on tech support phone calls in the future... if you think you might be able to do join HUMANITY and be treated as an equal and "peer" then read this:
[http://www.arachnoid.com/freeware/index.html](http://www.arachnoid.com/freeware/index.html)

And then do some searching about Netiquette BEFORE replying... take some time to fix your appearance online as if you were posting somewhere that would be searchable via GOOGLE for a small portion of eternity... how do you want to be viewed?  Will YOU evolve or persist in your prior state of mind?  

To save you time in this vitally important journey away from being a grumbling "primitive"... you could read these suggestions:  [http://www.stansgnosticus.net/netiquette](http://www.stansgnosticus.net/netiquette)

To the community... I greatly appreciate your help... you have helped me save $150 per month... and I recently invested this savings into a 22" LCD Monitor 1600x1080 ... I have noted that it mainly works well on my primitive laptop that dual boots (WINXP & UBUNTUSTUDIO) in WINXP as an extended monitor.  I'd love to see how it looks and works in LINUX... being able to view code, the terminal and manipulate an image capture of my desktop screen for making a tutorial website would be great fun during my spare time as a resident physician (joke about time intended).

QUESTION:
1) Should I persist to use UBUNTUSTUDIO or move back to one of the regular distros before delving into applying any existing monitor solutions?
2) I get a "out of range" when I do the first primitive step of booting into LINUX (UbuntuStudio) with the monitor simply attached and my laptop screen is black by the time I hear the ping (when it requests my login)... obviously I need to boot without it attached and make some setting adjustments before attaching the monitor.

Basic tips welcome.

Thank you,

~Shibby73~
[www.stansgnosticus.net](www.stansgnosticus.net)

My apologies for my apparently long and inflammatory retort... I know I've been a frustrated person/user more than once on these forums and have appreciated the journey that still resulted.  The first Linux communities I don't believe were as tolerant and that is one reason Ubuntu is becoming popular among the laity.  I do think we are all helping each other evolve as a society out of the unfortunate cultural by-product of our commercialized internet's devolution.

---

