---
title: "Rhythmbox: How to connect a Win mobile device?"
date: 2010-02-28
forum: Multimedia Software
---

### Post by totoff on 2010-02-28
Dear Forum members, I'm using Ubuntu since some month and lovin it. Only one thing with Rhythmbox and my HTC mobile phone running Win mobile 6.1 is annoying: The mobile device is never recognised as a music player nor as a usb device so I can't load music via Rhythmbox. Ubuntu recognises it as umts-modem which I like and would like to maintain. But is there any way to load music on it at the same time? I've already tried different settings on the devices usb-to-pc settings menu, but this only switches on and off the modem functionality but doesn't make ubuntu recognise the device as usb or music player. Your help is much appreciated.

---

### Post by mikewhatever on 2010-02-28
Do you have to use a special program with this phone and Windows, or can you just copy music drag and drop?

---

### Post by totoff on 2010-02-28
drag and drop is just fine.

---

### Post by sgosnell on 2010-02-28
Is all the music going to internal memory, or are you using a removable flash card?  If you have a card, invest $10 in a card reader, and transfer the music that way.  It's much faster and easier.  I don't much like using Rhythmbox or anything like that for transferring files, it's much easier to do it with Nautilus.

---

### Post by totoff on 2010-03-01
thank you sgosnell, that's a good idea. i have a mini sd card which is recognised as mass storage device. that's good enough. totoff

---

### Post by sgosnell on 2010-03-01
You can use rsync to sync the contents of the card and your HDD, probably a lot faster than syncing through Rhythmbox.  If you don't want to deal with the command line, install grsync, which is a GUI frontend for rsync, and it's very simple to use.

---

