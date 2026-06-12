---
title: "[SOLVED] Gstreamer and codec issues"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by addmoreice on 2008-03-20
Ok, I spent a few days getting everything on my new Gusty install looking perfect (i'm a bit of a perfectionist) and everything is looking lovely! I was looking at some of my older movies and I didn't have a codec so totem goes and looks for it suggests i need codec blah blah (i didn't look and right it down or anything) i install it and now ALL my files open with a weird scrambled screen.
I have been fiddling with this thing trying various fixes (uninstalling gstreamer reinstalling removing packages left and right etc). 
Now i'm pretty sure i'm in deep trouble because i can't even load up totem and play a file now (says failure to create GStreamer object) What i would like to do is to 
apt-get remove --purge
and remove ALL the codecs and gstreamer then reinstall gstreamer and basicly reset all the media settings to ubuntus default install. once i do that i can install the codecs i need and then make a nice backup of my system as it is. I would rather not reinstall everything just to fix this one issue. anyone have any suggestions on how to reset the media stuff in ubuntu back to default install? or maybe a list of all the media files i should remove then the default list to add? I have been looking but i can't even find a google list of where the codecs are actually installed!
heck i messed this thing up so bad i can't even use _Volume Control_ anymore! ugg!

---

### Post by addmoreice on 2008-03-20
ppppwwwease? <does big puppy dog eyes>

---

### Post by Bubba64 on 2008-03-20
Here are several links which should help you.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
Keep posting as an update if you need more help I would also install if your using Firefox these add ons.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
I realize that these add ons are not Firefox only useful but are from the Mozilla add on site.

---

### Post by addmoreice on 2008-03-20
I appreciate those links but that doesn't really help me much. i have installed uninstalled purged and generally removed everything i can think of and reinstalled but it still says my gstreamer install is bad. what are the packages i definately need to have gstreamer working? I am convinced i removed a needed system package not just the codecs.


OH i just realized i forgot to mention I'm using 64 bit ubuntu if that makes a difference.

---

### Post by Bubba64 on 2008-03-20
Synaptic has a history of what you have done. Also do you have the extra repositories open like backport an security. In synaptic file then history will tell what you have done. In synaptic setting then repositories will open your choices I have everything but source clicked on. The second link I posted addresses 64 bit if you read down the instructions. I would make sure your repositories are open the run then 2nd post stuff. You might also due a system update manager. The only thing I can tell beyond the links is that if you follow them, I think your stuck on the thought that you removed a system package when that probably isn't the case, although possible look through your history and see if that is the case. If you use the the instructions on the second post it will overwrite what you need and ask you to rmove what isn't.

---

### Post by addmoreice on 2008-03-20
OK! heres an update! i have stripped out a ton of things and reinstalled a lot of other things. heres where things get um...bad

without gstreamer0.10-ffmpeg i get this message:

The playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder
DivX MPEG-4 Version 5 decoder plugin which is not installed.

when i install gstreamer0.10-ffmpeg i get nothing but a weird scratchy image that doesn't change. I have to manually install that package it is not found (totem doesn't even offer to look)

any clues?

---

### Post by Bubba64 on 2008-03-20
Go to add remove in the right top corner click on all available applications then type gstreamer in search bar and install all the  gstreamer and ubuntu  add ons I don't know if when you open all applications if it reloads there or you have to reopen it. I am not an expert on any of this stuff as far as understanding how they work , but I generally know what you need. After posting I remembered that your 64 bit so here is a link I hope will help I am not at all familiar with he limitation of 32bit programs on a 64 bit set up.
[https://help.ubuntu.com/community/32bit_and_64bit?highlight=%2864%29%7C%28bit%29#head-3a72cf7ce84381e60939938e0403a035f30b90ef](https://help.ubuntu.com/community/32bit_and_64bit?highlight=%2864%29%7C%28bit%29#head-3a72cf7ce84381e60939938e0403a035f30b90ef)
Here is the page I got the 64 bit link from it has one more link on it.
[https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=64+bit&titlesearch=Titles](https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=64+bit&titlesearch=Titles)

---

### Post by addmoreice on 2008-03-20
hmm and now i don't have the add/remove programs thing in the top left hand corner under applications. i think i have completely hosed this install >.<

---

### Post by addmoreice on 2008-03-20
WOOT i got videos running! some how i had kubuntu and xubuntu restricted extras installed but not ubuntu restricted extras. so i removed kubuntus and xubuntus and installed ubuntus and that seemed to have fixed that now i need to figure out how to get my add/remove applications button on the left hand side back and to fix my volume control button (the next to network icon thing) working again and i think i'm set to do a backup so i can play without screwing things up (beyond recovery hehe)

any ideas on how to get back the add/remove program button?

---

### Post by addmoreice on 2008-03-20
woot added gnome -app-install and got my menu back. ok one more problem to solve (i will probably get it myself) going to mark this as solved because you did an awsome job and fixed my big issue from original posting. THANKS!

---

### Post by Bubba64 on 2008-03-20
There are posts on how to bring back add remove on the forum I have never had to do it so I don't know the terminal code. After thinking about the fact that you have 64 bit I am not sure you can install from add remove effectively without first making sure that the 32 bit programs will run.Hopefully somebody on the forum will see where you are at and step in with better instruction. You might try
sudo apt-get update just paste this into the terminal and input your password and see what gets reinstalled.

---

