---
title: "[SOLVED] Can't watch trailers(e.g.Apple trailers) or listen to Live radio."
date: 2008-07-16
forum: Multimedia Software
---

### Post by libe on 2008-07-16
[[IMG]http://img509.imageshack.us/img509/7081/screenshotappletrailersnj1.th.png[/IMG]](http://img509.imageshack.us/my.php?image=screenshotappletrailersnj1.png)
First of all hey and glad to be member of this community!
I'm having this ANNOYING problem and don't know how to solve it,any help?

---

### Post by ibutho on 2008-07-16
Install the ubuntu-restricted-extras package using the instructions [here]("https://help.ubuntu.com/community/RestrictedFormats"). Also install the totem-mozilla package. Hopefully that will resolve your problem.

---

### Post by stats on 2008-07-16
mplayerplug-in works nicely on the apple site
```
sudo apt-get install mozilla-mplayer
```

---

### Post by libe on 2008-07-16
> **ibutho said:**
> Install the ubuntu-restricted-extras package using the instructions [here]("https://help.ubuntu.com/community/RestrictedFormats"). Also install the totem-mozilla package. Hopefully that will resolve your problem.

> **stats said:**
> mplayerplug-in works nicely on the apple site
```
sudo apt-get install mozilla-mplayer
```

I've already installed ubuntu-restricted-extras,mozilla-plugin-vlc and totem-mozilla

---

### Post by carleeldean on 2008-07-16
I strongly suggest this from the comprehensive solution. I dabbled with this for quite some time but found this to be the best as yet. We will probably never get 100% on the apple site but 90-95% should be there.

--PART 2/5, AUDIO & VIDEO STREAMING--


OPTION 1, GECKO MEDIA PLAYER


UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY


The developer of the MPlayer plugin is now working on a new plugin called Gecko Media Player. I've been doing some testing and I have to say, it's working really well. This plugin works well without the need of adding configuration options. Installation and setup is simple, just copy and paste these commands:

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

sudo apt-get install gnome-mplayer gecko-mediaplayer

or if you're running Kubuntu, you might want the KDE frontend for MPlayer/Xine:

sudo apt-get install kmplayer gecko-mediaplayer

Restart your web browser and test the plugin here. If you have problems with some of the trailers, such as no video and a "Get the latest Quictime" notice, see my post here, but please be careful and read the instructions carefully.

Note: Please REBOOT if you are not carrying on with the rest of the how-to, as you have made lot's of changes to your system and could have some strange problems until you start a fresh session. If you still have problems after rebooting with certain applications, please read the troubleshooting section at the bottom.

---

### Post by libe on 2008-07-16
> **carleeldean said:**
> I strongly suggest this from the comprehensive solution. I dabbled with this for quite some time but found this to be the best as yet. We will probably never get 100% on the apple site but 90-95% should be there.

--PART 2/5, AUDIO & VIDEO STREAMING--


OPTION 1, GECKO MEDIA PLAYER


UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY


The developer of the MPlayer plugin is now working on a new plugin called Gecko Media Player. I've been doing some testing and I have to say, it's working really well. This plugin works well without the need of adding configuration options. Installation and setup is simple, just copy and paste these commands:

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

sudo apt-get install gnome-mplayer gecko-mediaplayer

or if you're running Kubuntu, you might want the KDE frontend for MPlayer/Xine:

sudo apt-get install kmplayer gecko-mediaplayer

Restart your web browser and test the plugin here. If you have problems with some of the trailers, such as no video and a "Get the latest Quictime" notice, see my post here, but please be careful and read the instructions carefully.

Note: Please REBOOT if you are not carrying on with the rest of the how-to, as you have made lot's of changes to your system and could have some strange problems until you start a fresh session. If you still have problems after rebooting with certain applications, please read the troubleshooting section at the bottom.

It worked!
thx a lot for the info!
Sorry for not searching the forum for an answer but i was a little impatient!

---

### Post by igotnoluck on 2009-05-24
thanks,
worked for me on 9.04 :)

---

### Post by apilastrijr on 2010-08-29
It worked well also in 10.04 LTS - Lucid Lynx
Thanks

---

