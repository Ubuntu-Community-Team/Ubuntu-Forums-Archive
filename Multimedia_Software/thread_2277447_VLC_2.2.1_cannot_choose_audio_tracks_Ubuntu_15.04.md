---
title: "VLC 2.2.1 cannot choose audio tracks Ubuntu 15.04"
date: 2015-05-09
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2015-05-09
Hi, I have vlc 2.2.1 on Ubuntu 15.04 64 bit and I notice that I can no longer choose different audio tracks (test file is MKV on another drive) The menu entry for Audio > Audio track is greyed out.  However I am able to choose from two different audio tracks using Smplayer with mpv backend and plain mpv (on Ubuntu15.04, mpv self compiled) and  also same version of vlc (2.2.1) on Trusty (self compiled against ffmpeg 2.6.2 ).

I have tried compiling vlc 2.2.1  myself and installing from [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1/+index?field.series_filter=vivid](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1/+index?field.series_filter=vivid) ( I upgraded ffmpeg from same ppa and compiled vlc and mpv against it) In both cases I cannot choose audio tracks.


I am wondering what may be missing, thanks.

---

### Post by mc4man on 2015-05-09
Maybe related to this thread - [http://ubuntuforums.org/showthread.php?t=2276869](http://ubuntuforums.org/showthread.php?t=2276869)
to test open vlc as such & see if ok
```
export QT_X11_NO_NATIVE_MENUBAR=1 && vlc
```

[https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059](https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059)

---

### Post by monkeybrain20122 on 2015-05-09
> **mc4man said:**
> Maybe related to this thread - [http://ubuntuforums.org/showthread.php?t=2276869](http://ubuntuforums.org/showthread.php?t=2276869)
to test open vlc as such & see if ok
```
export QT_X11_NO_NATIVE_MENUBAR=1 && vlc
```

[https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059](https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059)

Thanks, this workaround works in that the menu is now available but the colour of the dropdown has changed to black characters over a white background instead of white on black.

---

### Post by mc4man on 2015-05-09
> **monkeybrain20122 said:**
> Thanks, this workaround works in that the menu is now available but the colour of the dropdown has changed to black characters over a white background instead of white on black.
Yeah - that's a theme issue unrelated to this
From linked bug report I'd expect this to be fixed at some early point in 15.10, whether applied back on 15.04 is 50:50
(one of the 'advantages' to Ubuntu with these 9 month 'releases' is it's quite easy/acceptable to let a lot of bugs slide in the release they first occurred in.

Far ot - 
here I do run vlc with the menus in the window & have adjusted in ambiance to get dark menu drop downs. Generally that (change) is without issue though could affect something else somewhere

---

### Post by mc4man on 2015-05-09
If you wish to try - 
dl attached, extract
Then in /usr/share/themes/Ambiance/gtk-2.0 mv gtkrc to a .old or .bak 
Add the extracted gtkrc in it's place

Edit: that ^ will change your FF address bar dropdown to a dark with light text...

---

### Post by monkeybrain20122 on 2015-05-09
> **mc4man said:**
> If you wish to try - 
dl attached, extract
Then in /usr/share/themes/Ambiance/gtk-2.0 mv gtkrc to a .old or .bak 
Add the extracted gtkrc in it's place

Edit: that ^ will change your FF address bar dropdown to a dark with light text...

Thanks, I will try this when I am on 15.04.

> Yeah - that's a theme issue unrelated to this
From linked bug report I'd expect this to be fixed at some early point in 15.10, whether applied back on 15.04 is 50:50


 There is a patch in [https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059](https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059) I suppose it is for indicator-appmenu? I wonder how difficult it would be to compile it from source? If it is not too much hassles I would want to give it a try. I know about the hazards of interim releases, but 15.04 just seems so nice and smooth here.

---

### Post by mc4man on 2015-05-09
> **monkeybrain20122 said:**
> Thanks, I will try this when I am on 15.04.



 There is a patch in [https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059](https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059) I suppose it is for indicator-appmenu? I wonder how difficult it would be to compile it from source? If it is not too much hassles I would want to give it a try. I know about the hazards of interim releases, but 15.04 just seems so nice and smooth here.
Not too sure that the patch there will be the best solution. If inclined to try I'd package build using the current source 
This way easier to revert

As far as the attached rc file, I use it in 14.04 to add dark menu drops for gtk2 apps
(Only difference between the attached & here is I  change the bg & bg selected colors, for the one I attached I edited those back to the default colors

---

### Post by monkeybrain20122 on 2015-05-09
Hi, by giving it a try I meant to compile it myself. But if you are willing to package it I will test it for sure, you are the pro.

---

### Post by mc4man on 2015-05-09
> **monkeybrain20122 said:**
> Hi, by giving it a try I meant to compile it myself. But if you are willing to package it I will test it for sure, you are the pro.
It (the patch) seems to work but worth seeing if anything breaks ect.
That's why I thought you should package build/install to keep as is in Ubuntu
Really simple - in ex. below will keep at same package version so to revert just update back in synaptic

```

mkdir app-ind && cd app-ind
```
```
sudo apt-get install devscripts
```
```
sudo apt-get build-dep indicator-appmenu
```
```
wget https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059/+attachment/4387983/+files/indicator-appmenu.c.diff
```
```
apt-get source indicator-appmenu
```
```
cd ./indicator-appmenu-15.02.0+15.04.20150302
```
```
patch -Np0  -i  ../indicator-appmenu.c.diff
```
```
debuild -us -uc
```
Then install the resultant .deb with dpkg

---

### Post by monkeybrain20122 on 2015-05-10
Hi, Thanks for the help! I have compiled and reinstalled indicator-appmenu, after reboot vlc is working fine now. I haven't noticed any side effect on other applications so far. I am going to pin the package and mark this thread as solved.

P.S. On an unrelated topic, I have filed a bug against unity for the dash not recording activities for certain applications. It is probably not a very professional bug report, it would be helpful if you have any insight to add to it. [https://bugs.launchpad.net/unity/+bug/1453356](https://bugs.launchpad.net/unity/+bug/1453356) Thanks again!

Edited: I have created a post in the "known bugs and workaround" sticky in case someone else experiences the same problem and looks for solutions. [http://ubuntuforums.org/showthread.php?t=2276023&p=13282393#post13282393](http://ubuntuforums.org/showthread.php?t=2276023&p=13282393#post13282393)

---

### Post by mc4man on 2015-05-10
re: bug, trying to get a handle on, do these fall under?

Any video opened from Dash > Video lens will not show up in Dash > Files & Folders lens if opened with any player other than Totem? (ie. the default for that file type has been changed

If it doesn't show up to begin with, then in cases where it already was there somewhere in the list,  it won't be moved to top..

It may be easier to see that by starting with a fresh list, one way is to delete ~/.local/share/zeitgeist/activity.sqlite & log out/in

part 2:
With a cleared nautilus > Recent
Do videos opened from Dash > Videos with any other player than totem show up in nautilus > Recent ?

---

### Post by monkeybrain20122 on 2015-05-13
> **mc4man said:**
> re: bug, trying to get a handle on, do these fall under?

Any video opened from Dash > Video lens will not show up in Dash > Files & Folders lens if opened with any player other than Totem? (ie. the default for that file type has been changed

If it doesn't show up to begin with, then in cases where it already was there somewhere in the list,  it won't be moved to top..

It may be easier to see that by starting with a fresh list, one way is to delete ~/.local/share/zeitgeist/activity.sqlite & log out/in

part 2:
With a cleared nautilus > Recent
Do videos opened from Dash > Videos with any other player than totem show up in nautilus > Recent ?

I think I kind of know why, for the action of the application to be recorded it has to make a unity scope. For example, if you use a music player which doesn't have a unity scope, say replacing guayadeque (which is broken in 15.04) with guayadeque-svn then music files don't show up in the music lenses.

---

