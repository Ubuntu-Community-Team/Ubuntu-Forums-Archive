---
title: "Play/pause Media Player From Hot-key"
date: 2012-02-29
forum: Multimedia Software
---

### Post by user2037 on 2012-02-29
How does one do this on Xubuntu 11.10? Can it be done from command line?

---

### Post by Toz on 2012-02-29
The default media player in Xubuntu 11.10 is gmusicbrowser. See the "How do I control gmusicbrowser with global shortcuts or multimedia keys ?" section from this [_link_]("http://gmusicbrowser.org/faq.html") for more information, or open a terminal window and type in:
```
gmusicbrowser -listcmd
```
...for a list of commands that you can run to control the player.

EDIT: Or you can directly manipulate the fifo file. Here are some examples:
```

echo PlayPause > ~/.config/gmusicbrowser/gmusicbrowser.fifo

echo PrevSong > ~/.config/gmusicbrowser/gmusicbrowser.fifo

echo NextSong > ~/.config/gmusicbrowser/gmusicbrowser.fifo

echo DecVolume > ~/.config/gmusicbrowser/gmusicbrowser.fifo

echo IncVolume > ~/.config/gmusicbrowser/gmusicbrowser.fifo

echo Stop >  ~/.config/gmusicbrowser/gmusicbrowser.fifo

echo ShowHide >  ~/.config/gmusicbrowser/gmusicbrowser.fifo
```

---

### Post by user2037 on 2012-03-01
Gmusicbrowser doesn't have podcast support. How about Rhythmbox or Pithos?

---

### Post by Toz on 2012-03-01
I don't have rhythmbox installed to test. Does this command work:
```

dbus-send --type=method_call --dest=org.mpris.MediaPlayer2.rhythmbox /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Next
```

Source: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/875064/comments/9]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/875064/comments/9").

As for pithos, have a look here for something similar: [https://answers.launchpad.net/pithos/+question/166326]("https://answers.launchpad.net/pithos/+question/166326").

---

### Post by user2037 on 2012-03-14
Dbus-send worked for Rhythmbox. Thanks.

---

