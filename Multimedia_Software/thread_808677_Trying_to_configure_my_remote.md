---
title: "Trying to configure my remote"
date: 2008-05-26
forum: Multimedia Software
---

### Post by p-stone on 2008-05-26
Hello

I recently purchased a remote control on ebay. The way I read the description I thought it was a windows MCE remote knockoff that would be easy to configure with lirc. What I got instead is a different story, the remote requires no drivers, it works out of the box, I'm assuming it's emulating a keyboard and mouse somehow. There's a d-pad sort of thing with two buttons that controls my mouse and various buttons that perform other tasks, like closing windows, skipping media and inputting number keys. There's also a row of "quick start keys" that crash my session and return me to a command prompt that I have to hard reboot from. Anyway, for the most part the remote works but I'm really curious about how it's set up and if there's any way I can remap some of the buttons inputs. The problem is that I have no idea where to begin, the instructions for the remote are quite sparse and in horrible engrish (the remote was shipped from Hong Kong) Are there any input guru's on the forum that could point me to a starting point to troubleshoot and maybe reverse engineer this strange device? For what it's worth the remote is a tg801, I found a pdf manual for it online here [www.tigerfly.net/bookpic/20073201973697210.pdf](www.tigerfly.net/bookpic/20073201973697210.pdf)
although unless you can read mandarin(?) it won't do you much good

Thanks in advance

---

### Post by gilgongo on 2008-09-07
Same here. I'm struggling with this and so far have not yet found an answer but I think I'm close. Here's what I have so far:

1. My remote is a Speed Link SL-6399. Coincidentlally, I think it's exactly the same remote as the one being talked about here (and gives the same string when I run lsusb):

[http://www.mythtv.org/wiki/index.php/Generic_HID_%22MCE%22_Remotes](http://www.mythtv.org/wiki/index.php/Generic_HID_%22MCE%22_Remotes)

This says it uses the USB HID drivers, so you don't need lircd. Indeed, at the time of writing, lircd doesn't seem to even run on Hardy, but luckily that doesn't matter.

2. The above article talks about using xmodmap to re-map the keys sent by the remote to keys on the keyboad (er, I think), but stops short at actually telling you enough about what's needed to actually do that. I found a util called xkeycaps, which shows you which keys are being hit when you (for example) hit the "Play" button on the remote. You can also do this in another way with the xev util. I used this regexp to show me what keys were being send by the remote. 

xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'

So it looks like I can tell what XWindows is getting from the remote. So far, so good.

3. I now need to work out how to map (for example) the "Stop" key on my remote to the relevant key my application needs. I'm trying to use XBMC media center, which tells me that the keyboard key "x" invokes the stop command.

4. So - the challenge: I think the remote is sending CTRL+SHIFT+s (or CTRL+S). How do I use xmodmap to translate that into just "x"? The man page for xmodmap is rather hard to understand, and I don't think I can get xkeycaps to do it. All the examples I can find seem to be assuming that you just want to map one key to another, not a modified (CTRL+something) key to another

Hmmm.

---

