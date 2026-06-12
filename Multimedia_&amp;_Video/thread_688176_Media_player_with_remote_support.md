---
title: "Media player with remote support?"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by Kurosaki_Ichigo on 2008-02-05
Hi, I'm kinda new to Linux, been using Ubuntu for a few months now.
I was just wondering if there are any media players for Linux that support IR remote control (not looking for a media center just a player) I'm using the Microsoft MCE remote.

any help would be great thanx

---

### Post by fenian on 2008-02-05
Yes you can do this instructions are [here.]("https://help.ubuntu.com/community/InstallLirc/Gutsy")

---

### Post by wheredidrealitygo on 2008-02-05
I have the same remote as well, and I've had luck with Lirc and the media centre called "Elisa", it's only in developing stages, but it looks quite promising.

Mplayer movie player works well with it without configuration also.

---

### Post by kara.lockard on 2008-02-05
It's only in developing stages, but it looks quite promising.

---

### Post by Kurosaki_Ichigo on 2008-02-05
Alright thanx! man i love the Linux Community!
Anyway I guess I need to install Lirc before i can do anything?

---

### Post by wheredidrealitygo on 2008-02-05
Yeah, it's actually in the Synaptic repos, which makes it incredibly easy to install.

Go to System, Administration, Synaptic Package Manager, and find these three packages:

```
lirc
lirc-modules-source
mythbuntu-lirc-generator
```

it'll install everything you need right there.

make sure that you pay attention when the configuration window pops up, it'll configure your lirc for the Windows MCE remote if you select it (you want the newer one, there are two).

Then, you should run mythbuntu-lirc-generator so it can map your buttons properly.

So everything is installed and configured, now you just have to start it up.

```
sudo modprobe lirc_dev
sudo modprobe lirc_mceusb2
```

That loads the kernel modules so you can use the remote, and then ```
sudo /etc/init.d/lirc start
``` will start irc recording the infrared signals.

use the command ```
irw
``` to see if it's registering the signals properly.

I wish someone had told me all this when I started playing with it around a week or so ago hehe.

from there you can install elisa, which i can also walk you through if you need.

---

