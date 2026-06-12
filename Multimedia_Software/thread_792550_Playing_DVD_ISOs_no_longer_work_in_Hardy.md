---
title: "Playing DVD ISOs no longer work in Hardy"
date: 2008-05-13
forum: Multimedia Software
---

### Post by Chua-Chua on 2008-05-13
Hello,

I migrated from Feisty to Hardy and now VLC/Mplayer/xine can't open ISO files. 

I used to be able to just click on an ISO (ripped DVD) and VLC/Mplayer/xine will play it fine.

Is there something I need?

I don't have the default Ubuntu install, I have Ubuntu Studio with the rt kernel.

Thanks

---

### Post by mc4man on 2008-05-13
> I have Ubuntu Studio with the rt kernel.
With that as an unknown (to me) if you add vlc as a second choice of default player it'll be added to the r.click menu. Totem remains the other choice by default and stays that way.(also avaiable in r.click) To make totem-xine the default totem player run ```
sudo update-alternatives --config totem
``` and choose 2.
note: this is what does work with ubuntu 8.04/gnome

sorry  edit : how to add vlc  section 4/5
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Bakon Jarser on 2008-05-13
do regular dvd's work?  if not you need to install dvdcss

---

### Post by Chua-Chua on 2008-05-27
Hello, 

Yes regular DVDs work and I have dvdcss.

Sorry for the late reply.

I still have problems with opening ISOs in Gutsy.
I tried to change the default to totem-xine.
In VLC, it only plays the menu without sound or interaction, so I can only "view" the menu and not click on anything

Thanks for the replies.

---

