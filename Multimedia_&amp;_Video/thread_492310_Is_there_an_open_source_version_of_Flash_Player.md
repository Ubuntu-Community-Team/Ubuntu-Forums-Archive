---
title: "Is there an open source version of Flash Player?"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by xp_newbie on 2007-07-04
Is there an open source version of Flash Player?

I mean: any open source attempt to play flash based web pages (youtube etc.) - not necessarily 100% compatible with all the "bells & whistles", just something that plays most of the Flash Player material out there.

Somthing similar to Evince which can pretty impressively read Adobe Acrobat PDF files, without me having to install Adobe's Acrobat Reader.

Is there something like this for Macromedia (now Adobe) Flash Player?

Thanks,
Alex

---

### Post by moore.bryan on 2007-07-04
*i think you're looking for [gnash]("http://www.gnu.org/software/gnash/")...*

---

### Post by HuwSy on 2007-07-04
has anyone had gnash working with youtube and alike yet?

---

### Post by Gremlinzzz on 2007-07-04
sudo apt-get install flashplugin-nonfree
use the Guide Luke
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Gremlinzzz on 2007-07-04
Don't let the non-free throw ya it"s free.:D

---

### Post by jairtrejo on 2007-07-04
> **Gremlinzzz said:**
> Don't let the non-free throw ya it"s free.:D

Nah, free as in beer, not free as in freedom.

---

### Post by xp_newbie on 2007-07-04
> **moore.bryan said:**
> *i think you're looking for [gnash]("http://www.gnu.org/software/gnash/")...*

You are right! That is exactly the type of software I was looking for. Thank you!

[QUOTE=Gremlinzzz]*sudo apt-get install flashplugin-nonfree*[/QUOTE]

Sorry, but that is Adobe's proprietary (closed code) version. It is superior, I know, but it is also superior in terms of "spywareability" ;) - No thanks.

As for gnash, I searched for it in Synaptic Package Manager but couldn't find any mention of it. That was despite me enabling the Universe and Multiverse repositories. Where is it?

Thanks,
Alex

---

### Post by moore.bryan on 2007-07-04
> **xp_newbie said:**
> You are right! That is exactly the type of software I was looking for. Thank you!  As for gnash, I searched for it in Synaptic Package Manager but couldn't find any mention of it. That was despite me enabling the Universe and Multiverse repositories. Where is it?
Thanks,
Alex
*you're welcome... gnash is in the [universe repo]("http://packages.ubuntu.com/feisty/utils/gnash") ```
sudo aptitude install gnash
```*

---

### Post by xp_newbie on 2007-07-04
> **moore.bryan said:**
> *you're welcome... gnash is in the [universe repo]("http://packages.ubuntu.com/feisty/utils/gnash") ```
sudo aptitude install gnash
```*

Wow! what a quick reply. Thank you again.

This is strange - I am currently looking at my Synaptic with "Ubuntu 6.06 LTS (Binary) / Community maintained (Universe)" enabled, but I can't find any mention of gnash.

Could this be because I am using 6.06 (vs. 7.04 that you are using)?

Thanks,
Alex

---

### Post by xp_newbie on 2007-07-04
> **xp_newbie said:**
> This is strange - I am currently looking at my Synaptic with "Ubuntu 6.06 LTS (Binary) / Community maintained (Universe)" enabled, but I can't find any mention of gnash.

Could this be because I am using 6.06 (vs. 7.04 that you are using)?

OK - I just checked [http://packages.ubuntu.com/dapper/utils/]("http://packages.ubuntu.com/dapper/utils/") and there is no mention of the gnash package there. It looks like it has been introduced into Ubuntu only from version 7.x on...

Interestingly enough, I dis a search on 'flash' in Synaptic (on my Ubuntu 6.06) and found the following:
> 
**libflash-mozplugin**
GPL Flash (SWF) Library - Mozilla-compatible plugin

The GPL Flash library is a set of functions that can be used by
applications to play Flash movies. The core of the library is a
portable graphic renderer that can be used to add SWF support to an
application.

This package contains the Mozilla-compatible browser plugin, which
will work with many browsers (Mozilla, Firefox, Konqueror, etc).

Since it is GPL, it must be open-source, right?

Do you know anything about it?

Thanks,
Alex

---

### Post by moore.bryan on 2007-07-04
[I]i just checked things out and saw the dapper repos don't have gnash by default... you can enable the trevino repos, though; instructions are [here]("http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/").
the gpl flash library can cause problems on some sites; it's hit-or-miss.
[/I]

---

