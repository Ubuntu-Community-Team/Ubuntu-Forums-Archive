---
title: "USB Card Reader"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by Shadow Wolf on 2007-11-13
Hello, I'm having problems with my  Lexar USB card reader and I was wondering if someone would be willing to help out. When I plug it into my USB slot...nothing seems to happen at all aside from a momentary light up on my card reader. No icons appear on my desktop, nor in my Computer folder. The card I'm trying to have read is a 1 GB SD card that I use with my Cannon Powershot Digital Camera.

Before it would work perfectly fine in Windows XP...and Windows Vista, I would simply place it into a USB slot and it would get recognized as removable media and then I could browse to it.

I've tried looking into help files, but it only tells me steps to take if I were getting an icon of some sort, which I'm not.

By the way, I'm running Ubuntu 7.10 Gutsy Gibbion on an AMD 64 environment. If anyone could give me some advice on some steps to take, then I would appreciate it.

---

### Post by ddrichardson on 2007-11-13
What's the output of dmesg from the console when you connect it?

---

### Post by Shadow Wolf on 2007-11-13
I'm not sure what you mean by dmesg. The computer itself doesn't respond at all. It just continues about tis normal bussiness as if nothing had ever happened, but my card reader itself will have ti's little green light flash for a short moment.

---

### Post by ddrichardson on 2007-11-13
Ok, unplug it. Plug it in again and type dmesg in a terminal - post any lines that concern usb or a card reader.

---

### Post by Shadow Wolf on 2007-11-13
Heh, well this makes me blush....I plugged in the Card Reader and when I saw the light come on I started to tilt it...the light stayed on for longer so I kept it tilted at about a 45 degree angle and Linux read the reader...so it's working now. I guess I ahve to orient it into an odd position for it to connect properly.

---

### Post by ddrichardson on 2007-11-13
He he - has the cable been stressed? Quite often ignored principle of electronics known as minimum bend radius that when bent beyond cables degrade. Have a look at the connector itself on the reader, cheaper cards with poor soldering don't often grip forever.

---

