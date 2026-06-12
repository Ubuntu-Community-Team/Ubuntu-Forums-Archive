---
title: "VOLAR dongle, Kaffeine, &quot;Cannot find demultiplexor plugin for the given media data&quot;"
date: 2010-04-22
forum: Multimedia Software
---

### Post by bliffle on 2010-04-22
I have a Aver VOLAR (white) USB dongle  for HDTV which works with Avers software on XP, but I'd like to use Kaffeine (or whatever ubuntu player) So I installed their latest software, which is "AVERMEDIA-Linux-x86-H826D-0.10-beta.sh".

I ran "w_scan" to get the channel list:

```
w_scan -f a -A 1 -c US -k

```

which seemed to do the right thing.

When I started Kaffeine I was able to do the channels, and **the very first one I highlighted came up onscreen just fine!** But then I tried to change channel and got an error msg:

"Cannot find demultiplexor plugin for the given media data"

And when I tried to change back to the original channel I got the same thing.

In fact, the only channel Kaffeine would work on was the very first one that I tried after starting Kaffeine.

So, to watch a channel I have to kill Kaffeine, restart it, then select just the channel I want to watch.

How strange.

Is that "demultiplexor plugin" unique for each channel, or for the Volar? Why did it get lost?

How can I fix it?

---

### Post by xc3RnbFO8P on 2010-04-23
Try this:
[http://ubuntuforums.org/showpost.php?p=8439240&postcount=3]("http://ubuntuforums.org/showpost.php?p=8439240&postcount=3")

---

### Post by bliffle on 2010-04-24
I tried that, but nothing changed.

The other problem I have is that SOME of the channels detected by w_scan  do not go into the Kaffeine channel list.

---

### Post by bliffle on 2010-04-28
Well, I've discovered a sort-of workaround for the channel-switching problem: carefully click once on the new channel number. If that fails, go back to the opening screen and select Digital TV again.

I have no idea why I can't get ALL the channels.

Also, some channels play very choppily.

I have none of those problems with the crappy software supplied for Windows XP. I have different problems, but I CAN get all channels on XP. However, I always try to use Kaffeine first because Ubuntu is SO much better than XP.

It may be that I should use a different player from Kaffeine, but I don't know which one or how to set it up and detect the channels.

---

