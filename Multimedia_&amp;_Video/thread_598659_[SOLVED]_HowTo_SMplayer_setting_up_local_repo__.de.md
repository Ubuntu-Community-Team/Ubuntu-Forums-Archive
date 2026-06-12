---
title: "[SOLVED] HowTo SMplayer: setting up local repo / .deb for latest version"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by perixx on 2007-10-31
Hi there!


It's very common to happen that the official Ubuntu repositories have pretty outdated versions in store, lacking a lot of features. Thus, I decided to install the newest version of SMplayer directly from there:

> [http://smplayer.sourceforge.net/en/linux/download.php](http://smplayer.sourceforge.net/en/linux/download.php)
 
Unfortunately, installing downloaded .deb packages with Synaptic turned out to be a little more complicated as described here:

> [http://ubuntuforums.org/showthread.php?t=323431](http://ubuntuforums.org/showthread.php?t=323431)

The main reason is that Synaptic searches for the downloaded .deb packages - let's call it 'local repository' here - in a different path than the one I specified in Synaptic's Repository Manager. That's why I'm trying to give my solution to others here - I'm not pro, so please forgive any foolish stuff I write here - feel free to fix me up ;-] 


What to do:


1) download the Debian/Ubuntu package, e.g. 'smplayer_0.5.21_i386.deb'


2) create your local .deb repository folder, e.g /home/USER/downloads/dists/debian/main/binary-i386
-->_Always replace 'USER' with your user-account's name, please!_

**Important:** Synaptic will search for your downloaded .deb packages in a folder respectively to the local repository you specified in the 'Repository Manager' -->

Applications > System > Repositories > [Tab] 3rd party software > Add > Enter apt-line
```
deb file:/home/USER/downloads/ debian main
```

Make sure that your newly set up repository under '3rd party software' is checkmarked.

The 'Repository Manager' will insert 'dists' and 'binary-i386' folders to his searching path, looking for the files in:
```
/home/USER/downloads/dists/debian/main/binary-i386
```


3) copy your .deb package(s) into this directory


4) open a Terminal and enter: 
```
dpkg-scanpackages /home/USER/downloads/dists/debian/main/binary-i386/ /dev/null | gzip > /home/USER/downloads/dists/debian/main/binary-i386/Packages.gz
```

