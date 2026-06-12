---
title: "Is there a video program that will let me create menus?"
date: 2011-01-01
forum: Multimedia Software
---

### Post by xeddog on 2011-01-01
I have been searching through this forum (and some on the Internet) and unless I just have not used the correct arguments, I have not been able to find an application that will let me do what I want to do.  I have several downloaded tv programs that I would like to put on dvd with a menu so I can select any episode, watch it, and then be returned to the menu again.  

I have tried several programs including Cinelerra, Pitivi, open movie editor and a couple that I may have forgotten.  None of these appear to be able to create a menu system.

I have tried Bombono but it seems like all source files must be either mpg, mpeg, or vob format.  Almost all of my video files are either .avi or .mkv.  I could convert, but what a pita.

I tried Mandvd, but it either crashes, or does not produce a usable dvd.  Since it won't load an any machine I have tried, I am not sure what the output would look like anyway.

QDVD crashes unmercifully.  It seems like it would do what I want if I could get it to run without crashing.      

When I had Windows, I used a product called Pinnacle Studio which worked well even if it was slow.  But it does not have a linux version and the Windows version doesn't work in Wine.

Any suggestions???

Wayne

Intel I7-920 processor
6GB ram
1TB sata2 disk drive
etc.
Linux 64-bit Maverick

---

### Post by Mia1990 on 2011-01-02
Cinelerra, Pitivi, and open movie editor are just editors.Your wanting to make a dvd with menus correct?Try [tovid]("http://tovid.wikia.com/wiki/Tovid_Wiki") dvd burning software it works great and does really nice menus the only thing is i would install the svn version the website should tell you what you need to know.
good luck

---

### Post by rvchari on 2011-01-02
has anyone tried todisc-gui? does this mean the same in gui format for tovid ?

---

### Post by Rasa1111 on 2011-01-02
DeVeDe allows you to create menus. 
I know because i did it just a couple weeks ago.

 Not sure if its like what you want..
But I created a nice menu on a DVD i burned 
with the image I wanted for the menu, and was able to customize it decently. 
Came out well to.

---

### Post by lidex on 2011-01-02
DeVeDe as mentioned, also DVD Styler and ManDVD

---

### Post by xeddog on 2011-01-06
Just thought I'd give an update.  

Tovid was mentioned first, and I think it is the same thing as todisk-gui now.  I installed that a t tried it with no joy.  The program launched fine, was easy to create a menu system, and tweak the menu's somewhat.  I would click the button that said to run todisk now and I got a new window with a nice preview of the menu I created.  The menu header said to close the window to continue, and as soon as I closed it I got a small dialog box that said todisk was done.  I never could get it to create ANY files.  

DeVeDe was next.  It installed fine and was able to do what I wanted.  EXCEPT I wanted a little more in the menu.  DeVeDe only created buttons but I was holding out for something that would at least let me use thumbnails in the buttons.

ManDVD - I mentioned this one in my initial post.  If I remember, it has all I wanted, but it would not produce a usable disk.  I tried twice just to be sure.

That brings me to DVD Styler.  BINGO!  Quick to install and fairly easy to use.  Let me create the menu like I wanted and I was also able to create a usable disk.  Woohoo!  This is the one.  However, I do wish it would add one bell (or whistle if you prefer) and that would be the ability to create animated buttons.  Oh well.   I guess I got what I paid for.   :biggrin:

Thanks everyone.

Wayne

---

### Post by lidex on 2011-01-07
Sweet. Thanks for following up.
[http://sourceforge.net/tracker/?atid=600269&group_id=92301&func=browse](http://sourceforge.net/tracker/?atid=600269&group_id=92301&func=browse)

---

### Post by ronnielsen1 on 2011-01-07
>  However, I do wish it would add one bell (or whistle if you prefer) and that would be the ability to create animated buttons

Give it time. I'm sure it's a work in progress. I remember I checked out xmille (open source game of mille bournes) years ago and it was all text based and kind of lame. I checked it out years later and it was gui and pretty good

---

### Post by VanillaMozilla on 2011-03-24
There's a nice list here:
[https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring)

I had good luck with DeVeDe, provided I started with DVD-compliant files.  The menu was pretty good, but not slick or perfect.  Fast forward does not work right on the DVD (double and triple fast work), but otherwise pretty good.

One problem with all these programs is that there are too many conflicting and buggy libraries that they depend on.

---

### Post by schievelbein on 2011-08-01
This is another vote for DVD Styler.
I used to use Pinnacle for all of my videos that we produce.
Not that we have switched totally over to Ubuntu, I tried all of the programs listed above and gave up on most after 30-40 minutes.

IMHO, the easiest one to use was DVD-Styler and produced great results.

---

### Post by EkuquoL on 2011-08-01
... tl;dr

Your window scheme is mainly PNG, XFC, and other small JPG maskings / skins... You can create skins and even a splash screen<Opening screen animation> using GIMP. Just be sure you install Gimp GAP the animation suite for the application.

Too install schemes manually you will have to be root user.

---

