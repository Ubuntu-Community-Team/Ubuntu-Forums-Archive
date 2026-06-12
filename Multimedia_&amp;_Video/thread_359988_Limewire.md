---
title: "Limewire?"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by mikeaguilar1 on 2007-02-12
Hey fellas, Over the last couple of days ive made the switch to Linux. I am slowly figuring things out. I would like to know if there is Limewire for ubuntu?

If so where can i get it?

---

### Post by master.zen on 2007-02-12
limwire.com of course but how do you install :D

---

### Post by rsambuca on 2007-02-12
I would strongly recommend using Frostwire as an alternative.  It uses the same networks as Limewire.  Use Synaptic to install Java on your system first, and then go to frostwire.com and just download the installer for the ubuntu version.

---

### Post by master.zen on 2007-02-12
well i got frostwire how do i play mp3's though I've downloaded some songs but they wont play

EDIT: Got it

---

### Post by rsambuca on 2007-02-12
> **master.zen said:**
> well i got frostwire how do i play mp3's though I've downloaded some songs but they wont play

Instructions to install mp3 codecs:  [[COLOR="Red"]Link[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9")

---

### Post by mikeaguilar1 on 2007-02-12
> **rsambuca said:**
> I would strongly recommend using Frostwire as an alternative.  It uses the same networks as Limewire.  Use Synaptic to install Java on your system first, and then go to frostwire.com and just download the installer for the ubuntu version.

I took you up on that and download frostwire, BUT this java thing is alot harder. I went to synapatic to install java but there are so many java files :/. I installed most of em yet frostwire still does not work. What do i do?

---

### Post by mikeaguilar1 on 2007-02-12
> **mikeaguilar1 said:**
> I took you up on that and download frostwire, BUT this java thing is alot harder. I went to synapatic to install java but there are so many java files :/. I installed most of em yet frostwire still does not work. What do i do?

Bump

---

### Post by rsambuca on 2007-02-12
I can't remember the java stuff exactly.  I'll figure it out and post back here later.  For now, its dinner time and then I gotta put the kids to bed.  Check back later tonight!

---

### Post by rsambuca on 2007-02-12
Although this isn't how I did it the last time, I do remember now that I have used Automatix in the past.  It is a program that will automatically load a bunch of programs, codecs, drivers, etc. for your system using a Graphical interface.  Works quite well, although some command-line purists don't like it.  You just select what you want to install and it does everything for you.

If you like, just go to their website and follow the instructions.  [[COLOR="Red"]Automatix2[/COLOR]]("http://www.getautomatix.com/")

---

### Post by jammodotnet on 2007-02-13
> **rsambuca said:**
>  ... Automatix ... 

works like a charm!
:)

---

### Post by mikeaguilar1 on 2007-02-13
> **rsambuca said:**
> Although this isn't how I did it the last time, I do remember now that I have used Automatix in the past.  It is a program that will automatically load a bunch of programs, codecs, drivers, etc. for your system using a Graphical interface.  Works quite well, although some command-line purists don't like it.  You just select what you want to install and it does everything for you.

If you like, just go to their website and follow the instructions.  [[COLOR="Red"]Automatix2[/COLOR]]("http://www.getautomatix.com/")

I took your advice again and downloaded and installed Automatix. I instaleld sun java but still cannot get frostwire to run. I go to terminal and type "frostwire" and it still tells me that i need to upgrade to java 1.5 and to go to [www.java.com](www.java.com) . I am so lost. i am losing hope. Please help.

Ill pay pal you if you guys can help meo ut

---

### Post by rsambuca on 2007-02-13
Did you install Frostwire by itself first, or Java first?  I think you might want to uninstall frostwire via the same method you chose to install it.  ie if you used automatix to install, then use it to uninstall frostwire.

Then reinstall and see what happens.

---

### Post by kamaboko on 2007-02-18
there are two java downloads.  one is for firefox/mozz web apps that require java while the other is for stand-alone apps such as frostwire.  install the latter. i think the web app one is 1.5, while the stand-alone is 5.0.

---

### Post by Metallinut on 2007-02-18
I followed this post to install frostwire on my Edgy.  I already had JRE 1.5 on my machine, so I just went to frostwire.com, downloaded the .deb, and sudo dpkg -i'd it.

In my Applications menu, I have Frostwire listed, but no icon (don't know if there should be one or not.  Initial run ran me through the configuration wizard.  Once that was done, a window came up saying FrostWire (4.13.1 by the way), but there's nothing but a blank window.  

Any thoughts? - I'm on Gnome, using fglrx and an XGL session (shouldn't matter, but you never know).

Thanks,

---

### Post by rsambuca on 2007-02-18
Are you using Beryl?  If so, you either have to disable it or there is a small script on these threads somewhere (search for Frostwire and Beryl) that you have to run in order to get them to work at the same time.

---

### Post by Metallinut on 2007-02-18
Ah yes.  I had the same problem with googleearth.  If I just start it from a terminal, preceeded by DISPLAY=:0 it works.  Just can't resize or move the window, and it stays on top of all other windows.  Grr.  Oh well.  At least it's usable.

Thanks,

---

