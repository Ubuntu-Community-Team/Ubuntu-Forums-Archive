---
title: "Mobility Radeon 9600 M10"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by HybridGhost on 2007-05-15
Well I just Re-Installed Ubuntu and was playing a game of chess, going through the options and tried to turn on 3D mode, it came back saying...

"Your system does not have the required software to enable 3D mode.  Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings."

Anybody lend a helping hand to help me understand what those two things are?

I looked but if I clearly missed something, I'm more than willing to read if you point :)

Regards,

---

### Post by Vincent_Lin on 2007-05-15
Hi,

My IBM T42 has this ATI 9600 Mobility chip.  It took me a while to figure out how to enable 3D in ubuntu.  Thanks to friendly ubuntuforums help.  

First run this command in a terminal "glxinfo | grep direct".  If the return is similar to "Direct Rendering: yes", then your machine has 3D acceleration enabled.  Then someone else is more qualified to answer your question in terms that specific issue.

If the return from this command is similar to "Direct rendering: no", your installation does not have 3D acceleration enabled.  And most likely the installation of fglrx driver could resolve everything for you.

There are many ways to enable 3D acceleration for various ATI chips.  For this specific chip 9600M, basically you need to install fglrx driver from ATI.  However, those methods that you can find in this forum and elsewhere, those that are simple enough as either download installation script from ATI site and run it, or use command "sudo apt-get install xorg-driver-fglrx"  just did not work for me, at least on my T42.

I hope your machine is a fresh install and nothing serious are on your machine at this moment, because the only way I know of that can actually enable 3D acceleration for my T42/9600 Mobility requires a fresh install of ubuntu.

I followed this thread to install fglrx driver -  [http://ubuntuforums.org/showthread.php?t=191944](http://ubuntuforums.org/showthread.php?t=191944).
You might want to follow this thread, step by step as it is said, you should be all set.  No difference at all among different ubuntu versions.  As a matter of fact, I just installed Feisty on my T42 last night with this method and have 3D acceleration enabled. 

I still don't understand precisely why and what's the difference between this method and all other methods with fglrx driver.  The only possible guess, mine as well as others, is that "normal" ubuntu installation detects 9600M as an ATI chip and installs radeon driver by itself.  However, later installation of fglrx, no matter which method you try, does not overwrite (or fail to overwrite) some specific file(s) (version mismatch most likely) so that 3D acceleration is not enabled completely from this fglrx driver.  This method in above mentioned thread first installs vesa driver, so that you can later on install "clean" fglrx driver without instances.

Hope this works for you, and good luck.

Vincent

---

### Post by HybridGhost on 2007-05-15
Yes, it's a fresh install :) Havn't put anything on it till I get it running right.

Unfortunatly thought it says.

"Direct Rendering : Yes"

I thank you for your time and effort put into that post and it makes me happy that someone cares... I have a feeling there is something else that isn't working at this point though...

Anybody have any other ideas?

Regards,

---

### Post by Vincent_Lin on 2007-05-15
OK.  Your are welcome.

Go to Synaptic Package Manager, and type in OpenGL in search box, you will see python-opengl package there.  Mark it.  And then search gtkgl again and you will see libgtkglext1. mark it.

Then Click apply to allow it to install these packages, and other related packages, if any.  Try your Chess program and I think you should be fine after that.  

What Chess program?  Maybe I should be trying it as well.

Good luck.

Vincent

---

### Post by HybridGhost on 2007-05-15
Haha, I didn't know there was such a neat tool... I have to get my wireless nic working first though...  If I was at home it would be different but here I can't use the net without wireless enabled so I wil try that and see what happenes.

And it's the Chess game that comes with the install (Or updates?) with Ubuntu.

Again, thanks for all the help thus far, you've been a great help :)

Regards,

---

### Post by HybridGhost on 2007-05-15
Ok well Ive installed both of those and I still get the same message... Hm... any other ideas?

Regards,

---

### Post by Vincent_Lin on 2007-05-15
I tried Chess and I got the same message when I enabled 3D.

I search synaptic for python opengl gtkglext and installed some libraries that look suspicious enough for me, but still no go.

So I went to the source.  Open About Chess and you are offered a link to the homepage of this program.

[http://glchess.sourceforge.net](http://glchess.sourceforge.net)

Then you can click on packages link to the lefthand side of the page.  

[http://glchess.sourceforge.net/?q=node/7&PHPSESSID=8938089b98e5f4800bd6145fb3f7e8cd](http://glchess.sourceforge.net/?q=node/7&PHPSESSID=8938089b98e5f4800bd6145fb3f7e8cd)

Now, you have to follow the steps (in two sections - top and middle of the page) to download and install the packages for the program as well as the 3D texture stuff.  Click on the two links "glchess package" and "PyGtkGlExe" will actually down two packages.  Make sure you know where they are and use the command "dpkg -i xxx*.deb" as stated in this page to install these two packages.

"sudo apt-get install xxx-xxx-xxx" is a command line interface that performs the same functionality as synaptic offers.  Each "sudo apt-get install xxx-xxx" is similar to the combination of "download and run dpkg -i", except that apt-get will take care of dependency for you, a huge huge plus.

So, if your download (after you click) is offering you to run some sort of packaging program for you, you can simply use it and forget about running dpkg again.

Or, do exactly as this page says.

Finally, glchess is showing it's glorious 3D on my computer.  However, it does not work quite well for my XGL session with beryl running, when glchess is at fullscreen.

Have fun poking around.  At least I did.  Don't ask me why it was not taken care of before 7.04 is released.  Maybe you found a bug.


Vincent

---

