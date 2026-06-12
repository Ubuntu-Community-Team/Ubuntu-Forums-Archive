---
title: "Amarok 14"
date: 2010-10-11
forum: Multimedia Software
---

### Post by dave r on 2010-10-11
__ I have just upgraded to 10.04 and have installed the old version of Amarok, I have always found that this worked very well with my MP3 Player, a Creative Zen. This time Amarok wont connect to the player, when I try to connect I get a small window pop up that says 

could not launch the mail client:

KDEInit could not launch 'Kmail'.:
Could not find 'kmail' excutable.
           OK

It wont load then and if I click the OK button Amarok shuts down.

---

### Post by dave r on 2010-10-12
Bump

---

### Post by dave r on 2010-10-12
Bump

---

### Post by wkulecz on 2010-10-12
Try installing Kmail with synaptic, or try to figure out which package will install Kmail.

---

### Post by dave r on 2010-10-12
> **wkulecz said:**
> Try installing Kmail with synaptic, or try to figure out which package will install Kmail.

I don't want to install Kmail, I just want amarok to open my MP3 player when I click connect and not open this Kmail window, I use Evolution. I have used Amarok 14 both in 9.04 and 9.10 without problems, its worked very well up to now.

---

### Post by mc4man on 2010-10-12
Where did your amarok 14 come from?

