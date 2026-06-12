---
title: "Totem uninstaling"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by moonliter on 2006-12-26
When I try to remove totem movie player or totem firefox plugin I also have to remove ubuntu-desktop.Can I remove Totem without removing ubuntu-desktop ](*,)

---

### Post by tszanon on 2006-12-26
Since ubuntu-desktop depends on totem, I don't think so.

---

### Post by moonliter on 2006-12-26
Then is there a way to replace totem job in firefox with mplayer?

---

### Post by Ozzee on 2006-12-26
[This](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox) guide tells you how to install mplayer plugin for firefox. 

:)

---

### Post by moonliter on 2006-12-26
Thanks OZEE but I have already downloaded latest mplayer codecs and plugin for ubuntu but when I want to watch windows media player (wmv) format movie in firefox explorer that job do Totem.I want mplayer to play movie in firefox.

---

### Post by Mateo on 2006-12-26
Same problem here.  You can't remove the totem-mozilla plugin or it wants to remove ubuntu-desktop.

And any time you attempt to play a wmv file in browser, it uses the (worthless) totem plugin.  Frustrating.

---

### Post by tszanon on 2006-12-27
A suggestion (I have not tried to see if it works): delete (or move to some other place) the totem plugin from ~/.mozilla/plugins.

It's an invasive method, but it may work.

---

### Post by peebly on 2006-12-27
I think Totem lets ubuntu down, I cannot remember it actually working. It should be renamed total rubbish.

I have installed opensuse lately and installed vlc, and set it to use the vlc Mozilla plugin, everything works. your not forced to use crappy totem.

It could be bye bye Ubuntu.

---

### Post by peebly on 2006-12-27
Hello

Since my last post, I have found a method to control which media player gets used in firefox.

So far it works great.

[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

This firefox extension works on linux, it lets you decide which media player plugin gets used.

I have set wmv to play using VLC.

It automatically detects which ones you have installed and you can pick which one you want to use for different file types.

---

### Post by tszanon on 2006-12-27
> **peebly said:**
> Hello

Since my last post, I have found a method to control which media player gets used in firefox.

So far it works great.

[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

This firefox extension works on linux, it lets you decide which media player plugin gets used.

I have set wmv to play using VLC.

It automatically detects which ones you have installed and you can pick which one you want to use for different file types.

Thanks, I didn't know that.

---

### Post by highneko on 2006-12-27
I suggest you just remove the file associations:
```
sudo mv /usr/share/applications/totem.desktop /usr/share/applications/totem.desktop.die
sudo mv /usr/share/applications/rhythmbox.desktop /usr/share/applications/rhythmbox.desktop.die
```

I think this will make mplayer for firefox:
```
sudo apt-get remove totem-gstreamer-firefox-plugin
sudo apt-get install mozilla-mplayer
```

---

