---
title: "Separate X Screens Heartache - No desktop; Limited Compiz, Nautilus"
date: 2011-02-01
forum: Multimedia Software
---

### Post by copaceticjon on 2011-02-01
Well, i'm only about a week into Ubuntu, and although i'm feeling my way around little by little, i'm still very much a beginner at it.  The good news:  this is the first problem to completely stump me so far...

Separate X Screens is causing a whole mess of problems for me.

I am running Ubuntu 10.04 with a nVidia Corporation GT215 [GeForce GT 240] with a samsung LCD monitor in the VGA slot and a toshiba TV in the HDMI slot.  When i run only one display (the samsung) everything works perfectly.  Same with TwinView.  But with Separate X screens (my preferred setup), there is a whole list of problems.

First off, in SXscreens my desktop icons aren't shown and i can't right click into a context menu on the desktop.  Through diligent googling i've learned that Nautilus draws my desktop.  So upon checking for a running nautilus process in SXscreens mode i couldn't find one.  In standard, single display mode, a nautilus process IS running and i can right-click all day long.  Also, in SXscreens mode i can't open nautilus from a terminal.  The command:

> "jon@ubuntu:~$ nautilus"

yields this result:

> "(nautilus:5685): Unique-DBus-WARNING **: Error while sending message: Message did not receive a reply (timeout by message bus)

(nautilus:5685): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

And the command:

> "jon@ubuntu:~$ sudo nautilus"

yields this result:

> "The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 608 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)"

...but i can open it by clicking any option on my "Places" menu.  Additionally, both of the above commands work in single display mode and in TwinView.  And in gconf-editor, under apps/nautilus/preferences "show desktop" is checked (enabled).



I have "desktop cube" enabled with a 40% "opacity during rotation", as well as "rotate cube" and "cube reflection and deformation" with a cylinder deformation in Compiz.  It all works perfectly in single display mode and TwinView, but in SXscreens the following issues arise:

Main screen (samsung):  no transparency during rotation except top and bottom images, no cylinder deformation (it remains a cube), as well as a lack of ability to right-click into context menu and no desktop icons.

Second screen (toshiba): can't cycle through desktops, can't rotate cube with mouse (<ctrl><alt>Button1 just makes cursor disappear), no taskbar on top of screen (with applications, places, etc.) as well as a lack of ability to right-click into context menu and no desktop icons.

Additionally these problems *occasionally* arise:  No top bar on windows (i think it's called the title bar?  with the close, minimize, and maximize buttons) and login screen wallpaper stays on second display (the toshiba, this only happened once)


Has anyone encountered these problems or problems like them?  The desktop problem seems to be nautilus-based, but how?  And what's with the lack of Compiz functionality?  I am stumped.

---

### Post by BicyclerBoy on 2011-02-02
Separate X screens is still one X session.
Not sure if one nautilus process manages all the 'folder-browsers'  opened.

Have been using separate X screens with a least 2 displays since 8.04.
Normally do not use compiz screen effects because of the history of problems with video playback.
Currently running same OS version & same GPU as you.
Both screens have desktop menus & screen cycling. Always worked.
Have no problem opening many folder-browsers on any screen.
Desktop icons have **not** been possible on secondary X screen since 8.04.
I assumed 8.04 was at fault !

Just turned compiz **on**, works okay both screens & work fine with MythTV video playback.

Have noticed a bug with keyboard input **not** going to the correct screen after desktop cycling.
This only happens with compiz enabled.

So no icons on 2nd (or 3rd) screen. Bug or feature ? Who to ask ?
Compiz bug keyboard focus . Bug.

---

### Post by copaceticjon on 2011-02-02
Well, i've freshly installed because i got a little too careless with xorg.conf and ended up unable to login to ubuntu graphically.  whoops!

So, in my continued perusing i've gathered that compiz effects + separate x screens pretty much just means one dead, useless husk of a desktop set uselessly beside my main display. Too bad, but since then i've gotten TwinView to work almost exactly like i'm used to (in windows extended desktop mode). And i found the option to split the Desktop Cube in Compiz into two separate cubes for multiple displays, which got rid of the One Giant Cube problem that turned me off to TwinView initially.

So problem solved, in a way...

---

### Post by ffixcollector on 2011-03-27
I decided to hook up a second monitor today, and am running into the same problems. After some research I found this thread. I hope someone has an answer, because I to would like to get this working.

Specifically I would like to know if it is possible to have separate desktops, on each monitor. I would like to control them independently. I don't want both cubes to change when I switch workspaces on one monitor.

---

### Post by jzemeocala on 2011-09-26
Im sorry for bumping an old thread as my first post. But this is pretty much a duplicate of my own issue and although I have found several related threads on both this forum and the rest of the web, none of them have a solution.

---

### Post by snowglyder on 2011-11-16
I found this thread because I'm having an issue with the 3rd monitor not being able to see video in Chrome running on a separate X screen. I'm having the same issues with no right click on the desktop, no desktop icons, and Alt+F2 not working. I can live without right-click on the desktop and I use Screenlets with Folderview to see 

I have 2 nvidia cards for the separate X screens. One card does support 3 monitors, but I couldn't get the desired effect with a dedicated monitor for Chrome, so I installed another nvidia card for the 3rd monitor. I'm nearly satisfied with my setup, but the whole purpose of the 3rd monitor was to have Chrome open and constantly available for research and browsing (as I'm using this at work) and use the other 2 monitors in Twinview for managing my servers and testing in VMs. No video is bothering me more than I would've thought, so any ideas to get it working would be fantastic. Video does work on the Twinview monitors. 

If it helps anyone, I'm using Compiz to get Alt-F2 to bring up a terminal so I can easily run something on the separate X screen. Also, Compiz doesn't auto start for that screen so I've created a launcher for Chrome with the command "export DISPLAY=:0.1 && compiz --replace | /usr/bin/chromium-browser %U" to launch Chrome on that X screen and gives me Window decoration so I can get a title bar and the Compiz effects.

---

