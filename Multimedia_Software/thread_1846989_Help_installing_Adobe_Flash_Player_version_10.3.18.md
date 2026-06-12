---
title: "Help installing Adobe Flash Player version 10.3.183.710.3 or other"
date: 2011-09-20
forum: Multimedia Software
---

### Post by photosyn on 2011-09-20
I am a novice with Linux and am having trouble viewing some flash player videos that require Flash Player 10.3.  Although I am able to view most Adobe Flash Player video clips, I have recently gotten an error message for some (new ones, I suppose) saying that I need to load a newer version of Flash Player.  

I am currently using Ubuntu 10.04 (64 bit) and Mozilla Version 3.6.3 "Firefox for Ubuntu canonical 1.0".  My current version of Flash Player is LNX 10,0,45,2.  

I have tried FlashAid and it doesn't seem to help, although I might have made a mistake with it.  I also see that I could download Flash Player 11 at the following web site

[http://labs.adobe.com/technologies/flashplatformruntimes/flashplayer11/](http://labs.adobe.com/technologies/flashplatformruntimes/flashplayer11/)

however I do not know how to deal with the tar.gz file and am also not certain if those who know better that me would recommend this solution.

I am happy to upgrade Mozilla if it would help (I have been sticking with the version supplied by Ubuntu 10.04) or use another player, rather than Flash, if something would work.  

Thanks in advance for any help you can provide.  I have been using the Forum for several years and have always been able to find solutions through searching existing threads but this is the first time I've been stumped to the point of having to post a thread myself.

---

### Post by mikewhatever on 2011-09-20
You should run the Update Manager and apply the available updates. That should bring the Firefox version up to 3.6.22 and flash to whatever is the latest.

---

### Post by garvinrick4 on 2011-09-20
Open firefox window.
Go to tools and then to addons and type flash aid in search select to install.
Now in upper right will be a little red circle with a F in the middle click on it and 
will be three choices take one of the first two and follow easy instrutions.
It will remove all things flash and install the new versions and tweak for you and also keep you updated.
Has Solved the flash woes of many a user. Will reside under extensions in firefox. Enjoy.

---

### Post by garvinrick4 on 2011-09-20
@photosyn
> Thanks in advance for any help you can provide.  I have been using the  Forum for several years and have always been able to find solutions  through searching existing threads but this is the first time I've been  stumped to the point of having to post a thread myself.You know post 2 or 3 not just the one I gave you works, the Ubuntu repo's keep flash up to date as would
be expected. It looked like I wrote a post where mine was only way its not,  repo's also have 64 bit 11  in oneiric iincluded. 
If you have a mad desire to remove all things flash and install from tarball I will give you code, just say so and I will write it out for you.

---

### Post by photosyn on 2011-09-20
> **garvinrick4 said:**
> @photosyn

If you have a mad desire to remove all things flash and install from tarball I will give you code, just say so and I will write it out for you.

Not a mad desire, although learning to install from tarball would be educational for me.  I have FlashAid installed and it works for all Flash previous to 10.3.  Perhaps I do need to delete all things flash and re-install FlashAid.  Is there an easy way to do that?  (or would you suggest a tarball install for Flash)

Also, according to system manager I do have my system "up to date", despite the older version of Mozilla.  Would you suggest upgrading that?  I'm not sure how to do that either since Ubuntu includes it as a package.

Thanks for your patience with me.

---

### Post by garvinrick4 on 2011-09-20
> Thanks for your patience with me.You do not worry about that at all. I want you to learn Ubuntu and be a member of these Forums, Ubuntu is a passion of mine.

If it were my install I would go to this ppa site and install so as to get last stable version
of Firefox. It is a big difference in my opinion. It tells you the 3 lines to install in terminal.
```
sudo add-apt-repository ppa:mozillateam/firefox-stable 
``` ```
sudo apt-get update
``` ```
sudo apt-get install firefox
```[http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_stable?dist=lucid](http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_stable?dist=lucid)

> Perhaps I do need to delete all things flash and re-install FlashAid.   Is there an easy way to do that?  (or would you suggest a tarball  install for Flash)#Flash aid did remove all things flash and install a new version so do not worry about
that. Everytime you run the script (click on upper right red box with F in it and run.)
If flash is now working you are cool there.

---

### Post by garvinrick4 on 2011-09-20
> Not a mad desire, although learning to install from tarball would be educational for me.
Flash is just extracting the tarball and placing the
libflashplayer.so in /usr/lib/mozilla/plugins:
Remove all things Flash: Run each of these one at a time [COLOR=Red]with no Firefox running.[/COLOR]
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
Download your flashplayer and put on Desktop
cd Desktop
ls
tar zxvf (your flashplayer downloaded copy and paste it)
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
Done
[COLOR=Red]But you see Lovinglinux's flash aid does all this and more for you. (this is basically obsolete but just for your info)
[/COLOR]

---

### Post by garvinrick4 on 2011-09-20
> Not a mad desire, although learning to install from tarball would be educational for me.
Here is some tarball basic instructions (for your information)
# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

 [COLOR=Red]   ./configure[/COLOR] will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
    [COLOR=Red]make[/COLOR] will compile all the source files into executable binaries.
    Finally, [COLOR=Red]make install[/COLOR] will install the binaries and any supporting files into the appropriate locations.

# 3: Read INSTALL / README files for any additional instructions if needed.

---

### Post by photosyn on 2011-09-21
> **garvinrick4 said:**
> You do not worry about that at all. I want you to learn Ubuntu and be a member of these Forums, Ubuntu is a passion of mine.

You are very kind.  I also love Ubuntu and am determined to learn about it and pass it on.


> **garvinrick4 said:**
> 

#Flash aid did remove all things flash and install a new version so do not worry about
that. Everytime you run the script (click on upper right red box with F in it and run.)
If flash is now working you are cool there.

You've given me the CLUE and my problem is SOLVED.  You said that every time I ran the Flash script it should uninstall previous Flash and install new.  It seemed like it wasn't doing that and I finally noticed that the terminal preference was blank.  Don't know how that happened because it USED to work... Maybe I accidentally shut it off at some point.  but when I chose the path (which was easy -- it was a "down arrow" so I didn't have to think) Flash ran its script and now all Flash works.  I feel dumb for not seeing that before.  Thanks so very much. :D

