---
title: "live usb not getting desktop (unity?)"
date: 2011-01-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by candtalan on 2011-01-03
I have a desktop machine with a motherboard 
P4i65GV, that is, not 'old' hardware.
lspci shows
VGA compatible controller Intel Corp 82865G (rev02)

When using natty daily build (from this morning) in a unetbootin live usb stick, it boots up towards a live session but does not go into the expected desktop, which I guess is Unity (?), I only see Examples folder and an icon Install Ubuntu 11.04

But when I use the usb stick in an asus eeepc 900, I see a complete desktop, with left side icons.

Any suggestions please as how to get it run fully in the desktop machine?

tia

---

### Post by cariboo on 2011-01-03
If your graphics adapter doesn't support 3D, you won't be able to use Unity, what happens when you log out and select the classic desktop? Use ubuntu for a username with no password to log in again.

---

### Post by candtalan on 2011-01-03
I do not actually see any method of doing anything, in old money I see no panels, and there is no access to any apps, including terminal. Basically it is a partial desktop.

So it is useless to a normal live CD user.

I also do not see how I can logout of the live session. What command will cause a live session logout?
I can get a gnome terminal by opening the Examples folder, (nautilus?) and I can search for terminal, I see gnome-terminal, and start it. 

Then what?

tia

---

### Post by wojox on 2011-01-03
```
sudo logout
```

---

### Post by candtalan on 2011-01-03
> **wojox said:**
> ```
sudo logout
```

OK, thanks, but the objective is to try to use apparently a non 3D graphic card  with the live session.

A reboot starts the live session again, and still, the desktop does not complete.

---

### Post by wojox on 2011-01-03
After you enter your userName you should be able to choose Classic Desktop from the panel below.

---

### Post by candtalan on 2011-01-03
> **wojox said:**
> After you enter your userName you should be able to choose Classic Desktop from the panel below.

in an incomplete live session?
I do not see any method of getting to enter a username. Am I missing something?

---

### Post by wojox on 2011-01-03
In the GDM.

---

### Post by candtalan on 2011-01-03
I dont think I have the gdm (gnome display manager?) I see no gnome panels, I seea totally blank desktop space except for the install icon and the examples folder. Is this what you expect?

edit
(I can also see the background graphic)

---

### Post by ajgreeny on 2011-01-03
It should appear at the login screen of the live USB, but only after you have logged out and chosen the username to login.  _Do not reboot_ as that will not help at all, but just go straight to the desktop again.

If you can see no way to logout, and the **sudo logout** does not work (I didn't know that one myself), just use **Right Alt+Print Screen+K**, which will kill your xsession and should then go to the login screen.  There you can use *ubuntu* as the userlogin, then use the session menu for Classic Desktop, and finally just hit *enter* at the blank password screen.

---

### Post by candtalan on 2011-01-03
> **ajgreeny said:**
> It should appear at the login screen of the live USB, but only after you have logged out and chosen the username to login.  _Do not reboot_ as that will not help at all, but just go straight to the desktop again.

If you can see no way to logout, and the **sudo logout** does not work (I didn't know that one myself), just use **Right Alt+Print Screen+K**, which will kill your xsession and should then go to the login screen.  There you can use *ubuntu* as the userlogin, then use the session menu for Classic Desktop, and finally just hit *enter* at the blank password screen.

(I did try sudo logout but it caused a shut down)
Right Alt+Print Screen+K
works to produce a login screen! Ah, no mouse cursor. OK, Tab and Return gets to a password invite.

But, lacking a pointing device  I can not yet get to the session-type choices..... It is currently in its default of Ubuntu Desktop session. I have tried adding a usb mouse also (to the existing ps2 mouse) but still no cursor. 
Ah
ctrl alt and some blind use of the mouse left clicks aiming around the bottom of the display activates the lower panel menus and I  could  choose Classic Desktop.
:-)

Get error window:
'Indicator Applet Session' has quit unexpectedly
if you reload a panel object,  it will automatically be added back to the panel
don't reload, reload

(reload)

then clock has quit unexpectedly (similar message)
then lots of different similar errors. 

The cursor is a corrupted form, but is functioning.
System Preferences Appearance
only shows
Theme background fonts tabs, no graphics choice.

Something not working at all well with the graphics.

At least I managed to arrive at the classic desktop, thanks for the help. Not sure I can do much more with the live session at the moment.

---

### Post by candtalan on 2011-01-03
How do I file a bug relating to the Live USB/CD not working properly? I know about an installed system, apport  whatever. But a live cd problem? How do I even start to file a bug?
tia

edit
I have found how to file a non package specific bug

---

### Post by cariboo on 2011-01-03
You should be able to use Ctrl-Alt-T to open a terminal, you should then be able to use sudo logout to get to the login screen. Are you using a recent daily build iso?

---

### Post by cariboo on 2011-01-03
> **candtalan said:**
> How do I file a bug relating to the Live USB/CD not working properly? I know about an installed system, apport  whatever. But a live cd problem? How do I even start to file a bug?
tia

edit
I have found how to file a non package specific bug

Have a look at the [iso testing team page]("http://iso.qa.ubuntu.com/"), your bug may have been filed already. Just hover your mouse cursor over the bugs to what it's about.

---

### Post by candtalan on 2011-01-04
> **cariboo907 said:**
> You should be able to use Ctrl-Alt-T to open a terminal, you should then be able to use sudo logout to get to the login screen. Are you using a recent daily build iso?

I am using daily build iso from date 2011 January 03.
when the live CD has booted and run as far as it can - that is, to an incomplete desktop, then
Ctrl-Alt-T does not bring up a terminal.
However, Ctrl-Alt-F1 does bring a virtual terminal and then
sudo logout 
responds with command not found

---

### Post by candtalan on 2011-01-04
> **cariboo907 said:**
> Have a look at the [iso testing team page]("http://iso.qa.ubuntu.com/") 
Thanks, I was beginning to think I needed information like that....
I will follow that up. 
The bug I had already filed is
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/696999](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/696999)

