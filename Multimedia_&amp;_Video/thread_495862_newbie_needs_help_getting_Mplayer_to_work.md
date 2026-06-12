---
title: "newbie needs help getting Mplayer to work"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by henryvann101 on 2007-07-08
Hi gang,

Just installed Realplayer 10 out of Ubuntu Fiesty Automatix register.  Problem is, when I go to a website and click the music anchor, instead of opening and playing, my computer keeps defaulting to be opened by Totem MoviePlayer.  Also, I've tried opening Realplayer music links by opening RealPlayer first, File--->Open--->name of link; however, when I do this no sound comes out. 
Can anyone perhaps start me over again--by the numbers--- and walk me through a proper RealPlayer 10 settup?

Much thanks.
Henry

---

### Post by reclusivemonkey on 2007-07-09
> **henryvann101 said:**
> Hi gang,

Just installed Realplayer 10 out of Ubuntu Fiesty Automatix register.  Problem is, when I go to a website and click the music anchor, instead of opening and playing, my computer keeps defaulting to be opened by Totem MoviePlayer.  Also, I've tried opening Realplayer music links by opening RealPlayer first, File--->Open--->name of link; however, when I do this no sound comes out. 
Can anyone perhaps start me over again--by the numbers--- and walk me through a proper RealPlayer 10 settup?

Much thanks.
Henry

You can move the totem plugins to another directory or delete them altogether to let mplayer/realplayer handle things. What does

```

ls -l /usr/lib/firefox/plugins/

```

give you?

---

### Post by Gremlinzzz on 2007-07-09
Go to synaptic package manager and uninstall totem plugin
[http://smplayer.sourceforge.net/linux/index_en.php](http://smplayer.sourceforge.net/linux/index_en.php) 
click download get the ubuntu deb package easy to install
go to synaptic again and install mplayer plugin.
get win32 codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
check mplayer plugin here
[http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
If screen gray but i dont think it will be right click on screen click configure choose x11 for video and a alsa audio.to play divx movies online add these commands to terminal
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
:guitar:

---

