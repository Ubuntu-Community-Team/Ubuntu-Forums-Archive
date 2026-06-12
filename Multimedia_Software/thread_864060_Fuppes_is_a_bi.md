---
title: "Fuppes is a bi***"
date: 2008-07-19
forum: Multimedia Software
---

### Post by jcr1 on 2008-07-19
Can't install it. What's wrong with the bloody thing?

Been following these instructions :[http://ubuntuforums.org/showthread.php?t=597650](http://ubuntuforums.org/showthread.php?t=597650)

I download all the gubbins needed, untar'd into a folder. go into that folder and:

run sudo ./configure...it does things.

run sudo make... it does a lot of things

run sudo make install ...it runs but i'm not sure its right:

then instructions say to run sudo .ldconfig but there is no such command? the folder i am in is fuppes-SVN-578m which is what the downloaded tar untar'd to. 

there is no .fuppes folder in my home folder.

so no .fuppes no .ldconfig

Whats going on!?!

---

### Post by houbysoft.xf.cz on 2008-07-19
What about sudo ./ldconfig?

---

### Post by jcr1 on 2008-07-19
Sorry that's just a typo. It just returns a command not found.

---

### Post by jcr1 on 2008-07-19
would this have anything to do with installing on Xubuntu?

---

### Post by houbysoft.xf.cz on 2008-07-19
and have you tried just sudo ldconfig?

---

### Post by jcr1 on 2008-07-19
sudo ldconfig doesn't do anything. No error, just doesn't seem to do anything.

The next instruction says to go edit ~/.fuppes/fuppes.cfg but I just do not have a .fuppes directory. Nor is it in the fuppes-SVN... folder created from the tar.

Just don't know what to do...

---

### Post by jcr1 on 2008-07-20
ok ran thru this several times with the same result...no errors occur, but no .fuppes directory is created, hence I cannot set up the fuppes.cfg file as it doesn't exist! 

Whats going wrong?

---

### Post by thomascrabs on 2008-07-22
The directory and config files in ~/.fuppes/ are only created when fuppes is run for the first time.

Try running 'sudo fuppes' from the command line and see what happens and if it creates the directory / files.

Try this page - it helped me:

[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Linux](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Linux)

If your running 8.04 it has some extra stuff.


ldconfig should be in directory '/usr/sbin/' check if it is there. If so run 'sudo /sbin/ldconfig', if not :confused:.

---

### Post by Kibz on 2008-08-02
If I'm right in assuming that FUPPES has been installed successfully (the make install portion), then what you need to do, according to the FUPPES Wiki is to run fuppes from the terminal.

If fuppes runs successfully, it will create the $HOME/.fuppes/ folder, as well as the fuppes.cfg file with its default settings. You may need to fiddle with these in order to get everything working to your liking, but at least you'll have the file there to start.

---

