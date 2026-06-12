---
title: "What's the best way to install Real Player?"
date: 2008-04-29
forum: Multimedia Software
---

### Post by diablo75 on 2008-04-29
I have a fresh install of Ubuntu 8.04 on my system.  In the past, I've had mixed success with installing/getting real player to play anything.  It seemed to lock up more often than not.  Is this still the case these days?

---

### Post by lancern on 2008-04-30
I just had all 3rd party repos enabled in Synaptic and was able to install it in terminal
and it works fine for me..It seems to only wana play rm files and nothing else..I just use it to watch my older rm files that use an older rm codec and wont play in other players..

try:
Sudo apt-get install realplayer

---

### Post by diablo75 on 2008-04-30
> **lancern said:**
> I just had all 3rd party repos enabled in Synaptic and was able to install it in terminal
and it works fine for me..It seems to only wana play rm files and nothing else..I just use it to watch my older rm files that use an older rm codec and wont play in other players..

try:
Sudo apt-get install realplayer

Could you clarify which third party repos?  Because from the looks of it, I have them all enabled.  Aptitude/Synaptic still does not list real player as an available package to install.

---

### Post by lancern on 2008-04-30
[http://ubuntuforums.org/showthread.php?p=4737528](http://ubuntuforums.org/showthread.php?p=4737528)

try this link..someone has made a .deb for it..have tried and working for me

---

### Post by i2k on 2008-04-30
Helix Player is made by RealNetworks, the same people that make Real Player.

---

### Post by diablo75 on 2008-05-01
> **lancern said:**
> [http://ubuntuforums.org/showthread.php?p=4737528](http://ubuntuforums.org/showthread.php?p=4737528)

try this link..someone has made a .deb for it..have tried and working for me

I tried to install the deb, and while "realplayer" shows up in synaptic, it doesn't appear in the Applications menu anywhere.

So I downloaded the official bin file for version 11 from Real players website, and followed the correct steps to chmod and then run the bin, following the default install paths by pressing the enter key at each prompt.  Real Player now appears in the Sound & Video menu, but when I try to run it, I get this error:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=68232&stc=1&d=1209619142[/IMG]

I've had stability issues in the past with Helix, but I'll give it another shot.  In the mean time, can anybody explain what causes this error and how to fix it?

---

### Post by lancern on 2008-05-01
> The Deb installs into the /opt directory and the executable path is /opt/real/RealPlayer/realplay Use the menu editor to create a menu item for Real Player.

I just made a launcher for it on my panel..right click panel and choose launcher then just go to that location and drag and drop realplay onto the launcher.

[http://i164.photobucket.com/albums/u13/unlancer/snapshot17.jpg](http://i164.photobucket.com/albums/u13/unlancer/snapshot17.jpg)

---

