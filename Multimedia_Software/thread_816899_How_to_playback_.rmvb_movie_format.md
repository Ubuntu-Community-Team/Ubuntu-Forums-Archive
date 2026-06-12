---
title: "How to playback .rmvb movie format?"
date: 2008-06-03
forum: Multimedia Software
---

### Post by D.Sync on 2008-06-03
I had tried Movie Player (came pre-bundled with Ubuntu) and Mplayer Movie Player but still no avail.

I had tried searching for plugin for Movie Player but it seems couldn't find the right codec.

Any help?

---

### Post by kellemes on 2008-06-03
[http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/]("http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/")

Hope it works.

---

### Post by Pjotr123 on 2008-06-03
Here's a simple and effective how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Have fun!

Greeting, Pjotr.

---

### Post by D.Sync on 2008-06-03
I had followed [this]("http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/") guide but still couldn't get the video except the sound. By reading the comments I heard that I need to manually login as root to create a folder 'codec' under /usr/lib/ then move all those files I extracted from the essentialbuild-date to the folder.

How can I do so via terminal? Couldn't have permission to do so by now.

---

### Post by D.Sync on 2008-06-03
Guess I know how to do it, just type sudo command eh?

Finally got it to works after following the guides. Apparently the guide is targeted for Ubuntu 7.0x users.

> On Ubuntu 8.04,

you have to install libstdc++5 from synaptic
and copying the codecs to /usr/lib/codecs!!!

Great Tutorial!

---

### Post by D.Sync on 2008-06-03
There is one problem though, whenever I click double-size or fullscreen, the video image didn't fit the screen, it's just the window being doubled. Any ideas?

---

### Post by instinctive on 2008-06-03
> [http://www.simplehelp.net/2007/07/27...les-in-ubuntu/](http://www.simplehelp.net/2007/07/27...les-in-ubuntu/)

Hope it works.

OMG thank you for the guide. I have been waiting for an easy guide like this to watch real videos. I am also experiencing the same issue with the screen image, so if anyone has a solution that would be wonderful. Thank you very much.

---

### Post by instinctive on 2008-06-03
Just letting you know that I just found another guide that suggested to install the win32codecs in synaptic when the medibuntu repos is enabled. Since then I tried to watch the .rmvb file in totem and it works perfectly. I hope this works for everyone else.

---

### Post by D.Sync on 2008-06-03
Already installed but still couldn't play .rmvb on Totem.

---

### Post by wolfen69 on 2008-06-03
just a heads up here. go [HERE]("https://help.ubuntu.com/community/Medibuntu") and enable medibuntu repos. then:
```
sudo apt-get install mplayer vlc libdvdcss2
```there is no file that i cant play with these apps.

---

### Post by D.Sync on 2008-06-05
Indeed, VLC is a great universal media player.

---

