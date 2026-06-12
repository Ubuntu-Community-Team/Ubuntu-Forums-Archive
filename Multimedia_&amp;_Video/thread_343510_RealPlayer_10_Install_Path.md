---
title: "RealPlayer 10 Install Path"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by Graham1 on 2007-01-21
Hi All

Just downloaded and installed RealPlayer 10 into my home directory (i.e /home/user/Programs/RealPlayer. Wasn't sure where to install so I Installed into somewhere I knew I had rights. Just wondering whether there is a global folder (for all users) where I could have installed to?

:)

---

### Post by taurus on 2007-01-21
You could install it to /opt and have a link from /usr/bin/realplay to /opt/RealPlayer/realplay.  Then, everybody can run it.  Nice and clean.

---

### Post by Graham1 on 2007-01-21
Is that the prefered method? (for any application). I'm finding the directory structure hard in Linux compared to Windows :(. Btw, how do you make a link? (is that similar to a shortcut in Windows?).

:)

---

### Post by taurus on 2007-01-21
When you run the installer (with the sudo in front), it will ask you where you want to install it.  Pick /opt/RealPlayer and it will ask you if you want it to link it to /usr/bin.  Answer yes and you don't have to do it by hand.  Otherwise, the command would look something like

```
sudo ln -s /opt/RealPlayer/realplay /usr/bin/realplay
```

---

### Post by Graham1 on 2007-01-21
I have installed RealPlayer into /opt/RealPlayer but I don't have a shortcut in my menu. During installation, it said something about symbolic links (so I said yes), then something about user... which I wasn't sure about.

:)

---

### Post by taurus on 2007-01-21
You should say yes for that question as well.  Then, it will create an icon in Applications -> Video & Sound.

---

### Post by Graham1 on 2007-01-21
I think it was asking for a path (i.e /usr) but ... kept appearing (like it was installing something)

:)

---

### Post by Graham1 on 2007-01-22
Please see output below:-

"You have selected the following RealPlayer configuration:

Destination:            /opt/RealPlayer

1. Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

2. Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: .Y

3. enter the prefix for symbolic links [/usr]: "

I am unsure about step 3. I have tried /usr and left blank but still no shortcut :(.

:)

---

### Post by 4ebees on 2007-01-22
Hiya,

I'd try the following:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

I've installed RealPlayer on several machines using this guide and had no problems.

I realise it's not an answer to your direct question, but I've found it to be the simplest way to install and run RealPlayer. 

It installs the player here:

/usr/bin/realplay

and, as the site says:

"It will also install all the necessary plugins automagically for it to view embedded real videos in Firefox"

Hope this helps.

---

