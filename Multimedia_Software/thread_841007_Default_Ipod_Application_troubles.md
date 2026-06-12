---
title: "Default Ipod Application troubles"
date: 2008-06-26
forum: Multimedia Software
---

### Post by screaminj3sus on 2008-06-26
Rhythmbox automatically opens when I plug my ipod in. I am using hardy. There seems to be NO VISIBLE way to change it to banshee. There is no open with when I right click the ipod. No Multimedia tab in preferred appications or removable devices, is there anyway to do this?

---

### Post by ilarrain on 2008-06-27
I'm having the exactly same problem. I wan't to set up gtkpod to be the default program uppon ipod connection but I've found no visible way.

Maybe we'll have to mess with gconf-editor

---

### Post by LuisGMarine on 2008-06-28
Hello,

I was having a similar problem, and to this day I still can't find a fix for it.  All the guides out there that I have run into tell me to do this.

Go to:
[B]
      System > Preferences > Removeable Drives and Media[/B]

Then once that pulls up you need to click on the " Multimedia " tab, and you should be able to change the default application.

The only thing is that I don't have the multimedia tab! :lolflag:

Try it and maybe you don't have it, because most of the people that write these guides claim to be using 8.04.


[http://ubuntuforums.org/showthread.php?t=400584](http://ubuntuforums.org/showthread.php?t=400584)

Maybe it's a bug?

-xkill

---

### Post by LuisGMarine on 2008-06-28
I looked in it for you and this is what I came up with.  Hope this helps you!  Here is a link to my blog :

[http://luisgmarine.blogspot.com/2008/06/changing-default-application-to-open-up.html]("http://luisgmarine.blogspot.com/2008/06/changing-default-application-to-open-up.html")

-xkill

p.s. share the love, digg it or something.

---

### Post by Enlitend on 2008-06-28
I think the guy refers to System->Preferences->Preferred Application

In Mutlimedia tab, select Custom and enter the custom app you want to use.

---

### Post by LuisGMarine on 2008-06-28
Even doing that doesn't work.  I still didn't get the option, double clicking the iPod opens up nautilus.  It offered to open the program with rhythym box still, even though I had another command where you said to put it.

This fix at least puts it in the righ-click menu.  When I right-click my iPod, and I also see the option to open it up with my application, in my case Songbird.  Even Nautilus offers to open it with my default application, not the other one selected by Ubuntu.

The only bad thing is that the other default option picked before is still there, and I cant' seem to find it.  I'm probably going to do a wide system search and try to find out where their MIME_TYPES and desktop entries are linked to.

-xkill

---

### Post by ironwolfe on 2008-10-03
any luck with this?  I have the same problem.

---

### Post by mc4man on 2008-10-03
What player would you like to use?

edit
Banshee and rythmbox should be available as choice in preferences-> media -> audio player (whether they work right  depends on whether default launch command is proper, if not the copy .desktop will work if you find the proper comm.  

Songbird can be done by either editing in defaults.list (like as done for vlc) or as here (defaults.list is limited to 1 app added per line, using default launch command 
[http://ubuntuforums.org/showthread.php?p=5806103#post5806103](http://ubuntuforums.org/showthread.php?p=5806103#post5806103)

amarok here
[http://ubuntuforums.org/showthread.php?p=5459412#post5459412](http://ubuntuforums.org/showthread.php?p=5459412#post5459412)

Others (copy.desktop 
[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

### Post by tlee on 2009-07-28
FYI: [http://ubuntuforums.org/showthread.php?t=763156](http://ubuntuforums.org/showthread.php?t=763156)

Open a file browser, go to 'edit' -> 'preferences,' click on the 'media' tab.

---

### Post by commonplace on 2009-08-29
> **tlee said:**
> FYI: [http://ubuntuforums.org/showthread.php?t=763156](http://ubuntuforums.org/showthread.php?t=763156)

Open a file browser, go to 'edit' -> 'preferences,' click on the 'media' tab.

Thank you!! That did it for me.

/Kevin

---

### Post by caseyboardman on 2010-06-07
Bingo.  Thanks!

---

