---
title: "Help with Banshee"
date: 2009-02-26
forum: Multimedia Software
---

### Post by robond8 on 2009-02-26
Every time I plug in my Zen and open Banshee, Banshee closes for no reason. I know my mp3 player is fine because it works on WMP 11 and 10, Napster, Rythm Box, and many other programs. I would like to use it with Banshee. I have already tried re-installing Banshee twice. Any other suggestions?

Thanks and If you know of any other music player programs (besides Amorak!) that work on Ubuntu and will support MTP devices please tell me! Thanks

---

### Post by smbm on 2009-02-26
You could try running it from the command line like this

```
banshee --debug
```

Then when it's running plug your player in.

Then paste any text you get in the terminal in this thread and hopefully someone can find out the cause of the problem.

---

### Post by BrandonBan6 on 2009-04-30
hey Rob,

I'm getting more and more impressed with VLC player. Maybe check it out?

```

sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```

---

