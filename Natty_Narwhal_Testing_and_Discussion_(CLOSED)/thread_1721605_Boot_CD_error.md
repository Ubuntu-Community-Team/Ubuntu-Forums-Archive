---
title: "Boot CD error"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kingbirdy on 2011-04-04
I have a natty cd (well, dvd) that gives me an error when I try to boot with it and prompts me for something else to boot with. i wasnt sure what to type so i just shut down and came back to my lucid install. is this a problem because I used a dvd, or a real error? any help is appreciated!

EDIT: the error is as follows```

ISOLINUX 4.02 debian-20101016 ETCD Copyright (C) 1994-2010 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot:
```
at the last bit it wanted me to enter something.

---

### Post by mc4man on 2011-04-04
Had something similar a couple of times much eariler in natty, though was using usb stick.
Typing live worked, you could try that. (if may work or just produce another error

---

### Post by kingbirdy on 2011-04-06
> **mc4man said:**
> Had something similar a couple of times much eariler in natty, though was using usb stick.
Typing live worked, you could try that. (if may work or just produce another error
it did nothing for me

---

### Post by VMC on 2011-04-06
> **kingbirdy said:**
> I have a natty cd (well, dvd) that gives me an error when I try to boot with it and prompts me for something else to boot with. i wasnt sure what to type so i just shut down and came back to my lucid install. is this a problem because I used a dvd, or a real error? any help is appreciated!

EDIT: the error is as follows```

ISOLINUX 4.02 debian-20101016 ETCD Copyright (C) 1994-2010 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot:
```
at the last bit it wanted me to enter something.

There were problems with earlier versions of syslinux using ubuntu. How did you create your dvd? My Lucid does fine.

---

### Post by kingbirdy on 2011-04-07
well, I'd improperly put it on before, and so I tried to write over it (its an RW), but it wouldnt let me. so I copied the beta iso to a portable HD and then booted up windows and blanked the cd with Alcohol 120, and burned the image with the same program.

---

### Post by nyex on 2011-04-08
I'm having this same problem with Natty Beta on a usb stick (kingston, 4gb). 

I burned the same image to a cd and it did start to load but then it all went black, but I suspect it's my cd drive that is failing (reason why I'm trying the usb).

I downloaded the image twice (torrent and directly from the website) to make sure it wasn't a bad .iso, and I already lost count of how many times I created the liveusb with that tool that comes with Ubuntu.

I have no idea what to do. I have this extra notebook and I so wanted to use it to test Natty, but now I'm clueless.

---

### Post by VMC on 2011-04-08
> **nyex said:**
> I'm having this same problem with Natty Beta on a usb stick (kingston, 4gb). 

I burned the same image to a cd and it did start to load but then it all went black, but I suspect it's my cd drive that is failing (reason why I'm trying the usb).

I downloaded the image twice (torrent and directly from the website) to make sure it wasn't a bad .iso, and I already lost count of how many times I created the liveusb with that tool that comes with Ubuntu.

I have no idea what to do. I have this extra notebook and I so wanted to use it to test Natty, but now I'm clueless.

If you know how, edit the linux line and remove the silent and see if the boot completes.

---

### Post by cariboo on 2011-04-08
> **nyex said:**
> I'm having this same problem with Natty Beta on a usb stick (kingston, 4gb). 

I burned the same image to a cd and it did start to load but then it all went black, but I suspect it's my cd drive that is failing (reason why I'm trying the usb).

I downloaded the image twice (torrent and directly from the website) to make sure it wasn't a bad .iso, and I already lost count of how many times I created the liveusb with that tool that comes with Ubuntu.

I have no idea what to do. I have this extra notebook and I so wanted to use it to test Natty, but now I'm clueless.

That could indicate that the video driver isn't getting loaded properly. Try booting using the nomodeset option from the main menu screen. Press the any key when you see the man and keyboard, press F6, and select nomodeset from the menu, then press esc, and press enter. You should be taken to a desktop.

---

