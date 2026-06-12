---
title: "Guitar Tuner and webcam mic"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by Lothas on 2007-11-17
I'm having quite a lot of trouble trying to tune my guitar under Linux...

I tried installing gtkGuitune but apparently it doesn't work with my webcam built-in microphone so the program basically doesn't show anything.

Then I gave DGuitar a shot but it doesn't open. I tried running it from the console and this is what I got:
```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at dguitar.gui.DGuitar.<init>(DGuitar.java:756)
   at dguitar.gui.DGuitar.main(DGuitar.java:595)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...6 more

```

So I decided to try and install GuiTuner but the deb package won't install cause it says that I'm missing one of the dependancies, libx6g or something.

I also tried GTune but when running ./runme I got this:
```
make: *** No targets specified and no makefile found.  Stop.
cp: cannot stat `gtune': No such file or directory
cp: cannot stat `gtune_console': No such file or directory
cd: 5: can't cd to help
cp: cannot stat `gtune': No such file or directory
lothas@Lothas:~$ cd gtune-0.10/
lothas@Lothas:~/gtune-0.10$ ./runme
gcc -O2 -Wall `gnome-config --cflags glib gnome gnomeui gnorba gtk`   -c -o gnome-main.o gnome-main.c
/bin/sh: gnome-config: not found
gnome-main.c:5:19: error: gnome.h: No such file or directory
In file included from gnome-main.c:10:
interface.h:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘die’
interface.h:6: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘save_yourself’
In file included from gnome-main.c:10:
interface.h:6:22: warning: no newline at end of file
gnome-main.c: In function ‘main’:
gnome-main.c:25: warning: implicit declaration of function ‘gnome_init’
gnome-main.c:29: warning: implicit declaration of function ‘gtk_main’
make: *** [gnome-main.o] Error 1
cp: cannot stat `gtune': No such file or directory
cp: cannot stat `gtune_console': No such file or directory
cp: cannot create regular file `/usr/share/gnome/help/gtune/C/index.html': Permission denied
cp: cannot create regular file `/usr/share/gnome/help/gtune/C/prefs.jpeg': Permission denied
cp: cannot create regular file `/usr/share/gnome/help/gtune/C/gtune.jpeg': Permission denied
cp: cannot create regular file `/usr/share/gnome/help/gtune/C/topic.dat': Permission denied

