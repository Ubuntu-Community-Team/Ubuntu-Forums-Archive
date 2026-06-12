---
title: "Burnt dvds wont play in standalone player"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by rashaan salaam on 2008-02-14
I've compressed the dvd to an iso file using k9copy but when I burn that to a disc I can't get it to play in the dvd player that I have hooked up to my tv.  this dvd player plays other burnt dvds so I don't think it's the problem.  Anyone have any ideas?

---

### Post by aeiah on 2008-02-14
do you think it could be a pal / ntsc problem?

does the disk play in your computer once burnt?

---

### Post by rashaan salaam on 2008-02-14
the disc will play in my computer once burnt, just not in my dvd player.  i don't know what a pal / ntsc problem is.

---

### Post by aeiah on 2008-02-14
america uses ntsc for its video format, europe uses pal. other places use one or the other. perhaps you have authored your dvd in pal format and your dvd player can only play ntsc format movies or vice versa. its probably not the problem, but its worth looking at as its easy to correct

---

### Post by rashaan salaam on 2008-02-14
i guess that could be the problem. how would i figure out if that's what it is?  and if that's it how would i fix it?

---

### Post by dad311 on 2008-02-14
This is a common problem.  Not all DVD players will play home-made DVDs.  I have 4-5 DVD players round the house and and only 2 of them will play my home-made DVDs.  Its funny, sometimes its the cheap player that work the best with home-made DVDs.

You might try using different media (+R, -R, brand X, etc).

---

### Post by rashaan salaam on 2008-02-14
thanks for the advice guys.  i checked and k9copy is copying it as ntsc so that doesn't appear to be the problem.  maybe it is just the dvd player itself being weird about what kind of discs it likes or something.

---

### Post by gwpritch on 2008-02-14
I may be way off base, but I think the problem lies with k9copy. 
Any dvd I have authored using this app has failed to play in my dvdplayer although they will play flawlessly on my computer. 
dvd's authored with eg dvdshrink seem to play fine.

---

### Post by cotcot on 2008-02-14
I have no problem playing k9copy created dvd's. 
Sometimes the make of the dvd gives problems. Some blueish reflecting discs do not function on my player. Dvd-rw does not work neither.

---

### Post by wjston on 2008-02-14
> **rashaan salaam said:**
> I've compressed the dvd to an iso file using k9copy but when I burn that to a disc I can't get it to play in the dvd player that I have hooked up to my tv.  this dvd player plays other burnt dvds so I don't think it's the problem.  Anyone have any ideas?

I was having the same problem until I built K9copy from source. I realized I was missing a few dependencies that I believe solved this issue for me. Check to make sure you have these two libraries installed: libavcodec-dev libavformat-dev

If after installing these you still can't view your dvds, I would then install the latest K9copy from source following post #27 here (make sure you change the version of k9copy to the one you downloaded): [http://ubuntuforums.org/showthread.php?t=607991&highlight=k9copy&page=3](http://ubuntuforums.org/showthread.php?t=607991&highlight=k9copy&page=3)

---

### Post by polmir on 2008-02-14
What type is Your DVD home player? (model)

---

### Post by cowboyjo on 2008-03-02
An imperfect solution I've found is to un-mark the "Keep original menus" option in the "DVD playback options" tab on the right side of the k9copy window.  With that un-marked, I get a DVD that starts playing the movie as soon as I insert it, has no menus, but still has "chapters" that I can jump through with the "|<<" & ">>|" buttons on my DVD remote.

Specifically, my problem was that burnt DVDs created with k9copy were starting to play (some would display some initial screens, like language choice, and all would eventually get to the menu screen), but my Panasonic DVD player would then freeze on that screen.  (I'm curious as to whether this is what others mean when they say a burnt DVD would not play.)  To recover, I'd have to unplug the DVD player, plug it in again, and eject the DVD before it started to be read again. 

[The "K9 copy issues" thread [http://ubuntuforums.org/showthread.php?t=607991has](http://ubuntuforums.org/showthread.php?t=607991has) much useful explanation - esp. post 13 ( [http://ubuntuforums.org/showpost.php?p=3838852&postcount=13](http://ubuntuforums.org/showpost.php?p=3838852&postcount=13) ).  It's posts 26 & 27 have installation instructions for newbies.  But the menu bug is apparently not yet solved in k9copy.]

I tried marking the "burn with k3b" box in the "settings" -> "configure k9copy" -> "DVD" window, but got the same result.

When I did mark "Keep original menus" makin DVD copies with k9copy, they did work in my Toshiba SD-V280UA model DVD player (~5 yrs old).  It was my 10+ year old Panasonic DVD-CV37 that froze in the menus of these DVDs.  Both players will play DVD copies of home movies I've made with InterVideo WinDVD Creator in Windows.  Both players will play DVDs burnt with k9copy _without_ "Keep original menus".

In all cases, I'm using DVD+R media - cheap ones from various office discount stores.  I don't think the media quality is the problem, as was suggested in another post.

I also don't think PAL vs NTSC is related to my problem, as the DVDs burnt with k9copy will play in both my DVD players if I un-mark "Keep original menus" when I create them.  Maybe this is why k9copy information says you can _sometimes_ preserve the original menus.

BTW, if someone would post a link to k9copy or k3b documentation, I'd appreciate it.  I'm looking for something with information about settings and options.  I want much more detail than can be found at [http://www.dvd-guides.com/content/view/213/59/](http://www.dvd-guides.com/content/view/213/59/) .

---

