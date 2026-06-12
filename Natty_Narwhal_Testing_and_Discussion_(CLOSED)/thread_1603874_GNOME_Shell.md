---
title: "GNOME Shell"
date: 2010-10-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Merk42 on 2010-10-23
**BACK BY POPULAR DEMAND**

[b]This thread is for testing support and technical discussion.
Opinions should go to the [Community Cafe thread]("http://ubuntuforums.org/showthread.php?t=1457428") or ideally [the GNOME Shell mailing list]("http://mail.gnome.org/mailman/listinfo/gnome-shell-list")[/b].

I made this thread again because as before, I figured the sort of people that would install and test pre-release versions of a new UI would be the sort of people that install and test pre-release versions of Ubuntu.

**What is GNOME Shell?**
GNOME Shell, for those of you that do not know, is a user interface change to GNOME. With it, brings Mutter a combination of Metacity and Clutter, managing the windows. Say goodbye to compiz as it won't be compatible.

GNOME Shell will be [released as **one part of GNOME 3** in March of 2011]("http://mail.gnome.org/archives/devel-announce-list/2010-July/msg00003.html") it [will not be default in 11.04]("http://www.youtube.com/watch?v=YUAzicy_01o#t=17m40s"), that's [Unity](http://unity.ubuntu.com/), though GNOME Shell should still be an optional package.

**What does it look like?**
Here is GNOME Shell. 
[IMG]http://www.markecurtis.com/etc/gnomeshell/gnomeshell.png[/IMG]

The active application near "Activities" has a menu upon clicking. Clicking on the date or username provide a calendar and menu respectively
[IMG]http://www.markecurtis.com/etc/gnomeshell/menus.png[/IMG]

Currently some applications are open but hidden. Where are they?
This is the Activities overview, where you run and manage "Activities"
[IMG]http://www.markecurtis.com/etc/gnomeshell/overview.png[/IMG]

More applications can be run either by searching for the name in "Type to search...", or in this case, clicking the word applications
[IMG]http://www.markecurtis.com/etc/gnomeshell/moreapplications.png[/IMG]

One extra blank workspace is create by default. If an application is put onto that blank workspace, one more blank workspace will be created. The thumbnails on the right, viewable upon hover, let you switch among them. New applications can be opening onto specific workspaces by dragging the launcher to the workspace thumbnail on the right.
[IMG]http://www.markecurtis.com/etc/gnomeshell/add.png[/IMG]

Oh look, an instant message! Unlike the passive notify-OSD, clicking on this will bring up the window
[IMG]http://www.markecurtis.com/etc/gnomeshell/messages.png[/IMG]

If no action is taken, it resides in the lower right, viewable upon hover.
[IMG]http://www.markecurtis.com/etc/gnomeshell/messageexpand.png[/IMG]


**OMG GNOME SHELL IS AWFUL AND I HATE UNITY! I'm moving to xfce/Windows/an abacus**
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

Running Jaunty, Karmic, Lucid, Maverick and Natty, there are three ways to try GNOME Shell
[LIST]
[*]Build from source (recommended, as it provides the most recent version, though may occasionally break)
[*]Install the gnome-shell package (easy but out of date)
[*]**For Natty Narwhal Only** Use the [Ricotz PPA]("http://ubuntu-tweak.com/source/gnome-shell-testing/") (slightly harder, but more up to date)
[/LIST]
**As of Virtualbox 4.0 GNOME Shell will run in a virtual machine, but very slowly and glitchy, to the point of unusable**

Building from source is a bit more complicated than the GNOME instructions say. So fire up a terminal
```

sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils libpulse-dev libcanberra-dev autopoint libjasper-dev libvorbis-dev libpam-dev libxklavier-dev libgnome-keyring-dev libupower-glib-dev libgtop2-dev libcups2-dev evolution-data-server-dev libsqlite3-dev libproxy-dev libdb-dev libproxy-dev
```
```
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
```
```
/bin/bash gnome-shell-build-setup.sh
```
Get jhbuild (not a command line entry)
[LIST]
[*]For Lucid, Maverick, Natty via repository, package name "jhbuild".
[*][From Jaunty]("http://packages.ubuntu.com/en/jaunty/jhbuild")
[*][From Debian]("http://packages.debian.org/unstable/devel/jhbuild")
[/LIST]
```
jhbuild build
```


**IF YOU HAVE TROUBLE BUILDING**
**Hey it keeps "hanging up unexpectedly"**
Quit building and run
```
 pushd ~/gnome-shell/source/ && git clone git://git.gnome.org/gtk+ gtk3 && popd
``` then re run jhbuild build

**I'm getting a lot of "undefined reference" errors**
try ```
rm ~/gnome-shell/install/*.la && sudo rm -rf /usr/lib*/*.la
```
Then jhbuild build
If it still doesn't work, delete the ~/gnome-shell folder and try again

**I'm getting an error regarding libcanberra-gtk-module.so: undefined symbol: gtk_quit_add**
It's a known bug, just delete the file libcanberra-gtk-module.so


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

### Post by xtoudi on 2010-10-23
Great ... looking at required libs ... is it **libjasper-dev** required too??
Take a look at gnome-shell-build-setup.sh - seems to be required.

---

### Post by donniezazen on 2010-10-23
1. Last time i checked, i heard that ricotz has stopped updating his repo. Any information?

2. If i build from source how do i know when to rerun the build for upgrade?

3. WIll Gnome-Shell run smoothly on laptops which run Gnome 2 without any lag or resource hog?

Thanks.

---

### Post by Merk42 on 2010-10-23
> **xtoudi said:**
> Great ... looking at required libs ... is it **libjasper-dev** required too??
Take a look at gnome-shell-build-setup.sh - seems to be required.
Did a fresh install, looks like it is required.
Added to the OP

> **soham_1207 said:**
> 1. Last time i checked, i heard that ricotz has stopped updating his repo. Any information?

2. If i build from source how do i know when to rerun the build for upgrade?

3. WIll Gnome-Shell run smoothly on laptops which run Gnome 2 without any lag or resource hog?

Thanks.
[list=1]
[*]I don't use it, but it mentions Natty so I'm guessing it gets updated
[*]As I say in the OP, check the [commit log](http://git.gnome.org/browse/gnome-shell). You can also just rerun [FONT="Courier New"]jhbuild build[/FONT] whenever you want and it will only update the parts that need to be updated.
[*]Maybe? A "laptop which run GNOME 2" is too vague to give a definitive answer.
[/list]

---

### Post by davideotape on 2010-10-23
```
david@david-macbook:~$  pushd ~/gnome-shell/source/ && git clone git://git.gnome.org/gtk+ gtk3 && popd
~/gnome-shell/source ~
fatal: destination path 'gtk3' already exists and is not an empty directory.

```

?

---

### Post by keypox on 2010-10-23
Its sooo slow, dunno what happen but when i used it about a year ago it was fast.

Anyways im still not impressed i much prefer what we have, I do kinda like what Lion is gonna have the mission control.  It kinda reminds me of gnome shell.

---

### Post by ronacc on 2010-10-23
I'm getting this error 

```
make[1]: Entering directory `/home/ron/gnome-shell/source/gjs'
/bin/bash ./libtool --tag=CC   --mode=link gcc  -pthread -DXP_UNIX -DJS_THREADSAFE -I/home/ron/gnome-shell/install/include/glib-2.0 -I/home/ron/gnome-shell/install/lib64/glib-2.0/include -I/usr/include/xulrunner-1.9.2.11 -I/usr/include/xulrunner-1.9.2.11/nspr -I/usr/include/nspr    -Wsign-compare -Wcast-align -Wpointer-arith -Wnested-externs -Wmissing-prototypes -Wmissing-declarations -Wchar-subscripts -Wall -g -O2 -R /usr/lib/xulrunner-1.9.2.11 -rdynamic -L/home/ron/gnome-shell/install/lib64  -o gjs-console gjs_console-console.o libgjs.la 
libtool: link: gcc -pthread -DXP_UNIX -DJS_THREADSAFE -I/home/ron/gnome-shell/install/include/glib-2.0 -I/home/ron/gnome-shell/install/lib64/glib-2.0/include -I/usr/include/xulrunner-1.9.2.11 -I/usr/include/xulrunner-1.9.2.11/nspr -I/usr/include/nspr -Wsign-compare -Wcast-align -Wpointer-arith -Wnested-externs -Wmissing-prototypes -Wmissing-declarations -Wchar-subscripts -Wall -g -O2 -rdynamic -o .libs/gjs-console gjs_console-console.o  -L/home/ron/gnome-shell/install/lib64 ./.libs/libgjs.so -pthread -Wl,-rpath -Wl,/home/ron/gnome-shell/install/lib64 -Wl,-rpath -Wl,/usr/lib/xulrunner-1.9.2.11
/usr/bin/ld: gjs_console-console.o: undefined reference to symbol 'g_object_unref'
/usr/bin/ld: note: 'g_object_unref' is defined in DSO /home/ron/gnome-shell/install/lib64/libgobject-2.0.so.0 so try adding it to the linker command line
/home/ron/gnome-shell/install/lib64/libgobject-2.0.so.0: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[1]: *** [gjs-console] Error 1
make[1]: Leaving directory `/home/ron/gnome-shell/source/gjs'
make: *** [all] Error 2

```

I'm sure I've seen that before but I don't remember the fix , I searched the maverick version of this thread but with 84 pages of posts I couldn't find it .

edit: I tried the fixes in merck's first post , no help , wiped and started over no help .

---

### Post by autocrosser on 2010-10-23
Yes--I've got the same problem right now---prevents a Gnome-Shell update.....

---

### Post by davideotape on 2010-10-24
Here are the errors I'm getting:

```
  GISCAN Gtk-3.0.gir
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_x11_display_set_startup_notification_id'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_rgba_get_type'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_rgba_to_string'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_cairo_set_source_rgba'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_rgba_parse'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspectCmEWps/Gtk-3.0', '-export-dynamic', '-L.', 'libgtk-x11-3.0.la', '-pthread', '-L/home/david/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspectCmEWps/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/23]
```

```
/home/david/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_application_set_action_enabled'
/home/david/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_application_quit_with_data'
/home/david/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_application_add_action'
collect2: ld returned 1 exit status
make[3]: *** [gconf-sanity-check-2] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/gconf/gconf'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/gconf/gconf'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gconf'
make: *** [all] Error 2
*** Error during phase build of gconf: ########## Error running make   *** [13/23]

```

```
/usr/bin/ld: gjs_console-console.o: undefined reference to symbol 'g_object_unref'
/usr/bin/ld: note: 'g_object_unref' is defined in DSO /home/david/gnome-shell/install/lib/libgobject-2.0.so.0 so try adding it to the linker command line
/home/david/gnome-shell/install/lib/libgobject-2.0.so.0: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[1]: *** [gjs-console] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gjs'
make: *** [all] Error 2
*** Error during phase build of gjs: ########## Error running make   *** [15/23]

```

---

### Post by cariboo on 2010-10-24
I don't know if it still works, but I used gconf-editor to move the buttons in Maverick.

---

### Post by bluebyt on 2010-10-24
Thank you very much Merk42! This is very helpful.

I built Gnome shell on my computers and I noticed that is faster on my intel graphic system. Compare to my Nvidia system Gnome shell is slow.

I haven't notice too much changed since the las time I used it, about 6 month ago.

I wonder if they will change for the new mockups?
[http://www.webupd8.org/2010/07/new-gnome-shell-mockups-look-like-unity.html]("http://www.webupd8.org/2010/07/new-gnome-shell-mockups-look-like-unity.html")

---

### Post by bash on 2010-10-24
Since no one has mentioned it so far, here's the link to the instructions for the Maverick thread for testing the overlay-redesign branch:

[http://ubuntuforums.org/showpost.php?p=9944930&postcount=813](http://ubuntuforums.org/showpost.php?p=9944930&postcount=813)

Also in one of the last updates the Sound Applet (?) in the top Shell panel was changed and looks exactly like the Ubuntu one, including the horizontal volume slider but without the extra entries for media players.

---

### Post by praveenmarkandu on 2010-10-24
mutter relies on metacity if im not mistaken. so just go in gconf-editor  apps/metacity/general/button layout

i set mine to :minimize,maximize,close

---

### Post by Starks on 2010-10-25
With Unity coming, Shell is dead to me.

---

### Post by xtoudi on 2010-10-25
> **Starks said:**
> With Unity coming, Shell is dead to me.

so ... feel free ... don't read this thread :-)

---

### Post by regeya on 2010-10-25
> **Starks said:**
> With Unity coming, Shell is dead to me.

It's funny that an Ubuntu-only project that will essentially make Ubuntu's GNOME desktop a fork, is called 'Unity'.

---

### Post by ronacc on 2010-10-25
> **Starks said:**
> With Unity coming, Shell is dead to me.

since unity was dead to me the first time I booted it  , I guess we will be attending different funerals .

---

### Post by donniezazen on 2010-10-25
I am trying Unity it is not revolutionary but it is different. I miss my desktop. Is there a way to add other launchers to the available vertical dock?

---

### Post by cariboo on 2010-10-25
This really has nothing to do with gnome-shell, but, start an application, then right click on the icon in the panel, select Keep in Launcher then left click. See screen shot.

---

### Post by ronacc on 2010-10-25
anyone gotten gnome-shell to build in the last couple of days ? I'm still getting an error building gjs .

---

### Post by bluebyt on 2010-10-25
> **ronacc said:**
> anyone gotten gnome-shell to build in the last couple of days ? I'm still getting an error building gjs .

Yes I built it on my two computers without a hitch!

I even try overlay-redesign branch, working ok I guest.

Although It is still hard for me to click twice (click Activities and then click on the icon or Windows) to switch between windows.

---

### Post by again617 on 2010-10-25
> **ronacc said:**
> anyone gotten gnome-shell to build in the last couple of days ? I'm still getting an error building gjs .

I haven't gotten it to build in a while either.   According to the comments here: [http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html) it sounds as though having the firefox 4 ppa will break your gnome shell build.  

I'm using firefox 4 and I'm liking it so I don't really want to downgrade it.

---

### Post by autocrosser on 2010-10-25
It finally all built again tonight---I did do a ```
export PATH=$PATH:/home/dean/bin
```that I normally have not done--maybe it made a difference or gjs finally caught up.....not sure but its running again--I'm just using the main git--will wait til the gui settles again.....

---

### Post by ronacc on 2010-10-26
I wiped everything in my /home that had anything at all to do with GS including every trace of jhbuild and started from 0 again , atleast it died in a different place this time , building gtk3 , following Merk42's ins in post 1 and rerunning jhbuild finally got it to complete for me .

---

### Post by nilarimogard on 2010-10-26
> **again617 said:**
> I haven't gotten it to build in a while either.   According to the comments here: [http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html) it sounds as though having the firefox 4 ppa will break your gnome shell build.  

I'm using firefox 4 and I'm liking it so I don't really want to downgrade it.

It worked fine for me in 10.10 with the Mozilla Daily PPA enabled, but it seems it doesn't work in 10.04 so if you're using Ubuntu 10.04, you may need to use ppa-purge to completely purge the packages in the Mozilla Daily PPA.

The other error that everyone is getting regarding libgio-2.0.so (step 22/23) is easily fixable - as stated in the link above.

---

### Post by ronacc on 2010-10-26
> **again617 said:**
> I haven't gotten it to build in a while either.   According to the comments here: [http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html) it sounds as though having the firefox 4 ppa will break your gnome shell build.  

I'm using firefox 4 and I'm liking it so I don't really want to downgrade it.

you don't have to use the PPA , d/l the FF4 tarball unzip it in your /home or a seperate dir in your /home then open a terminal in the dir it creates and run it with ./firefox . I'm posting this from FF4 running in gnome-shell .

---

### Post by ronacc on 2010-10-26
mutter seems to be using a lot of cpu  12>14% idle and up to 25%  on a fairly fast AMD64x2 .

---

### Post by sgage on 2010-10-26
I just compiled GS without incident. Seems to be a together tree at the moment, should anyone want to try.

This was starting from scratch, under Natty.

Oh, it works pretty well. Seems to be getting a bit quicker and smoother.

---

### Post by kaitwospirit on 2010-10-26
I still can't get gjs to compile either. Getting the following error every time: 

In file included from /usr/include/xulrunner-1.9.2.12pre/jsatom.h:51:0,
                 from /usr/include/xulrunner-1.9.2.12pre/jscntxt.h:49,
                 from gjs/jsapi-private.cpp:35:
/usr/include/xulrunner-1.9.2.12pre/jsprvtd.h:69:0: warning: "INT_TO_JSID" redefined
gjs/compat.h:61:0: note: this is the location of the previous definition
In file included from /usr/include/xulrunner-1.9.2.12pre/jsatom.h:53:0,
                 from /usr/include/xulrunner-1.9.2.12pre/jscntxt.h:49,
                 from gjs/jsapi-private.cpp:35:
/usr/include/xulrunner-1.9.2.12pre/jslock.h:47:21: fatal error: pratom.h: No such file or directory
compilation terminated.


I ppa-purged mozilla-daily and have purged and reinstalled xulrunner twice. Anyone have any idea how to fix this?

---

### Post by ronacc on 2010-10-26
what worked for me was to wipe everything GS related including jhbuild in my /home and start from the beginning , following merk42's post #1 in this thread .

---

### Post by kaitwospirit on 2010-10-26
Even after a purge and reinstall of xulrunner, jhbuild, and gnome-shell, I'm still getting no success building gjs.

---

### Post by cmccauley on 2010-10-27
Hi all,

Just about the only thing that annoys me in GS is that there isn't any obvious way to get it to remember the number of workspaces that I use (4). It's probably been five or six months since I last looked into this but does anyone know of a way to do this? 

Thanks,

Chris

---

### Post by again617 on 2010-10-27
I think I found the solution for this error:```
checking if -I/usr/include/xulrunner-1.9.2.12pre/unstable works... no
configure: error: Unable to determine extra compiler flags needed
```

I noticed that there was no file or folder in /usr/include/xulrunner-1.9.2.12pre called unstable.  Looking in the file configure.ac I noticed this:

```
##  workaround for Ubuntu Hardy bug where mozilla-js.pc gives CFLAGS
## -I.../stable while jsapi.h is in .../unstable
```

So it looks as though this workaround for Hardy breaks in my Maverick.  I have jsapi.h in /usr/include/xulrunner-1.9.2.12pre.

On line 174 (in my configure.ac file) I saw the word unstable so I removed it.  So the line now looks like this ```
    try_cflags="-I`$PKG_CONFIG --variable=includedir $JS_PACKAGE`"
```

A couple of notes:
This isn't a good fix as configure.ac won't get automatically updated when you run jhbuild build anymore and if you wipe the directory then you will need to make this change again.

If you open configure.ac with vim, you can easily search for the word "unstable" by typing this: /unstable and then hitting return.

gjs still isn't building for because of this error now: ```
fatal error: glib.h: No such file or directory
```

---

### Post by augias on 2010-10-27
> **cmccauley said:**
> Hi all,

Just about the only thing that annoys me in GS is that there isn't any obvious way to get it to remember the number of workspaces that I use (4). It's probably been five or six months since I last looked into this but does anyone know of a way to do this? 

Thanks,

Chris

That bug is discussed here: [https://bugzilla.gnome.org/show_bug.cgi?id=602182](https://bugzilla.gnome.org/show_bug.cgi?id=602182)

There isn't an obvious way to do this because it isn't implemented yet for gnome-shell to start up and use however many default workspaces you have set in metacity gconf. (remember gnomeshell is still not a finished product)

---

### Post by ratcheer on 2010-10-27
> **regeya said:**
> It's funny that an Ubuntu-only project that will essentially make Ubuntu's GNOME desktop a fork, is called 'Unity'.

Actually, while the word "irony" is misused often, that is a good example of irony.

Tim

---

### Post by kaitwospirit on 2010-10-27
> **again617 said:**
> gjs still isn't building for because of this error now: ```
fatal error: glib.h: No such file or directory
```

Yeah, xulrunner updated, and now I'm not getting the error I was before but a completely different error, and gjs still doesn't build for me either. It's not either of the errors you've reported, though, which amuses me a little somehow.

---

### Post by cariboo on 2010-10-27
What I find ironic, is that the gnome proposed to change gnome-shell after Unity was released. :)

---

### Post by moore.bryan on 2010-10-27
> **augias said:**
> That bug is discussed here: [https://bugzilla.gnome.org/show_bug.cgi?id=602182](https://bugzilla.gnome.org/show_bug.cgi?id=602182)

There isn't an obvious way to do this because it isn't implemented yet for gnome-shell to start up and use however many default workspaces you have set in metacity gconf. (remember gnomeshell is still not a finished product)

It's somewhat good to see the GNOME Shell developers at least *willing* to look at adding a default number of workspaces other than one. I know when the discussions first started, GS was only ever going to ship with one and then "require" users to add more as necessary; the rationale seemed to be by using GS the way it was "intended," users wouldn't need more than one workspace.

+1 to the default extra workspaces.

---

### Post by Merk42 on 2010-10-27
[GNOME Shell 2.91.1 released](http://mail.gnome.org/archives/gnome-shell-list/2010-October/msg00042.html)

---

### Post by moore.bryan on 2010-10-27
> **bash said:**
> Since no one has mentioned it so far, here's the link to the instructions for the Maverick thread for testing the overlay-redesign branch:

[http://ubuntuforums.org/showpost.php?p=9944930&postcount=813](http://ubuntuforums.org/showpost.php?p=9944930&postcount=813)

Also in one of the last updates the Sound Applet (?) in the top Shell panel was changed and looks exactly like the Ubuntu one, including the horizontal volume slider but without the extra entries for media players.
And for anyone who tries this, finds it *catastrophically* ugly, and wants to revert back:
[list]
[*]mv ~/gnome-shell/source/gnome-shell ~/gnome-shell/source/gnome-shell.relayout
[*]cd ~/gnome-shell/source
[*]git clone git://git.gnome.org/gnome-shell
[*]jhbuild buildone -n gnome-shell -f
[/list]
When you restart GNOME Shell, you should be back to "normal."

---

### Post by xebian on 2010-10-27
> **Merk42 said:**
> [GNOME Shell 2.91.1 released](http://mail.gnome.org/archives/gnome-shell-list/2010-October/msg00042.html)

With GS out of favor will someone build the latest version?   The repo version 2.31 is way too old.

---

### Post by moore.bryan on 2010-10-27
> **xebian said:**
> With GS out of favor will someone build the latest version?   The repo version 2.31 is way too old.
What do you mean "out of favor?" An allusion to Unity? I don't think Unity is the main focus of GNOME; rather, it's the main focus of Canonical/Ubuntu.

---

### Post by xebian on 2010-10-27
> **moore.bryan said:**
> What do you mean "out of favor?" An allusion to Unity? I don't think Unity is the main focus of GNOME; rather, it's the main focus of Canonical/Ubuntu.

Isn't this Ubuntu forums?

---

### Post by moore.bryan on 2010-10-27
Very true, but it's a thread about GS, a non-Ubuntu designed piece of software.

---

### Post by Harry33 on 2010-10-28
> **xebian said:**
> With GS out of favor will someone build the latest version?   The repo version 2.31 is way too old.

Well I think that we have to wait for a while until official natty repo version get upgraded, because new GS needs GTK3.0.

However, there is a PPA around that really works, with GTK3.0 and all other new GS_2.91 dependencies. Latest updates are of today.
And it will not mess Gnome Panel, both GTK2.0 and GTK3.0 do work.

Rico Tzschichholz - Staging PPA:
[https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging)

And a word of warning there too:
DO NOT USE THESE PACKAGES !!!

---

### Post by xtoudi on 2010-10-28
> **moore.bryan said:**
> And for anyone who tries this, finds it *catastrophically* ugly, and wants to revert back:
[list]
[*]mv ~/gnome-shell/source/gnome-shell ~/gnome-shell/source/gnome-shell.relayout
[*]cd ~/gnome-shell/source
[*]git clone git://git.gnome.org/gnome-shell
[*]jhbuild buildone -n gnome-shell -f
[/list]
When you restart GNOME Shell, you should be back to "normal."

```
jhbuild buildone gnome-shell

```
or 
```
jhbuild buildone gnome-shell -f

```

This is enough ... this rebuilds master branch.

---

### Post by cmccauley on 2010-10-28
> **augias said:**
> That bug is discussed here: [https://bugzilla.gnome.org/show_bug.cgi?id=602182](https://bugzilla.gnome.org/show_bug.cgi?id=602182)

There isn't an obvious way to do this because it isn't implemented yet for gnome-shell to start up and use however many default workspaces you have set in metacity gconf. (remember gnomeshell is still not a finished product)

All this development time and it still can't remember how many workspaces I created last time I used it? That's a pretty basic requirement. 

I really like gnome-shell - as I said in the post this is about the only thing that really annoys me. Maybe I'm wrong, maybe the painfully slow development cycles also annoy me. 

Ah well, I'll stick with it for a bit longer.

---

### Post by seeker5528 on 2010-10-28
> **cmccauley said:**
> All this development time and it still can't remember how many workspaces I created last time I used it? That's a pretty basic requirement. 

That was a design decision to not start with multiple desktops enabled, the right hand giveth and the left hand taketh away, so unless the devs have changed their mind recently you will have to settle for the fact that being able to quickly, "intuitively" create/delete additional desktops on the fly was also part of the design decision.

To me, whether it is able to start with some defined number of multiple desktops or not is not really an interesting question.

The interesting question, since they now call desktops activities, 'will you actually someday be able to define an "activity" by name and have it come up with some defined list of applications running on that desktop?'.

Later, Seeker

---

### Post by ratcheer on 2010-10-28
> **seeker5528 said:**
> 

The interesting question, since they now call desktops activities, 'will you actually someday be able to define an "activity" by name and have it come up with some defined list of applications running on that desktop?'.



Now, ***that*** would be cool!

Tim

---

### Post by Reiger on 2010-10-28
Some day? You can have it today... 

[http://aseigo.blogspot.com/2010/10/activities-as-homonyms.html](http://aseigo.blogspot.com/2010/10/activities-as-homonyms.html)

I find it interesting how much of this stuff has been toyed, built and tested with in KDE already; Gnome would probably do well to adopt nepomuk and get lots of this sort of capability for free. The convergence between the two projects on terms of technical features implemented under the hoods suggests there's a way to merge consolidate these features in shared libraries. Akonadi is another prime example of this (which Gnome now supports as well AFAIK).

---

### Post by bash on 2010-10-28
> **ratcheer said:**
> Now, ***that*** would be cool!

Tim

Can't you already do something like this by hand with the current GNOME 2.x? I mean couldn't you just make a custom launcher that executes a shell script which starts you applications. And to make it fit in even better maybe make an extra category in the menu called "Activities". So you then get "Activities -> Coding" which executes a shell scripts, starting your IDE, a Nautilus window with your Source directory and a media player so can play death metal to help you concentrate.

---

### Post by moore.bryan on 2010-10-29
> **Reiger said:**
> Some day? You can have it today... 

[http://aseigo.blogspot.com/2010/10/activities-as-homonyms.html](http://aseigo.blogspot.com/2010/10/activities-as-homonyms.html)

I find it interesting how much of this stuff has been toyed, built and tested with in KDE already; Gnome would probably do well to adopt nepomuk and get lots of this sort of capability for free. The convergence between the two projects on terms of technical features implemented under the hoods suggests there's a way to merge consolidate these features in shared libraries. Akonadi is another prime example of this (which Gnome now supports as well AFAIK).

> **bash said:**
> Can't you already do something like this by hand with the current GNOME 2.x? I mean couldn't you just make a custom launcher that executes a shell script which starts you applications. And to make it fit in even better maybe make an extra category in the menu called "Activities". So you then get "Activities -> Coding" which executes a shell scripts, starting your IDE, a Nautilus window with your Source directory and a media player so can play death metal to help you concentrate.
Couldn't we just go in to one of the many GS files and change the name from "Activities," which I agree makes no sense, to "Overview," which--one can argue--it *should* be called any way?

---

### Post by Harry33 on 2010-10-29
> **moore.bryan said:**
> Couldn't we just go in to one of the many GS files and change the name from "Activities," which I agree makes no sense, to "Overview," which--one can argue--it *should* be called any way?

Wording "Overview" is definitely better thatn "Activities".
But then again, why use any word at all, a good looking GS-logo is even better.
Of coarse it could be ubuntu-logo in Ubuntu.

Anyway, I use mouse and hot-spot to open the overview, without any clicks.

---

### Post by tanmays on 2010-10-29
> **Harry33 said:**
> Well I think that we have to wait for a while until official natty repo version get upgraded, because new GS needs GTK3.0.

However, there is a PPA around that really works, with GTK3.0 and all other new GS_2.91 dependencies. Latest updates are of today.
And it will not mess Gnome Panel, both GTK2.0 and GTK3.0 do work.

Rico Tzschichholz - Staging PPA:
[https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging)

And a word of warning there too:
DO NOT USE THESE PACKAGES !!!

Is the PPA updated to recent version?

---

### Post by moore.bryan on 2010-10-29
> **Harry33 said:**
> Wording "Overview" is definitely better thatn "Activities".
But then again, why use any word at all, a good looking GS-logo is even better.
Of coarse it could be ubuntu-logo in Ubuntu.

Anyway, I use mouse and hot-spot to open the overview, without any clicks.
Found the lines... interestingly enough the markup previous to the line to change "Activities" to "Overview" gives us this:
```

/* Button on the left side of the panel. */
/* Translators: If there is no suitable word for "Activities" in your language, you can use the word for "Overview". */

```
That would tell me the word "Activities" is *specifically* intended; strange choice, no?

Any way, if you head to line 744 in panel.js, you can change "Actvities" to "Overview."
```

let label = new St.Label({ text: _("Overview") });

```

---

### Post by kaitwospirit on 2010-10-29
I still can't get gjs to compile. Now it's complaining about me lacking pretom.h in my xulrunner folder, which I have gathered is related to javascript, but have no idea how to fix. Reinstalling java, not surprisingly, didn't help.

---

### Post by cariboo on 2010-10-29
> **tanmays said:**
> Is the PPA updated to recent version?

I'm using the version from the rictoz ppa right now, it's the same version as  Merk42 linked to [here]("http://ubuntuforums.org/showpost.php?p=10036598&postcount=40").

---

### Post by seeker5528 on 2010-10-29
> **Reiger said:**
> Some day? You can have it today... 

[http://aseigo.blogspot.com/2010/10/activities-as-homonyms.html](http://aseigo.blogspot.com/2010/10/activities-as-homonyms.html)

I find it interesting how much of this stuff has been toyed, built and tested with in KDE already;

What KDE does, doesn't seem to allow for creating a launcher/.desktop file that will launch multiple applications from a single launcher. It's easy enough to create a script that you either add a link to somewhere or that is in the folder that folderview is pointed to, but you still have to switch to the desired desktop and run the script.

But what KDE does, does look pretty flexible. You can individually select between desktop and folder view on each desktop, have different wallpaper, different widgets, if folder view is chosen point each desktop to a different folder/location where you can filter the view to certain file types, have links to applications, etc..., or there is a folder view widget you can just place on a desktop and that whole set up can be saved as an activity, so one activity can cover a range of things on multiple desktops and with 3 clicks you can select a different activity that has a whole different range of stuff on multiple desktops. And plasma is not designed as an extension to kwin, so you can use whatever window manager/desktop environment you like and add plasma-desktop to your start up and it should work. 

> Gnome would probably do well to adopt nepomuk and get lots of this sort of capability for free. The convergence between the two projects on terms of technical features implemented under the hoods suggests there's a way to merge consolidate these features in shared libraries. Akonadi is another prime example of this (which Gnome now supports as well AFAIK).

I don't think that level of convergence is going to happen. What these types of things are being used to provide is interesting, but as long as the relevant database access is available and some standardized ontologies used, then the question of whether it's zeitgeist or nepomuk, or whatever being used in the background doesn't really seem all that interesting. 

Gnome shell seems much more limited by the nature of it's current design than by what these other background technologies will or won't allow, but not being a developer I can't really say if that is a hard limitation, or just where it happens to be at this particular stage of it's development. 

Later, Seeker

---

### Post by moore.bryan on 2010-10-30
> **seeker5528 said:**
> Gnome shell seems much more limited by the nature of it's current design than by what these other background technologies will or won't allow, but not being a developer I can't really say if that is a hard limitation, or just where it happens to be at this particular stage of it's development.
I would, somewhat, disagree here. A lot of comparison is drawn--rightfully so--between GS and other "launchers," but it's intended to be much more than that. I draw the comparison with the Apple iPad; technically, it *created* its own market for a device that *isn't* a collection of other things, but a new device itself. Although we can lump GNOME Shell into the window manager category, I believe it to be much more than that.

This is just the first iteration of it.

---

### Post by Harry33 on 2010-10-30
> **tanmays said:**
> Is the PPA updated to recent version?

Today (30th October) there is
gnome-shell - 2.91.1+git20101029.f21403fd-0ubuntu1~11.04~ricotz0.

So, yes it is.

Harry

---

### Post by seeker5528 on 2010-10-30
> **moore.bryan said:**
> I would, somewhat, disagree here. A lot of comparison is drawn--rightfully so--between GS and other "launchers," but it's intended to be much more than that. I draw the comparison with the Apple iPad; technically, it *created* its own market for a device that *isn't* a collection of other things, but a new device itself. Although we can lump GNOME Shell into the window manager category, I believe it to be much more than that.

On the iPad you could just as easily say that technically it is just a big iPhone, without the ability to actually use it like a phone.

If you are comparing 'launchers' you compare launchers. If you are comparing window managers, you compare window managers. If you compare shells you compare shells, plasma-desktop, Unity, and Gnome Shell. I can't think of anything else as far as Linux desktops go that might be grouped in that same category, and of these, IMHO, it seems clear the plasma-desktop is the most advance and the most flexible since the KDE guys created plasma in a forward looking way as something to take their development into the future and then built the shell out of that.

That's not to say that Unity and Gnome-Shell *need* the amount of flexibility plasma has in order to compete, but that means some things may have to be done outside the shell or tied to the shell in another way.

Later, Seeker

---

### Post by Reiger on 2010-10-30
I don't think you can compare plasma/gs/unity as equivalents. Unity/gs can be sort of compared because they both aim to provide roughly similar functionality: integrated launchers with desktop and window management.

But Plasma is somewhat a different beast. It is more of a blue print and a plumbing layer for the desktop than the actual desktop shell itself. That's the job of the various plasmoids, and as a result you can rip out/add/switch bits of the desktop at will.

---

### Post by moore.bryan on 2010-10-30
> **seeker5528 said:**
> On the iPad you could just as easily say that technically it is just a big iPhone, without the ability to actually use it like a phone.

If you are comparing 'launchers' you compare launchers. If you are comparing window managers, you compare window managers. If you compare shells you compare shells, plasma-desktop, Unity, and Gnome Shell. I can't think of anything else as far as Linux desktops go that might be grouped in that same category, and of these, IMHO, it seems clear the plasma-desktop is the most advance and the most flexible since the KDE guys created plasma in a forward looking way as something to take their development into the future and then built the shell out of that.

That's not to say that Unity and Gnome-Shell *need* the amount of flexibility plasma has in order to compete, but that means some things may have to be done outside the shell or tied to the shell in another way.

Later, Seeker
Some valid points, Seeker; however, the iPad *is not* an iPhone/iPod and was never intended to be. I know all the jokes about it, but those things aren't comparable.

> **Reiger said:**
> I don't think you can compare plasma/gs/unity as equivalents. Unity/gs can be sort of compared because they both aim to provide roughly similar functionality: integrated launchers with desktop and window management.

But Plasma is somewhat a different beast. It is more of a blue print and a plumbing layer for the desktop than the actual desktop shell itself. That's the job of the various plasmoids, and as a result you can rip out/add/switch bits of the desktop at will.
I would agree GS and Unity can be compared...

Good discussion guys!

---

### Post by moore.bryan on 2010-10-30
As of now, GS won't compile for me, dying here:
```


CCLD   test-theme
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_get_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell'
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

```
Anyone else? Any help?

Thanks!

---

### Post by Merk42 on 2010-10-30
> **moore.bryan said:**
> As of now, GS won't compile for me, dying here:
```


CCLD   test-theme
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_get_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell'
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

```
Anyone else? Any help?

Thanks!
I'm still on 10.10 but I just successfully built after deleting the folders ~/gnome-shell ~/source and the file ~/gnome-shell-build-setup.sh

---

### Post by bash on 2010-10-30
> **moore.bryan said:**
> As of now, GS won't compile for me, dying here:
```


CCLD   test-theme
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_get_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell'
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

```
Anyone else? Any help?

Thanks!

This seems to be [this error](http://ubuntuforums.org/showpost.php?p=9940810&postcount=795) again. Fix included in the link.

---

### Post by moore.bryan on 2010-10-31
Excellent... trying this now. Thanks, bash.

EDIT:
Worked like a charm; thanks, again.

---

### Post by youoh on 2010-10-31
running gnome-shell-build-setup.sh results in:

Please run 'sudo apt-get install libreadline5-dev ' and try again.

I have libreadline6-dev installed on wich depends swi-prolog.

manuelly edited the script and it seems to work.

---

### Post by davideotape on 2010-10-31
> **youoh said:**
> running gnome-shell-build-setup.sh results in:

Please run 'sudo apt-get install libreadline5-dev ' and try again.

I have libreadline6-dev installed on wich depends swi-prolog.

manuelly edited the script and it seems to work.

Yeah, if you get errors like that I think it's fine to manually edit the script to adjust for the lib that's installed.

---

### Post by Merk42 on 2010-10-31
It's not too noticeable in the new screenshots, but there is a new default theme when you run GNOME Shell. Quitting GNOME Shell returns you to whatever theme you were running.

---

### Post by bash on 2010-10-31
> **Merk42 said:**
> It's not too noticeable in the new screenshots, but there is a new default theme when you run GNOME Shell. Quitting GNOME Shell returns you to whatever theme you were running.

Oh wow, a new GTK+ theme. And I here I had hoped they merged back the overlay-redesign branch. Anyways time to recompile.

---

### Post by Half-Left on 2010-11-01
Just a note to NVIDIA users. Use maximum performance mode in the NVIDIA settings to get the best GNOME Shell performance.

Adaptive mode can make GS lag.

---

### Post by warrenc285 on 2010-11-01
> **Merk42 said:**
> It's not too noticeable in the new screenshots, but there is a new default theme when you run GNOME Shell. Quitting GNOME Shell returns you to whatever theme you were running.

Would you mind posting a screenshot of the new theme?

---

### Post by sgage on 2010-11-01
> **Half-Left said:**
> Just a note to NVIDIA users. Use maximum performance mode in the NVIDIA settings to get the best GNOME Shell performance.

Adaptive mode can make GS lag.


I don't seem to find such a setting in my "NVIDIA X-Server Settings". Can you direct me to where I might find it?

TIA

---

### Post by Half-Left on 2010-11-01
> **sgage said:**
> I don't seem to find such a setting in my "NVIDIA X-Server Settings". Can you direct me to where I might find it?

TIA

Should be under GPU- 0 > PowerMizer

---

### Post by Finalfantasykid on 2010-11-01
Unfortunatly I don't think you can select which performance mode you are in, Powermizer will still scale it for you, which causes lots of problems for me.

But I found this script which works perfectly for me :D

```

#!/bin/bash

while true; do
        nice /usr/bin/nvidia-settings -q all > /dev/null &
        sleep 25;
done

```

---

### Post by sgage on 2010-11-01
> **Half-Left said:**
> Should be under GPU- 0 > PowerMizer

Indeed it is - there is an entry for Performance Mode that is currently showing Maximum Performance. It doesn't seem to be settable - it's just a status line. But since I want max performance, no worries!

---

### Post by Half-Left on 2010-11-01
It's probably because you have an old GPU, which doesn't support power management. I can set it to adaptive or maximum performance for my 9600GT.

---

### Post by cariboo on 2010-11-01
My 8400GT and 9400GT don't allow you to make any changes from the nvidia panel, my 210GT does though. The 9400GT is already running at maximum

---

### Post by Half-Left on 2010-11-01
Strange. Here's mine.

---

### Post by sgage on 2010-11-01
> **Half-Left said:**
> Strange. Here's mine.

And here's mine.

Maybe it's a feature that my GPU doesn't have (GeForce 8500 GT).

---

### Post by Half-Left on 2010-11-01
Not sure, maybe newer GPU revisions have it. I'm using the 260.19.06 driver.

Anyway. When I set it to maximum performance, GNOME Shell is silky smooth all the time.

---

### Post by sgage on 2010-11-01
> **Half-Left said:**
> Not sure, maybe newer GPU revisions have it. I'm using the 260.19.06 driver.

Anyway. When I set it to maximum performance, GNOME Shell is silky smooth all the time.

I'm using the same driver. Probably just my old 8500.

Laugh of the day: I had left that screen shot open on my desktop, and no matter how many times I hit the quit button, nothing happened :KS

I suppose that's not as bad as the time I was reading a print magazine at my desk while checking my email, and tried to turn the page with the mouse...

---

### Post by cariboo on 2010-11-01
I'm using the same driver.

I'm using the version from ricotz ppa  (version 2.91.1+git20101030.3640a4dd-0ubuntu1~11.04~ricotz0) I find it very annoying that pop-up windows don't have a title bar. Is this the same if you build from source?

---

### Post by ratcheer on 2010-11-01
Is it possible to add the ricotz PPA to Maverick? The provided repository lines are for natty and when I added them, they all gave 404 errors. I removed them and changed "natty" to "maverick", but I still got the 404's.

Note that I only intend to try this on my testing system, just to see and play with Gnome Shell. Maybe I should just go ahead and install natty, there.

Tim

---

### Post by nilarimogard on 2010-11-01
> **cariboo907 said:**
> I'm using the same driver.

I'm using the version from ricotz ppa  (version 2.91.1+git20101030.3640a4dd-0ubuntu1~11.04~ricotz0) I find it very annoying that pop-up windows don't have a title bar. Is this the same if you build from source?

That's a new feature. In the changelog, it's called: "attaching modal dialogs to their parents"

---

### Post by cariboo on 2010-11-01
> **ratcheer said:**
> Is it possible to add the ricotz PPA to Maverick? The provided repository lines are for natty and when I added them, they all gave 404 errors. I removed them and changed "natty" to "maverick", but I still got the 404's.

Note that I only intend to try this on my testing system, just to see and play with Gnome Shell. Maybe I should just go ahead and install natty, there.

Tim

It looks like there is only a natty repository, but it should work with maverick. Did you remember to update the package list after adding the repository?

this is what the line in your sources .list should look like.

> deb [http://ppa.launchpad.net/ricotz/staging/ubuntu](http://ppa.launchpad.net/ricotz/staging/ubuntu) natty main

---

### Post by ratcheer on 2010-11-01
> **cariboo907 said:**
> It looks like there is only a natty repository, but it should work with maverick. Did you remember to update the package list after adding the repository?

this is what the line in your sources .list should look like.

Yes, I that is what I did. When I updated the Software Sources, it gave me the 404 Not Found. But, since the repository was in the list, I tried "sudo aptitude update" and it gave the 404's, again. When I removed the ppa from the Software Sources, update ran successfully, but of course, nothing from that ppa was included.

Tim

---

### Post by scradock on 2010-11-02
I got the same 404 errors when trying to start using the ricotz ppa; then I noticed that the OP instructions refer to adding the ppa:ricotz/testing. Re-doing "sudo add-apt-repository ppa:ricotz/staging" instead fixed the 404 errors. Apparently the key is the same, but has to be associated with the ppa correctly.

---

### Post by TheAnachron on 2010-11-02
Seriously, who told them about the new concept to be better? I don't see any reason why it should be faster, better or more useable.

I didn't test it, but that is my impression from the screenshots.

---

### Post by cariboo on 2010-11-02
Is this another new feature that came in today's gnome-shell update? Note the title bar.

---

### Post by scradock on 2010-11-02
> **scradock said:**
> I got the same 404 errors when trying to start using the ricotz ppa; then I noticed that the OP instructions refer to adding the ppa:ricotz/testing. Re-doing "sudo add-apt-repository ppa:ricotz/staging" instead fixed the 404 errors. Apparently the key is the same, but has to be associated with the ppa correctly.
To be sure, check the files in /etc/apt/sources.list.d/

If there is a "ricotz-testing-natty.list" as well as "ricotz-staging-natty.list" you should be ableto remove the -testing- one - apparently it doesn't exist anymore.

---

### Post by Merk42 on 2010-11-02
> **cariboo907 said:**
> Is this another new feature that came in today's gnome-shell update? Note the title bar.
The theme? I mentioned it a few posts ago (also you'll see it present in the first post).
I do find it interesting your buttons are on the left. Mine are on the right even though I'm using Ambiance. I'm building from source, perhaps what you're doing is causing the difference?
[ATTACH]174365[/ATTACH]

---

### Post by cariboo on 2010-11-02
> **Merk42 said:**
> The theme? I mentioned it a few posts ago (also you'll see it present in the first post).
I do find it interesting your buttons are on the left. Mine are on the right even though I'm using Ambiance. I'm building from source, perhaps what you're doing is causing the difference?
[ATTACH]174365[/ATTACH]

I moved then to the left, as that's what I'm used to [[IMG]http://imgur.com/R3LbN.png[/IMG]](http://imgur.com/R3LbN.png). I saw your post about a new theme, but obviously it didn't sink in.

---

### Post by ratcheer on 2010-11-03
> **cariboo907 said:**
> It looks like there is only a natty repository, but it should work with maverick. Did you remember to update the package list after adding the repository?

this is what the line in your sources .list should look like.

Ok, I got the repository added and installed gnome-shell and gnome3-session. I cannot get it to work, correctly. I can log in to the Gnome3 desktop, but my screen only has the background, no top panel. I can right-click on the desktop and get a flashing create launcher (or file or folder) dialog. If I create a folder, its icon is flashing, too.

Any idea how I can get from this to a functional Gnome3 desktop? This is on my Maverick testing image.

Thanks,
Tim

---

### Post by jorambler on 2010-11-03
> **TheAnachron said:**
> Seriously, who told them about the new concept to be better? I don't see any reason why it should be faster, better or more useable.

I didn't test it, but that is my impression from the screenshots.
No one told, as well as no one did say the old gnome shell was good enough to use as primary shell )

---

### Post by lucien on 2010-11-04
> **ratcheer said:**
> 
Any idea how I can get from this to a functional Gnome3 desktop? This is on my Maverick testing image.


Hi. Got the same issue here. Try running "gnome-shell --replace" in a terminal and you'll see some errormessages about mismatching GObject Introspection files.

Now you could just fetch the newest version of the corresponding "gir-<library-name>" packages from the natty repository (perhaps you should also update the "lib<library-name>" packes).

Greetings,
lucien

---

### Post by ricotz on 2010-11-04
> **ratcheer said:**
> Ok, I got the repository added and installed gnome-shell and gnome3-session. I cannot get it to work, correctly. I can log in to the Gnome3 desktop, but my screen only has the background, no top panel. I can right-click on the desktop and get a flashing create launcher (or file or folder) dialog. If I create a folder, its icon is flashing, too.

Any idea how I can get from this to a functional Gnome3 desktop? This is on my Maverick testing image.

Thanks,
Tim

 There is a reason why there are no package for maverick. Trying to patch up things while installing the natty packages on maverick might lead to a real mess. The dependencies needed to build the packages on maverick are not met and won't be available. So please don't try this way. 

The only way to test gnome-shell on maverick or less is jhbuild.

---

### Post by Harry33 on 2010-11-04
> **ratcheer said:**
> Ok, I got the repository added and installed gnome-shell and gnome3-session. I cannot get it to work, correctly. I can log in to the Gnome3 desktop, but my screen only has the background, no top panel. I can right-click on the desktop and get a flashing create launcher (or file or folder) dialog. If I create a folder, its icon is flashing, too.
Any idea how I can get from this to a functional Gnome3 desktop? This is on my Maverick testing image.
Thanks,
Tim

Ricotz staging repository does not work with Maverick, not even with a fully updated Maverick.
Rico has removed some packages (gobject-introspection, glib) and it is assumed that one uses the official Natty development packages instead.

So with Maverick, only use the official repos and you get a fully workin gnome-shell (v. 2.31.5).
or, if it is a newer GS you want,
upgrade to Natty and then add ricotz repository to sources.list
and be prepared to possible breakages in future. :guitar:

---

### Post by ratcheer on 2010-11-04
> **ricotz said:**
> There is a reason why there are no package for maverick. Trying to patch up things while installing the natty packages on maverick might lead to a real mess. The dependencies needed to build the packages on maverick are not met and won't be available. So please don't try this way. 

The only way to test gnome-shell on maverick or less is jhbuild.

Thank you. It is time to install natty in my testing partition. (Thanks also, Harry33)

Tim

---

### Post by ratcheer on 2010-11-04
Ok, I have upgraded my testing system to natty and am now running gnome-shell. It is very nice, much better than the current Unity.

Thanks, everyone.

Tim

---

### Post by rudihawk on 2010-11-05
Currently building it from source. 

Wow, it is taking ages!

---

### Post by sgage on 2010-11-05
I compiled GS today, and not much seems to have changed since yesterday :KS

However, I am running Thunderbird's Indicator addon, which uses the "envelope" notifier to indicate new incoming email to Thunderbird. Every time new mail arrives, GS crashes (disappears gracefully to the panels).

Anyone else getting this?

[Edited: Not so sure now - I think it was coincidence. Something is crashing GS regularly, though.]

---

### Post by simpleblue on 2010-11-07
> **sgage said:**
> I compiled GS today, and not much seems to have changed since yesterday :KS

However, I am running Thunderbird's Indicator addon, which uses the "envelope" notifier to indicate new incoming email to Thunderbird. Every time new mail arrives, GS crashes (disappears gracefully to the panels).

Anyone else getting this?

[Edited: Not so sure now - I think it was coincidence. Something is crashing GS regularly, though.]

If you want the full bleeding-edge experience I recommend installing Fedora 14 and trying it out. It seems that Ubuntu has abandoned Gnome shell, and Mint is staying with the current version of Gnome.

I have not had one crash yet on my F14 install... And installing GS on Fedora is a breeze:

```
su
yum install gnome-shell
```

p.s. If you don't like it, just goto Control Center-> Desktop Effects, and switch it back to regular gnome.

Enjoy! :popcorn:

---

### Post by bash on 2010-11-07
> **simpleblue said:**
> If you want the full bleeding-edge experience I recommend installing Fedora 14 and trying it out. It seems that Ubuntu has abandoned Gnome shell, and Mint is staying with the current version of Gnome.

Unless they will update the version in Fedora, F14 uses the exact same version of GNOME Shell (2.31.5) as Maverick. Rawhide has 2.91.1 (as does ricotz stating PPA), which is the latest "officially" release version. But bleeding edge in this case I would consider nightlies or compiled directly from git. 

So don't know why you recommend Fedora for the full bleeding-edge experience. I can happily run the Shell compiled from git in 10.10, except for the strangely translucent window borders I get with fglrx.

---

### Post by dext on 2010-11-07
> **bash said:**
> Unless they will update the version in Fedora, F14 uses the exact same version of GNOME Shell (2.31.5) as Maverick. Rawhide has 2.91.1 (as does ricotz stating PPA), which is the latest "officially" release version. But bleeding edge in this case I would consider nightlies or compiled directly from git. 

So don't know why you recommend Fedora for the full bleeding-edge experience. I can happily run the Shell compiled from git in 10.10, except for the strangely translucent window borders I get with fglrx.

there are to many dependancies that would need to go into F14 for Fedora to have GS2.91 .. im sure i could dig up a post from Adam Williamson about this same conversation in Fedoraforum. only way you'll get the latest GS in Maverick or F14 an thats to build it from jhbuild 

[http://forums.fedoraforum.org/showthread.php?t=246640](http://forums.fedoraforum.org/showthread.php?t=246640)

---

### Post by davideotape on 2010-11-07
Surely the bleeding edge is compiling from git, not installing anything from a repo?

---

### Post by davideotape on 2010-11-07
Hmm, now getting this error:

```
checking for VORBIS... configure: error: Package requirements ( vorbisfile ) were not met:

No package 'vorbisfile' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables VORBIS_CFLAGS
and VORBIS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

*** Error during phase configure of libcanberra: ########## Error running ./configure --prefix /home/david/gnome-shell/install --libdir '/home/david/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [23/25]

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

I've checked the repos, but I can't seem to find a vorbisfile package. Any ideas where to go from here?

---

### Post by xtoudi on 2010-11-07
Try libvorbis-dev.

---

### Post by simpleblue on 2010-11-07
> **davideotape said:**
> Surely the bleeding edge is compiling from git, not installing anything from a repo?

You're right. I was thinking of Rawhide and nightly builds when I wrote it.

> there are to many dependancies that would need to go into F14 for Fedora to have GS2.91 .. im sure i could dig up a post from Adam Williamson about this same conversation in Fedoraforum. only way you'll get the latest GS in Maverick or F14 an thats to build it from jhbuild 

It 'seems' to be working for me?. Does this means that perhaps I'm running an incomplete gnome shell? Or just one that is not able to update?

---

### Post by dext on 2010-11-07
> **simpleblue said:**
> It 'seems' to be working for me?. Does this means that perhaps I'm running an incomplete gnome shell? Or just one that is not able to update?
 depends where you got the updated GS from? ppa? or JHBuild?

---

### Post by simpleblue on 2010-11-07
> **dext said:**
> depends where you got the updated GS from? ppa? or JHBuild?

I just typed "yum install gnome-shell". I'm guessing I don't have the most updated version.

Is there an easy way to update to the latest version? Or perhaps a distro that comes with Gnome 3 preinstalled?

---

### Post by Merk42 on 2010-11-08
> **simpleblue said:**
> I just typed "yum install gnome-shell". I'm guessing I don't have the most updated version.

Is there an easy way to update to the latest version? Or perhaps a distro that comes with Gnome 3 preinstalled?

GNOME Shell is only part of GNOME 3. As both are in progress I don't know of any distro that has it preinstalled.

To get the latest version, read the first post of this thread. Granted the instructions assume you're using Ubuntu, but the only difference if any would be dependencies, which it will notify you of.

---

### Post by dext on 2010-11-08
> **simpleblue said:**
> I just typed "yum install gnome-shell". I'm guessing I don't have the most updated version.

Is there an easy way to update to the latest version? Or perhaps a distro that comes with Gnome 3 preinstalled?

Fedora13 came with Gnome-Shell preinstalled for users to try. only way to get the latest in Fedora without using JHbuild an thats to use Rawhide as in using a complete F15. as i said in a previous post, im sure i posted AdamW's post about why GS2.91 is not in F14

---

### Post by davideotape on 2010-11-08
> **xtoudi said:**
> Try libvorbis-dev.

Thank you good sir :)

Compiled fine, started it fine, saw the new theme, quickly stopped it.

---

### Post by xtoudi on 2010-11-08
> **davideotape said:**
> Thank you good sir :)

Compiled fine, started it fine, saw the new theme, quickly stopped it.

Like it too ... new theme ;)

---

### Post by simpleblue on 2010-11-08
I compiled on my Ubuntu Laptop last night and it got to clutter 24/25 and then displayed:


"undefined reference" errors

:(

Deleted gnome-shell folder and trying again.

Hope it works this time. [-o<

---

### Post by Merk42 on 2010-11-08
[**[SIZE="4"]GNOME Shell 2.91.2 released[/SIZE]**](http://mail.gnome.org/archives/gnome-shell-list/2010-November/msg00013.html)


> **simpleblue said:**
> I compiled on my Ubuntu Laptop last night and it got to clutter 24/25 and then displayed:


"undefined reference" errors

:(

Deleted gnome-shell folder and trying again.

Hope it works this time. [-o<

> **Merk42 said:**
> **I'm getting a lot of "undefined reference" errors**
try ```
rm ~/gnome-shell/install/*.la /usr/lib/*.la
```
Then jhbuild build
If it still doesn't work, delete the ~/gnome-shell folder and try again

---

### Post by bash on 2010-11-08
> **Merk42 said:**
> [**[SIZE="4"]GNOME Shell 2.91.2 released[/SIZE]**](http://mail.gnome.org/archives/gnome-shell-list/2010-November/msg00013.html)

> 593844 Alternative overview design idea

Got excited for a second when I saw this and hoped the overlay-redesign branch had finally been merged, but alas it was some bug from January. And sadly it seems work on the branch to make the overlay completely look like the new mock-ups has stopped as well.

---

### Post by simpleblue on 2010-11-08
> **Merk42 said:**
> [**[SIZE="4"]GNOME Shell 2.91.2 released[/SIZE]**](http://mail.gnome.org/archives/gnome-shell-list/2010-November/msg00013.html)

Thanks. This command did not work for me, however deleting the gnome-shell folder and recompiling did.

I'm liking GS3 alot. They've added the Universal Access applet at the top. So you can have a mouse keyboard, magnify, or have the screen contents be read to you... You could do this in regular Ubuntu but this time the menu is integrated with GS graphics.

They also made it so that if a notification pops up you can click on it to bring you to that program.


While running I noticed terminal say something I thought was perhaps a trifle suggestive:

```
Info: No sexy-python package found, don't worry it's optional.
```

:P

---

### Post by seeker5528 on 2010-11-08
I got Gnome-Shell from the ricotz staging repository and it works this time. It screws up all my other gnome logins, no matter window manager I attempt to use with it, but at least I am still able to log using a KDE, Lubuntu, or Openbox session. 

Apparently if you are like me, remove pulse-audio and use kmix instead by adding a kmix to the start up using the command 'kmix --keepvisibility' you are screwed. On the one hand by Gnome-Shell because it doesn't do the right thing when you click on kmix in the notification area and on the other hand by kmix itself because apparently what you used the --keepvisibility option for in the past is what it always does now, so if kmix was only showing in the tray area on it's last run it will only show in the tray area on it's next run, if kmix was showing the full mixer on it's last run it will show the full mixer on it's next run. D'oh

Later, Seeker

---

### Post by simpleblue on 2010-11-09
Distorted backgrounds when in this mode:



I'm running Fedora 14 with Gnome 3. The Ubuntu Gnome 3 didn't have this prob. Backgrounds were normal when in desktop mode.  I've tried using different images and changing from stretch to zoom to center... same issue.


This is what the terminal says:


```
[user@localhost src]$ ./gnome-shell --replace
Gtk-Message: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot open shared object file: No such file or directory
Panel leaving: a new panel shell is starting.

(gnome-panel:3137): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
      JS LOG: GNOME Shell started at Tue Nov 09 2010 02:17:18 GMT-0500 (EST)

(mutter:3184): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:3196): WARNING **: Error opening /var/log/ConsoleKit/history (Permission denied)
```

---

### Post by kyleabaker on 2010-11-10
Great thread! I hadn't looked into Gnome Shell much previously, but most of my questions were answered in the first post. I'm still not sure about Unity, but I guess I will be testing them both side by side at some point after Natty is released (or at least reaches alpha 2).

I know the whole browser ballot screen topic has been brought up for various elements of the OS for Mac/Win/Lin, but I think in this case it would be a great option to have, even if its a bit hidden during installation, so that users can install the environment they want right off the bat. Unfortunately, this probably isn't feasible with the disc size limit being such an issue these days. :/

I've grown to love Gnome 2.x over the years, with a dual screen setup and both panels on the bottom (one on each obviously). The biggest thing for me is that I want to keep my displays balanced in this way. So what I can tell from the screen shots of Gnome Shell, the setup is just a top panel with everything merged into it? Is that right?

---

### Post by moore.bryan on 2010-11-10
Anyone else getting this when trying to build today?
```


collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/bryan/gnome-shell/source/gtk3/gtk/tmp-introspectBwgO1O/Gtk-3.0', '-export-dynamic', '-L.', 'libgtk-x11-3.0.la', '../gdk/x11/libgdk-x11.la', '-pthread', '-L/home/bryan/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/bryan/gnome-shell/source/gtk3/gtk/tmp-introspectBwgO1O/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gtk3'
make: *** [all] Error 2

```

---

### Post by Saprissa on 2010-11-10
> **moore.bryan said:**
> Anyone else getting this when trying to build today?
```


collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/bryan/gnome-shell/source/gtk3/gtk/tmp-introspectBwgO1O/Gtk-3.0', '-export-dynamic', '-L.', 'libgtk-x11-3.0.la', '../gdk/x11/libgdk-x11.la', '-pthread', '-L/home/bryan/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/bryan/gnome-shell/source/gtk3/gtk/tmp-introspectBwgO1O/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gtk3'
make: *** [all] Error 2

```

I just completed a build 3 minutes ago without any errors, fwiw.

---

### Post by Saprissa on 2010-11-10
Ignore

---

### Post by sgage on 2010-11-11
Well, it had been a while, so I decided to see what was new with GS. Started from scratch. Didn't get far into building gobject-introspection  [2/25] when it gave up the ghost thusly:

```
*** Building gobject-introspection *** [2/25]
make  
make  all-recursive
make[1]: Entering directory `/home/sgage/gnome-shell/source/gobject-introspection'
Making all in .
make[2]: Entering directory `/home/sgage/gnome-shell/source/gobject-introspection'
  CCLD   g-ir-compiler
/usr/bin/ld: g_ir_compiler-compiler.o: undefined reference to symbol 'g_file_new_for_path'
/usr/bin/ld: note: 'g_file_new_for_path' is defined in DSO /home/sgage/gnome-shell/install/lib/libgio-2.0.so.0 so try adding it to the linker command line
/home/sgage/gnome-shell/install/lib/libgio-2.0.so.0: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [g-ir-compiler] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/25]
```

Any ideas?

TIA...

---

### Post by Anduu on 2010-11-11
> **sgage said:**
> Well, it had been a while, so I decided to see what was new with GS. Started from scratch. Didn't get far into building gobject-introspection  [2/25] when it gave up the ghost thusly:

```
*** Building gobject-introspection *** [2/25]
make  
make  all-recursive
make[1]: Entering directory `/home/sgage/gnome-shell/source/gobject-introspection'
Making all in .
make[2]: Entering directory `/home/sgage/gnome-shell/source/gobject-introspection'
  CCLD   g-ir-compiler
/usr/bin/ld: g_ir_compiler-compiler.o: undefined reference to symbol 'g_file_new_for_path'
/usr/bin/ld: note: 'g_file_new_for_path' is defined in DSO /home/sgage/gnome-shell/install/lib/libgio-2.0.so.0 so try adding it to the linker command line
/home/sgage/gnome-shell/install/lib/libgio-2.0.so.0: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [g-ir-compiler] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/25]
```

Any ideas?

TIA...

I have been building it daily for the last couple of weeks.Started getting this error 3 days ago.

I suspect with the slew of updates lately in Natty something has been broken but I haven't been able to track down the source yet....I haven't tried all that hard yet mind you.I'm hoping it will sort itself out ;)

---

### Post by Merk42 on 2010-11-11
> **Anduu said:**
> I have been building it daily for the last couple of weeks.Started getting this error 3 days ago.

I suspect with the slew of updates lately in Natty something has been broken but I haven't been able to track down the source yet....I haven't tried all that hard yet mind you.I'm hoping it will sort itself out ;)Doesn't work here in 10.10 either, I'm guessing that since it started right after GNOME reached 2.91.2 it's just the early severe breakage expected when starting a new point release.

---

### Post by sgage on 2010-11-12
Still no joy as of 11:00 a.m. EST. Guess I'll just keep trying from time to time until it clicks...

---

### Post by xtoudi on 2010-11-12
Checkout latest **overview-relayout** branch. 
Once again a lot of visual changes.

Now it looks like this ... but it's still so slow ...

*compiled on maverick*

EDIT.
Compiled again: overview: Update animation ([http://git.gnome.org/browse/gnome-shell/commit/?h=overview-relayout](http://git.gnome.org/browse/gnome-shell/commit/?h=overview-relayout))

and now animations are very fast ... but searching not so much :-)

---

### Post by moore.bryan on 2010-11-12
Still no love compiling at 7:22pm EDT.

---

### Post by dext on 2010-11-12
> **xtoudi said:**
> Checkout latest **overview-relayout** branch. 
Once again a lot of visual changes.

Now it looks like this ... but it's still so slow ...

*compiled on maverick*

EDIT.
Compiled again: overview: Update animation ([http://git.gnome.org/browse/gnome-shell/commit/?h=overview-relayout](http://git.gnome.org/browse/gnome-shell/commit/?h=overview-relayout))

and now animations are very fast ... but searching not so much :-) is that pic of GS or Unity?

---

### Post by Anduu on 2010-11-12
O.K. I am compiling again right now and it seems to have worked itself out...made it past stage 2 :KS

Keeping my fingers crossed that nothing new pops up.

EDIT

Still compiling,however,I just noticed there are now 28 stages...If I am not mistaken there were only 23 before weren't there?

---

### Post by Finalfantasykid on 2010-11-13
I was able to compile it earlier today, all 28 stages.  I had to do complete wipe of the directory though to get it to work.

I don't see anything different though.  I am using Maverick btw.

---

### Post by Anduu on 2010-11-13
D'oh!So close....

Stage 27/28

```
/usr/bin/ld: run_js_test-run-js-test.o: undefined reference to symbol 'gjs_context_new_with_search_path'
/usr/bin/ld: note: 'gjs_context_new_with_search_path' is defined in DSO /home/gstesting/gnome-shell/install/lib64/libgjs.so.0 so try adding it to the linker command line
/home/gstesting/gnome-shell/install/lib64/libgjs.so.0: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[3]: *** [run-js-test] Error 1
make[3]: Leaving directory `/home/gstesting/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/gstesting/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gstesting/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
```

---

### Post by xtoudi on 2010-11-13
> **dext said:**
> is that pic of GS or Unity?

It's GS - overview-relayout branch.

> **Finalfantasykid said:**
> I was able to compile it earlier today, all 28 stages.  I had to do complete wipe of the directory though to get it to work.

I don't see anything different though.  I am using Maverick btw.

Master branch looks like previous. You need to compile overview-relayout branch.

---

### Post by dext on 2010-11-13
> **xtoudi said:**
> It's GS - overview-relayout branch.doesnt look to bad.

---

### Post by moore.bryan on 2010-11-13
Grrr... compiling died at 23/28 because it can't find 'vorbisfile' even though I have the 'libvorbisfile3' and 'libvorbisfile-ruby1.8' installed.

Irritating!

---

### Post by xtoudi on 2010-11-13
> **moore.bryan said:**
> Grrr... compiling died at 23/28 because it can't find 'vorbisfile' even though I have the 'libvorbisfile3' and 'libvorbisfile-ruby1.8' installed.

Irritating!

libvorbis-dev is what you need.

---

### Post by moore.bryan on 2010-11-13
Thanks, xtoudi... I should have posted-back I figured that one out. Right now, it's sticking trying to build gnome-settings-daemon.
```


/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [26/28]

```

---

### Post by sgage on 2010-11-13
I see that people have been having some luck getting GS to compile. I just tried (after deleting the existing gnome-shell directory) and couldn't get through step 2:

```
/usr/bin/ld: ./.libs/libgirepository-parser.a(libgirepository_parser_la-giroffsets.o): undefined reference to symbol 'ffi_type_void'
/usr/bin/ld: note: 'ffi_type_void' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.5.2/../../../../lib/libffi.so so try adding it to the linker command line
/usr/lib/gcc/i686-linux-gnu/4.5.2/../../../../lib/libffi.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [g-ir-compiler] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/28]
```

I wonder if something in the big batch of upgrades this morning has broken it again...

Oh well, back to waiting.

---

### Post by moore.bryan on 2010-11-13
> **sgage said:**
> I see that people have been having some luck getting GS to compile. I just tried (after deleting the existing gnome-shell directory) and couldn't get through step 2:

Hmm... I get through that. Have you tried wiping the whole gnome-shell dir and starting fresh?

---

### Post by sgage on 2010-11-13
Yes, I wiped out ~/gnome-shell. Did you download that big wad of upgrades this morning?

[edit: I should add that I am doing this in natty]

---

### Post by moore.bryan on 2010-11-13
I've been trying to compile for three days now, with not one working. Right now, I'm on polkit [25/28], so we'll see soon... I hope.

---

### Post by moore.bryan on 2010-11-13
Still dies at gnome-settings-daemon [26/28] make with
```

CCLD   test-media-keys
/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [26/28]

```
Any ideas, folks?

When I skip this step and continue to build, gnome-shell [27/28] dies during make, so I guess this is kind of important.

---

### Post by xtoudi on 2010-11-13
> **moore.bryan said:**
> Still dies at gnome-settings-daemon [26/28] make with
```

CCLD   test-media-keys
/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [26/28]

```
Any ideas, folks?

When I skip this step and continue to build, gnome-shell [27/28] dies during make, so I guess this is kind of important.

Try **rm~/gnome-shell/install/lib/*.la** or **rm ~/gnome-shell/install/lib64/*.la** (if you have 64bit).
Then if you get an error chose 6 (get a whole module again).

---

### Post by moore.bryan on 2010-11-13
> **xtoudi said:**
> Try **rm~/gnome-shell/install/lib/*.la** or **rm ~/gnome-shell/install/lib64/*.la** (if you have 64bit).
Then if you get an error chose 6 (get a whole module again).
I tried that before and it didn't work, but I'll give it another shot... worth trying anything again.

---

### Post by xtoudi on 2010-11-13
Latest commit:
**	Skip drawing transparent borders and backgrounds** ([http://git.gnome.org/browse/gnome-shell/commit/?id=3138b20b11d67eb05fdda1926b7b0550dc2724d8](http://git.gnome.org/browse/gnome-shell/commit/?id=3138b20b11d67eb05fdda1926b7b0550dc2724d8))
this improves speed of GS a lot!! At least for me (Intel HD graphics).

Then you can merge master branch with overview-relayout to get speed and new UI.
```
cd ~/gnome-shell/source/gnome-shell
git merge overview-relayout
jhbuild buildone gnome-shell
```

And we've got latest master commits with overview-relayout branch.

---

### Post by moore.bryan on 2010-11-13
I've--finally--successfully built as of 11:54am EDT.

@xtoudi: How do a merge the transparent fix?

---

### Post by xtoudi on 2010-11-13
> **moore.bryan said:**
> I've--finally--successfully built as of 11:54am EDT.

@xtoudi: How do a merge the transparent fix?

Commit about skipping transparent borders ... is in master branch ... so standard compiling (jhbuild build) do that.

If you want to try overview-relayout branch (checkout att) do what I wrote previously.

---

### Post by moore.bryan on 2010-11-13
Right... thanks, xtoudi. I've tried the new overview layout and didn't like it, so I'm back to 'standard.'

---

### Post by xtoudi on 2010-11-13
> **moore.bryan said:**
> Right... thanks, xtoudi. I've tried the new overview layout and didn't like it, so I'm back to 'standard.'

This overview-relayout branch has UI interface similar to latest mockups so I'm afraid soon will be merged with master.
But ... will see :-)

---

### Post by Merk42 on 2010-11-13
For anyone having trouble, deleted ~/gnome-shell ~/source and gnome-shell-build-setup.sh and start all over.
Also libpam-dev is a new dependency

---

### Post by sgage on 2010-11-13
> **Merk42 said:**
> For anyone having trouble, deleted ~/gnome-shell ~/source and gnome-shell-build-setup.sh and start all over.
Also libpam-dev is a new dependency

Still no success - same problem at gobject-introspection. Help!

---

### Post by zuoken on 2010-11-13
My build was stalling at phase 2 with the error

```
** ERROR **: Invalid typelib for module 'GLib': In directory (Context: read_unichar/IOChannel)): Wrong tag in simple type
aborting...
/bin/bash: line 1:  7685 Trace/breakpoint trap   ./g-ir-compiler --includedir=. --includedir=./gir --includedir=. --includedir=. --includedir=. GLib-2.0.gir -o GLib-2.0.typelib
``` 

I'm guessing this has something to do with the last night's newly enabled gunichar.  Disabling gunichar in the scanner seems to work:

```
 @@ changes at line 143 in /giscanner/introspectablepass.py @@ class IntrospectablePass(object):
         if typeval.target_fundamental:
             if typeval.is_equiv(ast.TYPE_VALIST):
                 return False
+            # Mark UCHAR as not introspectable temporarily until
+            # we're ready to land the typelib changes
+            if typeval.is_equiv(ast.TYPE_UNICHAR):
+                return False
             # These are not introspectable pending us adding
             # larger type tags to the typelib (in theory these could
             # be 128 bit or larger)
```

jhbuild will automatically undo your changes if you're not careful, so you should run the commands in the following order:

```
jhbuild update
<edit /giscanner/introspectablepass.py as described above>
jhbuild clean gobject-introspection
jhbuild build --no-network
```

---

### Post by Dobbie03 on 2010-11-13
I just successfully built GS from Git but I want to know how to make GS start at login, anyone got any ideas how to do this?

---

### Post by cmwatford on 2010-11-13
> **MattDobson said:**
> I just successfully built GS from Git but I want to know how to make GS start at login, anyone got any ideas how to do this?
This should do it.
[http://live.gnome.org/GnomeShell#Running_gnome-shell_at_the_start_of_your_session](http://live.gnome.org/GnomeShell#Running_gnome-shell_at_the_start_of_your_session)

Edit: missed the part about git. Same principle should apply though. Just set it in startup preferences.

---

### Post by xtoudi on 2010-11-13
> **MattDobson said:**
> I just successfully built GS from Git but I want to know how to make GS start at login, anyone got any ideas how to do this?

```
ln -s ~/gnome-shell/install/share/applications/gnome-shell.desktop ~/.local/share/applications/gnome-shell.desktop
gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "gnome-shell" -t string
```

---

### Post by Anduu on 2010-11-13
I just wrote a quick script and added it to my startup applications.

```
#!/bin/sh
sleep 10
cd /home/gstesting/gnome-shell/source/gnome-shell/src/
./gnome-shell --replace
```

Saves me the trouble of having to revert back to standard gnome for whatever reason.

---

### Post by sgage on 2010-11-13
> **zuoken said:**
> My build was stalling at phase 2 with the error

```
** ERROR **: Invalid typelib for module 'GLib': In directory (Context: read_unichar/IOChannel)): Wrong tag in simple type
aborting...
/bin/bash: line 1:  7685 Trace/breakpoint trap   ./g-ir-compiler --includedir=. --includedir=./gir --includedir=. --includedir=. --includedir=. GLib-2.0.gir -o GLib-2.0.typelib
``` 

I'm guessing this has something to do with the last night's newly enabled gunichar.  Disabling gunichar in the scanner seems to work:

```
 @@ changes at line 143 in /giscanner/introspectablepass.py @@ class IntrospectablePass(object):
         if typeval.target_fundamental:
             if typeval.is_equiv(ast.TYPE_VALIST):
                 return False
+            # Mark UCHAR as not introspectable temporarily until
+            # we're ready to land the typelib changes
+            if typeval.is_equiv(ast.TYPE_UNICHAR):
+                return False
             # These are not introspectable pending us adding
             # larger type tags to the typelib (in theory these could
             # be 128 bit or larger)
```

jhbuild will automatically undo your changes if you're not careful, so you should run the commands in the following order:

```
jhbuild update
<edit /giscanner/introspectablepass.py as described above>
jhbuild clean gobject-introspection
jhbuild build --no-network
```

I followed the steps you outlined, but gobject-introspection still won't compile:

```
*** Building gobject-introspection *** [2/28]
make  
make  all-recursive
make[1]: Entering directory `/home/sgage/gnome-shell/source/gobject-introspection'
Making all in .
make[2]: Entering directory `/home/sgage/gnome-shell/source/gobject-introspection'
  CCLD   g-ir-compiler
/usr/bin/ld: ./.libs/libgirepository-parser.a(libgirepository_parser_la-giroffsets.o): undefined reference to symbol 'ffi_type_void'
/usr/bin/ld: note: 'ffi_type_void' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.5.2/../../../../lib/libffi.so so try adding it to the linker command line
/usr/lib/gcc/i686-linux-gnu/4.5.2/../../../../lib/libffi.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [g-ir-compiler] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/28]
```

Any idea what's going on?

---

### Post by Dobbie03 on 2010-11-13
> **xtoudi said:**
> ```
ln -s ~/gnome-shell/install/share/applications/gnome-shell.desktop ~/.local/share/applications/gnome-shell.desktop
gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "gnome-shell" -t string
```

Thanks, works perfectly.

---

### Post by Dobbie03 on 2010-11-13
> **Anduu said:**
> I just wrote a quick script and added it to my startup applications.

```
#!/bin/sh
sleep 10
cd /home/gstesting/gnome-shell/source/gnome-shell/src/
./gnome-shell --replace
```

Saves me the trouble of having to revert back to standard gnome for whatever reason.

Cool I used the option in the post before yours and that worked spot on.  Thanks for your help anyway.

---

### Post by Dobbie03 on 2010-11-13
Hopefully one last thing, is there anyway to change the default theme?

---

### Post by BobCFC on 2010-11-13
> **moore.bryan said:**
> Still dies at gnome-settings-daemon [26/28] make with
```

CCLD   test-media-keys
/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [26/28]

```
Any ideas, folks?

When I skip this step and continue to build, gnome-shell [27/28] dies during make, so I guess this is kind of important.

I was also stuck at step 26/28 with undefined reference. I got a 404 with rm ~/gnome-shell/install/lib64/*.la but followed these instructions to remove my global .la files and that worked

[http://live.gnome.org/GnomeShell/RemovingLaFiles](http://live.gnome.org/GnomeShell/RemovingLaFiles)

---

### Post by augias on 2010-11-13
> **MattDobson said:**
> Hopefully one last thing, is there anyway to change the default theme?

Thats "easy". Edit the CSS file in it. This post ought to give you some good pointers. [http://ubuntuforums.org/showthread.php?t=1479239](http://ubuntuforums.org/showthread.php?t=1479239) 

This post has examples of themes, but i wouldnt download them because the CSS file structure has changed over time upstream. you could download some and copy/paste specific parts but not the entire file. [http://ubuntuforums.org/showthread.php?t=1418056](http://ubuntuforums.org/showthread.php?t=1418056)

---

### Post by Dobbie03 on 2010-11-13
> **augias said:**
> Thats "easy". Edit the CSS file in it. This post ought to give you some good pointers. [http://ubuntuforums.org/showthread.php?t=1479239](http://ubuntuforums.org/showthread.php?t=1479239) 

This post has examples of themes, but i wouldnt download them because the CSS file structure has changed over time upstream. you could download some and copy/paste specific parts but not the entire file. [http://ubuntuforums.org/showthread.php?t=1418056](http://ubuntuforums.org/showthread.php?t=1418056)

Cool thanks for that.

---

### Post by sgage on 2010-11-15
Tried a compile from scratch this morning - still no luck with gobject-introspection:

```
/usr/bin/ld: ./.libs/libgirepository-parser.a(libgirepository_parser_la-giroffsets.o): undefined reference to symbol 'ffi_type_void'
/usr/bin/ld: note: 'ffi_type_void' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.5.2/../../../../lib/libffi.so so try adding it to the linker command line
/usr/lib/gcc/i686-linux-gnu/4.5.2/../../../../lib/libffi.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [g-ir-compiler] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/28]
```

Any ideas?

---

### Post by amrlima on 2010-11-16
> **moore.bryan said:**
> Still dies at gnome-settings-daemon [26/28] make with
```

CCLD   test-media-keys
/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/bryan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [26/28]

```
Any ideas, folks?

When I skip this step and continue to build, gnome-shell [27/28] dies during make, so I guess this is kind of important.

I'm having this same error, how did you managed to fix it?

Thanks!

---

### Post by Merk42 on 2010-11-16
> **amrlima said:**
> I'm having this same error, how did you managed to fix it?

Thanks!Did you try the tip in the [first post of this thread](http://ubuntuforums.org/showpost.php?p=10015153&postcount=1) or [here](http://code.google.com/webfonts?subset=latin)?

---

### Post by amrlima on 2010-11-16
> **Merk42 said:**
> Did you try the tip in the [first post of this thread](http://ubuntuforums.org/showpost.php?p=10015153&postcount=1) or [here](http://code.google.com/webfonts?subset=latin)?

I saw the issue with la files after my post. I'm build GS again now. Thanks!

---

### Post by moore.bryan on 2010-11-16
Sorry I'm late to the party... sometimes the *.la fix works, sometimes deleting the whole gnome-shell dir works, sometimes you need to stand on one leg while hopping and singing *Amazing Grace* during a full moon...

---

### Post by sgage on 2010-11-16
Well, I still can't compile the darn thing, but I'm running the latest ricotz version, and it's quite nice. Smooth and elegant, really quite snappy and usable. I am beginning to find myself a bit sorry that Ubuntu is ditching GS for Unity. It seems a sad dilution of effort. 

Oh well.

---

### Post by cmccauley on 2010-11-17
```
fatal: git-write-tree: error building trees
Cannot save the current index state
*** Error during phase checkout of gdk-pixbuf: ########## Error running git stash save jhbuild-stash *** [7/29]

  [1] Rerun phase checkout
  [2] Ignore error and continue to configure
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
```


Anyone seen this? I did a jhbuild -f -a -c just before

---

### Post by sgage on 2010-11-17
Well, another day, another attempt at compiling GS. At least I got past gobject-introspection this time:

```
dconf-1.0.c:(.text+0xe2f): undefined reference to `g_threads_got_initialized'
dconf-1.0.c:(.text+0xe3f): undefined reference to `g_thread_init'
dconf-1.0.c:(.text+0xe44): undefined reference to `g_type_init'
dconf-1.0.c:(.text+0xe62): undefined reference to `g_str_has_prefix'
dconf-1.0.c:(.text+0xe7b): undefined reference to `g_printerr'
dconf-1.0.c:(.text+0xec9): undefined reference to `g_printerr'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['gcc', '-o', '/home/sgage/gnome-shell/source/dconf/client/tmp-introspectExiPnP/dconf-1.0', '-L.', '-Wl,-rpath=.', '-ldconf', '-pthread', '-L/home/sgage/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/sgage/gnome-shell/source/dconf/client/tmp-introspectExiPnP/dconf-1.0.o']' returned non-zero exit status 1
make[1]: *** [dconf-1.0.gir] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/dconf/client'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/33]
```

There were many more undefined reference errors, but you get the picture.

What next?

---

### Post by Anduu on 2010-11-17
> **cmccauley said:**
> ```
fatal: git-write-tree: error building trees
Cannot save the current index state
*** Error during phase checkout of gdk-pixbuf: ########## Error running git stash save jhbuild-stash *** [7/29]

  [1] Rerun phase checkout
  [2] Ignore error and continue to configure
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
```


Anyone seen this? I did a jhbuild -f -a -c just before

Seriously,this all seems so random to me...Mine barfs at the dconf stage.

I have only managed to successfully build Gnome Shell ***once*** in the last 5 days.I am almost at the point where I am just going to say to hell with it and go with ricotz ppa.

---

### Post by celticbhoy on 2010-11-17
OK, I've had Gnome Shell running for a while but never updated, so I recompiled and got the .la file thing, removed them wiped & started over and the build finished. But when I try and run it I get this

```
office@office-laptop:~$ ~/gnome-shell/source/gnome-shell/src/gnome-shell --replace

GLib-GIO-ERROR **: Settings schema 'org.gnome.settings-daemon.plugins.xsettings' is not installed

aborting...
Shell killed with signal 5
office@office-laptop:~$ 

```


Any ideas how to fix?

---

### Post by bash on 2010-11-17
> **cmccauley said:**
> ```
fatal: git-write-tree: error building trees
Cannot save the current index state
*** Error during phase checkout of gdk-pixbuf: ########## Error running git stash save jhbuild-stash *** [7/29]

  [1] Rerun phase checkout
  [2] Ignore error and continue to configure
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
```


Anyone seen this? I did a jhbuild -f -a -c just before

Had this earlier as well. Using option [6] did the trick for me.

---

### Post by echelon89 on 2010-11-17
I've just installed the newest AMD Catalyst 10.11 on my ubuntu 10.10_x64, and the interface is still very laggy.
Also the decorator isn't working very well.

I wonder when GS will be usable for my ATI card :D (ATI HD5770 Vapor-X)

---

### Post by seeker5528 on 2010-11-18
Looks like the bugs have been filed to get things going on merging the overview-relayout branch into master.

[http://blogs.gnome.org/fmuellner/2010/11/16/moving-forward/](http://blogs.gnome.org/fmuellner/2010/11/16/moving-forward/)

Later, Seeker

---

### Post by maxfact on 2010-11-19
> **xtoudi said:**
> Latest commit:
**	Skip drawing transparent borders and backgrounds** ([http://git.gnome.org/browse/gnome-shell/commit/?id=3138b20b11d67eb05fdda1926b7b0550dc2724d8](http://git.gnome.org/browse/gnome-shell/commit/?id=3138b20b11d67eb05fdda1926b7b0550dc2724d8))
this improves speed of GS a lot!! At least for me (Intel HD graphics).

Then you can merge master branch with overview-relayout to get speed and new UI.
```
cd ~/gnome-shell/source/gnome-shell
git merge overview-relayout
jhbuild buildone gnome-shell
```

And we've got latest master commits with overview-relayout branch.

Hi,
How do I only upgrade the branch overview-relayout if you can always
Or should you take a normal build and then repeat the steps that you indicated in this post:
[http://art.ubuntuforums.org/showpost.php?p=9944930&postcount=813](http://art.ubuntuforums.org/showpost.php?p=9944930&postcount=813)

---

### Post by xtoudi on 2010-11-19
> **maxfact said:**
> Hi,
How do I only upgrade the branch overview-relayout if you can always
Or should you take a normal build and then repeat the steps that you indicated in this post:
[http://art.ubuntuforums.org/showpost.php?p=9944930&postcount=813](http://art.ubuntuforums.org/showpost.php?p=9944930&postcount=813)
If you want to change master to overview-relayout definitely you can try add 
```
branches['gnome-shell'] = (None, 'overview-relayout')
```
to you ~/.jhbuildrc file. After this you should always compile overview-relayout branch.

But right now overview-relayout is merged with master changes so if you want to taste this you can:
```
rm ~/gnome-shell/source/gnome-shell -rf
cd ~/gnome-shell/source/
git clone git://git.gnome.org/gnome-shell -b overview-relayout
jhbuild buildone -n gnome-shell -f
```

And if you want at the future upgrade only overview-relayout branch you need to change to this branch before pulling ... get the git manual.

I suggest wait a while ... overview-relayout will be merged into master soon.

Before doing this you should compile a whole GNOME-SHELL modules - **all 33 modules** !!!

---

### Post by sgage on 2010-11-19
Another day, another compile attempt. Another compile attempt, another fail on dconf. Does anyone have any insight into what's going on here? I'd love to check this thing out:

```
dconf-1.0.c:(.text+0xe2f): undefined reference to `g_threads_got_initialized'
dconf-1.0.c:(.text+0xe3f): undefined reference to `g_thread_init'
dconf-1.0.c:(.text+0xe44): undefined reference to `g_type_init'
dconf-1.0.c:(.text+0xe62): undefined reference to `g_str_has_prefix'
dconf-1.0.c:(.text+0xe7b): undefined reference to `g_printerr'
dconf-1.0.c:(.text+0xec9): undefined reference to `g_printerr'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['gcc', '-o', '/home/sgage/gnome-shell/source/dconf/client/tmp-introspectVjNorz/dconf-1.0', '-L.', '-Wl,-rpath=.', '-ldconf', '-pthread', '-L/home/sgage/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/sgage/gnome-shell/source/dconf/client/tmp-introspectVjNorz/dconf-1.0.o']' returned non-zero exit status 1
make[1]: *** [dconf-1.0.gir] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/dconf/client'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/33]
```

---

### Post by bdgdl08 on 2010-11-19
I apologize if I missed this somewhere in the thread, but I have been trying to get through it and haven't see this (nor did it come up in searching).

When I run the first command I get:


```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python-dev : Depends: python2.6-dev (>= 2.6.6-1~) but it is not going to be installed
E: Broken packages
```


If I try to install (sudo apt-get install  python2.6-dev) I get the same message about libssl-dev. If I try to install THAT, I get


```
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl0.9.8 (= 0.9.8o-1ubuntu4.1) but 0.9.8o-1ubuntu4.2 is to be installed
E: Broken packages
```


Please help.

---

### Post by Anduu on 2010-11-19
> **sgage said:**
> Another day, another compile attempt. Another compile attempt, another fail on dconf. Does anyone have any insight into what's going on here? I'd love to check this thing out:

```
dconf-1.0.c:(.text+0xe2f): undefined reference to `g_threads_got_initialized'
dconf-1.0.c:(.text+0xe3f): undefined reference to `g_thread_init'
dconf-1.0.c:(.text+0xe44): undefined reference to `g_type_init'
dconf-1.0.c:(.text+0xe62): undefined reference to `g_str_has_prefix'
dconf-1.0.c:(.text+0xe7b): undefined reference to `g_printerr'
dconf-1.0.c:(.text+0xec9): undefined reference to `g_printerr'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['gcc', '-o', '/home/sgage/gnome-shell/source/dconf/client/tmp-introspectVjNorz/dconf-1.0', '-L.', '-Wl,-rpath=.', '-ldconf', '-pthread', '-L/home/sgage/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/sgage/gnome-shell/source/dconf/client/tmp-introspectVjNorz/dconf-1.0.o']' returned non-zero exit status 1
make[1]: *** [dconf-1.0.gir] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/dconf/client'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/33]
```

I have been stuck in this boat for a couple of days now...no idea how to fix it.

On another note...if you select "give up on module" everything else builds fine except it barfs at the final stage and cannot build gnome-shell etc.

Also it seems some new dependencies are needed...libtasn1-3-dev and libupower-glib-dev IIRC

---

### Post by xtoudi on 2010-11-19
@sgage

```
cd ~/gnome-shell/source
rm -rf dconf
jhbuild buildone dconf -f

```
and here paste a litlle bit more logs...

---

### Post by cariboo on 2010-11-19
> **bdgdl08 said:**
> I apologize if I missed this somewhere in the thread, but I have been trying to get through it and haven't see this (nor did it come up in searching).

When I run the first command I get:


```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python-dev : Depends: python2.6-dev (>= 2.6.6-1~) but it is not going to be installed
E: Broken packages
```


If I try to install (sudo apt-get install  python2.6-dev) I get the same message about libssl-dev. If I try to install THAT, I get


```
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl0.9.8 (= 0.9.8o-1ubuntu4.1) but 0.9.8o-1ubuntu4.2 is to be installed
E: Broken packages
```


Please help.

You have to fix your broken packages before you can do anything. Open up synaptic and go to Edit->Fix Broken Packages, and fix the problem.

---

### Post by xtoudi on 2010-11-19
About deps ... there are a lot of new packages required to compile all 33 stages. A few of them already added to gnome-shell-build-setup.sh but a lot of them not. I should notice all of these ... stupid ...
There are a few changes too. New power tray icon and some power-manager stuff.
New smooth shadows around windows (mutter) - lookin' very very nice !!
And ... gnome-control-center ... all Gnome3!! But small piece of this is working right now :-)
Seems to GS is starting to link all modules of Gnome3.

---

### Post by Anduu on 2010-11-19
> **xtoudi said:**
> @sgage

```
cd ~/gnome-shell/source
rm -rf dconf
jhbuild buildone dconf -f

```
and here paste a litlle bit more logs...

Here is the entire stage with regards to the dconf failure
```

gstesting@StormChaser:~/gnome-shell/source$ jhbuild buildone dconf -f
*** Checking out dconf *** [1/1]
git clone git://git.gnome.org/dconf
Cloning into dconf...
remote: Counting objects: 1787, done.
remote: Compressing objects: 100% (1438/1438), done.
remote: Total 1787 (delta 1153), reused 460 (delta 307)
Receiving objects: 100% (1787/1787), 353.08 KiB | 256 KiB/s, done.
Resolving deltas: 100% (1153/1153), done.
git pull --rebase
Current branch master is up to date.
*** Configuring dconf *** [1/1]
./autogen.sh --prefix /home/gstesting/gnome-shell/install --libdir '/home/gstesting/gnome-shell/install/lib64' --disable-editor --disable-static --disable-gtk-doc 
automake (GNU automake) 1.11.1
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv2+: GNU GPL version 2 or later <http://gnu.org/licenses/gpl-2.0.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Tom Tromey <tromey@redhat.com>
       and Alexandre Duret-Lutz <adl@gnu.org>.
configure.ac:1: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=dconf
configure.ac:1: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=dconf
configure.ac:10: installing `aux/install-sh'
configure.ac:10: installing `aux/missing'
bin/Makefile.am: installing `aux/depcomp'
configure.ac:1: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=dconf
configure: WARNING: unrecognized options: --disable-static
checking for a BSD-compatible install... /usr/bin/install-check
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for valac... /home/gstesting/gnome-shell/install/bin/valac
checking /home/gstesting/gnome-shell/install/bin/valac is at least version 0.9.5... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gobject-introspection... yes
checking for gtkdoc-check... /usr/bin/gtkdoc-check
checking for gtkdoc-rebase... /usr/bin/gtkdoc-rebase
checking for gtkdoc-mkpdf... /usr/bin/gtkdoc-mkpdf
checking whether to build gtk-doc documentation... no
checking for gio... yes
checking which gtk+ version to compile against... 2.0
checking for gio-querymodules... /home/gstesting/gnome-shell/install/bin/gio-querymodules
configure: creating ./config.status
config.status: creating common/Makefile
config.status: creating gvdb/Makefile
config.status: creating engine/Makefile
config.status: creating gsettings/Makefile
config.status: creating client/dconf.pc
config.status: creating client/Makefile
config.status: creating service/Makefile
config.status: creating bin/Makefile
config.status: creating editor/Makefile
config.status: creating tests/Makefile
config.status: creating docs/Makefile
config.status: creating Makefile
config.status: executing depfiles commands
configure: WARNING: unrecognized options: --disable-static
*** Building dconf *** [1/1]
make  
Making all in gvdb
make[1]: Entering directory `/home/gstesting/gnome-shell/source/dconf/gvdb'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/gstesting/gnome-shell/source/dconf/gvdb'
Making all in service
make[1]: Entering directory `/home/gstesting/gnome-shell/source/dconf/service'
  CC     gvdb-builder.o
  CC     gvdb-reader.o
  CC     dconf-shmdir.o
  CC     dconf-interfaces.o
  CC     dconf-rebuilder.o
  CC     dconf-writer.o
  CC     dconf-state.o
  CC     service.o
  CCLD   dconf-service
  GEN    ca.desrt.dconf.service
make[1]: Leaving directory `/home/gstesting/gnome-shell/source/dconf/service'
Making all in gsettings
make[1]: Entering directory `/home/gstesting/gnome-shell/source/dconf/gsettings'
  CC     dconf-engine.o
  CC     dconf-shmdir.o
  CC     gvdb-reader.o
  CC     dconfsettingsbackend.o
  CCLD   libdconfsettings.so
make[1]: Leaving directory `/home/gstesting/gnome-shell/source/dconf/gsettings'
Making all in tests
make[1]: Entering directory `/home/gstesting/gnome-shell/source/dconf/tests'
  CC     dconf-paths.o
  CC     paths.o
  CCLD   paths
make[1]: Leaving directory `/home/gstesting/gnome-shell/source/dconf/tests'
Making all in client
make[1]: Entering directory `/home/gstesting/gnome-shell/source/dconf/client'
  CC     dconf-shmdir.o
  CC     dconf-paths.o
  CC     dconf-engine.o
  CC     gvdb-reader.o
  VALAC  libdconf_so_0_0_0_vala.stamp
  CC     dconf-client.o
  CCLD   libdconf.so.0.0.0
  GEN    libdconf.so.0
  GEN    libdconf.so
  GISCAN dconf-1.0.gir
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `g_string_append_c_inline':
dconf-1.0.c:(.text+0x7a): undefined reference to `g_string_insert_c'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `escaped_printf':
dconf-1.0.c:(.text+0x14e): undefined reference to `g_markup_vprintf_escaped'
dconf-1.0.c:(.text+0x194): undefined reference to `g_output_stream_write_all'
dconf-1.0.c:(.text+0x1bf): undefined reference to `g_log'
dconf-1.0.c:(.text+0x1ce): undefined reference to `g_clear_error'
dconf-1.0.c:(.text+0x1dd): undefined reference to `g_free'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `goutput_write':
dconf-1.0.c:(.text+0x227): undefined reference to `g_output_stream_write_all'
dconf-1.0.c:(.text+0x24f): undefined reference to `g_log'
dconf-1.0.c:(.text+0x25b): undefined reference to `g_clear_error'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `invoke_get_type':
dconf-1.0.c:(.text+0x288): undefined reference to `g_module_symbol'
dconf-1.0.c:(.text+0x291): undefined reference to `g_io_error_quark'
dconf-1.0.c:(.text+0x2b5): undefined reference to `g_set_error'
dconf-1.0.c:(.text+0x2d2): undefined reference to `g_io_error_quark'
dconf-1.0.c:(.text+0x2f6): undefined reference to `g_set_error'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `dump_properties':
dconf-1.0.c:(.text+0x319): undefined reference to `g_type_fundamental'
dconf-1.0.c:(.text+0x32b): undefined reference to `g_type_class_ref'
dconf-1.0.c:(.text+0x342): undefined reference to `g_object_class_list_properties'
dconf-1.0.c:(.text+0x354): undefined reference to `g_type_default_interface_ref'
dconf-1.0.c:(.text+0x36b): undefined reference to `g_object_interface_list_properties'
dconf-1.0.c:(.text+0x3af): undefined reference to `g_type_name'
dconf-1.0.c:(.text+0x3ee): undefined reference to `g_free'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `dump_signals':
dconf-1.0.c:(.text+0x418): undefined reference to `g_signal_list_ids'
dconf-1.0.c:(.text+0x449): undefined reference to `g_signal_query'
dconf-1.0.c:(.text+0x455): undefined reference to `g_type_name'
dconf-1.0.c:(.text+0x494): undefined reference to `g_type_name'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `dump_object_type':
dconf-1.0.c:(.text+0x4fc): undefined reference to `g_type_name'
dconf-1.0.c:(.text+0x537): undefined reference to `g_type_parent'
dconf-1.0.c:(.text+0x545): undefined reference to `g_string_new'
dconf-1.0.c:(.text+0x577): undefined reference to `g_type_name'
dconf-1.0.c:(.text+0x589): undefined reference to `g_string_append'
dconf-1.0.c:(.text+0x595): undefined reference to `g_type_parent'
dconf-1.0.c:(.text+0x5d5): undefined reference to `g_string_free'
dconf-1.0.c:(.text+0x5e6): undefined reference to `g_type_test_flags'
dconf-1.0.c:(.text+0x624): undefined reference to `g_type_interfaces'
dconf-1.0.c:(.text+0x64f): undefined reference to `g_type_name'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `dump_interface_type':
dconf-1.0.c:(.text+0x6cd): undefined reference to `g_type_name'
dconf-1.0.c:(.text+0x6fd): undefined reference to `g_type_interface_prerequisites'
dconf-1.0.c:(.text+0x72f): undefined reference to `g_type_name'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `dump_boxed_type':
dconf-1.0.c:(.text+0x7b0): undefined reference to `g_type_name'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `dump_flags_type':
dconf-1.0.c:(.text+0x7ef): undefined reference to `g_type_class_ref'
dconf-1.0.c:(.text+0x7ff): undefined reference to `g_type_name'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `dump_enum_type':
dconf-1.0.c:(.text+0x8b7): undefined reference to `g_type_class_ref'
dconf-1.0.c:(.text+0x8c7): undefined reference to `g_type_name'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `dump_fundamental_type':
dconf-1.0.c:(.text+0x986): undefined reference to `g_type_name'
dconf-1.0.c:(.text+0x9b4): undefined reference to `g_type_test_flags'
dconf-1.0.c:(.text+0x9df): undefined reference to `g_type_test_flags'
dconf-1.0.c:(.text+0xa05): undefined reference to `g_type_parent'
dconf-1.0.c:(.text+0xa13): undefined reference to `g_string_new'
dconf-1.0.c:(.text+0xa45): undefined reference to `g_type_name'
dconf-1.0.c:(.text+0xa56): undefined reference to `g_type_name'
dconf-1.0.c:(.text+0xa68): undefined reference to `g_string_append'
dconf-1.0.c:(.text+0xa74): undefined reference to `g_type_parent'
dconf-1.0.c:(.text+0xabd): undefined reference to `g_string_free'
dconf-1.0.c:(.text+0xae1): undefined reference to `g_type_interfaces'
dconf-1.0.c:(.text+0xb0c): undefined reference to `g_type_name'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `dump_type':
dconf-1.0.c:(.text+0xb64): undefined reference to `g_type_fundamental'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `g_irepository_dump':
dconf-1.0.c:(.text+0xc65): undefined reference to `g_module_open'
dconf-1.0.c:(.text+0xc75): undefined reference to `g_module_error'
dconf-1.0.c:(.text+0xc7d): undefined reference to `g_io_error_quark'
dconf-1.0.c:(.text+0xca0): undefined reference to `g_set_error'
dconf-1.0.c:(.text+0xcc3): undefined reference to `g_strsplit'
dconf-1.0.c:(.text+0xcd6): undefined reference to `g_file_new_for_path'
dconf-1.0.c:(.text+0xced): undefined reference to `g_file_new_for_path'
dconf-1.0.c:(.text+0xd09): undefined reference to `g_file_read'
dconf-1.0.c:(.text+0xd49): undefined reference to `g_file_replace'
dconf-1.0.c:(.text+0xd59): undefined reference to `g_input_stream_get_type'
dconf-1.0.c:(.text+0xd6b): undefined reference to `g_type_check_instance_cast'
dconf-1.0.c:(.text+0xd7d): undefined reference to `g_input_stream_close'
dconf-1.0.c:(.text+0xd8c): undefined reference to `g_output_stream_get_type'
dconf-1.0.c:(.text+0xd9e): undefined reference to `g_type_check_instance_cast'
dconf-1.0.c:(.text+0xdb0): undefined reference to `g_output_stream_get_type'
dconf-1.0.c:(.text+0xdc2): undefined reference to `g_type_check_instance_cast'
dconf-1.0.c:(.text+0xdde): undefined reference to `g_hash_table_new'
dconf-1.0.c:(.text+0xde7): undefined reference to `g_input_stream_get_type'
dconf-1.0.c:(.text+0xdf9): undefined reference to `g_type_check_instance_cast'
dconf-1.0.c:(.text+0xe01): undefined reference to `g_data_input_stream_new'
dconf-1.0.c:(.text+0xe11): undefined reference to `g_object_unref'
dconf-1.0.c:(.text+0xe2b): undefined reference to `g_data_input_stream_read_line'
dconf-1.0.c:(.text+0xe4d): undefined reference to `g_free'
dconf-1.0.c:(.text+0xe5e): undefined reference to `g_strchomp'
dconf-1.0.c:(.text+0xe96): undefined reference to `g_free'
dconf-1.0.c:(.text+0xeab): undefined reference to `g_hash_table_lookup'
dconf-1.0.c:(.text+0xec7): undefined reference to `g_hash_table_insert'
dconf-1.0.c:(.text+0xecc): undefined reference to `g_output_stream_get_type'
dconf-1.0.c:(.text+0xede): undefined reference to `g_type_check_instance_cast'
dconf-1.0.c:(.text+0xf03): undefined reference to `g_free'
dconf-1.0.c:(.text+0xf14): undefined reference to `g_hash_table_destroy'
dconf-1.0.c:(.text+0xf19): undefined reference to `g_output_stream_get_type'
dconf-1.0.c:(.text+0xf2b): undefined reference to `g_type_check_instance_cast'
dconf-1.0.c:(.text+0xf58): undefined reference to `g_input_stream_get_type'
dconf-1.0.c:(.text+0xf6a): undefined reference to `g_type_check_instance_cast'
dconf-1.0.c:(.text+0xf7b): undefined reference to `g_input_stream_close'
dconf-1.0.c:(.text+0xf8b): undefined reference to `g_output_stream_get_type'
dconf-1.0.c:(.text+0xf9d): undefined reference to `g_type_check_instance_cast'
dconf-1.0.c:(.text+0xfae): undefined reference to `g_output_stream_close'
/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o: In function `main':
dconf-1.0.c:(.text+0xff3): undefined reference to `g_threads_got_initialized'
dconf-1.0.c:(.text+0x1001): undefined reference to `g_thread_init'
dconf-1.0.c:(.text+0x1006): undefined reference to `g_type_init'
dconf-1.0.c:(.text+0x1026): undefined reference to `g_str_has_prefix'
dconf-1.0.c:(.text+0x1043): undefined reference to `g_printerr'
dconf-1.0.c:(.text+0x1095): undefined reference to `g_printerr'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['gcc', '-o', '/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0', '-L.', '-Wl,-rpath=.', '-ldconf', '-pthread', '-L/home/gstesting/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/gstesting/gnome-shell/source/dconf/client/tmp-introspectdi8DyO/dconf-1.0.o']' returned non-zero exit status 1
make[1]: *** [dconf-1.0.gir] Error 1
make[1]: Leaving directory `/home/gstesting/gnome-shell/source/dconf/client'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [1/1]

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

### Post by xtoudi on 2010-11-19
Do a whole procedure again step by step:

1. Get required libs (first post)
2.
```
cd ~
rm -rf ~/gnome-shell
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh

(here you should be prompted about installing new libs)

jhbuild build

```


EDIT:
I shouldn't ask ... can you do:
```
sudo apt-get install jhbuild
```

Somteimes, after installing new system we've got jhbuild on /home/user (other partition) but there is no jhbuild on system .. and this can do a mess??

---

### Post by sgage on 2010-11-19
> **xtoudi said:**
> Do a whole procedure again step by step:

1. Get required libs (first post)
2.
```
cd ~
rm -rf ~/gnome-shell
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh

(here you should be prompted about installing new libs)

jhbuild build

```

EDIT:
I shouldn't ask ... can you do:
```
sudo apt-get install jhbuild
```

Somteimes, after installing new system we've got jhbuild on /home/user (other partition) but there is no jhbuild on system .. and this can do a mess??

I've been doing it from the ground up every day for the past several days. I've been getting the latest gnome-shell-build-setup every day before attempting a compile, and have jhbuild installed. I make sure to delete *.la in the appropriate places, delete ~/gnome-shell and ~/Source, run the new gnome-shell-build-setup, and to the build. It always quits at dconf.

I have built GS successfully many, many times in the past, but lately I just can't get past dconf. I'm baffled.

---

### Post by xtoudi on 2010-11-19
lets remove old dconf config.
```
cd
mv .config/dconf .config/dconf-backup
```
and again
```
jhbuild buildone dconf -f
```

---

### Post by sgage on 2010-11-19
> **xtoudi said:**
> lets remove old dconf config.
```
cd
mv .config/dconf .config/dconf-backup
```
and again
```
jhbuild buildone dconf -f
```

Alas, same error on dconf :KS

---

### Post by moore.bryan on 2010-11-19
Thought I'd try the relayout branch and see the improvements, now GNOME Shell won't build...
```

cc1: warnings being treated as errors
shell-global.c: In function ‘shell_global_get_property’:
shell-global.c:164: error: implicit declaration of function ‘meta_plugin_get_background_actor’
shell-global.c:164: error: passing argument 2 of ‘g_value_set_object’ makes pointer from integer without a cast
/home/bryan/gnome-shell/install/include/glib-2.0/gobject/gobject.h:512: note: expected ‘gpointer’ but argument is of type ‘int’
make[3]: *** [libgnome_shell_la-shell-global.lo] Error 1
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-shell'
make: *** [all] Error 2

```
Help?

---

### Post by Anduu on 2010-11-19
> **sgage said:**
> Alas, same error on dconf :KS

No change on my end either.

---

### Post by xtoudi on 2010-11-20
> **Anduu said:**
> No change on my end either.

No idea what's wrong with your dconf ....
Do you have GS from ppa?? Ricotz PPA?? No idea what else you should check/uninstall/set ...

---

### Post by sgage on 2010-11-20
> **xtoudi said:**
> No idea what's wrong with your dconf ....
Do you have GS from ppa?? Ricotz PPA?? No idea what else you should check/uninstall/set ...

No, no GS installed, either from standard repo or ppa. I give up.

---

### Post by davideotape on 2010-11-20
Please could the original poster add 'libxklavier-dev' to the list of required packages :)

---

### Post by Anduu on 2010-11-20
I am giving it another go....My install is by no means standard(...I have been upgrading since at least Lucid IIRC...) and has several third party ppas in use.I went on a hunt for questionable package versioning and changed a few back to the default Natty versions,however none suggested a dconf issue,but we will see.

The OP definitely needs to revise the instructions.

New dependencies need to be added to the list.

Also the command for removing *.la files should more closely match what is here [http://live.gnome.org/GnomeShell/RemovingLaFiles](http://live.gnome.org/GnomeShell/RemovingLaFiles) 
In it's present form the command will not remove write protected system files nor .la files that may be in the lib32/lib64 directories.

I would suggest something like:

```
rm ~/gnome-shell/install/*.la && sudo rm -rf /usr/lib*/*.la
```

Anyways...as I write this my compile is at stage 14 "gconf" and no errors yet.We will see what happens when it gets do dconf again.

*crosses fingers*

---

### Post by ronacc on 2010-11-20
getting the same dconf error here with a build from absolute scratch , hand deleted everything having to do with GS and jhbuild and started over .

---

### Post by Anduu on 2010-11-20
No changes here...

I have pretty much spent all day with this.

I cannot,for the life of me,find anything wrong on my end.I have successfully cleaned my system of any ppas and reverted any packages which could even remotely effect things.

Something I have noticed:

The gnome-shell version in ricotz/testing ppa is 9 days old while gnome-shell in ricotz/staging [https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging) has failed to build recently(...the last few days IIRC...).Coincidence?

Another thing is that I get the exact same error building dconf regardless of whether I have any dconf libs installed or not.I can't find any configure errors either way.Does gnome-shell even use these or is it compiling it's own version and this is where it is failing?

I dunno...something tells me something is broken on their end.

Does anyone know of a more official place to discuss this or file a bug perhaps?

O.K. so I am rambling...I am far from an expert on all this however I am trying hard to learn to fix the more complex stuff.

---

### Post by dext on 2010-11-20
> **Anduu said:**
> No changes here...

I have pretty much spent all day with this.

I cannot,for the life of me,find anything wrong on my end.I have successfully cleaned my system of any ppas and reverted any packages which could even remotely effect things.

Something I have noticed:

The gnome-shell version in ricotz/testing ppa is 9 days old while gnome-shell in ricotz/staging [https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging) has failed to build recently(...the last few days IIRC...).Coincidence?

Another thing is that I get the exact same error building dconf regardless of whether I have any dconf libs installed or not.I can't find any configure errors either way.Does gnome-shell even use these or is it compiling it's own version and this is where it is failing?

I dunno...something tells me something is broken on their end.

Does anyone know of a more official place to discuss this or file a bug perhaps?

O.K. so I am rambling...I am far from an expert on all this however I am trying hard to learn to fix the more complex stuff.

yeah, try here [http://mail.gnome.org/mailman/listinfo/gnome-shell-list](http://mail.gnome.org/mailman/listinfo/gnome-shell-list)

---

### Post by Harry33 on 2010-11-21
> **Anduu said:**
> 
Something I have noticed:

The gnome-shell version in ricotz/testing ppa is 9 days old while gnome-shell in ricotz/staging [https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging) has failed to build recently(...the last few days IIRC...).Coincidence?


Well I think this is not coincidence. The problem seems to be quite common, suggesting a broken source at the moment.
The last successful build in ricotz PPA is git20101108.
That is almost two weeks old.
Rico is trying to build gnome-shell package more or less daily.
The other packages build fine (mutter, gjs, gnome-themes-standard, gnome-desktop3).

Would be interesting to see Rico comment on this.

---

### Post by bdgdl08 on 2010-11-22
> **cariboo907 said:**
> You have to fix your broken packages before you can do anything. Open up synaptic and go to Edit->Fix Broken Packages, and fix the problem.

I have done this, but it doesn't work. I have tried to manually install the dependencies, but that's a no-go as well. I get down to libssl0.9.8 and it tells me it's at the most current version. When I go to get libssl-dev it tells me I need libssl0.9.8 and that it will install it. I'm so confused!!!

---

### Post by Anduu on 2010-11-22
Ok Ok Ok Ok....grrr.

I think I have this figured out.

The command ```
sudo rm -rf /usr/lib*/*.la
``` which I got from here [http://live.gnome.org/GnomeShell/RemovingLaFiles](http://live.gnome.org/GnomeShell/RemovingLaFiles) for deleting .la files is just plain wrong.[COLOR="black"]**[COLOR="Red"]IT DOES NOT WORK!!!!![/COLOR]**[/COLOR] I just assumed the guys at Gnome knew what they were doing lol

Out of curiousity I did a search in Nautilus for .la files and guess what?I had like 400+ of them even after running sudo rm -rf /usr/lib*/*.la

I manually deleted them through Nautilus and am compiling as I write this.I pray this is the answer.

Now do not quote me on this but through some tinkering I believe the command should read ```
sudo rm  /usr/lib*/*.la
```
I think what is happening with the other command is that by employing wildcards AND the recursive switch rm messes up.
Maybe someone more knowledgable than me can clarify this?

I am sorry Merk42 I noticed you just updated the how-to :oops:

EDIT:

Damn....still barfs at dconf.

Welp...I'm out of ideas ](*,)

---

### Post by bash on 2010-11-23
> **Anduu said:**
> I would suggest something like:

```
rm ~/gnome-shell/install/*.la
```

You forgot the lib folder. Which also is different depending on if you have a 32 or 64 bit system. To be on the safe side:

```
rm ~/gnome-shell/install/lib/*.la && rm ~/gnome-shell/install/lib64/*.la
```

Also I just yesterday build all 33 steps, including both the normal and the overlay-redesign Shell branches, successfully. So it seems possible to build it. When something farks up, try option [6]. Sometimes it helps solve the problem, as git --rebases don't always seem to work flawlessly.

---

### Post by moore.bryan on 2010-11-23
@Anduu
The GNOME Shell build [page]("http://live.gnome.org/GnomeShell#Building") now tells us about the .la issue. The [page]("http://live.gnome.org/GnomeShell/RemovingLaFiles") it points to for more information talks about hard/soft linking in files and explains apt will put more .la files on your system. It suggests using the following code to keep those pesky .la files off your computer:
```

sudo tee /etc/apt/apt.conf.d/90removela <<< 'DPkg { Post-Invoke { "rm /usr/lib*/*.la 2> /dev/null || true"; }; };'

```

---

### Post by omega52390 on 2010-11-23
im having a new build error
```
/home/omega52390/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/omega52390/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/omega52390/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_list_free_full'
/home/omega52390/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_get_environ'
/home/omega52390/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/omega52390/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/omega52390/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/omega52390/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/omega52390/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/omega52390/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/omega52390/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/32]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"

```
first time trying to build from source i dont have much confidence in my cli skills also i had been running ricotz for a long time but since he stopped supporting 10.10 i figured I'd try this any tips i dont want to start over if i dont have to

update i did more reading on this thread tried doing the .la removal command (many of the different iterations) and i always get this error

```
omega52390@omega52390-laptop:~$ rm ~/gnome-shell/install/lib/*.la && rm ~/gnome-shell/install/lib64/*.la
rm: cannot remove `/home/omega52390/gnome-shell/install/lib/*.la': No such file or directory

```

---

### Post by bash on 2010-11-23
> **omega52390 said:**
> update i did more reading on this thread tried doing the .la removal command (many of the different iterations) and i always get this error

```
omega52390@omega52390-laptop:~$ rm ~/gnome-shell/install/lib/*.la && rm ~/gnome-shell/install/lib64/*.la
rm: cannot remove `/home/omega52390/gnome-shell/install/lib/*.la': No such file or directory

```

Then your probably have a 64 bit system. Try just using the second part:

```
rm ~/gnome-shell/install/lib64/*.la
```

---

### Post by omega52390 on 2010-11-23
@bash alright ill try that tried the combo one once didnt work however im having to rebuild step 8 due to some of the other things i tried so it may be a while

also after one thing cant remember what, I got a different error (still on 27 =P) but it seemed like i was moving foward if only slightly because it only had 3 makes fail instead of 5 dont know though i could have moved a step backward

---

### Post by moore.bryan on 2010-11-23
Two things:
[list]
[*]Is everyone running the overview-relayout branch seeing *really* slow response times to search?
[*]The new gnome-control-center GNOME Shell installs doesn't seem to obey the rules I set about not dimming the LCD when on battery.
[/list]
Any ideas? Thanks...

---

### Post by omega52390 on 2010-11-23
well i am now moving forward after deleting the gnome-shell folder i reran jhbuild and got all the way to 29/32 so i made it two steps closer however i have run into a new problem and its one that i can understand happening because it seems like its related to another issued on my system that i have been ignoring

```
checking for UPOWER... no
configure: error: Package requirements (upower-glib >= 0.9.1) were not met:

No package 'upower-glib' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables UPOWER_CFLAGS
and UPOWER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
*** Error during phase configure of gnome-control-center: ########## Error running ./autogen.sh --prefix /home/omega52390/gnome-shell/install --libdir '/home/omega52390/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [29/32]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"

```
it says upower is missing but when i look it up is shows it in synaptic (at least i think it does)
im going to try a few things but any advice in the mean time would be appreciated

---

### Post by Anduu on 2010-11-23
> **omega52390 said:**
> well i am now moving forward after deleting the gnome-shell folder i reran jhbuild and got all the way to 29/32 so i made it two steps closer however i have run into a new problem and its one that i can understand happening because it seems like its related to another issued on my system that i have been ignoring

```
checking for UPOWER... no
configure: error: Package requirements (upower-glib >= 0.9.1) were not met:

No package 'upower-glib' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables UPOWER_CFLAGS
and UPOWER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
*** Error during phase configure of gnome-control-center: ########## Error running ./autogen.sh --prefix /home/omega52390/gnome-shell/install --libdir '/home/omega52390/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [29/32]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"

```
it says upower is missing but when i look it up is shows it in synaptic (at least i think it does)
im going to try a few things but any advice in the mean time would be appreciated

Install libupower-glib1 and libupower-glib-dev

---

### Post by omega52390 on 2010-11-23
already had upower but installing upower dev fixed it thanks a ton :KS

---

### Post by Anduu on 2010-11-23
> **omega52390 said:**
> already had upower but installing upower dev fixed it thanks a ton :KS

Good stuff....let me know how the build goes?

It will be interesting to see if you get the same dconf error I do.

---

### Post by Merk42 on 2010-11-23
> **Anduu said:**
> Install libupower-glib1 and libupower-glib-devSo I guess those and libgnone-keyring-dev are new dependencies?

---

### Post by Anduu on 2010-11-23
> **Merk42 said:**
> So I guess those and libgnone-keyring-dev are new dependencies?

They are recent yes...since late last week or so when the build jumped to 32 stages.

---

### Post by Anduu on 2010-11-23
[SIZE="3"]**For those with jhbuild failing at the dconf stage:**[/SIZE]

Countless hours of monkeying around have finally paid off...I think :-k

I Googled up this obscure IRC log >>> [http://rotty.yi.org/irclogs/gnome/%23introspection/2010-09-07/#e402](http://rotty.yi.org/irclogs/gnome/%23introspection/2010-09-07/#e402) Check out <Keruspe>'s comments (I linked to the appropriate spot on the page...they should be the first visible...).There is a lot of interesting discussion there but his are the relevent points for us.

What I did was:

**1:** When the build fails select option 4 in the menu.This will drop you to the jhbuild shell.
**2:** Scroll up to and find the ./autogen line for the dconf stage
**3:** Copy/paste this line into the shell and add --disable-introspection at the end.It should look like ```
./autogen.sh --prefix ~/gnome-shell/install --libdir '~/gnome-shell/install/lib64' --disable-editor --disable-static --disable-gtk-doc [COLOR="Red"]--disable-introspection[/COLOR]
```
I am compiling 64bit so adjust your --libdir accordingly.

**4:** Hit enter and let it do it's thing.
**5:** Once it is done type [COLOR="Red"]exit[/COLOR] and hit enter.You will now be back at the menu.
**6:** Select option one and it should compile succesfully and then carry on with the rest of the stages.

One caveat...I have not played around a lot yet with it but gnome shell seems to function properly however I have no idea whether this breaks any functionality or not.

Let me know if this works for you and if it breaks anything.The impression I get from the chat log...although I don't exactly understand all of it...seems to suggest it shouldn't.

---

### Post by bash on 2010-11-24
> **Anduu said:**
> ```
./autogen.sh --prefix /home/gnomeshelltest/gnome-shell/install --libdir '/home/gnomeshelltest/gnome-shell/install/lib64' --disable-editor --disable-static --disable-gtk-doc [COLOR="Red"]--disable-introspection[/COLOR]
```

I assume your username for that install is gnomeshelltest? The command like that will only work for people who also call their install gnomeshelltest. To make it work for everyone change it to:

```
./autogen.sh --prefix [color=red]~[/color]/gnome-shell/install --libdir '[color=red]~[/color]/gnome-shell/install/lib64' --disable-editor --disable-static --disable-gtk-doc [COLOR="Red"]--disable-introspection[/COLOR]
```

---

### Post by Anduu on 2010-11-24
> **bash said:**
> I assume your username for that install is gnomeshelltest? The command like that will only work for people who also call their install gnomeshelltest. To make it work for everyone change it to:

```
./autogen.sh --prefix [color=red]~[/color]/gnome-shell/install --libdir '[color=red]~[/color]/gnome-shell/install/lib64' --disable-editor --disable-static --disable-gtk-doc [COLOR="Red"]--disable-introspection[/COLOR]
```

Whoops yeah...in my haste to post i forgot to note that....fixed.

---

### Post by omega52390 on 2010-11-24
ok now that i have the shell up and running im currently trying out the branch there are some really nice things about it like switching workspaces from overview by click and drag and moving apps to other workspaces by edge hitting but i would like a way to view all the workspaces at once again i miss that a lot

one other thing a bit more important than aesthetics thats bothering me is system settings is broken I it looks like it was made wrong and i cant use it at all is anyone else having problems with trying to use system settings?

oh yeah also my terminal is only transparent when maximized but not when its just a normal window does anyone else have this problem or a fix for it and why the hell did they do this theme thing i want my old theme is there anyway to put on a different one?

---

### Post by Anduu on 2010-11-24
> **omega52390 said:**
> ok now that i have the shell up and running im currently trying out the branch there are some really nice things about it like switching workspaces from overview by click and drag and moving apps to other workspaces by edge hitting but i would like a way to view all the workspaces at once again i miss that a lot

one other thing a bit more important than aesthetics thats bothering me is system settings is broken I it looks like it was made wrong and i cant use it at all is anyone else having problems with trying to use system settings?

oh yeah also my terminal is only transparent when maximized but not when its just a normal window does anyone else have this problem or a fix for it and why the hell did they do this theme thing i want my old theme is there anyway to put on a different one?

Did you compile it with my fix?Possible breakage from using that method?

I only have ricotz version to campare it to.System settings doesn't exist in that version.

My terminal too is solid coloured until maximised.

---

### Post by omega52390 on 2010-11-24
ok let me explain a bit more system settings was also broken when i originally built it as normal gs. before this i was running whatever ricotz stopped at on 10.10 and the control center worked fine.

---

### Post by moore.bryan on 2010-11-24
I don't think the new settings are completely integrated yet.

---

### Post by omega52390 on 2010-11-24
yeah i was just about to say that i realized that it was theme moving away from the gtk2 stuff that they were using as a crutch for the demo version that you get on 10.10. 

moving on i kinda like the branch build but i left it because there was no workspace overview option. but anyway i was wondering if you could use the themes I've seen before on the compiled version i know a lot has changed since those themes were made, also I'm assuming no gtk3 themes yet for use seeing as the themes settings is still the gtk2 one

---

### Post by omega52390 on 2010-11-24
dig some more playing around and went back to relayout branch. i also discovered that the search function on system settings still work even if it looks deprecated i also noticed the way internal application windows on certain program have this slick new way of appearing like on the archive manager the window that pops up to choose the extraction destination watch how it opens.

after all of my testing i have decided that i need a table/pad/slate/etc... you get the idea, NOW!!!! i want to put gnome shell on a tablet so freakin badly especially the relayout branch the way gs operates is by far the most touch friendly desktop interface i have ever seen or used!

one more thing i just remembered, when running the relayout branch do i still use plain jhbuild build to update or do i need some other options?

---

### Post by Anduu on 2010-11-24
Just a quick note:

Avoid the mozilla-daily ppa.It breaks the ability to build gjs by changing to an incompatible version of xulrunner.

---

### Post by moore.bryan on 2010-11-24
Has anyone found/does anyone have a fix to the slow lookup of installed programs in the overview-relayout branch?

---

### Post by xtoudi on 2010-11-25
> **moore.bryan said:**
> Has anyone found/does anyone have a fix to the slow lookup of installed programs in the overview-relayout branch?

You can always ask an author
[http://blogs.gnome.org/fmuellner/2010/11/16/moving-forward/](http://blogs.gnome.org/fmuellner/2010/11/16/moving-forward/)

I can confirm that problem exists.

---

### Post by chrisccoulson on 2010-11-25
> **Anduu said:**
> Just a quick note:

Avoid the mozilla-daily ppa.It breaks the ability to build gjs by changing to an incompatible version of xulrunner.

gjs is compatible with the versions in there. Please be more specific about the problem you're having

---

### Post by Harry33 on 2010-11-25
> **chrisccoulson said:**
> gjs is compatible with the versions in there. Please be more specific about the problem you're having

This was a problem before, but it was fixed during Maverick development cycle.
The package libgjs-dev depends on xulrunner.dev (>=1.9.2), I do not see any problems there.
Still, package gnome-shell depends on xulrunner-1.9.2, so that package must be available.

---

### Post by bash on 2010-11-25
> **Anduu said:**
> Just a quick note:

Avoid the mozilla-daily ppa.It breaks the ability to build gjs by changing to an incompatible version of xulrunner.

I use the moz-daily PPA and can build the Shell without a problem. So I can't confirm that problem.

Btw what I have been meaning to ask for a while, is anyone else getting really bad performance with the fglrx driver and the overlay-redesign branch? Additionally I get a lot of windows where the the -bar areas (menubar, toolbar, ...) are semi-transparent.

---

### Post by Anduu on 2010-11-25
> **chrisccoulson said:**
> gjs is compatible with the versions in there. Please be more specific about the problem you're having

I don't recall what the exact error was now but it failed to build until I removed the ppa and downgraded.

No time now but I will try it again this evening and see what's up.

---

### Post by moore.bryan on 2010-11-27
> **xtoudi said:**
> You can always ask an author
[http://blogs.gnome.org/fmuellner/2010/11/16/moving-forward/](http://blogs.gnome.org/fmuellner/2010/11/16/moving-forward/)

I can confirm that problem exists.

Thanks for the link, xtoudi; I posted, so we'll see if there's a response.

---

### Post by Harry33 on 2010-11-28
> **Harry33 said:**
> This was a problem before, but it was fixed during Maverick development cycle.
The package libgjs-dev depends on xulrunner.dev (>=1.9.2), I do not see any problems there.
Still, package gnome-shell depends on xulrunner-1.9.2, so that package must be available.

And now the newest gjs (0.7.7-0ubuntu1, new in launchpad, not in repos yet) needs xulrunner-2.0-mozjs and libgjs0b instead of libgjs0a.
There is, however, no gnome-shell package around yet not depending on xulrunner-1.9.2.

---

### Post by nilarimogard on 2010-11-28
.

---

### Post by nilarimogard on 2010-11-28
Those that use the Mozilla Daily PPA - yeah, it breaks stuff starting a few days ago, but it's easy to fix: you must not install "xulrunner-dev" but "xulrunner-1.9.2-dev" and everything will work.

If you do not do this, you'll get an error related to "gjs".

---

### Post by chrisccoulson on 2010-11-28
> **nilarimogard said:**
> Those that use the Mozilla Daily PPA - yeah, it breaks stuff starting a few days ago, but it's easy to fix: you must not install "xulrunner-dev" but "xulrunner-1.9.2-dev" and everything will work.

If you do not do this, you'll get an error related to "gjs".

Well, once [this]("https://wiki.ubuntu.com/DesktopTeam/Specs/Natty/Firefox4/XULRunner20Transition") list is complete, we'll be dropping xulrunner-1.9.2 anyway, so that will only ever be a temporary workaround

---

### Post by Harry33 on 2010-11-29
> **chrisccoulson said:**
> Well, once [this]("https://wiki.ubuntu.com/DesktopTeam/Specs/Natty/Firefox4/XULRunner20Transition") list is complete, we'll be dropping xulrunner-1.9.2 anyway, so that will only ever be a temporary workaround

Yes of course it is a natural development to shift to a more recent version (xulrunner-2.0 + xulrunner-2.0-mozjs; which are already in repos).
Yet there are no gnome-shell package around, that would use this new version.
It is mentioned as "done" in the list, but the only build (an old 2.31.5 version) failed in Launchpad.
When do we get to see a 2.91.x version of gnome-shell?

---

### Post by xtoudi on 2010-11-29
Seems that a few minutes ago **overview-relayout** branch was merged into master.
So now we've got complete new Gnome-Shell user interface - traditional 'jhbuild build' is enough to compile it (without any switching to other branches).

---

### Post by levk on 2010-11-29
I've just built everything this morning, I can't remember the last time I did before, but they've changed the expose-looking screen (whatever their official name for it is) and I can't seem to get it to display more than one desktop at once, am I just missing something or did they really do away with that?

---

### Post by xtoudi on 2010-11-29
> **levk said:**
> I've just built everything this morning, I can't remember the last time I did before, but they've changed the expose-looking screen (whatever their official name for it is) and I can't seem to get it to display more than one desktop at once, am I just missing something or did they really do away with that?

Yes, they did.

About transparency in terminal. Is it only on my terminal that my terminal has no transparency?? I think it happened when was added soft shadows in mutter (maybe two weeks ago).
Anyone can confirm this?

**EDIT**
There is transparency only when terminal is maximized.

---

### Post by Harry33 on 2010-11-29
> **xtoudi said:**
> Yes, they did.

About transparency in terminal. Is it only on my terminal that my terminal has no transparency?? I think it happened when was added soft shadows in mutter (maybe two weeks ago).
Anyone can confirm this?

**EDIT**
There is transparency only when terminal is maximized.

Yes same here, transparency only when maximized.
That might still be a bug.

---

### Post by Merk42 on 2010-11-29
For those who can't/won't/haven't yet built the most recent version, I've updated the images in the first post.

---

### Post by Anduu on 2010-11-29
Just built with the new branch...I like it a lot better than the old overview.Mutter seems quite a bit smoother now too.Not quite there yet though...

Still can't get dconf to build on its own...still have to use --disable-introspection during the configuration phase.Still bugs the crap out of me.

Quick question:
Gnome shell runs fine using xorg-edgers drivers however trying to run it using default xorg and radeon drivers results in massive screen artifacts/corruption.Is this normal?

---

### Post by autocrosser on 2010-11-30
> **Anduu said:**
> Just built with the new branch...I like it a lot better than the old overview.Mutter seems quite a bit smoother now too.Not quite there yet though...

Still can't get dconf to build on its own...still have to use --disable-introspection during the configuration phase.Still bugs the crap out of me.

Quick question:
Gnome shell runs fine using xorg-edgers drivers however trying to run it using default xorg and radeon drivers results in massive screen artifacts/corruption.Is this normal?

Yes---I did a rebuild & am now running the new GS---looks very sweet--using my dual 9800GT-SLI system & windows are MUCH smoother with this version---almost on time with the cursor....

Instersting......I had to do a full system rebuild this weekend (see:  [http://ubuntuforums.org/showthread.php?t=1633848](http://ubuntuforums.org/showthread.php?t=1633848)  &  [http://ubuntuforums.org/showthread.php?t=1632277&page=3](http://ubuntuforums.org/showthread.php?t=1632277&page=3)   If you want the details)...I would guess that a clean install "seemed" to make a real difference & the new version is so much better that the Unity-testing install I'm running also......

---

### Post by amoxi on 2010-11-30
@xtoudi,

I followed your tutorial earlier on how to enable overlay-relayout, and it worked nicely. 
Now that it has been merged into master I presume this is no longer necessary, so which of your changes do I have to undo to get back to default?

Cheers and thanks in advance
amoxi

---

### Post by xtoudi on 2010-11-30
> **amoxi said:**
> @xtoudi,

I followed your tutorial earlier on how to enable overlay-relayout, and it worked nicely. 
Now that it has been merged into master I presume this is no longer necessary, so which of your changes do I have to undo to get back to default?

Cheers and thanks in advance
amoxi

You don't need to undo any changes ... just compile everything.
In case of problems you can:
```
rm -rf ~/gnome-shell/source/gnome-shell
```
and compile again.

**EDIT.**
If you added branch overview-relayout to your **.jhbuildrc** just remove it.

---

### Post by amoxi on 2010-11-30
Thank you!

I will try that once I'm back at home.

oh, and by the way: Gnome Shell rocks!! :popcorn:

Cheers
amoxi

---

### Post by dyltman on 2010-11-30
```
make  
make  all-recursive
make[1]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon'
Making all in gnome-settings-daemon
make[2]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
make  all-am
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
make[2]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
Making all in plugins
make[2]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins'
Making all in common
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/common'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/common'
Making all in a11y-keyboard
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/a11y-keyboard'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/a11y-keyboard'
Making all in automount
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/automount'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/automount'
Making all in background
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/background'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/background'
Making all in clipboard
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/clipboard'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/clipboard'
Making all in datetime
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/datetime'
make  all-am
make[4]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/datetime'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/datetime'
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/datetime'
Making all in dummy
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/dummy'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/dummy'
Making all in housekeeping
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/housekeeping'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/housekeeping'
Making all in keybindings
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/keybindings'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/keybindings'
Making all in keyboard
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/keyboard'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/keyboard'
Making all in media-keys
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make  all-recursive
make[4]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
Making all in cut-n-paste
make[5]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys/cut-n-paste'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys/cut-n-paste'
make[5]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
  CCLD   test-media-keys
/home/marc/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_list_free_full'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_get_environ'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/marc/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/32]

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

I get this error when running jhbuild build

---

### Post by wersdaluv on 2010-11-30
> **dyltman said:**
> ```
make  
make  all-recursive
make[1]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon'
Making all in gnome-settings-daemon
make[2]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
make  all-am
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
make[2]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
Making all in plugins
make[2]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins'
Making all in common
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/common'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/common'
Making all in a11y-keyboard
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/a11y-keyboard'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/a11y-keyboard'
Making all in automount
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/automount'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/automount'
Making all in background
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/background'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/background'
Making all in clipboard
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/clipboard'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/clipboard'
Making all in datetime
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/datetime'
make  all-am
make[4]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/datetime'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/datetime'
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/datetime'
Making all in dummy
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/dummy'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/dummy'
Making all in housekeeping
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/housekeeping'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/housekeeping'
Making all in keybindings
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/keybindings'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/keybindings'
Making all in keyboard
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/keyboard'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/keyboard'
Making all in media-keys
make[3]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make  all-recursive
make[4]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
Making all in cut-n-paste
make[5]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys/cut-n-paste'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys/cut-n-paste'
make[5]: Entering directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
  CCLD   test-media-keys
/home/marc/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_list_free_full'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_get_environ'
/home/marc/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/marc/gnome-shell/install/lib64/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/marc/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/32]

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

I get this error when running jhbuild build

Getting the same error here. Help please

---

### Post by xtoudi on 2010-11-30
If you get libgio-2.0.so erros:

open second terminal:
```
rm ~/gnome-shell/install/lib64/*.la
rm ~/gnome-shell/install/lib/*.la
```

go back to main terminal, get option 6 (wipe).

---

### Post by ean5533 on 2010-11-30
> **xtoudi said:**
> If you get libgio-2.0.so erros:

open second terminal:
```
rm ~/gnome-shell/install/lib64/*.la
rm ~/gnome-shell/install/lib/*.la
```

go back to main terminal, get option 6 (wipe).

Thanks, that solved the issue for me

---

### Post by Decatf on 2010-11-30
I think this has been mentioned before but why does moving windows lag behind the cursor? 

I thought it was and it felt like performance problems before but I'm trying gnome shell again lately and it seems a lot more like window dragging friction is being done intentionally.

---

### Post by ronacc on 2010-11-30
I'm getting that undefined reference error earlier than the above , sofar I have twice removed the .la files and run step 6 and once deleted the entire gnome-shell dir and started from scratch it keeps stalling at 

```
/home/ron/gnome-shell/source/dconf/client/tmp-introspectFm0BEe/dconf-1.0.o: In function `main':
dconf-1.0.c:(.text+0xff3): undefined reference to `g_threads_got_initialized'
dconf-1.0.c:(.text+0x1001): undefined reference to `g_thread_init'
dconf-1.0.c:(.text+0x1006): undefined reference to `g_type_init'
dconf-1.0.c:(.text+0x1026): undefined reference to `g_str_has_prefix'
dconf-1.0.c:(.text+0x1043): undefined reference to `g_printerr'
dconf-1.0.c:(.text+0x1095): undefined reference to `g_printerr'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['gcc', '-o', '/home/ron/gnome-shell/source/dconf/client/tmp-introspectFm0BEe/dconf-1.0', '-L.', '-Wl,-rpath=.', '-ldconf', '-pthread', '-L/home/ron/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/ron/gnome-shell/source/dconf/client/tmp-introspectFm0BEe/dconf-1.0.o']' returned non-zero exit status 1
make[1]: *** [dconf-1.0.gir] Error 1
make[1]: Leaving directory `/home/ron/gnome-shell/source/dconf/client'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/32]

```

---

### Post by Anduu on 2010-11-30
> **ronacc said:**
> I'm getting that undefined reference error earlier than the above , sofar I have twice removed the .la files and run step 6 and once deleted the entire gnome-shell dir and started from scratch it keeps stalling at 

```
/home/ron/gnome-shell/source/dconf/client/tmp-introspectFm0BEe/dconf-1.0.o: In function `main':
dconf-1.0.c:(.text+0xff3): undefined reference to `g_threads_got_initialized'
dconf-1.0.c:(.text+0x1001): undefined reference to `g_thread_init'
dconf-1.0.c:(.text+0x1006): undefined reference to `g_type_init'
dconf-1.0.c:(.text+0x1026): undefined reference to `g_str_has_prefix'
dconf-1.0.c:(.text+0x1043): undefined reference to `g_printerr'
dconf-1.0.c:(.text+0x1095): undefined reference to `g_printerr'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['gcc', '-o', '/home/ron/gnome-shell/source/dconf/client/tmp-introspectFm0BEe/dconf-1.0', '-L.', '-Wl,-rpath=.', '-ldconf', '-pthread', '-L/home/ron/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/ron/gnome-shell/source/dconf/client/tmp-introspectFm0BEe/dconf-1.0.o']' returned non-zero exit status 1
make[1]: *** [dconf-1.0.gir] Error 1
make[1]: Leaving directory `/home/ron/gnome-shell/source/dconf/client'
make: *** [all-recursive] Error 1
*** Error during phase build of dconf: ########## Error running make   *** [18/32]

```

I haven't been able to build dconf properly for weeks now...I did find a workaround.

See here [http://ubuntuforums.org/showpost.php?p=10156003&postcount=219](http://ubuntuforums.org/showpost.php?p=10156003&postcount=219)

---

### Post by ronacc on 2010-11-30
Thanks Anduu for reminding me , you told me about that the last time I did a full rebuild a few days ago and it got me going that time too but I had forgotten already , short term memory loss :lolflag: I did have to make a couple of adjustments this time , it wanted an absolute path for libdir wouldn't accept the ~ and It threw an unknown option error about --disable-static so I deleted that and it building now , up to gnome-icon-theme .

---

### Post by Anduu on 2010-11-30
> **ronacc said:**
> Thanks Anduu for reminding me , you told me about that the last time I did a full rebuild a few days ago and it got me going that time too but I had forgotten already , short term memory loss :lolflag: I did have to make a couple of adjustments this time , it wanted an absolute path for libdir wouldn't accept the ~ and It threw an unknown option error about --disable-static so I deleted that and it building now , up to gnome-icon-theme .

You don't have to tell me about bad short term memory...mine is awful...lol :p

IIRC the --disable-static error has always popped up.

---

### Post by ronacc on 2010-11-30
Its built and running now , got some problems with this new build , lost my wireless in GS and ctrl>c in the term only half kills the shell and does not return to a normal sessiion , fortunately the term stayed active so I could restart the shell , its late here I'll play with it more tomorrow .

---

### Post by Dobbie03 on 2010-12-01
So yesterday I built the latest build and it looks great, but, how do I access my folders without using Docky or something similar?

---

### Post by Anduu on 2010-12-01
> **MattDobson said:**
> So yesterday I built the latest build and it looks great, but, how do I access my folders without using Docky or something similar?

Saw this discussed on the Gnome Shell mailing list...

One thing you can do for now is launch nautilus from a terminal.Then you can right click the nautilus icon on the sidebar and add it to your favourites.

---

### Post by Dobbie03 on 2010-12-01
Ewwww, thats a bit of a roundabout way to do it isn't it?

---

### Post by xtoudi on 2010-12-01
> **MattDobson said:**
> Ewwww, thats a bit of a roundabout way to do it isn't it?

Yes, it is.
If you have any places (left pane in nautilus) you can get it typing their names in overview.

---

### Post by cmccauley on 2010-12-01
Hi all,

Just built the latest gnome-shell and discovered that I can't see all my desktops in the Overview - not much of an overview then is it!

After about a year with GS, I think I've had enough. If the 'Overview' doesn't work then I'm going back to metacity + compiz.

Chris

---

### Post by ronacc on 2010-12-01
ATM I can't get a regular gnome desktop , nautilus dies trying to start with an undefined symbol error starting the gdu extension , both gnome-shell and unity are ok but on boot I have a blank background and have to start one or the other from term .

---

### Post by levk on 2010-12-01
OSX puts Finder on the dock without the possibility of removal, so they should put Nautilus on favorites. Although I have to say overall this branch feels like a usability regression to me, I really liked the multiple desktop view in overview and the recent documents stuff was nice too at least for me despite the general reaction

---

### Post by quickridge on 2010-12-01
> **levk said:**
> OSX puts Finder on the dock without the possibility of removal, so they should put Nautilus on favorites. Although I have to say overall this branch feels like a usability regression to me, I really liked the multiple desktop view in overview and the recent documents stuff was nice too at least for me despite the general reaction

I agree it does feel more or less like a regression. From what I read on the mailing list I assume they will implement some some form of 'Documents & Places' in the near future, although it seems like it might take longer than one would hope.

Also, I'm really missing the grid view. I never found the linear view  (is that what it's called?) useful unless I had a ton of windows on a single desktop. Unfortunately the only thing I've read concerning this from a developer was on Florian Mullner's blog where he claims that the future of grid mode is 'uncertain'.

---

### Post by levk on 2010-12-01
> **quickridge said:**
> I agree it does feel more or less like a regression. From what I read on the mailing this I assume they will implement some some form of 'Documents & Places' in the near future, although it seems like it might take longer than one would hope.

Also, I'm really missing the grid view. I never found the linear view  (is that what it's called?) useful unless I had a ton of windows on a single desktop. Unfortunately the only thing I've read concerning this from a developer was on Florian Mullner's blog where he claims that the future of grid mode is 'uncertain'.

Only reason for them I see to ax the grid view is it was weird when you had multiple monitors but I personally think they should've just worked on that part, they didn't have to actually display what the monitors look like, what you care about is that desktop with the applications running on it regardless of how many monitors that desktop takes up.

---

### Post by Dobbie03 on 2010-12-01
> **xtoudi said:**
> Yes, it is.
If you have any places (left pane in nautilus) you can get it typing their names in overview.

Ah still, I would rather have to click an icon rather than type a name of a folder.  Hope this feature comes back soon.

---

### Post by omega52390 on 2010-12-01
i really like the new system however i totally agree that the grid view is completely necessary so i must say that i dont like the current version entirely because of that lacking 
i have a great idea though which would probably require entirely too much coding to do
what if each screen has it own set of workspaces that show up on its screen in overview you can pick workspaces on each screen independently and if it get extra fun you could move workspaces in between screens

---

### Post by xtoudi on 2010-12-02
Here is nice mockup of the current overview with desktops (video)....it looks very promising ...
[http://jimmac.musichall.cz/log/?p=1107](http://jimmac.musichall.cz/log/?p=1107)

---

### Post by levk on 2010-12-02
> **xtoudi said:**
> Here is nice mockup of the current overview with desktops (video)....it looks very promising ...
[http://jimmac.musichall.cz/log/?p=1107](http://jimmac.musichall.cz/log/?p=1107)

They should give users more credit, I honestly never bothered to use multiple desktops before the grid view (ie before g-shell). Grid view is what made the leap for me.

This solution is OK I guess, but I doubt I'll be using it much anyway. The grid advantage is it lets you instinctively move your eyes to the part of the screen where the app you want is because that's where you left it. You don't really care about desktops as they are, you care to switch to a specific app. This way you introduce an extra click as compared to grid view - first you click the desktop then you click the app. With grid you just click the app.

I mean I honestly don't even know the proper terminology for things - whether they're called desktops or workspaces or whatever and I was able to pick things up fine.

---

### Post by Dobbie03 on 2010-12-03
This might sound like a silly question, but how often should I update GS?  Everyday or once a week?  How often are additions or updates being added?

---

### Post by Framli on 2010-12-03
This atom feed will keep you informed about every modifications. You can base your decisions to update on what you think worths it.
[http://git.gnome.org/browse/gnome-shell/atom/?h=master](http://git.gnome.org/browse/gnome-shell/atom/?h=master)

---

### Post by wersdaluv on 2010-12-03
Got a new build error
```

collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/32]

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

What do I do?

---

### Post by Harry33 on 2010-12-03
As I see this,
Gnome-Shell is quite tough one.
Not at all easy to test.
In official Natty repos there is no working version available.

---

### Post by Dobbie03 on 2010-12-03
> **wersdaluv said:**
> Got a new build error
```

collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/allan/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/32]

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

What do I do?

I think that is something to do with not having the latest version of libnotify, have you looked at this guide here:
[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)

Your error is mentioned there and how to fix it.

---

### Post by Dobbie03 on 2010-12-03
> **Framli said:**
> This atom feed will keep you informed about every modifications. You can base your decisions to update on what you think worths it.
[http://git.gnome.org/browse/gnome-shell/atom/?h=master](http://git.gnome.org/browse/gnome-shell/atom/?h=master)

Cool thanks for that.

---

### Post by sgage on 2010-12-04
Hello folks,

I hadn't tried to compile GS in quite some time, so I thought I'd give it a go this weekend. I get as far as mutter:

```
ui/theme.c: In function ‘meta_gtk_state_to_string’:
ui/theme.c:6109: error: enumeration value ‘GTK_STATE_INCONSISTENT’ not handled in switch
ui/theme.c:6109: error: enumeration value ‘GTK_STATE_FOCUSED’ not handled in switch
make[4]: *** [libmutter_private_la-theme.lo] Error 1
make[4]: Leaving directory `/home/sgage/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/sgage/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sgage/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sgage/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [16/32]
```

Any ideas?

---

### Post by xtoudi on 2010-12-04
There was a huge upload patches into GTK3 in last few hours so we need to wait. it seems that there are problems :-)
Look at this [http://git.gnome.org/browse/gtk+/log](http://git.gnome.org/browse/gtk+/log) - last 4 hours (now) ... a lot of pages!!

---

### Post by sgage on 2010-12-04
> **xtoudi said:**
> There was a huge upload patches into GTK3 in last few hours so we need to wait. it seems that there are problems :-)
Look at this [http://git.gnome.org/browse/gtk+/log](http://git.gnome.org/browse/gtk+/log) - last 4 hours (now) ... a lot of pages!!

Wow - I'll say! I'll try to be patient...

---

### Post by autocrosser on 2010-12-04
GTK3 just built for me----

EDIT--spoke too soon--Mutter errors:```
ui/theme.c: In function &#8216;meta_gtk_state_to_string&#8217;:
ui/theme.c:6109:3: error: enumeration value &#8216;GTK_STATE_INCONSISTENT&#8217; not handled in switch
ui/theme.c:6109:3: error: enumeration value &#8216;GTK_STATE_FOCUSED&#8217; not handled in switch

```

---

### Post by Anduu on 2010-12-04
Just built fine for me but will not run...
```

gnomeshelltest@StormChaser:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Window manager warning: Log level 16: specified class size for type `MetaFrames' is smaller than the parent type's `GtkWindow' class size
Window manager warning: Log level 8: g_once_init_leave: assertion `initialization_value != 0' failed
Window manager warning: Log level 8: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
pkill: 2770 - Operation not permitted
      JS LOG: GNOME Shell started at Sat Dec 04 2010 12:41:26 GMT-0700 (MST)

(mutter:3580): Gvc-WARNING **: Connection failed, reconnecting...
Window manager warning: Log level 8: gtk_widget_get_style: assertion `GTK_IS_WIDGET (widget)' failed
Window manager warning: Log level 8: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: Log level 8: gtk_widget_get_style: assertion `GTK_IS_WIDGET (widget)' failed
Window manager warning: Log level 8: gtk_style_attach: assertion `GTK_IS_STYLE (style)' failed
Shell killed with signal 11

(gnome-power-manager:3598): GLib-GObject-WARNING **: specified class size for type `GsdOsdWindow' is smaller than the parent type's `GtkWindow' class size

(gnome-power-manager:3598): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:3598): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed

(gnome-power-manager:3598): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:3598): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
gnomeshelltest@StormChaser:~/gnome-shell/source/gnome-shell/src$ 

```

I didn't build from scratch so that could possibly be the problem...I'll probably let things settle a bit before I try again.

---

### Post by xtoudi on 2010-12-04
> **autocrosser said:**
> GTK3 just built for me----

What about mutter? We're talking about problems with mutter.

EDIT - ok .. I see your EDIT ;-)

---

### Post by RJ12 on 2010-12-04
I'm having the same problem as everyone else with mutter. It seems like every time I try to "git" (lol) gnome-shell there is all ways some kind of wide spread problem.

---

### Post by sgage on 2010-12-04
> **RJ12 said:**
> I'm having the same problem as everyone else with mutter. It seems like every time I try to "git" (lol) gnome-shell there is all ways some kind of wide spread problem.

Hah! I know how you feel. I'll take a break from GS for a while, decide to check it out again, and *boom*, something unravels. I have an instinct for it ;)

---

### Post by RJ12 on 2010-12-04
I just hope its fixed soon :)

---

### Post by Harry33 on 2010-12-04
Also in Natty official repos there are issues with GTK+3 and mutter.
GTK+3 (2.91.5) makes mutter (2.91.3) segfault.
See the bug # 683279
[https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/683279](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/683279)

---

### Post by xtoudi on 2010-12-04
> **Harry33 said:**
> Also in Natty official repos there are issues with GTK+3 and mutter.
GTK+3 (2.91.5) makes mutter (2.91.3) segfault.
See the bug # 683279
[https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/683279](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/683279)

We've got GTK+3 (2.91.5) and mutter (2.91.3) since a week at least. And everything works great ... till now - so this is sth new.
Like I said before - a lot of patches into GTK+ a few hours ago.

---

### Post by Anduu on 2010-12-04
O.K. just tried building from scratch and mutter fails to build like everyone else.

Guess we just need to keep an eye out for GTK3/mutter updates...

---

### Post by xtoudi on 2010-12-04
> **Anduu said:**
> O.K. just tried building from scratch and mutter fails to build like everyone else.

Guess we just need to keep an eye out for GTK3/mutter updates...

Today new fixes are landing mostly on GTK3:
[http://git.gnome.org/browse/gtk+](http://git.gnome.org/browse/gtk+)
and mutter:
[http://git.gnome.org/browse/mutter](http://git.gnome.org/browse/mutter)

---

### Post by moore.bryan on 2010-12-04
Do we know if the recent fixes are addressing the usability issues with gnome-control-center?

---

### Post by xtoudi on 2010-12-05
> **moore.bryan said:**
> Do we know if the recent fixes are addressing the usability issues with gnome-control-center?

Compiled all.
Condition of gnome-control-center is much better.

---

### Post by tmacyunn on 2010-12-05
Hi all, today I update the gnome-shell sources and get an error, see:
```
cc1: warnings being treated as errors
gsd-media-keys-window.c: In function ‘draw_volume_boxes’:
gsd-media-keys-window.c:414: error: implicit declaration of function ‘gtk_widget_get_style’
gsd-media-keys-window.c:414: error: assignment makes pointer from integer without a cast
.....
*** Error during phase build of gnome-power-manager: ########## Error running make   *** [30/32]

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

I try some method ,such as delete the .la file, or choose "6" to recompile, but failed. Can some give a help?
Thanks a lot.

---

### Post by foureight84 on 2010-12-05
> **tmacyunn said:**
> Hi all, today I update the gnome-shell sources and get an error, see:
```
cc1: warnings being treated as errors
gsd-media-keys-window.c: In function ‘draw_volume_boxes’:
gsd-media-keys-window.c:414: error: implicit declaration of function ‘gtk_widget_get_style’
gsd-media-keys-window.c:414: error: assignment makes pointer from integer without a cast
.....
*** Error during phase build of gnome-power-manager: ########## Error running make   *** [30/32]

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

I try some method ,such as delete the .la file, or choose "6" to recompile, but failed. Can some give a help?
Thanks a lot.

I'm getting the same error~

---

### Post by sgage on 2010-12-05
> **foureight84 said:**
> I'm getting the same error~

And so am I.

[Edit: I told it to ignore the module and move on, and it finished up successfully from there. The resulting gnome-shell seems to be working fine.]

---

### Post by foureight84 on 2010-12-05
It looks like a code bug and not a dependency bug. I'm not seeing any error with make. just the output regarding &#8216;gtk_widget_get_style'

---

### Post by moore.bryan on 2010-12-05
> **xtoudi said:**
> Compiled all.
Condition of gnome-control-center is much better.
So, can I assume the GTK3 bugs are also fixed that kept almost everyone from successfully compiling?

---

### Post by xtoudi on 2010-12-05
> **moore.bryan said:**
> So, can I assume the GTK3 bugs are also fixed that kept almost everyone from successfully compiling?

Except gnome-power-manager, yes. But gnome-power-manager is not required to compile gnome-shell.

---

### Post by RJ12 on 2010-12-05
I'm getting the following error

```
/home/russjr08/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/russjr08/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_list_free_full'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/russjr08/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/32]

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

Edit: Never mind, got it working using the rm ~/gnome-shell/install/lib/*.la command (for 32 bit), but just figured out that gnome-shell doesn't really support my card right now.

---

### Post by Merk42 on 2010-12-05
> **RJ12 said:**
> I'm getting the following error

```
/home/russjr08/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_source_get_time'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/russjr08/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_list_free_full'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/russjr08/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/russjr08/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_get_monotonic_time'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/russjr08/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/32]

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


I want to use the new gnome shell so badly!

Those look like "a lot of 'undefined reference' errors", did you try what I suggested in the OP?
```
rm ~/gnome-shell/install/*.la && sudo rm -rf /usr/lib*/*.la

```

---

### Post by wersdaluv on 2010-12-05
Been getting this **Error during phase build of gnome-power-manager** error. I already tried building from scratch, but I still get it

```
*** Building gnome-power-manager *** [30/32]
make  
make  all-recursive
make[1]: Entering directory `/home/allan/gnome-shell/source/gnome-power-manager'
Making all in src
make[2]: Entering directory `/home/allan/gnome-shell/source/gnome-power-manager/src'
echo "#include \"gpm-marshal.h\"" > gpm-marshal.c && \
	/home/allan/gnome-shell/install/bin/glib-genmarshal gpm-marshal.list --prefix=gpm_marshal --body >> gpm-marshal.c
/home/allan/gnome-shell/install/bin/glib-genmarshal gpm-marshal.list --prefix=gpm_marshal --header > gpm-marshal.h
make  all-am
make[3]: Entering directory `/home/allan/gnome-shell/source/gnome-power-manager/src'
  CC     gpm-debug.o
  CC     gpm-array-float.o
  CC     gpm-idletime.o
  CC     egg-console-kit.o
  CC     gpm-common.o
  CC     gpm-brightness.o
  CC     gpm-marshal.o
  CC     gpm-upower.o
  AR     libgpmshared.a
  CC     gnome_power_manager-gpm-dpms.o
  CC     gnome_power_manager-gpm-phone.o
  CC     gnome_power_manager-gpm-backlight.o
  CC     gnome_power_manager-gpm-idle.o
  CC     gnome_power_manager-gpm-disks.o
  CC     gnome_power_manager-gpm-control.o
  CC     gnome_power_manager-gpm-button.o
  CC     gnome_power_manager-gpm-main.o
  CC     gnome_power_manager-gpm-manager.o
  CC     gnome_power_manager-gpm-tray-icon.o
  CC     gnome_power_manager-gpm-screensaver.o
  CC     gnome_power_manager-gsd-media-keys-window.o
cc1: warnings being treated as errors
gsd-media-keys-window.c: In function ‘draw_volume_boxes’:
gsd-media-keys-window.c:414:9: error: implicit declaration of function ‘gtk_widget_get_style’
gsd-media-keys-window.c:414:15: error: assignment makes pointer from integer without a cast
make[3]: *** [gnome_power_manager-gsd-media-keys-window.o] Error 1
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-power-manager/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/allan/gnome-shell/source/gnome-power-manager/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/allan/gnome-shell/source/gnome-power-manager'
make: *** [all] Error 2
*** Error during phase build of gnome-power-manager: ########## Error running make   *** [30/32]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"

```

What do I do?

---

### Post by sgage on 2010-12-05
> **wersdaluv said:**
> Been getting this **Error during phase build of gnome-power-manager** error. I already tried building from scratch, but I still get it

```
*** Building gnome-power-manager *** [30/32]
make  
make  all-recursive
make[1]: Entering directory `/home/allan/gnome-shell/source/gnome-power-manager'
Making all in src
make[2]: Entering directory `/home/allan/gnome-shell/source/gnome-power-manager/src'
echo "#include \"gpm-marshal.h\"" > gpm-marshal.c && \
	/home/allan/gnome-shell/install/bin/glib-genmarshal gpm-marshal.list --prefix=gpm_marshal --body >> gpm-marshal.c
/home/allan/gnome-shell/install/bin/glib-genmarshal gpm-marshal.list --prefix=gpm_marshal --header > gpm-marshal.h
make  all-am
make[3]: Entering directory `/home/allan/gnome-shell/source/gnome-power-manager/src'
  CC     gpm-debug.o
  CC     gpm-array-float.o
  CC     gpm-idletime.o
  CC     egg-console-kit.o
  CC     gpm-common.o
  CC     gpm-brightness.o
  CC     gpm-marshal.o
  CC     gpm-upower.o
  AR     libgpmshared.a
  CC     gnome_power_manager-gpm-dpms.o
  CC     gnome_power_manager-gpm-phone.o
  CC     gnome_power_manager-gpm-backlight.o
  CC     gnome_power_manager-gpm-idle.o
  CC     gnome_power_manager-gpm-disks.o
  CC     gnome_power_manager-gpm-control.o
  CC     gnome_power_manager-gpm-button.o
  CC     gnome_power_manager-gpm-main.o
  CC     gnome_power_manager-gpm-manager.o
  CC     gnome_power_manager-gpm-tray-icon.o
  CC     gnome_power_manager-gpm-screensaver.o
  CC     gnome_power_manager-gsd-media-keys-window.o
cc1: warnings being treated as errors
gsd-media-keys-window.c: In function ‘draw_volume_boxes’:
gsd-media-keys-window.c:414:9: error: implicit declaration of function ‘gtk_widget_get_style’
gsd-media-keys-window.c:414:15: error: assignment makes pointer from integer without a cast
make[3]: *** [gnome_power_manager-gsd-media-keys-window.o] Error 1
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-power-manager/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/allan/gnome-shell/source/gnome-power-manager/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/allan/gnome-shell/source/gnome-power-manager'
make: *** [all] Error 2
*** Error during phase build of gnome-power-manager: ########## Error running make   *** [30/32]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"

```

What do I do?

Well, as mentioned above in the thread, I picked door number 3 (give up on module) and the rest of the compile was successful, and the resulting GS seems to work just fine.

---

### Post by dext on 2010-12-05
i'd pick **8 Go to phase "clean"** and then maybe **6 - Go to phase "wipe directory and start over"**

---

### Post by sgage on 2010-12-05
> **dext said:**
> i'd pick **8 Go to phase "clean"** and then maybe **6 - Go to phase "wipe directory and start over"**

Except that won't work - at least it didn't for me in several tries. In any case gnome-shell does not depend on gnome-power-management, so you can just ignore it and move on. This has been discussed above in the thread.

---

### Post by wersdaluv on 2010-12-06
Network Manager dies whenever I run an Adobe Air app. 

Does this have something to do with the stuff that didn't build (gnome-power-manager or maybe stuff that depend on it)? This seems to be the first time I encountered something like this

---

### Post by tmacyunn on 2010-12-06
Just update the sources code, the errors seem to be solved. 
Thanks for those working on this.

---

### Post by wersdaluv on 2010-12-07
> **tmacyunn said:**
> Just update the sources code, the errors seem to be solved. 
Thanks for those working on this.
Same here. No more gnome-power-manager or any other error

---

### Post by youoh on 2010-12-07
Gnome-shell crash after recieving massages with Empathy.

trying to restart it result in :

JS LOG: GNOME Shell started at Tue Dec 07 2010 19:38:28 GMT+0100 (CET)
JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:12858): GdmUser-WARNING **: Unable to load CK history: no seat-id found
Shell killed with signal 11

relogging fixes this

---

### Post by Finalfantasykid on 2010-12-08
Compiled fine, but now I'm getting this after I hover over Activities a couple of times:

```
(gnome-panel:3381): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
      JS LOG: GNOME Shell started at Tue Dec 07 2010 23:38:46 GMT-0700 (MST)
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:8728): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:8745): WARNING **: Unknown option --since=2010-10-09T06:38:47.435087Z
**
Cogl-glx:ERROR:./cogl-pipeline.c:2964:_cogl_pipeline_layer_resolve_authorities: assertion failed: (remaining == 0)
Shell killed with signal 6

```

I'm using Maverick, Nvidia, 64-bit

---

### Post by simpleblue on 2010-12-10
For all those that don't want to compile there is a very easy way to try the most up to date Gnome Shell:


1. Download the [Fedora 15 Rawhide Iso]("http://alt.fedoraproject.org/pub/alt/nightly-composes/desktop/")
2. Run the livecd. enter the 'desktop effects' app and select 'Gnome 3'
3. You'll be running the newest build of Gnome Shell :)


[Here is a pic for those interested [click here]]("http://ubuntuone.com/p/SwK/")

---

### Post by xtoudi on 2010-12-10
> **simpleblue said:**
> For all those that don't want to compile there is a very easy way to try the most up to date Gnome Shell:


1. Download the [Fedora 15 Rawhide Iso]("http://alt.fedoraproject.org/pub/alt/nightly-composes/desktop/")
2. Run the livecd. enter the 'desktop effects' app and select 'Gnome 3'
3. You'll be running the newest build of Gnome Shell :)


[Here is a pic for those interested [click here]]("http://ubuntuone.com/p/SwK/")

1. Is this a daily iso ?
2. Download a whole iso to try GS ??
3. Fedora? This is Ubuntu forum ...

---

### Post by Harry33 on 2010-12-10
> **xtoudi said:**
> 1. Is this a daily iso ?
2. Download a whole iso to try GS ??
3. Fedora? This is Ubuntu forum ...

Simpleblue is right about the fact that if one does not want to use jhbuild, that might be one solution.
After all, there is not any working version (old or new) in neither of:
- Natty repositories
- Any PPA in launchpad.

Still I hope there will be one quite soon.
Micah Gersten is about to upload new Gnome-shell into Natty repos, one of these days I think.

---

### Post by simpleblue on 2010-12-10
> **xtoudi said:**
> 1. Is this a daily iso ?
2. Download a whole iso to try GS ??
3. Fedora? This is Ubuntu forum ...

This is an alternate solution. I agree that it is a big download, but it's main benefit is ease of use and not having to compile. There are many people having issues compiling on this thread.

And you get to see the bleeding edge of Linux (Fedora 15), which can be cool, so long as it doesn't crash and burn before it even starts. ;)

Personally I wouldn't want to try GS in Ubuntu because as of now there's no future in it. Ubuntu is moving away from GS.

---

### Post by cariboo on 2010-12-10
Ubuntu may be moving away from gnome-shell, but it will still be available in the repositories,. for anyone that wants to use it. As Harry33 says, hopefully there will be an updated version available. I personally prefer gnome-shell over Unity.

---

### Post by plun on 2010-12-10
> **cariboo907 said:**
>  I personally prefer gnome-shell over Unity.

Well.... I prefer Docky or sometimes AWN... :D

---

### Post by cariboo on 2010-12-10
I use docky along with Unity and gnome-shell

---

### Post by plun on 2010-12-10
> **cariboo907 said:**
> I use docky along with Unity and gnome-shell

Yup... do you need GS or Unity....? ;)

Both Gnome and Ubuntu are doing something that a normal user doesn't want !

A majority wants a dock as every descent Macuser....!!

---

### Post by cariboo on 2010-12-10
Do we actually need a two panel interface. To me it seems like Gnome and Ubuntu are trying to differentiate themselves from both Windows and OSX, which I welcome. Both Windows and OSX share a lot of things, and most Linux DEs share a lot with both, which makes it easier for users of both to make the transition to Ubuntu/Gnome. 

If you check the [Screenshot thread]("http://ubuntuforums.org/showthread.php?t=1562130") you will see many desktops are setup to emulate Windows or OSX, to me this is getting pretty tired looking, anything that can be done to change the user interface is a welcome change for many of us.

---

### Post by plun on 2010-12-10
> **cariboo907 said:**
> Do we actually need a two panel interface. To me it seems like Gnome and Ubuntu are trying to differentiate themselves from both Windows and OSX, which I welcome. Both Windows and OSX share a lot of things, and most Linux DEs share a lot with both, which makes it easier for users of both to make the transition to Ubuntu/Gnome. 

If you check the [Screenshot thread]("http://ubuntuforums.org/showthread.php?t=1562130") you will see many desktops are setup to emulate Windows or OSX, to me this is getting pretty tired looking, anything that can be done to change the user interface is a welcome change for many of us.

Well.... as I wrote both Ubuntu and Gnome missing the point what a user wants.....  Windows have some sort of a dock and for sure MacOsx got one.

Unity is beautiful eyecandy and GS is what the "nerds" brought to us, but both they are missing what a user wants.


I am going to use the best of the two running Docky or AWN.....!!


(sorry for my english;) )

---

### Post by terry_gardener on 2010-12-10
> **plun said:**
> Well.... as I wrote both Ubuntu and Gnome missing the point what a user wants.....  Windows have some sort of a dock and for sure MacOsx got one.

Unity is beautiful eyecandy and GS is what the "nerds" brought to us, but both they are missing what a user wants.


I am going to use the best of the two running Docky or AWN.....!!


(sorry for my english;) )

i think users dont necessarily want a dock they just want a quick and easy way to access the programs they use regulary. 

for example: my parents dont care about a dock they just want to be able to access the program they use regulary quickly and easily.

---

### Post by seeker5528 on 2010-12-10
Copied and pasted from my post in another thread....

I was watching this episode of Vanishing Son the other day and it started out with this story.

> 
This old man had a horse he kept penned in a field behind his house.
One day the horse escaped.
His neighbors all came over and said "That's bad." and the old man replied "How do you know?.
The next day the old man's horse returned bringing a bunch of wild horses with it.
His neighbors all came over and said "That's good." and the old man replied "How do you know?".

> **plun said:**
> Both Gnome and Ubuntu are doing something that a normal user doesn't want !

How do you know? ;)

Later, Seeker

---

### Post by cariboo on 2010-12-10
This discussion is getting a little off topic, I blame myself for that, so could we please keep this thread about gnome-shell, and not what our personal preferences are.

BTW, great analogy seeker5528

---

### Post by lime4x4 on 2010-12-10
Does gnome shell currently support 2 monitors each as a seperate x-screen?

---

### Post by Harry33 on 2010-12-11
> **cariboo907 said:**
> Ubuntu may be moving away from gnome-shell, but it will still be available in the repositories,. for anyone that wants to use it. As Harry33 says, hopefully there will be an updated version available. I personally prefer gnome-shell over Unity.

OK, I just noticed Rico has managed to build a new gnome-shell package.
You'll find it in his staging PPA:
[https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging)

The packages there are almost all very recent git-versions, so some precaution using them might be wise. On the other hand, most of the packages can be uninstalled without any effects on the normal system (gnome-panel, Natty). However packages like gnome-settings-daemon and libgnomekbd are GTK+3 versions and may break your system. I would not install those.

By looking at the dependencies of the new gnome-shell package
(2.91.3+git20101210.26a5197d-0ubuntu1~11.04~ricotz0.2)
I can see that it depends on very recent (not in Natty repos) clutter (1.5.8-0ubuntu1) and the package gir1.0-mutter-2.91.  So you must also use this staging PPA mutter, because in Natty repos we have gir1.0-mutter-2.31 (which is obviously an old name). Both those mutter packages are still of the version 2.91.3.

In Natty repos we have many recent packages like (gjs, libgjs0b, libgnome-desktop3, gsettings-desktop-schemas and gobject-introspection) and it is very likely that they will work.

The package gnome-themes-standard can only be found in Rico's PPA.

---

### Post by moore.bryan on 2010-12-11
Just to contribute: I just successfully built GNOME Shell on Ubuntu 10.10 and Fedora 14 with no errors.

---

### Post by cariboo on 2010-12-11
@moore.bryan: Congrats on finally getting it to work. :)

---

### Post by Harry33 on 2010-12-12
You can find a bleeding edge Gnome-Shell for Natty in the testing PPA of Rico Tzschichholz:
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

The packages there are all very recent versions and installing Gnome-shell from this PPA can be a good option to jhbuild.
However, keep in mind that this way it will be an installation into the system and will break some applications and functions.
Rico says in his PPA that Gnome-shell needs packages like gnome-settings-daemon_2.91.5.1 and thus also libgnomekbd_2.91.3.1. which both are GTK+3 versions.

Installing GTK+3 version of gnome-settings-daemon will break GTk2-theming in several ways. The themes in Gnome-panel (GTK+2) do not work after this. Also gdm will lose theming and its background (it will be plain black).

But it is also possible to downgrade GTK+3 version of gnome-settings-daemon and libgnomekbd7 and libgnomekbd-common to GTK+2 versions with Synaptic.

---

### Post by moore.bryan on 2010-12-13
> **cariboo907 said:**
> @moore.bryan: Congrats on finally getting it to work. :)

Thanks, cariboo!

---

### Post by autocrosser on 2010-12-15
Anyone having a problem building gobject-introspection this evening?  I'm getting a linking warning:  ```
  GISCAN GModule-2.0.gir
g-ir-scanner: GModule: warning: 1 warnings suppressed (use --warn-all to see them)
  GISCAN Gio-2.0.gir
/home/dean/gnome-shell/source/gobject-introspection/tmp-introspectrb2ZoP/Gio-2.0.o:(.data+0x548): undefined reference to `g_periodic_get_type'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', './libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/dean/gnome-shell/source/gobject-introspection/tmp-introspectrb2ZoP/Gio-2.0', '-export-dynamic', '-pthread', '-L/home/dean/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '-lgio-2.0', '/home/dean/gnome-shell/source/gobject-introspection/tmp-introspectrb2ZoP/Gio-2.0.o']' returned non-zero exit status 1
make[2]: *** [Gio-2.0.gir] Error 1
make[2]: Leaving directory `/home/dean/gnome-shell/source/gobject-introspection'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dean/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/32]

```

---

### Post by Merk42 on 2010-12-15
> **autocrosser said:**
> Anyone having a problem building gobject-introspection this evening?  I'm getting a linking warning:  ```
  GISCAN GModule-2.0.gir
g-ir-scanner: GModule: warning: 1 warnings suppressed (use --warn-all to see them)
  GISCAN Gio-2.0.gir
/home/dean/gnome-shell/source/gobject-introspection/tmp-introspectrb2ZoP/Gio-2.0.o:(.data+0x548): undefined reference to `g_periodic_get_type'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', './libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/dean/gnome-shell/source/gobject-introspection/tmp-introspectrb2ZoP/Gio-2.0', '-export-dynamic', '-pthread', '-L/home/dean/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '-lgio-2.0', '/home/dean/gnome-shell/source/gobject-introspection/tmp-introspectrb2ZoP/Gio-2.0.o']' returned non-zero exit status 1
make[2]: *** [Gio-2.0.gir] Error 1
make[2]: Leaving directory `/home/dean/gnome-shell/source/gobject-introspection'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dean/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/32]

```I just built (on 10.10) about an hour ago. I did have some problem, but deleting the gnome-shell and source files and redoing it from scratch worked.

---

### Post by Anduu on 2010-12-16
> **Merk42 said:**
> I just built (on 10.10) about an hour ago. I did have some problem, but deleting the gnome-shell and source files and redoing it from scratch worked.

I rebuilt from scratch tonight without any problems.

---

### Post by HalfEmptyHero on 2010-12-16
> **Harry33 said:**
> You can find a bleeding edge Gnome-Shell for Natty in the testing PPA of Rico Tzschichholz:
[https://launchpad.net/~ricotz/+archive/testing]("https://launchpad.net/%7Ericotz/+archive/testing")

The packages there are all very recent versions and installing Gnome-shell from this PPA can be a good option to jhbuild.
However, keep in mind that this way it will be an installation into the system and will break some applications and functions.
Rico says in his PPA that Gnome-shell needs packages like gnome-settings-daemon_2.91.5.1 and thus also libgnomekbd_2.91.3.1. which both are GTK+3 versions.

Installing GTK+3 version of gnome-settings-daemon will break GTk2-theming in several ways. The themes in Gnome-panel (GTK+2) do not work after this. Also gdm will lose theming and its background (it will be plain black).

But it is also possible to downgrade GTK+3 version of gnome-settings-daemon and libgnomekbd7 and libgnomekbd-common to GTK+2 versions with Synaptic.

I couldn't downgrade libgnomekbd-common without removing libgnomkbd7. After I did that gnome shell wouldn't show up. When I reinstalled it and upgraded settings daemon/libgnomkbd-common it worked again.

---

### Post by Harry33 on 2010-12-17
> **HalfEmptyHero said:**
> I couldn't downgrade libgnomekbd-common without removing libgnomkbd7. After I did that gnome shell wouldn't show up. When I reinstalled it and upgraded settings daemon/libgnomkbd-common it worked again.

Well fine its OK now.
And the Gnome-shell from ricotz PPA is anyway completely broken because of the transition from gir1.0 to gir1.2 in Ubuntu.

---

### Post by ronacc on 2010-12-17
gnome-shell built ok from scratch yesterday , today a build from scratch dies building mutter with this error .
```
cc1: warnings being treated as errors
ui/ui.c: In function ‘maybe_redirect_mouse_event’:
ui/ui.c:209:3: error: implicit declaration of function ‘gdk_display_get_core_pointer’
ui/ui.c:209:3: error: nested extern declaration of ‘gdk_display_get_core_pointer’
ui/ui.c:209:3: error: passing argument 2 of ‘gdk_event_set_device’ makes pointer from integer without a cast
/home/ron/gnome-shell/install/include/gtk-3.0/gdk/gdkevents.h:1089:12: note: expected ‘struct GdkDevice *’ but argument is of type ‘int’
make[4]: *** [ui.o] Error 1
make[4]: Leaving directory `/home/ron/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/ron/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ron/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ron/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [16/32]

```

---

### Post by mortski on 2010-12-17
> **autocrosser said:**
> Anyone having a problem building gobject-introspection this evening?  I'm getting a linking warning:  ```
  GISCAN GModule-2.0.gir
g-ir-scanner: GModule: warning: 1 warnings suppressed (use --warn-all to see them)
  GISCAN Gio-2.0.gir
/home/dean/gnome-shell/source/gobject-introspection/tmp-introspectrb2ZoP/Gio-2.0.o:(.data+0x548): undefined reference to `g_periodic_get_type'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', './libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/dean/gnome-shell/source/gobject-introspection/tmp-introspectrb2ZoP/Gio-2.0', '-export-dynamic', '-pthread', '-L/home/dean/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '-lgio-2.0', '/home/dean/gnome-shell/source/gobject-introspection/tmp-introspectrb2ZoP/Gio-2.0.o']' returned non-zero exit status 1
make[2]: *** [Gio-2.0.gir] Error 1
make[2]: Leaving directory `/home/dean/gnome-shell/source/gobject-introspection'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dean/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/32]

```

You can get past this error by removing the stale gperiodic.h from install/include/glib-2.0/gio/

---

### Post by omega52390 on 2010-12-17
anyone noticed they added win7 edge maxing i dont think i can ever leave gnome shell again now

---

### Post by HalfEmptyHero on 2010-12-17
Has anyone noticed that whenever a program is running that uses the bottom bar thingy (empathy, tomboy, etc.) the shell's zoom in/out to the dashboard is slowed down significantly?

---

### Post by moore.bryan on 2010-12-17
> **omega52390 said:**
> anyone noticed they added win7 edge maxing i dont think i can ever leave gnome shell again now

I wonder how long that's been in there... I compiled a couple of days ago and it's there too. Nice.

---

### Post by billyoc on 2010-12-18
> **mortski said:**
> You can get past this error by removing the stale gperiodic.h from install/include/glib-2.0/gio/
That did the trick, much obliged.

---

### Post by nazgul77 on 2010-12-18
> **mortski said:**
> You can get past this error by removing the stale gperiodic.h from install/include/glib-2.0/gio/

That did the trick, thanks.

---

### Post by xtoudi on 2010-12-18
> **moore.bryan said:**
> I wonder how long that's been in there... I compiled a couple of days ago and it's there too. Nice.

Left/right edge of screen at least two/three months - seriously :-).
Top edge completely rewritten one/two weeks ago.

---

### Post by moore.bryan on 2010-12-18
So nice... didn't notice, but a simple, clean addition. Kudos to developers.

---

### Post by Anduu on 2010-12-18
Just compiled today without a hitch,however gnome-shell dies with:

```
gnomeshelltest@StormChaser:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
pkill: 11430 - Operation not permitted
Window manager warning: Log level 16: Failed to load shared library 'libgnome-bluetooth-applet.so.0' referenced by the typelib: libgnome-bluetooth-applet.so.0.so: cannot open shared object file: No such file or directory
Window manager warning: Log level 8: g_ascii_strncasecmp: assertion `s2 != NULL' failed
Shell killed with signal 11

```

Seems the addition of the bluetooth applet is causing problems.

Anyone else seeing this?

---

### Post by dext on 2010-12-18
> **Anduu said:**
> Just compile today without a hitch,however gnome-shell dies with:

```
gnomeshelltest@StormChaser:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
pkill: 11430 - Operation not permitted
Window manager warning: Log level 16: Failed to load shared library 'libgnome-bluetooth-applet.so.0' referenced by the typelib: libgnome-bluetooth-applet.so.0.so: cannot open shared object file: No such file or directory
Window manager warning: Log level 8: g_ascii_strncasecmp: assertion `s2 != NULL' failed
Shell killed with signal 11

```

Seems the addition of the bluetooth applet is causing problems.

Anyone else seeing this?
wht if you Disable Bluetooth ? does it still Crash

---

### Post by Anduu on 2010-12-18
> **dext said:**
> wht if you Disable Bluetooth ? does it still Crash

Haven't gone that far yet.I have never had cause to disable specific modules so I am not even sure how to do that.

I'll have to look into it.

---

### Post by moore.bryan on 2010-12-18
Is anyone else still getting the bug where your wallpaper goes to a solid black background during Overview? Yeah, that's me. :-(

EDIT: Seems this was fixed by my most recent build; just wonder how it keeps creeping up.

On an unrelated note, do we yet have a solution for gnome-power-control to actually regain control over backlight brightness? I can't change when my display dims and when it doesn't.

EDIT 2: The latest build solves my "dimming" issue... I can just use the "Screen" setting to alter things.

---

### Post by Finalfantasykid on 2010-12-21
I can't seem to be able to compile GS at the moment.

```
checking /home/david/gnome-shell/install/bin/valac is at least version 0.11... no
configure: error: Vala 0.11 not found.
```

This is probably because I am running Maverick, which uses Vala 0.10 I think.  Is there any way around this, or should I just instal the latest vala from source?

---

### Post by dext on 2010-12-21
i would of thought **jhbuild** was frozen till they get 2.90.4 out the door which could be anytime now.

---

### Post by moore.bryan on 2010-12-22
I just compiled on Maverick with no problems yesterday... hmm. Don't quite know about the Vala error. Have you tried deleting the whole gnome-shell dir?

---

### Post by xtoudi on 2010-12-22
Latest commit: gnome-shell.modules: Build vala 0.11.2.

---

### Post by Finalfantasykid on 2010-12-22
Ok I deleted the folder and I got past the vala error, but now I'm getting this:

```

cc1: warnings being treated as errors
st/st-im-text.c: In function &#8216;window_for_actor&#8217;:
st/st-im-text.c:203: error: implicit declaration of function &#8216;gdk_window_lookup_for_display&#8217;
st/st-im-text.c:203: error: assignment makes pointer from integer without a cast
st/st-im-text.c:207: error: implicit declaration of function &#8216;gdk_window_foreign_new_for_display&#8217;
st/st-im-text.c:207: error: assignment makes pointer from integer without a cast
make[3]: *** [libst_1_0_la-st-im-text.lo] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [30/33]

```I'm guessing this is just a temporary error, and might be fixed later today.

EDIT:  Yay it seems to have been fixed.
EDIT2: Ok I just ran it, and it crashed instantly with this message:

```
david@david:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
      JS LOG: GNOME Shell started at Wed Dec 22 2010 14:58:31 GMT-0700 (MST)
Shell killed with signal 11
david@david:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Panel leaving: a new panel shell is starting.

(gnome-panel:22618): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
      JS LOG: GNOME Shell started at Wed Dec 22 2010 14:58:56 GMT-0700 (MST)
Shell killed with signal 11

```

---

### Post by dext on 2010-12-22
[GTK+3 Now Uses X Input 2 By Default, New Back-End Caps]("http://www.phoronix.com/scan.php?page=news_item&px=ODk0Ng") bit of News for some of you , 

 ( if there is no use for this News here, a Mod might wanna split it )

---

### Post by davideotape on 2010-12-23
```
make[2]: Entering directory `/home/david/gnome-shell/source/gobject-introspection'
  GISCAN Gio-2.0.gir
/home/david/gnome-shell/source/gobject-introspection/tmp-introspectkWQUmU/Gio-2.0.o:(.data+0x2a4): undefined reference to `g_periodic_get_type'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', './libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/david/gnome-shell/source/gobject-introspection/tmp-introspectkWQUmU/Gio-2.0', '-export-dynamic', '-pthread', '-L/home/david/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '-lgio-2.0', '/home/david/gnome-shell/source/gobject-introspection/tmp-introspectkWQUmU/Gio-2.0.o']' returned non-zero exit status 1
make[2]: *** [Gio-2.0.gir] Error 1
make[2]: Leaving directory `/home/david/gnome-shell/source/gobject-introspection'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gobject-introspection'
make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/33]

```

:(

---

### Post by olivier.blanc on 2010-12-23
> **Anduu said:**
> Just compiled today without a hitch,however gnome-shell dies with:

```
gnomeshelltest@StormChaser:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
pkill: 11430 - Operation not permitted
Window manager warning: Log level 16: Failed to load shared library 'libgnome-bluetooth-applet.so.0' referenced by the typelib: libgnome-bluetooth-applet.so.0.so: cannot open shared object file: No such file or directory
Window manager warning: Log level 8: g_ascii_strncasecmp: assertion `s2 != NULL' failed
Shell killed with signal 11

```

Seems the addition of the bluetooth applet is causing problems.

Anyone else seeing this?

I have the same problem since yesterday. Does anyone found a fix for that ?

Tnx

---

### Post by autocrosser on 2010-12-24
> **olivier.blanc said:**
> I have the same problem since yesterday. Does anyone found a fix for that ?

Tnx

Yes--create a link from your /gnome-shell/install/lib (or lib64--depends on your system)/gnome-bluetooth/libgnome-bluetooth-applet.so.0.0.0 to the main /lib & rename it according to your error......then GS will start.

---

### Post by Anduu on 2010-12-24
> **autocrosser said:**
> Yes--create a link from your /gnome-shell/install/lib (or lib64--depends on your system)/gnome-bluetooth/libgnome-bluetooth-applet.so.0.0.0 to the main /lib & rename it according to your error......then GS will start.

My brain isn't working today....I can't figure out the link.I have tried a couple of combinations but no luck.

Not sure what you mean by "the main /lib".Perhaps an example command I can modify to suit my needs?

Sorry but I am a relative noob where symlinks are concerned :(

---

### Post by autocrosser on 2010-12-24
> **Anduu said:**
> My brain isn't working today....I can't figure out the link.I have tried a couple of combinations but no luck.

Not sure what you mean by "the main /lib".Perhaps an example command I can modify to suit my needs?

Sorry but I am a relative noob where symlinks are concerned :(

I just did it the old fashioned way--nav to /gnome-shell/install/lib(or lib64)/gnome-bluetooth/libgnome-bluetooth-applet.so.0.0.0---right-click/make link & then move the link to either /lib or /lib64 (depending on your system type)--then rename the link to libgnome-bluetooth-applet.so.0 & you are good to go.....

I could write something but I'm lazy & just nav to where I want to go--I know it's cooler to open a term & input a single command, but sometimes it's better to go hunting for what you want--you get to know your system better that way ;)

---

### Post by Anduu on 2010-12-24
> **autocrosser said:**
> I just did it the old fashioned way--nav to /gnome-shell/install/lib(or lib64)/gnome-bluetooth/libgnome-bluetooth-applet.so.0.0.0---right-click/make link & then move the link to either /lib or /lib64 (depending on your system type)--then rename the link to libgnome-bluetooth-applet.so.0 & you are good to go.....

I could write something but I'm lazy & just nav to where I want to go--I know it's cooler to open a term & input a single command, but sometimes it's better to go hunting for what you want--you get to know your system better that way ;)

Cool...I kind of figured you meant the root libs folder but didn't want to muck about in there til I was sure of what I was doing.

Much appreciated ;)

---

### Post by autocrosser on 2010-12-24
> **Anduu said:**
> Cool...I kind of figured you meant the root libs folder but didn't want to muck about in there til I was sure of what I was doing.

Much appreciated ;)

Na--was way too simple--they just forgot to include the link in /gnome-shell/install/lib...I have seen that a few times over the past couple of years.....

O-crud---I hope you just moved it to /gnome-shell/install/lib....I guess that I'm a bit muddle-brained today......

---

### Post by Anduu on 2010-12-24
> **autocrosser said:**
> Na--was way too simple--they just forgot to include the link in /gnome-shell/install/lib...I have seen that a few times over the past couple of years.....

[COLOR="Red"]O-crud---I hope you just moved it to /gnome-shell/install/lib....I guess that I'm a bit muddle-brained today......[/COLOR]

Yup "~/gnome-shell/install/lib64/" lol....worked like a charm.

Thanks again :KS

---

### Post by ranch hand on 2010-12-25
> **autocrosser said:**
> I just did it the old fashioned way--nav to /gnome-shell/install/lib(or lib64)/gnome-bluetooth/libgnome-bluetooth-applet.so.0.0.0---right-click/make link & then move the link to either /lib or /lib64 (depending on your system type)--then rename the link to libgnome-bluetooth-applet.so.0 & you are good to go.....

I could write something but I'm lazy & just nav to where I want to go--I know it's cooler to open a term & input a single command, but sometimes it's better to go hunting for what you want--you get to know your system better that way ;)
I like doing it this way too.  I am real lazy, I have nautilus-gksu installed.  Just right click on the directory and select "open as administrator" in the menu, give password and you are in nautilus as root.

---

### Post by autocrosser on 2010-12-25
Yep--I've got nautilus-gksu installed also--very handy...Also nautilus-open-terminal--contrary to some things I say--I do use it quite a bit also....

Perhaps it's the Mac-background I've had that tends to make me nav around--I know that Windozs discourages muckin' about in file-systems ;)

---

### Post by ronacc on 2010-12-25
Merry Christmas RH glad to see you got a day off .

---

### Post by ranch hand on 2010-12-25
> **autocrosser said:**
> Yep--I've got nautilus-gksu installed also--very handy...Also nautilus-open-terminal--contrary to some things I say--I do use it quite a bit also....

Perhaps it's the Mac-background I've had that tends to make me nav around--I know that Windozs discourages muckin' about in file-systems ;)
Yup, they are both handier than a pocket on a shirt.

---

### Post by ronacc on 2010-12-27
after a fresh build just a few minutes ago , the build went ok , no hitches at all but I'm getting a  JS error when I try to start GS .
```
ron@ron-desktop2:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
    JS ERROR: !!!   Exception was: Error: Bad method name "Gdk.Display.get_device_state"
    JS ERROR: !!!     lineNumber = '43'
    JS ERROR: !!!     fileName = '/home/ron/gnome-shell/source/gnome-shell/js/ui/environment.js'
    JS ERROR: !!!     stack = '_blockMethod("Gdk.Display.get_device_state","global.get_pointer","gjs's handling of Gdk.ModifierType is broken. See bug 597292.")@/home/ron/gnome-shell/source/gnome-shell/js/ui/environment.js:43
init()@/home/ron/gnome-shell/source/gnome-shell/js/ui/environment.js:92
start()@/home/ron/gnome-shell/source/gnome-shell/js/ui/main.js:91
@<main>:1
'
    JS ERROR: !!!     message = 'Bad method name "Gdk.Display.get_device_state"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Bad method name "Gdk.Display.get_device_state"
ron@ron-desktop2:~/gnome-shell/source/gnome-shell/src$ No value set for `/apps/compiz-1/general/allscreens/options/active_plugins'
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing imgsvg options...done
Initializing imgjpeg options...done
Initializing vpswitch options...done
Initializing move options...done
Initializing resize options...done
Initializing cube options...done
Initializing switcher options...done
Initializing rotate options...done
constraining to 0
constraining to 0
constraining to 0
constraining to 0
ron@ron-desktop2:~/gnome-shell/source/gnome-shell/src$ 

```

then it dumps me back in classic .

---

### Post by ronniepoe on 2010-12-28
> **ronacc said:**
> after a fresh build just a few minutes ago , the build went ok , no hitches at all but I'm getting a  JS error when I try to start GS .
```
ron@ron-desktop2:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
    JS ERROR: !!!   Exception was: Error: Bad method name "Gdk.Display.get_device_state"
    JS ERROR: !!!     lineNumber = '43'
    JS ERROR: !!!     fileName = '/home/ron/gnome-shell/source/gnome-shell/js/ui/environment.js'
    JS ERROR: !!!     stack = '_blockMethod("Gdk.Display.get_device_state","global.get_pointer","gjs's handling of Gdk.ModifierType is broken. See bug 597292.")@/home/ron/gnome-shell/source/gnome-shell/js/ui/environment.js:43
init()@/home/ron/gnome-shell/source/gnome-shell/js/ui/environment.js:92
start()@/home/ron/gnome-shell/source/gnome-shell/js/ui/main.js:91
@<main>:1
'
    JS ERROR: !!!     message = 'Bad method name "Gdk.Display.get_device_state"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Bad method name "Gdk.Display.get_device_state"
ron@ron-desktop2:~/gnome-shell/source/gnome-shell/src$ No value set for `/apps/compiz-1/general/allscreens/options/active_plugins'
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing imgsvg options...done
Initializing imgjpeg options...done
Initializing vpswitch options...done
Initializing move options...done
Initializing resize options...done
Initializing cube options...done
Initializing switcher options...done
Initializing rotate options...done
constraining to 0
constraining to 0
constraining to 0
constraining to 0
ron@ron-desktop2:~/gnome-shell/source/gnome-shell/src$ 

```

then it dumps me back in classic .

I also did a fresh build just now, and I get essentially the same JS errors as above.

---

### Post by Quadunit404 on 2010-12-28
I am guessing that now that GNOME Shell requires Vala 0.11 it's impossible for us Maverick Meerkat users to build GS without installing updated Vala libraries :|

---

### Post by agomonos on 2010-12-28
comment line 91-92 in the file called environment.js as specified in the error. then gnome-shell should start and work properly.

---

### Post by ronacc on 2010-12-28
> **agomonos said:**
> comment line 91-92 in the file called environment.js as specified in the error. then gnome-shell should start and work properly.

that got it thanks .

---

### Post by xtoudi on 2010-12-28
> **Quadunit404 said:**
> I am guessing that now that GNOME Shell requires Vala 0.11 it's impossible for us Maverick Meerkat users to build GS without installing updated Vala libraries :|

And what is the problem with that?? jhubild compiles vala vala-0.11.2 - I have this one on MM.

---

### Post by Sashin on 2010-12-29
"sabdfl: why aren't you using unity?" nice.... :lolflag:

---

### Post by autocrosser on 2010-12-29
Maybe because we think GS is better????  :lolflag:

---

### Post by plun on 2010-12-29
> **autocrosser said:**
> Maybe because we think GS is better????  :lolflag:

Well... ontopic... I sucessfully installed Gnome-Shell from Ricotz ppa and it works..  a mutter-package force-overwrite and some aptitude cleaning an then it was OK.

I have some trouble with Firefox 4 and Gnome-Shell.... it just crashes sometimes :confused:

So back to Gnome Classic.............):P

Unity is just ugly and boring for the moment and Gnome-Shell is just a "clutter"....

This can end in a complete disaster for Ubuntu .....:^o

---

### Post by Harry33 on 2010-12-29
> **plun said:**
> Well... ontopic... I sucessfully installed Gnome-Shell from Ricotz ppa and it works..  a mutter-package force-overwrite and some aptitude cleaning an then it was OK.
...


Plun,
now that you have gnome-settings-daemon_2.91.6.2 and libgnomekbd_2.91.4-1,
are you able to edit theming if you start gnome-classic session and do you still have a themable gdm?

---

### Post by plun on 2010-12-29
> **Harry33 said:**
> Plun,
now that you have gnome-settings-daemon_2.91.6.2 and libgnomekbd_2.91.4-1,
are you able to edit theming if you start gnome-classic session and do you still have a themable gdm?

Nope, GDM just is ugly and I cannot change anything.  Minor problem !

Theming with Gnome Classic works just fine !

With Gnome-Shell I don't know how to change the theme....  also rather ugly..:confused:

---

### Post by Harry33 on 2010-12-29
> **plun said:**
> Nope, GDM just is ugly and I cannot change anything.  Minor problem !
Theming with Gnome Classic works just fine !
With Gnome-Shell I don't know how to change the theme....  also rather ugly..:confused:

Yes right, it seems the gnome-appearance-properties does not work in Gnome-shell anymore.
Last time I tried Gnome-Shell 2.91.3 I could not change anything in any theme, not even in Gnome-Classic when gnome-settings-daemon_2.91.* was installed.
I could only watch the window border named "Simple" and that one sure is ugly.

---

### Post by plun on 2010-12-29
> **Harry33 said:**
> Yes right, it seems the gnome-appearance-properties does not work in Gnome-shell anymore.
Last time I tried Gnome-Shell 2.91.3 I could not change anything in any theme, not even in Gnome-Classic when gnome-settings-daemon_2.91.* was installed.
I could only watch the window border named "Simple" and that one sure is ugly.


Yep.... this is how it looks for me.....

[[IMG]http://i.imgur.com/0BlbPs.jpg[/IMG]](http://imgur.com/0BlbP)

Ugly !!

---

### Post by cariboo on 2010-12-29
I'm using gnome-shell from the rictoz ppa too, I think it is really confused about windows decorations, Chromium uses the Ubuntu light theming, while the rest of the apps use the ugly default theme. I can't change the buttons to the proper side either.

**Note:** I use Sync, to keep my chromium bookmarks and some add-ons the same over all my installs.

---

### Post by Harry33 on 2010-12-30
In fact I have never been able to change the theme in Gnome-Shell. It seems to use the gnome-themes-standard all times.

And after the installation of gnome-settings-daemon_2.91.* the Gnome-Classic did also change into Simple theme only. Not to mention the ugly gdm without a background.

Perhaps it is possible to change this by installing
gnome-control-center_2.91.* (from Gnome3 Team PPA) and
gnome-themes_2.91.* (can be found on Gnome3 Stack PPA)

or perhaps gtk-theme-engine-clearlooks_2.91.* (from ricotz PPA).

---

### Post by augias on 2010-12-30
> **Harry33 said:**
> In fact I have never been able to change the theme in Gnome-Shell. It seems to use the gnome-themes-standard all times.

And after the installation of gnome-settings-daemon_2.91.* the Gnome-Classic did also change into Simple theme only. Not to mention the ugly gdm without a background.

Perhaps it is possible to change this by installing
gnome-control-center_2.91.* (from Gnome3 Team PPA) and
gnome-themes_2.91.* (can be found on Gnome3 Stack PPA)

or perhaps gtk-theme-engine-clearlooks_2.91.* (from ricotz PPA).

Thats really weird, i change themes all the time from the Appearance app. Just go to overview, type "app.." and change my theme whenever. Here's some visual proof I guess.
[http://dl.dropbox.com/u/208391/shell-caps/Workspace%201_001.jpeg]("http://dl.dropbox.com/u/208391/shell-caps/Workspace%201_001.jpeg")

In any case, remember that changing appearances in classic gnome doesn't affect gnome-shell. Different gconf settings...

P.S.: Try opening gconf-editor in gnome-shell, go to /desktop/gnome/shell/windows  and change the "theme value to the name of your theme (Respect upper and lowercase i think).  hth!

---

### Post by Yellow Pasque on 2010-12-30
> **plun said:**
> This can end in a complete disaster for Ubuntu .....:^o

How? GNOME Classic/2.32 is stable and familiar to previous Ubuntu users. I'm sure Unity will come around in good time (and hopefully, most users will have more capable graphics drivers by then). GS should eventually be a built-in/out-of-the-box option too, at least by the time that GNOME classic is deprecated.
(And that's just GNOME; there are plenty of other DE's too).

---

### Post by ronacc on 2010-12-30
> **Temüjin said:**
> How? GNOME Classic/2.32 is stable and familiar to previous Ubuntu users. I'm sure Unity will come around in good time (and hopefully, most users will have more capable graphics drivers by then). GS should eventually be a built-in/out-of-the-box option too, at least by the time that GNOME classic is deprecated.
(And that's just GNOME; there are plenty of other DE's too).

There are some of us who are not all that fond of either GS or Unity , given the choice of 2 evils I will pick GS ,but I honestly do not find it anywhere near as useful in my normal daily tasks as the classic desktop .

---

### Post by cariboo on 2010-12-30
Unless someone come up with a distro that forks the gnome two panel interface, eventually you're going to have to decide whether to use gnome-shell, unity, or kde.

That being said, I'm running an Ubuntu/Debian desktop using the gnome 3 build ppa and gnome-shell from the rictoz ppa.. There are a lot of things that don't work yet, Appearances being one of them

---

### Post by davepoth on 2010-12-30
> **cariboo907 said:**
> Unless someone come up with a distro that forks the gnome two panel interface, eventually you're going to have to decide whether to use gnome-shell, unity, or kde.

That being said, I'm running an Ubuntu/Debian desktop using the gnome 3 build ppa and gnome-shell from the rictoz ppa.. There are a lot of things that don't work yet, Appearances being one of them

We're still a long way from panel being deprecated, I think. If the need is there for a fork someone will do it I'm sure.

---

### Post by ronacc on 2010-12-30
I'm running natty classic desktop + GS local compiled , as I said above , when the choice comes I'll go with GS unity is a complete no starter for me but I am also looking for a soft place to land when the classic desktop disappears .

---

### Post by Yellow Pasque on 2010-12-30
> **ronacc said:**
> I'm running natty classic desktop + GS local compiled , as I said above , when the choice comes I'll go with GS unity is a complete no starter for me but I am also looking for a soft place to land when the classic desktop disappears .
Xfce/Xubuntu might be more to your liking then.

---

### Post by ronacc on 2010-12-30
well I have a bit of time to decide , I just did a complete rework of my "work" system , new box and all ( maverick installed there ) and won't do that again for another 2 years and thats the only one where the interface is important .

---

### Post by autocrosser on 2010-12-31
Well my friend---I think that I've come to a crossing in the road & Unity is not for me...I've installed Mint Debian 64bit & am exploring "options".......I would be quite sure that Debian will go with GS "sooner or later", but will keep with Classic Gnome for quite a while.  I have not severed my link with Ubuntu, but the number of ties has decreased quite a bit.

---

### Post by VMC on 2010-12-31
> **autocrosser said:**
> Well my friend---I think that I've come to a crossing in the road & Unity is not for me...I've installed Mint Debian 64bit & am exploring "options".......I would be quite sure that Debian will go with GS "sooner or later", but will keep with Classic Gnome for quite a while.  I have not severed my link with Ubuntu, but the number of ties has decreased quite a bit.

I've done exactly the same thing. Running Mint9 64bit and love it. I too wonder what will Mint use in place of its menu when the time comes to replace Gnome.

Although, the last ISO install of Unity has improved a lot. It's a work in progress. I could never get GS to run right, but that was early on.

---

### Post by Quadunit404 on 2010-12-31
> **xtoudi said:**
> And what is the problem with that?? jhubild compiles vala vala-0.11.2 - I have this one on MM.

I was asking that because earlier I saw an error related to Vala during the build process of something in this thread.

---

### Post by Harry33 on 2010-12-31
> **augias said:**
> Thats really weird, i change themes all the time from the Appearance app. Just go to overview, type "app.." and change my theme whenever. 

In any case, remember that changing appearances in classic gnome doesn't affect gnome-shell. Different gconf settings...


Do you have Natty-alfa1 installed here with GS?
What version of gnome-settings-daemon are you using?
What version of gnome-themes are you using?
What version of gnome-control-center are you using?
How does your logging screen (gdm) look like (theming, background)?

And finally, in Gnome-Classic, can you change themes (like window controls and borders)?

---

### Post by plun on 2010-12-31
Well, the gconf-editor works  !!  

/desktop/gnome/shell/windows/theme

PoC
[[IMG]http://i.imgur.com/7neYns.jpg[/IMG]](http://imgur.com/7neYn)

---

### Post by Harry33 on 2010-12-31
> **plun said:**
> Well, the gconf-editor works  !!  

/desktop/gnome/shell/windows/theme

PoC
[[IMG]http://i.imgur.com/7neYns.jpg[/IMG]](http://imgur.com/7neYn)

Plun,
Are you also able to edit themes in Gnome-Classic session?
Do you have a background in login screen (gdm)?

---

### Post by plun on 2010-12-31
> **Harry33 said:**
> Plun,
Are you also able to edit themes in Gnome-Classic session?
Do you have a background in login screen (gdm)?

I have no trouble with themes in Gnome Classic, GDM is without background (minor problem as I earlier wrote)

I can change themes in Gnome-Shell with gconf-editor.

The major problem for me is that Minefield somehow crashes GS after a while... trying to trace it.


I can see this in the terminal:

```
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:5921): GdmUser-WARNING **: Unable to load CK history: no seat-id found
Window manager warning: Log level 8: meta_window_raise: assertion `!window->override_redirect' failed
Shell killed with signal 11

```

---

### Post by plun on 2010-12-31
Spotify (paying Linux version) also crashes GS.....

```
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1800008 (Spotify)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
connecting notifications
Window manager warning: Log level 16: NOTE: Not using GLX TFP!

connecting notifications
connecting notifications
Window manager warning: Log level 16: STACK_OP_ADD: window 0x1800008 already in stack
Window manager warning: Log level 16: STACK_OP_ADD: window 0x1800008 already in stack
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1800026 (Spotify)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
15:32:00.628 I [ap:1387] Connecting to AP B1.spotify.com:4070
15:32:00.837 I [ap:937] Connected to AP: 78.31.8.42:4070
15:32:01.554 I [gui-model:2136] Login Code: 0
15:32:01.700 I [upnp:515] 192.168.1.254: got external ip 0x55E221B7
15:32:02.017 E [ap:3559] ChannelError(1, 1, playlist)
15:32:02.017 E [ap:3559] ChannelError(6, 1, playlist-info)
** (<unknown>:9563): DEBUG: NP_Initialize
** (<unknown>:9563): DEBUG: NP_Initialize succeeded
** (<unknown>:9563): DEBUG: NP_Initialize
** (<unknown>:9563): DEBUG: NP_Initialize succeeded
** (<unknown>:9563): DEBUG: NP_Initialize
** (<unknown>:9563): DEBUG: NP_Initialize succeeded
** (<unknown>:9563): DEBUG: NP_Initialize
** (<unknown>:9563): DEBUG: NP_Initialize succeeded

(<unknown>:9563): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(<unknown>:9563): Gdk-WARNING **: /build/buildd/gtk+2.0-2.23.3.is.2.23.2/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window
15:32:03.876 I [upnp:463] 192.168.1.254: mapping add ok
15:32:04.980 I [upnp:489] 192.168.1.254: Port 35366 mapped OK
15:32:12.806 E [ap:3559] ChannelError(0, 1, playlist)
15:32:14.184 I [main.cpp:603] Using PulseAudio
Shell killed with signal 11

```

A minimize and a GS restart and I am up and running......

---

### Post by plun on 2010-12-31
Question !

What is the keyboard shortcut for Activities and the serach for apps ?

Rather annoying to first click at the left and then go to the right side and search.....  must be a rather heavy HIG bug.. !!! IMHO

---

### Post by ronacc on 2010-12-31
will there be a way to move the hotspot for Activities ? top left corner is very annoying to me since that is where I put my close button on windows and on a maximized window it is all too easy to overshoot and end up in overview .

---

### Post by plun on 2010-12-31
> **ronacc said:**
> will there be a way to move the hotspot for Activities ? top left corner is very annoying to me since that is where I put my close button on windows and on a maximized window it is all too easy to overshoot and end up in overview .

Well... I also find it annoying..... and activities and search for an app is rather terrible.

"HIG" is this 
[http://en.wikipedia.org/wiki/Human_interface_guidelines](http://en.wikipedia.org/wiki/Human_interface_guidelines)

But somewhere in the Gnome-jungle its probably possible to file a bug ?

---

### Post by cariboo on 2010-12-31
> **plun said:**
> I have no trouble with themes in Gnome Classic, GDM is without background (minor problem as I earlier wrote)

I can change themes in Gnome-Shell with gconf-editor.

The major problem for me is that Minefield somehow crashes GS after a while... trying to trace it.


I can see this in the terminal:

```
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:5921): GdmUser-WARNING **: Unable to load CK history: no seat-id found
Window manager warning: Log level 8: meta_window_raise: assertion `!window->override_redirect' failed
Shell killed with signal 11

```

I see the same thing on my system, using Chromium all I have to do is open up the compiz forums in another tab, and I get an instant crash. Using firefox, it is random web sites.

---

### Post by plun on 2010-12-31
> **cariboo907 said:**
> I see the same thing on my system, using Chromium all I have to do is open up the compiz forums in another tab, and I get an instant crash. Using firefox, it is random web sites.

Well... it is rather strange it can works for a while and suddenly just crash.

It must be a better way to backtrace GS crashes ??  the terminal is just randomly outputs.

---

### Post by karmila on 2011-01-04
Hi All,

I'm trying to build gnome-shell on my maverick and now I get this error following with several options, which one should I pick?


> collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/ari/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/ari/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/ari/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ari/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ari/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/33]

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

:confused:
Thanks in advance.

---

### Post by davideotape on 2011-01-04
Had a quick search of this thread and it seems no-one has come up with this yet:

```
  GISCAN Gtk-3.0.gir
./.libs/libgtk-3.0.so: undefined reference to `gdk_device_get_window_at_position'
./.libs/libgtk-3.0.so: undefined reference to `gdk_device_get_position'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspectW4WDwf/Gtk-3.0', '-export-dynamic', '-L.', 'libgtk-3.0.la', '-pthread', '-L/home/david/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspectW4WDwf/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/33]
```

Anyone got any ideas?

---

### Post by gacb on 2011-01-04
I have my day job, which requires me to use multiple applications and I also wrote and continually edit my own website as well as composing and arranging music in my spare time.

As such, I use upwards of 20 applications on any given day; far too many to fit in the Unity panel and going to the master applications folder is far slower than opening them in the classic Gnome.

I also need to encrypt sensitive files/folders and Cryptkeeper is a panel applet.

I'll continue to use and test Natty/Unity, but can't do any serious work in Unity. The main reason I switched from Windows was speed, and Unity slows me down.

---

### Post by cariboo on 2011-01-04
I install docky, and then put any apps that don't fit in the panel there.

---

### Post by Merk42 on 2011-01-04
> **davideotape said:**
> Had a quick search of this thread and it seems no-one has come up with this yet:

```
  GISCAN Gtk-3.0.gir
./.libs/libgtk-3.0.so: undefined reference to `gdk_device_get_window_at_position'
./.libs/libgtk-3.0.so: undefined reference to `gdk_device_get_position'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspectW4WDwf/Gtk-3.0', '-export-dynamic', '-L.', 'libgtk-3.0.la', '-pthread', '-L/home/david/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspectW4WDwf/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/33]
```

Anyone got any ideas?

The first two lines look like the **undefined reference errors** I mention in the first post.
```
rm ~/gnome-shell/install/*.la && sudo rm -rf /usr/lib*/*.la
```Then jhbuild build
If it still doesn't work, delete the ~/gnome-shell folder and try again



> **gacb said:**
> I have my day job, which requires me to use multiple applications and I also wrote and continually edit my own website as well as composing and arranging music in my spare time.

As such, I use upwards of 20 applications on any given day; far too many to fit in the Unity panel and going to the master applications folder is far slower than opening them in the classic Gnome.

I also need to encrypt sensitive files/folders and Cryptkeeper is a panel applet.

I'll continue to use and test Natty/Unity, but can't do any serious work in Unity. The main reason I switched from Windows was speed, and Unity slows me down.
I've not tried it, but I'm pretty sure you can fit 20+ applications in Unity, the icons will just turn to the side to make room for others.
Though this thread is about GNOME Shell, not Unity.

---

### Post by Yellow Pasque on 2011-01-04
Is there a good non-Ubuntu (preferably Debian-based) distro to test vanilla GNOME3? I've got plenty of spare hard disk space and I'm going to try out Linux Mint. It's really ironic that Unity may fracture a huge userbase (if only temporarily).

---

### Post by autocrosser on 2011-01-04
I'm still following the Gnome-Shell threads here, but I've moved to Linux Mint Debian Edition. As soon as Debian finals Squeeze, it will be a nice rolling distro (and you can use sid as your source if you want!!! 32bit is in flux right now, but 64bit is working very well)---I'm starting a GS thread there (will be up by this weekend) & there is interest in GS at Mint. Come by & say Hi!!!!

Link: [http://forums.linuxmint.com/viewforum.php?f=141](http://forums.linuxmint.com/viewforum.php?f=141)

---

### Post by cariboo on 2011-01-04
I did a cli install from the alternate install CD then added the gnome-desktop-environment from the repositories. This gave me a desktop with Debian branding, and very little if anything from Ubuntu.  I then added the [gnome 3 team ppa]("https://launchpad.net/~gnome3-team/+archive/gnome3").

---

### Post by Harry33 on 2011-01-04
> **Temüjin said:**
> Is there a good non-Ubuntu (preferably Debian-based) distro to test vanilla GNOME3? I've got plenty of spare hard disk space and I'm going to try out Linux Mint. It's really ironic that Unity may fracture a huge userbase (if only temporarily).

Well nothing wrong with Ubuntu actually.
You can uninstall package ubuntu-desktop and then go on uninstalling unity with all its dependencies including compiz, if you like.
Gnome3 is available here:
Gnome3 Team:
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
and
Gnome-Shell here:
[https://launchpad.net/~ricotz/+archive/testing/+packages](https://launchpad.net/~ricotz/+archive/testing/+packages)

---

### Post by Yellow Pasque on 2011-01-04
> **Harry33 said:**
> Well nothing wrong with Ubuntu actually.
You can uninstall package ubuntu-desktop and then go on uninstalling unity with all its dependencies including compiz, if you like.
Gnome3 is available here:
Gnome3 Team:
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
and
Gnome-Shell here:
[https://launchpad.net/~ricotz/+archive/testing/+packages](https://launchpad.net/~ricotz/+archive/testing/+packages)
I know, but it is more cruft to take out if I want to try vanilla GS.

---

### Post by jerrylamos on 2011-01-05
> **gacb said:**
> I have my day job, which requires me to use multiple applications and I also wrote and continually edit my own website as well as composing and arranging music in my spare time.

As such, I use upwards of 20 applications on any given day; far too many to fit in the Unity panel and going to the master applications folder is far slower than opening them in the classic Gnome.

I also need to encrypt sensitive files/folders and Cryptkeeper is a panel applet.

I'll continue to use and test Natty/Unity, but can't do any serious work in Unity. The main reason I switched from Windows was speed, and Unity slows me down.

Yea, Verily!

I fill my screen with applications and "Unity" uses up valuable real estate with less function than Maverick.  I'm told I can "autohide" Unity, then what use is it?

O.K., have "Unity" for a "Lookie Feelie" for "Newbies".  When people graduate from "Newbie" then have the real Ubuntu with more function with less keystrokes and less mouse pointer and less windows.  Just the opposite of "Windows".

Jerry

---

### Post by Quadunit404 on 2011-01-05
Excuse me, anybody know what's going on here?

```
*** Configuring gdk-pixbuf *** [7/33]
./autogen.sh --prefix /home/tom/gnome-shell/install --libdir '/home/tom/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/tom/gnome-shell/install --libdir '/home/tom/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [7/33]

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

EDIT: Never mind, turns out I had an outdated gnome-shell-build-setup.sh and didn't know new dependencies appeared. gdk-pixbuf built fine after getting a new GSBS.sh.

EDIT AGAIN: Now I got this error:

```
/home/tom/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_source_get_time'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/tom/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_list_free_full'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_get_environ'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/tom/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_get_monotonic_time'
/home/tom/gnome-shell/install/lib64/libgdk-3.0.so: undefined reference to `g_slist_free_full'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/33]

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

### Post by Merk42 on 2011-01-05
> **Quadunit404 said:**
> Excuse me, anybody know what's going on here?

```
*** Configuring gdk-pixbuf *** [7/33]
./autogen.sh --prefix /home/tom/gnome-shell/install --libdir '/home/tom/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/tom/gnome-shell/install --libdir '/home/tom/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [7/33]

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

EDIT: Never mind, turns out I had an outdated gnome-shell-build-setup.sh and didn't know new dependencies appeared. gdk-pixbuf built fine after getting a new GSBS.sh.

EDIT AGAIN: Now I got this error:

```
/home/tom/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_source_get_time'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/tom/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_list_free_full'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_get_environ'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/tom/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_get_monotonic_time'
/home/tom/gnome-shell/install/lib64/libgdk-3.0.so: undefined reference to `g_slist_free_full'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/33]

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

Undefined reference, check the first post

---

### Post by Quadunit404 on 2011-01-05
I'll try that tomorrow. Thanks.

---

### Post by cangzhang on 2011-01-06
what should i do ?

*** Checking out gdk-pixbuf *** [7/33]
*** Configuring gdk-pixbuf *** [7/33]
./autogen.sh --prefix /home/cangzhang/gnome-shell/install --libdir '/home/cangzhang/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
/bin/sh: ./autogen.sh: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/cangzhang/gnome-shell/install --libdir '/home/cangzhang/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [7/33]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"

---

### Post by augias on 2011-01-06
> **cangzhang said:**
> what should i do ?

*** Checking out gdk-pixbuf *** [7/33]
*** Configuring gdk-pixbuf *** [7/33]
./autogen.sh --prefix /home/cangzhang/gnome-shell/install --libdir '/home/cangzhang/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
/bin/sh: ./autogen.sh: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/cangzhang/gnome-shell/install --libdir '/home/cangzhang/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [7/33]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"

Choice 6 is your friend.

---

### Post by Quadunit404 on 2011-01-06
Actually, I got that error before, and it was resolved by obtaining a new copy of gnome-shell-build-setup.sh because new dependencies appeared for GNOME Shell and therefore GSBS.sh has to be updated to know these new dependencies.

---

### Post by wacked_up on 2011-01-06
I'm on maverick and keep getting the error when building gnome-shell during the configure phase that mutter wasn't compiled against GTK+3.0.
Is there a way to fix that without breaking my normal install (Gnome2 + compiz)?

Thanks in advance.

---

### Post by Quadunit404 on 2011-01-06
Finally built GNOME Shell successfully. Now when I actually try to run it, I get this error:

```
tom@tom-laptop-linux:~$ ~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
mutter: symbol lookup error: /home/tom/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
tom@tom-laptop-linux:~$ Cannot register the panel shell: there is already one running.

```

Anybody know what's wrong?

---

### Post by Finalfantasykid on 2011-01-06
^I've been getting that error for the past couple of days.  It makes me think that when it does finally run again, there will be some nice changes :)

---

### Post by Merk42 on 2011-01-06
It was in the mailing list:
Basically something was removed from GTK+3 that libcanberra used
so just delete ~/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so and you'll be fine.

---

### Post by Finalfantasykid on 2011-01-06
Thanks that worked, but now I am getting a warning saying that the file is missing

Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

---

### Post by Quadunit404 on 2011-01-07
Okay, just tried out GNOME Shell and it freaked out whenever I tried opening up the Activities view and moving the mouse... gonna try rebuilding.

EDIT: Rebuilding didn't solve it. Here's the error:

```
(mutter:23138): Clutter-WARNING **: The required ID of 262915 does not refer to an existing actor; this usually implies that the pick() of an actor is not correctly implemented or that there is an error in the glReadPixels() implementation of the GL driver.

```

---

### Post by moore.bryan on 2011-01-08
Is anyone else getting an error when using "My Account," like this:
```

Failed to contact the accounts service
Please make sure that the AccountService is installed and enabled.

```
I have no idea what package it's looking for... thanks, in-advance!

---

### Post by Finalfantasykid on 2011-01-08
^I've been getting that message for a long time now.  I'm assuming that it is just not done yet.

---

### Post by moore.bryan on 2011-01-08
> **Finalfantasykid said:**
> ^I've been getting that message for a long time now.  I'm assuming that it is just not done yet.

That's what I figured, just wanted to find-out if I was the only one. Now there's--at least--two of us on this island. :-)

On another note, has anyone else noticed their time/date occasionally disappear and reappear?

---

### Post by moore.bryan on 2011-01-09
I now seem to have another issue. Even though I have GNOME Shell set to load at startup with the "--replace" option, it won't start unless I manually start it in a terminal.

Any ideas?

EDIT:
Perhaps I wrote too soon. Things now seem to work fine; strange. I wonder what could have been the issue.

---

### Post by ratcheer on 2011-01-11
I am sick and tired of Unity, so I installed the latest Gnome shell from the ricotz testing ppa, this morning. I also installed gnome3-session.

 ```
 Package: gnome-shell                     
 New: yes 
State: installed 
Automatically installed: no 
Version: 2.91.4+git20110108.a538027f-0ubuntu1~11.04~ricotz0    

Package: gnome3-session 
New: yes 
State: installed 
Automatically installed: no 
Version: 2.32.1-0ubuntu9 
```

If I try to login in to Gnome3 desktop, after a few seconds it just gives me another login dialog.  If I login to the Classic desktop, it works but my windows and stuff look like some kind of old MS Win NT stuff.  Can I get Gnome shell to work?   Can I make the Classic desktop look right? Should I just uninstall Gnome3 and forget about it?    

Tim

---

### Post by cariboo on 2011-01-11
Gnome-shell from the rictoz ppa seems to be a bit broken. I can't get it to start using a Gnome 3 session, but it does start and run if I type:

```
gnome-shell --replace in a terminal
```

in a terminal

---

### Post by ratcheer on 2011-01-11
> **cariboo907 said:**
> Gnome-shell from the rictoz ppa seems to be a bit broken. I can't get it to start using a Gnome 3 session, but it does start and run if I type:

```
gnome-shell --replace in a terminal
```in a terminal

Thanks, I will try that.

Tim

---

### Post by ratcheer on 2011-01-11
No luck. When I did that, I lost everything on the desktop except the terminal window I ran it from.

Tim

---

### Post by cariboo on 2011-01-11
I get that when gnome-shell crashes, I usually have to log out and back in again to get gnome-shell to work. Running it from a terminal gives a whole window full of errors, but for most things it doesn't seem to have much affect.

---

### Post by ratcheer on 2011-01-11
> **cariboo907 said:**
> I get that when gnome-shell crashes, I usually have to log out and back in again to get gnome-shell to work. Running it from a terminal gives a whole window full of errors, but for most things it doesn't seem to have much affect.

I'm not sure what you mean. Where do I run the command if not from a terminal? In Unity, if I run "compiz --replace" from a terminal, it works just fine.

Tim

---

### Post by cariboo on 2011-01-11
On my setup, gnome-shell isn't very stable, it crashes if you look at it sideways, I did mean starting it from a terminal. I'm running a cli setup, with the gnome-desktop-environment from the repositories, and the [gnome-3-team ]("http://https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds")repositories enabled.

Just checking the url for the gnome-team ppa caused gnome-shell to crash. :)

---

### Post by plun on 2011-01-11
> **cariboo907 said:**
> On my setup, gnome-shell isn't very stable, it crashes if you look at it sideways, I did mean starting it from a terminal. I'm running a cli setup, with the gnome-desktop-environment from the repositories, and the [gnome-3-team ]("http://https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds")repositories enabled.

Just checking the url for the gnome-team ppa caused gnome-shell to crash. :)

The Gnome3-team ppa is the most unstable software I have tested.... so I ppa-purged it this weekend and GS works again (only with ricotz ppa)

But.....  unstable as earlier... Minefield and Spotify just kills it randomly  !

No idea how to trace these crashes....

EDIT It is much more stable this evening....  came home and I have now been running GS for at least 30 minutes without any crash...

---

### Post by ratcheer on 2011-01-11
Ok, thanks. I fresh-reinstalled Natty from the Jan 8 alt iso just three days ago. It was fully updated before I added the ricotz ppa and installed gnome-shell and gnome3-session, this morning. Nothing else strange has been added to it.

So, I suppose I just need to purge the new stuff and see if I can get back to normal. If not, I can do another fresh install of Natty.

Tim

---

### Post by cariboo on 2011-01-11
> **plun said:**
> The Gnome3-team ppa is the most unstable software I have tested.... so I ppa-purged it this weekend and GS works again (only with ricotz ppa)

But.....  unstable as earlier... Minefield and Spotify just kills it randomly  !

No idea how to trace these crashes....

EDIT It is much more stable this evening....  came home and I have now been running GS for at least 30 minutes without any crash...

My setup when not using gnome-shell is just as stable as Natty, it's only gnome-shell that crashes often. I should also mention that I have Docky2 installed, and it's stability has improved a large amount over the last couple of updates.

---

### Post by moore.bryan on 2011-01-13
Building on my ancient g4 mac running Debian rolling succeeds, but running hits a snag:
```


bryan@mac:~/gnome-shell/install/bin$ ./gnome-shell --replace
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Window manager error: Unable to initialize Clutter.
bryan@mac:~/gnome-shell/install/bin$ Cannot register the panel shell: there is already one running.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

```
The issue with canberra's problem should be solved by deleting the one module, but I did that and it still throws this error. Huh?

---

### Post by Yellow Pasque on 2011-01-13
> **moore.bryan said:**
> Building on my ancient g4 mac running Debian rolling succeeds, but running hits a snag:
```


bryan@mac:~/gnome-shell/install/bin$ ./gnome-shell --replace
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Window manager error: Unable to initialize Clutter.
bryan@mac:~/gnome-shell/install/bin$ Cannot register the panel shell: there is already one running.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

```
The issue with canberra's problem should be solved by deleting the one module, but I did that and it still throws this error. Huh?
Maybe you should install libcanberra-gtk-module (and -dev package)?

---

### Post by moore.bryan on 2011-01-13
Thanks, Temüjin, I'll try that!

EDIT:
Well, no luck. When I try to install libcanberra-gtk-module, it's already installed. After much thinking, I realized I needed libcanberra-gtk3-module and libcanberra-gtk3-dev; however, those are not installable because they break pretty much everything on the system. Even using "sudo apt-get -t experimental install..." doesn't help the conflict.

Any other ideas, folks?

---

### Post by Tompalaz on 2011-01-14
I get this when I try to run GS
```
gnome-shell --replace
```
> tomas@htpc:~/gnome-shell/source/gnome-shell/src$ /usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
No value set for `/apps/compiz-1/general/allscreens/options/active_plugins'



---

### Post by Tompalaz on 2011-01-14
sorry, dubble post.

---

### Post by augias on 2011-01-14
> **moore.bryan said:**
> Thanks, Temüjin, I'll try that!

EDIT:
Well, no luck. When I try to install libcanberra-gtk-module, it's already installed. After much thinking, I realized I needed libcanberra-gtk3-module and libcanberra-gtk3-dev; however, those are not installable because they break pretty much everything on the system. Even using "sudo apt-get -t experimental install..." doesn't help the conflict.

Any other ideas, folks?

are you 100% sure you did this:
```
rm ~/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so
```

I'm asking the obvious question because you didn't mention exactly what command you used to get rid of the module. If That is what you did, then something else must be wrong, because that command solves it for everybody.

---

### Post by augias on 2011-01-14
> **Tompalaz said:**
> I get this when I try to run GS
```
gnome-shell --replace
```

That's some output from compiz, and it has nothing to do with gnome-shell. Please paste the output from the very start of issuing your gnome-shell --replace command.

---

### Post by Tompalaz on 2011-01-14
> **augias said:**
> That's some output from compiz, and it has nothing to do with gnome-shell. Please paste the output from the very start of issuing your gnome-shell --replace command.

Tried to rebuild GS but it wouldn't work. Installed from ricotz ppa.
Won't work though.

> tomas@htpc:~$ gnome-shell --replace
    JS ERROR: !!!   Failed to convert exception string to UTF-8
    JS ERROR: !!!   Failed to convert exception string to UTF-8
Window manager warning: Log level 32: Execution of main.js threw exception: JS_EvaluateScript() failed but no exception message?
tomas@htpc:~$ No value set for `/apps/compiz-1/general/allscreens/options/active_plugins'
[...]


---

### Post by plun on 2011-01-14
> **Tompalaz said:**
> Tried to rebuild GS but it wouldn't work. Installed from ricotz ppa.
Won't work though.

Ricotz ppa works for me.....  I have not installed the Gnome3 PPA, purged it last weekend !

This is what I get during a GS start

```
plun@plun-laptop:~$ gnome-shell --replace &
[1] 12793
plun@plun-laptop:~$       JS LOG: GNOME Shell started at Fri Jan 14 2011 23:23:23 GMT+0100 (CET)
plun@plun-laptop:~$ `menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:12832): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:12832): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:12832): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:12832): Gtk-WARNING **: Failed to load type module: (null)

      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:12817): GdmUser-WARNING **: Unable to load CK history: no seat-id found
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:12832): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:12832): Gtk-WARNING **: Failed to load type module: (null)



```


But crashes randomly.... touching Minefield and Spotify.... no idea howto trace it.

---

### Post by keypox on 2011-01-14
I get this error 

```
configure: error: Vala 0.11.4 not found.
*** Error during phase configure of dconf: ########## Error running ./autogen.sh --prefix /home/keypo/gnome-shell/install --libdir '/home/keypo/gnome-shell/install/lib' --disable-editor --disable-static --disable-gtk-doc  *** [19/33]
```

---

### Post by dext on 2011-01-14
if anyone wants to know, Gnome-shell akka Gnome3 is now Default in F15 so there's nomore dependency with Desktop-Effects now. apart from that i rather like its progress.

---

### Post by Harry33 on 2011-01-15
> **dext said:**
> if anyone wants to know, Gnome-shell akka Gnome3 is now Default in F15 so there's nomore dependency with Desktop-Effects now. apart from that i rather like its progress.

Just that
Gnome-shell is not Gnome3.
Just like Gnome-Panel or Unity are not Gnome2.

Gnome2 and Gnome3 are Desktop Environments.
Gnome-shell, Gnome-Panel and Unity are shells, which operate above the Gnome Desktop Environment (DE).

Gnome2 is a DE based on GTK+2.0 (published).
Gnome3 is a DE based on GTK+3.0 (under development).

---

### Post by dext on 2011-01-15
as i think Discussed before here, Unity is more Technically a compiz plugin  Gnome-shell is Gnome3 . you can have your opinion  and i'll have mine

---

### Post by Harry33 on 2011-01-15
> **dext said:**
> as i think Discussed before here, Unity is more Technically a compiz plugin  Gnome-shell is Gnome3 . you can have your opinion  and i'll have mine

Yes yes, look.
You mean different thing with a word Gnome3 as I do. No problem here.
You probably mean Gnome3-session.
Gnome3-session starts Gnome3 with a Gnome-shell session.
But when ready Gnome3 may also be started with Unity-session (at least in Ubuntu) and perhaps with Gnome-Panel session too (when gnome-panel has been ported to GTK+3.0).

---

### Post by njined on 2011-01-15
@keypox
simply go to ~/gnome-shell/source/dconf open configure file, search for vala and replace the 0.11.4 entry with 0.11.2

---

### Post by xtoudi on 2011-01-15
Or compile once again. vala-0.11.4 already added.

---

### Post by Quadunit404 on 2011-01-15
Rebuilding. Hopefully the GNOME Devs have fixed GS under a NVIDIA GT 330M, because when Natty comes out I'ma switching to GNOME Shell and if it still freaks out whenever I move the mouse over the panel or in the Activities view, then I don't know what I'll use beyond GNOME 2 again :|

EDIT: Nope, still looks like this:

[[IMG]http://i563.photobucket.com/albums/ss76/Quadunit404/th_IamprettysureIwouldntwantGStolooklikethis.png[/IMG]](http://i563.photobucket.com/albums/ss76/Quadunit404/IamprettysureIwouldntwantGStolooklikethis.png)

---

### Post by bruce89 on 2011-01-15
> **Harry33 said:**
> Just that
Gnome-shell is not Gnome3.
Just like Gnome-Panel or Unity are not Gnome2.

Gnome2 and Gnome3 are Desktop Environments.
Gnome-shell, Gnome-Panel and Unity are shells, which operate above the Gnome Desktop Environment (DE).

Gnome2 is a DE based on GTK+2.0 (published).
Gnome3 is a DE based on GTK+3.0 (under development).

> **dext said:**
> as i think Discussed before here, Unity is more Technically a compiz plugin  Gnome-shell is Gnome3 . you can have your opinion  and i'll have mine

To be technical (which I like being), gnome-shell is a core GNOME 3 module. gnome-panel is as well, but I believe it's currently broken.

Also, gnome-shell technically is a Mutter plugin.

---

### Post by bruce89 on 2011-01-15
So good, I posted it twice

---

### Post by Quadunit404 on 2011-01-15
Rebuilding yet again. Got this error again. I think that removing all the .la files in ~/gnome-shell/install/lib64 have something to do with the glitchiness I'm experiencing...

```
/home/tom/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_source_get_time'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/tom/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_list_free_full'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_get_environ'
/home/tom/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/tom/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_get_monotonic_time'
/home/tom/gnome-shell/install/lib64/libgdk-3.0.so: undefined reference to `g_slist_free_full'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/33]
```

---

### Post by keypox on 2011-01-15
> **njined said:**
> @keypox
simply go to ~/gnome-shell/source/dconf open configure file, search for vala and replace the 0.11.4 entry with 0.11.2

thanks

> **xtoudi said:**
> Or compile once again. vala-0.11.4 already added.

and thanks 

Will recompile when i get a chance, takes a while...  where is vala added is it just via update?

---

### Post by NightwishFan on 2011-01-15
> **dext said:**
> as i think Discussed before here, Unity is more Technically a compiz plugin  Gnome-shell is Gnome3 . you can have your opinion  and i'll have mine

The gnome shell is technically a mutter plugin. We can do this all day.. :rolleyes:

---

### Post by Tompalaz on 2011-01-16
Anyone else have problems to build gnome-settings-daemon?
I run 64bit maverick.

> Making all in a11y-keyboard
make[3]: Entering directory `/home/tomas/gnome-shell/source/gnome-settings-daemon/plugins/a11y-keyboard'
  CC     liba11y_keyboard_la-gsd-a11y-keyboard-plugin.lo
  CC     liba11y_keyboard_la-gsd-a11y-keyboard-manager.lo
  CC     liba11y_keyboard_la-gsd-a11y-preferences-dialog.lo
  CCLD   liba11y-keyboard.la
/bin/sed: can't read /home/tomas/gnome-shell/install/lib64/libgio-2.0.la: No such file or directory
libtool: link: `/home/tomas/gnome-shell/install/lib64/libgio-2.0.la' is not a valid libtool archive
make[3]: *** [liba11y-keyboard.la] Error 1
make[3]: Leaving directory `/home/tomas/gnome-shell/source/gnome-settings-daemon/plugins/a11y-keyboard'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tomas/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tomas/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/33]

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

Edit: found this, maybe it will works better now.
[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)
Edit2: no go there :(

Edit3: Finally it built fine. I get this error though:
> tomas@seedbox:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
mutter: symbol lookup error: /home/tomas/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
tomas@seedbox:~/gnome-shell/source/gnome-shell/src$ Cannot register the panel shell: there is already one running.

---

### Post by moore.bryan on 2011-01-16
> **augias said:**
> are you 100% sure you did this:
```
rm ~/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so
```
Confirmed

[quote=augias]I'm asking the obvious question because you didn't mention exactly what command you used to get rid of the module. If That is what you did, then something else must be wrong, because that command solves it for everybody.[/QUOTE]
No worries... I'd rather have you ask and me clarify than for us to sit around forever trying to figure something out.

I'm wondering if this is an issue since it's on my PPC iMac?

---

### Post by keypox on 2011-01-16
Finally got build success, but when running it i get 

```

Cannot register the panel shell: there is already one running.
```

---

### Post by augias on 2011-01-16
> **keypox said:**
> Finally got build success, but when running it i get 

```

Cannot register the panel shell: there is already one running.
```

That error message is about gnome-panel, nothing to do with gnome-shell. Look at the complete output from the moment you enter the shell --replace command. 

And before you post the error message, compare to some of the ones from the previous three pages to this thread, it might already be addressed there and you can sort yourself out much faster than waiting for a reply. :)

---

### Post by Tompalaz on 2011-01-16
> **keypox said:**
> Finally got build success, but when running it i get 

```

Cannot register the panel shell: there is already one running.
```

Had the same problem.
My entire error message:
> tomas@seedbox:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
mutter: symbol lookup error: /home/tomas/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
tomas@seedbox:~/gnome-shell/source/gnome-shell/src$ Cannot register the panel shell: there is already one running. 

I fixed it with:
```
rm ~/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so

```

For 32bit systems it's:
```
rm ~/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so
```

BTW, any tip for a good GTK theme to use with GS?

---

### Post by keypox on 2011-01-16
> **Merk42 said:**
> It was in the mailing list:
Basically something was removed from GTK+3 that libcanberra used
so just delete ~/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so and you'll be fine.

this fixed it for me, though was in /install/lib/   not lib64 

Im really liking gnome shell now.

---

### Post by moore.bryan on 2011-01-18
Strange new wrinkle:
After rebuilding yesterday, I can't seem to get GS to run at start. I've put a reference to "~/gnome-shell/install/bin/gnome-shell --restart" in my Startup Applications, but that gives me a blank desktop; running that *same* command in a term launches everything fine, though.

Any ideas?

---

### Post by Tompalaz on 2011-01-18
GS won't start for me either. Started yesterday after rebuilding.

I think it's this update that killed it:
[http://git.gnome.org/browse/gnome-shell/commit/?id=f91138d0a2fb1301a802d58db70587d2bfd5f2aa](http://git.gnome.org/browse/gnome-shell/commit/?id=f91138d0a2fb1301a802d58db70587d2bfd5f2aa)

> tomas@seedbox:~$ ./gnome-shell/source/gnome-shell/src/gnome-shell --replace
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.preferences' is not installed

aborting...
Shell killed with signal 5
tomas@seedbox:~$ Cannot register the panel shell: there is already one running.

---

### Post by augias on 2011-01-18
> **moore.bryan said:**
> Strange new wrinkle:
After rebuilding yesterday, I can't seem to get GS to run at start. I've put a reference to "~/gnome-shell/install/bin/gnome-shell --restart" in my Startup Applications, but that gives me a blank desktop; running that *same* command in a term launches everything fine, though.

Any ideas?
?????????????????
it's supposed to be 

~/gnome-shell/source/gnome-shell/src/gnome-shell --replace

[QUOTE=Tompalaz]GS won't start for me either. Started yesterday after rebuilding.

I think it's this update that killed it:
[http://git.gnome.org/browse/gnome-sh...0587d2bfd5f2aa](http://git.gnome.org/browse/gnome-sh...0587d2bfd5f2aa)
> tomas@seedbox:~$ ./gnome-shell/source/gnome-shell/src/gnome-shell --replace
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.preferences' is not installed

aborting...
Shell killed with signal 5
tomas@seedbox:~$ Cannot register the panel shell: there is already one running.[/QUOTE]

This would be the fourth time I've seen this error reported on this thread in the last 3 pages, so instead of answering I'd kindly ask you to please read the thread up to a few pages back. Your answer is there.

---

### Post by knarf on 2011-01-18
Now that Unity has made the wise step to release a [2D-version]("http://ubuntuforums.org/showthread.php?t=1668156") for those of use un/fortunate enough to be deprived of/spared a 3D-capable graphics driver the time is ripe for a 2D version of Gnome Shell. Sure, it will lack whizz-bang glitzy effects, gratuitous transparency effects and questionable animations but it should still be able to perform its main tasks on the large class of hardware which, for lack of driver or hardware support, are unable to run a hardware-accelerated compositor. Having a 2D-version of Gnome Shell means the standard Gnome desktop as deployed in Gnome 3 would work on all hardware, from the lowliest ARM-powered newbook and the venerable x86-powered oldbook to the most shiny fruitbook. That would be good. That would be Ubuntu (in the original sense of the word).

---

### Post by augias on 2011-01-18
> **knarf said:**
> Now that Unity has made the wise step to release a [2D-version]("http://ubuntuforums.org/showthread.php?t=1668156") for those of use un/fortunate enough to be deprived of/spared a 3D-capable graphics driver the time is ripe for a 2D version of Gnome Shell. Sure, it will lack whizz-bang glitzy effects, gratuitous transparency effects and questionable animations but it should still be able to perform its main tasks on the large class of hardware which, for lack of driver or hardware support, are unable to run a hardware-accelerated compositor. Having a 2D-version of Gnome Shell means the standard Gnome desktop as deployed in Gnome 3 would work on all hardware, from the lowliest ARM-powered newbook and the venerable x86-powered oldbook to the most shiny fruitbook. That would be good. That would be Ubuntu (in the original sense of the word).

heehee, or just use the gnome panel option.

---

### Post by xtoudi on 2011-01-18
> **augias said:**
> ?????????????????
it's supposed to be 

~/gnome-shell/source/gnome-shell/src/gnome-shell --replace



This would be the fourth time I've seen this error reported on this thread in the last 3 pages, so instead of answering I'd kindly ask you to please read the thread up to a few pages back. Your answer is there.

And what is your answer?? Remove **~/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so** ??? There is no **libcanberra-gtk-module.so** (or 32bit) file !!!

QUOTE again:
> Originally Posted by Tompalaz
GS won't start for me either. Started yesterday after rebuilding.

I think it's this update that killed it:
[http://git.gnome.org/browse/gnome-sh...0587d2bfd5f2aa](http://git.gnome.org/browse/gnome-sh...0587d2bfd5f2aa)
Quote:
tomas@seedbox:~$ ./gnome-shell/source/gnome-shell/src/gnome-shell --replace
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.preferences' is not installed

aborting...
Shell killed with signal 5
tomas@seedbox:~$ Cannot register the panel shell: there is already one running.

This is sth different.

---

### Post by augias on 2011-01-18
Well that's a default answer. i'm sorry if it didn't work for you. were you getting that same error launching from terminal?

when i'm stuck, i always dld the gnome-shell-build-setup.sh script from the first page (you have to do this now, new dependencies as of today jan 18)

run it with /bin/bash and preempt that *.la error with 
$ rm gnome-shell/install/lib/*.la
&
$ jhbuild build -acf. it takes time but what do you expect from testing right? : )

---

### Post by augias on 2011-01-18
Well that's a default answer. i'm sorry if it didn't work for you. were you getting that same error launching from terminal?

when i'm stuck, i always dld the gnome-shell-build-setup.sh script from the first page (you have to do this now, new dependencies as of today jan 18)

run it with /bin/bash and preempt that *.la error with 
$ rm gnome-shell/install/lib/*.la
&
$ jhbuild build -acf. it takes time but what do you expect from testing right? : )

---

### Post by knarf on 2011-01-18
> **augias said:**
> heehee, or just use the gnome panel option.
...and be a second-rate citizen for now and for ever? When all that stands between my PIII-m powered powerhouse and Real Ubuntu™ is the lack of a single glitzy feature? That would not be very Ubuntu now would it? That would be [Ubaguzi]("http://mwanasimba.online.fr/E_chaku_15.htm"), and we can't have that around here.

---

### Post by moore.bryan on 2011-01-18
AFAIK, both "~/gnome-shell/install/bin/gnome-shell --replace" and "~/gnome-shell/source/gnome-shell/src/gnome-shell --replace" do the same thing. In fact, on my machine, both work from terminal, but not autostarting.

Any other ideas?

---

### Post by moore.bryan on 2011-01-18
AFAIK, both "~/gnome-shell/install/bin/gnome-shell --replace" and "~/gnome-shell/source/gnome-shell/src/gnome-shell --replace" do the same thing. In fact, on my machine, both work from terminal, but not autostarting.

Any other ideas?

---

### Post by Merk42 on 2011-01-18
Just rebuilt completely from scratch and there is a new dependency, libcups2-dev

---

### Post by HalfEmptyHero on 2011-01-18
Is there anyway to get gnome-shell to stop hibernating? I built it from source on my laptop and whenever I close it, it hibernates. I like to keep my laptop on 24/7 so this is a bit of an annoyance. This only happens while in the shell, with classic gnome my laptop goes to blank screen on close like I want.

---

### Post by augias on 2011-01-18
Yeah, same happened to me! I messed around in the power settings on gnome-control-center. launch it from altf2 or system settings from the user menu on the right. A restart later got it.

---

### Post by 4leite on 2011-01-19
[QUOTE=xtoudi;10371872]And what is your answer?? Remove **~/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so** ??? There is no **libcanberra-gtk-module.so** (or 32bit) file !!!

Any luck with this? I am having the same problem:
```
undefined reference to `g_slist_free_full' gnome-shell ubuntu
```

completely fresh build from gnome-shell-build-setup.sh onwards.

---

### Post by HalfEmptyHero on 2011-01-19
> **augias said:**
> Yeah, same happened to me! I messed around in the power settings on gnome-control-center. launch it from altf2 or system settings from the user menu on the right. A restart later got it.

What settings did you change? I can't find anything that has to do with closing the lid.

---

### Post by augias on 2011-01-19
I know, :/  I just have "AC power and inactive" totally unchecked, as if to tell it to never hibernate. Also, when searching "power" in activities, there are two results: Power and Power Manager. The latter is the gtk2 app. couldn't hurt to mess around in that as well. That has a lid option. Hope that helps, it's all very weird having two power manager apps. Remember this worked for me after restarting.

---

### Post by augias on 2011-01-19
E: forums glitches

---

### Post by HalfEmptyHero on 2011-01-19
Somehow my gtk2 power manager doesn't show everything it used to. Could be because I installed kubuntu as well, although I'm using gdm instead of kdm. I edited the values in gconf to completely disable anything that had to do with hibernation or sleep, but mine still does it when I close it.

---

### Post by augias on 2011-01-19
You've got a real patchwork os on your hands! I'm sorry I can't help you further :(

---

### Post by HalfEmptyHero on 2011-01-19
Thanks anyways. I'll figure it out eventually.

---

### Post by moore.bryan on 2011-01-19
> **Merk42 said:**
> Just rebuilt completely from scratch and there is a new dependency, libcups2-dev
Thanks for this, Merk42;I couldn't figure what was going wrong in an earlier build.

On a side note, my "not starting at login" problem is also gone with a recent build.

---

### Post by HalfEmptyHero on 2011-01-19
Just rebuild from scratch and a new feature was added! You can now search google or wikipedia from the shell!

---

### Post by augias on 2011-01-19
could i recommend the OP add the url [http://git.gnome.org/browse/gnome-shell/log/?showmsg=1](http://git.gnome.org/browse/gnome-shell/log/?showmsg=1) to the first post? this is where peple can pop in and see what newness has been committed to git head. 

also recommend adding the command > $ jhbuild buildone gnome-shell as a faster alternative to updating the shell for non-crucial updates.

---

### Post by moore.bryan on 2011-01-20
Can anyone weigh-in on this: does the Mozilla Daily PPA still break GS?

---

### Post by keypox on 2011-01-20
what are the keyboard shortcuts?  Like how to pull up activities with keyboard?

figured out that one is super.  Nice

---

### Post by augias on 2011-01-21
[http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)  :)

---

### Post by ratcheer on 2011-01-22
Question: I see there was a new "release" of gnome-shell in the ricotz testing PPA on the 20th. Is it in good enough condition to try again, now?

Tim

---

### Post by ratcheer on 2011-01-22
> **ratcheer said:**
> Question: I see there was a new "release" of gnome-shell in the ricotz testing PPA on the 20th. Is it in good enough condition to try again, now?

Tim

No, it is not. Unless something else is needed that I don't have. It still accepts my login to gnome3-session, then returns me to the login dialog. It also still messes up the Classic desktop, making it look like old fashioned Windows NT.

I will poke around the PPA to see if I can find more info to get this going. If I can't, I guess I will have to reinstall Ubuntu, again.

Tim

---

### Post by Harry33 on 2011-01-22
> **ratcheer said:**
> No, it is not. Unless something else is needed that I don't have. It still accepts my login to gnome3-session, then returns me to the login dialog. It also still messes up the Classic desktop, making it look like old fashioned Windows NT.
...
Tim

The simple theme you refer to in Gnome-Classic is there because the package
gnome-settings-daemon_2.91.8 (of ricotz testing PPA)
breaks gnome-classic theming.
On the other hand, gnome-shell depends on it.

You can remove gnome-shell packages and just downgrade (in terminal with sudo dpkg -i)
gnome-settings-daemon and libgnomekbd.
No need to reinstall Ubuntu.

---

### Post by ratcheer on 2011-01-22
Thank you, Harry.

Tim

---

### Post by keypox on 2011-01-23
trying to build on my desktop never seems to work.  I get to step 27 and get a bunch of reference errors.  Run the command doesnt work.  Trying after deleting gnome-shell folder now.  

Seems like a waste though, as now the process has to redownload everything wasting valiable resources. (Not cpu, ram, etc, but real resources)

---

### Post by keypox on 2011-01-23
Nope didnt work again.  

```


/home/keypox/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_source_get_time'
/home/keypox/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/keypox/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/keypox/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/keypox/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_list_free_full'
/home/keypox/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_get_environ'
/home/keypox/gnome-shell/install/lib64/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/keypox/gnome-shell/install/lib64/libgtk-3.0.so: undefined reference to `g_get_monotonic_time'
/home/keypox/gnome-shell/install/lib64/libgdk-3.0.so: undefined reference to `g_slist_free_full'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/keypox/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/keypox/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/keypox/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/keypox/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keypox/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/33]

```

---

### Post by moore.bryan on 2011-01-23
Just for those interested in hardware compatibility, GNOME Shell *does not* run on my "ancient" iMac g4 PPC with 1gb RAM and the VGA compatible controller (nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)).

It built fine, just can't seem to run. :-(

---

### Post by dext on 2011-01-23
> **moore.bryan said:**
> Just for those interested in hardware compatibility, GNOME Shell *does not* run on my "ancient" iMac g4 PPC with 1gb RAM and the VGA compatible controller (nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)).

It built fine, just can't seem to run. :-(

maybe its time to switch to XFCE4.8

---

### Post by moore.bryan on 2011-01-24
Unfortunately, 4.6 is the latest for Debian PPC; 4.8 is just coming-out *and* there aren't any PPC packages yet. I *could* try and compile the whole thing myself, but I'm not suicidal.
;-)

---

### Post by sgage on 2011-01-24
Just did a fresh compile-from-scratch of GS today (first in a while), and I was surprised that it went right through to the end without error.

My joy was short-lived, however, when I tried to fire it up, and got:

```
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "gail-gnome": libgail-gnome.so: cannot open shared object file: No such file or directory
mutter: symbol lookup error: /home/sgage/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
sgage@presa:~$ /usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
No value set for `/apps/compiz-1/general/allscreens/options/active_plugins'
```

Any ideas?

TIA

---

### Post by wacked_up on 2011-01-24
> **sgage said:**
> Just did a fresh compile-from-scratch of GS today (first in a while), and I was surprised that it went right through to the end without error.

My joy was short-lived, however, when I tried to fire it up, and got:

```
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "gail-gnome": libgail-gnome.so: cannot open shared object file: No such file or directory
mutter: symbol lookup error: /home/sgage/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
sgage@presa:~$ /usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
No value set for `/apps/compiz-1/general/allscreens/options/active_plugins'
```

Any ideas?

TIA

Run it with the --replace option. Right now, Compiz is getting in the way. This will have it stop compiz and take over as a window manager. On exit, compiz will get restored.

---

### Post by sgage on 2011-01-24
> **wacked_up said:**
> Run it with the --replace option. Right now, Compiz is getting in the way. This will have it stop compiz and take over as a window manager. On exit, compiz will get restored.

Well, I did run it with the --replace option (been fiddling with Gnome Shell for a long time). And the odd thing, I'm running in Natty Classic (no effects) - I'm running metacity.

Very confusing!

---

### Post by Merk42 on 2011-01-24
> **sgage said:**
> Well, I did run it with the --replace option (been fiddling with Gnome Shell for a long time). And the odd thing, I'm running in Natty Classic (no effects) - I'm running metacity.

Very confusing!
Try deleting [FONT="Courier New"]/home/sgage/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so[/FONT]
There was some conflict where that file wants to use something that's been deprecated. I thought the issue was resolved in more recent builds, but I guess not

---

### Post by Quadunit404 on 2011-01-24
Encountered an error when building Mutter. Here's the error:

```
cc1: warnings being treated as errors
core/main.c: In function ‘sigterm_handler’:
core/main.c:445: error: ignoring return value of ‘write’, declared with attribute warn_unused_result
make[4]: *** [main.o] Error 1
make[4]: Leaving directory `/home/tom/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tom/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tom/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [16/33]
```

---

### Post by keypox on 2011-01-24
> **Quadunit404 said:**
> Encountered an error when building Mutter. Here's the error:

```
cc1: warnings being treated as errors
core/main.c: In function ‘sigterm_handler’:
core/main.c:445: error: ignoring return value of ‘write’, declared with attribute warn_unused_result
make[4]: *** [main.o] Error 1
make[4]: Leaving directory `/home/tom/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tom/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tom/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [16/33]
```

same here

---

### Post by rchiossi on 2011-01-24
> **Quadunit404 said:**
> Encountered an error when building Mutter. Here's the error:

```
cc1: warnings being treated as errors
core/main.c: In function &#8216;sigterm_handler&#8217;:
core/main.c:445: error: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
make[4]: *** [main.o] Error 1
make[4]: Leaving directory `/home/tom/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tom/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tom/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/gnome-shell/source/mutter'
make: *** [all] Error 2
*** Error during phase build of mutter: ########## Error running make   *** [16/33]
```

Same thing here... ill try an older revision of mutter to check if it is of any help...

EDIT: There was a commit in main.c file on 24/01. This commit is the cause of the warning. Just rollback this file to the previous commit and the compilation will proceed.

```

$git log ~/gnome-shell/source/mutter/src/core.c

commit 48b9807c86d520b4b007dd0a438f3c5d72a9a477 <---- the number that you want
Author: Nickolas Lloyd <ultrageek.lloyd@gmail.com>
Date:   Tue Aug 17 10:41:18 2010 +0000

$git checkout 48b9807c86d520b4b007dd0a438f3c5d72a9a477 ~/gnome-shell/source/mutter/src/core.c

```

---

### Post by Quadunit404 on 2011-01-24
Tried that. GNOME Shell became unusably slow. I mean, a snail could perform faster than it :|

EDIT: Well, damn, just realized there's a GS patch that fixes performance on NVIDIA cards, and I just deleted my installation. Looks like I'll have to rebuild tomorrow.

---

### Post by keypox on 2011-01-25
> **rchiossi said:**
> Same thing here... ill try an older revision of mutter to check if it is of any help...

EDIT: There was a commit in main.c file on 24/01. This commit is the cause of the warning. Just rollback this file to the previous commit and the compilation will proceed.

```

$git log ~/gnome-shell/source/mutter/src/core.c

commit 48b9807c86d520b4b007dd0a438f3c5d72a9a477 <---- the number that you want
Author: Nickolas Lloyd <ultrageek.lloyd@gmail.com>
Date:   Tue Aug 17 10:41:18 2010 +0000

$git checkout 48b9807c86d520b4b007dd0a438f3c5d72a9a477 ~/gnome-shell/source/mutter/src/core.c

```

how would you do the rollback?

> **Quadunit404 said:**
> Tried that. GNOME Shell became unusably slow. I mean, a snail could perform faster than it :|

EDIT: Well, damn, just realized there's a GS patch that fixes performance on NVIDIA cards, and I just deleted my installation. Looks like I'll have to rebuild tomorrow.

which patch would that be, im trying to build on desktop w/ nvidia.

---

### Post by keypox on 2011-01-25
new gnome 3 website.  [http://gnome3.org/tryit.html](http://gnome3.org/tryit.html)  live usbs "really soon"

---

### Post by stefanauss on 2011-01-25
> **rchiossi said:**
> 
EDIT: There was a commit in main.c file on 24/01. This commit is the cause of the warning. Just rollback this file to the previous commit and the compilation will proceed.

```

$git log ~/gnome-shell/source/mutter/src/core.c

commit 48b9807c86d520b4b007dd0a438f3c5d72a9a477 <---- the number that you want
Author: Nickolas Lloyd <ultrageek.lloyd@gmail.com>
Date:   Tue Aug 17 10:41:18 2010 +0000

$git checkout 48b9807c86d520b4b007dd0a438f3c5d72a9a477 ~/gnome-shell/source/mutter/src/core.c

```

To show the commit you posted, i have to correct the path to:

```
$ git log ~/gnome-shell/source/mutter/src/core/main.c
```

To rollback, i have to do the checkout when i'm inside the "mutter" directory.

Nevertheless, i can't compile mutter even after rolling back the commit. =(

---

### Post by sgage on 2011-01-25
> **stefanauss said:**
> Nevertheless, i can't compile mutter even after rolling back the commit. =(

Now mutter won't compile for me, either. Guess I'll try again tomorrow.

---

### Post by rchiossi on 2011-01-25
> **Quadunit404 said:**
> Tried that. GNOME Shell became unusably slow. I mean, a snail could perform faster than it :|

EDIT: Well, damn, just realised there's a GS patch that fixes performance on NVIDIA cards, and I just deleted my installation. Looks like I'll have to rebuild tomorrow.

Believe me, the performance has nothing to do with the rollback i proposed... it just add an unused variable back into the code to avoid de warnings. (The compilation fail in case of warnings for mutter).

I'm also using a computer with nvidia cpu and the performance is terrible... just upgraded my system and I'm still getting bad performance.

I'm looking into this issue, but I had no luck so far. =/

EDIT:
The new commits fixed the compilation problem for mutter and the performance seems to be a bit better. Its usable now, although the animations are still choppy.

---

### Post by ronacc on 2011-01-25
I've been trying to build gnome-shell all day but have given up 3 times due to unbelievably slow downloads from git , on the order of only 4% of the first module d/l'd after 1 hr. anyone else seeing this ?

---

### Post by Quadunit404 on 2011-01-25
Here's how to get and apply the patch for anyone else experiencing horrible performance on NVIDIA:

```
cd ~/gnome-shell/source/gnome-shell
curl http://bugzilla-attachments.gnome.org/attachment.cgi?id=157326 > shell-animations-nvidia.patch
git am shell-animations-nvidia.patch
make
make install
```

Yes, the make and make install parts are required for the patch to actually work.

---

### Post by sgage on 2011-01-26
Just tried a compile-from-scratch. Now it's clutter:

```
checking GL/glx.h usability... no
checking GL/glx.h presence... no
checking for GL/glx.h... no
configure: error: Unable to locate required GLX headers
*** Error during phase configure of clutter: ########## Error running ./autogen.sh --prefix /home/sgage/gnome-shell/install --libdir '/home/sgage/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [1/1]
```

---

### Post by Quadunit404 on 2011-01-26
I think that you need the proprietary drivers (for NVIDIA or ATi) or Intel's drivers to build Clutter :|

---

### Post by sgage on 2011-01-26
> **Quadunit404 said:**
> I think that you need the proprietary drivers (for NVIDIA or ATi) or Intel's drivers to build Clutter :|

?

In any case, I _am_ running the proprietary NVIDIA drivers. 

Judging from the sticky msg up top, it seems we might be in for some heavy weather for the next few days...

---

### Post by Quadunit404 on 2011-01-26
Which version are you using? I'm running NVIDIA driver v270.18. I just finished building the GNOME 3 stack without encountering any problems. I even patched it with the NVIDIA patch to fix the animations when using the proprietary NVIDIA drivers. It's running quite beautifully over here.

And since I use the X-Swat PPA rather than the Xorg-Edgers PPA (I prefer more stable stuff, thanks) and I use Maverick rather than Natty I won't really be affected by the X.org updates coming up in the XOE PPA.

---

### Post by omega52390 on 2011-01-27
i have a fun new problem i cant update the clutter build phase because jhbuild can't connect to the git repository 
i get fatal: unable to connect a socket (connection refused) every other phase builds perfectly

---

### Post by bmbaker on 2011-01-27
> **omega52390 said:**
> i have a fun new problem i cant update the clutter build phase because jhbuild can't connect to the git repository 
i get fatal: unable to connect a socket (connection refused) every other phase builds perfectly

yup i got the same thing !!

just gonna let it finish up and then tomorrow try :-

jhbuild build

again and hope it corrects itself

:-)

---

### Post by Rodrigo Chiossi on 2011-01-27
if you already have the repository, just skip the checkout and it will be fine.

As for the performance issue with nvidia, the patch proposed had no effect for me... still getting choppy animations.

---

### Post by Quadunit404 on 2011-01-27
The patch worked for me. GS seems to be less stable than without it, though.

Maybe it doesn't work with all NVIDIA cards? :???:

EDIT: Actually... you have to run make and then make install after patching the GS source for the patch to actually work :lol: because that's what I did after patching and it worked. Guess I'll go ahead and edit the NVIDIA fix instructions to reflect that.

---

### Post by moore.bryan on 2011-01-29
Git still won't work for me. :-(

---

### Post by sgage on 2011-01-29
> **moore.bryan said:**
> Git still won't work for me. :-(

Same here. It's been quite a while since I've been able to compile GS, and I'm curious as to where it is in its development.

---

### Post by Mblackwell on 2011-01-29
remove or rename your ~/gnome-shell/source/clutter directory, 

```

cd ~/gnome-shell/source/
git clone http://git.clutter-project.org/clutter

```

Wait a minute as you won't get any output except you'll get control back when it's finished.

Then build as normal.

I've built the entire stack multiple times in the last few days so I know there's nothing wrong with git. :)

---

### Post by Quadunit404 on 2011-01-29
I think I'll stick with my current build of GS until Clutter's build process is fixed. Sure, it's old, but if it works it works.

---

### Post by sgage on 2011-01-30
> **Mblackwell said:**
> remove or rename your ~/gnome-shell/source/clutter directory, 

```

cd ~/gnome-shell/source/
git clone http://git.clutter-project.org/clutter

```

Wait a minute as you won't get any output except you'll get control back when it's finished.

Then build as normal.

I've built the entire stack multiple times in the last few days so I know there's nothing wrong with git. :)

I tried this, and got past that problem. Now I'm back to this:

```
checking GL/glx.h usability... no
checking GL/glx.h presence... no
checking for GL/glx.h... no
configure: error: Unable to locate required GLX headers
*** Error during phase configure of clutter: ########## Error running ./autogen.sh --prefix /home/sgage/gnome-shell/install --libdir '/home/sgage/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [1/1]
```

What do I do about that?

[EDIT: Never mind, I figured it out. Somehow, I was missing mesa-common-dev. It is included in the code given in the 1st post in this thread, but somehow it didn't get installed. Once I installed it, the clutter compile just sailed right through.]

---

### Post by sgage on 2011-01-30
Ack! So near, and yet so far! Made it through to the gnome-shell module, and this is what happened:

```
tray/na-tray-child.c:418:7: error: implicit declaration of function ‘gtk_socket_get_plug_window’
tray/na-tray-child.c:418:7: error: implicit declaration of function ‘GTK_SOCKET’
tray/na-tray-child.c:418:19: error: assignment makes pointer from integer without a cast
tray/na-tray-child.c: In function ‘na_tray_child_get_wm_class’:
tray/na-tray-child.c:529:22: error: ‘NaTrayChild’ has no member named ‘icon_window’
tray/na-tray-child.c: In function ‘na_tray_child_has_alpha’:
tray/na-tray-child.c:368:1: error: control reaches end of non-void function
make[2]: *** [libtray_la-na-tray-child.lo] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make: *** [install-recursive] Error 1
*** Error during phase install of gnome-shell: ########## Error running make install *** [30/33]
```

Any ideas?

---

### Post by stanca on 2011-01-30
I made a script wich will install and start the Gnome 3 Shell or Gnome-Desktop3 automatically:

---

### Post by moore.bryan on 2011-01-30
Interesting new error on my Debian install:
```
configure: error: Could not figure out where Firefox JavaScript library lives
```
I've double- and triple-checked; I have libmozjs-dev installed and in the appropriate place.

Any thoughts?

FIXED:
Apparently, I'd updated everything *but* xulrunner-dev from the "experimental" repo.

---

### Post by Quadunit404 on 2011-01-30
Getting an error while checking out gdk-pixbuf:

```
*** Checking out gdk-pixbuf *** [7/33]
git stash save jhbuild-stash
po/gl.po: needs merge
po/gl.po: needs merge
po/gl.po: unmerged (5d21494f4791b26e5c6cc4987121bd58f3fe76fc)
po/gl.po: unmerged (6f1522f2acca0b723eb59f57e17ce0784f1c9923)
po/gl.po: unmerged (f8fb10f37f671cd1c1250efc8f57ff43bbe482a9)
fatal: git-write-tree: error building trees
Cannot save the current index state
*** Error during phase checkout of gdk-pixbuf: ########## Error running git stash save jhbuild-stash *** [7/33]

```

I decided to update GS and ran into this error while doing so :|

EDIT: Just ran option 6 (Wipe directory and start again) and NOW it builds.

---

### Post by ronacc on 2011-01-30
> **sgage said:**
> Ack! So near, and yet so far! Made it through to the gnome-shell module, and this is what happened:

```
tray/na-tray-child.c:418:7: error: implicit declaration of function &#8216;gtk_socket_get_plug_window&#8217;
tray/na-tray-child.c:418:7: error: implicit declaration of function &#8216;GTK_SOCKET&#8217;
tray/na-tray-child.c:418:19: error: assignment makes pointer from integer without a cast
tray/na-tray-child.c: In function &#8216;na_tray_child_get_wm_class&#8217;:
tray/na-tray-child.c:529:22: error: &#8216;NaTrayChild&#8217; has no member named &#8216;icon_window&#8217;
tray/na-tray-child.c: In function &#8216;na_tray_child_has_alpha&#8217;:
tray/na-tray-child.c:368:1: error: control reaches end of non-void function
make[2]: *** [libtray_la-na-tray-child.lo] Error 1
make[2]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/sgage/gnome-shell/source/gnome-shell/src'
make: *** [install-recursive] Error 1
*** Error during phase install of gnome-shell: ########## Error running make install *** [30/33]
```

Any ideas?

I ran into the same the exact same problems with glx and then gnome-shell  , try closing the term you built in , open a new one ad run jhbuild with the -fac options , that worked for me .

---

### Post by Quadunit404 on 2011-01-30
Mentlegen, I have good news: apparently the NVIDIA animations patch has been merged into GS and animations are now smooth like they should be.

Unless of course during the build process jhbuild found the NVIDIA patch in the GS source folder and automatically applied it. Someone else with a NVIDIA card mind confirming?

---

### Post by sgage on 2011-01-30
Well, after tearing it right down to the metal and starting fresh, GS compiled without complaints. I went to fire it up, and:

```
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "gail-gnome": libgail-gnome.so: cannot open shared object file: No such file or directory
mutter: symbol lookup error: /home/sgage/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
sgage@presa:~$ /usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
No value set for `/apps/compiz-1/general/allscreens/options/active_plugins'
```

I did use the --replace option in invoking gnome-shell. I am running metacity - is that a problem? I thought you couldn't run compiz and gnome-shell.

I would sure like to have a look at how GS is shaping up, but I'm just about to give up.

Thanks in advance for any insight you might be able to provide.

---

### Post by ronacc on 2011-01-30
I think that "`/apps/compiz-1/general/allscreens/options/active_plugins'" has something to do with unity .I'm going to try purging every part of unity that I can without destroying my install and see if that helps .

---

### Post by Merk42 on 2011-01-30
> **sgage said:**
> Well, after tearing it right down to the metal and starting fresh, GS compiled without complaints. I went to fire it up, and:

```
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "gail-gnome": libgail-gnome.so: cannot open shared object file: No such file or directory
mutter: symbol lookup error: /home/sgage/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
sgage@presa:~$ /usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
No value set for `/apps/compiz-1/general/allscreens/options/active_plugins'
```

I did use the --replace option in invoking gnome-shell. I am running metacity - is that a problem? I thought you couldn't run compiz and gnome-shell.

I would sure like to have a look at how GS is shaping up, but I'm just about to give up.

Thanks in advance for any insight you might be able to provide.
It's been said before in this thread.
Delete the libcanberra-gtk-module.so file it's referring to, it's a known bug.

I'll add it to the OP since that's been coming up a lot

---

### Post by ronacc on 2011-01-30
thanks that saved me from chasing my tail :p

---

### Post by omega52390 on 2011-01-31
since i had'nt said much in a while before my post about the git error i figured i would come back and say some stuff. 
first off thanks for the fix for git i havent been able to compile for a month or so due to issue after issue after this im back in and i cant believe how much i missed it

im digging the new schedule pane in the drop down calender but it needs to be centered better

 and now all i want is someone to get me a slate/tablet/touch thingy to shove GS onto, or even better if a manufacturer would make me one (/drool) 

also does anyone know if anyone from the GS team reads this thread cuz it would be nice to know that our issues and ideas are heard here

---

### Post by moore.bryan on 2011-01-31
Has the clutter git connection refused issue been solved for everyone but me?
:-(

---

### Post by Merk42 on 2011-01-31
> **moore.bryan said:**
> Has the clutter git connection refused issue been solved for everyone but me?
:-(
If it makes you feel any better, I'm still having the same issue.
Tried building the rest but it wouldn't run and now half of my cursors are black look like old GNOME cursors?

---

### Post by Quadunit404 on 2011-01-31
I successfully updated GS a day or two ago - remember that error code I posted a while back involving gdk-pixbuf? Yeah, it was rather easy to solve.

---

### Post by omega52390 on 2011-02-01
> **moore.bryan said:**
> Has the clutter git connection refused issue been solved for everyone but me?
:-(

no we all still have the problem however the workaround on page 53 does work perfectly i was able to build from scratch using it just fine

---

### Post by sgage on 2011-02-01
It seems that GS now requires some packages that are newer than what is in the repos:

```
configure: error: Package requirements (libecal-1.2 >= 1.6.0 libedataserver-1.2 >= 1.2.0 libedataserverui-1.2 >= 2.91.6) were not met:

Requested 'libedataserverui-1.2 >= 2.91.6' but version of libedataserverui is 2.32.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBECAL_CFLAGS
and LIBECAL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/sgage/gnome-shell/install --libdir '/home/sgage/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [29/32]
```

Presumably these packages will be updated soon...

---

### Post by fil0~ on 2011-02-01
> **sgage said:**
> It seems that GS now requires some packages that are newer than what is in the repos:
[..]
Presumably these packages will be updated soon...
Known issue, you can apply this patch: [http://fpaste.org/Y1pf/](http://fpaste.org/Y1pf/)
Worked for me.

---

### Post by Quadunit404 on 2011-02-01
> **fil0~ said:**
> Known issue, you can apply this patch: [http://fpaste.org/Y1pf/](http://fpaste.org/Y1pf/)
Worked for me.

Looking through that patch, I found this:

```
# Collect more than 20 libraries for a prize!
```

:lol:

PS: The GNOME Shell live CDs have been released, along with some UI changes. Read about it [here.]("http://www.omgubuntu.co.uk/2011/02/gnome-shell-gets-a-live-cd/")

EDIT: New error:

```
./.libs/libgtk-3.0.so: undefined reference to `gdk_window_get_drag_protocol'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/tom/gnome-shell/source/gtk3/gtk/tmp-introspecteDcul3/Gtk-3.0', '-export-dynamic', '-L.', 'libgtk-3.0.la', '-pthread', '-L/home/tom/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/tom/gnome-shell/source/gtk3/gtk/tmp-introspecteDcul3/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/tom/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tom/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tom/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/32]

```

Checking out if running phase "Wipe directory and start over" will do anything. If there are any new dependencies I'll post them here.

EDIT: New dependency: evolution-data-server-dev. However, installing that did nothing.

---

### Post by keypox on 2011-02-01
New error for me but got passed where i was before

```

gsd-xrandr-manager.c:652: error: ‘GdkNativeWindow’ undeclared (first use in this function)
gsd-xrandr-manager.c:652: error: (Each undeclared identifier is reported only once
gsd-xrandr-manager.c:652: error: for each function it appears in.)
gsd-xrandr-manager.c:652: error: expected ‘)’ before ‘parent_window_id’
make[3]: *** [libxrandr_la-gsd-xrandr-manager.lo] Error 1
make[3]: Leaving directory `/home/keypo/gnome-shell/source/gnome-settings-daemon/plugins/xrandr'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/keypo/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keypo/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [26/32]



```

got it from here [http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)

had to delete the old libnotify folder in ~/gnome-shell   then follow instructions on that error 

cd ~/bin
./jhbuild shell
cd ~/gnome-shell/source
git clone git://git.gnome.org/libnotify
cd ./libnotify
./autogen.sh --prefix $HOME/gnome-shell/install/
make && make install


```

configure: error: Package requirements (libecal-1.2 >= 1.6.0 libedataserver-1.2 >= 1.2.0 libedataserverui-1.2 >= 1.2.0) were not met:

No package 'libecal-1.2' found
No package 'libedataserver-1.2' found
No package 'libedataserverui-1.2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBECAL_CFLAGS
and LIBECAL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/keypo/gnome-shell/install --libdir '/home/keypo/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [29/32]

```

So close!!!!

---

### Post by arrimapirate on 2011-02-01
> **fil0~ said:**
> Known issue, you can apply this patch: [http://fpaste.org/Y1pf/](http://fpaste.org/Y1pf/)
Worked for me.

Can you please explain how to apply this patch? I encountered the same error when doing a sandbox build.

---

### Post by moore.bryan on 2011-02-01
How about the test-media-keys error; any ideas what I can do about this?
```
CCLD   test-media-keys
/home/bryan/gnome-shell/install/lib/libgtk-3.0.so: undefined reference to `g_source_get_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring_array'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/bryan/gnome-shell/install/lib/libgtk-3.0.so: undefined reference to `g_object_class_install_properties'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/bryan/gnome-shell/install/lib/libgtk-3.0.so: undefined reference to `g_list_free_full'
/home/bryan/gnome-shell/install/lib/libgtk-3.0.so: undefined reference to `g_object_notify_by_pspec'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/bryan/gnome-shell/install/lib/libgdk-3.0.so: undefined reference to `g_source_set_name'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_dup_bytestring_array'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/bryan/gnome-shell/install/lib/libgtk-3.0.so: undefined reference to `g_get_monotonic_time'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
/home/bryan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_take_variant'
/home/bryan/gnome-shell/install/lib/libgdk-3.0.so: undefined reference to `g_slist_free_full'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2

```
Oh, and clutter's up for me now...

---

### Post by Quadunit404 on 2011-02-01
Anybody ever figure out how to fix the GTK3 compilation error I posted? I tried removing the .la files from ~/gnome-shell/install/lib64 but that did nothing.

EDIT: Here it is again if anyone missed it

```

./.libs/libgtk-3.0.so: undefined reference to `gdk_window_get_drag_protocol'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/tom/gnome-shell/source/gtk3/gtk/tmp-introspectdOaF7v/Gtk-3.0', '-export-dynamic', '-L.', 'libgtk-3.0.la', '-pthread', '-L/home/tom/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/tom/gnome-shell/source/gtk3/gtk/tmp-introspectdOaF7v/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/tom/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tom/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tom/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/32]

```

EDIT: Deleting ~/gnome-shell worked. Well, gee, couldn't jhbuild tell me that was the problem the whole time? ](*,)

---

### Post by borghal on 2011-02-02
Thanks for this info QuadUnit 404, I was just getting frustrated having the same problem. Cheers!

---

### Post by Quadunit404 on 2011-02-02
In other news, apparently the NVIDIA animations patch has merged in the main GS source as I didn't have to patch the source code or anything.

Oh, and you also need to install some new dependencies for GS due to the new calendar I believe. GS should list them during the configure process if you don't have them already. Just search for them in the USC or Synaptic or whatever your package manager is and you should find them (install the ones with -dev at the end)

---

### Post by keypox on 2011-02-02
> **Quadunit404 said:**
> In other news, apparently the NVIDIA animations patch has merged in the main GS source as I didn't have to patch the source code or anything.

Oh, and you also need to install some new dependencies for GS due to the new calendar I believe. GS should list them during the configure process if you don't have them already. Just search for them in the USC or Synaptic or whatever your package manager is and you should find them (install the ones with -dev at the end)

I thought i posted to delete gnome-shell folder as that wokred for me, but guess i didnt hit submit lol.

Anyways i was stuck on the new dependencies

No package 'libecal-1.2' found
No package 'libedataserver-1.2' found
No package 'libedataserverui-1.2' found

are you saying they are fixed now?  Im about to try to build all over hoping it works this time  :popcorn:

---

### Post by KegHead on 2011-02-02
Hi Merk42!

Is there a USB download for 3.0 yet? (Ubuntu)

Thanks!

KegHead

---

### Post by Harry33 on 2011-02-02
> **keypox said:**
> I thought i posted to delete gnome-shell folder as that wokred for me, but guess i didnt hit submit lol.

Anyways i was stuck on the new dependencies

No package 'libecal-1.2' found
No package 'libedataserver-1.2' found
No package 'libedataserverui-1.2' found

are you saying they are fixed now?  Im about to try to build all over hoping it works this time  :popcorn:

New gnome-shell 2.91.6 is integrated with evolution-data-server to support calendar appointments.
Not actually big news.
Gnome-panel with its applets has been integrated that way for ages.

---

### Post by Quadunit404 on 2011-02-02
> **keypox said:**
> I thought i posted to delete gnome-shell folder as that wokred for me, but guess i didnt hit submit lol.

Anyways i was stuck on the new dependencies

No package 'libecal-1.2' found
No package 'libedataserver-1.2' found
No package 'libedataserverui-1.2' found

are you saying they are fixed now?  Im about to try to build all over hoping it works this time  :popcorn:

Run this:

```
sudo apt-get install libecal1.2-dev libedataserver1.2-dev libedataserverui1.2-dev
```

That should give you everything you need to build GS now in one command. The GNOME devs changed the calendar recently to put the Scheduled tasks part back into view, so you need to install those.

---

### Post by sgage on 2011-02-02
Built from scratch this morning without incident. Fired up GS and got the canberra error. Deleted the canberra file, and got the following:

```
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "gail-gnome": libgail-gnome.so: cannot open shared object file: No such file or directory
(mutter:1510): Clutter-DEBUG: Signal type minimize not supported

(mutter:1510): Clutter-DEBUG: Signal type maximize not supported

(mutter:1510): Clutter-DEBUG: Signal type restore not supported

Window manager warning: Log level 16: Failed to load shared library 'libgnome-bluetooth-applet.so.0' referenced by the typelib: libgnome-bluetooth-applet.soso: cannot open shared object file: No such file or directory
Window manager warning: Log level 8: g_ascii_strncasecmp: assertion `s2 != NULL' failed
Shell killed with signal 11
```

At this point, there is no panel or other evidence of GS. Metacity seems to be running. Alt-Tab rotates through open windows. I can right-click on the desktop and in the menu "open in terminal" to get a term going. I can type 'gnome-panel' and get my 2-panel setup going, and log out, etc. 

What is happening? I'm about to give up.

---

### Post by keypox on 2011-02-02
> **Quadunit404 said:**
> Run this:

```
sudo apt-get install libecal1.2-dev libedataserver1.2-dev libedataserverui1.2-dev
```

That should give you everything you need to build GS now in one command. The GNOME devs changed the calendar recently to put the Scheduled tasks part back into view, so you need to install those.

thank you sir i am now *** success *** [32/32]

However i had one last error when gnome shell wouldnt start that i fixed with.

rm ~/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so

It is super choppy on my system with nvidia.   Are you sure the nvidia patch is in?

EDIT: Ran the patch still choppy animations, running xswat with 260 gtx

---

### Post by Quadunit404 on 2011-02-02
It might be me using NVIDIA driver 270.18 from the X-Swatters PPA. Check the NVIDIA X Server settings and tell me the driver you have installed.

---

### Post by moore.bryan on 2011-02-02
Successfully built on my Debian 6.0 install. There is, apparently, a new wrinkle in how the time/day is portrayed in the panel: no longer is that controlled by the ~/gnome-shell/install/share/gnome-shell/js/ui/panel.js file... so, time to go figure out how to change "Wed 4:55 PM" to something more useful...

:-)

EDIT
Wow, that was easy. For anyone looking to change the clock format in the panel, you need to edit the ~/gnome-shell/install/share/gnome-shell/js/ui/dateMenu.js file.

Oh, and if you launch with ~/gnome-shell/source/gnome-shell/src/gnome-shell --replace instead of ~/gnome-shell/install/bin/gnome-shell --replace, you'll need to change those locations above to what works for you.

---

### Post by keypox on 2011-02-02
> **Quadunit404 said:**
> It might be me using NVIDIA driver 270.18 from the X-Swatters PPA. Check the NVIDIA X Server settings and tell me the driver you have installed.

Im also using x-swat, and the kernel updated today.

---

### Post by Quadunit404 on 2011-02-02
Huh... maybe the patch doesn't work with all NVIDIA cards?

You mind pasting the terminal output for GS? That might help us.

---

### Post by Merk42 on 2011-02-02
> **KegHead said:**
> Hi Merk42!

Is there a USB download for 3.0 yet? (Ubuntu)

Thanks!

KegHead
[There is](http://blog.crozat.net/2011/01/gnome-3-live-cd-usb-test-image.html), though it seems to be based off of openSUSE

---

### Post by keypox on 2011-02-02
> **Quadunit404 said:**
> Huh... maybe the patch doesn't work with all NVIDIA cards?

You mind pasting the terminal output for GS? That might help us.
```

Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-plugin": libglobalmenu-plugin.so: cannot open shared object file: No such file or directory
Window manager warning: Log level 16: Accessibility: org.a11y.atspi schema not found. Are you sure that at-spi or at-spi2 is installed on your system?
Window manager warning: Log level 16: Accessibility: invalid module path (NULL)
Window manager warning: Log level 16: Accessibility: error loading the atk-bridge. Although the accessibility on the system is enabled and clutter accessibility is also enabled, accessibility support on GNOME Shell will not work
      JS LOG: GNOME Shell started at Wed Feb 02 2011 21:15:34 GMT-0500 (EST)
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-plugin": libglobalmenu-plugin.so: cannot open shared object file: No such file or directory
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:8757): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:8784): WARNING **: Unknown option --since=2010-12-05T02:15:35.459451Z

```


> **Merk42 said:**
> [There is](http://blog.crozat.net/2011/01/gnome-3-live-cd-usb-test-image.html), though it seems to be based off of openSUSE

opensuse one didnt work for my but the fedora one did. 
[http://www.webupd8.org/2011/02/easily-test-gnome-shell-using-live-cd.html](http://www.webupd8.org/2011/02/easily-test-gnome-shell-using-live-cd.html)

---

### Post by Dobbie03 on 2011-02-03
> **xtoudi said:**
> ```
ln -s ~/gnome-shell/install/share/applications/gnome-shell.desktop ~/.local/share/applications/gnome-shell.desktop
gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "gnome-shell" -t string
```

I have used this to start GS at login but I wont to be able to choose what to use, how do I reverse it?

---

### Post by Quadunit404 on 2011-02-03
```
gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager "gnome-wm"
```

That should do the trick.

Now then, I created a Shell script that runs the command [FONT="Courier New"]jhbuild build --force --clean[/FONT] (aka update GS) and I want it so that Shell script runs every day at 5PM. Would adding this to my crontab work?

```
00 17 * * * /home/tom/scripts/update_gs.sh

```

Or do I have to add a [FONT="Courier New"]sh[/FONT] before the path to update_gs.sh?

---

### Post by bmbaker on 2011-02-04
error: GNOME Shell requires Mutter to be compiled against GTK+-3.0
*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/brian/gnome-shell/install --libdir '/home/brian/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [1/1]

Any ideas why i am getting this ?

---

### Post by wacked_up on 2011-02-04
> **bmbaker said:**
> error: GNOME Shell requires Mutter to be compiled against GTK+-3.0
*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/brian/gnome-shell/install --libdir '/home/brian/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [1/1]

Any ideas why i am getting this ?

Did you per change at one point check out the overlay-redesign branch and forgot to switch back to main?

I had that problem too and this was the reason.

---

### Post by bmbaker on 2011-02-04
> **wacked_up said:**
> Did you per change at one point check out the overlay-redesign branch and forgot to switch back to main?

I had that problem too and this was the reason.

ah yes indeed i did !! ha .-) thanks
so how do i switch back to the main after ?
or do i just redo all?

---

### Post by wacked_up on 2011-02-04
> **bmbaker said:**
> ah yes indeed i did !! ha .-) thanks
so how do i switch back to the main after ?
or do i just redo all?

in your home folder I think is a hidden file: .jhbuildrc-custom or something.
At one point you added there that you wanted the branch instead of the master. Remove or comment the line.

Then, on the terminal do this: jhbuild buildone -n gnome-shell

This just builds the shell, so you don't have to rebuild everything.

Enjoy!

---

### Post by NightwishFan on 2011-02-04
Just compiled Gnome Shell on Lucid, and it works great. I have to admit it does feel futuristic.

---

### Post by bmbaker on 2011-02-04
> **wacked_up said:**
> in your home folder I think is a hidden file: .jhbuildrc-custom or something.
At one point you added there that you wanted the branch instead of the master. Remove or comment the line.

Then, on the terminal do this: jhbuild buildone -n gnome-shell

This just builds the shell, so you don't have to rebuild everything.

Enjoy!

great thank you :-)
 I'll try it out again later!

---

### Post by Quadunit404 on 2011-02-04
Just updated GS. Encountered two checkout errors that were... easily resolved (all I had to do was choose phase "Wipe directory and start over") and so far I have noticed that animations - particularly the animation when switching to the Activities view - is much smoother.

Just gotta wait for all the crashing to be fixed (I experience random Shell crashes and get sent back to Compiz when that happens) and I'll set GS to be my desktop.

Oh, and that question regarding auto-updating GS through cron I asked earlier? Yeah, it'll work without [FONT="Courier New"]sh[/FONT]. I ran the command /home/tom/scripts/update_gs.sh in a terminal WITHOUT [FONT="Courier New"]sh[/FONT] and it ran.

---

### Post by keypox on 2011-02-05
Package requirements (libxklavier >= 5.1) were not met:

Requested 'libxklavier >= 5.1' but version of libxklavier is 5.0


For me today,  package not updated yet it seems.

---

### Post by NightwishFan on 2011-02-05
Boooo! I am unable to compile on Debian Sid because I need a newer version of libmoz.. something. :D

I grabbed the -dev from experiemental and it told me it couldnt find the proper place for it, so I will have to wait until Sid gets a newer fox.

---

### Post by moore.bryan on 2011-02-05
> **keypox said:**
> Package requirements (libxklavier >= 5.1) were not met:

Requested 'libxklavier >= 5.1' but version of libxklavier is 5.0


For me today,  package not updated yet it seems.
*Just* ran into this now... *really* irritating because I just compiled yesterday on my Debian install and everything went fine, so I thought it was the right time to compile on my Mint. Also, there's no libxklavier 5.1 *anywhere*, not even on their SourceForge page.

> **NightwishFan said:**
> Boooo! I am unable to compile on Debian Sid because I need a newer version of libmoz.. something. :D

I grabbed the -dev from experiemental and it told me it couldnt find the proper place for it, so I will have to wait until Sid gets a newer fox.

I got past this by rebooting, deleting the entire gnome-shell dir, and starting from scratch.

---

### Post by keypox on 2011-02-05
> **moore.bryan said:**
> *Just* ran into this now... *really* irritating because I just compiled yesterday on my Debian install and everything went fine, so I thought it was the right time to compile on my Mint. Also, there's no libxklavier 5.1 *anywhere*, not even on their SourceForge page.



I got past this by rebooting, deleting the entire gnome-shell dir, and starting from scratch.

yeah its really just if your lucky enough to build at hte right time lol.

---

### Post by moore.bryan on 2011-02-05
Hit or miss... wish they wouldn't put in a new necessary component without that component even being available, though...

---

### Post by kainos on 2011-02-05
> **moore.bryan said:**
> Hit or miss... wish they wouldn't put in a new necessary component without that component even being available, though...


Yes, that is exactly what has happened.

[http://permalink.gmane.org/gmane.comp.gnome.desktop/43957]("http://permalink.gmane.org/gmane.comp.gnome.desktop/43957")

Looks like that it will be released quickly.

---

### Post by NightwishFan on 2011-02-06
Got past the mozjs errors on sid, and now I am stuck on the above as well. I will post as soon as I am able to build and how if I figure it out.

---

### Post by Quadunit404 on 2011-02-06
Okay! Hope you figure it out, because I ran into that same error too :|

---

### Post by dancer_69 on 2011-02-06
I found a solution by searching in google here:
[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)


```
I got it to work by changing the configure.in for libgnomekbd on line 21
and configure.ac of gnome-control-center on line 172 from 5.1 to 5.0. All other instructions were as above (rm *.la and rm libcanberra-gtk-module.so). Thanks! 
```

---

### Post by moore.bryan on 2011-02-06
^ Patching didn't work for me, I guess because I fully deleted my gnome-shell dir thinking that could be causing some of the problems. For anyone else out there who is starting from scratch, the following did the trick for me: 
[LIST=1]
[*]Build until failure and the xklavier error.
[*]cd into ~/gnome-shell/source/libgnomekbd and edit the configure.in file to change the libxklavier requirement to 5.0 on line 21.
[*]Select choice "1" to reconfigure.
[*]The gnome-shell build will stop again at gnome-control-center. cd into ~/gnome-shell/source/gnome-control-center and edit the configure.ac file to change the libxklavier requirement to 5.0 on line 172.
[*]Select choice "1" to reconfigure.
[/LIST]

Everything should then continue fine. I'm recompiling a second time to make sure this all works and will post back success or failure.

---

### Post by dancer_69 on 2011-02-06
I didn't use the patches too. I did it like you just described, and now I can successfully start it.

**How can I login to gnome3 session now?**
Is there any commands or a file to edit to put it as an option in login sessions selection?

---

### Post by Quadunit404 on 2011-02-06
> **moore.bryan said:**
> ^ Patching didn't work for me, I guess because I fully deleted my gnome-shell dir thinking that could be causing some of the problems. For anyone else out there who is starting from scratch, the following did the trick for me: 
[LIST=1]
[*]Build until failure and the xklavier error.
[*]cd into ~/gnome-shell/source/libxklavier and edit the configure.in file to change the libxklavier requirement to 5.0 on line 21.
[*]Select choice "1" to reconfigure.
[*]The gnome-shell build will stop again at gnome-control-center. cd into ~/gnome-shell/source/gnome-control-center and edit the configure.ac file to change the libxklavier requirement to 5.0 on line 172.
[*]Select choice "1" to reconfigure.
[/LIST]

Everything should then continue fine. I'm recompiling a second time to make sure this all works and will post back success or failure.

Thanks. Works for me.

You might also want to change the ~/gnome-shell/source/libxklavier to ~/gnome-shell/source/libgnomekbd though :wink:

---

### Post by moore.bryan on 2011-02-06
I can confirm this works on my Linux Mint and Fedora installs... still waiting for it to compile on my Debian.

---

### Post by moore.bryan on 2011-02-06
My Debian install is still getting the same error I posted in #550 when trying to build gnome-settings-daemon with the test-media-keys.

Any ideas?

---

### Post by moore.bryan on 2011-02-06
> **Quadunit404 said:**
> Thanks. Works for me.

You might also want to change the ~/gnome-shell/source/libxklavier to ~/gnome-shell/source/libgnomekbd though :wink:
Thanks for catching that... caught it myself and made the change--apparently--right after your post!

> **moore.bryan said:**
> My Debian install is still getting the same error I posted in #550 when trying to build gnome-settings-daemon with the test-media-keys.

Any ideas?
I solved this by deleting any *.la files in /usr/lib--even though I already did that--and am rebuilding now. Fingers crossed.

---

### Post by MacUntu on 2011-02-06
Fresh Natty 64-bit: deleted the .la files, ran jhbuild, did the libxklavier version dance, had to remove gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so, then the shell started just fine.

---

### Post by moore.bryan on 2011-02-06
Turns-out GS won't run on my old iMac G4 "Flowerpot" because there are no NVIDIA PPC drivers out there. :-(

Oh well, 4/5 ain't bad.

---

### Post by Quadunit404 on 2011-02-06
Think it might be time to get a new computer, then?

According to the GNOME 3 site, any computer released in the last five years should be powerful enough for GS. The iMac G4 was discontinued 7 years ago.

---

### Post by NightwishFan on 2011-02-06
Just compiled and running on Debian Sid! :)

---

### Post by keypox on 2011-02-07
got it running here but animations are to slow with nvidia.

---

### Post by Quadunit404 on 2011-02-07
Okay, as of sometime around 8AM today, I have been using GS without it crashing _once_ on me. That's gotta be some sort of record, right?

---

### Post by NightwishFan on 2011-02-08
Tips for Squeeze/Sid users, if you want to have the shell perform well, remove the package "menu", because the gnome shell loads a copy of everything in its menu, which takes forever to load.

---

### Post by tjeremiah on 2011-02-08
anyone else having troubling install on a USB. I followed the commands on the Gnome 3 website but every time I input the iso source, I receive a "command not found."

---

### Post by NightwishFan on 2011-02-08
What is the exact command? Can you link me to the instructions?

---

### Post by moore.bryan on 2011-02-08
> **Quadunit404 said:**
> Think it might be time to get a new computer, then?

According to the GNOME 3 site, any computer released in the last five years should be powerful enough for GS. The iMac G4 was discontinued 7 years ago.
It *is* old, but I've other computers for "real" work... this is just my play one. I'd still like GS on it, though. Too bad.

And the issue seems to be with NVIDIA more than GS because they're the ones who haven't decided to support PPC architecture.

---

### Post by MacUntu on 2011-02-08
BTW, the libxklavier thingy has been (temporarily) fixed, jhbuild builds it from CVS.

---

### Post by tjeremiah on 2011-02-08
> **NightwishFan said:**
> What is the exact command? Can you link me to the instructions?
[http://www.gnome3.org/tryit.html](http://www.gnome3.org/tryit.html)
```
    Download the USB image writer (below) and extract it
    Open a terminal and navigate to the extracted image writer folder (eg. $ cd Downloads/abock-image-usb-stick-f3b1002)
    Prepare the image writer by running: $ chmod a+x ./image-usb-stick
    Remove any USB storage devices that you might have connected to your computer and insert the empty USB stick that you want to write to
    Run the image writer script: $ sudo ./image-writer path_to_the_live_image.iso
    To run the live image, reboot your computer with the USB stick attached

```
Everything runs smoothly until I point it to the path of the live image. Hit enter and receive a "command not found." I tried it under root too and get the same results.
```
blacksnake@blacksnake-VGN-NR160E:~$ cd /home/blacksnake/Downloads/abock-image-usb-stick-f3b1002
blacksnake@blacksnake-VGN-NR160E:~/Downloads/abock-image-usb-stick-f3b1002$ chmod a+x ./image-usb-stick
blacksnake@blacksnake-VGN-NR160E:~/Downloads/abock-image-usb-stick-f3b1002$ sudo ./image-writer /home/blacksnake/GNOME_3.x86_64-0.0.3-Build1.1.iso 
[sudo] password for blacksnake: 
sudo: ./image-writer: command not found


```

---

### Post by NightwishFan on 2011-02-08
I think they mean:
```
Run the image writer script: $ sudo ./image-usb-stick path_to_the_live_image.iso
```

Though I could be wrong.

*************

Isn't DD a simpler built in method to do this or is their method special or needed somehow. If all else fails I can walk you through a simple DD command to copy the iso.

---

### Post by tjeremiah on 2011-02-08
> **NightwishFan said:**
> I think they mean:
```
Run the image writer script: $ sudo ./image-usb-stick path_to_the_live_image.iso
```

Though I could be wrong.



You are CORRECT:guitar: that worked. Quick, someone contact Gnome and tell them they made an error :lolflag:

---

### Post by NightwishFan on 2011-02-08
> **tjeremiah said:**
> You are CORRECT:guitar: that worked. Quick, someone contact Gnome and tell them they made an error :lolflag:

No problems, enjoy! I sent them an email to a mailing list, but I accidentally sent two of the same by accident. I hope they do not think I sent spam! :)

---

### Post by keypox on 2011-02-08
gnome3 live usb doesnt work for me.  Only the fedora gnome 3 live works, smooth too, dunno why the git build is so choppy but fedora live is not.

I assume its using the open source driver and that is smoother with g-shell.

---

### Post by go7Ul1ai on 2011-02-08
I do the instructions above, but when attempting to boot from usb I just get "operating system not found". Damn it I've been itching to try GNOME Shell for 3 days now and it's just not happening for me, everything I've tried has failed (even trying to make a OpenSUSE 11.3 liveUSB and then installing GNOME Shell).

Meh, I just want a vanilla GNOME install, that's all. I've tried Foresight Linux from USB but I can't get that to work neither. Damn it

/rant

---

### Post by keypox on 2011-02-08
> **lee.jarratt said:**
> I do the instructions above, but when attempting to boot from usb I just get "operating system not found". Damn it I've been itching to try GNOME Shell for 3 days now and it's just not happening for me, everything I've tried has failed (even trying to make a OpenSUSE 11.3 liveUSB and then installing GNOME Shell).

Meh, I just want a vanilla GNOME install, that's all. I've tried Foresight Linux from USB but I can't get that to work neither. Damn it

/rant

try the fedora daily thats the only one that worked for me.

---

### Post by dext on 2011-02-08
have a look in the **Rawhide** sub-forum an you'll see the link to get it

---

### Post by simpleblue on 2011-02-09
> **dext said:**
> have a look in the **Rawhide** sub-forum an you'll see the link to get it

Here's a link to the nightly composes:

[http://alt.fedoraproject.org/pub/alt/nightly-composes/desktop/](http://alt.fedoraproject.org/pub/alt/nightly-composes/desktop/)

---

### Post by moore.bryan on 2011-02-09
For anyone who has built lately:
Does GS seem to take longer to load than before? Mine does... perhaps it's something to do with the Evolution calendar-sync thing...

---

### Post by Quadunit404 on 2011-02-09
Unable to check out Clutter from Git, going to have to wait until tomorrow to try out the new Auto-workspaces feature :(

---

### Post by xtoudi on 2011-02-10
Anyone noticed new look of ... right .. that thing at the right - this is my desktop right now after fresh compile.

---

### Post by Quadunit404 on 2011-02-10
That's no bug, it's a new feature. No seriously it is.

There was a mockup of automatic workspaces a while back. Now it's real. All what you do to make a new workspace is drag a window to the workspaces area and a new workspace is born.

---

### Post by xtoudi on 2011-02-10
> **Quadunit404 said:**
> That's no bug, it's a new feature. No seriously it is.

There was a mockup of automatic workspaces a while back. Now it's real. All what you do to make a new workspace is drag a window to the workspaces area and a new workspace is born.

ok .. this was little bit irony ... my mistake ;)

I know that ;) ...looks and works well.

---

### Post by Merk42 on 2011-02-10
> **xtoudi said:**
> Anyone noticed new look of ... right .. that thing at the right - this is my desktop right now after fresh compile.
I sure did, I changed the pictures in the OP last night.

---

### Post by keypox on 2011-02-10
Trying to build today get this error, guess i should try deleting gnome-shell dir. 

```



cc-background-item.c:36: fatal error: gdesktop-enums-types.h: No such file or directory
compilation terminated.
make[3]: *** [cc-background-item.lo] Error 1
make[3]: Leaving directory `/home/keypo/gnome-shell/source/gnome-control-center/panels/background'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/keypo/gnome-shell/source/gnome-control-center/panels'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keypo/gnome-shell/source/gnome-control-center'
make: *** [all] Error 2
*** Error during phase build of gnome-control-center: ########## Error running make   *** [28/33]

```

---

### Post by andrewthomas on 2011-02-10
> **keypox said:**
> Trying to build today get this error, guess i should try deleting gnome-shell dir. 

```



cc-background-item.c:36: fatal error: gdesktop-enums-types.h: No such file or directory
compilation terminated.
make[3]: *** [cc-background-item.lo] Error 1
make[3]: Leaving directory `/home/keypo/gnome-shell/source/gnome-control-center/panels/background'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/keypo/gnome-shell/source/gnome-control-center/panels'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keypo/gnome-shell/source/gnome-control-center'
make: *** [all] Error 2
*** Error during phase build of gnome-control-center: ########## Error running make   *** [28/33]

```
Install gnome-control-center-dev and restart the build

---

### Post by Quadunit404 on 2011-02-10
New error for me:

```
cc1: warnings being treated as errors
shell-doc-system.c: In function &#8216;shell_doc_system_open&#8217;:
shell-doc-system.c:274: error: passing argument 3 of &#8216;gtk_recent_info_get_application_info&#8217; from incompatible pointer type
/home/tom/gnome-shell/install/include/gtk-3.0/gtk/gtkrecentmanager.h:202: note: expected &#8216;const gchar **&#8217; but argument is of type &#8216;char **&#8217;
make[3]: *** [libgnome_shell_la-shell-doc-system.lo] Error 1
make[3]: Leaving directory `/home/tom/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tom/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [30/33]
```

EDIT: Resolved by selecting phase 6. GS updated successfully after that.

EDIT AGAIN: GS crashes upon startup for me. Why? I don't know.

---

### Post by keypox on 2011-02-10
> **andrewthomas said:**
> Install gnome-control-center-dev and restart the build

thanks got past that but next step errors

```



/bin/sed: can't read /home/keypo/gnome-shell/install/lib/libgio-2.0.la: No such file or directory
libtool: link: `/home/keypo/gnome-shell/install/lib/libgio-2.0.la' is not a valid libtool archive
make[3]: *** [liba11y-keyboard.la] Error 1
make[3]: Leaving directory `/home/keypo/gnome-shell/source/gnome-settings-daemon/plugins/a11y-keyboard'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/keypo/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keypo/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/33]

```

---

### Post by Buying_Some_Time on 2011-02-11
Hello, I've successfully built my gnome shell but, when I try to start it I get this error: 

```
Gtk-Message: Failed to load module "canberra-gtk-module"
Window manager warning: Log level 16: Accessibility: org.a11y.atspi schema not found. Are you sure that at-spi or at-spi2 is installed on your system?
Window manager warning: Log level 16: Accessibility: invalid module path (NULL)
Window manager warning: Log level 16: Accessibility: error loading the atk-bridge. Although the accessibility on the system is enabled and clutter accessibility is also enabled, accessibility support on GNOME Shell will not work
      JS LOG: GNOME Shell started at Fri Feb 11 2011 10:21:20 GMT-0500 (EST)
gnome-power-manager: error while loading shared libraries: libcanberra-gtk3.so.0: cannot open shared object file: No such file or directory
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:11324): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:11347): WARNING **: Unknown option --since=2010-12-13T15:21:26.982142Z
Window manager warning: Log level 8: meta_window_raise: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
```

Anyone know how to fix this? 

Thanks!

---

### Post by Universal344 on 2011-02-11
Anyone else getting a gnome shell crash when you go to activities?  if so do you know how to fix it?

---

### Post by MacUntu on 2011-02-11
Nope, just compiled it from scratch, and everything's working fine (Intel HD, 64-bit).

---

### Post by moore.bryan on 2011-02-11
How 'bout this one?
```

CC     gdkdevice-xi2.lo
gdkdevice-xi2.c: In function 'gdk_x11_device_xi2_query_state':
gdkdevice-xi2.c:370:5: warning: implicit declaration of function '_gdk_x11_device_xi2_translate_state'
gdkdevice-xi2.c: In function 'gdk_x11_device_xi2_grab':
gdkdevice-xi2.c:408:3: warning: implicit declaration of function '_gdk_x11_device_xi2_translate_event_mask'
gdkdevice-xi2.c:408:13: warning: assignment makes pointer from integer without a cast
gdkdevice-xi2.c: In function 'gdk_x11_device_xi2_select_window_events':
gdkdevice-xi2.c:627:15: warning: assignment makes pointer from integer without a cast
gdkdevice-xi2.c: At top level:
gdkdevice-xi2.c:637:1: error: conflicting types for '_gdk_x11_device_xi2_translate_event_mask'
gdkdevice-xi2.c:408:15: note: previous implicit declaration of '_gdk_x11_device_xi2_translate_event_mask' was here
gdkdevice-xi2.c:693:1: error: conflicting types for '_gdk_x11_device_xi2_translate_state'
gdkdevice-xi2.c:370:13: note: previous implicit declaration of '_gdk_x11_device_xi2_translate_state' was here
make[4]: *** [gdkdevice-xi2.lo] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gdk/x11'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/33]

```

---

### Post by oblocutor on 2011-02-12
> **moore.bryan said:**
> How 'bout this one?
```

CC     gdkdevice-xi2.lo
gdkdevice-xi2.c: In function 'gdk_x11_device_xi2_query_state':
gdkdevice-xi2.c:370:5: warning: implicit declaration of function '_gdk_x11_device_xi2_translate_state'
gdkdevice-xi2.c: In function 'gdk_x11_device_xi2_grab':
gdkdevice-xi2.c:408:3: warning: implicit declaration of function '_gdk_x11_device_xi2_translate_event_mask'
gdkdevice-xi2.c:408:13: warning: assignment makes pointer from integer without a cast
gdkdevice-xi2.c: In function 'gdk_x11_device_xi2_select_window_events':
gdkdevice-xi2.c:627:15: warning: assignment makes pointer from integer without a cast
gdkdevice-xi2.c: At top level:
gdkdevice-xi2.c:637:1: error: conflicting types for '_gdk_x11_device_xi2_translate_event_mask'
gdkdevice-xi2.c:408:15: note: previous implicit declaration of '_gdk_x11_device_xi2_translate_event_mask' was here
gdkdevice-xi2.c:693:1: error: conflicting types for '_gdk_x11_device_xi2_translate_state'
gdkdevice-xi2.c:370:13: note: previous implicit declaration of '_gdk_x11_device_xi2_translate_state' was here
make[4]: *** [gdkdevice-xi2.lo] Error 1
make[4]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gdk/x11'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bryan/gnome-shell/source/gtk3/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/33]

```

I think there's some old code left behind somewhere from the Gtk3 transition; erasing ~/gnome-shell and starting from scratch resolved this build error for me.

---

### Post by andrewthomas on 2011-02-12
> **Universal344 said:**
> Anyone else getting a gnome shell crash when you go to activities?
Mine crashes every time I go there.  
> **Universal344 said:**
>   if so do you know how to fix it?
I wish I knew.
Here is the beginning of the error that I get 
```

radeonSetSpanFunctions: bad format: 0x0002
radeonSetSpanFunctions: bad format: 0x0002
Shell killed with signal 11
./gnome-shell:534: Warning: g_variant_new_bytestring: assertion `string != NULL' failed
./gnome-shell:534: Warning: g_variant_new_variant: assertion `value != NULL' failed
./gnome-shell:534: Warning: g_variant_get_type: assertion `value != NULL' failed
./gnome-shell:534: Warning: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed
./gnome-shell:534: Warning: g_variant_builder_add_value: assertion `!GVSB(builder)->expected_type || g_variant_is_of_type (value, GVSB(builder)->expected_type)' failed
./gnome-shell:534: Warning: g_variant_builder_end: assertion `GVSB(builder)->offset >= GVSB(builder)->min_items' failed

```

---

### Post by andrewthomas on 2011-02-12
> **oblocutor said:**
> I think there's some old code left behind somewhere from the Gtk3 transition; erasing ~/gnome-shell and starting from scratch resolved this build error for me.
There is no reason to kill the entire directory, just the gtk3 source.

---

### Post by moore.bryan on 2011-02-12
> **oblocutor said:**
> I think there's some old code left behind somewhere from the Gtk3 transition; erasing ~/gnome-shell and starting from scratch resolved this build error for me.
I did this before, but am trying it again...

> **andrewthomas said:**
> There is no reason to kill the entire directory, just the gtk3 source.

Doesn't matter any way, now I get this when trying to get libcanberra:
```

*** Error during phase force_checkout of libcanberra: file hash is incorrect (expected 4b5d8d2c2835133620adbc53745dd107b6e58b9a2963059e8f457143fee00982, got 8231ee999a5e8471973809c6364484f9febd5078e3913afc6d2310e906fb7245) *** [14/33]

```

---

### Post by moore.bryan on 2011-02-12
Well, looks like all my problems went away. Successfully built on my Natty, Debian, and Fedora installs as of today.

---

### Post by psusi on 2011-02-12
I have been trying to get gnome3 to build for a few days.  I thought that the idea of jhbuild was that it installed everything to /opt where it would not interfere with gnome2, but it put some things in /usr/local.  When I rebooted, I had a messed up desktop that seemed to be caused by those parts in /usr/local being used instead of the gnome2 ones.  I even removed /usr/local from the PATH in /etc/environment and it did not help.  I finally had to delete /usr/local to get the system back to normal.

How are you guys managing to do this?

---

### Post by psusi on 2011-02-12
Ok, so I followed the instructions on the first page instead of the ones I got from gnome.org and I finally got it to actually build, but it fails to run with:


psusi@faldara:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
mutter: symbol lookup error: /home/psusi/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
psusi@faldara:~/gnome-shell/source/gnome-shell/src$ Cannot register the panel shell: there is already one running.

---

### Post by Quadunit404 on 2011-02-13
```
rm ~/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so
```

---

### Post by Merk42 on 2011-02-13
> **psusi said:**
> Ok, so I followed the instructions on the first page instead of the ones I got from gnome.org and I finally got it to actually build, but it fails to run with:


psusi@faldara:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
mutter: symbol lookup error: /home/psusi/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
psusi@faldara:~/gnome-shell/source/gnome-shell/src$ Cannot register the panel shell: there is already one running.

Read the entire first post...
Quadunit404 has the solution

---

### Post by MacUntu on 2011-02-13
I'm also trying to keep this answer at askubuntu.com up-to-date until we get a working PPA: [http://askubuntu.com/questions/22946/how-to-install-the-latest-gnome-3-build/25164#25164](http://askubuntu.com/questions/22946/how-to-install-the-latest-gnome-3-build/25164#25164)

If you need to update it, go ahead - it's a community answer, which anyone can edit.

---

### Post by keypox on 2011-02-13
built successful today.  Less errors too, just the 3 that I think everyone gets every time.   All documented with solutions, here and at [http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)

Still dog slow on nvidia though :(   I think i should try the nvidia patch again

---

### Post by Quadunit404 on 2011-02-14
Got the error, finally. Here's the full terminal output from launching the GS to the crash. (btw: I have an alias where gnome-shell runs ~/gnome-shell/install/bin/gnome-shell for easy launching)

```
tom@tom-laptop-linux:~$ gnome-shell --replace
Gtk-Message: Failed to load module "canberra-gtk-module"
Window manager warning: Log level 16: Accessibility: org.a11y.atspi schema not found. Are you sure that at-spi or at-spi2 is installed on your system?
Window manager warning: Log level 16: Accessibility: invalid module path (NULL)
Window manager warning: Log level 16: Accessibility: error loading the atk-bridge. Although the accessibility on the system is enabled and clutter accessibility is also enabled, accessibility support on GNOME Shell will not work
Panel leaving: a new panel shell is starting.

(gnome-panel:19650): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
Window manager warning: Log level 16: cannot register existing type `GdkWindow'
Window manager warning: Log level 8: g_once_init_leave: assertion `initialization_value != 0' failed
**
ERROR:gi/object.c:1256:gjs_define_object_class: assertion failed: (gtype != G_TYPE_INVALID)
Shell killed with signal 6

```

---

### Post by kainos on 2011-02-14
> **Quadunit404 said:**
> Got the error, finally. Here's the full terminal output from launching the GS to the crash. (btw: I have an alias where gnome-shell runs ~/gnome-shell/install/bin/gnome-shell for easy launching)

```
tom@tom-laptop-linux:~$ gnome-shell --replace
Gtk-Message: Failed to load module "canberra-gtk-module"
Window manager warning: Log level 16: Accessibility: org.a11y.atspi schema not found. Are you sure that at-spi or at-spi2 is installed on your system?
Window manager warning: Log level 16: Accessibility: invalid module path (NULL)
Window manager warning: Log level 16: Accessibility: error loading the atk-bridge. Although the accessibility on the system is enabled and clutter accessibility is also enabled, accessibility support on GNOME Shell will not work
Panel leaving: a new panel shell is starting.

(gnome-panel:19650): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
Window manager warning: Log level 16: cannot register existing type `GdkWindow'
Window manager warning: Log level 8: g_once_init_leave: assertion `initialization_value != 0' failed
**
ERROR:gi/object.c:1256:gjs_define_object_class: assertion failed: (gtype != G_TYPE_INVALID)
Shell killed with signal 6

```


I get the same error. Note: I get this error after executing rm ~/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so

---

### Post by NightwishFan on 2011-02-15
I had an error similar to that, I had to start fresh removing the install folder.

---

### Post by moore.bryan on 2011-02-15
I have found removing the gnome-shell dir completely **and** running jhbuild build -afc just to be sure usually gets rid of most errors...

---

### Post by Discospawn on 2011-02-15
Hi I just compiled gnome-shell from git with success, BUT when i type  ~/gnome-shell/install/bin/gnome-shell --replace gnome-panel starts. Anyone else got this problem?

---

### Post by Quadunit404 on 2011-02-15
Just successfully rebuilt GS - and so far I'm loving the new stuff :D

Still seems a bit crash-happy, though... most recent cause of a crash:

```
Window manager warning: Log level 16: invalid unclassed pointer in cast to `GObject'
Window manager warning: Log level 8: g_object_get_data: assertion `G_IS_OBJECT (object)' failed
Shell killed with signal 11

```

---

### Post by kainos on 2011-02-15
> **moore.bryan said:**
> I have found removing the gnome-shell dir completely **and** running jhbuild build -afc just to be sure usually gets rid of most errors...


Sometimes the simple solution works best. I did as you said and have my updated build in place now. I backed up the old directory just in case. But it worked great, thanks!

---

### Post by moore.bryan on 2011-02-15
Glad to hear you can now enjoy the GS most of us here love!

---

### Post by bmbaker on 2011-02-16
I don't know why but i keep getting this error in the build process the last 2 days!
has anyone any ideas?
Thanks
BB


Running ./configure --enable-maintainer-mode --prefix /home/brian/gnome-shell/install --libdir /home/brian/gnome-shell/install/lib --disable-static --disable-gtk-doc ...
configure: WARNING: unrecognized options: --disable-gtk-doc
checking for a BSD-compatible install... /home/brian/.local/bin/install-check
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
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
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for an ANSI C-conforming const... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for mallinfo... yes
checking for js-config... no
checking for JS... yes
checking for mozilla-js >= 1.9.2 ... yes
checking for JS_GetStringBytes in -lmozjs... no
checking for JS_GetFunctionName in -lmozjs... no
checking for JS_GetStringChars in -lmozjs... no
checking for mozilla-js >= 2 ... yes
checking for JS_FreezeObject in -lmozjs... yes
checking for JS_IsScriptFrame in -lmozjs... yes
checking for JS_EndPC in -lmozjs... yes
checking for JS_NewCompartmentAndGlobalObject in -lmozjs... yes
checking if SpiderMonkey needs extra compiler flags... yes
checking if -I/usr/include/xulrunner-2.0b12pre/unstable works... no
configure: error: Unable to determine extra compiler flags needed
*** Error during phase configure of gjs: ########## Error running ./autogen.sh --prefix /home/brian/gnome-shell/install --libdir '/home/brian/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [16/34]

---

### Post by bmbaker on 2011-02-16
?

---

### Post by NightwishFan on 2011-02-16
Try choosing "6" wipe directory and start over.

---

### Post by moore.bryan on 2011-02-16
@bmbaker: Are you trying to build on Ubuntu or Debian?

---

### Post by bmbaker on 2011-02-16
> **moore.bryan said:**
> @bmbaker: Are you trying to build on Ubuntu or Debian?

I have rebuilt the module 5 or 6 times now, rebuilt to scratch 3 times and its hangs at this point !

I am building in ubuntu 10.10

cheers 
BB

---

### Post by NightwishFan on 2011-02-16
There might be other issues then, perhaps a rebuild from scratch is needed.

---

### Post by bmbaker on 2011-02-16
> **NightwishFan said:**
> There might be other issues then, perhaps a rebuild from scratch is needed.

Ya i am doing again right now.
thanks for your replies :-)
BB

---

### Post by NightwishFan on 2011-02-16
With today's new changes it appears to be currently impossible to safely build the shell on Debian 6. You need the package "libtelepathy-glib-dev" of a newer version only found in experimental, and in order to upgrade to this package you are forced to remove several essential packages. (It is certainly possible to do this, which is why I said "safely build")

Yes yes I know this is Ubuntu forums, it is just what affects one hand might affect the other as they are so alike. ;)

---

### Post by bmbaker on 2011-02-16
well it finally installed :-)

but i don't see the new automatic workspaces !
is there something i am missing ?
Thanks
BB

---

### Post by Quadunit404 on 2011-02-16
To create a workspace:

1. Open up a window
2. Drag it to the Workspaces sidebar in Activities view
3. ???
4. Profit

---

### Post by NightwishFan on 2011-02-16
Should be on the right when you are in the overview mode.

---

### Post by bmbaker on 2011-02-16
nope its not there on the right.
to access multiple wk spaces i have to go into activities and add them manually!

---

### Post by bmbaker on 2011-02-16
this is what i was expecting !!

[HTML]https://lh4.googleusercontent.com/_1QSDkzYY2vc/TVMP7gNOdQI/AAAAAAAAC40/gPZbGrzmDd8/s500/Workspace%201_001.png[/HTML]

---

### Post by Merk42 on 2011-02-16
> **bmbaker said:**
> this is what i was expecting !!

[HTML]https://lh4.googleusercontent.com/_1QSDkzYY2vc/TVMP7gNOdQI/AAAAAAAAC40/gPZbGrzmDd8/s500/Workspace%201_001.png[/HTML]
That's what it should be. The images in the first post of this thread are of a 10.10 installation.
Maybe you need to delete gnome-shell and source folders and the gnome-shell-build-setup.sh file and do everything in the OP all over again?

Or maybe your mirror is out of date and doesn't have the newer workspaces?

---

### Post by NightwishFan on 2011-02-16
Agreed, I built on 10.04 10.10 and Debian 6 and I get the new workspace logic. For each I followed the instructions in the first post of this thread.

---

### Post by bmbaker on 2011-02-16
> **Merk42 said:**
> That's what it should be. The images in the first post of this thread are of a 10.10 installation.
Maybe you need to delete gnome-shell and source folders and the gnome-shell-build-setup.sh file and do everything in the OP all over again?

Or maybe your mirror is out of date and doesn't have the newer workspaces?

hmmmm ............. and how would i go about changing the 'mirror' ?
i used the instructions etc from the first post in this thread.

thanks
BB

---

### Post by puntigamer on 2011-02-16
while compiling gnome shell from git, i got the following error:

checking if -I/usr/include/xulrunner-2.0b12pre/unstable works... no
configure: error: Unable to determine extra compiler flags needed

Any tips, how could I get and install that xulrunner version?

---

### Post by bmbaker on 2011-02-16
bump :-)

i have deleted everything including jhbuild and i do from scratch as per first post ... again !!

what or how do i change the mirror site??

cheers
BB

---

### Post by njined on 2011-02-16
In Natty it appears much more stable over unity.

---

### Post by puntigamer on 2011-02-16
Me to, for the compiled one, when I would like to switch windows... 
The version from the packpage manager is ok.

---

### Post by Daveth on 2011-02-16
are you following these instructions?

[HTML]http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html[/HTML]

---

### Post by cariboo on 2011-02-16
Merged with the gnome shell thread in Natty Testing & Discussion

---

### Post by NightwishFan on 2011-02-16
Update: Seems they caught the issue, jhbuild now builds libtelepathy :)

---

### Post by bmbaker on 2011-02-17
Finally !! i got it to work :-)
i did a total re-install of ubuntu 10.10 from the ground up and worked through each step of setting up gnome shell from git, and jhbuild from git again with sanitycheck and then bootstrap and all is functioning brilliatly :-)
thanks for all the great posts on this thread.
cheers 
BB:guitar:

---

### Post by andrewthomas on 2011-02-17
On one of my installs I am missing the menu bar in nautilus and gnome-terminal.  

What could be the problem?

---

### Post by NightwishFan on 2011-02-17
EDIT:

You might have appmenu installed. Check synaptic to see if you have appmenu installed.

Otherwise, right click the terminal and choose "show menubar". See if that works.

---

### Post by keypox on 2011-02-17
nice article with links to live gnome shell cds here [http://maketecheasier.com/gnome-shell-is-almost-ready-to-rock-your-desktop/2011/02/17](http://maketecheasier.com/gnome-shell-is-almost-ready-to-rock-your-desktop/2011/02/17)

---

### Post by keypox on 2011-02-17
I just tryed using both monitors with gnome shell and the animations are super smooth with both enabled...

---

### Post by andrewthomas on 2011-02-18
> **NightwishFan said:**
> EDIT:

You might have appmenu installed. Check synaptic to see if you have appmenu installed.

Otherwise, right click the terminal and choose "show menubar". See if that works.

appmenu-gtk is installed and show menubar has a check.

---

### Post by NightwishFan on 2011-02-18
I would try removing appmenu perhaps.

---

### Post by andrewthomas on 2011-02-18
> **NightwishFan said:**
> I would try removing appmenu perhaps.
Removing appmenu-gtk did the trick.

Thanks.

I do have the same package on the other install and it works like it should.  Go figure.

---

### Post by kainos on 2011-02-19
> **NightwishFan said:**
> I would try removing appmenu perhaps.

Cool, I did that and it fixed my absent menu issues in Audacity. No more export UBUNTU_MENUPROXY=0 in the terminal before starting. Thanks.

---

### Post by moore.bryan on 2011-02-19
Does anyone else experience your "systray" icons randomly disappearing?

---

### Post by Tompalaz on 2011-02-20
When I run GS, the network manager can randomly die and cut my wireless.
Can't get it to connect again unless I kill X and log in again.

The new network manager in GS (I guess it's just a new interface) can't connect to my wireless either. I can see all the SSIDs nearby though.

---

### Post by plun on 2011-02-20
Up and running after a loooooooong build......what a relief with something rather stable.

gnome-control-center cannot be build as I can see, also the canberra-trouble.
No problem nevertheless.

Where can I find updated themes for GS ?  I can only find outdated themes.

---

### Post by Mblackwell on 2011-02-20
> **Tompalaz said:**
> When I run GS, the network manager can randomly die and cut my wireless.
Can't get it to connect again unless I kill X and log in again.

The new network manager in GS (I guess it's just a new interface) can't connect to my wireless either. I can see all the SSIDs nearby though.

In Shell it's still using nm-applet. There's a patch to move some of the functionality out into a proper systray icon (with nm-applet as a background process) but it hasn't landed. So what I'm saying is... it doesn't make sense to say that it's GNOME Shell's fault.

---

### Post by puntigamer on 2011-02-20
I really like Gnome-Shell, but the daily bulids system settings menu is somehow very primitive and unusable by me, unlike in the Shell from the repo. 
Is it so for you too?

---

### Post by puntigamer on 2011-02-20
> **moore.bryan said:**
> Does anyone else experience your "systray" icons randomly disappearing?
Yes, I'm :( And my Shell crashes on the activities menu, without the closed source video driver...

---

### Post by puntigamer on 2011-02-20
> **Daveth said:**
> are you following these instructions?

[HTML]http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html[/HTML]
Yes, it should be a video card driver issue.
I tried to install the ATI driver, and after a few login it seens to be ok, no crashes, but the icons are smaller and the windows panel like to go crazy :)

---

### Post by puntigamer on 2011-02-20
> **bmbaker said:**
> I don't know why but i keep getting this error in the build process the last 2 days!
has anyone any ideas?
Thanks
BB


```
Running ./configure --enable-maintainer-mode --prefix /home/brian/gnome-shell/install --libdir /home/brian/gnome-shell/install/lib --disable-static --disable-gtk-doc ...
configure: WARNING: unrecognized options: --disable-gtk-doc
checking for a BSD-compatible install... /home/brian/.local/bin/install-check
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
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
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for an ANSI C-conforming const... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for mallinfo... yes
checking for js-config... no
checking for JS... yes
checking for mozilla-js >= 1.9.2 ... yes
checking for JS_GetStringBytes in -lmozjs... no
checking for JS_GetFunctionName in -lmozjs... no
checking for JS_GetStringChars in -lmozjs... no
checking for mozilla-js >= 2 ... yes
checking for JS_FreezeObject in -lmozjs... yes
checking for JS_IsScriptFrame in -lmozjs... yes
checking for JS_EndPC in -lmozjs... yes
checking for JS_NewCompartmentAndGlobalObject in -lmozjs... yes
checking if SpiderMonkey needs extra compiler flags... yes
checking if -I/usr/include/xulrunner-2.0b12pre/unstable works... no
configure: error: Unable to determine extra compiler flags needed
*** Error during phase configure of gjs: ########## Error running ./autogen.sh --prefix /home/brian/gnome-shell/install --libdir '/home/brian/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [16/34]
purge the Mozilla Daily PPA (if you have it installed), and install Xulrunner-19.2-devsuite and its ~dev packpages ;)
```

---

### Post by moore.bryan on 2011-02-23
> **puntigamer said:**
> Yes, I'm :( And my Shell crashes on the activities menu, without the closed source video driver...

Do we know if this is getting fixed any time soon?

---

### Post by NightwishFan on 2011-02-23
> **moore.bryan said:**
> Do we know if this is getting fixed any time soon?

Perhaps check the gnome bugzilla for reports on the issue. The shell seems pretty easy to debug, so it probably will be fixed. :)

---

### Post by moore.bryan on 2011-02-23
> **NightwishFan said:**
> Perhaps check the gnome bugzilla for reports on the issue. The shell seems pretty easy to debug, so it probably will be fixed. :)

Thanks, checked there and there's no entry about it at all. Ironically, as I was looking at the Bugzilla page, my icons came back. ;-)

On another note, some of my programs are showing-up as doubles in GS's overview... even those that *do not* have double .desktop entries. Any ideas there?

---

### Post by NightwishFan on 2011-02-23
In Debian I have to remove a package called menu-xdg to get rid of duplicate entries. I never had to in Ubuntu.

---

### Post by Merk42 on 2011-02-23
[GNOME Shell 2.91.90 released](http://mail.gnome.org/archives/gnome-shell-list/2011-February/msg00196.html)
Updated the pictures in [the OP](http://ubuntuforums.org/showpost.php?p=10015153&postcount=1) to reflect the slight UI changes.

If Canonical moving the buttons to the left caused an uproar, I wonder how people will take what GNOME has done with the buttons.

---

### Post by moore.bryan on 2011-02-23
Thanks for that one... trying it now.

Just finished building from scratch and have a *transparent* panel. Not sure I like it...

---

### Post by NightwishFan on 2011-02-23
Woah... That is certainly odd.

---

### Post by bruce89 on 2011-02-23
> **Merk42 said:**
> If Canonical moving the buttons to the left caused an uproar, I wonder how people will take what GNOME has done with the buttons.

Arguably minimise doesn't make sense in gnome-shell due to the lack of a window list, whereas moving buttons made no difference (in either direction I may add)

> **moore.bryan said:**
> Just finished building from scratch and have a *transparent* panel. Not sure I like it...

That's definately not supposed to happen.

---

### Post by moore.bryan on 2011-02-24
> **NightwishFan said:**
> Woah... That is certainly odd.

> **bruce89 said:**
> Arguably minimise doesn't make sense in gnome-shell due to the lack of a window list, whereas moving buttons made no difference (in either direction I may add)



That's definately not supposed to happen.

Thanks for confirmation this is *not* normal; however, I've restarted three times and rebuilt twice and it's still that way. A new feature secretly tested on just me? I'm so special... ;-)

---

### Post by ronacc on 2011-02-24
when you figure out how you got the transparent panel let me know I prefer it that way , rebuilding now to see if I can get lucky too :lolflag:

---

### Post by dext on 2011-02-24
what Version of Gnome-panel do you have?

---

### Post by ronacc on 2011-02-24
> **dext said:**
> what Version of Gnome-panel do you have?

1.2.32.1-0ubuntu6

---

### Post by dext on 2011-02-24
> **ronacc said:**
> 1.2.32.1-0ubuntu6

you need the Gnome3 Panel which is [gnome3 gnome-panel]("ftp://ftp.gnome.org/pub/GNOME/sources/gnome-panel/2.91/")  im assuming by having 2.32 panel thats how he got transparent panel. just wondering if by any chance he had it on transparent before he did a re-build from jhbuild cause i dont recall being able to transparent the 2.91.xx panel

---

### Post by ronacc on 2011-02-24
I set my panel (2.32) to transparent before rebuild , no help , still don't have transparent in GS. I d/l'd the one from your link and I'll play with that tomorrow , it's a 1/4 to a pumpkin here so I'm shutting down for the night .

---

### Post by moore.bryan on 2011-02-25
> **ronacc said:**
> when you figure out how you got the transparent panel let me know I prefer it that way , rebuilding now to see if I can get lucky too :lolflag:
I've decided I'm not a fan of it, so you can have mine. ;-)

> **dext said:**
> what Version of Gnome-panel do you have?
2.30.2-3

> **dext said:**
> you need the Gnome3 Panel which is [gnome3 gnome-panel]("ftp://ftp.gnome.org/pub/GNOME/sources/gnome-panel/2.91/")  im assuming by having 2.32 panel thats how he got transparent panel. just wondering if by any chance he had it on transparent before he did a re-build from jhbuild cause i dont recall being able to transparent the 2.91.xx panel
I never had gnome-panel set to transparency, so why would that affect GNOME Shell?

EDIT:
Hmm... on a hunch, I looked in gconf-editor for anything related to gnome-panel and found under desktop>gnome>session>required_components>panel, nothing was listed. Changed it to read "gnome-panel," like it should, but am currently in a complete rebuild, so I have to wait for that to happen until I check to see if that fixed my error.

@ronacc: If the gconf setting is what made it transparent, I'll share the secret code and decoder ring with you. ;-)

---

### Post by xtoudi on 2011-02-25
You want transparent panel ?? Sth like this in attached pics??

It's so simple !!
You need to edit file **gnome-shell.css**. Lines at: /* Panel */

And here it is after modification: line with **background-color:** (the old one is with black and the second one is transparent). Additionally you have to comment **border-image** line - it's because this svg file contains black color as background - should be transparent color - this is bug in my opinion. This svg file it is nice thin border below panel.

0.6 is the amount of transparency.

```
#panel {
    color: #ffffff;
    /*background-color: black;*/
    background-color: rgba(0,0,0,0.6);
    /*border-image: url("panel-border.svg") 1;*/
}
```

---

### Post by moore.bryan on 2011-02-25
@xtoudi: my gnome-shell.css **is not** set-up for transparency, so I'm really not sure why the panel's transparent. 

Also, I've rebooted several times, setting gnome-panel in gconf-editor and there's no change. Apparently, I'm stuck with transparency for now... I think the reason I really hate it is the little black pieces in the attached screenshot. Perhaps that's the svg xtoudi mentioned...

EDIT:
Okay, commenting-out the svg reference gives me back my black panel; however, the "main" window is still rounded in the top right and left corners. Now, it's time to dig into the css! Wish me luck!!!

EDIT 2:
That was quick... looks like it was simpler than I expected; thanks GNOME Shell devs for not making it more complicated than it needed to be. In the gnome-shell.css file, under the Panel section, I altered the .panel-corner css to reflect 0px -panel-corner-radius.

Before:
```

.panel-corner {
    -panel-corner-radius: 10px;
    -panel-corner-background-color: black;
    -panel-corner-inner-border-width: 2px;
    -panel-corner-inner-border-color: transparent;
    -panel-corner-outer-border-width: 1px;
    -panel-corner-outer-border-color: #536272;

```
After:
```

.panel-corner {
    -panel-corner-radius: 0px;
    -panel-corner-background-color: black;
    -panel-corner-inner-border-width: 2px;
    -panel-corner-inner-border-color: transparent;
    -panel-corner-outer-border-width: 1px;
    -panel-corner-outer-border-color: #536272;

```
Still having the notification area icons sometimes show-up and sometimes not, though.... Any ideas there?

---

### Post by ronacc on 2011-02-25
thanks xtoudi I'll give that a try as soon as my rebuild finishes , for some reason GS wouldn't start after todays updates, so I'm rebuilding .

---

### Post by ronacc on 2011-02-25
Ok my rebuild finished and I applied xtoudi's fix ,it works , I adjusted the transparency to 0.1 instead of 0.6  .

---

### Post by gooeykablooey on 2011-02-25
> **moore.bryan said:**
> 
EDIT 2:
That was quick... looks like it was simpler than I expected; thanks GNOME Shell devs for not making it more complicated than it needed to be. In the gnome-shell.css file, under the Panel section, I altered the .panel-corner css to reflect 0px -panel-corner-radius.

Before:
```

.panel-corner {
    -panel-corner-radius: 10px;
    -panel-corner-background-color: black;
    -panel-corner-inner-border-width: 2px;
    -panel-corner-inner-border-color: transparent;
    -panel-corner-outer-border-width: 1px;
    -panel-corner-outer-border-color: #536272;

```After:
```

.panel-corner {
    -panel-corner-radius: 0px;
    -panel-corner-background-color: black;
    -panel-corner-inner-border-width: 2px;
    -panel-corner-inner-border-color: transparent;
    -panel-corner-outer-border-width: 1px;
    -panel-corner-outer-border-color: #536272;

```Still having the notification area icons sometimes show-up and sometimes not, though.... Any ideas there?

Sweet, I was wondering how to get rid of those little corners. I don't have a transparent panel, but that was still bugging me.

---

### Post by xtoudi on 2011-02-26
> **gooeykablooey said:**
> Sweet, I was wondering how to get rid of those little corners. I don't have a transparent panel, but that was still bugging me.

Comment all section, like here:

```
.panel-corner {
 /*   -panel-corner-radius: 10px;
    -panel-corner-background-color: black;
     -panel-corner-inner-border-width: 2px;
    -panel-corner-inner-border-color: transparent;
    -panel-corner-outer-border-width: 1px;
    -panel-corner-outer-border-color: #536272;*/
}
```

---

### Post by moore.bryan on 2011-02-26
Still seeing buggy notification icons; sometimes they show, sometimes they don't. Is anyone still having this issue?

---

### Post by pigusek on 2011-02-27
If you have got problem with
```

mutter: symbol lookup error: /home/pigi/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
pigi@pigi-gateway:~/gnome-shell/source/gnome-shell/src$ Cannot register the panel shell: there is already one running.
pigi@pigi-gateway:~/gnome-shell/source/gnome-shell/src$ Backend     : ini

```

while running or sth, the solution [rather workaround] is here:

[http://mail.gnome.org/archives/gnome-shell-list/2011-February/msg00137.html](http://mail.gnome.org/archives/gnome-shell-list/2011-February/msg00137.html)

jhbuild build --no-network gnome-shell

---

### Post by bmbaker on 2011-02-28
i was just testing for rebuilding from scratch, and i got this message:
[HTML]brian@Dreamer:~$ curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  7518  100  7518    0     0  10143      0 --:--:-- --:--:-- --:--:-- 17009
brian@Dreamer:~$ /bin/bash gnome-shell-build-setup.sh
Please run 'sudo apt-get install xulrunner-dev ' and try again.[/HTML]

so i installed the xulrunner-dev and now it gives me this:
[HTML]CXX    libgjs_la-jsapi-private.lo
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from /usr/include/xulrunner-2.0b13pre/pratom.h:46,
                 from /usr/include/xulrunner-2.0b13pre/jslock.h:47,
                 from /usr/include/xulrunner-2.0b13pre/jsstr.h:55,
                 from /usr/include/xulrunner-2.0b13pre/jsatom.h:52,
                 from /usr/include/xulrunner-2.0b13pre/jscntxt.h:59,
                 from gjs/jsapi-private.cpp:35:
/usr/include/xulrunner-2.0b13pre/prtypes.h:517: fatal error: obsolete/protypes.h: No such file or directory
compilation terminated.
make[1]: *** [libgjs_la-jsapi-private.lo] Error 1
make[1]: Leaving directory `/home/brian/gnome-shell/source/gjs'
make: *** [all] Error 2
*** Error during phase build of gjs: ########## Error running make   *** [16/35]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"[/HTML]

so i reinstalled  xulrunner-1.9.2-dev
and did #6 
it runs and then i get this:

[HTML]collect2: ld returned 1 exit status
make[3]: *** [run-js-test] Error 1
make[3]: Leaving directory `/home/brian/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/brian/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brian/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [32/35]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"[/HTML]

---

### Post by bmbaker on 2011-02-28
Andrew from Web Upd8 said:
"So you're using the Mozilla daily PPA, right? 

To get it working you need to completely remove the folder and start over. Install xulrunner-dev, and run the following steps:


curl -O [http://git.gnome.org/browse/gn...]("http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh")
export PATH=$PATH:/home/YOUR_USERNAME/bin #replace YOUR_USERNAME with your username
cd
chmod +x [gnome-shell-build-setup.sh]("http://gnome-shell-build-setup.sh/")
./[gnome-shell-build-setup.sh]("http://gnome-shell-build-setup.sh/")


And then, before starting to build Gnome Shell, install xulrunner-1.9.2-dev:
sudo apt-get install xulrunner-1.9.2-dev

Then you can start building Gnome Shell:
jhbuild build


This works for me.      "




> **bmbaker said:**
> i was just testing for rebuilding from scratch, and i got this message:
[HTML]brian@Dreamer:~$ curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  7518  100  7518    0     0  10143      0 --:--:-- --:--:-- --:--:-- 17009
brian@Dreamer:~$ /bin/bash gnome-shell-build-setup.sh
Please run 'sudo apt-get install xulrunner-dev ' and try again.[/HTML]so i installed the xulrunner-dev and now it gives me this:
[HTML]CXX    libgjs_la-jsapi-private.lo
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from /usr/include/xulrunner-2.0b13pre/pratom.h:46,
                 from /usr/include/xulrunner-2.0b13pre/jslock.h:47,
                 from /usr/include/xulrunner-2.0b13pre/jsstr.h:55,
                 from /usr/include/xulrunner-2.0b13pre/jsatom.h:52,
                 from /usr/include/xulrunner-2.0b13pre/jscntxt.h:59,
                 from gjs/jsapi-private.cpp:35:
/usr/include/xulrunner-2.0b13pre/prtypes.h:517: fatal error: obsolete/protypes.h: No such file or directory
compilation terminated.
make[1]: *** [libgjs_la-jsapi-private.lo] Error 1
make[1]: Leaving directory `/home/brian/gnome-shell/source/gjs'
make: *** [all] Error 2
*** Error during phase build of gjs: ########## Error running make   *** [16/35]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"[/HTML]so i reinstalled  xulrunner-1.9.2-dev
and did #6 
it runs and then i get this:

[HTML]collect2: ld returned 1 exit status
make[3]: *** [run-js-test] Error 1
make[3]: Leaving directory `/home/brian/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/brian/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brian/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [32/35]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"[/HTML]

---

### Post by andrewthomas on 2011-02-28
After rebuilding I could no longer log out due to 'gnome-session-quit' not found.

What I did was to build gnome-session from git

```
cd gnome-shell/source
git clone git://git.gnome.org/gnome-session
cd gnome-session
./autogen.sh
./configure --prefix /home/andrew_shell/gnome-shell/install --libdir /home/andrew_shell/gnome-shell/install/lib64 --disable-static --disable-gtk-doc
make 
make install
```now it is back to normal

---

### Post by bmbaker on 2011-02-28
tried that and it didn't wk for me :(

---

### Post by andrewthomas on 2011-02-28
> **bmbaker said:**
> tried that and it didn't wk for me :(

Did you change 
```
./configure --prefix /home/andrew_shell/gnome-shell/install --libdir home/andrew_shell/gnome-shell/install/lib64 --disable-static  --disable-gtk-doc
```to correspond to **your username** and lib directory (if not on amd64) ?

---

### Post by bmbaker on 2011-02-28
yes i did change my username and lib* instead of lib64
doing a fresh install now will see after if this fixs it :)


> **andrewthomas said:**
> Did you change 
```
./configure --prefix /home/andrew_shell/gnome-shell/install --libdir home/andrew_shell/gnome-shell/install/lib64 --disable-static  --disable-gtk-doc
```to correspond to **your username** and lib directory (if not on amd64) ?

---

### Post by TheAxeR on 2011-02-28
bmbaker are you still dealing with the xulrunner issue? If you are using the Mozilla Daily PPA I just figured out how to get around it. The folder structure for /usr/include/xulrunner-2.0b13pre/ seems to be different than expected.  I solved the issue by creating the folder /usr/include/xulrunner-2.0b13pre/obsolete and linking in the files from /usr/include/xulrunner-2.0b13pre/nspr/obsolete   I then changed the names to remove the "link to " portion.  GJS now builds properly for me.

---

### Post by andrewthomas on 2011-02-28
> **bmbaker said:**
> yes i did change my username and lib* instead of lib64
doing a fresh install now will see after if this fixs it :)
If you rebuild gnome-bluetooth, you may have to revert commit 
[082db0a06fec0839813f4d54288015df292a617c]("http://git.gnome.org/browse/gnome-bluetooth/commit/?id=082db0a06fec0839813f4d54288015df292a617c")
to get it to build.

EDIT: I also had to edit the gnome-themes-standard/configure.ac file
at line 44
```

AC_CONFIG_FILES([[FONT=monospace]
[/FONT]Makefile
themes/Makefile 
themes/Adwaita/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/backgrounds/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/cursors/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/gtk-2.0/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/gtk-3.0/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/metacity-1/Makefile[FONT=monospace]
[/FONT]themes/AdwaitaLowContrast/Makefile
themes/AdwaitaLowContrast/gtk-3.0/Makefile

``` the last two lines to ```

themes/LowContrast/Makefile
themes/LowContrast/gtk-3.0/Makefile

``` due to
Rename AdwaitaLowContrast to LowContrast
[e36d5c117f214b62442eabef2a614db6e0d8d40b]("http://git.gnome.org/browse/gnome-themes-standard/commit/?id=e36d5c117f214b62442eabef2a614db6e0d8d40b")

---

### Post by bmbaker on 2011-02-28
yes i have just run into this now, thanks for the heads up, I will call it a night for tonight and attack this again tomorrow :-)

> **andrewthomas said:**
> If you rebuild gnome-bluetooth, you may have to revert commit 
[082db0a06fec0839813f4d54288015df292a617c]("http://git.gnome.org/browse/gnome-bluetooth/commit/?id=082db0a06fec0839813f4d54288015df292a617c")
to get it to build.

EDIT: I also had to edit the gnome-themes-standard/configure.ac file
at line 44
```

AC_CONFIG_FILES([[FONT=monospace]
[/FONT]Makefile
themes/Makefile 
themes/Adwaita/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/backgrounds/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/cursors/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/gtk-2.0/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/gtk-3.0/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/metacity-1/Makefile[FONT=monospace]
[/FONT]themes/AdwaitaLowContrast/Makefile
themes/AdwaitaLowContrast/gtk-3.0/Makefile

``` the last two lines to ```

themes/LowContrast/Makefile
themes/LowContrast/gtk-3.0/Makefile

``` due to
Rename AdwaitaLowContrast to LowContrast
[e36d5c117f214b62442eabef2a614db6e0d8d40b]("http://git.gnome.org/browse/gnome-themes-standard/commit/?id=e36d5c117f214b62442eabef2a614db6e0d8d40b")

---

### Post by canga on 2011-02-28
I built a 10.10 system from scratch yesterday, applied the latest updates and then followed the OP of this forum to build gnome shell - all of this worked satisfactorily and I was able to try shell for the first time.  Didn&#901;t run for long before crashing, and at that point so did I.

Today, I ran jhbuild again which failed to complete.  I followed this advice:
> **andrewthomas said:**
> If you rebuild gnome-bluetooth, you may have to revert commit 
[082db0a06fec0839813f4d54288015df292a617c]("http://git.gnome.org/browse/gnome-bluetooth/commit/?id=082db0a06fec0839813f4d54288015df292a617c")
to get it to build.

EDIT: I also had to edit the gnome-themes-standard/configure.ac file
at line 44
```

AC_CONFIG_FILES([[FONT=monospace]
[/FONT]Makefile
themes/Makefile 
themes/Adwaita/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/backgrounds/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/cursors/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/gtk-2.0/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/gtk-3.0/Makefile[FONT=monospace]
[/FONT]themes/Adwaita/metacity-1/Makefile[FONT=monospace]
[/FONT]themes/AdwaitaLowContrast/Makefile
themes/AdwaitaLowContrast/gtk-3.0/Makefile

``` the last two lines to ```

themes/LowContrast/Makefile
themes/LowContrast/gtk-3.0/Makefile

``` due to
Rename AdwaitaLowContrast to LowContrast
[e36d5c117f214b62442eabef2a614db6e0d8d40b]("http://git.gnome.org/browse/gnome-themes-standard/commit/?id=e36d5c117f214b62442eabef2a614db6e0d8d40b")
which allowed the update of gnome-themes-standard (thanks to andrewthomas).  However the build does not run to completion due to this error:
```

*** Building gnome-shell *** [32/35]
make  
make  all-recursive
make[1]: Entering directory `/home/wl/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/home/wl/gnome-shell/source/gnome-shell/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/wl/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/home/wl/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/wl/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/home/wl/gnome-shell/source/gnome-shell/src'
make  all-am
make[3]: Entering directory `/home/wl/gnome-shell/source/gnome-shell/src'
  CC     libgdmuser_1_0_la-gdm-user.lo
  CC     libgdmuser_1_0_la-gdm-user-manager.lo
  CCLD   libgdmuser-1.0.la
  CC     libst_1_0_la-st-adjustment.lo
  CC     libst_1_0_la-st-bin.lo
  CC     libst_1_0_la-st-box-layout.lo
  CC     libst_1_0_la-st-box-layout-child.lo
  CC     libst_1_0_la-st-button.lo
  CC     libst_1_0_la-st-container.lo
  CC     libst_1_0_la-st-drawing-area.lo
  CC     libst_1_0_la-st-entry.lo
  CC     libst_1_0_la-st-focus-manager.lo
  CC     libst_1_0_la-st-group.lo
  CC     libst_1_0_la-st-icon.lo
  CC     libst_1_0_la-st-im-text.lo
  CC     libst_1_0_la-st-label.lo
  CC     libst_1_0_la-st-overflow-box.lo
  CC     libst_1_0_la-st-private.lo
  CC     libst_1_0_la-st-scroll-bar.lo
  CC     libst_1_0_la-st-scroll-view.lo
  CC     libst_1_0_la-st-table.lo
  CC     libst_1_0_la-st-table-child.lo
  CC     libst_1_0_la-st-texture-cache.lo
  CC     libst_1_0_la-st-theme-context.lo
  CC     libst_1_0_la-st-theme-node.lo
  CC     libst_1_0_la-st-theme-node-drawing.lo
  CC     libst_1_0_la-st-theme-node-transition.lo
  CC     libst_1_0_la-st-tooltip.lo
  CC     libst_1_0_la-st-widget.lo
  CC     libst_1_0_la-st-scroll-view-fade.lo
  CC     libst_1_0_la-st-enum-types.lo
  CCLD   libst-1.0.la
  CC     libtray_la-na-tray-child.lo
  CC     libtray_la-na-tray-manager.lo
  CCLD   libtray.la
  CC     libjs_test_la-shell-generic-container.lo
  CCLD   libjs-test.la
  CC     libgnome_shell_la-shell-enum-types.lo
  CC     libgnome_shell_la-gnome-shell-plugin.lo
  CC     libgnome_shell_la-shell-app.lo
  CC     libgnome_shell_la-shell-app-system.lo
  CC     libgnome_shell_la-shell-app-usage.lo
  CC     libgnome_shell_la-shell-arrow.lo
  CC     libgnome_shell_la-shell-doc-system.lo
  CC     libgnome_shell_la-shell-embedded-window.lo
  CC     libgnome_shell_la-shell-generic-container.lo
  CC     libgnome_shell_la-shell-gtk-embed.lo
  CC     libgnome_shell_la-shell-global.lo
  CC     libgnome_shell_la-shell-slicer.lo
  CC     libgnome_shell_la-shell-stack.lo
  CC     libgnome_shell_la-shell-tray-icon.lo
  CC     libgnome_shell_la-shell-tray-manager.lo
  CC     libgnome_shell_la-shell-util.lo
  CC     libgnome_shell_la-shell-window-tracker.lo
  CC     libgnome_shell_la-shell-wm.lo
  CC     libgnome_shell_la-shell-xfixes-cursor.lo
  CCLD   libgnome-shell.la
  CC     gnome_shell_calendar_server-calendar-sources.o
  CC     gnome_shell_calendar_server-gnome-shell-calendar-server.o
cc1: warnings being treated as errors
calendar-server/gnome-shell-calendar-server.c: In function ‘app_load_events’:
calendar-server/gnome-shell-calendar-server.c:603: error: implicit declaration of function ‘e_cal_view_stop’
make[3]: *** [gnome_shell_calendar_server-gnome-shell-calendar-server.o] Error 1
make[3]: Leaving directory `/home/wl/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/wl/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/wl/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [32/35]

```

Does anyone know how to proceed here?

---

### Post by canga on 2011-03-01
I have looked a bit deeper.

The function ‘e_cal_view_stop’ is defined in /usr/include/evolution-data-server-2.3x/libecal/e-cal-view.h from version 2.32, but the version installed with maverick's evolution-data-server-dev package is version 2.30 and the function isn't defined there.

It appears that I need to install version 2.32 of evolution-data-server-dev (and maybe others?) to be able to proceed.  Is this correct?  If so, how do I do this?

---

### Post by zachtib on 2011-03-01
> **canga said:**
> I have looked a bit deeper.

The function &#8216;e_cal_view_stop&#8217; is defined in /usr/include/evolution-data-server-2.3x/libecal/e-cal-view.h from version 2.32, but the version installed with maverick's evolution-data-server-dev package is version 2.30 and the function isn't defined there.

It appears that I need to install version 2.32 of evolution-data-server-dev (and maybe others?) to be able to proceed.  Is this correct?  If so, how do I do this?

I found a ppa that has evolution 2.32 for maverick, might help. I'm about to try it: [https://launchpad.net/~suraia/+archive/ppa](https://launchpad.net/~suraia/+archive/ppa)

EDIT: Bah. Didn't help.

---

### Post by andrewthomas on 2011-03-01
> **canga said:**
> I have looked a bit deeper.

The function ‘e_cal_view_stop’ is defined in /usr/include/evolution-data-server-2.3x/libecal/e-cal-view.h from version 2.32, but the version installed with maverick's evolution-data-server-dev package is version 2.30 and the function isn't defined there.

It appears that I need to install version 2.32 of evolution-data-server-dev (and maybe others?) to be able to proceed.  Is this correct?  If so, how do I do this?
Download the natty source:

[http://packages.ubuntu.com/source/natty/evolution-data-server](http://packages.ubuntu.com/source/natty/evolution-data-server)

then configure, make & then use checkinstall to build a .deb & install

---

### Post by bmbaker on 2011-03-01
I am still quite new to this can you give an expanded help on how to configure, make & then use checkinstall to build a .deb & install please :-)



> **andrewthomas said:**
> Download the natty source:

[http://packages.ubuntu.com/source/natty/evolution-data-server](http://packages.ubuntu.com/source/natty/evolution-data-server)

then configure, make & then use checkinstall to build a .deb & install

---

### Post by bmbaker on 2011-03-01
this went a little over my head I am afraid, but thank you. I used a different solution that i posted earlier that worked as well. :-)
> **TheAxeR said:**
> bmbaker are you still dealing with the xulrunner issue? If you are using the Mozilla Daily PPA I just figured out how to get around it. The folder structure for /usr/include/xulrunner-2.0b13pre/ seems to be different than expected.  I solved the issue by creating the folder /usr/include/xulrunner-2.0b13pre/obsolete and linking in the files from /usr/include/xulrunner-2.0b13pre/nspr/obsolete   I then changed the names to remove the "link to " portion.  GJS now builds properly for me.

---

### Post by javipas on 2011-03-01
I'm trying to compile GNOME 3 on my Ubuntu 10.10 32 bits, but no luck as of now. 

The process tops at [10/35]:

[I][COLOR="DarkRed"]Running automake-1.11...
configure.ac:4: warning: AC_INIT: not a literal: [http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-themes-standard](http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-themes-standard)
configure.ac:44: required file `themes/AdwaitaLowContrast/Makefile.in' not found
configure.ac:44: required file `themes/AdwaitaLowContrast/gtk-3.0/Makefile.in' not found
*** Error during phase configure of gnome-themes-standard: ########## Error running ./autogen.sh --prefix /home/javipas/gnome-shell/install --libdir '/home/javipas/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [10/35][/COLOR][/I]

I've tried to apply a

```
sudo rm -rf /usr/lib*/*.la

```
And then select the option 

```
[6] Go to phase "wipe directory and start over"

```
But the error comes again. Any ideas?

---

### Post by andrewthomas on 2011-03-01
> **javipas said:**
> I'm trying to compile GNOME 3 on my Ubuntu 10.10 32 bits, but no luck as of now. 

The process tops at [10/35]:

[I][COLOR=DarkRed]Running automake-1.11...
configure.ac:4: warning: AC_INIT: not a literal: [http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-themes-standard](http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-themes-standard)
configure.ac:44: required file `themes/AdwaitaLowContrast/Makefile.in' not found
configure.ac:44: required file `themes/AdwaitaLowContrast/gtk-3.0/Makefile.in' not found
*** Error during phase configure of gnome-themes-standard: ##########  Error running ./autogen.sh --prefix /home/javipas/gnome-shell/install  --libdir '/home/javipas/gnome-shell/install/lib'  --disable-static  --disable-gtk-doc  *** [10/35][/COLOR][/I]



[http://ubuntuforums.org/showpost.php?p=10506007&postcount=713](http://ubuntuforums.org/showpost.php?p=10506007&postcount=713)

You probably should read at least the last couple of pages in the thread.

---

### Post by andrewthomas on 2011-03-01
> **bmbaker said:**
> I am still quite new to this can you give an expanded help on how to configure, make & then use checkinstall to build a .deb & install please :-)
I know that you have gotten past this, but you may need the info for the future.
> **CheckInstall** keeps track of all files installed by a "make install" or  equivalent, creates a Slackware, RPM, or Debian package with those  files, and adds it to the installed packages database, allowing for easy  package removal or distribution. [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

**[SIZE=2]Compiling things on Ubuntu the Easy Way[/SIZE]**

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[SIZE=2]**Compiling software**[/SIZE]
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by rajeev1204 on 2011-03-01
Is there any PPA which i can install for gnome shell.

Natty doesnt have a package and the only ppa around seems to be dead as of now.

---

### Post by KegHead on 2011-03-01
Hi!

I'd like the ppa also.

KegHead

---

### Post by Framli on 2011-03-01
There is the Gnome3 Team PPA, with recents G-S builds: [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

---

### Post by javipas on 2011-03-01
> **andrewthomas said:**
> [http://ubuntuforums.org/showpost.php?p=10506007&postcount=713](http://ubuntuforums.org/showpost.php?p=10506007&postcount=713)

You probably should read at least the last couple of pages in the thread.

You're absolutely right. strange enough, the issue has dissapeared, I have had no need to change anything at all. 

I guess the maintainer for the script has updated that part. 

Building right now. 26/35... :)

Thx!

---

### Post by bmbaker on 2011-03-01
Great thanks i will continue my learning curve :-)

> **andrewthomas said:**
> I know that you have gotten past this, but you may need the info for the future.
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

**[SIZE=2]Compiling things on Ubuntu the Easy Way[/SIZE]**

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[SIZE=2]**Compiling software**[/SIZE]
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

ha! very useful indeed thanks again :-)

---

### Post by javipas on 2011-03-01
> **javipas said:**
> You're absolutely right. strange enough, the issue has dissapeared, I have had no need to change anything at all. 

I guess the maintainer for the script has updated that part. 

Building right now. 26/35... :)

Thx!

Mmm. Stopped at 32/35: 

```
cc1: warnings being treated as errors
calendar-server/gnome-shell-calendar-server.c: In function ‘app_load_events’:
calendar-server/gnome-shell-calendar-server.c:603: error: implicit declaration of function ‘e_cal_view_stop’
make[3]: *** [gnome_shell_calendar_server-gnome-shell-calendar-server.o] Error 1
make[3]: se sale del directorio «/home/javipas/gnome-shell/source/gnome-shell/src»
make[2]: *** [all] Error 2
make[2]: se sale del directorio «/home/javipas/gnome-shell/source/gnome-shell/src»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/home/javipas/gnome-shell/source/gnome-shell»
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [32/35]
```

I'm affraid I don't know what to do again :(

---

### Post by mortski on 2011-03-01
> **javipas said:**
> Mmm. Stopped at 32/35: 

```
cc1: warnings being treated as errors
calendar-server/gnome-shell-calendar-server.c: In function ‘app_load_events’:
calendar-server/gnome-shell-calendar-server.c:603: error: implicit declaration of function ‘e_cal_view_stop’
make[3]: *** [gnome_shell_calendar_server-gnome-shell-calendar-server.o] Error 1
make[3]: se sale del directorio «/home/javipas/gnome-shell/source/gnome-shell/src»
make[2]: *** [all] Error 2
make[2]: se sale del directorio «/home/javipas/gnome-shell/source/gnome-shell/src»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/home/javipas/gnome-shell/source/gnome-shell»
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [32/35]
```

I'm affraid I don't know what to do again :(

I added the PPA [https://launchpad.net/~suraia/+archive/ppa](https://launchpad.net/~suraia/+archive/ppa) and installed the libecal1.2-dev package there along with a couple of dependencies it brought in. Then you can make distclean and build the shell. I then removed the PPA as there is a whole mess of other stuff in there I did not want (leaving the couple of packages it installed).

This works for me, however I don't use Evo for anything so I wouldn't know if it broke anything. If you do use it, I'd install of the evolution packages found on that PPA before removing it.

---

### Post by bmbaker on 2011-03-01
well it compiled 
metacity --replace &
 ~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
i get this out put;

(mutter:23112): mutter-WARNING **: Could not load library [/home/brian/gnome-shell/source/gnome-shell/src/libgnome-shell.la (libmozjs.so: cannot open shared object file: No such file or directory)]

mutter-ERROR **: failed to load plugins
aborting...
Shell killed with signal 5


> **mortski said:**
> I added the PPA [https://launchpad.net/~suraia/+archive/ppa]("https://launchpad.net/%7Esuraia/+archive/ppa") and installed the libecal1.2-dev package there along with a couple of dependencies it brought in. Then you can make distclean and build the shell. I then removed the PPA as there is a whole mess of other stuff in there I did not want (leaving the couple of packages it installed).

This works for me, however I don't use Evo for anything so I wouldn't know if it broke anything. If you do use it, I'd install of the evolution packages found on that PPA before removing it.

---

### Post by maniacss on 2011-03-01
> **bmbaker said:**
> well it compiled 
metacity --replace &
 ~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
i get this out put;

(mutter:23112): mutter-WARNING **: Could not load library [/home/brian/gnome-shell/source/gnome-shell/src/libgnome-shell.la (libmozjs.so: cannot open shared object file: No such file or directory)]

mutter-ERROR **: failed to load plugins
aborting...
Shell killed with signal 5

I get the same error, help please?

---

### Post by antono on 2011-03-01
> **maniacss said:**
> I get the same error, help please?

[http://platonic.techfiz.info/2010/10/01/fix-broken-gnome-shell-due-to-missing-libmozjs-so/](http://platonic.techfiz.info/2010/10/01/fix-broken-gnome-shell-due-to-missing-libmozjs-so/)

---

### Post by bmbaker on 2011-03-02
this works ;-)
[http://live.gnome.org/JhbuildI...]("http://live.gnome.org/JhbuildIssues/mutter")


cd /usr/lib/
sudo ln -s /usr/lib/xulrunner-1.9.2.15pre/[libmozjs.so]("http://libmozjs.so/") [libmozjs.so]("http://libmozjs.so/")
sudo ldconfig [libmozjs.so]("http://libmozjs.so/")

> **antono said:**
> [http://platonic.techfiz.info/2010/10/01/fix-broken-gnome-shell-due-to-missing-libmozjs-so/](http://platonic.techfiz.info/2010/10/01/fix-broken-gnome-shell-due-to-missing-libmozjs-so/)

---

### Post by javipas on 2011-03-02
> **mortski said:**
> I added the PPA [https://launchpad.net/~suraia/+archive/ppa](https://launchpad.net/~suraia/+archive/ppa) and installed the libecal1.2-dev package there along with a couple of dependencies it brought in. Then you can make distclean and build the shell. I then removed the PPA as there is a whole mess of other stuff in there I did not want (leaving the couple of packages it installed).

Yippie!!

Successfully compiled and running right now :)

```
metacity --replace &
cd ~/gnome-shell/source/gnome-shell/src
./gnome-shell --replace
```

First the know message about libmozjs.so appeared, but I created the correct symlink and did a 'sudo ldconfig -v'. Then a new message showed:

[I][COLOR="Red"]javipas@Maverick:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
mutter: symbol lookup error: /home/javipas/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_add
javipas@Maverick:~/gnome-shell/source/gnome-shell/src$ /usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png[/COLOR][/I]

And I just did a 

```
rm ~/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so
```

And re-launched. Yiihaa!! :D

GNOME-Shell is running, but **its speed is a little dissapointing**. For example the "Exposé" effect on hovering the top-left corner is not quite smooth. I guess there is someway to try to fix this, but for the moment, I'm happy :D

Thx!

---

### Post by maniacss on 2011-03-02
> **antono said:**
> [http://platonic.techfiz.info/2010/10/01/fix-broken-gnome-shell-due-to-missing-libmozjs-so/](http://platonic.techfiz.info/2010/10/01/fix-broken-gnome-shell-due-to-missing-libmozjs-so/)

> **bmbaker said:**
> this works ;-)
[http://live.gnome.org/JhbuildI...]("http://live.gnome.org/JhbuildIssues/mutter")


cd /usr/lib/
sudo ln -s /usr/lib/xulrunner-1.9.2.15pre/[libmozjs.so]("http://libmozjs.so/") [libmozjs.so]("http://libmozjs.so/")
sudo ldconfig [libmozjs.so]("http://libmozjs.so/")

Thanks, this did the trick. :popcorn:

---

### Post by Finalfantasykid on 2011-03-03
I'm getting some cheese error when I am compiling gnome-control-center

```

um-photo-dialog.c:33: fatal error: cheese-avatar-chooser.h: No such file or directory
compilation terminated.

```

---

### Post by nzjrs on 2011-03-03
Just a quick note, I was able to install gnome-shell on a vanilla Ubuntu Natty install, using only the official gnome3 team PPA. Details here;

[http://mail.gnome.org/archives/gnome-shell-list/2011-March/msg00028.html](http://mail.gnome.org/archives/gnome-shell-list/2011-March/msg00028.html)

---

### Post by nuovodna on 2011-03-03
> **Finalfantasykid said:**
> I'm getting some cheese error when I am compiling gnome-control-center

```

um-photo-dialog.c:33: fatal error: cheese-avatar-chooser.h: No such file or directory
compilation terminated.

```

Same error here. It is a problem related to cheese: it should be compiled against gtk3 instead of gtk2

---

### Post by xtoudi on 2011-03-03
Now you can compile whole GS - all 40 stages. Yes, 40 !!
New git update info here [http://git.gnome.org/browse/gnome-shell/commit/?id=1c759384fac3113036011d03668a47b1b72c52ef](http://git.gnome.org/browse/gnome-shell/commit/?id=1c759384fac3113036011d03668a47b1b72c52ef)

You need to get latest gnome-shell-build-setup.sh (first post of this thread). 
Then check deps and update jhbuild 
```
/bin/bash gnome-shell-build-setup.sh
```
install new required stuff. 

Probably **libsqlite3-dev** and **gperf** too.

Compile as usual.
```
jhbuild build
```
That's all - compiled and working :)


EDIT:

**gnome-control-center** error:
*```
fatal error: cheese-avatar-chooser.h: No such file or directory compilation terminated.
```* is **fixed** too.

---

### Post by nuovodna on 2011-03-03
Confirmed. Now it works!

---

### Post by Merk42 on 2011-03-03
> **xtoudi said:**
> Now you can compile whole GS - all 40 stages. Yes, 40 !!
New git update info here [http://git.gnome.org/browse/gnome-shell/commit/?id=1c759384fac3113036011d03668a47b1b72c52ef](http://git.gnome.org/browse/gnome-shell/commit/?id=1c759384fac3113036011d03668a47b1b72c52ef)

You need to get latest gnome-shell-build-setup.sh (first post of this thread). 
Then check deps and update jhbuild 
```
/bin/bash gnome-shell-build-setup.sh
```
install new required stuff. 

Probably **libsqlite3-dev** and **gperf** too.

I got
```
libsqlite3-dev libproxy-dev libdb-dev libproxy-dev
```
Added to the OP

---

### Post by RavisPohan on 2011-03-03
Does anyone here have any idea why, despite having successfully compiled and run Gnome-Shell numerous times this week, I still have the maximise and minimise buttons on my windows?

---

### Post by dext on 2011-03-03
> **RavisPohan said:**
> Does anyone here have any idea why, despite having successfully compiled and run Gnome-Shell numerous times this week, I still have the maximise and minimise buttons on my windows?

did you delete **all** of your previous Gnome3 stuff before you rebuilt? my guess you probably had/have something left over from and older build you did which has gone into the new one

---

### Post by RavisPohan on 2011-03-03
> **dext said:**
> did you delete **all** of your previous Gnome3 stuff before you rebuilt? my guess you probably had/have something left over from and older build you did which has gone into the new one

I deleted:

- the gnome-shell directory in my home folder
- .jhbuildrc
- gnome-shell-build-setup.sh
- ~/bin/jhbuild and ~/bin/install-check
- the ~/source/jhbuild folder

I don't even think I had to delete all of those... have I missed anything out?

---

### Post by Rekenber on 2011-03-03
rekenber@RKPC:~$ ~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
(mutter:2815): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libmozjs.so: cannot open shared object file: No such file or directory)]

I dunno what to do :P

And gnome shell won't load. :P

Using 10.10 and GS is from git.

---

### Post by kainos on 2011-03-03
> **bmbaker said:**
> this works ;-)
[http://live.gnome.org/JhbuildI...]("http://live.gnome.org/JhbuildIssues/mutter")


cd /usr/lib/
sudo ln -s /usr/lib/xulrunner-1.9.2.15pre/[libmozjs.so]("http://libmozjs.so/") [libmozjs.so]("http://libmozjs.so/")
sudo ldconfig [libmozjs.so]("http://libmozjs.so/")


sudo ln -s /usr/lib/xulrunner-1.9.2.13/libmozjs.so libmozjs.so

I did this because I am still using 10.10

---

### Post by bmbaker on 2011-03-04
if you have the mozilla ppa enabled do this first

To get it working you need to completely remove the folder and start over. Install xulrunner-dev, and run the following steps:

sudo apt-get install xulrunner-dev

curl -O [http://git.gnome.org/browse/gn](http://git.gnome.org/browse/gn)...
export PATH=$PATH:/home/YOUR_USERNAME/bin #replace YOUR_USERNAME with your username
cd
chmod +x gnome-shell-build-setup.sh
./gnome-shell-build-setup.sh


And then, before starting to build Gnome Shell, install xulrunner-1.9.2-dev:

sudo apt-get install xulrunner-1.9.2-dev

cd /usr/lib/
sudo ln -s /usr/lib/xulrunner-1.9.2.15pre/[libmozjs.so]("http://libmozjs.so/") [libmozjs.so]("http://libmozjs.so/")
sudo ldconfig [libmozjs.so]("http://libmozjs.so/")

Then you can start building Gnome Shell:
jhbuild build

---

### Post by burdebc on 2011-03-04
> **Chauncellor said:**
> Hi, How does one get the close buttons back to the left? I've no experience with cl/mutter.
Go to System > Preferences > Appearance and change the theme.

---

### Post by fil0~ on 2011-03-04
I'm getting this error:

```
(mutter:12122): mutter-WARNING **: Could not load library [/home/XYZ/gnome-shell/source/gnome-shell/src/libgnome-shell.la (/home/XYZ/gnome-shell/install/lib64/libgjs.so.0: undefined symbol: JS_StrictPropertyStub)]

mutter-ERROR **: failed to load plugins
aborting...
```

How to solve?

---

### Post by rlklee on 2011-03-04
Getting same error. Built tonight on 11.04 alpha 3.

---

### Post by rlklee on 2011-03-04
> **fil0~ said:**
> I'm getting this error:

```
(mutter:12122): mutter-WARNING **: Could not load library [/home/XYZ/gnome-shell/source/gnome-shell/src/libgnome-shell.la (/home/XYZ/gnome-shell/install/lib64/libgjs.so.0: undefined symbol: JS_StrictPropertyStub)]

mutter-ERROR **: failed to load plugins
aborting...
```

How to solve?

It looks like it might be a problem with having installed xulrunner-dev after jhbuild rather than before hand. Rebuilding now to confirm. Will report back.

---

### Post by Rekenber on 2011-03-05
rekenber@RKPC:~$ ~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
(mutter:30660): mutter-WARNING **: Could not load library [/home/rekenber/gnome-shell/source/gnome-shell/src/libgnome-shell.la (libmozjs.so: cannot open shared object file: No such file or directory)]

mutter-ERROR **: failed to load plugins
aborting...
Shell killed with signal 5

rekenber@RKPC:~$

(mutter:30993): mutter-WARNING **: Could not load library [/home/rekenber/gnome-shell/install/lib/mutter/plugins/libgnome-shell.so (libmozjs.so: cannot open shared object file: No such file or directory)]

mutter-ERROR **: failed to load plugins
aborting...
Shell killed with signal 5



In 10.10 and from Git XD

---

### Post by Mblackwell on 2011-03-05
```
jon@jon:~/gnome-shell/source/gnome-shell$ git diff master
diff --git a/src/gnome-shell-jhbuild.in b/src/gnome-shell-jhbuild.in
index 220d53f..98bcacd 100755
--- a/src/gnome-shell-jhbuild.in
+++ b/src/gnome-shell-jhbuild.in
@@ -184,9 +184,20 @@ def start_shell(perf_output=None):
     jhbuild_gconf_source = os.path.join('@sysconfdir@', 'gconf/2/path.jhbuild'
     if os.path.exists(jhbuild_gconf_source):
         env['GCONF_DEFAULT_SOURCE_PATH'] = jhbuild_gconf_source
         env['GCONF_DEFAULT_SOURCE_PATH'] = jhbuild_gconf_source
-
-    if options.perf is not None:
-        env['SHELL_PERF_MODULE'] = options.perf
+    # Work around Ubuntu xulrunner bug,
+    # http://bugzilla.gnome.org/show_bug.cgi?id=573413
+    pkgconfig = subprocess.Popen(['pkg-config', '--variable=sdkdir', 'mozilla-
+                                 stdout=subprocess.PIPE)
+    mozjs_sdkdir = pkgconfig.communicate()[0].strip()
+    pkgconfig.wait()
+    if pkgconfig.returncode == 0:
+        mozjs_libdir = re.sub('-(sdk|devel)', '', mozjs_sdkdir)
+        if os.path.exists(mozjs_libdir + '/libmozjs.so'):
+            if 'LD_LIBRARY_PATH' in env and env['LD_LIBRARY_PATH']:
+                ld_library_path = env['LD_LIBRARY_PATH'] + ':' + mozjs_libdir
+            else:
+                ld_library_path = mozjs_libdir
+            env['LD_LIBRARY_PATH'] = ld_library_path
 
     if perf_output is not None:
         env['SHELL_PERF_OUTPUT'] = perf_output

```

Making that change and recompiling lets me run without having to do any funky linking.

Also you should be able to use 'jhbuild run gnome-shell' to run it without doing anything.

---

### Post by rlklee on 2011-03-05
> **rlklee said:**
> It looks like it might be a problem with having installed xulrunner-dev after jhbuild rather than before hand. Rebuilding now to confirm. Will report back.

I did this

```

jhbuild build --no-network gnome-shell
```

and then this

```
rm ~/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so
```

And it's up and running.

---

### Post by Rekenber on 2011-03-05
^^ Worked for me.

May I ask, why when I try to suspend or even shut down my computer, an error pops

"gnome-session-quit: no command found"......???

---

### Post by bmbaker on 2011-03-05
could you expand on this please :-)

> **Mblackwell said:**
> ```
jon@jon:~/gnome-shell/source/gnome-shell$ git diff master
diff --git a/src/gnome-shell-jhbuild.in b/src/gnome-shell-jhbuild.in
index 220d53f..98bcacd 100755
--- a/src/gnome-shell-jhbuild.in
+++ b/src/gnome-shell-jhbuild.in
@@ -184,9 +184,20 @@ def start_shell(perf_output=None):
     jhbuild_gconf_source = os.path.join('@sysconfdir@', 'gconf/2/path.jhbuild'
     if os.path.exists(jhbuild_gconf_source):
         env['GCONF_DEFAULT_SOURCE_PATH'] = jhbuild_gconf_source
         env['GCONF_DEFAULT_SOURCE_PATH'] = jhbuild_gconf_source
-
-    if options.perf is not None:
-        env['SHELL_PERF_MODULE'] = options.perf
+    # Work around Ubuntu xulrunner bug,
+    # http://bugzilla.gnome.org/show_bug.cgi?id=573413
+    pkgconfig = subprocess.Popen(['pkg-config', '--variable=sdkdir', 'mozilla-
+                                 stdout=subprocess.PIPE)
+    mozjs_sdkdir = pkgconfig.communicate()[0].strip()
+    pkgconfig.wait()
+    if pkgconfig.returncode == 0:
+        mozjs_libdir = re.sub('-(sdk|devel)', '', mozjs_sdkdir)
+        if os.path.exists(mozjs_libdir + '/libmozjs.so'):
+            if 'LD_LIBRARY_PATH' in env and env['LD_LIBRARY_PATH']:
+                ld_library_path = env['LD_LIBRARY_PATH'] + ':' + mozjs_libdir
+            else:
+                ld_library_path = mozjs_libdir
+            env['LD_LIBRARY_PATH'] = ld_library_path
 
     if perf_output is not None:
         env['SHELL_PERF_OUTPUT'] = perf_output

```Making that change and recompiling lets me run without having to do any funky linking.

Also you should be able to use 'jhbuild run gnome-shell' to run it without doing anything.

---

### Post by bmbaker on 2011-03-05
read a few pages back, i think page 70 or 71 :-)

> **Rekenber said:**
> ^^ Worked for me.

May I ask, why when I try to suspend or even shut down my computer, an error pops

"gnome-session-quit: no command found"......???

---

### Post by andrewthomas on 2011-03-05
> **Rekenber said:**
> ^^ Worked for me.

May I ask, why when I try to suspend or even shut down my computer, an error pops

"gnome-session-quit: no command found"......???

You need to also build gnome-session from git

[http://ubuntuforums.org/showpost.php?p=10504619&postcount=708](http://ubuntuforums.org/showpost.php?p=10504619&postcount=708)

---

### Post by bmbaker on 2011-03-05
duh!! figured it out should have double checked !!

sudo rm libmozjs.so
sudo ln -s /usr/lib/xulrunner-1.9.2.16pre/libmozjs.so libmozjs.so
sudo ldconfig libmozjs.so

---

### Post by dyltman on 2011-03-05
```

marc@marc-EX58-UD5:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
(mutter:25508): mutter-WARNING **: Could not load library [/home/marc/gnome-shell/source/gnome-shell/src/libgnome-shell.la (libmozjs.so: cannot open shared object file: No such file or directory)]

mutter-ERROR **: failed to load plugins
aborting...
Shell killed with signal 5
marc@marc-EX58-UD5:~/gnome-shell/source/gnome-shell/src$ Cannot register the panel shell: there is already one running.

```

Can't get it to work :S

---

### Post by nperry on 2011-03-05
```
configure: error: Package requirements (gio-2.0 libical >= 0.43 libxml-2.0 gconf-2.0) were not met:

No package 'libical' found

```

Any ideas? 

libical0 is  0.44-3

---

### Post by andrewthomas on 2011-03-05
> **nperry said:**
> ```
configure: error: Package requirements (gio-2.0 libical >= 0.43 libxml-2.0 gconf-2.0) were not met:

No package 'libical' found

```Any ideas? 

libical0 is  0.44-3
```
sudo apt-get install libical-dev libxml2-dev libgconf2-dev
```

---

### Post by Merk42 on 2011-03-05
I tried> **rlklee said:**
> ```

jhbuild build --no-network gnome-shell
```
```
rm ~/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so
```
and
> **bmbaker said:**
> sudo rm libmozjs.so
sudo ln -s /usr/lib/xulrunner-1.9.2.16pre/libmozjs.so libmozjs.so
sudo ldconfig libmozjs.so
but I'm still getting

> **dyltman said:**
> ```

marc@marc-EX58-UD5:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
(mutter:25508): mutter-WARNING **: Could not load library [/home/marc/gnome-shell/source/gnome-shell/src/libgnome-shell.la (libmozjs.so: cannot open shared object file: No such file or directory)]

mutter-ERROR **: failed to load plugins
aborting...
Shell killed with signal 5
marc@marc-EX58-UD5:~/gnome-shell/source/gnome-shell/src$ Cannot register the panel shell: there is already one running.

```


Seems to be pretty common so I'd like to know what to do to put in the OP

---

### Post by nperry on 2011-03-06
> **andrewthomas said:**
> ```
sudo apt-get install libical-dev libxml2-dev libgconf2-dev
```

Already installed, had to change the Configure file.

All built, but getting this.

```
neil@laptop:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace

(mutter:13675): mutter-WARNING **: Could not load library [/home/neil/gnome-shell/source/gnome-shell/src/libgnome-shell.la (libmozjs.so: cannot open shared object file: No such file or directory)]

mutter-ERROR **: failed to load plugins
aborting...
Shell killed with signal 5
 /usr/bin/compiz (core) - Error: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
```

So I did this,
```
neil@laptop:/usr/lib$ sudo ln -s /usr/lib/xulrunner-2.0b12/libmozjs.so libmozjs.so
```

Fixed.

---

### Post by bmbaker on 2011-03-06
hi i am quite new to linux,
and have just started looking into Autotools, like Autoconf etc.
and i was wondering if anyone had created a script to take care of this:-

I was just updating from git and i keep noticing this:

Please add the files
codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/conf](ftp://ftp.gnu.org/pub/gnu/conf)...

Does anyone know how to do this?

if you have could you share it so i can use it as a base.
cheers
BB

---

### Post by Bou on 2011-03-06
> **Merk42 said:**
> **How do I Try it?**

Running Jaunty, Karmic, Lucid, Maverick and Natty, there are three ways to try GNOME Shell
[LIST]
[*]Build from source (recommended, as it provides the most recent version, though may occasionally break)
[*]Install the gnome-shell package (easy but out of date)
[*]**For Natty Narwhal Only** Use the [Ricotz PPA]("http://ubuntu-tweak.com/source/gnome-shell-testing/") (slightly harder, but more up to date)
[/LIST]

I tried the PPA method but Ricotz's PPA seems to be empty, then tried the [Gnome3 PPA]("https://launchpad.net/~gnome3-team/+archive/gnome3") and it messed my system badly. What method do you recommend me to follow to install Gnome-shell on my laptop? Is the OP's "build from source" method reliable as of today?

---

### Post by bmbaker on 2011-03-06
follow the instructions in the first post :-)

> **Bou said:**
> I tried the PPA method but Ricotz's PPA seems to be empty, then tried the [Gnome3 PPA]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") and it messed my system badly. What method do you recommend me to follow to install Gnome-shell on my laptop? Is the OP's "build from source" method reliable as of today?

---

### Post by Bou on 2011-03-06
> **bmbaker said:**
> follow the instructions in the first post

Alright, I will. Since the PPA they recommended seems to be empty, I thought they might be outdated.

---

### Post by plun on 2011-03-06
Up and running

The Unity plugin must also be disabled.

[[IMG]http://i.imgur.com/cgN6Js.jpg[/IMG]](http://imgur.com/cgN6J)

Minimize and maximize is still there....

---

### Post by Bou on 2011-03-06
> **plun said:**
> The Unity plugin must also be disabled.

Would it be OK if I login to gnome-classic, then run ./gnome-shell --replace?

---

### Post by plun on 2011-03-06
> **Bou said:**
> Would it be OK if I login to gnome-classic, then run ./gnome-shell --replace?

The Unity plugin must first be disabled with **ccsm** !

OPs first message must be followed !

I also did this

```
cd /usr/lib

sudo ln -s /usr/lib/xulrunner-2.0b12/libmozjs.so libmozjs.so

```

---

### Post by emostarxd on 2011-03-06
Hi guys,
when I run this:
```
jhbuild build --no-network gnome-shell
```
I receive this:
```
libtool: link: cannot find the library `/home/emostar/gnome-shell/install/lib/libgio-2.0.la' or unhandled argument `/home/emostar/gnome-shell/install/lib/libgio-2.0.la'
make[4]: *** [libecal-1.2.la] Error 1
make[4]: Leaving directory `/home/emostar/gnome-shell/source/evolution-data-server/calendar/libecal'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/emostar/gnome-shell/source/evolution-data-server/calendar/libecal'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/emostar/gnome-shell/source/evolution-data-server/calendar'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/emostar/gnome-shell/source/evolution-data-server'
make: *** [all] Error 2
*** Error during phase build of evolution-data-server: ########## Error running make   *** [13/35]

```

Please help, I need to fix the MUTTER error (fix on previous page)

---

### Post by moore.bryan on 2011-03-07
> **fil0~ said:**
> I'm getting this error:

```
(mutter:12122): mutter-WARNING **: Could not load library [/home/XYZ/gnome-shell/source/gnome-shell/src/libgnome-shell.la (/home/XYZ/gnome-shell/install/lib64/libgjs.so.0: undefined symbol: JS_StrictPropertyStub)]

mutter-ERROR **: failed to load plugins
aborting...
```

How to solve?

Have you cleared-out your .la references?

---

### Post by HunterAtUbuntu on 2011-03-07
I've successfully compiled and gotten past a couple of startup errors with libmozjs.so and canberra-gtk-module. Now I'm getting a new error and can't find a solution.
```

Panel leaving: a new panel shell is starting.

(gnome-panel:12131): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
Gtk-Message: Failed to load module "canberra-gtk-module"

(mutter:15544): libupower-glib-WARNING **: No 'IsDocked' property
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Mon Mar 07 2011 14:38:16 GMT-0500 (EST)
Window manager warning: Log level 16: The program 'mutter' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 698 error_code 8 request_code 7 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

gnome-shell-calendar-server[15630]: Got HUP on stdin - exiting

```
Anyone know how to fix this?

---

### Post by rlklee on 2011-03-07
> **plun said:**
> The Unity plugin must first be disabled with **ccsm** !

[/CODE]

I'm not sure what you mean by this. What is "ccsm"? A search on this through the thread yields nothing but your comment. How exactly is the Unity Plugin to be disabled?

---

### Post by dext on 2011-03-07
> **rlklee said:**
> I'm not sure what you mean by this. What is "ccsm"? A search on this through the thread yields nothing but your comment. How exactly is the Unity Plugin to be disabled?

[http://wiki.compiz.org/CCSM](http://wiki.compiz.org/CCSM)

---

### Post by rlklee on 2011-03-07
> **dext said:**
> [http://wiki.compiz.org/CCSM](http://wiki.compiz.org/CCSM)

In the repos as compizconfig-settings-manager for those wondering.

---

### Post by omega52390 on 2011-03-07
successfully built but i get this when i try and run gs WHAT DO?

```
/home/omega52390/gnome-shell/source/gnome-shell/src/.libs/lt-gnome-shell-real: error while loading shared libraries: libmutter-wm.so.0: cannot open shared object file: No such file or directory

```

---

### Post by andrewthomas on 2011-03-08
> **omega52390 said:**
> successfully built but i get this when i try and run gs WHAT DO?

```
/home/omega52390/gnome-shell/source/gnome-shell/src/.libs/lt-gnome-shell-real: error while loading shared libraries: libmutter-wm.so.0: cannot open shared object file: No such file or directory

```
You need to rebuild against the new version of mutter
```
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh
jhbuild build -afc
```

---

### Post by andrewthomas on 2011-03-08
The telepathy-glib git repo has moved.  You can either

 in file** ~/gnome-shell/source/snome-shell/tools/build/gnome-shell.modules**
@19
```
 <repository type="git" name="git.collabora.co.uk"
      href="git://git.collabora.co.uk/git/"/>
```to
```

 <repository type="git" name="git.collabora.co.uk"
      href="git://git.collabora.co.uk/git/freedesktop.org-mirror/telepathy/"/>
```or just open another terminal
```
cd gnome-shell/source
git clone git://git.collabora.co.uk/git/freedesktop.org-mirror/telepathy/telepathy-glib.git
```and go on to configure

---

### Post by nperry on 2011-03-08
I have now fixed this. [https://bugzilla.gnome.org/show_bug.cgi?id=644239](https://bugzilla.gnome.org/show_bug.cgi?id=644239)

When running jhbuild all you need to do is wipe the dir and it will pick up the git change.

---

### Post by HunterAtUbuntu on 2011-03-08
Fixed my problem. It was because I was using separate x servers. Switched to twin view and it started

---

### Post by kainos on 2011-03-08
> **andrewthomas said:**
> You need to rebuild against the new version of mutter


Thanks!

---

### Post by x-shaney-x on 2011-03-09
Can anyone tell me what the current official stance is regarding gnome shell and natty?
I have been googling around but get a lot of conflicting information, much of which seems to be out of date and I haven't been personally following gnome shell or ubuntu development much.

Last I heard, gnome shell would NOT be used by default (obviously) but also would not be included as an option or even be in the repos at all but may be added at a later date or via a PPA.

I am currently using kubuntu but am becoming very frustrated with KDE at the moment and not sure my future lies there.
I have briefly tried various natty alphas and dailys and although I want to like Unity, there just something I don't like about it and I don't get on well with it.
I am also far from convinced it will be at a seriously usable, stable state by release.

Which leaves gnome shell.  I have been using the gnome3 live cd over the past couple of days and I am very impressed.
I would rather use it over unity any day but I have no intention of compiling or adding PPAs to use it, I would rather switch distro

---

### Post by keypox on 2011-03-09
Anyone try out Fedora 15 alpha yet? Easy way to install and update gnome-shell i think.

---

### Post by Rekenber on 2011-03-09
Now, this:

libtool: install: /usr/bin/install-check .libs/libpixbufloader-tiff.lai /home/rekenber/gnome-shell/install/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tiff.la
install: cannot stat `.libs/libpixbufloader-tiff.lai': No such file or directory
make[4]: *** [install-loaderLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make: *** [install-recursive] Error 1
*** Error during phase install of gdk-pixbuf: ########## Error running make install *** [7/40]

---

### Post by Bou on 2011-03-09
I have noticed that GTK3 apps (e.g. the sound settings) look terrible when you use gnome-shell on ubuntu; is there a package I can install to make them look good again?

---

### Post by andrewthomas on 2011-03-09
> **Rekenber said:**
> Now, this:

libtool: install: /usr/bin/install-check .libs/libpixbufloader-tiff.lai /home/rekenber/gnome-shell/install/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tiff.la
install: cannot stat `.libs/libpixbufloader-tiff.lai': No such file or directory
make[4]: *** [install-loaderLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make: *** [install-recursive] Error 1
*** Error during phase install of gdk-pixbuf: ########## Error running make install *** [7/40]
I am not getting this.  Just finished rebuilding on Arch & Natty.  
Have you updated & run your gnome-shell-build-setup script lately?

```
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh
jhbuild build
```I do this before each time I rebuild.

---

### Post by Rekenber on 2011-03-09
> **andrewthomas said:**
> I am not getting this.  Just finished rebuilding on Arch & Natty.  
Have you updated & run your gnome-shell-build-setup script lately?

```
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh
jhbuild build
```I do this before each time I rebuild.

I am rebuilding from scratch. XD

As usual Maverick, Git :P

---

### Post by sgage on 2011-03-09
Is it possible to compile GS on Lucid? I made a stab at it, but apt-get couldn't find autopoint in the repos. Is there a "best" place to get autopoint? Will the compile even work on GS?

TIA

---

### Post by andrewthomas on 2011-03-09
[http://packages.ubuntu.com/maverick/autopoint](http://packages.ubuntu.com/maverick/autopoint)

You could grab the gettext source here and build a deb with checkinstall.

---

### Post by sgage on 2011-03-09
> **andrewthomas said:**
> [http://packages.ubuntu.com/maverick/autopoint](http://packages.ubuntu.com/maverick/autopoint)

You could grab the gettext source here and build a deb with checkinstall.

Thanks, Andrew! That worked fine - and in fact, now I'm running Gnome Shell... :KS

---

### Post by andrewthomas on 2011-03-10
> **andrewthomas said:**
> After rebuilding I could no longer log out due to 'gnome-session-quit' not found.

What I did was to build gnome-session from git

```
cd gnome-shell/source
git clone git://git.gnome.org/gnome-session
cd gnome-session
./autogen.sh
./configure --prefix /home/andrew_shell/gnome-shell/install --libdir /home/andrew_shell/gnome-shell/install/lib64 --disable-static --disable-gtk-doc
make 
make install
```now it is back to normal

I have found another way of getting around this without building gnome-session.

1) create a file ~/gnome-session-save  containing
```
#!/bin/bash
gnome-session-save --logout-dialog
```and make it executable
2) create a symbolic link from gnome-session-quit to the file
```
ln -s ~/gnome-session-save ~/gnome-shell/install/bin/gnome-session-quit
```Now you can logout.

---

### Post by ratcheer on 2011-03-11
I am lost. I installed gnome-shell from the ppa. I have tried many suggestions in this thread, including using ccsm to disable the Unity plugin and linking /usr/lib/libmozjs.so to about four different things, most recently to /usr/lib/xulrunner-2.0b12/libmozjs.so

But, I still cannot get gnome-shell to start. Every time I try, I get:

```
 gnome-shell --replace &
[2] 3251
tim@nattytest:/usr/lib$ Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 705, in <module>
    normal_exit = run_shell()
  File "/usr/bin/gnome-shell", line 293, in run_shell
    if shell is None:
UnboundLocalError: local variable 'shell' referenced before assignment
/usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

[2]+  Exit 1                  gnome-shell --replace

```

I am running natty. What am I missing?

Tim

---

### Post by andrewthomas on 2011-03-11
> **ratcheer said:**
> I am lost. I installed gnome-shell from the ppa. I have tried many suggestions in this thread, including using ccsm to disable the Unity plugin and linking /usr/lib/libmozjs.so to about four different things, most recently to /usr/lib/xulrunner-2.0b12/libmozjs.so

But, I still cannot get gnome-shell to start. Every time I try, I get:

```
 gnome-shell --replace &
[2] 3251
tim@nattytest:/usr/lib$ Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 705, in <module>
    normal_exit = run_shell()
  File "/usr/bin/gnome-shell", line 293, in run_shell
    if shell is None:
UnboundLocalError: local variable 'shell' referenced before assignment
/usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

[2]+  Exit 1                  gnome-shell --replace

```I am running natty. What am I missing?

Tim
  Although I am building with jhbuild  not using the PPA so I don't have to do this, but it should work of you first replace with metacity then the shell

```
metacity --replace &
sleep 5 
gnome-shell --replace &
```

---

### Post by ratcheer on 2011-03-11
Thanks. That was one of the things I tried, but I will try it again. I think I tried it before the last time I linked libmozjs.so, so I guess it is worth another try.

So, back to natty ...

Tim

---

### Post by ratcheer on 2011-03-11
No, I still get the same thing:

```

tim@nattytest:~$ metacity --replace &
[1] 1672
tim@nattytest:~$ gnome-shell --replace &
[2] 1726
tim@nattytest:~$ Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 705, in <module>
    normal_exit = run_shell()
  File "/usr/bin/gnome-shell", line 293, in run_shell
    if shell is None:
UnboundLocalError: local variable 'shell' referenced before assignment
/usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

[2]+  Exit 1                  gnome-shell --replace

```

---

### Post by Sennaista on 2011-03-11
Hello all,

I've been using gnome-shell since yesterday and it's very smooth for a development version, just the occasional jerky window movement. The one thing that I miss is an indicator showing the current keyboard layout. It is a must for bilingual people and systems. Is there any way to fix this? Is an indicator planned for the final release?

Thanks.

---

### Post by Merk42 on 2011-03-11
Is GNOME Shell just not possible to build on 10.10 anymore?
I had to install [FONT="Courier New"]libjpeg8-dev[/FONT], but now I think it needs to install [FONT="Courier New"]libtiff-dev[/FONT], which it can't due to an unmet dependency on [FONT="Courier New"]libjpeg-dev[/FONT]

---

### Post by ratcheer on 2011-03-11
See posts 795-798. Can anyone help?

Thanks,
Tim

---

### Post by qamelian on 2011-03-11
> **Merk42 said:**
> Is GNOME Shell just not possible to build on 10.10 anymore?
I had to install [FONT=Courier New]libjpeg8-dev[/FONT], but now I think it needs to install [FONT=Courier New]libtiff-dev[/FONT], which it can't due to an unmet dependency on [FONT=Courier New]libjpeg-dev[/FONT]
It built fine on my 10.10 box two days ago, but it refused to actually run saying there was already a window manager running and instructin me to use the --replace option, which I was already using.

---

### Post by Mblackwell on 2011-03-11
> **ratcheer said:**
> See posts 795-798. Can anyone help?

Thanks,
Tim

Is Compiz disabled (it should be to use GS)?

---

### Post by andrewthomas on 2011-03-12
> **qamelian said:**
> It built fine on my 10.10 box two days ago, but it refused to actually run saying there was already a window manager running and instructin me to use the --replace option, which I was already using.
If you are having problems with this, you could try to use this
```

ln -s ~/gnome-shell/install/share/applications/gnome-shell.desktop ~/.local/share/applications/gnome-shell.desktop
gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "gnome-shell" -t string

```After you do this open up the ~/.gconf/desktop/gnome/session/required_components/ xml file and make sure that there are no other entries except for windowmanager

If you then get a gnome-shell command not found error in your .xsession-errors file then also use an autostarter

```
#!/bin/bash
~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
```

---

### Post by RavisPohan on 2011-03-12
> **Merk42 said:**
> Is GNOME Shell just not possible to build on 10.10 anymore?
I had to install [FONT="Courier New"]libjpeg8-dev[/FONT], but now I think it needs to install [FONT="Courier New"]libtiff-dev[/FONT], which it can't due to an unmet dependency on [FONT="Courier New"]libjpeg-dev[/FONT]

I don't know whether this will help you or not, but I hit a similar problem yesterday, and - just mucking around - found that, in addition to the installed libjpeg62-dev, there was also libjpeg8-dev. I tried installing the latter, to see whether it helped (involved removing libjpeg62-dev). It didn't, so I removed libjpeg8-dev, reinstalled libjpeg62-dev, tried again just on the off-chance, and... gnome-shell built without any problems.

I'm not 100% sure whether I've outlined what I did exactly, but it was along those lines. Maybe if you try different libjpeg combinations it will solve your problem, too.

---

### Post by sgage on 2011-03-12
I don't know about 10.10, but I just compiled GS a few days ago on 10.04 with no issues.

---

### Post by ratcheer on 2011-03-12
> **Mblackwell said:**
> Is Compiz disabled (it should be to use GS)?

Yes, the compiz Unity Plugin is de-selected. My screen looks like a 1990's Win NT 3.5 screen. Is there anything else that needs to be done?

Tim

---

### Post by moore.bryan on 2011-03-12
Any ideas how to fix this one?
```

*** Checking out clutter *** [17/40]
git clone git://git.clutter-project.org/clutter
Cloning into clutter...
fatal: read error: Connection reset by peer

```
There was a comment back on the dev list on 8 March about the server being down, but shouldn't it be back up by now?

---

### Post by ronacc on 2011-03-12
> **moore.bryan said:**
> Any ideas how to fix this one?
```

*** Checking out clutter *** [17/40]
git clone git://git.clutter-project.org/clutter
Cloning into clutter...
fatal: read error: Connection reset by peer

```
There was a comment back on the dev list on 8 March about the server being down, but shouldn't it be back up by now?

I've been getting the same error the last couple of days , latest attempt was a couple of hours ago , same result .

---

### Post by andrewthomas on 2011-03-13
> **ronacc said:**
> I've been getting the same error the last couple of days , latest attempt was a couple of hours ago , same result .
I stupidly selected "wipe directory," but luckily I had another partition that I was able to copy the files over from.

---

### Post by kv1dr on 2011-03-13
I get this error:

```
*** Izgradnja gnome-shell *** [37/40]
make  
make  all-recursive
make[1]: Entering directory `/home/kv1dr/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/home/kv1dr/gnome-shell/source/gnome-shell/data'
  GEN    gnome-shell.desktop.in
  GEN    gnome-shell.desktop
LC_ALL=C /usr/bin/intltool-merge -x -u /tmp org.gnome.shell.gschema.xml.in org.gnome.shell.gschema.xml
Merging translations into org.gnome.shell.gschema.xml.
CREATED org.gnome.shell.gschema.xml
  GEN    org.gnome.shell.gschema.valid
  GEN    gschemas.compiled
rm gnome-shell.desktop.in
make[2]: Leaving directory `/home/kv1dr/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/home/kv1dr/gnome-shell/source/gnome-shell/js'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kv1dr/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/home/kv1dr/gnome-shell/source/gnome-shell/src'
  GEN    stamp-st-enum-types.h
  GEN    st-enum-types.c
  GEN    stamp-st-marshal.h
  GEN    st-marshal.c
  GEN    stamp-st.h
  GEN    stamp-na-marshal.h
  GEN    na-marshal.c
  GEN    stamp-shell-marshal.h
  GEN    shell-marshal.c
  GEN    stamp-shell-enum-types.h
  GEN    shell-enum-types.c
make  all-am
make[3]: Entering directory `/home/kv1dr/gnome-shell/source/gnome-shell/src'
  CC     libgdmuser_1_0_la-gdm-user.lo
  CC     libgdmuser_1_0_la-gdm-user-manager.lo
  CCLD   libgdmuser-1.0.la
  CC     libst_1_0_la-st-adjustment.lo
  CC     libst_1_0_la-st-bin.lo
  CC     libst_1_0_la-st-border-image.lo
  CC     libst_1_0_la-st-box-layout.lo
  CC     libst_1_0_la-st-box-layout-child.lo
  CC     libst_1_0_la-st-button.lo
  CC     libst_1_0_la-st-clipboard.lo
  CC     libst_1_0_la-st-container.lo
  CC     libst_1_0_la-st-drawing-area.lo
  CC     libst_1_0_la-st-entry.lo
  CC     libst_1_0_la-st-focus-manager.lo
  CC     libst_1_0_la-st-group.lo
  CC     libst_1_0_la-st-icon.lo
  CC     libst_1_0_la-st-icon-colors.lo
  CC     libst_1_0_la-st-im-text.lo
  CC     libst_1_0_la-st-label.lo
  CC     libst_1_0_la-st-overflow-box.lo
  CC     libst_1_0_la-st-private.lo
  CC     libst_1_0_la-st-scrollable.lo
  CC     libst_1_0_la-st-scroll-bar.lo
  CC     libst_1_0_la-st-scroll-view.lo
  CC     libst_1_0_la-st-shadow.lo
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
  CC     libst_1_0_la-st-scroll-view-fade.lo
  CC     libst_1_0_la-st-enum-types.lo
  CC     libst_1_0_la-st-marshal.lo
  CCLD   libst-1.0.la
  CC     libtray_la-na-tray-child.lo
  CC     libtray_la-na-tray-manager.lo
  CC     libtray_la-na-marshal.lo
  CCLD   libtray.la
  CC     libgvc_la-gvc-mixer-stream.lo
  CC     libgvc_la-gvc-channel-map.lo
  CC     libgvc_la-gvc-mixer-card.lo
  CC     libgvc_la-gvc-mixer-sink.lo
  CC     libgvc_la-gvc-mixer-source.lo
  CC     libgvc_la-gvc-mixer-sink-input.lo
  CC     libgvc_la-gvc-mixer-source-output.lo
  CC     libgvc_la-gvc-mixer-event-role.lo
  CC     libgvc_la-gvc-mixer-control.lo
  CCLD   libgvc.la
  CC     libjs_test_la-shell-generic-container.lo
  CC     libjs_test_la-shell-perf-log.lo
  CCLD   libjs-test.la
  CC     libgnome_shell_la-shell-marshal.lo
  CC     libgnome_shell_la-shell-enum-types.lo
  CC     libgnome_shell_la-gnome-shell-plugin.lo
  CC     libgnome_shell_la-shell-app.lo
  CC     libgnome_shell_la-shell-a11y.lo
  CC     libgnome_shell_la-shell-app-system.lo
  CC     libgnome_shell_la-shell-app-usage.lo
  CC     libgnome_shell_la-shell-arrow.lo
  CC     libgnome_shell_la-shell-doc-system.lo
  CC     libgnome_shell_la-shell-embedded-window.lo
  CC     libgnome_shell_la-shell-generic-container.lo
  CC     libgnome_shell_la-shell-gtk-embed.lo
  CC     libgnome_shell_la-shell-global.lo
  CC     libgnome_shell_la-shell-perf-log.lo
  CC     libgnome_shell_la-shell-polkit-authentication-agent.lo
  CC     libgnome_shell_la-shell-slicer.lo
  CC     libgnome_shell_la-shell-stack.lo
  CC     libgnome_shell_la-shell-tray-icon.lo
  CC     libgnome_shell_la-shell-tray-manager.lo
  CC     libgnome_shell_la-shell-util.lo
  CC     libgnome_shell_la-shell-window-tracker.lo
  CC     libgnome_shell_la-shell-wm.lo
  CC     libgnome_shell_la-shell-xfixes-cursor.lo
  CC     libgnome_shell_la-shell-recorder.lo
  CC     libgnome_shell_la-shell-recorder-src.lo
  CCLD   libgnome-shell.la
  CC     gnome_shell_real-main.o
  CCLD   gnome-shell-real
  CC     gnome_shell_calendar_server-calendar-sources.o
  CC     gnome_shell_calendar_server-gnome-shell-calendar-server.o
  CCLD   gnome-shell-calendar-server
  CC     gnome_shell_perf_helper-shell-perf-helper.o
  CCLD   gnome-shell-perf-helper
  CC     test_theme-test-theme.o
cc1: warnings being treated as errors
st/test-theme.c: In function ‘main’:
st/test-theme.c:429: error: ignoring return value of ‘clutter_init’, declared with attribute warn_unused_result
make[3]: *** [test_theme-test-theme.o] Error 1
make[3]: Leaving directory `/home/kv1dr/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/kv1dr/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kv1dr/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [37/40]

  [1] Rerun phase build
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] zagon lupine
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"

```

what should I do now?

I tried [this]("http://ubuntuforums.org/showpost.php?p=10509056&postcount=730"), but it doesn't work for me.

---

### Post by ronacc on 2011-03-13
> **andrewthomas said:**
> I stupidly selected "wipe directory," but luckily I had another partition that I was able to copy the files over from.

thanks for the tip , I always save my last couple of successful builds by renameing them sequentialy before I start a new build so I was able to copy the clutter dir from there .

---

### Post by ronacc on 2011-03-13
something new ? I have been running GS all day , started it form classic in a terminal the "normal" way . I just tried to stop it by ctr+c in the term it started from and while the term returned me to a promt gs did not exit closeing the terminal did not cause gs to exit either .

---

### Post by andrewthomas on 2011-03-14
The shell now has 41 modules so you have to re-run.

```

curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh
```

Then rebuild.

---

### Post by ronacc on 2011-03-14
thanks for the heads up , rebuilding now .

---

### Post by samigina on 2011-03-15
Hi, I like GS, but it wasted space in my little screen. Theres some way to optimize screen usage? I mean, things like th Unity global menu, the window controsl in the panel...

---

### Post by keypox on 2011-03-15
does this work in ubuntu 11.04?  I am trying now but dunno waste the time if i dont have to.  Its running now.

---

### Post by ronacc on 2011-03-15
you may have to copy the clutter source from a previous build , the repo for that one has been down for a few days , otherwise it built ok for me . also you may need to delete the libcanberra-gtk-module.so symlink to get it to run .

---

### Post by Merk42 on 2011-03-15
I asked about the clutter Connect Reset issue and was told:
> The service is down for a couple of days now. Update
"gnome-shell/source/clutter/.git/config" to the following
URL (or do a checkout in gnome-shell/source from that URL
manually if you have already deleted it):So how would I do a manual checkout?

---

### Post by ronacc on 2011-03-15
from your gnome-shell/source dir in a terminal run ```
git checkout <url>
``` that should do it .

edit: see  [ftp://ftp.kernel.org/pub/software/scm/git/docs/v1.7.3.3/git-checkout.html](ftp://ftp.kernel.org/pub/software/scm/git/docs/v1.7.3.3/git-checkout.html)

---

### Post by Merk42 on 2011-03-15
> **ronacc said:**
> from your gnome-shell/source dir in a terminal run ```
git checkout <url>
``` that should do it .

edit: see  [ftp://ftp.kernel.org/pub/software/scm/git/docs/v1.7.3.3/git-checkout.html](ftp://ftp.kernel.org/pub/software/scm/git/docs/v1.7.3.3/git-checkout.html)

Whoops forgot to copy/paste the url. It said [http://git.clutter-project.org/clutter/](http://git.clutter-project.org/clutter/)
but if I try that I get ```
 git checkout http://git.clutter-project.org/clutter/
fatal: Not a git repository (or any of the parent directories): .git

```

---

### Post by Jesus_Valdez on 2011-03-15
I just copy my old files to the new clutter directory and select "2" from the jbuild options.

I assume no big changes in Clutter, and I'm running just fine.

So, when is coming out? Is really soon, right? What big changes, if any, can we expect? There will be a ppa once is out?

---

### Post by ronacc on 2011-03-16
> **Merk42 said:**
> Whoops forgot to copy/paste the url. It said [http://git.clutter-project.org/clutter/](http://git.clutter-project.org/clutter/)
but if I try that I get ```
 git checkout http://git.clutter-project.org/clutter/
fatal: Not a git repository (or any of the parent directories): .git

```

since I couldn,t check what the url actualy pointed at , I assumed it was a git repository . since you posted the url I can see it now , just go to that url  and download the latest clutter tar.gz and untar it into your gnomeshell/source dir.

---

### Post by maxfact on 2011-03-17
I have a solution from problem **Clutter**
needs to be done to resolve:
1) exit from the compilation with the option
```
[4] start shell
```
you will end up in the gnome folder shell / source```
~ / $ gnome-shell/source
```
2) give this command to download hand clutter
```
git clone http://git.clutter-project.org/clutter
```
3) once downloaded to the terminal clutter
```
. / configure - prefix $ HOME / gnome-shell / install /
``` (syntax needed to make sure that when you make install from the clutter is installed in the directory gnomeshell)
and ```
make & & make install
```
4) write terminal
```
exit
``` in order to return to the compilation of gnome shell at this point select
```
[2] Ignore error and continue to configure
```

Now compiling gnome shell should be no other problems

I apologize for my English I'm Italian and I used google translation for translated

---

### Post by DigitalDingo on 2011-03-17
> **Rekenber said:**
> libtool: install: /usr/bin/install-check .libs/libpixbufloader-tiff.lai /home/rekenber/gnome-shell/install/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tiff.la
install: cannot stat `.libs/libpixbufloader-tiff.lai': No such file or directory
make[4]: *** [install-loaderLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/rekenber/gnome-shell/source/gdk-pixbuf/gdk-pixbuf'
make: *** [install-recursive] Error 1
*** Error during phase install of gdk-pixbuf: ########## Error running make install *** [7/40]
I get this error too. Has anyone found a solution?

---

### Post by eclesh on 2011-03-17
> **DigitalDingo said:**
> I get this error too. Has anyone found a solution?


libtool: install: /usr/bin/install-check .libs/libpixbufloader-tiff.lai /home/rekenber/gnome-shell/install/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tiff.la
install: cannot stat `.libs/libpixbufloader-tiff.lai': No such file or directory


Maybe you don't have libtiff-dev installed? That might fix it.

---

### Post by andrewthomas on 2011-03-17
> **eclesh said:**
> Maybe you don't have libtiff-dev installed? That might fix it.
After that you need to **update** and rebuild
> **andrewthomas said:**
> The shell now has 41 modules so you have to re-run.

```

curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh
jhbuild build -afc
rm ~/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so

```

---

### Post by andrewthomas on 2011-03-17
> **maxfact said:**
> I have a solution from problem **Clutter**
needs to be done to resolve:
1) exit from the compilation with the option
```
[4] start shell
```you will end up in the gnome folder shell / source```
~ / $ gnome-shell/source
```2) give this command to download hand clutter
```
git clone http://git.clutter-project.org/clutter
```3) once downloaded to the terminal clutter
```
. / configure - prefix $ HOME / gnome-shell / install /
``` (syntax needed to make sure that when you make install from the clutter is installed in the directory gnomeshell)
and ```
make & & make install
```4) write terminal
```
exit
``` in order to return to the compilation of gnome shell at this point select
```
[2] Ignore error and continue to configure
```Now compiling gnome shell should be no other problems

I apologize for my English I'm Italian and I used google translation for translated
a better solution may be to just
```
cd ~/gnome-shell/source/
mv clutter clutter-git
git clone http://git.clutter-project.org/clutter/
```before you rebuild.
Then, when it gets to clutter it will try to reset back to git.
Open up another terminal and
```
cd gnome-shell/source/clutter
git remote set-url origin http://git.clutter-project.org/clutter
git pull --rebase
```
and choose to skip checkout and go on to configure

---

### Post by burdebc on 2011-03-17
Whenever I try to run jhbuild to install gnome shell on Ubuntu 10.10 I keep getting the following error message:

 $ ./autogen.sh --prefix /home/burdebc/gnome-shell/install --libdir '/home/burdebc/gnome-shell/install/lib64' --disable-static --disable-gtk-doc
/bin/bash: ./autogen.sh: No such file or directory

When I told it to continue to the next module everything except mutter built fine, and mutter fails because clutter is missing.  I have also attached a screenshot of the jhbuild window when the error occurs.  Any help will be greatly appreciated.

---

### Post by andrewthomas on 2011-03-17
> **burdebc said:**
> Whenever I try to run jhbuild to install gnome shell on Ubuntu 10.10 I keep getting the following error message:

 $ ./autogen.sh --prefix /home/burdebc/gnome-shell/install --libdir '/home/burdebc/gnome-shell/install/lib64' --disable-static --disable-gtk-doc
/bin/bash: ./autogen.sh: No such file or directory

When I told it to continue to the next module everything except mutter built fine, and mutter fails because clutter is missing.  I have also attached a screenshot of the jhbuild window when the error occurs.  Any help will be greatly appreciated.
Is your clutter directory empty?
 
If it is then,
```
cd ~/gnome-shell/source/
git clone http://git.clutter-project.org/clutter/
```Then to update it later you will have to run the following again if you have updated jhbuild and the gnome-shell-build-setup script.
```
cd gnome-shell/source/clutter
git remote set-url origin http://git.clutter-project.org/clutter
git pull --rebase
```If it isn't empty ( although it does seem to be,)  then just do the update command in another terminal and choose to move on to configure.

---

### Post by DigitalDingo on 2011-03-18
> **eclesh said:**
> Maybe you don't have libtiff-dev installed? That might fix it.
I have libtiff4-dev installed - shouldn't that be ok? I haven't had any problems compiling gnome-shell using jhbuild until a few days ago, and I don't think I installed anything that could mess things up...

---

### Post by maxfact on 2011-03-18
@DigitalDingo
try for 32 bit
```
rm ~/gnome-shell/install/lib/*.la
```  or for 64 bit
```
rm ~/gnome-shell/install/lib64/*.la
```

---

### Post by illbashu on 2011-03-18
```
OpenGL Info: Using XSHM for GLX_EXT_texture_from_pixmap
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@:0
("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/home/raza/gnome-shell/source/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old
/home/raza/gnome-shell/source/gnome-shell/src/gnome-shell-calendar-server: error while loading shared libraries: libecal-1.2.so.8: cannot open shared object file: No such file or directory

(lt-gnome-shell-real:1583): libupower-glib-WARNING **: No 'IsDocked' property
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Fri Mar 18 2011 13:10:48 GMT-0400 (EST)

(gnome-power-manager:1623): libupower-glib-WARNING **: No 'IsDocked' property

(gnome-power-manager:1623): libupower-glib-WARNING **: No 'IsDocked' property

(gnome-power-manager:1623): libupower-glib-WARNING **: No 'IsDocked' property

(lt-gnome-shell-real:1583): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:1631): WARNING **: Unknown option --since=2011-01-17T17:10:50.169099Z
```

Does anyone know how to fix this? 

BTW I'm using virtualbox and I installed the guest editions and compiz runs fine. I disabled compized and ran gnome-shell, the stuff loads but it's all messed up looking.

[http://img34.imageshack.us/img34/1776/screenshotubuntu1010run.png](http://img34.imageshack.us/img34/1776/screenshotubuntu1010run.png)

---

### Post by centos on 2011-03-19
Similar problem here, Ubuntu 10.10

```
./gnome-shell --replace
Panel leaving: a new panel shell is starting.

(gnome-panel:27206): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/home/honza/gnome-shell/source/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old

(lt-gnome-shell-real:27383): libupower-glib-WARNING **: No 'IsDocked' property
Varování správce oken: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Varování správce oken: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sat Mar 19 2011 09:46:45 GMT+0100 (CET)

(lt-gnome-shell-real:27383): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:27420): WARNING **: Unknown option --since=2011-01-18T08:46:46.999114Z
radeonSetSpanFunctions: bad format: 0x0002
radeonSetSpanFunctions: bad format: 0x0002
gnome-shell-calendar-server[27409]: Got HUP on stdin - exiting
Shell killed with signal 11

```

---

### Post by dext on 2011-03-19
could anyone tell me if there is a *Restart* & *Power off* & *Suspend* in your versions yet or no? all im seeing is Power Off an Suspend this is below _Log Out_

---

### Post by valorin on 2011-03-19
> **ratcheer said:**
> No, I still get the same thing:

```

tim@nattytest:~$ metacity --replace &
[1] 1672
tim@nattytest:~$ gnome-shell --replace &
[2] 1726
tim@nattytest:~$ Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 705, in <module>
    normal_exit = run_shell()
  File "/usr/bin/gnome-shell", line 293, in run_shell
    if shell is None:
UnboundLocalError: local variable 'shell' referenced before assignment
/usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

[2]+  Exit 1                  gnome-shell --replace

```

I have the exact same problem here. The only thing I can think of is that the PPA is broken, and nobody here actually uses it...

---

### Post by burdebc on 2011-03-19
I am getting an error message very similar to illbashu and centos when I launch gnome shell from the terminal, also it is rather slow and the windows look weird.  I have attached a copy of the messages terminal was giving and a screenshot of what my windows look like.  I would greatly appreciate any information.  Thanks.

---

### Post by DigitalDingo on 2011-03-20
> **maxfact said:**
> @DigitalDingo
try for 32 bit
```
rm ~/gnome-shell/install/lib/*.la
```  or for 64 bit
```
rm ~/gnome-shell/install/lib64/*.la
```Thanks for your suggestion, but it didn't solve the problem.

I did get it solved, however, by removing libjpeg8 and libjpeg8-dev and installing libjpeg62 and libjpeg62-dev instead. I don't know when or how the 8th version got into my system, but Gnome Shell compiles and runs just fine now. :)

---

### Post by kainos on 2011-03-21
I did a clean build yesterday after backing up a copy of the gnome-shell directory. It built fine, you may want to try that. Ubuntu 10.10, fyi.

---

### Post by false truths on 2011-03-21
I keep getting this when I try to install the dependencies. I don't have any repositories that should be conflicting (removed everything except my theme, icons, and AWN repositories), so I'm a little lost..

```
robert@robert-Presario-C700-Notebook-PC:~$ sudo apt-get install autopoint libsqlite3-dev libproxy-dev libdb-dev libproxy-dev libcups2-dev libupower-glib-dev libusb-1.0-0-dev libgnome-keyring-dev libvorbis-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev python-dev libpam-dev libreadline5-dev libpulse-dev liborbit2-dev libwnck-dev libtiff-dev libjpeg-dev libjasper-dev libical-dev libgtop2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libexpat-dev libdbus-glib-1-dev icon-naming-utils gtk-doc-tools gnome-common gperf flex bison
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libpam0g-dev' instead of 'libpam-dev'
Note, selecting 'libtiff4-dev' instead of 'libtiff-dev'
Note, selecting 'libjpeg62-dev' instead of 'libjpeg-dev'
Note, selecting 'libexpat1-dev' instead of 'libexpat-dev'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcroco3-dev : Depends: libglib2.0-dev (>= 2.0) but it is not going to be installed
 libdbus-glib-1-dev : Depends: libglib2.0-dev but it is not going to be installed
 libgnome-desktop-dev : Depends: libgtk2.0-dev (>= 2.14.0) but it is not going to be installed
 libgnome-keyring-dev : Depends: libglib2.0-dev (>= 2.16) but it is not going to be installed
 libgnome-menu-dev : Depends: libglib2.0-dev (>= 2.15.2) but it is not going to be installed
 libgstreamer0.10-dev : Depends: libglib2.0-dev but it is not going to be installed
 libgtop2-dev : Depends: libglib2.0-dev but it is not going to be installed
 liborbit2-dev : Depends: libidl-dev (>= 0.8.6-1) but it is not going to be installed
                 Depends: libglib2.0-dev but it is not going to be installed
 libpulse-dev : Depends: libglib2.0-dev but it is not going to be installed
 libupower-glib-dev : Depends: libglib2.0-dev but it is not going to be installed
 libwnck-dev : Depends: libglib2.0-dev (>= 2.13.0) but it is not going to be installed
               Depends: libpango1.0-dev but it is not going to be installed
               Depends: libgtk2.0-dev (>= 2.19.7) but it is not going to be installed
               Depends: libcairo2-dev but it is not going to be installed
 xulrunner-dev : Depends: xulrunner-1.9.2-dev but it is not going to be installed
E: Broken packages

```

---

### Post by bulldog on 2011-03-21
@False Truths,
I see you have broken packages.
Try to resolve this with synaptic first and try again.

---

### Post by Jesus_Valdez on 2011-03-21
You may need to look for those packages in Synaptic and downgrade them.

It used to give me that error a while ago whit a PPA that upgrade some packages.

---

### Post by false truths on 2011-03-21
I've tried to resolve them with Synaptic, with Apt, and with Aptitude. Nothing is fixing these broken packages for some reason.

---

### Post by sagara on 2011-03-22
If I install GNOME 3 on ubuntu 10.10, will this "replace" the GNOME2 stack and let me experience the real GNOME3 or its just an approximation of what it would be like?

After installing it felt like GNOME3 was still running on top of GNOME2, some pieces didn't seem to fit together:

- GTK theme was still the old gnome 2.x one eventhough the window bar reflected the new GNOME3 version.
- I was unable to change the wallpaper via the GNOME3 panel.  Even if I selected a new one, nothing would change.  I had to use the old GNOME2 panel for that.
- After opening a couple of windows, the animations got sloppy : (

I could go on, but I'm just not sure if this is expected or something went wrong with my installation.  Comments would be appreciated.

---

### Post by cariboo on 2011-03-22
You may be better off doing a Natty cli install using the alternate install iso, then installing the gnome-desktop-environment from the repositories, then installing the gnome 3 packages from the the [Gnome 3 Team]("https://launchpad.net/~gnome3-team/+archive/gnome3") ppa

---

### Post by ngsupb on 2011-03-22
Hi guys,

Do I understand correctly - there is no way to use hotkeys for the favorite applications in the dash in gnome-shell? :( I can't figure out how to switch between applications faster like in Unity.

---

### Post by Merk42 on 2011-03-22
> **sagara said:**
> If I install GNOME 3 on ubuntu 10.10, will this "replace" the GNOME2 stack and let me experience the real GNOME3 or its just an approximation of what it would be like?

After installing it felt like GNOME3 was still running on top of GNOME2, some pieces didn't seem to fit together:

- GTK theme was still the old gnome 2.x one eventhough the window bar reflected the new GNOME3 version.
- I was unable to change the wallpaper via the GNOME3 panel.  Even if I selected a new one, nothing would change.  I had to use the old GNOME2 panel for that.
- After opening a couple of windows, the animations got sloppy : (

I could go on, but I'm just not sure if this is expected or something went wrong with my installation.  Comments would be appreciated.
The pictures in the first post are on a 10.10 installation that had GNOME Shell built from scratch. I'm not sure why you don't see the GTK theme as it changes to that when it changes to the shell.

---

### Post by Mblackwell on 2011-03-22
> **ngsupb said:**
> Hi guys,

Do I understand correctly - there is no way to use hotkeys for the favorite applications in the dash in gnome-shell? :( I can't figure out how to switch between applications faster like in Unity.


Erm... Alt + Tab?

Edit: Also, don't forget Alt + <Above_Tab> (which is whatever key is above tab, on US keyboards ` [generally referred to as ~]) which lets you swap windows within application groups. This works without pressing Alt + Tab first. Note that you can the keyboard and the mouse to interact with the Alt + Tab popup.

---

### Post by Finalfantasykid on 2011-03-22
I personally dislike alt+tab for switching between applications.  Using alt+tab is a sequential way of switching applications.  If you have many programs running, then it can be annoying constantly hitting tab until you get to the right one.  Having something to move your mouse to so that you can simply click on an icon or a task bar item is much easier/faster IMO.

---

### Post by Mblackwell on 2011-03-22
Like... Alt+Tab?

Not to sound trite but you can click on anything in Alt+Tab making it effectively a grouped task-list. Or you can use the overview and click on the dash icons.

---

### Post by Merk42 on 2011-03-22
> **Mblackwell said:**
> Erm... Alt + Tab?

Edit: Also, don't forget Alt + <Above_Tab> (which is whatever key is above tab, on US keyboards ` [generally referred to as ~]) which lets you swap windows within application groups. This works without pressing Alt + Tab first. Note that you can the keyboard and the mouse to interact with the Alt + Tab popup.I think he means how in Unity one can have Super+1 Super+2 etc to instantly launch an app

---

### Post by ngsupb on 2011-03-23
> **Merk42 said:**
> I think he means how in Unity one can have Super+1 Super+2 etc to instantly launch an app

Yes, that is right. I found this way a lot faster rather than clicking alt+tab and choosing a window by using mouse. 

super+[1-9] switches to applications instantly too in case it is already running.

Can't find anything similar in gnome-shell.

---

### Post by moore.bryan on 2011-03-24
I didn't see one, but has the gtk3 build error been solved?
```

./.libs/libgtk-3.so: undefined reference to `gdk_x11_window_set_theme_variant'
collect2: ld returned 1 exit status
linking of temporary binary failed

```

---

### Post by Mblackwell on 2011-03-24
Ignore the error, and then rebuild gtk3. Not sure why but it seems like the file where the function is created is built after the file where the function is called.

---

### Post by cianca on 2011-03-26
When I start GS, i see that everything is a gray box. 

Here's the log

```
~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
Gtk-Message: Failed to load module "globalmenu-plugin"
Advertencia del gestor de ventanas: Los arreglos para aplicaciones rotas se han deshabilitado. Algunas aplicaciones podrían no comportarse correctamente.
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@:0
("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/home/o0o0o0o/gnome-shell/source/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old

(lt-gnome-shell-real:1978): libupower-glib-WARNING **: No 'IsDocked' property
Advertencia del gestor de ventanas: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Advertencia del gestor de ventanas: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sat Mar 26 2011 16:08:37 GMT-0300 (ART)
Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!

Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!

Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!


(lt-gnome-shell-real:1978): Cogl-glx-WARNING **: Skipping layers 1..n of your pipeline since the first layer is sliced. We don't currently support any multi-texturing with sliced textures but assume layer 0 is the most important to keep

(lt-gnome-shell-real:1978): Cogl-glx-WARNING **: Your hardware does not have enough texture unitsto handle this many texture layers
Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!


(lt-gnome-shell-real:1978): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:2011): WARNING **: Unknown option --since=2011-01-25T19:08:41.598929Z
Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!

Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!

Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!


(lt-gnome-shell-real:1978): Cogl-glx-WARNING **: Skipping layer 1 of your pipeline consisting of a sliced texture (unsuported for multi texturing)
^CShell killed with signal 2

```

I'm using an old ATI Radeon 9200SE with the xorg-edgers driver.

---

### Post by Mblackwell on 2011-03-26
the key here is ```

Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!

Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!

Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!


(lt-gnome-shell-real:1978): Cogl-glx-WARNING **: Skipping layers 1..n of your pipeline since the first layer is sliced. We don't currently support any multi-texturing with sliced textures but assume layer 0 is the most important to keep

(lt-gnome-shell-real:1978): Cogl-glx-WARNING **: Your hardware does not have enough texture unitsto handle this many texture layers
Advertencia del gestor de ventanas: Log level 16: NOTE: Not using GLX TFP!

```

---

### Post by WarriorIng64 on 2011-03-26
I was wondering if anyone could help shed some light on something that's been bugging me while I've been using GNOME Shell.

I am running Ubuntu 10.10 64-bit on my laptop, and I decided that I liked it enough that I replaced my regular GNOME login session with it using the instructions found here: [https://live.gnome.org/GnomeShell#Setting_up_gnome-shell_to_run_on_login]("https://live.gnome.org/GnomeShell#Setting_up_gnome-shell_to_run_on_login")

For a little while now, GNOME Shell was supposed to have new authentication dialogues in 2.91.90. Despite rebuilding everything from scratch as recently as a week ago (so now I'm on 2.91.92), I still get the "old" authentication dialogues we already see under GNOME 2.x in Ubuntu.

It was suggested to me that to see the new authentication dialogues, I need to first run ```
killall polkit-gnome-authentication-agent-1
``` and then type ```
r
``` into Alt+F2 to restart the Shell. I tried this but it has no effect.

Any ideas? I'd like to be able to see as much of the Shell as possible. Thanks in advance!

---

### Post by -unseen- on 2011-03-29
Hi,

I have been building GS successfully for a while now, but recently I ran into problems with it. libsoup can't be rebuilt, it gives th following error:

```

...
  CC     soup-proxy-resolver.lo
  CC     soup-proxy-resolver-default.lo
  CC     soup-proxy-resolver-static.lo
  CC     soup-proxy-uri-resolver.lo
  CC     soup-request.lo
  CC     soup-request-data.lo
  CC     soup-request-file.lo
  CC     soup-request-http.lo
  CC     soup-requester.lo
  CC     soup-server.lo
  CC     soup-session.lo
  CC     soup-session-async.lo
  CC     soup-session-feature.lo
  CC     soup-session-sync.lo
  CC     soup-socket.lo
  CC     soup-ssl.lo
  CC     soup-status.lo
  CC     soup-uri.lo
  CC     soup-value-utils.lo
  CC     soup-xmlrpc.lo
  CCLD   libsoup-2.4.la
  CC     soup-cookie-jar-sqlite.lo
  CC     soup-gnome-features.lo
  CC     soup-proxy-resolver-gnome.lo
  CC     soup-password-manager-gnome.lo
  CCLD   libsoup-gnome-2.4.la
  GISCAN Soup-2.4.gir
g-ir-scanner: Soup: warning: 13 warnings suppressed (use --warn-all to see them)
  GISCAN SoupGNOME-2.4.gir
./.libs/libsoup-gnome-2.4.so: undefined reference to `soup_proxy_resolver_default_get_type'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/unseen/gnome-shell/source/libsoup/libsoup/tmp-introspectZDMauN/SoupGNOME-2.4', '-export-dynamic', '-L.', 'libsoup-gnome-2.4.la', '-pthread', '-L/home/unseen/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/unseen/gnome-shell/source/libsoup/libsoup/tmp-introspectZDMauN/SoupGNOME-2.4.o']' returned non-zero exit status 1
make[3]: *** [SoupGNOME-2.4.gir] Error 1
make[3]: Leaving directory `/home/unseen/gnome-shell/source/libsoup/libsoup'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/unseen/gnome-shell/source/libsoup/libsoup'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/unseen/gnome-shell/source/libsoup'
make: *** [all] Error 2
*** Error during phase build of libsoup: ########## Error running make   *** [12/41]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"


```

I already checked wether libproxy-dev, libsoup2.4-dev and libsoup-gnome2.4-dev are installed, and they all are. I couldn't think of any other packages which could be missing.

I also tried deleting the *.la files, but no success either.

Maybe someone else already ran across that problem and found a way to fix it?

thanks

---

### Post by ojdon on 2011-03-30
Hi there,

A couple of days ago I was trying to install Gnome-Shell on my Natty machine using the Gnome 3 Team PPA. But once I log out of the Unity session the gdm switches to a basic grey theme and a black background. Once I log into Gnome-Shell it has no wallpaper and the icons on the top seem to have gone missing. I was using Faenza icons as well in Unity but all the applications reverted back to their default ones. There is no way I can even change the appearance back no matter what session I'm in. 

How can I go about installing Gnome-Shell successfully in Ubuntu? 

Thanks!

---

### Post by lisbonacid on 2011-03-30
> **-unseen- said:**
> Hi,

I have been building GS successfully for a while now, but recently I ran into problems with it. libsoup can't be rebuilt, it gives th following error:

```

...
  CC     soup-proxy-resolver.lo
  CC     soup-proxy-resolver-default.lo
  CC     soup-proxy-resolver-static.lo
  CC     soup-proxy-uri-resolver.lo
  CC     soup-request.lo
  CC     soup-request-data.lo
  CC     soup-request-file.lo
  CC     soup-request-http.lo
  CC     soup-requester.lo
  CC     soup-server.lo
  CC     soup-session.lo
  CC     soup-session-async.lo
  CC     soup-session-feature.lo
  CC     soup-session-sync.lo
  CC     soup-socket.lo
  CC     soup-ssl.lo
  CC     soup-status.lo
  CC     soup-uri.lo
  CC     soup-value-utils.lo
  CC     soup-xmlrpc.lo
  CCLD   libsoup-2.4.la
  CC     soup-cookie-jar-sqlite.lo
  CC     soup-gnome-features.lo
  CC     soup-proxy-resolver-gnome.lo
  CC     soup-password-manager-gnome.lo
  CCLD   libsoup-gnome-2.4.la
  GISCAN Soup-2.4.gir
g-ir-scanner: Soup: warning: 13 warnings suppressed (use --warn-all to see them)
  GISCAN SoupGNOME-2.4.gir
./.libs/libsoup-gnome-2.4.so: undefined reference to `soup_proxy_resolver_default_get_type'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/unseen/gnome-shell/source/libsoup/libsoup/tmp-introspectZDMauN/SoupGNOME-2.4', '-export-dynamic', '-L.', 'libsoup-gnome-2.4.la', '-pthread', '-L/home/unseen/gnome-shell/install/lib64', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/unseen/gnome-shell/source/libsoup/libsoup/tmp-introspectZDMauN/SoupGNOME-2.4.o']' returned non-zero exit status 1
make[3]: *** [SoupGNOME-2.4.gir] Error 1
make[3]: Leaving directory `/home/unseen/gnome-shell/source/libsoup/libsoup'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/unseen/gnome-shell/source/libsoup/libsoup'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/unseen/gnome-shell/source/libsoup'
make: *** [all] Error 2
*** Error during phase build of libsoup: ########## Error running make   *** [12/41]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"


```

I already checked wether libproxy-dev, libsoup2.4-dev and libsoup-gnome2.4-dev are installed, and they all are. I couldn't think of any other packages which could be missing.

I also tried deleting the *.la files, but no success either.

Maybe someone else already ran across that problem and found a way to fix it?

thanks


This can be solved by dropping out of gnome-shell, deleting your local directory and all source directories, and building from scratch.

HOWEVER, on Maverick, while the build is successful since Mar 28th, 2011, with a build from scratch, I'm getting these errors when trying to run gnome-shell:


```
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "globalmenu-plugin"
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/home/ccr/local/share/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old
/home/ccr/local/libexec/gnome-shell-calendar-server: error while loading shared libraries: libecal-1.2.so.8: cannot open shared object file: No such file or directory

(gnome-shell-real:13568): libupower-glib-WARNING **: No 'IsDocked' property
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Wed Mar 30 2011 14:57:45 GMT-0700 (PDT)
    JS ERROR: !!!   Exception was: Error: FIXME: Only supporting zero-terminated ARRAYs
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("FIXME: Only supporting zero-terminated ARRAYs")@gjs_throw:0
([object _private_GObject_GLocalFile],[object _private_Gio_SimpleAsyncResult])@/home/ccr/local/share/gnome-shell/js/ui/search.js:281
([object _private_GObject_GLocalFile],[object _private_Gio_SimpleAsyncResult])@/home/ccr/local/share/gjs-1.0/lang.js:110
'
    JS ERROR: !!!     message = 'FIXME: Only supporting zero-terminated ARRAYs'
    JS ERROR: !!!   Exception was: Error: FIXME: Only supporting zero-terminated ARRAYs
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("FIXME: Only supporting zero-terminated ARRAYs")@gjs_throw:0
([object _private_GObject_GLocalFile],[object _private_Gio_SimpleAsyncResult])@/home/ccr/local/share/gnome-shell/js/ui/search.js:281
([object _private_GObject_GLocalFile],[object _private_Gio_SimpleAsyncResult])@/home/ccr/local/share/gjs-1.0/lang.js:110
'
    JS ERROR: !!!     message = 'FIXME: Only supporting zero-terminated ARRAYs'

(gnome-shell-real:13568): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:13585): WARNING **: Unknown option --since=2011-01-29T21:57:46.148840Z

```

Oddly enough, if I just run "gnome-shell", it knocks out my gnome2 panel. Running "gnome-shell --replace after this allows the shell to run for a little bit, but then instability ensues...

---

### Post by false truths on 2011-03-30
I'm running into the same error on Maverick, with an updated build. I built from scratch 6 days ago and ran jhbuild build again today, and now Gnome Shell tries to run, and crashes with the same errors.

---

### Post by ojdon on 2011-03-30
Does anyone know how to fix my problem?

---

### Post by lisbonacid on 2011-03-30
> **ojdon said:**
> Does anyone know how to fix my problem?

Install from GIT using the jhbuild utility.

---

### Post by bmbaker on 2011-03-31
I have rebuilt gnome shell from scratch 3 times in the last 2 days, had no problems with installing or running after completion.
when i set up to build i always do jhbuild sanitycheck and then jhbuild bootstrap to make sure everything is ok.

one of the reasons i have been rebuilding so often is i have been experimenting with trying solve this :

 ```
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
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
``` 

whilst i have added these files codeset.m4 gettext.m4 glibc21.m4 iconv.m4 lcmessage.m4 progtest.m4 from the aclocal directory to my autoconf directory and also to the aclocal.m4 file

and also added :

```
addpath('PKG_CONFIG_PATH', os.path.join(os.sep, 'opt', 'gnome', 'lib', 'pkgconfig'))
    addpath('ACLOCAL_FLAGS', '/usr/share/aclocal')
    addpath('ACLOCAL_FLAGS', os.path.join(prefix, 'share/aclocal/'))
```

to the .jhbuildrc it still doesn seem to have taken care of this!!

is there something i have missed??
thanks BB

---

### Post by ojdon on 2011-03-31
Trying to install Gnome-Shell from git but I'm stuck at this step:
> *** Error during phase configure of clutter: ########## Error running ./autogen.sh --prefix /home/ollie/gnome-shell/install --libdir '/home/ollie/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [18/41]

Any help?

---

### Post by snlzkn on 2011-04-01
Hello,

I installed gnome-shell to my Natty from the ppas and It seems to work fine but my mutter does not work. All my window borders are terribly ugly. When I write mutter --replace I get this error:
```
mutter --replace
Window manager warning: Failed to load theme "Ambiance": Line 426 character 82: Element <shadow> is not allowed below <frame_style>
Window manager warning: Log level 16: Another compositing manager is running on screen 0
Window manager warning: Log level 8: add_win: assertion `info != NULL' failed
Window manager warning: Log level 8: meta_compositor_sync_window_geometry: assertion `info' failed
Window manager warning: Log level 8: add_win: assertion `info != NULL' failed
Window manager warning: Log level 8: meta_compositor_sync_window_geometry: assertion `info' failed
Window manager warning: Log level 8: add_win: assertion `info != NULL' failed
Window manager warning: Log level 8: meta_compositor_sync_window_geometry: assertion `info' failed
Window manager warning: Log level 8: add_win: assertion `info != NULL' failed
Segmentation fault (core dumped)

```

Gnome-shell is really cool but every window looks so terrible that I don't want to use it :D For some reason I could not find any info on mutter themes or this error. I switched to gnome-shell since my compiz in unity was crashing all the time. I erased all unity and compiz packages I hope this is not somehow related to that...

---

### Post by BigCityCat on 2011-04-03
Two errors

> Error during phase build of evolution-data-server: ########## Error running make

> (gnome-panel:7976): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@:0
("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/home/paul/gnome-shell/source/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old

(lt-gnome-shell-real:8102): libupower-glib-WARNING **: No 'IsDocked' property
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sun Apr 03 2011 17:55:44 GMT-0400 (EST)
    JS ERROR: !!!   Exception was: Error: FIXME: Only supporting zero-terminated ARRAYs
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("FIXME: Only supporting zero-terminated ARRAYs")@:0
("FIXME: Only supporting zero-terminated ARRAYs")@gjs_throw:0
@:0
([object _private_GObject_GLocalFile],[object _private_Gio_SimpleAsyncResult])@/home/paul/gnome-shell/source/gnome-shell/js/ui/search.js:281
([object _private_GObject_GLocalFile],[object _private_Gio_SimpleAsyncResult])@/home/paul/gnome-shell/install/share/gjs-1.0/lang.js:110
'
    JS ERROR: !!!     message = 'FIXME: Only supporting zero-terminated ARRAYs'
    JS ERROR: !!!   Exception was: Error: FIXME: Only supporting zero-terminated ARRAYs
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("FIXME: Only supporting zero-terminated ARRAYs")@:0
("FIXME: Only supporting zero-terminated ARRAYs")@gjs_throw:0
@:0
([object _private_GObject_GLocalFile],[object _private_Gio_SimpleAsyncResult])@/home/paul/gnome-shell/source/gnome-shell/js/ui/search.js:281
([object _private_GObject_GLocalFile],[object _private_Gio_SimpleAsyncResult])@/home/paul/gnome-shell/install/share/gjs-1.0/lang.js:110
'
    JS ERROR: !!!     message = 'FIXME: Only supporting zero-terminated ARRAYs'

(lt-gnome-shell-real:8102): GdmUser-WARNING **: Unable to load CK history: no seat-id found
Shell killed with signal 11
gnome-shell-calendar-server[8125]: Got HUP on stdin - exiting

---

### Post by Mblackwell on 2011-04-03
For now, until we figure out the bug:

- If you get an error during building Clutter just ignore and continue. Everything should still work properly

And for the above issue with search.js, it's known and will be patched. For now:

- If you are running from the install directory, rename/move/delete the folder ~/gnome-shell/install/share/gnome-shell/search_providers
- If you are running from the source directory, rename/move the folder ~/gnome-shell/source/gnome-shell/data/search_providers

---

### Post by WarriorIng64 on 2011-04-04
Thanks! I've been trying to get GNOME Shell to recompile from jhbuild for a couple days now, and the second search_providers folder removal did the trick. I did notice that it takes out the Google and Wikipedia buttons at the bottom of the search screen...but no big deal, at least for me.

---

### Post by Tompalaz on 2011-04-04
At my work they have blocked the git ports. 
However, I can tunnel to my ssh server at home.
Is there a way I bypass the port blocking using my server?

---

### Post by gnomeuser on 2011-04-04
I am determined to make this work with the gnome3 ppa. So far it is going quite well, only gdm and the adwaita default theme do not appear to be working right.

To log in now I have to drop to a vc, log in as my user, service restart gdm and then log in to gnome-shell otherwise no users will appear in the gdm selector.

gnome-themes does not install since it depends on the now non-existent gtk3-engines-pixbuf package (and apt-get/dpkg does not appear to have a way to make them pretend it is installed forever so it happily complains every time you apt-get anything making life miserable.. dpkg how I hate you). Hence the full glory of gnome3 is currently unattainable.

Also a number of the system tools and network manager do not act in a gnome3 way (as they do on the openSUSE based GNOME3 LiveUSB distro).

I signed up for the gnome3 team on lp and hopefully some extra hands on deck will help iron out the last bits.

---

### Post by paul_in_london on 2011-04-04
> To log in now I have to drop to a vc, log in as my user, service restart gdm and then log in to gnome-shell otherwise no users will appear in the gdm selector.

Another workaround you can use to restore the gdm user list is to delete **/var/log/ConsoleKit/history**. This is what I've been doing recently when I need to reboot.

---

### Post by pweyandt on 2011-04-04
I built last night and am running tonight.  If I decide to make Gnome 3.0 my default does it replace Gnome 2.3 or does it give the the choice to boot either 3.0 or 2.3?  
Thanks,
Pete

---

### Post by Todd_1215 on 2011-04-05
I decided to build Gnome 3 yesterday and followed the steps to build from source from [how-do-i-install-the-latest-version-of-gnome-3]("http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3")

I built on Maverick and had to remove the *.la files from /usr/lib directory before building. I also had to install package libmutter-dev which gives you the file Meta-2.91.gir. This wasn't in the list of packages required to build.

My build was successful but it did take me like three or four attempts to build before I got was able to build all 41 modules.

---

### Post by KegHead on 2011-04-05
Hi!

I'm waiting for the release date.

KegHead

---

### Post by cgarre on 2011-04-05
might be an old question .. i used gnome3 ppa on the beta 11.04 ... i am very exited to see gnome 3, it works much better than i had expected. But somehow i am unable to change the title bar, it doesnt look like gnome3, it looks more like windows :) i mean how do i change the windows title bar to look like gnome 3, in ubuntu 11.04 .. also the settings (control center) seems to have very few things to control .. i am guessing this is because ubuntu doesnt support gnome 3 well isnt it ?

---

### Post by mohegan on 2011-04-05
I think the package gnome-themes-standard is missing.
Install it and restart gdm or reboot.

---

### Post by paul_in_london on 2011-04-05
> gnome-themes does not install since it depends on the now non-existent gtk3-engines-pixbuf package (and apt-get/dpkg does not appear to have a way to make them pretend it is installed forever so it happily complains every time you apt-get anything making life miserable.. dpkg how I hate you). Hence the full glory of gnome3 is currently unattainable.

Have this issue on one of my installs, but a fix seems to be in the pipeline. From the changelog:

> Change Log

Version: 2.91.90-0ubuntu1~build2 	2011-04-01 23:03:13 UTC

 gnome-themes (2.91.90-0ubuntu1~build2) natty; urgency=low
 .
   * debian/control.in:
     **+ remove dependency on gtk3-engines-pixbuf**

---

### Post by Mblackwell on 2011-04-05
In the meantime you could always use equivs to build an empty package for gtk3-engines-pixbuf (which doesn't exist anymore because everything is part of gtk3-engines) and install it.

Assuming you're impatient.

---

### Post by buzzmandt on 2011-04-05
this may be already answered in the depths that are this thread, but would someone please help me on a simple matter.....

nm-applet isn't showing for my network manager.  nothing is showing for network managment.  what's the fix for this please?

---

### Post by Mblackwell on 2011-04-05
If you drop back to metacity and remove the indicator applet what happens?

Edit: Any way you go it's probably going to end at [https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741385](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741385)

---

### Post by Quackers on 2011-04-05
Does running ```
nm-applet
``` from a terminal bring it back?

---

### Post by Harry33 on 2011-04-06
Gnome-shell 3 release can now be downloaded from the Gnome3 PPA.
Also new release versions (3.0.0) of Gnome-desktop3, Gnome-settings-daemon, Gnome-themes-standard, libgnomekbd, Mutter and Nautilus are all there.

New upstream Gnome-shell release v. 3.0.0-0ubuntu1
```
Changelog

gnome-shell (3.0.0-0ubuntu1~build1) natty; urgency=low

  * New upstream release
  * debian/control.in:
    + bump build-dep on mutter (>= 3.0.0)
 -- Rico Tzschichholz <email address hidden>   Tue, 05 Apr 2011 19:31:07 +0200
```

---

### Post by KegHead on 2011-04-06
Hi Harry33!

Do you have a link?

Thanks!

KegHead

---

### Post by yaji on 2011-04-06
Anybody managed to run Gnome Shell with proprietary AMD drivers ? I'm asking because I have some problems with it. GS was working fine on open driver, but when I changed it to fglrx, Gnome Shell stopped working at all.

---

### Post by Harry33 on 2011-04-06
> **KegHead said:**
> Hi Harry33!
Do you have a link?
Thanks!
KegHead

Here is the link the Gnome3 PPA:

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

---

### Post by KegHead on 2011-04-06
Hi!

Thanks Harry33!

KegHead

---

### Post by Harry33 on 2011-04-06
> **KegHead said:**
> Hi!

Thanks Harry33!

KegHead

See also this thread (Gnome3):
[http://ubuntuforums.org/showthread.php?t=1722627](http://ubuntuforums.org/showthread.php?t=1722627)

---

### Post by buzzmandt on 2011-04-08
> **Quackers said:**
> Does running ```
nm-applet
``` from a terminal bring it back?
```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ nm-applet
An instance of nm-applet is already running.

** (nm-applet:30358): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ 

```
just rebuilt today (4/8/11) still no network manager.  complains about it already running

---

### Post by KegHead on 2011-04-08
Hi!

I tried and tried to make G3 work for me.

I tried it on Fedora 15.

It's just not for me.

I still love 11.04/classic/2.6.39.

KegHead

---

### Post by NightwishFan on 2011-04-08
I think personally I might go with Gnome Shell over Unity (and considering I am on Debian) I love how the mutter animations are always so clean. It looks really professional. (Not that Unity isn't)

I am going to move my family to Unity though.

---

### Post by KegHead on 2011-04-08
Hi!

I'm downloading Debian as I write this memo.

Any thoughts?

KegHead

---

### Post by NightwishFan on 2011-04-08
I couldn't compile it on stable, it works fine on Testing. The only issue is you will have to add the experimental repo and install: xulrunner-dev and libmozjs-dev (version 2.0 or so)

Remember to disable experimental after you install these.

---

### Post by KegHead on 2011-04-08
Hi!

Looked at Debian...it's nice, but I love Ubuntu.

Worst case---Xubuntu.

KegHead

---

### Post by Quackers on 2011-04-09
I just installed it using the gnome3 ppa and after a little tweaking it's fine :-)
It also has the "benefit" of getting the menu bar back at the top of the individual screens :-) (although it wasn't a problem for me with the global menu thing).
The only thing that has happened (once) is that synaptic was not closable after running some updates. It was "not responding" and I needed to force close it. It then would not open again until I rebooted. It seems fine now.

---

### Post by Nonno Bassotto on 2011-04-16
I can compile Gnome Shell fine on Ubuntu 10.04, but when I try to launch the shell, I have the same error as **illbashu** and **centos** on page 84

```

andrea@Leibniz:~/gnome-shell/install/bin$ ./gnome-shell --replaceGtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "atk-bridge"
Panel leaving: a new panel shell is starting.

(gnome-panel:20006): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@:0
("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/home/andrea/gnome-shell/install/share/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old

(gnome-shell-real:20455): libupower-glib-WARNING **: No 'IsDocked' property
Avviso del window manager: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Avviso del window manager: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sat Apr 16 2011 15:34:29 GMT+0200 (CET)
Avviso del window manager: Treating resize request of legacy application 0x7200067 (In arrivo ) as a fullscreen request
Avviso del window manager: Treating resize request of legacy application 0x900008d (GNOME Shel) as a fullscreen request
gnome-shell-calendar-server[20471]: Got HUP on stdin - exiting
Shell killed with signal 11

```

Is there any solution?

---

### Post by moore.bryan on 2011-04-16
I just installed from the GNOME3 PPA on a *completely* fresh Natty install and have only one gripe: the "Date and Time Settings" is *still* broke. Seriously guys... how hasn't this been fixed? Does anyone know of another way to launch those settings without needing to butcher the dateMenu.js file? I *know* how to hack GS to make it do what I want, but was hoping I didn't need to go down that route.

Thanks, in-advance...

---

### Post by KegHead on 2011-04-16
Hi Nonno,

Your English is great!

KegHead

---

### Post by Mblackwell on 2011-04-17
> **Nonno Bassotto said:**
> I can compile Gnome Shell fine on Ubuntu 10.04, but when I try to launch the shell, I have the same error as **illbashu** and **centos** on page 84

```

andrea@Leibniz:~/gnome-shell/install/bin$ ./gnome-shell --replaceGtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "atk-bridge"
Panel leaving: a new panel shell is starting.

(gnome-panel:20006): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@:0
("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/home/andrea/gnome-shell/install/share/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old

(gnome-shell-real:20455): libupower-glib-WARNING **: No 'IsDocked' property
Avviso del window manager: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Avviso del window manager: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sat Apr 16 2011 15:34:29 GMT+0200 (CET)
Avviso del window manager: Treating resize request of legacy application 0x7200067 (In arrivo ) as a fullscreen request
Avviso del window manager: Treating resize request of legacy application 0x900008d (GNOME Shel) as a fullscreen request
gnome-shell-calendar-server[20471]: Got HUP on stdin - exiting
Shell killed with signal 11

```

Is there any solution?

Run with -rg so it runs gdb. Get a backtrace.

---

### Post by 23dornot23d on 2011-04-17
Is there anybody else here getting this on upgrades ..... its the only package I cannot get
to install using aptitude safe-upgrade

```



root@keith-Aspire-7730ZG:/home/keith# aptitude safe-upgrade
Resolving dependencies...                
The following packages will be upgraded:
  gnome-accessibility-themes 
1 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0 B/414 kB of archives. After unpacking 0 B will be used.
Do you want to continue? [Y/n/?] y
(Reading database ... 328454 files and directories currently installed.)
Preparing to replace gnome-accessibility-themes 2.32.1-0ubuntu1 (using .../gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb) ...
Unpacking replacement gnome-accessibility-themes ...
dpkg: error processing /var/cache/apt/archives/gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb (--unpack):
 trying to overwrite '/usr/share/themes/HighContrastInverse/index.theme', which is also in package gnome-themes-standard 3.0.0-1~~build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
                                         
root@keith-Aspire-7730ZG:/home/keith# 





```I just wondered if anyone had a solution to this ...... as this will not install .....

---

### Post by pulpo69 on 2011-04-17
i've the same problem if i try to install gnome-themes-standard and get the same error message.
i don't get the shell only a purple screen and nothing.

---

### Post by bmbaker on 2011-04-17
try:
sudo dpkg -i --force-all /var/cache/apt/archives/gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb

> **23dornot23d said:**
> Is there anybody else here getting this on upgrades ..... its the only package I cannot get
to install using aptitude safe-upgrade

```



root@keith-Aspire-7730ZG:/home/keith# aptitude safe-upgrade
Resolving dependencies...                
The following packages will be upgraded:
  gnome-accessibility-themes 
1 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0 B/414 kB of archives. After unpacking 0 B will be used.
Do you want to continue? [Y/n/?] y
(Reading database ... 328454 files and directories currently installed.)
Preparing to replace gnome-accessibility-themes 2.32.1-0ubuntu1 (using .../gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb) ...
Unpacking replacement gnome-accessibility-themes ...
dpkg: error processing /var/cache/apt/archives/gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb (--unpack):
 trying to overwrite '/usr/share/themes/HighContrastInverse/index.theme', which is also in package gnome-themes-standard 3.0.0-1~~build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
                                         
root@keith-Aspire-7730ZG:/home/keith# 





```I just wondered if anyone had a solution to this ...... as this will not install .....

---

### Post by bmbaker on 2011-04-17
you can look through this link it has alot of useful info that might help :-)
[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)
[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

---

### Post by Nonno Bassotto on 2011-04-17
> **Mblackwell said:**
> Run with -rg so it runs gdb. Get a backtrace.

It seems I get no stack. How do I obtain a proper backtrace?

```

andrea@Leibniz:~/gnome-shell/install/bin$ ./gnome-shell -rg --replace
GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/andrea/gnome-shell/install/bin/gnome-shell-real...done.
(gdb) backtrace
No stack.

```

---

### Post by 23dornot23d on 2011-04-17
> **bmbaker said:**
> try:
sudo dpkg -i --force-all /var/cache/apt/archives/gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb


worked like a charm bmbaker - thank you once again ... this is becoming a regular now and I thank you very much for your help so far ..... ;)

```

keith@keith-Aspire-7730ZG:~$ sudo dpkg -i --force-all /var/cache/apt/archives/gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb
[sudo] password for keith: 
(Reading database ... 328454 files and directories currently installed.)
Preparing to replace gnome-accessibility-themes 2.32.1-0ubuntu1 (using .../gnome-accessibility-themes_3.0.0-0ubuntu1~build2_all.deb) ...
Unpacking replacement gnome-accessibility-themes ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/themes/HighContrastInverse/index.theme', which is also in package gnome-themes-standard 3.0.0-1~~build1
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/icons/HighContrastInverse/index.theme', which is also in package gnome-themes-standard 3.0.0-1~~build1
Setting up gnome-accessibility-themes (3.0.0-0ubuntu1~build2) ...
gtk-update-icon-cache: Cache file created successfully.
keith@keith-Aspire-7730ZG:~$ 


```

---

### Post by bmbaker on 2011-04-17
ur very welcome :-)

---

### Post by pulpo69 on 2011-04-17
i only get a purple screen when starting gnome-shell (via gdm).

gnome-shell: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

any idea?

---

### Post by 23dornot23d on 2011-04-17
Have you tried to purge the gnome 3 team PPA and then start again ..... this worked for me
a while back ...... and everything has been going forward since doing that .......

Here are the list of things I do ....... do them at your own risk though ......

 [GNOME3 THE WAY I INSTALLED IT]("https://sites.google.com/site/000menu/home/gnome---3")

**[COLOR=Red]USE only if you are testing and in a test environment[/COLOR]** - this I add as the same results 

may not apply to every computer and to every configuration

Worked for me though ..... and now I progress ..... with every update installed and no visible errors on upgrades ..... now ..... ;)

---

### Post by bmbaker on 2011-04-17
> **pulpo69 said:**
> i only get a purple screen when starting gnome-shell (via gdm).

gnome-shell: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

any idea?
if you have the mozilla daily ppa enabled
try this:-
search your system for libmozjs.so
and link like i done below

cd /usr/lib/
sudo ln -s /usr/lib/xulrunner-1.9.2.16pre/[libmozjs.so]("http://libmozjs.so/") [libmozjs.so]("http://libmozjs.so/")
sudo ldconfig [libmozjs.so]("http://libmozjs.so/")

[http://live.gnome.org/JhbuildIssues/mutter](http://live.gnome.org/JhbuildIssues/mutter)

---

### Post by bmbaker on 2011-04-17
> **bmbaker said:**
> you can look through this link it has alot of useful info that might help :-)
[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)
[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

check through these two links for what you need :-)

---

### Post by Ikbear on 2011-04-20
Hi, i did everything successfully, but after run this command: 

```
./gnome-shell --replace
```

 i get this error:

```
failed to create drawable

(lt-gnome-shell-real:2058 ) : Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context
Window manager error: Unable to initialize Clutter.
ikbear@Campusnetwork:~/gnome-shell/source/gnome-shell/src$ /usr/bin/compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
```

So what's the problem?

Thanks!

---

### Post by trusktr on 2011-04-24
Ikbear, Removing "nomodeset" from my kernel boot line (in Arch Linux that's in /boot/grub/menu.lst) fixed this issue for me.

---

### Post by dirk74 on 2011-04-24
I have a Gnome Shell from PPA on top of 11.04 Beta 2. The problem is with metacity. This is my screenshot:

[http://img823.imageshack.us/i/screenshotwko.jpg](http://img823.imageshack.us/i/screenshotwko.jpg)

Anyone with an idea to fix this?

---

### Post by dirk74 on 2011-04-24
I figured it out on another page. What needs to be done is:

sudo apt-get purge gnome-accessibility-themes 
sudo apt-get install gnome-themes-standard

---

### Post by matt_symes on 2011-04-24
/

---

### Post by pferraro on 2011-04-24
> **dirk74 said:**
> I have a Gnome Shell from PPA on top of 11.04 Beta 2. The problem is with metacity. This is my screenshot:

[http://img823.imageshack.us/i/screenshotwko.jpg](http://img823.imageshack.us/i/screenshotwko.jpg)

Anyone with an idea to fix this?

The Ambiance metacity theme does not work with mutter (and hasn't for a while now - anyone know why?).  Try changing the window border theme to "Adwaita" (the gnome-shell default), or any other theme for that matter:

gconftool --type string --set /desktop/gnome/shell/windows/theme Adwaita

The change does not take effect immediately.  Hit Alt-F2, then "r", then enter.  Presto...

---

### Post by moore.bryan on 2011-04-25
Just to share... successfully built on Natty this morning.

---

### Post by M4570D0N on 2011-04-25
> **dirk74 said:**
> I have a Gnome Shell from PPA on top of 11.04 Beta 2. The problem is with metacity. This is my screenshot:

[http://img823.imageshack.us/i/screenshotwko.jpg](http://img823.imageshack.us/i/screenshotwko.jpg)

Anyone with an idea to fix this?

Check out these two articles and some additional info in the comments of the articles:
[http://www.webupd8.org/2011/04/change-gnome-3-gnome-shell-or-classic.html](http://www.webupd8.org/2011/04/change-gnome-3-gnome-shell-or-classic.html)
[http://www.webupd8.org/2011/04/adwaita-improved-reduced-padding-for.html](http://www.webupd8.org/2011/04/adwaita-improved-reduced-padding-for.html)

---

### Post by illbashu on 2011-04-25
```
Please make sure that the AccountService is installed and enabled.
```

Anyone know how to fix that?

---

### Post by shaneo1 on 2011-04-25
Hi guys, this is my first post to the Ubuntu Forum, and I am rather new  to Ubuntu as well after discovering the power of linux back in January  2011, and ditching M$ all together.

I have been using Meerkat 10.10 and have recently installed 11.04 beta  2, not really liking the unity theme for desktop though it is very good  for net books, I decided to install Gnome 3 as detailed here [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

I used the command line:
```
sudo add-apt-repository ppa:gnome3-team/gnome3 
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
```and it installed great and I like it very much. However I have reinstalled
it a couple of times now and each time, I restart my machine and I login to
Gnome Shell, the activities task panel is missing from the top and I am unable
to do anything other than browse the web as firefox was the last window I had
open.  Pressing any of the keys like the super key or alt-f2 doesn't work.  
Also the windows theme has default to what Gmone 1 used to look like.

I would love to take a screen shot and show you what I mean but I cant.  

I can however drop in to tty1, ctrl-alt F1. 

Does anyone have any ideas how I can get my top panel back?  Many thanks in advance.
Btw I don't want to do a fresh install as I have some work on here I would like to keep
and some jack settings I don't want to have to do again to get wineasio working :smile:

Thanks  :popcorn: 


Shaneo

---

### Post by shaneo1 on 2011-04-25
Ok I have managed to restart gnome shell, but I get this error following it plus if I close terminal I lose Gnome Shell, do I have to have terminal open all the time to have it working?  or is there another way, the other thing is I have noticed is that root is showing in the top left not my user name....

```
$ sudo gnome-shell --replace
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old
Window manager warning: Log level 16: Error getting session for the process we are in: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2645' (g-io-error-quark 36)
      JS LOG: GNOME Shell started at Mon Apr 25 2011 20:48:53 GMT+0100 (BST)
```thanks

---

