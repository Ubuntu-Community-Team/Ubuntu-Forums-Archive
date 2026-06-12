---
title: "Current list of keyboard commands?"
date: 2009-10-13
forum: Mythbuntu
---

### Post by bcg30506 on 2009-10-13
I'm revamping some keys on our remote control and was trying to find a current list of mythfrontend keyboard commands.  The doc on their web site is old.  For instance, there is no mention of Ctrl+W to cycle thru aspect ratios at mythtv.org but this does work.

Anyone know where I can find a complete and current listing of all keyboard commands and frontend functionality so I can best map features we'd like to our available remote buttons?

---

### Post by larsolav on 2009-10-13
is this what you are looking for?
[http://www.mythtv.org/docs/mythtv-HOWTO-11.html](http://www.mythtv.org/docs/mythtv-HOWTO-11.html)
> W cycle through zoom and fill modes: 4:3 aspect ratio, 16:9, 4:3 Zoom  (like Pan and Scan), 16:9 Zoom, and 16:9 Stretch (eliminates black  sidebars in TV signal) 

[http://www.keyxl.com/aaa3626/343/MythTV-keyboard-shortcuts.htm](http://www.keyxl.com/aaa3626/343/MythTV-keyboard-shortcuts.htm)

---

### Post by chipppy on 2009-10-13
Good morning

Try 'edit keys' within your box then you will know exactly which keys do what within your distro.

Cheers
chipppy

---

### Post by bcg30506 on 2009-10-13
No.  That is the page that is old and missing new features and keys.  W now cycles through the picture fill modes (Off, Half, Full, Stretch) while Ctrl-W cycles through the aspect ratio overrides (Off, 4:3, 16:9, 14:9).

I've not yet found a page describing this change which got me wondering how many other updated or new features are available that we do not know about and might want to map to the remote control?

---

### Post by bcg30506 on 2009-10-13
> **chipppy said:**
> Good morning

Try 'edit keys' within your box then you will know exactly which keys do what within your distro.

Cheers
chipppy

This is a good start. Thanks!  However, it is not very convenient nor descriptive to get a complete list of functions and keys that can be mapped to a remote.  It is all there with some digging, but I do not know what have of the descriptions even mean.  A document describing this and showing the default key maps would be great - like on the mythtv.org documentation site - just updated to be current and complete.

---

### Post by jensk on 2009-10-13
You can find the current key bidings for your specific Myth setup in mythweb - tools - MythTv - keybindings. 

All the keys that is set is recorded there in list form and can be edited.
/jensk

---

### Post by bcg30506 on 2009-10-13
> **jensk said:**
> You can find the current key bidings for your specific Myth setup in mythweb - tools - MythTv - keybindings. 

All the keys that is set is recorded there in list form and can be edited.
/jensk

This helps having them in one scrollable and searchable page, but it still does not replace documentation in natural language.  Not being a coder of mythtv and having internal knowledge of its workings, it is virtually impossible to tell what some of these things are, like Menu Red, Green, Yellow, and Blue, and Menu Text.  I can make educated guesses for most, but still, it'd be nice to have the official documentation up to date by someone who understands it.

---

### Post by Neon Dusk on 2009-10-13
How about [http://svn.mythtv.org/trac/browser/trunk/mythtv/keys.txt](http://svn.mythtv.org/trac/browser/trunk/mythtv/keys.txt)

---

### Post by nickrout on 2009-10-13
> **Neon Dusk said:**
> How about [http://svn.mythtv.org/trac/browser/trunk/mythtv/keys.txt](http://svn.mythtv.org/trac/browser/trunk/mythtv/keys.txt)

Which of course is the trunk version, which may be different to what you have installed.

But I have not yet found a distro that doesn't install keys.txt, which should be the version current at your own version. In fact there should be multiple copies if you have all the myth packages installed:

[http://packages.ubuntu.com/search?mode=exactfilename&suite=jaunty&section=all&arch=any&searchon=contents&keywords=keys.txt.gz](http://packages.ubuntu.com/search?mode=exactfilename&suite=jaunty&section=all&arch=any&searchon=contents&keywords=keys.txt.gz)

By the way the change you refer to seems to have happened 2 years ago:

[http://svn.mythtv.org/trac/changeset/14477/trunk/mythtv/keys.txt](http://svn.mythtv.org/trac/changeset/14477/trunk/mythtv/keys.txt)

Of course if this page [http://www.mythtv.org/wiki/Keybindings](http://www.mythtv.org/wiki/Keybindings) is wrong, you could correct it. Thats what a wiki is all about. In fact thats what open source is all about, people contributing, so (without wanting to sound rude) DO IT!

---

### Post by bcg30506 on 2009-10-13
> **Neon Dusk said:**
> How about [http://svn.mythtv.org/trac/browser/trunk/mythtv/keys.txt](http://svn.mythtv.org/trac/browser/trunk/mythtv/keys.txt)

This seems correct.  Thanks!

---

### Post by bcg30506 on 2009-10-13
> **nickrout said:**
> Which of course is the trunk version, which may be different to what you have installed.

But I have not yet found a distro that doesn't install keys.txt, which should be the version current at your own version. In fact there should be multiple copies if you have all the myth packages installed:

[http://packages.ubuntu.com/search?mode=exactfilename&suite=jaunty&section=all&arch=any&searchon=contents&keywords=keys.txt.gz](http://packages.ubuntu.com/search?mode=exactfilename&suite=jaunty&section=all&arch=any&searchon=contents&keywords=keys.txt.gz)

By the way the change you refer to seems to have happened 2 years ago:

[http://svn.mythtv.org/trac/changeset/14477/trunk/mythtv/keys.txt](http://svn.mythtv.org/trac/changeset/14477/trunk/mythtv/keys.txt)

Of course if this page [http://www.mythtv.org/wiki/Keybindings](http://www.mythtv.org/wiki/Keybindings) is wrong, you could correct it. Thats what a wiki is all about. In fact thats what open source is all about, people contributing, so (without wanting to sound rude) DO IT!

I understand and have contributed some things already in open source land.  However in this case, I did not know what the corrections should be which is what started my quest.  I knew from another forum message about Ctrl-W but that was it.  I was not aware of keys.txt being installed with mythtv.  I'll search for it on my system as well.  Thanks for the tip and don't worry about sounding rude.  I'm a big boy with thick skin. :guitar:

---

### Post by johnnybirdman on 2009-10-29
> **bcg30506 said:**
> This seems correct.  Thanks!

I understand that 'W' in mythvideo will do a metadata search without having to go through 'M' menu.  I read this somewhere today on a search for a guide to the keyboard settings/shortcuts.  However, that is not on the list linked, i wonder how up to date it is.  And, it should be noted I'm talking about 9.10.  I'll try it later.
J.

---