This will create the 'Packages.gz' file, listing the SMplayer- and all other .deb files for Synaptic.
**Note:** If you get an error, that dpkg-scanpackages isn't availible, do ```
sudo apt-get install dpkg-dev
``` in the Terminal first, to install the necessary utility.

--> I couldn't figure out how to circumvent this step from within Synaptic, so I'd be glad to know how ;]


5) Do a 'Reload' in Synaptic - if you get no error messages regarding wrong paths for your repo, then everything should be ok. 

You should now find your newly added local repo content in the '**local main**' category and be able to mark SMplayer and the Themes for installation. Accept and do 'Apply' > accept again. There will be possibly some other dependent packages downloaded, but these are gathered from the official repositories.


**If not**, there will be a message showing the expected path where Synaptic looks for the local repository - make sure, it matches yours. If Synaptic will crash instead, enter 
```
sudo mousepad /etc/apt/sources.list
```
and put a '#' in front of the line with your local repository-path under the '3rd party section', in order to switch it off. 

You also can edit away here or re-edit your local repo in your 'Repository Manager'. Doublecheck all your paths for the correct locations and Upper/lower-case spelling.

**Important note:** It's possible that you add new .deb packages to your local repositories folder later, of course; just make sure that you redo Step 4) after each new added .deb file and 'Reload' in Synaptic in order to access it. 
Sometimes it may occur that it doesn't seem to work - try to check/uncheck your local repo under Options > Repositories > [Tab] 3rd party software > Close and do 'Reload' again.  


Maybe the pure CLI-method here also works for you and is also faster, so you might try this one instead:
> [http://ubuntuforums.org/showthread.php?t=62943](http://ubuntuforums.org/showthread.php?t=62943)

Good luck!


perixx

---

### Post by disturbedite on 2007-10-31
> **perixx said:**
> 
Unfortunately, installing downloaded .deb packages with Synaptic turned out to be a little more complicated as described here:
bah, who said anyone *had* to use synaptic (or adept for that matter) to install a deb package?
i install packages manually/locally all the time:
sudo dpkg -i /path/to/package.deb

but making locally installed packages install in the "correct" section would be useful.

---

### Post by perixx on 2007-10-31
Hello disturbedite...


> i install packages manually/locally all the time:
sudo dpkg -i /path/to/package.deb

I suppose you mean the same as this:
> Maybe the pure CLI-method here also works for you and is also faster, so you might try this one instead:

[http://ubuntuforums.org/showthread.php?t=62943](http://ubuntuforums.org/showthread.php?t=62943)


I don't know exactly what you want to say with this... perhaps you can explain?
> but making locally installed packages install in the "correct" section would be useful.


Anyway, I've read that the apt-get method is not as reliable as Synaptic when it comes to de-installing applications due to dependency problems and also in some other cases. Apart from that - I suppose it's not a bad idea at all to provide a visually appealing approach for these tasks to Linux-newbies - what's the point in having a package manager that's only half-functional; if adding repos from internet locations works fine, why not make additional local repos work smoothly?


perixx

---

### Post by srt4play on 2007-10-31
I think that's too much of a hassle and overkill for installing a single package. 

Why not just double-click the thing and install it with gdebi?

---

### Post by disturbedite on 2007-11-01
i hate gdebi, its slow as hell.

---

### Post by perixx on 2007-11-01
Well, I've gdebi installed but never tried it up to now...
I try hard to improve my skills and get beyond GUI-surfing only, but for most newcomers it's simply too much of a hassle to use the CLI method (apart from the fact that they've got to find out first, THAT and WHAT they have to type in. Visual tools are simply much easier to approach.

A newbie (like me) couldn't figure how to find out what's in store in the repos via Terminal commands [I know that you know ;]  -  but it wouldn't make too much sense also, to roam endless listings without descriptions. And from what I've heard, one can seriously mess things up when mixing GUI and CLI installation methods.

Speaking of GUI's - I don't know why the 'Add/Remove Manager' always shows different results regarding installed apps than Synaptic, btw...

Anyway - IF there is a good packet-managing application like Synaptic availible I can't see a reason why there isn't a simple solution provided for GUI-guys to adapt local repositories (correctly).... apart from whatever you personally like more.


perixx

---

### Post by disturbedite on 2007-11-01
> **perixx said:**
> Speaking of GUI's - I don't know why the 'Add/Remove Manager' always shows different results regarding installed apps than Synaptic, btw...
i never use that, i always use synaptic and i'm on kubuntu.  its kicks adept's butt.  but i've never seen any discrepancy between "Add/Remove Manager" and synaptic.

[quote=perixx]Anyway - IF there is a good packet-managing application like Synaptic availible I can't see a reason why there isn't a simple solution provided for GUI-guys to adapt local repositories (correctly).... apart from whatever you personally like more.[/quote]
i concur.

---

### Post by perixx on 2007-11-02
Hi disturbedite...


As you know, I've managed to install the latest .deb package of SMplayer (and some others) the way I described it. Regardless to the fact that I put other .deb packages into the same folder - as described - (and repeat the procedure) those app-packages are being placed into a different source category in Synaptic, at will it seems:

pcmanfm into archive.ubuntu.com/universe, gnome-commander into local/universe, xorg-edit and smplayer+themes into local/main.

Any idea how to change this behaviour?
What do you think, where should I these annoyances address to? :confused:

I also tried to use the latest gnome-commander debian package, but when I try to install it, a dependency problem occurs in Synaptic - telling me there's a conflict with another application and that it must be removed first (maybe Thunar?) - I'd bet it would also happen with apt-get.
PCManFM installed nicely. 

I've read that debian packages aren't always conform to Ubuntu and perhaps that's the case here..? If I had a clue on how to compile things myself... :(


Another question: would apt-get warn me if there are dependency problems before installing anything? If so, how do I assign a local .deb package to it?


perixx

---

### Post by perixx on 2007-11-07
Manually adding local repos with Synaptic turned out to be unusable to me - unpredictable results regarding where in the packet-categories the newly added packages will show up. 

Also its really too much trouble, so I d rather recommend using  the CLI method (I will next time) instead of mine, till Synaptic is bein fixed up! I wouldn t categorize this issue a bug (or maybe I should?) but unfinished application design...


perixx

---

### Post by perixx on 2007-12-08
Maybe there's no need to compile SMplayer for oneself -- 
.deb packages from the homepage work well on my Xubuntu system!

[http://smplayer.sourceforge.net/downloads.php?tr_lang=en&PHPSESSID=f943a2e357e2da47ee99809e924d6900]("http://smplayer.sourceforge.net/downloads.php?tr_lang=en&PHPSESSID=f943a2e357e2da47ee99809e924d6900")

perixx

---

