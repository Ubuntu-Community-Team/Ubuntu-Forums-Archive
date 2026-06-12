---
title: "Cannot configure behaviour of totem plugin"
date: 2011-05-08
forum: Multimedia Software
---

### Post by aussieguy32 on 2011-05-08
Hi, I am using the following:

ubuntu 10.04 LTS
firefox 3.6.17
totem 2.30.2

As it stands, if I play an mp3 file via the web, firefox will launch totem which will in turn launch goom.

Looks nice, but I would like to turn off the Visualisation which takes up the entire CPU. 

I try under firefox preferences, Edit->Preferences->Plugins, there isn't anything there I can change.

I try under firefox Utils->Plugins and there isn't anything there I can change.

I try using gconf-editor, there are different settings  there I can play with like:

Under /apps/totem/visual it has the setting "GOOM: what a GOOM!", I try and delete it, it doesn't change anything.

Still with gconf-editor I try changing /apps/totem/plugins/screensaver turning the setting of "active" to uncheck. No change, goom still comes up with the fantastic graphics I just don't want.

Still with gconf-editor I try changing /system/gstreamer/0.10/default/visualization from "goom" to blank. Again, no change.

If I look under the process list while totem is running goom I see the following:

/usr/lib/totem/totem-plugin-viewer --plugin-type cone --user-agent Mozilla/5.0 (X11; U; Linux x86_64; fr; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.04 (lucid) Firefox/3.6.17 --referrer [http://blah](http://blah) blah blah blah.mp3 --mimetype audio/mpeg

There doesn't seem to be anywhere I can change the command line which is being passed to totem to make it behave differently and turn off the goom visualizations.

I have tried starting up totem as a stand alone application, there I go into Edit->Preferences->Display and make sure the choice for "Show visual effects when an audio file is played" is unticked. That gives me the results I am after for totem as a stand alone application, which is no Visualizations whem audio file is being  played BUT It makes no change for totem running as a plugin in firefox.

Anyone have any ideas ? I would love some help.

---

### Post by aussieguy32 on 2011-05-08
Looks like others have had this problems as well:

[http://ubuntuforums.org/showthread.php?t=1065175](http://ubuntuforums.org/showthread.php?t=1065175)

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/273490](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/273490)

---

