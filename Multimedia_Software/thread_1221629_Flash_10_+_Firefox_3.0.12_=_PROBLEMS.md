---
title: "Flash 10 + Firefox 3.0.12 = PROBLEMS"
date: 2009-07-24
forum: Multimedia Software
---

### Post by jedimattk on 2009-07-24
I have been having problems with Flash ever since I made the switch to Ubuntu. It is the one and only thing I am unhappy with about my new OS. The first time I tried to watch Youtube videos in Firefox, it just showed a big grey box with a play symbol in the center, and clicking the play button did nothing no matter how many times I did so.

I downloaded the Flash Player 10 for Linux .deb installer from the Adobe website and installed it, to no avail. Well, I suppose it did have an effect ... clicking the big grey play button thingy now made the video window appear, but it never loaded. Similarly, when I try to play online games that rely on Flash to run, they also never load.

I used Synaptic to remove it again from my system and started over from scratch. Besides reinstalling Flash, I also reinstalled the libcurl3 plug-in, but the same things happen. Youtube videos don't load, AdventureQuest won't play correctly, and every time I go to a site using Flash my computer slows down a lot.

I never had these problems with Windows, so I know it's something to do with my configuration, which is as follows:

**OS: **Ubuntu 9.04 "Jaunty"
**Browser: **Mozilla Firefox 3.0.12 (latest release)
**Flash Version: **Flash Player 10 for Linux

I can provide more information if needed. Can anyone help me?

---

### Post by jedimattk on 2009-07-24
[B]UPDATE

[/B]I followed the instructions of someone else I found with a similar problem, and downloaded the tar.gz archive for Flash Player 10, unpacked it, and manually copied the files into the relevant Firefox plugins and components directories. I don't see any gray boxes anymore, but it still seems to be extremely buggy.

I tried YouTube first and the video window loaded, and the little bar started moving to show it was loading. But it wouldn't play. I then tried AQ (an online Flash-based game) and managed to get through the entire process of making a new character, but it vanished mysteriously and instantaneously afterwards. Several times.

Again, none of these problems occurred on Windows, so it's nothing to do with my computer itself, nor with the sites in question. I've tried everything I can think of, and I'm stumped.

---

### Post by lovinglinux on 2009-07-24
> **jedimattk said:**
> I have been having problems with Flash ever since I made the switch to Ubuntu. It is the one and only thing I am unhappy with about my new OS

Me too.

> **jedimattk said:**
> The first time I tried to watch Youtube videos in Firefox, it just showed a big grey box with a play symbol in the center, and clicking the play button did nothing no matter how many times I did so.

I downloaded the Flash Player 10 for Linux .deb installer from the Adobe website and installed it, to no avail. Well, I suppose it did have an effect ... clicking the big grey play button thingy now made the video window appear, but it never loaded. Similarly, when I try to play online games that rely on Flash to run, they also never load.

That's a plugin conflict, due to the presence of gnash plugin.

> **jedimattk said:**
> [B]UPDATE

[/B]I followed the instructions of someone else I found with a similar problem, and downloaded the tar.gz archive for Flash Player 10, unpacked it, and manually copied the files into the relevant Firefox plugins and components directories. I don't see any gray boxes anymore, but it still seems to be extremely buggy.

Instead of manually copying files, See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

> **jedimattk said:**
> [B]UPDATE

[/B]I followed the instructions of someone else I found with a similar problem, and downloaded the tar.gz archive for Flash Player 10, unpacked it, and manually copied the files into the relevant Firefox plugins and components directories. I don't see any gray boxes anymore, but it still seems to be extremely buggy.

I tried YouTube first and the video window loaded, and the little bar started moving to show it was loading. But it wouldn't play. I then tried AQ (an online Flash-based game) and managed to get through the entire process of making a new character, but it vanished mysteriously and instantaneously afterwards. Several times.

Again, none of these problems occurred on Windows, so it's nothing to do with my computer itself, nor with the sites in question. I've tried everything I can think of, and I'm stumped.

See Flash Optimization section of the tutorial above.

---

### Post by jedimattk on 2009-07-24
I followed your instructions for dealing with conflicted plugins, restarted my computer, and now it works great. YouTube is snappy and videos start playing automatically, just like on Windows. There are no problems I've yet found with streaming Flash games, video, or other multimedia. Thanks!!!

---

### Post by lovinglinux on 2009-07-24
> **jedimattk said:**
> I followed your instructions for dealing with conflicted plugins, restarted my computer, and now it works great. YouTube is snappy and videos start playing automatically, just like on Windows. There are no problems I've yet found with streaming Flash games, video, or other multimedia. Thanks!!!

You are welcome.

---

### Post by mbreezy on 2009-08-03
I'm having problems with flash and Ubuntu.  Many flash apps that have checkboxes and/or scroll bars those components will not work.  Any fixes on this?

---

