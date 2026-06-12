---
title: "Parts of Myth missing from install on Ubuntu?"
date: 2010-12-21
forum: Mythbuntu
---

### Post by GnomicGhost on 2010-12-21
Hi all, first off sorry if this is in the wrong section.  I think it could go in either "installations & upgrades" or here seeing as I am wanting to install Mythtv on a default Ubuntu 10.10 install.  (I want to use Ubuntu as I prefer the options available to me from the Gnome side of things and put Mythtv over the top of that)
Also, if this has been posted, again sorry, but I did a search and looked around a bit.

I have 2 questions/issues.
1 - Where is the gnome myth config GUI in the menu on a Myth over Ubuntu install?  I can't remember exactly what the name is in the menu on a Mythbuntu install, but it's a config window (in desktop environment, not MythBackend or Frontend setup) with about 8 or 9 options down the right hand side like: Jamu config, Default Login behaviour (or similar), etc.
I can't find that anywhere in the gnome menus?  Can I access it from a console command at all?

2 - (which I think could be fixed from issue 1)
When actually in Myth, I have only one menu for media on the PC.
Under "Media Library", I only have "Watch recordings".  In the Mythbuntu install, there are about 4 sub-menus for watching media (shows already on the HDD etc), Photos and Music (I think).
I am hoping it's just an option of selecting them from the GUI config screen from issue 1 where you can enable/disable MythWeb, MythNews, MythWeather, MythMovies etc.
But that's the menu I'm missing in the Gnome menus :(

Thanks in advance if you can help a new(ish) myth user :)

---

### Post by GnomicGhost on 2010-12-21
Solved my own problem (after a long while of trying)

I figured it would just be missing packages from the Myth install to resolve it.  It was.
I put the Mythbuntu LiveCD in and went to install screen from that (while in Ubuntu 10.10/Gnome) and just marked the relevant sounding packages that weren't checked for an upgrade/install from the LiveCD.

For anyone else interested who misses out on these when Myth is installed over a *buntu install, try:
sudo apt-get install mythgallery mythvideo mythmovies mythmusic mythbuntu-control-centre

Hopefully that will fill out the menu/sub-menu's fully for you too, and give you the GUI config at Desktop level

---

### Post by thatguruguy on 2010-12-21
I'm not sure that the mythbuntu control centre is the same thing as a "gnome myth config GUI", but whatever.  Glad you were able to get this sorted out.

---

### Post by AllGamer on 2011-05-10
seems like in v11.04 mythmovies was replaced by mythplugins

---

