---
title: "Web site broken by upgrade"
date: 2011-01-01
forum: Multimedia Software
---

### Post by VanillaMozilla on 2011-01-01
I upgraded directly from 10.04 (Lucid), and now have TWO problems.  I thought I was upgrading to 10.10.  Surprise!  I now have 11.04, and the following Web site is broken:

[http://kdhx.fm/archives/archive_gen.php?show=musicfromthehills](http://kdhx.fm/archives/archive_gen.php?show=musicfromthehills)

There are two "Play buttons just above two dates.  Neither button is now visible, and neither works.  So I have two problems:

(1) How do I get that to play?  What is the format/requirement?

(2) How the heck did I get directly to Natty Narwhal, and how do I get back?

---

### Post by CharlesA on 2011-01-01
It's likely that you upgraded to 10.10. Is 11.04 listed in "About me" ?

Also, install restricted-extras and see if that gets those working.

---

### Post by VanillaMozilla on 2011-01-01
About Me... is completely blank.  But System > About Ubuntu definitely shows 11.04, Natty Narwhal.  On the other hand, Firefox and Chromium both show 10.10.  Go figure.

Is this a known bug?  Has it been reported?

OK, so that solves one problem, probably.  Now for the Web site problem.  Outlines of the buttons appear briefly but then disappear.  It probably requires Flash(?).  I have

flashplugin-nonfree
flashplugin-installer
gnash
gnash-common
browser-plugin-gnash
swflash-mozilla   EDIT: no, that's swfdec-mozilla

and Firefox Plugins shows Gnash 0.8.8.

Any ideas?  Does it work for you?

---

### Post by wilee-nilee on 2011-01-01
Look in system monitor system tab.

---

### Post by VanillaMozilla on 2011-01-01
Yes, it's 10.10.

Restricted-extras doesn't do it.

---

### Post by wilee-nilee on 2011-01-01
> **VanillaMozilla said:**
> Yes, it's 10.10.

Restricted-extras doesn't do it.

Have you looked in menu-system-admin-additional drivers it may be a missing graphics driver.

I think that link is using flash so the restricted extras should have loaded the adobe flash, maybe not though if you have gnash already in.

---

### Post by ajgreeny on 2011-01-01
> Now for the Web site problem.  Outlines of the buttons appear briefly  but then disappear.  It probably requires Flash(?).  I have

flashplugin-nonfree
flashplugin-installer
gnash
gnash-common
browser-plugin-gnash
swflash-mozilla

and Firefox Plugins shows Gnash 0.8.8.Do you mean you have all those installed, or just that they are available in Software-Centre?

Whatever the answer to that, you should only ever have one flash package installed.  I would suggest you uninstall any **gnash** packages you have installed, probably also **swflash-mozilla **(do you mean swfdec-mozilla?) , if you have it, and then install **flashplugin-installer**, which will get the Adobe package direct from Adobe.

---

### Post by VanillaMozilla on 2011-01-01
Bingo!  Removed browser-plugin-gnash.  Problem solved.

One other problem with Flash, perhaps you can help.  I'm running Lucid, and also not able to play that Web page (no sound from Web page).  I don't have Gnash installed, but Firefox about:plugins (that's supposed to be about colon plugins) shows TWO versions of Flash, and I can't seem to get rid of the old one.

I have 10.1 r53 and 10.1 r102.  Both are supposed to be in file libflashplayer.so, but that file does not exist in the file system.  When I uninstalled
flashplug-nonfree and
flashplug-installer,

I still had Flash, and it functioned!  I reinstalled and I still have both versions.  Any ideas?

---

### Post by ajgreeny on 2011-01-01
In terminal run ```
sudo updatedb
```then
```
locate libflashplayer.so
```That will tell you where that plugin lib file is (or are).

EDIT:
Surely the about:plugins page of FF shows you the path to the lib files, doesn't it?  It does on my system.

---

### Post by VanillaMozilla on 2011-01-02
OK, it was in a hidden directory.  No wonder you use the command line for this.

Uninstalled flashplayer-nonfree, etc., deleted libflashplayer.so, and reinstalled.  Both problems solved.  Now I have only one version of Flash, and the Web site works.  This was a remnant from when it was difficult to get Flash installed.  Thanks very much.

[quote="ajgreeny"]Surely the about:plugins page of FF shows you the path to the lib files, doesn't it? It does on my system.[/quote]No.


Note to self:  Yet another 'Find Files' bug?  'libflashplayer.so' not found even when selecting hidden-files option?  Double check this.

---

### Post by VanillaMozilla on 2011-01-03
> **VanillaMozilla said:**
> Note to self:  Yet another 'Find Files' bug?  'libflashplayer.so' not found even when selecting hidden-files option?  Double check this.
Yes.  Another bug, I'm pretty sure.  I vaguely remember seeing a bug report, but I can't find it.  I've opened a discussion [here.]("https://answers.launchpad.net/ubuntu/+question/140030")

"Search for Files..." seems pretty unreliable.  I think they ought to either fix it or oust it from the desktop.

EDIT:  You have to press the "Add" button.  Probably not a bug.  Just a little gotcha.

---