```
I tried "sudo ./runme" but that didn't work either. **Please help!!!**

P.S.: I know the microphone works cause I've used it with skype

---

### Post by seachnasaigh on 2007-11-17
Sounds like you've got a package dependency problem ... sounds like you're missing some java and GCC libraries that your software needs to run. Couple of quick suggestions:

make sure you have the universe and multiverse repositories enabled
check for dependencies with apt using 

```
sudo apt-get update
sudo apt-get install
```

That should resolve dependencies or at least tell you what's missing.

ckr

---

### Post by mdebusk on 2007-11-17
> **Lothas said:**
> I'm having quite a lot of trouble trying to tune my guitar under Linux...

This may not look like a serious response at first, but it is.

I use the [Korg CA-30](http://korg.com/gear/info.asp?a_prod_no=CA30&category_id=5) and am very satisfied with it. You can [get it from Musician's Friend](http://www.musiciansfriend.com/product/Korg-CA30-Chromatic-Tuner?sku=210527) for about twenty bucks and it'll go anywhere your guitar does... unlike your computer. (You wouldn't take a laptop into a biker bar to play a gig, would you?)

Note: I work neither for Korg nor for Musician's Friend.

---

### Post by bluepowder7 on 2007-11-17
+1 to using a separate tuner.  how accurate is the sound card's A/D that the mic is hooked up to, anyways?  if it's just a plain mic input, is it even gonna be sampling at a high enough rate to give you a good resolution?

i use a Boss TU-80, which has a metronome built in as well.  and i have a standard Korg analog needle tuner.  cheap-n-cheerful!  oh, and i sometimes use a regular tuning fork, which i think cost me less than $10.

---

### Post by seachnasaigh on 2007-11-17
Yeah, well. I was trying to solve his computer problem, not his guitar problem ;)

Personally I use an intellitune for my 12-string and a Sabine on the body of my 6.
However, we have been known to take an older lappie with a firewire card into bars on gigs for doing recording and occasionally as an external fx machine (not too much time with that yet, however!)

ckr

---

### Post by Lothas on 2007-11-17
Ok, got it, I should buy one of those... I might even do it but so far, I've tuned my guitar under windows and it puts out a nice sound.

So... I tried updating but that didn't help with GuiTuner. It's still having dependencies problems :(

---

### Post by seachnasaigh on 2007-11-17
In that case you're probably going to have to take the more painful approach of reading the output of the errors and seeing what packages are missing, then going back into either Synaptic or apt-get and installing those packages, then repeat until you don't get package errors.

Did you install this GuiTuner through apt-get or did you use dpkg? My suspicion from your post is the latter, but even if the former I suspect it's a multiverse package and you're going to have to do it one step at a time. I'd start with GCC and java and go from there.

ckr

---

### Post by Lothas on 2007-11-18
What's the package name for guitune???
I'll take a look at the errors you mention but I'm not sure if I have seen any. Should I look after the first command or after the second (update)?

---

### Post by seachnasaigh on 2007-11-18
You should look for any errors on the apt-get thing after the update.

I'm not certain what the package name for that software is; if I've given you the impression that I've ever installed it, I apologise ... I don't use that software, and any suggestions here relate to installing packages under Ubuntu in general.

That said ...

Any software installation you try to do will have to be prepended with **sudo**; otherwise you're attempting an install with restricted privileges, and the installation will fail.

I have to say that the errors you reported for the GTune package look like the package itself might be an rpm (designed for a Fedora or RedHat system for example) though I'm not certain of that. Make sure that if you're installing something, it's dpkg and designed for a Debian-based flavour of Linux. Honestly, just a guess there as I didn't see the rest of your errors.

This bit here from your dguitar install ...

> Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at dguitar.gui.DGuitar.<init>(DGuitar.java:756)
   at dguitar.gui.DGuitar.main(DGuitar.java:595)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...6 more

... suggests one of two things. Either you were running the install with restricted privs, or you're missing some of the libgc packages or java packages or both. libgc is the gnu compiler library; the .so means "shared object", or a piece of code that several programs use. I don't think Ubuntu ships with all of the gnu compiler for the C programming language installed, and it looks from your snippet that this program attempts to use parts of that. 

This bit here from your Gtune install ...

> lothas@Lothas:~$ cd gtune-0.10/
lothas@Lothas:~/gtune-0.10$ ./runme
***
cp: cannot create regular file `/usr/share/gnome/help/gtune/C/index.html': Permission denied
cp: cannot create regular file `/usr/share/gnome/help/gtune/C/prefs.jpeg': Permission denied
cp: cannot create regular file `/usr/share/gnome/help/gtune/C/gtune.jpeg': Permission denied
cp: cannot create regular file `/usr/share/gnome/help/gtune/C/topic.dat': Permission denied

... is an example of doing an install without prepending "sudo" and running with restricted privs.

I see that you tried the sudo ./runme but that also didn't work, which suggests (again) missing dependent packages. 

If the software you're installing isn't in the universe or multiverse repositories for Ubuntu, and you're instead getting it from (for example) the manufacturer's website or one for guitar enthusiasts, then you're going to need to go back there and read up on what the software is dependent upon and make sure that your system has those installed, at a minimum. apt-get and synaptics both leverage the underlying Debian dpkg system of installation for software; some other Linux flavours (mandriva, fedora) use a system of commands like "./configure; make; make-install" directly and if the software installer assumes rpm (redhat package management) rather than dpkg, the installation will likely fail on an Ubuntu system. You can invoke dpkg directly without using apt-get or synaptics, though it is not for the faint of heart and requires some research to get right. 

Here is a pretty good tutorial:
[http://www.debuntu.org/2006/06/06/57-how-to-dpkg-guide](http://www.debuntu.org/2006/06/06/57-how-to-dpkg-guide)
Here's another:
[http://www.debianadmin.com/debianubuntu-package-management-using-dpkg.html](http://www.debianadmin.com/debianubuntu-package-management-using-dpkg.html)
And finally here's a good tutorial on using apt-get (which I recommend):
[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

Good luck!

ckr

---

### Post by Lothas on 2007-11-19
Ok.... So I gave a shot to checking for errors during the update. So far, after the first command, no errors (just Get, Hit and Ign commands).

Now I'll try sudo apt-get install:
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 gnash-common

That's the only "error" I get.

Regarding GuiTuner, I tried installing both the .rpm and .deb package (starting with the .deb): [http://digilander.libero.it/guituner/downloads.html](http://digilander.libero.it/guituner/downloads.html)
I tried contacting the developer but the e-mail link seems to be broken.

I guess I'll have to try something else or get a windoze emulator...

---

### Post by Lothas on 2007-11-20
I finally made it!!! I managed to install FMIT (Free Music Instrument Tuner) and after playing with it for a while and taking some cues from my skype config, I managed to make it work. Now if only I knew how to tune my guitar with it... it's a pretty powerful tool!

---

### Post by seachnasaigh on 2007-11-20
Congrats!

Now if you could do two quick things ... 
[LIST=1]
[*]Drop a quick post telling *how *you did it and
[*]Mark this post as solved
[/LIST]
That will help others in future who might have the same problem.

ckr

---

### Post by Lothas on 2007-11-20
This is what I did to configure FMIT:

I looked under skype options to see the configuration for video devices. There I saw that the input was hw:Camera,0. I copied that to FMIT's settings and I starting receiving input from the built-in microphone.

Now my guitar is tuned!

---

