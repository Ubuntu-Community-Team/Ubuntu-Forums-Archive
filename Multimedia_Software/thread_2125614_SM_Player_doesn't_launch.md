---
title: "SM Player doesn't launch"
date: 2013-03-14
forum: Multimedia Software
---

### Post by scottbomb on 2013-03-14
I've tried launching it 3 different ways and it won't start. I right-click a music file and select "open with SM Player" and nothing happens. I then try to launch SM Player from the menu and nothing happens. Out of curiosity I tried to launch it from a terminal and it gives the following:

```
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configuration s from ~/.fonts.conf is deprecated.
This is SMPlayer v. 0.8.3 running on Linux
```

It pauses for about 2-3 seconds, nothing happens, then I get my shell prompt back, ready for my next command. No other errors, nothing happens.

Is it refusing to start over a deprecated font? I entered "echo $#" and it returns a 0. 

I uninstalled and reinstalled both mplayer and smplayer and nothing has changed. 

Any ideas on what I can do next? Should I file a bug report against SMPlayer?

---

### Post by carl4926 on 2013-03-14
Try deleting the hidden folder in ~/.mplayer

---

### Post by andrew.46 on 2013-03-14
Mind you SMPlayer config would usually be in *$HOME.config/smplayer/smplayer.ini*. Before delving too deeply into config files perhaps try to use the latest version from the PPA of the SMPlayer developer. This single command should do this:

```

sudo add-apt-repository ppa:rvm/smplayer && \
sudo apt-get update && sudo apt-get -y install smplayer smtube

```

If the problem persists try running MPlayer from the cmmandline and see if that is running ok...

---

### Post by scottbomb on 2013-03-14
Thanks guys! I did both suggestions. It didn't fix it right away but it did work again after a reboot.

---

