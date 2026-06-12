---
title: "Select audio output Amarok in Gnome?"
date: 2009-05-03
forum: Multimedia Software
---

### Post by ernstblaauw on 2009-05-03
Hi,

I installed Amarok 2 in Jaunty, by running 'sudo aptitude install amarok'. This installs Amarok. However, there is no way to configure the audio output; inside Amarok, there is no option.

So, the only option is to install the package kdebase-workspace and run systemsettings. Inside the multimedia section, I could select pulse-audio (so the playback would not default to a digital output). Afterwards, I removed the kdebase-workspace package.

However, wouldn't it be better if Amarok could be configured or uses the default Gnome sound settings if it is started inside Gnome? The way I did it, is very clumsy.

[update]
I entered a bug report about this behavior on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/371360]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/371360")

---

