---
title: "BBC iPlayer flash full screen?"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by v4169sgr on 2007-12-15
Hello,

I am running Dapper [6.06], and accessing [http://www.bbc.co.uk/iplayer](http://www.bbc.co.uk/iplayer).

What do I need to do to run the flash window ful screen? Do I need to upgrade to Gutsy [7.10]?

TIA!

---

### Post by amias on 2007-12-16
its the same in gutsy , you could manually update with the tar.gz version or just wait for an ubuntu package.

---

### Post by v4169sgr on 2007-12-16
Thanks for the reply. After reading this:

[http://ubuntuforums.org/showpost.php?p=3916264&postcount=6](http://ubuntuforums.org/showpost.php?p=3916264&postcount=6)

and this:

[http://ubuntuforums.org/showthread.php?t=631310](http://ubuntuforums.org/showthread.php?t=631310)

and in the knowledge that I have flash dependencies elsewhere i.e. unhappy users if the flash plugin does not work, then I have decided to wait until my scheduled 8.04 upgrade in Summer '08, where everything should hopefully more or less fall into place, in a supportable way.

v 115 is I believe required for the full screen support I was looking for.

---

### Post by Mateo on 2007-12-16
does iPlayer do true full screen or just "big browser" full-screen?  I wasn't aware that flash could do true full screen yet.

---

### Post by v4169sgr on 2007-12-17
This article

[http://www.adobe.com/devnet/flashplayer/articles/full_screen_mode.html](http://www.adobe.com/devnet/flashplayer/articles/full_screen_mode.html)

would appear to suggest 'true' full screen, but I haven't tried it myself.

---

### Post by gryall on 2007-12-24
It is True full Screen. I have just got this to work by using the tar.gz provided by adobe.

---

### Post by chezzo on 2008-03-13
It may be because of Compiz, try [http://ubuntuforums.org/showthread.php?t=600795](http://ubuntuforums.org/showthread.php?t=600795)

> If not present install "Advanced Desktop Effect settings" , then uncheck "Unredirect fullscreen windows" in "General Options" and "Support legacy fullscreen" in the plugin "Workaround".
For me has been a definitive solution.

it worked for me!

---

### Post by p-w on 2008-05-21
Thanks chezzo, setting those options for compiz solved the problem for me on Hardy (8.04).  It is a shame the Advanced Desktop Effects Settings (package compizconfig-settings-manager) is not installed by default.

---

