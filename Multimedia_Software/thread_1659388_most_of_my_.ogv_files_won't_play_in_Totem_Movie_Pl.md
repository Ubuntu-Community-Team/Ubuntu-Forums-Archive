---
title: "most of my .ogv files won't play in Totem Movie Player"
date: 2011-01-04
forum: Multimedia Software
---

### Post by dgw on 2011-01-04
I have a lot of .ogv and .mpg files. Most of the .ogv files won't play, and none of the .mpg files will play, in Totem. I installed VLC media player and all the files will play in it. 

If I click on file properties in Nautilus for the files that won't play, it says "Creating Properties window. You can stop this operating by clicking cancel." but it never actually shows me the file properties. 

Anyone know what's wrong here?

---

### Post by dgw on 2011-01-04
I have more info. 

For a while (maybe 6 months?), I've noticed what I thought was a Cheese bug. The .ogv files that I'm having this issue with were all made in Cheese, and the .mpg files were made with my camera. When I open up Cheese and make a video, the first video I make turns out just fine. If I make subsequent videos, there's something wrong with them and they don't play at all....or so I thought. 

It just occurred to me that all the .ogv files that won't play in Totem were made before I noticed the Cheese-bug. Since noticing the bug that I thought was in Cheese, I've been restarting Cheese after I make a video so that I don't get any duds. 

I made a few videos in Cheese to test and indeed, videos made after the first one don't play in Totem, but they do play in VLC.

I don't know how this relates to the .mpg files not playing. Most of the .mpg files are years old, made with my camera, and I don't access them very often.

I'm not sure if this is a bug with Cheese, Totem, or Nautilus, or some weird bug-combo.

---

### Post by no2498 on 2011-01-04
try making your videos in vlc
open it click media , open capture divice
play , record


and if totem still dont work right
install smplayer
type it in a terminal it tells you how to install it

---

### Post by dgw on 2011-01-05
I tried to make a video in VLC and I think it recorded, but I don't know where VLC stores files. That was after spending far too long trying to figure out where the record button was, since it's apparently hidden by default. 

I don't really mind the Cheese issue, since I can still record videos with it, and I don't mind restarting it after each video. I was pretty freaked out when I thought a lot of my files had something seriously wrong with them, it was a relief to see them play in VLC and know they're ok. Now I just wonder if I should be bug-reporting this issue, and I'm not sure how to do that.

---

### Post by Yellow Pasque on 2011-01-05
It would help if you installed the appropriate -dbg packages for totem and gstreamer and started totem from a terminal.

---

### Post by no2498 on 2011-01-05
look in your home folder for vlc movies

---

### Post by dgw on 2011-01-07
> **Temüjin said:**
> It would help if you installed the appropriate -dbg packages for totem and gstreamer and started totem from a terminal.

Installed it for totem, but I don't know which package to install for gstreamer.

---

### Post by dgw on 2011-01-07
> **no2498 said:**
> look in your home folder for vlc movies

I'm not sure how I missed that, they are in my home folder. The videos made in VLC work in VLC, but not in Totem. In Totem I get the error "Could not demultiplex stream."

---

