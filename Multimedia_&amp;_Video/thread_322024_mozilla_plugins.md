---
title: "mozilla plugins"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by jake3988 on 2006-12-19
I recently installed mplayer plugin for mozilla.  There was also a wealth of plugins already there.

According to about:plugins nearly every mime type is covered and that they are all enabled.

Yet every site i go to, they don't work.  There something I'm missing?  My previous OS (freebsd) I never had to edit anything or do anything else to get them to work... anything I have to do here extra as to why they aren't working?

Thanks!

---

### Post by divague on 2006-12-19
if you're using edgy mplayer won't work because totem's plugin is installed. you have to uninstall totem' plgunin in order to get mplayer's plugin to work

---

### Post by kerry_s on 2006-12-19
Did you install the w32codecs? I use this repo->

sudo gedit /etc/apt/sources.list

add this to the bottom

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main 


the key, in terminal, run both these 1 at a time->

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 1F41B907 

gpg --armor --export 1F41B907 | sudo apt-key add -

---

### Post by jake3988 on 2006-12-20
No no.  Its not that they don't work, its that mozilla (and firefox) don't detect there's any plugin at all.  Just has that weird blue marker that says I have nothing to be able to play it.

Which is a lie.  Any other ideas?


Though, thanks for the tip for the w32codecs, I've been wondering where they were hiding.

---

### Post by kerry_s on 2006-12-20
Can you copy and paste the output of this->

```
ls -a ~/.mozilla/plugins

```

```
ls -a /usr/lib/mozilla/plugins
```

---

### Post by jake3988 on 2006-12-20
```

jake3988@jake3988-desktop:~/media$ ls -a ~/.mozilla/plugins/
ls: /home/jake3988/.mozilla/plugins/: No such file or directory
jake3988@jake3988-desktop:~/media$ ls -a /usr/lib/mozilla/plugins/
.                            libtotem-gmp-plugin.xpt          mplayerplug-in-qt.xpt
..                           libtotem-mully-plugin.so         mplayerplug-in-rm.so
libnullplugin.so             libtotem-mully-plugin.xpt        mplayerplug-in-rm.xpt
libtotem-basic-plugin.so     libtotem-narrowspace-plugin.so   mplayerplug-in.so
libtotem-basic-plugin.xpt    libtotem-narrowspace-plugin.xpt  mplayerplug-in-wmp.so
libtotem-complex-plugin.so   mplayerplug-in-dvx.so            mplayerplug-in-wmp.xpt
libtotem-complex-plugin.xpt  mplayerplug-in-dvx.xpt           mplayerplug-in.xpt
libtotem-gmp-plugin.so       mplayerplug-in-qt.so

```

---

### Post by kerry_s on 2006-12-21
> **jake3988 said:**
> ```

jake3988@jake3988-desktop:~/media$ ls -a ~/.mozilla/plugins/
ls: /home/jake3988/.mozilla/plugins/: No such file or directory
jake3988@jake3988-desktop:~/media$ ls -a /usr/lib/mozilla/plugins/
.                            libtotem-gmp-plugin.xpt          mplayerplug-in-qt.xpt
..                           libtotem-mully-plugin.so         mplayerplug-in-rm.so
libnullplugin.so             libtotem-mully-plugin.xpt        mplayerplug-in-rm.xpt
libtotem-basic-plugin.so     libtotem-narrowspace-plugin.so   mplayerplug-in.so
libtotem-basic-plugin.xpt    libtotem-narrowspace-plugin.xpt  mplayerplug-in-wmp.so
libtotem-complex-plugin.so   mplayerplug-in-dvx.so            mplayerplug-in-wmp.xpt
libtotem-complex-plugin.xpt  mplayerplug-in-dvx.xpt           mplayerplug-in.xpt
libtotem-gmp-plugin.so       mplayerplug-in-qt.so

```

Try opening synaptic & uninstall "totem-mozilla" so it uses mplayer instead.

---

### Post by jake3988 on 2006-12-21
Yeah, that worked.  Thanks.


Surprised Mozilla can get so confused by simply having multiple plugins that none work at all.  You'd think one would just take precedence over the other.  Oh well.

---

### Post by jake3988 on 2006-12-22
I tried your tip about the w32codecs.  The site seems to add fine... but there's no w32codecs available.

Where can I find the codecs?

Thanks!


Edit:  Nevermind.  I forgot to run sudo apt-get update.

It works fine now!

---

### Post by kerry_s on 2006-12-22
> **jake3988 said:**
> I tried your tip about the w32codecs.  The site seems to add fine... but there's no w32codecs available.

Where can I find the codecs?

Thanks!


Edit:  Nevermind.  I forgot to run sudo apt-get update.

It works fine now!

Your on a roll now! Time to watch some movies.

---

### Post by CheeseQueen452 on 2006-12-24
When I try to mark it for removal, it wants to remove "ubuntu-desktop". What exactly does that mean? Is it safe to remove it?

> **kerry_s said:**
> Try opening synaptic & uninstall "totem-mozilla" so it uses mplayer instead.

---

### Post by kerry_s on 2006-12-24
> **CheeseQueen452 said:**
> When I try to mark it for removal, it wants to remove "ubuntu-desktop". What exactly does that mean? Is it safe to remove it?

Yes, ubuntu-desktop is just meta package, that installs the ubuntu-desktop when you first install.

---

### Post by CheeseQueen452 on 2006-12-24
I uninstalled it, but playing streaming videos at news.yahoo.com & etonline.com with the mplayer plugin doesn't work. Also, when I open "add/remove", it keeps saying the list of available packages is out of date, & it wasn't doing that before. HELP!

---

### Post by kerry_s on 2006-12-24
> **CheeseQueen452 said:**
> I uninstalled it, but playing streaming videos at news.yahoo.com & etonline.com with the mplayer plugin doesn't work. Also, when I open "add/remove", it keeps saying the list of available packages is out of date, & it wasn't doing that before. HELP!

Use "synaptic" instead of "add/remove" & click the reload button to update your list of packages available.

Did you install the w32codecs?

---

### Post by CheeseQueen452 on 2006-12-25
Add/remove still says my list of available programs is out of date. What do I do? I tried following the instructions in this thread to install the w32codecs, but it didn't work. Or maybe I did something wrong? I need help!

> **kerry_s said:**
> Use "synaptic" instead of "add/remove" & click the reload button to update your list of packages available.

Did you install the w32codecs?

---

### Post by kerry_s on 2006-12-25
> **CheeseQueen452 said:**
> Add/remove still says my list of available programs is out of date. What do I do? I tried following the instructions in this thread to install the w32codecs, but it didn't work. Or maybe I did something wrong? I need help!

Can you start a new thread, I'm not very familiar with add/remove. When i open mine it updates itself. In any case you could use more help than i can give, so you need to start a thread so your problems what they see instead of "mozilla plugins".

---

