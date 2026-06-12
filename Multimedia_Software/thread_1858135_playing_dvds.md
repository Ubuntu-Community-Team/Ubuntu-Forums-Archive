---
title: "playing dvds"
date: 2011-10-11
forum: Multimedia Software
---

### Post by weezyrider on 2011-10-11
How do you get a recorded TV divx file to play? I have some handicam tapes I need to convert, but am not familiar with the dvr recorder. Figured if I could play a recorded BB game, I could handle the tape files. BTW- recorded OTA. No cable or satellite box involved.

---

### Post by lkjoel on 2011-10-11
Try typing this into a Terminal window:

*32 bit:*
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install w32codecs vlc

```

*64 bit:*
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install w64codecs vlc

```

---

### Post by weezyrider on 2011-10-13
Tried putting in what you gave me, still no joy. I'm trying to figure out what Toshiba does, and it's possible the DVD is in some kind of ISO format. I'm using DVD-R and no option to finalize. I think finalize only works with RAM discs and RWs. 

If I have the recorded DVD in any player, Ubuntu doesn't even SEE the player. All the players do work, I have some movie files from a memory stick written on a DVD and those play in all the players. When the movie file disk is in any player, Ubuntu sees it immediately. So it has to be file format of some kind. I can play the BB dvd in the old combo dvd/vhs and record onto vhs, so I don't think there's any signal that would prevent a copy being made.

I am finding info, but all of it is for Windows.

---

### Post by lkjoel on 2011-10-13
Could you give me the output of the following commands?
```
sudo lsusb -v
sudo lspci
sudo uname -a
sudo lsb_release -a

```

---

### Post by weezyrider on 2011-10-14
Do you want that posted? I'll do it later when I get on the desktop.
I just saw this post.
[http://ubuntuforums.org/showthread.php?t=1859683](http://ubuntuforums.org/showthread.php?t=1859683)

I'm wondering if Toshiba does something like this so you cannot copy digitally. What you gave me installed, but nothing sees those DVDs. Ubuntu doesn't even SEE the DVD player. It sees the floppy drive which shows up in places, but neither of the dvd drives unless a playable DVD is in the drive.
XP sees the player, sees the DVD, but I can't even check to find out what file formats Toshiba records in! 

The computer dvd players will play some movies. They will play Mpeg2, Mpeg4 which I downloaded from the video camera via memory stick and burned to a DVD. 

If there is no way around I might have to try making a VHS copy, then dubbing another DVD from the VHS.

---

### Post by weezyrider on 2011-10-21
I got it working. Hadn't finalized the DVD. Using DVD+R. The manual for the Toshiba has no index, and the finalize command was hard to find. I finally turned on settings and hunted for it through every menu setting on screen. 

The manual was very concerned with titling and subtitling DVDs. Most of the pages were dedicated to that. I don't bother. Usually 1 game per DVD. Now I can try using the IEEE1394 port to get stuff off the handicam - hopefully in MP4. Would rather edit on Ubuntu than on the recorder. 

I was worried that even if I selected MP4, the recorder would go to its native format.


The recorder will NOT record certain movies and premium channels if you are using cable. States that right in the manual.

---

