---
title: "How do I associate realplayer and flash with firefox?"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by bradford72 on 2007-01-25
I downloaded and unpacked both flash (by adobe) and realplayer, as I need them both in order to view and listen to all the content which is a part of a web enhanced spanish course I am taking.  I know for sure that I've got realplayer working, because I can take a round-about way to hear the files I need (if I download them and then open them with rp) but don't know how to associate both programs with firefox so that everything works correctly...any help here:confused:

---

### Post by pay on 2007-01-25
Try Edit --> Preferences --> Content --> Files Types. (in firefox)

---

### Post by bradford72 on 2007-01-25
> **pay said:**
> Try Edit --> Preferences --> Content --> Files Types. (in firefox)
nope...nothing that says File Types anywhere in there (Except for associating what Firefox can automatically do with downloads...and I can't add anything to that list...)  Do you know where the library file is for Firefox....or some such beast...also the place where extensions and plug-ins go?  I think I might try that, but don't know where to look for the files...

---

### Post by dannyboy1121 on 2007-01-25
I'm surprised nobody has come back quicker to support you on this.

The issue appears to be with Firefox associating the realplayer plug in with Totem .. the way to fix this is by clearing that association.

You can find clear instructions on this link ..

If anything is unclear .. post back and I will explain.

[http://jordilin.wordpress.com/2006/10/30/howto-firefox-and-the-realplayer-plugin-in-ubuntu-edgy-eft/](http://jordilin.wordpress.com/2006/10/30/howto-firefox-and-the-realplayer-plugin-in-ubuntu-edgy-eft/)

---

### Post by bradford72 on 2007-01-25
> **dannyboy1121 said:**
> I'm surprised nobody has come back quicker to support you on this.

The issue appears to be with Firefox associating the realplayer plug in with Totem .. the way to fix this is by clearing that association.

You can find clear instructions on this link ..

If anything is unclear .. post back and I will explain.

[http://jordilin.wordpress.com/2006/10/30/howto-firefox-and-the-realplayer-plugin-in-ubuntu-edgy-eft/](http://jordilin.wordpress.com/2006/10/30/howto-firefox-and-the-realplayer-plugin-in-ubuntu-edgy-eft/)

right on...I appreciate...using dapper though and instructions are for edgy...
> October 30th, 2006 &#8212; jordilin                                             When you install RealPlayer in Ubuntu Edgy Eft, it will install not only the player but also the firefox plugins. There&#8217;s a problem, though. Firefox is preconfigured to play real audio streams with totem. To use the real player plugin you must remove the totem plugin responsible to play these real audio streams. Just go to the firefox plugins directory located on:
 /usr/lib/mozilla-firefox/plugins
 and remove
 libtotem-complex-plugin.so
 libtotem-complex-plugin.xpt
 type:
 sudo rm libtotem-complex-plugin.*
 and happy listening with realplayer plugin for Firefox 2in my /usr/lib/mozilla-firefox/plugins there only appears to be one file, and its libunixprintplugin.so....I did receive a libflashplayer.so with the download, and put it in there...I also got a flashplayer.xpt that I stuck in components...but alas, nothing works yet!  thanks for the help so far...at least I know where some stuff lives now....any more ideas?

---

### Post by benerivo on 2007-01-25
I would guess the most popular way for new ubuntu users to install flash these days is to do it via a package manager such as the synaptic package manager supplied with ubuntu (available through the system menu), or as I did it, through Automatix ([http://www.getautomatix.com/)](http://www.getautomatix.com/)), which should install it directly to your Firefox folders.

---

### Post by bradford72 on 2007-01-25
> **benerivo said:**
> I would guess the most popular way for new ubuntu users to install flash these days is to do it via a package manager such as the synaptic package manager supplied with ubuntu (available through the system menu), or as I did it, through Automatix ([http://www.getautomatix.com/)]("http://www.getautomatix.com/%29"), which should install it directly to your Firefox folders.
hmmm...automatix didn't wanna do it for me...synaptic either...I've managed to get it, and it works, just not with firefox (which is, of course, where I need it to work!)...I get this from the support page> 
 Version: RealPlayer 10.0, Helix Player MS1 or later 
   [LIST=1]
[*]Install RealPlayer 10.
[*]Copy nphelix.so to your Mozilla plugins directory and nphelix.xpt to your Mozilla components directory.
[*]Make sure a symbolic link to the realplay script is in your PATH.[/LIST]I am reinstalling dapper, just to try to undo everything and try again....but the question is how do I make a symbolic link to the realplay script in my PATH? Also, do I copy those files to my /mozilla/plugins and /mozilla/components directories, or my /mozilla-firefox/plugins and /mozilla-firefox/components directories....or even my /firefox/plugins and /firefox/components directories?!!  I have all three (er all 6)

---

### Post by perce on 2007-01-25
> **bradford72 said:**
> right on...I appreciate...using dapper though and instructions are for edgy...
in my /usr/lib/mozilla-firefox/plugins there only appears to be one file, and its libunixprintplugin.so....I did receive a libflashplayer.so with the download, and put it in there...I also got a flashplayer.xpt that I stuck in components...but alas, nothing works yet!  thanks for the help so far...at least I know where some stuff lives now....any more ideas?

The plug-ins are in the directory /usr/lib/mozilla/plugins. However removing a file by hands is not the way we are suppposed to solve the problem in a package-oriented system like Ubuntu. I've not found a clean way to solve it yet, so for multimedia content I'm using Konqueror which is more configurable (and can be run under gnome too). Does anybody has a better idea on how to modify the file association for Firefox?

---

