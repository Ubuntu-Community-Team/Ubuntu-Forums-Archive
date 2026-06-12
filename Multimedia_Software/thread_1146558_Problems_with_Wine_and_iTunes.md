---
title: "Problems with Wine and iTunes"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Lakeside5 on 2009-05-02
I finally got an iPod, and  don't know much about them. I just know that I'm having a lot of trouble using Wine to  install iTunes, so put stuff on my iPod.  I downloaded two different versions of iTunes (8 and 7.20 and could not intall either. I think the problem is with Wine. Should I/how do I:  uninstall and and re-install Wine, and then  use it to install iTunes. Unless you have other suggestions. Whatever works, I would just like to be able to use my iPod, but people tell me iTunes is the best. thanks Also, after that, I guess I need Cross Over to actually run iTunes?

---

### Post by 7as3r on 2009-05-02
Hi Lakeside,

As far as I know iTunes does not work with Wine. Not sure about CrossOver, but looking at their web site it doesn't seem like it will work with that either... unless someone else knows better?

There are a few alternatives which can communicate with your ipod, but I think you may be out of luck if you want to use iTunes for sure.

AmaroK and Banshee are a couple alternatives, and there's also this wikipedia page which has a list of programs and their features:

[http://en.wikipedia.org/wiki/Comparison_of_iPod_Managers#Linux]("http://en.wikipedia.org/wiki/Comparison_of_iPod_Managers#Linux")

---

### Post by Gramps on 2009-05-02
I think you need iTunes for W2K to get it to work with Wine

---

### Post by 7as3r on 2009-05-03
Hey! Would you look at that... I actually got iTunes to install! Thanks to a little bit of personal knowledge, Google, and WineHQ.

There are a couple issues (like not having any buttons...) but if you really need iTunes then it's up to you if this is an issue or not. I'm just amazed that it actually installed.

Edit: Although I installed iTunes 8.1, apparently iTunes 7.2 works better if you can find it (so you might actually have a play button, etc)

Here's what I did (although this might not work for you, but hopefully it will). I'm running Ubuntu 8.10.

Download latest wine source files.

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449")

(I downloaded version 1.1.20)

Extract the folder to the desktop (or somewhere easily accessible).

Open the folder you just extracted and go to: dlls > msi and open the action.c file in gedit.

On Line 973 you should see:

```
if (rc != ERROR_SUCCESS)
         ERR("Execution halted, action %s returned %i\n", debugstr_w(action), rc);
```

Add this *after* that block of code:

```
if( rc == 1603 )
        rc = ERROR_SUCCESS;
```

Save the file and close gedit.

Now the fun part... compilation :)

One step before compiling is installing some packages. These are the ones I had to install, but you may need to install more/less depending on what you already have:

flex
bison
libXxf86vm-dev
libhal-dev
libncurses5-dev
libsane-dev
libcapi20-dev
libcups2-dev
libldap2-dev
libgtkglext1-dev
libxslt1-dev

I just opened synaptics and did a search for each one and marked them, then clicked apply at the end to install them all. I'm sure there is an easier way, but whatever...

Open a terminal window and go to the extracted folder (cd /blah/whatever/) and then type in:

```
./configure
```

You may get an error if you are missing some packages... if so, install them and do ./configure again. Eventually you will see a bunch of code fly by as the code gets configured and setup to be installed.

After it's configured you may or may not see some messages at the end. I had a few warnings and had to go back and install some more packages before continuing. There were a couple (colour management or something and openssl which I couldn't find and just ignored...) Otherwise just follow what it tells you to do and type this into the terminal:

```
make depend && make
```

This is where the long, seemingly un-ending process of compiling wine starts... I would suggest going and doing something else for awhile because it can take some time (in my case it took over an hour).

After all that is done, type in:

```
sudo make install
```

Which will start installing wine. Now, I'm not sure if this is a bad thing or not, but I had an older version of wine on my system already which I did not uninstall. After I did the "make install" though it seems to have upgraded it properly so I'm not too worried.

After the installation, if you had an older version of wine you have to restart your computer because the old wine stuff is still running. After I rebooted everything was running properly.

Now, install iTunes! I installed the latest version (8.1.something)

Let me know if anything doesn't make sense.

Thanks

---

### Post by battleshipterry on 2009-05-06
Trying this on 2 pcs one lappy which had no buttons as you said but some what worked.and desktop pc is still running script, I will give feed back later.I wish I had a older copy on Itunes.

I am running Intrepid on Desktop pc
and Jackalope on lappy.:)

---

### Post by lvleph on 2009-05-06
Easiest way to install multiple programs.
```
sudo apt-get install flex bison libXxf86vm-dev libhal-dev libncurses5-dev libsane-dev libcapi20-dev libcups2-dev libldap2-dev libgtkglext1-dev libxslt1-dev
```

Oh and here is the old iTunes.
```
http://www.oldapps.com/itunes.php
```

---

### Post by lvleph on 2009-05-06
I used the current version of wine in the ppa and installed iTunes 7.3 Win2K version and it seems to have worked perfectly.

---

### Post by discostoo on 2009-05-06
If you just want to use your iPod, don't go through the trouble of getting iTunes to work in Wine.  That's way to difficult of a solution to an easy problem.  Just plug the iPod in, and it should show up on your desktop.  I know for sure that both Rhythmbox (the default Ubuntu media player) and Banshee have no problems recognizing and accessing iPods.

---

### Post by battleshipterry on 2009-05-07
Cant download apps from Itunes and no games for Ipod/itouch, so not much more then a mp3 playery if U use Rhythmbox.so why pay 200 dollars for MP3 player just to use Rhythmbox.My point is, its the content Itunes has that drives us to use Itunes software.

---

### Post by discostoo on 2009-05-07
That's cool, I was just referring to the original poster, who said he just wants to use his iPod.  I assumed he meant use it as an MP3 player, which is what it is.  But it's true... I don't think the touch is supported by Banshee, though I'm not sure about Rhythmbox.  I just have a regular non-touch iPod, and I only use it to listen to music... Banshee/Rhythmbox both work great for that.

---

### Post by battleshipterry on 2009-05-07
I was able to get Itunes 7.3 to run with buttons and search window and it will do a search.I had to install Crossover to to get it to work.current version of Wine with 7.3 did not work,would only crash on loading.So after installing crossover both the game version and the regular version it worked.still Itunes is slow to respond to any mouse click,also will not see ether Itouch or 3rd gen Ipod,and pops up errors that say to reinstall Itunes that software that is for recognizing ipods is not installed.I was assuming that it just runs several programs like Bonjour,Quicktime,Apple updater and Ipod recognizing software,and all that causes problems in Linux.
This is mostly why I use linux to get rid of all the Bloat software that runs continuously and slows Windows down. so all in all it is best to follow Discostoo :) advice and use Banshee or Rhythmbox because I don't want Itunes running all that stuff and slowing down Linux.

---

