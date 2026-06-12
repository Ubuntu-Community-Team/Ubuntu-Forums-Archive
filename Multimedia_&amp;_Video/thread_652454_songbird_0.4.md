---
title: "songbird 0.4"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by quest23 on 2007-12-28
im currently running songbird 0.3 and i want to upgrade to 0.4 but i cant figure out how to do it...

0.3 was a .deb so it was easy..this one is Songbird_0.4_linux-i686.tar.gz file...so its a little different...can someone who has installed it help me out...i know how to uninstall the old one..just dotn know how to install a tar file..

---

### Post by buntunub on 2007-12-28
Compile it from source. Untar it and then just cd to the unpacked directory and type ./configure, make, and sudo make install.

---

### Post by meho_r on 2007-12-28
I think there's no need for installation at all. Just extract and run "songbird" file

---

### Post by the_Ben on 2007-12-30
I'm stuck installing Songbird 0.4 as well.  I untar-ed it at /usr/lib/Songbird, and navigated to that directory in the terminal.  When I type in "./configure", I get the error "No such file or directory."  Any ideas?

---

### Post by Go_Bucks on 2007-12-30
I just downloaded the software and it's as meho_r said. There is nothing to install. Just double click on the "songbird" file and it will run.

---

### Post by the_Ben on 2007-12-30
Double clicking on songbird doesn't do anything, and typing it in the terminal yields "Command not found".  Do I need to move the folder to a different directory?  It's currently in /usr/lib.

---

### Post by dasunst3r on 2007-12-30
If you just download the binaries and extract them, you can just double-click on songbird to launch it.

---

### Post by tdrusk on 2007-12-30
extract the folder and then go into it.

Go to the songbird file, it's blue

double click it.

---

### Post by BigSilly on 2007-12-31
You silly beggars! You just have to double-click the "songbird" executable, but you have to give it the permission to execute first. 

First right click the executable as above, then select properties, then the permissions tab. See that box that says "execute - allow executing file as a program". Tick it, and then you're away. You can now double click to launch the program. It's a good little tip to remember for future reference.

---

### Post by Go_Bucks on 2007-12-31
Mine was already set as an executable. I didn't have to change permissions.

---

### Post by bharadwaj on 2007-12-31
Directly launch the programm, Add the entry to desktop applications and even to file management menu

---

### Post by the_Ben on 2008-01-01
Okay, I tried the old standby of delete and reinstall, and it works like a charm.  Not sure what the issue was before.  Thanks for the help as always, gotta love the ubuntu forums!  Oh, and happy new year everybody!  \\:D/

---

### Post by ben2talk on 2008-01-18
Ok, the installation from automatix lived inside the /opt/automatix/ folder. If you browse there with nautilus, you can't do anything - it's protected. So launch root shell - or type sudo su.

Now type nautilus. When it's open, find your songbird tar.gz file, and unzip it. You can delete the archive now. Next, cut the folder and paste it on top of your original Songbird folder.

Then I noticed the launcher spellings... they don't match the old installation /songbird/Songbird. I simply renamed the folder 'songbird' to 'Songbird' and then the file 'Songird' to 'songbird'.

Now click your lovely eggy icon, and watch it spring to life! Attention to detail people ;) watch out for capitalisation - I noticed this first when I tried to 'cd desktop' and it didn't work!

---

### Post by jipke on 2008-01-20
I also downloaded the latest version of Songbird and simply extracted it in /home. When I doubleclick on the Songbird file it launches perfectly.

For what I understand executables (that I run from terminal) are installed in /bin. Do I have to copy the songbird dir in /home to /bin if I want this for Songbird? Or is there another way (on the forum I've read something about softlinks).

---

### Post by berthiggins on 2008-01-20
Am I missing something here I just went to edit/check for updates /update and it did it automatically itself!:confused:

---

### Post by bharadwaj on 2008-01-20
Guides cant be simpler that this
[http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)

---

### Post by bharadwaj on 2008-01-20
> **quest23 said:**
> im currently running songbird 0.3 and i want to upgrade to 0.4 but i cant figure out how to do it...

0.3 was a .deb so it was easy..this one is Songbird_0.4_linux-i686.tar.gz file...so its a little different...can someone who has installed it help me out...i know how to uninstall the old one..just dotn know how to install a tar file..
[http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)

---

### Post by kevindubrow on 2008-02-15
Is there a guide similar to that for .4? Because I am still lost even after reading this post.

---

### Post by lbarnes on 2008-02-29
yeah, i can't get it to work either
i just want a launch icon
i've got songbird folder in /opt
but it still says no such file exists, or something
i would like it in my applications list
and i think i read that just running it from the folder
and not installing it limits the functionality

how about a script like the one for 0.3?

---

### Post by lbarnes on 2008-02-29
[http://ubuntuforums.org/showthread.php?t=659452]("http://ubuntuforums.org/showthread.php?t=659452")

i found this link, thanks sub2007
i don't know why you guys said you don't install it 
that just doesn't make any sense

---

