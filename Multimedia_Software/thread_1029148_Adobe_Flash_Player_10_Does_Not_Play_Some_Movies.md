---
title: "Adobe Flash Player 10 Does Not Play Some Movies"
date: 2009-01-03
forum: Multimedia Software
---

### Post by tokyo-joe on 2009-01-03
Adobe Flash Player doesn't play some movies on Youtube after I have upgrade flashplugin-nonfree to Ver.10. I could watch almost all kinds of youtube movies before upgrading.
What shall I do to watch Youtube movies properly?

[What I Cannot Wath]
[http://www.youtube.com/watch?v=skvgjpIDae8](http://www.youtube.com/watch?v=skvgjpIDae8)
 sorry, guys...not sure this is a politically correct example....

[What I Can Wath]
[http://www.youtube.com/watch?v=LqAPtpSAV3o](http://www.youtube.com/watch?v=LqAPtpSAV3o)

[Systems]
OS: Ubuntu 8.10 Intrepid
Browser: Mozilla Firefox 3.0.5

[Relevant plugins(all installed)]
adobe-flashplugin   ver. 10.0.15.3-1intrepid2
flashplugin-nonfree  ver. 10.0.15.3ubuntu1~intrepid1

[What I have done]
-apt-get remove flashplugin-nonfree
-apt-get instal flashplugin-nonfree
-Copied libflashplayer.so to:
  + /usr/lib/firefox/plugins
  +~/.mozilla/plugins

Thanks in advance.

---

### Post by tokyo-joe on 2009-01-03
Additional informtion.
Here is what I got from "about:plugins" on Firefox (exerpt showing relevant items only).

-------------------------------------------------------------------------
Shockwave Flash

    File: libflashplayer.so
    Shockwave Flash 10.0 r15

MIME-type     Description     Extension     Validity
application/x-shockwave-flash     Shockwave Flash     swf     Valid
application/futuresplash     FutureSplash Player     spl     Valid

Shockwave Flash

    File: libswfdecmozilla.so
    Shockwave Flash 9.0 r999


MIME-type     Description     Extension     Validity
application/x-shockwave-flash     Adobe Flash movie     swf     Valid
application/futuresplash     FutureSplash movie     spl     Valid

Shockwave Flash

    File: libgnashplugin.so
    Shockwave Flash 9.0 r999. Gnash 0.8.4, the GNU SWF Player. Copyright © 2006, 2007, 2008 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 9.0 r999.

MIME-type     Description     Extension     Validity
application/x-shockwave-flash     Shockwave Flash     swf     Valid
-------------------------------------------------------------------------

---

### Post by halovivek on 2009-01-03
you can try to solve using this thread.
[http://ubuntuforums.org/showthread.php?t=1024873](http://ubuntuforums.org/showthread.php?t=1024873)
just post the result after doing.

---

### Post by ajgreeny on 2009-01-03
You appear to have several different versions of flash and gnash installed and I think that may be your problem, or at least part of it.

I am running 8.04.1  hardy with gnome desktop and have only the adobe-flashplugin from the partner repos installed using synaptic.  Everything is working extremely well on my machine, including your non-pc video that you say you can't see.  Try enabling the partner repos in intrepid, if they are available for that version, uninstall the flashplugin-nonfree and gnash, install the adobe-flashplugin, and see if things are any better.

---

### Post by tokyo-joe on 2009-01-03
> **halovivek said:**
> you can try to solve using this thread.
[http://ubuntuforums.org/showthread.php?t=1024873](http://ubuntuforums.org/showthread.php?t=1024873)
just post the result after doing.

I have installed ubuntu-restricted-extras, but nothing has changed.

---

### Post by tokyo-joe on 2009-01-03
> **ajgreeny said:**
> You appear to have several different versions of flash and gnash installed and I think that may be your problem, or at least part of it.

Try enabling the partner repos in intrepid, if they are available for that version, uninstall the flashplugin-nonfree and gnash, install the adobe-flashplugin, and see if things are any better.

I made it!!

Here are what I have done.
-Uninstalled all the items including "flash" and "gnash" in their names.
-Uninstalled ubuntu-restricted-extras (it had been installed during the try and error process this time).
-Installed ubuntu-restriced-extras.

That's it.
It seems many flash and gnash components were competing each other, as you mentioned.

Thank you very much for your supports, guys!!

---

