---
title: "Easy Install Everything For DVD MPEG AVI Playback &amp; VLC Auto DVD Play Upon Insertion"
date: 2008-04-23
forum: Multimedia Software
---

### Post by nicedude on 2008-04-23
UBUNTU GUTSY 32BIT COMMANDS TO INSTALL EVERYTHING NEEDED FOR VIDEO & DVD PLAYBACK - FIRST WHY DVD's DON'T PLAY AFTER UBUNTU INSTALL
Basically Codecs to play video files & DVD (ie. Divx, Xvid, Mpeg & DVD) Cant be installed with Ubuntu due to copyright & legal issues. So instead of trying to learn to compile your own versions of these softwares you can just add the Medibuntu repository and most things you need will be easily installable via synaptic or apt-get commands. Below are 3 commands that will do everything for you. The first 2 add Medibuntu to your repository source list & the 3rd will install everything you need to playback videos and mount and play DVD's. This is whats installed in my system and I use vlc to play DVD's and smplayer (which is a front end to Mplayer) to play Avi & Mpeg files. SMplayer just works the way I like since you can go full screen and then if you move the mouse to bottom of screen simple controls appear, it just worked the best of all I tried. If any or all of these softwares are already on your system don't worry as your system will just skip them. But don't run the Medibuntu commands if it is already in your sources list, it won't break anything but it will add more copies of the same repository to your lists. You can see if you have the Medibuntu repository as follows click top toolbar menu item named System -> Administration -> Software Sources, type your password and window will pop up - click on the tab called Third Party Sources and see if you see any that say Medibuntu in the list if yes skip the first two commands. To run the commands open a terminal ( top toolbar - Applications -> Accessories -> Terminal ) then carefully copy and paste the command one at a time into the terminal and press enter.

THIS IS ONLY TESTED ON UBUNTU GUTSY 32bit 7.10

Commands that will add the Medibuntu sofware repository to your sources - Note this is 2 commands so do each line separately 

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Command that will install all the software & codecs you need to play videos & DVD's - Note this is one command paste the whole thing.

sudo apt-get install vlc mplayer mozilla-mplayer smplayer smplayer-translations smplayer-themes ubuntu-restricted-extras w32codecs gnome-volume-manager libdvdcss2 libdvdnav4 libdvdread3 libvlc0 libxvidcore4 libwavpack1 libavcodec1d

MAKE VLC PLAY DVD's AUTOMATICALLY ON DISK INSERTION 
Now here's how to make VLC automatically play DVD's when you stick them in your system :-) . Go to top toolbar menu -> System -> Preferences -> Removable Drives & Media - when window pops up under first tab "Storage" I have the first 3 checked -> then click tab "Multimedia" and in Video DVD Disks make sure "play when inserted" is checked then add this without the quotes into the box "wxvlc %m" and then click close. 

I made and posted this since I see so many asking these questions and I want everyone to stay with Ubuntu instead of getting frustrated and going back to Microsoft's Garbage OS. The more of us there are the more the hardware makers will be forced to support Ubuntu & Linux in general or lose sales as a result. So spread the word about Ubuntu and let's grow this community. 

Thats all folks so now just stick in a DVD and smile real big :-)
 
P.S. I got the auto DVD play tip from someone here's post but couldn't find it again so if you are them or if someone knows the post I mean PM me and I would be glad to edit this post and give credit for it to that person. And if anyone sees any libraries I left out of the software install that might be needed by someone let me know and I'll add it.

---

### Post by wrgb2 on 2008-05-05
Thanks for posting this nicedude, I used it on Hardy Heron and it worked like a champ.  I put a link to this forum post on my blog, where I did a review of Hardy Heron.

Randy
[http://nocostsoftware.blogspot.com](http://nocostsoftware.blogspot.com)
[http://freebloggingtools.blogspot.com](http://freebloggingtools.blogspot.com)

---

