---
title: "[SOLVED] Can't change channel with up/down"
date: 2008-01-25
forum: Mythbuntu
---

### Post by tomashektor on 2008-01-25
First of all...I'm a total newbie to linux/mythbuntu.

Assembled my first HTPC recently and decided that I would give Mythbuntu a try. I'm overall happy with mythbuntu, but when I watch live tv I can't change the channel with up/down on the keyboard. When I press up or down myth says something like "unknown character". If I type the channel number I can change channel, but it's not easy to browse through the channels that way.

I've checked the key settings in mythtv and up/down are the keys that are supposed to change channels. Up/down works perfectly when I go through the menus of myth. Does anyone have an idea what might be the problem?

/Tomas

---

### Post by newlinux on 2008-01-25
It sounds like you are in browse mode, which means you have to hit enter to change the channel after you press up or down. If you want this to be different go to:

Utilities/Setup->Setup->TV Settings->Playback->On Screen Display

Uncheck "Always use Browse Mode when changing channels in LiveTV"

What you are seeing is the channel and program information when you press up and down. I'm guessing you don't have program guide information setup yet which why you get "unknown channel" or "unknown character" or whatever when you browse through channels.

---

### Post by onesojourner on 2008-01-25
My remote is messed up too- same problem. I have to hit the numbers to change channels. I think I am going to have to do a fresh install. I messed everything up. I can;t even play avi files now.

---

### Post by tomashektor on 2008-01-25
> **newlinux said:**
> It sounds like you are in browse mode, which means you have to hit enter to change the channel after you press up or down. If you want this to be different go to:

Utilities/Setup->Setup->TV Settings->Playback->On Screen Display

Uncheck "Always use Browse Mode when changing channels in LiveTV"

What you are seeing is the channel and program information when you press up and down. I'm guessing you don't have program guide information setup yet which why you get "unknown channel" or "unknown character" or whatever when you browse through channels.


That did the trick! Thanks a lot.

---

