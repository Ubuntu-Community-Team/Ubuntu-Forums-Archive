---
title: "GNOME Shell Testing"
date: 2010-05-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Merk42 on 2010-05-07
[b]This thread is for testing support and technical discussion.
Opinions should go to the [Community Cafe thread]("http://ubuntuforums.org/showthread.php?t=1457428") or ideally [the GNOME Shell mailing list]("http://mail.gnome.org/mailman/listinfo/gnome-shell-list")[/b].

I made this thread again because as before, I figured the sort of people that would install and test pre-release versions of a new UI would be the sort of people that install and test pre-release versions of Ubuntu.

**What is GNOME Shell?**
GNOME Shell, for those of you that do not know, is a user interface change to GNOME. With it, brings Mutter a combination of Metacity and Clutter, managing the windows. Say goodbye to compiz as it won't be compatible.

GNOME Shell will be [released as **one part of GNOME 3** in March of 2011]("http://mail.gnome.org/archives/devel-announce-list/2010-July/msg00003.html") it [will not be default in 10.10]("https://wiki.ubuntu.com/MeetingLogs/openweekLucid/AskMark") though there will be an optional package.

**What does it look like?**
Here is GNOME Shell. 

The active application near "Activities" has a menu upon clicking. Clicking on the date or username provide a calendar and menu respectively
[IMG]http://www.markecurtis.com/etc/gnomeshell/menus.png[/IMG]

Currently some applications are open but minimized. Where are they?
This is the Activities overview, where you run and manage "Activities"
[IMG]http://www.markecurtis.com/etc/gnomeshell/overview.png[/IMG]

More applications can be run either by searching for the name in "find", or clicking the bar that says applications
[IMG]http://www.markecurtis.com/etc/gnomeshell/moreapplications.png[/IMG]

You can easily add or subtract workspaces with the + and - buttons. By default workspaces are organized in wall form. The scrollbar, or smaller boxes let you switch among them
[IMG]http://www.markecurtis.com/etc/gnomeshell/workspacewall.png[/IMG]

You can also view all workspaces at once in a grid layout
[IMG]http://www.markecurtis.com/etc/gnomeshell/workspacegrid.png[/IMG]

Oh look, an instant message! Unlike the passive notify-OSD, clicking on this will bring up the window
[IMG]http://www.markecurtis.com/etc/gnomeshell/messages.png[/IMG]

If no action is taken, it resides in the lower right, viewable upon hover.
[IMG]http://www.markecurtis.com/etc/gnomeshell/messageexpand.png[/IMG]


**OMG GNOME SHELL IS AWFUL! I'm moving to xfce/Windows/an abacus**
Calm down. Look at the [GNOME 3 Myths]("http://live.gnome.org/GNOME3Myths")
> **MYTH: GNOME won't support the current panel and window manager anymore and I don't want to use GNOME Shell**

**TRUTH: The GNOME 2.x panel and Metacity (the window manager) will still be available.**
Downstream distributions such as Fedora, openSUSE and Ubuntu will have the option to include them in their distribution. You will be able to install them just as now you can install sawfish, compiz, etc inside your GNOME session. (There are no plans to support GNOME panel applets in GNOME Shell, TBA. This mailing list post has some information.) 


**How do I Learn More?**
[LIST]
[*]Read up on [the design document]("http://www.gnome.org/%7Emccann/shell/design/GNOME_Shell-20091114.pdf").  It gives an idea of where they'd like to go and why.
[*]If that's too much of a read, look at [this brief synopsis]("http://gnomejournal.org/article/85/easy-breezy-beautiful-gnome-shell") on GNOME Shell.
[*]Look at the [GNOME Shell cheat sheet]("http://live.gnome.org/GnomeShell/CheatSheet") for features.
[/LIST]

**How do I Try it?**

Running Jaunty, Karmic, Lucid and Maverick there are three ways to try GNOME Shell
[LIST]
[*]Install the gnome-shell package (easy but out of date)
[*]Use the [Ricotz PPA]("http://ubuntu-tweak.com/source/gnome-shell-testing/") (slightly harder, but more up to date)
[*]Build from source (more difficult, but up to date when something is added, provided you rerun jhbuild build)
[/LIST]
**As of Virtualbox 3.2.6 GNOME Shell will not run in a virtual machine, even with desktop additions installed**

Building from source is a bit more complicated than the GNOME instructions say. So fire up a terminal
[LIST=1]
[*]sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils
[*]curl -O [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh)
[*]/bin/bash gnome-shell-build-setup.sh
[*]Get jhbuild (not a command line entry)
[LIST]
[*]For Lucid via repository, package name "jhbuild".
[*][From Jaunty]("http://packages.ubuntu.com/en/jaunty/jhbuild")
[*][From Debian]("http://packages.debian.org/unstable/devel/jhbuild")
[/LIST]
 
[*]jhbuild build
[/LIST]

**IF YOU HAVE TROUBLE BUILDING**
**Hey it keeps "hanging up unexpectedly"**
Quit building and run
```
 pushd ~/gnome-shell/source/ && git clone git://git.gnome.org/gtk+ gtk3 && popd
``` 
then re run jhbuild build
**I'm getting a lot of "undefined reference" errors**
try ```
rm ~/gnome-shell/install/*.la /usr/lib/*.la
```
Then jhbuild build
If it still doesn't work, delete the ~/gnome-shell folder and try again

**Yay! It's finally done building! Now what?**
To run
[LIST=1]
[*]cd ~/gnome-shell/source/gnome-shell/src
[*]./gnome-shell --replace
[/LIST]

To quit GNOME Shell and return to the panels
[list=1[*]Go to the terminal
[*]hit CTRL-C[/list]

To update (check the [commit log]("http://git.gnome.org/browse/gnome-shell") for anything new)
[LIST]
[*]jhbuild build (rebuilds updated files)
[*]jhbuild build -f -a -c (builds all gnome shell files)
[/LIST]

To remove (if you want to do a clean install, or just remove it because you don't like it)
[LIST]
[*]Delete the folder gnome-shell in your home directory (assumes build from source)
[/LIST]

If you want to make it your default, put "gnome-shell --replace" in your Startup Items

**Love it? Hate it? Have a suggestion? Make your voice heard in the [GNOME Shell mailing list]("http://mail.gnome.org/mailman/listinfo/gnome-shell-list")**

---

### Post by cariboo on 2010-05-07
I find I use the search bar more often then the menu to find an application that I don't have in Docky. I usually only have to type one or two letters to find the app I want.

---

### Post by JCoster on 2010-05-07
I'd test GS more but at the moment it's unusable due to corrupt font rendering..  Any ideas?

Using the 'radeon' graphics driver.  Even if I try using it (despite fonts being unreadable) it crashes and restarts GDM.

Cheers,
JC

---

### Post by Madspyman on 2010-05-07
Doesn't work using the flgrx drivers in Lucid. It flickers every time I open something and skew the menus on back clicks. Using the open drivers it works better, with the exception of a white broken line that appears occasionally in the window upon resizing, and sometimes the colors for the icons change. Still works flawlessly in my Karmic partition under the same conditions.

---

### Post by Peter09 on 2010-05-07
> Doesn't work using the flgrx drivers in Lucid. It flickers every time I  open something and skew the menus on back clicks. Using the open drivers  it works better, with the exception of a white broken line that appears  occasionally in the window upon resizing, and sometimes the colors for  the icons change. Still works flawlessly in my Karmic partition under  the same conditions.

Same here, unusable at the moment.

---

### Post by descendent87 on 2010-05-07
Also uninstallable in maverick currently due to librsvg2-dev dependencies. Anyone who want's to try it either install from repo's (very old version) or try the PPA

---

### Post by KdotJ on 2010-05-07
I'll be honest, I like gnome shell, but I do love Compiz. I know that that gnome3 will have effects in it, but will we have stuff similar to the cube? the open/close animations? 3D windows?

I'll be sad to move away from Compiz and the way gnome is now. I know that I don't have to move up, but I like to keep up.

---

### Post by hikaricore on 2010-05-07
KDE4 has these things so I'm sure Gnome will implement them in to their terrible shell as well.

---

### Post by dyltman on 2010-05-08
Has anyone tried the replacement for nautilus; GNOME Activity Journal?

---

### Post by descendent87 on 2010-05-08
> **dyltman said:**
> Has anyone tried the replacement for nautilus; GNOME Activity Journal?
Not too up on Gnome 3 as I'm a KDE user but I'm pretty sure activity journal isn't replacing nautilus

---

### Post by dyltman on 2010-05-08
> **descendent87 said:**
> Not too up on Gnome 3 as I'm a KDE user but I'm pretty sure activity journal isn't replacing nautilus

[http://live.gnome.org/GNOME3Myths](http://live.gnome.org/GNOME3Myths)

> The GNOME file manager (Nautilus) will be removed from GNOME and replaced with the GNOME Activity Journal!

---

### Post by autocrosser on 2010-05-08
> **descendent87 said:**
> Also uninstallable in maverick currently due to librsvg2-dev dependencies. Anyone who want's to try it either install from repo's (very old version) or try the PPA

Hmmmm---I've been building from source all along & have not had that problem---GS is working fine here with the current maverick libs....

I might note that the build folder I'm using is more than a year old & I most likely also have older libs in my system.

---

### Post by 23meg on 2010-05-08
> **dyltman said:**
> [http://live.gnome.org/GNOME3Myths](http://live.gnome.org/GNOME3Myths)

> The GNOME file manager (Nautilus) will be removed from GNOME and replaced with the GNOME Activity Journal! 

The purpose of that page is to debunk common myths regarding GNOME 3, and that sentence is quoted as a myth. Nautilus is not going anywhere, and GAJ is not intended to be a replacement for it.

---

### Post by jppr on 2010-05-08
I run now gnome-shell in linux mint 9 rc and works fine = ), have to wait little longer if then install it also Maverick.

---

### Post by dyltman on 2010-05-08
> **23meg said:**
> The purpose of that page is to debunk common myths regarding GNOME 3, and that sentence is quoted as a myth. Nautilus is not going anywhere, and GAJ is not intended to be a replacement for it.

Oh silly me.

---

### Post by buzzmandt on 2010-05-09
merk, thanks for the very awesome post with screen shots and how to's for gnome shell.  I don't like it but i do try it from time to time to see how it's going.

---

### Post by plun on 2010-05-09
> **buzzmandt said:**
>  I don't like it but i do try it from time to time to see how it's going.

I have the same opinion, Gnome-Shell doesn't give me something new except for trouble to found a specific app.  Ok with Docky running.

---

### Post by 23meg on 2010-05-09
A friendly reminder, for those who haven't read the original post: 

This thread is dedicated to testing and technical discussion of GNOME Shell. Comments and opinions should go to [the thread(s) in Community Cafe]("http://ubuntuforums.org/showthread.php?t=1457428"), or the mailing list.

---

### Post by plun on 2010-05-09
> **23meg said:**
> A friendly reminder, for those who haven't read the original post: 

This thread is dedicated to testing and technical discussion of GNOME Shell. Comments and opinions should go to the thread(s) in Community Cafe, or the mailing list.

Testing software without opinions.??...must be mission impossible !

If a user don't test specific software, stay away !  IMHO...

---

### Post by Tompalaz on 2010-05-09
I have a interesting "problem".

If I attach a external screen to my laptop, Gnome-Shell runs much more smoothly. Without, it's not laggy, it's just not as fast/smooth.

MacBook 5,1
GPU: 9400M
Video out: DisplayPort
Driver: Nvidia-current (195.36.15)
Kernel: 2.6.32-22-generic

Up to Date Lucid install.
Gnome-shell is installed from source.

---

### Post by 23meg on 2010-05-09
> **plun said:**
> Testing software without opinions.??...must be mission impossible !

Yes, it can be hard (as well as unnecessary) to draw a line between opinions and exchange of technical facts, *during testing discourse*. 

However, drive-by comments in the form of "I like/hate GNOME Shell" / "It rocks" / "It's useless" etc. tend to come from people who are *not* actively testing it, and branch off into long, unproductive discussions of likes and dislikes. Those are the ones we want to avoid in this thread; they can happen in Community Cafe, which is the dedicated forum to that kind of discussion.

---

### Post by autocrosser on 2010-05-09
I notice that the calender has been given an update within the last day or so & there is a gconf key now for it....question is: where is the key? 

The calender has grown by 50% with the change & I want to shrink it back to a usable size.....:confused:

---

### Post by marijus on 2010-05-09
> **autocrosser said:**
> I notice that the calender has been given an update within the last day or so & there is a gconf key now for it....question is: where is the key? 

The calender has grown by 50% with the change & I want to shrink it back to a usable size.....:confused:

gconf-editor > desktop > gnome >shell > clock

---

### Post by autocrosser on 2010-05-09
Thank You, but I've been there......Yes--it works a treat on the clock (glad to have that control finally!), but the calendar size is not controllable from there---I reread the change log & I was mistaken...it's for the clock & not the calendar.  Anyone know where the conf is for it?

---

### Post by LKjell on 2010-05-10
Anyone tried gnome shell with xmonad wm?

---

### Post by MacUntu on 2010-05-10
AFAIK GNOME Shell depends on Mutter, so you can't run it with a different WM.

---

### Post by LKjell on 2010-05-10
Too bad then.

---

### Post by HolidayQueen on 2010-05-10
I tried to find any such Cafe threads. failed.

so ill post my question here,
How does the upcoming release of Unity affect plans for GS?

---

### Post by Merk42 on 2010-05-10
> **HolidayQueen said:**
> I tried to find any such Cafe threads. failed.

so ill post my question here,
How does the upcoming release of Unity affect plans for GS?

Too early to tell.

As I said in the first post, GNOME Shell will be available for Maverick though not default.

Also, Unity is focused specifically for Netbooks anyway.

---

### Post by Calash on 2010-05-10
> **Madspyman said:**
> Doesn't work using the flgrx drivers in Lucid. It flickers every time I open something and skew the menus on back clicks. Using the open drivers it works better, with the exception of a white broken line that appears occasionally in the window upon resizing, and sometimes the colors for the icons change. Still works flawlessly in my Karmic partition under the same conditions.

I was beginning to think I was the only one.  I get random distortions of various windows as I go to and from the overlay.

Running the PPA version.  Had to stop as it was impacting my work.


My home PC has a Nvidia card and runs fine, except for a bit of slowness that I would expect from an early version of software.

---

### Post by terry_gardener on 2010-05-10
is there going to be window list applet for seeingand changing what apps i have open quickly and easily.

---

### Post by Merk42 on 2010-05-10
> **terry_gardener said:**
> is there going to be window list applet for seeingand changing what apps i have open quickly and easily.

Not counting the overlay there isn't anything like that right now.

Asking for that feature often comes up in the mailing list so who knows what will happen in the long run

---

### Post by LKjell on 2010-05-10
So I tested this today. Installed nouveau with 3d support and I was surprise it work. However it would be hard to switch to it when you are so costumed to use a tiling windows manager. With gnome shell you have to use your mouse too much. Do not like that.

---

### Post by hikaricore on 2010-05-10
> **Merk42 said:**
> 
Asking for that feature often comes up in the mailing list so who knows what will happen in the long run

The gnome devs will brickwall it like they did the reasonable request for a screensaver options button for a decade.

---

### Post by VeeDubb on 2010-05-10
> **LKjell said:**
> With gnome shell you have to use your mouse too much. Do not like that.

You can still alt-tab to switch windows, you can still switch desktops with the keyboard (pretty sure anyway).  You can set keyboard shortcuts for the overlay.  I'm not really sure what you 'need' to use the mouse for that you don't 'need' to use if for now.

All this is really replacing is the panels, menus and compositor.

---

### Post by cariboo on 2010-05-10
Have a look at the gnome-shell [Cheat Sheet]("http://live.gnome.org/GnomeShell/CheatSheet").

---

### Post by LKjell on 2010-05-11
> **VeeDubb said:**
> You can still alt-tab to switch windows, you can still switch desktops with the keyboard (pretty sure anyway).  You can set keyboard shortcuts for the overlay.  I'm not really sure what you 'need' to use the mouse for that you don't 'need' to use if for now.

All this is really replacing is the panels, menus and compositor.

Resize my windows and juxapose two windows.

---

### Post by ranch hand on 2010-05-11
You are using it wrong.  This is supposed to be social from the start and here you are using your computer.  Bad, bad boy.

I think you may be surprised as things go on.  It has improved tremendously in the last 6 months.  Much more functionality.

Don't write it off just yet.

---

### Post by Tompalaz on 2010-05-11
> **LKjell said:**
> So I tested this today. Installed nouveau with 3d support and I was surprise it work. However it would be hard to switch to it when you are so costumed to use a tiling windows manager. With gnome shell you have to use your mouse too much. Do not like that.

Do you use the xorg-edgers ppa?

---

### Post by LKjell on 2010-05-11
> **Tompalaz said:**
> Do you use the xorg-edgers ppa?

Yes. However, you need a 2.6.34 kernel.

---

### Post by dyltman on 2010-05-11
Is there a way to quit looking glass?

---

### Post by Mblackwell on 2010-05-11
Press ESC

Ah you mean while testing elements. ALT+F2 run lg again and THEN press ESC.

There might be another way but I sure don't know it.

---

### Post by flintman on 2010-05-11
So I compiled the lastest version. when I run ./gnome-shell --replace I get a black screen that blinks with white lines on the top every few seconds. Anyone have that issue.

Thanks

---

### Post by Merk42 on 2010-05-11
> **flintman said:**
> So I compiled the lastest version. when I run ./gnome-shell --replace I get a black screen that blinks with white lines on the top every few seconds. Anyone have that issue.

Thanks

Works fine for me on an nVidia card with the proprietary drivers.

What's your video card/drivers?

---

### Post by flintman on 2010-05-11
it's just a dell optiplex GX260 on-board video

---

### Post by ranch hand on 2010-05-11
Have you set the desktop effects in System>Preferences>Appearance to "none"?  Worked for me.

---

### Post by Merk42 on 2010-05-11
Lot of new updates the past hour.

Like being able to click on the application name near Activities to quit it (I would imagine more options will be added there)

---

### Post by flintman on 2010-05-11
ya visual effects set to none

---

### Post by xtoudi on 2010-05-11
Alt+F2 crashes my GS (or Alt+F2 and Escape) - fresh compile. Other things works fine.

---

### Post by Merk42 on 2010-05-11
> **flintman said:**
> ya visual effects set to none

Try building again, as I said there were a lot of changes in the past 2 hours

Does the terminal display any particular error when you try to run ./gnome-shell --replace

---

### Post by autocrosser on 2010-05-11
> **Merk42 said:**
> Lot of new updates the past hour.

Like being able to click on the application name near Activities to quit it (I would imagine more options will be added there)

Sounds good...I'm at work right now, will rebuild tonight.

---

### Post by Merk42 on 2010-05-11
> **autocrosser said:**
> Sounds good...I'm at work right now, will rebuild tonight.

Check the first post for a peek

---

### Post by terry_gardener on 2010-05-11
i have the ricotz ppa. 

when i try gnome-shell it seems to work but when something happens on screen for example notifications or the tick near name changes to pause symbol the screen flickers briefly but annoying.

i listen alot to music and when the song changes it does a notification and the screen flickers. 

is this happening to anyone else. 

using nvidia binary drivers geforce 6150se gpu

---

### Post by marijus on 2010-05-11
is it possible to trigger the application change button (current ALT-TAB) with the middle mouse button? 

regards marijus

---

### Post by autocrosser on 2010-05-11
I've done the latest build---looks good. I like the new way to provide menus/control.

Interesting question: I tried to start Miro & it's not working....can someone else try it to see if it's a problem or just my install?

---

### Post by autocrosser on 2010-05-11
> **terry_gardener said:**
> i have the ricotz ppa. 

when i try gnome-shell it seems to work but when something happens on screen for example notifications or the tick near name changes to pause symbol the screen flickers briefly but annoying.

i listen alot to music and when the song changes it does a notification and the screen flickers. 

is this happening to anyone else. 

using nvidia binary drivers geforce 6150se gpu

What player are you using?  I'm using Exaile & building from source--no flicker here. SLI nvidia 9800GT cards.

---

### Post by terry_gardener on 2010-05-12
rhythmbox but it is gnome-shell issue since it happens when something changes on-screen graphically.

opening the calender by clicking the clock, 
notifications of any sort. 
when the available tick turns to pause button.
opening the overlay 

it will flicker 1-5 times and then stop lasts 1-2 seconds

---

### Post by url on 2010-05-12
Luckily gnome-shell won't be default in the maverick. Right decision.
[http://www.omgubuntu.co.uk/2010/05/mark-shuttleworth-no-gnome-shell-in.html](http://www.omgubuntu.co.uk/2010/05/mark-shuttleworth-no-gnome-shell-in.html)

---

### Post by cariboo on 2010-05-12
Please limit your posts in this thread to discussions about gnome shell, not opinions of whether it is good, bad or indifferent. If you want to add your opinion, there is a thread [here]("http://ubuntuforums.org/showthread.php?t=1457428&highlight=gnome-shell") for that.

---

### Post by Merk42 on 2010-05-12
> **url said:**
> <snip> gnome-shell won't be default in the maverick. <snip> 
[http://www.omgubuntu.co.uk/2010/05/mark-shuttleworth-no-gnome-shell-in.html](http://www.omgubuntu.co.uk/2010/05/mark-shuttleworth-no-gnome-shell-in.html)

I said that in the first post...

Of course it seems once a thread reaches 2+ pages no one reads the first post anymore :(

---

### Post by Mblackwell on 2010-05-12
Is it just me or does the status menu not actually DO anything to your status. At least in Pidgin.

---

### Post by xtoudi on 2010-05-12
> **Mblackwell said:**
> Is it just me or does the status menu not actually DO anything to your status. At least in Pidgin.

The same here - empathy.

---

### Post by donniezazen on 2010-05-12
I am unable to load GS. I get a blank screen and system crashes. I installed GS using PPA. I have a Dell E1505 and using nouveau drivers.

I get following error.
> gnome-shell --replace
Window manager warning: Log level 16: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libmozjs.so: cannot open shared object file: No such file or directory)]
Window manager warning: Log level 8: failed to load plugins
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
^CShell killed with signal 2
donnie@donnie-laptop:~$ Cannot register the panel shell: there is already one running.
/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
^C


Thanks.

---

### Post by Mblackwell on 2010-05-12
Go to Appearance and disable desktop effects.

---

### Post by donniezazen on 2010-05-12
> **Mblackwell said:**
> Go to Appearance and disable desktop effects.

Desktop effects don't work with Nouveau drivers. They are already disabled.

---

### Post by donniezazen on 2010-05-12
> sudo apt-get install curl libgstreamer0.10-dev libcroco3-dev xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
curl is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcroco3-dev: Depends: libglib2.0-dev (>= 2.0) but it is not going to be installed
  libdbus-glib-1-dev: Depends: libglib2.0-dev but it is not going to be installed
  libgconf2-dev: Depends: libglib2.0-dev (>= 2.14.0) but it is not going to be installed
                 Depends: liborbit2-dev (>= 1:2.10.2-1.1) but it is not going to be installed
  libgnome-menu-dev: Depends: libglib2.0-dev (>= 2.15.2) but it is not going to be installed
  libgstreamer0.10-dev: Depends: libglib2.0-dev but it is not going to be installed
  libgtk2.0-dev: Depends: libglib2.0-dev (>= 2.21.3) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
  librsvg2-dev: Depends: librsvg2-2 (= 2.26.2-0ubuntu1) but 2.26.2-0ubuntu2 is to be installed
                Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed
  libwnck-dev: Depends: libglib2.0-dev (>= 2.13.0) but it is not going to be installed
               Depends: libpango1.0-dev but it is not going to be installed
  xulrunner-dev: Depends: xulrunner-1.9.2-dev but it is not going to be installed
E: Broken packages


And

> sudo apt-get install libglib2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.24.0-0ubuntu4) but 2.24.1-0ubuntu1 is to be installed
E: Broken packages


Another error. Please help.

---

### Post by terry_gardener on 2010-05-12
are installing from default repos, ppa or from source?

i installed from ppa and it worked fine.

---

### Post by cariboo on 2010-05-12
I got a blank screen with a blocky font when I tried gnome-shell with the nouveau drivers the other day, I just installed the restricted drivers, an now everything works fine. I'm using the ricotz ppa for gnome shell.

---

### Post by donniezazen on 2010-05-12
> **terry_gardener said:**
> are installing from default repos, ppa or from source?

i installed from ppa and it worked fine.

I installed using ppa and also tried building up from source. Couldn't build from source due to dependency error. Probably the problem is with the nouveau drivers.

Thanks.

---

### Post by autocrosser on 2010-05-12
Yes---I'm building from source & using the restricted drivers---no problem. That's where I would go.

---

### Post by donniezazen on 2010-05-12
> **autocrosser said:**
> Yes---I'm building from source & using the restricted drivers---no problem. That's where I would go.

Well, using restricted drivers i get the following error.

> 
 gnome-shell --replace
Window manager warning: Log level 16: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libmozjs.so: cannot open shared object file: No such file or directory)]
Window manager warning: Log level 8: failed to load plugins


---

### Post by autocrosser on 2010-05-12
Hmmmm---I don't have anything in that location & don't get that error...you might want to delete your gnome-shell folder in your home & rebuild.... strange that it's asking for a library that is not in your system---works in my system without that one...

---

### Post by donniezazen on 2010-05-13
> **autocrosser said:**
> Hmmmm---I don't have anything in that location & don't get that error...you might want to delete your gnome-shell folder in your home & rebuild.... strange that it's asking for a library that is not in your system---works in my system without that one...

The one from official repo worked, but its slow and not very responsive. I will try to build from source.

Thanks

---

### Post by Tompalaz on 2010-05-13
[This update]("http://git.gnome.org/browse/gnome-shell/commit/?id=21ff050a405013347ff85d1fcd347131e2b0e491") seems pretty interesting, but it won't work for me. Can anyone of you guys use it?

---

### Post by xtoudi on 2010-05-13
> **Tompalaz said:**
> [This update]("http://git.gnome.org/browse/gnome-shell/commit/?id=21ff050a405013347ff85d1fcd347131e2b0e491") seems pretty interesting, but it won't work for me. Can anyone of you guys use it?

It's running a new workspace but an application is showing in current workspace ... so it looks like a bug. And it seems to be not working with ctrl+mouse - only middle mouse (scroll button).

---

### Post by Krause on 2010-05-14
Only been testing it for little over a day now but it seems pretty good once you get use to it.

What is the purpose of the shaded bottom bar that pops up when you bring the mouse to the bottom right corner of the screen?

---

### Post by Merk42 on 2010-05-14
> **Krause said:**
> Only been testing it for little over a day now but it seems pretty good once you get use to it.

What is the purpose of the shaded bottom bar that pops up when you bring the mouse to the bottom left corner of the screen?

Using the latest build from source nothing happens if you hover in the bottom left, for hovering in the bottom **right**, check the first post.

---

### Post by Krause on 2010-05-14
> **Merk42 said:**
> Using the latest build from source nothing happens if you hover in the bottom left, for hovering in the bottom **right**, check the first post.

Sorry, meant right.

So that bar is always there even when there is no messages, that's all its used for?

---

### Post by Merk42 on 2010-05-14
> **Krause said:**
> Sorry, meant right.

So that bar is always there even when there is no messages, that's all its used for?

CURRENTLY yes, just as the message indicator (envelope) is always present even if no messages.

There was some mockup of the bottom LEFT being used for the ....  [pooper](http://blogs.gnome.org/seth/2010/02/26/let-the-wild-rumpus-begin/)

I can't wait to use it with my image editing software so I can "stick the GIMP in the pooper"

---

### Post by hardwyrd on 2010-05-14
I'm on Gnome-shell for two days now. I haven't had any problem so far. It's now my main UI for Lucid.

My only beef is that I can't customize it too much yet. And if you have lots of favorites, the Recent Documents is displayed outside the viewable area of your display (no you can't see it). And to remedy it, I have to remove some favorites. 

Other than that, everything's working good so far. I'm looking for ways to customize this thing - perhaps through the JS source code?

Anybody have any ideas?



[[http://www.madforubuntu.com]](http://www.madforubuntu.com])

---

### Post by ranch hand on 2010-05-14
If you check this thread (from last round of testing) you will find a number of themes that folks have made that have not been transfered to the current thread;

[http://ubuntuforums.org/showthread.php?t=1305154](http://ubuntuforums.org/showthread.php?t=1305154)

If you find them it might be nice to post links to them in the old thread.  I know that the default theme (back a ways may have been changed) just about gave me seizures.  Some of the thems are pretty nice and folks did a great job on them.

They also make pretty good templates for you to fool around with.  There are instructions for installation of the themes.  A link to that would be real nice too for folks that want to fool with them.

---

### Post by m10 on 2010-05-16
I'm not sure wether this is the right place to post this since I'm using the lucid lynx....
I'm trying to get the gnome-shell running..
i tried both with the default repositories and the ricotz gnome shell testing ppa...
with the default packages i get:
> gnome-shell --replace
Window manager warning: Log level 16: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libmozjs.so: cannot open shared object file: No such file or directory)]
Window manager warning: Log level 8: failed to load plugins
while with the ppa packages i get a similar output:
> gnome-shell --replace

(mutter:18613): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (/usr/lib/libgjs-gi.so.0: undefined symbol: g_struct_info_is_foreign)]

can anybody help?
should i file bugs? where?

---

### Post by plun on 2010-05-16
Found this tutorial with in the tutorial forum.

[http://ubuntuforums.org/showthread.php?t=1479239](http://ubuntuforums.org/showthread.php?t=1479239)

How do I change icon size ???

---

### Post by Merk42 on 2010-05-16
> **m10 said:**
> I'm not sure wether this is the right place to post this since I'm using the lucid lynx....
I'm trying to get the gnome-shell running..
i tried both with the default repositories and the ricotz gnome shell testing ppa...
with the default packages i get:

while with the ppa packages i get a similar output:

can anybody help?
should i file bugs? where?

As both the Ricotz PPA and ESPECIALLY the package in the repositories are often outdated, try building from source.  You can find instructions for Lucid on the first post of this thread

---

### Post by m10 on 2010-05-17
> **Merk42 said:**
> As both the Ricotz PPA and ESPECIALLY the package in the repositories are often outdated, try building from source.

I am aware that any repository is most often at least slightly outdated and that building from source is the best option to get the latest development stuff. But it would have been nice to just easily install some packages to have a look at this stuff.
Also I am on dial-up speed and building from source always takes more bandwidth (and thus time to download) than installing binary packages.
I wanted to trade uptodate-ness(??) with bindwidth/time ;)
And what is the purpose of the packages anyway if they do not work?
I thought that was for people who prefer not (or are not able ) to build from source and still want to test it..

Nevertheless, thank you for the quick reply.
I now will go and build from source as you told me:)

---

### Post by Mblackwell on 2010-05-17
The PPA should be fine, the default repo packages are heavily outdated, and building from source shouldn't take any more real bandwidth once you download the initial packages GS depends on.

---

### Post by ranch hand on 2010-05-17
> **Mblackwell said:**
> The PPA should be fine, the default repo packages are heavily outdated, and building from source shouldn't take any more real bandwidth once you download the initial packages GS depends on.
I think you guys have been away from dial up too long.

My dial up at at the ranch, for instance was good for about 10Mb per hour.  It does not take much to make a big difference in the time it takes to download something.

Source files are no fun at all compared to binaries.

---

### Post by flintman on 2010-05-17
So I have a Dell Optiplex GX260. All stock.  Fresh install of 10.04.

I just compiled the latest version of gnome-shell.  When I run ./gnome-shell -r the screen blanks out and that's it.  I can't do anything from CONTROL-C to ALT CTRL F1.  I have to push the power button and restart.  Anyone else having this issue.

Thanks

---

### Post by Merk42 on 2010-05-17
> **flintman said:**
> So I have a Dell Optiplex GX260. All stock.  Fresh install of 10.04.

I just compiled the latest version of gnome-shell.  When I run ./gnome-shell -r the screen blanks out and that's it.  I can't do anything from CONTROL-C to ALT CTRL F1.  I have to push the power button and restart.  Anyone else having this issue.

Thanks

I'm not sure what ./gnome-shell -r is, the code is ./gnome-shell --replace.  Also, I suggest posting any other GNOME Shell issues in [this thread](http://ubuntuforums.org/showthread.php?t=1476241)

---

### Post by cariboo on 2010-05-17
Threads merged.

---

### Post by Tompalaz on 2010-05-17
Could you guys/gals with a laptop please test if gnome-shell gets more responsive if you connect a screen to your computer?

Gnome-Shell for me there's a big diffrence in response time and it feels much smoother/faster.
Thanks a bunch.

---

### Post by flintman on 2010-05-17
> **Merk42 said:**
> I'm not sure what ./gnome-shell -r is, the code is ./gnome-shell --replace.  Also, I suggest posting any other GNOME Shell issues in [this thread](http://ubuntuforums.org/showthread.php?t=1476241)

either one switches it -r or -replace.  Both cause the issue

---

### Post by ranch hand on 2010-05-17
Try "--replace"

---

### Post by donniezazen on 2010-05-17
> **flintman said:**
> So I have a Dell Optiplex GX260. All stock.  Fresh install of 10.04.

I just compiled the latest version of gnome-shell.  When I run ./gnome-shell -r the screen blanks out and that's it.  I can't do anything from CONTROL-C to ALT CTRL F1.  I have to push the power button and restart.  Anyone else having this issue.

Thanks

I have had the same issues when i used Gnome-shell with Nouveau drivers. Use Nvidia proprietary drivers and disable desktop effects.

---

### Post by screaminj3sus on 2010-05-17
anyone using gnome-shell with the oss ati drivers? on my laptop that has a mobility 2600pro mutter is really slow and the window borders look messed up, on my desktop with a 4870 its not slow but again the windows borders are messed up and other intermittent graphical glitches. Compiz works perfectly on both of them (except blur doesnt work)

---

### Post by null_pointer_us on 2010-05-18
> **Madspyman said:**
> Doesn't work using the flgrx drivers in Lucid. It flickers every time I open something and skew the menus on back clicks.
This is still happening.

Additional technical issues:

[LIST]
[*][COLOR="Red"][unusable][/COLOR] Many parts of Firefox do not redraw themselves properly. For example, when typing, backspacing, repositioning cursor, etc. in the Reply to Thread page here. Layman's guess: redraw events just seem to be randomly lost.
[*][COLOR="DarkOrange"][minor][/COLOR] Tooltip windows are skewed, with the bottom-left corner cut off and showing up on the bottom-right.
[*][COLOR="Red"][unusable][/COLOR] Script windows in Firefox, like when clicking the list button in this forum's Reply to Thread window, show up skewed. Yep, the entire window including the buttons.
[*][COLOR="DarkOrange"][minor][/COLOR] Default theme aesthetics/placement/effects are awful. For example, the app icon (in the top panel) appears to be zoomed and cut off for no apparent reason. Tooltips appear way too "high" based on where their shadows appear. etc. I hope this stuff is not hard-coded.
[*][COLOR="DarkOrange"][minor][/COLOR] Text appears at different vertical positions in top panel-like bar; some code should be added to align (and pad, if necessary) the top panel items based on some common text placement. Top panel items without text (e.g. notification icons) would need to be aligned based on where in the icon the opague pixels begin.
[*][COLOR="DarkOrange"][minor][/COLOR] Screenshots are not working. Best way to describe a visual artifact is to get a screencap, yet all I get in the screenshot window is a black screen with a mouse cursor.
[*][COLOR="DarkOrange"][minor][/COLOR] Window title bar buttons (min, max/restore, close) appear in top-right of window, whereas theme defines them to be in the top-left. I can't imagine this will work well when we get windicators![/LIST]

I'm not sure how many of these are driver issues. fglrx (Radeon HD5770)


Suggestion:

Traditionally, stuff like titlebar text, menus, toolbar icons, etc. has been justified (usually left-justified?). Perhaps it would be better to save the justified stuff for the gnome-shell (which is supposed to "stick" to the sides of the monitor), and let the app window content be centered within its window. This would provide some more visual separation between the apps and the shell, which currently appears mashed together.

---

### Post by xtoudi on 2010-05-18
> This is still happening.

Additional technical issues:

[*][COLOR="Red"][unusable][/COLOR] Many parts of Firefox do not redraw themselves properly. For example, when typing, backspacing, repositioning cursor, etc. in the Reply to Thread page here. Layman's guess: redraw events just seem to be randomly lost.

No problems here.
> 
[*][COLOR="DarkOrange"][minor][/COLOR] Tooltip windows are skewed, with the bottom-left corner cut off and showing up on the bottom-right.

No problems here.
> 
[*][COLOR="Red"][unusable][/COLOR] Script windows in Firefox, like when clicking the list button in this forum's Reply to Thread window, show up skewed. Yep, the entire window including the buttons.

No problems here.
> 
[*][COLOR="DarkOrange"][minor][/COLOR] Default theme aesthetics/placement/effects are awful. For example, the app icon (in the top panel) appears to be zoomed and cut off for no apparent reason. Tooltips appear way too "high" based on where their shadows appear. etc. I hope this stuff is not hard-coded.

its a taste thing. I like zoomed icons - it is very nice. And what about tooltips??
> 
[*][COLOR="DarkOrange"][minor][/COLOR] Text appears at different vertical positions in top panel-like bar; some code should be added to align (and pad, if necessary) the top panel items based on some common text placement. Top panel items without text (e.g. notification icons) would need to be aligned based on where in the icon the opague pixels begin.

Agree - vertical position is bad.
> 
[*][COLOR="DarkOrange"][minor][/COLOR] Screenshots are not working. Best way to describe a visual artifact is to get a screencap, yet all I get in the screenshot window is a black screen with a mouse cursor.

No problems here. I can get any screenshot.
> 
[*][COLOR="DarkOrange"][minor][/COLOR] Window title bar buttons (min, max/restore, close) appear in top-right of window, whereas theme defines them to be in the top-left. I can't imagine this will work well when we get windicators![/LIST]

The same here.


I've got some kind of Intel gfx. Need to check.
GS builded from source.

---

### Post by null_pointer_us on 2010-05-18
> **xtoudi said:**
> (snipped)
Thanks, probably a good number of these are bugs specific to my driver and/or hardware.

> its a taste thing. I like zoomed icons - it is very nice.
I don't; part of the screen looks like it's been cut off. But anyway, it's fine for everyone to use something different. I was just saying 1) I think it's a bad default and 2) I hope it's not hard-coded that way. Meaning, one should be able to choose a theme with or without the zoomed+clipped icon.

> And what about tooltips??
The shadow is thin and starts 5-7px away from the window. That makes the tooltip appear too "high." On second thought, maybe this is just a side effect of the window skew bug.

> I've got some kind of Intel gfx. Need to check.
GS builded from source.
For reference: Radeon HD5770, fglrx 2:8.723.1-0ubuntu3, and gnome-shell 2.29.1+git20100517.5de1a15d-0ubuntu1~10.04~ricotz1 from the Ricotz PPA.

---

### Post by xtoudi on 2010-05-18
> **null_pointer_us said:**
> 
The shadow is thin and starts 5-7px away from the window. That makes the tooltip appear too "high." On second thought, maybe this is just a side effect of the window skew bug.


I don't have any shadowed tooltips :-)
But there is sth strange with this. Network, volume tooltips are very nice, rounded. But "other" applications tooltips (skype) are pretty simple - they are diffrent in some way - very delicate diffrent.

---

### Post by Arla on 2010-05-18
> **Tompalaz said:**
> Could you guys/gals with a laptop please test if gnome-shell gets more responsive if you connect a screen to your computer?

Gnome-Shell for me there's a big diffrence in response time and it feels much smoother/faster.
Thanks a bunch.

So I can't try connecting a monitor, simply because I don't own one...

I'd read your thread a few times and figured it was something on your laptop, today I installed gnome-shell into my "normal" system (not my testing maverick partition where gnome-shell from the regular ubuntu repositories has actually been working out for me just fine) from the Ricotz PPA, and, well, performance really sucks, it's pretty much unusable (however as I said runs fine in my other partition).

Not sure if the fact that I use AWN is causing the suckiness, or something else yet.

---

### Post by dyltman on 2010-05-19
For some reason, from time to time when I use the indicators and go to activities the screen flickers for a while.

---

### Post by Tompalaz on 2010-05-19
madmed sent me a pm and we had a conversation regarding that gnome-shell felt slow.
> 
I'm running lucid, I tried without and with the PPA both are slow, Intel graphics 2.6.32-22 kernel.
Is quadrapassel working for you? because it uses clutter also.
Do you think it's a kernel issue?
I will try with fedora 13, it has the 2.6.34 kernel.

I asked him to try to plugin a monitor to see what happened. 
> That's wierd!! I plugged in my external monitor and both gnome shell and quadrapassel are running fast!!! but I still have the errors in the terminal!!
This affects both nVidia and Intel GPUs.
It would be nice to see if there's a patch/workaround to trick g-s to think there's a screen attached.   
This is a performance boost that devs/someone with the skills should look into. 
 
> **Arla said:**
> So I can't try connecting a monitor, simply because I don't own one...

I'd read your thread a few times and figured it was something on your laptop, today I installed gnome-shell into my "normal" system (not my testing maverick partition where gnome-shell from the regular ubuntu repositories has actually been working out for me just fine) from the Ricotz PPA, and, well, performance really sucks, it's pretty much unusable (however as I said runs fine in my other partition).

Not sure if the fact that I use AWN is causing the suckiness, or something else yet.

---

### Post by Peter09 on 2010-05-19
I am having exactly the same problems as post 97 in this thread, makes gnome-shell unusable.

---

### Post by HalfEmptyHero on 2010-05-19
Is anyone else's chat not working? When someone sends me messages (empathy) they don't show up in the status bar like before. The window pops up, but thats it.

---

### Post by cariboo on 2010-05-19
All application notifications that I have seen so far show up at the bottom of the screen, you can see the notification area if you move your mouse pointer to the lower right hand corner of the screen.

---

### Post by HalfEmptyHero on 2010-05-19
That's what I meant, the bottom of the screen. Chat used to show up in it,  now it doesn't.

---

### Post by Merk42 on 2010-05-19
> **HalfEmptyHero said:**
> That's what I meant, the bottom of the screen. Chat used to show up in it,  now it doesn't.

Looks like a bug that was fixed now
[http://git.gnome.org/browse/gnome-shell/commit/?id=b6a47cdf7674b23bb5946d7abc294dd842d9a63c](http://git.gnome.org/browse/gnome-shell/commit/?id=b6a47cdf7674b23bb5946d7abc294dd842d9a63c)

---

### Post by Arla on 2010-05-20
To add to my prior post, I've got no idea :)

I added AWN to my Maverick install (which was done as a fresh Lucid install, then upgraded to Maverick) and it worked fine, gnome-shell is performing admirably (totally usable) so I upgraded to the ricotz PPA from the version in the main repositories, still works fine, no problems, the only thing I can think of at this point is that my main partition was a Karmic upgrade, vs this one being a Lucid upgrade? Going to try reinstalling my main partition and see what happens.

---

### Post by autocrosser on 2010-05-20
I'm using AWN with my GS--I build from source & lately it's been running much faster...Nvidia SLI setup, but it was laggard a month ago....what hardware are you using?

---

### Post by Tompalaz on 2010-05-20
Have anyone tried gnome-shell with the nouveau drivers?
When I try, nautilus gets all screwed up. It's kind of transparent and the white colors in my wallpaper break through witch makes it difficult to see.

Screenshot
[http://preview.tinyurl.com/3y5ju4a](http://preview.tinyurl.com/3y5ju4a)

---

### Post by Arla on 2010-05-20
> **autocrosser said:**
> I'm using AWN with my GS--I build from source & lately it's been running much faster...Nvidia SLI setup, but it was laggard a month ago....what hardware are you using?

It's my Y450 laptop, which has a stock Intel graphics card if memory serves, the problem I have is that it works fine in my test partition which is a virtually clean install of Lucid upgraded to Maverick, but doesn't work in my main partition which was a Karmic install upgraded to Lucid during testing (I think, although now I think more it might have been just a lucid test build upgraded through the lucid testing process, I think lucid broke my machine once and I "had" to reinstall), and has more programs installed (and some things uninstalled).

As I said, will probably try tonight reinstalling my main partition (I want to reinstall some stuff without the recommends anyway, and find that a reinstall is quicker and easier than trying to remove the relevant packages) and I'll see where it leaves me.

I can make sure I create a package list before I reinstall, and that way might be able to get some idea of what is the offending package.

---

### Post by lime4x4 on 2010-05-20
Has anyone gotten gnome-shell to work with 2 monitors? I'm use to using 2 monitors with each one setup as a seperate xscreen
using nvidia-settings if i try to enable a 2nd xscreen on restart all i get a file manager that is constantly starting

---

### Post by KdotJ on 2010-05-20
Just out of interest, when will the Gnome-Shell inn the repo's be updated?

Or are we looking at no updates for the for-see-able future? The reason I ask is because I like keeping my home folder all tidy, building the gnome-shell from source adds a bunch of folders I don't want in there...

---

### Post by Mblackwell on 2010-05-20
Add the PPA in the OP.

---

### Post by KdotJ on 2010-05-20
> **Mblackwell said:**
> Add the PPA in the OP.

Then I just update and run gnome-shell via the terminal as usual?

---

### Post by Mblackwell on 2010-05-20
Yep.

---

### Post by KdotJ on 2010-05-20
ok cool I'll give it s shot

EDIT:
I added it and ran update manager, giving me a warning of "Partial Upgrade" is this normal??

"Not all updates can be installed"

---

### Post by null_pointer_us on 2010-05-20
Please read the partial upgrades sticky (if you haven't already):
[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

A good rule of thumb is: never use update manager for experimental or development packages. Learning more advanced package management tools (like aptitude or syntaptic) is pretty much required if you want to run these types of packages. Update manager is really only intended for official releases and stable package sets.

Regarding ricotz's gnome-shell PPA, I got some message about a gir1-glib conflict, but the packages seemed very specific to gnome-shell, so I opted to install the PPA versions.

---

### Post by KdotJ on 2010-05-20
In this case maybe I'll give this a miss until I read up more on aptitude or synaptic. I can't afford to mess up my system right now... thank you for your reply

---

### Post by Twiggy794 on 2010-05-21
> **lime4x4 said:**
> Has anyone gotten gnome-shell to work with 2 monitors? I'm use to using 2 monitors with each one setup as a seperate xscreen
using nvidia-settings if i try to enable a 2nd xscreen on restart all i get a file manager that is constantly starting

I am and it's working fine for me.

---

### Post by laborg on 2010-05-21
Hi!

I'm  building gnome-shell from the git-repository, but since yesterdays commits it's not working anymore

[PHP]do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
    JS ERROR: !!!   Exception was: Error: No JS module 'scripting' found in search path
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("No JS module 'scripting' found in search path")@:0
("No JS module 'scripting' found in search path")@gjs_throw:0
@/home/gerhard/gnome-shell/install/share/gnome-shell/js/ui/main.js:32
'
    JS ERROR: !!!     message = 'No JS module 'scripting' found in search path'
    JS ERROR: !!!   Exception was: Error: No JS module 'scripting' found in search path
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("No JS module 'scripting' found in search path")@:0
("No JS module 'scripting' found in search path")@gjs_throw:0
@/home/gerhard/gnome-shell/install/share/gnome-shell/js/ui/main.js:32
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
@<main>:1
'
    JS ERROR: !!!     message = 'No JS module 'scripting' found in search path'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: No JS module 'scripting' found in search path
gerhard@gerhard-laptop:~/gnome-shell/install/bin$ Cannot register the panel shell: there is already one running.[/PHP]

any hints how to correct this?

thx,

---

### Post by KdotJ on 2010-05-21
Well I've built from source on my netbook and gave it a spin. I don't really know what to say.. it's interesting. But everything seems so big, and when you're on the desktop, it just feels so empty and like you're trapped in a small space. I know it's early right now, and I can't wait to see what happens further down the line... but for now I'm not sold...

---

### Post by autocrosser on 2010-05-22
> **laborg said:**
> Hi!

I'm  building gnome-shell from the git-repository, but since yesterdays commits it's not working anymore

[PHP]do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
    JS ERROR: !!!   Exception was: Error: No JS module 'scripting' found in search path
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("No JS module 'scripting' found in search path")@:0
("No JS module 'scripting' found in search path")@gjs_throw:0
@/home/gerhard/gnome-shell/install/share/gnome-shell/js/ui/main.js:32
'
    JS ERROR: !!!     message = 'No JS module 'scripting' found in search path'
    JS ERROR: !!!   Exception was: Error: No JS module 'scripting' found in search path
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("No JS module 'scripting' found in search path")@:0
("No JS module 'scripting' found in search path")@gjs_throw:0
@/home/gerhard/gnome-shell/install/share/gnome-shell/js/ui/main.js:32
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
@<main>:1
'
    JS ERROR: !!!     message = 'No JS module 'scripting' found in search path'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: No JS module 'scripting' found in search path
gerhard@gerhard-laptop:~/gnome-shell/install/bin$ Cannot register the panel shell: there is already one running.[/PHP]any hints how to correct this?

thx,

I was having that problem yesterday also--rebuilding this evening all worked well again. Sometimes things get b0rked, so try until they are straightened out.....
Also, you might try calling the startup with:```
cd ~/gnome-shell/source/gnome-shell/src
``` instead of ~/gnome-shell/install/bin. Sometimes they forget to update the /install path.

---

### Post by Tompalaz on 2010-05-26
Does GS fail to build for any of you?
Can't upgrade from source to latest release.

jhbuild build -fac won't do it either.

---

### Post by Peter09 on 2010-05-26
As above I'm getting this

>    JS ERROR: !!!     message = 'Requiring Shell, version none: Requiring namespace 'Meta' version '2.29', but '2.31' is already loaded'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring Shell, version none: Requiring namespace 'Meta' version '2.29', but '2.31' is already loaded
peter@pavilion:~$ Cannot register the panel shell: there is already one running

Hence gnome-shell doesn't start

---

### Post by Merk42 on 2010-05-26
Have either of you tried deleting the ~/gnome-shell folder and rebuilding? Also what version of Ubuntu?

---

### Post by Tompalaz on 2010-05-28
> **Merk42 said:**
> Have either of you tried deleting the ~/gnome-shell folder and rebuilding? Also what version of Ubuntu?
Maverick. I tried to remove gnome-shell folder but it still fail to build on step 5

---

### Post by xtoudi on 2010-05-28
> **Tompalaz said:**
> Maverick. I tried to remove gnome-shell folder but it still fail to build on step 5

Maybe you should try to get latest gnome-shell-build-setup.sh:

```
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
```
and then
```
/bin/bash gnome-shell-build-setup.sh
```
...and
```
jhbuild build
```

---

### Post by donniezazen on 2010-05-28
> **Merk42 said:**
> Have either of you tried deleting the ~/gnome-shell folder and rebuilding? Also what version of Ubuntu?

I have wasted enough amount of time in building Gnome-shell from source with several installation failures. I am now using it from PPA.

---

### Post by ronacc on 2010-05-31
@ merk42 you need to edit the OP to point at the correct git repository that line should read

```
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
```

as it is now the .sh it downloads has a syntax error .

---

### Post by ronacc on 2010-05-31
trying a fresh build on maverick amd64  the jhbuild errors out during the build phase see attached txt file .

---

### Post by ronacc on 2010-05-31
nuts the file didn't attach trying again , had to trim a few errors out of it to get it bellow 19.5 kb to upload .

---

### Post by autocrosser on 2010-05-31
Yes--I've got the same error--also building on X86-64(Intel)--it's complaining about a couple of missing build files: gibaseinfo.h, gifunctioninfo.h, gitypelib.h & gitypes.h in /home/dean/gnome-shell/source/gir-repository/gir/tmp-introspectnTNmDC

I'm looking into it.....

---

### Post by autocrosser on 2010-05-31
OK--Found the problem---you will find the four files in: ./gnome-shell/install/include/gobject-introspection-1.0   In that folder create a folder called "girepository" (without the quotes) & move the four build files into it---then rerun the build. Someone messed up in one of the make files & did not include a create folder, so the build dumped the files "near" where they needed to go (at least that's my guess).

As soon as I created the "correct" folder the build sailed right past without errors.

By the way--the last fresh build I did had a "interesting" error during gconf---I had to change permissions on /usr/lib/gio/modules---it wanted to install libgsettingsgconfbackend.la & .so there--I had some minor issues making that writeable, but as it was just gio not the "real" gconf lib---I let it---so far no problems with it......

OK, whilst I typed this my build finished---so that is a quick patch/repair....

[edit]--I created links from the new folder back to the parent folder in case things get changed in the future--seems like a good idea.....

---

### Post by ronacc on 2010-05-31
thanks ,That got me as far as building clutter then it errored looking for a lib .
Its 11:15 pm local and I haven't started dinner yet , thats enough for tonight , I'll wipe and start from scratch tommorow.

---

### Post by autocrosser on 2010-05-31
That's the best idea--I nuked my ./gnome-shell folder before I did the build....nice to do a clean build every couple of weeks or so.....

Have a good evening & start fresh tomorrow!!!!

---

### Post by Merk42 on 2010-05-31
Updated the OP with the new git link.

As far as the problem now has anyone filed a bug?

---

### Post by autocrosser on 2010-05-31
No--I figure I'll look at it again tomorrow to see if it was fixed--betting on someone just forgetting a line. If it's still there tomorrow I'll get a bug posted--very sure that it's a bit late to do tonight.........

---

### Post by Finalfantasykid on 2010-06-01
I have been trying to get gnome-shell to work properly, but I am getting graphical problems all over the place.

```
(mutter:28868): Clutter-WARNING **: The required ID of 66122 does not refer to an existing actor; this usually implies that the pick() of an actor is not correctly implemented or that there is an error in the glReadPixels() implementation of the GL driver.

(mutter:28868): Clutter-WARNING **: The required ID of 65846 does not refer to an existing actor; this usually implies that the pick() of an actor is not correctly implemented or that there is an error in the glReadPixels() implementation of the GL driver.

(mutter:28868): Clutter-WARNING **: The required ID of 65846 does not refer to an existing actor; this usually implies that the pick() of an actor is not correctly implemented or that there is an error in the glReadPixels() implementation of the GL driver.

(mutter:28868): Clutter-WARNING **: The required ID of 66102 does not refer to an existing actor; this usually implies that the pick() of an actor is not correctly implemented or that there is an error in the glReadPixels() implementation of the GL driver.

```

From reading others posts in this thread, it seems other people are having the same, or very similar problems.  As a result of this, animations are not smooth, artifacts are going all over the place, and the mouse position is not being detected properly for rollovers/clicks, making navigation extremely difficult.  Occasionally gnome-shell will eventually just crash.  I have yet to find any solutions to this problem, or are there any?  

I am using the 195.36.15 drivers, and have the GeForce Go 7900 GS, and am running Lucid

---

### Post by wayneericgouin on 2010-06-01
What's the version number from the jhbuild. is it 2.31.2 or higher?

---

### Post by Finalfantasykid on 2010-06-01
Hmm, how would I check this?

---

### Post by ronacc on 2010-06-02
wiped everything and started over tonight , they must have updated both gnome-shell-build.sh and jhbuild.rc , when I ran the ...build.sh the first time tonight it asked me to install libgl1-mesa-dev it did not do so last night apearently that cured the failure at building clutter . reran the ....build.sh and it built a new jhbuild.rc , ran sudo jhbuild build , it didn't get stuck looking for those 4 files this time and it completed with sucess .  gnome-shell starts and runs but crashes starting some apps terminal starts ok Opera and FF crash it , it restarts metacity when it crashes so I could copy the output of the terminal I started it from and paste it to gedit to save it .I'm on my stable box right now and the saved file is on my test box I can post it from ther if it would be useful .

---

### Post by autocrosser on 2010-06-02
Yes--I did a clean build also without errors....looks like it was a minor "burp". I'm not having any problems running it--do notice that it "seems" snappier than it has for a while now...

I am having some problems with large Java windows (shudder & some crashing), but that's about it.....(play a browser game called Dark Orbit--pops a 1024x768 Java window in the middle of my 1920x1080 screen--the Java window is not happy about it)......

---

### Post by ronacc on 2010-06-02
I'll give that a try this evening , that is if I can find a browser that don't crash GS on my box:confused: I didn't play around much after I got it built last night , it was late again .

---

### Post by davideotape on 2010-06-02
Just tried compiling and running it. Get a lot of black, with bits of white and a ridiculously slow refresh rate. Here's my terminal output:

```
$ ./gnome-shell --replace
      JS LOG: GNOME Shell started at Wed Jun 02 2010 14:08:43 GMT+0100 (BST)
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
libgconf-2.so.4: failed to map segment from shared object: Permission denied
Failed to load module: /usr/lib/gio/modules/libgsettingsgconfbackend.so
libgconf-2.so.4: failed to map segment from shared object: Permission denied
Failed to load module: /usr/lib/gio/modules/libgsettingsgconfbackend.so
Error loading document: Error opening file: No such file or directory
Error loading document: Error opening file: No such file or directory
^CShell killed with signal 2
```

---

### Post by ronacc on 2010-06-02
@autocrosser its really acting wierd tonight , still using last nights build . 1st time I started it all was well even the browsers didn't crash it ! signed up and tried your game , it was stable for the short time I messed with it ( I also have a 1920x1080 display ) . It crashed the next several times I started it ( with a signal 6 ) then after completely killing compiz ( I had been just using metacity --replace) I got it to atart and run but now browsers are crashing it again ??? I'll try a rebuild this time inplace .

edit :  rebuild using -f -a -c  no help

---

### Post by autocrosser on 2010-06-03
I noticed that the rbga gtk stuff just came in again---Firefox is now crashing GS as soon as I start it & is having flash crash issues (in the normal Gnome session)...So I'm back to using Chrome in GS. The Java window flickering is the same as Firefox--no better--no worse & at least flash stuff is working in Chrome....

I think one difference between our builds is that I'm using the xorg-edgers PPA (not sure if you are or not)--just got a Nvidia driver update a day or so ago (using 259.29) & I'm running a SLI-setup. I think that the SLI is "covering" up some GS issues due to the available amount of Vram & GPU, at least that would be my take on it....other than what I've got going above, GS is working perfectly......(watch--I just hexed myself:) ).......:P

---

### Post by go7Ul1ai on 2010-06-03
Can some one post a screenshot of the current build (just curious to see if their are any visual changes since the last time I tested shell) :)

---

### Post by Merk42 on 2010-06-03
> **lee.jarratt said:**
> Can some one post a screenshot of the current build (just curious to see if their are any visual changes since the last time I tested shell) :)

First post of this thread, like always.

---

### Post by go7Ul1ai on 2010-06-03
> **Merk42 said:**
> First post of this thread, like always.

I actually wanted to see if there were any visual changes since the time those images on the 1st thread were posted. Actually..

---

### Post by Merk42 on 2010-06-03
> **lee.jarratt said:**
> I actually wanted to see if there were any visual changes since the time those images on the 1st thread were posted. Actually..

and I constantly update those images

---

### Post by go7Ul1ai on 2010-06-03
> **Merk42 said:**
> and I constantly update those images

Dude, chill out. Life is good :)

---

### Post by ranch hand on 2010-06-03
What Merk42 is trying to say is that the images are current.

They are very well maintained.

---

### Post by go7Ul1ai on 2010-06-03
I know he was, and I'm just saying chill out, because he seems to be having a bad day or something :/

---

### Post by cariboo on 2010-06-03
Any opinions on the new notifications? I prefer the older ones.

---

### Post by hrhnick on 2010-06-03
any way to disable the empathy "in notification chat"?

i can't seem to get a regular conversation window unless i initiate the chat. :(

---

### Post by zekopeko on 2010-06-04
> **cariboo907 said:**
> Any opinions on the new notifications? I prefer the older ones.

I can't wait to be a "click-to-dismiss" slave to notifications again.

---

### Post by ronacc on 2010-06-04
after a fresh rebuild this morning , played around a bit more , FF and Opera still crashing GS , chromium and epiphany do not . the output from the terminal GS was started from seem to indicate that the problem is associated with GDK .

---

### Post by plun on 2010-06-04
> **ronacc said:**
> after a fresh rebuild this morning , played around a bit more , FF and Opera still crashing GS , chromium and epiphany do not . the output from the terminal GS was started from seem to indicate that the problem is associated with GDK .

Yup.... stone-dead when Firefox starts, ok with Chromium.

```
plun@plun-laptop:~$ gnome-shell --replace
      JS LOG: GNOME Shell started at Fri Jun 04 2010 18:10:35 GMT+0200 (CET)
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
Window manager warning: Log level 16: STACK_OP_LOWER_BELOW: window 0x200036e not in stack
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
Bug in window manager: Unexpected X error: BadDrawable (invalid Pixmap or Window parameter) serial 5341 error_code 9 request_code 53 minor_code 0)
Shell killed with signal 6
```

---

### Post by T-rock007 on 2010-06-04
You know i really don't like gnome-shell very much.

---

### Post by zekopeko on 2010-06-04
> **T-rock007 said:**
> You know i really don't like gnome-shell very much.

Join the club.

---

### Post by 23meg on 2010-06-04
Let me briefly interrupt the club proceedings with [my friendly reminder from post #18]("http://ubuntuforums.org/showpost.php?p=9268526&postcount=18"); thanks.

---

### Post by Starks on 2010-06-04
Why is gnome-shell still the unintuitive turd it was a few months back?

---

### Post by luceerose on 2010-06-04
I have started an opinions thread on gnome-shell here;

[http://ubuntuforums.org/showthread.php?t=1501690](http://ubuntuforums.org/showthread.php?t=1501690)

---

### Post by phenest on 2010-06-04
I still feel that + for adding workspaces should be bigger like it was in the beginning to provide a large drop area when dragging icons over it. Sometimes the icons (or windows) completely obscure it and I can miss.

I'd tell the Gnome devs myself but am always a little nervous of their reaction.

Other than that, I'm feeling very positive about GS, and look forward to the release.

---

### Post by ronacc on 2010-06-04
> **phenest said:**
> 
I'd tell the Gnome devs myself but am always a little nervous of their reaction..

They are trying to "sell" their creation to us . The customer should never be afraid of the "store" , after all he can take his buisness elsewhere .

---

### Post by phenest on 2010-06-05
> **ronacc said:**
> They are trying to "sell" their creation to us . The customer should never be afraid of the "store" , after all he can take his buisness elsewhere .

I appreciate what you're saying, but my comment is based on past experience.

I'm looking to add the Ricotz PPA to Debian Squeeze. The one in the Debian repo is quite out of date. add-apt-repository doesn't exist in Debian. Any idea what url and key I need?

---

### Post by plun on 2010-06-05
> **phenest said:**
> 
I'm looking to add the Ricotz PPA to Debian Squeeze. The one in the Debian repo is quite out of date. add-apt-repository doesn't exist in Debian. Any idea what url and key I need?

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

```
deb http://ppa.launchpad.net/ricotz/testing/ubuntu lucid main 
deb-src http://ppa.launchpad.net/ricotz/testing/ubuntu lucid main
```

EDIT or maybe... where is Debian Squeeze in progress...:confused:

```
deb http://ppa.launchpad.net/ricotz/testing/ubuntu maverick main 
deb-src http://ppa.launchpad.net/ricotz/testing/ubuntu maverick main 
```


Howto add a key
[http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/](http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/)

------------------

The Firefox crash is fixed in Ricotz latest version from today. !


--

---

### Post by phenest on 2010-06-05
Lucid is closest but it won't install gjs because xulrunner must be >=1.9.2 but I only have 1.9.1 at best.

EDIT: BTW, Maverick is based on sid which is quite a way ahead of squeeze.

---

### Post by phenest on 2010-06-05
Thanks for any help plun, but I decided to compile it instead. I even created a .deb package too (a newly learnt skill).

I wish it didn't flicker so. :(

---

### Post by mr_hangman on 2010-06-06
I compiled GS from source and have been using it for a while. I really like the idea and want to use it on everyday basis but there are two problems. The screen flickers very often and the frame rate is quite low (~10 fps). This makes my eyes hurt and reduces productivity. 

I'm running Lucid 10.04 on my laptop with Core2Duo 2.2GHz, 2GB RAM and Geforce 8600M GS 256MB. Compiz runs smoothly on it. I know that GS is still under development but is there a way to solve these problems?

---

### Post by davideotape on 2010-06-07
Should I need root privileges to compile gnome-shell or not?

And I'm currently getting this error:

```
$ ./gnome-shell --replace
      JS LOG: GNOME Shell started at Mon Jun 07 2010 12:00:46 GMT+0100 (BST)
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
Bug in window manager: Unexpected X error: BadWindow (invalid Window parameter) serial 2530 error_code 3 request_code 2 minor_code 0)
Shell killed with signal 6

```

---

### Post by ronacc on 2010-06-07
I don't know if you "should" need root privileges , but I did on my sys , without it the build would fail trying to write a file to /usr/lib .

---

### Post by davideotape on 2010-06-07
That sounds like the same reason that I needed to sudo the build. I was just curious as to whether there would be any unintended side affects if it was building with root privileges.

---

### Post by Merk42 on 2010-06-07
> **davideotape said:**
> Should I need root privileges to compile gnome-shell or not?

And I'm currently getting this error:

```
$ ./gnome-shell --replace
      JS LOG: GNOME Shell started at Mon Jun 07 2010 12:00:46 GMT+0100 (BST)
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
Bug in window manager: Unexpected X error: BadWindow (invalid Window parameter) serial 2530 error_code 3 request_code 2 minor_code 0)
Shell killed with signal 6

```

You shouldn't need root privileges to run jhbuild build, nor ./gnome-shell --replace

---

### Post by ronacc on 2010-06-07
I didn't think you should but without sudo it errors on me trying to write a file to /usr/lib , I'll copy down exactly which one on todays build and post it .

edit: I had copied it , here it is .

```
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['gcc', '-Wall', '-pthread', '-I/home/ron/gnome-shell/install/include/gobject-introspection-1.0', '-I/usr/include/glib-2.0', '-I/usr/lib/glib-2.0/include', '-I/usr/include/dbus-1.0', '-I/usr/lib/dbus-1.0/include', '-I/usr/include/glib-2.0', '-I/usr/lib/glib-2.0/include', '-I/usr/include/dbus-1.0', '-I/usr/lib/dbus-1.0/include', '-I/usr/include/glib-2.0', '-I/usr/lib/glib-2.0/include', '-c', '-o', '/home/ron/gnome-shell/source/gir-repository/gir/tmp-introspectCVu041/DBus-1.0.o', '/home/ron/gnome-shell/source/gir-repository/gir/tmp-introspectCVu041/DBus-1.0.c']' returned non-zero exit status 1
make[2]: *** [DBus-1.0.gir] Error 1
make[2]: Leaving directory `/home/ron/gnome-shell/source/gir-repository/gir'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ron/gnome-shell/source/gir-repository'
make: *** [all] Error 2
*** Error during phase build of gir-repository: ########## Error running make   *** [2/9]

```

---

### Post by davideotape on 2010-06-07
> **Merk42 said:**
> You shouldn't need root privileges to run jhbuild build, nor ./gnome-shell --replace

This is what I get after getting rid of ~/gnome-shell and starting again:

```
$ jhbuild build
jhbuild build: could not download http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules: [Errno 13] Permission denied: '/home/dstansby/.cache/jhbuild/gnome-shell.modules-'

```

---

### Post by MacUntu on 2010-06-07
Is there a way to just build with jhbuild and then install using root privileges? I don't feel like I want root-owned files all over my home directory. :D

---

### Post by xtoudi on 2010-06-07
> **davideotape said:**
> This is what I get after getting rid of ~/gnome-shell and starting again:

```
$ jhbuild build
jhbuild build: could not download http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules: [Errno 13] Permission denied: '/home/dstansby/.cache/jhbuild/gnome-shell.modules-'

```

You don't need any special pirvs.
just do:

```

sudo chown dstansby.dstansby -R ~/.cache       (for sure)
chmod +wr -R ~/.cache 
```

---

### Post by davideotape on 2010-06-07
> **xtoudi said:**
> You don't need any special pirvs.
just do:

```

sudo chown dstansby.dstansby -R ~/.cache       (for sure)
chmod +wr -R ~/.cache 
```

Thanks, got rid of first error. There's another one though:

```
][	 ]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' | /bin/sed 's/.* //' | sort | uniq > .libs/libgsettingsgconfbackend.exp
libtool: relink: /bin/grep -E -e "^g_io_module_(load|unload|query)" ".libs/libgsettingsgconfbackend.exp" > ".libs/libgsettingsgconfbackend.expT"
libtool: relink: mv -f ".libs/libgsettingsgconfbackend.expT" ".libs/libgsettingsgconfbackend.exp"
libtool: relink: echo "{ global:" > .libs/libgsettingsgconfbackend.ver
libtool: relink:  cat .libs/libgsettingsgconfbackend.exp | sed -e "s/\(.*\)/\1;/" >> .libs/libgsettingsgconfbackend.ver
libtool: relink:  echo "local: *; };" >> .libs/libgsettingsgconfbackend.ver
libtool: relink:  gcc -shared  .libs/libgsettingsgconfbackend_la-gconfsettingsbackend-module.o .libs/libgsettingsgconfbackend_la-gconfsettingsbackend.o   -Wl,-rpath -Wl,/home/dstansby/gnome-shell/install/lib -L/home/dstansby/gnome-shell/install/lib -lgconf-2 -L/usr/lib -lgio-2.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  -pthread -pthread   -pthread -Wl,-soname -Wl,libgsettingsgconfbackend.so -Wl,-version-script -Wl,.libs/libgsettingsgconfbackend.ver -o .libs/libgsettingsgconfbackend.so
libtool: install: /usr/bin/install-check .libs/libgsettingsgconfbackend.soT /usr/lib/gio/modules/libgsettingsgconfbackend.so
install: cannot remove `/usr/lib/gio/modules/libgsettingsgconfbackend.so': Permission denied
make[2]: *** [install-giomoduleLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/dstansby/gnome-shell/source/gconf/gsettings'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dstansby/gnome-shell/source/gconf/gsettings'
make: *** [install-recursive] Error 1
*** Error during phase install of gconf: ########## Error running make install *** [5/9]

  [1] Rerun phase install
  [2] Ignore error and continue to next module
  [3] Give up on module
  [4] Start shell
  [5] Reload 
```

---

### Post by xtoudi on 2010-06-07
> **davideotape said:**
> Thanks, got rid of first error. There's another one though:

```
][	 ]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' | /bin/sed 's/.* //' | sort | uniq > .libs/libgsettingsgconfbackend.exp
libtool: relink: /bin/grep -E -e "^g_io_module_(load|unload|query)" ".libs/libgsettingsgconfbackend.exp" > ".libs/libgsettingsgconfbackend.expT"
libtool: relink: mv -f ".libs/libgsettingsgconfbackend.expT" ".libs/libgsettingsgconfbackend.exp"
libtool: relink: echo "{ global:" > .libs/libgsettingsgconfbackend.ver
libtool: relink:  cat .libs/libgsettingsgconfbackend.exp | sed -e "s/\(.*\)/\1;/" >> .libs/libgsettingsgconfbackend.ver
libtool: relink:  echo "local: *; };" >> .libs/libgsettingsgconfbackend.ver
libtool: relink:  gcc -shared  .libs/libgsettingsgconfbackend_la-gconfsettingsbackend-module.o .libs/libgsettingsgconfbackend_la-gconfsettingsbackend.o   -Wl,-rpath -Wl,/home/dstansby/gnome-shell/install/lib -L/home/dstansby/gnome-shell/install/lib -lgconf-2 -L/usr/lib -lgio-2.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  -pthread -pthread   -pthread -Wl,-soname -Wl,libgsettingsgconfbackend.so -Wl,-version-script -Wl,.libs/libgsettingsgconfbackend.ver -o .libs/libgsettingsgconfbackend.so
libtool: install: /usr/bin/install-check .libs/libgsettingsgconfbackend.soT /usr/lib/gio/modules/libgsettingsgconfbackend.so
install: cannot remove `/usr/lib/gio/modules/libgsettingsgconfbackend.so': Permission denied
make[2]: *** [install-giomoduleLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/dstansby/gnome-shell/source/gconf/gsettings'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dstansby/gnome-shell/source/gconf/gsettings'
make: *** [install-recursive] Error 1
*** Error during phase install of gconf: ########## Error running make install *** [5/9]

  [1] Rerun phase install
  [2] Ignore error and continue to next module
  [3] Give up on module
  [4] Start shell
  [5] Reload 
```

Need to wait ... this happens often (wait few minutes/hours). There is sth wrong with sources. I've got this too.

```
jhbuid build -fac 
```
seems to be not working neither.

---

### Post by MacUntu on 2010-06-07
Ok, the install phase of the gconf module fails as unprivileged user (libtool: install: /usr/bin/install -c .libs/libgsettingsgconfbackend.soT /usr/lib/gio/modules/ won't success), so I went to #gnome-shell and got this:

> <fmuellner> gconf now has a backend for gsettings, which is part of the current development version of glib
<fmuellner> its install location is not determined by gconf (or the jhbuild prefix), but by the path where glib/gio expect it to be
<fmuellner> it's some variable in the gio pkg-config file
<fmuellner> the cleanest solution is to make the jhbuild gconf _not_ build the gsettings backend
<fmuellner> at least for now - you will have to change that when we start requiring gsettings ourselves
<fmuellner> **add the following to .jhbuildrc-custom:**
<fmuellner> **module_autogenargs['gconf'] = '--disable-gsettings-backend'**
...
<fmuellner> please mention that **the solution above (--disable-gsettings-backend) will break once we move to gsettings**

Seems to work, but currently there's a blocker bug: [https://bugzilla.gnome.org/show_bug.cgi?id=620860](https://bugzilla.gnome.org/show_bug.cgi?id=620860)

---

### Post by xtoudi on 2010-06-07
> **MacUntu said:**
> Ok, the install phase of the gconf module fails as unprivileged user (libtool: install: /usr/bin/install -c .libs/libgsettingsgconfbackend.soT /usr/lib/gio/modules/ won't success), so I went to #gnome-shell and got this:



Seems to work, but currently there's a blocker bug: [https://bugzilla.gnome.org/show_bug.cgi?id=620860](https://bugzilla.gnome.org/show_bug.cgi?id=620860)

Like I said before - there is no reason to sudo jhbuild. It should work without any special user privs. Look at the first post of this thread or here, at source:

[http://live.gnome.org/GnomeShell/](http://live.gnome.org/GnomeShell/)

---

### Post by themarker0 on 2010-06-07
Can anyone tell me the best way to test. Does it virtualize yet?

---

### Post by davideotape on 2010-06-07
Hmm, I have a ~/.jhbuildrc and a ~/.jhbuildrc-custom but no ~/.jhbuild-custon

---

### Post by MacUntu on 2010-06-07
> **davideotape said:**
> Hmm, I have a ~/.jhbuildrc and a ~/.jhbuildrc-custom but no ~/.jhbuild-custon

Good catch - it's a typo, he meant ~/.jhbuildrc-custom.

---

### Post by Merk42 on 2010-06-07
> **themarker0 said:**
> Can anyone tell me the best way to test. Does it virtualize yet?

You could read the [first post](http://ubuntuforums.org/showpost.php?p=9257172&postcount=1)...

As I said there, it doesn't yet work in Virtualbox.  You can either build from source or use the PPA. As you may have seen from these recent posts, building from source may not work right this moment, should in a day or two provided they fix the bug. It's like testing Maverick, breakage happens from time to time.

---

### Post by davideotape on 2010-06-07
Unfortuantly, I've tried that and I'm still getting a permission denied error:

```
libtool: install: /usr/bin/install-check .libs/libgsettingsgconfbackend.soT /usr/lib/gio/modules/libgsettingsgconfbackend.so
install: cannot remove `/usr/lib/gio/modules/libgsettingsgconfbackend.so': Permission denied
make[2]: *** [install-giomoduleLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/dstansby/gnome-shell/source/gconf/gsettings'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dstansby/gnome-shell/source/gconf/gsettings'
make: *** [install-recursive] Error 1
*** Error during phase install of gconf: ########## Error running make install *** [5/9]

  [1] Rerun phase install
  [2] Ignore error and continue to next module
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration

```

---

### Post by MacUntu on 2010-06-07
Looks like you have some leftovers, did you use 'jhbuild build -f -a -c'?

Edit: Blocker fixed, should compile now.

---

### Post by davideotape on 2010-06-07
> **MacUntu said:**
> Looks like you have some leftovers, did you use 'jhbuild build -f -a -c'?

Nope, I didn't, and now I have it's worked :D Thanks

---

### Post by terry_gardener on 2010-06-07
> **mr_hangman said:**
> I compiled GS from source and have been using it for a while. I really like the idea and want to use it on everyday basis but there are two problems. The screen flickers very often and the frame rate is quite low (~10 fps). This makes my eyes hurt and reduces productivity. 

this is the reason i dont use it more often. the flickering does my head in. it seems to do it when anything pops up on the screen, and even sometimes flickers when you change to the overlay.

however i used the ppa instead of installing from source.

---

### Post by lesnoland on 2010-06-07
Greetings,

After trying gnome-shell and unity on my Intel graphics card, I decided to install Lucid, and give it a try on my Sony Vaio VGN-NW21SF Notebook, equiped with an ATI Mobility Radeon HD 4550 graphics card.

Software info:

Operating System: Ubuntu Lucid Lynx 

Video Driver: fglrx 8.732-0ubuntu1 (ati website 10.5 catalyst), repository.

Gnome Shell: repository, ricoz, last build.

Unity: repository

Report: I experience the following: constant flickers, rendering problems (text is deformed, windows are not rendered), basically its unusable.


display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 3.3.9836 Compatibility Profile Context


Update: works fine with radeon.

---

### Post by ronacc on 2010-06-08
since yesterday I have been getting the folowing error
```
Generating and caching the translation database
Merging translations into mutter.desktop.
  GEN    Meta-2.31.gir
Traceback (most recent call last):
  File "/home/ron/gnome-shell/install/bin/g-ir-scanner", line 38, in <module>
    sys.exit(scanner_main(sys.argv))
  File "/home/ron/gnome-shell/install/lib64/gobject-introspection/giscanner/scannermain.py", line 284, in scanner_main
    transformer.register_include(include_obj)
  File "/home/ron/gnome-shell/install/lib64/gobject-introspection/giscanner/transformer.py", line 113, in register_include
    self._parse_include(filename)
  File "/home/ron/gnome-shell/install/lib64/gobject-introspection/giscanner/transformer.py", line 134, in _parse_include
    parser = self._cachestore.load(filename)
  File "/home/ron/gnome-shell/install/lib64/gobject-introspection/giscanner/cachestore.py", line 125, in load
    fd = open(store_filename)
IOError: [Errno 13] Permission denied: '/home/ron/.cache/g-ir-scanner/981fffa3036fc02e2a752e118ad6ddef72f72a82'
make[4]: *** [Meta-2.31.gir] Error 1
make[4]: Leaving directory `/home/ron/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/ron/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ron/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ron/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [6/9]

```
I have done 3 complete wipes and started over even once removing and reinstalling jhbuild ( including ~./jhbuildrc ) no help .

---

### Post by autocrosser on 2010-06-08
Hmmm--are you still doing a "sudo jhbuild"???  I just did a full rebuild & went thru with no errors. Back when it was needing to install a file in /usr/lib I changed the permissions on that folder only so I could do a "normal" build without sudo (if you can call anything about GS "normal":lolflag:).  

I really would change things that way & try it again---I pointed out the folder in question a couple of pages ago.....Other than using sudo to build in your /home, I can't think of anything that is causing your problem......if you want me to look at your build output, PM me & I'll send you my email.....

Just by looking at your info---delete your /.cache folder & do a non-sudo build--change the permissions on /usr/lib---My note from page#14> By the way--the last fresh build I did had a "interesting" error during  gconf---I had to change permissions on /usr/lib/gio/modules---it wanted  to install libgsettingsgconfbackend.la & .so there--I had some minor  issues making that writeable, but as it was just gio not the "real"  gconf lib---I let it---so far no problems with it......

---

### Post by ronacc on 2010-06-08
I wasn't using sudo , I deleted ./cache/jhbuild and g-ir-scanner I had other things in there I didn't want to wipe so I didn't nuke the whole thing . running the build now with -f -a -c  .

---

### Post by ronacc on 2010-06-08
ok it went that time thanks .

---

### Post by autocrosser on 2010-06-09
Perfect--thought you had a permission problem from your build info---glad to see that it was a easy fix!!!

---

### Post by ronacc on 2010-06-09
I'm glad you picked up on that , when I read through it I completely missed the permission denied .

---

### Post by lesnoland on 2010-06-09
Anyone else gettings this?

```

WARNING: Skipping unknown interface GtkFileChooserEmbed
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  DBusGLib-1.0.gir -o DBusGLib-1.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  DBus-1.0.gir -o DBus-1.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  GConf-2.0.gir -o GConf-2.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  Pango-1.0.gir -o Pango-1.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  PangoFT2-1.0.gir -o PangoFT2-1.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  PangoCairo-1.0.gir -o PangoCairo-1.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  PangoXft-1.0.gir -o PangoXft-1.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  Atk-1.0.gir -o Atk-1.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  GdkPixbuf-2.0.gir -o GdkPixbuf-2.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  Gdk-2.0.gir -o Gdk-2.0.typelib
/home/lightb/gnome-shell/install/bin/g-ir-compiler --includedir=. --includedir=.  Gtk-2.0.gir -o Gtk-2.0.typelib
Gtk-2.0.gir: error: Type reference 'GModule' not found
make[2]: *** [Gtk-2.0.typelib] Error 1
make[2]: Leaving directory `/home/lightb/gnome-shell/source/gir-repository/gir'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lightb/gnome-shell/source/gir-repository'
make: *** [all] Error 2
*** Error during phase build of gir-repository: ########## Error running make   *** [2/9]

  [1] Rerun phase build
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```

I tried everything but cant seem to get rid of it, since yesterday when I did a rebuild.


Distro: Lucid, all packages from 1st page installed.

UPDATE: Solved, just jhbuild build -acf, new working version available.

---

### Post by ronacc on 2010-06-09
did you try deleting everthing and starting from scratch ?

---

### Post by johnyrkj on 2010-06-09
I've a very strange problem with my terminal. Once opened I get a fully  blank terminal with only the blingking console....not even the  uname/hostname is there...its absolutely emply and the cursor blinks in  the very first pixel....And on the top of that it doesn't respond to  commands.....for example typing pwd and enter will just get the letter  pwd typed and cursor goes to the next line...that is the terminal just  looks like an editor...i've tried with alt-f2 to invoke xterm....even  xterm has the same problem....Does anyone has a solution to this  problem....I'm totlally in fix and unable to proceed....I would greatly  appreciate a reply.

---

### Post by ronacc on 2010-06-09
I hate to sugest this for linux , but have you tried a reboot ? If that dont work reboot into recovery mode and update from there .

---

### Post by lesnoland on 2010-06-09
yes i did, i removed bin, jhbuild, .jhbuildrc, .jhbuilrc-custom, gnome-shell, and started again. also i downloaded the script again, and started, still nothing.

> **ronacc said:**
> did you try deleting everthing and starting from scratch ?

---

### Post by ronacc on 2010-06-09
see autocrossers post above and also delete your ~./cache or at least the jhbuild and g-ir-scanner dirs that are in there , thats what did it for me .

---

### Post by davideotape on 2010-06-09
Sigh, still getting this:

```
$ ./gnome-shell --replace
      JS LOG: GNOME Shell started at Wed Jun 09 2010 16:40:58 GMT+0100 (BST)
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
Bug in window manager: Unexpected X error: BadWindow (invalid Window parameter) serial 2047 error_code 3 request_code 2 minor_code 0)
Shell killed with signal 6

```

---

### Post by lesnoland on 2010-06-09
removed .cache, still nothing.

> **ronacc said:**
> see autocrossers post above and also delete your ~./cache or at least the jhbuild and g-ir-scanner dirs that are in there , thats what did it for me .

---

### Post by autocrosser on 2010-06-09
David & lesnoland---

Couple of thoughts--I have been having problems using Firefox or Seamonkey in a GS session--Chrome works (not sure why--have not pinned it down good enough for a bug report)....

Do a fresh build & .tar the build file/PM me & I'll give you my Email...maybe something during build that is bonkers...

Any apps that you are running on GS session start?  Stop services/apps one at a time--may be a conflict--make sure to start GS in a terminal & send/post output....

I'm at work right now---will be home/in front of my system in about 5 hours (US Pacific time---6PM)

Cheers!!!!

---

### Post by Bou on 2010-06-09
Dumb question maybe, but does it happen to you that the version from the repos is nice and smooth and the one from the PPA is much shakier?

---

### Post by ranch hand on 2010-06-09
The one from the repo is "stable" and very far behind development so it should be that way.  It also really does not look a lot like the one from the ppa or the one you build.

There are a lot of features that you are not getting at all in the repo version.

---

### Post by autocrosser on 2010-06-10
Hey Ron---  I've opened a bug with GS...It's been bugging (oh-bad :)  )me for about a week now & I know you are 64 bit like I am....here goes: All of my mozilla browsers (3.6, 3.7 testing & Seamonkey testing 2.0) will crash GS as soon as they open...I'm getting a elf class 32 error---looks like:> dean@linux:~/gnome-shell/install/bin$ ./gnome-shell --replace
/home/dean/.themes/Human-Blue-Lucid/gtk-2.0/gtkrc:141: Invalid color constant
'##C6C7CA'
/home/dean/.themes/Human-Blue-Lucid/gtk-2.0/gtkrc:141: Invalid color constant
'##C6C7CA'
Window manager warning: Workarounds for broken applications disabled. Some
applications may not behave properly.
     JS LOG: GNOME Shell started at Wed Jun 09 2010 20:38:32 GMT-0700 (PST)
/home/dean/.themes/Human-Blue-Lucid/gtk-2.0/gtkrc:141: Invalid color constant
'##C6C7CA'
/home/dean/.themes/Human-Blue-Lucid/gtk-2.0/gtkrc:141: Invalid color constant
'##C6C7CA'
/home/dean/.themes/Human-Blue-Lucid/gtk-2.0/gtkrc:141: Invalid color constant
'##C6C7CA'
/home/dean/.themes/Human-Blue-Lucid/gtk-2.0/gtkrc:141: Invalid color constant
'##C6C7CA'
/home/dean/.themes/Human-Blue-Lucid/gtk-2.0/gtkrc:141: Invalid color constant
'##C6C7CA'
/home/dean/.themes/Human-Blue-Lucid/gtk-2.0/gtkrc:141: Invalid color constant
'##C6C7CA'
Window manager warning: Log level 16: STACK_OP_LOWER_BELOW: window 0x3800486
not in stack
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap
== NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap
== NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: meta_frame_style_draw_with_style:
assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap
== NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: meta_frame_style_draw_with_style:
assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap
== NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: meta_frame_style_draw_with_style:
assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap
== NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: meta_frame_style_draw_with_style:
assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
Bug in window manager: Unexpected X error: BadPixmap (invalid Pixmap parameter)
serial 7670 error_code 4 request_code 54 minor_code 0)
LoadPlugin: failed to initialize shared library
/usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: wrong
ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/usr/lib/mozilla/plugins/libflashplayer.so
[/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/usr/lib/mozilla/plugins/libnullplugin.so
[/usr/lib/mozilla/plugins/libnullplugin.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: wrong
ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/usr/lib/mozilla/plugins/libflashplayer.so
[/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/usr/lib/mozilla/plugins/libnullplugin.so
[/usr/lib/mozilla/plugins/libnullplugin.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: wrong
ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/usr/lib/mozilla/plugins/libflashplayer.so
[/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/usr/lib/mozilla/plugins/libnullplugin.so
[/usr/lib/mozilla/plugins/libnullplugin.so: wrong ELF class: ELFCLASS32]
Shell killed with signal 6

Notn sure what's really going on--I've tried playing with plugins & changing some---why GS b0rks because of something that is not a problem in the normal session--I'm not sure of.....More interestingly, Google Chrome (not Chromium) with the same linked plugin library is not causing a problem....

Bug report is:[https://bugzilla.gnome.org/show_bug.cgi?id=621164](https://bugzilla.gnome.org/show_bug.cgi?id=621164)

This started about a week ago--not sure what commit started the problem....can you confirm or test?

---

### Post by autocrosser on 2010-06-10
Hmmm--I cleaned every single ELF Class32 error up & now I get:> dean@linux:~/gnome-shell/install/bin$ ./gnome-shell --replace
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
      JS LOG: GNOME Shell started at Wed Jun 09 2010 23:13:20 GMT-0700 (PST)
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
Window manager warning: Log level 8: gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
Window manager warning: Log level 8: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
Bug in window manager: Unexpected X error: BadPixmap (invalid Pixmap parameter) serial 12301 error_code 4 request_code 54 minor_code 0)
Shell killed with signal 6
Again only with the Mozilla browser apps....Chrome works normally & I've found out that Opera won't work at all---but it won't crash the system either.....

---

### Post by cariboo on 2010-06-10
Thunderbird crashes GS for me. Firefox seems to be ok, I just haven't bothered tracking the problem down yet. I'm using the ricotz ppa version.

---

### Post by autocrosser on 2010-06-10
Can you run a crash & see what the term output is?  If it looks similar, add to the bug report? How close is the PPA to daily builds?

---

### Post by davideotape on 2010-06-10
I'm not even getting to a stage where I can run anything! When I run it I get a black screen with some artefacts and a cursor, and that's it. I'll try a completely clean build today.

And a suggestion: Could the OP add to the first post which files/directories need to be removed if you want to do a clean build?

---

### Post by MacUntu on 2010-06-10
Currently not building (same output as lesnoland).

---

### Post by davrosuk on 2010-06-10
Its working for me on a fully up-to-date Lucid using the PPA. I really like GNOME Shell - mainly because I don't get screen tearing in iPlayer or YouTube any more (I've never managed to stop that with compiz). 

I do have a bug or two which I've logged. The one that's a little annoying is when I click on the calendar the font is way to small to read - and its the same when I right click on anything in the Activities menu. Don't know if anyone else has that issue - I'm running on an Nvidia 8800 GTS. I do realise that its very early days for GS so I'm sure these niggles will be worked out.

Noticed a very similar bug logged upstream too (so similar I think its the same):
[https://bugzilla.gnome.org/show_bug.cgi?id=599876]("https://bugzilla.gnome.org/show_bug.cgi?id=599876")

---

### Post by Merk42 on 2010-06-10
> **davideotape said:**
> I'm not even getting to a stage where I can run anything! When I run it I get a black screen with some artefacts and a cursor, and that's it. I'll try a completely clean build today.

And a suggestion: Could the OP add to the first post which files/directories need to be removed if you want to do a clean build?

Should just be ~/gnome-shell

Added to the first post though.


Also, my old monitor was going after 10+ years, so now there are fancy new widescreen screenshots.

---

### Post by Peter09 on 2010-06-10
I must admit I was getting a bit jaded with the appearance gnome-shell (it seemed hard and inflexible) until I installed some of the themes drifting around - its looking really good now.

---

### Post by autocrosser on 2010-06-10
> **Peter09 said:**
> I must admit I was getting a bit jaded with the appearance gnome-shell (it seemed hard and inflexible) until I installed some of the themes drifting around - its looking really good now.

Links?  What one are you using? More information please?

---

### Post by Peter09 on 2010-06-10
Here
 
[http://ubuntuforums.org/showthread.php?t=1418056](http://ubuntuforums.org/showthread.php?t=1418056)
 
and
[http://www.webupd8.org/2010/02/5-amazing-gnome-shell-themes-and-how-to.html](http://www.webupd8.org/2010/02/5-amazing-gnome-shell-themes-and-how-to.html)
 
 
as a quick look I cannot find the theme I'm using - I'll keep looking. It has a lot of transparency in it which makes it feel softer.

---

### Post by lesnoland on 2010-06-10
It will work now, I spoke with some people on irc.gnome.org, and it seems it was an ubuntu only issue, but it has been fixed, it works for me at least, you just need to to jhbuild build -acf, or just step 6 again.

> **MacUntu said:**
> Currently not building (same output as lesnoland).

---

### Post by cariboo on 2010-06-10
> **autocrosser said:**
> Can you run a crash & see what the term output is?  If it looks similar, add to the bug report? How close is the PPA to daily builds?

With the ppa update yesterday, Thunderbird didn't crash today. :)

The version I'm using is gnome-shell_2.31.2+git20100610

---

### Post by MacUntu on 2010-06-10
> **lesnoland said:**
> It will work now, I spoke with some people on irc.gnome.org, and it seems it was an ubuntu only issue
I already wondered why there's no bug report about that blocker - now I know. :D

> **lesnoland said:**
> it works for me at least
Yes, for me too. Until it breaks again, of course. QUICK! QUICK! Compile while it's working! ):P

PS: do you guys also get the "fatal: read error: Connection reset by peer" every now and then during checkout?

---

### Post by autocrosser on 2010-06-10
> **MacUntu said:**
> I already wondered why there's no bug report about that blocker - now I know. :D


Yes, for me too. Until it breaks again, of course. QUICK! QUICK! Compile while it's working! ):P

PS: do you guys also get the "fatal: read error: Connection reset by peer" every now and then during checkout?

Yes---normally during mutter or clutter checkout.....I just rerun it & then I get a complete build....

---

### Post by lesnoland on 2010-06-10
Just in case someone gets the wrong colors on the screen (blue turns to brown, yellow to blue, etc), and you are using mesa radeon use the following patch:

[http://bugzilla.openedhand.com/attachment.cgi?id=2001](http://bugzilla.openedhand.com/attachment.cgi?id=2001)

from here:

[http://bugzilla.openedhand.com/show_bug.cgi?id=2100](http://bugzilla.openedhand.com/show_bug.cgi?id=2100)

---

### Post by mr_hangman on 2010-06-17
I have a question. If I previously installed GS from the PPA and now want to try from source, what should I uninstall from the package manager? Is it only gnome-shell or everything that was pulled in (git, mutter,...)?
Right now I'm having this warning every time there is an update in the package manager

```
*** Error during phase build of gobject-introspection: ########## Error running make   *** [1/9]

  [1] Rerun phase build
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
```

---

### Post by autocrosser on 2010-06-19
Major change on building GS this evening....several new parts--ATK, GTK+, Pango---13 total build parts--major increase in download time.

Commit log: > Use GSettings for all Shell configuration. GConf is kept to read configuration from external programs (Metacity, Nautilus and Magnifier), but ShellGConf is removed because it's mostly useless for the few calls we still have. Also get rid of unused GConf code in ShellAppSystem.  A basic GConf schema is still used to override Metacity defaults and configure Magnifier in a system-wide fashion. GConf is also used as GSettings backend via the GSETTINGS_BACKEND environment variable. All of this will be removed when these programs have been ported to GSettings and able to use dconf.  GLib 2.25.9 is required. Schemas are converted to the new XML format, and compiled at build time in data/ so that the Shell can be run from the source tree. This also requires setting the GSETTINGS_SCHEMA_DIR environment variable both when running installed or from source tree, in src/gnome-shell.in and src/gnome-shell-clock-preferences.in.  [https://bugzilla.gnome.org/show_bug.cgi?id=617917](https://bugzilla.gnome.org/show_bug.cgi?id=617917) Be ready for a long download & do a complete rebuild--lots of changes!!!!!  FYI---GTK+ is a 164mb load it self!!!!!

---

### Post by mr_hangman on 2010-06-19
I just tried this new build after a long download. The build get stuck in step 8/13. This is the error


```
configure: WARNING: *** TIFF loader will not be built (TIFF library not found) ***
configure: error: 
*** Checks for TIFF loader failed. You can build without it by passing
*** --without-libtiff to configure but some programs using GTK+ may
*** not work properly
*** Error during phase configure of gtk+: ########## Error running ./autogen.sh --prefix /home/tian/gnome-shell/install --libdir '/home/tian/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [8/13]

  [1] Rerun phase configure
  [2] Ignore error and continue to clean
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 
```

The choice [1] and [5] brings me back to the same warning.
[2] just skips step 8/13 and continue.
[3] quits the build.
[4] says 'exit shell to continue with build' and gives me back the prompt.
[6],[7] and [8] give another warning

```
*** Distcleaning gtk+ *** [8/13]
make   distclean
make: *** No rule to make target `distclean'.  Stop.
```

and the options are reduced to [1]-[5].

Does anybody have any idea what's wrong with my system? Right now I cannot compile gnome shell at all :???:.

---

### Post by xtoudi on 2010-06-19
Just install libtiff4-dev. It is required for GTK+.

---

### Post by MacUntu on 2010-06-19
If you've added ```
module_autogenargs['gconf'] = '--disable-gsettings-backend'
``` to your ~/.jhbuildrc-custom then you now need to remove it.

---

### Post by mr_hangman on 2010-06-19
Thank you. Installing libtiff4-dev solved the problem.
Now when I run ./gnome-shell --replace, I get an error

```
Failed to start shell
Traceback (most recent call last):
  File "./gnome-shell", line 701, in <module>
    
  File "./gnome-shell", line 254, in run_shell
    
  File "./gnome-shell", line 202, in start_shell
    
  File "./gnome-shell", line 127, in _get_glx_extensions
    
  File "/usr/lib/python2.6/subprocess.py", line 633, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1139, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
Cannot register the panel shell: there is already one running.
```

I followed the instructions I found but they seem to be quite old and don't work anymore.


Edited: I reinstalled all dependencies from the repo and it's working now :).
Thanks

---

### Post by phoenixpb on 2010-06-19
I have tried to build gnome shell from source
I have this error message on ubuntu 10.04 lucid

/usr/lib/libpangocairo-1.0.so: undefined reference to `pango_fc_font_create_metrics_for_context'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1

any idea ?

Thanks

---

### Post by autocrosser on 2010-06-19
In a case where you have a non-build:
1. Try building with```
jhbuild build -f -a -c
```
2. If you still have a non-build, trash your entire ~/gnome-shell folder & do a fresh build.
3. If none of the above works---wait 24 hrs & try again---sometimes commits get "stuck".

---

### Post by ranch hand on 2010-06-19
I am going to have to put this on one of my installs.  Sounds like there has been a lot of change.

I installed UNE on my desktop and I have been impressed with it.  It actually seems more usable, to me, than GS.

That is not fair though as I have not seen GS since before the end of 10.04-testing.  going to have to get on the stick here.

---

### Post by autocrosser on 2010-06-19
It looks a bit different--lots of changes under the hood--seeing the start of gtk3--code from the new gdm, etc, etc....They are phasing in the new schema code--edited xml & other fun toys ;)  Look at my #227 posting.....

All in all good fun whilst Maverick is a bit boring.....

---

### Post by Merk42 on 2010-06-19
> **autocrosser said:**
> It looks a bit different--lots of changes under the hood--seeing the start of gtk3--code from the new gdm, etc, etc....They are phasing in the new schema code--edited xml & other fun toys ;)  Look at my #227 posting.....

All in all good fun whilst Maverick is a bit boring.....

The only UI difference I noticed was the icon next to your name in the upper right

---

### Post by autocrosser on 2010-06-20
The applications list sorting has been changed--the old side menu thing has been dropped--changes in the way the notifications area is displayed (ubuntu-specific ways are reverted) & a couple of other things that I'm not remembering right now.....there have been a couple of interesting commits as of late.....

Most of the interesting things are not visible--adding Pango, GTK+, ATK & a couple of other depends to the build.

More info: the Applications in overlay has been divided into three sub-groups--Apps, Games & Tools.

  One of the "interesting" commits:> Canonical replaced status icons with libindicator based solutions, which don't work in the shell environment. Force the distro-patched versions to fall-back to upstream.  [https://bugzilla.gnome.org/show_bug.cgi?id=621382](https://bugzilla.gnome.org/show_bug.cgi?id=621382) 

Another one:> Add animated display of startup notification
The shell design says that upon launching an application, no X window should have focus, and we should display an animated launching indicator.  Implement this by in panel.js, keep track of the last started application.  If there isn't currently an X focus, show an animation for the last starting application.  [https://bugzilla.gnome.org/show_bug.cgi?id=598349](https://bugzilla.gnome.org/show_bug.cgi?id=598349) 


---

### Post by MacUntu on 2010-06-20
I wonder when they'll do something about GS's speed - everything feels sluggish on my two test systems (especially when compared to the Unity shell, but I guess that's no fair comparison).

---

### Post by joshmuffin on 2010-06-20
Hey I've been trying to get gnome-shell working on 10.04 for a while using all 3 install methods but they never seem to work. Any who last night I did a clean install and I know have a partition with 10.10 alpha on it aswell as my 10.04 partition. I'm using the maverick partition just to much around and test things out. I tried installing gnome shell from the repo's (to see if I could even get it started) and what a surprise, nothing.
Here's the output:
```
josh@josh-desktop:~$ gnome-shell --replace

(mutter:23316): mutter-WARNING **: Plugin API mismatch for [/usr/lib/mutter/plugins/libgnome-shell.so]
^CShell killed with signal 2
josh@josh-desktop:~$ Cannot register the panel shell: there is already one running.
compiz (core) - Warn: SmcOpenConnection failed: None of the authentication protocols specified are supported

```

If anyone has any idea how to fix this it would be most appreciated. I might try installing gnome shell the jhbuild way but I can't imagine it working anyway. 

Thanks, Josh

---

### Post by wojox on 2010-06-20
I Build Gnome Shell from source this morning. I did this a few months ago and I have to say it's coming along nice and stable.

One question I have is in the top right corner by my name there is a Network Applet and what looks like Gnome Control Center Applet.

I've tried everything, right,left, middle clicking. It doesn't do anything. Anyone else have this problem? Is their a work around for this?

I'm of to check out some Gnome Shell Themes. :p

---

### Post by wojox on 2010-06-20
> **joshmuffin said:**
> Hey I've been trying to get gnome-shell working on 10.04 for a while using all 3 install methods but they never seem to work. Any who last night I did a clean install and I know have a partition with 10.10 alpha on it aswell as my 10.04 partition. I'm using the maverick partition just to much around and test things out. I tried installing gnome shell from the repo's (to see if I could even get it started) and what a surprise, nothing.
Here's the output:
```
josh@josh-desktop:~$ gnome-shell --replace

(mutter:23316): mutter-WARNING **: Plugin API mismatch for [/usr/lib/mutter/plugins/libgnome-shell.so]
^CShell killed with signal 2
josh@josh-desktop:~$ Cannot register the panel shell: there is already one running.
compiz (core) - Warn: SmcOpenConnection failed: None of the authentication protocols specified are supported

```

If anyone has any idea how to fix this it would be most appreciated. I might try installing gnome shell the jhbuild way but I can't imagine it working anyway. 

Thanks, Josh

Do you have these Packages installed?

```
sudo apt-get install mutter mutter-common gir1.0-clutter-1.0 libclutter-1.0-0 gjs gir1.0-freedesktop gir1.0-glib-2.0 gobject-introspection libgirepository1.0-0
```

---

### Post by davideotape on 2010-06-20
Any chance that we could have libtiff4-dev added to the packages in the original post - [http://ubuntuforums.org/showpost.php?p=9482358&postcount=229](http://ubuntuforums.org/showpost.php?p=9482358&postcount=229)

---

### Post by Merk42 on 2010-06-20
> **davideotape said:**
> Any chance that we could have libtiff4-dev added to the packages in the original post - [http://ubuntuforums.org/showpost.php?p=9482358&postcount=229](http://ubuntuforums.org/showpost.php?p=9482358&postcount=229)

Is that mandatory now or just a temporary workaround?

---

### Post by davideotape on 2010-06-20
I should think it's mandatory if GTK+ is being built. And I'm still getting a right mess when starting gnome-shell (clean build from source) - 

```
$ ./gnome-shell --replace
      JS LOG: GNOME Shell started at Sun Jun 20 2010 13:36:30 GMT+0100 (BST)

(mutter:24235): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:24235): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:24235): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:24235): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:24235): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:24235): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:24235): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:24235): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:24235): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:24235): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:24235): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:24235): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:24235): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:24235): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:24235): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:24235): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:24235): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:24235): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:24235): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:24235): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
^CShell killed with signal 2
dstansby@dstansby-desktop:~/gnome-shel
```

---

### Post by wojox on 2010-06-20
> **davideotape said:**
> Any chance that we could have libtiff4-dev added to the packages in the original post - [http://ubuntuforums.org/showpost.php?p=9482358&postcount=229](http://ubuntuforums.org/showpost.php?p=9482358&postcount=229)

Have you tried downloading it? It's just a package.

---

### Post by wojox on 2010-06-20
Merk42 have you seen my post on building the shell from src? [http://ubuntuforums.org/showpost.php?p=9486605&postcount=240](http://ubuntuforums.org/showpost.php?p=9486605&postcount=240)

---

### Post by davideotape on 2010-06-20
> **wojox said:**
> Have you tried downloading it? It's just a package.

Yes, I've installed it, I just thought it might be a good idea to get it put in the original post as a package that needs installing from the Ubuntu repo before building gnome-shell.

---

### Post by wojox on 2010-06-20
> **davideotape said:**
> Yes, I've installed it, I just thought it might be a good idea to get it put in the original post as a package that needs installing from the Ubuntu repo before building gnome-shell.


Okay, I follow what your saying now. :p

---

### Post by Merk42 on 2010-06-20
Added libtiff4-dev to the OP

> **wojox said:**
> Merk42 have you seen my post on building the shell from src? [http://ubuntuforums.org/showpost.php?p=9486605&postcount=240](http://ubuntuforums.org/showpost.php?p=9486605&postcount=240)The network manager for me works the same as it does using GNOME Panel

---

### Post by Nr90 on 2010-06-20
Do other people with laptops still experience the slowness of GS?
I haven't tried attaching another monitor to see if it speeds up.
Like this it is to laggy to use comfortably.

---

### Post by uBeer on 2010-06-20
> **Nr90 said:**
> Do other people with laptops still experience the slowness of GS?
I haven't tried attaching another monitor to see if it speeds up.
Like this it is to laggy to use comfortably.

Well, I do note that window movement feels like it is a few frames behind. Metacity composited and Compiz do a way better job of moving the window.
And going into the overlay stutters.

Tested on NVIDIA 9800 GT with nvidia drivers.

---

### Post by quickridge on 2010-06-20
I'm not sure why it would depend on whether or not you are on a laptop. Anyway, it works fine on mine. Although, I do get that screen flicker sometimes (possibly related to propriety nvidia drivers?).

---

### Post by mr_hangman on 2010-06-20
I just noticed this too. The window movement is indeed slower than the mouse. 
The frame rate of the effects is also low including video in overlay mode.
I'm on NVIDIA 8600M GS with proprietary driver.

---

### Post by autocrosser on 2010-06-20
It's to do with the nvidia cards---I'm running a SLI-dual 9800GT set & I get a couple of frames behind also...

---

### Post by wojox on 2010-06-20
> **Merk42 said:**
> Added libtiff4-dev to the OP

The network manager for me works the same as it does using GNOME Panel

Okay I rebooted and every thing is fine. :p

---

### Post by Mblackwell on 2010-06-20
[https://bugzilla.gnome.org/attachment.cgi?id=157326](https://bugzilla.gnome.org/attachment.cgi?id=157326)

This should give people not using xserver 1.9 reduced flickering (if any) and increased performance.

Source:
[https://bugzilla.gnome.org/show_bug.cgi?id=613936](https://bugzilla.gnome.org/show_bug.cgi?id=613936)

---

### Post by dino99 on 2010-06-21
> **Mblackwell said:**
> [https://bugzilla.gnome.org/attachment.cgi?id=157326](https://bugzilla.gnome.org/attachment.cgi?id=157326) [COLOR="Red"]look the date:[/COLOR] [COLOR="Blue"]Mon Sep 17 00:00:00 2001[/COLOR]


This should give people not using xserver 1.9 reduced flickering (if any) and increased performance.

Source:
[https://bugzilla.gnome.org/show_bug.cgi?id=613936](https://bugzilla.gnome.org/show_bug.cgi?id=613936)

so few years later  :confused:

---

### Post by Mblackwell on 2010-06-21
Uh... Huh? The patch hasn't been around that long. Just since March. The fix isn't really a fix, it's a workaround for a bug in Xserver that was tracked down and fixed in 1.9. Read the bug report before making comments like that...

---

### Post by Peter09 on 2010-06-21
Just downloaded the latest update from the ricotz repository. Gnome-shell fails to install and leaves me with a screen that flickers and is unresponsive.

---

### Post by xtoudi on 2010-06-21
> Add animated display of startup notification
The shell design says that upon launching an application, no X window should have focus, and we should display an animated launching indicator. Implement this by in panel.js, keep track of the last started application. If there isn't currently an X focus, show an animation for the last starting application. [https://bugzilla.gnome.org/show_bug.cgi?id=598349](https://bugzilla.gnome.org/show_bug.cgi?id=598349)

Is there anyone here who can tell me where can I find this in GS?? 
I usually rebuild all my GS ever day, right after new commits in [http://git.gnome.org/browse/gnome-shell](http://git.gnome.org/browse/gnome-shell) ... I noticed this commit a few days ago and so far I don't see any effects 
According to commit thread ([https://bugzilla.gnome.org/show_bug.cgi?id=598349](https://bugzilla.gnome.org/show_bug.cgi?id=598349)) should be an animated effect right on/after application name ... top panel.

---

### Post by Peter09 on 2010-06-22
after an update from Ricotz repository I am getting this erro.

GLib-GIO-ERROR **: Settings schema 'org.gnome.shell' is not installed


and gnome-shell fails to run. Any hints?

---

### Post by youoh on 2010-06-22
dependecies are off

remove gnome-shell

install libglib2.0-dev

reinstall gnome-shell

voila

---

### Post by Mblackwell on 2010-06-22
Is anyone else having this? I tried to file a bug but the server seems to be having an issue. Whenever I restart Gnome Shell it resets my custom settings now, including my favorites and my current workspace view to linear.

---

### Post by youoh on 2010-06-22
+1

---

### Post by Mblackwell on 2010-06-22
Good to know. I filed a bug, actually 3, since I noticed you can't move windows between workspaces rapidly, and worse I noticed for some reason now changing the resolution while in gnome shell causes X to freeze.

---

### Post by Nr90 on 2010-06-22
> **Peter09 said:**
> after an update from Ricotz repository I am getting this erro.

GLib-GIO-ERROR **: Settings schema 'org.gnome.shell' is not installed


and gnome-shell fails to run. Any hints?

Same here,
Tried what Youoh posted, but didn't help.

Have you made a bug?

---

### Post by Peter09 on 2010-06-22
No not had chance to put a bug report in yet.

---

### Post by Mblackwell on 2010-06-22
> **youoh said:**
> +1

Update the PPA. It's resolved now.

---

### Post by stan3a on 2010-06-25
> **Peter09 said:**
> after an update from Ricotz repository I am getting this erro.

GLib-GIO-ERROR **: Settings schema 'org.gnome.shell' is not installed


and gnome-shell fails to run. Any hints?

I found I needed to run:

```
sudo glib-compile-schemas /usr/share/glib-2.0/schema
```

---

### Post by Peter09 on 2010-06-25
Does anyone else have this issue with the current design of Gnome-Shell.
I have a wide screen HP Pavilion laptop 17" type job, nearly a desktop :)
 
Anyway in the overview mode with two or more workspaces open, if I want to drag an application to a 'far' workspace I run out of touchpad room. Lifting a finger to move backwards to continue the drag leaves the application in a 'near' workspace.
 
While, I guess, this is not a really big issue, it just makes things a bit clumsy.

---

### Post by MadCookie on 2010-06-26
> **Peter09 said:**
> Does anyone else have this issue with the current design of Gnome-Shell.
I have a wide screen HP Pavilion laptop 17" type job, nearly a desktop :)
 
Anyway in the overview mode with two or more workspaces open, if I want to drag an application to a 'far' workspace I run out of touchpad room. Lifting a finger to move backwards to continue the drag leaves the application in a 'near' workspace.
 
While, I guess, this is not a really big issue, it just makes things a bit clumsy.

Can't you just change your mouse settings?

---

### Post by Shivan on 2010-06-30
that's not really a software problem. you wouldn't file a bug because your mouse reached the edge of your physical desk.

---

### Post by NightwishFan on 2010-07-01
I quit using the shell since I install Lucid, I come back and it is amazing. The Gnome developers really know what we need in a user interface.

Of course it is not perfect. I could do with the activities animation being redone a little. It feels sluggish once you are used to it. Though I like the comfort of an animated interface.

---

### Post by Paulgirardin on 2010-07-03
> **Peter09 said:**
> Does anyone else have this issue with the current design of Gnome-Shell.
I have a wide screen HP Pavilion laptop 17" type job, nearly a desktop :)
 
Anyway in the overview mode with two or more workspaces open, if I want to drag an application to a 'far' workspace I run out of touchpad room. Lifting a finger to move backwards to continue the drag leaves the application in a 'near' workspace.
 
While, I guess, this is not a really big issue, it just makes things a bit clumsy.

I agree.
I think the "Add Workspaces +" button would be better made larger and positioned nearer the Applications panel.

---

### Post by luceerose on 2010-07-04
I installed from source without a problem.
Running Maverick with nvidia. Using Amarok & Thunderbird w/ firetray plugin.
I tried GS a few weeks ago & didn't like it but I'm trying it again.
I played around with the .css file & some of the .js files, changed fonts, reduced Icon size to fit more in applications menu, etc.
After those minor tweaks I'm starting to get used to it.
Now I think GS is starting to show some real promise.
Just a few minor issues I stumbled across;
1) The openoffice tray icon isn't there, although the quickstarter does seem to be active, just no icon.
2) I had to add the volume icon to startup programs. I don't really mind that I had to add it manually, at least I have a volume in the panel now.
3) Could someone tell me how to make the date on the panel say, like, "Monday July 5" instead of "Mon Jul 5" ?

I like the applications area. It looks great. But I would rather it list all open applications, not just the one in foreground. And I'd prefer it on a bottom panel along with a trashcan & the ability to add applets.

---

### Post by luceerose on 2010-07-04
Ok, the openoffice quickstarter icon just showed up for some reason.
I don't know why.
Weird.

---

### Post by Mblackwell on 2010-07-04
> **larsenguitars said:**
> 3) Could someone tell me how to make the date on the panel say, like, "Monday July 5" instead of "Mon Jul 5" ?

I like the applications area. It looks great. But I would rather it list all open applications, not just the one in foreground. And I'd prefer it on a bottom panel along with a trashcan & the ability to add applets.

3) Right click and select Preferences. You can change the format there.

As for applets, there are no Applets in Gnome Shell. There's no such thing. And the bottom panel is reserved for notifications and tray icons (eventually).

As for the application icon on the top panel that will eventually be full menu of some kind for that application. I can't recall if it's completely spec-ed out yet.

---

### Post by davideotape on 2010-07-06
Gnome-shell still refuses to work properly for me:

```
~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Starting dconf-service...  started
      JS LOG: GNOME Shell started at Tue Jul 06 2010 14:08:45 GMT+0100 (BST)

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:18206): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:18206): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed
^CShell killed with signal 2

```

---

### Post by Peter09 on 2010-07-06
I think the current default theme for gnome-shell does not do it any favors, it provides a very hard look to the interface. It really should be changed now to give a softer experience. Making a softer theme overcomes (somewhat) the criticism of context change from workspace to overlay.

I have been using GS for some time now and think its  very good. indeed switching back to normal gnome is annoying, fiddling with all those long menus. 

The dock in the overlay is excellent and the ability to just hit the windows key and start typing a name to get to application, once you realize you can do it, is a great time saver. 

I also use the overlay mode to monitor multiple windows (email, player, terminal etc) from the same view.

I've attached my current desktop, which is themed. (not designed by me).

---

### Post by NightwishFan on 2010-07-06
That is a really cool theme! :)

---

### Post by autocrosser on 2010-07-06
> **Peter09 said:**
> I've attached my current desktop, which is themed. (not designed by me).

Where did you get that one?  looks quite good!!

---

### Post by Peter09 on 2010-07-07
Its one of the themes from this thread
[http://ubuntuforums.org/showthread.php?t=1418056](http://ubuntuforums.org/showthread.php?t=1418056)

Unfortunately I'm not quite sure which one it is, I think it may be from post 71 in the thread. Anyway I'll attach the theme here.

---

### Post by autocrosser on 2010-07-07
Heads up everyone!!!!  Major changes to the build tonight----GTK3 has been included along with all the depends.  I have been building/downloading for over 35 minutes now & am at 8/21---looks like MAJOR changes to the shell are in order.

---

### Post by hrhnick on 2010-07-07
> **autocrosser said:**
> Heads up everyone!!!!  Major changes to the build tonight----GTK3 has been included along with all the depends.  I have been building/downloading for over 35 minutes now & am at 8/21---looks like MAJOR changes to the shell are in order.

so exciting. will this improve speed/performance?

---

### Post by autocrosser on 2010-07-07
I'm not sure---yet....   I had 3 errors on the build, so I'm doing a clean rebuild---almost thru & will post after with impressions.....

---

### Post by autocrosser on 2010-07-07
Well---It's a "wait & see"---2 errors in the final build (gnome-shell) with a non-run.....Looks like I need to trash my current install & totally start from scratch again....Or they have not updated the gnome-shell builds....

Run trace looks like this:

dean@linux:~/gnome-shell/install/bin$ ./gnome-shell --replaceGtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
    JS ERROR: !!!   Exception was: Error: Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded")@:0
("Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded")@gjs_throw:0
@/home/dean/gnome-shell/install/share/gnome-shell/js/ui/main.js:18
'
    JS ERROR: !!!     message = 'Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded'
    JS ERROR: !!!   Exception was: Error: Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded")@:0
("Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded")@gjs_throw:0
@/home/dean/gnome-shell/install/share/gnome-shell/js/ui/main.js:18
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
@<main>:1
'
    JS ERROR: !!!     message = 'Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded
/home/dean/.themes/MurrinaLoveGray/gtk-2.0/gtkrc:50: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.

---

### Post by Merk42 on 2010-07-07
I tried going back to the very beginning and it wanted to install a few more dependencies:
sudo apt-get install libtiff-dev libpng-dev libjpeg-dev

unfortunately, this happens
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libtiff4-dev instead of libtiff-dev
libtiff4-dev is already the newest version.
Note, selecting libpng12-dev instead of libpng-dev
libpng12-dev is already the newest version.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
```

So when you try to rerun /bin/bash gnome-shell-build-setup.sh it still complains of the same dependencies

---

### Post by autocrosser on 2010-07-07
Yes--I just did the jhbuild (bypassing /bin/bash gnome-shell-build-setup.sh) & got a build----but there is a part of gtk3 that is giving the gnome-shell final build fits. (it can't build the test-theme & bombs out)  I'm going to wait until tomorrow to see if things are ironed out.....

---

### Post by Finalfantasykid on 2010-07-08
^I'm getting that as well.  I'm doing a rebuild to see if it works, otherwise like you I might have to wait until tomorrow or something for it to work.

I'm also still getting this error when using gnome-shell.

```
Clutter-WARNING **: The required ID of 65948 does not refer to an existing actor; 
this usually implies that the pick()
of an actor is not correctly implemented or that there is an error in the glReadPixels()
implementation of the GL driver.

```

---

### Post by Saner on 2010-07-08
> 
<russo79> Saner: Try using this file ([http://pastebin.com/ytpgBxbT](http://pastebin.com/ytpgBxbT)) instead of gnome-shell-build-setup.sh 
<russo79> Saner: I explicitly set the dependencies of ubuntu packages.



Cant say its going to work because I am still building, but it solves the dependencies issue.

---

### Post by 23dornot23d on 2010-07-09
I have not been able to get Gnome3 running since the Safe-Upgrade yesterday - 
I have had it running in the past though and it looked quite good.

The desktop Mutter is great for me ..... have added Cairo Dock and it gives it a really clean professional feel ..... and can choose all the 4 desktops and run most programs.

Ksnapshot would not work from the Gmenu ..... but runs fine from a terminal window, dragged and dropped the icon in that works in Gnome Desktop ..... but when switching here it stops working ......

Here is the way it looks if you can ignore the terminal window ..... it has a [E17 feel to it]("http://5270667693938030042-a-1802744773732722657-s-sites.googlegroups.com/site/23dsources/allsorts/DesktopLucidtoMaverick23.jpeg?attachauth=ANoY7cqvBk9r4Me9UJXkDu_BLivMOLcaEbKugF1wdVUEzzLeFN3ru9pJZOlytXHMjXR-HINJZv39O29cPUL3iM2VJFH5sbk2tbcHOxBFfa7N5hlmW1D0jH4hxe9dxgdhQBlKrgKgh59WfL431e3TSuSreBlUBL5fG0eOAcIogYp_KN7q_kee241_UaXOosBVcJV38mZCgE_-NKkjfg2laQUqP3qh_EZt5H-HViPjFCbNdWjAICByL1k%3D&attredirects=0").

I like this Desktop the way it is and it will now stay like this on my computer ...... 
( To log out and use another desktop if you set it up this way - use the middle mouse button on the red exit off switch - took some finding so thought I would mention it here - for those that do not know about it )



I followed this ..... to try to set up [Gnome3 (Gnome-shell)]("http://joneslee85.wordpress.com/2010/06/06/howto-install-gnome-shell-on-ubuntu-maverick-10-10/") but its not working yet the screen goes completely white as it goes in .... which is odd ..... similar to what compiz would do when it was not going to work in the early days .........

Ok got it running after adding the dependencies at the beginning of this thread

aptitude install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential

[Gnome 3]("http://5270667693938030042-a-1802744773732722657-s-sites.googlegroups.com/site/23dsources/allsorts/DesktopLucidtoMaverick24.jpeg?attachauth=ANoY7cp7AciLtlvOAy_34ianLfYUiQsNRuleUAKXiB5sD_SsbzsU8qJjcuMd6rRKbyWw73HTQCtGwzzCfBZRmnSYg5QeStM670bKkDWNMm2a5O7XR1tl6pgF9nLE3-bzmrobVaJIxOaxuioxAWOImMHOvrZwOtnHJc5YV2SjzjockqlX_loHKSMnIqb3fubDryFDThGY3-Y6PcGC10ZXDb7qIGSfJbZlXbWRgQ7YeXytAs9c7mFhE7Y%3D&attredirects=0")

Will start testing it now .... ksnapshot works from the find option now in Activities ......

(Was going to use Gtk-recordmydesktop to make a video of it ...... but the top menu bar disappears when going into record mode ..... also the ogv files are turning into garbage on You-Tube and in Openshot ..... seems to be the file format works ok in VLC though bizarre ? has it changed ? used to be able to put my tutorials staight into [You-Tube what's happened here then ?]("http://sites.google.com/site/blenderlearn/assignments/project3")
go down to the bottom of the link page if you want to see the results ....)

Here is the [raw OGV file its 9 Meg]("http://sites.google.com/site/23dsources/allsorts/out-1.ogv?attredirects=0&d=1") if anybody wants to check it out .........

Wow just had 70 degrees on the thermal reading for the Graphics Card ....... usually runs around 56 - 58 ....... dropped back
into normal Gnome and already its dropped 3-4 degrees ....... might be that I was running video ..... but its the highest
I have ever seen on this computer ...... the battery feels hot too ...... but not sure how to check the thermal reading for that though ....... will turn it all
off for time being ......... and try again tomorrow or tonight with this computer  ..... it is an extremely hot day here .......

The feel of Gnome 3 could grow on me ..... very organised and easy  to use ....

---

### Post by NightwishFan on 2010-07-09
Go to the... lace of lost voices.... ther.. great power... find what you seek. :)


If it is a very hot day I advise you store your battery somewhere room temperature. It is not good for a battery to be in 90f temperatures. I do not think Gnome Shell should cause much overhead if it is not constanly animating, because that should be done by the graphics card. What chip do you have?

---

### Post by BwackNinja on 2010-07-09
> **autocrosser said:**
> Well---It's a "wait & see"---2 errors in the final build (gnome-shell) with a non-run.....Looks like I need to trash my current install & totally start from scratch again....Or they have not updated the gnome-shell builds....

Run trace looks like this:

dean@linux:~/gnome-shell/install/bin$ ./gnome-shell --replaceGtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
    JS ERROR: !!!   Exception was: Error: Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded")@:0
("Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded")@gjs_throw:0
@/home/dean/gnome-shell/install/share/gnome-shell/js/ui/main.js:18
'
    JS ERROR: !!!     message = 'Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded'
    JS ERROR: !!!   Exception was: Error: Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded")@:0
("Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded")@gjs_throw:0
@/home/dean/gnome-shell/install/share/gnome-shell/js/ui/main.js:18
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
@<main>:1
'
    JS ERROR: !!!     message = 'Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring Shell, version none: Requiring namespace 'Gtk' version '2.0', but '3.0' is already loaded
/home/dean/.themes/MurrinaLoveGray/gtk-2.0/gtkrc:50: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.

From what I see, there is a check for gtk 2.0 but 3.0 is there instead. Just change the check. It should be on or at least referenced on line 18 of /home/dean/gnome-shell/install/share/gnome-shell/js/ui/main.js. It should run after that or at least give some more interesting errors.

---

### Post by 23dornot23d on 2010-07-09
> **NightwishFan said:**
> Go to the... lace of lost voices.... ther.. great power... find what you seek. :)


If it is a very hot day I advise you store your battery somewhere room temperature. It is not good for a battery to be in 90f temperatures. I do not think Gnome Shell should cause much overhead if it is not constanly animating, because that should be done by the graphics card. What chip do you have?


Cheers ..... 

I have just had a good read up on the batteries .... 

I think I will take it out ....... the computer is dual core 2.1 ghz .... and when doing nothing was 70% on both processors ,,,,,, its having a rest now as it went back up to 70 again in Gnome3 ..... it drops at least 5 degrees when I return to Gnome ...... am constantly aware of the problems with the graphics drivers from the last overheating of Graphics Cards ..... the battery is another thing ..... but its not that far away from the Graphics card ........

I have just upgraded and noticed at first a drop in temps on the 9300 Nvidia Graphics Card ....... after the upgrade ,,,,,,,,,, 

I have a Desktop and running the same latest Nvidia driver that is low at 46 degrees a big difference,

Will try again later its getting dark here now and the temps do drop ......... 

I am on a different laptop at the moment so I cannot give a great deal of information yet .........

Here is the link showing the Thermal at 69 degrees .

[http://sites.google.com/site/keithaerospace92/mylinks](http://sites.google.com/site/keithaerospace92/mylinks)

---

### Post by cariboo on 2010-07-09
This thread is drifting away from gnome-shell testing, please start new threads for anything not pertaining to gnome-shell.

---

### Post by 23dornot23d on 2010-07-10
I have been only running and using gnome3 ..... for 5 hours today after the latest upgrades .....  
My main applications used today were Blender Wings3d and Firefox it dropped out of Firefox once for some strange reason then auto resumed 
(will check and see if it was recorded in the logs).
The GPU is at 61 degrees ..... even though its exceptionally hot here again but this Temp 61 is ok now using gnome3.



This is all I can see a Seg Fault by Mutter ..... but I do not understand it ...... this info was taken from the Syslog

Jul 10 16:05:00 keith-laptop kernel: [ 6231.761940] mutter[1936]: segfault at fe8f8f8f ip 00a13a19 sp bfc0af70 error 4 in libglib-2.0.so.0.2510.0[9b9000+c9000]
Jul 10 16:09:01 keith-laptop CRON[5874]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jul 10 16:17:01 keith-laptop CRON[5939]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 10 16:39:01 keith-laptop CRON[6146]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jul 10 16:39:39 keith-laptop kernel: [ 8310.653070] CE: hpet increased min_delta_ns to 11250 nsec
Jul 10 16:45:11 keith-laptop kernel: [ 8643.153082] CE: hpet increased min_delta_ns to 16875 nsec
Jul 10 17:09:01 keith-laptop CRON[6465]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jul 10 17:17:01 keith-laptop CRON[6542]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


The version of Maverick I am running here is a Upgrade from Lucid Lynx 10.04 to 10.10 ..........
keith@keith-laptop:~$ uname -a
Linux keith-laptop 2.6.35-6-generic #9-Ubuntu SMP Wed Jun 30 23:09:46 UTC 2010 i686 GNU/Linux

(Once I work out how to upgrade the Kernel **without the automatic Grub Update** destroying my menu System - 

Its sorted  ...... LOVE it MAVERICK ROCKS .. >>>>>>

The[ Grub update]("http://sites.google.com/site/problems7730zg/home/grub-2-problem-of-other-operating-systems-wanting-to-overwrite-the-good-one") works on Aptitude Safe-Upgrade without getting rid of my menu now .........

My menu system is still at 1440x900 and my nice background to the menu that I have set up is still there - great.

keith@keith-laptop:~$ uname -a
Linux keith-laptop 2.6.35-7-generic #12-Ubuntu SMP Fri Jul 9 21:09:19 UTC 2010 i686 GNU/Linux
keith@keith-laptop:~$

---

### Post by mr_hangman on 2010-07-10
I just removed gnome-shell folder in my home and started jhbuild from nothing.
The compilation got stuck at step 20/21 and gave this error,

```
make[3]: Entering directory `/home/tian/gnome-shell/source/gnome-shell/src'
  CCLD   test-theme
/home/tian/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/tian/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/tian/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status

```

Does anybody have this problem?

---

### Post by BwackNinja on 2010-07-10
> **mr_hangman said:**
> I just removed gnome-shell folder in my home and started jhbuild from nothing.
The compilation got stuck at step 20/21 and gave this error,

```
make[3]: Entering directory `/home/tian/gnome-shell/source/gnome-shell/src'
  CCLD   test-theme
/home/tian/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/tian/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/tian/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status

```

Does anybody have this problem?

Looks like you need glib newer than this commit 3 days ago where g_variant_new_bytestring_array is introduced:

[http://git.gnome.org/browse/glib/commit/?id=d9e90c3894739bdfa642e35bdea866c6d0ab7ef2](http://git.gnome.org/browse/glib/commit/?id=d9e90c3894739bdfa642e35bdea866c6d0ab7ef2)

---

### Post by mr_hangman on 2010-07-10
> **BwackNinja said:**
> Looks like you need glib newer than this commit 3 days ago where g_variant_new_bytestring_array is introduced:

[http://git.gnome.org/browse/glib/commit/?id=d9e90c3894739bdfa642e35bdea866c6d0ab7ef2](http://git.gnome.org/browse/glib/commit/?id=d9e90c3894739bdfa642e35bdea866c6d0ab7ef2)

I'm sorry but I have no idea how to get a newer glib.
Do you have an instruction on that?

---

### Post by KdotJ on 2010-07-10
Hey guys, I added the PPA to my repos, did a apt-get update and an apt-get upgrade, installed gnome-shell and did the old gnome-shell --replace

My terminal threw this back at me...

```

Starting dconf-service...  
Failed to start /usr/lib/gnome-shell/dconf-service: [Errno 2] No such file or directory

```

any ideas here?

---

### Post by srikumar on 2010-07-10
Same here. I have been using Ricotz's ppa for months now. gnome-shell just stopped working today after an update. Hopefully, this will be fixed with another update soon.

---

### Post by 23dornot23d on 2010-07-10
After I added the PPA and did the update and upgrade ......

I also did the following .......... then it worked OK ......... 
I am running Gnome3 now and have added all the latest updates - also re booted and still ok .......

( Ok I got it running after adding the dependencies at the beginning of this thread - you could try this )

**aptitude install** curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev  xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev  libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev  libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev  libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core  flex bison automake build-essential

---

### Post by srikumar on 2010-07-10
> **23dornot23d said:**
> 
**aptitude install** curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev  xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev  libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev  libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev  libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core  flex bison automake build-essential

Tried that, didn't work. It seems you are building gnome-shell from source, which explains all those *-dev packages. I am trying to use the binaries built in ricotz/testing ppa.

---

### Post by x-shaney-x on 2010-07-11
I'm just wondering if anyone is using gnome shell from the standard maverick or lucid repos?
It's a while since I gave it a whirl but it refuses to install on either lucid or maverick due to a version dependency problem.

I've found the ricotz ppa gives me problems (mainly with unity) and I just don't do compiling anymore (gentoo put me off that for life).

---

### Post by cariboo on 2010-07-11
> I'm just wondering if anyone is using gnome shell from the standard maverick or lucid repos?
It's a while since I gave it a whirl but it refuses to install on either lucid or maverick due to a version dependency problem.

I've found the ricotz ppa gives me problems (mainly with unity) and I just don't do compiling anymore (gentoo put me off that for life).

The version of mutter that Unity uses is different from the version that gnome-shell uses, so you're bound to have problems.

---

### Post by KdotJ on 2010-07-11
Thanks for the suggestions guys. I'm not really after building gnome-shell from source though.  
Just to clarify, is gnome-shell the same thing as gnome3 ??

---

### Post by Merk42 on 2010-07-11
> **KdotJ said:**
> Just to clarify, is gnome-shell the same thing as gnome3 ??

**No**

GNOME-Shell is only one aspect of GNOME 3.
Others are GTK3+ and Zeitgeist

As such you'll be able to use GNOME3's GTK3+ and Zeitgeist, yet still use GNOME 2.X's panel interface.

---

### Post by KdotJ on 2010-07-11
> **Merk42 said:**
> **No**

GNOME-Shell is only one aspect of GNOME 3.
Others are GTK3+ and Zeitgeist

As such you'll be able to use GNOME3's GTK3+ and Zeitgeist, yet still use GNOME 2.X's panel interface.


Oh ok, thanks for clearing that up for me. 
So the user can pick an choose aspects? (but not have gnome-shell with the gnome 2.x panels?)
how can I test gnome3 now?

---

### Post by Merk42 on 2010-07-11
> **KdotJ said:**
> Oh ok, thanks for clearing that up for me. 
So the user can pick an choose aspects? (but not have gnome-shell with the gnome 2.x panels?)
how can I test gnome3 now?

Read the first post of this thread...
(keep in mind there are currently some issues building due to a massive change)

---

### Post by KdotJ on 2010-07-11
> **Merk42 said:**
> Read the first post of this thread...
(keep in mind there are currently some issues building due to a massive change)


Thanks Merk42, but this is for gnome-shell. I was wonderig how to I stall and play around with the other aspects of gnome3 which were outlined a to me in the last few posts. Recently, gnome-shell won't load for m, but I'm assuimg this is due to the current big updates then

---

### Post by autocrosser on 2010-07-11
Ok--I found the bug that was causing GS to do a non-build:  [https://bugzilla.gnome.org/show_bug.cgi?id=623952](https://bugzilla.gnome.org/show_bug.cgi?id=623952)

Apparently, there is a problem with .la files in /usr/lib---the "fix" is to move all the .la files out into a backup file. I will be looking at the files to see which one is causing the problem & add the info to the report & post it here.......

With the fix, GS can build without errors---I do not see any "major" differences using gtk3, however there is a noticeable speed improvement dragging windows around with my Nvidia SLI card setup---"almost" real time movement now---I'm sure that the Intel & ATI card users will see some improvement also......The flash during animation is mostly gone--I do see it 1 out of 4~5 times now--it use to be every time, so that is a real plus also.

---

### Post by xtoudi on 2010-07-11
According previous post:
There is sth wrong with /usr/lib/libfreetype.la.

With this lib I've got 
```
/home/tomek/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/tomek/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/tomek/gnome-shell/install/lib64/libgdk-x11-3.0.so: undefined reference to `g_source_set_name'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'

```


without lib:

```
libtool: link: cannot find the library `/usr/lib/libfreetype.la' or unhandled argument `/usr/lib/libfreetype.la'
```

This library should be compiled with GS - and is missing...I think.

---

### Post by quickridge on 2010-07-11
> **xtoudi said:**
> According previous post:
There is sth wrong with /usr/lib/libfreetype.la.

With this lib I've got 
```
/home/tomek/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/tomek/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/tomek/gnome-shell/install/lib64/libgdk-x11-3.0.so: undefined reference to `g_source_set_name'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'

```
without lib:

```
libtool: link: cannot find the library `/usr/lib/libfreetype.la' or unhandled argument `/usr/lib/libfreetype.la'
```This library should be compiled with GS - and is missing...I think.


If you delete the gnome-shell folder and rebuild from scratch it should go away. At least it did for me.

Something like:

rm -rf ~/gnome-shell
jhbuild build

---

### Post by xtoudi on 2010-07-11
> **quickridge said:**
> If you delete the gnome-shell folder and rebuild from scratch it should go away. At least it did for me.

Something like:

rm -rf ~/gnome-shell
jhbuild build

I did it 4 times today (morning) ... ok once again ;-)

---

### Post by quickridge on 2010-07-11
I'm not sure if it does anything (updates the jhbuild thingy) but you could also do:

bash gnome-shell-build-setup.sh 

before running the build. I'm just getting this from the bugzilla listing linked above
> [http://ubuntuforums.org/showthread.php?p=9576769#post9576769](http://ubuntuforums.org/showthread.php?p=9576769#post9576769)

I did this before running the build but am not sure if it did anything.

---

### Post by ov3rcl0ck on 2010-07-11
Very sleek, but I'm an old fashion kinda linux guy(even though I'm young). I boot up into a graphical interface, where I can get most of my development work done and all, then I can start X with "startx", which loads up my openbox setup(with a sexy tint2 toolbar and custom conky script) where I can get my leisure and web browsing done(well web browsing with images).

However I'm starting to get turned off by Ubuntu itself, but I like the community, I like Debian, and I like ubuntus more cutting edge repos, since I like the latest and greatest, regardless of my old fashioness.

Just hoping Ubuntu keeps everything more Linuxy, and stops trying to copy other OS's/UIs and does its own thing. Keep the flexiblity and customization aspect of Linux in Ubuntu, but of course make it a bit easier for the new comers.

Just don't forget, Ubuntu still has advanced/power users, and its supposed to be linux for EVERYBODY, and they seem to be forgetting.

---

### Post by autocrosser on 2010-07-11
> **ov3rcl0ck said:**
> Very sleek, but I'm an old fashion kinda linux guy(even though I'm young). I boot up into a graphical interface, where I can get most of my development work done and all, then I can start X with "startx", which loads up my openbox setup(with a sexy tint2 toolbar and custom conky script) where I can get my leisure and web browsing done(well web browsing with images).

However I'm starting to get turned off by Ubuntu itself, but I like the community, I like Debian, and I like ubuntus more cutting edge repos, since I like the latest and greatest, regardless of my old fashioness.

Just hoping Ubuntu keeps everything more Linuxy, and stops trying to copy other OS's/UIs and does its own thing. Keep the flexiblity and customization aspect of Linux in Ubuntu, but of course make it a bit easier for the new comers.

Just don't forget, Ubuntu still has advanced/power users, and its supposed to be linux for EVERYBODY, and they seem to be forgetting.

Interesting point---but Gnome developers are doing this---not Ubuntu. You CAN still do things your own way in Ubuntu. Personally, I really like the way GS is going & have helped alpha & "beta" test it from the very first.

---

### Post by Merk42 on 2010-07-11
> **quickridge said:**
> I'm not sure if it does anything (updates the jhbuild thingy) but you could also do:

bash gnome-shell-build-setup.sh 

before running the build. I'm just getting this from the bugzilla listing linked above


I did this before running the build but am not sure if it did anything.

After running bash gnome-shell-build-setup.sh how do you get around the following error?
```
Please run 'sudo apt-get install libtiff-dev libpng-dev libjpeg-dev ' and try again.
```
I did that and it installs packages versions with numbers in file name, so the dependency error still comes up.

---

### Post by autocrosser on 2010-07-11
> **Merk42 said:**
> After running bash gnome-shell-build-setup.sh how do you get around the following error?
```
Please run 'sudo apt-get install libtiff-dev libpng-dev libjpeg-dev ' and try again.
```I did that and it installs packages versions with numbers in file name, so the dependency error still comes up.

Bug Report on the build script: [https://bugzilla.gnome.org/show_bug.cgi?id=624009](https://bugzilla.gnome.org/show_bug.cgi?id=624009)

If you do the patch as per info in the report, the build script works correctly.

I'm working in the newest GS right now---what a relief to have a build that works again!!!!!
Patched version of build script attached.....

---

### Post by quickridge on 2010-07-11
This dependency error came up again?
"Please run 'sudo apt-get install libtiff-dev libpng-dev libjpeg-dev ' and try again."

or are you talking about all those undefined references that occur during the build phase of gnome-shell.

If its the former than you are probably seeing some other bug with the build script for gnome-shell and should report it (verify that those packages were properly installed first). If its the latter than I would just go to that bug report that was linked to earlier and see what they have to say there.

---

### Post by x-shaney-x on 2010-07-11
> **cariboo907 said:**
> The version of mutter that Unity uses is different from the version that gnome-shell uses, so you're bound to have problems.

Yes, which is why I was inquiring about the gnome shell in the standard repos and if anyone has it working?

---

### Post by KdotJ on 2010-07-11
I have had in the past, but it's old and doesn't have a lot of the stuff the PPA has, and even less than if you compile it from source. Though right now I can't get anything to work

---

### Post by KdotJ on 2010-07-11
OK, I did a aptitude safe-upgrade and now it works...
Slow... but it works lol

---

### Post by quickridge on 2010-07-11
Is the ricotz ppa really that far behind a daily build of gnome-shell? I've been building it for myself for a while, so just curious.

---

### Post by 23dornot23d on 2010-07-11
> **KdotJ said:**
> OK, I did a aptitude safe-upgrade and now it works...
Slow... but it works lol

I found it slow going into the Desktop  ... but I also load Cairo-Dock .... which takes a little extra time ........

But once the Desktop loaded :- it was as fast as my normal Gnome Desktop .....
 
I had Blender Wings3d and (Namoroka open with 29 tabs) 
and in Blender it was as fast at rendering and moving objects about.
I have also added Gimp 2.7.2 and it compiled ok and runs well so far.

How are you judging the speed ?

( the one thing I do not like is it goes into screensaver mode and you cannot press the shift key or move the mouse to stop it )
( it fades out to a black screen and the login ....... as its fading there is nothing that you can do to stop it ...... shift - space - escape ) 

Is there a way to measure the speed - like a Benchmark test somewhere ........ ?

I will have a look around ..... but if anyone has a link to one at hand please post it .... ty

---

### Post by moore.bryan on 2010-07-12
I've been using gnome-shell for quite a while now and love it, but have begun to wonder how to *permanently* replace metacity and gnome-panel. I currently just "gnome-shell --replace" on start-up, but I want to lose gnome-panel completely. Any ideas?

---

### Post by 23meg on 2010-07-12
> **23dornot23d said:**
> 
Is there a way to measure the speed - like a Benchmark test somewhere ........ ?

[http://blog.fishsoup.net/2010/05/26/measuring-gnome-shell-performance/](http://blog.fishsoup.net/2010/05/26/measuring-gnome-shell-performance/)

---

### Post by 23dornot23d on 2010-07-12
> **23meg said:**
> [http://blog.fishsoup.net/2010/05/26/measuring-gnome-shell-performance/](http://blog.fishsoup.net/2010/05/26/measuring-gnome-shell-performance/)

Cheers - I will see if I have the right setup so that I can get this to run and give valid results.

---

### Post by Peter09 on 2010-07-12
>  			 		   		 		 		I've been using  gnome-shell for quite a while now and love it, but have begun to wonder  how to *permanently* replace metacity and gnome-panel. I currently  just "gnome-shell --replace" on start-up, but I want to lose  gnome-panel completely. Any ideas?


Not sure of the official way but in Ubuntu-Tweak the session section allows you to put gnome-shell as the window manager. Thats how I did it.

---

### Post by moore.bryan on 2010-07-12
> **Peter09 said:**
> Not sure of the official way but in Ubuntu-Tweak the session section allows you to put gnome-shell as the window manager. Thats how I did it.

AFAIK, all that does is run the "gnome-shell --replace" at startup... in essence, I already do that. I can't uninstall gnome-panel and metacity without losing, practically, everything.

Thanks, but I think I'm looking for a more permanent solution.

---

### Post by 23dornot23d on 2010-07-12
Gnome 3 now not working after the Maverick Grub2 was installed.

(will look for GRUB2 Thread as that is the problem)
Nearly everything I open now crashes too ..... [GRUB2]("http://ubuntuforums.org/showthread.php?t=1516515&page=3") or something else ?

---

### Post by xtoudi on 2010-07-12
> **23dornot23d said:**
> Gnome 3 now not working after the Maverick Grub2 was installed.

(will look for GRUB2 Thread as that is the problem)
Nearly everything I open now crashes too ..... [GRUB2]("http://ubuntuforums.org/showthread.php?t=1516515&page=3") or something else ?

This thread is about gnome-shell ... gnome-shell is only a part of Gnome3.

---

### Post by 23dornot23d on 2010-07-12
gnome shell is not working .... either .... so end of testing unless someone has some better ideas

---

### Post by xtoudi on 2010-07-12
> **23dornot23d said:**
> gnome shell is not working .... either .... so end of testing unless someone has some better ideas


My gnome-shell is working very well. If you cannot run any application than you should look out or report this in other threads. It has nothing to do with GS ... I think.

---

### Post by ioca100 on 2010-07-12
Gnome shell does not work:
-:~$ gnome-shell --replace
mutter: error while loading shared libraries: libgirepository-1.0.so.0: cannot open shared object file: No such file or directory
:~$ Cannot register the panel shell: there is already one running.

---

### Post by ronacc on 2010-07-12
I have been playing with gnome-shell for a good while now and have been trying gnome3 for the last couple of days and from a personal point of view they hold no advantages and have several annoying properties , I don't think I will like the move .

---

### Post by moore.bryan on 2010-07-13
Is anyone else using the Ricotz PPA install and getting this:
```
bryan@blue-asus:~$ gnome-shell --replace

(mutter:1850): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libgirepository-1.0.so.0: cannot open shared object file: No such file or directory)]
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```

---

### Post by munooka on 2010-07-13
I am having this crash

---

### Post by p0rkjello on 2010-07-13
Yep gnome-shell appears to be broken atm. At least via the PPA. Looks like it now has a GTK+ 3.0 dependency. :(

I really enjoyed using it. Hoping for a fix or work around.

---

### Post by cyberkilla on 2010-07-13
-- Never Mind --

---

### Post by moore.bryan on 2010-07-13
> **munooka said:**
> I am having this crash

> **p0rkjello said:**
> Yep gnome-shell appears to be broken atm. At least via the PPA. Looks like it now has a GTK+ 3.0 dependency. :(

I really enjoyed using it. Hoping for a fix or work around.

It seems we can assume it's borked for now... I just had another error last week, so it seems like things are moving forward quickly; that's nice to see!

---

### Post by youoh on 2010-07-13
```
mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libgirepository-1.0.so.0: cannot open shared object file: No such file or directory)]

```

but 

libgirepository-1.0.so.1 is installed

---

### Post by 23dornot23d on 2010-07-13
> **youoh said:**
> ```
mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libgirepository-1.0.so.0: cannot open shared object file: No such file or directory)]

```but 

libgirepository-1.0.so.1 is installed

I get this very same warning now after today's upgrades.

---

### Post by mr_hangman on 2010-07-13
I just got this error,

```
Gee-1.0.gir:3:1: error: Unsupported version '1.0'
error parsing file Gee-1.0.gir: Unsupported version '1.0'
```

I tried to install libgee2 and libgee-dev but that doesn't solve the problem.

---

### Post by tiger2wander on 2010-07-14
I've got same problem when call `gnome-shell`:
```

~]$ gnome-shell --replace
mutter: error while loading shared libraries: libgirepository-1.0.so.0: cannot open shared object file: No such file or directory

```

libgirepository1.0-0 is installed

Before upgrade after I ran `gnome-shell --replace` my desktop got some screwed menu, text on top right and window manager has been freeze, can not kill mutter process even with SIGKILL and root privilege :(

---

### Post by davideotape on 2010-07-15
Trying to do a completely clean rebuild, and getting this:

```
$ sudo apt-get install libtiff-dev libpng-dev libjpeg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libtiff4-dev instead of libtiff-dev
libtiff4-dev is already the newest version.
Note, selecting libpng12-dev instead of libpng-dev
libpng12-dev is already the newest version.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

dstansby@dstansby-desktop:~/Shell$ /bin/bash gnome-shell-build-setup.sh 
Please run 'sudo apt-get install libtiff-dev libpng-dev libjpeg-dev ' and try again.

```

Any ideas what I'm doing wrong?

EDIT: I think I've found the problem. I have libtiff4-dev, libpng12-dev and libjpeg62-dev installed (note the numbers) How can I get around this?

---

### Post by SevenMachines on 2010-07-15
> **davideotape said:**
> Trying to do a completely clean rebuild, and getting this:

```
$ sudo apt-get install libtiff-dev libpng-dev libjpeg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libtiff4-dev instead of libtiff-dev
libtiff4-dev is already the newest version.
Note, selecting libpng12-dev instead of libpng-dev
libpng12-dev is already the newest version.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

dstansby@dstansby-desktop:~/Shell$ /bin/bash gnome-shell-build-setup.sh 
Please run 'sudo apt-get install libtiff-dev libpng-dev libjpeg-dev ' and try again.

```Any ideas what I'm doing wrong?

EDIT: I think I've found the problem. I have libtiff4-dev, libpng12-dev and libjpeg62-dev installed (note the numbers) How can I get around this?
i think someone mentioned another fix for this earlier in the thread, i just edited the script (well sed'd it :) ) to replace 
libtiff-dev with libtiff4-dev and the other 2 as well in the script

$sed -i 's/libtiff-dev/libtiff4-dev/g' gnome-shell-build-setup.sh
$sed -i 's/libjpeg-dev/libjpeg62-dev/g' gnome-shell-build-setup.sh
$sed -i 's/libpng-dev/libpng12-dev/g' gnome-shell-build-setup.sh

---

### Post by autocrosser on 2010-07-15
> **davideotape said:**
> Trying to do a completely clean rebuild, and getting this:

```
$ sudo apt-get install libtiff-dev libpng-dev libjpeg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libtiff4-dev instead of libtiff-dev
libtiff4-dev is already the newest version.
Note, selecting libpng12-dev instead of libpng-dev
libpng12-dev is already the newest version.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

dstansby@dstansby-desktop:~/Shell$ /bin/bash gnome-shell-build-setup.sh 
Please run 'sudo apt-get install libtiff-dev libpng-dev libjpeg-dev ' and try again.

```Any ideas what I'm doing wrong?

EDIT: I think I've found the problem. I have libtiff4-dev, libpng12-dev and libjpeg62-dev installed (note the numbers) How can I get around this?


Look at my posts from the last couple of days---I posted a patched gnome-shell-build-setup.sh that gets around the issue--bear in mind that building has many problems right now---look at prior posts....

---

### Post by ricotz on 2010-07-15
When you are using the ppa:ricotz/testing ppa:

There are quite some issues with the latest updates. It is the best to use ppa-purge to revert to the default distribution packages.
sudo apt-get install ppa-purge
sudo ppa-purge -p testing ricotz

Please do this as soon as possible!

---

### Post by ioca100 on 2010-07-15
Thank you , I did it and  it is all right now.

---

### Post by moore.bryan on 2010-07-15
> **ricotz said:**
> When you are using the ppa:ricotz/testing ppa:

There are quite some issues with the latest updates. It is the best to use ppa-purge to revert to the default distribution packages.
sudo apt-get install ppa-purge
sudo ppa-purge -p testing ricotz

Please do this as soon as possible!

Any ETA on getting things back-up to "amazing?"
:-)

---

### Post by autocrosser on 2010-07-16
As far as building from source--all works again---so I would guess that the PPA will catch up in a couple of days........

---

### Post by dino99 on 2010-07-16
> **ricotz said:**
> When you are using the ppa:ricotz/testing ppa:

There are quite some issues with the latest updates. It is the best to use ppa-purge to revert to the default distribution packages.
sudo apt-get install ppa-purge
sudo ppa-purge -p testing ricotz

Please do this as soon as possible!

got these warnings when purging:

WARNING: WARNING: /usr/share/pyshared/httplib2-0.6.0.egg-info is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/httplib2/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/httplib2/iri2uri.py is linked but does not belong to any package.

---

### Post by cresny on 2010-07-16
> **mr_hangman said:**
> I just got this error,

```
Gee-1.0.gir:3:1: error: Unsupported version '1.0'
error parsing file Gee-1.0.gir: Unsupported version '1.0'
```

I tried to install libgee2 and libgee-dev but that doesn't solve the problem.

I still cannot do a clean build without this error. Any ideas?

---

### Post by mr_hangman on 2010-07-16
> **cresny said:**
> I still cannot do a clean build without this error. Any ideas?

I got through that by choosing option no.6, 
[6] Go to phase "wipe directory and start over".

It didn't work a couple days ago. I think they just fixed this problem yesterday.

---

### Post by cariboo on 2010-07-16
> **dino99 said:**
> got these warnings when purging:

WARNING: WARNING: /usr/share/pyshared/httplib2-0.6.0.egg-info is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/httplib2/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/httplib2/iri2uri.py is linked but does not belong to any package.


I saw the same message after updating last night, so I'm not sure if it has anything to do with gnome-shell.

---

### Post by ranch hand on 2010-07-16
> **cariboo907 said:**
> I saw the same message after updating last night, so I'm not sure if it has anything to do with gnome-shell.
It does not.  I do not have GS on any install currently but have that warning on most.

---

### Post by davideotape on 2010-07-16
Gnome-shell still looks rubbish, and is totally unusable on my system. Any light shed on the matter would be welcome

```
dstansby@dstansby-desktop:~$ cd gnome-shell/source/gnome-shell/src/
dstansby@dstansby-desktop:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Starting dconf-service...  started
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
      JS LOG: GNOME Shell started at Fri Jul 16 2010 18:01:53 GMT+0100 (BST)

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
^CShell killed with signal 2

```

---

### Post by autocrosser on 2010-07-16
> **davideotape said:**
> Gnome-shell still looks rubbish, and is totally unusable on my system. Any light shed on the matter would be welcome

```
dstansby@dstansby-desktop:~$ cd gnome-shell/source/gnome-shell/src/
dstansby@dstansby-desktop:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Starting dconf-service...  started
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
      JS LOG: GNOME Shell started at Fri Jul 16 2010 18:01:53 GMT+0100 (BST)

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:14018): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:14018): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
^CShell killed with signal 2

```

Have you tried a complete clean & rebuild?  The sources were cleaned up last nite, so things "might" look better today.......

---

### Post by Merk42 on 2010-07-16
> **autocrosser said:**
> Have you tried a complete clean & rebuild?  The sources were cleaned up last nite, so things "might" look better today.......Keep in mind a complete clean and rebuild will still cause the following problem:```
Please run 'sudo apt-get install libtiff-dev libpng-dev libjpeg-dev ' and try again.
```

Easily remedied by the custom gnome-build-setup.sh mentioned by autoscrosser on [Page 32](http://ubuntuforums.org/showthread.php?t=1476241&page=32)

EDIT:
Now I'm getting errors regarding libgio-2.0.so

---

### Post by p0rkjello on 2010-07-16
Anyone know how to get around the following error? Ubuntu 10.04 

```
*** Building libgee *** [17/21]
make  
make  all-recursive
make[1]: Entering directory `/home/abounds/gnome-shell/source/libgee'
Making all in gee
make[2]: Entering directory `/home/abounds/gnome-shell/source/libgee/gee'
make  all-am
make[3]: Entering directory `/home/abounds/gnome-shell/source/libgee/gee'
/home/abounds/gnome-shell/install/bin/g-ir-compiler --shared-library=libgee -o Gee-1.0.typelib Gee-1.0.gir
Gee-1.0.gir:3:1: error: Unsupported version '1.0'
error parsing file Gee-1.0.gir: Unsupported version '1.0'
make[3]: *** [Gee-1.0.typelib] Error 1
make[3]: Leaving directory `/home/abounds/gnome-shell/source/libgee/gee'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/abounds/gnome-shell/source/libgee/gee'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/abounds/gnome-shell/source/libgee'
make: *** [all] Error 2
*** Error during phase build of libgee: ########## Error running make   *** [17/21]

```

---

### Post by davideotape on 2010-07-17
> **p0rkjello said:**
> Anyone know how to get around the following error? Ubuntu 10.04 

```
*** Building libgee *** [17/21]
make  
make  all-recursive
make[1]: Entering directory `/home/abounds/gnome-shell/source/libgee'
Making all in gee
make[2]: Entering directory `/home/abounds/gnome-shell/source/libgee/gee'
make  all-am
make[3]: Entering directory `/home/abounds/gnome-shell/source/libgee/gee'
/home/abounds/gnome-shell/install/bin/g-ir-compiler --shared-library=libgee -o Gee-1.0.typelib Gee-1.0.gir
Gee-1.0.gir:3:1: error: Unsupported version '1.0'
error parsing file Gee-1.0.gir: Unsupported version '1.0'
make[3]: *** [Gee-1.0.typelib] Error 1
make[3]: Leaving directory `/home/abounds/gnome-shell/source/libgee/gee'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/abounds/gnome-shell/source/libgee/gee'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/abounds/gnome-shell/source/libgee'
make: *** [all] Error 2
*** Error during phase build of libgee: ########## Error running make   *** [17/21]

```

[http://ubuntuforums.org/showpost.php?p=9597356&postcount=356](http://ubuntuforums.org/showpost.php?p=9597356&postcount=356)

And I've just done a completely clean build. Gnome-shell hasn't been working for me at all for the last few months.

---

### Post by autocrosser on 2010-07-17
> **davideotape said:**
> [http://ubuntuforums.org/showpost.php?p=9597356&postcount=356](http://ubuntuforums.org/showpost.php?p=9597356&postcount=356)

And I've just done a completely clean build. Gnome-shell hasn't been working for me at all for the last few months.

Could you give me some output---I've got a clean build that is working fine here.....

---

### Post by davideotape on 2010-07-17
Here's my latest output after doing a jhbuild build -f -a -c:

```
dstansby@dstansby-desktop:~$ cd gnome-shell/source/gnome-shell/src/
dstansby@dstansby-desktop:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Starting dconf-service...  started
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
      JS LOG: GNOME Shell started at Sat Jul 17 2010 15:14:06 GMT+0100 (BST)

(mutter:2798): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:2798): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:2798): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:2798): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:2798): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:2798): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:2798): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:2798): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:2798): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:2798): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:2798): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:2798): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:2798): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:2798): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:2798): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed

(mutter:2798): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:2798): Cogl-glx-WARNING **: ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

(mutter:2798): St-CRITICAL **: setup_framebuffers: assertion `priv->old_offscreen != COGL_INVALID_HANDLE' failed

(mutter:2798): Cogl-glx-CRITICAL **: cogl_material_set_layer_combine_constant: assertion `cogl_is_material (handle)' failed

(mutter:2798): Cogl-glx-CRITICAL **: cogl_set_source: assertion `cogl_is_material (material_handle)' failed
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
^CShell killed with signal 2

```

---

### Post by gotjazz on 2010-07-17
hrm I keep getting ```
/home/peter/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/peter/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/peter/gnome-shell/install/lib/libgdk-x11-3.0.so: undefined reference to `g_source_set_name'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status

```any news on that one?

---

### Post by mr_hangman on 2010-07-17
> **gotjazz said:**
> hrm I keep getting ```
/home/peter/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/peter/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/peter/gnome-shell/install/lib/libgdk-x11-3.0.so: undefined reference to `g_source_set_name'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status

```any news on that one?

I followed the instruction mentioned in this thread few days ago - [http://ubuntuforums.org/showpost.php...&postcount=311](http://ubuntuforums.org/showpost.php...&postcount=311) - removing all *.la files in /usr/lib/.
I did it by moving them to another folder.

```
cd /usr/lib/
sudo mkdir la_files
sudo mv *.la la_files/
```

Not sure if this will effect other applications but so far I have no problem at all.

---

### Post by p0rkjello on 2010-07-17
I have gotten past the libgee error (thanks davidiotape) and moved on to the next error..

```
  CCLD   test-theme
/home/abounds/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/abounds/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/abounds/gnome-shell/install/lib/libgdk-x11-3.0.so: undefined reference to `g_source_set_name'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/abounds/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/abounds/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/abounds/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/abounds/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [20/21]

```


Guess I should have refreshed the page.. before posting :P

---

### Post by SevenMachines on 2010-07-17
> **gotjazz said:**
> hrm I keep getting ```
/home/peter/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/peter/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/peter/gnome-shell/install/lib/libgdk-x11-3.0.so: undefined reference to `g_source_set_name'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status

```any news on that one?

Means that the makefiles are missing glib-2.0 libs being passed to the linker, you could hack them manually but it would take a *long* time :(
Are you using binutils-gold? that will fail on this, if you are then use straight binutils instead.

---

### Post by SevenMachines on 2010-07-17
> **mr_hangman said:**
> I followed the instruction mentioned in this thread few days ago - [http://ubuntuforums.org/showpost.php...&postcount=311](http://ubuntuforums.org/showpost.php...&postcount=311) - removing all *.la files in /usr/lib/.
I did it by moving them to another folder.

```
cd /usr/lib/
sudo mkdir la_files
sudo mv *.la la_files/
```Not sure if this will effect other applications but so far I have no problem at all.

I wouldnt recommend that, not at all :) those are your libtool libraries, you might need them sometime:) In general, dont fiddle in the system directories!

---

### Post by p0rkjello on 2010-07-17
> **mr_hangman said:**
> I followed the instruction mentioned in this thread few days ago - [http://ubuntuforums.org/showpost.php...&postcount=311](http://ubuntuforums.org/showpost.php...&postcount=311) - removing all *.la files in /usr/lib/.
I did it by moving them to another folder.

```
cd /usr/lib/
sudo mkdir la_files
sudo mv *.la la_files/
```

Not sure if this will effect other applications but so far I have no problem at all.

I was able to get everything compiled. Had to delete the gnome-shell directory and start over. Moved the /usr/lib/*.la file to a temp location then returned them after the build. Thanks

---

### Post by autocrosser on 2010-07-17
> **gotjazz said:**
> hrm I keep getting ```
/home/peter/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/peter/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/peter/gnome-shell/install/lib/libgdk-x11-3.0.so: undefined reference to `g_source_set_name'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/peter/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status

```any news on that one?


That needs the script I posted a couple of pages ago & a clean (remove everything in ~/gnome-shell) rebuild.......

*****davidiotape---what video driver are you using?*****

*****p0rkjello---looks good--I had forgot about the .la files---davidiotape & gotjazz---move the .la files in /usr/lib to a "safe" backup---I posted that stuff about a week ago*****

---

### Post by Merk42 on 2010-07-17
> **autocrosser said:**
> That needs the script I posted a couple of pages ago & a clean (remove everything in ~/gnome-shell) rebuild.......

*****davidiotape---what video driver are you using?*****

*****p0rkjello---looks good--I had forgot about the .la files---davidiotape & gotjazz---move the .la files in /usr/lib to a "safe" backup---I posted that stuff about a week ago*****

I used that script, deleted my ~/gnome-shell folder and STILL got those errors

---

### Post by autocrosser on 2010-07-17
Hmmmm---  I've deleted the ~/gnome-shell folder, .jhbuildrc, .jhbuildrc-custom & the gnome-shell-build-setup.sh script several times in the last week or so---I no longer get the errors. Not sure what "really" cleared it all.....but I get a clean build every time now.

If you have not deleted .jhbuildrc & jhbuildrc-custom lately---that would be a very good idea---they will be rebuilt with the custom gnome-shell-build-setup script.

---

### Post by Merk42 on 2010-07-17
> **autocrosser said:**
> Hmmmm---  I've deleted the ~/gnome-shell folder, .jhbuildrc, .jhbuildrc-custom & the gnome-shell-build-setup.sh script several times in the last week or so---I no longer get the errors. Not sure what "really" cleared it all.....but I get a clean build every time now.

If you have not deleted .jhbuildrc & jhbuildrc-custom lately---that would be a very good idea---they will be rebuilt with the custom gnome-shell-build-setup script.

Deleted, and subsequently reinstalled, jhbuild.

Now when running /bin/bash gnome-shell-build-setup.sh (with the patched file), I get the following:
```
Updating jhbuild ... refusing to pull with rebase: your working tree is not up-to-date
```
Attempting to then run jhbuild build:
```
Traceback (most recent call last):
  File "/home/merk/Source/jhbuild/jhbuild/config.py", line 181, in __init__
    execfile(_defaults_file, self._config)
IOError: [Errno 2] No such file or directory: '/home/merk/Source/jhbuild/jhbuild/defaults.jhbuildrc'
jhbuild: could not load config defaults
```

---

### Post by autocrosser on 2010-07-17
Not sure what is going on with that---I'm including the 3 files that I'm using--i can confirm that they work on my system......

---

### Post by Merk42 on 2010-07-17
> **autocrosser said:**
> Not sure what is going on with that---I'm including the 3 files that I'm using--i can confirm that they work on my system......

Where do those files go?

---

### Post by autocrosser on 2010-07-17
> **Merk42 said:**
> Where do those files go?

The .rc & .rc-custom are just in your /home---look at the bottom in the .dot files.....

---

### Post by Merk42 on 2010-07-17
> **autocrosser said:**
> The .rc & .rc-custom are just in your /home---look at the bottom in the .dot files.....

Oh.. looks like I forgot to delete ~/source/jhbuild
It builds again, but still getting the libgio and libgtk3 errors

---

### Post by autocrosser on 2010-07-17
> **Merk42 said:**
> Oh.. looks like I forgot to delete ~/source/jhbuild
It builds again, but still getting the libgio and libgtk3 errors

Looks like we need to include a mini-tutorial on what "should" be deleted to get a clean build---I had forgot the ~/sorce/jhbuild :oops:

---

### Post by Merk42 on 2010-07-17
> **autocrosser said:**
> Looks like we need to include a mini-tutorial on what "should" be deleted to get a clean build---I had forgot the ~/sorce/jhbuild :oops:

I plan on updating the OP about it, but given in my case, it still doesn't correctly build, I haven't added it yet.

---

### Post by davideotape on 2010-07-18
I'm using the open source Noveau driver with a GeForce 9400M

---

### Post by autocrosser on 2010-07-18
> **davideotape said:**
> I'm using the open source Noveau driver with a GeForce 9400M


Ah!!!  That explains this error:   (mutter:2798): Cogl-glx-WARNING **:  ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

You do not seem to be using a video driver that supports acceleration. You would need to use the Gallum experimental 3D for Noveau or use the closed-source Nvidia driver.....

Here for the Gallum 3D:  [http://ubuntuforums.org/showthread.php?t=1531554](http://ubuntuforums.org/showthread.php?t=1531554)

---

### Post by dext on 2010-07-18
> **autocrosser said:**
> Ah!!!  That explains this error:   (mutter:2798): Cogl-glx-WARNING **:  ./cogl-framebuffer.c:424: Failed to create an OpenGL framebuffer

You do not seem to be using a video driver that supports acceleration. You would need to use the Gallum experimental 3D for Noveau or use the closed-source Nvidia driver.....

Here for the Gallum 3D:  [http://ubuntuforums.org/showthread.php?t=1531554](http://ubuntuforums.org/showthread.php?t=1531554)

the latest stable 256 Nvidia driver doesnt support the 2.6.35 kernel from what i know of

---

### Post by autocrosser on 2010-07-18
> **dext said:**
> the latest stable 256 Nvidia driver doesnt support the 2.6.35 kernel from what i know of

I'm using the latest Nvidia driver with the 2.6.35.8 kernel....working just fine here.

---

### Post by dext on 2010-07-18
> **autocrosser said:**
> I'm using the latest Nvidia driver with the 2.6.35.8 kernel....working just fine here.

i forgot Ubuntu is using 1.8.x still, so yeah it would work, Fedora it doesnt work with the newer X-Server-1.9

---

### Post by gotjazz on 2010-07-18
hrm I just finished my first successful build. 
Is it me or does the rather old version the official ubuntu repos perform much faster than an up-to-date build?

---

### Post by autocrosser on 2010-07-18
> **dext said:**
> i forgot Ubuntu is using 1.8.x still, so yeah it would work, Fedora it doesnt work with the newer X-Server-1.9

Yes---I'm waiting for xorg-edgers to get sorted out & then I'll re-enable the PPA again...

---

### Post by autocrosser on 2010-07-18
> **gotjazz said:**
> hrm I just finished my first successful build. 
Is it me or does the rather old version the official ubuntu repos perform much faster than an up-to-date build?

Lower requirements for the older build (from repo)--gtk3 & the new mutter/clutter need more to work correctly...

---

### Post by Tompalaz on 2010-07-19
I have a problem on installing stage 3

tomas@MacBook:~$ /bin/bash gnome-shell-build-setup.sh 
Please run 'sudo apt-get install libtiff-dev libpng-dev libjpeg-dev ' and try again.

I've already installed those packages.

running updated maveric

edit: nevermind, found the patch [http://ubuntuforums.org/showthread.php?p=9576769#post9576769](http://ubuntuforums.org/showthread.php?p=9576769#post9576769)
thanks autocrosser!

edit2: Havn't tried GS for a while, must say, it's been very much improved since I tried it last time, about 2 months ago. However, it's still a bit laggish.
Using the nVidia 256.31 driver.

---

### Post by davideotape on 2010-07-19
Here's how I've got on since my last post:

I don't want to install the closed source driver, because the boot splash looks 'orrible and I'd lose brightness control

So, I've installed libgl1-mesa-dri-experimental as recommended here: [http://ubuntuforums.org/showpost.php?p=9595229&postcount=5](http://ubuntuforums.org/showpost.php?p=9595229&postcount=5)

Restarted, build gnome-shell and it now works :D Thanks to all that helped



EDIT: My buttons have moved back to the right when running gnome-shell :(

---

### Post by autocrosser on 2010-07-19
> **davideotape said:**
> Here's how I've got on since my last post:

I don't want to install the closed source driver, because the boot splash looks 'orrible and I'd lose brightness control

So, I've installed libgl1-mesa-dri-experimental as recommended here: [http://ubuntuforums.org/showpost.php?p=9595229&postcount=5](http://ubuntuforums.org/showpost.php?p=9595229&postcount=5)

Restarted, build gnome-shell and it now works :D Thanks to all that helped



EDIT: My buttons have moved back to the right when running gnome-shell :(

Hmmm--try changing your theme or use the gconf way to put the buttons back....glad to see that you've got GS working---have fun!!

---

### Post by Mblackwell on 2010-07-19
Ricotz PPA version works again. Loverly.

---

### Post by symon1980 on 2010-07-19
yeah, I noticed the fix last nite. Sweeeeet.

Although.. there is still no visible changes/features added to the current gnome-shell.... lol
When the hell is there gonna be features added to gnome-shell??? its been developing at a crawl it seems and final release is due in merely a few weeks.... arghhhhhhh! nooooooooo Pleaseeeeee Don't let the final release be THIS thing! Lol :p

---

### Post by Merk42 on 2010-07-20
> **symon1980 said:**
> yeah, I noticed the fix last nite. Sweeeeet.

Although.. there is still no visible changes/features added to the current gnome-shell.... lol
When the hell is there gonna be features added to gnome-shell??? its been developing at a crawl it seems and final release is due in merely a few weeks.... arghhhhhhh! nooooooooo Pleaseeeeee Don't let the final release be THIS thing! Lol :pWhat sort of features were you expecting?

---

### Post by gotjazz on 2010-07-20
well a more organized way of browsing applications is something one would expect before the final release. 
Also while a taskbar seems to be out of the question SOME  graphical way of changing between open windows on one workplace without leaving it or alt+tabbing would seem like a must-have....
but maybe that's just my old-fashionedness ;)

edit: oh and a tool to at least marginally configure and/or theme the whole thing.

---

### Post by mr_hangman on 2010-07-20
What I really want to see in GS is the ability to drag and drop files. 
At the moment I cannot drag a file from one maximized window to another one. 
This feature is very useful for music player, copying files or sending files via IM (also attaching files in gmail with chrome :)).

---

### Post by davideotape on 2010-07-20
Hmm, getting a new error when I try to build now:

```
dconfsettingsbackend.c: In function ‘dconf_settings_backend_send’:
dconfsettingsbackend.c:387: error: incompatible type for argument 3 of ‘g_dbus_connection_send_message’
/home/dstansby/gnome-shell/install/include/glib-2.0/gio/gdbusconnection.h:125: note: expected ‘GDBusSendMessageFlags’ but argument is of type ‘volatile guint32 *’
dconfsettingsbackend.c:387: error: too few arguments to function ‘g_dbus_connection_send_message’
cc1: warnings being treated as errors
dconfsettingsbackend.c:390: error: passing argument 4 of ‘g_dbus_connection_send_message_with_reply_sync’ makes integer from pointer without a cast
/home/dstansby/gnome-shell/install/include/glib-2.0/gio/gdbusconnection.h:141: note: expected ‘gint’ but argument is of type ‘void *’
dconfsettingsbackend.c:390: error: too few arguments to function ‘g_dbus_connection_send_message_with_reply_sync’
make[1]: *** [dconfsettingsbackend.lo] Error 1
make[1]: Leaving directory `/home/dstansby/gnome-shell/source/dconf/gsettings'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/21]

```

---

### Post by mr_hangman on 2010-07-20
I got this error during step 1/21.

```
./.libs/libgio-2.0.so: undefined reference to `WIFEXITED'
./.libs/libgio-2.0.so: undefined reference to `WEXITSTATUS'
```

Any idea?

---

### Post by moore.bryan on 2010-07-20
Any reason why the status icon is still missing by the name?

---

### Post by symon1980 on 2010-07-20
> **Merk42 said:**
> What sort of features were you expecting?

I have created blueprints and a video of what I think makes sense to add to gnome-shell to make it more useable....

[http://www.youtube.com/watch?v=T8HWhln3IMo](http://www.youtube.com/watch?v=T8HWhln3IMo)

---

### Post by NightwishFan on 2010-07-20
No offense, and I am sure they thank you for the input, but at this stage I think they are looking for real code and not mockups.

---

### Post by rayraven on 2010-07-20
It's probably something very simple, but for the life of me i cant figure out how to get rid of the notifications? 

Like for example, i get a notification when i connect to the wifi, but it just stays in the tray at the bottom. Is this how it's supposed to be?

---

### Post by mr_hangman on 2010-07-20
> **rayraven said:**
> It's probably something very simple, but for the life of me i cant figure out how to get rid of the notifications? 

Like for example, i get a notification when i connect to the wifi, but it just stays in the tray at the bottom. Is this how it's supposed to be?

If I understand it right, you have to hover the mouse over it. When a small extended part pops up, click the icon in front of the title.

This is one of those things that kinda bug me. Everytime I have to aim for this small icon. Even when there is no icon I still have to click the empty space in the front. 
I hope there will be some improvements for this :).

---

### Post by rayraven on 2010-07-20
> **mr_hangman said:**
> If I understand it right, you have to hover the mouse over it. When a small extended part pops up, click the icon in front of the title.

This is one of those things that kinda bug me. Everytime I have to aim for this small icon. Even when there is no icon I still have to click the empty space in the front. 
I hope there will be some improvements for this :).

Thanks! That got rid of those notifications.

You are right though, this does need more improvement.

---

### Post by mr_hangman on 2010-07-20
> **davideotape said:**
> Hmm, getting a new error when I try to build now:

```
dconfsettingsbackend.c: In function ‘dconf_settings_backend_send’:
dconfsettingsbackend.c:387: error: incompatible type for argument 3 of ‘g_dbus_connection_send_message’
/home/dstansby/gnome-shell/install/include/glib-2.0/gio/gdbusconnection.h:125: note: expected ‘GDBusSendMessageFlags’ but argument is of type ‘volatile guint32 *’
dconfsettingsbackend.c:387: error: too few arguments to function ‘g_dbus_connection_send_message’
cc1: warnings being treated as errors
dconfsettingsbackend.c:390: error: passing argument 4 of ‘g_dbus_connection_send_message_with_reply_sync’ makes integer from pointer without a cast
/home/dstansby/gnome-shell/install/include/glib-2.0/gio/gdbusconnection.h:141: note: expected ‘gint’ but argument is of type ‘void *’
dconfsettingsbackend.c:390: error: too few arguments to function ‘g_dbus_connection_send_message_with_reply_sync’
make[1]: *** [dconfsettingsbackend.lo] Error 1
make[1]: Leaving directory `/home/dstansby/gnome-shell/source/dconf/gsettings'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/21]

```

I'm having the same problem with the new commit. Any workaround yet?

---

### Post by Merk42 on 2010-07-20
> **NightwishFan said:**
> No offense, and I am sure they thank you for the input, but at this stage I think they are looking for real code and not mockups.
(paraphrased for comedic effect)
*EARLY IN THE DEV CYCLE*
"Thank you for your input, but we're hard at work implementing what we mocked up, so wait until after we'd added those features before giving input"

*LATER IN THE DEV CYCLE*
"Thank you for your input, but we're hard at work fixing bugs with what we implemented and since we've invested so much, we're not going to implement any new ideas at this stage, it would have been better to give your input earlier"

---

### Post by NightwishFan on 2010-07-20
Exactly. ;)

Well no, but as they say code speaks.

---

### Post by hrhnick on 2010-07-20
the nvidia restricted drivers never liked gnome shell for me, to choppy to be usable.

i recently switched to the libgl1-mesa-dri-experimental and now its super smooth! only issue is that my desktop wallpaper "bleeds" through my window.

any ideas?
using the ppa.

---

### Post by lesnoland on 2010-07-21
You need to:

```

cd gnome-shell/install/lib
rm -rf *.la
jhbuild buildone gnome-shell -acf

```

This fixed it two times for me. No need to touch /usr/lib,or erase the whole dir.

> **xtoudi said:**
> According previous post:
There is sth wrong with /usr/lib/libfreetype.la.

With this lib I've got 
```
/home/tomek/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/tomek/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/tomek/gnome-shell/install/lib64/libgdk-x11-3.0.so: undefined reference to `g_source_set_name'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/tomek/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'

```


without lib:

```
libtool: link: cannot find the library `/usr/lib/libfreetype.la' or unhandled argument `/usr/lib/libfreetype.la'
```

This library should be compiled with GS - and is missing...I think.

---

### Post by Tompalaz on 2010-07-21
> **hrhnick said:**
> the nvidia restricted drivers never liked gnome shell for me, to choppy to be usable.

i recently switched to the libgl1-mesa-dri-experimental and now its super smooth! only issue is that my desktop wallpaper "bleeds" through my window.

any ideas?
using the ppa.

Same problem here. Been like this for a couple of months now.
It's just parts of the window/windows that's "transparent".

GS is much faster using the nouveau, to bad we cant use gs with nouveau...

---

### Post by hrhnick on 2010-07-21
> **Tompalaz said:**
> Same problem here. Been like this for a couple of months now.
It's just parts of the window/windows that's "transparent".

GS is much faster using the nouveau, to bad we cant use gs with nouveau...

my windows only look normal when maximized, and my terminal for some reason. pita.

---

### Post by autocrosser on 2010-07-21
I guess that I'm one of the few that is not having a problem with GS & the Nvidia drivers----but I am using a SLI setup with two 9500GT DDR3 1024mb cards---so it looks like the requirement for nvidia with GS to run smooth is running SLI......

---

### Post by davideotape on 2010-07-22
Running smooth but getting that horrible bleed through effect - 

[IMG]http://web16.twitpic.com/img/133689863-254868755c5d6eb5c56bd978f6ac4bdc.4c4863f8-scaled.png[/IMG]

---

### Post by Tompalaz on 2010-07-22
Anyone filed a bug on that one?

---

### Post by davideotape on 2010-07-22
> **Tompalaz said:**
> Anyone filed a bug on that one?

I would have done if I knew where to file bugs for gnome-shell :(

---

### Post by 23meg on 2010-07-22
> **davideotape said:**
> I would have done if I knew where to file bugs for gnome-shell :(

Report them in the gnome-shell product at [https://bugzilla.gnome.org](https://bugzilla.gnome.org).

---

### Post by davideotape on 2010-07-22
Cheers, reported [https://bugzilla.gnome.org/show_bug.cgi?id=625044](https://bugzilla.gnome.org/show_bug.cgi?id=625044)

---

### Post by Mblackwell on 2010-07-22
> **hrhnick said:**
> the nvidia restricted drivers never liked gnome shell for me, to choppy to be usable.

i recently switched to the libgl1-mesa-dri-experimental and now its super smooth! only issue is that my desktop wallpaper "bleeds" through my window.

any ideas?
using the ppa.

Note that the restricted drivers will be sped up once xorg 1.9 has a rollout. There was a bug of sorts that slowed things down because of the way gnome-shell works. In the meantime to improve performance with the NVIDIA binaries open /usr/share/gnome-shell/js/ui/chrome.js and find the following:

```

queueUpdateRegions: function() {
        if (!this._updateRegionIdle)
            this._updateRegionIdle = Mainloop.idle_add(Lang.bind(this, this._updateRegions),
                                                       Meta.PRIORITY_BEFORE_REDRAW);
},

```

and change **Meta.PRIORITY_BEFORE_REDRAW** to **500**, like so:

```

queueUpdateRegions: function() {
        if (!this._updateRegionIdle)
            this._updateRegionIdle = Mainloop.idle_add(Lang.bind(this, this._updateRegions),
                                                       500);
},

```

You'll see a MASSIVE performance increase across the board.

---

### Post by autocrosser on 2010-07-23
Thank You---that did speed up my setup---not MASSIVE, but a notable improvement!!!!

---

### Post by mr_hangman on 2010-07-23
I couldn't find that file in the place you mentioned. Maybe because I compile from source.
So, I changed it in ~/gnome-shell/source/gnome-shell/js/ui/chrome.js and wow! it really speeds up GS.
Thanks for the tip.

---

### Post by hrhnick on 2010-07-23
so after having issues, i clean installed, enabled the nonfree nvidia drivers,
and now, shell fails to start, ppa version.



```
hrhnick@desktop:~$ gnome-shell --replace
**
ERROR:girffi.c:85:_gi_type_tag_get_ffi_type: code should not be reached
Shell killed with signal 6
hrhnick@desktop:~$ 
(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Unable to open desktop file firefox.desktop for panel launcher

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:22291): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:22291): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

---

### Post by kaitwospirit on 2010-07-23
I have that issue too. I think I noticed one of the files used in the ppa updated through the main repos, and my suspicion is that's what broke it. I'm going to do some testing and I'll be back if that's what it was.

ETA: Nope, I was wrong I guess. Not sure what caused the problem then.

---

### Post by hrhnick on 2010-07-23
> **kaitwospirit said:**
> I have that issue too. I think I noticed one of the files used in the ppa updated through the main repos, and my suspicion is that's what broke it. I'm going to do some testing and I'll be back if that's what it was.

i tried ppapurging and it didnt help :-(

---

### Post by autocrosser on 2010-07-24
Try purging the PPA & build it from source---there are quite a few things that are in flux right now & you will have the git versions with a build---

---

### Post by Kasiraman on 2010-07-24
> **mr_hangman said:**
> I'm having the same problem with the new commit. Any workaround yet?

I had a similar problem in this stage as well.

I had to Copy the libdconf.so.0 file from /home/*username*/gnome-shell/source/dconf/client to /home/*username*/gnome-shell/install/lib and then rerun the build, it fixed the problem

---

### Post by mixint27 on 2010-07-25
I really want to try gnome shell but i get this error:

checking for DEPENDENT... configure: error: Package requirements (glib-2.0 > 2.14.0 gthread-2.0 gmodule-2.0 >= 2.7.0 gobject-2.0 >= 2.7.0 ORBit-2.0 >= 2.4.0 dbus-1 >= 1.0.0 dbus-glib-1 >= 0.74 gio-2.0 >= 2.25.9) were not met:

No package 'ORBit-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPENDENT_CFLAGS
and DEPENDENT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

*** Error during phase configure of gconf: ########## Error running ./autogen.sh --prefix /home/tony/gnome-shell/install --libdir '/home/tony/gnome-shell/install/lib' --disable-defaults-service --disable-static --disable-gtk-doc  *** [13/21]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
------

Please help me out...

thank you!

---

### Post by gotjazz on 2010-07-25
hrm I'm thinking of rebuilding from scratch later today - is moving around all the *.la files still necessary?

---

### Post by autocrosser on 2010-07-25
gotjazz---I haven't done that for a week or so now---give it a try.....

mixint27---you need the development versions of those to build...

---

### Post by Merk42 on 2010-07-25
> **Kasiraman said:**
> I had a similar problem in this stage as well.

I had to Copy the libdconf.so.0 file from /home/*username*/gnome-shell/source/dconf/client to /home/*username*/gnome-shell/install/lib and then rerun the build, it fixed the problem

Still got the error when I tried that.

I hope there haven't been any major GUI changes to GNOME Shell recently. I can't update the images since I haven't been able to successfully build for some time.

---

### Post by gotjazz on 2010-07-25
> **Merk42 said:**
> Still got the error when I tried that.

I hope there haven't been any major GUI changes to GNOME Shell recently. I can't update the images since I haven't been able to successfully build for some time.

hrm for me that did the trick - but at step 21 (gnome-shell itself) libfreetype.la is making trouble again. with it i get the old undefinded references problem and without it it complains about it not being there.

Moving *.la files is not a good idea anymore anyway as this step seems to really need them now.

---

### Post by autocrosser on 2010-07-25
> **Merk42 said:**
> Still got the error when I tried that.

I hope there haven't been any major GUI changes to GNOME Shell recently. I can't update the images since I haven't been able to successfully build for some time.

It's all looking the same to me--just all the under the hood changes...

---

### Post by Peter09 on 2010-07-25
Since the latest updates of Gnome-Shell I am getting no Recent-Items displayed. I have looked in .recently-used.xbel  and things appear to be happening there. Any suggestions?

---

### Post by mixint27 on 2010-07-25
> **autocrosser said:**
> 

mixint27---you need the development versions of those to build...


thanks. what development versions do i need so i can proceed and where do i get these from.

if you can be specific please...thanks!

---

### Post by bethebunny on 2010-07-25
I've been getting this error when trying to build dconf, both last night and today:

```


make[1]: Entering directory `/home/bunny/gnome-shell/source/dconf/client'
  GISCAN dconf-0.3.gir
/home/bunny/gnome-shell/source/dconf/client/tmp-introspectnyKmuP/dconf-0.3: error while loading shared libraries: libdconf.so.0: cannot open shared object file: No such file or directory
Command '['/home/bunny/gnome-shell/source/dconf/client/tmp-introspectnyKmuP/dconf-0.3', '--introspect-dump=/home/bunny/gnome-shell/source/dconf/client/tmp-introspectnyKmuP/types.txt,/home/bunny/gnome-shell/source/dconf/client/tmp-introspectnyKmuP/dump.xml']' returned non-zero exit status 127
make[1]: *** [dconf-0.3.gir] Error 1
make[1]: Leaving directory `/home/bunny/gnome-shell/source/dconf/client'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/21]

```

This looks like a path error of some sort. 

```

$ ls ~/gnome-shell/source/dconf/client | grep libdconf
libdconf.so
libdconf.so.0
libdconf_so_0_vala.stamp

```

In case this was related to the bug discussed on the previous page, I tried that workaround to no avail.

```

$ ls /home/bunny/gnome-shell/install/lib | grep libdconf
libdconf.so.0

```

Any ideas on how to fix this? Looking forward to trying out gnome-shell!

---

### Post by autocrosser on 2010-07-25
> **mixint27 said:**
> thanks. what development versions do i need so i can proceed and where do i get these from.

if you can be specific please...thanks!

Get the same version names with the .dev after the library......

---

### Post by autocrosser on 2010-07-25
If you don't get a build the first time just try building again---and sometimes waiting a couple of hours (in case a commit is "stuck") will solve the issue.

---

### Post by autocrosser on 2010-07-25
> **Merk42 said:**
> Still got the error when I tried that.

I hope there haven't been any major GUI changes to GNOME Shell recently. I can't update the images since I haven't been able to successfully build for some time.

OK--I just was able to do a completely non-modified build--used the normal gnome-shell-build-setup.sh, did not modify any files & did a normal jhbuild build -f -a -c.....everything built without error.  How long this will hold true is the Developers knowledge & no-one else, but as of this moment I have a "stock" build running.........

---

### Post by Merk42 on 2010-07-25
> **autocrosser said:**
> OK--I just was able to do a completely non-modified build--used the normal gnome-shell-build-setup.sh, did not modify any files & did a normal jhbuild build -f -a -c.....everything built without error.  How long this will hold true is the Developers knowledge & no-one else, but as of this moment I have a "stock" build running.........Yet when I try it I get the aforementioned libgio and libdconf errors.
Perhaps because I'm on Lucid?

---

### Post by bethebunny on 2010-07-25
> **autocrosser said:**
> OK--I just was able to do a completely non-modified build--used the normal gnome-shell-build-setup.sh, did not modify any files & did a normal jhbuild build -f -a -c.....everything built without error.  How long this will hold true is the Developers knowledge & no-one else, but as of this moment I have a "stock" build running.........

I just did this as well, starting about 20 minutes after you posted, and am having precisely the same problem detailed in my previous post earlier on the page. Any clue why this might be happening?

---

### Post by autocrosser on 2010-07-25
Not sure--I'm building with Maverick x86-64---so in theory that "should" be harder to build.....I would guess that the Lucid .libs are "old" enough to not work well....

I'm no longer doing anything special to build---just have all the depends & run the script.

---

### Post by gotjazz on 2010-07-26
indeed - just installed macerick on my distrohopping partition and lo and behold. gnome-shell is built without a single complaint....

edit: 32bit in this case
edit2: although after building the graphical errors in 10.4 were less severe - but i assume that has something to do with xorg-server versions or the like. i had the same with OpenSUSE 11.3....

---

### Post by utnubu12 on 2010-07-26
I had the same "make: *** [all-recursive] Error 1" problem as bethebunny. > ```
make[1]: Entering directory `/home/bunny/gnome-shell/source/dconf/client'
  GISCAN dconf-0.3.gir
/home/bunny/gnome-shell/source/dconf/client/tmp-introspectnyKmuP/dconf-0.3: error while loading shared libraries: libdconf.so.0: cannot open shared object file: No such file or directory
Command '['/home/bunny/gnome-shell/source/dconf/client/tmp-introspectnyKmuP/dconf-0.3', '--introspect-dump=/home/bunny/gnome-shell/source/dconf/client/tmp-introspectnyKmuP/types.txt,/home/bunny/gnome-shell/source/dconf/client/tmp-introspectnyKmuP/dump.xml']' returned non-zero exit status 127
make[1]: *** [dconf-0.3.gir] Error 1
make[1]: Leaving directory `/home/bunny/gnome-shell/source/dconf/client'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/21]
```
Any help would be appreciated.

---

### Post by nls1729 on 2010-07-26
RE - dconf problem with gnome-shell build...  The problem has been reported to gnome folks.  GNOME Bugzilla – Bug 625236

---

### Post by mixint27 on 2010-07-26
im now having the same issue...


> **utnubu12 said:**
> I had the same "make: *** [all-recursive] Error 1" problem as bethebunny. 
Any help would be appreciated.

---

### Post by Peter09 on 2010-07-27
> Since the latest updates of Gnome-Shell I am getting no Recent-Items displayed. I have looked in .recently-used.xbel and things appear to be happening there. Any suggestions?
 
Anyone any suggestions as to where to start looking for this - I have re-purged the ppa and reinstalled gnome-shell, but no change.

---

### Post by NightwishFan on 2010-07-27
I would appreciate it if someone gives me a head up when the jhbuild is fixed. I also get the dconf failure.

---

### Post by VH-BIL on 2010-07-27
I will not move to Gnome 3 if I can't use Compiz!

---

### Post by x-shaney-x on 2010-07-27
> **VH-BIL said:**
> I will not move to Gnome 3 if I can't use Compiz!
I would hope Gnome3 would have a more extensive composite manager by then (or one to build on).

As much as I love compiz there are aspects that really spoil it (scale not showing minimized windows, window switchers showing big, very badly scaled icons for minimized windows etc).
The devs have made clear there will never be any hacky workarounds and it has been a problem for some time.

A window scale/present windows/expose, whatever you want to call it should show all windows, minimized or not, surely it's pointless otherwise?
I'm not personally bothered about the big eye candy stuff but the basics should be included in gnome 3.

---

### Post by VH-BIL on 2010-07-27
> **x-shaney-x said:**
> I would hope Gnome3 would have a more extensive composite manager by then (or one to build on).

As much as I love compiz there are aspects that really spoil it (scale not showing minimized windows, window switchers showing big, very badly scaled icons for minimized windows etc).
The devs have made clear there will never be any hacky workarounds and it has been a problem for some time.

A window scale/present windows/expose, whatever you want to call it should show all windows, minimized or not, surely it's pointless otherwise?
I'm not personally bothered about the big eye candy stuff but the basics should be included in gnome 3.

I don't find these to be problems for me. I like grouping and tabbing and using a computer without wobbly windows don't seem right anymore :p

---

### Post by gotjazz on 2010-07-27
wobbly windows? You really use that? Always makes me dizzy....

---

### Post by Peter09 on 2010-07-27
Yeah - I also like wobbly windows - it makes the desktop feel less wooden and fixed.

---

### Post by VH-BIL on 2010-07-27
I read somewhere that Compiz where thinking of making their own shell now that Gnome3 are integrating the window manager.

---

### Post by x-shaney-x on 2010-07-27
There was talk about that a long time ago.  A lot of changes have happened and I believe they only have one serious developer now.  Maybe the re-write will bring more cooks to the stove but only time will tell.
It doesn't seem to have the draw it did a couple of years ago.

---

### Post by KdotJ on 2010-07-27
> **x-shaney-x said:**
> There was talk about that a long time ago.  A lot of changes have happened and I believe they only have one serious developer now.  Maybe the re-write will bring more cooks to the stove but only time will tell.
It doesn't seem to have the draw it did a couple of years ago.

I too believe this. From what I have heard, there is only the one developer for Compiz now. And it's not an easy process going through files of code from the former devs

---

### Post by gotjazz on 2010-07-27
so anyway - when was the last time anyone successfully build GS on Ubuntu 10.4?

---

### Post by mr_hangman on 2010-07-27
> **gotjazz said:**
> so anyway - when was the last time anyone successfully build GS on Ubuntu 10.4?

I just successfully built GS with the newest commit.

FYI, the whole notification popup now is clickable :).

---

### Post by rayraven on 2010-07-27
> **mr_hangman said:**
> I just successfully built GS with the newest commit.

FYI, the whole notification popup now is clickable :).

Nice to hear!!

---

### Post by gotjazz on 2010-07-27
> **mr_hangman said:**
> I just successfully built GS with the newest commit.

FYI, the whole notification popup now is clickable :).

hrm so no missing dconf stuff, no undefined references or anything? And you're running Ubuntu 10.4? Interesting - I always assumed those 2 problems had something to do with how up-to-date certain things are seeing as I have no problem building gs on 10.10 alpha but it doesn't work on 10.4.

hrmpf - 10.4 doesn't build it but used to run it well - with 10.10 it's the other way around. Building in one and copying it over maybe? :p

---

### Post by mr_hangman on 2010-07-27
> **gotjazz said:**
> hrm so no missing dconf stuff, no undefined references or anything? And you're running Ubuntu 10.4? Interesting - I always assumed those 2 problems had something to do with how up-to-date certain things are seeing as I have no problem building gs on 10.10 alpha but it doesn't work on 10.4.

hrmpf - 10.4 doesn't build it but used to run it well - with 10.10 it's the other way around. Building in one and copying it over maybe? :p

Yes, I'm on lucid 10.04. I used to have those errors but they're gone with no explanation. What I did was just kept compiling and cleaning the dir. Did you try [6] Go to phase "wipe directory and start over"?

---

### Post by gotjazz on 2010-07-27
several times each try - i also started over with a completely clean build three times today alone...

oh well - one more time before i go to bed :D (if I delete the gnome-shell dir, the source dir, the twi jhbuild files in the home dir as well as even the build-setup script before starting over that's as clean as it gets, right?)

---

### Post by mr_hangman on 2010-07-27
> **gotjazz said:**
> several times each try - i also started over with a completely clean build three times today alone...

oh well - one more time before i go to bed :D (if I delete the gnome-shell dir, the source dir, the twi jhbuild files in the home dir as well as even the build-setup script before starting over that's as clean as it gets, right?)

I guess I need someone to answer this question. But as far as I know those are all the files needed for compiling GS. :popcorn:

---

### Post by gotjazz on 2010-07-27
hrm i installed a clean 10.4 on another machine and the build is running on it now with nothing but updating lucid from the official repos between install and building.....

i just keep wonderign if the distro is making such differences for building then what are all the devs using - debian unstable? :D

edit: nope - both errors again. i copied over that dconflib to get around the first one but gnome-shell itself still wont build...

---

### Post by quickridge on 2010-07-27
I am no longer seeing an error during the dconf build phase. However, gnome-shell will no longer start in the usual way. The work around is found in this bug report:
[https://bugzilla.gnome.org/show_bug.cgi?id=625345](https://bugzilla.gnome.org/show_bug.cgi?id=625345)

type
jhbuild run gnome-shell --replace


This works for me. I finally have gnome-shell again after several long days (its hard to stop hitting windows key for everything).

---

### Post by N4zroth on 2010-07-28
Hey,
now that i got to build gnome-shell (thanks to the guys in IRC), it seems to use a lot of resources, all my applications start lagging. Is that normal?
My sys specs are: P8600 2.4 Ghz, 2 GB RAM and a Mobility Radeon 3650.
Thanks.

---

### Post by gotjazz on 2010-07-28
Ah - something new:
```
*** Arbeitskopie wird erstellt gtk3 *** [8/21]
git clone git://git.gnome.org/gtk%2b gtk3
Initialized empty Git repository in /home/peter/gnome-shell/source/gtk3/.git/
fatal: The remote end hung up unexpectedly
*** Fehler während Phase checkout von gtk3: ########## Fehler beim Ausführen von git clone git://git.gnome.org/gtk%2b gtk3 *** [8/21
```I guess [http://git.gnome.org/browse/gnome-shell/commit/?id=b76fe12209e2c3224bd327959755d1f8c018a3c8](http://git.gnome.org/browse/gnome-shell/commit/?id=b76fe12209e2c3224bd327959755d1f8c018a3c8) didn't quite work out the way it was expected

---

### Post by autocrosser on 2010-07-28
Hmmm---I just did a full rebuild & did not have that problem---

---

### Post by alphonce on 2010-07-29
it's a bug with git ([http://thread.gmane.org/gmane.comp.version-control.git/151529]("http://thread.gmane.org/gmane.comp.version-control.git/151529"))

a workaround:

download [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules]("http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules")

and change the '%2d' to a '+' at row 88.
then change ~/.jhbuildrc at row 21, comment the original moduleset row and add a custom one to your altered gnome-shell.modules i.e. ```
moduleset = '/home/josef/Source/gnome-shell.modules'
```
and run jhbuild again. works for me :p

```
jhbuild build
```

> **gotjazz said:**
> Ah - something new:
```
*** Arbeitskopie wird erstellt gtk3 *** [8/21]
git clone git://git.gnome.org/gtk%2b gtk3
Initialized empty Git repository in /home/peter/gnome-shell/source/gtk3/.git/
fatal: The remote end hung up unexpectedly
*** Fehler während Phase checkout von gtk3: ########## Fehler beim Ausführen von git clone git://git.gnome.org/gtk%2b gtk3 *** [8/21
```I guess [http://git.gnome.org/browse/gnome-shell/commit/?id=b76fe12209e2c3224bd327959755d1f8c018a3c8](http://git.gnome.org/browse/gnome-shell/commit/?id=b76fe12209e2c3224bd327959755d1f8c018a3c8) didn't quite work out the way it was expected

---

### Post by Masteredu on 2010-07-29
HI! my prob is it gives an error in the 20/21 section.
the error is from make :


/home/gotwig/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Fehler 1
make[3]: Verlasse Verzeichnis '/home/gotwig/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Fehler 2
make[2]: Verlasse Verzeichnis '/home/gotwig/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/gotwig/gnome-shell/source/gnome-shell'
make: *** [all] Fehler 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [20/21]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"


PLS. HELP ME :(!

---

### Post by N4zroth on 2010-07-29
I had the same problem. I got the following solution from the guys on IRC (thanks):

- go to your ~/gnome-shell/install/lib/
- copy all *.la files to a backup location ($ mkdir ~/backup && mv *.la ~/backup/)
- build only gnome-shell ($ jhbuild buildone -afcn gnome-shell)
- copy all *.la files back ($ mv ~/backup/* ~/gnome-shell/install/lib/)
- build again ($ jhbuild build)
- it should run fine now and you should be able to run $ jhbuild run gnome-shell

I hope this helps :)

---

### Post by Masteredu on 2010-07-29
it work´s. thx!

---

### Post by gotjazz on 2010-07-29
Thanks a lot - gtk3 is building again :)

> **alphonce said:**
> it's a bug with git ([http://thread.gmane.org/gmane.comp.version-control.git/151529](http://thread.gmane.org/gmane.comp.version-control.git/151529))

a workaround:

download [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules](http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules)

and change the '%2d' to a '+' at row 88.
then change ~/.jhbuildrc at row 21, comment the original moduleset row and add a custom one to your altered gnome-shell.modules i.e. ```
moduleset = '/home/josef/Source/gnome-shell.modules'
```and run jhbuild again. works for me :p

```
jhbuild build
```

---

### Post by keypox on 2010-07-29
So what is the new procedure to get gnome shell working?  Does the OP still apply?

---

### Post by wersdaluv on 2010-07-29
> **alphonce said:**
> it's a bug with git ([http://thread.gmane.org/gmane.comp.version-control.git/151529]("http://thread.gmane.org/gmane.comp.version-control.git/151529"))

a workaround:

download [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules]("http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules")

and change the '%2d' to a '+' at row 88.
then change ~/.jhbuildrc at row 21, comment the original moduleset row and add a custom one to your altered gnome-shell.modules i.e. ```
moduleset = '/home/josef/Source/gnome-shell.modules'
```
and run jhbuild again. works for me :p

```
jhbuild build
```
For some reason, this didn't work for me. 

I also got 
```
*** Checking out gtk3 *** [8/21]
git clone git://git.gnome.org/gtk%2b gtk3
Initialized empty Git repository in /home/allan/gnome-shell/source/gtk3/.git/
fatal: The remote end hung up unexpectedly
*** Error during phase checkout of gtk3: ########## Error running git clone git://git.gnome.org/gtk%2b gtk3 *** [8/21]

```

What could be the fix?

---

### Post by wersdaluv on 2010-07-29
magcius (Jasper St. Pierre)on #gnome-shell was kind enough to give us workarounds.

To those face the [git bug]("http://thread.gmane.org/gmane.comp.version-control.git/151529") or ```
*** Checking out gtk3 *** [8/21]
git clone git://git.gnome.org/gtk%2b gtk3
Initialized empty Git repository in /home/allan/gnome-shell/source/gtk3/.git/
fatal: The remote end hung up unexpectedly
*** Error during phase checkout of gtk3: ########## Error running git clone git://git.gnome.org/gtk%2b gtk3 *** [8/21]
```
This is because git broke and is backwards incompatible. It's hard to fix both ways. The workaround is running
```
pushd ~/gnome-shell/source/ && git clone git://git.gnome.org/gtk+ gtk3 && popd
```


As for those using **nVidia**, GS is going to be really slow without a xorg patch. Here's the [bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=613936"). [Here's the patch]("http://fpaste.org/dcsD/").

OP: Please add these to the first post.

---

### Post by Mblackwell on 2010-07-29
> **wersdaluv said:**
> magcius (Jasper St. Pierre)on #gnome-shell was kind enough to give us workarounds.

To those face the [git bug]("http://thread.gmane.org/gmane.comp.version-control.git/151529") or ```
*** Checking out gtk3 *** [8/21]
git clone git://git.gnome.org/gtk%2b gtk3
Initialized empty Git repository in /home/allan/gnome-shell/source/gtk3/.git/
fatal: The remote end hung up unexpectedly
*** Error during phase checkout of gtk3: ########## Error running git clone git://git.gnome.org/gtk%2b gtk3 *** [8/21]
```
This is because git broke and is backwards incompatible. It's hard to fix both ways. The workaround is running
```
pushd ~/gnome-shell/source/ && git clone git://git.gnome.org/gtk+ gtk3 && popd
```


As for those using **nVidia**, GS is going to be really slow without a xorg patch. Here's the [bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=613936"). [Here's the patch]("http://fpaste.org/dcsD/").

OP: Please add these to the first post.

[http://ubuntuforums.org/showpost.php?p=9624079&postcount=419](http://ubuntuforums.org/showpost.php?p=9624079&postcount=419)

Doing this is a quick fix until Xorg 1.9 is pushed. It should be placed in the OP.

---

### Post by magcius on 2010-07-30
I don't use Ubuntu currently, sorry, I'm now on Arch. wers linked me to the thread.

There are two patches for nVidia, one for the [xorg server](http://fpaste.org/dcsD/), and one for [gnome-shell](https://bugzilla.gnome.org/attachment.cgi?id=157326). I am not sure if the current version of the server (1.7.5) is compatible with this patch. Someone might want to make a PPA for the xorg server if it is.

I have the first patch applied for my xserver, but I don't have the one for the shell applied currently. I will try it soon.

There are a couple issues here, the slowdown on my old AGP card is due to the fact that setting the input shapes cause some expensive calculations happen in the driver, so the first patch is necessary to make sure that it only does the expensive calculation when it's updating the correct field.

The second patch sets the priority timer that sets the input region to not happen while animations are in progress.

Mblackwell, there are two different patches here. And I do not believe that the 256 driver series is stable with 1.9.

---

### Post by mixint27 on 2010-07-30
hello...so i was now able to run gnome shell...

I get this error in the terminal...how can i fix this.

Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
      JS LOG: GNOME Shell started at Thu Jul 29 2010 23:32:54 GMT-0700 (PST)
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
Allocating 107 x 26 radeon RBO (pitch 112)
Allocating 107 x 26 radeon RBO (pitch 128)
Allocating 107 x 26 radeon RBO (pitch 112)
Allocating 107 x 26 radeon RBO (pitch 112)
Allocating 107 x 26 radeon RBO (pitch 128)

---

### Post by magcius on 2010-07-30
Those aren't bugs.

The first is due to the shell using gtk3 while your current modules were built for gtk2. There's no harm there.

The rest of the output is pretty much useless, and has to do with the Raedon driver.

If something doesn't work or runs slow, that's not very good.

Furthermore, I'm going to crowd-source this some more. Would those who are running the shell from git/jhbuild (NOT from ricotz's PPA) mind registering for the shell performance tracker: [http://shell-perf.gnome.org/home](http://shell-perf.gnome.org/home)

You'll get an email of what to do. Make sure to run the tests with only a simple terminal window open, otherwise the tests aren't reproducible.

---

### Post by gotjazz on 2010-07-30
AH now that's a good thing - registered and tested

---

### Post by Mblackwell on 2010-07-30
> **magcius said:**
> I don't use Ubuntu currently, sorry, I'm now on Arch. wers linked me to the thread.

There are two patches for nVidia, one for the [xorg server](http://fpaste.org/dcsD/), and one for [gnome-shell](https://bugzilla.gnome.org/attachment.cgi?id=157326). I am not sure if the current version of the server (1.7.5) is compatible with this patch. Someone might want to make a PPA for the xorg server if it is.

I have the first patch applied for my xserver, but I don't have the one for the shell applied currently. I will try it soon.

There are a couple issues here, the slowdown on my old AGP card is due to the fact that setting the input shapes cause some expensive calculations happen in the driver, so the first patch is necessary to make sure that it only does the expensive calculation when it's updating the correct field.

The second patch sets the priority timer that sets the input region to not happen while animations are in progress.

Mblackwell, there are two different patches here. And I do not believe that the 256 driver series is stable with 1.9.

I see what you're saying, but the "second patch" as you call it will give a huge increase in performance. It turned GS on my old 9300 from a sluggish mess into a smooth experience. You shouldn't need to go through the trouble of patching and building xorg for now.

---

### Post by magcius on 2010-07-30
Depends on your card. The gnome-shell patch didn't do anything for me, the xserver patch gave a major improvement.

---

### Post by Mblackwell on 2010-07-30
Interesting.

---

### Post by Merk42 on 2010-07-30
Well I guess I should update it say it is impossible to build on anything less than Maverick?
Even with the GTK+ patch, I STILL get the libgio and libgtk errors.

So I guess when that new look gets in GNOME Shell I can't update the images since I'm only running Lucid.

---

### Post by Mblackwell on 2010-07-30
Curious why the Ricotz PPA hasn't been updated since the 4th of July...

---

### Post by mixint27 on 2010-07-30
> **magcius said:**
> Those aren't bugs.

The first is due to the shell using gtk3 while your current modules were built for gtk2. There's no harm there.

The rest of the output is pretty much useless, and has to do with the Raedon driver.

If something doesn't work or runs slow, that's not very good.

Furthermore, I'm going to crowd-source this some more. Would those who are running the shell from git/jhbuild (NOT from ricotz's PPA) mind registering for the shell performance tracker: [http://shell-perf.gnome.org/home](http://shell-perf.gnome.org/home)

You'll get an email of what to do. Make sure to run the tests with only a simple terminal window open, otherwise the tests aren't reproducible.

thanks for your input. i have been getting errors while using gnome in the terminal; all about clutter warnings...but gnome on my laptop seems to run pretty good. have note experienced slowness yet.

---

### Post by magcius on 2010-07-31
If anybody is experiencing errors or warnings, we can't do anything about them unless you tell us what they are.

Merk42, I'm guessing that you're having some link warnings: 'undefined reference'?

Try: rm ~/gnome-shell/install/*.la /usr/lib/*.la

---

### Post by Merk42 on 2010-07-31
> **magcius said:**
> If anybody is experiencing errors or warnings, we can't do anything about them unless you tell us what they are.

Merk42, I'm guessing that you're having some link warnings: 'undefined reference'?

Try: rm ~/gnome-shell/install/*.la /usr/lib/*.la

Yes which I mentioned pages ago, but I guess it got lost.
I ran that command and I still get errors
```
make[2]: Entering directory `/home/merk/gnome-shell/source/gobject-introspection/gir'
  CC     libgirepository_everything_1_0_la-everything.lo
  CCLD   libgirepository-everything-1.0.la
/bin/sed: can't read /usr/lib/libfreetype.la: No such file or directory
libtool: link: `/usr/lib/libfreetype.la' is not a valid libtool archive
make[2]: *** [libgirepository-everything-1.0.la] Error 1
make[2]: Leaving directory `/home/merk/gnome-shell/source/gobject-introspection/gir'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/merk/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/21]

```

---

### Post by magcius on 2010-07-31
That doesn't look very good. sed shouldn't be run on something like that.

I'd suggest rm -rf ~/gnome-shell and rerunning the [setup script](http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh) and doing another jhbuild.

---

### Post by MacUntu on 2010-07-31
*** success *** [21/21]

It definitely builds right now (except for that git incompatibility thing).

Edit:

Wow, you weren't kidding with > As for those using nVidia, GS is going to be really slow without a xorg patch.
Compared to Unity it's awfully slow. Not sure I want to compile the whole Xorg, though.

---

### Post by magcius on 2010-07-31
You could try the gnome-shell patch first:

```

cd ~/gnome-shell/source/gnome-shell/
curl http://bugzilla-attachments.gnome.org/attachment.cgi?id=157326 > nvidia-flash.patch
git am flash.patch

```

Then rebuild with jhbuild.

---

### Post by MacUntu on 2010-07-31
Thanks, it's indeed a lot better now.

---

### Post by Merk42 on 2010-07-31
Finally built successfully, as such I've added a bit to the OP.

---

### Post by quickridge on 2010-07-31
> **magcius said:**
> You could try the gnome-shell patch first:

```

cd ~/gnome-shell/source/gnome-shell/
curl http://bugzilla-attachments.gnome.org/attachment.cgi?id=157326 > nvidia-flash.patch
git am flash.patch

```Then rebuild with jhbuild.

Thanks for the showing how to incorporate a patch into the jhbuild sequence. I was doing it manually before this.

This patch improved performance slightly while I am watching videos (I was having trouble for some reason while running gnome-shell) but the flickering still remains.  I'm too lazy to deal with the xorg patch so I think I'll just deal with it for now.

---

### Post by NightwishFan on 2010-07-31
I got the GTK3 build error and did the workaround as was suggested earlier. It is building now *fingers crossed*.

---

### Post by magcius on 2010-07-31
> **Merk42 said:**
> 
**How do I Try it?**

Running Jaunty, Karmic, Lucid and Maverick there are three ways to try GNOME Shell
[LIST]
[*]Install the gnome-shell package (easy but out of date)
[*]Use the [Ricotz PPA]("http://ubuntu-tweak.com/source/gnome-shell-testing/") (slightly harder, but more up to date)
[*]Build from source (more difficult, but up to date when something is added, provided you rerun jhbuild build)
[/LIST]

ricotz is now out of date. Don't use it.

> **Merk42 said:**
> 
[*]Get jhbuild (not a command line entry)
[LIST]
[*]For Lucid via repository, package name "jhbuild".
[*][From Jaunty]("http://packages.ubuntu.com/en/jaunty/jhbuild")
[*][From Debian]("http://packages.debian.org/unstable/devel/jhbuild")
[/LIST]


The gnome-shell-setup-build.sh will actually check out jhbuild for you. It will be in ~/bin/jhbuild. We regularly update jhbuild when it breaks our build, and it will auto-update with that script, so it is best to use that instead of the package.

> **Merk42 said:**
> 
**Yay! It's finally done building! Now what?**
To run
[LIST=1]
[*]cd ~/gnome-shell/source/gnome-shell/src
[*]./gnome-shell --replace
[/LIST]

To quit GNOME Shell and return to the panels
[list=1[*]Go to the terminal
[*]hit CTRL-C[/list]

To update (check the [commit log]("http://git.gnome.org/browse/gnome-shell") for anything new)
[LIST]
[*]jhbuild build (rebuilds updated files)
[*]jhbuild build -f -a -c (builds all gnome shell files)
[/LIST]



The commit log of gnome-shell isn't really what you should only check. This is gnome 3 really, so we make a lot of other modifications which should solve other things like performance, graphics glitches. Really, I run jhbuild again, and then use Alt+F2 'replace' to restart it.

> **Merk42 said:**
> 
If you want to make it your default, put "gnome-shell --replace" in your Startup Items

Not a good idea either, if you really want to do this, I would suggest using a different GDM session. There are various tutorials all over the web.

> **Merk42 said:**
> 
**Love it? Hate it? Have a suggestion? Make your voice heard in the [GNOME Shell mailing list]("http://mail.gnome.org/mailman/listinfo/gnome-shell-list")**
The mailing list really isn't the best place for feedback anymore. For design issues, we have meetings in IRC on gimpnet, #gnome-shell, Wednesdays from 2-4 PM EST.

---

### Post by NightwishFan on 2010-07-31
Thanks for the information magcius!

As far as my building went, Success! I had to do the gtk3 workaround listed previous in this thread, and then followed bugzilla comments: 13 & 15 and got it working. Keeping it on my laptop full time, it runs great.

[https://bugzilla.gnome.org/show_bug.cgi?id=623952](https://bugzilla.gnome.org/show_bug.cgi?id=623952)

---

### Post by Merk42 on 2010-07-31
> **magcius said:**
> ricotz is now out of date. Don't use it.



The gnome-shell-setup-build.sh will actually check out jhbuild for you. It will be in ~/bin/jhbuild. We regularly update jhbuild when it breaks our build, and it will auto-update with that script, so it is best to use that instead of the package.



The commit log of gnome-shell isn't really what you should only check. This is gnome 3 really, so we make a lot of other modifications which should solve other things like performance, graphics glitches. Really, I run jhbuild again, and then use Alt+F2 'replace' to restart it.


Not a good idea either, if you really want to do this, I would suggest using a different GDM session. There are various tutorials all over the web.


The mailing list really isn't the best place for feedback anymore. For design issues, we have meetings in IRC on gimpnet, #gnome-shell, Wednesdays from 2-4 PM EST.

Wow just tear apart my entire OP :(

So if people shouldn't check the commit log for updates, what should they check?

---

### Post by fremantle on 2010-07-31
what were you guys thinking? gnome shell looks <snip>!!!!!! i hope someone keeps maintaining the good old gnome we love. i mean seriously, you replace apps, places, system with "activities"///././././ <snip>.

---

### Post by NightwishFan on 2010-07-31
Bah, it is quite awesome, and it is something new. I hope it works out quite nicely.

---

### Post by Merk42 on 2010-08-01
> **fremantle said:**
> what were you guys thinking? gnome shell looks <snip>!!!!!! i hope someone keeps maintaining the good old gnome we love. i mean seriously, you replace apps, places, system with "activities"///././././ <snip>.
Did you read the first post or just look at the pictures?
> **Merk42 said:**
> **OMG GNOME SHELL IS AWFUL! I'm moving to xfce/Windows/an abacus**
Calm down. Look at the [GNOME 3 Myths]("http://live.gnome.org/GNOME3Myths")
> **MYTH: GNOME won't support the current panel and window manager anymore and I don't want to use GNOME Shell**

**TRUTH: The GNOME 2.x panel and Metacity (the window manager) will still be available.**
Downstream distributions such as Fedora, openSUSE and Ubuntu will have the option to include them in their distribution. You will be able to install them just as now you can install sawfish, compiz, etc inside your GNOME session. (There are no plans to support GNOME panel applets in GNOME Shell, TBA. This mailing list post has some information.) 

---

### Post by Mblackwell on 2010-08-01
> **fremantle said:**
> what were you guys thinking? gnome shell looks <snip>!!!!!! i hope someone keeps maintaining the good old gnome we love. i mean seriously, you replace apps, places, system with "activities"///././././ <snip>.

Pretty sure you're looking for this thread:

[http://ubuntuforums.org/showthread.php?t=1457428](http://ubuntuforums.org/showthread.php?t=1457428)

---

### Post by magcius on 2010-08-01
There are other things that are built besides gnome-shell during jhbuild time. These are not the only part of gnome3. Suggesting that we go to the commit log for gnome-shell is bad. There's no reason to go every time.

Also, unfortunately, gnome-panel is not maintained currently, and probably won't have a maintainer again. So, while available, isn't going to be getting the bump to gnome 3 or upgrades. It's up to the maintainers now.

Why can't we use or extend compiz with a plugin? Because it's not under our control. We have to manipulate window textures and such. We'd rather have something that we control. Clutter (and its little brother mutter which was made for Moblin/Intel) were with our vision: the developers already worked on gnome, and had coding standards like gnome.

We're a little pressed on extensibility right now, and we know it sucks. Firefox/Mozilla's Add-ons were developed after people saw what kind of modifications people made to the codebase, and adding ways to make that easier. I'm doing the same thing in several ways, so I hope to present to the team what a helpful extension model would be and where we need "hooks" the most. Right now most would agree that the top panel would be nice for widgets/gadgets/["gizmos"](http://live.gnome.org/GnomeShell/Design/Whiteboards/Gizmos). I'm going to be implementing a "Show Desktop" for the top panel as a test demonstration.

Regarding "Recent Items": it's been a placeholder for a good while now, so there was no good effort to do anything with the design (like clearing the data or removing the panel).

The categories were a conscious design decision to try and emphasize the search bar, but it failed, and we're adding them back, although a lot of applications should be a lot better categorized: Accessories vs. System Tools vs. Programming vs. Preferences vs. Administration. Raise hands: Who else goes looking through each of those? The lines were always a bit blurred, and we'd like a bit better standards on those.

Yes, the design has sucked for a little bit now. It's been through several iterations and the current design, while neat (debatable), it's found a lot of scope creep. A lot of the good features in gnome 2 were underused, and a lot of the bad ones (unstable, technically unmaintainable, outdated) were overused.

We're doing some more new mockups and testing to see how you like it. We've gotten lots of feedback, doing some user testing, and we're rethinking how we do some design principles. No, we're not going to include "Wobbly Windows", we're looking for good user interface, not 5 minute OpenGL transformation demos applied to window textures..

There are still a few design issues standing with the new gnome-shell-design, but I have addressed mccann and jimmac, and we are looking forward to getting these resolved.

Instead of "it sucks", tell us why it sucks: do you not like the context switch of going to the overview and would like easier window/workspace switching? Is it slow (plug for the [Shell Performance](http://shell-perf.gnome.org/) Not extensible enough? Are the colors too ugly?

tl;dr: read it. I don't need analysis or an essay. It's not that long, trust me.

---

### Post by cariboo on 2010-08-01
I decided to try to build gnome-shell, I ran the build setup script 4 hours ago and now I'm at 75%. Is this normal?

---

### Post by NightwishFan on 2010-08-01
Not normal for me, I downloaded and built the whole shell in around 40 mins.

---

### Post by Merk42 on 2010-08-01
> **magcius said:**
> There are other things that are built besides gnome-shell during jhbuild time. These are not the only part of gnome3. Suggesting that we go to the commit log for gnome-shell is bad. There's no reason to go every time.
So, nowhere then?
There's nothing equivalent to a change log anywhere?

> **cariboo907 said:**
> I decided to try to build gnome-shell, I ran the build setup script 4 hours ago and now I'm at 75%. Is this normal?
What does the terminal say?
Ever since GTK3 was included it does take quite a bit of time to download everything for GNOME Shell.

---

### Post by ranch hand on 2010-08-01
> **magcius said:**
> There are other things that are built besides gnome-shell during jhbuild time. These are not the only part of gnome3. Suggesting that we go to the commit log for gnome-shell is bad. There's no reason to go every time.

Also, unfortunately, gnome-panel is not maintained currently, and probably won't have a maintainer again. So, while available, isn't going to be getting the bump to gnome 3 or upgrades. It's up to the maintainers now.

Why can't we use or extend compiz with a plugin? Because it's not under our control. We have to manipulate window textures and such. We'd rather have something that we control. Clutter (and its little brother mutter which was made for Moblin/Intel) were with our vision: the developers already worked on gnome, and had coding standards like gnome.

We're a little pressed on extensibility right now, and we know it sucks. Firefox/Mozilla's Add-ons were developed after people saw what kind of modifications people made to the codebase, and adding ways to make that easier. I'm doing the same thing in several ways, so I hope to present to the team what a helpful extension model would be and where we need "hooks" the most. Right now most would agree that the top panel would be nice for widgets/gadgets/["gizmos"]("http://live.gnome.org/GnomeShell/Design/Whiteboards/Gizmos"). I'm going to be implementing a "Show Desktop" for the top panel as a test demonstration.

Regarding "Recent Items": it's been a placeholder for a good while now, so there was no good effort to do anything with the design (like clearing the data or removing the panel).

The categories were a conscious design decision to try and emphasize the search bar, but it failed, and we're adding them back, although a lot of applications should be a lot better categorized: Accessories vs. System Tools vs. Programming vs. Preferences vs. Administration. Raise hands: Who else goes looking through each of those? The lines were always a bit blurred, and we'd like a bit better standards on those.

Yes, the design has sucked for a little bit now. It's been through several iterations and the current design, while neat (debatable), it's found a lot of scope creep. A lot of the good features in gnome 2 were underused, and a lot of the bad ones (unstable, technically unmaintainable, outdated) were overused.

We're doing some more new mockups and testing to see how you like it. We've gotten lots of feedback, doing some user testing, and we're rethinking how we do some design principles. No, we're not going to include "Wobbly Windows", we're looking for good user interface, not 5 minute OpenGL transformation demos applied to window textures..

There are still a few design issues standing with the new gnome-shell-design, but I have addressed mccann and jimmac, and we are looking forward to getting these resolved.

Instead of "it sucks", tell us why it sucks: do you not like the context switch of going to the overview and would like easier window/workspace switching? Is it slow (plug for the [Shell Performance]("http://shell-perf.gnome.org/") Not extensible enough? Are the colors too ugly?

tl;dr: read it. I don't need analysis or an essay. It's not that long, trust me.
I really like the menus as they are in the current gnome, all of them.  Yes I use the catagories and have no trouble with them.

A bunch of icons, that you have to memorize, cluttering things up are not needed at all unless you are an avid employee of business' that use pictures on their cash registers.

Text is neater and takes up less room.

As for your colors I have not built GS in a while and want to.  Reading the problems folks are having does not encourage this.  The last time I had up I had to change the theme from another OS on the drive because looking at the default (black) theme made me have eye twitches and a migraine in the first 5 minutes.  From that, I would say that the folks designing it have very strange taste in themes.

There are, or were, lots of much better themes available from folks around the forum though.  Therefore it is not something I worry about.  I was even able to mess with it a bit.  That was very nice.

The design is pretty bad for me as far as using it goes.  I have 6 work spaces with different, and multible, things on each and use them all.  I have the switcher at top center of my screen and can get to the one I need very fast with one move of the mouse.  None of this gratuitous wild swinging of the mouse back and forth across the screen and obnoxious zooming in and out.

I think the current design is probably usable if you use one work space and do not much more than chat and watch YouTube clips (gossip and giggles).

A decent menu and some usable way to us work spaces are really just foundational needs for this to work in a non irritating manner.

The last mockup I saw looked more like the Unity desktop which I would say in a big improvement but lacking in the flexibility that I am used to and which made me decide to use gnome in the first place.

Thank you for the information on GS and Gnome3.  Very interesting and informative.

I hope the directions for building work next week as I intend to put (attempt anyway) GS on one of my 10.10 installs and give it a whirl.

---

### Post by cariboo on 2010-08-01
> What does the terminal say?
Ever since GTK3 was included it does take quite a bit of time to download everything for GNOME Shell.

I got tired of waiting yesterday, so I am downloading it again today. This has been running for just over 2 hours:

```
/bin/bash gnome-shell-build-setup.sh
Checking out jhbuild into /home/me/Source/jhbuild ... remote: Counting objects: 23058, done.
remote: Compressing objects: 100% (5913/5913), done.
Receiving objects:   4% (923/23058), 172.00 KiB
```

---

### Post by NightwishFan on 2010-08-01
I think something is in error. ;/ Do you have a good connection with the destination?

---

### Post by Merk42 on 2010-08-01
> **cariboo907 said:**
> I got tired of waiting yesterday, so I am downloading it again today. This has been running for just over 2 hours:

```
/bin/bash gnome-shell-build-setup.sh
Checking out jhbuild into /home/me/Source/jhbuild ... remote: Counting objects: 23058, done.
remote: Compressing objects: 100% (5913/5913), done.
Receiving objects:   4% (923/23058), 172.00 KiB
```
As long as that receiving objects percentage is going up you're fine.
Like I said a lot has to be downloaded.
On the plus side, once everything builds successfully, subsequent runs of "jhbuild build" will only download the parts that have changed so it will be much quicker

---

### Post by MacUntu on 2010-08-01
But that's only jhbuild - there's definitely something wrong. Checking out jhbuild should be done in no time.

---

### Post by cariboo on 2010-08-01
> **NightwishFan said:**
> I think something is in error. ;/ Do you have a good connection with the destination?

In a browser I can connect to the gnome-shell git index almost instantly.

---

### Post by Mblackwell on 2010-08-01
I decided to try building since the PPA is so far behind. So far so good, but how long will this take to compile? Normally I make -j5 (which builds the entire Wine tree in about 5 minutes) but that didn't appear to be an option in this case.

---

### Post by autocrosser on 2010-08-01
It takes me about 40 minutes with a i7-940 clocked @ 3.8ghz. That's a clean build without any major downloads.

---

### Post by Mblackwell on 2010-08-01
It built fine, but it doesn't seem to save dconf settings. Meaning my favorites aren't retained when I restart among other things. What am I missing/how do I remedy it?

---

### Post by ramarcos on 2010-08-03
> **mblackwell said:**
> it built fine, but it doesn't seem to save dconf settings. Meaning my favorites aren't retained when i restart among other things. What am i missing/how do i remedy it?


+1

---

### Post by cariboo on 2010-08-03
I finally managed to get gnome-shell to build, on a system running Lucid.

---

### Post by NightwishFan on 2010-08-03
> **Mblackwell said:**
> It built fine, but it doesn't seem to save dconf settings. Meaning my favorites aren't retained when I restart among other things. What am I missing/how do I remedy it?

I have this issue as well.

---

### Post by Mblackwell on 2010-08-04
Completely purge the ricotz ppa if you had it installed before. Then uninstall any copies of gnome-shell remaining, and all dependencies that went with it. When you're clean make sure to reinstall any necessary packages to get the build-setup script working. 

(note: in my case some ubuntu-desktop packages ended up removed by the end, so I ran apt-get install -f to fix this)

Then delete the ~/.config/dconf folder and /usr/lib/*.la to remove old modules(you may need to use sudo for the second) and if you've already compiled delete the ~/gnome-shell/install folder.

Then run gconftool-2 --recursive-unset /desktop/gnome/shell and follow that with gconftool-2 --recursive-unset /apps/gnome-shell


When all this is done run jhbuild build -afc

You should now have a nice working copy of gnome-shell with dconf settings saved. Thanks to magcius and drago01 for the help, it took basically all day to figure out what exactly was going on.

In addition repo installed copies of gnome-shell may have linked gsettings-data-convert to your startup applications. Since this doesn't exist globally anymore you'll have to change this to your local copy (~/gnome-shell/source/gconf/gsettings/gsettings-data-convert).

Someone point out if that's even a necessary program to have running anymore.

---

### Post by Starks on 2010-08-04
I think liborbit2-dev are now needed for the compilation.

---

### Post by Tchus on 2010-08-04
Hi all,
I want to test gnome shell, I tried every thing to build and every time I got a error, now I have this message "vala-0.9.4 not found" and when I look into ~/gnome-shell/source I see that he "git" vala-.0.9.3, any idea how to fix this ?

---

### Post by hotstovejer on 2010-08-04
I'm also having an issue where I run the gnome-shell-build-setup.sh, and it tells me
```
GNOME 2.26 or newer is required to build GNOME Shell

```

I'm running Lucid, so what the heck! I checked the script, and that's the first thing it checks!

---

### Post by ramarcos on 2010-08-04
> **Tchus said:**
> Hi all,
I want to test gnome shell, I tried every thing to build and every time I got a error, now I have this message "vala-0.9.4 not found" and when I look into ~/gnome-shell/source I see that he "git" vala-.0.9.3, any idea how to fix this ?


Having the same issue... something related to 

[https://bugzilla.gnome.org/show_bug.cgi?id=626000](https://bugzilla.gnome.org/show_bug.cgi?id=626000)

any known workaround while bug is opened?

---

### Post by cariboo on 2010-08-04
I just built gnome-shell on lucid yesterday, with no problems. If I remember correctly lucid uses gnome 2.28.

---

### Post by Koekey on 2010-08-04
> **Tchus said:**
> Hi all,
I want to test gnome shell, I tried every thing to build and every time I got a error, now I have this message "vala-0.9.4 not found" and when I look into ~/gnome-shell/source I see that he "git" vala-.0.9.3, any idea how to fix this ?

Had the same problem.

Just to fix this quick and dirty you could just build vala-0.9.4 yourself.

```
$ wget http://download.gnome.org/sources/vala/0.9/vala-0.9.4.tar.bz2
```

extract to anywhere you want.

```
$ ./configure && make
$ cp compiler/valac ~/gnome-shell/install/bin/
```

run jhbuild again.

It is not very elegant, but at least it works until the developers have found a solution ;)

---

### Post by ramarcos on 2010-08-05
> **Mblackwell said:**
> Completely purge the ricotz ppa if you had it installed before. Then uninstall any copies of gnome-shell remaining, and all dependencies that went with it. When you're clean make sure to reinstall any necessary packages to get the build-setup script working. 


How can you be sure everything is clean? How can you obtain a list of all dependecies gnome-shell install (from official repositories and from ricotz)?

> **Mblackwell said:**
> 
In addition repo installed copies of gnome-shell may have linked gsettings-data-convert to your startup applications. Since this doesn't exist globally anymore you'll have to change this to your local copy (~/gnome-shell/source/gconf/gsettings/gsettings-data-convert).

Someone point out if that's even a necessary program to have running anymore.


How is it done?

Thanks!

---

### Post by magcius on 2010-08-05
The moduleset was updated to vala 0.9.4 yesterday, it should be fine to build now.

You can look at the ricotz PPA page to see what the packages you should uninstall are, but the major one you need to uninstall is called d-conf; Debian's dconf is unrelated.

You can remove gsettings-data-convert (you shouldn't need it in the startup applications) by using the Startup Applications dialog in System Preferences or deleting the appropriate .desktop file in ~/.config/autostart

---

### Post by wdg on 2010-08-06
On Lucid I'm getting a different dconf problem to what has been described earlier. Is anyone else seeing this?
```

  GISCAN dconf-0.3.gir
Traceback (most recent call last):
  File "/home/xxx/gnome-shell/install/bin/g-ir-scanner", line 38, in <module>
    sys.exit(scanner_main(sys.argv))
  File "/home/xxx/gnome-shell/install/lib/gobject-introspection/giscanner/scannermain.py", line 330, in scanner_main
    glibtransformer.get_get_type_functions())
  File "/home/xxx/gnome-shell/install/lib/gobject-introspection/giscanner/dumper.py", line 246, in compile_introspection_binary
    return dc.run()
  File "/home/xxx/gnome-shell/install/lib/gobject-introspection/giscanner/dumper.py", line 132, in run
    self._link(bin_path, o_path)
  File "/home/xxx/gnome-shell/install/lib/gobject-introspection/giscanner/dumper.py", line 241, in _link
    subprocess.check_call(args)
  File "/usr/lib/python2.6/subprocess.py", line 493, in check_call
    retcode = call(*popenargs, **kwargs)
  File "/usr/lib/python2.6/subprocess.py", line 480, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.6/subprocess.py", line 633, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1139, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
make[1]: *** [dconf-0.3.gir] Error 1

```

---

### Post by Tompalaz on 2010-08-06
I get this error when I try to build..

> *** Configuring gdk-pixbuf *** [7/21]
./autogen.sh --prefix /home/tomas/gnome-shell/install --libdir '/home/tomas/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/tomas/gnome-shell/install --libdir '/home/tomas/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [7/21]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice:

Anything I can do?

Tried distclean, clean, wipe directory, rerun.

---

### Post by JustRon on 2010-08-06
> **Tompalaz said:**
> Anything I can do?

You must install the package "autopoint"

```
sudo apt-get install autopoint
```

---

### Post by Tompalaz on 2010-08-06
> **JustRon said:**
> You must install the package "autopoint"

```
sudo apt-get install autopoint
```

Thanks!

---

### Post by FFuser on 2010-08-06
> **Mblackwell said:**
> 
and /usr/lib/*.la to remove old modules(you may need to use sudo for the second)

This will ruin all the ubuntu *-dev packages and make it impossible to compile any other programs that want to link to libraries isn't it?

---

### Post by Mblackwell on 2010-08-06
[https://bugzilla.gnome.org/show_bug.cgi?id=623952#c11](https://bugzilla.gnome.org/show_bug.cgi?id=623952#c11)

[http://live.gnome.org/GnomeShell/RemovingLaFiles](http://live.gnome.org/GnomeShell/RemovingLaFiles)

---

### Post by tanmays on 2010-08-07
It worked :) Thanks

> **alphonce said:**
> it's a bug with git ([http://thread.gmane.org/gmane.comp.version-control.git/151529]("http://thread.gmane.org/gmane.comp.version-control.git/151529"))

a workaround:

download [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules]("http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell.modules")

and change the '%2d' to a '+' at row 88.
then change ~/.jhbuildrc at row 21, comment the original moduleset row and add a custom one to your altered gnome-shell.modules i.e. ```
moduleset = '/home/josef/Source/gnome-shell.modules'
```
and run jhbuild again. works for me :p

```
jhbuild build
```

---

### Post by tanmays on 2010-08-07
Here is Gnome-shell running on my HP DV2124 TU laptop.

---

### Post by tanmays on 2010-08-07
Just one problem. The Volume indicator is missing.

---

### Post by hrhnick on 2010-08-07
> **tanmays said:**
> Just one problem. The Volume indicator is missing.

add an entry to your startup applications for 'gnome-volume-control-applet'

it should appear when you restart your session. ;)

---

### Post by NightwishFan on 2010-08-08
Does anyone else have the ugly right click menu on the window borders?

---

### Post by magcius on 2010-08-08
Are you running gnome-shell with sudo or as root? That may cause it.

---

### Post by NightwishFan on 2010-08-08
No I built and run as my own user. I will poke around a bit. I believe it does it with just mutter as well.

---

### Post by autocrosser on 2010-08-08
FYI--Gnomelook.org has a couple of themes just out---Half-left has been making some that work with the build GS. Also available here: [http://half-left.deviantart.com/](http://half-left.deviantart.com/)

The Ambiance theme works very well---a little light on the overlay for my taste, but much better than the default theme!!!!!

Just setup his Sonar theme--looks very good!!

---

### Post by ranch hand on 2010-08-08
That does look pretty nice.  I am not a fan of GS but they did have the right idea when making it easy to make themes for it.

There are quite a few nice ones out there.

---

### Post by xtoudi on 2010-08-09
> **tanmays said:**
> Here is Gnome-shell running on my HP DV2124 TU laptop.

Is it conky?? If so ... when you're switching between apps (alt+tab) is conky visible on list of running apps??
I can not figure out how to get rid conky from GS alt+tab list.

it's my conky config about this:

```
own_window yes
own_window_transparent yes
#own_window_type override 
#own_window_type desktop
#own_window_hints sticky,skip_taskbar
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by CJN on 2010-08-10
Hey guys, just checking in, wondering if anyone's heard if compiz has started work to support gnome shell or if someone's working on a replacement.

Based on a closer read of the first post I'm guessing not. Bummer, looks like I have some work to do.

---

### Post by magcius on 2010-08-10
What do you need from Compiz in gnome-shell?

They are not, and never will be compatible.

Compiz is a window manager, gnome-shell is a window manager too. They won't be compatible without serious effort.

---

### Post by godhika on 2010-08-10
A slight correction: Mutter (Metacity + Clutter) is the window manager - Gnome-Shell is just a plugin for Mutter (just like Unity is)

---

### Post by magcius on 2010-08-10
Yes, that's true now, but it won't be in the future.

mutter is planned to be a library, since the plugin interface
is good in theory, but risky, finicky, and terrible to work
with.

So, mutter will only be an auxiliary to Moblin and gnome-shell.

---

### Post by autocrosser on 2010-08-10
Half-left has posted a new theme for GS---Elementary....  Look at his Deviant-Art page for it...see my post at the top of the page.....

---

### Post by davideotape on 2010-08-11
Hmm, doing a completely clean build, and I get this:

```
*** Configuring gdk-pixbuf *** [7/21]
./autogen.sh --prefix /home/david/gnome-shell/install --libdir '/home/david/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/david/gnome-shell/install --libdir '/home/david/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [7/21]

```

Prevents me from going any further.

---

### Post by autocrosser on 2010-08-11
> **davideotape said:**
> Hmm, doing a completely clean build, and I get this:

```
*** Configuring gdk-pixbuf *** [7/21]
./autogen.sh --prefix /home/david/gnome-shell/install --libdir '/home/david/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/david/gnome-shell/install --libdir '/home/david/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [7/21]

```Prevents me from going any further.

Look a couple of pages ago---you need to "sudo apt-get install autopoint" or use your favorite package manager.....That will clear that problem---there are several others right now that I'm working thru---will post with "solutions" if they look interesting......

---

### Post by GraemeLockett on 2010-08-11
Hi Ricotz,

I used your PPA to look at gnome shell testing and recently upgraded to Maverick Alpha 3. When the upgrade complete the apt-get tools started complaining. 

The following packages have unmet dependencies:
 gir1.0-glib-2.0 : Depends: libgirepository1.0-1 (>= 0.9.3) but it is not going to be installed
 python-gobject : Depends: libgirepository1.0-1 (>= 0.6.14) but it is not going to be installed
 python-gobject-cairo : Depends: libgirepository1.0-1 (>= 0.6.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


It doesn't matter what I do I cant seem to get rid of this message any suggestions?

---

### Post by Harry33 on 2010-08-12
> **GraemeLockett said:**
> 
The following packages have unmet dependencies:
 gir1.0-glib-2.0 : Depends: libgirepository1.0-1 (>= 0.9.3) but it is not going to be installed
 python-gobject : Depends: libgirepository1.0-1 (>= 0.6.14) but it is not going to be installed
 python-gobject-cairo : Depends: libgirepository1.0-1 (>= 0.6.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Gnome-shell is broken at the moment in maverick. A number of packages are rebuilt against the new gobject-introspection (0.93).
But package gnome-shell is missing right now. The old gnome-shell_2.31.2-1ubuntu1 cannot be installed on to the new upgraded maverick.

Your problem is also about the gobject-introspection.
It contains three packages: gir1.0-freedesktop, gir1.0-glib-2.0 and libgirepository1.0-1.
The latter is a new one and it conflicts the old one (libgirepository1.0-0). You must remove the old package.

You should not use Rico's PPA at the moment at all. It contains only some of GS packages and no gnome-shell at all.
Wait until maverick gets updated and use Gnome-panel meanwhile.

---

### Post by davideotape on 2010-08-12
Hmm, next error I'm getting is

```
make[2]: *** No rule to make target `ug.gmo', needed by `all-yes'. Stop.
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk3/po-properties'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/21]
```

---

### Post by sgage on 2010-08-12
Does anyone know if/when Rico's ppa will have the full set of gnome-shell files?

---

### Post by gotjazz on 2010-08-12
anyone else getting the following at the end while building gnome-shell itself? ```
 CC     libtray_la-na-tray-child.lo
cc1: warnings being treated as errors
tray/na-tray-child.c: In function &#8216;na_tray_child_new&#8217;:
tray/na-tray-child.c:268: error: implicit declaration of function &#8216;gdk_screen_get_rgb_visual&#8217;
tray/na-tray-child.c:268: error: comparison between pointer and integer
tray/na-tray-child.c:269: error: implicit declaration of function &#8216;gdk_screen_get_rgb_colormap&#8217;
tray/na-tray-child.c:269: error: assignment makes pointer from integer without a cast

```

---

### Post by magcius on 2010-08-12
> **davideotape said:**
> Hmm, next error I'm getting is

```
make[2]: *** No rule to make target `ug.gmo', needed by `all-yes'. Stop.
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk3/po-properties'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/21]
```

cd ~/gnome-shell/source/gtk3 && cp po/ug.po po-properties/

> **gotjazz said:**
> anyone else getting the following at the end while building gnome-shell itself? ```
 CC     libtray_la-na-tray-child.lo
cc1: warnings being treated as errors
tray/na-tray-child.c: In function &#8216;na_tray_child_new&#8217;:
tray/na-tray-child.c:268: error: implicit declaration of function &#8216;gdk_screen_get_rgb_visual&#8217;
tray/na-tray-child.c:268: error: comparison between pointer and integer
tray/na-tray-child.c:269: error: implicit declaration of function &#8216;gdk_screen_get_rgb_colormap&#8217;
tray/na-tray-child.c:269: error: assignment makes pointer from integer without a cast

```

Yes. gtk+ just went through a big API break. We're getting patches ready and hopefully things should work tomorrow. Hopefully. There haven't been that many changes if you already have a built copy.


To those using ricotz's PPA: don't. He isn't updating it anymore. It screws up your system in ways I don't understand (APT dependency problems). It's old, will be old, and won't work.

---

### Post by sgage on 2010-08-12
"To those using ricotz's PPA: don't. He isn't updating it anymore. It screws up your system in ways I don't understand (APT dependency problems). It's old, will be old, and won't work."

If this is true, then some sort of announcement needs to be made, because there are several articles out there regarding gnome-shell that point to his PPA. There will be lots of confused and disappointed people...

---

### Post by magcius on 2010-08-12
It is best not to use any distribution packages from now on, until release of gnome3. Please, please, please use jhbuild.

Why?

[quote=old explanation, ignore this]
gnome-shell requires gtk3. gtk3 has an API and API break. A very extreme one from now on.

A system-wide installation of gtk3 is going to break. Break bad. Break hard.

jhbuild does sandboxing with a bunch of environment hacks to make sure that gtk3 only runs for gnome-shell and a couple other things. It never touches your system libraries, it installs into a separate prefix.
[/quote]

Yes, things are broken right now with building from jhbuild. This is the API/ABI break I mentioned. It should hopefully be cleared up tomorrow.

EDIT: looks like libgtk has been renamed to libgtk-x11-3.0.so after the break. So, yeah, my bad, a recent PPA should work fine.

It looks like ricotz' PPA has been updated sometime today, but does not include all the libraries that are needed. The jhbuild dependencies were just updated to cairo 1.9.14 to fix a rendering problem. There's about 14 or 15 other dependencies that we require. jhbuild will do the right thing. ricotz may not update the dependencies for several days.

Nothing against ricotz. I'm not saying he's unable, or unwilling, I'm saying that jhbuild is automatic, and ricotz is human. Same goes for any other system package maintainer.

---

### Post by Harry33 on 2010-08-13
> **magcius said:**
> 
It looks like ricotz' PPA has been updated sometime today, but does not include all the libraries that are needed. The jhbuild dependencies were just updated to cairo 1.9.14 to fix a rendering problem. There's about 14 or 15 other dependencies that we require. jhbuild will do the right thing. ricotz may not update the dependencies for several days.

Nothing against ricotz. I'm not saying he's unable, or unwilling, I'm saying that jhbuild is automatic, and ricotz is human. Same goes for any other system package maintainer.

Building GS with jhbuild works if source is in working condition.

But using a PPA (like Rico's) will only work when and as long as it is fully compatible with maverick's most recent upgrades/updates. And because a lot of gnome packages will be rebuilt and upgraded quite often now, they will possibly break GS from any PPA as well.
If you demand that Rico should be able keep the GS in his PPA in working order, he would have to rebuilt almost whole gnome at the same time as mavericks official packages are rebuilt.

The package gnome-shell is missing from maverick's repos right now, because there is no one around to rebuilt all the time and follow these ABI breaks.

---

### Post by davideotape on 2010-08-13
Next error I'm getting is in gtk-engines-3:

```
  CC     clearlooks_style.lo
./src/clearlooks_style.c: In function ‘clearlooks_style_draw_box’:
./src/clearlooks_style.c:775: warning: #warning Assuming non-pulsing progress bars because there is currently no way to query them in GTK+ 3.0.
./src/clearlooks_style.c: In function ‘clearlooks_style_draw_layout’:
./src/clearlooks_style.c:1796: error: ‘GdkGC’ undeclared (first use in this function)
./src/clearlooks_style.c:1796: error: (Each undeclared identifier is reported only once
./src/clearlooks_style.c:1796: error: for each function it appears in.)
./src/clearlooks_style.c:1796: error: ‘gc’ undeclared (first use in this function)
./src/clearlooks_style.c:1801: error: ‘GtkStyle’ has no member named ‘text_gc’
./src/clearlooks_style.c:1801: error: ‘GtkStyle’ has no member named ‘fg_gc’
./src/clearlooks_style.c:1808: error: ‘old_gc’ undeclared (first use in this function)
make[2]: *** [clearlooks_style.lo] Error 1
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk-engines/engines/clearlooks'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk-engines/engines'
make: *** [all-recursive] Error 1
*** Error during phase build of gtk-engines-3: ########## Error running make   *** [10/21]

```

---

### Post by sgage on 2010-08-13
OK, here's the result of my last attempt to compile:

make[3]: Entering directory `/home/sgage/gnome-shell/source/librsvg/gtk-engine'
  CC     libsvg_la-svg-draw.lo
  CC     libsvg_la-svg-main.lo
  CC     libsvg_la-svg-render.lo
  CC     libsvg_la-svg-rc-style.lo
  CCLD   libsvg.la
  CC     libsvg_3_la-svg-draw.lo
  CC     libsvg_3_la-svg-main.lo
  CC     libsvg_3_la-svg-render.lo
svg-render.c: In function ‘pixbuf_render’:
svg-render.c:430: warning: implicit declaration of function ‘gdk_draw_pixbuf’
svg-render.c:430: warning: nested extern declaration of ‘gdk_draw_pixbuf’
svg-render.c:434: error: ‘GDK_RGB_DITHER_NORMAL’ undeclared (first use in this function)
svg-render.c:434: error: (Each undeclared identifier is reported only once
svg-render.c:434: error: for each function it appears in.)
svg-render.c: In function ‘theme_pixbuf_render’:
svg-render.c:831: error: ‘GdkGC’ undeclared (first use in this function)
svg-render.c:831: error: ‘tmp_gc’ undeclared (first use in this function)
svg-render.c:832: error: ‘GdkGCValues’ undeclared (first use in this function)
svg-render.c:832: error: expected ‘;’ before ‘gc_values’
svg-render.c:838: warning: implicit declaration of function ‘gdk_gc_new’
svg-render.c:838: warning: nested extern declaration of ‘gdk_gc_new’
svg-render.c:843: error: ‘GDK_RGB_DITHER_NORMAL’ undeclared (first use in this function)
svg-render.c:847: error: ‘gc_values’ undeclared (first use in this function)
svg-render.c:847: error: ‘GDK_TILED’ undeclared (first use in this function)
svg-render.c:849: warning: implicit declaration of function ‘gdk_gc_new_with_values’
svg-render.c:849: warning: nested extern declaration of ‘gdk_gc_new_with_values’
svg-render.c:850: error: ‘GDK_GC_FILL’ undeclared (first use in this function)
svg-render.c:850: error: ‘GDK_GC_TILE’ undeclared (first use in this function)
svg-render.c:852: warning: implicit declaration of function ‘gdk_draw_rectangle’
svg-render.c:852: warning: nested extern declaration of ‘gdk_draw_rectangle’
make[3]: *** [libsvg_3_la-svg-render.lo] Error 1
make[3]: Leaving directory `/home/sgage/gnome-shell/source/librsvg/gtk-engine'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/librsvg/gtk-engine'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/librsvg'
make: *** [all] Error 2
*** Error during phase build of librsvg: ########## Error running make   *** [9/21]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


Is this something that I just wait for new code to come along?

---

### Post by NightwishFan on 2010-08-13
I can confirm being unable to build gtk-engines-3 and librsvg. I have no solution as of late.

---

### Post by sgage on 2010-08-13
NightwishFan,

Thanks for corroborating. I am hoping it's just part of the GTK api changes mentioned up-thread and will soon resolve itself.

---

### Post by moore.bryan on 2010-08-13
On a side-note, does anyone know if there's been movement on the different background on each workspace with GS?

Also, could someone weigh-in on the relative benefits of building on Lucid vs. using the PPA?

Thanks, in-advance.

---

### Post by magcius on 2010-08-15
I do have an librsvg patch, but I don't have anybody who can apply it for me.

Here are the patches you need to apply:

mutter  -- [https://bugzilla.gnome.org/show_bug.cgi?id=626583](https://bugzilla.gnome.org/show_bug.cgi?id=626583)
librsvg -- [https://bugzilla.gnome.org/show_bug.cgi?id=626605](https://bugzilla.gnome.org/show_bug.cgi?id=626605)

With gtk-engines-3 you can choose 'give up on this module' or apply all the patches in this bug. Most
of the direct Gdk call patching is in a lot of old themes that are, uh, old, like Raleigh and crux and so on.

gtk-engines-3 -- [https://bugzilla.gnome.org/show_bug.cgi?id=626678](https://bugzilla.gnome.org/show_bug.cgi?id=626678) (optional)

It's easiest to patch these guys with git-bz.

To get git-bz:

```

sudo curl http://git.fishsoup.net/cgit/git-bz/plain/git-bz > /usr/lib/git-core/git-bz && chmod +x !#:4

```

Apply the patches:

```

cd ~/gnome-shell/source/gtk-engines
yes | git bz apply 626678
cd ~/gnome-shell/source/mutter
yes | git bz apply 626583
cd ~/gnome-shell/source/librsvg
yes | git bz apply 626605

```

Rebuild.

---

### Post by sgage on 2010-08-15
Thanks magcius!

Unfortunately, bugzilla.gnome.org is not responding this morning, but I'll keep trying. I am very curious to get GS compiled - it's been a while since I've tested it, and I know it's come a long way...

---

### Post by magcius on 2010-08-15
Yeah, the rack at RH that hosts a large portion of gnome infrastructure is down, along with several other RH/Fedora sites.

---

### Post by sgage on 2010-08-15
Yes, I see now that gnome.org is completely offline. Oh well, I must be patient... I'll try again later.

---

### Post by autocrosser on 2010-08-15
> **magcius said:**
> I do have an librsvg patch, but I don't have anybody who can apply it for me.

Here are the patches you need to apply:

mutter  -- [https://bugzilla.gnome.org/show_bug.cgi?id=626583](https://bugzilla.gnome.org/show_bug.cgi?id=626583)
librsvg -- [https://bugzilla.gnome.org/show_bug.cgi?id=626605](https://bugzilla.gnome.org/show_bug.cgi?id=626605)

With gtk-engines-3 you can choose 'give up on this module' or apply all the patches in this bug. Most
of the direct Gdk call patching is in a lot of old themes that are, uh, old, like Raleigh and crux and so on.

gtk-engines-3 -- [https://bugzilla.gnome.org/show_bug.cgi?id=626678](https://bugzilla.gnome.org/show_bug.cgi?id=626678) (optional)

It's easiest to patch these guys with git-bz.

To get git-bz:

```

sudo curl http://git.fishsoup.net/cgit/git-bz/plain/git-bz > /usr/lib/git-core/git-bz && chmod +x !#:4

```Apply the patches:

```

cd ~/gnome-shell/source/gtk-engines
yes | git bz apply 626678
cd ~/gnome-shell/source/mutter
yes | git bz apply 626583
cd ~/gnome-shell/source/librsvg
yes | git bz apply 626605

```Rebuild.

The site is back upright now......Only problem is that I'm getting a "permission denied" when I run the sudo curl fetch for git-bz.....```
sudo curl http://git.fishsoup.net/cgit/git-bz/plain/git-bz > /usr/lib/git-core/git-bz && chmod +x !#:4
``` Is that code correct?

---

### Post by magcius on 2010-08-15
> **autocrosser said:**
> The site is back upright now......Only problem is that I'm getting a "permission denied" when I run the sudo curl fetch for git-bz.....```
sudo curl http://git.fishsoup.net/cgit/git-bz/plain/git-bz > /usr/lib/git-core/git-bz && chmod +x !#:4
``` Is that code correct?

If it's giving an error, mind pasting it? WFM.

---

### Post by autocrosser on 2010-08-15
I just hand-installed git-bz & got the patches done--building now....we'll see how it goes.

---

### Post by sgage on 2010-08-15
Well, for me, now the compile pukes on gconf.

Someone please post here when there is a compilable set of code. I've tried my best to get everything patched and good, but no joy.

---

### Post by autocrosser on 2010-08-15
Several errors--I forced it thru--but not pretty.......

```
*** Checking out librsvg *** [9/21]
git pull --rebase
It looks like git-am is in progress. Cannot rebase.
*** Error during phase checkout of librsvg: ########## Error running git pull --rebase *** [9/21]

  [1] Rerun phase checkout
  [2] Ignore error and continue to configure
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"

```This was the worst one......


Well--it's a non-run right now...guess I'll wait for a day or so.....

---

### Post by magcius on 2010-08-15
git-am is in progress.

That usually means the patch didn't apply.

```

cd ~/gnome-shell/source/librsvg && git am --abort

```

---

### Post by Jazz11 on 2010-08-15
mutter not building, bz patch not working...
any cure?

---

### Post by chenxiaolong on 2010-08-15
I also can't get mutter to compile:

```
  CC     workspace.o
  CC     xprops.o
  CC     fixedtip.o
  CC     frames.o
cc1: warnings being treated as errors
ui/frames.c: In function &#8216;setup_bg_cr&#8217;:
ui/frames.c:2014: error: implicit declaration of function &#8216;gdk_window_get_back_pixmap&#8217;
ui/frames.c:2014: error: nested extern declaration of &#8216;gdk_window_get_back_pixmap&#8217;
ui/frames.c:2031: error: implicit declaration of function &#8216;gdk_window_get_background&#8217;
ui/frames.c:2031: error: nested extern declaration of &#8216;gdk_window_get_background&#8217;
make[4]: *** [frames.o] Error 1
make[4]: Leaving directory `/home/goudouyaosi/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/goudouyaosi/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/goudouyaosi/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/goudouyaosi/gnome-shell/source/mutter'
make: *** [all] Error 2
***** Error during phase build of mutter: ########## Error running make   *** [14/21]**

```

Seems like there are still some gdk functions that didn't get patched to use cairo.

---

### Post by Jazz11 on 2010-08-16
mutter can be compiled now..

delete git-bz in /usr/lib/git-core/ 
again :
sudo curl [http://git.fishsoup.net/cgit/git-bz/plain/git-bz](http://git.fishsoup.net/cgit/git-bz/plain/git-bz) > /usr/lib/git-core/git-bz && chmod +x !#:4
cd ~/gnome-shell/source/mutter
yes | git bz apply 626583


then,

cd gnome-shell/install/lib
rm -rf *.la
jhbuild buildone gnome-shell -acf

rebuild.

---

### Post by chenxiaolong on 2010-08-16
Awesome! That worked. I got my first gnome-shell compilation working :D.

---

### Post by sgage on 2010-08-16
Well, I'm at the point where it compiles all the way down to gnome-shell itself, 20/21, and it starts throwing "undefined references". The first post says to remove the .la files, but then it complains about them being missing. Is there anything I can do to drive this thing through to completion?

---

### Post by magcius on 2010-08-16
Paste the error message.

There's a few things that could cause undefined references right now.

---

### Post by sgage on 2010-08-16
It goes like this:

make[3]: Entering directory `/home/sgage/gnome-shell/source/gnome-shell/src'
  CCLD   test-theme
/home/sgage/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/sgage/gnome-shell/install/lib/libclutter-glx-1.0.so: undefined reference to `g_object_notify_by_pspec'
/home/sgage/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/sgage/gnome-shell/install/lib/libclutter-glx-1.0.so: undefined reference to `g_source_set_name'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [20/21]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice:

---

### Post by Mblackwell on 2010-08-16
Quick guess that you previously had GS installed via PPA?

---

### Post by magcius on 2010-08-16
You say you have removed all the .la files?

In all of /usr/lib, /usr/lib64 and ~/gnome-shell/install/lib?

Oh, and ppa-purge ricotz's PPA too.

---

### Post by Mblackwell on 2010-08-16
Then also sudo apt-get remove gnome-shell (because it will replace the ppa version with the repo version which is also wrong).

---

### Post by 4leite on 2010-08-16
I was getting the same error message as chenxiaolong. Removed la files as per magcius suggestion. I also had gnome-shell installed via ppa, ppa-purge did not work, but I *think* I have managed to manually remove it. Now receiving the following error message:
```
libtool: link: gcc -std=gnu99 -shared  .libs/imam-et.o   -Wl,-rpath -Wl,/home/jon/gnome-shell/source/gtk3/gdk/.libs -Wl,-rpath -Wl,/home/jon/gnome-shell/source/gtk3/gtk/.libs -Wl,-rpath -Wl,/home/jon/gnome-shell/install/lib64 -Wl,-rpath -Wl,/home/jon/gnome-shell/install/lib64 -L/home/jon/gnome-shell/install/lib64 ../../gdk/.libs/libgdk-x11-3.0.so ../../gtk/.libs/libgtk-x11-3.0.so /home/jon/gnome-shell/install/lib64/libpangocairo-1.0.so -lX11 -lXcomposite -lXdamage -lXfixes /home/jon/gnome-shell/install/lib64/libatk-1.0.so /home/jon/gnome-shell/install/lib64/libcairo.so /home/jon/gnome-shell/install/lib64/libgdk_pixbuf-2.0.so -lm -lpng12 /home/jon/gnome-shell/install/lib64/libgio-2.0.so /home/jon/gnome-shell/install/lib64/libpangoft2-1.0.so /home/jon/gnome-shell/install/lib64/libpango-1.0.so -lfreetype -lfontconfig /home/jon/gnome-shell/install/lib64/libgobject-2.0.so /home/jon/gnome-shell/install/lib64/libgmodule-2.0.so /home/jon/gnome-shell/install/lib64/libgthread-2.0.so -lrt /home/jon/gnome-shell/install/lib64/libglib-2.0.so  -pthread   -pthread -Wl,-soname -Wl,im-am-et.so -o .libs/im-am-et.so
/bin/sed: can't read /usr/lib/libfreetype.la: No such file or directory
libtool: link: `/usr/lib/libfreetype.la' is not a valid libtool archive
make[3]: *** [im-am-et.la] Error 1
make[3]: Leaving directory `/home/jon/gnome-shell/source/gtk3/modules/input'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jon/gnome-shell/source/gtk3/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jon/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/21]

```

---

### Post by magcius on 2010-08-17
You need to rebuild everything.

Probably best to delete the installation folder (~/gnome-shell/install)

Otherwise libtool et al will hold on to the old .la files.

---

### Post by 4leite on 2010-08-17
Cheers for help so far... I'm going to leave it for the day with the following error:

```
ui/frames.c: In function &#8216;setup_bg_cr&#8217;:
ui/frames.c:2014: error: implicit declaration of function &#8216;gdk_window_get_back_pixmap&#8217;
ui/frames.c:2014: error: nested extern declaration of &#8216;gdk_window_get_back_pixmap&#8217;
ui/frames.c:2031: error: implicit declaration of function &#8216;gdk_window_get_background&#8217;
ui/frames.c:2031: error: nested extern declaration of &#8216;gdk_window_get_background&#8217;
make[4]: *** [frames.o] Error 1
make[4]: Leaving directory `/home/jon/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jon/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/jon/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jon/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [14/21]

```

---

### Post by magcius on 2010-08-17
> **magcius said:**
> You need to rebuild everything.

Probably best to delete the installation folder (~/gnome-shell/install)

Otherwise libtool et al will hold on to the old .la files.

> **4leite said:**
> Cheers for help so far... I'm going to leave it for the day with the following error:

```
ui/frames.c: In function ‘setup_bg_cr’:
ui/frames.c:2014: error: implicit declaration of function ‘gdk_window_get_back_pixmap’
ui/frames.c:2014: error: nested extern declaration of ‘gdk_window_get_back_pixmap’
ui/frames.c:2031: error: implicit declaration of function ‘gdk_window_get_background’
ui/frames.c:2031: error: nested extern declaration of ‘gdk_window_get_background’
make[4]: *** [frames.o] Error 1
make[4]: Leaving directory `/home/jon/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jon/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/jon/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jon/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [14/21]

```

See the instructions a page or earlier about applying the patches from bugzilla.

In fmueller's latest patch, he screwed up a GTK+ version check.

This should fix it:

```
sed -i.bak 's/GTK_VERSION/GTK_CHECK_VERSION/' ~/gnome-shell/source/mutter/src/ui/frames.c
```

If you get patch errors, cd to the module and git reset --hard origin.

---

### Post by tanmays on 2010-08-17
> **magcius said:**
> I do have an librsvg patch, but I don't have anybody who can apply it for me.

Here are the patches you need to apply:

mutter  -- [https://bugzilla.gnome.org/show_bug.cgi?id=626583](https://bugzilla.gnome.org/show_bug.cgi?id=626583)
librsvg -- [https://bugzilla.gnome.org/show_bug.cgi?id=626605](https://bugzilla.gnome.org/show_bug.cgi?id=626605)

With gtk-engines-3 you can choose 'give up on this module' or apply all the patches in this bug. Most
of the direct Gdk call patching is in a lot of old themes that are, uh, old, like Raleigh and crux and so on.

gtk-engines-3 -- [https://bugzilla.gnome.org/show_bug.cgi?id=626678](https://bugzilla.gnome.org/show_bug.cgi?id=626678) (optional)

It's easiest to patch these guys with git-bz.

To get git-bz:

```

sudo curl http://git.fishsoup.net/cgit/git-bz/plain/git-bz > /usr/lib/git-core/git-bz && chmod +x !#:4

```

Apply the patches:

```

cd ~/gnome-shell/source/gtk-engines
yes | git bz apply 626678
cd ~/gnome-shell/source/mutter
yes | git bz apply 626583
cd ~/gnome-shell/source/librsvg
yes | git bz apply 626605

```

Rebuild.

I have build gnome-shell under Linux Mint 9 (Ubuntu 10.04) following these instruction. But it seems very slow and crashes most of the time.

Previously I had built it 2 weeks before when it was fast and usable. But this time I think its not usable for me.

Hope things to get better in future :)

---

### Post by tanmays on 2010-08-17
I have just updated Chromium browser to Version 7.0.497. Whenever I try to type in the address bar of chromium browser, Gnome-shell restarts. Seems like a bug !!!

However, for the time being Gnome-shell is pretty useless for me due to restarts and crashes.

---

### Post by sgage on 2010-08-17
Hello all, and thanks for all the help so far!

Anyway, I never installed the PPA GS on this system, but I did install the stock repo version, and deleted it before embarking on this project.

I did in fact delete all the .la files from both /usr/lib and ~/gnome-shell/install/lib. Everything was going along fine until gnome-shell (20/21) started complaining about not finding the .la files. I copied them back in one by one as gnome-shell "asked" for them, and finally got the "undefined reference" errors posted above.

So near, and yet so far! What next?

---

### Post by sgage on 2010-08-17
Well, I deleted ~/gnome-shell, made sure all .la files were deleted, and started over. Applied the librsvg and mutter patches successfully. Things were cruising along nicely until:

treeset.c: In function ‘gee_tree_set_range_init’:
treeset.c:2675: warning: assignment discards qualifiers from pointer target type
treeset.c:2676: warning: assignment discards qualifiers from pointer target type
treeset.c: In function ‘gee_tree_set_range_init_head’:
treeset.c:2689: warning: assignment discards qualifiers from pointer target type
treeset.c: In function ‘gee_tree_set_range_init_tail’:
treeset.c:2699: warning: assignment discards qualifiers from pointer target type
treeset.c: In function ‘gee_tree_set_range_cut’:
treeset.c:2791: warning: assignment discards qualifiers from pointer target type
treeset.c:2798: warning: assignment discards qualifiers from pointer target type
  CCLD   libgee.la
/home/sgage/gnome-shell/install/bin/g-ir-compiler --shared-library=libgee -o Gee-1.0.typelib Gee-1.0.gir
Gee-1.0.gir:2035:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2102:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2295:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2441:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2481:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2730:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2766:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2873:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3114:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3288:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3414:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3738:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3782:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3801:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4016:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4176:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4473:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4513:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4653:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4656:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4672:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:5042:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:5055:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir: error: Type reference 'EqualDataFunc' not found
make[2]: *** [Gee-1.0.typelib] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/libgee/gee'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/libgee'
make: *** [all] Error 2
*** Error during phase build of libgee: ########## Error running make   *** [17/21]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


Now what?

---

### Post by magcius on 2010-08-17
> **sgage said:**
> Hello all, and thanks for all the help so far!

Anyway, I never installed the PPA GS on this system, but I did install the stock repo version, and deleted it before embarking on this project.

I did in fact delete all the .la files from both /usr/lib and ~/gnome-shell/install/lib. Everything was going along fine until gnome-shell (20/21) started complaining about not finding the .la files. I copied them back in one by one as gnome-shell "asked" for them, and finally got the "undefined reference" errors posted above.

So near, and yet so far! What next?

Paste the exact error messages?

re: slowness

The slowness is our fault: we're creating a bunch of FBOs, which is inherently expensive, but significantly worse on nVidia.

You can revert commit 0905 in gnome-shell if you want to go back to where it was before.
> **sgage said:**
> Well, I deleted ~/gnome-shell, made sure all .la files were deleted, and started over. Applied the librsvg and mutter patches successfully. Things were cruising along nicely until:

treeset.c: In function ‘gee_tree_set_range_init’:
treeset.c:2675: warning: assignment discards qualifiers from pointer target type
treeset.c:2676: warning: assignment discards qualifiers from pointer target type
treeset.c: In function ‘gee_tree_set_range_init_head’:
treeset.c:2689: warning: assignment discards qualifiers from pointer target type
treeset.c: In function ‘gee_tree_set_range_init_tail’:
treeset.c:2699: warning: assignment discards qualifiers from pointer target type
treeset.c: In function ‘gee_tree_set_range_cut’:
treeset.c:2791: warning: assignment discards qualifiers from pointer target type
treeset.c:2798: warning: assignment discards qualifiers from pointer target type
  CCLD   libgee.la
/home/sgage/gnome-shell/install/bin/g-ir-compiler --shared-library=libgee -o Gee-1.0.typelib Gee-1.0.gir
Gee-1.0.gir:2035:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2102:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2295:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2441:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2481:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2730:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2766:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:2873:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3114:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3288:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3414:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3738:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3782:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:3801:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4016:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4176:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4473:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4513:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4653:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4656:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:4672:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:5042:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir:5055:1: warning: dropping to PASSTHROUGH
Gee-1.0.gir: error: Type reference 'EqualDataFunc' not found
make[2]: *** [Gee-1.0.typelib] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/libgee/gee'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/libgee'
make: *** [all] Error 2
*** Error during phase build of libgee: ########## Error running make   *** [17/21]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


Now what?

Verified myself with a build here.

---

### Post by sgage on 2010-08-17
I just successfully completed a compile... 

Still needed the librsvg and mutter patches, but it compiled to completion.

Now to explore a bit...

Thanks, everyone!

---

### Post by autocrosser on 2010-08-17
So, assuming a clean build (delete everything & start fresh)---what is needing to be patched/modified to have a good build?

Any idea when the files will be updated so a run can be made without patching files?

---

### Post by ranch hand on 2010-08-17
> **autocrosser said:**
> So, assuming a clean build (delete everything & start fresh)---what is needing to be patched/modified to have a good build?

Any idea when the files will be updated so a run can be made without patching files?
I would like to know this too.   I would really like to put it back on one of my installs.

I also, certainly, do not like it well enough to fight with it.

I have 3 installs that I could put it on.  No deletions needed as GS has never been on them.  Anytime the bugger will build I will put it on here.

---

### Post by tanmays on 2010-08-18
> **4leite said:**
> Cheers for help so far... I'm going to leave it for the day with the following error:

```
ui/frames.c: In function ‘setup_bg_cr’:
ui/frames.c:2014: error: implicit declaration of function ‘gdk_window_get_back_pixmap’
ui/frames.c:2014: error: nested extern declaration of ‘gdk_window_get_back_pixmap’
ui/frames.c:2031: error: implicit declaration of function ‘gdk_window_get_background’
ui/frames.c:2031: error: nested extern declaration of ‘gdk_window_get_background’
make[4]: *** [frames.o] Error 1
make[4]: Leaving directory `/home/jon/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jon/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/jon/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jon/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [14/21]

```

Same error for me today. :(

---

### Post by tanmays on 2010-08-18
I am encountering the following error :

> CC     default_la-default.lo
CCLD   default.la
/bin/sed: can't read /usr/lib/libfreetype.la: No such file or directory
libtool: link: `/usr/lib/libfreetype.la' is not a valid libtool archive
make[4]: *** [default.la] Error 1
make[4]: Leaving directory `/home/tanmay/gnome-shell/source/mutter/src/compositor/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tanmay/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tanmay/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tanmay/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [14/21]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 

What to do ?

---

### Post by sgage on 2010-08-18
Here's what I did to successfully compile yesterday:

I backed up and deleted all the .la files in /usr/lib.

Delete ~/gnome-shell/install

Applied the patches posted by magcius a few pages back:

"It's easiest to patch these guys with git-bz.

To get git-bz:

Code:

sudo curl [http://git.fishsoup.net/cgit/git-bz/plain/git-bz](http://git.fishsoup.net/cgit/git-bz/plain/git-bz) > /usr/lib/git-core/git-bz && chmod +x !#:4

Apply the patches:

Code:

cd ~/gnome-shell/source/gtk-engines
yes | git bz apply 626678
cd ~/gnome-shell/source/mutter
yes | git bz apply 626583
cd ~/gnome-shell/source/librsvg
yes | git bz apply 626605"

Actually, I did not have to apply the gtk-engines patch.

If you have deleted your entire gnome-shell directory to start fresh, you'll have to wait until the process fails during mutter/librsvg, so the source will have been downloaded so you can patch it.

After doing these things, it compiled!

---

### Post by sgage on 2010-08-18
I just completed a fresh compile from scratch (deleted my entire gnome-shell directory). The issue with mutter seems to have been addressed in the source - the only patch I had to apply was the librsvg patch.

---

### Post by tanmays on 2010-08-18
Complied fresh and jhbuild finished without any error.

But gnome-shell crashes everytime I try to type something in a browser window.

The following error is repeatedly displayed in the terminal :

> (gnome-panel:2801): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-panel:2801): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed



> 
(gnome-panel:2884): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

What to do?

---

### Post by sgage on 2010-08-18
That's a new one on me.

I'd just wait a bit and try again. You didn't get the librsvg error? That's the last one left for me...

---

### Post by ktp on 2010-08-18
> **ranch hand said:**
> I would like to know this too.   I would really like to put it back on one of my installs.

I also, certainly, do not like it well enough to fight with it.

I have 3 installs that I could put it on.  No deletions needed as GS has never been on them.  Anytime the bugger will build I will put it on here.

you might be waiting for while at this rate =)  I don't mind fighting the build but this is becoming really hard to keep up.  Maybe time to get one good build and wait for while.

---

### Post by ranch hand on 2010-08-18
> **ktp said:**
> you might be waiting for while at this rate =)  I don't mind fighting the build but this is becoming really hard to keep up.  Maybe time to get one good build and wait for while.
I can understand that.  I just have never liked what I saw when I got it up.

I do want to see where it is now and where it may be going but I am not going to waste time on it.   I do have some confidence that they will get it straightened out.

The kernel keeps changing and the big xorg change can not have been the easiest thing to work through.  I would say that is probably the problem with the ppa too.

This thread is very interesting and I enjoy following it.  I just do not think it worth the hassle at this time.

---

### Post by 4leite on 2010-08-19
finally!

*** success *** [21/21]

cheers magcius et al

---

### Post by NightwishFan on 2010-08-19
Librsvg still fails for me, however I used "jhbuild buildone" on gnome-shell and mutter and the shell launches.

---

### Post by magcius on 2010-08-19
librsvg is the only patch you need to apply.

I've tried to contact people to apply the patch upstream. I failed. I'll keep trying.

It's not under active development, and I wish there was a replacement, because it's very slow.

---

### Post by youoh on 2010-08-19
just finished building successfully without any patches.

one annoying thing: sometimes gnome-shell crashes when using dropdown boxes in Chromium.

---

### Post by tanmays on 2010-08-19
Installed Ubuntu 10.10 Alpha 3. Installed Gnome-Shell 2.31.5 from the ubuntu repository.

Now GS don't load with the following message:

> (mutter:1766): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libmozjs.so: cannot open shared object file: No such file or directory)]

Pressing Ctrl+C crashes the Terminal.

---

### Post by tanmays on 2010-08-19
> **youoh said:**
> just finished building successfully without any patches.

one annoying thing: sometimes gnome-shell crashes when using dropdown boxes in Chromium.

Same happened to me previously. Typing in the address bar of chromium always crashed GS.

---

### Post by magcius on 2010-08-19
Please, please, please, don't use gnome-shell from the ubuntu repos NOR ricotz's PPA. They are old, and won't work.

Use jhbuild as outlined in the first post. You will need a patch for librsvg: unfortunately, I can't get it upstream, I've tried. I will try some more, but none of the maintainers are reachable.

Do this after you get a build error for librsvg when using jhbuild:

```

cd ~/gnome-shell/source/librsvg
yes | git bz apply 626605

```

And then choose option 1: Rerun phase build.

Merk42: mind adding these instructions to the OP, along with fixing your formatting?

---

### Post by ranch hand on 2010-08-19
OK, I'll bite.  What is Ctrl+C supposed to do?

I am only familiar with -c to clear the history.

---

### Post by autocrosser on 2010-08-19
> **magcius said:**
> Please, please, please, don't use gnome-shell from the ubuntu repos NOR ricotz's PPA. They are old, and won't work.

Use jhbuild as outlined in the first post. You will need a patch for librsvg: unfortunately, I can't get it upstream, I've tried. I will try some more, but none of the maintainers are reachable.

Do this after you get a build error for librsvg when using jhbuild:

```

cd ~/gnome-shell/source/librsvg
yes | git bz apply 626605

```And then choose option 1: Rerun phase build.

Merk42: mind adding these instructions to the OP, along with fixing your formatting?


OK--That went clean---now I get a build error in gjs:```
*** Building gjs *** [15/21]
make  
make  all-am
make[1]: Entering directory `/home/dean/gnome-shell/source/gjs'
/bin/bash ./libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I.   -pthread -DXP_UNIX -DJS_THREADSAFE -I/home/dean/gnome-shell/install/include/glib-2.0 -I/home/dean/gnome-shell/install/lib64/glib-2.0/include -I/usr/include/xulrunner-1.9.2.8 -I/usr/include/xulrunner-1.9.2.8/nspr -I/usr/include/nspr    -DGJS_TOP_SRCDIR=\".\" -DGJS_JS_DIR=\"/home/dean/gnome-shell/install/share/gjs-1.0\" -DGJS_NATIVE_DIR=\"/home/dean/gnome-shell/install/lib64/gjs-1.0\"   -Wfloat-equal -Wsign-compare -Wcast-align -Wpointer-arith -Wnested-externs -Wmissing-prototypes -Wmissing-declarations -Wchar-subscripts -Wall -g -O2 -MT libgjs_la-jsapi-private.lo -MD -MP -MF .deps/libgjs_la-jsapi-private.Tpo -c -o libgjs_la-jsapi-private.lo `test -f 'gjs/jsapi-private.cpp' || echo './'`gjs/jsapi-private.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -pthread -DXP_UNIX -DJS_THREADSAFE -I/home/dean/gnome-shell/install/include/glib-2.0 -I/home/dean/gnome-shell/install/lib64/glib-2.0/include -I/usr/include/xulrunner-1.9.2.8 -I/usr/include/xulrunner-1.9.2.8/nspr -I/usr/include/nspr -DGJS_TOP_SRCDIR=\".\" -DGJS_JS_DIR=\"/home/dean/gnome-shell/install/share/gjs-1.0\" -DGJS_NATIVE_DIR=\"/home/dean/gnome-shell/install/lib64/gjs-1.0\" -Wfloat-equal -Wsign-compare -Wcast-align -Wpointer-arith -Wnested-externs -Wmissing-prototypes -Wmissing-declarations -Wchar-subscripts -Wall -g -O2 -MT libgjs_la-jsapi-private.lo -MD -MP -MF .deps/libgjs_la-jsapi-private.Tpo -c gjs/jsapi-private.cpp  -fPIC -DPIC -o .libs/libgjs_la-jsapi-private.o
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from gjs/jsapi-private.cpp:30:
gjs/jsapi-util.h:28: warning: #warning Include <gjs/gjs.h> instead of <gjs/jsapi-util.h>
In file included from gjs/context-jsapi.h:27,
                 from gjs/jsapi-private.cpp:32:
./gjs/context.h:28: warning: #warning Include <gjs/gjs.h> instead of <gjs/context.h>
In file included from /usr/include/xulrunner-1.9.2.8/jsatom.h:53,
                 from /usr/include/xulrunner-1.9.2.8/jscntxt.h:49,
                 from gjs/jsapi-private.cpp:35:
/usr/include/xulrunner-1.9.2.8/jslock.h:47: fatal error: pratom.h: No such file or directory
compilation terminated.
make[1]: *** [libgjs_la-jsapi-private.lo] Error 1
make[1]: Leaving directory `/home/dean/gnome-shell/source/gjs'
make: *** [all] Error 2
*** Error during phase build of gjs: ########## Error running make   *** [15/21]

```
looks like a "new" patch is in order?  I can pass that error & finish the build & it will run OK....

---

### Post by NightwishFan on 2010-08-19
Ctrl+C in a terminal is a interrupt signal to kill the current task.

---

### Post by ranch hand on 2010-08-20
> **NightwishFan said:**
> Ctrl+C in a terminal is a interrupt signal to kill the current task.
Well, thanks a bunch.

That will be handy the next time I screw up and give the wrong command when update/upgrading in chroot instead of killing the terminal.

That is one handy little thing to know.

---

### Post by Harry33 on 2010-08-20
> **ranch hand said:**
> Well, thanks a bunch.
That will be handy the next time I screw up and give the wrong command when update/upgrading in chroot instead of killing the terminal.

Actually Ctrl+C does not kill the terminal.
It kills the application started in the terminal.
So, if you start gnome-shell in terminal (gnome-shell --replace), you can quit GS by hitting Ctrl+C in terminal.

---

### Post by ranch hand on 2010-08-20
Yes, I understood that.  It is just great.

Had a buggered command (not a great typest) and used it to get back to the proper prompt.

I can't use it with GS as I do not have GS installed.   I will wait for it to settle down to a buildable state before plying with it.

---

### Post by Harry33 on 2010-08-20
> **tanmays said:**
> Installed Ubuntu 10.10 Alpha 3. Installed Gnome-Shell 2.31.5 from the ubuntu repository.
Now GS don't load with the following message:
    (mutter:1766): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libmozjs.so: cannot open shared object file: No such file or directory)]

Pressing Ctrl+C crashes the Terminal.

That mutter warning is like it says. It cannot find mozilla javascript spider monkey = libmozjs.so
This is the launchpad bug #576991, still unresolved.

You can workaround it though, by creating a symlink in the folder /usr/lib/ which points to /usr/lib/xulrunner-1.9.2.8/libmozjs.so
or
simply copying the libmozjs.so file into the folder /usr/lib/

---

### Post by Harry33 on 2010-08-20
> **ranch hand said:**
> 

...

I can't use it with GS as I do not have GS installed.   I will wait for it to settle down to a buildable state before plying with it.

OK fine.
You can, however, install GS directly from Mavericks official repos. It works very well now.
And yet, install also the package gnome3-session. Then you can choose in the login screen (gdm) to start gnome3 (gnome-shell) or ubuntu desktop environment (gnome-panel).
This is very handy, because if future updates break GS, then you can start gnome-panel instead.

The only issue is that gnome-shell does not find libmozjs.so because of the bug #576991.
But I just posted an easy workaround above.

---

### Post by ranch hand on 2010-08-20
Is the repo version close to current?  I know that it was way behind at one time and I assume it still is.

I am good at being wrong about these things though.

---

### Post by Harry33 on 2010-08-20
> **ranch hand said:**
> Is the repo version close to current?  I know that it was way behind at one time and I assume it still is.
I am good at being wrong about these things though.

You are right about GS in repo being somewhat behind.
On the other hand, it is not that buggy.

Anyway, the biggest difference is that mavericks GS has been built against GTK+2.0. Well, using GTK+3.0 would break all the other gnome packages for sure.
As of today there are etc.
- gnome-shell_2.31.5-2ubuntu1
- gjs_0.71-1ubuntu1 with ligjs0a
- gobject introspection v. 0.9.3-0ubuntu4 with libgirepository1.0-1
- mutter_2.31.5-0ubuntu3.1
- clutter-1.0_1.2.12-0ubuntu8

---

### Post by Merk42 on 2010-08-20
> **magcius said:**
> Merk42: mind adding these instructions to the OP, along with fixing your formatting?

What formatting needs to be fixed?

---

### Post by tanmays on 2010-08-21
> **Harry33 said:**
> That mutter warning is like it says. It cannot find mozilla javascript spider monkey = libmozjs.so
This is the launchpad bug #576991, still unresolved.

You can workaround it though, by creating a symlink in the folder /usr/lib/ which points to /usr/lib/xulrunner-1.9.2.8/libmozjs.so
or
simply copying the libmozjs.so file into the folder /usr/lib/

Thanks.

It worked flawlessly.

Now using it as default for my desktop.

However I could not type anything in the Alt+F2 window and Application Search Box  !!!

SOLVED: Seems like an iBus problem. Turning off iBus worked.

---

### Post by tanmays on 2010-08-21
Here is a screenshot of my Gnome-shell desktop:

It uses Elementary theme by Sean W

> Link : [http://half-left.deviantart.com/#/d2vktxy](http://half-left.deviantart.com/#/d2vktxy)

---

### Post by ranch hand on 2010-08-21
Thanks for the screen shot.  Looks an awful lot better than the last time I had it on here.

That theme isn't too bad either.  I do not go for the gray but I think even I could change that to some thing I liked better.

Not to hot on the whole GS thing at all but the ease of modifying  or changing a theme is just great.

---

### Post by moore.bryan on 2010-08-21
Maybe not formatting, but perhaps the directions could be updated to include all the patching?

---

### Post by ktp on 2010-08-21
I can't wait to see this in action:

[http://live.gnome.org/GnomeShell/Design/Whiteboards/OverviewWindowDND](http://live.gnome.org/GnomeShell/Design/Whiteboards/OverviewWindowDND)

[http://live.gnome.org/GnomeShell/Design/Whiteboards/](http://live.gnome.org/GnomeShell/Design/Whiteboards/)

---

### Post by autocrosser on 2010-08-21
Well--I've got a build running---one error that "seems" to be non-fatal, but causes a gjs non-build....```
*** Checking out gjs *** [15/21]
git pull --rebase
Current branch master is up to date.
*** Building gjs *** [15/21]
make  
make  all-am
make[1]: Entering directory `/home/dean/gnome-shell/source/gjs'
/bin/bash ./libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I.   -pthread -DXP_UNIX -DJS_THREADSAFE -I/home/dean/gnome-shell/install/include/glib-2.0 -I/home/dean/gnome-shell/install/lib64/glib-2.0/include -I/usr/include/xulrunner-1.9.2.8 -I/usr/include/xulrunner-1.9.2.8/nspr -I/usr/include/nspr    -DGJS_TOP_SRCDIR=\".\" -DGJS_JS_DIR=\"/home/dean/gnome-shell/install/share/gjs-1.0\" -DGJS_NATIVE_DIR=\"/home/dean/gnome-shell/install/lib64/gjs-1.0\"   -Wfloat-equal -Wsign-compare -Wcast-align -Wpointer-arith -Wnested-externs -Wmissing-prototypes -Wmissing-declarations -Wchar-subscripts -Wall -g -O2 -MT libgjs_la-jsapi-private.lo -MD -MP -MF .deps/libgjs_la-jsapi-private.Tpo -c -o libgjs_la-jsapi-private.lo `test -f 'gjs/jsapi-private.cpp' || echo './'`gjs/jsapi-private.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -pthread -DXP_UNIX -DJS_THREADSAFE -I/home/dean/gnome-shell/install/include/glib-2.0 -I/home/dean/gnome-shell/install/lib64/glib-2.0/include -I/usr/include/xulrunner-1.9.2.8 -I/usr/include/xulrunner-1.9.2.8/nspr -I/usr/include/nspr -DGJS_TOP_SRCDIR=\".\" -DGJS_JS_DIR=\"/home/dean/gnome-shell/install/share/gjs-1.0\" -DGJS_NATIVE_DIR=\"/home/dean/gnome-shell/install/lib64/gjs-1.0\" -Wfloat-equal -Wsign-compare -Wcast-align -Wpointer-arith -Wnested-externs -Wmissing-prototypes -Wmissing-declarations -Wchar-subscripts -Wall -g -O2 -MT libgjs_la-jsapi-private.lo -MD -MP -MF .deps/libgjs_la-jsapi-private.Tpo -c gjs/jsapi-private.cpp  -fPIC -DPIC -o .libs/libgjs_la-jsapi-private.o
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from gjs/jsapi-private.cpp:30:
gjs/jsapi-util.h:28: warning: #warning Include <gjs/gjs.h> instead of <gjs/jsapi-util.h>
In file included from gjs/context-jsapi.h:27,
                 from gjs/jsapi-private.cpp:32:
./gjs/context.h:28: warning: #warning Include <gjs/gjs.h> instead of <gjs/context.h>
In file included from /usr/include/xulrunner-1.9.2.8/jsatom.h:53,
                 from /usr/include/xulrunner-1.9.2.8/jscntxt.h:49,
                 from gjs/jsapi-private.cpp:35:
/usr/include/xulrunner-1.9.2.8/jslock.h:47: fatal error: pratom.h: No such file or directory
compilation terminated.
make[1]: *** [libgjs_la-jsapi-private.lo] Error 1
make[1]: Leaving directory `/home/dean/gnome-shell/source/gjs'
make: *** [all] Error 2
*** Error during phase build of gjs: ########## Error running make   *** [15/21]
```I've looked at the files it makes reference to & 4 of them do not even exist in my xulrunner-1.9.2.8-dev---the jslock.h file looks like:```
#ifndef jslock_h__
#define jslock_h__

#include "jstypes.h"
#include "jsprvtd.h"    /* for JSScope, etc. */
#include "jspubtd.h"    /* for JSRuntime, etc. */

#ifdef JS_THREADSAFE
# include "pratom.h"
# include "prlock.h"
# include "prcvar.h"
# include "prthread.h"
#endif
```This is lines 39 thru 51 in jslock.h---problem is that the files pratom.h, prlock.h, prcvar.h & prthread.h do not exist......

Ideas anyone?

---

### Post by moore.bryan on 2010-08-21
I'm trying to jhbuild GS, but am having some problems. I previously used the PPA version on my Lucid machine with no issues until this afternoon, when it just wouldn't load. I hadn't even run an upgrade or anything.

Regardless, I ran ppa-purge on the Ricotz repo, thinking that would downgrade all the important packages. Then, I followed the instructions on the GNOME website for GS. It stuck on 2/21, trying to make gobject-introspection. Doing some research, I found it might be caused by non-downgraded packages. When I fired-up Synaptic and searched for versions containing "ricotz," imagine my surprise at finding all the following packages were still the PPA version: gconf-defaults-service, gconf2, gconf2-common, gobject-introspection, gtk2-engines-pixbuf, libatk1.0-0, libatk1.0-data, libatk1.0-dev, libclutter1.0-0, libdconf0, libgail-common, libgail18, libgconf2-4, libgconf2-dev, libgirepository1.0-0, libglib2.0-0, libglib2.0-bin, libglib2.0-data, libglib2.0-dev, libgtk2.0-0, libgtk2.0-bin, libgtk2.0-common, libgtk2.0-dev, libjson-glib-1.0-0, libmutter-private0, libpango1.0-0, libpango1.0-common, libpango1.0-dev, libwnck-common, libwnck-dev, libwnck22, mutter, mutter-common.

So, I began to mark each of them for downgrade, but when I got to gconf2-common, it wanted to--basically--remove every damn package.

What's the deal? How can I downgrade those packages without doing a complete reinstall and fix my system so I can jhbuild?

---

### Post by autocrosser on 2010-08-21
You will need to do a PPA purge---I got PPA-Purge from the Xorg-edgers PPA, but the purge works for any PPA--Info: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

You can add the edgers PPA to your source list, just get PPA-purge & then un-enable edgers again....explanation on using purge is in edgers info.....

EDIT: Looks like you can get purge from the swat PPA also--safer PPA to use & easier to disable.... [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)  You still need to read the purge usage in the edgers PPA....

---

### Post by lesnoland on 2010-08-22
I have built it finally after adding those patches, but its REALLY slow.

According to gnome people you need to do this, in order to get rid of the SLOWNESS:

```
cd ~/gnome-shell/source/gnome-shell/; git revert 0905940ef84cc4943873a4615eb495a0a103c942; jhbuild build -n
```

---

### Post by Harry33 on 2010-08-22
> **moore.bryan said:**
> 
...
When I fired-up Synaptic and searched for versions containing "ricotz," imagine my surprise at finding all the following packages were still the PPA version: gconf-defaults-service, gconf2, gconf2-common, gobject-introspection, gtk2-engines-pixbuf, libatk1.0-0, libatk1.0-data, libatk1.0-dev, libclutter1.0-0, libdconf0, libgail-common, libgail18, libgconf2-4, libgconf2-dev, libgirepository1.0-0, libglib2.0-0, libglib2.0-bin, libglib2.0-data, libglib2.0-dev, libgtk2.0-0, libgtk2.0-bin, libgtk2.0-common, libgtk2.0-dev, libjson-glib-1.0-0, libmutter-private0, libpango1.0-0, libpango1.0-common, libpango1.0-dev, libwnck-common, libwnck-dev, libwnck22, mutter, mutter-common.

So, I began to mark each of them for downgrade, but when I got to gconf2-common, it wanted to--basically--remove every damn package.

What's the deal? How can I downgrade those packages without doing a complete reinstall and fix my system so I can jhbuild?

If ppa-purge does not work and the packages you listed are in the filesystem of lucid, here is what you can do to downgrade the packages you cannot remove (like gtk2-0 and gconf).

First start lucid (the gnome-panel session, ubuntu desktop edition).
Download from launchpad the newest official packages. You can search from here (64-bit): [https://launchpad.net/ubuntu/lucid/amd64](https://launchpad.net/ubuntu/lucid/amd64)

To downgrade gtk2.0 (2.20.1-0ubuntu2), download all six packages:
- gir1.0-gtk-2.0
- gtk2-engines-pixbuf
- ligail18
- libgtk2.0-0
- libgtk2.0-bin
- libgtk2.0-common

To downgrade gconf (2.28.1-0ubuntu1), download all five packages:
- gconf-defaults-service
- gconf2
- gconf2-common
- gir1.0-gconf-2.0
- libgconf2-4

Then in terminal, use dpkg and downgrade all dependant packages at the same time (use the full package name):

sudo dpkg -i gconf-defaults-service_2.28.1-0ubuntu1_amd64.deb package2 ...

You see synaptic cannot resolve the dependencies when multiple packages are concerned.

---

### Post by ronjouch on 2010-08-22
Hi there,

If that helps somebody, GS compiles as of today 2010/08/22 on an up-to-date Maverick. I followed [http://live.gnome.org/GnomeShell#Building](http://live.gnome.org/GnomeShell#Building) , plus:
[LIST]
[*]jhbuild autoinstalls lots of packages but seems to miss two, so ```
sudo apt-get install autopoint liborbit2-dev
```
[*]apply libsrvg patch #626605 mentioned on [http://ubuntuforums.org/showthread.php?p=9724017](http://ubuntuforums.org/showthread.php?p=9724017)
[/LIST]
As mentioned before in this post, don't use any PPA, it won't work, will kill three kittens and will screw your packages state; use jhbuild.

---

### Post by moore.bryan on 2010-08-22
> **autocrosser said:**
> You will need to do a PPA purge---I got PPA-Purge from the Xorg-edgers PPA, but the purge works for any PPA--Info: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

You can add the edgers PPA to your source list, just get PPA-purge & then un-enable edgers again....explanation on using purge is in edgers info.....

EDIT: Looks like you can get purge from the swat PPA also--safer PPA to use & easier to disable.... [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)  You still need to read the purge usage in the edgers PPA....

> **Harry33 said:**
> If ppa-purge does not work and the packages you listed are in the filesystem of lucid, here is what you can do to downgrade the packages you cannot remove (like gtk2-0 and gconf).

First start lucid (the gnome-panel session, ubuntu desktop edition).
Download from launchpad the newest official packages. You can search from here (64-bit): [https://launchpad.net/ubuntu/lucid/amd64](https://launchpad.net/ubuntu/lucid/amd64)

To downgrade gtk2.0 (2.20.1-0ubuntu2), download all six packages:
- gir1.0-gtk-2.0
- gtk2-engines-pixbuf
- ligail18
- libgtk2.0-0
- libgtk2.0-bin
- libgtk2.0-common

To downgrade gconf (2.28.1-0ubuntu1), download all five packages:
- gconf-defaults-service
- gconf2
- gconf2-common
- gir1.0-gconf-2.0
- libgconf2-4

Then in terminal, use dpkg and downgrade all dependant packages at the same time (use the full package name):

sudo dpkg -i gconf-defaults-service_2.28.1-0ubuntu1_amd64.deb package2 ...

You see synaptic cannot resolve the dependencies when multiple packages are concerned.

Thanks, guys, but my system was so borked I had to do a clean install of everything... trying to compile now.

Thanks, again...

---

### Post by ktp on 2010-08-22
> **moore.bryan said:**
> Thanks, guys, but my system was so borked I had to do a clean install of everything... trying to compile now.

Thanks, again...

sometimes fresh start is not a bad idea. =)

---

### Post by moore.bryan on 2010-08-22
> **ktp said:**
> sometimes fresh start is not a bad idea. =)
Sage advice!

Now, I'm having a problem applying patches... I tried to curl git-bz, but I get this:
```
bash: /usr/lib/git-core/git-bz: Permission denied
```
Huh?

EDIT

Never mind, I just manually installed and--I think--I applied the patch. We'll see.

---

### Post by moore.bryan on 2010-08-22
I'm getting the dconf error now... and I didn't see a "fix" in this thread; rather, it seemed to just "go away" for anyone. Any ideas?
```


make[1]: Entering directory `/home/bryan/gnome-shell/source/dconf/gsettings'
  CC     dconfsettingsbackend.o
cc1: warnings being treated as errors
dconfsettingsbackend.c: In function ‘dconf_settings_backend_get_bus’:
dconfsettingsbackend.c:384: error: passing argument 2 of ‘g_dbus_connection_add_filter’ from incompatible pointer type
/home/bryan/gnome-shell/install/include/glib-2.0/gio/gdbusconnection.h:494: note: expected ‘GDBusMessageFilterFunction’ but argument is of type ‘gboolean (*)(struct GDBusConnection *, struct GDBusMessage *, gboolean,  void *)’
dconfsettingsbackend.c:403: error: passing argument 2 of ‘g_dbus_connection_add_filter’ from incompatible pointer type
/home/bryan/gnome-shell/install/include/glib-2.0/gio/gdbusconnection.h:494: note: expected ‘GDBusMessageFilterFunction’ but argument is of type ‘gboolean (*)(struct GDBusConnection *, struct GDBusMessage *, gboolean,  void *)’
make[1]: *** [dconfsettingsbackend.o] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/dconf/gsettings'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/21]

```

---

### Post by sgage on 2010-08-22
I'm getting the dconf error too. I find that ignoring it and going to the next module then goes to completion, and the resulting GS seems to work normally.

---

### Post by moore.bryan on 2010-08-22
> **sgage said:**
> I'm getting the dconf error too. I find that ignoring it and going to the next module then goes to completion, and the resulting GS seems to work normally.

I'm trying that now... wonder why the error is there for some of us and not others. Are you, by any chance, running Maverick or Lucid?

---

### Post by sgage on 2010-08-22
I am running Maverick. I compiled yesterday with no dconf error, so go figure! Still need that librsvg patch, though...

---

### Post by moore.bryan on 2010-08-22
> **sgage said:**
> I am running Maverick. I compiled yesterday with no dconf error, so go figure! Still need that librsvg patch, though...
I haven't even tried building on my Maverick install, yet. And now I'm getting the gnome-shell build error on 20/21 that seems to have gone away for everyone but me...

---

### Post by moore.bryan on 2010-08-22
Just over two-and-one-half hours later and everything compiled fine, save for the dconf errors, but it won't start:
```


bryan@blue-asus:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Starting dconf-service... ** Message: Attempting to migrate ~/.config/dconf to ~/.config/dconf/user
** Message: Successful.
 started
Failed to start shell
Traceback (most recent call last):
  File "./gnome-shell", line 768, in <module>
    
  File "./gnome-shell", line 320, in run_shell
    
  File "./gnome-shell", line 268, in start_shell
    
  File "./gnome-shell", line 193, in _get_glx_extensions
    
  File "/usr/lib/python2.6/subprocess.py", line 633, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1139, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
bryan@blue-asus:~/gnome-shell/source/gnome-shell/src$ Cannot register the panel shell: there is already one running.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
bryan@blue-asus:~/gnome-shell/source/gnome-shell/src$ WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```
Ideas?

---

### Post by mixint27 on 2010-08-22
*** Building libgee *** [17/21]
make  
 cd . && /bin/bash /home/tony/gnome-shell/source/libgee/missing --run automake-1.11 --gnu
gee/Makefile.am:85: HAVE_INTROSPECTION does not appear in AM_CONDITIONAL
Makefile.am:3: NULL multiply defined in condition TRUE ...
Makefile.decl:11: ... `NULL' previously defined here
Makefile.am:1:   `Makefile.decl' included from here
make: *** [Makefile.in] Error 1
*** Error during phase build of libgee: ########## Error running make   *** [17/21]

what should i do here? please help. thanks.

---

### Post by autocrosser on 2010-08-22
> **moore.bryan said:**
> Just over two-and-one-half hours later and everything compiled fine, save for the dconf errors, but it won't start:
```


bryan@blue-asus:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Starting dconf-service... ** Message: Attempting to migrate ~/.config/dconf to ~/.config/dconf/user
** Message: Successful.
 started
Failed to start shell
Traceback (most recent call last):
  File "./gnome-shell", line 768, in <module>
    
  File "./gnome-shell", line 320, in run_shell
    
  File "./gnome-shell", line 268, in start_shell
    
  File "./gnome-shell", line 193, in _get_glx_extensions
    
  File "/usr/lib/python2.6/subprocess.py", line 633, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1139, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
bryan@blue-asus:~/gnome-shell/source/gnome-shell/src$ Cannot register the panel shell: there is already one running.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
bryan@blue-asus:~/gnome-shell/source/gnome-shell/src$ WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```Ideas?


Hmmm---what video driver are you using?

---

### Post by tanmays on 2010-08-23
I am using the Maverik Alpha 3 Repo Gnome Shell since 3 days. It works fine and no crashes/restarts till date.

The GS version is 2.31.5

What is the version of recent GS available on git?

---

### Post by tanmays on 2010-08-23
The mockups at [http://live.gnome.org/GnomeShell/Design/Whiteboards/](http://live.gnome.org/GnomeShell/Design/Whiteboards/) looks quite promising. I am really excited about Gnome 3

---

### Post by frustphil on 2010-08-23
> **tanmays said:**
> The mockups at [http://live.gnome.org/GnomeShell/Design/Whiteboards/](http://live.gnome.org/GnomeShell/Design/Whiteboards/) looks quite promising. I am really excited about Gnome 3

I wonder what happens if too many icons are on the left sidebar. Will it shrink or what? I would love to see unity launcher integrated into gnome shell but I can't imagine how.

---

### Post by moore.bryan on 2010-08-23
> **autocrosser said:**
> Hmmm---what video driver are you using?

i915, xorg-video-intel.

---

### Post by moore.bryan on 2010-08-23
@autocrosser: Your train of thinking got me thinking, so I purged **any** and **all** xorg-video-* that weren't my Intel one, started my GS build from scratch, and... voila, it works. I still get the same error I mentioned above, but it seems to no longer be fatal.

Oh, and for the record, I think I may be in-love with GS; I found myself hating the "default" desktop.

EDIT

Does anyone else out there have GS crap-out on them randomly and then come-back?

---

### Post by moore.bryan on 2010-08-23
> **tanmays said:**
> Same happened to me previously. Typing in the address bar of chromium always crashed GS.

Any fix to this?

---

### Post by ktp on 2010-08-23
> **frustphil said:**
> I wonder what happens if too many icons are on the left sidebar. Will it shrink or what? I would love to see unity launcher integrated into gnome shell but I can't imagine how.

I wouldn't hold my breath on that.

---

### Post by tanmays on 2010-08-24
> **moore.bryan said:**
> Any fix to this?

The repo version of Maverick works fine... the build version gave me that error.

---

### Post by moore.bryan on 2010-08-24
> **tanmays said:**
> The repo version of Maverick works fine... the build version gave me that error.
Sorry, I was specifically asking about my build on my Lucid install... besides, I thought we "weren't supposed" to use the Maverick repo version because it was busted; is it working again?

---

### Post by sgage on 2010-08-24
I just tried the Maverick repo version, and it works fine, plus it's much snappier than my compiled version. Not sure how old a version it is, but it seems a lot more recent than the ancient Lucid version.

---

### Post by plun on 2010-08-24
> **sgage said:**
> I just tried the Maverick repo version, and it works fine, plus it's much snappier than my compiled version. Not sure how old a version it is, but it seems a lot more recent than the ancient Lucid version.

About Mavericks package

> gnome-shell (2.31.5-2ubuntu1) maverick; urgency=low

  * Merge from debian experimental. Remaining changes:
    - debian/patches/04_workaround_libmozjs_build.patch:
      + workaround build issues due to libmozjs not being installed as a lib
  * Drop debian/patches/01_favorite_apps.diff: Keep firefox as default browser

 -- Laurent Bigonville <bigon@ubuntu.com>  **Mon, 16 Aug 2010 21:24:15 +0200**

[http://packages.ubuntu.com/maverick/gnome-shell](http://packages.ubuntu.com/maverick/gnome-shell)


---

### Post by sgage on 2010-08-24
Thanks for the info, plun, and the reminder on how to find info about packages.

---

### Post by moore.bryan on 2010-08-24
This may be an academic question, but can someone explain the logic of jhbuild using /home/<user> instead of putting GS into /opt? I try to keep my /home tidy and building GS leaves "junk" all over the place. Is it safe to delete those dirs after building?

---

### Post by ranch hand on 2010-08-24
As this is a testing version of GS it makes sense to have those files where you have permission to do as you please with them.

---

### Post by moore.bryan on 2010-08-24
> **ranch hand said:**
> As this is a testing version of GS it makes sense to have those files where you have permission to do as you please with them.

That makes sense, but I know Ubuntu used to (at least, I remember it with Warty) use /opt for that. What's the purpose of /opt then?

---

### Post by ranch hand on 2010-08-24
If you are installing a stable app /opt makes sense, you probably do not need to mess with the files at all.

---

### Post by mojo on 2010-08-24
The default maverick gnome-shell works fine for me except the Search box in Activities doesn't work, I get errors in console:

```


mojo@mojo:~/Sites/spree-skat*****$ gnome-shell --replace
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
      JS LOG: GNOME Shell started at Wed Aug 25 2010 08:39:21 GMT+1000 (EST)
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
Error loading document: Error opening file: No such file or directory
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
      JS LOG: Command line: /usr/bin/gjs-console
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4d368f4 (About Apta)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4c000be (Ruby - spr)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument


```

Is it just me or anyone having the same issue?

---

### Post by NightwishFan on 2010-08-24
I still am unable to launch the shell in Maverick. I have this bug occur.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/623548](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/623548)

---

### Post by mixint27 on 2010-08-25
> **mixint27 said:**
> *** Building libgee *** [17/21]
make  
 cd . && /bin/bash /home/tony/gnome-shell/source/libgee/missing --run automake-1.11 --gnu
gee/Makefile.am:85: HAVE_INTROSPECTION does not appear in AM_CONDITIONAL
Makefile.am:3: NULL multiply defined in condition TRUE ...
Makefile.decl:11: ... `NULL' previously defined here
Makefile.am:1:   `Makefile.decl' included from here
make: *** [Makefile.in] Error 1
*** Error during phase build of libgee: ########## Error running make   *** [17/21]

what should i do here? please help. thanks.

bump!

---

### Post by moore.bryan on 2010-08-25
I *just* rebuilt without *any* errors and without using the librsvg patch. Is it too soon to hope!?
;-)

---

### Post by plun on 2010-08-25
> **NightwishFan said:**
> I still am unable to launch the shell in Maverick. I have this bug occur.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/623548](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/623548)


Just add a symlink and it works
```

sudo ln -s /usr/lib/xulrunner-1.9.2.8/libmozjs.so  /usr/lib/
```

---

### Post by NightwishFan on 2010-08-25
Thanks Plun!

Also:

[QUOTE="Gnome Shell Git"]The librsvg theme engine uses now-gone GTK+ drawing functions so doesn't compile with GTK+ 3. Since we don't need the theme engine anyways, skip bulding it. [/QUOTE]

---

### Post by sgage on 2010-08-25
> **moore.bryan said:**
> I *just* rebuilt without *any* errors and without using the librsvg patch. Is it too soon to hope!?
;-)


Hey, me too! Compiled without a hitch, and runs fine. Though it still seems slow. the place where this mostly bothers me is hitting the magic corner - unless the response to hitting the hot corner is nearly instantaneous, my work flow in GS isn't really comfortable.

The (Maverick) repo version seems much snappier to me.

---

### Post by seeker5528 on 2010-08-25
> **moore.bryan said:**
> That makes sense, but I know Ubuntu used to (at least, I remember it with Warty) use /opt for that. What's the purpose of /opt then?

[http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES](http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES)

If you had multiple users on your box that wanted to try GS, then '/opt/*packagename*/' or /usr/local/' would be the place to put them. If you are the only user on your box that will be using GS, it seems like a waste of time to install it to a location outside of your home directory.

Later, Seeker

---

### Post by moore.bryan on 2010-08-26
> **sgage said:**
> Hey, me too! Compiled without a hitch, and runs fine. Though it still seems slow. the place where this mostly bothers me is hitting the magic corner - unless the response to hitting the hot corner is nearly instantaneous, my work flow in GS isn't really comfortable.

The (Maverick) repo version seems much snappier to me.
I still need to install on my Maverick install... looking forward to it now!

> **seeker5528 said:**
> [http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES](http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES)

If you had multiple users on your box that wanted to try GS, then '/opt/*packagename*/' or /usr/local/' would be the place to put them. If you are the only user on your box that will be using GS, it seems like a waste of time to install it to a location outside of your home directory.

Later, Seeker
Do "we" (whomever that is) assume Ubuntu is only being set-up for one user or do the GNOME developers only suggest to build GNOME Shell for testing purposes? I just find it strange everything happens in /home.

Now, I've run into a new problem and need to file a bug report... when I go to the overview, it fails to show my desktop background and, instead, goes all white. When I come back out of overview, everything's fine, though. Strange...

---

### Post by autocrosser on 2010-08-26
> **moore.bryan said:**
> I still need to install on my Maverick install... looking forward to it now!


Do "we" (whomever that is) assume Ubuntu is only being set-up for one user or do the GNOME developers only suggest to build GNOME Shell for testing purposes? I just find it strange everything happens in /home.

Now, I've run into a new problem and need to file a bug report... when I go to the overview, it fails to show my desktop background and, instead, goes all white. When I come back out of overview, everything's fine, though. Strange...

When you are testing GS the "assumed" mode is one user. so installing to /home is fine. When it is released for real, I would say that it will be installed in the usual places......running it from /home right now makes it easier to fix when it b0rks up......

Reports need to goto Gnome bugzilla, so you will need to make a account there & look at reports.......

---

### Post by moore.bryan on 2010-08-26
> **autocrosser said:**
> When you are testing GS the "assumed" mode is one user. so installing to /home is fine. When it is released for real, I would say that it will be installed in the usual places......running it from /home right now makes it easier to fix when it b0rks up......
I guess that was my original point: how's /home any easier than /opt? I was always under the impression /opt was for self-installed programs; wrong for me to assume that.

> Reports need to goto Gnome bugzilla, so you will need to make a account there & look at reports.......
Already have an account and reported bug... thanks, though.

---

### Post by ranch hand on 2010-08-26
> **moore.bryan said:**
> I guess that was my original point: how's /home any easier than /opt? I was always under the impression /opt was for self-installed programs; wrong for me to assume that.


Already have an account and reported bug... thanks, though.
In your home directory you do not need to be root.  It is easier to fix.

---

### Post by ranch hand on 2010-08-26
Now that you have the ability to build the bugger I may try it.

Just have to ask about this.  I installed the repo version on one of my throw away OS' (10.10).  It does not work at all.  Just freezes the box solid when I attempt to switch to it.  Is the build going to work any better in with any likely hood?

I would think that although the repo version may be behind it should have some possibility that it works.  Hopefully more than the build would.

---

### Post by sgage on 2010-08-26
The Maverick repo version of GS is quite recent, and works fine on my machine, and is faster than the locally compiled version.

---

### Post by ranch hand on 2010-08-26
This is a real drag then as I really wanted to get this up and compare it to Uninty.

Can't get either to work.  Well Unity works better.  Box does not freeze solid.  It flashes from white screen to wallpaper and back very fast.  TTy works to get out.

Oh well, just have to wait.  They are installed.  Just a matter of waiting until an update fixes them.

---

### Post by seeker5528 on 2010-08-26
> **moore.bryan said:**
> Do "we" (whomever that is) assume Ubuntu is only being set-up for one user or do the GNOME developers only suggest to build GNOME Shell for testing purposes?

There would be some exceptions due to the way some things work, but generally speaking I would expect just about any developer to only suggest building something that is in heavy development for testing purposes only. 

Also generally speaking, it should be suggested that anything that you are not quite sure about should be installed in your home directory instead of a system wide location. 

This may not do heaps for your own personal security and data protection, but should minimize the ability of the software in question to act on locations that you as a user don't have direct access to.

If you had a directory in your home directory named 'test' with 'test/bin/' for executables, then you could create a '.xprofile' file in your home directory with a line like...

```
export PATH="~/test/bin/:$PATH"
```

if you want the executables to be in your path when you log in to an X session.

Later, Seeker

---

### Post by ktp on 2010-08-26
> **moore.bryan said:**
> I guess that was my original point: how's /home any easier than /opt? I was always under the impression /opt was for self-installed programs; wrong for me to assume that.

If you know what you are doing then /home and /opt are same...just a folder.  But in general, [opt is for non-default software installs]("http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html"), like you said.  

For this, I like to think this is something you are developing and/or "playing around" so I would like to think of it as just keeping things in the "bin" directory to build, run, and test code as I develop.  Now this "bin" can be whatever you want it to be and is easy for you.

---

### Post by moore.bryan on 2010-08-26
> **ktp said:**
> For this, I like to think this is something you are developing and/or "playing around"
I think that's the point I was making... I was always under the impression that was what /opt was for. Mea culpa. Thanks for indulging me, guys; we can get back to the real work of getting the kinks out of GS! :-)

---

### Post by autocrosser on 2010-08-26
Yes---fun stuff---I just like going in & modding the files without mucking around with root every time--simpler=better/easier......

Also, if I need to move to my backup install--I can just grab files & move them.....I do the same with my BOINC install--much easier than mucking with stuff in /opt........

---

### Post by Harry33 on 2010-08-27
> **ranch hand said:**
> This is a real drag then as I really wanted to get this up and compare it to Uninty.

Can't get either to work.  Well Unity works better.  Box does not freeze solid.  It flashes from white screen to wallpaper and back very fast.  TTy works to get out.

Oh well, just have to wait.  They are installed.  Just a matter of waiting until an update fixes them.

Ranch hand,

What exactly you mean by "freeze solid".
Could you try to start GS in terminal:
gnome-shell --replace
and then post here the error messages.

Maverick's GS does really work well now (in a fully updated maverick).
But you have to tell gnome-shell where the file libmozjs.so is located.
That is why you have to make a symlink in the folder /usr/lib/

Like this:
sudo ln -s /usr/lib/xulrunner-1.9.2.8/libmozjs.so  /usr/lib/

---

### Post by vivek40 on 2010-08-27
Hii I am trying to use gnome-shell on my lucid.I installed it using this:-
sudo apt-get install gnome-shell
However when i run it using gnome-shell --replace. I get the following error at the terminal.. please help
[HTML]
Cannot register the panel shell: there is already one running.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
[/HTML]

---

### Post by phenest on 2010-08-27
I'm using the repo (not ppa) version of GS. If I have 2 workspaces and drag Thunderbird to one, and Firefox to the other, they both end up being started in the same workspace. Rather than opening in the workspace it was dragged to, it's opening in the active workspace. Does this still happen in the latest version too, or should it be reported as a bug?

EDIT: This has been reported: [bug 604514]("https://bugzilla.gnome.org/show_bug.cgi?id=604514")

---

### Post by ranch hand on 2010-08-27
> **Harry33 said:**
> Ranch hand,

What exactly you mean by "freeze solid".
Could you try to start GS in terminal:
gnome-shell --replace
and then post here the error messages.

Maverick's GS does really work well now (in a fully updated maverick).
But you have to tell gnome-shell where the file libmozjs.so is located.
That is why you have to make a symlink in the folder /usr/lib/

Like this:
sudo ln -s /usr/lib/xulrunner-1.9.2.8/libmozjs.so  /usr/lib/
I would be most happy to post that information if I had it.

When I boot to the normal Ubuntu desktop and run "gnome-shell --replace" the terminal
disappears (although the workspace switchers still shows it) and the only thing that will work is to unplug my box to get out.  Tty does not work.  Alt + SysRq + b does not work.

This is what I would call a total freeze.

Are you saying that GS will not run without xulrunner?  Or just Mozilla stuff will not run under GS without that fix?

I admit that I have not done that and was over on that install today and all I did was check that the regular Ubuntu ran with the newest updates.  Never checked GS (or Unity) as none of the upgrades seemed to have anything to do with them.  Was figuring on seeing about those things this evening when checking the upgrades from then.

---

### Post by Harry33 on 2010-08-27
> **ranch hand said:**
> 
...
Are you saying that GS will not run without xulrunner?  Or just Mozilla stuff will not run under GS without that fix?
...

Yes, GS package depends on xulrunner.
And to be more specific, it is the package libgjs0a, that is depending on xulrunner. You cannot install it without xulrunner.

The file libmozjs.so is Mozilla's javascript spidermonkey and GS wont run without it. You see, most if not all the settings in GS are written in javascript.

---

### Post by ranch hand on 2010-08-27
> **Harry33 said:**
> Yes, GS package depends on xulrunner.
And to be more specific, it is the package libgjs0a, that is depending on xulrunner. You cannot install it without xulrunner.

The file libmozjs.so is Mozilla's javascript spidermonkey and GS wont run without it. You see, most if not all the settings in GS are written in javascript.
Of coarse.  I should have thought of that.  I will be over there this evening and will make that link.

I will then give it another whack.  Might even work.

I will then report on my success.

---

### Post by ranch hand on 2010-08-27
Well that really helped.

Booted to the OS with the repo version of GS installed.  Ran;
```

sudo ln -s /usr/lib/xulrunner-1.9.2.8/libmozjs.so /usr/lib/

```
This allowed GS to start before my system froze.

Got the top panel and my wallpaper.  Cursor would move.  Nothing worked using the mouse.

Tty2 would not allow me to "startx"  as program startx not installed.  Rebooted to gnome desktop and here I am.

I am using the edgers drivers on this OS and nothing seems to work as far as GS is concerned.

At least now it works as well as Unity.

Improvement is just a matter of time I am sure.  Will continue to monitor.

Have not been able to use GS since 2 weeks before 10.04-testing ended.  I have no idea how to file a bug on this as I have no idea what the problem is.

---

### Post by Harry33 on 2010-08-28
> **ranch hand said:**
> 
...
Tty2 would not allow me to "startx"  as program startx not installed.  Rebooted to gnome desktop and here I am.

I am using the edgers drivers on this OS and nothing seems to work as far as GS is concerned.

At least now it works as well as Unity.

Improvement is just a matter of time I am sure.  Will continue to monitor.

Have not been able to use GS since 2 weeks before 10.04-testing ended.  I have no idea how to file a bug on this as I have no idea what the problem is.

Hi Ranch hand,

Well I am afraid waiting for new updates may not help here.
Maverick's GS has been in working order for ~3 weeks now.
You have something else wrong there that can be corrected.
I also use xorg-edgers repo, but nothing else, just official maverick with all updates.

It might help if I can have more info on your setup.
I assume it is a Maverick with edgers PPA.
So you have xserver-xorg-core_1.9.0+git20100821
and gnome-shell_2.31.5-2ubuntu1.
- 
But what other repos affecting this? You don't have Rico's PPA?
Which graphics card you have? What drivers you use?

---

### Post by ranch hand on 2010-08-28
The edgers ppa is the only one.  The only other thing I add is medibuntu.

I think all the relevant specs for my box are in my sig.

It could just be my video card.  The bugger is poorly supported all around.  The OSS drivers have always been much better than the ATI drivers and still are.

Under 10.04(testing) I had to have the edgers drivers to get GS to work when I installed it in that cycle.  Then the default drivers caught up and GS worked with those.  About 2 weeks before 10.04 was released GS (build variety) refused to work and I needed the partition for ISO testing and never reinstalled it.

Have not been able to get it to work in 10.10 at all.  Beats me.

Can't get Unity to work either although it seems to be slightly better without the edgers drivers (doesn't work either way but with out those drivers tty works).

---

### Post by cariboo on 2010-08-28
I installed the version from the repository last night and it works quite well almost. I use two user accounts, when I logged into the other account to do some work, then logged back into the first account the system locked up so hard I had to use the reset button to reboot.

---

### Post by Madspyman on 2010-08-29
Just installed the version from the repo on my Maverick partition, it not only didn't work but also kicked me out to the GDM login. I remember back in Karmic when I could use gnome-shell flawlessly. I'll have to try the version from the ppa to see if I get better results.

---

### Post by Merk42 on 2010-08-29
> **Madspyman said:**
> Just installed the version from the repo on my Maverick partition, it not only didn't work but also kicked me out to the GDM login. I remember back in Karmic when I could use gnome-shell flawlessly. I'll have to try the version from the ppa to see if I get better results.

Why not just build from source?

---

### Post by cariboo on 2010-08-29
> **Merk42 said:**
> Why not just build from source?

I don't know about Madspyman, but I have problems downloading from the git repository, I tried the other day and after 4 hours it was still sitting a 0%.

Other than a bug when switching users gnome-shell from the repositories works quite well for me.

---

### Post by Madspyman on 2010-08-29
> **Merk42 said:**
> Why not just build from source?

Thats usually what I end up doing, didn't help in Lucid when I tried it though, I haven't been able to get shell working properly since Karmic. Sometimes installing fglrx helps not for long though, and currently that's not an option in Maverick.

---

### Post by Harry33 on 2010-08-30
> **ranch hand said:**
> The edgers ppa is the only one.  The only other thing I add is medibuntu.

I think all the relevant specs for my box are in my sig.

It could just be my video card.  The bugger is poorly supported all around.  The OSS drivers have always been much better than the ATI drivers and still are.

Under 10.04(testing) I had to have the edgers drivers to get GS to work when I installed it in that cycle.  Then the default drivers caught up and GS worked with those.  About 2 weeks before 10.04 was released GS (build variety) refused to work and I needed the partition for ISO testing and never reinstalled it.

Have not been able to get it to work in 10.10 at all.  Beats me.

Can't get Unity to work either although it seems to be slightly better without the edgers drivers (doesn't work either way but with out those drivers tty works).

Hi Ranch hand,

I just found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/626743](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/626743)

It is about xserver-xorg-video-ati driver being incompatible with GS window manager (mutter).
You might see this as your system freezes, perhaps mutter dies.

---

### Post by ranch hand on 2010-08-30
Yup, I believe that is the problem.  I have a similar problem with Unity that has this same basis.

Mutter will, I am sure, come around soon, at least for Unity (I think they use a slightly different version) because of the priority Unity has in this release.

The upcoming ISO testing will see the OS that I have GS on reinstalled.  I have fooled with it too much to trust the results.  I will reinstall GS and continue to see if it works.

I may fool with my bios and see if switching to the integrated Intel video controller works better with both of them.  I think some folks are having some difficulty with them with Intel too.

I would REALLY  like to be able to compare the two.

The screen shots I have seen make it look like some of my biggest problems with GS have seen some real improvement.  Oh well, just need to wait.

---

### Post by Madspyman on 2010-08-30
> **Harry33 said:**
> Hi Ranch hand,

I just found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/626743](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/626743)

It is about xserver-xorg-video-ati driver being incompatible with GS window manager (mutter).
You might see this as your system freezes, perhaps mutter dies.

This would explain my problem as well with both shell and unity.

---

### Post by lesnoland on 2010-08-31
Am I the only one getting this:

[https://bugzilla.gnome.org/show_bug.cgi?id=628381](https://bugzilla.gnome.org/show_bug.cgi?id=628381)

---

### Post by bprins on 2010-09-01
Hi,

Trying to get Gnome Shell up and running (in Maverick, but that's all fine). 

```

sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get install gnome-shell
sudo apt-get gnome3-session

```

If I now type
```

sudo gnome-shell --replace

```

Then I get the (pretty cool!) gnome 3 desktop environment. But, I don't want to type gnome-shell --replace, I want to log into gnome shell. Hence I installed gnome3-session.

So the suggestion from a tutorial is to uninstall gnome-session, and install gnome3-session. 

Q1: sudo apt-get remove gnome-session-* uninstalls ubuntu-desktop. Is that what I should do? sudo apt-get install gnome3-session does not reinstall ubuntu-desktop. Don't I still need ubuntu-desktop? I've tried what the tutorial proposed anyway, ending up with the probem that X is not starting.

Now, as a workaround, I can add "sudo gnome-shell --replace" as a startup script, but that's a bit lame. I just want to replace gnome2 with gnome3 (gnome shell).

Q2: Different website claims that I can change the session manager in System->Pref->desktop. I don't have that application in Maverick. Any other way available?

Either the answer to Q1 or Q2 might help me getting gnome3 up and running.

Thanks a lot in advance!

Bas

---

### Post by dino99 on 2010-09-01
you might already find a thread about gnome-shell into maverick subforum

[http://ubuntuforums.org/showthread.php?t=1476241](http://ubuntuforums.org/showthread.php?t=1476241)

---

### Post by bprins on 2010-09-01
looks like dependencies aren't set properly.

sudo apt-get remove gnome-session-* also removes gdm and ubuntu-desktop
sudo apt-get install gnome3-session does not install gdm.

Reinstalled gdm after installing gnome3-session
```

sudo apt-get install gnome3-session
sudo apt-get install gdm

```

gdm start gave an error, so just ran sudo reboot.

After that, I logged right into gnome-shell. 

Is this supposed to be the "how-to-install-gnome-shell"? 

It works now, so no problem, but still I have the feeling I made life a bit harder then necessary.

Thanks all.

Bas

---

### Post by Elfy on 2010-09-01
moved to maverick forum

---

### Post by plun on 2010-09-01
Ricotz ppa is broken for the moment.

Use the gnome-shell package within Mavericks repo !!

Works just fine....


(Ubuntu Mozilla Daily PPA breaks Mavericks gnome-shell, gjs trouble)

---

### Post by 23meg on 2010-09-01
Threads merged.

---

### Post by Harry33 on 2010-09-02
> **bprins said:**
> looks like dependencies aren't set properly.

sudo apt-get remove gnome-session-* also removes gdm and ubuntu-desktop
sudo apt-get install gnome3-session does not install gdm.

Reinstalled gdm after installing gnome3-session
```

sudo apt-get install gnome3-session
sudo apt-get install gdm

```gdm start gave an error, so just ran sudo reboot.

After that, I logged right into gnome-shell. 

Is this supposed to be the "how-to-install-gnome-shell"? 

It works now, so no problem, but still I have the feeling I made life a bit harder then necessary.

Thanks all.

Bas

Bprins,

No, you should not remove gnome-session-* at all.
Only install gnome3-session and gnome-shell packages with all the dependencies they bring about.

Then, reboot and from login screen of gdm choose session "Gnome3" instead of "Ubuntu Desktop Edition."
Then the next time you reboot you will be automatically logged into gnome3 session.
Should you want to go back to gnome-panel (Ubuntu Desktop Edition), then again, choose that one from the login screen.

Harry

---

### Post by Harry33 on 2010-09-02
> **plun said:**
> Ricotz ppa is broken for the moment.

Use the gnome-shell package within Mavericks repo !!

Works just fine....


(Ubuntu Mozilla Daily PPA breaks Mavericks gnome-shell, gjs trouble)

That is correct.
Rico's PPA "Gnome Shell Testing" has been broken for weeks now. Several packages missing.
Rico has gathered the new GS packages in his PPA "Staging".
But the advice is not to use it.
Anyway, it would install GTK+3.0 (2.90.6) into your system with awkward consequences.

---

### Post by sgage on 2010-09-02
Hello Folks,

I'm back in the fray of trying to compile GS. Full disclosure: I am running Lucid these days.

Anyway, the problem is pango:

Traceback (most recent call last):
  File "/home/sgage/gnome-shell/install/bin/g-ir-scanner", line 44, in <module>
    sys.exit(scanner_main(sys.argv))
  File "/home/sgage/gnome-shell/install/lib/gobject-introspection/giscanner/scannermain.py", line 325, in scanner_main
    main.transform()
  File "/home/sgage/gnome-shell/install/lib/gobject-introspection/giscanner/maintransformer.py", line 60, in transform
    self._namespace.walk(self._pass_type_resolution)
  File "/home/sgage/gnome-shell/install/lib/gobject-introspection/giscanner/ast.py", line 405, in walk
    node.walk(callback, [])
  File "/home/sgage/gnome-shell/install/lib/gobject-introspection/giscanner/ast.py", line 484, in walk
    res = callback(self, chain)
  File "/home/sgage/gnome-shell/install/lib/gobject-introspection/giscanner/maintransformer.py", line 649, in _pass_type_resolution
    self._transformer.resolve_type(field.type)
  File "/home/sgage/gnome-shell/install/lib/gobject-introspection/giscanner/transformer.py", line 830, in resolve_type
    return self.resolve_type(typeval.element_type)
  File "/home/sgage/gnome-shell/install/lib/gobject-introspection/giscanner/transformer.py", line 838, in resolve_type
    return self._resolve_type_from_ctype(typeval)
  File "/home/sgage/gnome-shell/install/lib/gobject-introspection/giscanner/transformer.py", line 803, in _resolve_type_from_ctype
    raise TypeResolutionException(e)
giscanner.transformer.TypeResolutionException: Unknown namespace for identifier 'ParenStackEntry'
make[4]: *** [Pango-1.0.gir] Error 1
make[4]: Leaving directory `/home/sgage/gnome-shell/source/pango/pango'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/sgage/gnome-shell/source/pango/pango'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sgage/gnome-shell/source/pango/pango'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/pango'
make: *** [all] Error 2
*** Error during phase build of pango: ########## Error running make   *** [5/21]


Anyone else having this one? Any ideas on how to get through it?

TIA...

---

### Post by davideotape on 2010-09-02
Not getting that error, but this one: 

```
/home/david/gnome-shell/install/share/gir-1.0/Pango-1.0.gir: Incompatible version 1.1 (supported: 1.2)
make[4]: *** [Gdk-3.0.gir] Error 1
make[4]: Leaving directory `/home/david/gnome-shell/source/gtk3/gdk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/gtk3/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk3/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/21]
```

Seems like pango is out of date or the version hasn't been updated?

Edit:

Getting the same for clutter, mutter and gnome-shell too

---

### Post by lesnoland on 2010-09-02
Same error here, I will inspect it later.

> **davideotape said:**
> Not getting that error, but this one: 

```
/home/david/gnome-shell/install/share/gir-1.0/Pango-1.0.gir: Incompatible version 1.1 (supported: 1.2)
make[4]: *** [Gdk-3.0.gir] Error 1
make[4]: Leaving directory `/home/david/gnome-shell/source/gtk3/gdk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/gtk3/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk3/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/21]
```

Seems like pango is out of date or the version hasn't been updated?

Edit:

Getting the same for clutter, mutter and gnome-shell too

---

### Post by DemonBob on 2010-09-04
I'm getting the below when trying to run gnome-shell from the repos.... any advice?


```
demonbob@sys-desktop:~$ gnome-shell --replace
Shell killed with signal 11
demonbob@sys-desktop:~$ Cannot register the panel shell: there is already one running.

```

---

### Post by NightwishFan on 2010-09-04
Try disabling Compiz before you run gnome-shell --replace.

---

### Post by DemonBob on 2010-09-04
> **NightwishFan said:**
> Try disabling Compiz before you run gnome-shell --replace.

It's not running. Also set to none in appearance.

---

### Post by NightwishFan on 2010-09-04
Google searches show similar issues however nothing specific. I wonder, could you check your Xorg and System logs after starting the gnome shell and tell me what (if any) error messages occur.

---

### Post by DemonBob on 2010-09-04
Only thing i see is this in syslog. 

```
Sep  4 01:55:22 sys-desktop kernel: [15749.956793] mutter[14037]: segfault at 404 ip 008cc826 sp bf9bf6ec error 4 in libGL.so.1.2[8ca000+5000]
Sep  4 01:58:16 sys-desktop kernel: [15923.598994] mutter[14510]: segfault at 404 ip 00913826 sp bf8e559c error 4 in libGL.so.1.2[911000+5000]

```

---

### Post by NightwishFan on 2010-09-04
Thanks. What type of card do you have? Someone had this issue using an ATI card. If you are on Intel or Nvidia Proprietary it should just work. ATI is a big question mark though.

---

### Post by DemonBob on 2010-09-04
Intel - It was working fine a few days ago. I don't know what changed.

```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

```

---

### Post by davideotape on 2010-09-04
Brand new error:

```
../glib/gmacros.h:32: error: #error "Only <glib.h> can be included directly."
make[4]: *** [gobject.lo] Error 1
make[4]: Leaving directory `/home/david/gnome-shell/source/glib/gobject'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/glib/gobject'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/glib/gobject'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/glib'
make: *** [all] Error 2
*** Error during phase build of glib: ########## Error running make   *** [1/21]
```

---

### Post by NightwishFan on 2010-09-04
Purge and reinstall mutter and gnome-shell. Not sure what else to say, nothing more specific is in the logs. :( Sorry I could not be of help.

---

### Post by ronjouch on 2010-09-04
> **davideotape said:**
> Brand new error:

```
../glib/gmacros.h:32: error: #error "Only <glib.h> can be included directly."
make[4]: *** [gobject.lo] Error 1
make[4]: Leaving directory `/home/david/gnome-shell/source/glib/gobject'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/glib/gobject'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/glib/gobject'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/glib'
make: *** [all] Error 2
*** Error during phase build of glib: ########## Error running make   *** [1/21]
```

Same thing here with a cannot-be-fresher-and-cleaner jhbuild on a just-installed Meerkat beta.

---

### Post by ronjouch on 2010-09-04
GLib should build again now, but gobject-introspection is still broken.

---

### Post by tanmays on 2010-09-05
I am now using the Maverick Beta Repo version of Gnome-Shell. GS working perfectly for me.

Where can I find the WM Theme of GS which shows only the maximize and close button? IMO its useless to have minimize button on GS.

Is the GIT build version working perfectly now?

---

### Post by Harry33 on 2010-09-05
Yes the maverick's GS works now OK.

The Mozilla Spider Monkey problem has been fixed now:
- gjs_0.7.1-1ubuntu2
- gnome-shell_2.31.5-2ubuntu2
Both gjs and gnome-shell now find libmozjs.so, there is a wrapper added for that purpose.
See the fixed Launchpad bug#576991
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/576991](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/576991)

:!: Those of you, who made a symlink into the folder /usr/lib/ pointing to /usr/lib/xulrunner-1.9.2.8/libmozjs.so, can now, and should delete that symlink.
Even more important, if someone copied the libmozjs.so into the folder /usr/lib/, is to delete it; for safety reasons. :!:

---

### Post by plun on 2010-09-05
> **Harry33 said:**
> Yes the maverick's GS works now OK.

The Mozilla Spider Monkey problem has been fixed now:
- gjs_0.7.1-1ubuntu2
- gnome-shell_2.31.5-2ubuntu2
Both gjs and gnome-shell now find libmozjs.so, there is a wrapper added for that purpose.
See the fixed Launchpad bug#576991
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/576991](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/576991)

:!: Those of you, who made a symlink into the folder /usr/lib/ pointing to /usr/lib/xulrunner-1.9.2.8/libmozjs.so, can now, and should delete that symlink.
Even more important, if someone copied the libmozjs.so into the folder /usr/lib/, is to delete it; for safety reasons. :!:

Yep..... now its possible to use the Ubuntu Mozilla Daily PPA and Mavericks Gnome-Shell package.

Now its just a challenge to find any joy with Gnome-Shell.....:-$

---

### Post by davideotape on 2010-09-05
Nope, git still isn't building cleanly:

```
make[2]: Entering directory `/home/david/gnome-shell/source/gtk-engines/engines/clearlooks'
  CC     clearlooks_rc_style.lo
  CC     clearlooks_style.lo
./src/clearlooks_style.c: In function ‘clearlooks_style_draw_box’:
./src/clearlooks_style.c:775: warning: #warning Assuming non-pulsing progress bars because there is currently no way to query them in GTK+ 3.0.
./src/clearlooks_style.c:787: error: ‘GTK_PROGRESS_LEFT_TO_RIGHT’ undeclared (first use in this function)
./src/clearlooks_style.c:787: error: (Each undeclared identifier is reported only once
./src/clearlooks_style.c:787: error: for each function it appears in.)
./src/clearlooks_style.c:788: error: ‘GTK_PROGRESS_RIGHT_TO_LEFT’ undeclared (first use in this function)
./src/clearlooks_style.c:807: error: ‘GTK_PROGRESS_BOTTOM_TO_TOP’ undeclared (first use in this function)
./src/clearlooks_style.c:809: error: ‘GTK_PROGRESS_TOP_TO_BOTTOM’ undeclared (first use in this function)
make[2]: *** [clearlooks_style.lo] Error 1
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk-engines/engines/clearlooks'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk-engines/engines'
make: *** [all-recursive] Error 1
*** Error during phase build of gtk-engines-3: ########## Error running make   *** [10/21]

```

Although the pango version issue seems to have been resolved

---

### Post by mixint27 on 2010-09-05
> **davideotape said:**
> Nope, git still isn't building cleanly:

```
make[2]: Entering directory `/home/david/gnome-shell/source/gtk-engines/engines/clearlooks'
  CC     clearlooks_rc_style.lo
  CC     clearlooks_style.lo
./src/clearlooks_style.c: In function ‘clearlooks_style_draw_box’:
./src/clearlooks_style.c:775: warning: #warning Assuming non-pulsing progress bars because there is currently no way to query them in GTK+ 3.0.
./src/clearlooks_style.c:787: error: ‘GTK_PROGRESS_LEFT_TO_RIGHT’ undeclared (first use in this function)
./src/clearlooks_style.c:787: error: (Each undeclared identifier is reported only once
./src/clearlooks_style.c:787: error: for each function it appears in.)
./src/clearlooks_style.c:788: error: ‘GTK_PROGRESS_RIGHT_TO_LEFT’ undeclared (first use in this function)
./src/clearlooks_style.c:807: error: ‘GTK_PROGRESS_BOTTOM_TO_TOP’ undeclared (first use in this function)
./src/clearlooks_style.c:809: error: ‘GTK_PROGRESS_TOP_TO_BOTTOM’ undeclared (first use in this function)
make[2]: *** [clearlooks_style.lo] Error 1
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk-engines/engines/clearlooks'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk-engines/engines'
make: *** [all-recursive] Error 1
*** Error during phase build of gtk-engines-3: ########## Error running make   *** [10/21]

```Although the pango version issue seems to have been resolved

getting the same error.

---

### Post by x-shaney-x on 2010-09-07
I am trying gnome shell again for the first time in a while, hated it at first sight but starting to like it now so just have a couple of questions about it:

1.  Does anyone know any way to re-order the favourites without removing them all and then adding them in the order I want them?
I'm very obsessive compulsive about the order of things.

2.  Has anyone tried running a dock app like awn or docky with shell
If so does it cause any problems when opening the activities panel?
Specifically, if the dock is on the left since that's where I normally have it.

<EDIT>
Tried number 2 myself and awn works very well with no problems so far.

---

### Post by tanmays on 2010-09-08
> **x-shaney-x said:**
> 
1.  Does anyone know any way to re-order the favourites without removing them all and then adding them in the order I want them?
I'm very obsessive compulsive about the order of things.



How to arrange the favorites?

---

### Post by x-shaney-x on 2010-09-08
Yes.  Arrange them in the order I want.
I group my favourites together (whether using a dock, mint menu or whatever) and that's the way I like it.
Also, if using the dock extension for gnome shell it also uses the favourites from the side panel and can't be re-ordered.

---

### Post by sgage on 2010-09-09
Has anyone managed to compile gnome-shell lately? I haven't been able to in quite some time.

I just tried this morning - got as far as clutter, which failed.

Oh well.

---

### Post by whollycow on 2010-09-09
> **sgage said:**
> Has anyone managed to compile gnome-shell lately? I haven't been able to in quite some time.

I just tried this morning - got as far as clutter, which failed.

Oh well.

Fail here, too.  I tried a couple of times last week and it failed on GTK3.  Seems strange that the problem doesn't seem to have been addressed at all.

---

### Post by sgage on 2010-09-09
> **whollycow said:**
> Fail here, too.  I tried a couple of times last week and it failed on GTK3.  Seems strange that the problem doesn't seem to have been addressed at all.

I had the gtk3 fail last week too. It really does seem strange that nobody seems to care to make this thing compilable so we can test it. Oh well.

---

### Post by x-shaney-x on 2010-09-10
I have been running shell for a couple of days with only minor issues.
One thing is, I couldn't help feeling something was missing and I finally realised what it is... indicators.

Anyone know how to make them show on the panel or are they just incompatible with shell (at the moment or forever)?

---

### Post by Merk42 on 2010-09-10
> **x-shaney-x said:**
> I have been running shell for a couple of days with only minor issues.
One thing is, I couldn't help feeling something was missing and I finally realised what it is... indicators.

Anyone know how to make them show on the panel or are they just incompatible with shell (at the moment or forever)?
Incompatible.
I'm sure there will eventually be a workaround either from GNOME or Ayatana, unless Unity is secretly planned to replace the desktop as well.

---

### Post by sgage on 2010-09-10
> **Merk42 said:**
> Incompatible.
I'm sure there will eventually be a workaround either from GNOME or Ayatana, unless Unity is secretly planned to replace the desktop as well.

But some notification-area stuff works.

E.g., to get the volume control, type Alt F2, gnome-volume-control-applet, and you're good to go. Haven't really tried anything else.

---

### Post by seeker5528 on 2010-09-10
> **sgage said:**
> But some notification-area stuff works.

All the notification-area stuff should work, correct? Or did the G-S devs break it in a different way than the Ubuntu devs?

It's the indicators that are not compatible.

---

### Post by x-shaney-x on 2010-09-10
Yea I'm getting notifications stuff - wifi, sound etc as normal just the indicators missing.

---

### Post by Half-Left on 2010-09-10
> **whollycow said:**
> Fail here, too.  I tried a couple of times last week and it failed on GTK3.  Seems strange that the problem doesn't seem to have been addressed at all.

GTK3 is having a lot of API changes at the moment and there for breaking other things which then have to be adapted.

---

### Post by Merk42 on 2010-09-10
Built fine for me just now in Lucid, had to delete the gnome-shell and source folders in ~/.
Of course once I ran it and went to the overview it broke. I could click on a window to bring it to front, but it wouldn't respond to mouse or keyboard input. Thankfully the menu in the upper right still worked so I had to click logout and wait for it to count down.

---

### Post by jjcv on 2010-09-11
Built cleanly today on 10.10 Beta 64bit system.  Been a while.  :-)

---

### Post by sgage on 2010-09-12
> **jjcv said:**
> Built cleanly today on 10.10 Beta 64bit system.  Been a while.  :-)

Built cleanly for me, too, on a 10.04.1 32-bit system. Everything seems to work. It seems it might be just a tad quicker than the last time I compiled, but that could be my imagination.

---

### Post by tanmays on 2010-09-15
Current update of Maverick breaks my gnome-shell. Everything freezes now... Totally unusable :(

---

### Post by Peter09 on 2010-09-15
Currently on Maverick I am getting the following Bug.
 
When I first go into overlay mode everything looks OK, then I realised that some Icons were upside down (although the text was OK) and then I saw that the text was on the wrong icon!. As soon as I asked for a refresh of the Icons they became corrupt. (Only the icon, not the whole screen). Could this been a faulty theme?

---

### Post by BwackNinja on 2010-09-15
> **Peter09 said:**
> Currently on Maverick I am getting the following Bug.
 
When I first go into overlay mode everything looks OK, then I realised that some Icons were upside down (although the text was OK) and then I saw that the text was on the wrong icon!. As soon as I asked for a refresh of the Icons they became corrupt. (Only the icon, not the whole screen). Could this been a faulty theme?

Sounds more like a driver bug. What driver are you using? Do you see any corruption like that outside of gnome-shell?

---

### Post by Peter09 on 2010-09-15
This is an Upgrade to Maverick (about a week ago) The card is an ATI card but not at home at the moment so can give no more details. No other corruption that I can see.
 
I get no corruption using the standard desktop.

---

### Post by tanmays on 2010-09-16
Building GS fresh on my Linux Mint Debian Install. The debian testing repo has a really old GS version. Lets hope everything goes well.

---

### Post by davideotape on 2010-09-19
Quick question: what should I do if I get this type of error:

```
*** Checking out gdk-pixbuf *** [7/21]
git stash save jhbuild-stash
po/cs.po: needs merge
po/de.po: needs merge
po/gl.po: needs merge
po/he.po: needs merge
po/nl.po: needs merge
po/pt.po: needs merge
po/sl.po: needs merge
po/cs.po: needs merge
po/de.po: needs merge
po/gl.po: needs merge
po/he.po: needs merge
po/nl.po: needs merge
po/pt.po: needs merge
po/sl.po: needs merge
po/cs.po: unmerged (d5c1afc3455c7134c6dcdbd82c78d22bc2b61b99)
po/cs.po: unmerged (3a7e7017c03e24a2e943fc6b544eba7a14d3baf2)
po/cs.po: unmerged (a64455d1b8bafb5fea28d24d629043c320ce0135)
po/de.po: unmerged (81f61e9966040ce0f33c2872233a5ca8e4370009)
po/de.po: unmerged (8b918caefbee6ac48a1d0e26eb714d314d8d7050)
po/de.po: unmerged (3d70aaf3e3f2e6a361208a4ec67abc9a71af4f49)
po/gl.po: unmerged (254400a4e3eee9668e50c0e1d5c4195961f6d53e)
po/gl.po: unmerged (72c0a51800b72464f096add514a647d186585093)
po/gl.po: unmerged (d5933d11863868d92567f1f9696c7567b3b08375)
po/he.po: unmerged (0d62fa3f8757d631b98d74197a5e75bb68bb4115)
...
fatal: git-write-tree: error building trees
Cannot save the current index state

```

Is this just a server issue that I need to wait for the git server to resolve?

---

### Post by autocrosser on 2010-09-19
I ran into that one too----I just trashed the gdk_pixbuf folder & rebuilt again--looks like a old file thing with git---Mine wouldn't resolve with the older stuff----and a clean download went right thru with no errors......

---

### Post by davideotape on 2010-09-25
> **averlon said:**
> Hi,
how do I deactivate (not deinstall) GNOME from loading when I start my server?

I don't really think this is the right place to be asking this; try posting in the general help forum over here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by moore.bryan on 2010-10-01
Is anyone having GS crash when they try to move a window?

Also wondering where I can change the button (menu, min, max, close) positioning. When GS is running, my gconf settings are ignored and GS puts the buttons on the right-side ("old" way) with all windows *except* for chromium, which has the buttons on the left-side ("new" way).

Thanks...

---

### Post by decoherence on 2010-10-02
I had that problem as well. Additionally, the process would choke shortly after that until I installed the icon-naming-utils package.

---

### Post by moore.bryan on 2010-10-02
> **decoherence said:**
> I had that problem as well. Additionally, the process would choke shortly after that until I installed the icon-naming-utils package.
Hmm... wonder what that package has anything to do with GS behavior.

And installing icon-naming-utils doesn't fix my problem... any other ideas folks?

---

### Post by quickridge on 2010-10-02
I haven't been able to get past this error during the build phase of gnome-shell for a couple of weeks now. Anyone know what the problem might be:

```

/home/quickridge/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/quickridge/gnome-shell/install/lib64/libclutter-glx-1.0.so: undefined reference to `g_object_class_install_properties'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/quickridge/gnome-shell/install/lib64/libclutter-glx-1.0.so: undefined reference to `g_object_notify_by_pspec'
/home/quickridge/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/quickridge/gnome-shell/install/lib64/libclutter-glx-1.0.so: undefined reference to `g_source_set_name'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
/home/quickridge/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_take_variant'
```

I'm still running Lucid if that matters. Thanks for any help in advance.

---

### Post by Starks on 2010-10-02
How's G-S looking for Natty?

---

### Post by Merk42 on 2010-10-02
> **Starks said:**
> How's G-S looking for Natty?
UDS hasn't happened, and Maverick isn't even done. So I think right now Natty only exists as "yes the name of the next development release will be Natty Narwhal".
Also GNOME Shell has yet to implement it's massive UI change, so, it's way too early to tell.

---

### Post by moore.bryan on 2010-10-03
So, I have found the ~/gnome-shell/install/gconf/schemas/gnome-shell.schemas file, which overrides metacity's usual button behavior, but even though I "fixed" them and restarted, GS refuses to acknowledge the change. Am I missing another file?

---

### Post by cariboo on 2010-10-03
Unless things have changed a great deal, you can change button order and position using gconf editor. Go to desktop->gnome->shell->windows.

I'm still using the version from the repos, as it takes well over 24 hours to download from the git repositories.

---

### Post by bash on 2010-10-03
> **Merk42 said:**
> Also GNOME Shell has yet to implement it's massive UI change, so, it's way too early to tell.

Anyone got an idea or could point me to a resource about when they are planning to start implementing the new design? Last time I had a peak at the mailing lists I couldn't find anything about it. And from the commit log it doesn't appear like the have started at all, except for the universal access applet.

---

### Post by Starks on 2010-10-03
Wait. What new UI?

They're trashing the current godawful one?

---

### Post by go7Ul1ai on 2010-10-03
Gnome Shell just seems to be a massive fail in my opinion..

---

### Post by Merk42 on 2010-10-03
> **Starks said:**
> Wait. What new UI?

They're trashing the current godawful one?

Yes and no.
The newest mockup looks inspired by Unity, but it totally isn't and they just happened to be making drastic changes completely unrelated to Canonical's work.
[http://arstechnica.com/open-source/news/2010/07/gnome-3-not-ready-yet-release-pushed-back-to-2011.ars](http://arstechnica.com/open-source/news/2010/07/gnome-3-not-ready-yet-release-pushed-back-to-2011.ars)

---

### Post by ronacc on 2010-10-03
since I utterly detest unity and won't even use it on my netbook , I somehow don't think thats going to grow on me :lolflag:

or to quote bill the cat   "gag acck ".

---

### Post by bash on 2010-10-03
> **Merk42 said:**
> Yes and no.
The newest mockup looks inspired by Unity, but it totally isn't and they just happened to be making drastic changes completely unrelated to Canonical's work.
[http://arstechnica.com/open-source/news/2010/07/gnome-3-not-ready-yet-release-pushed-back-to-2011.ars](http://arstechnica.com/open-source/news/2010/07/gnome-3-not-ready-yet-release-pushed-back-to-2011.ars)

Additionally there is also a short video of the new the design in action:

[http://vimeo.com/13797705](http://vimeo.com/13797705)

*Note: This is just an animated mockup and not an actual implementation of it*

---

### Post by MishaAct on 2010-10-04
> **bash said:**
> Additionally there is also a short video of the new the design in action:

[http://vimeo.com/13797705](http://vimeo.com/13797705)

*Note: This is just an animated mockup and not an actual implementation of it*
OMG
I've just realized what gnome-shell resembles: iPhone/Android/etc shell
I don't think this is good idea, since those solutions were introduced for smartphones with their tiny screens. It's funny, but GS isn't compact: it simulates those shells, but it needs large screens and doesn't suit netbooks well.
So the GS "uniqueness" isn't uniqueness at all but attempt to turn PC into the huge toy like smartphones are ))

---

### Post by ranch hand on 2010-10-04
> **MishaAct said:**
> OMG
I've just realized what gnome-shell resembles: iPhone/Android/etc shell
I don't think this is good idea, since those solutions were introduced for smartphones with their tiny screens. It's funny, but GS isn't compact: it simulates those shells, but it needs large screens and doesn't suit netbooks well.
So the GS "uniqueness" isn't uniqueness at all but attempt to turn PC into the huge toy like smartphones are ))
So it seems to fit the current Ubuntu direction exactly.

---

### Post by moore.bryan on 2010-10-04
> **cariboo907 said:**
> Unless things have changed a great deal, you can change button order and position using gconf editor. Go to desktop->gnome->shell->windows.

I'm still using the version from the repos, as it takes well over 24 hours to download from the git repositories.
I thought the same, Cariboo, until I changed everything and nothing happened. Then I was poking around and found the ~/gnome-shell/install/etc/gconf/schemas/gnome-shell.schemas file. In it, one finds the following line
```

<!-- Metacity overrides -->

```
which implies anything following is altered from metacity and gconf's settings. Later in the file, one finds the button_layout spec and the pertinent line is
```

This key overrides /apps/metacity/general/button_layout when running GNOME Shell.

```
So... not sure how to fix this one.

---

### Post by moore.bryan on 2010-10-04
> **Merk42 said:**
> Yes and no.
The newest mockup looks inspired by Unity, but it totally isn't and they just happened to be making drastic changes completely unrelated to Canonical's work.
[http://arstechnica.com/open-source/news/2010/07/gnome-3-not-ready-yet-release-pushed-back-to-2011.ars](http://arstechnica.com/open-source/news/2010/07/gnome-3-not-ready-yet-release-pushed-back-to-2011.ars)

So long as we get rid of the Unity bs, I don't mind it.

---

### Post by gotjazz on 2010-10-04
hrm so am I the only one getting "configure: error: Unable to determine extra compiler flags needed" during configuring gjs?

---

### Post by Starks on 2010-10-04
> **bash said:**
> Additionally there is also a short video of the new the design in action:

[http://vimeo.com/13797705](http://vimeo.com/13797705)

*Note: This is just an animated mockup and not an actual implementation of it*
That still looks terrible. If Ubuntu ever adopts this, I'm going to Mint or Fedora. I don't care if a gnome-panel option is left in.

Watch how this kills the growing momentum of desktop Linux.

---

### Post by bash on 2010-10-04
> **Starks said:**
> That still looks terrible. If Ubuntu ever adopts this, I'm going to Mint or Fedora. I don't care if a gnome-panel option is left in.

Watch how this kills the growing momentum of desktop Linux.

Considering that quite a few of the Shell devs are employed by Red Hat, Fedora will most likely adopt it sooner than later.

---

### Post by Starks on 2010-10-04
D:

Is nothing sacred anymore?

---

### Post by seeker5528 on 2010-10-04
> **Starks said:**
> Is nothing sacred anymore?

Cows.:P

---

### Post by cariboo on 2010-10-04
As the local ranchers here say. "there ain't no sacred cows here" :)

---

### Post by seeker5528 on 2010-10-04
> **cariboo907 said:**
> As the local ranchers here say. "there ain't no sacred cows here" :)

Wha-a-a-a-t!?!? You mean they don't thank the great cow spirit for the meat, cheese, money in their pockets, etc... ? :o

Later, Seeker

---

### Post by ronacc on 2010-10-04
all hail the t-bone :P

---

### Post by Merk42 on 2010-10-04
In more relevant news, [GNOME Shell is now at version 2.91.0](http://mail.gnome.org/archives/gnome-shell-list/2010-October/msg00001.html)

---

### Post by 23dornot23d on 2010-10-06
I like the latest release ...... clean and tidy ...... just add cairo-dock ..... its superb .... plus compiz ....

[LINK]("https://sites.google.com/site/000menu/home/gnome---3")

There should be a PPA like this with a blank desktop - for all people to have a play with ...........

Just needs one addition ...... a save feature once its set up ....... as the user likes it  .........

---

### Post by moore.bryan on 2010-10-07
> **23dornot23d said:**
> I like the latest release ...... clean and tidy ...... just add cairo-dock ..... its superb .... plus compiz ....

[LINK]("https://sites.google.com/site/000menu/home/gnome---3")

There should be a PPA like this with a blank desktop - for all people to have a play with ...........

Just needs one addition ...... a save feature once its set up ....... as the user likes it  .........

Maybe I misunderstood, but Compiz isn't compatible with GS.

---

### Post by 23dornot23d on 2010-10-07
Compiz seems to be working for me now ...... 

After doing a direct upgrade from that PPA and using Gnome 3 ..... 
( The overall look is good - and the functionality is excellent  )

[COLOR=Blue]If transparent overlays could be added to this using the function keys to give it more options like the way you had the Gnome Workspace Layout that would be good ..... 
to be able to toggle the options on and off would be even better .....
[/COLOR]
The visual effects mode changes for me from right clicking on the desktop - so this allowed some of the compiz effects to work for me

 
Just if someone could tell me what to do to get it to stick with the visual effects - it always forgets my settings ..... 

[B]Each time I re-boot I do not really want to have to keep setting compiz effects to work again - is there a easy way to do this .....
one line of code as it starts up in the startup manager maybe !


[/B][B]... I like it now .....  just the way it is ..... looks great and so  easy to use mouseover and one click to get where I want to be .... [LINK]("https://sites.google.com/site/000menu/home/gnome---3")
[/B]

---

### Post by seeker5528 on 2010-10-07
> **23dornot23d said:**
> After doing a direct upgrade from that PPA and using Gnome 3 ..... 
( The overall look is good - and the functionality is excellent  )

From my understanding of the way things work, Compiz with Gnome 3 shouldn't be significantly different than Compiz with Gnome 2. 
 
> 
[B]Each time I re-boot I do not really want to have to keep setting compiz effects to work again - is there a easy way to do this .....
one line of code as it starts up in the startup manager maybe !

Assuming compiz does the correct thing if you treat it like a normal window manager... Creating a file in your home directory named .xprofile and including the following line of text

```
export WINDOW_MANAGER="/usr/bin/compiz"
```

should work.

Otherwise you might have to go to 'Startup Applications' and add an item that uses the exec line

```
compiz --replace
```

Later, Seeker

---

### Post by 23dornot23d on 2010-10-07
Cheers Seeker5528

That works great ..... now I have a nice neat desktop  ...... I like it ........ Thank you ;) 

:KS:KS:KS:KS:KS

---

### Post by terry_gardener on 2010-10-07
why cant i build gnome-shell 

when i try get.

```
git clone git://git.gnome.org/gdk-pixbuf
Initialized empty Git repository in /home/terry/gnome-shell/source/gdk-pixbuf/.git/
remote: Counting objects: 229298, done.
remote: Compressing objects: 100% (32561/32561), done.
remote: Total 229298 (delta 196967), reused 228518 (delta 196355)
Receiving objects: 100% (229298/229298), 133.74 MiB | 395 KiB/s, done.
Resolving deltas: 100% (196967/196967), done.
git pull --rebase
Current branch master is up to date.
*** Configuring gdk-pixbuf *** [7/23]
./autogen.sh --prefix /home/terry/gnome-shell/install --libdir '/home/terry/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/terry/gnome-shell/install --libdir '/home/terry/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [7/23]

  [1] Rerun phase configure
  [2] Ignore error and continue to clean
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 

```

tried 1 and 2 = get same message 
tried 3 and it finishes but gnome-shell and other packages dont build and therefore doesn't work. 
trued 6 and get same message. 

i have even tried deleting the whole gnome-shell folder from home dir and starting again still get this message. 

any ideas

---

### Post by 23dornot23d on 2010-10-07
I too was trying to see where they are with this project at the moment ......

I use a old version of Gnome-Shell that I run from Linux Mint ........
I have no idea why the latest is not working ...:(... sorry ....

Maybe they have emptied it out and are leaving it till after the new release to start development again.

[B]Has the new Gnome Shell been removed till after the new MM 10.10 release ?
[/B] 
For me personally I just would like a Desktop thats clean and functional to work in efficiently ....
so far so good ..... with Gnome 3 and Compiz .... 
I just need the organisation part now

Interesting point of view compiz effects can be added to Mutter (Metacity 3) .... is this happening though ? ..... [LINK]("http://www.tuxmachines.org/node/39771")

[B]Why do Mutter and Compiz crash and are the effects from Compiz going to be added to Gnome-Shell ?
[/B] 
Nice recent write up on where Gnome-Shell is heading .... [Link]("http://apcmag.com/gnome-wants-to-match-kde-and-windows.htm")

---

### Post by wersdaluv on 2010-10-07
**Merk42**,

When Maverick is finally out and this forum (Maverick testing) is already closed, can you start a thread on Installation & Upgrades or wherever fit to continue this discussion?

It's also nice if users of the currently latest stable version of Ubuntu can discuss installing GNOME Shell from source. ;)

---

### Post by sendblink23 on 2010-10-07
I need help

I'm stuck within: jhbuild build

```
*** Configuring gdk-pixbuf *** [7/23]
./autogen.sh --prefix /home/sendblink23/gnome-shell/install --libdir '/home/sendblink23/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/sendblink23/gnome-shell/install --libdir '/home/sendblink23/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [7/23]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 

```


Any ideas to fix this????
I've already tried many times "1" & "6" and I keep getting the same Error in there

---

I've already tried deleting the gnome-shell directory & trying again.. but I still get stuck in the same error :(

---

### Post by Merk42 on 2010-10-07
sendblink23 and terry_gardener
You could try to delete the gnome-shell folder, **and** the source folder also found in home.
Then redo the building instructions from step 1 on the first page of this thread.

wersdaluv
GNOME Shell will still be in development during Natty's development cycle, so I'm not sure if it should be on areas of the forum where people aren't using pre-relase software yet.

---

### Post by sendblink23 on 2010-10-07
> **Merk42 said:**
> sendblink23 and terry_gardener
You could try to delete the gnome-shell folder, **and** the source folder also found in home.
Then redo the building instructions from step 1 on the first page of this thread.

wersdaluv
GNOME Shell will still be in development during Natty's development cycle, so I'm not sure if it should be on areas of the forum where people aren't using pre-relase software yet.

I have just tried it now.. erasing "gnome-shell" & "source" folder & starting again from Step 1 .. and again I get the exact same error

[HTML]*** Checking out gdk-pixbuf *** [7/23]
git clone git://git.gnome.org/gdk-pixbuf
Initialized empty Git repository in /home/sendblink23/gnome-shell/source/gdk-pixbuf/.git/
remote: Counting objects: 229298, done.
remote: Compressing objects: 100% (32561/32561), done.
remote: Total 229298 (delta 196968), reused 228518 (delta 196355)
Receiving objects: 100% (229298/229298), 133.73 MiB | 505 KiB/s, done.
Resolving deltas: 100% (196968/196968), done.
git pull --rebase
Current branch master is up to date.
*** Configuring gdk-pixbuf *** [7/23]
./autogen.sh --prefix /home/sendblink23/gnome-shell/install --libdir '/home/sendblink23/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/sendblink23/gnome-shell/install --libdir '/home/sendblink23/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [7/23]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 
[/HTML]

I have re-downloaded those files over 6 times already(a hassle with slow internet)... something must be going wrong on the other side or something is missing or etc

I'm on 10.10 RC x64 using all the latest updates... is there anything else we could try? I hopefully want to be able to test this before 10.10 RC ends ;)

---

### Post by Mblackwell on 2010-10-08
sudo apt-get install autopoint

---

### Post by sendblink23 on 2010-10-08
> **Mblackwell said:**
> sudo apt-get install autopoint

thanks it moved allot further but now I'm stuck here on #22/23...

```
 CC     libgnome_shell_la-shell-recorder-src.lo
  CCLD   libgnome-shell.la
  CC     test_theme-test-theme.o
  CCLD   test-theme
/home/sendblink23/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 1
*** Building gnome-shell *** [22/23]
make  
make  all-recursive
make[1]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make  all-am
make[3]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
  CCLD   test-theme
/home/sendblink23/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 1
*** Building gnome-shell *** [22/23]
make  
make  all-recursive
make[1]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make  all-am
make[3]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
  CCLD   test-theme
/home/sendblink23/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 1
*** Building gnome-shell *** [22/23]
make  
make  all-recursive
make[1]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make  all-am
make[3]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
  CCLD   test-theme
/home/sendblink23/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 

```


Any other ideas?


I re-ran: jhbuild build so it shows exactly where it errors
```
*** Checking out gnome-shell *** [22/23]
git pull --rebase
Current branch master is up to date.
*** Building gnome-shell *** [22/23]
make  
make  all-recursive
make[1]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make  all-am
make[3]: Entering directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
  CC     libgdmuser_1_0_la-gdm-user.lo
  CC     libgdmuser_1_0_la-gdm-user-manager.lo
  CCLD   libgdmuser-1.0.la
  CC     libst_1_0_la-st-adjustment.lo
  CC     libst_1_0_la-st-bin.lo
  CC     libst_1_0_la-st-box-layout.lo
  CC     libst_1_0_la-st-box-layout-child.lo
  CC     libst_1_0_la-st-button.lo
  CC     libst_1_0_la-st-clickable.lo
  CC     libst_1_0_la-st-container.lo
  CC     libst_1_0_la-st-drawing-area.lo
  CC     libst_1_0_la-st-entry.lo
  CC     libst_1_0_la-st-group.lo
  CC     libst_1_0_la-st-im-text.lo
  CC     libst_1_0_la-st-label.lo
  CC     libst_1_0_la-st-overflow-box.lo
  CC     libst_1_0_la-st-private.lo
  CC     libst_1_0_la-st-scroll-bar.lo
  CC     libst_1_0_la-st-scroll-view.lo
  CC     libst_1_0_la-st-table.lo
  CC     libst_1_0_la-st-table-child.lo
  CC     libst_1_0_la-st-texture-cache.lo
  CC     libst_1_0_la-st-theme-node.lo
  CC     libst_1_0_la-st-theme-node-drawing.lo
  CC     libst_1_0_la-st-theme-node-transition.lo
  CC     libst_1_0_la-st-tooltip.lo
  CC     libst_1_0_la-st-widget.lo
  CC     libst_1_0_la-st-enum-types.lo
  CCLD   libst-1.0.la
  CC     libtray_la-na-tray-child.lo
  CC     libtray_la-na-tray-manager.lo
  CCLD   libtray.la
  CC     libgnome_shell_la-shell-enum-types.lo
  CC     libgnome_shell_la-gnome-shell-plugin.lo
  CC     libgnome_shell_la-shell-app.lo
  CC     libgnome_shell_la-shell-app-system.lo
  CC     libgnome_shell_la-shell-app-usage.lo
  CC     libgnome_shell_la-shell-arrow.lo
  CC     libgnome_shell_la-shell-doc-system.lo
  CC     libgnome_shell_la-shell-drawing.lo
  CC     libgnome_shell_la-shell-embedded-window.lo
  CC     libgnome_shell_la-shell-generic-container.lo
  CC     libgnome_shell_la-shell-gtk-embed.lo
  CC     libgnome_shell_la-shell-global.lo
  CC     libgnome_shell_la-shell-slicer.lo
  CC     libgnome_shell_la-shell-stack.lo
  CC     libgnome_shell_la-shell-tray-icon.lo
  CC     libgnome_shell_la-shell-tray-manager.lo
  CC     libgnome_shell_la-shell-uri-util.lo
  CC     libgnome_shell_la-shell-window-tracker.lo
  CC     libgnome_shell_la-shell-wm.lo
  CCLD   libgnome-shell.la
  CC     test_theme-test-theme.o
  CCLD   test-theme
/home/sendblink23/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sendblink23/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 

```

---

### Post by Bo Rosén on 2010-10-08
I get the same error in 22.

---

### Post by symon1980 on 2010-10-08
> **23dornot23d said:**
> I too was trying to see where they are with this project at the moment ......

I use a old version of Gnome-Shell that I run from Linux Mint ........
I have no idea why the latest is not working ...:(... sorry ....

Maybe they have emptied it out and are leaving it till after the new release to start development again.

[B]Has the new Gnome Shell been removed till after the new MM 10.10 release ?
[/B] 
For me personally I just would like a Desktop thats clean and functional to work in efficiently ....
so far so good ..... with Gnome 3 and Compiz .... 
I just need the organisation part now

Interesting point of view compiz effects can be added to Mutter (Metacity 3) .... is this happening though ? ..... [LINK]("http://www.tuxmachines.org/node/39771")

[B]Why do Mutter and Compiz crash and are the effects from Compiz going to be added to Gnome-Shell ?
[/B] 
Nice recent write up on where Gnome-Shell is heading .... [Link]("http://apcmag.com/gnome-wants-to-match-kde-and-windows.htm")




Compiz is not compatible with Gnome-shell. Why do people keep saying or assuming that it is???? its been covered many times....
Mutter is a window manager
Compiz is a window manager
you cannot have both of them running at the same time.... 
Unless they develop some hack to make it work which has not been planned. Gnome don't want compiz to be compatible with Gnome-shell

---

### Post by sgage on 2010-10-08
> **Bo Rosén said:**
> I get the same error in 22.

My compile fails in 22 as well, but with a different error
[Edit: I didn't scroll down - looks like the same error]

```
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [1/1]
```

Oh well, the version in the repos works, but I want to see what's new.

---

### Post by xtoudi on 2010-10-08
> **symon1980 said:**
> Compiz is not compatible with Gnome-shell. Why do people keep saying or assuming that it is???? its been covered many times....
Mutter is a window manager
Compiz is a window manager
you cannot have both of them running at the same time.... 
Unless they develop some hack to make it work which has not been planned. Gnome don't want compiz to be compatible with Gnome-shell

Hi is writing about Gnome3 - not GNOME-SHELL! That's why :)

---

### Post by 23dornot23d on 2010-10-08
> **symon1980 said:**
> Compiz is not compatible with Gnome-shell. Why do people keep saying or assuming that it is???? its been covered many times....
Mutter is a window manager
Compiz is a window manager
you cannot have both of them running at the same time.... 
Unless they develop some hack to make it work which has not been planned. Gnome don't want compiz to be compatible with Gnome-shell

[B]Nobody has assumed anything as far as I know .....

I asked 2 completely clear questions ( of which neither were answered )
[/B]
If you click on either of the links I posted they said nothing of the sort about adding compiz to Gnome-shell ......  the piece in the link did imply that mutter may be adding the compiz effects .... though .... 
I was merely asking for clarification of that said article .....

[COLOR=Red]( In my previous Link all I showed was how I like the look of GNOME 3 with compiz ).[/COLOR]

Is this Gnome-Shell thing some kind of clique .... a little clique excluding any other input ?

**It asked at the beginning of this thread for technical questions .....  **

Asking if compiz type effects are to be added to mutter is a technical question - technical people in the know could answer but refrain from doing so .... but in the clique type scenario that you seem to have here.
 
* which as far as I can see excludes some USER's

Your answer should have gone something like this.

[B]Merk,

> 
Gnome don't want compiz to be compatible with [Gnome-shell]("https://sites.google.com/site/000menu/home/gnome---3/gnome---shell") - do they ?
[/B]

The answer is probably a simple ..... no .... but if you asked it - you might have got a response ..... thats how a clique works . ( its called ignorance )

But if they do intend making some of the compiz effects work in Mutter - 

Then it is something I think that some of the users are interested in ...... I am ....

I can understand wanting to be able to make GNOME3 of use to the wider community by not needing extra special graphics cards ..... but in time the graphics inbuilt into computers will advance and you will be left with a System that is old fashioned before it begins.

If Gnome 3 is intended to be run on a 486 then thats what your design should be around and I applaud you for that  it must take a lot of work to achieve that.

These were a couple of quick observances of **[Gnome-shell]("https://sites.google.com/site/000menu/home/gnome---3/gnome---shell")**

The younger generation have choices though and I am sure that they will make them - in March 2011 but probably not just  based on what will still run ok on a 486 .... although I do think they will like speed and quick performance. 

I also like an efficient system and a few effects .... and 3D just so you know what I would like you to tailor it around but seeing as I am just a user - 
I would not worry too much about that - 
Hope to see it make it into the next release  ok 

 ...... thanks for the reply  ;) ....... shame it did not answer either of the 2 questions asked though .....

although this almost did .......

Unless they develop some hack to make it work which has not been planned.

---

### Post by sendblink23 on 2010-10-08
> **sgage said:**
> My compile fails in 22 as well, but with a different error
[Edit: I didn't scroll down - looks like the same error]

```
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [1/1]
```

Oh well, the version in the repos works, but I want to see what's new.

Buuuuu :/

How do I install the one on the repo hehehe I'll might just play with that for now?

---

### Post by terry_gardener on 2010-10-08
> **sendblink23 said:**
> Buuuuu :/

How do I install the one on the repo hehehe I'll might just play with that for now?

should as simple as sudo apt-get install gnome-shell

or you can install from software center or synaptic

---

### Post by xtoudi on 2010-10-08
> **sgage said:**
> My compile fails in 22 as well, but with a different error
[Edit: I didn't scroll down - looks like the same error]

```
/home/sgage/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [1/1]
```

Oh well, the version in the repos works, but I want to see what's new.

1. jhbuild build
2. wait for error then on other terminal session:
>    rm ~/gnome-shell/install/lib64/*.la 

   or in case of 32bits
> 
rm ~/gnome-shell/install/lib/*.la

3. go back to main terminal session and use option 6


This always works in case of libgio errors.

---

### Post by sgage on 2010-10-08
> **xtoudi said:**
> 

This always works in case of libgio errors.

Well, it worked this time anyway! Thanks! I had already removed /usr/lib/*.la, but didn't get the ones in /gnome-shell.

---

### Post by terry_gardener on 2010-10-08
followed the advice above and it now works succesfully 

it doesn't look any different visually since the last time i used it, it is smoother though

---

### Post by sendblink23 on 2010-10-08
crap it sucks I can't test whats mentioned above... since my lan connection got lost(hasn't comeback since almost 2 hours ago - cable broadband connection)... no internet for my desktop :(

So, I will test now on a laptop I have on which the wireless works fine(I also have dsl connection, but that router is too far from my desktop)... hopefully it goes through entirely on this laptop

---
Update

Perfect, it ran 1st try on the laptop
Yes, I had to do on #22 what was mentioned on the above post:
> 1. jhbuild build
2. wait for error then on other terminal session:
Quote:
rm ~/gnome-shell/install/lib64/*.la
or in case of 32bits
Quote:
rm ~/gnome-shell/install/lib/*.la
3. go back to main terminal session and use option 6

---

### Post by a-user on 2010-10-08
compiling gnome-shell fails for me with this error:

```

checking for an ANSI C-conforming const... yes
checking for js-config... no
checking for JS... yes
checking for JS_CallTracer in -lmozjs... no
configure: error: SpiderMonkey is too old, Firefox 3 is required
*** Fehler während Phase configure von gjs: ########## Fehler beim Ausführen von ./autogen.sh --prefix /home/costin/gnome-shell/install --libdir '/home/costin/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [15/23]

```

i have either firefox 3 (namarok) as well as ff 4 latest beta from ppa. i also have xulrunner-1.9.2-dev installed which is the newest as far as i know.

---

### Post by moore.bryan on 2010-10-08
> **23dornot23d said:**
> [COLOR=Red]( In my previous Link all I showed was how I like the look of GNOME 3 with compiz ).[/COLOR]
Silly question, but why are you posting those queries in a thread devoted to GNOME Shell?

[quote=23dornot23d]Is this Gnome-Shell thing some kind of clique .... a little clique excluding any other input ?[/quote]
It's just that this thread is supposed to be about GS, not about GNOME 3, or at least that was always my understanding.

[quote=23dornot23d]* which as far as I can see excludes some USER's[/quote]
Huh?

---

### Post by 23dornot23d on 2010-10-08
> 
Silly question, but why are you posting those queries in a thread devoted to GNOME Shell?
I wanted to have a look to see **how far Gnome-Shell had progressed**
so I added the PPA as required to test it out. 

I used option 2 at the beginning of this thread to try to load Gnome-Shell up to see how it looked - that was the result so I posted it.

The result of a clean and clear desktop was what I got ...... so I posted what I saw with comments relating to it .... 
( What I saw was as a nice setup - I thought initially that the direction of Gnome-Shell had changed .... also I liked the idea of the availability of a clean Desktop in a PPA )

Since I posted it - this is the second response .... why do you think I asked the questions I asked ..... has it been cleared out till after the MM release ..... are compiz effects going to be added to Mutter ...... they are questions relating to what is happened and what I could see after adding the Ricotz PPA ...... 

Since my post numerous users have started to get interested in Gnome-Shell again ......

There was not a post for 2 days before I posted and the posts before I began were not related to Gnome-Shell until Merk brought it back on track ...... but if you want to pick the odd one line of text out of what I write and do not answer the questions ........ 
what am I to make of it .... 

Neither of the questions have been answered yet .... but I guess I should just now start to assume things - as nothing is clear on here .

Here is another question that may not get answered ..... where is the efficiency ?
I was using Alt+F2 when I began with Linux many moons ago ..... 

**What is the quick and efficient way to start an application up now ...... is it ALT+F2 .... ?**

---

### Post by sendblink23 on 2010-10-09
> **23dornot23d said:**
> I wanted to have a look to see **how far Gnome-Shell had progressed**
so I added the PPA as required to test it out. 

I used option 2 at the beginning of this thread to try to load Gnome-Shell up to see how it looked - that was the result so I posted it.

The result of a clean and clear desktop was what I got ...... so I posted what I saw with comments relating to it .... 
( What I saw was as a nice setup - I thought initially that the direction of Gnome-Shell had changed .... also I liked the idea of the availability of a clean Desktop in a PPA )

Since I posted it - this is the second response .... why do you think I asked the questions I asked ..... has it been cleared out till after the MM release ..... are compiz effects going to be added to Mutter ...... they are questions relating to what is happened and what I could see after adding the Ricotz PPA ...... 

Since my post numerous users have started to get interested in Gnome-Shell again ......

There was not a post for 2 days before I posted and the posts before I began were not related to Gnome-Shell until Merk brought it back on track ...... but if you want to pick the odd one line of text out of what I write and do not answer the questions ........ 
what am I to make of it .... 

Neither of the questions have been answered yet .... but I guess I should just now start to assume things - as nothing is clear on here .

Here is another question that may not get answered ..... where is the efficiency ?
I was using Alt+F2 when I began with Linux many moons ago ..... 

**What is the quick and efficient way to start an application up now ...... is it ALT+F2 .... ?**

just click on the Keyboard the "Windows Icon" that will open up the Shell thing(on which you will be directly typing for the search - which is used to search for the app you wish to open/use)... now I have no clue what would be for as in run commands, it must be another keyboard clicking combination

---

### Post by a-user on 2010-10-09
compiling gnome-shell fails for me with this error:

```

checking for an ANSI C-conforming const... yes
checking for js-config... no
checking for JS... yes
checking for JS_CallTracer in -lmozjs... no
configure: error: SpiderMonkey is too old, Firefox 3 is required
*** Fehler während Phase configure von gjs: ########## Fehler beim  Ausführen von ./autogen.sh --prefix /home/costin/gnome-shell/install  --libdir '/home/costin/gnome-shell/install/lib64'  --disable-static  --disable-gtk-doc  *** [15/23]

```i have either firefox 3 (namarok) as well as ff 4 latest beta  from ppa. i also have xulrunner-1.9.2-dev installed which is the newest  as far as i know.

---

### Post by 23meg on 2010-10-09
> **bash said:**
> Anyone got an idea or could point me to a resource about when they are planning to start implementing the new design? Last time I had a peak at the mailing lists I couldn't find anything about it. And from the commit log it doesn't appear like the have started at all, except for the universal access applet.

The initial commit is in the *overview-relayout* branch in git now.

---

### Post by bash on 2010-10-09
> **mgunes said:**
> The initial commit is in the *overview-relayout* branch in git now.

Thanks for the heads up, just discovered it as well. Now on to getting it compiled. For those interested there is a blog post on planet GNOME that shows the progress made so far:

***Current***

[[img]http://blogs.gnome.org/fmuellner/files/2010/10/Pantallazo-300x175.png[/img]](http://blogs.gnome.org/fmuellner/files/2010/10/Pantallazo.png)


***Target***

[[img]http://static.arstechnica.net/assets/2010/07/overview-application-picker-thumb-640xauto-15572.png[/img]](http://git.gnome.org/browse/gnome-shell-design/plain/mockups/static/overview-window-picker.png)


Source: [http://blogs.gnome.org/fmuellner/2010/10/05/from-the-land-of-shell/](http://blogs.gnome.org/fmuellner/2010/10/05/from-the-land-of-shell/)

---

### Post by phenest on 2010-10-09
What files and folders do I need to turn this into a .deb? Do I just need the stuff in the ~/gnome-shell/install folder? And should the 'include' and 'share' folders go into /usr?

---

### Post by marijus on 2010-10-09
how to build from the overview-relayout branch?

---

### Post by ronacc on 2010-10-09
for an interesting effect try running gnome-shell from a Lubuntu session . You get gnome-shell AND the Lubuntu DT complete with bottom pannel . see SS

---

### Post by Starks on 2010-10-09
gtk3 failing to build

```
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/eric/gnome-shell/source/gtk3/gtk/tmp-introspectXxfNfl/Gtk-3.0', '-export-dynamic', '-L.', '-L/home/eric/gnome-shell/install/lib', 'libgtk-x11-3.0.la', '-pthread', '-L/home/eric/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/eric/gnome-shell/source/gtk3/gtk/tmp-introspectXxfNfl/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/eric/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/eric/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/eric/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/eric/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 

```

---

### Post by chenxiaolong on 2010-10-09
On a fresh build (in Ubuntu 10.04 amd64), everything compiles correctly up until gnome-shell:

```
...
CCLD   libgnome-shell.la
  CC     test_theme-test-theme.o
  CCLD   test-theme
/home/maomao/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/maomao/gnome-shell/install/lib64/libclutter-glx-1.0.so: undefined reference to `g_object_class_install_properties'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/maomao/gnome-shell/install/lib64/libclutter-glx-1.0.so: undefined reference to `g_object_notify_by_pspec'
/home/maomao/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/maomao/gnome-shell/install/lib64/libclutter-glx-1.0.so: undefined reference to `g_source_set_name'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
/home/maomao/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_value_take_variant'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/maomao/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/maomao/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/maomao/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

```

It seems like gnome-shell is having problems linking to GTK 3?

---

### Post by xtoudi on 2010-10-09
> **chenxiaolong said:**
> 
It seems like gnome-shell is having problems linking to GTK 3?

Post #795 (previous page).

---

### Post by 23dornot23d on 2010-10-09
Thanks for answering my question sendblink23 ...... that explains exactly what is going to happen when this ever goes live .........

@Ronacc
Using Lubuntu makes it work well .... it also allows quick shortcuts to be placed on the side bars .....

I like this idea ..... better than having to go hunting for things ..... or remembering application names and typing them in to get them started .....
 
New Users are not going to know names of applications - (as some of the more experienced users will .....)

My thoughts .... 
If a user comes from another environment  
They may type in ....
 PAINT - for a paint application they need to use .... but they are not going to find one .
ie **Mypaint - Gimp - Pinta** ..... we know them by name ... new users don't 

Also for
 WORD - for a program that lets them create a document ..... 
ie **Abiword - Scribus - Openoffice **

Useful applications need to be available from the start ....... IMHO .....
________________________________________________________________

> **ronacc said:**
> for an interesting effect try running gnome-shell from a Lubuntu session . You get gnome-shell AND the Lubuntu DT complete with bottom pannel . see SS

I like this idea and it now makes it functional and more efficient , for starting applications up - it also means that the useful things are visible to the user from the
start.

________________________________________________________________

I did get some errors when doing this though .... from Lubuntu ..... 

```

keith@keith-laptop:~$ gnome-shell --replace
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
      JS LOG: GNOME Shell started at Sat Oct 09 2010 21:48:15 GMT+0200 (CET)
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
** Message: Error: Resource not found.
gstfilesrc.c(1055): gst_file_src_start (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstFileSrc:source:
No such file "/home/keith/Desktop/Harrier.wmv"

** Message: Error: Resource not found.
gstfilesrc.c(1055): gst_file_src_start (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstFileSrc:source:
No such file "/home/keith/Desktop/Safe_Sep.wmv"

totem-video-thumbnailer couldn't open file 'file:///home/keith/Desktop/Harrier.wmv'
totem-video-thumbnailer couldn't open file 'file:///home/keith/Desktop/Safe_Sep.wmv'
Reason: Location not found..
Reason: Location not found..

```[B]

[_But it is running ok_]("http://img297.imageshack.us/img297/3047/screenshot4jn.png")[/B][_ with Lubuntu_]("http://img297.imageshack.us/img297/3047/screenshot4jn.png") ...... Thank you .... for looking at my views on this - this has been constructive ..... some of the others seem to be sticking to the plan .... but ignoring any new constructive input ...... 

All I ever want from LINUX .... is that it wipes the floor with other OS's .....

Its only going to do that if New Users can make it work ......

 New Users - it needs to pull them into a better working environment ...... 

**( Please - anybody that has spent a lot of time working on this - I do not knock the work you are doing - I just want to see it succeed ..... and brainstorming and having other options for New Users and Old Users alike is going to make this a better system for all ...... ) **

---

### Post by xtoudi on 2010-10-09
[SIZE="4"]**[COLOR="Navy"]overview-relayout branch[/COLOR]**: how to do it :-)[/SIZE]

Blog about this
[http://blogs.gnome.org/fmuellner/2010/10/05/from-the-land-of-shell/](http://blogs.gnome.org/fmuellner/2010/10/05/from-the-land-of-shell/)

A few steps:

**_First:_**
Steps at first post of this thread are still _**required**_!!
Next get a whole GS and all required modulsets git clone - easy way to do that:
> jhbuild build

1. Remove or backup old GS
> rm  ~/gnome-shell/source/gnome-shell -rf
2. it's important to cd into right place
> cd  ~/gnome-shell/source/
3. Get the latest overview-relayout branch
> git clone git://git.gnome.org/gnome-shell -b overview-relayout
4. Build overview-relayout branch: make sure that other modules are ok (traditional 'jhbuild build' is done without errors) - below we are only compiling last gnome-shell modulset)
> jhbuild buildone -n gnome-shell -f

And we've got this awesome GS - this is mine GS

---

### Post by chenxiaolong on 2010-10-09
xtoudi: Thank you very much. That worked.

---

### Post by sendblink23 on 2010-10-09
@ xtoudi
Thanks it worked nicely for me too

---

### Post by Mblackwell on 2010-10-09
Sadly it makes the app panel a weird size (probably due to my 4:3 resolution, though I haven't been able to discuss it with anyone yet).

It's also ungodly slow for me, so I've stuck with master for now.

---

### Post by 23dornot23d on 2010-10-09
For some reason it fails right towards the end ....

```

root@keith-laptop:~/gnome-shell/source/gnome-shell# aptitude safe-upgrade
Resolving dependencies...                
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
                                         
root@keith-laptop:~/gnome-shell/source/gnome-shell# jhbuild build
*** Checking out glib *** [1/23]
git pull --rebase
Current branch master is up to date.
*** Skipping glib (not updated) *** [1/23]
*** Checking out gobject-introspection *** [2/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gobject-introspection (not updated) *** [2/23]
*** Checking out pixman *** [3/23]
*** Skipping pixman (not updated) *** [3/23]
*** Checking out cairo *** [4/23]
*** Skipping cairo (not updated) *** [4/23]
*** Checking out pango *** [5/23]
git pull --rebase
Current branch master is up to date.
*** Skipping pango (not updated) *** [5/23]
*** Checking out atk *** [6/23]
git pull --rebase
Current branch master is up to date.
*** Skipping atk (not updated) *** [6/23]
*** Checking out gdk-pixbuf *** [7/23]
git stash save jhbuild-stash
Saved working directory and index state On master: jhbuild-stash
HEAD is now at f047700 autogen: Explicitly allow libtool > 2.2
git pull --rebase
Current branch master is up to date.
git stash pop
# On branch master
# Changed but not updated:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#    modified:   po/bg.po
#    modified:   po/ca.po
#    modified:   po/el.po
#    modified:   po/nb.po
#    modified:   po/pa.po
#    modified:   po/pt_BR.po
#    modified:   po/ro.po
#    modified:   po/ru.po
#    modified:   po/zh_HK.po
#    modified:   po/zh_TW.po
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#    ABOUT-NLS
#    aclocal.m4
#    config.guess
#    config.h.in
#    config.rpath
#    config.sub
#    depcomp
#    gtk-doc.make
#    install-sh
#    ltmain.sh
#    m4/codeset.m4
#    m4/gettext.m4
#    m4/glibc2.m4
#    m4/glibc21.m4
#    m4/iconv.m4
#    m4/intdiv0.m4
#    m4/intl.m4
#    m4/intldir.m4
#    m4/intlmacosx.m4
#    m4/intmax.m4
#    m4/inttypes-pri.m4
#    m4/inttypes_h.m4
#    m4/lcmessage.m4
#    m4/lib-ld.m4
#    m4/lib-link.m4
#    m4/lib-prefix.m4
#    m4/lock.m4
#    m4/longlong.m4
#    m4/nls.m4
#    m4/po.m4
#    m4/printf-posix.m4
#    m4/progtest.m4
#    m4/size_max.m4
#    m4/stdint_h.m4
#    m4/uintmax_t.m4
#    m4/visibility.m4
#    m4/wchar_t.m4
#    m4/wint_t.m4
#    m4/xsize.m4
#    missing
#    po/Rules-quot
#    po/bg.po~
#    po/ca.po~
#    po/el.po~
#    po/nb.po~
#    po/pa.po~
#    po/pt_BR.po~
#    po/remove-potcdate.sed
#    po/ro.po~
#    po/ru.po~
#    po/stamp-po
#    po/zh_HK.po~
#    po/zh_TW.po~
no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (babe4b69c9cd28f0db3f56de263fcf2d547304e2)
*** Skipping gdk-pixbuf (not updated) *** [7/23]
*** Checking out gtk3 *** [8/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gtk3 (not updated) *** [8/23]
*** Checking out librsvg *** [9/23]
git pull --rebase
Current branch master is up to date.
*** Skipping librsvg (not updated) *** [9/23]
*** Checking out gtk-engines-3 *** [10/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gtk-engines-3 (not updated) *** [10/23]
*** Checking out json-glib *** [11/23]
git pull --rebase
Current branch master is up to date.
*** Skipping json-glib (not updated) *** [11/23]
*** Checking out clutter *** [12/23]
git pull --rebase
Current branch master is up to date.
*** Skipping clutter (not updated) *** [12/23]
*** Checking out gconf *** [13/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gconf (not updated) *** [13/23]
*** Checking out mutter *** [14/23]
git pull --rebase
Current branch master is up to date.
*** Skipping mutter (not updated) *** [14/23]
*** Checking out gjs *** [15/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gjs (not updated) *** [15/23]
*** Checking out vala *** [16/23]
*** Skipping vala (not updated) *** [16/23]
*** Checking out dconf *** [17/23]
git pull --rebase
Current branch master is up to date.
*** Skipping dconf (not updated) *** [17/23]
*** Checking out gnome-desktop-3 *** [18/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gnome-desktop-3 (not updated) *** [18/23]
*** Checking out gsettings-desktop-schemas *** [19/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gsettings-desktop-schemas (not updated) *** [19/23]
*** Checking out gnome-icon-theme *** [20/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gnome-icon-theme (not updated) *** [20/23]
*** Checking out gnome-icon-theme-symbolic *** [21/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gnome-icon-theme-symbolic (not updated) *** [21/23]
*** Checking out gnome-shell *** [22/23]
git pull --rebase
Current branch overview-relayout is up to date.
git show-ref --quiet --verify refs/heads/master
git checkout --track -b master origin/master
Branch master set up to track remote branch master from origin.
Switched to a new branch 'master'
*** Building gnome-shell *** [22/23]
make  
make  all-recursive
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/data'
 cd .. && /bin/bash /root/gnome-shell/source/gnome-shell/config/missing --run automake-1.11 --foreign data/Makefile
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell
 cd .. && /bin/bash ./config.status data/Makefile 
config.status: creating data/Makefile
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/data'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/js'
 cd .. && /bin/bash /root/gnome-shell/source/gnome-shell/config/missing --run automake-1.11 --foreign js/Makefile
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell
 cd .. && /bin/bash ./config.status js/Makefile 
config.status: creating js/Makefile
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/js'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/src'
make  all-am
make[3]: Entering directory `/root/gnome-shell/source/gnome-shell/src'
  CC     libgnome_shell_la-shell-app.lo
  CC     libgnome_shell_la-shell-app-system.lo
  CC     libgnome_shell_la-shell-window-tracker.lo
  CCLD   libgnome-shell.la
  CCLD   test-theme
/root/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/root/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```almost builds .... !!!

Tried to do it the way above ...... too

```

root@keith-laptop:~/gnome-shell/source/gnome-shell# rm ~/gnome-shell/source/gnome-shell -rf 
root@keith-laptop:~/gnome-shell/source/gnome-shell# cd ~/gnome-shell/source/ 
root@keith-laptop:~/gnome-shell/source# git clone git://git.gnome.org/gnome-shell -b overview-relayout 
Initialized empty Git repository in /root/gnome-shell/source/gnome-shell/.git/
remote: Counting objects: 12823, done.
remote: Compressing objects: 100% (5868/5868), done.
remote: Total 12823 (delta 9764), reused 8933 (delta 6708)
Receiving objects: 100% (12823/12823), 2.91 MiB | 216 KiB/s, done.
Resolving deltas: 100% (9764/9764), done.
root@keith-laptop:~/gnome-shell/source# jhbuild buildone -n gnome-shell -f 
*** Configuring gnome-shell *** [1/1]
./autogen.sh --prefix /root/gnome-shell/install --libdir '/root/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.67
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.1
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6b
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.27.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.1
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.25
checking for gnome-common >= 2.3.0...
  testing gnome-doc-common... found 2.28.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running libtoolize...
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: copying file `config/ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gnome-doc-common...
Running aclocal-1.11...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell
Running autoconf...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell
Running autoheader...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell
Running automake-1.11...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell
configure.ac:17: installing `config/compile'
configure.ac:21: installing `config/config.guess'
configure.ac:21: installing `config/config.sub'
configure.ac:9: installing `config/install-sh'
configure.ac:9: installing `config/missing'
src/Makefile.am: installing `config/depcomp'
Running ./configure --enable-maintainer-mode --prefix /root/gnome-shell/install --libdir /root/gnome-shell/install/lib --disable-static --disable-gtk-doc ...
configure: WARNING: unrecognized options: --disable-gtk-doc
checking for a BSD-compatible install... /usr/bin/install-check
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether NLS is requested... yes
checking for intltool >= 0.26... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.22... yes
checking for gconftool-2... /root/gnome-shell/install/bin/gconftool-2
Using config source xml:merged:/root/gnome-shell/install/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for a Python interpreter with version >= 2.5... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for GStreamer (needed for recording functionality)... yes
checking for TEST_SHELL_RECORDER... yes
checking for MUTTER_PLUGIN... yes
checking for JS_NewGlobalObject... no
checking for sn_startup_sequence_get_application_id... no
checking for TIDY... yes
checking for ST... yes
checking for GDMUSER... yes
checking for TRAY... yes
checking for fdwalk... no
checking for mallinfo... yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.27.1)
checking for mutter... /root/gnome-shell/install/bin/mutter
checking if mutter was compiled with GTK+-3.0... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating js/Makefile
config.status: creating src/Makefile
config.status: creating tests/Makefile
config.status: creating po/Makefile.in
config.status: creating man/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
configure: WARNING: unrecognized options: --disable-gtk-doc
Now type `make' to compile gnome-shell
*** Building gnome-shell *** [1/1]
make  
make  all-recursive
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/data'
  GEN    gnome-shell.desktop.in
  GEN    gnome-shell.desktop
  GEN    gnome-shell-clock-preferences.desktop.in
  GEN    gnome-shell-clock-preferences.desktop
LC_ALL=C /usr/bin/intltool-merge -x -u /tmp org.gnome.accessibility.magnifier.gschema.xml.in org.gnome.accessibility.magnifier.gschema.xml
Merging translations into org.gnome.accessibility.magnifier.gschema.xml.
CREATED org.gnome.accessibility.magnifier.gschema.xml
  GEN    org.gnome.accessibility.magnifier.gschema.valid
LC_ALL=C /usr/bin/intltool-merge -x -u /tmp org.gnome.shell.gschema.xml.in org.gnome.shell.gschema.xml
Merging translations into org.gnome.shell.gschema.xml.
CREATED org.gnome.shell.gschema.xml
  GEN    org.gnome.shell.gschema.valid
  GEN    gschemas.compiled
rm gnome-shell-clock-preferences.desktop.in gnome-shell.desktop.in
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/src'
  GEN    stamp-st-enum-types.h
  GEN    st-enum-types.c
  GEN    stamp-st-marshal.h
  GEN    st-marshal.c
  GEN    st.h
  GEN    stamp-na-marshal.h
  GEN    na-marshal.c
  GEN    stamp-shell-marshal.h
  GEN    shell-marshal.c
  GEN    stamp-shell-enum-types.h
  GEN    shell-enum-types.c
make  all-am
make[3]: Entering directory `/root/gnome-shell/source/gnome-shell/src'
  CC     libgdmuser_1_0_la-gdm-user.lo
  CC     libgdmuser_1_0_la-gdm-user-manager.lo
  CCLD   libgdmuser-1.0.la
  CC     libst_1_0_la-st-adjustment.lo
  CC     libst_1_0_la-st-bin.lo
  CC     libst_1_0_la-st-border-image.lo
  CC     libst_1_0_la-st-box-layout.lo
  CC     libst_1_0_la-st-box-layout-child.lo
  CC     libst_1_0_la-st-button.lo
  CC     libst_1_0_la-st-clickable.lo
  CC     libst_1_0_la-st-clipboard.lo
  CC     libst_1_0_la-st-container.lo
  CC     libst_1_0_la-st-drawing-area.lo
  CC     libst_1_0_la-st-entry.lo
  CC     libst_1_0_la-st-group.lo
  CC     libst_1_0_la-st-im-text.lo
  CC     libst_1_0_la-st-label.lo
  CC     libst_1_0_la-st-overflow-box.lo
  CC     libst_1_0_la-st-private.lo
  CC     libst_1_0_la-st-scrollable.lo
  CC     libst_1_0_la-st-scroll-bar.lo
  CC     libst_1_0_la-st-scroll-view.lo
  CC     libst_1_0_la-st-shadow.lo
  CC     libst_1_0_la-st-subtexture.lo
  CC     libst_1_0_la-st-table.lo
  CC     libst_1_0_la-st-table-child.lo
  CC     libst_1_0_la-st-texture-cache.lo
  CC     libst_1_0_la-st-theme.lo
  CC     libst_1_0_la-st-theme-context.lo
  CC     libst_1_0_la-st-theme-node.lo
  CC     libst_1_0_la-st-theme-node-drawing.lo
  CC     libst_1_0_la-st-theme-node-transition.lo
  CC     libst_1_0_la-st-tooltip.lo
  CC     libst_1_0_la-st-widget.lo
  CC     libst_1_0_la-st-enum-types.lo
  CC     libst_1_0_la-st-marshal.lo
  CCLD   libst-1.0.la
  CC     libtray_la-na-tray-child.lo
  CC     libtray_la-na-tray-manager.lo
  CC     libtray_la-na-marshal.lo
  CCLD   libtray.la
  CC     libgnome_shell_la-shell-marshal.lo
  CC     libgnome_shell_la-shell-enum-types.lo
  CC     libgnome_shell_la-gnome-shell-plugin.lo
  CC     libgnome_shell_la-shell-app.lo
  CC     libgnome_shell_la-shell-app-system.lo
  CC     libgnome_shell_la-shell-app-usage.lo
  CC     libgnome_shell_la-shell-arrow.lo
  CC     libgnome_shell_la-shell-doc-system.lo
  CC     libgnome_shell_la-shell-drawing.lo
  CC     libgnome_shell_la-shell-embedded-window.lo
  CC     libgnome_shell_la-shell-generic-container.lo
  CC     libgnome_shell_la-shell-gtk-embed.lo
  CC     libgnome_shell_la-shell-process.lo
  CC     libgnome_shell_la-shell-global.lo
  CC     libgnome_shell_la-shell-perf-log.lo
  CC     libgnome_shell_la-shell-slicer.lo
  CC     libgnome_shell_la-shell-stack.lo
  CC     libgnome_shell_la-shell-tray-icon.lo
  CC     libgnome_shell_la-shell-tray-manager.lo
  CC     libgnome_shell_la-shell-uri-util.lo
  CC     libgnome_shell_la-shell-window-tracker.lo
  CC     libgnome_shell_la-shell-wm.lo
  CC     libgnome_shell_la-shell-xfixes-cursor.lo
  CC     libgnome_shell_la-shell-recorder.lo
  CC     libgnome_shell_la-shell-recorder-src.lo
  CCLD   libgnome-shell.la
  CC     test_theme-test-theme.o
  CCLD   test-theme
/root/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/root/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [1/1]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```

---

### Post by sendblink23 on 2010-10-09
> **23dornot23d said:**
> For some reason it fails right towards the end ....

```

root@keith-laptop:~/gnome-shell/source/gnome-shell# aptitude safe-upgrade
Resolving dependencies...                
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
                                         
root@keith-laptop:~/gnome-shell/source/gnome-shell# jhbuild build
*** Checking out glib *** [1/23]
git pull --rebase
Current branch master is up to date.
*** Skipping glib (not updated) *** [1/23]
*** Checking out gobject-introspection *** [2/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gobject-introspection (not updated) *** [2/23]
*** Checking out pixman *** [3/23]
*** Skipping pixman (not updated) *** [3/23]
*** Checking out cairo *** [4/23]
*** Skipping cairo (not updated) *** [4/23]
*** Checking out pango *** [5/23]
git pull --rebase
Current branch master is up to date.
*** Skipping pango (not updated) *** [5/23]
*** Checking out atk *** [6/23]
git pull --rebase
Current branch master is up to date.
*** Skipping atk (not updated) *** [6/23]
*** Checking out gdk-pixbuf *** [7/23]
git stash save jhbuild-stash
Saved working directory and index state On master: jhbuild-stash
HEAD is now at f047700 autogen: Explicitly allow libtool > 2.2
git pull --rebase
Current branch master is up to date.
git stash pop
# On branch master
# Changed but not updated:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#    modified:   po/bg.po
#    modified:   po/ca.po
#    modified:   po/el.po
#    modified:   po/nb.po
#    modified:   po/pa.po
#    modified:   po/pt_BR.po
#    modified:   po/ro.po
#    modified:   po/ru.po
#    modified:   po/zh_HK.po
#    modified:   po/zh_TW.po
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#    ABOUT-NLS
#    aclocal.m4
#    config.guess
#    config.h.in
#    config.rpath
#    config.sub
#    depcomp
#    gtk-doc.make
#    install-sh
#    ltmain.sh
#    m4/codeset.m4
#    m4/gettext.m4
#    m4/glibc2.m4
#    m4/glibc21.m4
#    m4/iconv.m4
#    m4/intdiv0.m4
#    m4/intl.m4
#    m4/intldir.m4
#    m4/intlmacosx.m4
#    m4/intmax.m4
#    m4/inttypes-pri.m4
#    m4/inttypes_h.m4
#    m4/lcmessage.m4
#    m4/lib-ld.m4
#    m4/lib-link.m4
#    m4/lib-prefix.m4
#    m4/lock.m4
#    m4/longlong.m4
#    m4/nls.m4
#    m4/po.m4
#    m4/printf-posix.m4
#    m4/progtest.m4
#    m4/size_max.m4
#    m4/stdint_h.m4
#    m4/uintmax_t.m4
#    m4/visibility.m4
#    m4/wchar_t.m4
#    m4/wint_t.m4
#    m4/xsize.m4
#    missing
#    po/Rules-quot
#    po/bg.po~
#    po/ca.po~
#    po/el.po~
#    po/nb.po~
#    po/pa.po~
#    po/pt_BR.po~
#    po/remove-potcdate.sed
#    po/ro.po~
#    po/ru.po~
#    po/stamp-po
#    po/zh_HK.po~
#    po/zh_TW.po~
no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (babe4b69c9cd28f0db3f56de263fcf2d547304e2)
*** Skipping gdk-pixbuf (not updated) *** [7/23]
*** Checking out gtk3 *** [8/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gtk3 (not updated) *** [8/23]
*** Checking out librsvg *** [9/23]
git pull --rebase
Current branch master is up to date.
*** Skipping librsvg (not updated) *** [9/23]
*** Checking out gtk-engines-3 *** [10/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gtk-engines-3 (not updated) *** [10/23]
*** Checking out json-glib *** [11/23]
git pull --rebase
Current branch master is up to date.
*** Skipping json-glib (not updated) *** [11/23]
*** Checking out clutter *** [12/23]
git pull --rebase
Current branch master is up to date.
*** Skipping clutter (not updated) *** [12/23]
*** Checking out gconf *** [13/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gconf (not updated) *** [13/23]
*** Checking out mutter *** [14/23]
git pull --rebase
Current branch master is up to date.
*** Skipping mutter (not updated) *** [14/23]
*** Checking out gjs *** [15/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gjs (not updated) *** [15/23]
*** Checking out vala *** [16/23]
*** Skipping vala (not updated) *** [16/23]
*** Checking out dconf *** [17/23]
git pull --rebase
Current branch master is up to date.
*** Skipping dconf (not updated) *** [17/23]
*** Checking out gnome-desktop-3 *** [18/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gnome-desktop-3 (not updated) *** [18/23]
*** Checking out gsettings-desktop-schemas *** [19/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gsettings-desktop-schemas (not updated) *** [19/23]
*** Checking out gnome-icon-theme *** [20/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gnome-icon-theme (not updated) *** [20/23]
*** Checking out gnome-icon-theme-symbolic *** [21/23]
git pull --rebase
Current branch master is up to date.
*** Skipping gnome-icon-theme-symbolic (not updated) *** [21/23]
*** Checking out gnome-shell *** [22/23]
git pull --rebase
Current branch overview-relayout is up to date.
git show-ref --quiet --verify refs/heads/master
git checkout --track -b master origin/master
Branch master set up to track remote branch master from origin.
Switched to a new branch 'master'
*** Building gnome-shell *** [22/23]
make  
make  all-recursive
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/data'
 cd .. && /bin/bash /root/gnome-shell/source/gnome-shell/config/missing --run automake-1.11 --foreign data/Makefile
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell
 cd .. && /bin/bash ./config.status data/Makefile 
config.status: creating data/Makefile
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/data'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/js'
 cd .. && /bin/bash /root/gnome-shell/source/gnome-shell/config/missing --run automake-1.11 --foreign js/Makefile
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell
 cd .. && /bin/bash ./config.status js/Makefile 
config.status: creating js/Makefile
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/js'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/src'
make  all-am
make[3]: Entering directory `/root/gnome-shell/source/gnome-shell/src'
  CC     libgnome_shell_la-shell-app.lo
  CC     libgnome_shell_la-shell-app-system.lo
  CC     libgnome_shell_la-shell-window-tracker.lo
  CCLD   libgnome-shell.la
  CCLD   test-theme
/root/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/root/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```

almost builds .... !!!


Did you try what was mentioned a few posts back( [http://ubuntuforums.org/showpost.php?p=9940810&postcount=795](http://ubuntuforums.org/showpost.php?p=9940810&postcount=795) )... that I and some others had the same exact issue on #22... it worked for us

---

### Post by 23dornot23d on 2010-10-09
Ok cheers .... will have a look ty

Did that ,,,,, it went all the way through and completed successfully .... but when I did the 

gnome-shell --replace

it failed

```

make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/po'
Making all in man
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/man'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/man'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell'
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell'
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell'
*** Installing gnome-shell *** [22/23]
make install
Making install in data
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell/data'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/data'
make[2]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/root/gnome-shell/install/etc/gconf/gconf.xml.defaults /root/gnome-shell/install/bin/gconftool-2 --makefile-install-rule ./gnome-shell.schemas
Attached schema `/schemas/desktop/gnome/shell/windows/attach_modal_dialogs' to key `/desktop/gnome/shell/windows/attach_modal_dialogs'
Installed schema `/schemas/desktop/gnome/shell/windows/attach_modal_dialogs' for locale `C'
Attached schema `/schemas/desktop/gnome/shell/windows/button_layout' to key `/desktop/gnome/shell/windows/button_layout'
Installed schema `/schemas/desktop/gnome/shell/windows/button_layout' for locale `C'
Attached schema `/schemas/desktop/gnome/shell/windows/side_by_side_tiling' to key `/desktop/gnome/shell/windows/side_by_side_tiling'
Installed schema `/schemas/desktop/gnome/shell/windows/side_by_side_tiling' for locale `C'
test -z "/root/gnome-shell/install/share/applications" || /bin/mkdir -p "/root/gnome-shell/install/share/applications"
 /usr/bin/install-check -m 644 gnome-shell.desktop gnome-shell-clock-preferences.desktop '/root/gnome-shell/install/share/applications'
test -z "/root/gnome-shell/install/share/gnome-shell/images" || /bin/mkdir -p "/root/gnome-shell/install/share/gnome-shell/images"
 /usr/bin/install-check -m 644 close-black.svg magnifier.svg '/root/gnome-shell/install/share/gnome-shell/images'
test -z "/root/gnome-shell/install/share/gnome-shell" || /bin/mkdir -p "/root/gnome-shell/install/share/gnome-shell"
 /usr/bin/install-check -m 644 clock-preferences.ui '/root/gnome-shell/install/share/gnome-shell'
test -z "/root/gnome-shell/install/share/gnome-shell/theme" || /bin/mkdir -p "/root/gnome-shell/install/share/gnome-shell/theme"
 /usr/bin/install-check -m 644 theme/add-workspace.svg theme/close-window.svg theme/close.svg theme/corner-ripple.png theme/dialog-error.svg theme/gnome-shell.css theme/mosaic-view-active.svg theme/mosaic-view.svg theme/move-window-on-new.svg theme/process-working.png theme/remove-workspace.svg theme/scroll-button-down-hover.png theme/scroll-button-down.png theme/scroll-button-up-hover.png theme/scroll-button-up.png theme/scroll-hhandle.svg theme/scroll-vhandle.svg theme/section-more.svg theme/section-more-open.svg theme/separator-white.png theme/single-view-active.svg theme/single-view.svg theme/toggle-off-us.svg theme/toggle-off-intl.svg theme/toggle-on-us.svg theme/toggle-on-intl.svg theme/ws-switch-arrow-left.svg theme/ws-switch-arrow-right.svg '/root/gnome-shell/install/share/gnome-shell/theme'
test -z "/root/gnome-shell/install/etc/gconf/schemas" || /bin/mkdir -p "/root/gnome-shell/install/etc/gconf/schemas"
 /usr/bin/install-check -m 644 gnome-shell.schemas '/root/gnome-shell/install/etc/gconf/schemas'
test -z "/root/gnome-shell/install/etc/xdg/menus" || /bin/mkdir -p "/root/gnome-shell/install/etc/xdg/menus"
 /usr/bin/install-check -m 644 gs-applications.menu '/root/gnome-shell/install/etc/xdg/menus'
test -z "/root/gnome-shell/install/share/gnome-shell/shaders" || /bin/mkdir -p "/root/gnome-shell/install/share/gnome-shell/shaders"
 /usr/bin/install-check -m 644 shaders/dim-window.glsl '/root/gnome-shell/install/share/gnome-shell/shaders'
test -z "/root/gnome-shell/install/share/glib-2.0/schemas" || /bin/mkdir -p "/root/gnome-shell/install/share/glib-2.0/schemas"
/usr/bin/install-check -m 644 org.gnome.accessibility.magnifier.gschema.xml org.gnome.shell.gschema.xml "/root/gnome-shell/install/share/glib-2.0/schemas"
test -n "" || /root/gnome-shell/install/bin/glib-compile-schemas /root/gnome-shell/install/share/glib-2.0/schemas
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/data'
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell/data'
Making install in js
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell/js'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/root/gnome-shell/install/share/gnome-shell/js" || /bin/mkdir -p "/root/gnome-shell/install/share/gnome-shell/js"
/bin/mkdir -p '/root/gnome-shell/install/share/gnome-shell/js/ui/status'
 /usr/bin/install-check -m 644  ui/status/accessibility.js '/root/gnome-shell/install/share/gnome-shell/js/ui/status'
/bin/mkdir -p '/root/gnome-shell/install/share/gnome-shell/js/ui'
 /usr/bin/install-check -m 644  ui/altTab.js ui/appDisplay.js ui/appFavorites.js ui/boxpointer.js ui/calendar.js ui/chrome.js ui/dash.js ui/dnd.js ui/docDisplay.js ui/environment.js ui/extensionSystem.js ui/genericDisplay.js ui/iconGrid.js ui/lightbox.js ui/link.js ui/lookingGlass.js ui/magnifier.js ui/magnifierDBus.js ui/main.js ui/messageTray.js ui/notificationDaemon.js ui/overview.js ui/panel.js ui/panelMenu.js ui/placeDisplay.js ui/popupMenu.js ui/runDialog.js ui/scripting.js ui/search.js ui/shellDBus.js ui/statusIconDispatcher.js ui/statusMenu.js ui/telepathyClient.js ui/tweener.js ui/windowAttentionHandler.js ui/windowManager.js ui/workspace.js ui/workspacesView.js ui/workspaceSwitcherPopup.js '/root/gnome-shell/install/share/gnome-shell/js/ui'
/bin/mkdir -p '/root/gnome-shell/install/share/gnome-shell/js/prefs'
 /usr/bin/install-check -m 644  prefs/clockPreferences.js '/root/gnome-shell/install/share/gnome-shell/js/prefs'
/bin/mkdir -p '/root/gnome-shell/install/share/gnome-shell/js/misc'
 /usr/bin/install-check -m 644  misc/docInfo.js misc/fileUtils.js misc/format.js misc/gnomeSession.js misc/params.js misc/telepathy.js '/root/gnome-shell/install/share/gnome-shell/js/misc'
/bin/mkdir -p '/root/gnome-shell/install/share/gnome-shell/js/perf'
 /usr/bin/install-check -m 644  perf/core.js '/root/gnome-shell/install/share/gnome-shell/js/perf'
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/js'
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell/js'
Making install in src
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell/src'
make  install-am
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/src'
make[3]: Entering directory `/root/gnome-shell/source/gnome-shell/src'
test -z "/root/gnome-shell/install/bin" || /bin/mkdir -p "/root/gnome-shell/install/bin"
 /usr/bin/install-check gnome-shell gnome-shell-clock-preferences '/root/gnome-shell/install/bin'
test -z "/root/gnome-shell/install/libexec" || /bin/mkdir -p "/root/gnome-shell/install/libexec"
test -z "/root/gnome-shell/install/lib/mutter/plugins" || /bin/mkdir -p "/root/gnome-shell/install/lib/mutter/plugins"
 /bin/bash ../libtool   --mode=install /usr/bin/install-check   libgnome-shell.la '/root/gnome-shell/install/lib/mutter/plugins'
libtool: install: /usr/bin/install-check .libs/libgnome-shell.so /root/gnome-shell/install/lib/mutter/plugins/libgnome-shell.so
libtool: install: /usr/bin/install-check .libs/libgnome-shell.lai /root/gnome-shell/install/lib/mutter/plugins/libgnome-shell.la
libtool: finish: PATH="/root/gnome-shell/install/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/sbin" ldconfig -n /root/gnome-shell/install/lib/mutter/plugins
----------------------------------------------------------------------
Libraries have been installed in:
   /root/gnome-shell/install/lib/mutter/plugins

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/root/gnome-shell/install/lib/gnome-shell" || /bin/mkdir -p "/root/gnome-shell/install/lib/gnome-shell"
 /usr/bin/install-check -m 644 Shell-0.1.typelib St-1.0.typelib Gdm-1.0.typelib '/root/gnome-shell/install/lib/gnome-shell'
make[3]: Leaving directory `/root/gnome-shell/source/gnome-shell/src'
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/src'
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell/src'
Making install in tests
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell/tests'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/tests'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/tests'
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell/tests'
Making install in po
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell/po'
linguas="ar bg ca cs da de el en_GB es et fi fr ga gl he hu id it ja ko lt nb nl nn pa pl pt pt_BR ro ru sl sr sr@latin sv ta th tr uk vi zh_CN zh_HK zh_TW "; \
    for lang in $linguas; do \
      dir=/root/gnome-shell/install/share/locale/$lang/LC_MESSAGES; \
      /bin/bash /root/gnome-shell/source/gnome-shell/config/install-sh -d $dir; \
      if test -r $lang.gmo; then \
        /usr/bin/install-check -m 644 $lang.gmo $dir/gnome-shell.mo; \
        echo "installing $lang.gmo as $dir/gnome-shell.mo"; \
      else \
        /usr/bin/install-check -m 644 ./$lang.gmo $dir/gnome-shell.mo; \
        echo "installing ./$lang.gmo as" \
         "$dir/gnome-shell.mo"; \
      fi; \
      if test -r $lang.gmo.m; then \
        /usr/bin/install-check -m 644 $lang.gmo.m $dir/gnome-shell.mo.m; \
        echo "installing $lang.gmo.m as $dir/gnome-shell.mo.m"; \
      else \
        if test -r ./$lang.gmo.m ; then \
          /usr/bin/install-check -m 644 ./$lang.gmo.m \
        $dir/gnome-shell.mo.m; \
          echo "installing ./$lang.gmo.m as" \
           "$dir/gnome-shell.mo.m"; \
        else \
          true; \
        fi; \
      fi; \
    done
installing ar.gmo as /root/gnome-shell/install/share/locale/ar/LC_MESSAGES/gnome-shell.mo
installing bg.gmo as /root/gnome-shell/install/share/locale/bg/LC_MESSAGES/gnome-shell.mo
installing ca.gmo as /root/gnome-shell/install/share/locale/ca/LC_MESSAGES/gnome-shell.mo
installing cs.gmo as /root/gnome-shell/install/share/locale/cs/LC_MESSAGES/gnome-shell.mo
installing da.gmo as /root/gnome-shell/install/share/locale/da/LC_MESSAGES/gnome-shell.mo
installing de.gmo as /root/gnome-shell/install/share/locale/de/LC_MESSAGES/gnome-shell.mo
installing el.gmo as /root/gnome-shell/install/share/locale/el/LC_MESSAGES/gnome-shell.mo
installing en_GB.gmo as /root/gnome-shell/install/share/locale/en_GB/LC_MESSAGES/gnome-shell.mo
installing es.gmo as /root/gnome-shell/install/share/locale/es/LC_MESSAGES/gnome-shell.mo
installing et.gmo as /root/gnome-shell/install/share/locale/et/LC_MESSAGES/gnome-shell.mo
installing fi.gmo as /root/gnome-shell/install/share/locale/fi/LC_MESSAGES/gnome-shell.mo
installing fr.gmo as /root/gnome-shell/install/share/locale/fr/LC_MESSAGES/gnome-shell.mo
installing ga.gmo as /root/gnome-shell/install/share/locale/ga/LC_MESSAGES/gnome-shell.mo
installing gl.gmo as /root/gnome-shell/install/share/locale/gl/LC_MESSAGES/gnome-shell.mo
installing he.gmo as /root/gnome-shell/install/share/locale/he/LC_MESSAGES/gnome-shell.mo
installing hu.gmo as /root/gnome-shell/install/share/locale/hu/LC_MESSAGES/gnome-shell.mo
installing id.gmo as /root/gnome-shell/install/share/locale/id/LC_MESSAGES/gnome-shell.mo
installing it.gmo as /root/gnome-shell/install/share/locale/it/LC_MESSAGES/gnome-shell.mo
installing ja.gmo as /root/gnome-shell/install/share/locale/ja/LC_MESSAGES/gnome-shell.mo
installing ko.gmo as /root/gnome-shell/install/share/locale/ko/LC_MESSAGES/gnome-shell.mo
installing lt.gmo as /root/gnome-shell/install/share/locale/lt/LC_MESSAGES/gnome-shell.mo
installing nb.gmo as /root/gnome-shell/install/share/locale/nb/LC_MESSAGES/gnome-shell.mo
installing nl.gmo as /root/gnome-shell/install/share/locale/nl/LC_MESSAGES/gnome-shell.mo
installing nn.gmo as /root/gnome-shell/install/share/locale/nn/LC_MESSAGES/gnome-shell.mo
installing pa.gmo as /root/gnome-shell/install/share/locale/pa/LC_MESSAGES/gnome-shell.mo
installing pl.gmo as /root/gnome-shell/install/share/locale/pl/LC_MESSAGES/gnome-shell.mo
installing pt.gmo as /root/gnome-shell/install/share/locale/pt/LC_MESSAGES/gnome-shell.mo
installing pt_BR.gmo as /root/gnome-shell/install/share/locale/pt_BR/LC_MESSAGES/gnome-shell.mo
installing ro.gmo as /root/gnome-shell/install/share/locale/ro/LC_MESSAGES/gnome-shell.mo
installing ru.gmo as /root/gnome-shell/install/share/locale/ru/LC_MESSAGES/gnome-shell.mo
installing sl.gmo as /root/gnome-shell/install/share/locale/sl/LC_MESSAGES/gnome-shell.mo
installing sr.gmo as /root/gnome-shell/install/share/locale/sr/LC_MESSAGES/gnome-shell.mo
installing sr@latin.gmo as /root/gnome-shell/install/share/locale/sr@latin/LC_MESSAGES/gnome-shell.mo
installing sv.gmo as /root/gnome-shell/install/share/locale/sv/LC_MESSAGES/gnome-shell.mo
installing ta.gmo as /root/gnome-shell/install/share/locale/ta/LC_MESSAGES/gnome-shell.mo
installing th.gmo as /root/gnome-shell/install/share/locale/th/LC_MESSAGES/gnome-shell.mo
installing tr.gmo as /root/gnome-shell/install/share/locale/tr/LC_MESSAGES/gnome-shell.mo
installing uk.gmo as /root/gnome-shell/install/share/locale/uk/LC_MESSAGES/gnome-shell.mo
installing vi.gmo as /root/gnome-shell/install/share/locale/vi/LC_MESSAGES/gnome-shell.mo
installing zh_CN.gmo as /root/gnome-shell/install/share/locale/zh_CN/LC_MESSAGES/gnome-shell.mo
installing zh_HK.gmo as /root/gnome-shell/install/share/locale/zh_HK/LC_MESSAGES/gnome-shell.mo
installing zh_TW.gmo as /root/gnome-shell/install/share/locale/zh_TW/LC_MESSAGES/gnome-shell.mo
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell/po'
Making install in man
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell/man'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/root/gnome-shell/install/share/man/man1" || /bin/mkdir -p "/root/gnome-shell/install/share/man/man1"
 /usr/bin/install-check -m 644 gnome-shell.1 '/root/gnome-shell/install/share/man/man1'
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell/man'
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell/man'
make[1]: Entering directory `/root/gnome-shell/source/gnome-shell'
make[2]: Entering directory `/root/gnome-shell/source/gnome-shell'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/root/gnome-shell/source/gnome-shell'
make[1]: Leaving directory `/root/gnome-shell/source/gnome-shell'
*** success *** [23/23]
root@keith-laptop:~/gnome-shell/source/gnome-shell# gnome-shell --replaceTraceback (most recent call last):
  File "/root/gnome-shell/install/bin/gnome-shell", line 766, in <module>
    start_dconf_await_service()
  File "/root/gnome-shell/install/bin/gnome-shell", line 129, in start_dconf_await_service
    bus = dbus.SessionBus(mainloop=dbus_loop)
  File "/usr/lib/pymodules/python2.6/dbus/_dbus.py", line 219, in __new__
    mainloop=mainloop)
  File "/usr/lib/pymodules/python2.6/dbus/_dbus.py", line 108, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
root@keith-laptop:~/gnome-shell/source/gnome-shell# 


```


Do you have to reboot for this to work ?

---

### Post by ronacc on 2010-10-09
you shouldn't need to reboot . try from scratch building gnome -shell as a normal user , you should not be building it as root .

---

### Post by 23dornot23d on 2010-10-09
Cheers .... did not realise ... am now in a fresh install of Maverick ...will try as normal user and not root ....

Thanks but still no luck .... now on my desktop machine and running as normal user.

```

  CC     libgnome_shell_la-shell-tray-manager.lo
  CC     libgnome_shell_la-shell-uri-util.lo
  CC     libgnome_shell_la-shell-window-tracker.lo
  CC     libgnome_shell_la-shell-wm.lo
  CC     libgnome_shell_la-shell-xfixes-cursor.lo
  CCLD   libgnome-shell.la
libtool: link: cannot find the library `/home/keith/gnome-shell/install/lib/libgio-2.0.la' or unhandled argument `/home/keith/gnome-shell/install/lib/libgio-2.0.la'
make[3]: *** [libgnome-shell.la] Error 1
make[3]: Leaving directory `/home/keith/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/keith/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```

---

### Post by xtoudi on 2010-10-10
> **23dornot23d said:**
> Cheers .... did not realise ... am now in a fresh install of Maverick ...will try as normal user and not root ....

Thanks but still no luck .... now on my desktop machine and running as normal user.

```

  CC     libgnome_shell_la-shell-tray-manager.lo
  CC     libgnome_shell_la-shell-uri-util.lo
  CC     libgnome_shell_la-shell-window-tracker.lo
  CC     libgnome_shell_la-shell-wm.lo
  CC     libgnome_shell_la-shell-xfixes-cursor.lo
  CCLD   libgnome-shell.la
libtool: link: cannot find the library `/home/keith/gnome-shell/install/lib/libgio-2.0.la' or unhandled argument `/home/keith/gnome-shell/install/lib/libgio-2.0.la'
make[3]: *** [libgnome-shell.la] Error 1
make[3]: Leaving directory `/home/keith/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/keith/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```

rm ~/gnome-shell/install/lib/*.la
then if you get this error choose 6.

---

### Post by sendblink23 on 2010-10-10
> **xtoudi said:**
> rm ~/gnome-shell/install/lib/*.la
then if you get this error choose 6.

its quite funny he had teh same error as before & I already told him what to do previously - he did use it and it worked for him... no clue why didn't he try again the same thing when he exactly now got stuck on the same one LOL

---

### Post by xtoudi on 2010-10-10
> **sendblink23 said:**
> its quite funny he had teh same error as before & I already told him what to do previously - he did use it and it worked for him... no clue why didn't he try again the same thing when he exactly now got stuck on the same one LOL

I'm not sure he did it exactly as we told.

---

### Post by 23dornot23d on 2010-10-10
I have tried it at least 4 times if not more ..... but will continue .... others have done it right first time here .... I think .

Once you get used to wiping it and starting all over its not so bad ...... at least its on the laptop and the desktop now and fails at the same point ..... must be a coincidence.

Was tired yesterday though ..... seems a simple enough procedure ..... as you say.

It seems it downloads everything ok .....

It makes and compiles it ok .... right upto step 22 each time .... when it fails at exactly the same place  for both computers.

after removing it and trying again .... it said success .... but would not run ...... 

Am dying to see it working ...... so will do it one more time.


Ok just so you know exactly what I do ...... here is the procedure that I follow

Building from source is a bit more complicated than the GNOME instructions say. So fire up a terminal
[LIST=1]
[*]sudo  apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev  xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev  libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev  libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev  libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core  flex bison automake build-essential icon-naming-utils
[*]curl -O [http://git.gnome.org/browse/gnome-sh...build-setup.sh]("http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh")
[*]/bin/bash gnome-shell-build-setup.sh
[*]Get jhbuild (not a command line entry)
[LIST]
[*]For Lucid via repository, package name "jhbuild".
[*][From Jaunty]("http://packages.ubuntu.com/en/jaunty/jhbuild")
[*][From Debian]("http://packages.debian.org/unstable/devel/jhbuild")
[/LIST]
 
[*]jhbuild build
[/LIST]

Then when this fails ......

Then [goto this post]("http://ubuntuforums.org/showpost.php?p=9944930&postcount=813") and follow the procedure here

**_First:_**
Steps at first post of this thread are still _**required**_!!
Next get a whole GS and all required modulsets git clone - easy way to do that:
     Quote:
                                                 jhbuild build                                 
1. Remove or backup old GS
     Quote:
                                                 rm  ~/gnome-shell/source/gnome-shell -rf                                 
2. it's important to cd into right place
     Quote:
                                                 cd  ~/gnome-shell/source/                                 
3. Get the latest overview-relayout branch
     Quote:
                                                 git clone git://git.gnome.org/gnome-shell -b overview-relayout                                 
4. Build overview-relayout branch: make sure that other modules  are ok (traditional 'jhbuild build' is done without errors) - below we  are only compiling last gnome-shell modulset)
     Quote:
                                                 jhbuild buildone -n gnome-shell -f                                 
And we've got this awesome GS - this is mine GS


I then go to [this post]("http://ubuntuforums.org/showpost.php?p=9940810&postcount=795") and do the commands here ....

rm ~/gnome-shell/install/lib/*.la 



then once its wiped start all over again ..... ok seems easy enough to follow .....


Ok we start again ..... I will show each step

Step 1 ....

A clean install of Maverick ...... must do this ... first so we repeat the procedure properly .......

---

### Post by xtoudi on 2010-10-10
> **23dornot23d said:**
> 
Ok we start again ..... I will show each step

Step 1 ....

A clean install of Maverick ...... must do this ... first so we repeat the procedure properly .......

Listen - just do the steps at first post.

Then when error will appear (during 'jhbuild build') open second terminal and:
>  rm ~/gnome-shell/install/lib/*.la
or if you have 64bit
>  rm ~/gnome-shell/install/lib64/*.la
after that go back to first terminal and choos 6, write 'yes' - this will download fresh git clone of GS and will start compiling it. 
It should work.

Forget at the moment about compiling overview-relayout branch. 'Clean' gnome-shell is enough for you to testing.

---

### Post by 23dornot23d on 2010-10-10
Ok will do this now .... thank you ...

Ok Step ONE

```

root@keith-laptop:/home/keith# sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
curl is already the newest version.
libgl1-mesa-dev is already the newest version.
libgl1-mesa-dev set to manually installed.
libgtk2.0-dev is already the newest version.
libgtk2.0-dev set to manually installed.
mesa-common-dev is already the newest version.
mesa-common-dev set to manually installed.
python-dev is already the newest version.
python-dev set to manually installed.
xserver-xephyr is already the newest version.
xserver-xephyr set to manually installed.
mesa-utils is already the newest version.
The following extra packages will be installed:
  autoconf autotools-dev docbook docbook-dsssl docbook-to-man git intltool
  jade libdbus-1-dev liberror-perl libidl-dev libiw-dev libjpeg62-dev
  libltdl-dev libncurses5-dev libnotify-dev libnspr4-dev libnss3-dev
  liborbit2-dev libsp1c2 libtiffxx0c2 libtool libxres-dev orbit2 sp
  x11proto-resource-dev xulrunner-1.9.2-dev
Suggested packages:
  autoconf2.13 autoconf-archive gnu-standards autoconf-doc bison-doc psgml
  docbook-defguide jadetex docbook-dsssl-doc git-doc git-arch git-cvs git-svn
  git-email git-daemon-run git-gui gitk gitweb gstreamer0.10-doc libtool-doc
  automaken gfortran fortran95-compiler gcj
The following NEW packages will be installed
  autoconf automake autotools-dev bison docbook docbook-dsssl docbook-to-man
  flex git git-core gnome-common gtk-doc-tools icon-naming-utils intltool jade
  libcroco3-dev libdbus-1-dev libdbus-glib-1-dev liberror-perl libffi-dev
  libgconf2-dev libgnome-desktop-dev libgnome-menu-dev libgstreamer0.10-dev
  libidl-dev libiw-dev libjpeg62-dev libltdl-dev libncurses5-dev libnotify-dev
  libnspr4-dev libnss3-dev liborbit2-dev libreadline5-dev librsvg2-dev
  libsp1c2 libtiff4-dev libtiffxx0c2 libtool libwnck-dev libxres-dev orbit2 sp
  x11proto-resource-dev xulrunner-1.9.2-dev xulrunner-dev
0 upgraded, 46 newly installed, 0 to remove and 13 not upgraded.
Need to get 22.5MB of archives.
After this operation, 94.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ maverick/main xulrunner-1.9.2-dev i386 1.9.2.12~hg20101010r34669+nobinonly-0ubuntu1~umd1 [5,500kB]
Get:2 http://fr.archive.ubuntu.com/ubuntu/ maverick/main flex i386 2.5.35-9.1 [244kB]
Get:3 http://fr.archive.ubuntu.com/ubuntu/ maverick/main x11proto-resource-dev all 1.1.0-1 [4,106B]
Get:4 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libxres-dev i386 2:1.0.4-1 [12.9kB]
Get:5 http://fr.archive.ubuntu.com/ubuntu/ maverick/main autoconf all 2.67-2ubuntu1 [569kB]
Get:6 http://fr.archive.ubuntu.com/ubuntu/ maverick/main autotools-dev all 20100122.1 [70.7kB]
Get:7 http://fr.archive.ubuntu.com/ubuntu/ maverick/main automake all 1:1.11.1-1 [608kB]
Get:8 http://fr.archive.ubuntu.com/ubuntu/ maverick/main bison i386 1:2.4.1.dfsg-3 [468kB]
Get:9 http://fr.archive.ubuntu.com/ubuntu/ maverick/main docbook all 4.5-4 [450kB]
Get:10 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libsp1c2 i386 1.3.4-1.2.1-47build3 [1,491kB]
Get:11 http://fr.archive.ubuntu.com/ubuntu/ maverick/main jade i386 1.2.1-47build3 [305kB]
Get:12 http://fr.archive.ubuntu.com/ubuntu/ maverick/main docbook-dsssl all 1.79-6 [344kB]
Get:13 http://fr.archive.ubuntu.com/ubuntu/ maverick/main sp i386 1.3.4-1.2.1-47build3 [173kB]
Get:14 http://fr.archive.ubuntu.com/ubuntu/ maverick/main docbook-to-man i386 1:2.0.0-28 [72.4kB]
Get:15 http://fr.archive.ubuntu.com/ubuntu/ maverick/main liberror-perl all 0.17-1 [23.8kB]
Get:16 http://fr.archive.ubuntu.com/ubuntu/ maverick/main git i386 1:1.7.1-1.1 [5,784kB]
Get:17 http://fr.archive.ubuntu.com/ubuntu/ maverick/main git-core all 1:1.7.1-1.1 [1,352B]
Get:18 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libtool i386 2.2.6b-2ubuntu1 [524kB]
Get:19 http://fr.archive.ubuntu.com/ubuntu/ maverick/main intltool all 0.41.1-1 [103kB]
Get:20 http://fr.archive.ubuntu.com/ubuntu/ maverick/main gnome-common all 2.28.0-1 [16.0kB]
Get:21 http://fr.archive.ubuntu.com/ubuntu/ maverick/main gtk-doc-tools all 1.15-1ubuntu1 [177kB]
Get:22 http://fr.archive.ubuntu.com/ubuntu/ maverick/main icon-naming-utils all 0.8.90-2 [11.5kB]
Get:23 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libcroco3-dev i386 0.6.2-1 [118kB]
Get:24 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libdbus-1-dev i386 1.4.0-0ubuntu1 [26.2kB]
Get:25 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libdbus-glib-1-dev i386 0.88-2 [100kB]
Get:26 http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ maverick/main xulrunner-dev i386 1.9.2.12~hg20101010r34669+nobinonly-0ubuntu1~umd1 [29.3kB]
Get:27 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libidl-dev i386 0.8.14-0.1 [84.0kB]
Get:28 http://fr.archive.ubuntu.com/ubuntu/ maverick/main liborbit2-dev i386 1:2.14.18-0.1 [378kB]
Get:29 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libgconf2-dev i386 2.31.91-0ubuntu3 [231kB]
Get:30 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libgnome-desktop-dev i386 1:2.32.0-0ubuntu1 [118kB]
Get:31 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libgnome-menu-dev i386 2.30.4-0ubuntu1 [47.0kB]
Get:32 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libgstreamer0.10-dev i386 0.10.30-1build2 [927kB]
Get:33 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libjpeg62-dev i386 6b-16.1 [188kB]
Get:34 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libltdl-dev i386 2.2.6b-2ubuntu1 [193kB]
Get:35 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libncurses5-dev i386 5.7+20100626-0ubuntu1 [1,580kB]
Get:36 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libnotify-dev i386 0.5.0-2ubuntu1 [16.2kB]
Get:37 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libnspr4-dev i386 4.8.6-0ubuntu1 [263kB]
Get:38 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libnss3-dev i386 3.12.7-0ubuntu1 [264kB]
Get:39 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libreadline5-dev i386 5.2-7build1 [224kB]
Get:40 http://fr.archive.ubuntu.com/ubuntu/ maverick/main librsvg2-dev i386 2.32.0-0ubuntu1 [133kB]
Get:41 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libtiffxx0c2 i386 3.9.4-2 [6,422B]
Get:42 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libtiff4-dev i386 3.9.4-2 [247kB]
Get:43 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libwnck-dev i386 1:2.30.5-0ubuntu1 [242kB]
Get:44 http://fr.archive.ubuntu.com/ubuntu/ maverick/main orbit2 i386 1:2.14.18-0.1 [11.4kB]
Get:45 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libiw-dev i386 30~pre9-3ubuntu4 [59.0kB]
Get:46 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libffi-dev i386 3.0.9-2ubuntu2 [95.2kB]
Fetched 22.5MB in 1min 27s (258kB/s)                                           
Extract templates from packages: 100%
Selecting previously deselected package flex.
(Reading database ... 328044 files and directories currently installed.)
Unpacking flex (from .../flex_2.5.35-9.1_i386.deb) ...
Selecting previously deselected package x11proto-resource-dev.
Unpacking x11proto-resource-dev (from .../x11proto-resource-dev_1.1.0-1_all.deb) ...
Selecting previously deselected package libxres-dev.
Unpacking libxres-dev (from .../libxres-dev_2%3a1.0.4-1_i386.deb) ...
Selecting previously deselected package autoconf.
Unpacking autoconf (from .../autoconf_2.67-2ubuntu1_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20100122.1_all.deb) ...
Selecting previously deselected package automake.
Unpacking automake (from .../automake_1%3a1.11.1-1_all.deb) ...
Selecting previously deselected package bison.
Unpacking bison (from .../bison_1%3a2.4.1.dfsg-3_i386.deb) ...
Selecting previously deselected package docbook.
Unpacking docbook (from .../archives/docbook_4.5-4_all.deb) ...
Selecting previously deselected package libsp1c2.
Unpacking libsp1c2 (from .../libsp1c2_1.3.4-1.2.1-47build3_i386.deb) ...
Selecting previously deselected package jade.
Unpacking jade (from .../jade_1.2.1-47build3_i386.deb) ...
Selecting previously deselected package docbook-dsssl.
Unpacking docbook-dsssl (from .../docbook-dsssl_1.79-6_all.deb) ...
Selecting previously deselected package sp.
Unpacking sp (from .../sp_1.3.4-1.2.1-47build3_i386.deb) ...
Selecting previously deselected package docbook-to-man.
Unpacking docbook-to-man (from .../docbook-to-man_1%3a2.0.0-28_i386.deb) ...
Selecting previously deselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package git.
Unpacking git (from .../git_1%3a1.7.1-1.1_i386.deb) ...
Selecting previously deselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.7.1-1.1_all.deb) ...
Selecting previously deselected package libtool.
Unpacking libtool (from .../libtool_2.2.6b-2ubuntu1_i386.deb) ...
Selecting previously deselected package intltool.
Unpacking intltool (from .../intltool_0.41.1-1_all.deb) ...
Selecting previously deselected package gnome-common.
Unpacking gnome-common (from .../gnome-common_2.28.0-1_all.deb) ...
Selecting previously deselected package gtk-doc-tools.
Unpacking gtk-doc-tools (from .../gtk-doc-tools_1.15-1ubuntu1_all.deb) ...
Selecting previously deselected package icon-naming-utils.
Unpacking icon-naming-utils (from .../icon-naming-utils_0.8.90-2_all.deb) ...
Selecting previously deselected package libcroco3-dev.
Unpacking libcroco3-dev (from .../libcroco3-dev_0.6.2-1_i386.deb) ...
Selecting previously deselected package libdbus-1-dev.
Unpacking libdbus-1-dev (from .../libdbus-1-dev_1.4.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libdbus-glib-1-dev.
Unpacking libdbus-glib-1-dev (from .../libdbus-glib-1-dev_0.88-2_i386.deb) ...
Selecting previously deselected package libidl-dev.
Unpacking libidl-dev (from .../libidl-dev_0.8.14-0.1_i386.deb) ...
Selecting previously deselected package liborbit2-dev.
Unpacking liborbit2-dev (from .../liborbit2-dev_1%3a2.14.18-0.1_i386.deb) ...
Selecting previously deselected package libgconf2-dev.
Unpacking libgconf2-dev (from .../libgconf2-dev_2.31.91-0ubuntu3_i386.deb) ...
Selecting previously deselected package libgnome-desktop-dev.
Unpacking libgnome-desktop-dev (from .../libgnome-desktop-dev_1%3a2.32.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgnome-menu-dev.
Unpacking libgnome-menu-dev (from .../libgnome-menu-dev_2.30.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgstreamer0.10-dev.
Unpacking libgstreamer0.10-dev (from .../libgstreamer0.10-dev_0.10.30-1build2_i386.deb) ...
Selecting previously deselected package libjpeg62-dev.
Unpacking libjpeg62-dev (from .../libjpeg62-dev_6b-16.1_i386.deb) ...
Selecting previously deselected package libltdl-dev.
Unpacking libltdl-dev (from .../libltdl-dev_2.2.6b-2ubuntu1_i386.deb) ...
Selecting previously deselected package libncurses5-dev.
Unpacking libncurses5-dev (from .../libncurses5-dev_5.7+20100626-0ubuntu1_i386.deb) ...
Selecting previously deselected package libnotify-dev.
Unpacking libnotify-dev (from .../libnotify-dev_0.5.0-2ubuntu1_i386.deb) ...
Selecting previously deselected package libnspr4-dev.
Unpacking libnspr4-dev (from .../libnspr4-dev_4.8.6-0ubuntu1_i386.deb) ...
Selecting previously deselected package libnss3-dev.
Unpacking libnss3-dev (from .../libnss3-dev_3.12.7-0ubuntu1_i386.deb) ...
Selecting previously deselected package libreadline5-dev.
Unpacking libreadline5-dev (from .../libreadline5-dev_5.2-7build1_i386.deb) ...
Selecting previously deselected package librsvg2-dev.
Unpacking librsvg2-dev (from .../librsvg2-dev_2.32.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libtiffxx0c2.
Unpacking libtiffxx0c2 (from .../libtiffxx0c2_3.9.4-2_i386.deb) ...
Selecting previously deselected package libtiff4-dev.
Unpacking libtiff4-dev (from .../libtiff4-dev_3.9.4-2_i386.deb) ...
Selecting previously deselected package libwnck-dev.
Unpacking libwnck-dev (from .../libwnck-dev_1%3a2.30.5-0ubuntu1_i386.deb) ...
Selecting previously deselected package orbit2.
Unpacking orbit2 (from .../orbit2_1%3a2.14.18-0.1_i386.deb) ...
Selecting previously deselected package libiw-dev.
Unpacking libiw-dev (from .../libiw-dev_30~pre9-3ubuntu4_i386.deb) ...
Selecting previously deselected package xulrunner-1.9.2-dev.
Unpacking xulrunner-1.9.2-dev (from .../xulrunner-1.9.2-dev_1.9.2.12~hg20101010r34669+nobinonly-0ubuntu1~umd1_i386.deb) ...
Selecting previously deselected package xulrunner-dev.
Unpacking xulrunner-dev (from .../xulrunner-dev_1.9.2.12~hg20101010r34669+nobinonly-0ubuntu1~umd1_i386.deb) ...
Selecting previously deselected package libffi-dev.
Unpacking libffi-dev (from .../libffi-dev_3.0.9-2ubuntu2_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 5 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up flex (2.5.35-9.1) ...
Setting up x11proto-resource-dev (1.1.0-1) ...
Setting up libxres-dev (2:1.0.4-1) ...
Setting up autoconf (2.67-2ubuntu1) ...
Setting up autotools-dev (20100122.1) ...
Setting up automake (1:1.11.1-1) ...
update-alternatives: using /usr/bin/automake-1.11 to provide /usr/bin/automake (automake) in auto mode.
Setting up bison (1:2.4.1.dfsg-3) ...
update-alternatives: using /usr/bin/bison.yacc to provide /usr/bin/yacc (yacc) in auto mode.
Setting up docbook (4.5-4) ...
Setting up libsp1c2 (1.3.4-1.2.1-47build3) ...
Setting up jade (1.2.1-47build3) ...
Setting up docbook-dsssl (1.79-6) ...
Setting up sp (1.3.4-1.2.1-47build3) ...
Setting up docbook-to-man (1:2.0.0-28) ...
Setting up liberror-perl (0.17-1) ...
Setting up git (1:1.7.1-1.1) ...
Setting up git-core (1:1.7.1-1.1) ...
Setting up libtool (2.2.6b-2ubuntu1) ...
Setting up intltool (0.41.1-1) ...
Setting up gnome-common (2.28.0-1) ...
Setting up gtk-doc-tools (1.15-1ubuntu1) ...
Setting up icon-naming-utils (0.8.90-2) ...
Setting up libcroco3-dev (0.6.2-1) ...
Setting up libdbus-1-dev (1.4.0-0ubuntu1) ...
Setting up libdbus-glib-1-dev (0.88-2) ...
Setting up libidl-dev (0.8.14-0.1) ...
Setting up liborbit2-dev (1:2.14.18-0.1) ...
Setting up libgconf2-dev (2.31.91-0ubuntu3) ...
Setting up libgnome-desktop-dev (1:2.32.0-0ubuntu1) ...
Setting up libgnome-menu-dev (2.30.4-0ubuntu1) ...
Setting up libgstreamer0.10-dev (0.10.30-1build2) ...
Setting up libjpeg62-dev (6b-16.1) ...
Setting up libltdl-dev (2.2.6b-2ubuntu1) ...
Setting up libncurses5-dev (5.7+20100626-0ubuntu1) ...
Setting up libnotify-dev (0.5.0-2ubuntu1) ...
Setting up libnspr4-dev (4.8.6-0ubuntu1) ...
Setting up libnss3-dev (3.12.7-0ubuntu1) ...
Setting up libreadline5-dev (5.2-7build1) ...
Ignoring install-info called from maintainer script
The package libreadline5-dev should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package libreadline5-dev should be rebuilt with new debhelper to get trigger support
Setting up librsvg2-dev (2.32.0-0ubuntu1) ...
Setting up libtiffxx0c2 (3.9.4-2) ...
Setting up libtiff4-dev (3.9.4-2) ...
Setting up libwnck-dev (1:2.30.5-0ubuntu1) ...
Setting up orbit2 (1:2.14.18-0.1) ...
Setting up libiw-dev (30~pre9-3ubuntu4) ...
Setting up xulrunner-1.9.2-dev (1.9.2.12~hg20101010r34669+nobinonly-0ubuntu1~umd1) ...
Setting up xulrunner-dev (1.9.2.12~hg20101010r34669+nobinonly-0ubuntu1~umd1) ...
Setting up libffi-dev (3.0.9-2ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@keith-laptop:/home/keith# uname -a
Linux keith-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
root@keith-laptop:/home/keith# 


```Ok that seemed to go ok

Step 2

```

root@keith-laptop:/home/keith# curl -O http://git.gnome.org/browse/gnome-sh...build-setup.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2609  100  2609    0     0   5624      0 --:--:-- --:--:-- --:--:-- 10562
root@keith-laptop:/home/keith# exit
exit


```That appeared to go ok ..... but had to run it as root ..... (if not root it would fail to create it)
```

keith@keith-laptop:~$ curl -O http://git.gnome.org/browse/gnome-sh...build-setup.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0Warning: Failed to create the file gnome-sh...build-setup.sh: Permission 
Warning: denied
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
curl: (23) Failed writing body (0 != 488)

```[COLOR=Red]


**I Guess I should not proceed beyond here ...... as it fails ....**

**So what should be happening here > ?**

Step 3

[/COLOR]```
 [COLOR=Red]
keith@keith-laptop:~$ /bin/bash gnome-shell-build-setup.sh
/bin/bash: gnome-shell-build-setup.sh: No such file or directory

[/COLOR]
```That is supposed to run the script I guess .... but it will not for me .... even If I am root .... as it says it does not exist.


[B]SO THE QUESTION IS - IS THIS COMMAND RIGHT .....  others have got by here without a problem .... I guess .....

so is my system missing something ?
[/B]
___________________________________________________________________________________________________


**I do try to get it to work .....** with my limited knowledge of how its meant to work ...... its a script so shouldn't it work anywhere 
if its pointing to the right directories !!!

I run the script after downloading it ...... and making it executable ..... though ..... maybe this is where I go wrong !!!

I use this link to download the script file [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh)

Go to properties ..... make it executable and .... 
Then run it !!!!

Which gives a error saying

Please run 'sudo apt-get install libjasper-dev ' and try again.


So now I add it ....

```

keith@keith-laptop:~/Desktop$ sudo apt-get install libjasper-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  libjasper-dev
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 550kB of archives.
After this operation, 1,176kB of additional disk space will be used.
Get:1 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libjasper-dev i386 1.900.1-7 [550kB]
Fetched 550kB in 2s (220kB/s)         
Selecting previously deselected package libjasper-dev.
(Reading database ... 334830 files and directories currently installed.)
Unpacking libjasper-dev (from .../libjasper-dev_1.900.1-7_i386.deb) ...
Setting up libjasper-dev (1.900.1-7) ...
keith@keith-laptop:~/Desktop$ 


```Maybe this is where I go wrong ......

I run the script ... but does it matter where I run it from > ?

```

keith@keith-laptop:~/Desktop$ ./gnome-shell-build-setup.sh
Created /home/keith/Source
Checking out jhbuild into /home/keith/Source/jhbuild ... remote: Counting objects: 24043, done.
remote: Compressing objects: 100% (6895/6895), done.
remote: Total 24043 (delta 18789), reused 21841 (delta 17068)
Receiving objects: 100% (24043/24043), 4.49 MiB | 218 KiB/s, done.
Resolving deltas: 100% (18789/18789), done.
done
Installing jhbuild...
Writing ~/.jhbuildrc ... done
Writing example ~/.jhbuildrc-custom ... done
PATH does not contain /home/keith/bin, it is recommended that you add that.

Done.
keith@keith-laptop:~/Desktop$ 


```Step 4

```

root@keith-laptop:/# aptitude install jhbuild
The following NEW packages will be installed:
  cvs{a} jhbuild libsvn1{a} mercurial{a} mercurial-common{a} subversion{a} 
0 packages upgraded, 6 newly installed, 0 to remove and 13 not upgraded.
Need to get 4,950kB of archives. After unpacking 19.4MB will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://fr.archive.ubuntu.com/ubuntu/ maverick/main cvs i386 1:1.12.13-12ubuntu1 [1,685kB]
Get:2 http://fr.archive.ubuntu.com/ubuntu/ maverick/universe jhbuild i386 2.29.2-1 [679kB]
Get:3 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libsvn1 i386 1.6.12dfsg-1ubuntu1 [839kB]
Get:4 http://fr.archive.ubuntu.com/ubuntu/ maverick/universe mercurial-common all 1.6.3-1 [1,320kB]
Get:5 http://fr.archive.ubuntu.com/ubuntu/ maverick/universe mercurial i386 1.6.3-1 [53.2kB]
Get:6 http://fr.archive.ubuntu.com/ubuntu/ maverick/main subversion i386 1.6.12dfsg-1ubuntu1 [374kB]
Fetched 4,950kB in 19s (253kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package cvs.
(Reading database ... 334859 files and directories currently installed.)
Unpacking cvs (from .../cvs_1%3a1.12.13-12ubuntu1_i386.deb) ...
Selecting previously deselected package jhbuild.
Unpacking jhbuild (from .../jhbuild_2.29.2-1_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.6.12dfsg-1ubuntu1_i386.deb) ...
Selecting previously deselected package mercurial-common.
Unpacking mercurial-common (from .../mercurial-common_1.6.3-1_all.deb) ...
Selecting previously deselected package mercurial.
Unpacking mercurial (from .../mercurial_1.6.3-1_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.6.12dfsg-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up cvs (1:1.12.13-12ubuntu1) ...
Ignoring install-info called from maintainer script
The package cvs should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package cvs should be rebuilt with new debhelper to get trigger support
Setting up jhbuild (2.29.2-1) ...
Setting up libsvn1 (1.6.12dfsg-1ubuntu1) ...
Setting up mercurial-common (1.6.3-1) ...
Setting up mercurial (1.6.3-1) ...

Creating config file /etc/mercurial/hgrc.d/hgext.rc with new version
Setting up subversion (1.6.12dfsg-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
                                         
root@keith-laptop:/# 


```Step 5

jhbuild build

It now downloads and builds ...... but fails at stage 22 normally .... 

[B]I guess at stage 3 .... you know what to do as you build it ok ..... "as for me" .... any help would be appreciated ..........
to go beyond this stage ......

Seeing as nobody is around at the moment .... I will put the script in the 
/bin

and run it from there ...... see if that works ....
[/B]

---

### Post by Mblackwell on 2010-10-10
sh gnome-shell-build-setup.sh

---

### Post by xtoudi on 2010-10-10
Step 2 again (**not as root - do not use root during the whole process of compiling GS**):

```
cd ~
curl -O [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh)

```

LOOK AT YOUR URL! You can't just copy  this - there's URL inside!!

And do this and next step in your home dir.

---

### Post by ronacc on 2010-10-10
why are you running as root all the time ? That is very bad practice . You should run as a regular user and use sudo ( or gksudo ) for tasks that need root privileges . The only reason to run as root would be heavy duty maintenance work .

---

### Post by xtoudi on 2010-10-10
> **23dornot23d said:**
> 

Maybe this is where I go wrong ......

I run the script ... but does it need to be in /bin/bash/

Script must be in your HOME dir but now it has root privilegees, that's all. Now you have use root:

> cd ~
sudo chown YOUR_NAME.YOUR_NAME gnome-shell-build-setup.sh
and then
> cd ~
/bin/bash gnome-shell-build-setup.sh

**And don't write inside the same post - there's mess!!!**

---

### Post by Merk42 on 2010-10-10
Great, I'm gone for the weekend and the new UI comes out. Well as 10.10 was released today, it'll probably have to wait until the Natty Narwhal Testing and Discussion forum

---

### Post by xtoudi on 2010-10-10
> **Merk42 said:**
> Great, I'm gone for the weekend and the new UI comes out. Well as 10.10 was released today, it'll probably have to wait until the Natty Narwhal Testing and Discussion forum

So far new UI is .... so slow ;-)

---

### Post by xtoudi on 2010-10-10
> **23dornot23d said:**
> 

Step 2

```

root@keith-laptop:/home/keith# curl -O http://git.gnome.org/browse/gnome-sh...build-setup.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2609  100  2609    0     0   5624      0 --:--:-- --:--:-- --:--:-- 10562
root@keith-laptop:/home/keith# exit
exit


```That appeared to go ok ..... but had to run it as root ..... (if not root it would fail to create it)
```

keith@keith-laptop:~$ curl -O http://git.gnome.org/browse/gnome-sh...build-setup.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0Warning: Failed to create the file gnome-sh...build-setup.sh: Permission 
Warning: denied
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
curl: (23) Failed writing body (0 != 488)

```[COLOR=Red]


**I Guess I should not proceed beyond here ...... as it fails ....**

**So what should be happening here > ?**



Now there's a file 'gnome-shell-build-setup.sh' in your HOME dir and it has ROOT privilegs!!! Delete this file and download gnome-shell-build-setup.sh again using curl and your KEITH (I guess) user.
I think ... I'm done. Now read again 3-4 last pages ... there's enough knowledge to do this very easy.

---

### Post by 23dornot23d on 2010-10-10
Ok I have to get out of the habit of running as root ...... sorry ....

I will delete that script file and run it as normal user ....


keith@keith-laptop:~$ curl -O [http://git.gnome.org/browse/gnome-sh...build-setup.sh](http://git.gnome.org/browse/gnome-sh...build-setup.sh)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2609    0  2609    0     0   4413      0 --:--:-- --:--:-- --:--:-- 10648
keith@keith-laptop:~$

keith@keith-laptop:~$ /bin/bash gnome-shell-build-setup.sh
Updating jhbuild ... done
Installing jhbuild...
Writing ~/.jhbuildrc ... done
PATH does not contain /home/keith/bin, it is recommended that you add that.

Done.
keith@keith-laptop:~$


Ok jhbuild is working now ...... hopefully we are there ..... cheers for sticking with it ..... ty

---

### Post by xtoudi on 2010-10-10
[SIZE="4"][/SIZE]> **23dornot23d said:**
> Ok I have to get out of the habit of running as root ...... sorry ....

I will delete that script file and run it as normal user ....


keith@keith-laptop:~$ curl -O [http://git.gnome.org/browse/gnome-sh...build-setup.sh](http://git.gnome.org/browse/gnome-sh...build-setup.sh)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2609    0  2609    0     0   4413      0 --:--:-- --:--:-- --:--:-- 10648
keith@keith-laptop:~$

Clean up that mess.
> cd ~
sudo rm -rf gnome-shell


then
> 
export PATH=$PATH:/home/keith/bin
cd ~
jhbuild build
when you will get the error about libgio (step 22) ... you know the rest.

**[COLOR="Red"]do not write inside the same post!![/COLOR]**

---

### Post by ronacc on 2010-10-10
best to wipe gnome-shell jhbuild and everything you did as root and start from the beginning as a normal user . anything you did as root will be owned by root and not writable ( and maybe not even accessible ) as a normal user .

---

### Post by 23dornot23d on 2010-10-10
Ok will do that ...... fresh clean install again is easiest but I will remove the existing as you say and try it first .... 
and no using root .... other than to delete the mess that I created .....  will do it as sudo ;)

```

I just needed these too - but this was just to get by my errors .....
{ sudo apt-get install jhbuild libjasper-dev libdconf0 }

```Building from source is a bit more complicated than the GNOME  instructions say. So fire up a terminal
[LIST=1]
[*]sudo  apt-get install curl libtiff4-dev  libgstreamer0.10-dev libcroco3-dev  xserver-xephyr xulrunner-dev  python-dev mesa-utils mesa-common-dev  libreadline5-dev libgl1-mesa-dev  libwnck-dev librsvg2-dev  libgnome-desktop-dev libgnome-menu-dev  libffi-dev libgtk2.0-dev  libgconf2-dev libdbus-glib-1-dev gtk-doc-tools  gnome-common git-core  flex bison automake build-essential  icon-naming-utils
[*]curl -O [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh)
[*]/bin/bash gnome-shell-build-setup.sh
[*]Get jhbuild (not a command line entry)
[LIST]
[*]For Lucid via  repository, package name "jhbuild".
[*][From Jaunty]("http://packages.ubuntu.com/en/jaunty/jhbuild")
[*][From Debian]("http://packages.debian.org/unstable/devel/jhbuild")
[/LIST]
 
[*]jhbuild build
[/LIST]


ok this bit I missed before .... 

```

export PATH=$PATH:/home/keith3/bin
cd ~
jhbuild build                      

```Thanks again ,

Ok getting there .... back on it ..... cleared it all out and created 
a New User ..... doing it this way now ....

[IMG]http://img685.imageshack.us/img685/9206/workspace1003.jpg[/IMG]


ok this is going slowly but surely on the laptop ..... the desktop will get the same treatment if this works ok

8/23 gtk3 went in ok for me ....
9/23 librsvg ok
10/23 gtk engines 3 ok
11/23 json-glib ok
12/23 clutter ok
13/23 gconf ok
14/23 mutter ok
15/23 gjs ok
16/23 vala ok
17/23 dconf ok
18/23 gnome desktop 3 ok
19/23 gsettings desktop schemas ok
20/23 gnome icon theme ok
21/23 icon theme symbolic ok
22/23 gnome shell failed ..........


so now to the step to clean it out and remove the library


```

  CC     test_theme-test-theme.o
  CCLD   test-theme
/home/keith3/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [22/23]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 4
exit shell to continue with build
keith3@keith-laptop:~/gnome-shell/source/gnome-shell$ rm ~/gnome-shell/install/lib/*.la
keith3@keith-laptop:~/gnome-shell/source/gnome-shell$ exit
exit

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 6


```Ok 23/23 success ....... lets run it now ..... ;)


keith3@keith-laptop:~$ gnome-shell --replace
Starting dconf-service...  
Failed to start /usr/lib/d-conf/dconf-service: [Errno 2] No such file or directory
keith3@keith-laptop:~$ 

:(

Ok found this [Bug report]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=595598") and a solution I think


[COLOR=Red]**This bug can be fixed by installing libdconf0 from experimental.**[/COLOR]
It seems that this dependency is currently missing.



```

keith3@keith-laptop:~$ gnome-shell --replace
Starting dconf-service...  
Failed to start /usr/lib/d-conf/dconf-service: [Errno 2] No such file or directory
keith3@keith-laptop:~$ sudo aptitude install libdconf0
[sudo] password for keith3: 
The following NEW packages will be installed:
  libdconf0 
0 packages upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 41.4kB of archives. After unpacking 180kB will be used.
Get:1 http://fr.archive.ubuntu.com/ubuntu/ maverick/main libdconf0 i386 0.5-1ubuntu6 [41.4kB]
Fetched 41.4kB in 0s (68.6kB/s)
Selecting previously deselected package libdconf0.
(Reading database ... 335686 files and directories currently installed.)
Unpacking libdconf0 (from .../libdconf0_0.5-1ubuntu6_i386.deb) ...
Processing triggers for libglib2.0-0 ...
Setting up libdconf0 (0.5-1ubuntu6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
keith3@keith-laptop:~$ gnome-shell --replace
    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
      JS LOG: GNOME Shell started at Sun Oct 10 2010 23:39:40 GMT+0200 (CET)
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument



```[B]Ok I have it running now and [its the exact same version I have already previously had running]("http://www.youtube.com/watch?v=M2VDSBcRdVE") ..... where is the applications tab ? ....


[SCREENSHOT LINK]("http://img96.imageshack.us/img96/7452/workspace10068.png")


So to completely get it uptodate do I do this now ?

[/B]> 
jhbuild build                                 
1. Remove or backup old GS
     Quote:
                                                 rm  ~/gnome-shell/source/gnome-shell -rf                                 
2. it's important to cd into right place
     Quote:
                                                 cd  ~/gnome-shell/source/                                 
3. Get the latest overview-relayout branch
     Quote:
                                                 git clone  git://git.gnome.org/gnome-shell -b overview-relayout                                  
4. Build overview-relayout branch: make sure that other modules  are ok  (traditional 'jhbuild build' is done without errors) - below we  are  only compiling last gnome-shell modulset)
     Quote:
                                                 jhbuild buildone -n gnome-shell -f                                 
And we've got this awesome GS - this is mine GS
[B]Ok so Step one ..... 

1. Remove or backup old GS ..... ok backup sounds good at this point .... don't burn our bridges ...

[COLOR=Blue]I think I will archive GS source into another directory .... {[/COLOR][/B][COLOR=Blue]~/gnome-shell/source/                                 [B]}

[COLOR=Black]OK now have Gnome-Shell Archive , so next step ....

[/COLOR][/B][/COLOR]rm  ~/gnome-shell/source/gnome-shell -rf                                 
cd  ~/gnome-shell/source/                                 
git clone  git://git.gnome.org/gnome-shell -b overview-relayout                                  
jhbuild buildone -n gnome-shell -f                                 

```

*** Installing gnome-shell *** [1/1]
make install
Making install in data
make[1]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/data'
make[2]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/data'
make[2]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/home/keith3/gnome-shell/install/etc/gconf/gconf.xml.defaults /home/keith3/gnome-shell/install/bin/gconftool-2 --makefile-install-rule ./gnome-shell.schemas
Attached schema `/schemas/desktop/gnome/shell/windows/attach_modal_dialogs' to key `/desktop/gnome/shell/windows/attach_modal_dialogs'
Installed schema `/schemas/desktop/gnome/shell/windows/attach_modal_dialogs' for locale `C'
Attached schema `/schemas/desktop/gnome/shell/windows/button_layout' to key `/desktop/gnome/shell/windows/button_layout'
Installed schema `/schemas/desktop/gnome/shell/windows/button_layout' for locale `C'
Attached schema `/schemas/desktop/gnome/shell/windows/side_by_side_tiling' to key `/desktop/gnome/shell/windows/side_by_side_tiling'
Installed schema `/schemas/desktop/gnome/shell/windows/side_by_side_tiling' for locale `C'
test -z "/home/keith3/gnome-shell/install/share/applications" || /bin/mkdir -p "/home/keith3/gnome-shell/install/share/applications"
 /usr/bin/install-check -m 644 gnome-shell.desktop gnome-shell-clock-preferences.desktop '/home/keith3/gnome-shell/install/share/applications'
test -z "/home/keith3/gnome-shell/install/share/gnome-shell/images" || /bin/mkdir -p "/home/keith3/gnome-shell/install/share/gnome-shell/images"
 /usr/bin/install-check -m 644 close-black.svg magnifier.svg '/home/keith3/gnome-shell/install/share/gnome-shell/images'
test -z "/home/keith3/gnome-shell/install/share/gnome-shell" || /bin/mkdir -p "/home/keith3/gnome-shell/install/share/gnome-shell"
 /usr/bin/install-check -m 644 clock-preferences.ui '/home/keith3/gnome-shell/install/share/gnome-shell'
test -z "/home/keith3/gnome-shell/install/share/gnome-shell/theme" || /bin/mkdir -p "/home/keith3/gnome-shell/install/share/gnome-shell/theme"
 /usr/bin/install-check -m 644 theme/add-workspace.svg theme/close-window.svg theme/close.svg theme/corner-ripple.png theme/dialog-error.svg theme/gnome-shell.css theme/mosaic-view-active.svg theme/mosaic-view.svg theme/move-window-on-new.svg theme/process-working.png theme/remove-workspace.svg theme/running-indicator.svg theme/scroll-button-down-hover.png theme/scroll-button-down.png theme/scroll-button-up-hover.png theme/scroll-button-up.png theme/scroll-hhandle.svg theme/scroll-vhandle.svg theme/section-more.svg theme/section-more-open.svg theme/separator-white.png theme/single-view-active.svg theme/single-view.svg theme/toggle-off-us.svg theme/toggle-off-intl.svg theme/toggle-on-us.svg theme/toggle-on-intl.svg theme/ws-switch-arrow-left.svg theme/ws-switch-arrow-right.svg '/home/keith3/gnome-shell/install/share/gnome-shell/theme'
test -z "/home/keith3/gnome-shell/install/etc/gconf/schemas" || /bin/mkdir -p "/home/keith3/gnome-shell/install/etc/gconf/schemas"
 /usr/bin/install-check -m 644 gnome-shell.schemas '/home/keith3/gnome-shell/install/etc/gconf/schemas'
test -z "/home/keith3/gnome-shell/install/etc/xdg/menus" || /bin/mkdir -p "/home/keith3/gnome-shell/install/etc/xdg/menus"
 /usr/bin/install-check -m 644 gs-applications.menu '/home/keith3/gnome-shell/install/etc/xdg/menus'
test -z "/home/keith3/gnome-shell/install/share/gnome-shell/shaders" || /bin/mkdir -p "/home/keith3/gnome-shell/install/share/gnome-shell/shaders"
 /usr/bin/install-check -m 644 shaders/dim-window.glsl '/home/keith3/gnome-shell/install/share/gnome-shell/shaders'
test -z "/home/keith3/gnome-shell/install/share/glib-2.0/schemas" || /bin/mkdir -p "/home/keith3/gnome-shell/install/share/glib-2.0/schemas"
/usr/bin/install-check -m 644 org.gnome.accessibility.magnifier.gschema.xml org.gnome.shell.gschema.xml "/home/keith3/gnome-shell/install/share/glib-2.0/schemas"
test -n "" || /home/keith3/gnome-shell/install/bin/glib-compile-schemas /home/keith3/gnome-shell/install/share/glib-2.0/schemas
make[2]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/data'
make[1]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/data'
Making install in js
make[1]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/js'
make[2]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/keith3/gnome-shell/install/share/gnome-shell/js" || /bin/mkdir -p "/home/keith3/gnome-shell/install/share/gnome-shell/js"
/bin/mkdir -p '/home/keith3/gnome-shell/install/share/gnome-shell/js/ui/status'
 /usr/bin/install-check -m 644  ui/status/accessibility.js '/home/keith3/gnome-shell/install/share/gnome-shell/js/ui/status'
/bin/mkdir -p '/home/keith3/gnome-shell/install/share/gnome-shell/js/ui'
 /usr/bin/install-check -m 644  ui/altTab.js ui/appDisplay.js ui/appFavorites.js ui/boxpointer.js ui/calendar.js ui/chrome.js ui/dnd.js ui/docDisplay.js ui/environment.js ui/extensionSystem.js ui/genericDisplay.js ui/iconGrid.js ui/lightbox.js ui/link.js ui/lookingGlass.js ui/magnifier.js ui/magnifierDBus.js ui/main.js ui/messageTray.js ui/notificationDaemon.js ui/overview.js ui/panel.js ui/panelMenu.js ui/placeDisplay.js ui/popupMenu.js ui/runDialog.js ui/scripting.js ui/search.js ui/shellDBus.js ui/statusIconDispatcher.js ui/statusMenu.js ui/telepathyClient.js ui/tweener.js ui/viewSelector.js ui/windowAttentionHandler.js ui/windowManager.js ui/workspace.js ui/workspacesView.js ui/workspaceSwitcherPopup.js '/home/keith3/gnome-shell/install/share/gnome-shell/js/ui'
/bin/mkdir -p '/home/keith3/gnome-shell/install/share/gnome-shell/js/prefs'
 /usr/bin/install-check -m 644  prefs/clockPreferences.js '/home/keith3/gnome-shell/install/share/gnome-shell/js/prefs'
/bin/mkdir -p '/home/keith3/gnome-shell/install/share/gnome-shell/js/misc'
 /usr/bin/install-check -m 644  misc/docInfo.js misc/fileUtils.js misc/format.js misc/gnomeSession.js misc/params.js misc/telepathy.js '/home/keith3/gnome-shell/install/share/gnome-shell/js/misc'
/bin/mkdir -p '/home/keith3/gnome-shell/install/share/gnome-shell/js/perf'
 /usr/bin/install-check -m 644  perf/core.js '/home/keith3/gnome-shell/install/share/gnome-shell/js/perf'
make[2]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/js'
make[1]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/js'
Making install in src
make[1]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/src'
make  install-am
make[2]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/src'
make[3]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/src'
test -z "/home/keith3/gnome-shell/install/bin" || /bin/mkdir -p "/home/keith3/gnome-shell/install/bin"
 /usr/bin/install-check gnome-shell gnome-shell-clock-preferences '/home/keith3/gnome-shell/install/bin'
test -z "/home/keith3/gnome-shell/install/libexec" || /bin/mkdir -p "/home/keith3/gnome-shell/install/libexec"
test -z "/home/keith3/gnome-shell/install/lib/mutter/plugins" || /bin/mkdir -p "/home/keith3/gnome-shell/install/lib/mutter/plugins"
 /bin/bash ../libtool   --mode=install /usr/bin/install-check   libgnome-shell.la '/home/keith3/gnome-shell/install/lib/mutter/plugins'
libtool: install: /usr/bin/install-check .libs/libgnome-shell.so /home/keith3/gnome-shell/install/lib/mutter/plugins/libgnome-shell.so
libtool: install: /usr/bin/install-check .libs/libgnome-shell.lai /home/keith3/gnome-shell/install/lib/mutter/plugins/libgnome-shell.la
libtool: finish: PATH="/home/keith3/gnome-shell/install/bin:/home/keith3/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/sbin" ldconfig -n /home/keith3/gnome-shell/install/lib/mutter/plugins
----------------------------------------------------------------------
Libraries have been installed in:
   /home/keith3/gnome-shell/install/lib/mutter/plugins

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/home/keith3/gnome-shell/install/lib/gnome-shell" || /bin/mkdir -p "/home/keith3/gnome-shell/install/lib/gnome-shell"
 /usr/bin/install-check -m 644 Shell-0.1.typelib St-1.0.typelib Gdm-1.0.typelib '/home/keith3/gnome-shell/install/lib/gnome-shell'
make[3]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/src'
make[2]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/src'
make[1]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/src'
Making install in tests
make[1]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/tests'
make[2]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/tests'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/tests'
make[1]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/tests'
Making install in po
make[1]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/po'
linguas="ar bg ca cs da de el en_GB es et fi fr ga gl he hu id it ja ko lt nb nl nn pa pl pt pt_BR ro ru sl sr sr@latin sv ta th tr uk vi zh_CN zh_HK zh_TW "; \
    for lang in $linguas; do \
      dir=/home/keith3/gnome-shell/install/share/locale/$lang/LC_MESSAGES; \
      /bin/bash /home/keith3/gnome-shell/source/gnome-shell/config/install-sh -d $dir; \
      if test -r $lang.gmo; then \
        /usr/bin/install-check -m 644 $lang.gmo $dir/gnome-shell.mo; \
        echo "installing $lang.gmo as $dir/gnome-shell.mo"; \
      else \
        /usr/bin/install-check -m 644 ./$lang.gmo $dir/gnome-shell.mo; \
        echo "installing ./$lang.gmo as" \
         "$dir/gnome-shell.mo"; \
      fi; \
      if test -r $lang.gmo.m; then \
        /usr/bin/install-check -m 644 $lang.gmo.m $dir/gnome-shell.mo.m; \
        echo "installing $lang.gmo.m as $dir/gnome-shell.mo.m"; \
      else \
        if test -r ./$lang.gmo.m ; then \
          /usr/bin/install-check -m 644 ./$lang.gmo.m \
        $dir/gnome-shell.mo.m; \
          echo "installing ./$lang.gmo.m as" \
           "$dir/gnome-shell.mo.m"; \
        else \
          true; \
        fi; \
      fi; \
    done
installing ar.gmo as /home/keith3/gnome-shell/install/share/locale/ar/LC_MESSAGES/gnome-shell.mo
installing bg.gmo as /home/keith3/gnome-shell/install/share/locale/bg/LC_MESSAGES/gnome-shell.mo
installing ca.gmo as /home/keith3/gnome-shell/install/share/locale/ca/LC_MESSAGES/gnome-shell.mo
installing cs.gmo as /home/keith3/gnome-shell/install/share/locale/cs/LC_MESSAGES/gnome-shell.mo
installing da.gmo as /home/keith3/gnome-shell/install/share/locale/da/LC_MESSAGES/gnome-shell.mo
installing de.gmo as /home/keith3/gnome-shell/install/share/locale/de/LC_MESSAGES/gnome-shell.mo
installing el.gmo as /home/keith3/gnome-shell/install/share/locale/el/LC_MESSAGES/gnome-shell.mo
installing en_GB.gmo as /home/keith3/gnome-shell/install/share/locale/en_GB/LC_MESSAGES/gnome-shell.mo
installing es.gmo as /home/keith3/gnome-shell/install/share/locale/es/LC_MESSAGES/gnome-shell.mo
installing et.gmo as /home/keith3/gnome-shell/install/share/locale/et/LC_MESSAGES/gnome-shell.mo
installing fi.gmo as /home/keith3/gnome-shell/install/share/locale/fi/LC_MESSAGES/gnome-shell.mo
installing fr.gmo as /home/keith3/gnome-shell/install/share/locale/fr/LC_MESSAGES/gnome-shell.mo
installing ga.gmo as /home/keith3/gnome-shell/install/share/locale/ga/LC_MESSAGES/gnome-shell.mo
installing gl.gmo as /home/keith3/gnome-shell/install/share/locale/gl/LC_MESSAGES/gnome-shell.mo
installing he.gmo as /home/keith3/gnome-shell/install/share/locale/he/LC_MESSAGES/gnome-shell.mo
installing hu.gmo as /home/keith3/gnome-shell/install/share/locale/hu/LC_MESSAGES/gnome-shell.mo
installing id.gmo as /home/keith3/gnome-shell/install/share/locale/id/LC_MESSAGES/gnome-shell.mo
installing it.gmo as /home/keith3/gnome-shell/install/share/locale/it/LC_MESSAGES/gnome-shell.mo
installing ja.gmo as /home/keith3/gnome-shell/install/share/locale/ja/LC_MESSAGES/gnome-shell.mo
installing ko.gmo as /home/keith3/gnome-shell/install/share/locale/ko/LC_MESSAGES/gnome-shell.mo
installing lt.gmo as /home/keith3/gnome-shell/install/share/locale/lt/LC_MESSAGES/gnome-shell.mo
installing nb.gmo as /home/keith3/gnome-shell/install/share/locale/nb/LC_MESSAGES/gnome-shell.mo
installing nl.gmo as /home/keith3/gnome-shell/install/share/locale/nl/LC_MESSAGES/gnome-shell.mo
installing nn.gmo as /home/keith3/gnome-shell/install/share/locale/nn/LC_MESSAGES/gnome-shell.mo
installing pa.gmo as /home/keith3/gnome-shell/install/share/locale/pa/LC_MESSAGES/gnome-shell.mo
installing pl.gmo as /home/keith3/gnome-shell/install/share/locale/pl/LC_MESSAGES/gnome-shell.mo
installing pt.gmo as /home/keith3/gnome-shell/install/share/locale/pt/LC_MESSAGES/gnome-shell.mo
installing pt_BR.gmo as /home/keith3/gnome-shell/install/share/locale/pt_BR/LC_MESSAGES/gnome-shell.mo
installing ro.gmo as /home/keith3/gnome-shell/install/share/locale/ro/LC_MESSAGES/gnome-shell.mo
installing ru.gmo as /home/keith3/gnome-shell/install/share/locale/ru/LC_MESSAGES/gnome-shell.mo
installing sl.gmo as /home/keith3/gnome-shell/install/share/locale/sl/LC_MESSAGES/gnome-shell.mo
installing sr.gmo as /home/keith3/gnome-shell/install/share/locale/sr/LC_MESSAGES/gnome-shell.mo
installing sr@latin.gmo as /home/keith3/gnome-shell/install/share/locale/sr@latin/LC_MESSAGES/gnome-shell.mo
installing sv.gmo as /home/keith3/gnome-shell/install/share/locale/sv/LC_MESSAGES/gnome-shell.mo
installing ta.gmo as /home/keith3/gnome-shell/install/share/locale/ta/LC_MESSAGES/gnome-shell.mo
installing th.gmo as /home/keith3/gnome-shell/install/share/locale/th/LC_MESSAGES/gnome-shell.mo
installing tr.gmo as /home/keith3/gnome-shell/install/share/locale/tr/LC_MESSAGES/gnome-shell.mo
installing uk.gmo as /home/keith3/gnome-shell/install/share/locale/uk/LC_MESSAGES/gnome-shell.mo
installing vi.gmo as /home/keith3/gnome-shell/install/share/locale/vi/LC_MESSAGES/gnome-shell.mo
installing zh_CN.gmo as /home/keith3/gnome-shell/install/share/locale/zh_CN/LC_MESSAGES/gnome-shell.mo
installing zh_HK.gmo as /home/keith3/gnome-shell/install/share/locale/zh_HK/LC_MESSAGES/gnome-shell.mo
installing zh_TW.gmo as /home/keith3/gnome-shell/install/share/locale/zh_TW/LC_MESSAGES/gnome-shell.mo
make[1]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/po'
Making install in man
make[1]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/man'
make[2]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/keith3/gnome-shell/install/share/man/man1" || /bin/mkdir -p "/home/keith3/gnome-shell/install/share/man/man1"
 /usr/bin/install-check -m 644 gnome-shell.1 '/home/keith3/gnome-shell/install/share/man/man1'
make[2]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/man'
make[1]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell/man'
make[1]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell'
make[2]: Entering directory `/home/keith3/gnome-shell/source/gnome-shell'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell'
make[1]: Leaving directory `/home/keith3/gnome-shell/source/gnome-shell'
*** success *** [1/1]
keith3@keith-laptop:~/gnome-shell/source$ 


```Ok Gnome Shell runs ..... [but I am not seeing a lot of difference to what I had before ....]("http://img163.imageshack.us/img163/3474/workspace1011.png")

  [COLOR=Red]This was the version you show  [SCREENSHOT SHOWN BEFORE SHOWING THE NEW LOOK]("http://ubuntuforums.org/attachment.php?attachmentid=171765&d=1286658447") the look there is different to what I am seeing .... [/COLOR][B][COLOR=Red]
[/COLOR] 
What am I missing here ?
[/B] 
here is the output when I use it ....... if its of use to anyone ......

```

keith3@keith-laptop:~/gnome-shell/source$ gnome-shell --replace    JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
      JS LOG: GNOME Shell started at Mon Oct 11 2010 00:25:22 GMT+0200 (CET)
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager],[object _private_Gdm_User])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
Window manager warning: Log level 8: meta_window_raise: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_lower: assertion `!window->override_redirect' failed



```[IMG]http://img151.imageshack.us/img151/2153/latestsmall.png[/IMG]
[B]
I have a full Archive now of all the source files and directories ..... 
so now it should not be too difficult to update ..... [/B]

___________________________

Onward .......

Used it for a couple if hours now .

Its excellent for organising windows.

Now when I go to desktops without it .... 

I miss it ...... :(

Ok if you run docky with it ..... this is good ..... conky works ok too ........

There would be a video here too .... but still having problems uploading 
ogv files to You-Tube
Imageshack does not want to know ..... guess I will need to convert it ,

[B]Top left for the Gnome-Shell will not work with gtk-recordmydesktop ... at the moment ...
ALT key opens Gnome-Shell window ... so have now got a video ..... 

[_A bit glitchy at the moment though_]("http://www.youtube.com/watch?v=N_OzBRY7Jms") .... 

Still working on it ..... 
[/B]

---

