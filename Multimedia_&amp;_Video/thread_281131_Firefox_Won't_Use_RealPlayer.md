---
title: "Firefox Won't Use RealPlayer"
date: 2006-10-20
forum: Multimedia &amp; Video
---

### Post by Synikk on 2006-10-20
I've just installed RealPlayer 10 on 6.06 and I can't get Firefox to open streaming RealPlayer audio files with RealPlayer. It tries to open them with Totem. I've tried restarting Firefox, but no dice. It plays imbedded streams just fine, however.

I installed RealPlayer to /opt/RealPlayer, is this okay? I followed the instruction out of a book (Ubuntu Linux for Non-Geeks).

---

### Post by DC@DR on 2006-10-20
Probably I think you could install MediaPlayerConnectivity extenstion from [https://addons.mozilla.org/firefox/extensions/](https://addons.mozilla.org/firefox/extensions/), and then in the option of that extension, you can choose which player to open what streaming file...give it a try :)

---

### Post by bswilson on 2006-10-20
You need to make sure that there's a link to your RealPlayer 10 program's libraries in your Firefox installation's plugin directories.

By default, the directory where Firefox is installed is called **/usr/lib/firefox/plugins**.  So, close Firefox, and run this command:

```
$ ln -s /opt/RealPlayer/libnullplugin.so /usr/lib/firefox/plugins/libnullplugin.so
```

Now restart Firefox; you should be in business.

---

### Post by Synikk on 2006-10-20
> **bswilson said:**
> You need to make sure that there's a link to your RealPlayer 10 program's libraries in your Firefox installation's plugin directories.

By default, the directory where Firefox is installed is called **/usr/lib/firefox/plugins**.  So, close Firefox, and run this command:

```
$ ln -s /opt/RealPlayer/libnullplugin.so /usr/lib/firefox/plugins/libnullplugin.so
```

Now restart Firefox; you should be in business.

Alright, that got me somewhere. However, now the streams are opening with the MPlayer plugin! [This post]("http://www.ubuntuforums.org/showpost.php?p=1159174&postcount=1") says:

> I couldn't even remember if real player came with a plugin by itself. Which of course it did. However I found mplayer plugin to override it by default. Type: "about:Plugins" in firefox title bar to find out.

So I went to /usr/lib/mozilla-firefox/plugins/ and removed "mplayerplug-in-rm.*". That is the plugin that exclusively handled real media.

Should I try this?

---