---

### Post by jerrylamos on 2011-01-04
> **candtalan said:**
> I dont think I have the gdm (gnome display manager?) I see no gnome panels, I seea totally blank desktop space except for the install icon and the examples folder. Is this what you expect?

If you can see the install icon, then try right click on the mouse to create a launcher.  Pick any name.  For command use: gnome-terminal
Should create a terminal icon.
Double click on that and try:
gnome-panel &
for desktop panels.
Also, see the thread "No Gnome panel" for suggestions like in the gnome-terminal:
gconftool-2 --shutdown
rm -rf ~.gconf/apps/panel
pkill gnome-panel
I use that so much I made it into an exec.
On my ati radeon mobility 7500 the usual Alt-F2 and Ctrl-Alt-T do not work.  On CD live (or USB live I assume) I have to do:
Ctrl-Alt-F1
sudo service gdm stop
sudo service gdm start && gnome-panel &
in order to get a screen with the install icon, then proceed as above creating a launcher.  The resulting desktop panels are somewhat usable with some serious problems.

Oh, I forgot, for the ati radeon mobility 7500 I also have to put 
radeon.modeset=0
in the boot line.  My ati radeon xpress 200 boots O.K. into Unity, even from USB, the only one of my four test pc's that will.  25% success rate, how's that for market share.

Fun trying to use an Alpha 1 isn't it, with anything but the hardware the "Unity" developers are using.  Maybe (or maybe not) after they shake the big bugs out of "Unity" Ubuntu might think about the rest of us.  There's always Lucid 10.04 LTS or Lubuntu or ...

Jerry

---

### Post by candtalan on 2011-01-05
Note: now using natty daily current of date 2011 january 05
used in usb stick with unetbootin. It booted  into the desktop with no unity nor gnome panels (second try, the first try hung)

> **jerrylamos said:**
> If you can see the install icon, then try right click on the mouse to create a launcher.  Pick any name.  For command use: gnome-terminal

thanks, yes but I also went to /usr/bin/ to get the executable link.... :-)

> 
Should create a terminal icon.
Double click on that and try:
gnome-panel &
for desktop panels.

Works, thanks

Today, when panels are in place there is no corruption of the mouse or display. Accepted that it did not boot into its desired desktop display, it is now a usable system.

---

### Post by tormod on 2011-04-15
> **cariboo907 said:**
> You should be able to use Ctrl-Alt-T to open a terminal, you should then be able to use sudo logout to get to the login screen. Are you using a recent daily build iso?
Where is your "sudo logout" coming from? How would that combination of keywords possibly make sense? "logout" is a shell built-in that only works in a login shell, like on a console. And of course to be run as the user who wants to log out. "sudo" is for running a system command with root privileges. Please do a minimal amount of verification to avoid misleading and confusing other users.

BTW, the Canonical usability "experts" have now removed the logout option in the live session, ([https://bugs.launchpad.net/ubuntu/+source/casper/+bug/750140](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/750140)) so you are left with hacks like "killall gnome-session" to log out...

---

