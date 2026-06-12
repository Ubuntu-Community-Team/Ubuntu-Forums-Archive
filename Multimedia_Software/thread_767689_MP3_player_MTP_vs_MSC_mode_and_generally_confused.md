---
title: "MP3 player MTP vs MSC mode and generally confused"
date: 2008-04-25
forum: Multimedia Software
---

### Post by MountainX on 2008-04-25
I'm running Hardy and I have a Sandisk Sansa c150 2GB MP3 player.

I can connect it via USB using either MTP mode (the default) or MSC mode. Which one should I use? I mainly use the player for audio books. It seems that I don't see all the files on the player when I use MSC mode, but I read that I should install mtp-tools to use MTP mode properly (even though I can already connect).

I'm just not sure of the "best practices" for using the Sansa with Linux.

I would like to create play lists too to I can play my audiobooks in the correct chapter order. What's the best way to do this?

So far, all the guides I've found deal with older versions of Ubuntu. I'm looking for the best way to do this stuff in Hardy. Thanks.

---

### Post by MountainX on 2008-04-25
I've been reading a bunch of stuff on the Sansa and Linux. I would still like to find out the answer to my question about MTP vs MSC modes with Hardy, etc.

However, for the benefit of others reading this thread, I did find a good article here:
[http://blog.linuxoss.com/2007/01/28/using-a-sandisk-mp3-player-on-a-linux-desktop/](http://blog.linuxoss.com/2007/01/28/using-a-sandisk-mp3-player-on-a-linux-desktop/)

---

### Post by mykrob on 2008-04-25
If i understand correctly, if you transferred anything to the device using MTP mode, it will not show up in MSC mode, and vice versa.. Best bet is to use the device's internal menu to format it, then set it to MSC, and ONLY use it in MSC mode. I did this with my E250 and my C200.

---

### Post by HunterThomson on 2008-04-25
Hardy already has the newest versions of MTP installed.

---

### Post by MountainX on 2008-04-26
> **HunterThomson said:**
> Hardy already has the newest versions of MTP installed.

I am able to connect in MTP mode. However, when I try to run mtp-detect, I get this:

```
mtp-detect
The program 'mtp-detect' is currently not installed.  You can install it by typing:
sudo apt-get install mtp-tools
bash: mtp-detect: command not found

```

That's why I thought it wasn't installed. Maybe I don't need mtp-detect because I am able to read and write in MTP mode. 

However, see the post above about MSC mode. Should I just use MSC in Hardy like people recommend for Gutsy? I'm still confused.

---

### Post by MountainX on 2008-04-26
> **mykrob said:**
> If i understand correctly, if you transferred anything to the device using MTP mode, it will not show up in MSC mode, and vice versa.. Best bet is to use the device's internal menu to format it, then set it to MSC, and ONLY use it in MSC mode. I did this with my E250 and my C200.

I could definitely do that. I've tested it and it works. And I think you are right about files copied in one mode not showing up in the other mode.

But in Hardy, both MTP and MSC modes work. Which is better? And will it make any difference for playlists?

Finally, I know this is a dumb question, but if I just listen to chapters of audiobooks, do I even need playlists? I assume I don't if my tags are set correctly. As you can probably tell, I'm a noob.

---

