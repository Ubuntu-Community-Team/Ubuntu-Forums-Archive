---
title: "flash/youtube on lucid lynx"
date: 2010-05-26
forum: Multimedia Software
---

### Post by iochinome on 2010-05-26
hello,

I just installed lucid lynx as an upgrade; on the previous distribution, I had no problem playing youtube videos on either firefox or mozilla, i.e. flash was installed and running happily. then, with lucid lynx, it stopped working for some odd reason- the youtube videos initially said that i did not have the right plugin, which i tried to install... (and then it failed because it said that i already had it) 

now, youtube videos just say 'an error occured' and dont play, and all other flash things fail.
does anybody have any ideas for how to fix this??

thanks!

---

### Post by gator2802 on 2010-05-26
> **iochinome said:**
> hello,
 
I just installed lucid lynx as an upgrade; on the previous distribution, I had no problem playing youtube videos on either firefox or mozilla, i.e. flash was installed and running happily. then, with lucid lynx, it stopped working for some odd reason- the youtube videos initially said that i did not have the right plugin, which i tried to install... (and then it failed because it said that i already had it) 
 
now, youtube videos just say 'an error occured' and dont play, and all other flash things fail.
does anybody have any ideas for how to fix this??
 
thanks!
 Same thing happened to me the other day as well.  The easiest solution would be to use synaptic to uninstall and then reinstall the firefox plugin.  I had a version conflict after the upgrade.

---

### Post by lovinglinux on 2010-05-26
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by iochinome on 2010-05-26
> **gator2802 said:**
> Same thing happened to me the other day as well.  The easiest solution would be to use synaptic to uninstall and then reinstall the firefox plugin.  I had a version conflict after the upgrade.

do you know the name of the package to uninstall? thanks!

(by the way, this doesnt work on chrome either...)

---

### Post by lovinglinux on 2010-05-26
> **iochinome said:**
> do you know the name of the package to uninstall? thanks!

(by the way, this doesnt work on chrome either...)

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Automat2 on 2010-05-27
> **lovinglinux said:**
> Install [FLASH-AID]("http://flash-aid-extension.blogspot.com") extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR=Sienna]**Flash Optimization**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html") section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

Thanks lovinglinux. I've tried Flash-Aid and so far it seems to be working fine.

---

