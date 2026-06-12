---
title: "dvd::rip play"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by triplemaya on 2007-12-27
Hi. I have managed to rip a dvd with dvd::rip, thanks for the help, now I want to play it, just off the hard drive, I have no interest in making copies. I have a directory called the name I selected, and in that directory is a directory called avi which is empty, a directory called tmp which has pictures in it, and a directory called vob which has all the film clips in it. I can play one at a time by dragging the clip into a movie player, but I was hoping for a somewhat less interactive method of viewing the movie!? This must be possible, but the documentation does not seem to address it. Please could someone give me the kiddy version of how to watch a movie ripped with dvd::rip. Thanks. I'm running ubuntu gutsy with gnome in case that makes any difference.

---

### Post by RudolfMDLT on 2007-12-27
Okay, firstly, lets make sure that you have all the necessary goodies:

Go here: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624) and follow the how to and make sure that you have libdvdcss2 and w32codecs installed. Open synaptic and install Totem-Xine and kaffeine. Kaffeine may be a big download if you have no other KDE app's installed so if it does turn out a big download you don't have to install it - I just prefer it as it works better. 

Now open totem and click on Movi and click on open, navigate to the folder and while holding the shift key click the first and then the last icon. Press open and you should be set.

---

### Post by triplemaya on 2007-12-27
Hi. Thanks for your post. I have xine installed already, so I tried what you suggested, but it would not accept the directories. To make sure I was doing it right I ran totem from the command line.

 Under directory vob there are 26 directories, and in each one there is one or more vob files. When I highlighted all of the 26 directories in the open dialog, it did not respond to me pressing the add button.

I tried it first without installing kaffeine, in case this would work, so I then tried with kaffeine, though I was not sure what this was meant to do. This makes no difference, I still cannot add the directories with the vob files in them.

I tried kaffeine from the command line, but it does not accept any way of playing dvds except from the disk.

Surely there must be a way to do this!? Surely if dvd::rip is capable of making a dvd disk it must keep all the menus etc, or it must be possible to do this?

---

### Post by RudolfMDLT on 2007-12-27
DVD rip puts the VOB files in folders? thats very odd. You are supposed to select the files within a folder not just the folders. I haven't yet found an app that does a recursive folder search like winamp.

Search through the folders by hand and find the folder where the main title is, and then add it's content to the play list as this is the movi you want to watch? Or do you want the Menu system and everything to work? In that case I recommend you rip an ISO image using K9Copy and use VLC to play the ISO.

---

### Post by triplemaya on 2007-12-28
That works. Thanks again.

---

### Post by RudolfMDLT on 2007-12-28
pleasure! :)

---

