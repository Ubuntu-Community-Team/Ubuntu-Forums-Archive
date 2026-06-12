---
title: "Why does this Ebay url crash my Firefox &amp; Opera??"
date: 2008-09-07
forum: Multimedia Software
---

### Post by Morty007 on 2008-09-07
The following url is a ebay page for someone selling laptops. Whenever I scroll down to where the description is my cpu usage goes sky high and causes Firefox to crash. In opera it doesn't crash but it does spike the cpu. 

I have adobe flash 10, the latest rc version. I believe it did it in version 9 also. Is it affecting you when you scroll down to the green sides?

Edit- I forgot to add that it does this in safe mode and when I disable that flash plugin. Crazy!

[http://cgi.ebay.com/NEW-DELL-INSPIRON-1525-LAPTOP-NOTEBOOK-2-2GHZ-WARRANTY_W0QQitemZ130251997263QQihZ003QQcategoryZ177QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/NEW-DELL-INSPIRON-1525-LAPTOP-NOTEBOOK-2-2GHZ-WARRANTY_W0QQitemZ130251997263QQihZ003QQcategoryZ177QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by Kronie on 2008-09-07
just went through the whole page without any freezes or crashes...

---

### Post by rzrgenesys187 on 2008-09-07
Hmm... No crashes for me.  My cpu usage did jump but no more than for any other web page

---

### Post by Morty007 on 2008-09-07
What flash versions are you guys running?

---

### Post by Morty007 on 2008-09-09
Bizarre, I just booted up a Mandriva live cd and checked the url from within the live cd, and I get the same high cpu usage.

---

### Post by wolfen69 on 2008-09-09
sounds like a firefox problem to me. i would completely remove it, then: ```
sudo apt-get clean
```then ```
sudo apt-get autoremove
```then reinstall firefox. it can't hurt.

---

### Post by Morty007 on 2008-09-10
I'll give that a try Wolfen and then post back, thanks!

Edit- I put firefox at the end of each line above right?

---

### Post by gandaran on 2008-09-10
what RAM and Swap does the computer have?

---

### Post by Morty007 on 2008-09-10
2 Gigs of ram, and it looks like a 5 Gig swap. I'm about to try the uninstall of firefox now.

---

### Post by Morty007 on 2008-09-10
I didn't remove it right. Can someone help?

marc@marc-desktop ~ $ sudo apt-get clean firefox
[sudo] password for marc: 
marc@marc-desktop ~ $ sudo apt-get autoremove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
The following packages were automatically installed and are no longer required:
  mplayer-skins libsvga1 mplayer libamrnb3 libamrwb3 libenca0 libggi2 libgif4
  libgii1 libgii1-target-x
The following packages will be REMOVED:
  libamrnb3 libamrwb3 libenca0 libggi2 libgif4 libgii1 libgii1-target-x
  libsvga1 mplayer mplayer-skins
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
After this operation, 13.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 116810 files and directories currently installed.)
Removing mplayer ...
Removing libamrnb3 ...
Removing libamrwb3 ...
Removing libenca0 ...
Removing libggi2 ...
Removing libgif4 ...
Removing libgii1 ...
Removing libgii1-target-x ...
Removing libsvga1 ...
Removing mplayer-skins ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
marc@marc-desktop ~ $ sudo apt-get clean firefox
marc@marc-desktop ~ $ sudo apt-get clean
marc@marc-desktop ~ $

---

### Post by Morty007 on 2008-09-10
Well I totally erased FF, reinstalled and went to that same url...and the same damn thing. :confused:

---

### Post by gandaran on 2008-09-11
> **Morty007 said:**
> Well I totally erased FF, reinstalled and went to that same url...and the same damn thing. :confused:

removing and installing again firefox won't fix the problem, you'll  still have the firefox configuration files with the addons in the hidden home folder,( you can try deleting the home .mozilla folder, backup first the folder).
I'm still inclined to believe it has something to do with hardware, drivers or if you running special effects/compiz or maybe the flash version installed.
I use flash 9 on opera, for firefox flash 10, I used to have some firefox crashes with flash 10, but since upgrading ram from 512 kbs to 1GB, I haven't had a single crash, this is not your case, your have more than enough RAM.   
do you have ubuntu 8.04/firefox updated?

---

### Post by Morty007 on 2008-09-11
Thanks for the reply Gandaran.

 I manually deleted those configuartion files (that was my windoze experience coming into play) and firefox is 3.0.1, the latest version. 

I'm actually using linux mint 5 and it is fully updated. I posted this on the mint forums and others there aren't having any issues with that url. It crashed so much last night I couldn't get anything done unless I used opera. I'm using flash 10 in opera and its smooth as can be.

I have not tried disabling compiz, so I will try that.

---

