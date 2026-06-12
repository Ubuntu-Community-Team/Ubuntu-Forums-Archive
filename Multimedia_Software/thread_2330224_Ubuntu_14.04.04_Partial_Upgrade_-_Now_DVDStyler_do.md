---
title: "Ubuntu 14.04.04 Partial Upgrade - Now DVDStyler doesn't work."
date: 2016-07-09
forum: Multimedia Software
---

### Post by 77_GCSX on 2016-07-09
1st the PC = Ubuntu 14.04.04 Kernel 3.13.0.61 64 bit.

I've been using Ubuntu AND DVDStyler for quite some time now with no issues. Just a few days ago the Software Updater told me about a "Partial Upgrade". Afterwards DVDStyler stpped working with the following error when I tried to generate the ISO file:
[IMG]https://goo.gl/photos/TASEYmUwr2F1yXaF9[/IMG]

Sorry for my fumbling here but I cannot seem to insert an image so I'm attaching one of the error.

Thanks for any help on this!!

---

### Post by jmgangemi on 2016-07-10
How did you install DVDStyler?

Did you install it from the Ubuntu repository or directly from the developer?

If you installed it via the Ubuntu repository, remove the program and install it again using the following commands at the terminal 
(Press <CTRL>+<ALT>+<T> on your keyboard to bring up a terminal window).

sudo apt-get purge dvdstyler

apt will ask you if you want to remove the package press Y and ENTER.

after the program and its other components have been purged, reboot the computer.

You can do this at the terminal by typing the following and pressing ENTER

sudo reboot

After your computer has restarted, login again and open a terminal window by pressing 
<CTRL>+<ALT>+<T>

To install dvdstyler that is in the Ubuntu repositories type the following:

sudo apt-get update

press ENTER, then type:

sudo apt-get install dvdstyler

if apt asks you if you want to install dvdstyler, press Y and ENTER.

Hopefully it will install without errors.  To close the terminal window, type the following and press ENTER.

exit

Hopefully the program will work again.

---

### Post by 77_GCSX on 2016-07-13
Got a chance to try this. I followed the steps EXACTLY and it still doesn't work.

Something to note here: When I did the above steps there was no short cut in the Launcher AND when I searched the dashboard for DVDStyler nothing came up. So, I removed it using the Software Center and re-installed via the same and still the same error.

One more thing to note: DeVeDeNG installed works fine, so I have something that makes ISO's. I am just so use to DVDStyler that it's going to take a little bit to get use to DeVeDeNG.

---

### Post by 77_GCSX on 2016-07-26
Just an update:

I have upgraded my movie server which is using 16.04.01 32 bit. It has the same issue with DYDStyler as this issue being reported. I thought the upgrade 'might' fix the problem but it didn't. I hope this helps shed more light on this problem.

BTW: DeVeDeNG does still work and I've made a few ISO's with it that play just fine so this isn't a MAJOR issue but I would like to see if something could be done to fix the DVDStyler issue.

Thanks again!
Paul

---

### Post by mc4man on 2016-07-27
Maybe this quick reply works, maybe yet another 'forbidden'

Well there is no dvdstyler in 16.04 so what are you using?
(- works fine here in 16.04 from[ here]("https://launchpad.net/~mc3man/+archive/ubuntu/check1") (- minimal testing

---

### Post by mc4man on 2016-07-27
screen here

---

### Post by 77_GCSX on 2016-08-01
> **mc4man said:**
> screen here
[https://ubuntuforums.org/showthread.php?t=2331939&p=13523089&viewfull=1#post13523089](https://ubuntuforums.org/showthread.php?t=2331939&p=13523089&viewfull=1#post13523089)

Nice to see it working on 16.04.

So, now that I have added the ppa and done the sudo apt-get update how does one actually get the 16.04 version installed? I've searched the dashboard for DVDStyler but nothing comes up. I've also tried the new and improved 'Ubuntu Software' with no luck.

Thanks again! Paul

---

### Post by mc4man on 2016-08-01
Well make sure it's installed as update what? (there is no dvdstyler in 16.04
 This will either install or tell you it's already installed - 
```
sudo apt install dvdstyler 

```
Then because of [a continuing bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1506744") not yet fixed some packages need a log out before they'll show up in the Dash

---

### Post by 77_GCSX on 2016-08-02
> **mc4man said:**
> Well make sure it's installed as update what? (there is no dvdstyler in 16.04
 This will either install or tell you it's already installed - 
```
sudo apt install dvdstyler 

```
Then because of [a continuing bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1506744") not yet fixed some packages need a log out before they'll show up in the Dash


AWESOME!! It now works on 16.04.1! 

Now, does this work on 14.04.4 64 bit LTS? If so I'd like to try it out since it still doesn't work on my 14.04.4 64 bit system.

But overall, all is good now!!

Thanks!! :)

---

### Post by mc4man on 2016-08-02
> **77_GCSX said:**
> AWESOME!! It now works on 16.04.1! 

Now, does this work on 14.04.4 64 bit LTS? If so I'd like to try it out since it still doesn't work on my 14.04.4 64 bit system.

But overall, all is good now!!

Thanks!! :)
No you can't use that package on 14.04.

For 14.04 I have it in an [extensive ppa ]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6")as it needed either libav11 or ffmpeg 2.x.x. I tried with both & while both worked I did see some players having small issues with menus when ffmpeg was used so it uses libav11. (both are quite capable for dvd video conversion.
Use of this ppa requires reading the page first! (the ppa is due for some upgrades, may have time shortly

But I've noticed this standalone ppa has restarted so maybe you'll wish to try it for 14.04 - 
[https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/dvdstyler](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/dvdstyler)

(- when I tried his 14.04 build quite some time ago it was a fail creating menus but there are new builds up so maybe ok. If it doesn't work out then the Just Looking2 ppa works fine, you'll need to remove libwxsvg2v2 & dvdstyler from panda jim first for same reasons as below

If you try it, (pj ppa), & it  works out for 14.04 & you wish to use that ppa for 16.04 also then you'll need to do something first before switching ppa's in 16.04 - 
1. remove the check1 ppa
2. remove dvdstyler & libwxsvg3
3. add the panda jim ppa, update sources, install dvdstyler

The reason for 1. & 2. first is when I put this up over  a year ago in 14.04 & then copied over to 16.04 several months ago there was no wxsvg using wxgtk3 so I named the package to suit, i.e. libwxsvg3 .That PJ ppa is using what Debian eventually renamed to  - libwxsvg2v5 so the packages aren't replacements but contain the same named .so file. In such cases apt will fail unless told to force an overwrite.

---

### Post by 77_GCSX on 2016-08-29
UPDATE:

Still on 14.04.05 and had some updates to install including a DVDStyler update. After a reboot DVDStyler now WORKS! I don't know what changed but it's fixed.

Thanks all, especially mc4man for the link to the 16.04 version.

---

