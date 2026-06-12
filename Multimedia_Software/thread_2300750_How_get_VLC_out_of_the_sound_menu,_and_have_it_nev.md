---
title: "How get VLC out of the sound menu, and have it never ever ever come back"
date: 2015-10-28
forum: Multimedia Software
---

### Post by nickTaylor1181 on 2015-10-28
Hi all.

How do I get VLC out of the sound menu?... forever?

There a lots of answers to this when I google it, but they don't work...  as soon as you open VLC, it comes back again.

I find it incredibly irritating - it's the sort of spammy thing that microsoft always tries to do - and I've been trying to get rid of it for years now.


But you know... enough about me. 

Does anyone know how to get rid of it, so it never ever comes back?

Cheers


Nick.

---

### Post by shantiq on 2015-10-28
[COLOR=#000000][INDENT]**PS EDIT **then it dawns on me that you want to KEEP vlc and remove it from sound menu only ... anyway will leave the info here for reference[/INDENT]

====



[/COLOR]
ok Nick i would surmise if you run
```
sudo updatedb && locate vlc
``` in terminal
which will update your database and seek every even tiny file containing the word vlc that you will then find ALL matters vlc still on your system

I take it you have already run ```
sudo apt-get remove --purge vlc
```

so now to remove ALL those files you have found in the locate search   EVERYTHING
then surely the sound will not pick on any vlc if there is none left


or more thorough MAKE SURE no file is up for removal that you want kept

on my setup if i run ```
sudo apt-get remove --purge [COLOR=#800000]vlc*[/COLOR]
```   it will remove all of those

```
sudo apt-get remove --purge vlc*Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libvlc-dev' for regex 'vlc*'
Note, selecting 'python-vlc' for regex 'vlc*'
Note, selecting 'ttf-vlgothic' for regex 'vlc*'
Note, selecting 'libgavl-ocaml' for regex 'vlc*'
Note, selecting 'libgavl1-dbg' for regex 'vlc*'
Note, selecting 'avl' for regex 'vlc*'
Note, selecting 'vlc-plugin-notify' for regex 'vlc*'
Note, selecting 'vlock' for regex 'vlc*'
Note, selecting 'libvlc0-dev' for regex 'vlc*'
Note, selecting 'vlc-plugin-fluidsynth' for regex 'vlc*'
Note, selecting 'fuse-posixovl' for regex 'vlc*'
Note, selecting 'libvlccore7' for regex 'vlc*'
Note, selecting 'libvlccore8' for regex 'vlc*'
Note, selecting 'vlc-nox' for regex 'vlc*'
Note, selecting 'browser-plugin-vlc' for regex 'vlc*'
Note, selecting 'fonts-vlgothic' for regex 'vlc*'
Note, selecting 'vlc-plugin-samba' for regex 'vlc*'
Note, selecting 'libgavl-dev' for regex 'vlc*'
Note, selecting 'vlc-plugin-zvbi' for regex 'vlc*'
Note, selecting 'libavl-dev' for regex 'vlc*'
Note, selecting 'vlc-plugin-jack' for regex 'vlc*'
Note, selecting 'liquidsoap-plugin-gavl' for regex 'vlc*'
Note, selecting 'convlit' for regex 'vlc*'
Note, selecting 'vlc-plugin-sdl' for regex 'vlc*'
Note, selecting 'vlc-data' for regex 'vlc*'
Note, selecting 'libavl1' for regex 'vlc*'
Note, selecting 'libservlet3.0-java' for regex 'vlc*'
Note, selecting 'libgavl-doc' for regex 'vlc*'
Note, selecting 'libgavl-ocaml-dev-pobd2' for regex 'vlc*'
Note, selecting 'libvlccore-dev' for regex 'vlc*'
Note, selecting 'libgavl-ocaml-dev' for regex 'vlc*'
Note, selecting 'vlc-plugin-libde265' for regex 'vlc*'
Note, selecting 'phonon4qt5-backend-vlc' for regex 'vlc*'
Note, selecting 'libservlet2.5-java' for regex 'vlc*'
Note, selecting 'vlogger' for regex 'vlc*'
Note, selecting 'phonon-backend-vlc' for regex 'vlc*'
Note, selecting 'libjnlp-servlet-java' for regex 'vlc*'
Note, selecting 'vlan' for regex 'vlc*'
Note, selecting 'vlc-plugin-vlsub' for regex 'vlc*'
Note, selecting 'vlc-plugin-libde265-dbg' for regex 'vlc*'
Note, selecting 'libvlfeat-dev' for regex 'vlc*'
Note, selecting 'libservlet2.4-java' for regex 'vlc*'
Note, selecting 'libvldocking-java' for regex 'vlc*'
Note, selecting 'phonon-backend-vlc-dbg' for regex 'vlc*'
Note, selecting 'libservlet2.5-java-doc' for regex 'vlc*'
Note, selecting 'mozilla-plugin-vlc' for regex 'vlc*'
Note, selecting 'vlc-plugin-svg' for regex 'vlc*'
Note, selecting 'libgavl-ocaml-pobd2' for regex 'vlc*'
Note, selecting 'vlc' for regex 'vlc*'
Note, selecting 'libvlc5' for regex 'vlc*'
Note, selecting 'libvlfeat0' for regex 'vlc*'
Note, selecting 'libvlfeat-doc' for regex 'vlc*'
Note, selecting 'libspring-web-servlet-java' for regex 'vlc*'
Note, selecting 'remuco-vlc' for regex 'vlc*'
Note, selecting 'apvlv' for regex 'vlc*'
Note, selecting 'octave-vlfeat' for regex 'vlc*'
Note, selecting 'vlc-dbg' for regex 'vlc*'
Note, selecting 'vlc-plugin-pulse' for regex 'vlc*'
Note, selecting 'libservlet3.0-java-doc' for regex 'vlc*'
Note, selecting 'libvlfeat0-dbg' for regex 'vlc*'
Note, selecting 'libgavl1' for regex 'vlc*'
Package 'ttf-vlgothic' is not installed, so not removed
Package 'mozilla-plugin-vlc' is not installed, so not removed
Package 'python-vlc' is not installed, so not removed
Note, selecting 'libgavl-ocaml' instead of 'libgavl-ocaml-pobd2'
Note, selecting 'libgavl-ocaml-dev' instead of 'libgavl-ocaml-dev-pobd2'
Package 'libvlc0-dev' is not installed, so not removed
Package 'avl' is not installed, so not removed
Package 'fonts-vlgothic' is not installed, so not removed
Package 'vlan' is not installed, so not removed
Package 'apvlv' is not installed, so not removed
Package 'browser-plugin-vlc' is not installed, so not removed
Package 'convlit' is not installed, so not removed
Package 'fuse-posixovl' is not installed, so not removed
Package 'libavl-dev' is not installed, so not removed
Package 'libavl1' is not installed, so not removed
Package 'libgavl-dev' is not installed, so not removed
Package 'libgavl-doc' is not installed, so not removed
Package 'libgavl-ocaml' is not installed, so not removed
Package 'libgavl-ocaml-dev' is not installed, so not removed
Package 'libgavl1-dbg' is not installed, so not removed
Package 'libjnlp-servlet-java' is not installed, so not removed
Package 'libservlet2.4-java' is not installed, so not removed
Package 'libservlet2.5-java' is not installed, so not removed
Package 'libservlet2.5-java-doc' is not installed, so not removed
Package 'libspring-web-servlet-java' is not installed, so not removed
Package 'libvldocking-java' is not installed, so not removed
Package 'libvlfeat-dev' is not installed, so not removed
Package 'libvlfeat-doc' is not installed, so not removed
Package 'libvlfeat0' is not installed, so not removed
Package 'libvlfeat0-dbg' is not installed, so not removed
Package 'octave-vlfeat' is not installed, so not removed
Package 'remuco-vlc' is not installed, so not removed
Package 'vlc-plugin-vlsub' is not installed, so not removed
Package 'vlock' is not installed, so not removed
Package 'vlogger' is not installed, so not removed
Package 'libservlet3.0-java' is not installed, so not removed
Package 'libservlet3.0-java-doc' is not installed, so not removed
Package 'vlc-plugin-sdl' is not installed, so not removed
Package 'vlc-plugin-jack' is not installed, so not removed
Package 'vlc-dbg' is not installed, so not removed
Package 'vlc-plugin-pulse' is not installed, so not removed
Package 'libvlccore-dev' is not installed, so not removed
Package 'libvlc-dev' is not installed, so not removed
Package 'phonon-backend-vlc' is not installed, so not removed
Package 'phonon-backend-vlc-dbg' is not installed, so not removed
Package 'vlc-plugin-svg' is not installed, so not removed
Package 'vlc-plugin-fluidsynth' is not installed, so not removed
Package 'vlc-plugin-zvbi' is not installed, so not removed
Package 'phonon4qt5-backend-vlc' is not installed, so not removed
Package 'vlc-plugin-libde265' is not installed, so not removed
Package 'vlc-plugin-libde265-dbg' is not installed, so not removed

The following packages will be REMOVED
  libgavl1* libvlc5* libvlccore7* libvlccore8* liquidsoap-plugin-all*
  liquidsoap-plugin-gavl* vlc* vlc-data* vlc-nox* vlc-plugin-notify*
  vlc-plugin-samba*
0 to upgrade, 0 to newly install, 11 to remove and 0 not to upgrade.
After this operation, 56.2 MB disk space will be freed.
Do you want to continue? [Y/n] 
```


then to run ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo updatedb && locate vlc[/FONT][/COLOR]
```
to make sure the purge was total

... and now check your sound menu




is what i would do here ...   there might be a quicker route ....   maybe

[B]
PS EDIT   [/B]then it dawns on me that you want to KEEP vlc and remove it from sound menu only   ...    anyway will leave the info here for reference

---

### Post by VMC on 2015-10-28
```
gsettings set com.canonical.indicator.sound interested-media-players "[]"
```

---

### Post by nickTaylor1181 on 2015-10-29
Yup :)

VLC is absolutely brilliant. I don't want to get rid of it, I just want to stop it interfering with the sound menu... I mean as it stands, the sound-menu is pretty much unusable, because you have to scroll past all the VLC cruft to get to "sound settings" or the volume slider. 

I think I might just make a link directly to sound settings and lose the sound menu. Kindof crap though. This seems to be a recurring theme etc. Every new machine I get I come up against this same problem. I've never managed to fix it.

---

### Post by nickTaylor1181 on 2015-10-29
Hiya - thanks for you reply.

Unfortunately, that's a member of the "gsettings / dconfig" family of proposed solutions. It doesn't work. Or it does, until you run VLC again - then  the offending controls come back, and they don't go away.

---

### Post by shantiq on 2015-10-29
you have read all these i suppose  [ askubuntu]("https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCEQFjAAahUKEwih_a3rj-fIAhWBURoKHSTmDRI&url=http%3A%2F%2Faskubuntu.com%2Fquestions%2F468811%2Fremove-vlc-player-from-sound-menu-in-unity-bar&usg=AFQjCNGTv6D8qGvj2Ri9ZSNXK9tlaIDBNw&sig2=YayGuOnvL8dnzRc6qARNaA") and [howtogeek]("http://www.howtogeek.com/113897/how-to-remove-media-players-from-ubuntus-sound-menu-add-your-own/")  [omgubuntu]("http://www.omgubuntu.co.uk/2014/11/remove-players-ubuntu-sound-menu")
all 3 seem happy with the results of their manipulations

---

### Post by nickTaylor1181 on 2015-10-30
Ahah... I hadn't seen the bit about : 

sudo mv /usr/lib/vlc/plugins/control/libdbus_plugin.so /usr/lib/vlc/plugins/control/libdbus_plugin.so.backup

If you don't do that, then you can actually see VLC re-adding itself to interested-media-players  when you start it up. Moving the plugin seems to stop this from happening.


Thank you ! :)



Nick

---

### Post by shantiq on 2015-10-30
cool Nick.   this is what i love about Ubuntu and the net
somehow since so many of us using it the answer is often already there since someone somewhere will have bumped into similar snag
Strength in numbers :]

---

### Post by deadflowr on 2015-10-31
> **VMC said:**
> ```
gsettings set com.canonical.indicator.sound interested-media-players "[]"
```
Run this along with
backlisted-media-players option
```
gsettings set com.canonical.indicator.sound blacklisted-media-players "['vlc.desktop']"
```

But this thread is somehow tagged as UbuntuGnome, so don't know how any of this would work for that.

Edit: nevermind, seems somethings busted with it.

---

