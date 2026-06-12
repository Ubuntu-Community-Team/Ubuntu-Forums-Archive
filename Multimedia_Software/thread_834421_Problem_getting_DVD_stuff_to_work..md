---
title: "Problem getting DVD stuff to work."
date: 2008-06-19
forum: Multimedia Software
---

### Post by juiceman on 2008-06-19
I"m following the sticky tutorial for all this stuff and getting DVDs to work (like Happy Gilmore).

I was about halfway through the process when I went to bed.  I get up this morning and my update manager has like 4 libraries waiting for Medibuntu.

When I try to click install, it says I have to "Manually run dkpg --configure -a".  But when I go into terminal it says I need superuser access for that.  Wtf does that mean?  I'm the only user, the administrator.

Furthermore, Aside from those libraries, I attempted to make progress in the direction the tutorial is going. So i go into terminal and type in:

cody@smacktop:~$ sudo apt-get install regionset
[sudo] password for cody: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
cody@smacktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
cody@smacktop:~$ 

AND I GET THE SAME CRAP!  What can I do to make progress here.  I just want to be able to pop a DVD into my DVDrom drive and watch it.  Why and how is such a common activity not a simple point-and-click away?  This is something the next release of Ubuntu might focus on.

HELP!
Juice

---

### Post by cozmicharlie on 2008-06-19
The permissions in Linux can be confusing for new users (and older users).  Basically whenever it asks for for super user it means you have to add "sudo" before the command.  So to run "dkpg --configure -a"  at the prompt (#) type the following:

```
#sudo dkpg --configure -a
```

It will ask for your password and you just type in the password you set up when you installed Ubuntu.  

Ubuntu does not use administrators like Windows.  You are a user or you are root.  Users don't have root privileges.  It is a security measure but can be very frustrating for new users.

As you work your way through the tutorial, post back if you have any problems and I will help you so you can watch DVD's.

---

### Post by juiceman on 2008-06-20
Ok, 
I did what you said and got so far as to get everything loaded 'properly'.  Basically, no errors.

Now I have another problem.  I loaded up a burned DVD that has no menus and it worked great.  But when I load up billy madison or sinbad, it seems to lock up VLC.  I have to force quit to get it to stop sitting there doing nothing.  It won't even load any video at all.

Help?>

---

### Post by mc4man on 2008-06-20
Did you run regionset and make sure drive is set to a region?
Did you install libdvdcss2?
If so and vlc still doesn't work, open vlc from the terminal, try playback of disk and ck. errors.

---

### Post by cozmicharlie on 2008-06-20
By "sticky" tutorial I assume you mean this ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)).

As mc4man suggests, did you get through the tutorial and install all the DVD libraries, codecs etc?

This is from the tutorial:

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc

```
**Zero DVD Playback:** Installed the necessary applications and packages but still cannot play/rip commercial DVDs? Perhaps you should make sure the DVD drive has been set to the correct region. If you have never successfully played DVDs in Ubuntu or Windows, install the following command line based application:

```
sudo apt-get install regionset

```
Please be aware that most drives limit you to about 5 changes (regionset should tell you how many you have left), so if you plan to watch foreign DVDs, it would be best to have a secondary external DVD drive and have it set to a different region to the one in your machine. To set or change your DVD drives region, put any disc into your drive and type "sudo regionset" into the terminal, then simply select the relevant region code. Here is the list of region codes and which countries they cover:

RC1 = North America (USA and Canada)
RC2 = Europe, Middle East, South Africa and Japan
RC3 = Southeast Asia, Taiwan, Korea
RC4 = Latin America, Australia, New Zealand
RC5 = Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
RC6 = China

For those of you who previously played DVDs in GNU/Linux or Windows, but for some reason are unable to now, it could be related to faulty leads/connectors, but give this one last software-related method a try:

```
sudo apt-get install build-essential debhelper fakeroot

```
then:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

or if you get an error with that command:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```
Some DVD Playback: If unlike above you have followed Part 4 of my how-to and most DVDs play fine, but you're having trouble with some newer DVDs, please refer to this link and concentrate on the solution for VLC (this bug was apparently fixed in February 2008).

---

### Post by juiceman on 2008-06-20
I did everything and even the troubleshooting things.  Still no worky.  

I think it is related to the 'menus' of these dvds.  The fact that they are not just a video stream from the getgo, but have menus and such....

---

### Post by mc4man on 2008-06-20
what you should do is open vlc from the terminal ect. and post the error messages
edit:
> Still no worky
The default launch command for vlc ( vlc %U ) is not good for proper disc navigation and on _some_ discs will prevent vlc from opening at all.
Go to edit menus (right click on applications or go system -> preferences -> main menu), expand sound and video, and on right side right click on vlc -> properties. Change the launcher command to
```
vlc %m
```
or if you want to make vlc the default autoplay player here's a simple way (includes above)
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by juiceman on 2008-06-20
> **mc4man said:**
> what you should do is open vlc from the terminal ect. and post the error messages
edit:

The default launch command for vlc ( vlc %U ) is not good for proper disc navigation and on _some_ discs will prevent vlc from opening at all.
Go to edit menus (right click on applications or go system -> preferences -> main menu), expand sound and video, and on right side right click on vlc -> properties. Change the launcher command to
```
vlc %m
```
or if you want to make vlc the default autoplay player here's a simple way (includes above)
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

The %m fixed it.  I have sinbad rockin right now!  Thanks dude.  Pimpstylee!

---

