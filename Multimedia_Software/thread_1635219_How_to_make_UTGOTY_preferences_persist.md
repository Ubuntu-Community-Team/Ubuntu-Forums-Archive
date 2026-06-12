---
title: "How to make UTGOTY preferences persist"
date: 2010-12-01
forum: Multimedia Software
---

### Post by Sylos on 2010-12-01
Hello
Due to some foolishness on my part I have needed to reinstall UT GOTY on my Ubuntu Karmic PC. I have run the loki installer fine and the game runs but every time I load it up I am back to Player as my name and the default video settings. For some reason my changes are not being saved.

The loki readme states that a .loki/ut folder is set up in the ?home folder and this is where all the config is stored. There isnt one shown in Nautilus BUT if i try to create one it says it is already in use. So I had a look through the CLI and got this:

```
saric@saric-desktop:~/.loki/ut$ ls
install_dir  System

```

Not sure what this means.

I did note during the install that the shell kept saying it couldnt create the .loki/ut directory but it seems to be there.

Can anyone shed some light on how to get my preferences to stick. I have a hankering for some fragging.

Thanks

---

### Post by Sylos on 2010-12-02
Well Im an official dunce!
The hidden folder .loki/ut was created as root - hence the game couldnt write any config to it. A quick chown and all is well.

Let the fragging commence.

---

