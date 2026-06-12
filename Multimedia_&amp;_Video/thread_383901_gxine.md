---
title: "gxine"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by talon 2 on 2007-03-13
I can't get gxine to work.  When trying to use ot it opens then a get a message about not finding plugins.
I did some looking around. I found in the veiw tab. then to the xine engine log. then to plugin log.  It shows many plugins. the last one at the bottom shows this  skipping unreadable plugin directory/home/my username/.xine plugins

Any help would be geatly appreaciated.

---

### Post by Neobuntu on 2007-03-14
...Not enough info about what you are running it on but generally, purge everything to do with xine and just reinstall it.

---

### Post by talon 2 on 2007-03-15
> **Neobuntu said:**
> ...Not enough info about what you are running it on but generally, purge everything to do with xine and just reinstall it.

Hi thanks for the response.  I am running ubuntu 6.06 debian i believe this is this is the version i am ruuning.

---

### Post by Neobuntu on 2007-03-19
6.06 LTS is a perfect place to be right now and it's is an overall layer of user ease over Debian's genius.

I prefer Kubuntu's KDE but that's me and you can ```
sudo aptitude kubuntu-desktop
``` (and choose KDM) if you want to try both. be sure to set your session, at the KDM login to KDE as well; before entering your password. I think it's better to start with a Kubuntu CD so the install is lighter (without both) but if you want to try both it doesn't matter.

You will enjoy far reaching stability in every avenue with the LTS version and you are able to upgrade to "Edgy" (6.10 not-LTS) as it further stabilizes and you are ready. It's good now, I know (I use it) but getting better. Don't rush.

That said, I recommend that you install Automatix. It is an addition to the regular package manager and handles stuff that's deemed legally troublesome (thanks to monopoly lawyers and lack of software freedoms) for Ubuntu to include by it's self. Follow the easy manual install, for your version. Normally, one does NOT install things "manually" or programs not in the ubuntu tested (.deb) package repositories. Automatix its self, is and has, an Ubuntu package for Dapper and it then installs custom tweaks and additions, of many types, tested specifically for Dapper. With Dapper (6.06) currently, I believe you simply download Automatix(2) in package form, and right click it, for installation with the normal package manager. It will then be on your 'System" menu and ready for check/un-check box, ease. Check it out.

[http://getautomatix.com](http://getautomatix.com)

Automatix makes "codecs" easy to install, for movie playing, among many other things. One could do all these things one by one, on the command line and without Automatix but with Automatix, it couldn't be simpler or take less time. There's discussion about newer testing releases; not needing Automatix, as much.

Also of note: Xine and mplayer are the movie players behind your GUI front end media players such as  Kaffine, Totem etc. There's also VLC player; with it's set of codecs. Realplayer is another one and it's easy to add in Automatix. So whatever movie you might download, it has any number of possible formats. What would you do then? Just try different media players and see which one works best on that stream; however it was encoded.

In the MS Windows world, one usually has to use VLC for Windows anyway and you have much less choice,  as usual.

Overall for you and with Ubuntu, Totem (Media Player) would most likely fit you best. I love the way Totem goes full screen with the "f" key and stretches (to any size) with the "r" and "t" keys. This way one can chop off a small part of the sides (wide screen); in exchange for a bigger screen. (And it does not matter that it's a GTK2/Gnome program while I run KDE/Kubuntu. I use the Aquativo gtk2-engine (look) for gnome programs I run in KDE and that matches wonderfully with the Milk setting in the ("sudo aptitude install baghira") "Baghira" KDE style.

Hope that helps.

---

