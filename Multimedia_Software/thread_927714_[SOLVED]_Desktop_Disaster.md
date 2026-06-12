---
title: "[SOLVED] Desktop Disaster"
date: 2008-09-23
forum: Multimedia Software
---

### Post by tinylasers on 2008-09-23
Hey y'all, my desktop recently crashed, and I think it might have to do with the fact that I installed some KDE applications. I am using the gnome desktop with Intrepid Ibex. 

EDIT: sorry guys I am actually using HARDY. Oops. I am so super new I got confused about the version naming conventions.  

The computer goes to a black screen with white letters after booting up, the last visible line of communication says something about not starting the KDE Desktop because it is not the default. Well, duh.  

I activated the terminal with ctrl-alt-F1. After searching the forums I have tried these commands with no luck:

sudo dpkg-reconfigure xserver-xorg

sudo apt-get install ubuntu-desktop

sudo dpkg --configure -a

sudo dpkg-reconfigure xserver-xorg startx

sudo /etc/init.d/gdm start

the xorg thing seems to be more interested in my keyboard layout than my desktop.

the fourth try listed above returned the result "startx is not installed". don't know how to do that, would installing startx help?

the last command returned "*Starting GNOME Display Manager..."
and then nothing happened. 

HELP PLEASE THX

---

### Post by luckydeveloper on 2008-09-23
> **tinylasers said:**
> Hey y'all, my desktop recently crashed, and I think it might have to do with the fact that I installed some KDE applications. I am using the gnome desktop with Intrepid Ibex. 

sudo apt-get install ubuntu-desktop



u say you have gnome desktop in Intrepid Ibex. so there will be no use in giving the above command.

Kde apps are really troublesome for gnome as far as i know..cos.. when you want to uninstall them...its really a pain in the a**...:lolflag:

if i were in your case... i would make a backup of things and try installing Intrepid again.

hey... Intrepid Ibex is under heavy testing.. and they will roll out that version soon...more stable than today. So never under estimate Intrepid Ibex:)

---

### Post by overdrank on 2008-09-23
Moved :)

---

### Post by luckydeveloper on 2008-09-23
please gimme clear details of the problem like.. " what did you do to recognize the problem ?" and things like that. 

hey can you login to your account...i mean... can you see the login screen without any probs . 

and .. did you install just kde apps or the full kde-desktop. ?

---

### Post by Paqman on 2008-09-23
First of all, Intrepid Ibex is still Alpha software. It's not recommended for use if you're not experienced at debugging Linux. I would recommend rolling back to Hardy if that's not you.

Installing KDE apps on Gnome is no problem, they work fine (but may launch slightly slower than Gnome apps). 

What was the last thing you did before the system went awry? Did you install anything? Did the system update itself?

---

### Post by luckydeveloper on 2008-09-23
> **Paqman said:**
> First of all, Intrepid Ibex is still Alpha software. It's not recommended for use if you're not experienced at debugging Linux. I would recommend rolling back to Hardy if that's not you.

Installing KDE apps on Gnome is no problem, they work fine (but may launch slightly slower than Gnome apps). 

What was the last thing you did before the system went awry? Did you install anything? Did the system update itself?

you are right... i guess he is a beginner...so rolling back might not look good on his part...there must be a solution for this...

---

### Post by ronacc on 2008-09-23
try sudo startx in a terminal by itself , if it still says not installed do sudo apt-get -i xinit   .

---

### Post by tinylasers on 2008-09-24
OK it might all be coming together now. First to answer your questions and explain step by step:

> **Paqman said:**
> First of all, Intrepid Ibex is still Alpha software. It's not recommended for use if you're not experienced at debugging Linux. I would recommend rolling back to Hardy if that's not you.

What was the last thing you did before the system went awry? Did you install anything? Did the system update itself?

> **luckydeveloper said:**
> 

hey can you login to your account...i mean... can you see the login screen without any probs . 

and .. did you install just kde apps or the full kde-desktop. ?

As noted in the edit to my original post, **I'm actually using HARDY**. Please forgive the error. 

