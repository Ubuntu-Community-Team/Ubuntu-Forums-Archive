---
title: "El Classico: No sound in flash... Even after reinstall."
date: 2010-07-26
forum: Multimedia Software
---

### Post by qetuR on 2010-07-26
The topic that creeps people out. Maybe I'm screwed, but lets hope not.

I'm gonna give you as much info as I know is needed.

Acer TimeLineX 3820TG. ATI HD 5850 and Realtek Semiconductor Corp. soundcard. Using Ubuntu 10.04 64 bit.
 When I first installed Ubuntu, the soundcard did not work properly i.e. no sound from jack or the mic didnt work either, I went to this page: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810) updated the ALSA as stated in the topic.

After this, everything looked good. Everything worked except the flash-sound. 

I have:

* Removed flash, firefox and chrome. 
* Manualy removed the flashplugin.so, boath in $HOME and in /etc/<something>
* I tried to use this guide: [http://ubuntuforums.org/showthread.php?t=204022](http://ubuntuforums.org/showthread.php?t=204022), but I think I ruined it moore. (Creates some symbolic links)
* Re-installed flash, firefox and chrome. I have tried FLASH-AID plugin in Firefox, I have tried donwloading flash from synaptic.
* Tried to figure somthing out on IRC, without success.

Now what, forum? Please help me...

---

### Post by lidex on 2010-07-27
[http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

Oh yeah, and if you managed to bork your flash install, try this extension:
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Yellow Pasque on 2010-07-27
You should probably undo that symbolic link stuff (rm the stuff you created).

If you compiled vanilla upstream ALSA, you need to configure ALSA apps to use pulseaudio: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by qetuR on 2010-07-27
> **lidex said:**
> [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

Oh yeah, and if you managed to bork your flash install, try this extension:
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

THANKS ALOT! Started working directly after trying your first link. Awesome! (I have already tried FLASH-AID, as stated in topic) :) But thanks anyway.

Edit: A bit quick there. The sound works, as it should but now I'm back to the original problem, not be able to listen through my jack out or mic in on the laptop. That kinda sucks... :/ Since I'm begining playing HoN alot lately. :P

---

