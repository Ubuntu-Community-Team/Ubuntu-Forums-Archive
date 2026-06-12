---
title: "How to Properly install Gimpshop so it does NOT break the Gimp"
date: 2008-07-25
forum: Multimedia Software
---

### Post by Maverick88 on 2008-07-25
Gimpshop is a hack on an older version of the Gimp (version 2.2).  It tries to rearrange the menus so that they look more like Photoshop. 

Gimpshop is old and has not been updated for some time.  So please note that you can no longer print from gimpshop in Hardy Heron (since it uses the older gimp-print system).  If you want to print your creations, load your image into another program (like the Gimp 2.4.5) and print from there.

Around the net you will see sites explain that all you need to do to install gimpshop on Hardy Heron is the following:

1.  Download the .DEB package for gimphop from the gimpshop website. ( [http://www.gimpshop.com/](http://www.gimpshop.com/) )
2.  Run the following command in an administrators account in Terminal:

sudo dpkg -i (path to gimpshop package)

3.  To run gimpshop, run the following in a Terminal:

/usr/local/bin/gimp

4.   (Optional) Create a menu item in GNOME, KDE etc for gimpshop

And yes for a  SHORT period of time, you can get BOTH the gimp and gimpshop to work at the same time using these instructions.  But the minute you upgrade or **install ANY PACKAGE** (which does not even have to be related to the gimp or gimpshop) or run "ldconfig", **THE GIMP WILL NO LONGER WORK**.  (But you can still run gimpshop)

When you install any package from the repos or run "sudo ldconfig", the library cache is regenerated.  It is the regeneration of the library cache AFTER gimpshop is installed that breaks the gimp.  When you run the gimp, you will see this message:

./gimp-2.4: symbol lookup error: ./gimp-2.4: undefined symbol: gimp_micro_version

Please note that the problem with the gimp not starting is related to the way gimpshop was packaged. Gimpshop is an OLD unofficial package so you really cannot blame Ubuntu.  The gimpshop package probably worked just fine on older Ubuntu systems where gimp 2.2 was installed. 

On newer Ubuntu systems like Hardy Heron, you would have been able to avoid these problems if you compiled from source and used the right compile options.  So binary packages (although convenient) are often the source of problems especially if they are old and unofficial!


**_THE PROBLEM:_**

Since the gimp is part of the Ubuntu repositories, the gimp's libraries are located in /usr/lib and /usr.  To work properly, the gimp must load its libraries from these two locations.

On the other hand, since the gimp is really a third party hack, the gimpshop's libraries are located in /usr/local/lib.  If you are compiling software from source (and not using the Ubuntu packages), one typically deposits the final binary in /usr/local/bin and any needed libraries in /usr/local/lib.  So the gimpshop approach is not too crazy.

The problem with the Gimp failing to start is related to how Linux systems load libraries.

Like most Linux systems, Ubuntu FIRST loads libraries from /usr/local/lib and THEN loads libraries from /usr/lib and /lib.

So when you try to run the Gimp, the Gimp first looks into the /usr/local/lib location and loads some older, conflicting libraries (which just happen to have the same names as the newer libraries) and tries to use them.  As a result, the Gimp fails to run.

(But gimpshop runs just fine since Ubuntu first loads the libraries in the /usr/local/lib directory where gimpshop installed its libraries).


_**THE SOLUTION:**_

You could change the order in which Linux loads libraries but that is not advisable.  Some other programs may not run if they do not load libraries from /usr/local/lib first.

So if you really want to keep both the gimp and gimpshop on the same computer, you have two choices:

1.  Recompile the gimpshop from source and tell it to save its libraries in another library location (e.g.  /usr/local/gimplib directory) and the main program in a location preferably not in the PATH such as the /usr/local/gimpbin directory.  Then run gimpshop like this:

LD_LIBRARY_PATH=/usr/local/gimplib  /usr/local/gimpbin/gimp

OR

2.  Tell JUST the Gimp to FIRST load the libraries in /usr/lib and /lib FIRST before loading any libraries in /usr/local/lib (where the gimpshop package presently stores its libraries).

The first solution is really the best solution but it is more work.  You might even be able to compile back in printing support for gimpshop.

The second solution is easier but might have drawbacks.  Here is how you do it.  To run the gimp from the Terminal, just type:

LD_LIBRARY_PATH=/usr/lib  /usr/bin/gimp

Give it a try and you will see that the Gimp now runs again since it first looks in the /usr/lib direcrory for its libraries.  This command ONLY affects where the gimp (/usr/bin/gimp) looks for its libraries.  It does not affect other programs.

To be able to run the Gimp from the GNOME GUI (e.g. Applications - Graghics - Gimp), you will need to create a shell script and tell the GNOME GUI to run it when you click the menu item.

To create the shell script, navigate to the /usr/bin folder and create a file called "gimp-hack-2.4" as follows:

cd /usr/bin
sudo gedit gimp-hack-2.4

Now type the following into the editor and save it:

#!/bin/sh

LD_LIBRARY_PATH=/usr/lib  /usr/bin/gimp

# EOF

Now change some of the symbolic links.  Right now /usr/bin/gimp points to /usr/bin/gimp-2.4.  We want /usr/bin/gimp to point to /usr/bin/gimp-hack-2.4.  So run these commands:

cd /usr/bin
sudo ln -sf  gimp-hack-2.4  gimp
ls -la gimp*

Now you should see gimp pointing to gimp-hack-2.4.  So you can just run the gimp from the /usr/bin directory by typing just "./gimp".  If you are not in that directory, type /usr/bin/gimp.

Now edit the menu item for the gimp in GNOME. 

1.  Click on System - Preferences - Main Menu.
2.  Click on "Graphics" in the leftmost column called Menus.
3.  Now RIGHT Click on "GIMP Image Editor" in the Items column and select properties.
4.  Change the Command line to read as follows:

/usr/bin/gimp %U

5.  Save changes

That is it!!  You will have to make the changes to the GNOME Menus in EACH user account if you want other users to be able to run the Gimp from the Menus.

[B][U]
POSSIBLE SHORTCOMINGS WITH THE SECOND APPROACH:[/U][/B]

If other programs and scripts call /usr/bin/gimp-2.4, gimp will not run.  Other programs and scripts should really call /usr/bin/gimp which should work.


_**Making Menu Items for Gimpshop:**_

The gimpshop package does not install or create any menu items in GNOME, KDE, etc.  But you can do it.  e.g. For GNOME in Ubuntu, do the following:

1. Click on System - Preferences - Main Menu.
2. Click on "Graphics" in the leftmost column called Menus.
3. Click on "New Item" button.
4. Change the Name to "Gimpshop"
4. Change the Command line to read as follows:

/usr/local/bin/gimp %U

5. Save changes

That is it!! You will have to make the changes to the GNOME Menus in EACH user account if you want other users to be able to run the Gimpshop from the Menus.

Good luck and have fun with Gimpshop and the Gimp.

---

### Post by EXCiD3 on 2008-07-25
Nice tut. I will ahve to try this out, i remember using Gimpshop back in the day on windows and totally forgot about it. Gives me a good reason to start learning Gimp again ;)

---

### Post by Maverick88 on 2008-07-25
There is also a THIRD solution which I did not mention.  Compile gimpshop so it does not dynamically load libraries.  i.e. build with static libraries built into the binary.  This makes the binary large and inefficient.  But it should not create any shared libraries in /usr/local/lib.  As a result, the gimp 2.4.5 should continue to run.

I understand many third party developers use this approach to avoid problems with Linux distros that may have incompatible libraries.  (e.g. Google earth?  Skype?)

I prefer the two other approaches in my previous post which use dynamic libraries.  You will use less RAM in the long run, etc.

---

### Post by Maverick88 on 2008-07-26
OOPS I made a small mistake in the gimp-hack-2.4 scipt and forgot to tell you to make it executable.  gimp-hack-2.4 should look like this:

#!/bin/sh

LD_LIBRARY_PATH=/usr/lib /usr/bin/gimp-2.4

# EOF

To make it executable.  Run "sudo chmod +x /usr/bin/gimp-hack-2.4"

I have also added instructions to change the name of the gimpshop executable from gimp to gimpshop. Now "gimp" in Terminal runs the gimp 2.4.5 and "gimpshop"runs gimpshop.

Here are the instructions again (Rev 2) with all the errors fixed and the new additions.  I tested them by booting off the Hardy Heron 8.04.1 LiveCD, installing gimpshop and following my instructions.  They should work without error.

_**[SIZE="6"]REV 2 - How to Properly install Gimpshop so it does NOT break the Gimp[/SIZE]**_

Gimpshop is a hack on an older version of the Gimp (version 2.2). It tries to rearrange the menus so that they look more like Photoshop.

Gimpshop is old and has not been updated for some time. So please note that you can no longer print from gimpshop in Hardy Heron (since it uses the older gimp-print system). If you want to print your creations, load your image into another program (like the Gimp 2.4.5) and print from there.

Around the net you will see sites explain that all you need to do to install gimpshop on Hardy Heron is the following:

1. Download the .DEB package for gimphop from the gimpshop website. ( [http://www.gimpshop.com/](http://www.gimpshop.com/) )
2. Run the following command in an administrators account in Terminal:

sudo dpkg -i (path to gimpshop package)

3. To run gimpshop, run the following in a Terminal:

/usr/local/bin/gimp

4. (Optional) Create a menu item in GNOME, KDE etc for gimpshop

And yes for a SHORT period of time, you can get BOTH the gimp and gimpshop to work at the same time using these instructions. But the minute you upgrade or install ANY PACKAGE (which does not even have to be related to the gimp or gimpshop) or run "ldconfig", THE GIMP WILL NO LONGER WORK. (But you can still run gimpshop)

When you install any package from the repos or run "sudo ldconfig", the library cache is regenerated. It is the regeneration of the library cache AFTER gimpshop is installed that breaks the gimp. When you run the gimp, you will see this message:

./gimp-2.4: symbol lookup error: ./gimp-2.4: undefined symbol: gimp_micro_version

Please note that the problem with the gimp not starting is related to the way gimpshop was packaged. Gimpshop is an OLD unofficial package so you really cannot blame Ubuntu. The gimpshop package probably worked just fine on older Ubuntu systems where gimp 2.2 was installed.

On newer Ubuntu systems like Hardy Heron, you would have been able to avoid these problems if you compiled from source and used the right compile options. So binary packages (although convenient) are often the source of problems especially if they are old and unofficial!


_**THE PROBLEM:**_

Since the gimp is part of the Ubuntu repositories, the gimp's libraries are located in /usr/lib and /usr. To work properly, the gimp must load its libraries from these two locations.

On the other hand, since the gimp is really a third party hack, the gimpshop's libraries are located in /usr/local/lib. If you are compiling software from source (and not using the Ubuntu packages), one typically deposits the final binary in /usr/local/bin and any needed libraries in /usr/local/lib. So the gimpshop approach is not too crazy.

The problem with the Gimp failing to start is related to how Linux systems load libraries.

Like most Linux systems, Ubuntu FIRST loads libraries from /usr/local/lib and THEN loads libraries from /usr/lib and /lib.

So when you try to run the Gimp, the Gimp first looks into the /usr/local/lib location and loads some older, conflicting libraries (which just happen to have the same names as the newer libraries) and tries to use them. As a result, the Gimp fails to run.

(But gimpshop runs just fine since Ubuntu first loads the libraries in the /usr/local/lib directory where gimpshop installed its libraries).


_**THE SOLUTION:**_

You could change the order in which Linux loads libraries but that is not advisable. Some other programs may not run if they do not load libraries from /usr/local/lib first.

So if you really want to keep both the gimp and gimpshop on the same computer, you have two choices:

1. Recompile the gimpshop from source and tell it to save its libraries in another library location (e.g. /usr/local/gimplib directory) and the main program in a location preferably not in the PATH such as the /usr/local/gimpbin directory. Then run gimpshop like this:

LD_LIBRARY_PATH=/usr/local/gimplib /usr/local/gimpbin/gimp

OR

2. Tell JUST the Gimp to FIRST load the libraries in /usr/lib and /lib FIRST before loading any libraries in /usr/local/lib (where the gimpshop package presently stores its libraries).

The first solution is really the best solution but it is more work. You might even be able to compile back in printing support for gimpshop.

The second solution is easier but might have drawbacks. Here is how you do it. To run the gimp from the Terminal, just type:

LD_LIBRARY_PATH=/usr/lib /usr/bin/gimp

Give it a try and you will see that the Gimp now runs again since it first looks in the /usr/lib direcrory for its libraries. This command ONLY affects where the gimp (/usr/bin/gimp) looks for its libraries. It does not affect other programs.

To be able to run the Gimp from the GNOME GUI (e.g. Applications - Graghics - Gimp), you will need to create a shell script and tell the GNOME GUI to run it when you click the menu item.

To create the shell script, navigate to the /usr/bin folder and create a file called "gimp-hack-2.4" as follows:

cd /usr/bin
sudo gedit gimp-hack-2.4

Now type the following into the editor and save it:

#!/bin/sh

LD_LIBRARY_PATH=/usr/lib /usr/bin/gimp-2.4

# EOF

Now make the gimp-hack-2.4 script executable by running these commands in Terminal:

cd /usr/bin
sudo chmod +x gimp-hack-2.4


Now change some of the symbolic links. Right now /usr/bin/gimp points to /usr/bin/gimp-2.4. We want /usr/bin/gimp to point to /usr/bin/gimp-hack-2.4. So run these commands:

cd /usr/bin
sudo ln -sf gimp-hack-2.4 gimp
ls -la gimp*

Now you should see gimp pointing to gimp-hack-2.4. So you can just run the gimp from the /usr/bin directory by typing just "./gimp". If you are not in that directory, type /usr/bin/gimp.

Now edit the menu item for the gimp in GNOME.

1. Click on System - Preferences - Main Menu.
2. Click on "Graphics" in the leftmost column called Menus.
3. Now RIGHT Click on "GIMP Image Editor" in the Items column and select properties.
4. Change the Command line to read as follows:

/usr/bin/gimp %U

5. Save changes

That is it!! You will have to make the changes to the GNOME Menus in EACH user account if you want other users to be able to run the Gimp from the Menus.


_**POSSIBLE SHORTCOMINGS WITH THE SECOND APPROACH:**_

If other programs and scripts call /usr/bin/gimp-2.4, gimp will not run. Other programs and scripts should really call /usr/bin/gimp which should work.

If other programs use gimp libraries, they might end up loading some of older, obsolete libraries in /usr/local/lib (in which gimpshop stored its libraries).  If so, they might crash.  You can fix these programs by doing a similar hack.  (e.g. running a script where LD_LIBRARY_PATH=/usr/lib is placed before command which runs the program,

The best solution really is option 1 where you recompile gimpshop so it saves its libraries in another location.


**_Changing The Name of the Gimpshop Executable From gimp to gimpshop_**

You will notice that if you open up a Terminal and run "gimp", gimpshop launches and NOT the gimp-2.4.5.  Since gimpshop placed its executable (called just gimp) in /usr/local/bin, it is launched first due to the order of directories listed in your PATH environment variable.  (Open up the Terminal and run "echo $PATH" to see for yourself). 

It is easily fixed by just changing the name of the gimpshop executable from gimp to gimpshop.  Run these commands in Terminal:

cd /usr/local/bin
sudo mv gimp gimpshop

Now gimp runs gimp and gimpshop runs gimpshop!


_**Making Menu Items for Gimpshop:**_

The gimpshop package does not install or create any menu items in GNOME, KDE, etc. But you can do it. e.g. For GNOME in Ubuntu, do the following:

1. Click on System - Preferences - Main Menu.
2. Click on "Graphics" in the leftmost column called Menus.
3. Click on "New Item" button.
4. Change the Name to "Gimpshop"
4. Change the Command line to read as follows:

/usr/local/bin/gimpshop %U

5. Save changes

That is it!! You will have to make the changes to the GNOME Menus in EACH user account if you want other users to be able to run the Gimpshop from the Menus.

Good luck and have fun with Gimpshop and the Gimp.

---

### Post by map on 2009-01-20
Having seen gimpshop now, I've seen enough of it.  That is, I'd appreciate it if you'd tell me how to uninstall it since I don't really feel a need for it and the 'real' gimp, the latter being enough for me.

I did try somebody's claimed method for getting rid of gimpshop, but it didn't work and since you seem to be extremely knowledgeable in the gimp vs. gimpshop area, I'm hoping your advice will do the trick.

A reply here would probably help others who were ashamed to ask, but a direct reply to me (which I seem to recall can be done via the Forum, somehow or another) in addition would be greatly appreciated, so i won't have to remember to keep checking in here.  After all, I've already forgotten the suggested removal method I used, and that was only around half an hour ago....

thanks and cheers, map

---