The way this disaster started was because I wanted to manage my fonts (I do design work and wanted to clear unused fonts and add useful ones). I did not install the KDE desktop, just kfont viewer (through add/remove programs) and Fontmatrix, which I had to install manually into its own folder. Fontmatrix, BTW, barely worked (kept closing its own window when I clicked on anything), and kfont didn't have enough functionality for me, so I started editing my font library using gksudo nautilus. (I think this is where the problem starts, keep reading).

So, I got rid of a bunch of fonts I didn't want, and restarted the computer. Uh-oh, no more desktop. When I start up, I get the Ubuntu progress bar, but before I can get to the login screen, then the screen flashes on and off a few times before I get this message:

====================

*Starting anac(h)ronistic cron anacron     [OK]
*Starting deferred execution scheduler atd     [OK]
*Starting periodic command scheduler crond     [OK]
*Enabling additional executable binary formats binfmt-support     [OK]
*Checking battery state...     [OK]
Not starting K Display Manager 9kdm-kde4); it is not the default display manager. 
*running local boot scripts (/etc/rc.local)     [OK]

Then I press ctrl-alt-F1 to start the Terminal. I get this message:

Loading please wait
kinit: name-to-dev-t(dev/disk/by-uuid0d2276dc-de67-42cf-a336-c97bf419f983)=sda5(8,5)
kinit: trying to resume from dev/disk/by-uuid0d2276dc-de67-42cf-a336-c97bf419f983
kinit: No resume image, doing normal boot...
Ubuntu 8.04.1 (none) tty1
(none)login

====================

OK, now we're at where you found me at the beginning of this thread. I tried the various fixes that I listed in the first post with no result. Then...

> **ronacc said:**
> try sudo startx in a terminal by itself , if it still says not installed do sudo apt-get -i xinit   .

HERE WE GO...I tried installing xinit, the computer says I have the latest version. Nothing to see here. HOWEVER, it did give me this useful log:

====================

(++) from command line, (!!) notice, (II)
(WW) warning, (EE) error, (NI) not implemented, (??) unknown,
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 23 23:54:28 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(II) Module "ramdac" already built-in
expected keysym, gotXF86KbdLightOnOff: line 70 of pc
expected keysym, gotXF86KbdBrightnessDown: line 71 of pc
expected keysym, gotXF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 8
expected keysym, gotXF86KbdLightOnOff: line 70 of pc
expected keysym, gotXF86KbdBrightnessDown: line 71 of pc
expected keysym, gotXF86KbdBrightnessUp: line 72 of pc
[B]
Fatal server error:
could not find default font 'fixed'[/B]

waiting for x server to begin accepting connections
giving up
xinit: connection reset by peer (errno 104): unable to connect to x server
xinit: No such process (errno 3): server error.
xauth (argv):1: bad display name "(none):0" in "remove" command
aay@(none):~$

====================

Note the line that says FATAL SERVER ERROR. Is there a way to reinstall the necessary fonts without having to reinstall from disk? I did not totally delete the ones I didn't want, they are just moved to a different folder. 

Also, so this doesn't happen again, is there a program to simply deactivate fonts rather than having to move/erase them to a place where apps can't see them? Or is there a way to set the default font to a font that I actually want to use?

---

### Post by ronacc on 2008-09-24
just copy them back to where they were , you can do this from the terminal or you could use the live cd . you will probably have to use sudo to do it ( or gksudo if you use the live cd and nautilus ) . you can select the fonts in system>preferences>appearence>fonts  also many apps let you select the fonts they use which would overide the above selections for that individual app .

---

### Post by tinylasers on 2008-09-25
I tried copying the fonts back using sudo mv, didn't work and I got a little freaked out. Looking back, I probably just didn't copy the folders in the same way they were originally arranged (withoug the GUI it's hard for me to tell WHERE things are).

However, I used the install CD and launched Nautilus as root and it worked like a charm. 

Kinda messed up that one little font caused such a mess? I don't even want it. You would think the system would be able to find aonther/similar font to use but I guess not. Anyway, thanks for all the help, this has been great training.

---

### Post by ronacc on 2008-09-25
you might want to install mc , it is in synaptic , it is a linux clone of the old msdos norton comander , its a filemanager that runs from terminal , its not a gui but it makes it easier to navigate around and do things when you can't get to a gui .

---

