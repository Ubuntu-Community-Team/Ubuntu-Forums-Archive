---
title: "Flashplayer plays but cant Interact"
date: 2010-02-18
forum: Multimedia Software
---

### Post by HunterAnderson on 2010-02-18
Hey. umm question. Flashplayer, what is the matter with it if you try to use some flash oriented object such as youtube video players or some flash game and it comes on however you cant click anything. For example on youtube I can open a video and because its set to autoplay it will start and play however I cant set volume, pause, enlarge or anything. Its the same with all other objects as such. I've tried reinstallation  but it wouldnt work. Any suggestions? Thanks for any help or ideas.](*,)

---

### Post by RedSingularity on 2010-02-18
Have you tried removing flash player and purging all its settings then reinstalling?

---

### Post by HunterAnderson on 2010-02-18
Took a couple tries before I got the commands right but I got it purged and installed but no luck.

---

### Post by HunterAnderson on 2010-02-18
another thing I hadn't really noticed before but may help. It will detect my mouse being over a button or such but it wont let me select or change anything.

---

### Post by bhj6268 on 2010-02-18
I'm having the exact same issue!  Have you found a solution yet?  If so please help!

---

### Post by HunterAnderson on 2010-02-18
no. no solution yet but you may want to try what RedSingularity said. The code should be as follows

> sudo apt-get purge flashplugin-installer

and then to reinstall it

> sudo apt-get install flashplugin-installer

you may not need the code but just in case you or someone else does. This didnt fix mine but you may have some luck with it.

---

### Post by lovinglinux on 2010-02-19
For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by Villiam on 2010-02-19
I have seen this problem at one of my office colleagues laptop. Setting his screen resolution to a higher level solved the issue. May be it will work at your end too.

---

### Post by HunterAnderson on 2010-02-19
Thanks for the ideas I tried to install the other flash plugin and installation worked great but didn't fix the problem. I also tried different resolutions but still no go.:icon_frown:

---

### Post by RedSingularity on 2010-02-19
Did you have it working at one point in the past?

---

### Post by HunterAnderson on 2010-02-20
it was working at one point but i cant think of anything thats happened or got changed between now and then

---

### Post by RedSingularity on 2010-02-20
Ok then try this, 

sudo apt-get autoremove --purge flashplugin-installer

Then delete the following file, (Show hidden files by pressing Ctl-H)

/home/you/.macromedia

Then reinstall flash player with 

sudo apt-get install flashplugin-installer

---

### Post by bhj6268 on 2010-02-20
> **lovinglinux said:**
> For 32bit see [this]("http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2").

For 64bit see [this]("http://ubuntuforums.org/showthread.php?t=1358591").


Thanks It worked like a charm.  

1st I used this command:  sudo apt-get purge flashplugin-installer

Then I saved the 64 bit and ran it in the terminal.  Then I restarted and boom it worked instantly.

Again thanks

---

### Post by sweltman on 2010-02-20
**LovingLinux--Spot on!** :D

This is my first foray into Ubuntu Linux although I have played with Mandriva for years.  I really like this distro.  Its solid and works very well for everything that I am trying to accomplish except book keeping (but i am still searching for a good open source tool even if it's at cost).  

In regards to the flash issues, I had no flash after the update.  Totem was in the way.  The only thing that I needed to do (in addition to the script (flash_remove.sh) was run the Get64BitFlash script.  I had one other little gotcha.  I somehow didn't get rid of the 9.999 Flash plugin which was broken (and was the 32 bit version anyhow).  The add-ins on the browser should probably be unselected (or told not to load) before performing these 2 scripts.  

You guys ROCK!!  Great support for this.  Thank you and I hope to contribute soon.

Steve Weltman
Absolute Networks & Sales

---

### Post by norcalltd on 2010-02-22
I'm having the same issue.  The option I'm trying to click (Play in this instance) changes color to indicate I am mousing over it, and after frantic clicking I am able to get the button I'm trying to click to work.  More often nothing happens and I simply quit.  I've purged then reinstalled Flash 10, changed resolutions and neither of these options work. Is anyone using one of the open source players having this issue?

---

### Post by HunterAnderson on 2010-02-22
im not sure what happened to mine but it just decided to start workin all the sudden. i hadent changed anything but for some reason its workin now. I dont know what happened but maybe yall(other people havin the problem) can find some way to get it to work. Ill try to figure out what happened to mine.

---

