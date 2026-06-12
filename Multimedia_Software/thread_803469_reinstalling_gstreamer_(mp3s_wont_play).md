---
title: "reinstalling gstreamer (mp3s wont play)"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Demoreel on 2008-05-22
My problem was that every program I was using would freeze (amarok, rhythmbox, noatun) when I would try to play my mp3s. Now I'm fairly new to linux (I'm using the latest Ubuntu) but realitively competent or so I thought. I read somewhere that reinstalling gstreamer might stop the freezing. I went into SPM and removed everything which had gstreamer in the title....apparently bad choice. I thought I would just be able to find them and reinstall them. this is the error I'm coming up with
---------------------
gstreamer0.10-plugins-good:

Package gstreamer0.10-plugins-good has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


---------------------- 

any thoughts? once I install gstreamer properly and if it doesn't work, any thoughts on how to stop these players from freezing? id rather not reinstall ubuntu

---

### Post by Demoreel on 2008-05-22
and to add to that............

whenever i try and enter an address into firefox, i get this message:

--------------------------------ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias(b9board.com)
7:getEngineByAlias(b9board.com)
8:getShortcutOrURI(b9board.com,[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(false)
15:onKeyPress([object KeyboardEvent])
16:onxblkeypress([object KeyboardEvent])
----------------------------

i think im screwed

---

### Post by cor2y on 2008-05-22
you need the correct gstreamer plugin.
Here are all the gstreamer plugins for media playback, make sure to enable the restricted, universe and multiverse repos, note these plugins do not help with encrypted dvd playback but for multimedia files like mp3 etc they do.
gstreamer0.10-ffmpeg (ffmpeg support)
gstreamer0.10-fluendo-mp3 (mp3 support/playback)
gstreamer0.10-pitfdll (to use the w32codec pack if installed)
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

Optional Plugins
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-fluendo-mpegmux

---

### Post by Demoreel on 2008-05-22
thank you...........


but how do I get those? go to the site and download? terminal?

---

### Post by cor2y on 2008-05-22
either launch synaptic and search for all those listed plugins or via the terminal```
sudo apt-get install gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
``` remember to have the restricted, universe and multiverse repos enabled otherwise synaptic won't be able to get all of them.

---

### Post by Demoreel on 2008-05-22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-fluendo-mp3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-fluendo-mp3 has no installation candidate



seems to be the same error when trying to install the 'good' in SPM

---

### Post by cor2y on 2008-05-22
what version of ubuntu is this and did you enable all the repos i said to?
System->Administration->Software Sources

---

### Post by staticsage on 2008-05-26
I have the same problem. Any program I open an mp3 in will freeze randomly. Any ideas? I'm on a Dell Precision M60 laptop with an external Philips PSC805 Aurillium sound card. I have ubuntu-restricted-extras installed as well.

---

### Post by Mecasickle on 2010-03-21
How do I add the repository?

---

### Post by garvinrick4 on 2010-03-22
> **Mecasickle said:**
> How do I add the repository?

Hey Mecasickle just open Software sources under System/Admin
and under Ubuntu Software tab click first 4 box's no need for
source code and hit close and they will reload for you.

---

