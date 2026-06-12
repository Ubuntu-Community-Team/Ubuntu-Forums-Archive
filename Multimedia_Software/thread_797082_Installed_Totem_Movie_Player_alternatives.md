---
title: "Installed Totem Movie Player alternatives"
date: 2008-05-16
forum: Multimedia Software
---

### Post by interse on 2008-05-16
How do I get alternatives to Total Movie Player, after being installed, to appear in the Preferences / Media tab in the DVD Video option?

After installation, I have rebooted and yet ONLY Totem Movie Player appears in the DVD Video opton.

---

### Post by mc4man on 2008-05-17
if your referring to totem-xine vs. totem-gstreamer then you can choose one or the other as default. The name will still show Movie Player. To switch run
```
sudo update-alternatives --config totem
``` and follow prompt

edit; in addition to autoplay the default totem will become your app menu version. In your r.click menu you will see 2 totems, xine and gstreamer and can choose either one

---

### Post by interse on 2008-05-17
Actually I have installed two alternative media players, gxine and VLC media player.  Neither of these appear in the DVD Video options tab in the Preferences / Media tab under DVD players.  

How do I get them to appear so that one of the can be selected as the default player?

---

### Post by mc4man on 2008-05-17
> Actually I have installed two alternative media players, gxine and VLC media player sorry i misread your post. Here's a link to where the instr. are already nicely explained. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)   go down to section 4/5, includes for both gutsy and hardy in terms of vlc. For gxine in gutsy you'd just have to experiment with command, in hardy I'd stick to vlc.
The other thing to note is in the instructions it mentions changing the launcher for vlc from wcvlc %F. You may see instead vlc %U, no matter just change it as shown.

edit: the instr. in the sticky linked above concerning setting vlc as a default (autoplay) choice in 8.04 _only_ apply to ubuntu (gnome). In kubuntu they'll produce mixed results, in xubuntu are unnecessary and may bork things up. For xubuntu see here
[http://ubuntuforums.org/showthread.php?p=4974123#post4974123](http://ubuntuforums.org/showthread.php?p=4974123#post4974123)

---

