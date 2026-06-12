---
title: "File transfer to zen makes it freeze every time"
date: 2009-10-28
forum: Multimedia Software
---

### Post by mrpeachy on 2009-10-28
I have ubuntu jaunty

I have successfully mounted my Zen Mozaic as a file system (if anyone is interested on how to do this i used this guide : [http://www.anythingbutipod.com/forum/showthread.php?t=32817](http://www.anythingbutipod.com/forum/showthread.php?t=32817) )

When i drag pictures from my ubuntu pictures folder to the pictures folder on the zen, it seems like everything is fine.  I can see the thumbnails all load up in the zen folder.

But when i unplug the zen and take a look at the pictures the same thing always happens: i can see the first 9 thumbnails of the photos, but the tenth thumbnail is a few vertical black and white lines and the zen freezes up.

I can reset the zen, mount it again and delete the photos and them my zen works just fine.

Can anyone think of an explaination or a fix for this behaviour?  
In Windows i can drag the same files into the zen without a problem, but i would like to get it working in ubuntu!

---

### Post by mrpeachy on 2009-10-29
more info re my zen problem.

here is a picture of what my zen looks like after moving photos onto it from ubuntu.
[http://www.flickr.com/photos/96021423@N00/4055816987/](http://www.flickr.com/photos/96021423@N00/4055816987/)

some of the thumbnails look fine, some are just the black and white lines that you see in the pic.  Then when i scroll through the thumbnails I get to a thumbnail that doesn't load at all and this is when the zen freezes up.

I can remont the zen in ubuntu and look at all the pictures from the pictures folder on the zen.

any ideas?

---

### Post by mrpeachy on 2009-10-31
*bump*  this is the only issue that is keeping me back from ditching Windows entirely.

just want to get my zen to work!  same thing happens when i upload photos using gnomad2 instead of just dragging them into the folder.

---

### Post by syelyah on 2009-10-31
Have you tried using Gnomad2? Making my Zen work was my only problem with U until I installed it. Gnomad2 is in the repositories and you just have to plug in the device, select unmount and open the program to be able to transfer music or data files (pictures in your case). 

Hope that can help you...

---

### Post by mrpeachy on 2009-10-31
Yep, have used Gnomad2.  I can upload mp3's just fine no problems and it uploads my photos too.

Problem is on the zen, after i unplug and try to browse the pictures, many of the thumbnails are just black and white lines... when i click them to display the image it appears as it should.

---

### Post by wildweathel on 2009-10-31
My gut instinct is that this is due to a bug in the MTP-protocol software.  Since stable Ubuntu releases aren't cutting edge, it's entirely possible that the bug has been fixed in the "upstream" software.  For example, the current of libmtp is 1.0.1, but my Karmic install has 0.3.7-3ubuntu2.  "dpkg-query -p libmtp8" will check what version you have installed, probably 0.3.0-1ubuntu3.  

So, I think the next thing to try is to install a later version of libmtp8/mtp-tools and see if that fixes the problem.  The easiest way to do that is install the version from Karmic.

The most "correct" way to do this is to add the Karmic software sources, but "pin" them so your computer doesn't decide to upgrade.  Unfortunately, there isn't yet a user-friendly way to do this, and making a mistake might suddenly and accidentally upgrade you to Karmic.

Since this is just a small change, it's easier and safer to just download the .deb packages and install them manually (double-click, type in password).  

[list]
[*][http://packages.ubuntu.com/karmic/libmtp8](http://packages.ubuntu.com/karmic/libmtp8)
[*][http://packages.ubuntu.com/karmic/mtp-tools](http://packages.ubuntu.com/karmic/mtp-tools)
[/list]


Hopefully, that will fix things.  

If not, you can downgrade to the version you have installed now.  To do that, open Synaptic (System -> Administration), search for libmtp8, right-click, "mark for reinstallation," repeat for mtp-tools, click "apply."  Good luck.

---

### Post by mrpeachy on 2009-10-31
Thanks for the suggestions.

Actually i did just upgrade to Karmic.  Using the zen mozaic is *much* easier now, don't have to be root etc.  

And running karmic seems to have stopped the freeze up problem.  But still getting the black/white line thumbnails on the zen.

has anyone else had a similar problem with photos on a zen mozaic??

---

