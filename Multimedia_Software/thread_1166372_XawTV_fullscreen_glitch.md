---
title: "XawTV fullscreen glitch"
date: 2009-05-21
forum: Multimedia Software
---

### Post by paul_r on 2009-05-21
Hi people,

I was running in 1024 resolution for a while just because for fullscreen on XawTV I would get letterboxing on my favorite 1280. So today I found out about the xawtvrc config and entered it in the correct directory. Before I rebooted, it was fine and when I went into fullscreen the screen would go to 1024 within the native 1280 the desktop is running. Somehow, since reboot when I go into fullscreen, it seems to go into 640x480 and I can use the cursor to scroll around the picture.

This change from your native desktop res to a xawtv res is from the:

```

fullscreen = 1024x768

```

in xawtvrc

Once more, this worked before I rebooted fine and was wondering if anyone has an ideas as to what's going on.

Paul R.

edit after solved:

It appears xawtv has a newer version motv which this issue does not occur. This package has stopped being included since intrepid, and I got it from hardy. More on it @ [https://bugs.launchpad.net/ubuntu/+source/motv/+bug/277761]("https://bugs.launchpad.net/ubuntu/+source/motv/+bug/277761")

---

