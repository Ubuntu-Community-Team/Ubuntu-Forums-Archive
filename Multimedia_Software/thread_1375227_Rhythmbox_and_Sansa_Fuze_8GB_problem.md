---
title: "Rhythmbox and Sansa Fuze 8GB/ problem"
date: 2010-01-07
forum: Multimedia Software
---

### Post by firmlytogether on 2010-01-07
Rhythmbox Version: 0.12.5
Sansa: Fuze 8GB
Ubuntu 9.10
 1) I put the Sansa under the MSC setting, attach to computer and I can see it on my desktop. I can open it from the desktop and see the first level of folders (MUSIC, VIDEOS, etc) When I open Rhythmbox, the icon appears, but it shows nothing inside device (which there are). Also, under Rhythmbox=>edit=>Plugins=> I have not checked Portable Player - MTP or Portable Player - iPod [there is no Portable Player - MSC, which I believe is the default when nothing is check (?).
 2) I put the Sansa under the MTP setting, attach to computer and I can see it on my desktop, I can open it from the desktop and I can see everything inside the Sansa. When I open Rhythmbox, I go to Rhythmbox=>edit=>Plugins=> and check Portable Player - MTP and I can see the device and all the music under it but cannot play any of them - it gives an error sign.
 Questions:
 *Do I need to delete rhythmbox and reinstall it?
        =>  Is not have a choice for Portable Player - MSC under the Plugin section of Rhythmbox a problem?
*What is wrong with it?
 What I want to do:
 *I want to rip my CD's to the Sansa, but can't because this situation.
 Thank you for helping!

---

### Post by Merovius on 2010-01-07
I have two Sansa'a an e250 and a Fuze. I set them both to MTP mode for use with Rhythmbox. I set them to MSC for use as a flash drive in  nautilus (drag n drop). 

Whatever you put on in MSC mode some times won't be visible in Rhythmbox and visa versa I believe. It is best to use one way or the other. Either will work. 

I always start Rhythmbox then plug in the Sansa. Sometimes more then once. Then it seems to work fine for the most part. I use mine for podcasts that I load through Rhythmbox. Also remember to right click the Sansa and eject it in Rhythmbox before you unplug it. 

In Nautilus remember to unmount the Sansa before unplugging it.

---

### Post by lgalicki on 2010-02-20
Hello people.

I have a Sansa Fuze with 8GB and I'm running Ubuntu 9.10 with Rhythmbox. I have set the Fuze to work with MTP. The packages mtpfs and mtp-tools have been instaled, and the MTP support plugin has been activated in Rhythmbox. The player is being recognized by Rhytmbox, and I'm able to see its content and drag and drop files in it. The problem is when I eject the Fuze. Rhytmbox freezes and then, after a couple of minutes, it returns. The Fuze, in the other hand, freezes and never returns. I'm forced to disconnect it "by force" and, as expected, its content is corupted and not playable.

I got it to work under MSC, but I really wanted to use MTP. Does anybody else have this problem? Any tips?

In time, Fuze's firmware version I'm using is V02.03.31P the latest provided by Sandisk at the time of this post.

Thank you!

---

### Post by Merovius on 2010-02-20
I have found that most of the time the Sansa'a work well with Rhythmbox and Ubuntu. BUT, not always. I have had periods when mine acted as yours does. Most of the time not. Sometimes I plug it in and nothing happens. I try again and again until it pops up. The gray out just means it hasn't responded in a while and *may* be frozen. Most often it's just busy.  My wifes Fuze did freeze up once on me. I thought it was because the cable was not fully "clicked" in and I moved it. I updated the firmware with the sandisk update tool (in Windows) and it has not frozen since. Might do that if you haven't. Good luck.

---

### Post by lgalicki on 2010-02-20
Thank you for the reply! I really appreciate your fast response. :)

I actually already updated it to the last firmware avaliable from Sandisk, but I've decided to use a different approach. What was bugging me is that under MSC I couldn't get the album artwork, but I just found out how to do it.

In case someone is in the same situation as me, here's what we gotta do:  put an image of the artwork in the same folder where the music files are. You should have a folder for each album. The name of the image must be *folder.jpg*.

Regards!

---

### Post by Merovius on 2010-02-21
Thanks. Great tip. Will have to remember that. Glad it's sorted out. :)

---

### Post by ebharv on 2010-02-21
Has anyone come across this problem with a Fuze 8GB:

I plug in my Fuze using MSC. I can see all the files and folders. I can drag and drop files and folders. I can see the Fuze connected in Rhythmbox I can add music in Rhythmbox (only though copy/paste though). When I eject the Fuze and disconnect it my media refreshes and there are no songs. 

When I plug it back in. It opens in Nautilus and Rhythmbox and there are indeed songs on the player. I can even play the song from the player through Rhythmbox. The Fuze will not load the songs though.

Never mind I solved the problem:

The Fuze will not recogize Ogg audio files with the .oga extension. Ogg audio must have the .ogg extension.

---

