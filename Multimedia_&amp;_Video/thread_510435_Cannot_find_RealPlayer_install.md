---
title: "Cannot find RealPlayer install"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by Jored on 2007-07-26
I running Xubuntu 7.04 with Xfce desktop.

I've installed Real Player from the downloaded RealPlayer10GOLD.bin file and got a message that it had installed successfully, yet I can't find it anywhere. 

When I was going through the installation process a question about choosing a directory came up (can't remember exactly the wording) and I answered Y (I knew no better). It came back saying that Real Player was now configured correctly (??) and installation had completed successfully.

I'm sorry but I'm a newbie and would appreciate step by step guidance. From another post I got help from a great guy, but unfortunately he didn't know the Xfce environment and his instructions were for Gnome.

:confused:

---

### Post by tk03759 on 2007-07-26
From what I remember, RealPlayer, if you use the installation method that you did, installs to your home folder.

You can find it by going to Places > Home Folder > and I think a Real Player folder.

If you don't like the way it installed (I wasn't satisfied), you can go to Applications > Add/Remove. Make sure that it searches for All Available Applications, and type in real player. check it off, click apply, and Real Player will be installed.

I'd just liike to note though, that Real Player for linux isn't very functional as a default media player. Don't expect the same Real Player you'd find on Windows. Good alternatives are banshee or amarok.

Edit: I didn't realize you were using Xubuntu. I'm not as familiar with it eithor, but I'm pretty sure this should be the same. I don't remember if Xubuntu uses Add/Remove, so you might have to use synaptic instead?

---

### Post by tbroderick on 2007-07-26
Use locate to search for it.

```

sudo updatedb
locate realplayer
```

---

### Post by Bablefish on 2007-07-26
Or use this Terminal command

sudo apt-get install realplayer

---