---

### Post by photosyn on 2011-09-21
> **garvinrick4 said:**
> 

[COLOR=Red]But you see Lovinglinux's flash aid does all this and more for you. (this is basically obsolete but just for your info)
[/COLOR]

Yes, I see that and now I understand better what Lovinglinux's flash aid does.  Its great that you spelled it out for me so I can see how the script works and how I could actually do it myself too!  Very good.  I appreciate the info.

---

### Post by photosyn on 2011-09-21
> **garvinrick4 said:**
> Here is some tarball basic instructions (for your information)

Now perhaps it has become a mad desire because I think I can actually do it.  I will try it tomorrow when I am more awake and let you know how it goes.  

Can't tell you how nice it is to have help.

---

### Post by garvinrick4 on 2011-09-21
> Now perhaps it has become a mad desire because I think I can actually do  it.  I will try it tomorrow when I am more awake and let you know how  it goes.  
 Had to happen if not now sooner or later, enjoy.
> Can't tell you how nice it is to have help.
It was my pleasure, if you will go up to Thread Tools in upper right and mark as Solved.
So others with same can benefit.

I will keep this thread as subscribed for a week or so if you make anymore posts I will get it.

---

### Post by photosyn on 2011-09-22
garvinrick4
Just wanted to let you know that I successfully upgraded Mozilla Firefox and have been practicing tarballing.  Getting pretty good at it.  Thanks again for all of your help.  
photosyn

---

### Post by garvinrick4 on 2011-09-23
> **photosyn said:**
> garvinrick4
Just wanted to let you know that I successfully upgraded Mozilla Firefox and have been practicing tarballing.  Getting pretty good at it.  Thanks again for all of your help.  
photosyn It was my pleasure, enjoy your Ubuntu and I will see you around these Forums.
Tarballing sounds like something that was done at the Woodstock Pop festival in 1969!!!

---