You may wish to follow this simple how-to for lucid
(I'm on maverick and have amarok-1.4 installed/working using a very similar method

[http://ubuntuforums.org/showthread.php?t=1559002](http://ubuntuforums.org/showthread.php?t=1559002)

Edit:
otherwise there are pre-build .debs of pana available in several ppa's for lucid

---

### Post by dave r on 2010-10-13
> **mc4man said:**
> Where did your amarok 14 come from?

You may wish to follow this simple how-to for lucid
(I'm on maverick and have amarok-1.4 installed/working using a very similar method

[http://ubuntuforums.org/showthread.php?t=1559002](http://ubuntuforums.org/showthread.php?t=1559002)

Edit:
otherwise there are pre-build .debs of pana available in several ppa's for lucid

I got it from here
[http://www.techtickle.com/how-to-install-amarok-1-4-in-ubuntu-lucid-karmic-jaunty-linux.html](http://www.techtickle.com/how-to-install-amarok-1-4-in-ubuntu-lucid-karmic-jaunty-linux.html).

Your how to looks a bit complicated for a simple fella like me but I'm going to see how it works

---

### Post by dave r on 2010-10-13
Installed using your method but can't start Amarok, get this message 

Amarok could not be started!
This may be bedause the amarokapp binary is not in your PATH.
Try locating and running amarokapp from a terminal
                  OK

---

### Post by mc4man on 2010-10-13
> I got it from here
That ppa's version should be able to work on lucid.
While dentaku65's method produces a fuller featured amarok than the ppa you should probably uninstall what you did and resolve why the ppa wasn't working.

Assuming you followed his how-to and haven't deleted the the source folder then open a terminal and 
```
cd amarok-1.4.10 && sudo make uninstall
```

Then reinstall amarok14 from the ppa. Before reinstalling go into home folder (view - show hidden files), and open .kde/share/config
Delete any files that start with amarok.
While there you could also go to .kde/share/apps and delete the amarok folder
Then reinstall from the ppa and try.
(Or ask how to remove any ppa amarok14 packages and install pana instead

---

### Post by dave r on 2010-10-13
> **mc4man said:**
> That ppa's version should be able to work on lucid.
While dentaku65's method produces a fuller featured amarok than the ppa you should probably uninstall what you did and resolve why the ppa wasn't working.

Assuming you followed his how-to and haven't deleted the the source folder then open a terminal and 
```
cd amarok-1.4.10 && sudo make uninstall
```

Then reinstall amarok14 from the ppa. Before reinstalling go into home folder (view - show hidden files), and open .kde/share/config
Delete any files that start with amarok.
While there you could also go to .kde/share/apps and delete the amarok folder
Then reinstall from the ppa and try.
(Or ask how to remove any ppa amarok14 packages and install pana instead


It seems that where ever I get Amarok from it either will not install or it installs and when I try to connect to the player I get the error message. I tried Pana but have the same problem as with Amarok, try to connect to the player and I get the Kmail message. I am wondering if the computer is missreading the player in some way? If so I am wondering if theres some way to change this?

---

### Post by mc4man on 2010-10-13
I don't think this has anything to do with kmail (amarok is probably crashing and looking for kmail to send crash info

Try removing all amarok/pana installs  - if you didn't already then do the sudo make uninstall on that amarok source file.
Also search amarok and pana in synaptic - completely remove any packages found, if anything.

Also remove those files and folder in your home folder ->  .kde or even just delete the .kde folder itself. (maybe removing the .kde folder is best at this point, certainly if you've no other kde apps installed

Then pick one, install and open from a terminal using either 
amarokapp or panaapp
Post what the output is.

---

### Post by dave r on 2010-10-14
> **mc4man said:**
> I don't think this has anything to do with kmail (amarok is probably crashing and looking for kmail to send crash info

Try removing all amarok/pana installs  - if you didn't already then do the sudo make uninstall on that amarok source file.
Also search amarok and pana in synaptic - completely remove any packages found, if anything.

Also remove those files and folder in your home folder ->  .kde or even just delete the .kde folder itself. (maybe removing the .kde folder is best at this point, certainly if you've no other kde apps installed

Then pick one, install and open from a terminal using either 
amarokapp or panaapp
Post what the output is.

I cleaned up then installed Pana, tried it with the player and got the kmail message. I then restarted Pana with the panapp command and got the output below.

dave@DavesBoxOfTricks:~$ panaapp
kbuildsycoca running...
Reusing existing ksycoca
DCOP Cleaning up dead connections.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP



One interesting thing is neither Amarok or Pana show up in the Applications menu after they are installed. I have found another music player, Clementine, this works very well with the player, unfortunately it messes up the computer, with Clementine installed I cant access my home folder, so I cant use it.

---

### Post by mc4man on 2010-10-14
> Clementine, this works very well with the player, unfortunately it messes up the computer, with Clementine installed I cant access my home folder, so I cant use it.

See here about something other than nautilus becoming default folder handler (usually all folders except those on desktop.

[http://ubuntuforums.org/showthread.php?t=1596041](http://ubuntuforums.org/showthread.php?t=1596041)

pana appears to be opening fine - don't know why it doesn't like your player
(you did delete all those config files in .kde

---

### Post by dave r on 2010-10-14
> **mc4man said:**
> See here about something other than nautilus becoming default folder handler (usually all folders except those on desktop.

[http://ubuntuforums.org/showthread.php?t=1596041](http://ubuntuforums.org/showthread.php?t=1596041)

pana appears to be opening fine - don't know why it doesn't like your player
(you did delete all those config files in .kde
 
I deleted the whole folder, but the install put a new version in my home folder.

---

### Post by dave r on 2010-10-15
> **mc4man said:**
> See here about something other than nautilus becoming default folder handler (usually all folders except those on desktop.

[http://ubuntuforums.org/showthread.php?t=1596041](http://ubuntuforums.org/showthread.php?t=1596041)

pana appears to be opening fine - don't know why it doesn't like your player
(you did delete all those config files in .kde

I installed Ubuntu Tweak and used that to change the file associations, unfortunately Clementine doesn't work well with the player, if I import music it puts it outside the players file system and the player can't see it.

---

### Post by dave r on 2010-10-16
I'm going to close down this thread now. Many thanks to mc4man for his help. I don't think we can mark it as solved as we still don't know for certain what the cause is, I think mc4mans idea that amarok is crashing and is trying to call home is about right, and we have not come up with a solution. What's happened is I have managed to get my MP3 player to work with the latest amarok. I would have preferred to have used the old amarok, clementine or exaile, all have a better layout, but there are problems with all of these.

---

